# OOP3



## 상속

### 상속 (Inheritance)이란 ?

> 클래스에서 가장 큰 특징은 `상속` 기능이 있다는 것입니다. 부모 클래스의 모든 속성이 자식 클래스에 상속되므로 코드의 재사용성이 높아집니다.

```python
class Person:
    pass

class Student(Person):				# 상속은 클래스의 인자로 넣어줍니다.
    pass
```

### 상속의 이점

- 코드의 중복정의가 줄어듭니다.
- 공통된 속성이나 메서드를 부모 클래스에 정의하고 상속받아 적은 코드로 다양한 형태의 객체를 만들 수 있습니다.

```python
issubclass(Student, Person)			# 상속 여부 확인하는 함수 (내장 타입에도 적용)
```

- `.super()`: 자식 클래스에 메서드를 추가로 구현할 수 있습니다.

```python
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email 
        
    def greeting(self):
        print(f'안녕, {self.name}')
        
        
class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        super().__init__(name, age, number, email)		# 코드 중복 방지
        self.student_id = student_id
```



## 메서드 오버라이딩

> Method Overriding(메서드 재정의): 자식 클래스에서 부모 클래스의 메서드를 재정의하는 것

- 상속 받은 메서드를 재정의할 수 있으며, 이 때 **같은 이름의 메서드**로 덮어씁니다.



## 상속관계에서의 이름공간

- 기존 `인스턴스 -> 클래스` 순의 탐색에서 확장됩니다.
  - `인스턴스 -> 자식 클래스 -> 부모 클래스`



## 다중 상속

> 두 개 이상의 클래스를 상속받는 경우, 다중 상속이 됩니다.

- 이 때, 공통된 속성이 있다면 먼저 상속받는 클래스의 속성을 받습니다.

```python
class Mom(Person):
    gene = 'XX'
    def swim(self):
        pass

class Dad(Person):
    gene = 'XY'
    def walk(self):
        pass
    
class FirstChild(Mom, Dad):
    def cry(self):
        pass
    
class SecondChild(Dad, Mom):
    pass

baby = FirstChild('첫째')			# 이름 속성은 Person(최상위 클래스)에서 받았다고 가정
baby.gene						# Mom의 gene인 XX 반환
baby2 = SecondChild('둘째')
baby2.gene						# Dad의 gene인 XY 반환
```

