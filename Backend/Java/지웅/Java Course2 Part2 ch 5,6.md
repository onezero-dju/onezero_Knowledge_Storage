# 1. 객체와 클래스의 등장
``
자료형에는 두 가지 종류가 있다 이전 내용에서는[[Java Course2 Part2 ch 2,3,4]] PDT기본 자료형에 대하여 다루었고 이번 시간부터는 ==**UDDT사용자 정의 자료형**==에 대하여 배울 것이다.
사용자 정의 자료형에서 객체와 클래스라는 개념이 나온다.
``
- **프리미티브 타입 데이터** : short,int,char,boolean,float,double/값을 하나의 데이터 타입에 대입해서 사용하는 형태
- **레퍼런스 타입 데이터** : 뜻처럼 참조 데이터라는 뜻으로 사용자 정의 변수(객체)가 이에 해당한다.
- ==**객체지향프로그래밍이 뭔가요??**== : 새로운 자료형을 만들어서 쓸 수 있는 언어, 클래스(객체) 단위로 프로그래밍 하는 것
``
>예시를 들어보자..
>책이라는 데이터 변수를 1개의 변수로 표현 가능한가요??
>>no
>책이라는 데이터를 변수 5개로 표현할 수 있나요?
>>이름 저자 출판사 표지 가격 = yes


| hello | 장지웅 | 한빛출판사 | img | 23000 |
| ----- | --- | ----- | --- | ----- |
| 칼의노래  | 김훈  | 미디어~  | img | 10000 |
위와 같은 구조의 데이터 타입이 **객체**이다. 
- **클래스(class)** : 새로운 자료형을 만들고, 설계하고, 모델링하는 도구

# 2. 새로운 자료형 생성하기

사용자 정의 자료형을 클래스를 이용하여 만들자.
```java
public class Book {  
    public String title;  
    public int Price;  
    public String Author;  
    public String company;  
    public int page;  
    public String isbn;       
}
```

- 객체 생성방법 : `Book b = new Book()` `new Book()` 에서 위에서 설정한 class대로 Book이라는 자료형을 생성한다. `Book b`에서 b라는 변수가 생성된 자료형을 가르키게 되면서 객체생성이 마무리되는것
- ![[Pasted image 20241118173322.png]]
- 사진처럼 Member m 변수가 선언되고 new Member()가 Member클래스를 객체로 생성 후에 그것의 주소를 m이 가리키는 식으로 객체가 생성되는 것이다. 

```java
public class BookExam {  
    public static void main(String[] args) {  
        Book b = new Book();  
        b.title="java";  
        b.Author="jiwoong";  
        b.company="한빛출판사";  
        b.isbn="1199110";  
        b.page=123;  
        b.Price=9900;  
        System.out.println(b.Author+" "+b.title+" "+b.company+" "+b.isbn+" "+b.page);  
    }  
}
```

# 실습 1 ch5 끝

>Q. 자신이 좋아하는 노래데이터를 저장하고 출력하십시오
- 조건
	- class로 music자료형을 모델링할 것
	- 자료형에는 제목, 가수, 작곡가, 공개일자, 곡 길이(초)가 포함될것
--- 
# 3. 데이터를 이동하는 배열

한 개의 데이터를 다루는 방법을 학습했었다. 이제부터는 여러개의 데이터를 다루는 ==**배열(array)**== 에 대하여 알아보자

- **배열은** 동일한 데이터 타입들을 여러개의 묶음으로 합쳐서 다루는 것을 배열이라한다.
- ![[Pasted image 20241118180053.png]]
- `[]`를 묶음기호라 한다`[]`가 하나만 있을때는 1차원 배열`[][]`처럼 2개면 2차원 배열이라 한다.
- java에서는 배열을 객체로 취급한다.
- ==`int[] a=new int[5]` 처럼 객체와 동일하게 생성한다==
- ![[Pasted image 20241118180801.png]]
- 배열 생성
```java
public class myclasstest {  
    public static void main(String[] args) {  
        int[] nums= new int[5];  
        nums[0]=1;  
        nums[1]=2;  
        nums[2]=3;  
        nums[3]=4;  
        nums[4]=5;  
  
        for(int i=0;i<nums.length;i++){  
            System.out.println(nums[i]);  
        }
        for (int data:nums){ //향상된 for문 위랑 같은 결과가 나온  
	    System.out.println(data);  
    }  
}
```
- 한번에 초기화 하는법
```java
public class Array {
	public static void main(String[] args){
		int[] a={10,10,10,10,10}; //자동으로 길이 설정됨
		for(int i =0;i<a.length;i++){
			System.out.println(a[i]);
		}
	}
}
```
# 실습 2 배열 초기화 연습

>Q. char[]배열에 'B' 'A' 'N' 'A' 'N' 'A' '1' '0'이라는 문자가 저장하고. 대문자로된 APPLE을 소문자 apple로 출력하시오
> - 힌트 대문자와 소문자의 아스키코드값을 차이는 32이다.

```java
char[] c ={'B','A','N','A','N','A','0','1'};
for (int i=0;i<i.length;i++){
	System.out.print((char)(c[i]+32));
}
System.out.println()
for (int i=0;i<i.length;i++){
    System.out.print((c[i]-'0'));
}
```
# 4. 기본배열과 객체배열

**기본배열**은 `int[],float[],char[]` 같은것들을 뜻하고 **객체배열**은 사용자 정의 자료형을 배열로 생성하는것을 뜻한다.

`Book[]b=new Book[3]`

위에처럼 적으면 ==객체배열==을 생성할 수 있다.
정확히 실체를 생성한건 아니고 실제 배열을 가르킬 주소칸 3칸을 선언해줬다고 보는것이 적절하다. 이를위해사
```java
public class MovieArrayTest {  
    public static void main(String[] args) {  
        Movie[] m=new Movie[3]; //변수 생성  
        m[0]=new Movie();  //실체 객체생성  
        m[0].title="죠스바";  
        m[0].year=2019;  
        m[0].director="장징중";  
          
        m[1]=new Movie();  // 생성  
        m[1].title="나 홀로 영화관에";  
        m[1].year=2019;  
        m[1].director="박찬욱";  
          
        m[2]=new Movie();  //생성  
        m[2].title="나는 모솔";  
        m[2].year=2019;  
        m[2].director="";  
        for (int i = 0; i < m.length; i++) {  
            System.out.println(m[i].title+" "+m[i].year+" "+m[i].director);  
        }  
    }  
}
```
주소가 가르키는 객체의 실체를 `new`를 이용하여 일일히 선언해줘야 한다.

# 5. 이미지를 표현하는 2차원 배열

**Pixcel** : 화소라고도 하며 이미지를 생성하기위한 최소단위를 뜻합니다.
`int[][]a=new int[행][열];`
ex) `int[][]a=new int[2][4];`

| a[0][0] | a[0][1] | a[0][2] | a[0][3] |
| ------- | ------- | ------- | ------- |
| a[1][0] | a[1][1] | a[1][2] | a[1][3] |
>서로 다른 크기의 배열 만들기
>![[Pasted image 20241119150453.png]]

# 실습 3 코드보고 틀린부분 지적

좋아하는 영화 3편을 출력하기위해 Movie클래스 생성후 main클래스에서 영화에대한 객체배열을 생성하고 저장&출력하는 코드이다 다음중 틀린부분은?
```java
public class Movie {  
    public String title;  
    public int year;  
    public String director;  
}
```
```java
public class MovieArrayTest {  
    public static void main(String[] args) {  
        Movie[] m=new Movie[3]; 
        m[1].title="버스운전사";  
        m[1].year=2018;  
        m[1].director="송찬의";  
  
        m[2].title="나 홀로 영화관에";  
        m[2].year=2009;  
        m[2].director="진민서";  
  
        m[3].title="어벤죠스";  
        m[3].year=2013;  
        m[3].director="류승원";  
        for (int i = 0; i < m.length; i++) {  
            System.out.println(m[i].title+" "+m[i].year+" "+m[i].director); 
        }  
    }  
}
```

**기본배열**은 `int[],float[],char[]` 같은것들을 뜻하고 **객체배열**은 사용자 정의 자료형을 배열로 생성하는것을 뜻한다.


---
ch 5 1,2 김영욱 - 새로운 변수의 필요성
ch 5 4, ch6 2 진민서 - 객체변수의 저장방법, 배열필요한 이유
ch 6 3,4 송찬의 - 배열생성방법, 반복문
나&혜성선배님 - 배열 초기화, 기본배열과 객체배열
ch  6 8,9 류승원 - 2차원 배열, 다차원 배열

시작전
- 질문많이 해주세요
	- 일영동아리 문화이다..
	- 뭔가 이상하거나 궁금한게 생긴다면 주저말고 편하게 질문하면 좋겠다.
