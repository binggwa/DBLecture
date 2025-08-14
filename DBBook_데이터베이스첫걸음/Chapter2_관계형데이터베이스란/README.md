## SQL 기초지식
### SQL 이란?
- Structured Query Language
- 관계형 데이터베이스가 데이터를 조작하기 위해 준비한 언어
- 여러 소프트웨어 공통으로 SQL을 사용할 수 있음
- ex)
```java
SELECT 이름
    FROM 주소록
    WHERE 주소 LIKE '%서울시%';
```
### 4가지 기본 조작
1. SELECT
2. INSERT
3. UPDATE
4. DELETE

### 소프트웨어와 데이터베이스의 관계
- 데이터베이스는 애플리케이션 > 미들웨어 > OS에 이르는 계층 관계 중 미들웨어에 위치한다.