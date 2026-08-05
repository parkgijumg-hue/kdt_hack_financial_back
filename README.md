# 금융한걸음 백엔드

금융한걸음의 Java 17 기반 전통형 Spring MVC WAR 프로젝트 초기 골격입니다. 현재 저장소에는 설정과 빈 패키지 구조만 있으며, 실행 가능한 API와 비즈니스 로직은 아직 없습니다.

## 기술 스택

- Java 17
- Spring Framework 5.3.x, Spring MVC 5.3.x
- Spring Security 5.8.x
- MyBatis 3.5.x, MyBatis-Spring 2.1.x
- MySQL, Redis
- Gradle, WAR, Apache Tomcat 9
- Springfox 3.0.x
- Log4j2, log4jdbc
- JJWT 의존성 준비
- JUnit 5, Mockito

## 폴더 구조

- `src/main/java/com/financialstep/common`: 공통 설정과 향후 공통 패키지
- `src/main/java/com/financialstep/domain`: 도메인별 빈 계층 패키지
- `src/main/resources`: MyBatis, DB 연결, 로그 설정
- `src/main/webapp/WEB-INF`: Spring MVC XML 설정과 JSP 위치
- `src/test/java`: 향후 테스트 코드 위치
- `.github/ISSUE_TEMPLATE`: 이슈와 PR 템플릿

## 환경변수

- `DB_DRIVER_CLASS_NAME`
- `DB_URL`
- `DB_USERNAME`
- `DB_PASSWORD`
- `REDIS_HOST`
- `REDIS_PORT`

민감정보는 설정 파일에 직접 작성하지 않고 실행 환경에서 주입합니다.

## 빌드

```sh
./gradlew clean compileJava war
```

현재는 API, 인증 처리, SQL, 도메인 로직이 없는 빈 골격 상태입니다. 기능 구현 시 도메인별 계층과 테스트를 단계적으로 추가합니다.
