# DataBase : 데이터의 저장소

## DBMS(DataBase Management System)
- 데이터 베이스를 운영하고 관리하는 소프트웨어


![image](https://github.com/user-attachments/assets/8af06f41-e1a5-41fa-962c-38099d73db8f)

# spring의 아키텍처

- **controller**로 요청이 들어오면 이 비지니스 로직을 처리하는 부분을 **service**라고 부른다
- 그리고 service는 **repository**라는 데이터 영역과 붙어있다


# @RequiredArgsConstructor
- 생성자 메소드로 채워주는 어노테이션
- 의존성 주입을 간소화하는 데 많이 사용
- 별도의 @Autowired 없이 생성자 주입을 사용할 수 있다

---
# @Bean과 @Autowired
- Spring Framework에서 의존성 주입을 처리하는데 중요한 어노테이션이다

## @Bean
- @Bean은 개발자가 직접 컨트롤할 수 있는 객체를 정의할 때 사용된다
- 즉, 해당 메서드에서 반환된 객체는 Spring의 컨테이너에 빈으로 등록되며, 다른 곳에서 사용할 수 있게 됩니다.

## @Autowired
- spring이 자동으로 빈을 주입할 수 있도록 해주는 어노테이션이다
- @Autowired가 붙어 있는 필드나 메서드가 있으면, Spring 컨테이너는 그에 맞는 빈을 찾아 자동으로 주입해준다

## @Bean VS @Autowired
- **@Bean** : Spring 컨터에너에 빈을 직접 등록할 때 사용
> 주로 개발자가 명시적으로 정의하는 메소드에서 사용됨

- **@Autowired** : Spring 컨테이너에서 관리하는 빈을 자동으로 주입할 때 사용
> 의존성을 자동으로 해결함