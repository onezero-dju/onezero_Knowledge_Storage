# Web개론

## Web이란? (World Wide Web, WWW, W3)

- 인터넷에 연결된 컴퓨터를 통해 사람들이 정보를 공유할 수 있는 전 세계적인 정보 공간을 말한다.
1. Web Site
2. User Interface
3. API (Application Programming Interface)

### HTTP (Hypertext Transfer Protocol)
1. HTTP는 RFC 2616에서 규정된 Web에서 데이터를 주고받는 프로토콜입니다. 
2. 이름에는 **하이퍼텍스트 전송용 프로토콜**로 정의되어 있지만, 실제로는 HTML, XML, JSON, 이미지, 음성, 비디오, JavaScript, PDF 등 
   다양한 컴퓨터에서 다룰 수 있는 것을 모두 전송할 수 있습니다.
3. HTTP는 TCP를 기반으로 한 REST의 특징을 모두 구현하고 있는 Web 기반의 프로토콜입니다.
![1280X1280](https://github.com/user-attachments/assets/7d000cbb-5ed8-480a-80c8-5675a3313a80)

### HTTP 메소드

| Method  | 의미                | CRUD | 멱등성 | 안전성 | Path Variable | Query Parameter | DataBody |
|---------|---------------------|------|--------|--------|---------------|-----------------|----------|
| **GET**    | 리소스 취득          | R    | O      | O      | O             | O               | X        |
| **POST**   | 리소스 생성          | C    | X      | X      | O             | ㅁ               | O        |
| **PUT**    | 리소스 갱신, 생성    | C / U| O      | X      | O             | △               | O        |
| **DELETE** | 리소스 삭제          | D    | O      | X      | O             | X               | X        |
| **HEAD**   | 헤더 데이터 취득     | -    | O      | O      | -             | -               | -        |
| **OPTIONS**| 지원하는 메소드 취득 | -    | O      | -      | -             | -               | -        |
| **TRACE**  | 요청 메시지 반환     | -    | O      | -      | -             | -               | -        |
| **CONNECT**| 프록시 동작의 터널 접속 변경 | - | X      | -      | -             | -               | -        |

### URI (Uniform Resource Identifier)
#### 리소스 식별자
- 특정 사이트
- 특정 쇼핑 목록
- 동영상 목록
- 모든 정보에 접근 할 수 있는 정보

### HTML (Hyper Text Markup Language)
#### 하이퍼미디어 포맷
- XML을 바탕으로 한 범용 문서 포맷
- 이를 이용하여 Chrome, Safari, Explorer에서 사용자가 알아보기 쉬운 형태로 표현된다.
