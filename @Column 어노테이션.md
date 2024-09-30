@Column 어노테이션으로 설정할 수 있는 속성
- name
- nullable
- unique
- length
- oclumnDefinition
- insertable, updatetable

## 언제 사용하는가?
- 필드명과 컬럼명이 다를 때,
	```
	@Column(name = "book_title")
private String title;

- nullable 여부를 설정할 때,
```
@Column(nullable = false)
```
- 길이 제한을 설정할 때,
```
@Column(length = 100)
```
- 유일성을 부여할 때,
```
@Column(unique = true)
```
- 컬럼 타입을 직접 정의할 때,
```
@Column(columnDefinition = "TEXT")
```