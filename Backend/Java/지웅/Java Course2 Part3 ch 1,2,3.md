# 사용자 정의 자료형# 1. 자바에서 객체란??

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