# 사용자 정의 자료형

- **모델이란?** : class=model 클래스를 역할에 따라 부르는 이름을 모델이라고 부른다.
	- 역할에 따라 다양한 모델을 만들어 사용할수있다.

- **모델의 종류** : 
	- 시작 클래스 : main 클래스 (모델로 특별히 분류하지는 않는듯)
	- DTO,VO : 데이터를 담는 모델 (사용자 정의 자료형)
	- DAO : 데이터를 처리하는 모델 (데이터 베이스) CRUD
	- Utility : 도움을 주는 모델 (반복적 사용 기능을 편리하게사용하기위해 클래스로 만들어 논것) java.util

C언어 파이썬 등에서 부르는 함수 이것을 확장시킨것이 자바에서 객체이다 객체를 class 라고 부르는데 아래에서부터는 class라 부르겠다 자바기본제공자료형이 아닌 클래스로 만든 자료형을 레퍼런스 타입 이라하고 요런게
**프리미티브타입** : short, int, long, char, boolean, float, double / 값을 변수에 대입하여 사용하는 형태

Java는 시작했을때  
`public class (class이름){`
이런식으로 나오는데
위에 public 이나 class는 나중에설명하구

먼저기본으로알아야할것은 main 이다
```java
public class mapapi {  
    public static void main(String[] args) {
    }
}
```
>위에 보이듯이 public static void main(String[] args) { 이 부분이 바로 C++로 따지면 main 함수이다. 

그럼 새로 클래스를 만들자 

```java
public class Book {  
    public String title;  
    public int price;  
    public String company;  
    public String author;  
    public int page;  
    public String isbn;  
}
```
위에처럼 book 이라는 객체 자료형을 만들었는데 이는 

main이나 다른클래스에서 객체생성후 사용할수 있다. 

>main class 생성
```java
public class BookTest {  
    public static void main(String[] args) {
    book b = new book[4];
    }
}
```

>book 객체(b)에 새로운 자료형 넣기
```java
public class BookTest {  
    public static void main(String[] args) {
    book b = new book[4];
    b.title="솔챌하는법";
    b.int = 29000;
    b.company = "일영컴퍼니";
    }
}	
```

위와같이 자바는
1. 새로운 자료형을 정의
2. 정의된 자료형을 객체로 생성
3. 생성된 객체에 값을 넣을수있게됨

객체가 만들어지고 각 값을 초기화 해주는 법은 생성자 함수를 만들면 된다.
```java
public class Book {  
    public String title;  
    public int price;  
    public String company;  
    public String author;  
    public int page;  
    public String isbn;  
    public Book(){
    this.title=title
    
    }
}
public Book(){

}
```
![[Pasted image 20241203125610.png]]
# 객체 보안(접근제한)

- 접근제어자 : 
	- public : 모든 패키지에서 접근 가능
	- private : 모든 패키지에서 접근 불가(자기자신만 접근가능)
	- protrcted : 상속관계에서 하위클래스에서 상위클래스에 접근 가능
	- default : 동일한 패키지에서만 접근가능

- 패키지 : 
	- 패키지내에 클래스들은 기본적으로 서로 접근 가능하다. 
	- ![[Pasted image 20241203125610.png]]





실습 2. 몇년도 몇월을 입력받아서 그 날짜의 요일 출력하는 메서드 만들기
$$h = (q + \left\lfloor \frac{13(m + 1)}{5} \right\rfloor + K + \left\lfloor \frac{K}{4} \right\rfloor + \left\lfloor \frac{J}{4} \right\rfloor - 2 \times J) \mod 7$$
```java
int h = (date + ((13 * (month + 1)) / 5) + year + (year / 4) - (year / 100) + (year / 400)) % 7;
```

- 위에서 $⌊$ 요 기호는 **내림**을 나타내는 기호이다. 수학에서 "⌋"은 **소수점을 버리고 정수 부분만 남기는 내림**(floor)을 나타낸다. 즉, 어떤 실수나 숫자를 내림하여 정수로 만드는 연산을 의미함 
	- 예를 들어, 3.73.73.7을 내리면 333이 된다. −3.7-3.7−3.7을 내리면 −4-4−4가 된다. 이는 "내림" 또는 "버림(floor)" 연산이라고도 부른다.

- "mod"는 나머지 연산을 나타냅니다.

- h는 요일을 나타내는 값입니다. (0 = Saturday, 1 = Sunday, ..., 6 = Friday)
- q는 날짜 (일)
- m은 월 (3 = March, 4 = April, ..., 12 = December, January과 February은 13, 14로 취급)
- K는 년도의 100으로 나눈 나머지 (년 % 100)
- J는 년도를 100으로 나눈 몫 (년 // 100)
- **1월**과 **2월**은 **13월, 14월**로 취급합니다.

변수를 함수에서 호출할때 인자
호출되면 인수