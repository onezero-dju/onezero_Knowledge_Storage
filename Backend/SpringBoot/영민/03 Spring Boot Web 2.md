# Spring Boot의 다양한 기능 - Object Mapper
JSON -- [[역직력화]] --> DTO
JSON <-- [[직력화]] --- DTO

가운데에서 역직렬화와 직렬화를 하는 것이 Object Mapper이다.
	*( Jackson 라이브러리라고도 한다. )*


@Autowired
	Spring에서 관리하는 bean들 중에 자동으로 생성되는 object mapper를 가져오는 역할을 한다.
	<메서드에 붙는 어노테이션>


### 직렬화 하는 방법
`var user = new UserRequest();`
user 객체를 만들고 정보를 입력한다.

`var json = objectMapper.writeValueAsString(user);`
	user라는 객체를 **직렬화 하기 위한 코드**
	`json`을 출력하여 확인을 해보면, 객체에 담겨있던 내용들이 JSON으로 바뀌어 출력되는 것을 확인할 수 있다.


### 역직렬화 하는 방법
`var dto = objectMapper.readValue(json, UserRequest.class)`
	json이라는 객체를 UserRequest class에 **역직렬화하기 위한 코드**
	`dto`를 출력하게 되면, DTO 형식의 내용이 출력되는 것을 확인할 수 있다.

RequestBody에 있는 JSON 데이터들은 해당 클래스에 역직렬화와 직렬화를 하여 출력하는 것이다.



### Object Mapper의 동작 방식
##### writeValueAsString
Getter, Setter 메서드를 지우고, 하나의 전체 생성자를 만들어서 실행하면 이상한 값을 얻음.
toString은 직렬화 안됨

**Object Mapper의 동작 방식은 변수에 매칭 되는 것이 아니라 ==메서드에 매칭==이 된다.**
기본적으로 생성되는 메서드는 get 메서드이다. 그렇기에 메서드명은 get으로 시작되면, 매칭이 되는 것이다.

이상한 값을 가져올 때도 있는데, 이는 get메서드가 있기 때문이다. 이를 무시하기 위해서는 `@JsonIgnore` 어노테이션을 메서드 앞에 달아두어 무시할 수 있다.

해당 변수에 `@JsonProperty("user_email")` 어노테이션을 달아 강제로 이름을 변경해서 매칭할 수도 있다.


##### readValue
*(ObjectMapper는 [[리플렉션]] 기반으로 동작하기 때문에, 생성자가 private이라도 인스턴스를 생성할 수 있다.)*

JSON을 DTO로 바꿀때는 
Setter 메서드를 참고하는데 Setter 메서드가 없으면, get메소드를 통해서도 세팅이 가능하다.

우리는 lombok을 사용하기 때문에 set 메서드를 만들기 보다는 

@JsonProperty를 이용해 setter와 getter가 없어도 매칭이 가능하다. 하지만 변수가 많아진다면, 사용하기 어려워진다.

그렇기에 돌아가
@NoArgsConstructor
@AllArgsConstructor 어노테이션을 사용하면 된다.








### Object Mapper 최종 정리
RequestBody를 통해 데이터가 서버에 들어올 때에는( *JSON -> DTO, **역직렬화*** )  데이터들을 매칭하여 객체를 만들어 주게 된다.
반대로 서버에서 응답으로 객체를 return하게 되면 **직렬화**를 통해서 JSON으로 바꾸어주는 역할을 하는게 ObjectMapper이다.

Object Mapper는 변수가 아닌 getter, setter 메서드에 매칭이된다. 그렇기에 `@NoArgsConstructor`
`@AllArgsConstructor` 어노테이션을 사용하여 자동으로 관리할 수 있다. `@JsonProperty`를 변수앞에 달아 다른 이름으로 매칭할 수도 있다.