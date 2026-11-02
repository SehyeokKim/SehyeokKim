<div align="center">

![header](./assets/header-v3.svg)

### 『 편향 없이 보고, 행동은 빠르게 』

*Unbiased view, bias for action.*

</div>

<br/>

## About Me

지켜보고 지켜주는 시스템을 만드는 개발자 김세혁입니다.

AWS 자산을 24시간 관제하는 플랫폼, LLM이 인프라를 건드리기 전에 거치는 가드레일, 실시간 CCTV 이상행동 탐지, 얼굴 데이터를 남기지 않는 성인 인증을 만들어 왔습니다. 모두 "믿고 맡길 수 있는 감시와 자동화"를 다룬 일이었습니다.

기술을 고를 때는 "다들 쓰니까"보다 "이 상황에서 이걸 왜 써야 하지?"를 먼저 묻습니다. 답은 오래 고민하지 않고 직접 만들어 보면서 확인합니다. 고른 이유는 ADR로 남기고 AI를 쓸 때도 이 기준을 따릅니다. AI로 속도를 내더라도 검증과 책임은 제가 집니다.

- 현재: 인공지능사관학교 7기 AI 보안(클라우드·인프라) 과정, AWS FinSecOps 플랫폼 Vigilantis 팀장(PM)
- 지원 분야: IT Ops / AI · Infra & DevSecOps
- 주력: Python(FastAPI) · AWS(Boto3) · Terraform · Docker · PostgreSQL · CI/CD · LangGraph · Next.js
- 연락처: kimseh0418@gmail.com
- 포트폴리오 사이트: [sehyeokkim.com](https://sehyeokkim.com)

<br/>

## Education & Certifications

| 구분 | 내용 | 기관 | 기간 / 취득일 |
|:---:|---|---|:---:|
| 학력 | 컴퓨터공학 학사 | 전남대학교 (여수캠퍼스) | 2020.03 - 2026.02 |
| 교육 | 인공지능사관학교 7기 AI 보안(클라우드 및 인프라) 과정 | 광주 인공지능사관학교 | 2026.05 - 수강 중 |
| 교육 | 침해사고 대응훈련: 악성 문서파일 분석(HWP, MS Office) | 한국인터넷진흥원(KISA) | 2025.08.04 - 08.17 |
| 교육 | 호남권 정보보호 특별과정 | 한국인터넷진흥원(KISA) | 2025.08.21 |
| 자격 | **AWS Certified AI Practitioner (AIF-C01)** | AWS | 2026.09.23 |
| 자격 | TRIZ 1수준 (창의적 문제해결) | 한국트리즈협회 | 2024.10.02 |

<br/>

## Projects

### [Vigilantis](https://github.com/ProjectVigilantis/vigilantis): AWS FinSecOps 자율 관제·조치 플랫폼 `2026.08 - 진행 중 · 4인 팀 팀장(PM) · Infra & DevSecOps + FE`

> AWS 자산과 보안 위협을 24시간 관제하고 AI가 제안한 조치를 4단계 가드레일로 검증한 뒤 원클릭으로 실행합니다. 실패하면 자동으로 원복합니다. 인공지능사관학교 팀 프로젝트로, 10/15에 MVP 마감 판정을 통과해 `v1.0.0`을 냈고 지금은 AWS Marketplace 기반 SaaS로 옮기는 중입니다.

- Boto3로 EC2·SG·NACL·EBS 조치 엔진을 만들었습니다. 조치 직전에 스펙을 JSON으로 백업한 뒤 2/2 Status Check를 지켜보다가 실패하면 원래대로 되돌립니다.
- 런북은 Action Whitelist에 등록된 10종(본편 7, 롤백 3)입니다. EC2 다운사이징과 원복, NACL 차단과 해제, 미사용 SG 삭제와 재생성, 미부착 EBS 삭제가 들어 있습니다. 여기에 EC2 격리·해제 경로(격리 전 SG·타겟 그룹 백업)를 더했습니다.
- 10/12부터 10/14까지 학원 AWS 계정에서 실 AWS 스모크(A1-A9)와 격리·해제 첫 검증을 돌렸습니다.
- 플랫폼 배포 스크립트를 직접 짰습니다. CloudFront, ALB, ECS Fargate, RDS를 태그로 찾아 멱등하게 세우고 내립니다. 앱은 장기 액세스 키 없이 역할 전환(AssumeRole + ExternalId)으로만 관제 대상 계정에 들어갑니다. SaaS 전환 뒤에는 플랫폼 계정과 고객 계정을 나눴습니다. `vigilantis.dev` 도메인을 붙이고 CloudFront에서 ALB까지 가는 구간도 HTTPS로 바꿨습니다.
- FE 담당이 빠진 뒤 Next.js 16 대시보드를 통째로 맡았습니다. mock 계층 1,762줄을 걷어내고 실제 API에 붙였습니다. 이후 `DESIGN.md`로 화면 규칙을 정해 고객 관리 화면, 랜딩·로그인, 처리방침·약관 화면까지 만들었습니다.
- CI는 LocalStack과 PostgreSQL 서비스 컨테이너 위에서 `test`·`web`·`ai-signature` 세 잡으로 돕니다. 최근 dev 기준 pytest 6,458개가 통과합니다. `.dockerignore` 하나로 빌드 컨텍스트를 710MB에서 1.6MB로 줄였습니다.
- PR 140건을 올려 138건을 머지했고 팀원 PR 166건을 리뷰했습니다. 머지를 뺀 커밋은 216건입니다(2026-11-02, dev 기준). ADR은 12건 남겼습니다.
- `FastAPI` `Boto3` `PostgreSQL` `LangGraph` `OpenAI` `Next.js 16` `Docker` `LocalStack` `ECS Fargate` `CloudFront` `GitHub Actions`

### [AgeTrust](https://github.com/ZeroTurst-NoneBelieve/agetrust-backend): W3C DID/VC 기반 Zero-Trust 성인 인증 `2026.08 - 2026.10 · 4인 팀 PM · Backend`

> 얼굴 대조는 기기 안에서 끝내고 키오스크에는 DID/VC로 성인 여부만 증명하는 인증 플랫폼입니다. 서버에 얼굴 데이터를 남기지 않습니다. 10/29 시연을 마치고 종료했습니다.

- FastAPI 백엔드의 뼈대와 API 계약을 잡았습니다. API v1 라우팅, JWT 인증 미들웨어, 모델·스키마 계층, Alembic 마이그레이션을 구성했습니다.
- 해시체인 감사 로그 API를 만들었습니다. Outbox에서 Kafka로 가는 이벤트 파이프라인에는 실제 PostgreSQL로 검증하는 테스트를 붙였습니다. `verification_logs` 스키마는 nonce 해시와 키오스크 단위 UNIQUE를 넣어 다시 설계했습니다.
- 에러 응답의 `detail.code`를 통일하고 동시 가입 409 회귀 테스트를 넣었습니다. `constraints.txt`로는 전이 의존성을 고정했습니다. GitHub Actions CI와 ruff도 이때 들였습니다.
- PM으로서 ADR 16건 중 미결 8건을 정리하고 승인·CI·최신화를 강제하는 브랜치 룰셋을 운영했습니다. 전 레포에서 PR 29건 작성, 16건 리뷰, 이슈 44건, 커밋 126건입니다.
- `FastAPI` `PostgreSQL` `Alembic` `Kafka` `Docker` `W3C DID/VC` `Flutter`

### [sehyeokkim.com](https://github.com/SehyeokKim/sehyeokkim.com): AWS 서버리스로 직접 운영하는 이력서 사이트 `2026.10 · 개인 프로젝트`

> 이력서 사이트를 AWS 위에 직접 설계하고 배포해 10월에 마무리했습니다. 공개 이력서와, 저만 Google 로그인으로 들어가는 구직 공고 대시보드(`/private`)가 있습니다. ([sehyeokkim.com](https://sehyeokkim.com))

- CloudFront 하나 아래에 S3 정적 사이트(OAC)와 API Gateway → Lambda(FastAPI + Mangum) → DynamoDB를 함께 둬서 CORS 없이 httpOnly 쿠키로 인증합니다.
- 인프라는 전부 Terraform(S3 백엔드, `use_lockfile`)입니다. 관리 계정과 워크로드 계정을 나눴고 사람은 IAM Identity Center(SSO + MFA)로만 들어갑니다. IAM 사용자와 장기 액세스 키는 하나도 없습니다.
- GitHub Actions는 OIDC 임시 자격 증명으로 웹 파일만 배포합니다. 배포 역할은 `main`의 `production` 환경에서만 맡을 수 있고 버킷 쓰기와 CloudFront 무효화 말고는 권한이 없습니다. 인프라 변경은 PR에서 plan을 보고 제가 직접 적용합니다.
- 로그인은 Lambda가 Google OIDC를 직접 처리합니다. state·PKCE·nonce와 ID 토큰 서명을 확인한 뒤 허용한 계정 하나만 통과시킵니다. 비밀값은 SSM Parameter Store(SecureString)에 둡니다.
- 상시 과금 리소스 없이 온디맨드만 쓰고 AWS Budgets로 월 $5 예산 알림을 걸었습니다. 설계 결정은 ADR 5건으로 남겼습니다.
- `Terraform` `CloudFront` `S3` `Lambda` `API Gateway` `DynamoDB` `FastAPI` `Next.js` `GitHub Actions OIDC`

### [Model Registry API](https://github.com/SehyeokKim/model-registry-api): 멀티테넌트 AutoML 플랫폼의 모델 관리 API `2026.10 · 개인 프로젝트`

> AutoML 서비스를 가정했습니다. 고객이 데이터를 올려 학습시키고 버전 관리된 모델로 추론하는 서비스입니다. 그중 모델과 모델 버전의 생명주기를 맡는 API 서버를 만들었습니다. `docker compose up -d` 한 번이면 DB, 마이그레이션, API가 순서대로 뜹니다.

- 모델은 고객 조직이 소유합니다. 다른 조직의 모델은 있는지조차 드러내지 않도록 404로 답합니다. repository 함수는 `organization_id`를 필수로 받게 해서 조직 조건을 빠뜨릴 수 없게 했습니다.
- 동시성은 두 겹입니다. 모델 행을 `FOR NO KEY UPDATE`로 잠가 버전 번호가 빈틈이나 중복 없이 늘어나게 했습니다(동시 10건 → 1-10). `row_version` 기반 ETag와 `If-Match`로는 낡은 화면에서 저장하는 lost update를 막았습니다.
- 목록은 keyset 페이지네이션과 `LATERAL` 집계로 페이지에 든 모델만 계산합니다. 모델 2만 건, 버전 6만 건에서 `EXPLAIN ANALYZE`로 21행만 읽는 것(0.5ms)을 확인했습니다.
- 소프트 삭제와 복원 기한, 기한이 지난 모델의 영구 삭제 배치, 에러 코드 카탈로그, Kubernetes 참조 매니페스트까지 넣었습니다. 테스트는 실제 PostgreSQL 위에서 338개가 통과하고 ADR은 9건입니다.
- `FastAPI` `SQLAlchemy 2.1` `Alembic` `PostgreSQL 16` `Docker Compose` `Kubernetes` `GHCR`

### [Our Date Map](https://github.com/SehyeokKim/our-date-map): 커플 데이트 기록·계획 PWA `2026.07 - 운영 중 · 개인 프로젝트 · 풀스택`

> 지도에 추억을 핀으로 남기고 다음 데이트 코스를 짜며 Web Push로 서로를 부르는 커플용 PWA입니다. 기획부터 배포와 운영까지 혼자 했습니다. ([our-date-map.vercel.app](https://our-date-map.vercel.app))

- 모든 테이블이 `USING (true)`로 열려 있던 것을 발견해 나 또는 연결된 파트너만 읽는 `TO authenticated` RLS로 전부 바꿨습니다. 적용 전에 트랜잭션 안에서 역할별 조회 건수를 확인하고 ROLLBACK으로 되돌려 봤습니다.
- 커플 연결은 전역 고유 4자리 태그(#0000)로 요청, 수락, 해제합니다. 커플이 함께 쓰는 테마(색상 3 × 폰트 3)를 위해 모달 12종의 스타일을 토큰으로 묶었습니다.
- 데이트 코스는 구간마다 대중교통·자동차·도보 추천 경로 중 하나를 고릅니다. 10월에 대중교통 경로를 ODsay에서 카카오맵 API로 바꿨습니다. 계산한 경로는 플랜에 저장해 다시 열 때 API를 부르지 않습니다.
- Kakao OAuth, Service Worker Web Push(VAPID), 이미지 자동 압축(300KB), 스키마 마이그레이션 22건.
- 커밋 114건, 운영 배포는 시맨틱 버전 릴리스 30회(v1.0.0 - v1.26.1)로 정리했습니다.
- `Next.js 16` `React 19` `TypeScript` `Tailwind v4` `Supabase` `Vercel` `PWA`

### [Smart Doorlock CCTV](https://github.com/jnucpe20/server-public): AI 이상행동 탐지 도어락·CCTV `2025.03 - 2025.12 · 캡스톤 졸업작품 · 3인 팀 · 백엔드`

> 라즈베리파이 카메라 영상을 WebRTC로 실시간 스트리밍하고 X3D-M 모델이 폭행·납치 같은 이상행동을 잡아 바로 알립니다. 캡스톤 최종 평가 A+를 받았습니다.

- REST API, WebRTC(SRS), AI 분석기, MQTT 브로커가 Docker Compose 한 번으로 함께 뜨도록 서버를 구성했습니다.
- SWAG 리버스 프록시와 Let's Encrypt로 HTTPS를 붙였습니다. MQTT로 도어락을 원격 제어하고 FCM과 WebSocket으로 푸시를 보냅니다.
- `FastAPI` `WebRTC(SRS)` `MQTT` `Redis` `X3D-M` `Raspberry Pi` `Flutter`

<br/>

## AI Engineering: AI로 문제를 푸는 방식

> 모든 프로젝트를 AI 코딩 에이전트(주로 Claude Code)와 함께 만들었고 제품에도 AI를 넣었습니다.
> 저는 AI가 잘하는 일과 못하는 일을 나눠 맡기고 결과를 검증할 수 있게 구조를 짜는 데 신경을 씁니다.

### 핵심 역량

- AI 에이전트 오케스트레이션. 워크트리로 AI 세션을 격리해 여러 개를 동시에 돌렸습니다. 4인 팀 프로젝트에서 PR 140건과 커밋 216건(둘 다 팀 최다)을 처리했습니다.
- LLM 제품화. LangGraph, Structured Output, 4단계 가드레일을 묶어 LLM이 인프라를 건드려도 안전한 범위 안에서만 움직이게 설계했습니다.
- AI 워크플로 설계. 프로젝트마다 AI 작업 규약(`CLAUDE.md`)을 두고 명세를 먼저 씁니다. 위험한 작업 앞에는 승인 게이트를 두며 규약은 CI로 강제합니다.
- AI 결과물 검증. 재현 출력과 `파일:줄` 근거를 요구합니다. 테스트를 먼저 늘리고 모델은 실측으로 비교합니다.
- 자격. AWS Certified AI Practitioner (2026.09)

### 프로젝트별 활용 사례

#### Vigilantis: LLM이 AWS 인프라를 조작해도 안전하도록

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| LLM이 잘못된 조치를 제안하면 실제 인프라가 망가짐 | LangGraph FinOps·SecOps 그래프와 Pydantic Structured Output 위에 ① 입력 검증 → ② Action Whitelist → ③ ARN Match → ④ AWS Dry-Run 가드레일을 둠. 실행이 실패해도 스펙 JSON 백업으로 자동 롤백 | LLM은 허용된 조치와 대상만 실행할 수 있음. 실행·롤백 엔진과 Dry-Run precheck 10종을 직접 구현 |
| 어떤 모델을 써야 할지 근거가 없음 | 팀 AI 담당과 14개 모델·파라미터 조합을 3라운드에 걸쳐 1,824회 실측 비교. LLM-judge·factcheck 평가 하네스 운영 | 확정 600회에서 환각 0건, 경쟁 모델보다 비용 1/9, SecOps 기준선 21 PASS / 0 FAIL |
| 다운사이징 목표 타입(`target_instance_type`)이 모든 모델에서 흔들림 | 이 필드를 AI 출력에서 빼고 서버 규칙으로 계산하게 바꿈(#345) | "AI는 추정, 서버는 계산"으로 정리. 절감액 기능도 AI는 단가만 추정하게 설계 |
| FE 담당 이탈로 대시보드가 비어 버림 | AI 에이전트와 함께 Next.js 16 FE를 인수해 mock 계층 1,762줄을 걷어내고 실제 API에 연결 | 범위를 줄이지 않고 일정 유지. SaaS 전환 화면(고객 관리, 랜딩·로그인)까지 이어서 담당 |
| 한 폴더에서 AI 세션 여러 개가 checkout을 서로 덮어씀 | "세션 1 = worktree 1 = 브랜치 1 = 이슈 1"로 정하고 워크트리 관리 스크립트(378줄)를 작성. 슬롯마다 포트를 나눠 전용 Docker 스택을 띄우고 리뷰용 워크트리는 따로 둠 | FE·INFRA·리뷰를 AI 세션 3개로 동시에 진행 |
| 팀원마다 AI가 다른 스타일로 코드를 씀 | 팀 공유 `CLAUDE.md`(브랜치·커밋·PR·리뷰 규약)와 개인 `CLAUDE.local.md`를 분리. AI 커밋의 신원과 서명 문구를 검사하는 CI `ai-signature` 잡 추가(#340, #403) | AI를 쓰든 안 쓰든 같은 규약, 같은 책임자로 이력이 남음 |
| 팀원 PR 166건을 혼자 리뷰해야 함 | AI가 리뷰 초안과 이슈 CLOSE 추천까지 쓰고 승인·종료·주차 판정은 PM이 직접 확정. 유료 LLM 호출은 규모를 먼저 추정하고 승인 | 리뷰 속도는 AI가 올리고 최종 판단은 사람이 내림 |

#### AgeTrust: AI가 만든 결과물을 믿을 수 있게

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| AI가 "통과했다", "문제없다"고 해도 실제와 다를 수 있음 | AI의 모든 주장에 재현 출력이나 `파일:줄` 근거를 붙이도록 작업 규약에 적고 리뷰는 결론 먼저, 근거 다음 순서로 고정 | 문서의 코드 인용을 실제 소스와 대조해 인용 오류 2건을 머지 전에 잡음(docs PR #5) |
| CI는 초록불인데 E2E가 조용히 skip됨. 빈 DB로 마이그레이션 왕복만 해서는 검증이 안 됨 | 직접 확인한 함정을 AI 규약 문서에 교훈으로 쌓아 다음 세션이 같은 실수를 하지 않게 함 | Outbox를 실제 PostgreSQL로 검증하는 테스트(#54), 동시 가입 회귀 테스트(#57) 추가 |
| (제품) 얼굴 데이터를 서버에 남기면 안 됨 | 팀에서 온디바이스 얼굴 임베딩(SFace INT8 ONNX)으로 설계하고 서버에는 판정 결과와 해시체인 감사 로그만 저장 | 개인정보를 저장하지 않는 구조. 백엔드는 해시체인 감사 로그 API로 무결성을 보장(#26) |

#### Model Registry API: AI가 짠 코드를 그대로 믿지 않기

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| 짧은 기간에 낯선 도메인(AutoML 모델 관리)을 설계해야 함 | 작업 전에 `CLAUDE.md`, `CONTRIBUTING.md`, 초기 ADR로 규칙을 먼저 고정하고 기능마다 "계획 → 승인 → 구현 → 검증 → CI → 머지 승인" 순서로 진행. 머지는 항상 직접 승인 | ADR 9건, 테스트 338개 |
| 테스트가 통과해도 그 테스트가 정말 무언가를 막는지 알 수 없음 | 지연 로딩 금지나 `SKIP LOCKED` 같은 핵심 장치를 일부러 빼고 돌려 해당 테스트가 실패하는지 확인(변이 확인) | 실패할 때 테스트가 멈춰 버리는 구조를 찾아 고침 |
| AI가 범위를 넓히자고 하면 그대로 따라가기 쉬움 | Kubernetes 매니페스트 추가처럼 범위가 커지는 결정은 다른 AI 에이전트에게 반대 입장 검토를 맡기고 그 근거를 ADR 원문과 대조 | 마이그레이션 Job 실행 순서, 계정 분리, 매니페스트와 앱의 불일치 위험을 매니페스트와 테스트에 반영 |
| AI가 구현 중에 계획에 없던 문제를 찾음 | 근거와 함께 보고하게 하고 동작이 바뀌는 수정은 승인한 뒤에만 반영 | 목록 집계가 조직 전체 버전을 읽던 문제, 쓰지 않는 스키마 문서까지 읽던 문제를 고침 |

#### Our Date Map: AI 에이전트와 혼자 풀스택 개발·운영

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| 혼자서 기획, FE, BE, DB, 배포를 다 해야 함 | Claude Code를 주 개발 도구로 쓰고 큰 작업은 `tasks/task-XX.md`에 명세를 쓰고 → 구현하고 → 요약하는 순서로 AI에 맡김 | 7월부터 10월까지 운영 배포 30회(v1.0.0 - v1.26.1) |
| Next.js 16이 AI 학습 데이터보다 새로워 AI가 옛 API로 코드를 씀 | 규약에 "작업 전에 `node_modules/next/dist/docs/`부터 읽을 것"을 넣어 최신 공식 문서를 근거로 쓰게 함 | 최신 API 기준으로 구현 |
| AI가 운영 DB나 배포를 잘못 건드리면 되돌리기 어려움 | `!DB`(마이그레이션·RLS), `!main`(배포), `!explain`(설명만) 명령 플래그로 권한을 나누고 기존 행 수정·삭제는 금지 | RLS 전면 교체도 트랜잭션 + ROLLBACK으로 역할별 조회 건수를 먼저 확인하고 적용 |
| 외부 API 쿼터(당시 ODsay 하루 1,000회) 초과 위험 | AI와 호출 경로를 분석해 경유지가 바뀔 때만 부르고 구간 경로를 재사용하게 설계. 실패 응답을 1시간 캐시하던 버그도 찾아 고침 | 쿼터 소진 위험 해소. 카카오맵으로 바꾼 뒤에도 저장 경로 재사용과 2초 지연 조회로 호출을 줄임 |
| `main` checkout 때 로컬 전용 AI 설정 파일이 지워지는 사고 | 원인을 찾고 "`main` checkout 금지, 배포는 `git push origin dev:main`으로만" 규칙을 적음 | 같은 사고 재발 없음 |

#### Smart Doorlock CCTV: 실시간 영상 AI를 서비스로

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| I3D 모델은 64프레임 입력이라 실시간 처리가 어려움 | 팀에서 X3D-M(16프레임)으로 바꿔 파인튜닝하고 16프레임 슬라이딩 윈도우와 임계값 0.7로 폭행·납치 등 위협 클래스 5개를 탐지 | 탐지 결과를 이벤트 API, 전후 15초 영상 클립, FCM 푸시로 연결 |
| 모델을 바꿀 때 라벨이 뒤바뀐 채 조용히 돌아갈 위험 | 클래스 이름을 체크포인트의 `class_to_idx`에서 읽고 모델이 없거나 구조가 다르면 기동 자체를 실패시킴(fail-fast) | 잘못된 가중치로 탐지가 실패하는데도 모르는 상황을 막음 |
| AI 분석기를 서버에 안정적으로 붙여야 함(백엔드 담당) | AI 분석기를 독립 컨테이너로 떼어 REST API, WebRTC(SRS), MQTT와 Docker Compose로 묶음 | 명령 한 번으로 전체 시스템 기동, 캡스톤 최종 평가 A+ |

#### 반복 업무 자동화

- 일일 업무일지. Claude Code 스킬을 만들었습니다. GitHub(커밋·PR·리뷰·이슈)와 Slack 활동을 모아 교육기관 양식(hwpx) 업무일지를 채웁니다.
- 기술 블로그 초안. Gemini API로 Velog 초안을 뽑는 CLI를 만들었습니다. 기존 글을 few-shot으로 넣어 문체와 구조를 맞추고 자기 글이 예시로 다시 섞이지 않도록 순환 참조를 막았습니다.
- Claude Code 플러그인 마켓플레이스. 제가 쓰는 플러그인을 fork해 한곳에 모으고 GitHub Actions가 매일 원본과 동기화하게 했습니다.

### 배운 점

1. AI에게 맡길 일과 맡기지 않을 일을 나눕니다. 재현성이 낮은 필드는 서버 규칙으로 옮겼고 금액처럼 틀리면 안 되는 값은 AI가 추정만 하고 계산은 서버가 하게 했습니다. AI 품질 문제 상당수는 프롬프트를 다듬을 때보다 역할을 나눌 때 풀렸습니다.
2. 1,824회 실측 비교로 모델을 골라 품질을 지키면서 비용을 1/9로 줄였습니다. 프롬프트도 스냅샷과 기준선으로 회귀를 관리합니다.
3. AI에게는 최신 근거를 줘야 합니다. 학습 데이터보다 새로운 프레임워크에서는 공식 문서를 먼저 읽게 한 것만으로 결과가 달라졌습니다.
4. 규칙은 문서로 적는 것만으로는 잘 안 지켜집니다. 사람도 AI도 잊어버리니까요. 명령 플래그, CI 잡, 워크트리 격리처럼 어기기 어려운 구조를 짜 두는 편이 효과가 있었습니다.
5. DB 변경, 배포, 과금, 이슈 종료처럼 되돌리기 어려운 작업은 사람이 엽니다. 명시적인 플래그와 제 승인이 있어야 실행됩니다.
6. 사고가 나면 규칙으로 남깁니다. AI 세션 충돌, 설정 파일 유실, 조용히 skip된 테스트를 겪을 때마다 AI 규약 문서에 교훈으로 적어 다음 세션이 같은 실수를 되풀이하지 않게 했습니다.
7. AI가 만든 결과물의 책임은 제게 있습니다. 빨리 만든 만큼 리뷰, 테스트, 근거 확인에 시간을 씁니다. Vigilantis에서 기능을 늘리는 동안 테스트도 6,458개까지 같이 늘었습니다.

<br/>

## How I Lead & Collaborate

팀장이라면 제가 코드를 잘 짜는 것보다 팀이 같은 기준으로 움직이게 하는 일이 먼저라고 생각합니다.

- 리뷰는 CODEOWNERS와 브랜치 룰셋으로 승인 리뷰와 CI 통과를 강제합니다. Vigilantis에서는 팀원 PR 166건을 직접 리뷰했습니다.
- 아키텍처 결정은 ADR(Vigilantis 12건)로, 진행 상황은 주 2회 갱신하는 `PROJECT_STATUS.md`(SSOT)로 남겨 "왜 이렇게 했는지"가 사라지지 않게 합니다. 주차마다 판정 기준을 미리 적어 두고 판정일에는 기준 문구를 고치지 않고 칸만 채웁니다.
- GitHub Actions CI(pytest, web, ai-signature)와 gitmoji + TYPE 커밋·브랜치 컨벤션을 설계해 운영합니다.
- docker-compose와 LocalStack으로 "내 컴퓨터에서만 되는" 문제를 없앴습니다.
- 팀원이 빠졌을 때 범위를 줄이지 않고 FE를 직접 넘겨받아 일정을 지켰습니다.

<br/>

## Tech Stack

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white"/>
  <img src="https://img.shields.io/badge/Terraform-844FBA?style=for-the-badge&logo=terraform&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white"/>
</p>
<p>
  <img src="https://img.shields.io/badge/LangGraph-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white"/>
  <img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white"/>
  <img src="https://img.shields.io/badge/Claude_Code-D97757?style=for-the-badge&logo=claude&logoColor=white"/>
</p>
<p>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white"/>
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white"/>
</p>

<br/>

![footer](./assets/footer.svg)
