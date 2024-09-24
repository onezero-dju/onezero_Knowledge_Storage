참고 - [[HTTP 메소드]]

- **CRUD 역할**: PUT은 주로 ==**C(Create) 또는 U(Update)** 역할==을 합니다. 즉, 리소스가 이미 존재하면 업데이트하고, 존재하지 않으면 새로운 리소스를 생성할 수 있습니다.
    
- **멱등성**: PUT은 **멱등성**이 있습니다. 같은 요청을 여러 번 보내더라도 결과는 동일합니다. 예를 들어, 동일한 데이터를 여러 번 PUT 요청으로 전송해도 리소스의 상태는 변하지 않고 요청한 상태로 유지됩니다.
    
- **안정성**: **안정성**은 없습니다. 요청을 처리하면 리소스가 변경되므로 서버의 상태에 영향을 줍니다.
    
- **Path Variable과 Query Parameter**: PUT은 주로 **Path Variable**을 사용해 특정 리소스를 식별하며, 경우에 따라 **Query Parameter**도 사용될 수 있습니다.
    
- **DataBody**: PUT 요청에는 **DataBody**가 필수로 포함되며, 갱신할 데이터가 요청 본문에 담깁니다.




### 코드리뷰

@RestController
	// restapi를 사용하기에 해당 어노테이션을 설정함. 
	<클래스에 붙는 어노테이션>
@RequestMapping("/api")
	// api로 시작하는 주소를 Mapping한다는 어노테이션 
	<클래스에 붙는 어노테이션>


@PutMapping("/put")
	<메서드에 붙는 어노테이션>


@RequestBody UserRequest userRequest
	<매게변수에 붙는 어노테이션>

#### [[로그백]]
[[@Slf4j]]
	[[로그백]]관련된 어노테이션
	<클래스에 붙는 어노세이션>
	system.out이 아닌, log.info("Request : {}", userRequest)로 실행함,
	`@Slf4j`를 사용하면, 로그를 통해 **요청이 들어온 시간**, **로그 레벨(예: INFO, ERROR 등)**, 그리고 **어떤 스레드에서 처리되었는지**와 같은 정보를 확인할 수 있습니다.



#### boolean type vs Boolean type
**프리미티브 타입**인 `boolean`의 기본값은 `false`이다.
`boolean isKorean`의 **snake case**는 `is_korean`이라고 생각할 수 있다. 하지만 boolean 타입의 is로 시작하는 시리즈는 불리언 값을 의미한다. 그렇기에 setter 메서드는 setIsKorean이 아닌 setKorean으로 자동 생성이 된다.

그래서 Client의 요청을 같은 변수명인 `isKorean`으로 해두면, Server의 응답과 매칭이 되지 않는다.

이 문제는 Client 요청 시 `isKorean` 대신 `Korean`으로 전달하여 해결할 수 있다. 하지만, 이 방법은 **JSON**에서 전달하려는 의미를 충분히 전달하지 못하고 혼란을 초래할 수 있다. 그리고 데이터가 없을 때는 `null`이어야 하는데, 기본값인 `false`로 처리되는 문제도 발생할 수 있다.

따라서, 이를 해결하기 위해 **레퍼런스 타입**인 `Boolean`을 사용하는 것이 적절하다. `Boolean`을 사용하면 기본값이 `null`이 될 수 있으며, setter 메서드도 `setIsKorean`으로 정확하게 생성된다.




### System.out과 로그백으로 출력하는 차이
`System.out.println()`은 간단하지만 자주 사용하면 프로그램 속도를 느리게 하고 성능에 영향을 줄 수 있다. 반면, Logback은 **버퍼링**과 **비동기 처리**를 통해 성능을 향상시키고, 여러 스레드에서 안전하게 로그를 관리할 수 있다. 또한, 로그에 **시간**, **로그 레벨**, **스레드 정보** 등을 쉽게 추가하여 더 유용한 정보를 확인할 수 있다.