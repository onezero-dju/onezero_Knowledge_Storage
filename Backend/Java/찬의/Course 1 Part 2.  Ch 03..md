프로그래밍의 3대 요소인 변수, 자료형, 할당
Variable : 데이터를 저장하는 메모리 공간의 이름(symbol)
DataType : 변수의 크기와 어떤 종류의 데이터를 저장할 것인지를 결정하는 것
Assign : 변수에 데이터를 저장하는 것

변수를 만들 때 고려되는 것?
-> 크기와 데이터의 종류

변수를 만들려면 (메모리에 기억공간을 만들려면)?
-> 선언 (declaration)을 해야한다.

자료형의 종류
기본자료형(Primitive DataType), 사용자정의자료형(User Define DataType)

Primitive Data Type : 프로그램에서 기본적으로 제공해주는 자료형
User Define DataType : 사용자가 만들어서 사용하는 자료형

정수, 실수, 문자, (참, 거짓) 의 4가지 기본 타입이 존재함

byte, short, int, long
1           2      4      8
float, double
4             8
char
2
boolean
1

Java는 long distance = 100000; 으로 초기화 하려고 하면
100000을 int로 읽기 때문에 21억까지 받을 수 있음
21억을 넘어가는 정수를 초기화에 사용하고 싶다면 100000L로 선언하여 long형이라는 것을 알려줘야 함

자동차 정보를 저장하기 위해서 8개의 독립적인 변수가 사용되었다? 바람직한가?