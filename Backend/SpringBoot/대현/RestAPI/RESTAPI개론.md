# **RESTAPI개론**

## **REST (Representational State Transfer, 자원의 상태 전달)                               네트워크 아키텍처 원리**

1. **Client, Server** : 클라이언트와 서버가 서로 **독립적으로** 분리되어져
있어야 한다.
   - 한 곳에 클라이언트와 서버가 있는 것이 아니라 떨어져있는 상태에서 서로
    자원의 상태를 주고받는 것이 REST의 기준이다

2. **Stateless** : 요청에 대해서 클라이언트의 상태가 **서버에 저장을 하지
않는다.**

3. **캐시** : 클라이언트는 서버의 응답을 캐시 할 수 있어야 한다.
클라이언트가 캐시를 통해서 **응답을 재사용**할 수 있어야 하며, 이를
통해서 **서버의 부하를 낮춘다**.

4. **계층화 (Layered System)** : 서버와 클라이언트 사이에, 방화벽,
게이트웨이, Proxy 등 다계층 형태를 구성할 수 있어야 하며, 확장 할 수
있어야 한다.

5. **인터페이스 일관성** : 아키텍처를 단순화시키고 작은 단위로 분리하여서,
클라이언트, 서버가 독립적으로 개선될 수 있어야 한다.

6. **Code On Demand (optional)** 자바 애플릿, 자바스크립트 플래시 등
특정기능을 서버가 클라이언트에 코드를 전달하여 실행 할 수 있어야 한다.

---

### **인터페이스의 일관성**
> **인터페이스 일관성이 잘 지켜졌는지에 따라 REST를 잘 사용했는지 판단을 할 수 있다.**
>1. 자원 식별
>2. 메시지를 통한 리소스 조작
>3. 자기서술적 메시지
>4. 애플리케이션 상태에 대한 엔진으로서 하이퍼미디어

#### **자원의 식별**

- 웹 기반의 REST에서는 리소스 접근을 URI를 사용합니다.
```https://foo.co.kr/user/100```
   - Resource : user
   - 식별자 : 100

#### **메시지를 통한 리소스 조작**
- Web에서는 다양한 방식으로 데이터를 전송할 수 있습니다.

- 그 중에는 **HTML, XML, JSON, TEXT** 등등 다양한 방법이 있습니다.

- 이 중에서 리소스의 타입을 알려주기 위해서 **header 부분에 content-type를
  통해서** 어떠한 타입인지를 지정할 수 있습니다.

#### **자기서술적 메시지**
- 요청하는 데이터가 어떻게 처리 되어져야 하는지 충분한 데이터를 포함할 수
있어야 합니다.

- HTTP 기반의 REST에서는 **HTTP Method** 와 **Header**의 정보로 이를
표현할 수 있습니다.

#### **애플리케이션 상태에 대한 엔진으로서 하이퍼미디어**

- RESTAPI를 개발할 때에도 단순히 Client 요청에 대한 데이터만 내리는 것이
아닌 관련된 리소스에 대한 Link 정보까지 같이 포함 되어야 한다.
- 이러한 조건들을 잘 갖춘 경우 **REST Ful** 하다고 말하고 이를 **RESTAPI**라고 부릅니다.
---
**URI 설계**
> **URL는 URI의 하위 개념입니다.**

1. URI (Uniform Resource Identifier)
인터넷에서 특정 자원을 나타내는 주소값. 해당 값은 유일 합니다.
```https://www.foo.co.kr/resource/sample/1```
   - response : sample1.pdf, sample2.pdf, sample.doc

2. URL (Uniform Resource Locator)
인터넷 상에서의 자원, 특정 파일이 어디에 위치하는지 식별하는 주소
```https://www.foo.co.kr/sample1.pdf```


> URI 설계원칙 (RFC-3986)                                                                    
> - 슬래시 구분자 ( / )는 계층관계를나타내는데사용한다.
>>
> - URI 마지막 문자로 ( / )는 포함하지않는다.
>>
> - 하이픈 ( - )은 URI 가독성을 높이는데 사용한다.
>>
> - 밑줄( \_ )은 사용하지 않는다.
>>
> - URI 경로에는 소문자가 적합하다
>>
> - 파일 확장자는 URI에 포함하지 않는다.
>>
> - 프로그래밍 언어에 의존적인 확장자를 사용하지 않는다.
>>
> - 구현에 의존적인 경로를 사용하지 않는다
>>
> - 세션 ID를 포함하지 않는다.
>>
> - 프로그래밍 언어의 Method명을 이용하지 않는다.
>>
> - 명사에 단수형 보다는 복수형을 사용해야 한다. 컬렉션에 대한 표현은 복수로 사용
>>
> - 컨트롤러 이름으로는 동사나 동사구를 사용한다.
>>
> - 경로 부분 중 변하는 부분은 유일한 값으로 대체한다.
>>
> - CRUD 기능을 나타내는 것은 URI에 사용하지 않는다.
>>
> - URI Query Parameter 디자인
>   - URI 쿼리 부분으로 컬렉션 결과에 대해서 필터링 할 수 있다.
>   - URI 쿼리는 컬렉션의 결과를 페이지로 구분하여 나타내는데 사용한다.
>>
> - API에 있어서 서브 도메인은 일관성 있게 사용해야 한다.
>>
> - 클라이언트 개발자 포탈 서브 도메인은 일관성 있게 만든다.
