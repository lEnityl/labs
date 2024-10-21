# Тема 7. Работа с файлами
Отчет по Теме #7 выполнил:
- Ковех Екатерина
- ИВТ-22-1

| Задание | Лаб_раб | Сам_раб |
| - | - | - |
| Задание 1 | + | + |
| Задание 2 | + | + |
| Задание 3 | + | + |
| Задание 4 | + | + |
| Задание 5 | + | + |
| Задание 6 | + |  |
| Задание 7 | + |  |
| Задание 8 | + |  |
| Задание 9 | + |  |
| Задание 10 | + |  |

# Лабараторные работы 
   ## Лабараторная работа 1
  ### Результат
  
 ![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l1.png)

## Лабараторная работа 2

 ```python
f = open("input.txt", "r")
print(f.readline())
f.close()

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l2.png)

## Лабараторная работа 3

 ```python
f = open("input.txt", "r")
print(f.readlines())
f.close()

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l3.png)

## Лабараторная работа 4

 ```python
with open("input.txt") as f:
    print(f.readlines())

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l4.png)

## Лабараторная работа 5

 ```python
with open("input.txt") as f:
    print(f.read())

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l5.png)

## Лабораторная работа 6
 ```python
with open("input.txt", "a+") as f:
    f.write("\nLast")

with open("input.txt", "r") as f:
    result = f.readlines()
    print(result)

```
### Результат
![Меню]()

## Лабораторная работа 7
 ```python
lines = ["one", "two", "three"]
with open("input.txt", "w") as f:
    for line in lines:
        f.write("Cycle run " + line + "\n")
    print("Done!")

```
### Результат
![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l7_1.png)
![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l7_2.png)

## Лабораторная работа 8
 ```python
import os


def print_docs(directory):
    all_files = os.walk(directory)
    for catalog in all_files:
        print(f"Papca {catalog[0]} contains: ")
        print(f"Directories: {", ".join([folder for folder in catalog[1]])}")
        print(f"Files: {", ".join(file for file in catalog[2])}")
        print("-"*40)

print_docs("C:/Users/Александр/Desktop/Программная инженерия скрины/Tema_7")

```
### Результат
![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l8.png)

## Лабораторная работа 9
 ```python
def longest_words(file):
    with open(file, encoding="utf-8") as f:
        words = f.read().split()
        max_lenght = len(max(words, key=len))
        for word in words:
            if len(word) == max_lenght:
                sought_words = word

        if len(sought_words) == 1:
            return sought_words[0]
        return sought_words


print(longest_words("input.txt"))

```
### Результат
![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l9.png)

## Лабораторная работа 10
 ```python
import csv, datetime, time

with open("rows_300.csv", "w", encoding="utf-8", newline="") as f:
    writer = csv.writer(f)
    writer.writerow(["№", "Sec", "Microsec"])
    for line in range(1,301):
        writer.writerow([line, datetime.datetime.now().second,
                         datetime.datetime.now().microsecond])
        time.sleep(0.01)

```
### Результат
![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/l10.png)


# Самостоятельные работы

## Самостоятельная работа №1

 ```python
import string

with open("input.txt", "r", encoding="utf-8") as f:
    file = f.readlines()

    deleted_words = list(string.punctuation)
    deleted_words.append("—")

    all_words = 0
    most_pop_dict = {}

    for line in file:
        line_words = line.split()

        for words in line_words:
            words = words.lower()

            if words not in deleted_words:

                for j in range(len(deleted_words)):
                    if deleted_words[j] in words:
                        words = words.replace(deleted_words[j], "")

                all_words += 1
                most_pop_dict[words] = most_pop_dict.get(words, 0) + 1

    most_pop_word = max(most_pop_dict, key=most_pop_dict.get)
    print(f"Самое популярное слово в тексте: '{most_pop_word}'. Оно встречается {most_pop_dict[most_pop_word]} раз/а.")
    print(all_words)

    f.close()

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/s1.png)

## Краткий вывод:
   В программе открывается файл, в котором больше 200 слов. Создаётся список со знаками исключениями, которые не учитываются при подсчёте(например, точка, запятая, двоеточие и тп), а так же создаётся словарь, в котором ключом будет являться слово, а значением количество встречаемости этого слова в файле. Затем запускаются 3 вложенных цикла for, которые сперва считывают строчку из файла, записывая её в список с разделителем пробелом. Затем все слова переводятся в нижний регистр для корректного подсчёта, после идёт проверка, что слово не является запрещённым символом, затем идёт проверка не присутствует ли запрещённый символ в слове(например, коггда ставится точка в конце предложения, пробела перед ней нет и слово "да" и "да." считаются за разные слова), если символ присутсвует, то он удаляется из слова и наконец слово записывается в словарь, если такого слова ранее там не было, если слово уже есть в словаре, то значение этого ключа увеличивается на 1. Затем в словаре находится ключ с наибольшим значением через функцию max и результат выводится в консоль.
 
## Самостоятельная работа №2

 ```python
def set_expenses(day: str, money: int):
    with open("input.txt", "r+") as file:
        lines = file.readlines()
        if int(lines[0]) < 0:
            print("У вас уже имеется долг, поэтому тратить больше нельзя!")
            return
        lines[0] = str(int(lines[0]) - money) + "\n"
        flag = False

        for i in range(len(lines)):
            if day in lines[i]:
                if i + 1 < len(lines):
                    lines[i + 1] = str(int(lines[i + 1]) + money) + "\n"
                else:
                    lines.append(str(money) + "\n")
                flag = True
        if not flag:
            lines.append(day + "\n")
            lines.append(str(money) + "\n")

        if int(lines[0]) >= 0:
            print(f"Запись о тратах успешно добавлена! У вас осталось {lines[0].replace("\n", "")} рублей!")
        else:
            print(
                f"Запись о тратах успешно добавлена! Сейчас у вас образовался долг в размере"
                f" {lines[0].replace("\n", "")} рублей!")

        file.seek(0)
        file.writelines(lines)
        file.truncate()
        file.close()

        question()


def get_expenses(day: str):
    with open("input.txt", "r") as file:
        lines = file.readlines()

        flag = False

        for i in range(len(lines)):
            if day in lines[i]:
                print(f"{lines[i].replace("\n", "")} вы потратили {lines[i + 1].replace("\n", "")} рублей.")
                print(f"У вас осталось {lines[0].replace("\n", "")} рублей!")
                flag = True

        if not flag:
            print("Записи для этого числа не создано, пожалуйста, создайте её!")

        file.close()

        question()


def question():
    user_say = str(
        input("Введите '+', если вы хотите добавить запись, "
              "или '=', если вы хотите узнать траты за определённую дату: \n"))
    if user_say == "+":
        user_say = str(input("Введите число и количество денег, которые были потрачены в эту дату через пробел: \n"))
        day = user_say.split()[0] + " " + user_say.split()[1]
        money = int(user_say.split()[2])
        set_expenses(day, money)
    elif user_say == "=":
        day = str(input("Введите число за которое вы хотите узнать траты: \n"))
        get_expenses(day)


if __name__ == '__main__':
    question()

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/s2.png)

## Краткий вывод:
  В программе создаётся 2 функции, первая для записи расходов, вторая для получения расходов в определённый день. Изначально существует текстовый файл для учёта расходов, в котором в первой строке записано количество денег, которые у нас имеются. При запуске программы пользователю предлагается выбрать, хочет он записать расходы или узнать их, если он хочет записать расходы, то должен ввести день в формате "день месяц" и количество этих расходов. После ввода данных вызывается первая функция, которая проверяет есть ли запись об этом дне в файле, если нет, то она создаётся в конце файла в формате "дата" "расходы", разделяясь на 2 подрядидущие строки, если есть, то к существующим расходам прибавляются новые, а из бюджета вычитается необходимая сумма. Также в случае, если бюджет станет равен 0 или меньше, то программа сообщит эб этом и не даст записать новые расходы. Если пользователь захочет получить информацию о расходах, то он должен будет указать дату, если она есть в файле, то будет выведена справка по расходам в указанный день и оставшийся бюджет.

## Самостоятельная работа №3

 ```python
with open("input.txt", "r") as file:
    lines = file.readlines()

    summ_letters = 0
    summ_words = 0
    summ_lines = len(lines)
    for i in range(len(lines)):
        summ_words += len(lines[i].split())
        for k in range(len(lines[i])):
            if (lines[i][k] != ".") and (lines[i][k] != " ") and (lines[i][k] != "\n"):
                summ_letters += 1
    print(summ_letters)
    print(summ_words)
    print(summ_lines)

```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/s3.png)

## Краткий вывод:
  В программе сперва открывается файл, затем создаются переменные для подсчёта числа символов, слов и строк. Число строк считается сразу, исходя из длинны списка, в котором каждая строка является отдельным элементом. После запускается цикл for в котором происходит подстчёт слов, путём деления элементов изначального списка на отдельные элементы, которые и являются отдельными словами. После запускается ещё один вложенный цикл for, в котором происходит подсчёт символов, при условии, что символ не является точкой, пробелом или символом перехода к следующей строке. Затем идёт вывод полученной информации в консоль. 

## Самостоятельная работа №4

 ```python
with open("input.txt", "r") as file:
    line = list(file.readline().split())

    input_str = ("Hello, world! Python IS the programming language of thE future. My EMAIL is...\n"
                 "PYTHON is awesome")
    index_next_line = input_str.index("\n")
    print(index_next_line)
    input_list = input_str.split()

    for i in range(len(input_list)):
        for k in range(len(line)):
            if line[k] in input_list[i].lower():
                for j in line[k]:
                    input_list[i] = input_list[i].lower().replace(j, "*")

    out_string = ""
    for i in input_list:
        out_string += i + " "
        if len(out_string) == index_next_line + 1:
            out_string += "\n"
    print(out_string)

```

### Результаты

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/s4.png)

## Краткий вывод:
  В программе открывается файл и из его данных создаётся список с запрещённыйми словами. Затем создаётся переменная с исходным текстом. После этот текст записывается в список, разделяя слова пробелами. Затем идёт проверка, содержится ли запрещенное слово в конкретном слове, если да, то идёт посимвольная замена символов исходного слова на "*", если этот символ содержится в запрещенном слове, после чего идёт вывод результата в консоль.
  

## Самостоятельная работа №5

Напишите программу, которая принимает поисковый запрос и выводит названия текстовых файлов, содержащих искомую подстроку.

 ```python
import os
if __name__ == '__main__':
	folder = 'C:\\Users\\ekkov\\OneDrive\\Рабочий стол\\python\\nado'
	answ = set()
	search = input()
	for filename in os.listdir(folder):
            filepath = os.path.join(folder, filename)
with open(filepath, 'r', encoding = 'utf-8') as fp:
        	for line in fp:
            	    if search in line:
                	    answ.add(filename)
for i in answ:
	print(i) 

```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_7/lab7/s5.png)

## Краткий вывод:
  Программа ищет слово по файлам и выводит название файла, в котором нашла, на экран


# Общий вывод 

Для работы с файлами в Python используется функция open(), которая открывает файлы для чтения или записи.
Файлы могут быть прочитаны с использованием метода read() или записаны с использованием метода write(). Это позволяет программам взаимодействовать с содержимым файлов.
Важно закрывать файлы после их использования с помощью метода close(), чтобы избежать утечек ресурсов.
Python поддерживает работу с текстовыми файлами, бинарными файлами, а также файлами в режиме добавления данных.
Работа с файлами может вызывать ошибки, поэтому важно использовать конструкции обработки исключений, такие как try и except, для более надежного кода.

Эффективное владение навыками работы с файлами не только обеспечивает управление данными в программах, но также способствует безопасности и устойчивости приложений.
