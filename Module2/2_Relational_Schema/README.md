# 1. 관계형 스키마란?
***
### Database Relations
- 데이터베이스 관계를 표현하기 위해 관계형 스키마를 사용함
- 속성 집합과 해당 도메인으로 관계를 정의함
- 관계형 데이터베이스 스키마
  - 관계형 스키마의 세트, 각각 고유한 이름을 가짐
- 일반적인 포맷
  - Name(Attribute1, Attribute2, ..., Attributex(fk), ... , AttributeN)
  - 키 임을 표현할 때 밑줄로 표현
  - fk는 foreign key임을 나타냄
- ex)
  - Stores(<u>StoreID</u>, Street, City, Zip) : Primary key(StoreID)에는 밑줄 포함
  - Employees(<u>EmpID</u>,FirstName,LastName,DoB,Position,Department,StoreID(fk)) : EmpID 가 primary key
### Properties of Relations
- 각 튜플은 구분된다. 즉, 중복되는 튜플은 없다
- 속성의 순서는 중요하지 않다 (열의 순서는 중요하지 않다)
- 튜플의 순서는 이론적으로 의미가 없다
- 관계의 각 셀에는 정확히 하나의 값이 들어 있다
- 각 속성은 구분되는 이름을 가지고 있다
- 속성 값은 모두 같은 도메인에서 가져온 것
- 관계 이름이 관계형 모델의 다른 모든 관계 이름과 구별되어야 한다