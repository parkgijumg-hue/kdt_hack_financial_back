# AGENTS.md

현재 이 저장소는 금융한걸음 백엔드의 구조만 갖춘 초기 골격이며, 비즈니스 로직과 실행 가능한 API는 없습니다.

## 계층 책임

- Controller: HTTP 요청과 응답 경계만 담당하고 비즈니스 판단을 넣지 않습니다.
- Service: 도메인 흐름과 트랜잭션 경계를 담당하며, 구현체는 인터페이스 뒤에 둡니다.
- Mapper: MyBatis를 통한 DB 접근만 담당하고 도메인 판단을 넣지 않습니다.
- DTO: 계층 사이 데이터 전달에만 사용하고 엔티티나 설정 객체 역할을 섞지 않습니다.

의존성 주입은 생성자 주입을 기본으로 합니다.

## 향후 구현 순서

도메인 기능은 Controller -> Service Interface/ServiceImpl -> Mapper Interface -> DTO -> Mapper XML -> Test 순서로 추가합니다.

## 코드 규칙

- Java 17, Spring Framework 5.3.x, Spring Security 5.8.x, Tomcat 9의 `javax.*` 호환선을 유지합니다.
- 공통 설정을 변경할 때는 영향을 받는 도메인, XML 설정, 빌드 의존성을 먼저 확인합니다.
- 빈 패키지는 Java marker class 대신 `.gitkeep`으로 유지합니다.
- 테스트는 구현한 계층의 책임에 맞춰 추가합니다.

## 금지 규칙

- `SELECT *`를 사용하지 않습니다.
- 필드 주입을 사용하지 않습니다.
- `System.out`을 사용하지 않습니다.
- 비밀정보를 커밋하지 않습니다.
- 민감정보를 로그에 남기지 않습니다.
- Spring Boot, Spring 6, Spring Security 6, `jakarta.*`, Tomcat 10 이상으로 올리지 않습니다.

## 검증 명령

```sh
./gradlew dependencies --configuration runtimeClasspath
./gradlew compileJava
./gradlew war
```
