---
title: "코딩 배우기 #6 : Python"
# date: 2024-11-30 22:22:42 +0900
categories: [Note, TIL]
tags: [Python, Learn]
media_subpath: /assets/posts/2024
image: til.png
---

- 코딩을 배우다 보면 흥미로운 사실이 하나 있는데, 그것은 코딩에 `추상적인 개념`이 많다는 것이다. 코딩은 0이 아니면 1이기 때문에 복잡할지언정 모든 것이 딱딱 명확하다고 생각했었는데 공부할수록 추상적인 부분이 많다.
- 예를 들어, `return`이라는 함수가 있는데, 값을 `반환`하는 역할을 한다. 처음에는 도대체 `print`와 차이가 무언지 몰라서 한참을 헤맸다. 물론 알고나면 아무것도 아니지만 비전공자 입장에서는 당황스러웠다. 
- 아직도 `객체화`라는 의미는 이해가 가질 않는다. 아직 다른 지식이 덜 쌓여서 그런 거겠지.

### 함수 만들기
```python
def func():
	print('Hello')
func()

def func2(a, b): # 인자명은 무엇이나 관계없음
	print('Hello!', a, b) # 앞에서 설정한 인자를 모두 쓰지 않아도 됨. 또는 아예 안써도 문제 없음.
func2('Tom', 'John')

def func3(c, d):
	return c + d 
func3(3, 4)
# return은 결과를 반환하는 함수(출력이 아님 != print)
# 전단 함수에 print를 사용하여 값이 반환된것처럼 보이나 그렇지 않음
# def 아래에 여러줄의 코드 사용가능. 단, return까지만 실행됨. return이후는 실행되지 않음.
```

### 함수에서 return의 의미
- return의 의미를 설명으로 이해하기 보다는 예제로 이해하는 것이 좋을 것
- print는 값을 보여줄 뿐 값을 반환하지는 않음(print는 구문일 뿐, 함수가 아님)
- return은 값을 반환할 뿐 값을 보여주지는 않음

```python
# return 미사용시
def add(a, b):
	print(a + b)

x = add(1, 2) 
# 결과값 3은 add함수의 print로 인함
print(x)
# 결과값 None은 return이 없어 a + b 값이 x에 반환되지 않아서임
print(add(1, 2))
# 결과값 3은 print함수 안에 add(1, 2)가 반환한 값(자체적으로 print함수 있으므로)
# 결과값 None은 감싼 add가 아무런 값을 반환(return)하지 않아서 나오는 결과
```

```python
# return 사용시
def add2(a, b):
	return a + b

x = add2(1, 2) 
# 함수에 print를 포함하지 않음으로 아무런 값 출력 안함. 그러나 return을 사용해서 x는 3의 값을 받음.
print(x)
# x가 return으로 3의 값을 가짐
print(add2(1, 2))
# return으로 add2가 값을 반환하므로 3출력
```

```python
# 지역변수(local variable) : 함수 안에서 선언되고 사용됨
# 전역변수(global variable) : 함수 밖에서 선언되고 사용됨

def sum(a,b): # 여기 a는 지역변수(함수 밖으로 넘어가지 않음)
	result = a + b
	return result
a = 1         # 여기 a는 전역변수
print(sum(2,3))
```

```python
# return은 여러개의 값도 반환가능(다른 언어는 대부분 불가)
def returns(a): 
    b = a + 1
    c = b + 1 
    return a, b, c # 단, 튜플(tuple)로 반환함
print(returns(1)) 
```

```python
# return은 값을 반환하는 용도 외에 구문을 종료하는 역할로도 많이 사용
def id_check(id): 
    if id == "admin": 
        print("invalid id: admin") 
        return    # 여기서는 구문을 종료하는 용도(return 이후 구문 실행 안됨)
    print("valid id: ", id)

id_check('admin')
id_check('user')
```