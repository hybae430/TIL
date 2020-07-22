# Function 2

## 함수와 스코프 (scope)

> 함수는 코드 내부에 `지역 스코프(local scope)`를 생성한다.

- **전역 스코프 (`global scope`) / 전역 변수 (`local variable`)**: 코드 어디에서든 참조할 수 있는 공간/변수
- **지역 스코프 (`local scope`) / 지역 변수 (`local variable`)**: 함수 내부에서만 참조할 수 있는 공간/변수
- 전역 변수는 어디서든 참조 가능하지만, 전역에서 지역 변수를 호출할 수는 없다.
  - 전역 변수를 지역 스코프에서 바꾸고자 할 경우 `global`선언을 활용할 수 있다.

```python
global_num = 3
def local_scope():
    global global_num				# 전역 변수 가져오기
    global_num = 5					# 변경
    return f'global_num이 {global_num}으로 설정되었습니다.'

print(local_scope())				# global_num이 5으로 설정되었습니다.
print('global_num:', global_num)	# global_num: 5
```

### 이름 검색 (resolution) 규칙

> 파이썬에서 사용되는 식별자들은 namespace에 저장되어 있다. 이름들은 `LEGB Rule`에 따라 검색한다.

- `L`ocal scope: 정의된 함수
- `E`nclosed scope: 상위 함수
- `G`lobal scope: 함수 밖의 변수 혹은 import된 모듈
- `B`uilt-in scope: 파이썬안에 내장되어 있는 함수 또는 속성

### 변수의 수명주기 (lifecycle)

- **빌트인 스코프`(built-in scope)`**: 파이썬이 실행된 이후부터 영원히 유지
- **전역 스코프`(global scope)`**: 모듈이 호출된 시점/이름 선언된 이후부터 인터프리터가 끝날때까지 유지
- **지역(함수) 스코프`(local scope)`**: 함수가 호출될 때 생성되고, 함수가 종료/처리되지 않는 예외를 일으킬 때 삭제

## 재귀 함수 (recursive function)

> 재귀 함수는 함수 내부에서 자기 자신을 호출하는 함수를 뜻한다.

### 팩토리얼 계산

1. 반복문을 이용한 팩토리얼 계산

```python
def fact(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result
print(fact(5))					# 120
```

2. 재귀를 이용한 팩토리얼 계산

```python
def factorial(n):
    if n == 1:
        return 1
    return n * factorial(n - 1)
print(factorial(5))				# 120
```

### 피보나치 수열

1. 반복문을 이용한 피보나치 수열 계산

```python
def fib_loop(n):
    fibo = [0, 1, 1]
    for i in range(3, n + 1):
        fibo.append(fibo[i - 1] + fibo[i - 2])
    return fibo[n]
print(fib_loop(10))				# 55
```

2. 재귀를 이용한 피보나치 수열 계산

```python
def fib(n):
    if n == 1 or n == 2:
        return 1
    return fib(n - 1) + fib(n - 2)
print(fib(10))					# 55
```

### 최대 재귀 깊이

> 끝없이 재귀 함수를 호출할 경우 RecursionError가 발생한다. 파이썬에서는 최대 재귀 깊이(maximum recursion depth)가 1,000으로 정해져 있기 때문이다.

### 반복문과 재귀 함수의 차이

> 두 코드 모두 원리는 같다!

- 재귀 호출은 `변수 사용`을 줄일 수 있다.
- 재귀함수는 기본적으로 같은 문제를 점점 적은 범위로 줄여서 푸는 방식이다.
- 재귀함수를 작성할 때는 반드시 `base case`를 지정해 주어야 한다. (더 이상 반복되지 않는 지점)
- 코드가 더 직관적이고 이해하기 쉬운 경우가 있다.
  - **그러나 대부분의 재귀함수 풀이는 반복문보다 느리다.**