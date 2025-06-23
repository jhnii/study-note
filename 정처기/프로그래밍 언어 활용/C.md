## 표준 함수

### 문자열 함수
| 함수                                  | 설명                                               |
| ----------------------------------- | ------------------------------------------------ |
| `char* strcat(dest, src);`          | src의 문자열을 dest 문자열 뒤에 붙임                         |
| `char* strncat(dest, src, maxlen);` | src의 문자열에서 maxlen의 개수만큼 dest 문자열 뒤에 붙임           |
| `char* strcpy(dest, src);`          | src의 문자열을 dest 문자열에 복사                           |
| `char* strncpy(dest, src, maxlen);` | src의 문자열에서 maxlen의 개수만큼 dest 문자열에 복사             |
| `int strcmp(s1, s2);`               | s1, s2를 사전순으로 비교하여, s1이 s2보다 작으면 음수, 같으면 0, 크면 양수 반환 |
| `int strncmp(s1, s2, maxlen);`      | maxlen 길이만큼 s1, s2를 사전순으로 비교하여, s1이 s2보다 작으면 음수, 같으면 0, 크면 양수 반환 |
| `unsigned int strlen(s);`           | s의 길이를 알려줌                                       |
| `char* strrev(str);`                | str 내에 문자열을 거꾸로 뒤집음                              |
| `char* strchr(str, c);`             | str 내에 c가 존재하는지 검색하여, 찾으면 해당 문자의 포인터를, 찾지 못하면 NULL을 반환 |

### 수학 함수
| 함수                    | 설명                      |
| ----------------------- | ------------------------- |
| `double sqrt(n);`       | n의 제곱근을 계산합니다.    |
| `double ceil(n);`       | n보다 크거나 같은 가장 작은 정수를 반환합니다. (올림) |
| `double floor(n);`      | n보다 작거나 같은 가장 큰 정수를 반환합니다. (내림) |

### 유틸리티 함수
| 함수                               | 설명                                     |
| ---------------------------------- | ---------------------------------------- |
| `int rand();`                      | 0부터 RAND_MAX(보통 32767)까지의 난수를 생성합니다. |
| `void srand(seed);`                | 난수 생성기의 시드를 초기화합니다.         |
| `long time(NULL);`                 | 현재 시간을 초 단위로 반환합니다. (주로 `srand`의 시드로 사용) |
| `int atoi(str);`                   | 문자열을 정수로 변환합니다.             |
| `double atof(str);`                | 문자열을 double형 실수로 변환합니다.    |
| `void itoa(value, str, radix);`    | 정수를 문자열로 변환합니다. (base에 따라 다양한 진법으로 변환 가능) |

### 문자 관리 함수
| 함수                                  | 설명                                                     |
| ----------------------------------- | -------------------------------------------------------- |
| `int isalpha(int c);`               | `c`가 *알파벳*인지 확인합니다. (isupper(c) \|\| islower(c))      |
| `int isupper(int c);`               | `c`가 *대문자*인지 확인합니다.                                    |
| `int islower(int c);`               | `c`가 *소문자*인지 확인합니다.                                    |
| `int isdigit(int c);`               | `c`가 *10진수 숫자*인지 확인합니다.                              |
| `int isxdigit(int c);`              | `c`가 *16진수 숫자*인지 확인합니다.                              |
| `int isalnum(int c);`               | `c`가 *알파벳 또는 숫자*인지 확인합니다. (isalpha(c) \|\| isdigit(c)) |
| `int tolower(int c);`               | `c`를 소문자로 변환합니다.                                      |
| `int toupper(int c);`               | `c`를 *대문자*로 변환합니다.                                      |
| `int iscntrl(int c);`               | `c`가 제어 문자인지 확인합니다.                                  |
| `int ispunct(int c);`               | `c`가 구두점 문자인지 확인합니다.                                |
| `int isprint(int c);`               | `c`가 출력 가능한 문자인지 확인합니다. (공백 포함)                 |
| `int isspace(int c);`               | `c`가 공백 문자인지 확인합니다. (`' ', '\f', '\n', '\r', '\t', '\v'`) |
| `int isgraph(int c);`               | `c`가 공백을 제외한 출력 가능한 문자인지 확인합니다.                |
 

---


## 포인터

포인터는 다른 변수의 메모리 주소를 저장하는 변수입니다. C언어의 강력한 기능 중 하나로, 메모리에 직접 접근하여 데이터를 조작할 수 있게 해줍니다.

### 포인터 선언 및 기본 사용법

포인터는 가리키고자 하는 변수의 자료형 뒤에 `*`를 붙여 선언합니다. 변수의 주소를 얻기 위해서는 `&`(주소 연산자)를 사용하고, 포인터가 가리키는 값에 접근하기 위해서는 `*`(역참조 연산자)를 사용합니다.

**예시:**
```c
#include <stdio.h>

int main() {
    int var = 20;   // 실제 변수
    int *ip;        // 정수형 포인터 선언

    ip = &var;      // var 변수의 주소를 포인터 ip에 저장

    printf("var 변수의 주소: %p\n", &var);
    printf("ip에 저장된 주소: %p\n", ip);
    printf("ip가 가리키는 값: %d\n", *ip);

    return 0;
}
```

### 포인터와 배열

배열의 이름은 그 자체로 배열의 첫 번째 요소의 주소를 가리키는 포인터 상수입니다. 따라서 포인터를 사용하여 배열의 요소에 접근할 수 있습니다.

**예시:**
```c
#include <stdio.h>

int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *p = arr; // 배열 이름은 첫 번째 요소의 주소와 같음 (p = &arr[0]; 과 동일)

    printf("배열의 요소 접근:\n");
    for (int i = 0; i < 5; i++) {
        printf("*(p + %d): %d\n", i, *(p + i));
    }

    return 0;
}
```

### 포인터와 함수 (Call by Reference)

함수에 포인터를 인자로 전달하면, 함수 내에서 원래 변수의 값을 변경할 수 있습니다. 이를 'Call by Reference'라고 합니다.

**예시:**
```c
#include <stdio.h>

void swap(int *x, int *y) {
    int temp;
    temp = *x; // x가 가리키는 값을 temp에 저장
    *x = *y;   // y가 가리키는 값을 x가 가리키는 곳에 저장
    *y = temp; // temp 값을 y가 가리키는 곳에 저장
}

int main() {
    int a = 100;
    int b = 200;

    printf("교환 전: a = %d, b = %d\n", a, b);
    swap(&a, &b); // a와 b의 주소를 전달
    printf("교환 후: a = %d, b = %d\n", a, b);

    return 0;
}
```

### 동적 메모리 할당

프로그램 실행 중에 필요한 만큼의 메모리를 할당받아 사용할 수 있습니다. `malloc`, `calloc` 함수를 사용하며, 사용이 끝난 메모리는 `free` 함수를 통해 반드시 해제해야 합니다.

**예시:**
```c
#include <stdio.h>
#include <stdlib.h> // malloc, free 함수를 위해 필요

int main() {
    int *ptr;
    int n = 5;

    // int 5개 크기만큼 동적 메모리 할당
    ptr = (int*)malloc(n * sizeof(int));

    if (ptr == NULL) {
        printf("메모리 할당 실패\n");
        return 1;
    }

    for (int i = 0; i < n; i++) {
        ptr[i] = i + 1;
    }

    printf("동적 할당된 배열 요소:\n");
    for (int i = 0; i < n; i++) {
        printf("%d ", ptr[i]);
    }
    printf("\n");

    // 할당된 메모리 해제
    free(ptr);

    return 0;
}
```

### 이중 포인터 (Pointer to Pointer)

이중 포인터는 다른 포인터의 주소를 저장하는 포인터입니다. 포인터 자체를 함수 내에서 변경해야 할 때 유용하게 사용됩니다.

**예시:**
```c
#include <stdio.h>
#include <stdlib.h>

void allocateMemory(int **pptr) {
    *pptr = (int*)malloc(sizeof(int)); // pptr이 가리키는 곳(ptr)에 메모리 주소를 할당
}

int main() {
    int *ptr = NULL;

    allocateMemory(&ptr); // ptr의 주소를 전달

    if (ptr == NULL) {
        return 1;
    }

    *ptr = 10;
    printf("할당된 메모리의 값: %d\n", *ptr);

    free(ptr);

    return 0;
}
```

### 함수 포인터

함수 포인터는 함수의 시작 주소를 저장하는 포인터입니다. 이를 이용해 함수를 다른 함수의 인자로 전달하거나, 상황에 따라 다른 함수를 호출하게 만들 수 있습니다.

**예시:**
```c
#include <stdio.h>

int add(int a, int b) { return a + b; }
int subtract(int a, int b) { return a - b; }

int main() {
    int (*fp)(int, int); // int형 인자 두 개를 받고 int를 반환하는 함수 포인터 선언
    int result;

    fp = add; // 함수 포인터에 add 함수의 주소를 할당
    result = fp(10, 5);
    printf("add 결과: %d\n", result);

    fp = subtract; // 함수 포인터에 subtract 함수의 주소를 할당
    result = fp(10, 5);
    printf("subtract 결과: %d\n", result);

    return 0;
}
```
 