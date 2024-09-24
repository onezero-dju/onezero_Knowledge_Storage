# Spring Boot Web 에서의 예외처리 실전 적용

### 예외 처리를 해야하는 이유
각 서버마다 정해진 규격의 API가 있다. 그렇기에 어떤 상황에서도 정해진 형태의 응답이 내려와야한다.

정상적인 응답의 형태와 비정상적인 응답의 형태는 다르다. Client 입장에서 데이터를 요청할 때마다 응답이 달라지게 되면 불편함이 생기게 된다. 이는 API의 공통성이 깨지게 되는 것과 동일하다.

이러한 불편한 점을 해결하기 위해 Web Server를 만들 때, `Exception Handler Advice`를 통해 동일한 응답을 내려줄 수 있도록 예외처리를 해야한다.


---

### 코드 리뷰

동일한 형태의 데이터를 반환할 하나의 모델을 만든다. 이 모델에는 `resultCode`, `resultMessage`그리고 마지막으로 제네릭 타입의 `data`를 받는다.
제네릭 형으로 데이터를 받는 이유는 어떠한 데이터든 일관된 응답을 내리기 위함이다.

`data`는 제네릭 타입이기 때문에 이에 들어갈 예제 모델을 만든다. 이는 `UserResponse` class이다. 여기에는 `id`, `name`, `age`의 변수가 들어간다.
@Builder
	<클래스에 붙는 어노테이션>
	[[builder 패턴]]을 사용하기 위한 어노테이션이다.


`UserApiController` class를 만들어 관리한다.


```
private static List<\UserResponse> userList = List.of(  
        UserResponse.builder()  
                .id("1")  
                .age(10)  
                .name("홍길동")  
                .build()  
        ,  
        UserResponse.builder()  
                .id("2")  
                .age(10)  
                .name("유관순")  
                .build()  
);
```
처럼 builder 패턴을 이용하여 객체를 생성할 수 있으며, 이를 List 로 관리할 수 있다.


```
@GetMapping("/id/{userId}")  
	<메서드에 붙는 어노테이션>
public Api<\UserResponse> getUser(  
        @PathVariable String userId  
	        <매개변수에 붙는 어노테이션>
) {
	var user = userList.stream().filter(  
        it -> it.getId().equals(userId)  
	)  
        .[[findFirst()]]
        .get();
```

//**`userList.stream()`**: `userList`에서 **스트림**을 생성합니다. 스트림은 리스트 내의 요소를 하나씩 처리할 수 있게 해줍니다.

// **`filter(it -> it.getId().equals(userId))`**: `filter()`는 스트림 내의 요소 중 주어진 조건에 맞는 요소만 남겨줍니다. 이 경우에는 `it.getId()`가 `userId`와 같은 요소만 남깁니다. 이 단계에서는 조건을 만족하는 모든 요소가 여전히 스트림에 있을 수 있습니다.

// **`findFirst()`**: 필터된 요소 중에서 **첫 번째 요소**를 반환합니다. 스트림이 정렬되어 있지 않다면 어떤 요소가 "첫 번째"가 될지 확실하지 않을 수 있지만, 정렬된 스트림의 경우 첫 번째 요소가 확실히 결정됩니다.

// **`get()`**: `findFirst()`는 **Optional** 객체를 반환합니다. 이 Optional 객체는 값이 있을 수도 있고 없을 수도 있기 때문에, `get()`을 사용하면 실제 값을 꺼낼 수 있습니다. 만약 값이 존재하지 않으면 `NoSuchElementException`이 발생할 수 있습니다.


```
Api<UserResponse> response = Api.<UserResponse>builder()  
        .resultCode(String.valueOf(HttpStatus.OK.value()))  
        .resultMessage(HttpStatus.OK.name())  
        .data(user)  
        .build();

return response;
```
이는 Client가 요청하는 `userId`가 스트림에 있으면 반환한다. 하지만 없으면 `NoSuchElementException`이 발생할 수 있따.

그렇기에 일관된 응답을 위해서는 예외처리를 해야한다.


```
@ExceptionHandler(value = {NoSuchElementException.class})  
public ResponseEntity<Api> noSuchElement(  
        NoSuchElementException e  
) {  
    log.error("에러발생", e);  
  
    var response = Api.builder()  
            .resultCode(String.valueOf(HttpStatus.NOT_FOUND.value()))  
            .resultMessage(HttpStatus.NOT_FOUND.getReasonPhrase())  
            .build();  
  
    return ResponseEntity  
            .status(HttpStatus.NOT_FOUND)  
            .body(response);  
}
```
해당 코드를 ExceptionHandler class에 작성을 한다. 이 코드를 작성하게 되면, `NoSuchElementException`에 대한 예외를 잡아 작동이 된다.
예외 결과로 응답은 404를 반환하고 데이터 body에는 `resultCode`와 `resultMessage`를 반환한다.



---
### 예외처리 우선순위

정확한 이해를 위해 `RestApiExceptionHandler` class 에서는 Global하게 예외를 잡지 않고,
GlobalExceptionHandler라는 class를 만들어 따로 관리한다.

Handler가 2개인 경우 순서를 지정해 줄 수 있다.
@Order(value = Integer.MAX_VALUE)
	<클래스에 붙는 어노테이션>
	 우선순위가 가장 낮은 순위

@Order(1)
	<클래스에 붙는 어노테이션>
	 MAX_VALUE 보다는 우선순위가 높음.
Order 값을 통해서 우선순위가 결정된다. 숫자가 낮을수록 더 높은 우선순위를 가집니다.


Global 예외처리는 우선순위를 가장 낮게 설정하여 실행되어야 한다. 이러한 예외처리를 하여 예상치 못한 예외를 잡을 수 있다. 

그렇기에 GlobalExceptionHandler는 필수로 넣어야 한다.
