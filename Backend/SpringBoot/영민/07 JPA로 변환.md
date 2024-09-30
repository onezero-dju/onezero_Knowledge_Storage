# Memory DB를 MySQL로 변환
builder.gradle 파일에 JPA랑 MySQL 의존성(Dependencies)을 추가
```
dependencies {
	runtimeOnly 'com.mysql:mysql-connector-j'
	testImplementation 'org.springframework.boot:spring-boot-starter-test'
}
```

1. DataBase를 연결하기 위해 application.yaml 파일에 datasouce를 연결
	url에 주소와 DataBase이름을 작성

2. [[JPA 옵션]]
	`show-sql: true` : sql문이 실행될 때마다 로그를 출력
	`format_sql: true` : sql문이 실행될 때마다 format형식을 출력
	
	hibernate 옵션
		`ddl-auto: validation` : 내가 만든 Entity와 DataBase 컬럼 내용의 일치 여부 확인
		`ddl-auto: create` : 내가 만든 Entity를 기반으로 DataBase에 table을 생성
		`ddl-auto: create-drop` : 서버가 실행 될 때마다 table이 drop되고 create됨 (Memory DB와 유사)
		`ddl-auto: update` : Entity와 DataBase를 비교하여 다른 내용은 DataBase에 업데이트
	
	validation 옵션을 사용하여 Entity의 내용이 원격에 적용되지 않도록 하는 것이 좋음.


Repository 변경 사항
1. 기존 Memory DB에서는 SimpleRepository의 내용을 상속 받고 있었지만, JPA가 제공해주는 JpaRepository를 상속 받아 쉽게 관리한다.
2. Repository는 class가 아닌 interface로 설정한다.
3. JpaRepository를 상속 받고 있기에 어노테이션을 따로 달지 않아도 Spring에서 매칭해준다.

Entity 변경 사항
1. `@Entity(name = "book")` 어노테이션을 통해 Mapping 하고자 하는 Table의 이름으로 연결
2. Entity 어노테이션이 붙어있는 class는 `@Id`와 `@GeneratedValue(strategy = GenerationType.IDENTITY)` 어노테이션이 붙은 DataBase의 PrimaryKey에 해당되는 이름의 변수를 작성해줘야한다.
	ex) private Long id;
*(GeneratedValue는 해당 값을 어떻게 관리하는지 작성해야하는 어노테이션이다. MySQL은 보통 IDENTITY의 방식으로 관리한다.)*



---

Query문을 직접 return 해주는 것이 아니라 Method의 형태로 Query문이 반환 될 수 있도록 Method로 실행하는 것이 간단하다.


*([Query Method의 본문](https://docs.spring.io/spring-data/jpa/reference/jpa/query-methods.html) 참고)*
`findAllByScoreGreaterThanEqual()` 
By를 넣는 이유는 By를 기준으로 왼쪽은 메서드명(findAll = 모두 찾겠다.) / 오른쪽은 쿼리문에 해당된다.


`findAllByScoreGreaterThanEqualAndScoreLessThanEqual()`
keyword : `findAll` , `GreaterThanEqual`, `LessThanEqual`

### Native Query
Query 형식의 메서드를 만들어도 되지만 실행되는 기능이 많거나 복잡한 Query문 같은 경우에는 메서드 호출이 어려워진다. 그래서 어노테이션으로 지정해 줄 수 있다.

```
@Query(
	"select u from user u where u.score >= ?1 AND u.score <= ?2"
)
List<UserEntity> score(  
        int min, int max  
);
```

매게변수의 네이밍 바인딩을 할 수 있음.
```
@Query(  
        value = "select * from user u where u.score >= :min AND u.score <= :max",  
        nativeQuery = true  
)  
List<UserEntity> score(  
        @Param(value = "min") int min,  
        @Param(value = "max") int max  
);
```




### 강사님이 가장 추천하는 방법
가능하면, Query Method를 사용하는 것.
부득이하게 복잡한 Query를 사용해야하는 경우에는 Native Query를 사용
Native Query를 사용할 때, 손이 좀 가더라고 Parameter Binding을 해주는 것이 좋다.
