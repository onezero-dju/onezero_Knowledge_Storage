# application.properties
- spring project에 대한 여러가지 설정 값들을 지정하는 것이다
- 이것을 .yaml파일로 바꿔서 사용할 수도 있다

## .yaml파일 이란
- 특정한 키가 있고 들여쓰는 방식을 yaml방식이라고 한다

```yaml
spring:
  jpa:

    #애플리케이션 실행 중에 JPA가 실행하는 SQL 쿼리를 출력
    show-sql: true       

    properties:

      #SQL 쿼리 출력 시에 포맷팅을 적용해 읽기 쉽게 만들어준다
      format_sql: true       

      #Hibernate가 사용할 SQL Dialect을 지정
      dialect: org.hibernate.dialect.MySQL8Dialect   

    #Hibernate가 애플리케이션 실행 시 데이터베이스 스키마를 어떻게 다룰지 설정
    hibernate:
      ddl-auto: validate

  #1. jdbc:mysql://localhost:3306/user: 데이터베이스 서버가 localhost에서 구동 중이고, user라는 데이터베이스를 사용한다는 뜻이다
  #2. useSSL=false: SSL 사용을 비활성화한다.
  #3. useUnicode=true: 유니코드 지원을 활성화한다
  #4. allowPublicKeyRetrieval=true: MySQL 서버의 공개 키를 허용하여 보안상의 이유로 키를 수동으로 제공하지 않아도 되게 설정한다
  datasource:
    url: jdbc:mysql://localhost:3306/user?useSSL=false&useUnicode=true&allowPublicKeyRetrieval=true

    #MySQL 데이터베이스와 연결하기 위해 사용되는 JDBC 드라이버의 클래스
    driver-class-name: com.mysql.cj.jdbc.Driver

    #mysql 데이터베이스에 연결할 때 사용자 게정과 비밀번호를 지정함
    username: root
    password: root1234!!
```