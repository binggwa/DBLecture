# SELECT 문으로 테이블 내용을 살펴보자
- show databases;
- use (데이터베이스 이름);
- show tables;
- select (속성명) from (테이블명) where (조건) and/or (조건);
  - 조건 <> (같지 않다)
- select DISTINCT district ~~ : 중복 행을 제외하고 표시
### 연산자 우선순위
1. INTERVAL
2. BINARY, COLLATE
3. -(단항 감산), ~(단항 비트 반전)
4. ^
5. *, /, DIV, %, MOD
6. -, +
7. <<, >>
8. &
9. |
10. =, <=>, >=, >, <=, <, <>, !=, IS, LIKE, REGEXP, IN
11. BETWEEN, CASE, WHEN, THEN, ELSE
12. NOT
13. &&, AND
14. XOR
15. ||, OR
16. =(대입 등호), :=
### SQL 기술 규칙
- SQL 문의 마지막에 딜리미터 (대부분 세미콜론 ; ) 을 붙인다
- 키워드(SELECT, FROM 등)의 대소문자는 구별하지 않는다
- 정수는 그대로, 문자열이나 날짜 시각은 작은따옴표('')로 감싼다
- 단어는 반각 스페이스나 개행으로 구별한다. 전각 스페이스는 사용하지 않는다
# SELECT 문을 응용해 보자
- 조건에 order by (속성명) : 오름차순으로 정렬
- order by (속성명) desc : 내림차순으로 정렬
- SELECT count(*) from city where countrycode = 'KOR'; : 실제 행수 카운트
- select group_concat(name) : 문자열이 한 줄에 집약
- select district, count(*) from city where countrycode = 'KOR' group by district; : 행정구역별로 그룹을 나눠 몇 개의 도시가 등록되어 있는지 확인
- select, from, where, group by, having, order by 순
# 데이터의 갱신 삽입 제거
- update city set name = 'Siheung' where countrycode = 'KOR' and district = 'Kyounggi' and name = 'Shihung';
- insert into city values (default, 'Gimpo', 'KOR', 'Kyonggi', 359584);
- delete from city where id = 4080;
- UPDATE (테이블명) SET (열명 = 값)
  - set으로 지정한 열 이외의 것은 변경되지 않음, 갱신할 대상을 where로 간추리는 구문 자주 사용
  - (엶영 = 값) WHERE 조건;
- 복수열의 동시 갱신
  - set 열명=값, 열명=값 ...
- show create table city\G
  - 테이블 정의를 세로로 보기 쉽게 정렬하는 명령
- desc city;
  - 단순 열의 정보를 알고 싶을 때 사용
- auto_increment
  - 기계적으로 유니크한 번호를 할당하고 싶을 때 사용
- insert into 테이블명(열1, 열2, ...) VALUES (값1, 값2, ...);
- INSERT INTO 테이블1 SELECT * FROM 테이블2
  - values 대신에 입력한 값으로 select 문의 결과를 사용하는 방법
- CREATE TABLE 테이블명1 LIKE 테이블명2
  - 테이블명2와 같은 구조의 테이블을 작성할 수 있음(데이터는 없음)
- DELETE FROM 테이블명 WHERE 조건;
# 뷰를 작성하고 복수 테이블에서 선택해보자
- create view citykyonggi as select id, name, population from city where countrycode = 'KOR' and district = 'Kyonggi';
- 서브쿼리 생성
- 결합 실행
### 뷰의 작성과 서브쿼리 및 결합
- 뷰를 사용하는 이점
  - 복잡한 select 문을 일일이 매번 기술할 필요가 없다.
  - 필요한 열과 행만 사용자에게 보여줄 수 있고, 갱신 시에도 뷰 정의에 따른 갱신으로 한정할 수 있다.
  - 데이터 저장 없이 (기억장치 용량을 사용하지 않고) 실현할 수 있다
- CREATE VIEW 뷰명(열명1, 열명2, ...) AS SELECT 문;
- 서브쿼리
  - SELECT 문의 결과를 데이터처럼 다루거나 수치처럼 취급해 조건문에 이용하는 쿼리
- 결합 (JOIN)
  - 하나의 테이블에 있는 열만으로는 데이터가 충족되지 않는 경우에 열을 가지고 오는 조작
  - 내부결합과 외부결합이 있ㅇ므
- 내부결합
  - 열을 가지고와 행에 결합하기 위한 조건을 ON 으로 지정함
  - SELECT 선택하고싶은 열 리스트 FROM 첫번째 테이블명 INNER JOIN 두번쨰 테이블명 ON 결합 조건;
- 외부결합
  - SELECT 선택하고싶은 열 리스트 FROM 첫번째 테이블명 LEFT OUTER JOIN 두번째 테이블명 ON 결합 조건;
  - 왼쪽 테이블의 전체 행이 표시되고, 다른 테이블의 행 데이터는 결합 조건과 일치할 때 그 값이 되고, 없으면 NULL이 됨 