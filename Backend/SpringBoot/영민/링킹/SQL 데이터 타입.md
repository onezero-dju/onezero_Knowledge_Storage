*(색칠한 것은 자주 사용하는 타입)*
**Primary Key는 BIGINT로 잡는 것이 좋음**.

| Type           | Java                       | 설명                                  |
| -------------- | -------------------------- | ----------------------------------- |
| CHAR(N)        | String                     | **고정 길이**의 문자열 데이터                  |
| ==VARCHAR(N)== | String                     | **가변 길이**의 문자열 데이터                  |
| TINYTEXT(N)    | String                     | 문자열 데이터 (255)                       |
| ==TEXT(N)==    | String                     | 문자열 데이터 (65535)                     |
| MEDIUMTEXT(N)  | String                     | 문자열 데이터 (16777215)                  |
| LONGTEXT(N)    | String                     | 문자열 데이터 (4294967295)                |
| ==JSON==       | String                     | JSON 문자열 데이터                        |
|                |                            |                                     |
| TINYINT(N)     | Integer, int               | 정수형 데이터 -128 ~ +127, 0 ~ 255        |
| SMALLINT       | Integer, int               | 정수형 데이터 -32768 ~ + 32767, 0 ~ 65536 |
| MEDIUMINT      | Integer, int               | 정수형 데이터                             |
| ==INT==        | Integer, int               | 정수형 데이터                             |
| ==BIGINT==     | Long, long                 | 정수형 데이터 (무제한 수 표현)                  |
| FLOAT          | Float, float               | 부동소수점 데이터                           |
| DECIMAL        | BigDecimal                 | 고정 소수형 데이터                          |
| DOUBLE         | Double, double             | 부동 소수형 데이터                          |
|                |                            |                                     |
| ==DATE==       | Date, LocalDate            | 날짜(년도, 월, 일) 형태 기간 데이터              |
| ==TIME==       | Time, LocalTime            | 시간(시, 분, 초, 나노초) 형태 데이터             |
| ==DATETIME==   | DateTime,<br>LocalDateTime | 날짜와 시간 데이터                          |
| ==TIMESTAMP==  | DateTime,<br>LocalDateTime | 날짜와 시간 데이터, Time Zone의 속성을 사용       |
| Year           | Year                       | 년도 표현 데이터 타입                        |
|                |                            |                                     |
| BINARY(N)      | byte[]                     | CHAR 형태의 이진 타입                      |
| BYTE(N)        | byte[]                     | CHAR 형태의 이진 타입                      |
| VARBINARY(N)   | byte[]                     | VARCHAR 형태의 이진 타입                   |
| TINYBLOB(N)    | byte[]                     | 이진데이터 타입 (255)                      |
| BLOB(N)        | byte[]                     | 이진데이터 타입 (65535)                    |
| MEDIUMBLOB(N)  | byte[]                     | 이진데이터 타입 (16777215)                 |
| LONGBLOB(N)    | byte[]                     | 이진데이터 타입 (4294967295)               |



