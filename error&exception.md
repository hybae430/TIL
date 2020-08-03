# error & exception

# 에러 (Error)

## 문법 에러 (Syntax Error)

> 문법 에러가 있는 프로그램은 실행되지 않습니다.

- 에러 발생 시 `SyntaxError`라는 키워드와 에러 상세 내용을 보여줍니다.
- `파일이름`과 `줄번호`, `^` 문자를 통해 파이썬이 코드를 읽어들일 때(`parser`) 문제가 발생한 위치를 표시합니다.
  - `parser`는 줄에서 에러가 감지된 가장 앞의 위치를 가리키는 '`^`'를 표시합니다.
  - 정확한 위치를 지정하지 않을 때도 있으므로 지정된 위치 전후를 모두 확인해야 합니다.

```python
# EOL (End of Line Error)
print('hi)

# EOF (End of File Error)
print('hi'
```



# 예외 (Exception)

> 문법적으로는 문제가 없지만, 실행시 발생하는 에러입니다.

- 모든 에러는 `Exception`을 상속받아 이뤄집니다.

```python
# ZeroDivisionError (0으로 나눌 경우)
1 / 0

# NameError (정의되지 않은 변수 호출)
print(me)

# TypeError (1: 맞지 않는 타입끼리 연산 등 동작 실행)
1 + '1'

# TypeError (2: 함수 잘못 호출 - 인자 개수 초과 / 미만 등)
round('3.5')	# 함수에 지원하지 않는 타입 넣기

# ValueError (1: 존재하지 않는 값 찾을 때)
numbers = [1, 2]
numbers.index(3)

# ValueError (2: 타입은 맞으나 값이 적절하지 않을 경우)
int('3.5')

# IndexError (존재하지 않는 idx 찾을 때)
mylist = []
mylist[-1]

# KeyError (존재하지 않는 key를 호출)
mydic = {'아침밥': '계란'}
mydic['점심밥']

# ModuleNotFoundError (모듈이 없는 경우)
import mymodule

# ImportError (모듈은 있지만 모듈 내 클래스 등을 가져올 때 오류)
from random import sam

# KeyboardInterrupt (무한루프 등에서 사용자가 직접 프로그램을 중지하는 경우)
while True:
    continue	# 무한루프 -> 사용자가 ctrl + c로 탈출하면 keboardinterrupt 발생
```



## 예외 처리 (Exception Handling)

### `try`&`except`

> `try`문을 사용하여 예외 처리를 할 수 있습니다.

```python
try:
    num = int(input('값을 입력하세요: '))
    print(num)
except:
    print('숫자를 입력해주세요.')
```

### 에러 메세지 (`as`)

> `as` 키워드를 활용하여 에러 메세지를 보여줄 수 있습니다.

```python
try:
    mylist = []
    print(mylist[-1])
except IndexError as error:		# 에러메세지를 error 변수에 저장
    print(error)
```

### 복수의 예외 처리

- 괄호가 있는 튜플로 여러 개의 예외를 지정할 수 있습니다.

```python
try:
    mylist = []
    print(mylist[-1])
except (IndexError, ValueError):
    print('에러가 발생했습니다.')
```

- 혹은 각각 다른 오류 메세지를 출력할 수 있습니다.
  - 이 때 가장 작은 범위의 에러부터 **순차적**으로 걸리기 때문에 순서에 유의해야 합니다.

```python
try:
    mylist = []
    print(mylist[-1])
except Exception:		# 가장 큰 범위
    print('에러 발생')
except IndexError:
    print('올바른 범위를 입력해주세요.')
except ValueError:
    print('적절한 값을 입력해주세요.')
```

### `else`

> 에러가 발생하지 않는 경우 실행시킬 문장에 사용되기 때문에 `except` 코드 뒤에 와야 합니다.

### `finally`

> 예외의 발생 여부와 관계없이 항상 실행되는 코드입니다.



## 예외 발생시키기 (Exception Raising)

### `raise`

> `raise`를 통해 예외를 강제로 발생시킬 수 있습니다.

```python
raise NameError('이름이 없습니다.')		# 오류 발생


```

### `assert`

> **상태를 검증하는데 사용**되며 무조건 `AssertionError`가 발생합니다.

```python
# assert 뒤의 boolean이 거짓일 경우 에러 메세지 출력
assert type(1) == int, '문자열을 입력하였습니다.'
```

