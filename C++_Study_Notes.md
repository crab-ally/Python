# C++

## 1. 기본

### 1-1. 자료형

| 자료형 | 설명 | 헤더파일 |
| --- | --- | --- |
| int | 정수형 | |
| float, double | 실수형 | |
| char | 문자형 | |
| bool | 불리언형 | |
| std::string | 문자열형 | `<string>` |

> bool 형식은 1이 참, 0이 거짓으로 표현된다.  
> true/false 형식으로 출력하려면 `std::boolalpha`를 사용해야 한다.  
> 이를 해제하려면 `std::noboolalpha`를 사용해야 한다.

### 1-2. 화면에 출력

`std::cout << "출력 문자열" << 변수명 << std::endl;`

| std::cout | 화면에 출력 | 버퍼에 저장했다 출력할 수 있음 |
| std::endl | 줄바꿈 및 버퍼 비우기(flush) | 즉시 출력 보장 |

> `<iostream>` 헤더파일 필요
> `std::` 생략 하려면 `using namespace std;` 사용

### 1-3. 키보드 입력 받기

| `std::cin >> 변수명` | 공백 전까지만 읽어옴 |
| `std::getline(std::cin, 변수명)` | 엔터 전까지 읽어옴 |

```cpp
int age;
std::string name;

std::cin >> age;    // 엔터를 포함하지 않고 읽어옴. 버퍼에 엔터가 남아있음
std::cin.ignore();  // 버퍼에 남아있는 엔터를 제거
std::getline(std::cin,name);   // 버퍼에 엔터가 남아있다면 동작이 원활하지 않음
```

### 1-4. const

값을 변경하지 못하게 만드는 키워드

### 1-5. return 값

- 0: 정상 종료
- 1: 오류 종료

---

## 2. 조건문

### 2-1. if문

```cpp
if (조건) {
  // 조건이 참일 때 실행
} else if (조건) {
  // 조건이 참일 때 실행
} else {
  // 조건이 거짓일 때 실행
}
```

### 2-2. switch문

```cpp
switch (변수) {
  case 값1:  // 변수의 값이 값1일 때
    // 실행
    break;  // switch문 탈출
  case 값2:  // 변수의 값이 값2일 때
    // 실행
    break;
  default:  // 위의 모든 case에 해당하지 않을 때
    // 실행
    break;
}
```

---

## 3. 반복문

### 3-1. for문

```cpp
for (초기화; 조건; 증감) {
  // 실행
}
```

### 3-2. while문

```cpp
while (조건) {
  // 실행
}
```

### 3-3. do-while문

```cpp
do {
  // 실행
} while (조건);
```

### 3-4. break, continue

- break: 반복문 탈출
- continue: 현재 반복 건너뛰고 다음 반복 실행

---

## 4. 함수

```cpp
반환타입 함수명(매개변수) {
  // 실행
  return 반환값;
}
```

> 반환값이 없다면 반환타입으로 `void` 사용  
> `main` 함수 보다 먼저 선언하거나 `main` 함수 보다 아래에 있다면 함수 헤더를 먼저 선언 해야 함

### 4-1. 참조 전달

```cpp
void print(int& a) {
  a = 10;
  std::cout << a << std::endl;
}

int main() {
  int b = 0;
  print(b); // 10
  std::cout << b << std::endl;  // 10
  return 0;
}
```

> `a`는 `b`와 같은 메모리를 가리키는 별명  
> 함수 호출 시 변수 복사가 일어나지 않음  
> `const`를 매개변수 앞에 붙여주면 함수 안에서 변수 값을 변경하지 못하게 할 수 있음

---

## 5. 배열

```cpp
#include <vector>

int battery[4] = {1,2,3,4}; // 크기 고정
std::vector<int> batterys = {1,2,3,4}; // 크기 가변

batterys.size(); // 벡터 크기 반환
batterys.push_back(5); // 벡터에 값 추가

for (std::size_t i : batterys) { // 벡터 순회
  std::cout << i << std::endl;
}
```

> `std::size_t`는 부호없는 정수형으로 벡터의 크기를 나타낼 때 사용한다.

---

## 6. 포인터와 참조

### 6-1. 포인터

주소를 저장하는 변수 (메모리 공간 차지)

```cpp
int a = 10;
int* p = &a; // 포인터 변수 p는 변수 a의 메모리 주소를 가리킴
int* ptr = nullptr; // 눌 포인터

std::cout << *p << std::endl; // 역참조(*), a의 값을 출력
```

#### 포인터 객체 접근

```cpp
struct Point {
    int x;
    int y;
};

int main() {
    Point p = {10, 20};
    Point* ptr = &p;

    // 1. 화살표 연산자 사용 (가장 일반적이고 권장되는 방법)
    std::cout << ptr->x << std::endl;  // 출력: 10
    std::cout << ptr->y << std::endl;  // 출력: 20

    // 2. 역참조와 점(.) 연산자 조합
    std::cout << (*ptr).x << std::endl;  // 출력: 10
    std::cout << (*ptr).y << std::endl;  // 출력: 20

    return 0;
}
```

#### 동적 할당

프로그램 실행 중(runtime)에 원하는 크기의 메모리를 만들기 위해서 사용

```cpp
int n;
std::cin >> n;

int* arr = new int[n];  // 메모리 주소 반환
delete[] arr;  // 메모리 해제
```

### 6-2. 참조

기존 변수의 별명

```cpp
int a = 10;
int& r = a; // 참조 변수 r은 변수 a를 가리킴

std::cout << r << std::endl; // a의 값을 출력
```

---