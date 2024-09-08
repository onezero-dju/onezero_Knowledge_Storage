
# Spring Boot Web에서 응답 만들기

| String         | 일반 Text Type 응답                                 |
| -------------- | ----------------------------------------------- |
| Object         | 자동으로 Json 변환되어 응답 상태값은 항상  200 OK               |
| ResponseEntity | Body의 내용을 Object로 설정 상황에 따라서 HttpStatus Code 설정 |
| @ResponseBody  | RestController가 아닌곳 (Controller)에서 Json응답을 내릴때  |

### 코드리뷰
@RestController
@RequestMapping("/api/v1")
	<클래스에 붙는 어노테이션>

@GetMapping("")
	<메서드에 붙는 메서드>
	추가적인 주소를 안받는다.


@JsonNaming(PropertyNamingStrate**gies**.SnakeCaseStrategy.class)
	<객체 클래스에 붙는 어노테이션>

Object class를 리턴하게 되면, spring boot 가 알아서 JSON으로 바꿔 응답을 내려준다.
응답의 형식은 `@JsonNaming` 어노테이션에 따라 snake case, camel case 값이 달라진다.


### 응답 처리
메서드의 타입을 ResponseEntity class로 선언하고, 
	*(ResponseEntity<\UserRequest>처럼 제네릭으로 메서드 타입을 선언하는 것이 더 좋음. )*
`var response = ResponseEntity.status(HttpStatus.OK).body(user);`
의 변수를 선언하여 리턴 하면, 응답 값을 커스텀할 수 있다.

`HttpStatus.OK` 같은 경우는 200의 응답 값을 가지고 있으며, `OK` 이외에도 `CREATE` 혹은 `BAD REQUEST`는 각각 201번, 400번 응답을 내려준다.


응답에 header를 추가할 수도 있다.
`var response = ResponseEntity.status(HttpStatus.OK).header("x-custom", "hi").body(user);`

#### 다른 방식의 응답 처리

다른 방식으로 응답 값을 커스텀할 수도 있다.


기존의 `@RestController`는 RestAPI를 사용하겠다는 어노테이션이다. 즉 응답값이 JSON으로 내려가겠다는 선언이다. 하지만 Spring Boot에는 Json응답만 있는게 아니기에 HTML을 사용하기 위해
`@Controller` 어노테이션을 <클래스에 붙여 사용하는 어노테이션> 사용하면 된다.

`@Controller` 어노테이션을 사용할때는, 메서드 앞에 `@ReponseBody`라는 어노테이션을 추가해야한다. 만약에 `@ResponseBody` 어노테이션이 없다면, 404 에러가 발생한다. 그러한 이유는 HTML의 형식을 리턴해야하는데, 지원하지 않기 때문이다.

---

`@GetMapping`이외에도 `@RequestMapping(path = "", method = RequestMethod.GET)`을 사용하여 동일하게 사용할 수 있다.

RequestMapping을 사용할 때, 어떤 메서드인지( *GET인지, PUT인지...* ) 지정하지 않으면 모든 메서드를 사용할 수 있어 지정해야한다. 하지만 명확한 GetMapping처럼 확실하게 지정해주는 것이 좋음.

`@RequestMapping`어노테이션은 그냥 참고용..





### ResponseEntity는 언제 사용하는가?
\
로직을 처리하다가 예외가 발생했을 때, 응답 코드를 내리는 용도로 사용된다.