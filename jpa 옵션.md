`show-sql: true` : sql문이 실행될 때마다 로그를 출력
`format_sql: true` : sql문이 실행될 때마다 format형식을 출력

### hibernate 옵션
`ddl-auto: validation` : 내가 만든 Entity와 DataBase 컬럼 내용의 일치 여부 확인
`ddl-auto: create` : 내가 만든 Entity를 기반으로 DataBase에 table을 생성
`ddl-auto: create-drop` : 서버가 실행 될 때마다 table이 drop되고 create됨 (Memory DB와 유사)
`ddl-auto: update` : Entity와 DataBase를 비교하여 다른 내용은 DataBase에 업데이트

validation 옵션을 사용하여 Entity의 내용이 원격에 적용되지 않도록 하는 것이 좋음.
