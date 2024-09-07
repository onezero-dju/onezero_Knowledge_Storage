# PUT이란?
- 리소스 갱신, 생성 메소드이다
- 멱등성이 있다 즉, 몇번을 요청해도 똑같은 데이터가 유지된다

| Method  | 의미                | CRUD | 멱등성 | 안전성 | Path Variable | Query Parameter | DataBody |
|---------|---------------------|------|--------|--------|---------------|-----------------|----------|
| **PUT**    | 리소스 갱신, 생성    | C / U| O      | X      | O             | △               | O        |
---

```
 @PutMapping("/put")
    public void  put(@RequestBody UserRequest userRequest) {
        log.info("Request : {}", userRequest);

    }
```
---

## @Slf4j
- 로그백과 관련된 어노테이션이다
   - 로그백은 **자체적으로 버퍼를 가지고 있기 때문에** 해당 버퍼의 내용을 담고 바로 다음 메소드를 할 수 있도록 return이 된다 
   - 그리고 버퍼의 내용이 콘솔에 찍히게 된다
 
- Systemout으로 찍는 값들은 프로그램이 실행이 될 때 Systemout이 실행이 되고 다음 메소드가 실행이된다
   - 때문에 Systemout을 많이 사용할수록 서버의 **진행속도, 처리 속도가 저하**된다