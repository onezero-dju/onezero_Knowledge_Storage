변수에 길이를 정해주는 어노테이션
```java
@Size(min = 1, max = 12) //password의 길이는 1~12까지의 문자열이 들어가야 한다.
private String password;
```