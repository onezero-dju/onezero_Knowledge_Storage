# Filter 와 Interceptor

![[Pasted image 20241103180047.png]]

## Filter
### 1. 필터란 무엇인가?
필터는 **클라이언트 요청이 서버의 주요 로직에 도달하기 전에 데이터를 검사하고, 조작하며, 접근을 제어하는 중간 처리기** 역할을 합니다. 필터는 서블릿 컨테이너의 **가장 앞단에 위치**하여, 클라이언트에서 들어오는 모든 요청과 서버에서 나가는 응답을 가로채어, 지정된 로직을 수행할 수 있습니다. 이러한 이유로 보안, 로깅, 데이터 검증과 같은 공통적인 작업을 처리하는 데 매우 유용합니다.

### 2. 필터의 역할
필터는 주로 아래와 같은 역할을 수행합니다:

- **인증 및 권한 부여**
- **요청 로깅 및 모니터링**
- **데이터 검증 및 수정**
- **CORS 설정**(Cross-Origin Resource Sharing)
- **데이터 압축 및 변환**

### 3. 필터의 작동 원리
필터는 **서블릿 필터 체인**에서 동작하며, 각 필터는 요청과 응답을 다음 필터로 전달하거나, 특정 조건을 만족하지 않는 경우 요청을 차단할 수 있습니다. 필터는 체인 형태로 구성되어 있어, 요청이 들어올 때 모든 필터를 거친 후 최종적으로 애플리케이션의 컨트롤러에 도달합니다. 요청이 처리된 후에도 응답 역시 필터 체인을 통과하여 클라이언트에 반환됩니다.



### `ContentCachingRequestWrapper`와 `HttpServletRequestWrapper`의 차이

#### 1. `HttpServletRequestWrapper`

`HttpServletRequestWrapper`는 **기존의 `HttpServletRequest` 객체를 래핑하여 특정 요청을 수정하거나 확장할 수 있는 기능을 추가한 클래스**입니다. 기본적으로 제공되는 `HttpServletRequest`의 기능을 확장하고, 필요에 따라 메서드를 오버라이드하여 요청의 일부를 조작할 수 있습니다. 하지만 요청 본문(body)을 직접적으로 캐싱하지 않으므로, 요청 본문을 한 번 읽고 나면 다시 접근할 수 없는 한계가 있습니다.

- **주요 사용 사례**: 헤더 값 추가/변경, 파라미터 추가, 요청 경로 변경 등
- **장점**: `HttpServletRequest`의 기본 기능을 쉽게 확장할 수 있음
- **단점**: 요청 본문을 한 번 읽고 나면 재사용할 수 없음

#### 2. `ContentCachingRequestWrapper`

**`ContentCachingRequestWrapper`**는 **`HttpServletRequestWrapper`를 상속**하여 **요청 본문(body)을 캐싱**할 수 있는 기능이 추가된 클래스입니다. 이 래퍼는 요청 본문을 메모리에 저장해두기 때문에, 본문 데이터를 여러 번 읽거나 사용할 수 있습니다. 이는 요청 본문을 검증하거나 로깅해야 하는 상황에서 유용하게 사용됩니다.

- **주요 사용 사례**: 요청 본문을 로깅하거나, 데이터를 검사하여 여러 번 접근해야 하는 경우
- **장점**: 요청 본문을 여러 번 읽을 수 있어 반복 접근이 가능
- **단점**: 요청 본문을 메모리에 캐싱하므로, 대용량 데이터가 포함된 요청에서는 메모리 사용량이 증가할 수 있음

|특징|`HttpServletRequestWrapper`|`ContentCachingRequestWrapper`|
|---|---|---|
|**기본 목적**|`HttpServletRequest` 기능을 확장|요청 본문을 캐싱하여 여러 번 읽기 가능|
|**요청 본문(body) 접근**|한 번만 읽기 가능|캐싱하여 여러 번 접근 가능|
|**주요 사용 사례**|헤더, 파라미터 추가, 경로 변경 등|요청 본문을 로깅하거나 데이터 검사 시 활용|
|**사용 시 장점**|기본 요청 확장 가능, 설정이 간단|본문 반복 접근 가능, 로깅 및 데이터 검증에 유리|
|**사용 시 단점**|본문 재사용 불가|캐싱으로 인해 메모리 사용량 증가 가능|



## Interceptor
Filter 이후에 Hander Mapping이 일어나고 나면, 그 후에 Interceptor를 통해 전달된다.

### Interceptor란?
Interceptor(인터셉터)는 **Spring MVC에서 클라이언트의 요청을 가로채어 추가 작업을 수행할 수 있는 컴포넌트**입니다. 클라이언트의 요청이 **컨트롤러에 도달하기 전과 후, 그리고 뷰가 렌더링된 후**에 필요한 로직을 추가할 수 있도록 지원합니다. 인터셉터는 주로 **보안 검사, 로깅, 데이터 처리 등의 공통 작업을 구현**할 때 사용됩니다.

### Interceptor의 주요 역할
인터셉터는 Spring MVC의 요청 흐름에서 **컨트롤러의 실행 전후**에 가로채어 다음과 같은 작업을 수행할 수 있습니다.
- **컨트롤러 실행 전(preHandle)**
	값이 true -> controller 전달 / 값이 false -> contoller에 전달하지 않는다.
- **컨트롤러 실행 후(postHandle)**
- **뷰 렌더링 후(afterCompletion)**


```
var methodLevel = handlerMethod.getMethodAnnotation(OpenApi.class);  
if (methodLevel != null) {  
    log.info("method level");  
    return true;  
}

var classLevel = handlerMethod.getBeanType().getAnnotation(OpenApi.class);  
if (classLevel != null) {  
    log.info("class level");  
    return true;  
}  
  
log.info("open api 아닙니다 : {}", request.getRequestURI());  
return false;
```
메서드나 클래스 수준에서 특정 어노테이션(`OpenApi`)이 존재하는지 검사하여, 해당 어노테이션이 있으면 요청을 허용하고, 없으면 요청을 차단하는 조건부 접근 제어 로직









# Spring AOP

AOP( Aspect Oriented Programming )
관점지향 프로그램

스프링 어플리케이션은 대부분 특별한 경우를 제외하고는 MVC 웹 어플리케이션에서는 Web Layer, Business Layer, Data Layer로 정의.

- Web Layer : REST API를 제공하며, Client 중심의 로직 적용
- Business Layer :  내부 정책에 따른 logic을 개발하며, 주로 해당 부분을 개발
- Data Layer : 데이터 베이스 및 외부와의 연동을 처리























