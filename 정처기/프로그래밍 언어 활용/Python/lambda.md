# Python Lambda 함수

## 1. Lambda 함수란?

람다(Lambda) 함수는 이름이 없는 익명 함수(Anonymous Function)입니다. `def` 키워드를 사용하여 함수를 정의하는 것과 달리, `lambda` 키워드를 사용하여 간단한 한 줄짜리 함수를 만들 수 있습니다.

- 이름이 없으므로 한 번 사용되고 버려지는 간단한 기능에 주로 사용됩니다.
- 복잡한 함수보다는 간단한 기능을 수행하는 데 적합합니다.
- 다른 함수의 인자로 함수를 전달할 때 유용하게 사용됩니다. (예: `map`, `filter`, `sorted` 등)

## 2. 구문

람다 함수의 기본 구문은 다음과 같습니다.

```python
lambda 인자1, 인자2, ... : 표현식
```

- **`lambda`**: 람다 함수를 선언하는 키워드입니다.
- **`인자`**: 함수에 전달되는 매개변수입니다. 쉼표(`,`)로 구분하여 여러 개를 지정할 수 있습니다.
- **`표현식`**: 인자를 사용하여 계산되고, 그 결과가 반환되는 부분입니다. 별도의 `return` 문이 없으며, 표현식의 결과 자체가 반환값입니다.

## 3. 사용법 및 예시

### 3.1. 기본 사용법

```python
# 두 수를 더하는 람다 함수
add = lambda x, y: x + y
print(add(5, 3))  # 출력: 8

# 인수가 없는 람다 함수
say_hello = lambda: "Hello, World!"
print(say_hello()) # 출력: Hello, World!
```

### 3.2. 고차 함수(Higher-Order Function)와 함께 사용

람다 함수의 진정한 강력함은 `map`, `filter`, `sorted`와 같은 고차 함수와 함께 사용될 때 나타납니다.

#### `map()` 함수와 함께 사용

`map()` 함수는 시퀀스(리스트, 튜플 등)의 각 요소에 지정된 함수를 적용하여 새로운 `map` 객체를 반환합니다.

```python
numbers = [1, 2, 3, 4, 5]

# 각 요소를 제곱하는 람다 함수 적용
squared_numbers = list(map(lambda x: x ** 2, numbers))
print(squared_numbers)  # 출력: [1, 4, 9, 16, 25]
```

#### `filter()` 함수와 함께 사용

`filter()` 함수는 시퀀스의 각 요소에 함수를 적용하여 결과가 `True`인 요소들만 걸러내어 새로운 `filter` 객체를 반환합니다.

```python
numbers = [1, 2, 3, 4, 5, 6]

# 짝수만 필터링하는 람다 함수 적용
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)  # 출력: [2, 4, 6]
```

#### `sorted()` 함수와 함께 사용

`sorted()` 함수는 시퀀스를 정렬할 때 `key` 인자에 함수를 지정하여 정렬 기준을 설정할 수 있습니다.

```python
# 튜플의 두 번째 요소를 기준으로 정렬
pairs = [(1, 'one'), (4, 'four'), (2, 'two'), (3, 'three')]

sorted_pairs = sorted(pairs, key=lambda pair: pair[1])
print(sorted_pairs)  # 출력: [(4, 'four'), (1, 'one'), (3, 'three'), (2, 'two')]

# 복잡한 객체 리스트 정렬
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def __repr__(self):
        return f"Person({self.name}, {self.age})"

people = [
    Person("Alice", 30),
    Person("Bob", 25),
    Person("Charlie", 35)
]

# 나이를 기준으로 정렬
sorted_people = sorted(people, key=lambda person: person.age)
print(sorted_people) # 출력: [Person(Bob, 25), Person(Alice, 30), Person(Charlie, 35)]
```

### 3.3. 함수를 반환하는 함수 (클로저)

함수 내에서 람다를 정의하고 반환하여 클로저(closure)를 만들 수 있습니다.

```python
def make_incrementor(n):
    return lambda x: x + n

increment_by_2 = make_incrementor(2)
increment_by_10 = make_incrementor(10)

print(increment_by_2(5))  # 출력: 7
print(increment_by_10(5)) # 출력: 15
```

## 4. 언제 람다를 사용해야 하는가?

- **간단한 일회성 함수가 필요할 때**: `def`를 사용하여 정식으로 함수를 정의하기에는 너무 간단하고, 한 번만 사용할 함수에 적합합니다.
- **코드의 간결성**: `map`, `filter`, `sorted` 등의 인자로 함수를 전달할 때 코드를 더 간결하게 만들 수 있습니다.
- **가독성**: 람다 함수가 너무 복잡해지면 오히려 가독성을 해칠 수 있습니다. 복잡한 로직은 `def`를 사용하여 명시적으로 함수를 정의하는 것이 좋습니다. 일반적으로 람다 함수는 한 줄로 표현할 수 있는 간단한 로직에 사용하는 것이 바람직합니다.
