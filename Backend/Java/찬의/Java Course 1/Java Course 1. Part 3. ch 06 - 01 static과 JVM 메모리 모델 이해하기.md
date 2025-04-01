public static void main (String[] args){}
static이 어떤 의미인가?

static 키워드와 메모리 관계를 이해하고 JVM에 사용하는 메모리 모델을 통해 자바 프로그램이 어떻게 구동되는지 원리를 학습하는 것을 목표로 한다.

메인(시작) 클래스는 왜 객체생성 없이(new)실행이 되나요?
메인(시작)클래스가 동작(실행)되는 방식을 이해해야 한다.
1. JVM이 실행할 클래스를 찾는다. 찾았다면?
2. static 키워드가 붙어있는 멤버들을 정해진 메모리(static-zone)위치에 한번 자동으로 로딩한다.
	1. static 멤버들은 클래스를 사용하는 시점에서 딱 한번 메모리에 로딩된다는 점이 중요하다.
	2. 여기서는 main()메서드가 static이기 때문에 메모리에 자동으로 로딩한다.
3. JVM이 static-zone에서 main()메서드를 호출한다.
4. 호출된 메서드를 Call Stack Frame Area(Stack Area)에 push(기계어 코드를 넣고) 한 뒤 동작을 시작한다.
Method Area가 존재하고 Method Area의 static-zone에 static키워드가 붙어 있으면 올라가고 static 키워드가 없으면 none-static-zone으로 올라간다.

후에 Stack Area가 생성되고 main()이 push되어 동작을 시작.

Call Static Frame Area
- 메서드가 호출되면 호출된 기계어 코드가 push되고 실행되는 메모리 공간
- 현재 프로그램이 실행되고 있는 상태를 파악할 수 있다.
- LIFO구조이다.
PC
- 현재 수행중인 프로그램 위치


