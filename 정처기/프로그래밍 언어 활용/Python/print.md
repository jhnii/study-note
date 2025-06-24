# Python `print` 함수

파이썬의 `print` 함수는 터미널이나 콘솔에 데이터를 출력하는 데 사용되는 내장 함수입니다. 단순한 텍스트부터 변수, 복잡한 데이터 구조까지 다양한 유형의 값을 출력할 수 있습니다. `print` 함수는 출력을 더 유연하게 제어할 수 있는 여러 파라미터와 문자열 포매팅 방법을 제공합니다.

## `end` 파라미터

`print` 함수는 기본적으로 출력 내용 끝에 줄바꿈 문자(`\n`)를 추가합니다. 이는 `print` 함수가 호출될 때마다 새로운 줄에 출력이 시작되도록 합니다. `end` 파라미터를 사용하면 이 기본 동작을 변경할 수 있습니다. `end`에 특정 문자열을 지정하면, `print` 함수는 줄바꿈 대신 해당 문자열을 출력 끝에 추가합니다.

**예시:**

```python
# 기본적으로 줄바꿈이 일어남
print("Hello")
print("World")
# 출력:
# Hello
# World

# end 파라미터를 사용하여 공백으로 연결
print("Hello", end=" ")
print("World")
# 출력:
# Hello World

# end 파라미터를 사용하여 쉼표와 공백으로 연결
print("apple", end=", ")
print("banana", end=", ")
print("cherry")
# 출력:
# apple, banana, cherry
```
`end`에 빈 문자열(`""`)을 지정하면, 여러 `print` 함수의 출력을 줄바꿈 없이 바로 이어서 출력할 수 있습니다.

---

## 문자열 포매팅

`print` 함수와 함께 사용되는 문자열 포매팅은 동적인 값을 문자열에 삽입하여 가독성 높고 유연한 출력을 만드는 방법입니다. 파이썬에서는 여러 가지 문자열 포매팅 방식을 지원합니다.

### `%` 연산자를 이용한 포매팅 (구식)

`%` 연산자는 C언어의 `printf` 함수와 유사한 형식으로 문자열을 포매팅합니다. 포맷 지정자(`%s`, `%d`, `%f` 등)를 사용하여 문자열 안에 값을 삽입할 위치를 표시합니다.

-   `%s`: 문자열 (모든 파이썬 객체를 문자열로 변환)
-   `%d`: 정수
-   `%f`: 부동소수점 수

**예시:**

```python
name = "Alice"
age = 30
pi = 3.14159

# %s, %d 사용
print("My name is %s and I am %d years old." % (name, age))
# 출력: My name is Alice and I am 30 years old.

# %f 사용 (소수점 자릿수 지정)
print("Pi is approximately %.2f." % pi)
# 출력: Pi is approximately 3.14.
```
이 방식은 오래된 코드를 유지보수할 때 여전히 볼 수 있지만, 최신 파이썬에서는 더 발전된 포매팅 방법을 사용하는 것이 권장됩니다.

### `str.format()` 메소드 활용

`str.format()` 메소드는 `%` 연산자보다 더 강력하고 유연한 포매팅 기능을 제공합니다. 중괄호(`{}`)를 플레이스홀더로 사용하며, 인덱스나 이름으로 값을 전달할 수 있습니다.

**예시:**

```python
name = "Bob"
age = 25

# 위치 기반 포매팅
print("My name is {} and I am {} years old.".format(name, age))
# 출력: My name is Bob and I am 25 years old.

# 인덱스 기반 포매팅
print("My name is {0} and I am {1} years old. {0} is a good name.".format(name, age))
# 출력: My name is Bob and I am 25 years old. Bob is a good name.

# 키워드 기반 포매팅
print("My name is {name} and I am {age} years old.".format(name="Charlie", age=35))
# 출력: My name is Charlie and I am 35 years old.
```

### f-string (포맷된 문자열 리터럴)

파이썬 3.6부터 도입된 f-string은 가장 현대적이고 직관적인 문자열 포매팅 방법입니다. 문자열 앞에 `f` 또는 `F`를 붙이고, 중괄호 안에 변수나 표현식을 직접 넣어 사용합니다. 코드가 간결하고 가독성이 높으며, 실행 속도도 가장 빠릅니다.

**예시:**

```python
name = "David"
age = 40

# 변수 삽입
print(f"My name is {name} and I am {age} years old.")
# 출력: My name is David and I am 40 years old.

# 표현식 삽입
print(f"In 5 years, I will be {age + 5} years old.")
# 출력: In 5 years, I will be 45 years old.

# 함수 호출 결과 삽입
print(f"My name in uppercase is {name.upper()}.")
# 출력: My name in uppercase is DAVID.

# 포맷 지정자 사용
pi = 3.14159265
print(f"Pi is approximately {pi:.2f}.")
# 출력: Pi is approximately 3.14.
```

f-string은 현재 파이썬에서 가장 권장되는 문자열 포매팅 방식입니다.
