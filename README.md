# Тема 8
Отчет по Теме #8 выполнил:
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
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

my_car=Car("Save", "Me")
```
  ### Результат
  
 ![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/l1.png)

## Лабараторная работа 2
  
 ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")
my_car=Car("Save", "Me")
my_car.drive()
```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/l2.png)

## Лабараторная работа 3
  
 ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")

class ECar(Car):
    def __init__(self, make, model, bc):
        super().__init__(make, model)
        self.bc = bc

    def charge(self):
        print(f"Charging the {self.make} {self.model} with {self.bc} kWh")

my_Ecar=ECar("Tesla", "S", 75)
my_Ecar.drive()
my_Ecar.charge()
```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/l3.png)

## Лабараторная работа 4

 ```python
class Car:
    def __init__(self, make, model):
        self.make = make
        self.model= model

    def drive(self):
        print(f"Driving the {self.make} {self.model}")


my_car=Car("Tesla", "S")
print(my_car.make)
my_car.drive()
```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/l4.png)

## Лабараторная работа 5

 ```python
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height
    
    def area(self):
        return self.width * self.height
    
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    def area(self):
        return 3,14*self.radius*self.radius
```
### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/l5.png)



# Самостоятельные работы

## Самостоятельная работа №1

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

    def awail(self):
        print(f"I have {self.food} {self.sleep}")

my_mood=Mood("No food", "No sleep")
my_mood.awail()
```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/s1.png)

## Краткий вывод:
Класс — это шаблон для создания объектов. Он определяет свойства (атрибуты) и поведение (методы) объектов
 
## Самостоятельная работа №2

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

    def awail(self):
        print(f"I have {self.food} {self.sleep}")

my_mood=Mood("No food", "No sleep")
my_mood.awail()
```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/s1.png)

## Краткий вывод:

Атрибуты в объектно-ориентированном программировании представляют собой переменные, которые хранят состояние объекта и определяют его характеристики

## Самостоятельная работа №3

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

class EMood(Mood):
    def __init__(self, food, sleep, emoites):
        super().__init__(food, sleep)
        self.e = emoites

    def feel(self):
        print(f"I have {self.food} {self.sleep} and {self.e}")
my_mood=EMood("no food", "no sleep", "depression")
my_mood.feel()
```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/s3.png)

## Краткий вывод:

Наследование позволяет создавать новые классы на основе существующих. Новый класс (подкласс) наследует атрибуты и методы родительского класса (суперкласса), что способствует повторному использованию кода и улучшает его структуру.

## Самостоятельная работа №4

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

class EMood(Mood):
    def __init__(self, food, sleep, emoites):
        super().__init__(food, sleep)
        self.e = emoites

    def feel(self):
        print(f"I have {self.food} {self.sleep} and {self.e}")
my_mood=EMood("no food", "no sleep", "depression")
my_mood.feel()
```

### Результаты

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/s3.png)

## Краткий вывод:

Инкапсуляция позволяет скрывать внутренние детали реализации и защищать состояние объекта от несанкционированного доступа. Это достигается с помощью модификаторов доступа (например, использование одного или двух подчеркиваний перед именем атрибута).

## Самостоятельная работа №5

 ```python
class Mood:
    def __init__(self, food, sleep):
        self.food = food
        self.sleep= sleep

class EMood(Mood):
    def __init__(self, food, sleep, emoites):
        super().__init__(food, sleep)
        self.e = emoites

    def feel(self):
        print(f"I have {self.food} {self.sleep} and {self.e}")
my_mood=EMood("no food", "no sleep", "depression")
my_mood.feel()
```

### Результат

![Меню](https://github.com/lEnityl/labs/blob/Tema_8/lab8/s3.png)

## Краткий вывод:

Полиморфизм позволяет использовать объекты разных классов через единый интерфейс. Это означает, что один и тот же метод может вести себя по-разному в зависимости от объекта, который его вызывает

# Общий вывод 

Объектно-ориентированное программирование — это парадигма программирования, которая основывается на концепции "объектов", представляющих собой экземпляры классов. ООП позволяет организовывать код таким образом, чтобы он был более структурированным, переиспользуемым и удобным для сопровождения
