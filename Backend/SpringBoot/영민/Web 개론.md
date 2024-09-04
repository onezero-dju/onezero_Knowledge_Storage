
# Web
(World Wide Web, WWW, W3)
인터넷에 연결된 컴퓨터를 통해 사람들이 정보를 공유할 수 있는 전 세계적인 **정보 공간**을 말한다.

- Web Site
	Ex ) Google, Naver, Daum ... etc

- [[User Interface]]를 통해 직접 인터넷에 있는 정보를 보기도 한다.
	Ex ) Chrome, Safari, Explorer, Smart Watch, IPTV ... etc

- API
	Web 서비스를 제공하기 위해 api를 개발한다.
	ex ) Kakao Open API, Google Open API, Naver Open API



## Web의 구성 요소
#### URL (Unifom Resource Identifier)
**리소스 식별자**
- 특정 사이트, 쇼핑 목록, 동영상 목록
모든 정보에 접근 할 수 있는 정보

한 개의 리소스에 접근할 수 있는 주소는 여러 개가 있을 수 있으나, 
하나의 주소로 여러 개의 리소스에 접근할 수 없다.

#### HTML (Hyper Text Markup Language)
하이퍼미디어 포멧
XML을 바탕으로한 범용 문서 포멧
Chrome, Safarim, Explorer에서 사용자가 알아보기 쉽게 변형

#### HTTP (Hypertext Transfer Protocol)
어플리케이션 컨트롤
프로토콜은 데이터를 주고 받을 때의 약속과 같음.


HTTP는 WEB에서 데이터를 주고 받는 프로토콜
HTML, XML, JSON, Image, Voice, Video, Javascript, PDF 등
특정한 데이터를 보내는 것이 통신이며, 보내주는 프로토콜이 HTTP


Client -- 요청 --> Server
Client <-- 응답-- Server
Server는 Client 요청에 대한 응답을 보내는 것


##### HTTP에 있는 여러가지 메소드
|         | 의미                 | CRUD  | 멱등성 | 안정성 | Path Variable | Query Parameter | DataBody |
| :------ | :----------------- | :---: | :-: | :-: | :-----------: | :-------------: | :------: |
| GET     | 리소스 취득             |   R   |  O  |  O  |       O       |        O        |    X     |
| POST    | 리소스 생성, 추가         |   C   |  X  |  X  |       O       |        △        |    O     |
| PUT     | 리소스 갱신, 생성         | C / U |  O  |  X  |       O       |        △        |    O     |
| DELETE  | 리소스 삭제             |   D   |  O  |  X  |       O       |        O        |    X     |
| HEAD    | 헤더 데이터 취득          |   -   |  O  |  O  |       -       |        -        |    -     |
| OPTIONS | 지원하는 메소드 취득        |   -   |  O  |  -  |       -       |        -        |    -     |
| TRACE   | 요청메시지 반환           |   -   |  O  |  -  |       -       |        -        |    -     |
| CONNECT | 프록시 동작의 터널 접속으로 변경 |   -   |  X  |  -  |       -       |        -        |    -     |

멱등성 : 서버에 여러 번 요청해도 항상 결과가 같으면 멱등하다
안정성 : 특정한 데이터에 요청했을 때, 데이터의 변화가 없어야한다.
[[Path Variable]]
[[Query Parameter]]
Data Body : http body에 실을 수 있는가


##### HTTP Status code
클라이언트(Client)가 서버(Server)에 요청을 했을 때, 응답에 대한 코드

|     | 의미        | 내용                                                 |
| --- | --------- | -------------------------------------------------- |
| 1XX | 처리중       | 처리가 계속 되고 있는 상태. 클라이언트는 요청을 계속 하거나 서버의 지시에 따라서 재요청 |
| 2XX | 성공        | 요청 성공                                              |
| 3XX | [[리다이렉트]] | 다른 리소스 리다이렉트. 해당 코드를 받았을때는 Response의 새로운 주소로 다시 요청 |
| 4XX | 클라이언트 에러  | 클라이언트의 요청에 에러가 있는 상태. 재전송하여도 에러가 해결되지 않는다.         |
| 5XX | 서버에러      | 서버 처리 중 에러가 발생한 상태. 재전송시 에러가 해결 되었을 수도 있다.         |



