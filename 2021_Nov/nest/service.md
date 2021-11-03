### Service

```
nest g service name
```

- 재사용성 때문에 대부분의 비즈니스 로직은 service에

- @Injectable 붙여줌으로서 provider로 지정해줌
- provider 는 종속성을 주입할 수 있게 해주는 것
- 객체는 서로 다양한 관계 만들 수 있으며 객체의 인스턴스 연결하는 기능을 대부분 Nest runtime에 위임
- controller 는 HTTP 요청을 처리하고 더 복잡한 작업을 provider 로 위임
- provider 는 모듈에서 provider로 선언된 일반 ts class

#### Dependency injection (종속성 주입)

- nest에서는 ts 기능 덕에 종속성이 유형별로 해결됨

```
constructor(private whateverService: WhateverService) {}
```
