# 1. 정규화 형식 및 정규화 프로세스
***
### Normalization Process
- 정규화 과정은 관계를 덜 제한된 형식에서 더 제한된 형식으로 변환하는 것
- 더 낮은 정규화 형식에서 더 높은 정규화 형식으로의 관계를 가질 때 점점 더 많은 요구 사항을 추가할 것
- 제한 수준을 Normal Form(정규화 형태) 이라고 함
  - Unnormalized Form (UNF)
    - 어떠한 제한도 없는 테이블
    - 테이블만 있으면 정규화된 형식임
  - First Normal Form (1NF)
    - 모든 UNF가 1NF가 될 수는 없다
  - Second Normal Form (2NF)
  - Third Normal Form (3NF)
  - Higher Normal Forms (BCNF, 4NF, 5NF etc..)
### UNF
- 하나 이상의 중복되는 그룹을 포함하는 테이블
### 1NF
- 관계에서 각 행열에 단 하나의 값만 포함하고 있음 (1차 정규화 양식의 필수조건)
- 관계의 정의와 같다
  - 각 셀은 정확히 하나의 값만 가져야 함
### 2NF
- 2가지 조건이 필요함
- 1NF일 것
- 기본키가 아닌 모든 속성은 기본키에 완전 함수 종속(fully functionally dependent)되어있어야 함
- ex)
- Relation R (<u>A, B, C</u>, D, E, F, G)
  - FD1 : A, B, C -> D, E, F, G
  - FD2 : A -> D
  - FD3 : B, C -> E
  - FD4 : F -> G
- R은 2NF인가? No
- A는 기본키 ABC의 부분집합이며, A가 D를 결정하기 때문에 D는 ABC 에 부분 종속적이기 때문
- B, C -> E 또한 마찬가지. B,C가 ABC 의 부분집합이므로 E는 ABC에 부분 종속적
### 1NF to 2NF
- 부분 종속성을 없애야 함
- relation R에서 FD2와 FD3가 부분 종속적임을 알았으니, 이들을 새 관계로 옮겨야 함
- 결정자는 새 관계에서 기본키가 되고, 원래 관계에서 외래키가 될것이다.
- Relation R(<u>A(fk), B(fk), C(fk)</u>, F, G)
  - FD1 : A, B, C -> F, G
  - FD2 : F -> G
- Relation R1 (<u>A</u>, D)
  - FD1 : A -> D
- Relation R2 (<u>B, C</u>, E)
  - FD1 : B, C -> E
### 3NF
- 2NF일 것
- 기본키가 아닌 어떠한 속성도 기본키에 전이적 종속이어서는 안된다.
- 즉, 기본키에 대한 어떠한 전이적 종속이 하나라도 있다면, 그 관계는 3NF가 아니다.
### Example
- Relation R (<u>A, B, C</u>, F, G)
  - FD1 : A, B, C -> F, G
  - FD2 : F -> G
- R은 3NF인가? No
  - ABC -> F -> G의 전이적 종속성이 있기 때문
### 2NF to 3NF
- 전이적 종속성을 없애야 함, FD2를 새 관계로 옮김
- Relation R (<u>A(kf), B(kf), C(kf)</u>, F(kf))
  - FD1 : A, B, C -> F
- Relation R3 (<u>F</u>, G)
  - FD1 : F -> G