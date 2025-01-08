# 정보 은닉이란?

>다른객체에게 자신의 정보를 숨기고 자신의 동작, 기능, 연산만을 통해 접근을 허용하는 것으로, 클래스 외부에서 특정 정보에 접근을 막는다는 의미이다.

# `Getter Setter`메서드 만들기


`private`로 선언한다 하더라도 함수 내에서 자기 자신은 this로 접근 가능하다.

정보 은닉된 객체getter,setter사용
```java
public class PersonVO {
	private String name;
	private int age;
	private String phone;
	public void setName(String name){
		this.name=name;
	}
	public void setAge(int age){
		this.age=age;
	}
	public void setPhone(String phone){
		this.phone=phone	
	}
	public String getName(){
		return this.name;
	}
	public int getage(){
		return this.age;
	}
	public String getphone(){
		return this.phone;
	}
}
```

정보 불러오기
```java
PersonVO vo = new PersonVO();
vo.setName("홍길동");
vo.setAge(5000);
vo.setPhone("X");
```
# 생성자를 이용한 초기화

생성자 메서드를 이용하여 상태정보에 초기화 라는 방법으로 값을 집어넣을 수 있다

객체 모델링 중에 아무런 생성자 메서드를 안넣으면 기본으로 디폴드 생성자 함수를 만든다
```java
//없을경우 생성되는 디폴트 생성자 함수
public PersonVO{
}
```
객체가 생성됨과 동시에 객체에 상태 정보에다가 값을 넣는 작업을 생성자함수를 이용해 초기화라고 합니다.
```java
public class PersonVO {
	private String name;
	private int age;
	private String phone;
	
	public PersonVO(String _name,int _age,String _phone){
		this.name = _name;
		this.age = _age;
		this.phone = _phone;
	}

	public void setName(String name){
		this.name=name;
	}
	public void setAge(int age){
		this.age=age;
	}
	public void setPhone(String phone){
		this.phone=phone	
	}
	public String getName(){
		return this.name;
	}
	public int getage(){
		return this.age;
	}
	public String getphone(){
		return this.phone;
	}
}
```
사용법
```java
public class Main {  
    public static void main(String[] args) {  
	    //시작하자마자 초기화
        PersonVO vo = new PersonVO("홍길동",23,"X");
    }
}
```
# toString메서드로 객체값 출력하기

객체가 가즈고있는 상태값을 String형태로 출력시켜주는 메서드 toString 만들자.
```java
public String toString() {  
	return "PersonVO{" +  
		"name='" + name + '\'' +  
		", age=" + age +  
		", phone='" + phone + '\'' +  
		'}';  
}
```