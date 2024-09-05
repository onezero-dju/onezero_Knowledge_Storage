참고 : [[HTTP 메소드]]

[Spring initializr](https://start.spring.io/)에서 프로젝트를 설치할 수 있다.
설정값은 아래와 같다.
Gradle - Groovy

[[Dependencies]]
- Lombok 라이브러리 사용
- Spring Web

프로젝트를 만들어 IntelliJ로 프로젝트를 열어서 작업하는 것.
프로젝트를 실행했을 때, Tomcat port가 무엇으로 시작되는지를 확인 해야한다.


### [[어노테이션]]
`@RestController`
	// Rest api를 처리해주는 컨트롤러
`@RequestMapping("/api")`
	// 괄호 안에 있는 주소를 받는다.


`@GetMapping`
	// Get Method를 사용하기 위해 해당 어노테이션을 작성
	@GetMapping에 path를 설정할 수 있다.
	ex) `@GetMapping(path = "/hello")
	이렇게 되면, /api/hello 의 주소를 받는 것이다.


### 주소
local 주소 이므로 URL은 http로 시작한다. 그 이유는 [[localhost에서 http쓰는 이유]]에서 확인 가능하다.

코드를 실행하였을 때, 해당 주소에 들어가 F12번을 눌러 응답을 확인해서 [[HTTP Status code]]가 200대 이면 요청이 성공된것이다.

메소드 반환값으로 HTML 태그를 직접 넣어도 된다.


### 전체적인 흐름
클라이언트는 서버에 특정 데이터를 요청했고, 서버는 그 요청에 대한 응답을 내려줌.
그 응답은 문자열로 되어 있음. 해당 문자열을 꾸미는 것은 브라우저이다.
데이터를 전달해주는 것은 문자열이다. 그런 문자열은 HTML, JSON, 혹은 특정파일의 형태인지는 해석하기에 따라 다르다.

문자가 전달되는데, 이러한 문자가 전달이 될때는 0과 1의 비트 단위에 데이터가 전달되는 것이다.
이렇게 전달되는것이 [[OSI 7 Layer]]를 타는 것이다.

서버에서 중요한 것은 어떠한 문자를 만들어 내느냐가 중요하다.


