# Spring Data JPA

### [[JDBC]] (Java DataBase Connectivity)
자바 언어로 데이터베이스 프로그래밍을 하기 위한 **라이브러리**


### [[JPA]]
JAVA ORM(Object Relation Mapping) 기술에 대한 **인터페이스**

ORM
	객체와 데이터베이스의 관계를 맵핑 하는 방법


데이터 베이스의 데이터와 객체 클래스에 맵핑을 해주는 기술에 대한 인터페이스가 JPA이다.


JPA의 인터페이스를 구현한 라이브러리
Hibernate 외에 EclipseLink, DataNucleus, OpenJPA, TopLink 등등 ...

Hibernate 외에 등등 어떠한 라이브러리를 써도 반복되는 작업의 발생
이를 편리하게 사용하고, Transaction 관리도 Spring에서 관리해주는 형태



>코드를 많이 치는 것이 어려우니 인터페이스(= JPA)를 만듬. 인터페이스를 통해 구현한 라이브러리가 Hibernate. 하지만 Hibernate에도 반복되는 코드가 있음. 그래서 transaction관리도 spring이 해주는 것이 Spring Data JPA


Application  <->  Spring Data JPA  -  JPA - Hibernate or etc ...  -  JDBC  <->  DB

jdbc에는 low한 쿼리문을 반환
이것을 구현하는것이 hibernate 라이브러리
hibernate 라이브러리와 다른 라이브러리를 포함한 것을 관리하는 것이 jpa
jpa와 라이브러리들을 묶어서 관리하는것이 spring data jpa




---


@Entity(name = "{테이블 명}")
	<클래스에 붙는 어노테이션>
	해당 어노테이션을 붙이면 테이블 명과 연결해주는 것이다.


JpaRepository 인터페이스는 사용하고자 하는 Repository 인터페이스에 상속되어야한다.
해당 인터페이스는 spring framework에서 추상화된 클래스를 작성하여 제공하는 인터페이스를 사용하기만 하면 된다.

장점 : 
이미 jpa에서 구현해둔 jpa repository를 상속 받는 것 만으로써 쿼리를 날리지 않아도 해당 내용을 찾아 올 수 있다.


```
@GetMapping("/{name}")  
public void autoSave(  
        @RequestParam String name  
) {  
    var user = UserEntity.builder()  
            .name(name)  
            .build();
    userRepository.save(user);
}

// user 라는 테이블에 name이라는 필드에 RequestParam으로 받은 name의 값을 넣어 build한 것
// user를 Repository에 저장
```
