# beforegoing-server

`beforegoing-server`는 사용자가 집을 나설 때 반복적인 시나리오를 준비하는 데 도움이 되는 스마트 체크리스트 애플리케이션을 위한 백엔드 서버입니다. 시나리오 관리, 미션 체크리스트, 시간 또는 위치 기반 알림과 같은 기능을 제공합니다. 또한 날씨 API와 통합하여 관련 정보를 제공합니다.

## 주요 기능

- **사용자 인증**: 카카오 및 Apple OAuth2를 사용한 소셜 로그인을 지원합니다. JWT를 통해 세션을 관리하여 인증합니다.
- **시나리오 관리**: 사용자는 "출근 전" 또는 "운동 전"과 같은 자신만의 시나리오를 생성, 업데이트 및 삭제할 수 있습니다.
- **미션 체크리스트**: 각 시나리오에는 완료 여부를 표시할 수 있는 '미션'(작업) 목록이 포함되어 있습니다.
- **알림**: 시나리오를 시간 기반 또는 위치 기반 알림에 연결하여 사용자에게 미리 알려줍니다.
- **날씨 정보 연동**: 기상청과 Open-Meteo에서 날씨 및 대기 질 데이터를 가져옵니다. 이 데이터는 사용자가 미션을 완료하는 데 도움이 되도록 제공됩니다(예: 비 예보 시 우산 챙기기 제안).

## 기술 스택

- **Backend**: Java 17, Spring Boot
- **Database**: MySQL, JPA (Hibernate), Flyway
- **Authentication**: Spring Security, JWT, OAuth2
- **Caching**: Redis
- **API**: RESTful API with OpenAPI/Swagger
- **External Communication**: OpenFeign
- **Monitoring**: Sentry

## 디렉터리 구조

```
.
├── src
│   ├── main
│   │   ├── java/com/und/server
│   │   │   ├── auth            # 인증 및 권한 부여
│   │   │   ├── member          # 사용자 관리
│   │   │   ├── scenario        # 시나리오 및 미션 관리
│   │   │   ├── notification    # 알림 관리
│   │   │   ├── weather         # 외부 날씨 API 연동
│   │   │   └── common          # 공통 유틸리티 및 예외 처리
│   │   └── resources
│   │       ├── application.yml # 메인 설정 파일
│   │       └── db/migration    # Flyway 데이터베이스 마이그레이션
│   └── test
│       └── java/com/und/server # 단위 및 통합 테스트
├── build.gradle                # 프로젝트 종속성 및 빌드 설정
└── Dockerfile                  # 애플리케이션의 Docker 이미지 빌드
```
