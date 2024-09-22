#### RestApiController
- 서버 -> 클라이언트가 요청을 함 (진입점이 어떠한 주소인지 작성을 해야함)->@RestController 작성 (RestApi를 처리하는 컨트롤러), @RequestMapping("/api") (어떠한 주소를 갖겠다)-> api로 시작하는 주소는 RestApiController로 요청을 받겠다 라고 설정
- GetMapping (Get 메소드를 하기 위해) + (path = "hello") ->  api중에서도 어떠한 주소를 처리하겠다.
- 서버가 있고 컨트롤러가 있음, 여기에 들어오는 주소중에 ooo/api/hello라는 주소는  hello메소드가 처리하겠다.
- local이면 http
- http://localhost:8080/자신이 요청한 주소/ 요청한 주소\
- 마우스 우클릭 -> 검사  -> 네트워크 -> f5 -> 자신이 만든 것 클릭 
- Request URL - 자신이 요청한 URL
- Content-Type - 컨텐츠의 형태를 알 수 있음
- html 태그를 사용하면 이쁘게 포장되어 브라우저에 보여줌
- 서버의 일정 클라이언트는 요청을 하였고 -> 여기에 대한 응답을 해줌 (문자열) -> 해당 문자열을 가지고 이쁘게 꾸며준 것은 브라우저임 -> 문자열은 전달이 될 때 0 OR 1의 비트단위가 전달이 되는 것이다.

#### REST API
- PATH Variable
	- 주소 내에 정보를 전달 하는 방법
	- PathVariable를 받기 위해서는 중괄호를 넣어줘야 함
	- @PathVariable을 소괄호 제일 앞에 넣어줘야 함
	- String 뒤 나오는 말은 위에 중괄호 사이에 넣어준 것과 동일해야 함
	- api 하위에 echo라는 주소에 특정한 PathVariable가 들어가게 되면 문자열로 받기 위해 String 으로 받게 되며 PathVariable을 동일하게 맞춰주면 됨
	- PathVariable가 있는 곳에 자동으로 값이 매칭이 되고 시스템 매칭을 찍고 리턴을 시킴
	- 서버에 특정 값을 요청을 함 -> 해당 서버는 그 특정 값을 에코로 내려주는 형태로 작성 함
		- http://localhost:8080/api/echo/{message} -> message에 다른 것을 입력해주면 입력이 됨
	- 만약 String 다음에 PathVariable가 다른 값이 입력이 된다면 @PathVariable다음 
		- (name = "PathVariable")를 입력한 후 String 후 다른 PathVariable를 입력하면 됨
	- 한글이 깨질때 해결 방법
		- UTF-8(3바이트)을 사용함 (한글을 표기하기 위한 인코딩 방식 = 윈도우를 쓰고 있기 때문에 
		- 윈도우는 MS949를 사용함 (2바이트)
		- MS949 = EUC-KR
		- file -> settings -> encoding을 입력 -> file Encodings -> UTF-8로 통일 시킴 -> apply
		- file -> settings -> encoding을 입력 Console -> Defaulte Encodings를 UTF-8로 변경
		- 만약 오류가 났을때 첫번째나 두번째 것을 들어가 제일 위로 올리면 왜 안되는지 알려줌
		- 포트를 사용하고 있을때에는 새로 만들지 못함 -> 없애거나, 서버를 다르게 띄우는 방법 두가지가 있음
		- 기존것을 X를 누르면 실행이 됨
		- Teminal에 들어가 netstat -ano | findstr8080을 입력
			- taskkill /f /pid 고유 번호 입력
	- - 저번 시간 복습	 
		 - toUpperCase(); -> 대문자로 변환 
		 - Integer age => null 할당 가능
		 - int age => 0이 기본값
		 - 주소를 받을때는 int age
		 - PathVariable int age
		 - PathVariable boolean isMan
		 - 위 두개를 넣을때는 GetMapping 뒤에 /age/{age}/is-man/{isMan}을 넣어줘야 함
		 - 주소는 소문자로만 하고 하이픈 사용 중괄호 뒤에는 대문자 사용 가능
		 - System.out.println()을 각각 만들어 줘야 함
		 - http://localhost:8080/api/echo/steve/age/20/is-man/true -> 주소 적는 법
#### Get
- CRUD -> R
- 멱등성 -> O
- 안정성 -> O
- Path Variable -> O
- Qiery Parameter O
- DataBody -> X

Query Parameter
 - ?로 시작하고 이어주는 형태는 &로 묶어준다.

- GetMapping 뒤에 (path = "/book") 작성 -> (api 뒤에 작성되는 부분)
- String을 받을 때에는  @RequestParam을 사용해준다.
- 위 변수명이 동일하면 동일한 값이 들어오게 됨
- issued-month 같은 경우에는 String 앞에 (name ="issued-month)작성 후 String 뒤에 issuedMonth를 작성해준다.
- 언더바 ( _ )는 괜찮다 

#### BookQueryParam
- Data -> 롬복을 사용할 때 쓰는 데이터
- 앞쪽에서 사용한 변수 그대로 사용하고 private로 묶어줌
- 왼쪽에 스트럭쳐 부분을 클릭하면 해당 클래스에 어떠한 메소드 들이 있는지 확인 가능
- @AllArgsConstructor를 사용하면 전체 파라미터가 들어간 스트링 4개를 받는 파라미터가 생김
	- 기본 생성자가 사라짐
		 - NoArgsConstructor는 어노테이션 중 하나로 파라미터가 없는 기본 생성자를 자동으로 생성해줌
- 위 모델을 만들면 본 코드에서  쓰던 @PathVariable 이 부분을 다 지우고 자신이 적었던 모델 이름을 적으면 됨 ex) (BookQueryParm bookQueryParm)을 적어줌
- 다음 호출 부분에 {system.out.println(bookQueryParm);}을 적어줌
- 하지만 다음 같은 부분을 받기 위해서는 규칙이 있어야 함 (주소를 설계할 때 정상적인 주소가 편함)
- 객체로 받을 때에는 변수의 내용이 많을 때에는 간단하게 적어서 받을 수 있음
- 2~4개 정도는 파라미터를 불러와도 

#### POST
- CRUD -> C
- 멱등성 -> X (데이터가 계속 변화함)
- 안정성 -> X (데이터가 변화하기 때문에 안정적이지 않음)
- Path Variable -> O
- Quiery Parameter -> 세모 (가질순 있지만 적절하지 않을 수 있음) (특정 데이터에 필터링 하는 것)
- DataBody -> O 

HTTP Body
- HTTP Header ()
- HTTP Body (특정한 메세지를 담을 수 있음 (문자로)->  TEXT, HTML, JSON가능)
	- Post + 암호화(이번엔 사용하지 않음)
- api client를 사용 -> 크롬 오른쪽 위에 퍼즐 모양 누른 후 들어감
	- 메소드를 바꾸면서 쓰면 됨\
	- POST를 들어가서 언어를 바꾸면 Headers가 언어에 따라바뀌게 됨
- Post는 객체 형식으로만 받을수 있음
	- 모델을 만든 후 소괄호에 @RequestBody를 적은 후 클래스 이름을 적고 매개변수 이름을 적어줌
- JSON
	- 기본적으로 key와  value로 이루어져 있음
	- 중괄호( { } )로  시작하게 되어있음
		- 다음에는  "key와" : "value"로 이루어져 있음
		- 가능한 것
			- String: 문자  
			- Number: 숫자 (소숫점, int, double, float) 
			- Boolean :true false
			- {중괄호}: object
			- []대괄호: arrary
		- "name" : "Spring Boot", 
		- "number" : "100", "
		- category" : "JAVA"
		- 위처럼 작성하면 됨 시작과 끝에는 중괄호 작성
	- return bookRequest;로 하고싶다면 
		- public void post를 -> public BookRequest post로 변경하면 됨
			- Json에서 Body에 리턴값이 나옴
	- 만약 String으로 받고싶다면
		- return bookRequest.toString();로 바꿈
		- public String post로 바꿈
		- 실행을 하면 body에 BookRequest(name=Spring Boot, number=100, category=JAVA)가 뜸
		- Contetn-Type이 text/plain;charset-UTF-8로 바뀜
	- 파일 저장하는 방법
		- save as누른 후
		- My drive
		- Create -> project
		- add한 후 Name 바꿔주고 저장
	- 깨질 때는  add header에서 Content-Encoding을 UTF-8로 바꿈 
		- 안될 시 help에 Edit VM option을 들어감
			- -Dfile.encoding= UTF-8
			- -Dconsole.encoding= UTF-8
			- 추가해 준 후 재부팅\
- JSON 형태
	- "key" : "value"
	- "array " : [  10,  20,  30  ] (배열) (array의 타입은 동일 해야 함)
	- "string_array" : [  "홍길동","이순신","유관순"  ]
	- "object_array" : [ { "name" : "홍길동" }, { "name" : "이순신" }, {"name" : "유관순"}] object안에 JSON 형태를 받을 수 있음
- JSON을 표현하는 방식
	- snake case
		- 언더바( _ )로 구분 함
			- user_name
			- user_age
	- camel case
		- 지금 많이 사용하고 있는 JAVA의 case
		- 소문자 대문자로 구분
			- userName
			- userAge

- 만약 보내는 쪽에서 snake case로 하면
	- userName는 null값이 나옴 (매칭이 되지 않음)
	- userAge는 int 타입이기 때문에 0이 디폴틑`ㅌ` 값임
		- 위를 잘 나오게 하기 위해서는 Integer타입으로 바꿔줘야 함
		- 하지만 Integer을 사용해도null값이 나와서 @JsonNaming(value = PropertyNamingStrategies.SnakeCaseStrategy.class)를 추가해줘야 함 (gies가 들어가는 것을 설정해 줘야함.)
		- 위를 설정 했다면 해당 클래스의 변수들은 SNAKE CASE들로 매핑하겠다 라고 설정하는 것임

#### PUT
- CRUD -> C/U
- 멱등성 -> O 
- 안정성 -> X (데이터가 변화하기 때문에 안정적이지 않음)
- Path Variable -> O
- Quiery Parameter -> 세모 (가질순 있지만 적절하지 않을 수 있음) (특정 데이터에 필터링 하는 것)
- DataBody -> O 

- Slf4j
	- log팩 관련 된 어노테이션
	- log.info()가 생김
	- 괄호 ( () ) 안에 "Request : {}"를 적어준 후 userRequest를 적어주면 됨
- PUT메소드를 사용 함
	- boolean의 디폴트 값은 false이기 때문에  false가 나옴
		- 스트럭처를 보면 is라는 것이 boolean을 뜻하는 것이기 때문에 setKorean으로 처리가 되어 false가 나오게 되는 것임
		- 이를 해결하기 위한 방법 2가지가 있음
			- 요청을 할 때에 is_korean이 아닌 korean으로 요청을 함
				- 하지만 이렇게 할 시에는 JSON이 전달하고자 하는 의미를 잘 전달하지 못할 수 있음
			- boolean을 Boolean으로 적어주면 잘 나옴
- system.out.println과 log.info의 차이점
	- 똑같은 콘솔을 출력하는 메소드는 맞음
		- system.out.println이 먼저 실행이 되고 해당 다음 메소드가 호출이 됨
			- 그러다 보면 서버의 진행 시간이 많이 걸리게 됨
		- log.info는 버퍼를 가지고 있기 때문에 해당 버퍼의 내용을 담고 바로 다음 메소드를 진행 할 수 있도록 리턴이 됨 그리고 버퍼의 내용이 콘솔에 찍히게 됨
		- 그렇기 때문에 해당 버퍼의 사이즈를 설정 할 수 있음
			- 이러한 부분 때문에 해당 서버의 진행 속도에 영향을 크게 주지 않음
				- 하지만 가득 차게 된다면 영향은 똑같이 받게 됨
				- 활용을 할 때 JSON으로 받게 되면  원하는 포멧을 바꿔줄 수 있음
					- 그러므로 로그의 형태를 마음대로 바꿀 수 있음
					- 언제 요청을 받았는지 어떤 쓰레드가 처리를 했는지도 볼 수도 있음
#### DELETE
- CRUD -> D
- 멱등성 -> O 
- 안정성 -> X (데이터가 변화하기 때문에 안정적이지 않음)
- Path Variable -> O
- Quiery Parameter -> O
- DataBody -> X (데이터를 별도로 전달하지 않기 때문에 필요 없음)

- @DeleteMapping을 적은 후 {path = }을 적어준다면 여러가지 주소도 가능함
- delete를 받을 때는 Path Variable와 Quiery Parameter 두 가지로 받을 수 있지만 Path Variable로 받는 것을 추천 함
	- 한가지 주소만 추천을 함
		- 원래 있던 주소가 오류가 났다면 하나를 더 추가해서 모든 클라이언트를 이동할 때까지 놔둔 후 다 옮겼다면 원래 있던 주소를 삭제해도 됨