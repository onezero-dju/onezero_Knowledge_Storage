
### JSON을 부르는 방식
snake case
- 언더바( _ )로 구분
	ex) user_name

camel case
- 소문자, 대문자로 구분
	ex) userName



### 코드리뷰
서버와 클라이언트에서 JSON을 다르게 요구하게 되면 값을 받지 못한다.
	ex ) Client는 snake case / Server는 camel case



@JsonNaming(PropertyNamingStrate**gies**.SnakeCaseStrategy.class)
	*(**gies**에 유의해야한다. 이게 최신버전.)*
	*(구버전은 PropertyNamingStrategy.SnakeCaseStrategy.class 라고 한다. 이는 [[디프리케이트]] 되었다.)* 
	객체 클래스에 붙음.
	<클래스에 붙는 어노테이션>



서버에서 모델을 생성할 때, 일관성을 유지하기 위해 snake case나 camel case 중 하나의 케이스로 통일하여 작성해야 한다.
(*우리는 snake case를 사용할 것이다.*)













