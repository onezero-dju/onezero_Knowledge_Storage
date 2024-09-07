# POST란?
- Databody를 통해서 Data를 전달하는 방식이 POST방식이다.
- POST방식은 Default가 객체로 데이터를 받아야한다.

---

## @RequestBody
- POST 또는 PUT 방식에서 HTTP body로 들어오는 데이터를 해당 객체에다가 데이터 클래스에 매핑을 해주겠다는 의미이다.

### RequestBody로 사용자의 이름, 전화번호, 이메일을 받는 POST Method 만들기
- **UserRequest**
   ```
   @Data
   @AllArgsConstructor
   @NoArgsConstructor

   public class UserRequest {
       private String userName;

       private int userAge;

       private String email;
   }
   ```
- **POST Method**
   ```
   @PostMapping("/user")
       public void User(@RequestBody UserRequest userRequest){
           System.out.println(userRequest);

       }
   ```
---
## **JSON의 형태**
- 기본적으로 **Key : Value**의 형태를 가진다
   - 가장 바깥쪽은 중괄호로 시작을 하고 그 다음은 Key : Value가 한 쌍으로 매핑이 되어있다
> - **예시**
>   - {
>    "key" : "value"
>   }
>> 
> - String : 문자
> - Number : 숫자 (소숫점, ing double, float)
> - Boolean : true / false
> - {} : Object
> - [] : arrary

### JSON의 array기본적인 규칙
- 반드시 ([ ])안에 있는 자료형은 동일해야 한다
>   - {
>    "array" : [10, 20, 30],
>    "string_array" : ["홍길동", "이순신", "유관순"],
>    "object_array" : [{"name" : "홍길동"}, {"name" : "이순신"}]
>   }

### JSON의 표현 방식
1. **snake case**
   - 구분짓는 부분에 ( _ ) 언더바로 표현한다

2. **camel case**
   - 자바의 방식
   - 첫번째 시작은 **소문자로 시작**하고 **구분을 짓는 부분에 대문자**로 표현