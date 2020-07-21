# Control Flow

## 제어문 (Control Statement)

- 조건문
- 반복문

> 제어문을 사용하여 순서도(Flow Chart)를 코드로 표현할 수 있다.

### 조건문 (Conditional Statement)

####  `if`조건문

> `if`문은 반드시 **참/거짓**을 판단할 수 있는 조건과 함께 사용되어야 한다.

- `if` 조건이 참일 경우 `:` 이후의 문장을 수행한다.
- `else`, `elif`는 선택적으로 사용 가능하다.

##### 주의사항

- 반드시 **들여쓰기**에 유의해야 한다.
  - 파이썬에서는 코드 블록을 `{}`가 아닌 들여쓰기로 판단한다.
  - 보편적으로 PEP-8에서 권장하는 **4spaces**를 사용한다.

#### `elif`복수 조건

> 2개 이상의 조건을 활용할 경우 `elif <조건>:`을 활용합니다

#### 중첩 조건문 (Nested Conditional Statement)

> 조건문은 다른 조건문에 중첩될 수도 있다.

#### 조건 표현식 (Conditional Expression)

> 일반적으로 조건에 따라 값을 정할 때 활용하며, **삼항 연산자(Ternary Operator)**라고 부른다.

##### 활용법

```python
num = int(input('숫자를 입력하세요: '))
value = num if num >= 0 else -num
print(value)				# 절대값 출력
```

### 반복문 (Loop Statement)

- while
- for

#### `while`반복문

> `while`문은 조건식이 참(`True`)인 경우 반복적으로 코드를 실행한다.

##### 주의사항

- `while`문 역시 들여쓰기에 주의하여야 하며, **반드시 종료조건을 설정해야 한다.**

#### `for`문

> `for`문은 시퀀스(String, Tuple, List, Range)나 다른 순회가능한 객체(iterable)의 요소들을 순회한다.

- `for`문에서 요소 값에 다른 값을 할당해도 다음 반복구문에 영향을 주지 않는다.

```python
for i in range(5):
    print(i)
    i = 5					# dead code
```

##### 리스트(list) 순회에서 index의 활용하기

- `range()`: 순회할 list의 길이를 활용하여 index를 조작할 수 있다.

##### **`enumerate()`**: 인덱스(index)와 값(value)을 함께 활용 가능

```python
lunch = ['짜장면', '초밥', '피자', '햄버거']

for idx, menu in enumerate(lunch):	# 추가 변수 사용
    print(idx, menu)

lunch_list = list(enumerate(lunch))
print(lunch_list)			#[(0, '짜장면'), (1, '초밥'), (2, '피자'), (3, '햄버거')]
```

- `enumerate(lunch, start = 1)`으로 1부터 카운트 할 수도 있다.

### 반복제어 (`break`, `continue`, `for-else`)

#### `break`

> `for`이나 `while`문에서 빠져나간다.

#### `continue`

> 이후의 코드를 수행하지 않고 **다음 요소부터** 계속하여 반복을 수행한다.

#### `for-else`

> 끝까지 반복문을 시행한 이후에 실행된다.

- 반복에서 리스트의 소진이나 (`for`의 경우) 조건이 거짓이 돼서 (`while`의 경우) 종료할 때 실행된다.
- `break`를 통해 중간에 종료되지 않은 경우만 실행한다.

#### `pass`

> 아무것도 하지 않지만, 문법적으로 문장이 필요할 때 사용한다. **(continue와 구분!)**