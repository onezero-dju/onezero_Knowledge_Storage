![스크린샷 2024-09-16 14-09-46](https://github.com/user-attachments/assets/76f71fee-315a-4548-b20c-ec7939dfcc3f)

# @RestControllerAdvice
- RestAPI가 사용하는 곳에 예외가 발생하는 것을 감지한다

## @ExceptionHandler
- @ExceptionHandler(value = {Exception.class})

## basePackages
- @RestControllerAdvice(basePackages = "package 경로")
   - package 경로에 있는 모든 Exception을 잡겠다는 것이다.


## ExceptionHandler가 두 개 이상일 때 순서 지정
- @Order를 통해서 순서를 지정할 수 있다
- 우선 순위를 빠르게 하고 싶다면 int의 크기가 최소값을 지정해주면 된다