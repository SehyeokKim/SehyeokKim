<div align="center">

![header](https://capsule-render.vercel.app/api?type=waving&color=0:000000,100:1c2833&height=200&section=header&text=Sehyeok%20Kim&fontSize=48&fontColor=ffffff&desc=Infra%20%26%20DevSecOps%20Engineer&descSize=18&descAlignY=75)

### 『 아무도 보지 않을 때에도, 누군가 보고 있는 것처럼 당당하게 행동한다 』

*Integrity is doing the right thing, even when no one is watching.*

</div>

<br/>

## 👋 About Me

**"지켜보고, 지켜주는 시스템"** 을 만드는 개발자 김세혁입니다.

24/7 클라우드 관제, AI 가드레일, 실시간 CCTV 감시, Zero-Trust 인증 —
제가 만들어온 프로젝트는 모두 *신뢰할 수 있는 감시와 자동화*라는 하나의 주제로 이어집니다.
좌우명 그대로, 보는 사람이 없어도 스스로 떳떳한 코드와 기록(문서·리뷰·CI)을 남기는 것을 원칙으로 합니다.

- 🔭 **현재**: AWS FinSecOps 플랫폼 **Vigilantis** 팀장(PM) · Infra & DevSecOps 담당
- 🛠️ **주력**: Python(FastAPI) · AWS(Boto3) · Docker · PostgreSQL · CI/CD
- 🎓 전남대학교 컴퓨터공학전공
- 📫 **Contact**: kimseh0418@gmail.com

<br/>

## 🚀 Projects

### 🛡️ [Vigilantis](https://github.com/ProjectVigilantis/vigilantis) — AWS FinSecOps 자율 관제 플랫폼 `팀장 / PM · Infra & DevSecOps`

> 24/7 AWS 자산·보안 상시 관제 + **4단계 AI 가드레일** 기반 원클릭 자율 조치 + **자동 롤백(Auto-Rollback)** 플랫폼

- Boto3 기반 **EC2/SG 제어 모듈**과 스펙 JSON 백업 → Status Check 감시 → 부팅 실패 시 **자동 원복 엔진** 설계·구현
- **LocalStack 기반 팀 표준 개발 환경**(docker-compose·시드 데이터) 구축 — 실 AWS 비용 없이 전 팀원 동일 환경 보장
- 아키텍처 결정을 **ADR 6건**으로 기록하고, `PROJECT_STATUS.md`를 단일 기준 문서(SSOT)로 운영
- `FastAPI` `Boto3` `PostgreSQL` `LangGraph` `Docker` `LocalStack` `GitHub Actions`

### 🔐 [AgeTrust](https://github.com/ZeroTurst-NoneBelieve/agetrust-backend) — W3C DID/VC 기반 Zero-Trust 성인 인증 `Backend · Infra`

> 개인정보 노출 없이 키오스크에서 성인 여부만 증명하는 **DID/VC(Verifiable Credential) 인증 서비스**

- FastAPI 백엔드 구조 설계 및 **FastAPI + PostgreSQL + Kafka docker-compose 인프라 일원화**
- revert로 유실된 DID 암호화 키 유틸을 추적·복원해 dev 기동 불가 이슈 해결
- `FastAPI` `PostgreSQL` `Kafka` `Docker` `W3C DID/VC`

### 📹 [Smart Doorlock CCTV](https://github.com/jnucpe20/server-public) — AI 이상행동 탐지 도어락·CCTV 시스템 `캡스톤 · Team INVICTUS`

> 라즈베리파이 카메라 → **WebRTC 실시간 스트리밍** → **X3D-M 모델**이 폭행·납치 등 이상행동을 탐지해 즉시 알림

- Docker Compose 한 번으로 REST API·WebRTC(SRS)·AI 분석기·MQTT 브로커가 함께 뜨는 서버 아키텍처
- SWAG 리버스 프록시 + Let's Encrypt HTTPS, MQTT 도어락 원격 제어, FCM/WebSocket 푸시
- `FastAPI` `WebRTC(SRS)` `MQTT` `Redis` `X3D-M` `Raspberry Pi` `Flutter`

### 💕 [Our Date Map](https://github.com/SehyeokKim/our-date-map) — 커플 데이트 기록·계획 PWA `개인 프로젝트 · 풀스택`

> 지도 위에 추억을 핀으로 남기고, 다음 데이트 코스를 짜고, Web Push로 서로를 부르는 **커플 전용 PWA**

- Kakao OAuth 로그인, Kakao Mobility·ODsay API 경로 시각화, 서비스 워커 기반 Web Push 구현
- 클라이언트 이미지 자동 압축(300KB), 소프트 삭제·복원 등 실사용 품질 중심 설계
- `Next.js 16` `React 19` `TypeScript` `Tailwind v4` `Supabase` `PWA`

<br/>

## 🤝 How I Lead & Collaborate

혼자 잘 짜는 코드보다, **팀이 같은 기준으로 움직이게 만드는 것**이 팀장의 일이라고 믿습니다.

- **리뷰 문화**: CODEOWNERS로 PM 승인 리뷰를 강제하고, DB 저장 계층·가드레일 Whitelist 등 팀원 핵심 PR을 직접 리뷰
- **기록 문화**: 아키텍처 결정은 ADR로, 프로젝트 범위·계약은 SSOT 문서로 남겨 "왜"가 사라지지 않게 관리
- **자동화**: GitHub Actions CI(pytest) 구축, gitmoji + TYPE 커밋·브랜치 컨벤션 설계 및 운영
- **환경 표준화**: docker-compose·LocalStack으로 "내 컴퓨터에서만 되는" 문제를 구조적으로 제거

<br/>

## 🛠 Tech Stack

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white"/>
  <img src="https://img.shields.io/badge/AWS-232F3E?style=for-the-badge&logo=amazonwebservices&logoColor=white"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white"/>
</p>
<p>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white"/>
  <img src="https://img.shields.io/badge/Flutter-02569B?style=for-the-badge&logo=flutter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Kafka-231F20?style=for-the-badge&logo=apachekafka&logoColor=white"/>
</p>

<br/>

## 📊 GitHub Stats

<p>
  <img src="https://github-readme-stats-sigma-five.vercel.app/api/top-langs/?username=SehyeokKim&layout=compact&theme=one-dark" height="165"/>
</p>

![GitHub Activity Graph](https://github-readme-activity-graph.vercel.app/graph?username=SehyeokKim&theme=react-dark&hide_border=true)

![footer](https://capsule-render.vercel.app/api?type=waving&color=0:1c2833,100:000000&height=120&section=footer)
