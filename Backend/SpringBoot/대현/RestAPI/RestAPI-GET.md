# Controller
- Controller는 클라이언트로부터 어떤 주소로 요청을 받을 것인지를 설정하는 역할을 합니다.

   ```
   @RestController
   @RequestMapping("/api")
   public class RestApiController {

      //"http://localhost:8080/api/hello"
      @GetMapping("/echo/{message}/age/{age}/is-man/{isMan}")
      public String echo(
               @PathVariable(name = "message") String msg,
               @PathVariable int age,
               @PathVariable boolean isMan
      ) {
         System.out.println("echo: " + msg);
         System.out.println("echo: " + age);
         System.out.println("echo: " + isMan);

         return msg.toUpperCase();
      }
   }
   ```

## @RestController
- RestAPI를 처리하는 어노테이션이다
- RestApiController라고v 하는 기능을 하는 특정한 클래스를 지정하기 위해서 하는 것이다

## @RequestMapping
- 어떠한 주소를 받겠다(처리하겠다)를 지정하는 어노테이션이다
- RestApiController는 /api라고 하는 주소를 모두 받아드리겠다라는 뜻이다
- 그 클래스안에 존재하는 것중에 @GetMapping이 있고 path라는 것은 /api 하위에/ hello라는 주소를 처리하는 메소드를 만들고 이 주소가 return하는 것은 html 태그를 가진 문자열이다


> **통신이란 문자열 데이터를 주고받는 과정이라고 할 수 있습니다.**
> - 서버는 클라이언트가 요청한 특정 데이터를 문자열 형태로 응답합니다. 
> - 이 문자열은 브라우저에 의해 예쁘게 꾸며져서 보이게 됩니다. 
>   - 즉, 서버와 클라이언트 간의 데이터는 항상 문자열 형태로 전달되며, 이 문자열이  HTML, JSON 등 어떤 형식인지에 따라 다르게 해석됩니다.

# PATH Variable
- 주소 내에 정보를 전달하는 방법
- **@GetMapping(path = "/echo/{path Variable name})**

## @PathVariable
- 위 { }안에 들어간 이름과 동일하게 맞추면 된다
   - 예시 : @PathVariable String path Variable name
      - 또는 @PathVariable(name = "path Variable name") String name

> **Integer VS int ->  이 둘의 차이는 타입의 차이이다**
> - Reference 타입의 Integer는 null이 할당 될 수 있다
> - Primitive 타입의 Int는 null이 할당될 수 없고 default가 0이다

> **PathVariable에 Reference 타입을 써도 되나요?**
> - 주소 자체가 해당 값이기 때문에 PathVariable에 null이 들어오면 안된다
> - **따라서 Reference 타입의 Integer가 들어올 수 없다**

> **포트찾기 (Window 기준)**
> - netstat -ano | findstr 8080
>   - 여기서 PID를 찾고
> - teskkill /f /pid 0000
>   - PID를 없애면 된다

# Query Parameter
- 특정 정보의 필터링을 걸때 사용한다.
  - ?로 시작하고, 이어주는 형태는 &로 묶어준다

  ```
    @GetMapping("/book")
    public void queryParam(
            @RequestParam String category,
            @RequestParam String issuedYear,
            @RequestParam(name = "issued-month") String issuedMonth,
            @RequestParam String issued_day
            ){
        System.out.println(category);
        System.out.println(issuedYear);
        System.out.println(issuedMonth);
        System.out.println(issued_day);
    }
  ```

- 객체로 받는 방법
   - /model/BookQueryParam
   ```
   @Data                   //자동으로 get, set 매소드들이 만들어진다
   @AllArgsConstructor     // 전체파라미터
   @NoArgsConstructor      // 기본 생성자
   @JsonNaming(value = PropertyNamingStrategies.SnakeCaseStrategy.class)

   public class BookQueryParam {

      private String category;

      private String issuedYear;

      private String issuedMonth;

      private String issued_day;

   }
   ```
   ```
   @GetMapping("/book2")
    public void queryParamDto(BookQueryParam bookQueryParam){

        System.out.println(bookQueryParam);

    }
   ```

