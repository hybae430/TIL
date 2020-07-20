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

```python
print('\
안녕\
나는\
python이야\
')
```

- 단, `[]` `{}` `()`는 `\` 없이도 가능하다.

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

```python
# 같은 값 동시에 할당
x = y = 'ssafy'

# 다른 값 동시에 할당
a, b = 2020, 4
```

