### main.ts

- 핵심기능 NestFactory 사용해 Nest 애플리케이션 인스턴스 생성하는 애플리케이션 엔트리 파일
- 애플리케이션을 부트스트랩하는 비동기 함수 포함됨
- HTTP 리스너를 시작하기만하면 애플리케이션이 인바운드 HTTP 요청 기다릴 수 있음

```
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  /** nest 애플리케이션 인스턴스 생성위한 핵심 NestFactory 클래스 사용
  *
  * create(): NestFactory가 제공하는 애플리케이션 인스턴스 생성할 수 있는 정적 메서드
  * INestApplication 인터페이스 충족하는 애플리케이션 객체 반환
  */

  await app.listen(3000);
}
bootstrap();

```
