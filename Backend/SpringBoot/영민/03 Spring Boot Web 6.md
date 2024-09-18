# [[Validation]] 실습

### LocalDateTime 의 형식
`yyyy-MM-ddTHH:mm:ss:SSS`
순서대로 년, 월, 일, 시, 분, 초, 밀리초 이다.
날짜(Date)와 시간(Time)은 구분해주는 T(*time의 약자*)를 작성해야한다. 여기서 부터 시간이라는 뜻으로 사용된다.


### Validation 활용
모델 변수에 [[Validation 어노테이션]]을 붙인다.

Controller에서 매개변수에서 모델을 받게되는데, 이때 `@Valid`어노테이션을 걸어둔다.
@Valid
	<매개변수에 붙는 어노테이션>
	매개변수를 받을 때, 해당 객체의 [[Validation 어노테이션]]을 검증을 받게 되는 것이다.

자주 쓰는 Validation 어노테이션
	@NotNull        // != null  
	@NotEmpty       // != null && name != ""  
    @NotBlank       // != null && name != "" &&  name != " "
NotBlank의 범용성이 넓기에 자주 사용된다.


Validation 어노테이션에 message를 활용하여 에러 메시지를 커스텀할 수 있다.

---



잘못된 형식이 입력이 되면 Valid에 의해 어떤 문제가 발생했는지 Server에서는 Warning이라는 로그를 통해 확인할 수 있다.
하지만, Client는 어떤 문제가 발생하였는지 알 수 없다. 그렇기에 ResponseEntity를 통해 어떤 HttpStatus를 반환할지 정하고 body에 에러메시지를 보여줄 수 있다.



### body에 에러메시지 출력 방법
`api` class를 만들어 HttpStatus 와 함께 `data`를 보여줄 것이다. api에서 제네릭 타입으로 받는 data에서도 Valid 검증이 필요하다. 그렇기에 `data`에도 `@Valid` 어노테이션을 달아줘야한다.

Controller에서 매개변수로 `BindingResult` 타입을 가진 매개변수는 Valid가 실행되었을 때, 해당 결과를 매개변수에 담는다.


받은 Valid 결과를 List로 받아와 map으로 하나씩 메시지를 커스텀할 수 있다.
커스텀한 에러메시지들은 HttpStatus Code와 Message를 body로 내보낼 수 있다.

### Handler 사용
BindingResult로 매개변수를 받지 않고 잘못된 값을 받게되면 에러가 발생한다.
그러한 예외를 Handler를 통해 받아 ResponseEntity로 404 에러 또한 발생 시킬 수 있다.

