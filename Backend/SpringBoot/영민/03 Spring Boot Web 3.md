# Spring Boot Web에서 예외처리

### 전체적인 구조
![[Pasted image 20240917180917.png]]
1. Client의 Request
2. Filter 구간 통과
3. DispatcherServlet에서 Handler Mapping을 통해서 어떤 주소를 가진 컨트롤러를 Mapping할지 결정
4. Handler Interceptor
5. Controller에서 어떤 로직을 처리하여 서비스와 데이터를 제공 
6. 이후에 들어왔던 구간들을 다시 통과하여 Response한다.

>Controller에서 로직을 처리하는 과정에서 예외가 발생하게 되면, Exception Handler가 이를 캐치하여 예외에 대한 응답을 내려줄 수 있다.




### 코드 리뷰

@RestController
@RequesetMappint("/api")
	<클래스에 붙는 어노테이션>

@GetMapping(path = "")
	<메서드에 붙는 어노테이션>
public void hello() {
throw **new** RuntimeException("예외 메시지");
	명확하게 throw가 발생하기 때문에, **new**를 걸어줘야 해야한다
}

hello 라는 함수가 호출이 되면, 500 응답을 받게 된다. 예외 메시지는 서버에서 확인할 수 있다.
[[HTTP Status code]] 를 확인하면, 500번 대 에러는 "서버 처리 중 에러가 발생한 상태. 재전송시 에러가 해결 되었을 수도 있다."이다.

---

코딩을 하면서 자주 만나는 에러는 `Out of Index` 이다.
이러한 예외가 발생했을 때, 서버가 원하는 응답을 내려줄 수록 잡아줄 수 있다. 하지만, 하나하나 찾아서 `try catch`로 묶는것은 비효율적다.

그렇기에 Global하게 `Exception Handler`를 사용하여 처리해야한다.


@RestControllerAdvice
	<클래스에 붙는 어노테이션>
	해당 클래스는 Rest API가 사용하는 곳에 예외를 감지한다.


@Slf4j
	<메서드에 붙는 어노테이션>
	로그를 확인하기 위함
@ExceptionHandler(value = {Exception.class})
	<메서드에 붙는 어노테이션>
	어떠한 예외를 잡을건지 클래스를 작성하는 것.
	`Exception.class`를 작성하게 되면 모든 예외를 처리하다는 의미이다.
public ResponseEntity exception (
	exception e
) {
	log.error("에러 메시지", e);
	return ResponseEntity.status(200).build();
}

매개변수에 `Exception e`를 받는다. 이후에 `log.error`를 통해 어떤 에러가 발생했는지 로그를 출력한다. 응답을 상태를 200으로 지정하여 반환하며, `body`는 없이 `build`한다.

---

### 덜 Global한 예외 처리
원하는 예외만 처리할 수도 있다. `Out of Index`의 경우는 `IndexOutOfBoundsException.class` 내에 예외 이므로 메서드 앞에 어노테이션을 바꿔주면 된다.

@ExceptionHandler(value = {IndexOutOfBoundsException.class})
	<메서드에 붙는 어노테이션>
	어떠한 예외를 잡을건지 클래스를 작성하는 것.


---


### 특정 예외 처리
`Exception Handler class` 에서 처리하고 있는(우리가 구현한) 예외는 2가지가 있다. 모든 예외를 잡아주는 어노테이션 
==`@ExceptionHandler(value = {Exception.class})`==와 

`out of index`예외를 잡아주는 어노테이션
==`@ExceptionHandler(value = {IndexOutOfBoundsException.class})`==이다.
number format exception은 out of index가 아니므로, Exception.class에 해당 된다.

---

number format exception과 같은 특정 예외가 발생하는 클래스 내에서

@ExceptionHandler(value = { NumberFormaatException.class })
	<메서드에 붙는 어노테이션>
public ResponseEntity numberFormatException(
	NumberFormatException e
) {
	log.error("예외 메시지", e);
	return ResponseEntity.ok().build();
}

`numberForamtException`메서드를 선언하면, `Exception Handler class`를 거치지 않고 예외를 처리할 수 있다. 하지만 Controller class의 코드가 길어지게 되면 추천하지 않는다.

---

`Exception Handler class`에서 
@RestControllerAdvice(**basePackages** = "com.example.exception.controller")
해당 어노테이션과 같이 **특정 패키지** 지정하여 해당 패키지 내에서 발생하는 예외를 잡을 수 있다.

@RestControllerAdvice(**basePackageClasses** = "RestApiController.class, RestApiBController.class")
해당 어노테이션과 같이 **특정 클래스**를 지정하여 해당 클래스에서 발생하는 예외를 잡을 수도 있다.

어노테이션으로 지정할 수도 있다. 이는 추후에 할 작성할 것이다.
