# Function 1

## 함수 (Function)

> 특정한 기능(function)을 하는 코드의 묶음

#### 함수를 쓰는 이유

- 가독성
- 재사용성
- 유지보수

#### 함수의 선언과 호출

- `def`로 시작하여 `:`로 끝나고, 코드블록을 추가한다.
- **`return`값이 없으면 `None`값을 반환한다.**

```python
# 실수하기 쉬운 것들
result = print('hi')	# hi 출력
type(result)			# NoneType 출력

sorted_list = [5, 2, 3, 4, 1].sort()
print(sorted_list)		# None 출력
```

- 내장함수(built-in-functions)

```python
dir(__builtins__)		# built in 함수 출력하는 명령어
```

#### 함수의 Output

##### 함수의 `return`

- 함수는 반환값이 있으며, 이는 어떠한 것이라도 상관없지만 **단 하나의 객체**만 반환된다.
- 함수가 `return`되거나 종료되면, 함수를 호출한 곳으로 돌아간다.

#### 함수의 입력 (Input)

- 매개변수 (parameter): 함수 정의 단계에서 입력을 받아 함수 내부에서 활용할 `변수`
- 인자 (argument): 함수 호출 단계에서 실제로 전달되는 `입력값`

##### 함수의 인자

> 함수는 입력값(input)으로 `인자(argument)`를 넘겨줄 수 있다.

- 위치 인자 (Positional Arguments): 함수는 기본적으로 인자를 위치로 판단한다.
- 기본 인자 값 (Default Argument Values): 함수가 호출될 때, 인자를 지정하지 않아도 기본 값을 설정할 수 있다.
  - **단, 기본 인자값을 가지는 인자 다음에 기본 값이 없는 인자를 사용할 수 없다.**

```python
def greeting(name = '익명'):
    return (f'{name}, 안녕?')
print(greeting())				# 익명, 안녕?
print(greeting('하영'))			# 하영, 안녕?
```

- 키워드 인자 (Keyword Arguments): 직접 변수의 이름으로 특정 인자를 전달한다.
  - **단, `키워드 인자`를 활용한 다음에 `위치 인자`를 활용할 수 없다.**
  - **전부 키워드 표시 하거나, 전부 안 하거나, 제일 끝에만 하거나!**

```python
def greeting(age, name = '익명'):
    return f'{age}세 {name}님 환영합니다.'
greeting(name = '홍길동', 20)		# SyntaxError 발생
```

#### 정해지지 않은 여러 개의 인자 처리

> `print()`함수도 내장함수 코드를 살펴보면 인자에 `*`가 붙어있다.

##### 가변 (임의) 인자 리스트 (Arbitrary Argument Lists)

> 가변 인자 리스트는 `tuple`형태로 처리가 되며, 매개변수에 `*`로 표현한다.(`*args`) eg) `print()`

##### 가변 (임의) 키워드 인자 (Arbitrary Keyword Arguments)

> 정해지지 않은 키워드 인자들은 `dict`형태로 처리가 되며, `**`로 표현한다.(`**kwargs`) eg)`dict()`

```python
def my_dict(**kwargs):
    return kwargs
my_dict(한국어 = '안녕')				# {'한국어': '안녕'}
# return 타입은 dict
type(my_dict(한국어 = '안녕'))		# dict
```

