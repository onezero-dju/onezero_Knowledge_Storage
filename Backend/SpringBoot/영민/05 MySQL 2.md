# [[쿼리문]]

### CREATE
데이터베이스 생성
`CREATE DATABASE [DB명]`

테이블의 생성
```
CREATE TABLE [테이블명]
(
 [컬럼명][타입][컬럼속성][DEFAULT 값][COMMENT],
 ...
 PRIMARY KEY([기본키 컬럼])
)
```


### INSERT
```
INSERT INTO [테이블 이름]
(
 [컬럼이름1],
 [컬럼이름2],
 [컬럼이름3]
)
VALUES
(
 [컬럼1의 데이터값],
 [컬럼2의 데이터값],
 [컬럼3의 데이터값]
)


// 없어도 되는 값
- NULL 허용 인 컬럼
- DEFAULT 값을 가지는 컬럼
- AUTO INCREMENT (PRIMARY KEY) 컬럼
```

### UPDATE
```
UPDATE [테이블 이름] SET
[컬럼이름] = [값],
...
...
...
WHERE
[조건절]
```


### SELECT
```
SELECT [선택할 필드]
FROM [테이블 명] AS [별칭]
WHERE [조건절]
```


`Set as Default Schema`를 데이터 베이스에 설정을 해두는 것은 SQL문을 실행시킬 때, 기본값으로 설정해둔 것이다.


### schema에서 table을 만드는 방법
- 직접 쿼리문을 작성하는 방법
- GUI 툴을 이용해서 create table이라던지 각각의 툴에 맞는 형태를 사용해서 생성할 수도 있다.

### 백틱, 작은 따옴표 구분
백틱 ( \` ) 은 보통 \` 변수명 \`으로 우리가 지정한 명사를 칭한다.
작은 따옴표( ' )는 보통 문자열에 사용된다.

### Table 값 입력
Table에 값을 입력하는 방법은 SQL [[쿼리문]]을 사용하여 데이터를 입력하고 실행하여 넣어도 되지만,  GUI 테이블에 직접 값을 입력하고 Apply를 해도 된다.


