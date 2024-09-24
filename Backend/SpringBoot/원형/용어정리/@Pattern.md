변수에 정규식을 정할수 있다.
eg.
```java
@Pattern(regexp = "^\\d{2,3}-\\d{3,4}-\\d{4}$",message = "휴대폰 번호 양식에 맞지 않습니다.") //phoneNumber라는 변수에 010-1111-2222라는 형식이 적용된다. 그게 아니면 메시지를 반환한다.
private String phoneNumber;
```
