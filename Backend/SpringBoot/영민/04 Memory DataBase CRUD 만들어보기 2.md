### 요청과 응답의 구조
- Client -> 서버에 요청 -> Controller가 요청을 받음.
- Controller -> Service에 요청 -> Service는 비즈니스 로직 수행.
- Service -> Repository로 데이터베이스 처리 요청 및 결과 수신.
- Service -> Controller에 처리 결과 전달.
- Controller -> Client에 응답.
*(Service는 **비즈니스 로직**을 처리하고, Repository는 **데이터베이스와 상호작용**합니다.)*


@Service
	<클래스에 붙는 어노테이션>
	해당 클래스가 **비즈니스 로직**을 처리하는 **서비스 클래스**임을 명시적으로 나타내며, Spring이 이 클래스를 **Spring 컨테이너에 [[Bean]]으로 등록**하고 **의존성 주입**을 통해 사용할 수 있게 합니다.


@Controller
	<클래스에 붙는 어노테이션>
	http 요청이 들어오는 것과 response를 처리하는 영역이라고 표시하는 어노테이션


@Configuration
	<클래스에 붙는 어노테이션>
	해당 어노테이션은 Spring Boot가 실행하면서, 가장 먼저 설정을 해준다는 의미에 어노테이션이다.
	알아서 데이터를 주입해준다.

@Bean
	<메서드에 붙는 어노테이션>
	반환값이 Bean으로 만들어지면 Spring에 의해 관리가 된다.






### Service에서 Repository를 연결하는 방법
##### 1. Service와 Repository가 다른 패키지에 있는 경우
- `@Configuration` 이라는 어노테이션을 붙인 클래스를 만든다. 해당 어노테이션은 Spring boot가 실행하면서, 가장 먼저 설정을 해준다는 의미에 어노테이션이다.
- `@Bean` <메서드에 붙는 어노테이션> 해당 메서드를 통해 **새로운 객체**를 생성하고 반환하여 Spring이 이 객체를 관리하게 만듭니다.

##### 2. Service와 Repository가 같은 패키지에 있는 경우
- Repository 클래스에 `@Service` 어노테이션을 붙여 Spring 컨테이너에 Bean으로 등록한다.
- `@Autowired` 어노테이션을 변수 선언 앞에 붙여 Spring 컨테이너에서 필요한 Bean을 찾아서 해당 필드에 자동으로 주입한다.




### dataList에서 삭제하는 방법
- `prevData`는 `Optional<UserEntity>` 타입이기 때문에, 바로 삭제할 수 없습니다.
- `prevData.get()`을 사용해서 `Optional` 내부에 있는 실제 `UserEntity` 객체를 꺼내서, `dataList.remove()`에 전달해야 삭제가 됩니다.
- `Optional`은 객체가 존재하지 않을 수도 있기 때문에, 내부에 있는 객체를 꺼낼 때는 `get()`을 사용해서 **실제 객체**를 가져와야 합니다.



Delete나 findById 같은 경우에는 PathVariable을 통해 경로에 있는 {id}를 받아와 매개변수로 사용하면된다.


### findone
QueryParam으로 전체 데이터 중에 원하는 데이터를 찾아올 때 쿼리를 붙여 찾아올 수 있다.



### 사용자 10명을 생성 후 70점 이상의 사용자의 정보를 찾아주는 method 작성하기
- User 패키지 이외에 Book 패키지를 만들어 BookEntity에 어떤 형식으로 넣을지 선언한다.
- BookRepository를 만들어 BookEntity를 상속 받는다. BookRepository는 Bean으로 만들어 줘야함.
- BookService를 만들어 BookRepository를 이어 준다. Service에 기능들을 넣는다.
	- Repository에 SimpleDataRepository에서 선언하지 않은 기능을 선언했다면, Service 에서 그 기능을 사용할 수 있다.
- Controller를 만들어 @RequiredArgsConstructor를 통해 BookService를 받는다.
- BookService를 이용하여 메서드들을 사용할 수 있다.


@RequiredArgsConstructor
	<클래스에 붙는 어노테이션>
	`final` 필드와 `@NonNull`로 지정된 필드를 인자로 받는 **생성자를 자동으로 생성**해주는 Lombok 어노테이션입니다.
	이를 통해 **필수적인 의존성**을 간편하게 주입받을 수 있으며, **생성자 주입**을 사용하는 클래스에서 불필요한 코드 작성을 줄여줍니다.




