# Тема 10. Декораторы и исключения
Отчет по Теме #10 выполнил:
- Ковех Екатерина
- ИВТ-22-1

| Задание | Лаб_раб | Сам_раб |
| - | - | - |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |


# Лабараторные работы 
   ## Лабараторная работа 1

  ```python
from functools import lru_cache


@lru_cache(None)
def fib(n):
    if n == 0:
        return 0
    elif n == 1:
        return 1
    return fib(n - 1) + fib(n - 2)


if __name__ == '__main__':
    print(fib(496))


```
  ### Результат
  
 ![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/l1.png)

## Лабараторная работа 2

 ```python
def check(input_func):
    def output_func(*args):
        name, age = args[0], args[1],

        if age < 0 or age > 130:
            age = "Nononono"
        input_func(name, age)

    return output_func


@check
def personal_info(name, age):
    print(f"Name: {name} Age: {age}")


if __name__ == '__main__':
    personal_info("Volodimir", 38)
    personal_info("Alex", -5)
    personal_info("Tamik", 131, 14, 1, 1, 1, 1, 1)

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/l2.png)

## Лабараторная работа 3

 ```python
def data(*args):
    try:
        for i in range(len(*args)):
            try:
                result = (args[0][i] * 15) // 10
                print(result)
            except Exception as ex:
                print(ex)
    except Exception as e:
        print(e)
    finally:
        print("Information is obrabotana")


if __name__ == '__main__':
    data([1, 15, "Hello", "i", "try", "crash", 3, 2])

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/l3.png)

## Лабараторная работа 4

 ```python
class NegativeValueException(Exception):
    pass


def check_name(name):
    if len(name) > 10:
        raise NegativeValueException("Len > 10 simbols")
    else:
        print("All is fine")


if __name__ == '__main__':
    name = "12345678910"
    check_name(name)

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/l4.png)

## Лабараторная работа 5

 ```python
class SiteChecker:
    def __init__(self, func):
        print("> Class SiteChecker metod __init__: all is good")
        self.func = func

    def __call__(self):
        print("> Test before start", self.func.__name__)
        self.func()
        print("> Test free on")


@SiteChecker
def site():
    print("Site is hard working")


if __name__ == '__main__':
    print(">> Site started")
    site()
    print(">> Site off")

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/l5.png)



# Самостоятельные работы

## Самостоятельная работа №1

  ```python
import time


def fib():
    fib1 = fib2 = 1

    for i in range(2, 200):
        fib1, fib2 = fib2, fib1 + fib2
        print(fib2, end=" ")


if __name__ == '__main__':
    a = time.time()
    fib()
    b = time.time()
    print(f"\nПрограмма выполнялась {int((b - a) * 1000)} миллисекунд")

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/s1.png)

## Краткий вывод:
Программа считает время начала выполнения функции и время, когда функция будет выполнена, после чего выводит результат в консоль.
 
## Самостоятельная работа №2

 ```python
def check_file(name):
    try:
        f = open(name)

        f_str = f.readlines()
        f_str[0] = f_str[0]
        for i in f_str:
            print(i, end="")
    except:
        print("Файл пустой")


if __name__ == '__main__':
    check_file("not_space.txt")

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/s2.png)

## Краткий вывод:
Программа получает на вход имя файла, если файл находится в той же директории, что и программа, либо путь до файла, после чего в блоке трай происходит чтение этого файла, все строки файла записываются в переменную f_str, после чего происходит попытка перезаписать значение первой строки на само себя, если это получится сделать, то программа выведет файл построчно, если файл будет пустой, то будет выброшено исключение, после чего в консоль будет выведена соответствующая информация.

## Самостоятельная работа №3

 ```python
def func(x):
    try:
        print(2 + int(x))
    except ValueError:
        print("Неподходящий тип данных. Ожидалось число")


if __name__ == '__main__':
    func(input("Введите число: "))

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/s3.png)

## Краткий вывод:
Программа получает число от пользователя, которое передаёт в функцию, если было передано целое число, то программа выведет в консоль результат от 2+n. Если программа выбросит ошибку ValueError, то программа её обработает и в консоль выведет предупреждение.

## Самостоятельная работа №4

 ```python
def debug_decorator(func):
    def wrapper(*args):
        print(f"Вызов функции: {func.__name__}")
        print(f"Аргументы: {args[0], args[1]}")
        result = func(args[0], args[1])
        print(f"Результат: {result}")
        return result

    return wrapper


@debug_decorator
def addition(x, y):
    return x + y


@debug_decorator
def division(x, y):
    return x / y


if __name__ == '__main__':
    addition(11, 14)
    print()
    division(11, 14)

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/s4.png)

## Краткий вывод:
Был реализован декоратор для дебага, который выводит в консоль информацию о том какая функция была вызвана, что она получила на вход и какой результат функции был возвращён.

## Самостоятельная работа №5

 ```python
class NegativeValueError(Exception):
    pass


def try_number(value):
    if value < 0:
        raise NegativeValueError(value)
    return value * 2


try:
    result = try_number(5)
    print(f"Результат обработки: {result}")
except NegativeValueError as e:
    print(f"Произошла ошибка: {e}")

try:
    result = try_number(-3)
    print(f"Результат обработки: {result}")
except NegativeValueError as e:
    print(f"Произошла ошибка: {e}")

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_10/lab10/s5.png)

## Краткий вывод:

В программе был создан класс исключений, который наследуется от класса с исключениями, если программа в блоке try получит ошибку, то её обработает и выведет необходимую информацию.


# Общий вывод 

Декораторы и исключения являются важными элементами языка программирования Python, играя ключевую роль в управлении поведением программы и обработке ошибок. Изучив их применение, можно сделать следующие выводы:

   1. Декораторы для модификации функций:
   В Python декораторы предоставляют элегантный способ модифицировать поведение функций. Они позволяют добавлять дополнительную функциональность к существующим функциям, не изменяя их код напрямую.

   2. Обработка исключений:
   Исключения в Python предоставляют механизм обработки ошибок. Блоки try-except позволяют написать код, который может корректно реагировать на возможные ошибки в процессе выполнения программы, обеспечивая    более устойчивую работу.
   
   3. Пользовательские исключения:
   Python позволяет создавать собственные классы исключений, что делает возможным определение и обработку специфичных ситуаций в приложении. Это улучшает читаемость кода и делает его более модульным.
   
   4. Контекстные менеджеры:
   Декораторы также используются для создания контекстных менеджеров, которые облегчают работу с ресурсами, такими как файлы или сетевые соединения, и автоматически освобождают их после использования.
   
   5. Обработка ошибок ввода/вывода:
   Декораторы и исключения в Python играют важную роль при обработке ошибок ввода/вывода. Они позволяют создавать более надежные программы, способные адекватно реагировать на различные сценарии                взаимодействия с внешними данными.

Использование декораторов и обработка исключений предоставляют разработчикам мощные инструменты для создания надежных и гибких программ в Python. Эти концепции становятся фундаментом для эффективного управления потоком выполнения и обеспечивают более безопасное взаимодействие с данными и ресурсами.
