# 데이터 구조 (Data Structure) 1

> **Program = Data Sturcture + Algorithm** -Niklaus Wirth

- 순서가 있는(ordered) 데이터 구조
  - 문자열(String)
  - 리스트(List)
- 데이터 구조에 적용 가능한 Built-in Function
  - `map()`
  - `filter()`



## 문자열 (String)

> Immutable, ordered, iterable

### 조회 / 탐색

- `.find(x)`: **x의 첫 번째 위치**를 반환합니다. 값이 존재하지 않을 경우 `-1`을 반환합니다.
- `.index(x)`: **x의 첫 번째 위치**를 반환합니다. 값이 존재하지 않을 경우, **오류**가 발생합니다.

### 값 변경

- `.replace(old, new[, count])`: `old`의 문자열을 `new`의 문자열로 바꿔 반환합니다. count를 지정하면 그 횟수만큼만 시행합니다.

- `.strip([chars])`: 특정한 문자를 제거합니다.

  ```python
  '	oh!\n'.strip()			# 특정 문자 지정없으면 공백 제거 -> oh!
  '	oh!\n	'.lstrip()		# 'oh!\n	' 왼쪽만 제거
  'hehehihihihi'.rstrip('hi')		# 'hehe' 오른쪽만 제거
  ```

- `.split()`: 문자열을 특정 단위로 나누어 리스트로 반환합니다.

- `'separator'.join(iterable)`: separator를 구분자로 합쳐 한 문자열로 반환합니다.

### 문자 변형

> **원본 자체를 변형시키는 것이 아님!**

- `.capitalize()`: 맨 앞글자를 대문자로 바꿔 반환
- `.title()`: 공백이나 `''`이후를 대문자로 바꿔 반환
- `.upper()`: 문자열 전체를 대문자로 바꿔 반환

```python
a = 'this is my student\'s call'

a.capitalize()		# "This is my student's call"
a.title()			# "This Is My Student'S Call"
a.upper()			# "THIS IS MY STUDENT'S CALL"
```

- `.lower()`: 문자열 전체를 소문자로 바꿔 반환
- `.swapcase()`: 문자열의 대소문자를 서로 바꿔 반환
- 문자열 검증 메소드 (참 / 거짓 반환): `.isalpha()`, `.isdecimal()`, `.isdigit()`, `.isnumeric()`, `.isspace()`, `.isupper()`, `.istitle()`, `.islower()`



## 리스트 (List)

> Mutable, ordered, iterable

### 값 추가 및 삭제

- `.append(x)`: 리스트 맨 뒤에 값을 추가합니다.
- `.extend(iterable)`: 리스트에 iterable(list, range, tuple, *string*) 값을 붙일 수 있습니다.

```python
cafe = ['starbucks']			# ['starbucks']
cafe.append(['hollys'])			# ['starbucks', ['hollys']]
cafe.extend(['tomntoms'])		# ['starbucks', ['hollys'], 'tomntoms']
cafe.append('gongcha')			# ['starbucks', ['hollys'], 'tomntoms', 										'gongcha']
cafe.extend('ediya')			# ['starbucks', ['hollys'], 'tomntoms', 										'gongcha', 'e', 'd', 'i', 'y', 'a']
```

- `.insert(i, x)`: `i`번째 위치에 `x`를 추가합니다.
  - `i`가 리스트의 길이를 넘어설 때는 리스트 맨 뒤에 원소를 추가합니다.
- `.remove(x)`: 리스트에서 값이 x인 것을 삭제합니다. 값이 없을 경우 오류가 발생합니다.
- `.pop(i)`: `i`번째 위치의 값을 삭제하고 반환합니다. `i`가 없을 경우 맨 뒤의 항목으로 대신합니다.
- `.clear()`: 빈 리스트로 초기화합니다.

### 탐색 및 정렬

- `.index(x)`: `x`값의 index를 반환합니다. 값이 없을 경우 오류가 발생합니다.

- `.count(x)`: `x`값의 개수를 반환합니다.

- `.sort()`: `sorted()`와 달리 **원본 list를 변형시키고, None을 리턴합니다**

- `.reverse()`: 반대로 뒤집습니다. **(정렬 아님!)**

  ```python
  a = ['starbucks', 'hollys', 'tomntoms']
  a.reverse()		# 이대로 출력하면 None return
  print(a)		# ['tomntoms', 'hollys', 'starbucks']
  ```

### 리스트 복사

- `copy_list = original_list` 등으로 복사하면 **절대 안됨**! (참조값이 복사되어 둘다 원본이 되어버림)

#### 얕은 복사 (shallow copy)

1. slice 연산자 사용 `[:]`

   ```python
   a = [1, 2, 3]
   b = a[:]
   ```

2. `list()` 활용

   ```python
   a = [1, 2, 3]
   b = list(a)
   ```

#### 깊은 복사 (deep copy)

```python
import copy
a = [1, 2, [1, 2]]
b = copy.deepcopy(a)
```

### List Comprehension

> 표현식과 제어문을 통해 리스트를 생성합니다. 여러 줄의 코드를 한 줄로 줄일 수 있습니다.

```python
even_list = [i for i in range(1, 11) if i % 2 == 0]
print(even_list) = [2, 4, 6, 8, 10]

# 1부터 50 사이의 자연수 중 피타고라스 방정식 만족하는 수 찾기
result = [(x, y, z) for x in range(1, 50) for y in range(x + 1, 50) for z in range(y + 1, 50) if z * z == x * x + y * y]

# 모음 제거하기
result = [word for word in words if word not in vowels]
```

- elif는 if else문의 중첩으로 써야 합니다.
  - [식 if 조건식 else 식 if ... else ... for 변수 in iterable]



## 데이터 구조에 적용가능한 Built-in Function

> iterable 데이터 구조에 적용가능한 Built-in Function
>
> iterable: `list`, `dict`, `set`, `str`, `bytes`, `tuple`, `range`

- `map(function, iterable)`

  -  iterable 데이터 구조의 모든 요소에 function 적용 후 `map_object`형태로 반환합니다.

  ```python
  # function으로 사용자 정의 함수도 쓸 수 있음
  new_numbers = list(map(cube, numbers))		# cube(n)은 세제곱 사용자 정의 함수
  ```

- filter(function, iterable)

  - iterable 데이터 구조에서 function 반환값이 `True`인 것만 `filter object`로 반환합니다.

  ```python
  new_numbers = list(filter(odd, numbers))	# odd(n)은 홀수면 참 반환하는 함수
  new_numbers = [number for number in numbers if number % 2]		# 동일 값 반환
  ```

- `zip(*iterables)`

  - 복수의 iterable 객체를 모아 튜플의 모음으로 구성된 `zip object`로 반환합니다.

  ```python
  drinks = ['beer', 'wine', 'soju']
  foods = ['chicken', 'pasta', 'pork']
  pair = list(zip(drinks, foods))		# [('beer, chicken'), ('wine', 'pasta'), 									('soju, pork')]
  ```

- `reduce(function, iterable[, initializer])`

  - 인자가 두 개인 `function`을 왼쪽에서 오른쪽으로 `iterable` 항목에 누적으로 적용하여 단일 값으로 줄입니다.

  ```python
  from functools import reduce
  reduce(lambda x, y: x + y, [1, 2, 3, 4, 5])		# ((((1 + 2) + 3) + 4) + 5)
  ```

  