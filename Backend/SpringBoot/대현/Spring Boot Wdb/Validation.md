![image](https://github.com/user-attachments/assets/b6b8b22a-c372-43cf-bf29-9dc9f516ae8a)

![image](https://github.com/user-attachments/assets/895683d2-393c-42d1-802a-a27a0a1e79cd)


# Validation을 사용하는 이유
1. 유효성 검증하는 코드의 길이가 너무 길다
2. service logic에 대해서 방해가 된다
3. 흩어져 있는 경우 어디서 검증 되었는지 찾기 힘들다
4. 검증 로직이 변경되는 경우 테스트 코드 등, 전체 로직이 흔들릴 수 있다.

||||
|------|------------|-------------|
|@Size|문자 길이 측정|Int Type 불가|
|@NotNull|null 불가| |
|@NotEmpty|null, ""불가|
|@NotBlank|null, "", " " 불가|
|@Pattern|정규식 적용||
|@Max | 최대값|
|@Min |최소값|
|@AssertTrue/False |별도 Logic 적용 |
|@Valid | 해당 object validation 실행|
|@Past | 과거 날짜
|@PastOrPresent| 오늘이거나 과거 날짜
|@Future | 미래 날짜
|@FutureOrPresent| 오늘이거나 미래 날짜

# bindingResult 인터페이스
- 해당 @valid가 실행이 되었을 때 해당 결과를 bindingResult에 담아준다


