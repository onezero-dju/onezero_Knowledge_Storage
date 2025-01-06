# 연산자와 명령문
## Scanner
> Q. 키보드로 부터 데이터를 입력받는 방법 실습
```java
Scanner scan = new Scanner (System.in);//스캐너 객체 생성
int num = scan.nextInt();//정수 입력
float num = scan.nextFloat();
double num = scan.nextDouble();
String str =scan.next();//문자열입력(공백 앞까지 입력 받음)
String str=scan.nextLine();//문자열 입력 (엔터까지 입력받음)
```
>위에서  첫줄에 `(System.in)`은 입력을 키보드(기본입력장치)로 입력받겠다고 선언하는거다.

# 대입, 관계 연산자
## 산술`+`,`-`,`*`,`/(몫)`,`%(나머지)


| 연산의 형태   | 결과  | 정수 예시             |
| -------- | --- | ----------------- |
| 정수형과 정수형 | 장수형 | 5/2 - 2           |
| 실수형과 실수형 | 실수형 | 5.0/2,0 - 실수형 2.5 |
| 정수형과 실수형 | 실수형 | 5/2.0 - 실수형 2,5   |

| 연산자 | 의미  | 정수 예시  | 실수예시                 |
| --- | --- | ------ | -------------------- |
| /   | 몫   | 11/4=2 | 11.0\4.0=2.75        |
| %   | 나머지 | 11%4=3 | 11.0%4.0= ==**오류**== |

## 나누기와 나머지 연산자의 활용 (정수의 자릿수 구하기)


| digit  | 3625        |
| ------ | ----------- |
| 일의 자릿수 | 3625%10     |
| 십의 자릿수 | 3625/10%10  |
| 백의 자릿수 | 3625/100%10 |
| 천의 자릿수 | 3625/1000   |

## 대입 `+=`,`-=`,`*=`,`%=`,`=`
대입연산자(=): 연산자 오른쪽 수식의 값을 왼쪽에 대입

>변수(L-Value)=수식(R-Value)

| 복합 대입 연산자 | 풀어쓰기  |
| --------- | ----- |
| a+=b      | a=a+b |
| a-=b      | a=a-b |
| a*=b      | a=a*b |
| a/=b      | a=a/b |
| a%=b      | a=a%b |

a변수 길이가 길어지면 불편하기 떄문에
# 논리사고 if swich for while

## if
```java
if (조건식){
	내용
}else{

}
```
if문안에 **조건식이 맞을경우** **괄호 안에 내용이 실행된**다는 의미이다. **틀릴경우에는 else 괄호안에 내용**이 실행된다.

## swich case
```java
String day = "Sunday";
swich(day){
	case "Sunday" :
	System.out.println("야구하기");
	break
	case "Monday" :
	case "Tuesday" :
	System.out.println("농구하기");
	break
	default:
		System.out.println("휴식");
}
```
break문이 중간중간 없다면은 Sunday가 조건이 걸렸을때 야구와 농구가 동시출력될것이다. 그래서 탈출하는 break가 필요하다.

## for while
```java
for (초기식;조건식;증감식){
	반복할 문장;
}
```
>조건식이 거짓일 경우에 탈출한다

```java
for (변수 : 컬랙션){
	반복할 문장;
}
```
>컬랙션 내에 문장들을 변수에 차래차래 집어넣고 수만큼 반복

```java
do{
	무조건 최소 한번은 실행할 문장
}
while(조건문);
```
>조건문이 참인동안 반복

# 매개변수 전달기법(Parameter passing)

- 메서드 설계할때 
```java
public static void maxmin(int a,int b){
	함수 내용;
}
```
>public static은 공개범위 즉 함수 접속범위 같은거고
>void쪽은 반환할 값 타입을 적는것 그리고 ()안에 있는것은 매개변수(parameter)를 뜻함
- 메서드의 오버로딩
```java
public int add (int a, int b){
	int sum = a+b;
	return sum;
}
```
```java
public int add (float a, float b){
	int sum = a+b;
	return sum;
}
```
```java
public int add (int a, int b,int c){
	int sum = a+b+c;
	return sum;
}
```
저런식으로 메서드의 이름이 같더라도 매개변수에 들어가는 값이 다르다면 같은 이름으로 가능하다.

- **정적 바인딩?** : 컴파일 시점에서 전부 무슨 함수가 호출되는지 전부 하나 하나 살펴보는것이 아닌 미리 어디 메서드로 호출될지 선택되는 것 (속도 향상)