- 도커에 대한 설정 
```yaml
version : "3"  # 버전 
services:  
  db:  
    image: mysql:latest  #어떤 이미지를 사용 할것인지 
    restart: always  # 재시작 주기
    command:  
      - --lower_case_table_names=1  
      - --character-set-server=utf8mb4  
      - --collation-server=utf8mb4_unicode_ci  
    container_name: mysql2  
    ports:  
      - "3308:3306"  # 왼쪽 포트는 호스트의 포트, 오른쪽 포트는 컨테이너의 MySQL 포트입니다.  
    environment:  
      MYSQL_DATABASE: mydb   # 데이터 베이스 이름
      MYSQL_ROOT_PASSWORD: root1234   #데이터베이스 페스워드
      TZ: Asia/Seoul  #TimeZone
    volumes:   #폴더 동기화 (백업본 경로 설정)
      - /Users/choewonhyeong/Desktop/my_fucking_project/springproject/mysql:/var/lib/mysql
```