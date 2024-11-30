---
title: "코딩 배우기 #8 : Python"
# date: 2024-11-30 22:22:42 +0900
categories: [Note, TIL]
tags: [Python, Learn]
media_subpath: /assets/posts/2024
image: til.png
---

- 데이터 구조는 크게 List, Tuple, Dictionary, Set 이렇게 4가지 정도인 것 같다.
- 배우는 입장에서는 어떤 형태이든 명령어는 동일하면 좋겠는데, 데이터 구조에 따라 명령어가 미묘하게 다르다. 예를 들어 List는 추가할때, `list.append()`를 사용하지만 Set는 `set.add() 또는 set.update`를 사용한다. `del`은 List에서는 사용가능하지만 Set에서는 사용불가이다.
- 이유가 있을 것이다.

### 데이터구조 : Dictionary

```python
# 빈 데이터 만들기
data_list = list() # []
data_tuple = tuple() # () // 그런데 Tuple은 추가, 삭제가 안되니 빈목록을 쓸 이유가?
data_dict = dict() # {}
```

```python
# Dictionary
data = {'한국':'KR', '일본':'JP', '중국':'CN'} # 키:값
data['한국'] # 읽기
data['미국'] = 'US' # 추가
del data['한국'] # 삭제
data['일본'] = 'JR' # 수정
# 키 값의 수정은 삭제후 추가로 처리
print(data)

data.keys() # 키만 추출(리스트 형태)
data.values() # 값만 추출(리스트 형태)
data.items() # 키와 값 모두 추출(리스트 안에 튜플쌍 형태)
```

### 데이터구조 : SET
```python
# 선언 + 입력
# 변수명 = set(),
# 변수명 = {data1, data2, ...}
# 변수명 = set(데이터1),
# 변수명 = set({데이터1, 데이터2, ...})
data_set = set() # {}
data_set = {} # dict와 같은 괄호
type(data_set) # 타입이 dict로 출력됨, 때문에 집합은 set()을 많이 사용함

data_set = set('apple') # 단 하나의 데이터일 경우
data_set = set({'apple', 'dell'}) # 두개 이상인 경우

# 읽기
# Set은 인덱스를 지원하지 않아 아래와 같이 적으면 에러
data_set[0] # 에러

# 그러나 반복문에서는 지원
for i in data_set:
	print(data)

data_set = {'apple', 'dell', 'samsung', 'lg'}
'motorola' in data_set # 있는지 없는지 확인. True/False로 결과 나옴
```

```python
# 연산
data1 = {'apple', 'samsung', 'lg'}
data2 = {'samsung', 'lg', 'sk'}
print(data1 & data2) # 교집합
print(data1 | data2) # 합집합
print(data1 - data2) # 차집합
print(data1 ^ data2) # 여집합
```

```python
# Set은 순서가 없고, 중복이 없음
# 수학 집합 연산을 위한 자료형
# 중복이 없는 특성을 이용하는 경우
data_list = ['apple', 'dell', 'samsung', 'lg', 'apple', 'dell', 'samsung', 'lg', 'apple', 'dell', 'samsung', 'lg']
data_list2 = set(data_list) # 중복 데이터가 정리되어 변환됨
print(data_list2)
print(list(data_list2))
```

```python
# Set 관련
set_data = {1, 2, 3}
set_data.add(4) # 리스트와 달리 append가 아니다.
set_data.update([5, 6]) # 여러 데이터 추가
set_data.remove(2) # Set은 인덱스를 지원하지 않아 del은 사용불가
print(set_data)
```
