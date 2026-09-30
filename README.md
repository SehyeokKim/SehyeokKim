<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=0:000000,100:1c2833&height=200&section=header&text=Sehyeok%20Kim&fontSize=48&fontColor=ffffff&desc=Infra%20%26%20DevSecOps%20%C2%B7%20IT%20Ops%20%2F%20AI&descSize=18&descAlignY=75&animation=fadeIn)

### 『 아무도 보지 않을 때에도, 누군가 보고 있는 것처럼 당당하게 행동한다 』

*Integrity is doing the right thing, even when no one is watching.*

</div>

<br/>

## 👋 About Me

**"지켜보고, 지켜주는 시스템"** 을 만드는 개발자 김세혁입니다.

24/7 클라우드 관제, AI 가드레일, 실시간 CCTV 감시, Zero-Trust 인증 —
제가 만들어온 프로젝트는 모두 *신뢰할 수 있는 감시와 자동화*라는 하나의 주제로 이어집니다.
좌우명 그대로, 보는 사람이 없어도 스스로 떳떳한 코드와 기록(문서·리뷰·CI)을 남기는 것을 원칙으로 합니다.
AI 역시 같은 원칙으로 씁니다 — **AI는 빠르게 만들고, 검증과 책임은 사람이 집니다.**

- 🔭 **현재**: 인공지능사관학교 7기 AI 보안(클라우드·인프라) 과정 · AWS FinSecOps 플랫폼 **Vigilantis** 팀장(PM)
- 🎯 **지원 분야**: IT Ops / AI · Infra & DevSecOps
- 🛠️ **주력**: Python(FastAPI) · AWS(Boto3) · Docker · PostgreSQL · CI/CD · LangGraph · Next.js
- 📫 **Contact**: kimseh0418@gmail.com

<br/>

## 🎓 Education & Certifications

| 구분 | 내용 | 기관 | 기간 / 취득일 |
|:---:|---|---|:---:|
| 학력 | 컴퓨터공학 학사 | 전남대학교 (여수캠퍼스) | 2020.03 – 2026.03 |
| 교육 | 인공지능사관학교 7기 – AI 보안(클라우드 및 인프라) 과정 | 광주 인공지능사관학교 | 2026.05 – 수강 중 |
| 교육 | 침해사고 대응훈련 – 악성 문서파일 분석(HWP, MS Office) | 한국인터넷진흥원(KISA) | 2025.08.04 – 08.17 |
| 교육 | 호남권 정보보호 특별과정 | 한국인터넷진흥원(KISA) | 2025.08.21 |
| 자격 | **AWS Certified AI Practitioner (AIF-C01)** | AWS | 2026.09.23 |
| 자격 | TRIZ 1수준 (창의적 문제해결) | 한국트리즈협회 | 2024.10.02 |

<br/>

## 🚀 Projects

### 🛡️ [Vigilantis](https://github.com/ProjectVigilantis/vigilantis) — AWS FinSecOps 자율 관제·조치 플랫폼 `2026.08 – 진행 중 · 팀장(PM) · Infra & DevSecOps + FE`

> 24/7 AWS 자산·보안 상시 관제 + **4단계 AI 가드레일** 기반 원클릭 자율 조치 + **자동 롤백(Auto-Rollback)** 플랫폼 (인공지능사관학교 팀 프로젝트)

- **실행·롤백 엔진**: Boto3 기반 EC2·SG·NACL·EBS 조치 직전 스펙 JSON 백업 → 2/2 Status Check 감시 → 실패 시 자동 원복
- **런북 10종**(본편 7 + 롤백 3): EC2 다운사이징/원복, NACL 차단/해제, 미사용 SG 삭제/재생성, 미부착 EBS 삭제 — Action Whitelist 기반
- **실시간 관제 대시보드**: FE 담당 이탈 후 범위 축소 없이 **Next.js 16 FE 전부 인수** — mock 계층(1,762줄) 폐기 후 실 API 연결, 자산 토폴로지·위협 공격 경로·메트릭 추이 차트
- **Infra/CI**: LocalStack·PostgreSQL 서비스 컨테이너 CI, GitHub Actions 3잡(`test`·`web`·`ai-signature`), `.dockerignore`로 빌드 컨텍스트 **710MB → 1.6MB**, Dependabot 경보 15건 해소
- **규모**: PR **113건 작성(109건 머지) · 98건 리뷰**, 커밋 152건(머지 제외) — 모두 팀 최다, CI 테스트 **2,754 passed**, ADR 9건 운영
- `FastAPI` `Boto3` `PostgreSQL` `LangGraph` `OpenAI` `Next.js 16` `Docker` `LocalStack` `GitHub Actions`

### 🔐 [AgeTrust](https://github.com/ZeroTurst-NoneBelieve/agetrust-backend) — W3C DID/VC 기반 Zero-Trust 성인 인증 `2026.08 – 진행 중 · PM · Backend`

> 얼굴 데이터를 서버에 남기지 않고 **온디바이스 AI 얼굴 대조 + DID/VC**로 키오스크에서 성인 여부만 증명하는 인증 플랫폼

- FastAPI 백엔드 골격·API 계약 설계(API v1 라우팅, JWT 인증 미들웨어, 모델·스키마 계층), Alembic 마이그레이션 구성
- **해시체인 감사 로그 API**, Outbox → Kafka 이벤트 파이프라인 실 PostgreSQL 검증 테스트, `verification_logs` 스키마 재설계(nonce 해시·키오스크 단위 UNIQUE)
- 에러 응답 `detail.code` 표준화, 동시 가입 409 회귀 테스트, `constraints.txt`로 전이 의존성 고정, **GitHub Actions CI + ruff 도입**
- PM으로 ADR 16건 중 미결 8건 정리, 브랜치 룰셋(승인·CI·최신화 강제) 운영, 전 레포 PR 29건 작성 · 16건 리뷰 · 이슈 44건, 커밋 126건
- `FastAPI` `PostgreSQL` `Alembic` `Kafka` `Docker` `W3C DID/VC` `Flutter`

### 💕 [Our Date Map](https://github.com/SehyeokKim/our-date-map) — 커플 데이트 기록·계획 PWA `2026.07 – 2026.09 · 개인 프로젝트 · 풀스택`

> 지도 위에 추억을 핀으로 남기고, 다음 데이트 코스를 짜고, Web Push로 서로를 부르는 **커플 전용 PWA** — 기획부터 배포·운영까지 단독 ([our-date-map.vercel.app](https://our-date-map.vercel.app))

- **보안**: 전 테이블 `USING (true)` 공개 상태를 발견해 "나 또는 연결된 파트너"만 읽는 `TO authenticated` RLS로 전면 교체 — 적용 전 트랜잭션+ROLLBACK으로 역할별 조회 건수 검증
- **커플 연결**: 전역 고유 4자리 태그(#0000) 요청 → 수락 → 해제 흐름, 커플 공유 테마(색상 3 × 폰트 3, 모달 12종 토큰화)
- **외부 API 쿼터 보호**: ODsay(일 1,000회) 호출을 경유지 변경 시로 한정, 구간 단위 경로 재사용, 실패 응답 캐시 버그 수정
- Kakao OAuth, Kakao Mobility·ODsay 경로 시각화, Service Worker Web Push(VAPID), 이미지 자동 압축(300KB), 스키마 마이그레이션 21건
- 운영 배포 25회를 **v1.0.0 – v1.24.0** 시맨틱 버전 릴리스로 정리
- `Next.js 16` `React 19` `TypeScript` `Tailwind v4` `Supabase` `Vercel` `PWA`

### 📹 [Smart Doorlock CCTV](https://github.com/jnucpe20/server-public) — AI 이상행동 탐지 도어락·CCTV `2025.03 – 2025.12 · 캡스톤 졸업작품 · 3인 팀 · 백엔드`

> 라즈베리파이 카메라 → **WebRTC 실시간 스트리밍** → **X3D-M 모델**이 폭행·납치 등 이상행동을 탐지해 즉시 알림 — **최종 평가 A+**

- Docker Compose 한 번으로 REST API·WebRTC(SRS)·AI 분석기·MQTT 브로커가 함께 뜨는 서버 아키텍처
- SWAG 리버스 프록시 + Let's Encrypt HTTPS, MQTT 도어락 원격 제어, FCM/WebSocket 푸시
- `FastAPI` `WebRTC(SRS)` `MQTT` `Redis` `X3D-M` `Raspberry Pi` `Flutter`

<br/>

## 🤖 AI Engineering — AI로 문제를 푸는 방식

> **"AI로 속도를 내고, 설계와 검증으로 신뢰를 만든다."**
> 모든 프로젝트를 AI 코딩 에이전트(Claude Code 등)와 함께 개발했고, 제품에도 AI를 넣어 왔습니다.
> 제가 중요하게 생각하는 것은 AI를 *쓰는 것* 자체가 아니라, **AI가 잘하는 일과 못하는 일을 나눠 맡기고, 결과를 검증 가능한 구조로 만드는 것**입니다.

### 핵심 역량

- **AI 에이전트 오케스트레이션** — 워크트리 격리로 여러 AI 세션을 병렬 운영하며 4인 팀 프로젝트에서 PR 113건·커밋 152건(팀 최다)을 처리
- **LLM 제품화** — LangGraph + Structured Output + 4단계 가드레일로 LLM이 인프라를 *안전하게* 조작하도록 설계
- **AI 워크플로 설계** — 프로젝트별 AI 작업 규약(`CLAUDE.md`), 작업 명세 기반 개발, 위험 작업 승인 게이트, CI 기반 규약 강제
- **AI 결과물 검증** — 재현 출력·`파일:줄` 근거 요구, 테스트 우선 확장(2,754 passed), 모델 실측 비교로 AI 품질을 수치로 관리
- **자격** — AWS Certified AI Practitioner (2026.09)

### 프로젝트별 활용 사례

#### 🛡️ Vigilantis — LLM이 AWS 인프라를 조작해도 안전하도록

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| LLM이 잘못된 조치를 제안하면 실제 인프라가 망가짐 | LangGraph FinOps·SecOps 그래프 + Pydantic Structured Output, **① 입력 검증 → ② Action Whitelist → ③ ARN Match → ④ AWS Dry-Run** 4단계 가드레일. 실패해도 스펙 JSON 백업 기반 자동 롤백 | LLM은 *허용된 조치·대상*만 실행 가능, 실행·롤백 엔진과 Dry-Run precheck 10종 직접 구현 |
| 어떤 모델을 써야 하는지 근거가 없음 | 팀 AI 담당과 14개 모델·파라미터 조합 × 3라운드 **1,824회 실측 비교**, LLM-judge·factcheck 평가 하네스 운영 | 확정 600회 환각 0건, 경쟁 모델 대비 **비용 1/9**, SecOps 기준선 21 PASS / 0 FAIL |
| 실측 결과 다운사이징 목표 타입(`target_instance_type`)이 모든 모델에서 흔들림 | 해당 필드를 AI 출력에서 제거하고 **서버 결정 규칙으로 계산**하도록 재설계(#345) | "AI는 추정, 서버는 계산" 원칙 확립 — 이후 절감액 기능도 AI는 단가만 추정하도록 설계 |
| FE 담당 이탈로 대시보드 전체가 공백 | AI 에이전트와 함께 Next.js 16 FE를 인수 — mock 계층 1,762줄 폐기 후 실 API 연결, 토폴로지·공격 경로·추이 차트 구현 | 범위 축소 없이 일정 유지 |
| 한 폴더에서 AI 세션 여러 개가 checkout을 충돌시킴 | "세션 1 = worktree 1 = 브랜치 1 = 이슈 1" 원칙, 워크트리 관리 스크립트(378줄) 작성 — 슬롯별 포트로 전용 Docker 스택 기동, 리뷰 전용 워크트리 분리 | FE·INFRA·리뷰 작업을 AI 세션 3개로 동시에 진행 |
| 팀원마다 AI가 다른 스타일로 코드를 씀 | 팀 공유 `CLAUDE.md`(브랜치·커밋·PR·리뷰 규약) + 개인 `CLAUDE.local.md` 분리, AI 커밋 신원·서명 문구를 검사하는 CI `ai-signature` 잡(#340, #403) | AI를 쓰든 안 쓰든 같은 규약·같은 책임 주체로 이력 관리 |
| 리뷰 부담(팀원 PR 98건) | AI가 리뷰 초안과 이슈 CLOSE *추천*까지 작성하고, 승인·종료·주차 판정은 PM이 직접 확정. 유료 LLM 호출은 규모 추정 후 승인 | 리뷰 속도는 AI로, 최종 판단은 사람으로 |

#### 🔐 AgeTrust — AI가 만든 결과물을 믿을 수 있게

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| AI가 "통과했다", "문제없다"고 말해도 실제와 다를 수 있음 | AI의 모든 주장에 **재현 출력 또는 `파일:줄` 근거**를 요구하도록 작업 규약 명문화, 리뷰는 "결론 먼저 + 근거" 형식 고정 | 문서의 코드 인용을 실제 소스와 교차검증해 **인용 오류 2건을 머지 전 차단**(docs PR #5) |
| CI 초록불인데 E2E가 조용히 skip, 빈 DB 마이그레이션 왕복만으로는 검증이 안 됨 | 실측으로 확인한 함정을 AI 규약 문서에 "교훈"으로 누적해 다음 세션이 같은 실수를 반복하지 않게 함 | Outbox를 실 PostgreSQL로 검증하는 테스트(#54), 동시 가입 회귀 테스트(#57) 추가 |
| (제품) 얼굴 데이터를 서버에 남기면 안 됨 | 팀에서 온디바이스 얼굴 임베딩(SFace INT8 ONNX)으로 설계, 서버는 판정 결과와 해시체인 감사 로그만 저장 | 개인정보 비저장 구조 — 백엔드는 해시체인 감사 로그 API로 무결성 보장(#26) |

#### 💕 Our Date Map — AI 에이전트와 1인 풀스택 개발·운영

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| 혼자서 기획·FE·BE·DB·배포를 모두 해야 함 | Claude Code를 주 개발 도구로 사용, 큰 작업은 `tasks/task-XX.md` **명세 작성 → 구현 → 요약** 순서로 AI에 위임 | 약 2.5개월간 운영 배포 25회(v1.0.0 – v1.24.0) |
| Next.js 16은 AI 학습 데이터보다 최신이라 AI가 옛 API로 코드를 씀 | 규약에 "작업 전 `node_modules/next/dist/docs/`를 먼저 읽을 것"을 넣어 **최신 공식 문서를 근거로** 코드를 쓰게 함 | 최신 API 기준으로 구현 |
| AI가 운영 DB나 배포를 잘못 건드리면 복구가 어려움 | `!DB`(마이그레이션·RLS) · `!main`(배포) · `!explain`(설명만) **명령 플래그로 권한 게이팅**, 기존 행 데이터 수정·삭제는 금지 | RLS 전면 교체도 트랜잭션+ROLLBACK으로 역할별 조회 건수를 먼저 검증한 뒤 적용 |
| 외부 API 쿼터(ODsay 일 1,000회) 초과 위험 | AI와 호출 경로를 분석해 호출 시점 한정·구간 재사용 설계, 실패 응답 1시간 캐시 버그 발견·수정 | 쿼터 소진 위험 해소 |
| `main` checkout으로 로컬 전용 AI 설정 파일이 지워지는 사고 | 원인 분석 후 "`main` checkout 금지, `git push origin dev:main`으로만 배포" 규칙 명문화 | 재발 방지 |

#### 📹 Smart Doorlock CCTV — 실시간 영상 AI를 서비스로

| 문제 | AI 활용 / 해결 | 결과 |
|---|---|---|
| I3D 모델은 64프레임 입력이라 실시간 처리가 어려움 | 팀에서 **X3D-M(16프레임)으로 전환**·파인튜닝, 16프레임 슬라이딩 윈도우 + 임계값 0.7로 폭행·납치 등 5개 위협 클래스 탐지 | 실시간 탐지 → 이벤트 API·전후 15초 영상 클립·FCM 푸시로 연결 |
| 모델 교체 시 라벨이 뒤바뀐 채 조용히 동작할 위험 | 클래스 이름을 체크포인트의 `class_to_idx`에서 읽고, 모델이 없거나 구조가 다르면 **기동 실패(fail-fast)** 하도록 설계 | 잘못된 가중치로 탐지가 실패해도 모르는 상황 차단 |
| AI 분석기를 서버에 안정적으로 붙여야 함(백엔드 담당) | AI 분석기를 독립 컨테이너로 분리하고 REST API·WebRTC(SRS)·MQTT와 Docker Compose로 통합 | 명령 한 번으로 전체 시스템 기동, 캡스톤 **최종 평가 A+** |

#### ⚙️ 반복 업무 자동화

- **일일 업무일지 자동 작성** — GitHub(커밋·PR·리뷰·이슈)와 Slack 활동을 수집해 교육기관 양식(hwpx) 업무일지를 채우는 Claude Code 스킬 제작
- **기술 블로그 초안 생성기** — Gemini API + 기존 글 few-shot으로 문체·구조를 맞춘 Velog 글 초안 생성 CLI 제작, 자기 글이 예시로 섞이지 않도록 순환 참조 차단

### 배운 점

1. **AI에게 맡길 일과 맡기지 않을 일을 나눈다** — 재현성이 낮은 필드는 서버 규칙으로 옮기고, 금액처럼 틀리면 안 되는 값은 AI는 추정만·서버가 계산하게 했습니다. AI 품질 문제의 상당수는 프롬프트가 아니라 *역할 분담*으로 풀렸습니다.
2. **모델은 감이 아니라 측정으로 고른다** — 1,824회 실측 비교로 품질은 유지하면서 비용을 1/9로 줄였습니다. 프롬프트도 스냅샷과 기준선으로 회귀를 관리합니다.
3. **AI에게는 최신 근거를 줘야 한다** — 학습 데이터보다 새로운 프레임워크에서는 공식 문서를 먼저 읽게 하는 것만으로 결과가 달라졌습니다. 컨텍스트 설계가 곧 품질입니다.
4. **규칙은 문서보다 구조로 강제해야 지켜진다** — 사람도 AI도 규약을 잊습니다. 명령 플래그·CI 잡·워크트리 격리처럼 *어기기 어려운 구조*를 만드는 쪽이 효과적이었습니다.
5. **되돌리기 어려운 작업은 사람이 연다** — DB 변경·배포·과금·이슈 종료는 명시적 플래그와 사람 승인 뒤에만 실행합니다.
6. **사고는 규칙으로 남긴다** — AI 세션 충돌, 설정 파일 유실, 조용히 skip된 테스트 같은 사고를 그때그때 AI 규약 문서에 교훈으로 쌓아, 다음 세션의 AI가 같은 실수를 하지 않게 했습니다.
7. **AI 산출물의 책임은 사람에게 있다** — AI로 빠르게 만든 만큼 리뷰·테스트·근거 확인에 시간을 씁니다. Vigilantis에서 기능을 늘리는 동안 CI 테스트도 2,754개까지 함께 늘린 이유입니다.

<br/>

## 🤝 How I Lead & Collaborate

혼자 잘 짜는 코드보다, **팀이 같은 기준으로 움직이게 만드는 것**이 팀장의 일이라고 믿습니다.

- **리뷰 문화**: CODEOWNERS·브랜치 룰셋으로 승인 리뷰와 CI 통과를 강제하고, Vigilantis에서 팀원 PR 98건을 직접 리뷰
- **기록 문화**: 아키텍처 결정은 ADR로, 진행 상황은 주 2회 갱신하는 `PROJECT_STATUS.md`(SSOT)로 남겨 "왜"가 사라지지 않게 관리
- **자동화**: GitHub Actions CI(pytest·web·ai-signature), gitmoji + TYPE 커밋·브랜치 컨벤션 설계 및 운영
- **환경 표준화**: docker-compose·LocalStack으로 "내 컴퓨터에서만 되는" 문제를 구조적으로 제거
- **공백 대응**: 팀원 이탈 시 범위를 줄이지 않고 FE 영역을 직접 인수해 일정 유지

<br/>

## 🛠 Tech Stack

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white"/>
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

## 📊 GitHub Stats

<p>
  <img src="https://github-readme-stats-anuraghazra1.vercel.app/api/top-langs/?username=SehyeokKim&layout=compact&theme=onedark" height="165"/>
</p>

![GitHub Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=SehyeokKim&theme=react-dark&hide_border=true)

![footer](https://capsule-render.vercel.app/api?type=waving&color=0:1c2833,100:000000&height=120&section=footer)
