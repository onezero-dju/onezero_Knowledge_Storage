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
|필드(Field)   | 어트리뷰트(Attribute)         | 컬럼(Column) |

# 데이터베이스 생성
- CREATE DATABASE [DB명]

# 테이블의 생성
- CREATE TABLE[테이블명]
(
    [컬럼명][타입][컬럼속성][DEFAULT 값][COMMENT],
    ...
    ...
    PRIMARY KEY ([기본키 컬럼])
)

## 예시
```sql
CREATE TABLE `user`(
    `id` bigint(32) NOT NULL AUTO_INCREMENT,
    `name` varchar(50) NOT NULL COMMENT '사용자 이름',
    `age` INT NOT NULL DEFAULT '1' COMMENT '사용자 나이',
    `email` varchar(50) NULL DEFAULT '' COMMENT '이메일 주소',
    PRIMARY KEY (`id`)
);
```

# 데이터 삽입
- INSERT INTO [테이블 이름]
(
    [컬럼이름 1],
    [컬럼이름 2],
    [컬럼이름 3]
)
VALUES
(
    [컬럼1의 데이터값],
    [컬럼2의 데이터값],
    [컬럼3의 데이터값]
)

- 없어도 되는 값
   - NULL 허용 인 컬럼
   - DEFAULT값을 가지는 컬럼
   - AUTO_INCREMENT (PRIMARY KEY) 컬럼

## 예시
```sql
INSERT INTO `user`
(
    `name`,
    `age`,
    `email`,
)
VALUES
(
    `홍길동`,
    `10`,
    `hong@gmail.com`
);
```

# 데이터 업데이트
- UPDATE[테이블 이름]SET
[컬럼이름] = [값],
...
...
...
WHERE
[조건절]

## 예시
```sql
UPDATE `user` SET
age = `20`
WHERE
id > 0
and
name = `유관순`
```

# 데이터를 조회
- SELECT [선택할 필드]
FROM[테이블 명] AS[별칭]
WHERE[조건절]

## 예시
```sql
SELECT * FROM user.book;
```

# 데이터 타입
|Type  | JAVA               | 설명 | 
|---------|---------------------|------|
|CHAR(N)   | String       | 고정 길이의 문자열 데이터  |
|VARCHAR(n) | String | 가변 길이의 문자열 데이터 |
|TINYTEXT(N) | String | 문자열 데이터 (255) |
|TEXT(N) | String |문자열 데이터 (65535) | 
|MEDIUMTEXT(N) | String |문자열 데이터(16777215)|
LONGTEXT(N) | String | 문자열 데이터 |
|JSON | String | JSON 문자열 데이터|
|TINYINT(N) | Integer, int | 정수형 데이터 -128 ~ +127, 0 ~ 255 |
|SMALLINT | Integer, int | 정수형 데이터 타입 -32768 ~ +32767, 0 ~ 65536 |
|MEDIUMINT | Integer, int |정수형 데이터 |
|INT | Integer, int |정수형 데이터|
|BIGINT | Long, long | 정수형 데이터 (무제한 수 표현) |
|FLOAT | Float, float | 부동소수점 데이터 | 
|DECIMAL | BigDecimal | 고정 소수형 데이터
|DOUBLE | Double, double | 부동 소수형 데이터 |
|DATA | Data,LocalData | 날짜(년도, 월, 일) 형태 기간 데이터|
|TIME | Time,LocalTime | 시간(시, 분, 초, 나노초) 형태 데이터 |
|DATETIME | Datetime,LocalDateTime | 날짜와 시간 데이터| 
|TIMESTAMP | DataTime,LocalDateTime | 날짜와 시간 데이터, Time Zone의 속성을 사용|
|Year | Year | 년도 표현 데이터 타입|
|BINARY(N) | byte[] | CHAR 형태의 이진 타입|
|BYTE(N) | byte[] |CHAR 형태의 이진 타입 |
|VARBINARY(N) | byte[] |VARCHAR 형태의 이진 타입|
|TINYBLOB(N) | byte[] | 이진데이터 타입 (255)|
|BLOB(N) | byte[] | 이진테이터 타입|
|MEDIUMBLOB(N) | byte[] | 이진데이터 타입|
|LONGBLOB(N) | byte[] |이진데이터 타입