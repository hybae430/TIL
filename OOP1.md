# OOP1



## 객체 (Object)

> Python에서 모든 것은 객체입니다.
>
> 모든 객체는 타입(type), 속성(attribute), 조작법(method)를 가집니다.

### 객체 (Object)의 특징

- **타입(type)**: 어떤 operator와 method가 가능한가?
- **속성(attribute)**: 어떤 데이터를 가지는가?
- **조작법(method)**: 어떤 함수를 할 수 있는가?



## 타입 (Type)과 인스턴스 (Instance)

### 타입 (Type)

> 공통된 속성과 조작법을 가진 객체들의 분류

### 인스턴스 (Instance)

> 파이썬에서 모든 것은 객체이며, 이 객체는 모두 특정 타입의 인스턴스입니다.

```python
a = int(10)			# a, b는 객체
b = int(20)			# a, b는 int타입의 인스턴스
```



## 속성 (Attribute)과 메서드 (Method)

### 속성 (Attribute)

> 속성은 객체의 상태 / 데이터를 뜻합니다.

```python
# 복소수의 속성
x = -200 + 20j
x.real			# -200.0
x.imag			# 20.0
```

### 메서드 (Method)

> 특정 객체에 적용할 수 있는 행위 / 함수를 뜻합니다.

```python
dir(list)		# list타입 객체가 가지는 모든 메서드를 보여줍니다.
```



## 객체 지향 프로그래밍 (Object-Oriented Program)

> Object가 중심(oriented)이 되는 프로그래밍을 말합니다.
>
> 객체 지향 프로그래밍은 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러 가개의 독립된 단위, 즉 "객체"들의 모임으로 파악하고자 하는 것입니다. <wikipedia>

### 절차 중심 vs. Object 중심

- 프로그래밍 패러다임의 차이: 어떻게 프로그램을 organize할 것인가?

### Object 중심의 장점

- 코드의 **직관성**
- 활용의 **용이성**
- 변경의 **유연성**



## 클래스 (Class)와 객체 (Object)

> `class`: 객체들의 분류를 정의할 때 쓰이는 키워드

### 클래스 (Class) 생성

- 클래스의 이름은 `PascalCase`로 정의합니다.
  - `PascalCase`: 연달아 오는 단어의 모든 앞글자와 맨 앞 문자를 대문자로 쓰는 표기법
- 클래스 내부에는 데이터와 함수를 정의할 수 있고, 이 함수를 **메서드(method)**라고 부릅니다.

### 인스턴스 (Instance) 생성

- 인스턴스는 클래스를 호출함으로 생성됩니다.
- `type()` 함수를 통해 생성된 객체의 클래스를 확인할 수 있습니다.

```python
class Person:
    """
    이것은 Person 클래스입니다.
    """
    
p1 = Person()				# 객체 생성
print(type(p1))				# <class '__main__.Person'>
print(person.__doc__)		# 이것은 Person 클래스입니다.
```

### 메서드 (Method) 정의

- 특정 데이터 타입 / 클래스의 객체에 공통적으로 적용 가능한 함수들(행위)을 의미합니다.

### 생성자 (Constructor)  / 소멸자 (Destructor) 메서드

> 인스턴스 객체가 생성 / 소멸될 때 호출되는 함수를 의미합니다.

```python
class number:
	def __init__(self):
        print('생성')
    def __del__(self):
        print('소멸')
```

### 속성 (Attribute) 정의

```python
class Person:
    def __init__(self, name):
        self.name = name		# 생성과 동시에 속성에 값 할당 (변경 가능)
```

### 매직메서드

- 더블언더스코어(`__`)가 있는 메서드는 특별하기 때문에 `스페셜 메서드` / `매직 메서드`로 불립니다.

```python
3.14.__add__(2.5)			# 5.6400000000000001
...
```

- `__str__(self)`: 특정 객체를 출력(`print()`)할 때 보여줄 내용을 정의할 수 있습니다.

  ```python
  class Person:
      def __str__(self):
          return '이 클래스는 Person입니다.'
      
  p1 = Person()
  print(p1)		# 이 클래스는 Person입니다.
  ```

- `self`: 인스턴스 자신을 나타내는 키워드
  - 파이썬에서 메서드는 호출시 **첫 번째 인자로 자기 자신이 전달되게** 설계되었습니다.
  - 보통 `self`를 매개변수명으로 많이 사용하지만 변경가능합니다.