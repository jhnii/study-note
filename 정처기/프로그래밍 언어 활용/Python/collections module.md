# Python Collections

Python의 `collections` 모듈은 내장 컨테이너(dict, list, set, tuple)에 대한 대안을 제공하는 특수 컨테이너 데이터 유형을 구현합니다.

## `namedtuple`

이름 붙은 필드를 갖는 튜플 서브클래스를 만드는 팩토리 함수입니다. 위치 인덱스뿐만 아니라 이름으로도 필드에 접근할 수 있어 가독성이 높은 코드를 작성할 수 있습니다.

```python
from collections import namedtuple

# 'Point'라는 이름의 namedtuple을 정의합니다. 필드는 'x'와 'y'입니다.
Point = namedtuple('Point', ['x', 'y'])

# namedtuple 인스턴스를 생성합니다.
p = Point(11, y=22)

# 이름으로 필드에 접근합니다.
print(p.x + p.y)  # 출력: 33

# 인덱스로도 접근할 수 있습니다.
print(p[0] + p[1]) # 출력: 33
```

## `deque`

'double-ended queue'의 약자로, 양쪽 끝에서 항목을 효율적으로 추가하거나 제거할 수 있는 리스트와 유사한 컨테이너입니다. 스택과 큐를 구현하는 데 유용합니다.

```python
from collections import deque

# deque를 생성합니다.
d = deque('ghi')

# 오른쪽에 항목 추가
d.append('j')
# 왼쪽에 항목 추가
d.appendleft('f')

print(d)  # 출력: deque(['f', 'g', 'h', 'i', 'j'])

# 왼쪽에서 항목 제거
print(d.popleft()) # 출력: 'f'

# 오른쪽에서 항목 제거
print(d.pop()) # 출력: 'j'

print(d) # 출력: deque(['g', 'h', 'i'])
```

## `ChainMap`

여러 개의 딕셔너리나 다른 매핑들을 그룹화하여 하나의 업데이트 가능한 뷰로 만듭니다. 여러 컨텍스트를 처리할 때 유용합니다.

```python
from collections import ChainMap

d1 = {'a': 1, 'b': 2}
d2 = {'c': 3, 'd': 4}

# d1과 d2를 연결합니다.
chain = ChainMap(d1, d2)

print(chain['a'])  # 출력: 1
print(chain['c'])  # 출력: 3
```

## `Counter`

해시 가능한(hashable) 객체의 개수를 세는 데 사용되는 딕셔너리 서브클래스입니다.

```python
from collections import Counter

# 문자열에서 각 문자의 개수를 셉니다.
c = Counter('gallahad')
print(c)  # 출력: Counter({'a': 3, 'l': 2, 'g': 1, 'h': 1, 'd': 1})

# 리스트에서 각 항목의 개수를 셉니다.
word_counts = Counter(['red', 'blue', 'red', 'green', 'blue', 'blue'])
print(word_counts['blue']) # 출력: 3
```

## `OrderedDict`

항목이 추가된 순서를 기억하는 딕셔너리 서브클래스입니다. Python 3.7부터는 일반 `dict`도 삽입 순서를 유지하지만, `OrderedDict`는 순서와 관련된 추가적인 기능(예: `move_to_end()`)을 제공합니다.

```python
from collections import OrderedDict

# 순서가 있는 딕셔너리를 생성합니다.
d = OrderedDict()
d['first'] = 1
d['second'] = 2
d['third'] = 3

for key, value in d.items():
    print(key, value)
# 출력:
# first 1
# second 2
# third 3

d.move_to_end('first')
print(''.join(d.keys())) # 출력: secondthirdfirst
```

## `defaultdict`

딕셔너리에 존재하지 않는 키에 접근할 때, 지정된 기본값을 반환하는 딕셔너리 서브클래스입니다. `KeyError`를 방지할 수 있습니다.

```python
from collections import defaultdict

# int를 기본 팩토리로 사용하면, 존재하지 않는 키에 대해 0을 반환합니다.
d = defaultdict(int)
d['a'] += 1
print(d['a'])  # 출력: 1
print(d['b'])  # 출력: 0

# list를 기본 팩토리로 사용하면, 항목을 그룹화하는 데 유용합니다.
s = [('yellow', 1), ('blue', 2), ('yellow', 3), ('blue', 4)]
d = defaultdict(list)
for k, v in s:
    d[k].append(v)

print(sorted(d.items())) # 출력: [('blue', [2, 4]), ('yellow', [1, 3])]
```

## `UserDict`, `UserList`, `UserString`

각각 `dict`, `list`, `str` 내장 타입을 감싸는(wrap) 클래스입니다. 이 클래스들을 상속받아 기존 내장 타입의 동작을 수정하거나 새로운 기능을 추가하기 용이합니다. 내부 데이터는 `data` 속성에 저장됩니다.

### `UserDict` 예제
```python
from collections import UserDict

# 키를 항상 소문자로 저장하는 커스텀 딕셔너리
class LowerKeyDict(UserDict):
    def __setitem__(self, key, value):
        super().__setitem__(key.lower(), value)

d = LowerKeyDict()
d['KEY'] = 'value'
print(d)  # 출력: {'key': 'value'}
```

### `UserList` 예제
```python
from collections import UserList

# 추가할 때 항상 정수형으로 변환하는 커스텀 리스트
class IntList(UserList):
    def append(self, item):
        super().append(int(item))

l = IntList()
l.append('1')
l.append(2.0)
print(l) # 출력: [1, 2]
```

### `UserString` 예제
```python
from collections import UserString

# 문자열을 항상 대문자로 다루는 커스텀 문자열
class UpperString(UserString):
    def __init__(self, seq):
        super().__init__(str(seq).upper())

s = UpperString('hello')
print(s) # 출력: HELLO
```
