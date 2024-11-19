# Java는 객체지양 프로그램이다.
> 클래스 (객체) 단위로 프로그래밍을 하는것
![[스크린샷 2024-11-08 203749.png]]
# Java SE 프로젝트 구조 살펴보기

자바 프로젝트 구조에는 JavaEE 와 SE가 있는데 이 강의에서는 SE에 대하여 다룰 것이다. 
이 프로젝트에는 실행 코드 파일(out)[^1] 소스 코드 파일(src)[^2] 이 있다.

1. **소스 코드 작성**: `Main.java`와 같은 파일에 자바 코드 작성.
2. **컴파일**: `javac Main.java` 명령을 통해 소스 코드가 바이트 코드로 변환되고 `Main.class` 파일(실행 코드 파일)이 생성됨.
3. **실행**: `java Main` 명령을 통해 JVM이 바이트 코드를 해석하고 프로그램이 실행됨.

- 위 과정중 컴파일과 실행 단계가 intelij에서 자동으로 해준다. 
- 터미널에서 컴파일&실행하는 방법 ![[Pasted image 20241108215034.png|500]]
	- 뒤에 -encording UFT-8은 한국어가 들어갔을 경우 붙여야한다.
--- 
# JVM과 자바의 구동방식

위에서도 설명되어있듯 소스코드를 실행시키려면  `javac Main.java` 명령을 통해 소스 코드를 바이트 코드로 변환시키고 JVM(Java Virtual Machine)이 바이트 코드를 해석해서 실행시킨다. 

>왜 이렇게 하는걸까??
- 개발하고있는 운영체제 이외의 다른 운영체제에서 잘돌아가도록 하기위해 중간코드(바이트코드)로 만들어 놓고 JVM이 자신의 OS(운영체제)에 맞게 한 번 더(2차)컴파일 하여 메모리에 로딩하여 실행하는것이다.
- JVM은 자동으로 메모리를 관리해준다.
## Part2 ch2 응용코드
```java
 package Part1;  
  
import java.util.Scanner;  
  
public class Operator {  
    public static void main(String[] args) {  
        Scanner sc = new Scanner(System.in);  
        int a,b,c,d,e,f,g;  
        System.out.println("국어 :");  
        a=sc.nextInt();  
        System.out.println("과학 :");  
        b=sc.nextInt();  
        System.out.println("한문 :");  
        c=sc.nextInt();  
        System.out.println("사회 :");  
        d=sc.nextInt();  
        System.out.println("영어 :");  
        e=sc.nextInt();  
        System.out.println("역사 :");  
        f=sc.nextInt();  
        System.out.println("수학 :");  
        g=sc.nextInt();  
  
        float sum=a+b+c+d+e+f+g;  
        System.out.println("총점: "+sum+"평균: "+(sum/7));  
    }  
}
```
--- 
# Java 기본 문법

java는 위에서 설명했듯 명령어를 쓰는방법은 **파일경로를 일일히 다 적거나** 아님 파일을 import 해서 import한 파일내의 명령어들을 쓰는 방법이 있다. 

## 0. 시작함수
```java
public class Calculatar{ //클래스 선언
	public static void main(String[] args){
		//main(){ } 메인메서드 이런식으로 시작하는 자바 플로그램을 Java SE 프로그램이라한다.
	}
}
```
## 1. 변수, 자료형(데이터 타입)

### 변수, 자료형, 할당
**프로그래밍**에는 **3대 요소**가 있다.
변수, 자료형, 할당

**변수**
>데이터를 저장하는 데이터 공간의 이름
- `$`나 `_`이외 특수문자는 변수이름에 사용불가
- 숫자로 시작 불가
- 대소문자 구분
- 키워드(예약어)는 변수이름 불가

**자료형** 
>변수의 크기와 어떤 종류를의 데이터를 저장할것인지 결정하는것
- String (문자)
- int (정수)
	- long(8바이트 크기의 변수로 변수대입값 뒤에 `l`또는 `L`을 붙여줘야한다.)
- char (한글자)
- float (실수 뒤에 f붙여주기)
- double (긴실수)
- boolean (참 거짓)

**할당**
>변수에 데이터를 저장하는것
- 변수 초기화 : 변수 선언이후에 아무런값도 할당하지 않는다면 쓰래기값이 들어가있게 되는데 이를 방지하기위해 초기화가 필요하다.

### 변수 저장 과정
![[스크린샷 2024-11-11 235610.png]]
변수를 생성하면 symbol table에 Key-value형식으로 value에는 저장할 주소가 적혀있고 a에 뭔가 할당한다 하면 그 주소에 메모리에 값을 저장하게 된다.

[[2.객체 생성 (기본)]]
[[CLI]]
### String
`int`나 기본자료형의 경우에는 컴파일러가 오류를 발견할때 이미 가즈고있는 어휘이기 때문에 안걸리지만 `String`은 기본자료형이 아니기에 원래는 위에서 언급했듯 어디에 이 자료형이있는지 적어줘야 한다.(`java.lang.String`) 하지만 api의 위치를 먼저 컴파일러에게 알려줬기 때문에 String을 쓰면 자동으로 컴파일러가` java.lang.String`로 바꿔서 인식한다.

- 대소문자 아스키값 차이는 32다
## 2. 진수
자료형이란 메모리(바이트)의 크기를 지정하는 문법을 뜻한다.

- signed char 1바이트 양음수 따짐 -128~127 =char
- unsigned char 1바이트 양수 0~255
- signed short int 2바이트 양음수 2^15~-32768 = short
- unsigned short int 2바이트 양수 0~2^16 (65536) = unsigned short
- signed long int 4바이트 양음수 -2^31~2^31 = int
- unsigned long int 4바이트 양수 0~2^32 = unsigned int
- float 4바이트 실수 (6자리)
- double 8바이트 실수 (16자리)
- long double (30자리까지 가능 이론적이라고한다 실제로는 이정도는 아닌가보다.)

> 실수 기본형은 double형 이기때문에 float 형을 쓸때 value 값 뒤에 f 붙여줘야한다. 안된다면 lf붙여주자.

### 2.0 보수

이거 구하는법 알고있었는데 그냥 다까먹어버렸넹

### 2의보수

![[Pasted image 20241112005126.png]]  
_간편_

1. 뒤에서 처음만나는 1까지는 그냥적기
2. 나머지는 0과1을 반대로함  
    _계산_
3. 1의 보수 구하기
4. 거기에 1더하기

### 1의보수

![[Pasted image 20241112005111.png|700]]  
_간편_

1. 0과1을 뒤집기  
    _계산_
2. 구할 보수의 원래값의 자릿수만큼 1로 이루어진 것에 구할보수값 빼기

### 2-1.진수

10진수는 그냥  
8진수는 앞에 0 붙이기 017  
16잔수는 앞애0x붙이기 0x0F

## 형 변환
- 큰 타입을 작은걸로 바꿀때 문제가 되는데 그때 캐스팅 문법 즉 강제형변환을 해준다.

그 과정에서 당연하지만 데이터를 잃게 된다.
![[스크린샷 2024-11-12 003403.png]]
- 예시
- ![[스크린샷 2024-11-12 003601.png]]