# 데이터 타입
[[SQL 데이터 타입]]

### 문자
| Type           | Java   | 설명                   |
| -------------- | ------ | -------------------- |
| CHAR(N)        | String | **고정 길이**의 문자열 데이터   |
| ==VARCHAR(N)== | String | **가변 길이**의 문자열 데이터   |
| TINYTEXT(N)    | String | 문자열 데이터 (255)        |
| ==TEXT(N)==    | String | 문자열 데이터 (65535)      |
| MEDIUMTEXT(N)  | String | 문자열 데이터 (16777215)   |
| LONGTEXT(N)    | String | 문자열 데이터 (4294967295) |
| ==JSON==       | String | JSON 문자열 데이터         |



TEXT에다가 JSON타입의 문자열을 넣어 사용할 수도 있음.

TEXT타입 컬럼에 JSON을 넣으면 해당 JSON 값에서 특정 검색 같은 기능이 불가능
JSON 타입의 컬럼에 JSON문자열을 넣어두면, JSON body에 있는 내용들을 검색하거나 필터링을 하여 데이터를 다룰 수 있다.

### 수치
| Type       | Java           | 설명                                  |
| ---------- | -------------- | ----------------------------------- |
| TINYINT(N) | Integer, int   | 정수형 데이터 -128 ~ +127, 0 ~ 255        |
| SMALLINT   | Integer, int   | 정수형 데이터 -32768 ~ + 32767, 0 ~ 65536 |
| MEDIUMINT  | Integer, int   | 정수형 데이터                             |
| ==INT==    | Integer, int   | 정수형 데이터                             |
| ==BIGINT== | Long, long     | 정수형 데이터 (무제한 수 표현)                  |
| FLOAT      | Float, float   | 부동소수점 데이터                           |
| DECIMAL    | BigDecimal     | 고정 소수형 데이터                          |
| DOUBLE     | Double, double | 부동 소수형 데이터                          |

BigDecimal 은 보통 금액을 다룰 때 사용하는 데이터 타입이다.

NOT NULL의 컬럼에서는 Integer, int 모두 가능하다
하지만, NULL을 허용하는 컬럼에서는 [[프리미티브 타입]]의 int는 올 수 없다. 그러한 이유는 프리미티브 타입은 null이 될 수 없다. null과 0은 다르다.

그렇기 때문에 default 값이 0인 경우를 제외하고는 Integer를 사용하는 것이 좋다.

**Primary Key는 BIGINT로 잡는 것이 좋음**. 간혹 INT로 잡은 서비스들이 데이터 길이가 꽉 차게 되어 문제가 발생할 수 있다.


### 시간
| Type          | Java                       | 설명                            |
| ------------- | -------------------------- | ----------------------------- |
| ==DATE==      | Date, LocalDate            | 날짜(년도, 월, 일) 형태 기간 데이터        |
| ==TIME==      | Time, LocalTime            | 시간(시, 분, 초, 나노초) 형태 데이터       |
| ==DATETIME==  | DateTime,<br>LocalDateTime | 날짜와 시간 데이터                    |
| ==TIMESTAMP== | DateTime,<br>LocalDateTime | 날짜와 시간 데이터, Time Zone의 속성을 사용 |
| Year          | Year                       | 년도 표현 데이터 타입                  |
Time Zone의 속성
UTD, Asia seoul 와 같이 지역을 지정해서 해당 시간을 사용

### BYTE
| Type          | Java   | 설명                    |
| ------------- | ------ | --------------------- |
| BINARY(N)     | byte[] | CHAR 형태의 이진 타입        |
| BYTE(N)       | byte[] | CHAR 형태의 이진 타입        |
| VARBINARY(N)  | byte[] | VARCHAR 형태의 이진 타입     |
| TINYBLOB(N)   | byte[] | 이진데이터 타입 (255)        |
| BLOB(N)       | byte[] | 이진데이터 타입 (65535)      |
| MEDIUMBLOB(N) | byte[] | 이진데이터 타입 (16777215)   |
| LONGBLOB(N)   | byte[] | 이진데이터 타입 (4294967295) |


*(색칠한 것은 자주 사용하는 타입)*