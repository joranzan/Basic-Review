# Hash 
#### _(unordered_set / unordered_map)_   
 **조한준**
* * *

#### 기존 DAT 활용의 단점:

* ###### 배열의 크기가 정해져 있음
* ###### Index에 양의 정수만 가능
* ###### 1억 이상의 큰 수 불가능
* ###### 사용되지 않는 중간 값들로 인한 메모리 낭비

  `모두 배열의 특성 때문에 생긴 불편함`

#### Hash는 이러한 단점을 보완할 수 있다 !
---
## 1. Hash의 개념

### `1.장점`
-  이미 만들어진 구조이기 때문에 따로 구현할 필요 없음
-  필요한 것만 사용하므로 메모리 절약
-  Index에 자료형에 따른 제약이 없음
-  ex)
   -  int
   -  string
   -  float
   -  double
   -  struct
   -  vector
   -  pair
<br>

### `2.Hash Function`
- 데이터를 찾아가기 위해 필요한 함수
- 시간복잡도에 큰 영향을 끼침
- **서로 다른 Key값을 넣어도 내부적인 연산 과정에서 같은 Hash Value가 나올 수 있음**
  - Hash Value : 원본 Key값이 Hash Function에 입력되었을 때 반환된 값
  - Hash Table에서 같은 Hash Value에 여러 데이터가 저장되는 현상 발생
  - 이런 경우 **Hash Value의 중복으로 인한 충돌**이 발생했다 한다

`이를 해결하기 위해서 Hash 구조에서는 Chaining 기법을 사용한다`

<br>

### `3.Chaining 기법`
- 같은 Hash Value에 여러 데이터를 저장
- 저장할 때 원본 Key값도 함께 저장함
  - Hash 구조의 데이터를 확인하면 {key,value} 쌍으로 저장되어 있음
  - 출력할 때 key값이 같이 출력되는 이유

`하지만 최악의 경우 모든 데이터에 대하여 Hash Function에서 구한 Hash Value값이 중복된다면 시간복잡도 O(N)`
##### 따라서 Hash Function이 매우 중요하다
- 내부 계산의 반복이 최대한 적게
- 최대한 충돌이 발생하지 않도록 (중복 줄이기)

<br>

### `4.시간복잡도`
- ##### 일반적인 경우
  - `O(1)`
- ##### 최악의 경우 (모든 데이터 중복)
  - `O(N)`
- ---



## 2. Hash Function 오버라이딩

- ##### unordered_map의 정의
  ```
  class unordered_map : public _Hash<_Umap_traits<_Kty, _Ty, _Uhash_compare<_Kty, _Hasher, _Keyeq>, _Alloc, false>>
  ```
  - 3번째 인자가 Hash Function

- ##### 오버라이딩 하는 방법
  1. 구조체 선언으로 **함수 객체** 만든다
  2. 객체 내 Hash Function의 동작을 구현한다 *(key 받고 Hash Value를 return하는 함수)*
  3. 만든 함수 객체를 자료구조 선언부의 3번째 인자에 넣기
  4. **Key값에 대하여  == 연산자**가 정의되어있지 않다면 새로 정의해줘야 한다





---

## 3. unordered_set

#### 1) 선언
```
#include<unordered_set>
```
#### 2) 명령어
- ##### insert : 삽입
- ##### erase : 데이터 삭제
- ##### find : 데이터 찾기
  

---

## 4. unordered_map

#### 1) 선언
```
#include<unordered_map>
```
#### 2) 명령어
`(set과 동일하다)`
- ##### insert : 삽입
- ##### 자료이름[key값] = value : 수정 추가
- ##### erase : 데이터 삭제
- ##### find : 데이터 찾기

----

###### 질문 목록
- 어떤 문제에서 Hash 자료구조를 사용하면 효율적일까요? 
  - (어떤 유형의 문제에서 고려해야 할까)
- Hash Function을 오버라이딩 해야하는 경우 다른 자료구조를 쓰는게 나을까요? 
  - (오버라이딩은 가급적 지양해야할까?)
- Hash Function을 오버라이딩 할 때 return 값을 size_t 외에 string같은 값으로 return 받아도 되나요?
- 이건 Hash 관련은 아닌데 Github 사용 방법이 익숙하지 않아서 혹시 좀 능숙한 분들 어떻게 활용하시는지 여쭤봐도 될까요?