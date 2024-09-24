# docker-compose.yaml
- yaml 파일은 TAP으로 구분한다
```yaml
version: "3"
server: 
    db: 
        image: mysql:8.0.26
        restart: always
        command: 
            - --lower_case_table_name=1
            - --character_set-server=utf8mb4
            - --collation-server=utf8mb4_unicode_ci
        container_name: mysql
        ports: 
            - "3306:3306"
        environment:
            - MYSQL_DATABASE=데이터베이스 이름
            - MYSQL_ROOT_PASSWORD= 본인 비밀번호
            - TZ=Asia/Seoul
        volumes:
            - 저장할 공간의 주소

```

# 