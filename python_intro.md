# Python 기초

## 기초 문법 (Syntax)

### 주석 (Comment)

- 한 줄 주석은 `#`(pound, hash, sharp)로, 여러 줄 주석은 공식적으로는 없다.
- 여러 줄 주석을 표현하고 싶을 때에는 `#`으로 한 줄씩 작성하거나, `'''` 또는 `"""`(multiline string)을 사용할 수 있다.(multiline string은 원래 함수/클래스를 설명하기 위한 기능)

```python
# 주석은 이렇게 입력합니다
'''
여러줄 주석은
이렇게 할 수 있습니다.
'''
```

### 코드 라인

- 파이썬 코드는 '1 Line 1 Statement(1줄에 1문장)'가 원칙이다.
- Statement은 파이썬이 실행 가능(executable)한 최소한의 코드 단위이다.

```python
print('hello')
print('world')
```

- 이 때 print문 두 개를 한 줄에 출력하고자 하는 경우 `;`(semi-colon)을 통해 표현할 수 있지만, 파이썬에서 이를 권장하지 않는다.

```python
# 여기서 ';'가 빠지면 SyntaxError가 발생한다.
print('hello'); print('world')
```

- 또한 여러 줄의 string을 한 번에 출력하기 위해 `\`를 사용할 수 있지만, 이것도 자주 쓰이진 않는다.
  - 단, `[]` `{}` `()`는 `\` 없이도 가능하다.

```python
print('\
안녕\
나는\
python이야\
')
```

## 변수 (Variable)

### 할당 연산자

- 변수는 `=`을 통해 할당(assignment) 된다.
- 변수의 데이터 타입은 `type()`, 메모리 주소는 `id()`로 확인할 수 있다.

```python
x = 'ssafy'
type(x)		# 'str'
id(x)		# 숫자 메모리주소
```

- 같은 값을 동시에 할당하거나 다른 값을 동시에 할당할 수 있다.
  - 변수의 개수가 할당하는 값보다 많거나 적을 때 오류가 발생한다.

```python
# 같은 값 동시에 할당
x = y = 'ssafy'

# 다른 값 동시에 할당
a, b = 2020, 4
```

- 이를 활용하면 중간 변수 없이 값을 `swap`할 수 있다.

```python
a, b = 10, 20
a, b = b, a		# (a, b) = (b, a) tuple 개념을 이용함!
```

### 식별자 (Identifiers)

>  파이썬에서 식별자는 변수, 함수, 모듈, 클래스 등을 식별하는데 사용되는 이름(name)이다.

- 식별자는 알파벳, `_`, 숫자로 구성된다.
- 첫 글자에 숫자가 올 수 없으며, 대소문자를 구별하고, 예약어와 내장함수(built-in-function)를 사용할 수 없다.
  - 내장함수로 식별자를 설정한 경우 구동은 되지만, 후에 기본 기능과 충돌하여 프로그램에 혼란을 줄 수 있다.

```python
# 예약어인 만큼 파이썬 환경에서 쓰면 단어의 색이 다른 것이 보인다.
False, None, True, and, as, assert, break, class, continue, def, del, elif ...
```

```python
# 이 예약어가 궁금할 경우
import keyword
print(keyword.kwlist)

print = 'ssafy'		# 오류 안남
print(print)		# 오류 발생 (print가 내장함수인지 문자열인지 프로그램에서 혼동)
del print
print('hello')		# 정상 동작
```

## 데이터 타입 (Datat Type)

### 숫자 (Number) 타입

#### (1) `int` (정수, integer)

> 모든 정수는 `int`로 표현된다. (파이썬 3.x 버전에서는 `long`타입 없음)

- 파이썬에서 표현할 수 있는 가장 큰 수
  - 파이썬은 정수 자료형(integer)에서 오버플로우가 없다. (`arbitrary-precision arithmetic` 사용)
  - 가장 큰 숫자를 활용하기 위해 `sys`모듈을 사용한다.

- arbitrary-precision arithmetic
  - 사용할 수 있는 메모리양이 정해져 있는 기존의 방식과 달리, 현재 남아있는 만큼의 가용 메모리를 모두 수 표현에 끌어다 쓸 수 있는 형태

- n진수 만들기

```python
# 2진수
binary_num = 0b10	# 2 출력

# 8진수
octal_num = 0o10	# 8 출력

# 16진수
hexa_num = 0x10		# 16 출력
```

#### (2) `float` (부동소수점, 실수, floating point number)

> 실수는 `float`로 표현되는데, 컴퓨터가 이를 표현하는 과정에서 `부동소수점`을 사용하며 항상 같은 값으로 일치하지 않는다. (floating point rounding error)

- e, E를 사용하여 컴퓨터식 지수 표현을 할 수 있다.
- 실수의 연산
  - 실수의 덧셈은 쉽게 가능하지만, 뺄셈에 있어 주의가 필요하다. **★매우 중요!★**
    - 따라서 뺄셈에 있어 반올림 함수인 `round()`, `math` 모듈, `sys` 모듈을 활용할 수 있다.

```python
# 실수의 덧셈
3.5 + 3.2		# 6.7 출력

# 실수의 뺄셈
3.5 - 3.2		# 0.29999999 출력
```

```python
a = 3.5 - 3.2
b = 0.3
round(a, 1)		# 0.3 출력
```

```python
# sys 모듈 | math 모듈 사용
import sys
import math

abs(a - b) <= sys.float_info.epsilon
math.isclose(a, b)						# True일 경우 같다고 인지
```

#### (3) `complex` (복소수, complex number)

> 실수로 표현되는 실수부와 허수부로 구성되어 있으며, 허수부는 `j`로 표현한다.

- 문자열을 복소수로 변환할 수 있는데, 이 때 연산자 주위에 공백이 있으면 안 된다.

```python
a = 3 + 4j
b = complex('3+4j')		# 변환 가능
c = complex('3 + 4j')	# 오류 발생
```

### 문자 (String) 타입

#### 기본 활용법

- 문자열은 Single quotes(`'`)나 Double quotes(`"`)를 활용하여 표현 가능하다.
- 문자열을 묶을 때 동일한 문장부호를 활용해야 하며, `PEP-8`에서는 하나의 문장부호를 선택하여 유지하도록 하고 있다.
- 사용자에게 받은 입력은 기본적으로 `str` 타입니다. (연산 등에 typecasting 필요)

#### 따옴표 사용

- 문자열 안에 문장부호(`'`,`"`)가 사용될 경우 이스케이프 문자(`\`)나 다른 문장부호를 사용할 수 있다.

```python
"내 이름은 \"배하영\"이다."
"내 이름은 '배하영'이다."
```

- 여러 줄에 걸쳐 있는 문장은 다음과 같이 표현 가능하다. (`PEP-8` 메뉴얼)

```python
print("""
이것은
여러 줄에 걸친
문자열입니다.
""")
```

- 문자열은 `+` 연산자로 이어 붙이거나, `*` 연산자로 반복시킬 수 있다.
  - 변수화해서도 사용가능하다.
  - 연산자 없이도 두 개 이상의 문자열이 연속해서 나타나면 프로그램에서 자동으로 이어붙인다.

```python
'hello' + 'violet'		# 'helloviolet'
'hello' * 2				# 'hellohello'
a = 'hello'				
a + 'violet'			# 'helloviolet'
a 'violet'				# 오류 발생
```

#### 이스케이프 시퀀스

> `\`를 활용하여 문자열을 조작한다.

| 예약문자 |    내용(의미)     |
| :------: | :---------------: |
|    \n    |      줄 바꿈      |
|    \t    |        탭         |
|    \r    |    캐리지리턴     |
|    \0    |     널(Null)      |
|    \\    |        `\`        |
|    \'    | 단일인용부호(`'`) |
|    \"    | 이중인용부호(`"`) |

- `print()`의 default 인자인 end='\n'을 조작해서도 비슷한 결과를 낼 수 있다.

```python
print('hello\tviolet')
print('hello', end='\t')
print('violet')				# 'hello	violet'
```

#### String interpolation

- %-formatting
- `str.format()`
- `f-strings`: 파이썬 3.6 이후 버전에서 지원
  - 여러 줄 문자열에서도 사용 가능하며, 연산 및 출력형식 지정이 가능하다.

```python
name = 'violet'
print('내 이름은 %s 입니다.' % name)
print('내 이름은 {} 입니다.'.format(name))
print(f'내 이름은 {name} 입니다.')		# 내 이름은 violet 입니다.
```

```python
import datetime
now = datetime.datetime.now()

# '오늘은 2020년 이번달은 07월 오늘은 20일'
f'오늘은 {now:Y}년 이번달은 {now:%m}월 오늘은 {now:d}일'

# 연산 및 출력형식 지정
pi = 3.141592
r = 10
print(f'{pi:.3} 넓이는: {pi * r * r:.3}')		# .3은 3번째 자리에서 반올림이라는 뜻
```

### 참/거짓 (Boolean) 타입

> 비교/논리 연산 수행 등에서 사용되는 `bool` 타입 변수: `True`, `False`

- 다음은 `False`로 변환된다.

```python
0, 0.0, (), [], {}, '', None
```

#### `None` 타입

- `None`의 type은 `NoneType`이며 변수에 넣었을 때 출력되는 `bool`값은 `False`이다.

### 형변환 (Type conversion, Typecasting)

> 파이썬에서 데이터타입은 암시적 또는 명시적으로 변환할 수 있다.

#### 암시적 형변환 (Implicit Type Conversion)

> `bool`, Numbers(`int`,`float`,`complex`)끼리 가능하다.

#### 명시적 형변환 (Explicit Type Conversion)

- string -> integer: 형식에 맞는 숫자만 가능
- integer -> string: 모두 가능

```python
number = input('숫자를 입력해주세요: ')		## str type
number * 2									## 오류 발생 int(number) 캐스팅 필요
int('3.5')									## 오류 발생 int(float('3.5')) 더블캐스팅 필요
```

## 연산자 (Operator)

- 산술 연산자
- 비교 연산자
- 논리 연산자
- 복합 연산자
- 기타 연산자

### 산술 연산자

> Python에서는 기본적인 사칙연산이 가능하다.

- `**`는 제곱(^)을 나타낸다.

- divmod는 몫과 나머지를 동시에 반환하는 함수이다.

```python
a, b = divmod(5, 2)		## (2, 1)
```

### 비교 연산자

> 우리가 수학에서 배운 연산자와 동일하게 값을 비교할 수 있다.

- `is`와 `is not`은 값이 아닌 객체 비교 연산자이다.
  - 따라서 `None`,`True`,`False` 등을 비교할 때 효과적이다.

```python
a = 3.0
b = 3
a == b			# True
a is b			# False
```

### 논리 연산자

> `&` `|` 는 파이썬에서 비트 연산자를 의미한다.

- `and`, `or`, `not`을 사용한다.
  - 파이썬에서 and는 a가 거짓이면 a를 리턴하고, 참이면 b를 리턴한다.
  - 파이썬에서 or은 a가 참이면 a를 리턴하고, 거짓이면 b를 리턴한다.

#### 단축평가

> 첫 번째 값이 확실할 때,  두 번째 값은 확인하지 않기 때문에 속도를 향상시킬 수 있는 기술이다.

```python
vowels = 'aeiou'
('a' and 'b') in vowels		# False
('a' or 'b') in vowels		# True
```

### 복합 연산자

> 연산과 대입이 함께 이뤄지는 연산자로 반복문에서 자주 활용된다.

### 기타 주요 연산자

#### Concentration

- 숫자가 아닌 자료형은 `+`연산자를 통해 합칠 수 있다.

#### Containment Test

- `in`연산자를 통해 요소가 속해있는지 여부를 확인한다.

#### Identity

- `is`연산자를 통해 동일한 객체인지 확인한다.

#### Indexing/Slicing

- `[]`를 통해 값을 접근하고(Indexing), `[:]`을 통해 리스트를 자를 수 있다(Slicing).

```python
a = [1, 2, 3, 4, 5]
# Indexing
a[3]			# 4
# Slicing
a[1:3]			# [2, 3]
```

### 연산자 우선순위

0. `()`을 통한 grouping
1. Slicing
2. Indexing
3. `**`
4. `+`,`-` (음수/양수 부호)
5. `*`, `/`, `%`
6. `+`,`-`
7. `in`,`is`
8. `not`
9. `and`
10. `or`

## 표현식 (Expression) & 문장 (Statement)

### 표현식

> 표현식 => `evaluate` => 값

- 하나의 값(value)로 환원(reduce)될 수 있는 문장을 말한다.
- `식별자`,`값`,`연산자`로 구성된다.
  - **할당문은 표현식이 아니다.**

### 문장

> 파이썬이 실행 가능한 최소한의 코드 단위 (a syntatic unit of programming)