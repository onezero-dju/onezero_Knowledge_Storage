- **MySQL**은 데이터를 저장하고 관리하는 관계형 데이터베이스입니다.
- **Docker**는 애플리케이션을 컨테이너에 담아 어디서든지 동일한 환경에서 실행할 수 있도록 도와주는 플랫폼입니다.
- **Docker와 MySQL을 함께 사용**하면, 데이터베이스 환경을 더 쉽게 배포하고 관리할 수 있습니다. MySQL 설치와 설정 과정을 Docker 컨테이너로 처리함으로써 빠르고 일관된 환경을 제공합니다.
---
# SQL
SQL은 관계형 데이터베이스 관리 시스템의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어


SQL이라는 언어 
- MySQL
- Oracle
- MariaDB
관계형 DB - RDB

---
### DDL (Data Definition Language) : 데이터를 정의
- CREATE : 테이블의 생성
- ALTER : 테이블의 구조 변경
- DROP : 테이블 삭제
- RENAME : 테이블 이름 변경
- COMMENT : 테이블 및 컬럼 주석 추가
- TRUNCATE : 데이터 초기화

### DML (Data Manipulation Language) : 데이터를 조작 *(우리가 자주 사용할 것)*
- SELECT : 데이터를 조회
- INSERT : 데이터를 삽입
- UPDATE : 데이터 업데이트
- DELETE : 데이터 삭제

### DCL (Data Control Language) : 데이터 제어
- GRANT : 특정 데이터 베이스 사용자에게 권한 부여
- REVOKE : 특정 데이터 베이스 사용자의 권한 회수
- COMMIT : 트랜잭션의 작업이 정상적으로 완료
- ROLLBACK : 트랜잭션의 작업이 비정상적으로 종료되어 원래 상태로 복구

---

[[명칭 정리]]

| 파일 시스템       | DB 모델링            | RDB                           |
| ------------ | ----------------- | ----------------------------- |
| 파일 (File)    | 엔티티 (Entity)      | 테이블 (Table)                   |
| 레코드 (Record) | 튜플 (Tuple)        | 행 (Row)                       |
| 키 (Key)      | 유니크값 (Identifier) | 키 (Primary Key), (Unique Key) |
| 필드 (Field)   | 어트리뷰트 (Attribute) | 컬럼 (Column)                   |
// 같은 열에 있는 명칭은 같은 것을 의미. 어디서 불리느냐에 따라 명칭이 달라지는 것.











