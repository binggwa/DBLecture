# MySQL
### 관리 명령
- show status
  - like 'Threads_connected';
  - like 'Uptime';
  - like 'Queries';
- SQL 문은 반드시 SELECT, INSERT, DELETE, UPDATE 중 하나의 단어로 시작한다
- 이 외의 단어로 시작한다면 거의 관리 명령이다
# 관계형 데이터베이스의 계층
- 스키마 (폴더)
- 데이터베이스
- 인스턴스 : DBMS가 동작할 때의 단위, OS에서는 프로세스라 부름
  - 메모리나 CPU를 실제로 사용하는 실체
- 1개의 인스턴스 아래에는 복수 개의 데이터베이스 존재 가능
- 1개의 데이터베이스 아래에는 복수의 스키마 존재 가능
- 1개의 스키마 아래에는 복수 개의 테이블 존재 가능한 깔끔한 트리 구조
- MySQL은 데이터베이스 계층과 스키마 계층 통합
- Oracle은 인스턴스 아래에 데이터베이스를 1개만 만들 수 있다
- 3계층 : Oracle, MySQL
- 4계층(ANSI가 정한 표준 SQL) : SQL Server, DB2, PostgreSQL