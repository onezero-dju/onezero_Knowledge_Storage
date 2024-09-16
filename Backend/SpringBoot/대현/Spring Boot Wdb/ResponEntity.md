|Spring | 일반 Text Type 응답|
|--------|-----------------------------------------------|
|Object| 자동으로 Json변환되어 응답 상태값은 항상 200 OK|
|ResponseEntity | Body의 내용을 Object로 설정 상황에 따라서 HttpStatus Code 설정|
|@ResponseBody| RestController가 아닌 곳(Controller)에서 Json응답을 내릴 때 |

---
# ResponseEntity
- .status()에는 HttpStatus코드를 넣어줄 수 있다
- .header()로 헤더도 바꿀 수 있다
- .body()로 지정해줄 수 있다


