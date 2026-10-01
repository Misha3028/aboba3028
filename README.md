import random


class Student:
    def __init__(self, name):
        self.name = name
        self.progress = 10
        self.gladness = 30
        self.energy = 50
        self.money = 1000
        self.alive = True

    def study(self):
        print("Я пішов в IT STEP")
        self.progress += 2
        self.energy -= 1
        self.money -= 40
        self.gladness += random.randint(-4, 1)

    def chill(self):
        print("Я пішов гулять с кєнтамі")
        self.progress -= 0.5
        self.energy -= 4
        self.gladness += 1
        self.money -= 50

    def sleep(self):
        print("Я пішов спать")
        self.energy += 8
        self.gladness += 1

    def eat(self):
        print("Я покушав чіпсікі і Нон Стопчіка")
        self.energy += 1
        self.gladness += 1
        self.money -= 80

    def work(self):
        print("Я пішов арбайтать на завод")
        self.energy += random.randint(-4, -1)
        self.gladness -= 1
        self.money += 300


    def is_alive(self):
        if self.gladness <= 0:
            print("В мене дипресняк :(")
            self.alive = False
        if self.energy <= 0:
            print("В мене нема сил будто переїхав камаз :(")
            self.alive = False
        if self.progress <= 0:
            print("В мене в мозгах одні брейнроти :(")
            self.alive = False
        if self.money <= 0:
            print("Тепер я бомж і в мене нєма дєнєг :(")
            self.alive = False
        if self.progress > 100:
            print("Я умні бо закінчив шаг")
            self.alive = False

    def live(self, day):
        print(f"День №{day} з життя {self}")
        print("-"*30)

        func = [self.study, self.chill, self.sleep, self.eat, self.work]
        random.choice(func)()

        self.info()
        self.is_alive()
        print()

    def info(self):
        print(f"На сьогодні {self.name} має:")
        print(f"Задоволення : {self.gladness}")
        print(f"Знання      : {self.progress}")
        print(f"Енергія     : {self.energy}")
        print(f"Гроші       : {self.money}")

student = Student("Mishanya")
for day in range(365):
    if not student.alive:
        break
    student.live(day)
