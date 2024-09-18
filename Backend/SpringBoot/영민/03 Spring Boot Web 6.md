# [[Validation]] 1
### LocalDateTime 의 형식
`yyyy-MM-ddTHH:mm:ss:SSS`
순서대로 년, 월, 일, 시, 분, 초, 밀리초 이다.
날짜(Date)와 시간(Time)은 구분해주는 T(*time의 약자*)를 작성해야한다. 여기서 부터 시간이라는 뜻으로 사용된다.

### Validation 활용
모델 변수에 [[Validation 어노테이션]]을 붙인다.

Controller에서 매개변수에서 모델을 받게되는데, 이때 `@Valid`어노테이션을 걸어둔다.
@Valid
	<매개변수에 붙는 어노테이션>
	매개변수를 받을 때, 해당 객체의 [[Validation 어노테이션]]을 검증을 받게 되는 것이다.

자주 쓰는 Validation 어노테이션
	@NotNull        // != null  
	@NotEmpty       // != null && name != ""  
    @NotBlank       // != null && name != "" &&  name != " "
NotBlank의 범용성이 넓기에 자주 사용된다.

Validation 어노테이션에 message를 활용하여 에러 메시지를 커스텀할 수 있다.


---
# Validation 2

잘못된 형식이 입력이 되면 Valid에 의해 어떤 문제가 발생했는지 Server에서는 Warning이라는 로그를 통해 확인할 수 있다.
하지만, Client는 어떤 문제가 발생하였는지 알 수 없다. 그렇기에 ResponseEntity를 통해 어떤 HttpStatus를 반환할지 정하고 body에 에러메시지를 보여줄 수 있다.



### body에 에러메시지 출력 방법
`api` class를 만들어 HttpStatus 와 함께 `data`를 보여줄 것이다. api에서 제네릭 타입으로 받는 data에서도 Valid 검증이 필요하다. 그렇기에 `data`에도 `@Valid` 어노테이션을 달아줘야한다.

Controller에서 매개변수로 `BindingResult` 타입을 가진 매개변수는 Valid가 실행되었을 때, 해당 결과를 매개변수에 담는다.


받은 Valid 결과를 List로 받아와 map으로 하나씩 메시지를 커스텀할 수 있다.
커스텀한 에러메시지들은 HttpStatus Code와 Message를 body로 내보낼 수 있다.

### Handler 사용
BindingResult로 매개변수를 받지 않고 잘못된 값을 받게되면 에러가 발생한다.
그러한 예외를 Handler를 통해 받아 ResponseEntity로 404 에러 또한 발생 시킬 수 있다.


---
# Validation 3

커스텀한 Validation

Validation 할 때, 중복 조건.
name 또는 nickName 하나는 있어야한다는 조건.
둘 중에 하나라도 있어야한다는 어노테이션은 지원되지 않는다.



@AssertTrue
	`@AssertTrue`는 필드나 메서드가 `true`여야 유효성 검사를 통과한다.
	<메서드에 붙는 어노테이션>


@AssertFalse
	@AssertTrue의 반대. false이여야 유효성 검사를 통과한다.

---
### 커스텀 어노테이션

##### 사용 이유
1. 재사용성
2. 유지보수의 편리성
3. 코드 가독성 및 일관성
4. 복잡한 검증 로직 분리
5. 메타데이터 추가


##### 만드는 방법
1. 어노테이션 클래스를 만들어 검증에 걸렸을 때 발생할 default message와 정규식을 작성한다.
2. 검증을 위한 validator 클래스를 만든다.
3. `implements ConstraintValidator<A, T>` validator 클래스는 이를 상속 받는다.
	A : 어노테이션
	T : 검사할 데이터 타입
4. **`initialize()`** 메서드에서는 **`PhoneNumber`** 어노테이션으로부터 정규 표현식을 받아와 저장합니다.
5. **`isValid()`** 메서드에서는 전달된 문자열 값(전화번호)을 **정규 표현식**과 비교하여 일치하면 `true`, 그렇지 않으면 `false`를 반환합니다.
==6. Pattern.matches(`정규식`, `입력값`) 으로 넣어야한다.==
7. 검증을 해주는 validator 클래스를 어노테이션 클래스에 넣어 어떤걸로 검증하는지 작성한다.
8. 어노테이션 클래스에 group과 payload를 작성한다.
	- `groups()`는 상황에 따라 다른 유효성 검사를 적용할 수 있도록 **유효성 검사 그룹**을 정의하는 필드입니다. 이를 사용하지 않으면 모든 상황에서 동일한 검사가 적용됩니다.
	- `payload()`는 유효성 검사의 **추가 메타데이터**를 전달할 수 있는 용도로 사용되며, 검증 실패 시 추가적인 정보를 전달하거나 특정 행동을 트리거할 수 있습니다. 이를 사용하지 않으면 기본적인 검증 로직만 실행됩니다.


6번을 Pattern.matches(`입력값`, `정규식`) 으로 하게 되면, 정확한 값을 Client가 입력해도 false를 반환한다. 
~~(이거 때문에 1시간 날림... 아니 강의에선 입력값 정규식 순으로 넣던데...ㅠ)~~

