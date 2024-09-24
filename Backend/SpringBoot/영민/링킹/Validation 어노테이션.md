
| 어노테이션             | 설명                      | 특이사항        |
| ----------------- | ----------------------- | ----------- |
| @Size             | 문자 길이 측정                | Int Type 불가 |
| @NotNull          | null 불가                 |             |
| @NotEmpty         | null, "" 불가             |             |
| @NotBlank         | null, "", " " 불가        |             |
| @Pattern          | 정규식 사용                  |             |
| @Max              | 최대값                     |             |
| @Min              | 최소값                     |             |
| @Email            | Email 양식에 맞게 적용         |             |
| @AssertTrue/False | 별도 Logic 적용             |             |
| @Valid            | 해당 object validation 실행 |             |
| @Past             | 과거 날짜                   |             |
| @PastOrPresent    | 오늘이거나 과거 날짜             |             |
| @Future           | 미래 날짜                   |             |
| @FutureOrPresent  | 오늘이거나 미래 날짜             |             |

핸드폰 번호 정규식
	`"^\\d{2,3}-\\d{3,4}-\\d{4}$"`
	핸드폰 번호의 정규식은 없기 때문에, 
	==`@Pattern(regexp = "^\\d{2,3}-\\d{3,4}-\\d{4}$")`==
	으로 정규식을 만들어 사용한다. 
	regxp는 문자열의 패턴을 받아 정규화한다.


Validation 어노테이션에 괄호를 열어 message를 남길 수 있다.
	ex ) Email(message = "이메일 양식에 맞지 않습니다.")
	이메일 양식에 맞지 않는 데이터가 들어오면 로그가 남는다.

