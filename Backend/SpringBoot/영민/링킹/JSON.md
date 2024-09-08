**JSON**(JavaScript Object Notation)은 **데이터를 저장하고 전송하기 위한 경량의 데이터 형식**입니다. 사람이 읽기 쉽고, 기계가 해석하고 생성하기도 쉬운 구조를 가지고 있으며, 주로 웹에서 클라이언트와 서버 간의 데이터 교환에 사용

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