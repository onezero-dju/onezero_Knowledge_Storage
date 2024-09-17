`@Builder`는 객체 생성 시 복잡한 생성자 대신 빌더 패턴을 사용하여 **더 유연하고 가독성 높은 코드**를 작성할 수 있게 해주는 Lombok의 어노테이션입니다. 이를 통해 필드의 순서나 필요 여부에 상관없이 객체를 쉽게 생성할 수 있습니다.


```
import lombok.Builder;
import lombok.ToString;

@Builder
@ToString
public class User {
    private String name;
    private int age;
    private String email;
}
```
이러한 방식으로 모델을 생성한다.


```
public class Main {
    public static void main(String[] args) {
        // 빌더를 이용해 User 객체 생성
        User user = User.builder()
                        .name("Alice")
                        .age(25)
                        .email("alice@example.com")
                        .build();  // 객체 생성 완료

        System.out.println(user);
    }
}
```
이러한 방식으로 builder 패턴을 사용하여 모델을 불러올 수 있다.

만약에 age와 같은 변수를 모델 생성 시 작성하지 않으면, 기본값이 설정된다.
