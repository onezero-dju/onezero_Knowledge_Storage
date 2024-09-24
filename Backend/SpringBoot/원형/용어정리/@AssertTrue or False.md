별도의 로직을 적용시킬수 있음

```java
@AssertTrue(message = "name or nickname은 반드시 1개가 존재하야 합니다. ")
private boolean isNameCheck(){

	//별도의 로직
	if(Objects.nonNull(name)&& !name.isBlank()){
		return true;
	}
	if(Objects.nonNull(name)&& !nickname.isBlank()){
		return true;
	}
	return false;
}
```