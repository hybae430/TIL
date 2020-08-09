# 데이터 구조 (Data Structure) 2

- 순서가 없는(unordered) 데이터 구조
  - 세트(Set)
  - 딕셔너리(Dictionary)



## 세트 (Set)

> Mutable, unordered, iterable

### 추가 및 삭제

- `.add(ele)`: `elem`을 세트에 추가합니다.

- `.update(*others)`: 여러가지 값(iterable)을 추가합니다.

  ```python
  a = {'starbucks'}
  a.update({'hollys', 'tomntoms'}, ['tomntoms', 'gongcha'])
  # {'starbucks', 'hollys', 'tomntoms', 'gongcha'} 중복제거, 순서는 랜덤
  ```

- `.remove(elem)`: `elem`을 삭제하고, 없으면 `KeyError`가 발생합니다.
- `.discard(elem)`: `elem`을 삭제하고, 없어도 에러가 발생하지 않습니다.
- `.pop()`: **임의의 원소**를 제거하고 그 값을 반환합니다.



## 딕셔너리 (Dictionary)

> Mutable, unordered, iterable
>
> `Key : Value` 페어의 자료구조

### 조회

- `.get(key[, default])`: `key`를 통해 `value`를 가져오며 절대 `KeyError`가 발생하지 않습니다. `key`가 없을 경우 그 키에 `default`값을 넣어 새로운 페어를 생성합니다.

  - `default`는 기본적으로 `None`입니다.

  ```python
  my_dict = {'starbucks' : '카페', 'emart' : '마트', 'LGTWINS' : '프로야구구단'}
  print(my_dict['homeplus'])				# KeyError 발생
  print(my_dict.get('homeplus'))			# None 반환 (기본값이 None)
  print(my_dict.get('homeplus', '마트'))	# 마트 반환
  ```

### 추가 및 삭제

- `.pop(key[, default])`: `key`가 딕셔너리에 있으면 제거 후 그 값을 반환합니다. 없을 경우 `default`값을 반환합니다.
  - 이 때, `default`값도 없을 경우 `KeyError`가 발생합니다.

- `.update()`: 값을 제공하는 `key`, `value`로 덮어씁니다.

```python
my_dict = {'starbucks' : '카페', 'emart' : '마트'}
my_dict.update(starbucks = '도서관')
```

### 딕셔너리 순회 (반복문 활용)

- dictionary에서 `for`를 활용하는 4가지 방법

  1. `key` 활용
  2. `.keys()` 활용
  3. `.values()` 활용
  4. `.items()` 활용

  ```python
  for key in dict:
      print(dict[key])
  
  for key in dict.keys():
      print(dict[key])
  
  for val in dict.values():
      print(val)
  
  for key, val in dict.items():
      print(key, val)
  ```

### Dictionary comprehension

```python
cubic = {x : x ** 3 for x in range(1, 5)}
print(cubic)		# {1 : 1, 2 : 8, 3 : 27, 4 : 64}

dusts = {'서울': 72, '대전': 82, '구미': 29, '광주': 45}
result = {x : '나쁨' if y > 80 else '보통' for x, y in dusts.items()}
print(result)		# {'서울': '보통', '대전': '나쁨', '구미': '보통', '광주': '보통'}
```

