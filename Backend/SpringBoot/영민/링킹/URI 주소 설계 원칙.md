*( 원칙이므로 꼭 이걸 지켜야하는 것은 아님 )*
- 슬래시 구분자 ( / )는 계층 관계를 나타내는 데 사용한다.
- URI 마지막 문자로 ( / ) 는 포함하지 않는다.
- 하이픈 ( - )은 URI가독성을 높이는데 사용한다.
- 밑줄 ( _ )은 사용하지 않는다.
- URI 경로에는 소문자가 적합하다.
- **파일 확장자**는 URI에 포함하지 않는다.
- **프로그래밍 언어에 의존적인 확장자**를 사용하지 않는다.
- **구현에 의존적인 경로**를 사용하지 않는다.
- 세션 ID를 포함하지 않는다.
- 프로그래밍 언어의 Method명을 이용하지 않는다.
- 명사에 단수형 보다는 복수형을 사용해야 한다. 컬렉션에 대한 표현은 복수로 사용
- 컨트롤러 이름으로는 동사나 동사구를 사용한다.
- 경로 부분 중 변하는 부분은 유일한 값으로 대체 한다.
- CRUD 기능을 나타내는 것은 URI에 사용하지 않는다.
- URI [[Query Parameter]] 디자인
	- URI 쿼리 부분으로 컬렉션 결과에 대해서 필터링 할 수 있다.
	- URI 쿼리는 컬렉션의 결과를 페이지로 구분하여 나타내는데 사용한다.
- API에 있어서 서브 도메인은 일관성 있게 사용해야 한다.
- 클라이언트 개발자 포탈 서브 도메인은 일관성 있게 만든다.

>볼드한 것을 지키지 않으면 취약점으로 해커에게 공격 받을 수 있음.