# JDBC란?(Java DataBase Connectivity)
- 자바 언어로 데이터베이스 프로그래밍을 하기 위한 라이브러리

```query
String jdbcDriver = "com.mysql.jdbc.Driver";             //mysql 로드

//내가 연결하고 하는 데이터베이스
String jdbcUrl = "jdbc:mysql://localhost:3306/user?serverTimezone=Asia/Seoul"; 
try{
    Class.forName(jdbcDriver).newInstance();
    Connection con = DriverManager.getConnection(jdbcUrl,"root", "root123!@#");
    
    //커넥트
    Statement st = con.createStatement();

    //내가 질의하고자하는 query문 작성
    String sql = "SELECT * FROM user";

    //query문 실행
    ResultSet rs = st.executeQuery(sql);

    while (rs.next()) {
        String name = rs.getString(1);
        String age = rs.getString(2);
        String email = rs.getString(3);

        System.out.println(name + " " + age + " " + email);
    }

    rs.close();
    st.close();
    con.close();
    }catch (Exception e) {
        e.printStackTrace();
    }
```


# JPA란 JAVA ORM(Object Relational Mapping) 기술에 대한 인터페이스
- ORM : 객체와 데이터 베이스의 관계를 맵핑하는 방법

## EX)
```
public class User {
    private String name;
    private int age;
    private String email;
}
```

# JPA의 인터페이스를 구현한 라이브러리
- Hibernate 외에 EclipseLink, DataNucleus, OpenJPA, TopLink 등등등
```
public class User {
    private String name;
    private int age;
    private String email;
}

EntityManager entityManager = entityManager.getTransaction().begin();

var user = new User("홍길동",20,"hong@gmail.com);

entityManager.persist(user);
entityManager.getTransaction().commit();
entityManager.close();
```

## Hibernate 외에 등등 어떠한 라이브러리를 써도 반복되는 작업의 발생
- 이를 편리하게 사용하고, Transaction 관리도 Spring에서 관리해주는 형태

```
@Transactional
public User save(User user) {
    return userRepository.save(user);
}

@Transactional
@Override
public <S extends T> S save(S entity) {
    Assert.notNull(entity,"Entity must not be null");

    if(entityInformation.isNew(entity)) {
        em.persist(entity);
        return entity;
    }else {
        return em.merge(entity);
    }
}
```
![image](https://github.com/user-attachments/assets/d79868eb-6fc1-4405-9451-927e9a9f2605)

# Spring Data JPA
- 자동으로 Hibernate에서 query문을 만들어주고 이 query는 Spring JAP를 통해서 실행이 된다