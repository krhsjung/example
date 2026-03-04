## Project Overview & Design Decisions (Example Project)

### Project Overview

- 본 프로젝트는 개인 프로젝트이지만, 실무 환경을 가정해 설계/구현/운영까지 경험하는 것을 목표로 했습니다.
- 한 줄 요약: Web/Mobile 환경 차이를 고려해 인증, 보안, 배포까지 설계한 서비스 구조

### 프로젝트 목적

- 단순 CRUD가 아닌 실제 운영 가능한 서비스 구조 설계
- Web과 Mobile 간 인증 방식 차이를 고려한 아키텍처 설계
- 배포, 보안, 확장성을 고려한 백엔드/인프라 경험 정리

### Git Repository

- Backend
  - NestJS: [https://github.com/krhsjung/example-nestjs](https://github.com/krhsjung/example-nestjs)
- Frontend (React)
  - [https://github.com/krhsjung/example-react](https://github.com/krhsjung/example-react)
- Mobile
  - Android: [https://github.com/krhsjung/example-android](https://github.com/krhsjung/example-android)
- Infra
  - Docker/Kubernetes 환경: [https://github.com/krhsjung/development-environment](https://github.com/krhsjung/development-environment)
  - Helm 배포 구성: [https://github.com/krhsjung/example-helm](https://github.com/krhsjung/example-helm)

### 전체 아키텍처 요약

#### 서비스 접근 흐름

- Reverse Proxy 기반 단일 진입점으로 인증/API 트래픽을 통제하는 구조입니다.
- 외부 요청은 Nginx를 통해서만 유입되고, API 처리는 내부 Kubernetes 네트워크에서만 수행됩니다.

#### 도메인 및 라우팅

- Base Domain: `https://hsjung.asuscomm.com`
- API Endpoint: `/example/nestjs/development/api`
- 요청 흐름: `HTTPS 443 -> Nginx -> NodePort (30000)`

#### 설계 포인트

- Reverse Proxy 기반 단일 진입점 유지
- Backend API 외부 직접 노출 방지
- 서비스 확장 시 Pod 수평 확장 고려

### Design Decisions Summary

- 본 프로젝트에서는 단순 구현이 아닌, 실제 서비스 운영을 전제로 한 의사결정을 기준으로 설계했습니다.
- **Web과 Mobile 인증 방식을 분리**
  - 브라우저와 모바일의 보안 정책 및 사용성 차이를 고려
  - Web은 Session + HttpOnly Cookie 기반으로 XSS 대응 강화
  - Mobile은 추후 JWT 기반 인증으로 분리 예정
- **Backend API를 외부에 직접 노출하지 않음**
  - Nginx를 단일 진입점으로 구성해 인증 및 API 트래픽 통제
  - 내부 Kubernetes 네트워크에서만 API 접근 허용
- **Kubernetes를 단일 노드 환경으로 시작**
  - 고가용성보다는 운영 환경 시뮬레이션과 구조 이해에 집중
  - 추후 클러스터 확장을 고려한 구조 설계
- **Redis를 캐시가 아닌 인증 인프라로 활용**
  - 세션 스토리지 및 토큰 관리 용도
  - Refresh Token 회전 및 토큰 무효화 확장 고려
- **Database를 Kubernetes 외부에 구성**
  - 데이터 안정성과 운영 리스크 최소화 목적
  - 컨테이너 재배포 시 데이터 유실 방지

## View Definition Guide (Example Project)

- 상세 뷰 가이드는 [Example_View_Definition_Guide.md](./Example_View_Definition_Guide.md) 참고
