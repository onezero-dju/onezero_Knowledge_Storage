# 사용자 정의 자료형

- **모델이란?** : class=model 클래스를 역할에 따라 부르는 이름을 모델이라고 부른다.
	- 역할에 따라 다양한 모델을 만들어 사용할수있다.

- **모델의 종류** : 
	- 시작 클래스 : main 클래스 (모델로 특별히 분류하지는 않는듯)
	- DTO,VO : 데이터를 담는 모델 (사용자 정의 자료형)
	- DAO : 데이터를 처리하는 모델 (데이터 베이스)
	- Utility : 도움을 주는 모델 (반복적 사용 기능을 편리하게사용하기위해 클래스로 만들어 논것)

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

객체에 저장된 값을 마음대로 바꾸면 곤란하기때문에 이를 방지하기위해 getter 와 setter를 쓰기 시작했음!! 

```java
public class book {  
    private int price;  
    private String title;  
    private String author;  
  
    public book(int price, String title, String author) {  
        this.price = price;  
        this.title = title;  
        this.author = author;  
    }  
  
    public String getTitle() {  
        return title;  
    }  
  
    public void setTitle(String title) {  
        this.title = title;  
    }  
  
    public int getPrice() {  
        return price;  
    }  
  
    public void setPrice(int price) {  
        this.price = price;  
    }  
  
    public String getAuthor() {  
        return author;  
    }  
  
    public void setAuthor(String author) {  
        this.author = author;  
    }  
  
    @Override  
    public String toString() {  
        return "book{" +  
                "price=" + price +  
                ", title='" + title + '\'' +  
                ", author='" + author + '\'' +  
                '}';  
    }  
}
```

위에 처럼 this 를 이용하여 `private`로 접근불가능하더라도 setter 를 이용하여 함수내에 포인터인 this. 를 이용해 private에 접근할수 있었다.



```java
public class main {  
    public static void main(String[] args) {  
        book BK =new book(23,"장","중");  
        System.out.println(BK.toString());  
    }  
}
```

> 실행시
> book{price=23, title='장', author='중'}