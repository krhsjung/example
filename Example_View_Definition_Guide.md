## View Definition Guide (Example Project)

### 1) 컬러 시스템 (Example UI v1)

#### 1.0 컬러 팔레트

Primary:

- `Core` `#1D3557` ↔ `#AFC7EA` - 핵심 제목/브랜드 인상
- `Base` `#F5F8FC` ↔ `#0F1726` - 앱 기본 배경

Secondary:

- `Surface` `#FFFFFF` ↔ `#1A2436` - 카드/패널
- `Surface Soft` `#EDF3FB` ↔ `#243146` - 보조 카드
- `Text` `#162338` ↔ `#E7EEFA` - 기본 텍스트
- `Text Muted` `#5F6F85` ↔ `#AAB8CC` - 보조 텍스트
- `Border` `#D4DEEC` ↔ `#30425E` - 경계/구분선
- `Accent` `#4A78B8` ↔ `#76A3E4` - 강조 포인트
- `Link` `#2E67B1` ↔ `#8BB6F2` - 링크/참조

Support:

- `Success` `#3F8A64` ↔ `#66C491` - 성공 상태
- `Warning` `#C3872C` ↔ `#E9B05A` - 경고 상태
- `Danger` `#C75B5B` ↔ `#EC8E8E` - 오류/위험 상태

Semantic:

- `On Core` `#FFFFFF` ↔ `#0F1726` - Core 배경 위 전경색
- `Success Surface` `#E9F6EF` ↔ `#1B3A2C` - 성공 배경
- `Warning Surface` `#FFF6E8` ↔ `#4B3A1E` - 경고 배경
- `Danger Surface` `#FDEEEE` ↔ `#4D2525` - 오류/위험 배경
- `Info Surface` `#EAF2FF` ↔ `#1E2E4B` - 안내 배경

Gradient Stops:

- `Gradient Page Start` `#F5F8FC` ↔ `#0F1726`
- `Gradient Page End` `#DCE8F8` ↔ `#1A2740`
- `Gradient Hero Start` `#EAF2FF` ↔ `#101C2D`
- `Gradient Hero Mid` `#D4E3F8` ↔ `#1B2B45`
- `Gradient Hero End` `#BDD5F4` ↔ `#243A5A`

주석:

- `↔` 왼쪽은 Light, 오른쪽은 Dark 값
- 컴포넌트에서는 HEX 직접 사용 대신 아래 UI/시맨틱 토큰으로 매핑해 사용

#### 1.1 배경 그라데이션 토큰

| 토큰 | 값 | 용도 |
| --- | --- | --- |
| `Gradient Page` | `$Gradient Page Start -> $Gradient Page End` | 전체 페이지 배경 |
| `Gradient Hero` | `$Gradient Hero Start -> $Gradient Hero Mid -> $Gradient Hero End` | 헤더/히어로 강조 영역 |
| `Gradient Surface` | `$Surface -> $Surface Soft` | 카드/패널의 약한 깊이 표현 |

원칙:

- 방향은 `135deg`로 통일
- 텍스트/아이콘에는 그라데이션을 사용하지 않고 단색만 사용
- 대비가 떨어지는 구간에서는 `Surface` 단색 배경으로 대체

#### 1.2 UI 모드 색상 토큰 매핑

- `View BG` -> `Base`
- `View Surface` -> `Surface`
- `View Surface Alt` -> `Surface Soft`
- `Text Primary` -> `Text`
- `Text Secondary` -> `Text Muted`
- `Border Default` -> `Border`
- `Accent` -> `Accent`
- `Link` -> `Link`

#### 1.3 Semantic 매핑

- `State Success` -> `Success` + `Success Surface`
- `State Warning` -> `Warning` + `Warning Surface`
- `State Danger` -> `Danger` + `Danger Surface`
- `State Info` -> `Accent` + `Info Surface`

### 2) 레이아웃 토큰 (Spacing / Radius / Shadow)

- `Space-1: 4`, `Space-2: 8`, `Space-3: 12`, `Space-4: 16`, `Space-6: 24`, `Space-8: 32`
- 카드/패널 기본 패딩: `16~24`
- 기본 Radius: `12`, 강조 카드 Radius: `16`
- 그림자는 약하게 1단만 사용하고, 상태 전달은 색상/텍스트로 해결한다.

### 3) 타이포/가독성 기준

- Heading은 2단계까지만 운영한다. (`H1`, `H2`)
- 본문 최소 `16px`, 보조 텍스트 최소 `13px`
- 숫자/지표/버전은 고정폭 계열 또는 동일 폭 느낌의 스타일을 사용한다.
- 한 문단은 3줄 내로 제한하고, 긴 설명은 목록으로 분해한다.

### 4) 핵심 컴포넌트 뷰 규칙

- `Architecture Card`: 구성요소, 책임, 연결 경계를 3블록으로 고정
- `Decision Block`: `문제 -> 선택 -> 근거 -> 트레이드오프` 4행 고정
- `Validation Block`: `검증 항목`, `방법`, `결과`, `리스크` 표 고정
- `Platform Compare Table`: Web/Mobile 행 비교 템플릿 고정

### 5) 인터랙션/모션 원칙

- 모션은 이해 보조 용도로만 사용한다.
- 섹션 진입 페이드/슬라이드(150~220ms) 이외의 과한 전환은 금지한다.
- 로딩 상태는 스켈레톤 우선, 스피너는 짧은 대기 구간에만 사용한다.

### 6) 반응형 기준 (Web 우선)

- Breakpoint: `Mobile (<=767)`, `Tablet (768~1199)`, `Desktop (>=1200)`
- Desktop에서는 2열까지 허용, Mobile에서는 단일 컬럼으로 강제한다.
- 모바일에서 표는 카드 스택으로 변환하고, 비교 항목 라벨을 유지한다.

### 7) 접근성/품질 기준

- 텍스트 대비는 WCAG AA 기준 이상 유지
- 포커스 표시를 제거하지 않는다.
- 색상만으로 상태를 전달하지 않고 아이콘/텍스트를 함께 사용한다.
- 최종 배포 전 체크리스트
  - 핵심 목적 30초 전달 가능 여부
  - 인증 차이 설명 2분 전달 가능 여부
  - 링크/다이어그램/표 간 정보 불일치 여부
