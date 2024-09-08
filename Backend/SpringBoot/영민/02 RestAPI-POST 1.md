참고 - [[HTTP 메소드]]

- **CRUD 역할**: POST는 **C(Create)** 역할을 합니다. 서버에 새로운 리소스를 생성하는 요청을 보낼 때 사용됩니다. 또한, 데이터를 처리하는 목적으로도 사용됩니다(예: 양식 제출, 파일 업로드 등).
    
- **멱등성**: POST는 **멱등성이 없습니다**. 동일한 POST 요청을 여러 번 보내면 그때마다 새로운 리소스가 생성될 수 있어, 결과가 달라질 수 있습니다. 예를 들어, 동일한 데이터로 두 번 POST 요청을 하면 두 개의 리소스가 생성될 수 있습니다.
    
- **안정성**: POST는 **안정성이 없습니다**. POST 요청은 서버에 새로운 데이터를 생성하거나 작업을 수행하기 때문에 서버의 상태가 변합니다.
    
- **Path Variable과 Query Parameter**: POST 요청에서도 **Path Variable**을 사용할 수 있지만, 주로 특정 리소스를 추가하는 용도로 사용됩니다. **Query Parameter**는 선택적으로 사용될 수 있습니다.
    
- **DataBody**: POST는 **DataBody**가 필수입니다. 새로운 데이터를 서버에 보내기 위해 요청 본문에 데이터가 포함되며, 이 데이터가 서버에서 처리됩니다

POST는 클라이언트에서 서버로 데이터를 전송하고, 서버에서 이를 처리하여 새로운 리소스를 만들거나 상태를 변경하는 데 사용됩니다.

### [[Data Body]]
HTTP 통신에는 HTTP Header와 HTTP Body로 나뉨

http body에는 문자를 담을 수 있음.
문자는 단순 text, html, json, etc
문자로 이루어진 데이터가 body 에 들어간다.

이렇게 되면 좋은 점이 외부 주소에는 해당 데이터가 노출되지 않는다.
그렇기에 GET 방식보다는 더 안전함

실무에서는 GET 방식 보다는 POST 방식 더 나아가 암호화 방식을 사용한다고 한다.





### 코드 리뷰

@RestController
	// restapi를 사용하기에 해당 어노테이션을 설정함. 
	<클래스에 붙는 어노테이션>
@RequestMapping("/api")
	// api로 시작하는 주소를 Mapping한다는 어노테이션 
	<클래스에 붙는 어노테이션>


@PostMapping("/post")
	// post에 요청을 받기 위한 어노테이션
	<메소드에 붙는 어노테이션>


**POST 방식의 경우는 default가 객체로 매개변수를 받아와야한다.**
참고 - [[객체 만들 때 어노테이션]]

@RequestBody BookRequest bookRequest
	// http body로 들어오는 데이터를 해당 객체에 mapping을 하겠다는 어노테이션
	// spring boot web의 기본값을 json, html이다.
	<매게변수에 붙는 어노테이션>




### [[JSON]]
 key : value 로 이루어져 있다.
{
	"name" : "Spring Boot",
	"number" : "100",
	"category" : "JAVA"
}

JSON에서 지원하는 데이터 유형
- **문자열(String)**: `"example"`
- **숫자(Number)**: `42`, `3.14` 
	*( int, double, float 의 데이터 타입을 따로 구분하지 않음 )*
- **불리언(Boolean)**: `true`, `false`
- **객체(Object)**: `{ "key": "value" }`
- **배열(Array)**: `[ "value1", "value2", "value3" ]`




Talend API에서 주소를 맞추고 BODY에 JSON형식의 데이터를 넣고 SEND를 하게 되면 서버 로그에 값들이 넘어오는 것을 확인할 수 있다.




