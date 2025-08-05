# 1. ERD를 관계형 모델로 변환하는 방법
***
### Converting ERADs to RMs
- ERAD를 관계형 모델로 변환해야 함
- 대다수의 ER 모델에서는 엔티티와 약한 엔티티가 쉽게 관계로 전환됨
- 일반적인 단계
  - 각 엔티티가 직접 관계로 변환
  - 개체의 속성이 관계의 속성이 된다
  - 엔티티의 식별자가 관계의 키가 된다
  - 관계는 외래 키로 매핑되고 이 외래 키는 관계 유형에 따라 특정 개체에 매핑됨 (관계의 카디널리티에 따라 달라짐)
  - 전환 시 참여 여부와 관계 이름이 무시됨
### Binary, One to Many
- 전환을 할 수 있는 몇 가지 시나리오 중 하나
1. 엔티티 이름을 관계 이름으로 변환
2. 속성을 표시 및 식별자를 기본 키로 표시
3. 관계를 살펴보고, 관계를 외래 키로 변환해야 함
4. One 의 기본 키를 Many 의 외래 키로 변환
### Binary, Many to Many
- 처음 2단계는 완전히 똑같음
3. Entity1_2 라는 새로운 관계를 만들어야 함 (관계1과 관계2의 연결용 엔티티)
4. 각각의 식별자를 기본 키와 외래 키로 만듬 (이름이 같은 경우, Attribute1A, 1B로 만듬)
### Unary, One to Many
- 마지막 단계에서 One의 기본 키가 Many의 외래 키가 되어야하므로, 외래 키로서 이름을 1B로 바꾸고 추가
### Unary, Many to Many
- Entity1(Attribute1, Attribute2, Attribute3)
- Entity1_1(Attribute1A(fk), Attribute1B(fk))
### One to One
- Merge
  - 둘을 하나의 관계로 병합하거나 하나의 엔티티로 병합해도 큰 차이가 발생하지 않음
- Not Merge
  - One to One 은 One to Many 의 특수한 경우로 취급할 수 있음
  - 양측이 모두 필수인 경우, 한 쪽을 One으로, 다른 쪽을 Many로 취급함
  - 한쪽만 필수인 경우, 필수인 쪽을 One으로, 다른 쪽을 Many로 취급함
  - 둘다 선택적인 경우, 기본 키에 대해 잘 생각해 봐야 함
### More Than Binary
- 만약 관계가 2 엔티티보다 더 많은 경우, 이들을 binary/unary 관계로 나눌 방법을 생각해봐야 함
- 이런 관계는 다룰 수 없음
***
# 2. Practice
***
- 주어진 ERD를 관계형 모델로 변환하는 연습
- Instructors(Name, <u>EmpID</u>, SSN, DoB, Email, Salary, SupervisorID(fk))
- Course(Title, <u>Course#</u>, Time, Location, Description, Title(fk))
- Instructor_Course(<u>EmpID(fk), Course#(fk)</u>)


- Programs(<u>Title</u>, Chair, Office#, Contact, Description)
- Students(Name,<u>StuID</u>, DoB, Email, Title(fk), EmpID(fk))
- Students_Course(<u>StuID(fk), Course#(fk)</u>)
- Students_Students(<u>StuID(fk), FriendID(fk)</u>) <- 동일 속성을 가질 수 없으므로 이름 변경