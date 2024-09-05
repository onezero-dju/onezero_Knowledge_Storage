**Web개론**

**Web이란? (World Wide Web, WWW, W3)**

인터넷에 연결된 컴퓨터를 통해 사람들이 정보를 공유할 수 있는 전 세계적인
정보 공간을 말한다.

Web Site

User Interface

API(Application Programming Interface)

**HTTP (Hypertext Transfer Protocol)**

**어플리케이션 컨트롤**

+-----------------------------------+-----------------------------------+
| GET                               | OPTIONS                           |
|                                   |                                   |
| POST                              | HEAD                              |
|                                   |                                   |
| PUT                               | TRACE                             |
|                                   |                                   |
| DELETE                            | CONNECT                           |
+-----------------------------------+-----------------------------------+

RFC 2616에서 규정된 Web에서 데이터를 주고 받는 프로토콜

이름에는 하이퍼텍스트 전송용 프로토콜로 정의되어 있지만 실제로는 HTML,
XML, JSON, Image, Voice, Video, Javascript, PDF 등 다양한 컴퓨터에서
다룰 수 있는 것은 모두 전송할 수 있다

HTTP는 TCP를 기반으로 한 REST의 특징을 모두 구현하고 있는 Web기반의
프로토콜

![](media/image1.png){width="5.75in" height="3.4270833333333335in"}

  --------- ------------- -------- -------- -------- ---------- ----------- ----------
                의미        CRUD    멱등성   안전성     Path       Query     DataBody
                                                      Variable   Parameter  

  GET        리소스 취득     R        O        O         O           O          X

  POST       리소스 생성     C        X        X         O          ㅁ          O

  PUT       리소스 갱신,   C / U      O        X         O           △          O
                생성                                                        

  DELETE     리소스 삭제     D        O        X         O           O          X

  HEAD       헤더 데이터     \-       O        O         \-         \-          \-
                취득                                                        

  OPTIONS     지원하는       \-       O        \-        \-         \-          \-
             메소드 취득                                                    

  TRACE      요청메시지      \-       O        \-        \-         \-          \-
                반환                                                        

  CONNECT   프록시 동작의    \-       X        \-        \-         \-          \-
            터널 접속으로                                                   
                변경                                                        
  --------- ------------- -------- -------- -------- ---------- ----------- ----------

**URI (Uniform Resource Identifier)**

**리소스 식별자**

특정 사이트

특정 쇼핑 목록

동영상 목록

모든 정보에 접근 할 수 있는 정보

**HTML (Hyper Text Markup Language)**

**하이퍼미디어 포맷**

XML을 바탕으로한 범용 문서 포맷

이를 이용하여 Chrome, Safari, Explorer에서 사용자가 알아보기 쉬운 형태로
표현
