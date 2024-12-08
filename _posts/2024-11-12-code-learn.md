---
title: "코딩 배우기 #1 : Python 변수"
date: 2024-11-12 21:21:57 +0900
categories: [Note, TIL]
tags: [Python, Learn]
media_subpath: /assets/posts/2024
image: til.png
---

- 파이썬이 직관적이라는 말이 이해가 된다. 어떻게 보면 엑셀과도 비슷하다는 생각이 드는데, 특히 문자열은 꼭 " "로 감싸주어야 작동하는 것이 닮았다.
- "Hello World!"는 만국 공통이구나. 워드프레스를 설치하면 항상 맨 처음 보던 문구.
- 너무 정리해서 적으려 하지말고, 일단은 적어야겠다.

### 출력
```python
print("Hello World!")
```

### 계산
```python
print(3 + 7)
print(9 - 3)
print(2 * 6)
print(2 ** 3) # 거듭제곱
print(7 / 4) # 일반적인 나누기
print(7 // 4) # 몫
print(7 % 4) # 나머지

# 표시방법
num1 = 2
num2 = 3
print (num1, "+", num2, "=", num1 + num2)
```

### 변수

```python
# 변수의 종류
str_data = "Hello" # 문자열(string)
int_data = 1       # 숫자:정수(integer)
float_data = 1.1   # 숫자:부동소수점(float)
bool_data = True   # 특별한 타입:True/False(Boolean)
print(str_data, int_data, float_data, bool_data)

# 네이밍컨벤션(Naming Convention)
# 식별자를 만들 때 가독성이 좋도록 단어를 한눈에 구분하기 위해서 규정한 이름짓는 규칙
myCamelCase = 'Camel Case'
MyPascalCase = 'Pascal Case'
my_snake_case = 'Snake Case' # ✔ // mysnakecase in not recommended
# 숫자로 시작할수 없음, 특수문자는 언더바만 허용, 공백불가

# Boolean
print(3 > 7)
print(3 < 7) 
print(3 >= 7)
print(3 <= 7) 
print(3 == 7) 
print(3 != 7) # <,>,!는 = 앞에 와야함

# 변수타입
# 형변환(Type casting)
print(float(1))  # int to float 
print(int(1.1))  # float to int 
print(str(2))    # int to string 
print(int("3")) # string to int

# 타입확인
print(type(int("3")))
```
