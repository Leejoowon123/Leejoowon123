[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=50&pause=1000&center=true&vCenter=true&width=800&height=60&lines=Hi+I'm+joowon+LEE;%E3%81%93%E3%82%93%E3%81%AB%E3%81%A1%E3%81%AF%E3%80%81%E3%82%A4%E3%83%BB%E3%82%B8%E3%83%A5%E3%82%A6%E3%82%A9%E3%83%B3%E3%81%A7%E3%81%99;Hola%2C+Soy+Joowon+LEE)](https://git.io/typing-svg)

👋 Hi there! I'm JOOWON LEE
🌐 I enjoy working on Back-end & AI development 

- **GitHub:** [Leejoowon123](https://github.com/Leejoowon123)
- **블로그:** [joowon582.tistory.com](https://joowon582.tistory.com/)
- **GMAIL:** joowon582@gmail.com
- **Linked-In:** [Linked-In](https://www.linkedin.com/in/Leejoowon1)
---
## 🔭 I’m currently working on...
### JLPT 10분 학습 큐 (JLPT-10min)
- **프로젝트 소개** : JLPT(일본어능력시험)를 준비할 수 있도록 설계된 웹 기반 학습 도구입니다. 복습, 단어, 문법, 독해, 청해, '오늘의 10분 학습 큐'를 중심으로, 단계별 암기 및 실시간 회화 연습까지 지원
- **링크** : https://github.com/Leejoowon123/jlpt-10min
- **기술스택:**
- Frontend Core
  - **Language:** Vanilla JavaScript (ES Modules)
  - **Markup & Styling:** HTML5, CSS3 (No Framework)
- Web APIs & Cloud
  - **Web APIs:** Web Speech API (내장 TTS/STT 활용한 청해 및 회화 평가)
  - **Storage:** Web Storage API (`localStorage` 기반 로컬 데이터 관리)
  - **Backend (Serverless):** Firebase (Spark Plan)
    - `Authentication`: 이메일/비밀번호 기반 회원가입 및 로그인
    - `Realtime Database`: 기기 간 진도율(Progress) 동기화 및 실시간 접속자 수(Presence) 추적
- QA & DevOps
  - **Deployment:** GitHub Pages (정적 웹 호스팅)
  - **CI/CD:** GitHub Actions (main 브랜치 PR/Push 시 자동 QA 파이프라인 구동)
  - **Testing:** jsdom 기반 QA 시스템 (Smoke Test 133개 체크 + 126개 사용자 시나리오 테스트 완벽 통과)
### 아키텍처 특징 (Architecture Highlights)
- **Cost-Effective & Serverless:** GitHub Pages와 Firebase 무료 플랜 조합으로 **서버 유지 비용 0원**
- **Robust Stability:** `jsdom` 환경에서 250개 이상의 테스트 케이스를 통과해야만 배포되는 CI/CD 환경 구축
- **Privacy-First:** 사용자의 개인 학습 기록은 기본적으로 브라우저 로컬에 보관, 원할 때만 클라우드 계정에 연동

---

## 📂 Projects
### 1. 인사 통합 플랫폼
- **프로젝트 소개**: HR 업무를 단일 플랫폼으로 통합하고, 운영 정책과 의사결정을 문서로 추적 가능하게 만든 사내 시스템 기획 프로젝트
- **기간**: 2026.01 ~ 2026.06
- **링크**: Private 처리(사내 정보로 Private 처리)
- **주요기능**
  - 14개 HR 업무 영역 통합: 식권, 휴일근무 등의 직원 신청부터 인사발령, 평가 등 HR 운영까지 단일 업무 흐름으로 표준화
  - 3계층 권한 거버넌스: 역할 기반(기본), 부서 기반(조직), 사용자 개별(예외)의 3가지 모드로 권한 통제
  - 단일 권한 카탈로그: 53개 메뉴와 130개 버튼 권한을 중앙에서 관리하여 권한 우회 원천 차단
  - 결재 및 상태 자동 연동: 5개 신청 모듈의 상태 변화를 결재 문서와 연동하고, 변경 전후의 모든 이력을 감사 로그로 자동 기록
  - 외부 시스템(ERP) 격리 연동: 각 화면에서 개별적으로 호출하던 ERP 연동을 1개의 전용 영역으로 통합하여 단일 통로로 구성
- **시스템 기획 및 설계 전략 (Architecture & Strategy)**
  - 환경: 사내 웹 기반 HR 시스템
  - 하이브리드 투트랙(Two-Track) 구조 도입: 리스크가 집중된 핵심 비즈니스 영역(60%)은 '헥사고날 아키텍처+DDD'를 엄격히 적용하고, 단순 데이터 입출력 영역(40%)은 'MVC(FastAPI Router)'를 채택하여 오버 엔지니어링을 방지하고 개발 생산성 향상
  - 도메인 주도 설계(DDD) 및 이벤트 기반 통신: 서비스 간 직접 호출을 전면 배제하고, 오직 도메인 이벤트(Publish/Subscribe)로만 소통하도록 설계 → 승진 처리 롤백 등의 강결합 문제를 해결하고 도메인 간 완벽한 논리적 격리
  - 비동기 이벤트 리스너 활용: 외부 알림(SMTP 메일 등) 전송 시 비동기 이벤트 리스너를 도입하여, 외부 서버 장애가 발생해도 핵심 인사 업무 트랜잭션은 정상 유지되도록 결과적 일관성을 확보
  - AI 및 변화에 대응하는 확장성: 데이터 변경 없이 무거운 읽기(Read)를 수행하는 AI HR 챗봇용 Read Adapter를 분리하여 핵심 로직 보호. 매년 변동되는 세법 등은 전략(Strategy) 패턴을 활용해 어댑터만 교체하도록 설계하여 코드 의존성을 낮춤 
  - 동시성 리스크 3중 방어: 차량 예약 등 충돌이 발생할 수 있는 기능은 사전 가용성 확인, DB 잠금, 중복 차단 제약의 3중 인프라 패턴으로 방어
  - 표준 응답 규약 도입: 업무 로직과 화면 응답 처리를 분리, 성공·실패·오류를 담는 표준 응답 형식 정의
  - 거대 모듈 분할: 단일 파일로 묶여있던 엑셀 출력 모듈 등을 외부 진입점은 유지한 채 책임별로 8개로 분할하여 회귀 사고 방지
- **도입 효과 (Impact)**
  - 유지보수 비용 감소: 표준 책임 분리 구조를 통해 화면별 변경 영향 범위 30% 감소
  - 안정성 대폭 향상: 화면 단독 검증이 가능해지면서 자동 검증 시나리오가 600건에서 2,371건으로 4배 증가
  - 외부 의존도 하락: ERP 스펙 변경 시 연동 영역 1곳만 수정하도록 개선하여 수정 비용을 85% 절감
  - 추적성 및 거버넌스 확립: 17건의 운영 정책 결정문을 문서화하고 모든 데이터 상태 변화를 기록하여 컴플라이언스 감사에 즉시 대응 가능 
 
### 2. 전략 분석 자동화 시스템
- **프로젝트 소개**: 전략기획팀 실무 자동화를 위해 개발된 LLM 기반 전략 분석 및 KPI 성과 관리 시스템입니다.
사용자는 회사명과 전략 방향만 입력하면, 기업의 내외부 환경 분석부터 실행 가능한 KPI 설계, 달성 여부 시각화까지 전략 기획 전 과정을 자동화된 인터페이스를 통해 수행할 수 있습니다.

- **기간**: 2025.05 ~ 2025.06
- **링크**: https://github.com/Leejoowon123/Streamlit_Project
- **기술스택:**

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![STREAMLIT](https://img.shields.io/badge/Streamlit-FF4B4B?&style=for-the-badge&logo=Streamlit&logoColor=white)


### 3. AI TAX
- **프로젝트 소개:**
  [졸업논문] : AI세금 최적화 및 경제적 영향 분석 시스템 개발
- **역할:** SOLO
- **기간:** 2025.02 ~ 2025.03
- **링크:**
  https://github.com/Leejoowon123/2025oss-couscous
- **기술스택:**

![JUPYTER](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter)
![STREAMLIT](https://img.shields.io/badge/Streamlit-FF4B4B?&style=for-the-badge&logo=Streamlit&logoColor=white)
![PYTHON](https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white)
![MYSQL](https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white)
![DOCKER](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![SCKITLEARN](https://camo.githubusercontent.com/09080e19f66c73a55b0f50494d4a828b3f9294e88adfc8fb9c3696c949cf696a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f7363696b69746c6561726e2d4637393331453f7374796c653d666f722d7468652d6261646765266c6f676f3d6e756d7079266c6f676f436f6c6f723d7768697465)
![SCIPY](https://img.shields.io/badge/scipy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white)

### 4. SKNETWORKS-FAMILY-AICAMP / SKN03-2rd-3Team (코딩하는 망곰이들)
- **프로젝트 소개:**  
  한국 엑티브 시니어를 위한 망곰이 지도 구축
- **링크:**
  https://github.com/SKNETWORKS-FAMILY-AICAMP/SKN03-2nd-3Team
- **역할:** Full-Stack(개발), 데이터 분석, AWS 연동
- **기간:** 2024.09 ~ 2024.09
- **기술스택:**

![STREAMLIT](https://img.shields.io/badge/Streamlit-FF4B4B?&style=for-the-badge&logo=Streamlit&logoColor=white)
![PYTHON](https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white)
![DOCKER](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/Amazon_AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![DJANGO](https://img.shields.io/badge/Django-092E20?style=for-the-badge&logo=django&logoColor=white)
![SCKITLEARN](https://camo.githubusercontent.com/09080e19f66c73a55b0f50494d4a828b3f9294e88adfc8fb9c3696c949cf696a/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f7363696b69746c6561726e2d4637393331453f7374796c653d666f722d7468652d6261646765266c6f676f3d6e756d7079266c6f676f436f6c6f723d7768697465)
![SQLLITE](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)

### 5. SKNETWORKS-FAMILY-AICAMP / SKN03-FINAL-2Team
- **프로젝트 소개:**  
  DeepFM 모델을 사용하여 유저 특성(배우) - 아이템 특성 (장르) 간의 시스템 구축
- **링크:**
  https://github.com/SKNETWORKS-FAMILY-AICAMP/SKN03-FINAL-2Team
- **역할:** 팀원 (최종 보고서 작성, 데이터분석, DeepFM 선택)
- **기간:** 2024.11 ~ 2025.01
- **기술스택**

![STREAMLIT](https://img.shields.io/badge/Streamlit-FF4B4B?&style=for-the-badge&logo=Streamlit&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![MYSQL](https://img.shields.io/badge/MySQL-00000F?style=for-the-badge&logo=mysql&logoColor=white)
![AWS](https://img.shields.io/badge/Amazon_AWS-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white)
![DOCKER](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![TENSORFLOW](https://img.shields.io/badge/TensorFlow-FF6F00?style=for-the-badge&logo=tensorflow&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![JUPYTER](https://img.shields.io/badge/Made%20with-Jupyter-orange?style=for-the-badge&logo=Jupyter)

---

## 📊 GitHub Stats & Language Usage

| GitHub Streak | Top Langs |
| ------------- | --------- |
| [![GitHub Streak](https://streak-stats.demolab.com/?user=Leejoowon123)](https://git.io/streak-stats) | ![Top Langs](https://github-readme-stats.vercel.app/api/top-langs/?username=Leejoowon123&theme=blue-green) |

---
## ✨ Baekjoon solved rank
[![Solved.ac Profile](http://mazassumnida.wtf/api/v2/generate_badge?boj=happy0693)](https://solved.ac/happy0693/)
<!--
**Leejoowon123/Leejoowon123** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...

-->
