# Spring Boot Validation

Spring Boot 에서는
spring-boot-starter-validation  Dependecies를 통해 Validation 할 수 있다.

beanvalidation 을 검색하여 어노테이션의 설명을 자세히 볼 수 있다.
[Jakarta Bean Validation](https://beanvalidation.org/2.0/spec/)

핸드폰번호 정규식
`"^\\{2,3}-\\d{3,4}-\\{4}\$"`



Validation을 사용하는 이유
1. 유효성 검증 하는 코드의 길이가 너무 길다
2. service logic에 대해서 방해가 된다.
3. 흩어져 있는 경우 어디서 검증 되었는지 찾기 힘들다.
4. 검증 로직이 변경되는 경우 테스트 코드 등, 전체 로직이 흔들릴 수 있다.



[[Validation 어노테이션]]

| 어노테이션             | 설명                      | 특이사항        |
| ----------------- | ----------------------- | ----------- |
| @Size             | 문자 길이 측정                | Int Type 불가 |
| @NotNull          | null 불가                 |             |
| @NotEmpty         | null, "" 불가             |             |
| @NotBlank         | null, "", " " 불가        |             |
| @Pattern          | 정규식 사용                  |             |
| @Max              | 최대값                     |             |
| @Min              | 최소값                     |             |
| @AssertTrue/False | 별도 Logic 적용             |             |
| @Valid            | 해당 object validation 실행 |             |
| @Past             | 과거 날짜                   |             |
| @PastOrPresent    | 오늘이거나 과거 날짜             |             |
| @Future           | 미래 날짜                   |             |
| @FutureOrPresent  | 오늘이거나 미래 날짜             |             |
