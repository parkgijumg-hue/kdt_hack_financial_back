# Backend

금융한걸음 서비스의 백엔드 서버입니다.

실제 송금 없이 계좌이체 과정을 연습할 수 있도록 가상 시나리오, 단계별 입력 검증, AI 튜터 안내와 학습 피드백을 제공합니다.

## 🛠 기술 스택

| 구분 | 기술 |
| --- | --- |
| **Backend** | Java, Spring |
| **Database** | MySQL |
| **API** | REST API |
| **AI** | 생성형 AI API, Step-aware Context, Structured Response |
| **안전 제어** | 입력 마스킹, 규칙 우선 검증, 고정 도움말 전환 |

## 📂 프로젝트 구조

```text
src/
├── main/
│   ├── java/
│   │   └── com/
│   │       └── financialstep/
│   │           ├── common/
│   │           │   ├── config/
│   │           │   ├── exception/
│   │           │   ├── response/
│   │           │   └── util/
│   │           └── domain/
│   │               ├── transfer/
│   │               │   ├── controller/
│   │               │   ├── service/
│   │               │   ├── repository/
│   │               │   └── dto/
│   │               ├── tutor/
│   │               │   ├── controller/
│   │               │   ├── service/
│   │               │   └── dto/
│   │               ├── scenario/
│   │               │   ├── controller/
│   │               │   ├── service/
│   │               │   ├── repository/
│   │               │   └── dto/
│   │               ├── learning/
│   │               │   ├── controller/
│   │               │   ├── service/
│   │               │   ├── repository/
│   │               │   └── dto/
│   │               └── member/
│   │                   ├── controller/
│   │                   ├── service/
│   │                   ├── repository/
│   │                   └── dto/
│   └── resources/
│       ├── application.yml
│       ├── application-local.yml
│       ├── application-test.yml
│       └── prompts/
└── test/
    └── java/
        └── com/
            └── financialstep/
```

## ⚙️ 주요 설정 파일

| 파일 | 설명 |
| --- | --- |
| `application.yml` | 애플리케이션 공통 설정 |
| `application-local.yml` | 로컬 DB와 외부 API 설정 |
| `application-test.yml` | 테스트 환경 설정 |
| `prompts/` | AI 튜터 프롬프트와 고정 도움말 관리 |

> `application-local.yml`과 API 키 등 민감정보가 포함된 파일은 Git에 올리지 않습니다.

## 🔐 금융·AI 안전 규칙

- 실제 계좌, 비밀번호, OTP, 주민등록번호를 수집하거나 저장하지 않습니다.
- 계좌이체 연습에는 교육용 가상 데이터만 사용합니다.
- 계좌 형식, 금액 범위, 진행 순서는 서버 규칙으로 검증합니다.
- AI에는 현재 단계와 필요한 최소 정보만 전달합니다.
- 규칙과 AI 응답이 충돌하면 서버 규칙을 우선합니다.
- AI 응답은 정해진 형식으로 검증한 후 사용자에게 전달합니다.
- AI 호출 실패 시 검증된 고정 도움말로 전환합니다.
- 개인정보와 계좌번호는 로그에 출력하지 않습니다.

## 📝 네이밍 규칙

### Java

- Controller: `TransferPracticeController`
- Service: `TransferPracticeService`
- Repository: `TransferPracticeRepository`
- Request: `TransferStartRequest`
- Response: `TransferResultResponse`
- Exception: `InvalidTransferStepException`

### API

- 리소스명은 복수형 명사를 사용합니다.
- URL에는 동사 대신 리소스명을 사용합니다.
- JSON 필드는 `camelCase`로 작성합니다.

```text
POST /api/practices
GET  /api/practices/{practiceId}
POST /api/practices/{practiceId}/steps
POST /api/tutor/guides
GET  /api/scenarios
```
