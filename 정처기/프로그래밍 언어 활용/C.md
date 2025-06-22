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
 