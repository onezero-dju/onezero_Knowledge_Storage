# SQL
- SQL은 관계형 데이터베이스 관리 시스템의 데이터를 관리하기 위해 설계된 특수 목적의 프로그래밍 언어

## DDl(Data Definition Language) : 데이터를 정의
- CREATE : 데이터의 생성
- ALTER : 테이블의 구조 변경
- DROP : 테이블 삭제
- RENAME : 테이블 이름 변경
- COMMENT : 테이블 및 컬럼 주석 추가
- TRUNCATE : 데이터 초기화

## DML(DATA mANIPULATION lANGUAGE) : 데이터를 조작
- SELECT : 데이터를 조회
- INSERT : 데이터를 삽입
- UPDATE : 데이터 업데이트
- DELETE : 데이터 삭제

## DCL (Data Control Language) : 데이터 제어
- GRANT : 특정 데이터 베이스 사용자에게 권한 부여
- REVOKE : 특정 데이터 베이스 사용자의 권한 회수
- COMMIT : 트랜잭션의 작업이 정상적으로 완료
- ROLLBACK : 트랜잭션의 작업이 비정상적으로 종료되어 원래 상태로 복구

| 파일시스템  | DB 모델링                | RDB | 
|---------|---------------------|------|
|파일(File)   | 엔티티(Entitiy)         | 테이블(Table)  |
|레코드(Record)   | 튜플(Tuple)         | 행(Row)  |
|키(Key)   | 유니크값(Identifier)         | 키(Primary Key, Unique Key)  |
|필드(Field)   | 어트리뷰트(Attribute)         | 컬럼(Column)  |