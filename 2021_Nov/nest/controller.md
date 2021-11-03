### Controller

```
nest g controller name
```

- 들어오는 요청 처리, 클라이언트에 응답 반환
- 애플리케이션에 대한 특정 요청 수신하는 역할
- 데코레이터를 통한 라우팅 세팅도 함 ( 요청을 해당 컨트롤러에 연결토록 )
- @Controller() 데코레이터 사용
- @Get, @Post 같은 HTTP 요청 메서드 데코레이터는 Nest에 HTTP 요청에 대한 특정 엔드포인트 핸들러 생성토록 지시
