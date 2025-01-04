---
title: "코딩 배우기 #9 : Python 클래스와 객체"
date: 2024-12-30 15:34:26 +0900
categories: [Note, TIL]
tags: [Python, Learn]
image: /assets/posts/til.png
---

- 늘상 들리던 "객체지향"이라는 말이 드디어 나오다.
- 아, 이런식이구나 싶다가도 구체적인 말로 표현하려고 하면 또 명확하지가 않다.

### 클래스의 개념
```python
# 클래스
class Animal:
    def __init__(self, species, age, name):
        self.species = species
        self.age = age
        self.name = name

    def eat(self):
        print(f"{self.name}이(가) 먹이를 먹습니다.")

    def move(self):
        print(f"{self.name}이(가) 움직입니다.")

    def sound(self):
        print(f"{self.name}이(가) 소리를 냅니다.")

# 객체는 클래스에 의해 정의된다.
dog = Animal("개", 3, "멍멍이")
cat = Animal("고양이", 2, "야옹이")

# 객체는 클래스에서 정의한 속성(종, 나이, 이름)과 메서드(eat, move, sound)를 가진다. 
print(dog.species)
print(dog.age)
print(dog.name)
print(cat.species)
print(cat.age)
print(cat.name)
```
### 클래스의 상속
```python
# 클래스 상속
class Dog(Animal):
    def bark(self):
        print(f"{self.name}이(가) 멍멍 짖습니다.")

class Cat(Animal):
    def meow(self):
        print(f"{self.name}이(가) 야옹 소리를 냅니다.")

dog = Dog("개개", 33, "멍멍이이")
cat = Cat("고양양", 22, "야옹옹이")

dog.eat()
dog.move()
dog.bark()
cat.eat()
cat.move()
cat.meow()
```
