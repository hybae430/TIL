#  Data Container

## 컨테이너 (Container)

- 여러 개의 값을 저장할 수 있는 것
  - 시퀀스(Sequence) 형: 순서가 있는(ordered) 데이터
  - 비 시퀀스(Non-sequence)형: 순서가 없는(unordered) 데이터

### 시퀀스형 컨테이너

> `시퀀스(Sequence)`는 데이터가 순서대로 나열된 형식을 나타낸다. (정렬: sorted와 다름)

#### 특징

1. 순서를 가질 수 있다.
2. Indexing이 가능하다.

#### 종류

1. 리스트(list)
2. 튜플(tuple)
3. 레인지(range)
4. *문자형(string)* 
5. *바이너리(binary)*

### 리스트 (`list`)

> 리스트는 대괄호 `[]` 및 `list()`를 통해 만들 수 있고, 값에 대한 접근은 `list[i]`로 한다.

### 튜플 (`tuple`)

> 튜플은 리스트와 유사하지만, `()`로 묶어 표현한다.

- python_intro 파일에 있는 `swap`, `divmod` 예제 또한 튜플과 유사하거나 활용하는 기능이다.
- 하나의 항목으로 구성된 튜플은 값 뒤에 쉼표를 붙여서 만든다.

```python
a = (3,)
print(a)			# (3,) 출력 (오류 X)
```

### 레인지 (`range()`)

> `range`는 숫자의 시퀀스를 나타내기 위해 사용된다.

- `range(n)`: 0부터 n-1까지의 값을 가짐
- `range(n, m)`: n부터 m-1까지의 값을 가짐
- `range(n, m, s)`: n부터 m-1까지 s만큼 증가/감소하는 값을 가짐(s의 부호에 따라)

### 시퀀스에서 활용할 수 있는 연산자 / 함수

| operation      | 설명                                    |
| -------------- | --------------------------------------- |
| `in`/`not in`  | containment test                        |
| `+`            | concatenation                           |
| s`*`n          | s를 n번 반복하여 더하기                 |
| `s[i : j : k]` | i번째부터 j-1번째까지 k간격으로 slicing |
| len(s)         | s의 길이                                |
| min(s)/max(s)  | 최솟/최댓값                             |
| s.count(x)     | s에서 x의 개수                          |

```python
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# containment test
3 in numbers		# True
10 not in numbers	# False

# concatenation
a = [7, 1, 3]
numbers + a

b = [0] * 6
print(b)			# [0, 0, 0, 0, 0, 0]

c = list(range(0, 31, 3))
print(c)			# [0, 3, 6, 9, 12, 15, 18, 21, 24, 27, 30]
```

### 비 시퀀스형 컨테이너

- set
- dictionary

#### `set`

- `set`은 순서가 없는 자료구조이다.
  - 수학에서의 집합과 동일하게 처리되며, `{}`로 만든다.
  - 값이 중복되지 않고(여러 번 넣어도 한 개로 처리), 빈 셋은 `set()`로만 생성가능하다. (`{}`X)
  - 문자의 경우 알파벳 순으로, 숫자의 경우 오름차순으로 자동정렬된다.
- `set`의 연산자는 `|` `&`가 있으며, 각각 합집합과 교집합을 구할 수 있다.

```python
set1 = {'v1', 'v2'}
set2 = {'v1', 'v1', 'v3', 'v4'}

# 합집합/교집합 연산
print(set1 | set2)		# {'v1', 'v2', 'v3', 'v4'}
print(set1 & set2)		# {'v1'}

# 중복값 없음
set2					# {'v1', 'v3', 'v4'}

# list의 중복값 없애기
l = [1,1,3,5,2,2,6,4,3,6,6,6,2]
l = set(l)

print(list(l))			# [1, 2, 3, 4, 5, 6]
```

#### `dictionary`

- `dictionary`는 `key`와 `value`가 쌍으로 이루어져 있는 궁극의 자료구조이다.
  - `{}`나 `dict()`로 생성할 수 있다. (빈 `set`을 `{}`로 생성할 수 없는 이유!)
    - 요소 추가는 (`dictionary[key] = value`로도 가능)
  - `key`는 변경 불가능한 데이터만 가능하다. (string, integer, float, boolean, tuple, range)
    - `key`는 중복 불가능하다.
  - `value`는 `list`, `dictionary`를 포함한 모든 것이 가능하다.

```python
# 빈 dictionary 생성
dic1 = {}
dic2 = dict()

# key/value 확인하기
dic1 = {'서울': '02', '경기': '031'}
dic1.keys()			# dict.keys(['서울', '경기'])
dic1.values()		# dict_values(['02', '031'])
dic1.items()		# dict_items([('서울', '02'), ('경기', '031')])
```

### 컨테이너형 형변환

|                | string |   list   |  tuple   | range |   set    | dictionary |
| :------------: | :----: | :------: | :------: | :---: | :------: | :--------: |
|   **string**   |        |    O     |    O     |   X   |    O     |     X      |
|    **list**    |   O    |          |    O     |   X   |    O     |     X      |
|   **tuple**    |   O    |    O     |          |   X   |    O     |     X      |
|   **range**    |   O    |    O     |    O     |       |    O     |     X      |
|    **set**     |   O    |    O     |    O     |   X   |          |     X      |
| **dictionary** |   O    | O(key만) | O(key만) |   X   | O(key만) |            |

## 데이터의 분류 **(중요!)**

> `mutable` vs. `immutable`

### 변경 불가능한 (`immutable`) 데이터

- 숫자(Number)
- 글자(String)
- 참/거짓(Boolean)
- `range()`
- `tuple()`
- `frozenset()`

### 변경 가능한(`mutable`) 데이터

- `list`
- `dict`
- `set`
- 사용자가 만든 데이터 타입