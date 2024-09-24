참고 - [[HTTP 메소드]]

- **CRUD 역할**: DELETE는 ==**D(Delete)** 역할==을 수행하며, 서버에서 특정 리소스를 제거하는 요청을 보냅니다.
    
- **멱등성**: DELETE는 **멱등성**을 가집니다. 즉, 같은 DELETE 요청을 여러 번 보내도 결과는 동일합니다. 첫 번째 요청에서 리소스가 삭제되었으면, 이후의 DELETE 요청은 성공적으로 처리가 되더라도 서버에 남아있는 리소스는 없으며 결과적으로 상태가 변하지 않습니다.
    
- **안정성**: DELETE는 **안정성**이 없습니다. 리소스를 삭제하는 작업은 서버의 상태를 변경하기 때문에, 요청이 서버의 상태에 영향을 줍니다.
    
- **Path Variable과 Query Parameter**: DELETE 요청은 주로 **Path Variable**을 사용해 삭제할 리소스를 식별합니다. **Query Parameter**도 경우에 따라 사용될 수 있습니다. 예를 들어, 조건에 맞는 리소스를 삭제할 때 Query Parameter를 사용할 수 있습니다.
    
- **DataBody**: DELETE 메서드는 일반적으로 **DataBody**가 필요하지 않으며, 리소스의 경로만을 통해 삭제 작업을 처리합니다. 하지만, 특정 API에서는 조건에 따라 본문 데이터를 허용하는 경우도 있습니다.



@DeleteMapping("/delete")
@DeleteMapping(path = {"/delete", "/del"})
@DeleteMapping(path = {"user/{userName}/delete", "user/{userName}/del"})
	<메서드에 붙는 어노테이션>
	path로 지정하면, 2가지 이상의 주소를 설정할 수 있다.



@PathVariable String userName
	<매게변수에 붙는 어노테이션>


Client 요청을 통해 들어온 userName은 Server에서는 삭제하면 된다.





