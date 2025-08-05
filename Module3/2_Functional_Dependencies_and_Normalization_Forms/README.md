# 1. 완전(Full), 부분(Partial), 이행적(Transitive) 함수 종속성
***
### Special Types of FDs
- 정규화를 위한 몇가지 특별한 유형을 이해해야 함
  - Full / Partial FDs
  - Transitive FDs
### Full / Partial FDs
- 하나의 관계에서, 만약 속성 A의 집합이 속성 B를 결정한다면,
  - A:(a1,a2,...,an) -> B
  - A의 어떠한 부분집합도 B를 결정할 수 없을 때, 이를 완전 (Full) 함수적 종속이라 함
  - A의 모든 것이 B를 결정하기 위해 필요하다는 것을 Full이라고 표현함
- 만약 A의 적절한 부분 집합이 있다면, 이것을 부분 (Partial) 함수적 종속이라 함
- 정규 형식 중 하나에 필요한 완전 함수 종속을 위해 불필요한 속성을 제거하여 A를 최소화할 필요가 있음
### Example
- Relation R (<u>A, B, C</u>, D, E, F, G)
  - FD1 : A, B, C -> D, E, F, G
  - FD2 : A -> D
  - FD3 : B, C -> E
  - FD4 : F -> G
- FD1 is Full or Partial? FD2의 영향으로 Partial
- FD3 is Full or Partial? 현재 정보로는 B나 C 어떤 것이 E에 영향을 끼치는 지 모름 Full
### Transitive FDs
- 한 관계에서, 만약 속성 A가 B를 결정하고, B가 C를 결정하면, (C is not A)
  - FD1 : A -> B
  - FD2 : B -> C
  - A -> C 도 성립함
### Example
- FD1에서 ABC가 G를 결정하는 것이 Transitive라 볼 수 있음