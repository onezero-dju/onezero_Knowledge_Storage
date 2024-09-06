참고 - [[HTTP 메소드]]

# [[Path Variable]]로 받는 방법
@GetMapping(path = "/echo/{**message**}")
중괄호에 유의


### 메소드에 매개변수를 선언

@PathVariable String **message**
	변수명은 메소드의 어노테이션에 있는 괄호안에 있는 변수명과 같아야한다.


주소로 입력 되는 값을 문자로 parsing하는 것이다.
메소드의 변수로 자동으로 값이 매칭이 되는 것이다.

클라이언트는 어떤 값을 요청하게 되면, 서버는 그 특정 값을 echo로 내려는 역할을 한다.


@PathVariable(name = "message") String **msg**
	이렇게 변수명이 다른 경우에는 어노테이션에 name이라는 변수에 원하는 데이터 값을 넣으면 msg에 name의 값이 매칭이 되어 사용할 수 있다.



### port 오류
port가 이미 열려있다고 뜬다면,

window 기준
cmd에 `netstat -ano | findstr {port 번호}` 을 입력해서 ID를 찾고
`taskkill /f /pid {해당 ID}`을 입력하여 port 를 닫을 수 있다.



### Integer와 int의 차이

레퍼런스 타입의 Integer는 null이 할당 될 수 있다.
int 타입은 null이 할당 될 수 없고, 디폴트 값이 0이다.


[[Path Variable]]인 경우는 주소에 null이 들어올 수 없으므로 [[프리미티브 타입]](Primitive Type)의 데이터가 와야한다.
	*( null 인 경우 404 ERROR 발생 )*








# [[Query Parameter]]로 받는 방법
```
http://localhost:8080/api/book?category=IT&issuedYear=2023&issued-month=01&issued_day=31
```

@GetMapping(path = "/book")

매개변수 설정
@RequestParm String category
@RequestParm String issuedYear
@RequestParm(name = "issued-month") String issuedMonth
	원칙을 잘 지키는 코드
@RequestParm String issued_day

변수명이 동일하면 요청되는 동일한 값으로 매칭된다.
java에서는 `issued-month`와 같이 - 를 변수명으로 사용하지 못하므로, 따로 이름을 설정해줘야 한다.


주소에는 대문자를 사용하지 않음.
	참고 : [[URI 주소 설계 원칙]]
Java는 카멜 케이스를 사용함.



#### 모델을 활용한 Query Parameter

@Data 
	어노테이션을 클래스 앞에 선언한다.
	이는 lombok을 사용하기 위함이다.

lombok을 사용하게 되면, 자동으로 Get, Set 메소드들이 만들어진다.

@AllArgsConstructor
	전체 파라미터를 가진 생성자 어노테이션\

@NoArgsConstructor
	파라미터를 받지 않는 기본 생성자 어노테이션




### 객체를 매개변수로 받는 경우

BookQueryParam bookQueryParam
	@RequestParam 을 사용하지 않고 객체를 선언하여 받는다.

하나의 규칙을 정해야한다.
	ex ) QueryParam을 사용하는 경우에는 카멜 케이스를 사용한다.
	그렇지 않으면, 값을 받아오지 못할 수도 있음 (null)










