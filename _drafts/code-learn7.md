---
title: "코딩 배우기 #7 : Python"
# date: 2024-11-30 22:22:42 +0900
categories: [Note, TIL]
tags: [Python, Learn]
media_subpath: /assets/posts/2024
image: til.png
---

### 데이터 구조 : Tuple
```python
# 수정, 추가, 삭제 안됨
# 선언하고 읽기만 가능
# return 하면 Tuple로 결과값이 반환됨
# 그럼에도 불구하고 가능한 것
data1 = (1, 2, 3)
data2 = (4, 5, 6)
data3 = data1 + data2
print(data3)
data4 = data1 * 3
print(data4)
```

```python
# Tuple은 변수값을 상호 교환할 때 사용 가능
x = 1
y = 2
# x, y 값을 서로 바꿀 경우 보통은 임시 변수를 만들어서 교환하나 파이썬 Tuple은 아래처럼 처리 가능
x, y = y, x # 이렇게 쓰면 양쪽이 Tuple로 인식됨
print(x, y)
```

```python
# Tuple 덕분에 여러값 반환 가능
def func(a, b):
	plus = a + b
	minus = a - b
	return plus, minus # 두변수를 괄호로 묶어도 됨
plus, minus = func(5, 3)
print(plus, minus)
```

```python
# List와 Tuple의 전환
print(list((1, 2)))
print(tuple([3, 4]))
```
