HTTP 통신에는 HTTP Header와 HTTP Body로 나뉨

http body에는 문자를 담을 수 있음.
문자는 단순 text, html, json, etc
문자로 이루어진 데이터가 body 에 들어간다.

이렇게 되면 좋은 점이 외부 주소에는 해당 데이터가 노출되지 않는다.
그렇기에 GET 방식보다는 더 안전함

실무에서는 GET 방식 보다는 POST 방식 더 나아가 암호화 방식을 사용한다고 한다.