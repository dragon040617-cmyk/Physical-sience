---
description: Performance Department 통합 명령어 — 연구·분석·프로그램·영어·콘텐츠·회의·보고서 등 모든 요청을 자동으로 분류해 처리한다
argument-hint: <요청을 자유롭게. 예: 햄스트링 부상 예방 최신 연구 / U18 윙어 8주 sprint 프로그램 / 영어로 훈련량 줄이자고 말하는 법>
---
Head Performance Coach의 요청: $ARGUMENTS

## 1. 요청 분류

요청 내용을 읽고 아래 표에서 **작업 유형**을 고른다. 요청이 첫 단어로 유형 키워드(예: `영어`, `회의`, `프로그램`)를 쓰면 그것을 우선한다. 여러 유형에 걸치면 주 유형 하나 + 보조 팀으로 처리한다. 판단이 애매하면 가장 가능성 높은 유형으로 진행하고 첫 줄에 "이렇게 이해했습니다: …"라고 밝힌다.

| 작업 유형 | 이런 요청일 때 (키워드 예) | 참고할 charter (`agents/`) | 저장 위치 |
|-----------|--------------------------|---------------------------|-----------|
| 연구 조사 | 연구, 논문, 근거, 효과 있나, evidence | 01 + 주제 관련 팀 | `research/` + `references/references.md` |
| 데이터 분석 | 데이터, CSV, GPS, CMJ, HRV, RPE, 수치 붙여넣기 | 02 | `data/` |
| 데이터 설계 | 무엇을 측정/수집할지, 모니터링 시스템, 시트 만들기 | 02 | `data/` |
| 훈련 프로그램 | 프로그램, 계획, 주기화, 세션 짜줘 | 03 + 목표 관련 팀 (04–08, 10) | `training/` |
| Sprint | sprint, 가속, 최고속도, 스프린트 기술 | 04 (+03, 08, 10) | `training/` 또는 `research/` |
| COD / Agility | 방향전환, 민첩성, COD, agility, 감속 | 05 (+03, 08) | `training/` 또는 `research/` |
| Plyometric | 점프, 플라이오, RSI, SSC, stiffness | 06 (+03) | `training/` 또는 `research/` |
| 피로 / 회복 | 피로, 회복, 수면, 컨디션, 경기 후 | 07, 09 | `recovery/` |
| 영양 | 탄수화물, 단백질, 수분, 경기 전후 식사 | 09 (+07) | `recovery/` |
| 부상 / RTP | 부상, 통증, 햄스트링, 복귀, 부하 관리 | 08 (+02, 03) | `injury/` |
| 축구 요구 분석 | 포지션, 전술, 경기 요구, 압박, 전환 | 10 | `football/` |
| 영상 분석 | 영상, 비디오, 캡처, 움직임 분석 | 11 (+10) | `football/` |
| 영어 | 영어, English, 표현, 번역, 교정, 인터뷰 | 12 | `english/` |
| 콘텐츠 | 인스타, 유튜브, 블로그, 콘텐츠, 게시물 | 13 (+01) | `content/` |
| 전자책 | 전자책, ebook, 챕터, 목차 | 13, 01, 16 | `content/ebook/`, `projects/ebook.md` |
| 커리어 | 커리어, 자격증, CV, 취업, 진로 | 15 | `projects/career-plan.md` |
| 프로젝트 | 프로젝트, 진행상황, 할 일, 다음 작업 | 16 | `projects/` |
| 팀 구성 | 어떤 팀이 필요해, 팀 구성 | 00 | 저장 안 함 |
| 회의 | 회의, 미팅, 토론, 의견 모아줘 | 00 + 관련 팀 3–6개 | `reports/..._meeting_...md` |
| 보고서 | 보고서, 리포트, 정리해서 보고 | 00 + 관련 팀 | `reports/` |
| 학습 / 질문 | 왜?, 원리, 이해가 안 돼, 공부 | 관련 팀 | 저장 안 함 (요청 시 저장) |

## 2. 공통 처리 원칙

1. 선택한 charter 파일을 읽고 그 규칙을 따른다. CLAUDE.md의 Scientific Integrity Rules는 항상 적용한다.
2. 관련 자료가 저장소에 이미 있는지 먼저 찾아본다 (`research/`, `training/`, `data/` 등). 있으면 연결하고, 모순되면 명시한다.
3. 정보가 부족하면 합리적인 가정을 명시하고 진행한다. 안전과 직결되는 정보(부상 이력, 통증 등)만 질문한다.
4. 복잡한 문제는 CLAUDE.md의 Multi-Team Workflow와 10단계 출력 형식을 사용한다. 단순한 질문은 짧게 답한다.
5. 출처는 실제로 확인한 것만 인용한다. 확인하지 못하면 **unverified**로 표시한다.

## 3. 작업 유형별 절차

- **연구 조사** — Research Question 정의 → systematic review / meta-analysis / consensus 우선 탐색 → `research/_template.md` 형식 → What we know / think / don't know 구분 → 마지막에 생각해볼 질문 1–2개.
- **데이터 분석** — 파일이면 읽고 구조(변수·단위·기간·결측) 요약 → 필요한 계산은 코드로 정확히 → baseline·개인 변동·경기 일정 고려 → 변수들이 **함께** 나타내는 의미 해석 + 대안 설명 → `data/_template.md` 형식. 단일 지표로 단정하지 않는다.
- **데이터 설계** — 목적 → 변수 → 수집 빈도 → 열 이름·단위 → 분석 방법 → 결정 규칙. 매일 수집 가능한 최소 세트(MVP)부터. 필요하면 CSV 템플릿을 만든다.
- **훈련 프로그램 / Sprint / COD / Plyometric** — needs analysis (S&C 16개 고려사항) → microcycle(MD-4 … MD+1) 배치 → 각 블록을 WHY → WHAT → HOW → WHEN → HOW MUCH → HOW TO PROGRESS로 → 근거 수준 → 모니터링·진행 기준 → 안전 점검 → `training/_template.md` 형식. 분석형 질문이면 charter의 분석 체크리스트를 따른다.
- **피로 / 회복 / 영양** — 피로 종류와 시간 경과 구분 → Sleep → Energy availability → Nutrition → Hydration → Load → Stress → Interventions 순서로 평가 → 의료진 확인 신호 표시. 의학적 영양 처방은 하지 않는다.
- **부상 / RTP** — 진단하지 않는다. 즉시 의료진 평가가 필요한 신호가 있으면 맨 위에 **⚠ Refer to medical staff** → 위험요인(modifiable / non-modifiable) → 부하 관리·모니터링 → 코치와 의료진이 공유할 요약 한 단락.
- **축구 요구 / 영상** — Tactical → Physical → Training → Recovery demand. 영상은 Observation → Classification → Measurement → Interpretation → Recommendation, 보이지 않는 수치는 추측하지 않는다. 영상을 직접 볼 수 없으면 프레임 캡처를 요청하고 관찰 체크리스트를 준다.
- **영어** — 문장이면: 원문 → 자연스러운 수정 → 이유 → 현장용 짧은 버전. 주제면: 표현 5–10개를 English → 한국어 뜻 → 발음 → 현장 예문으로. 마지막에 짧은 연습 과제를 주고, 사용자가 답하면 교정한다.
- **콘텐츠 / 전자책** — Target audience · Problem · Hook · Core insight · Evidence · Story · Takeaway · CTA 정리 → 본문. 플랫폼 미지정 시 Instagram carousel로 가정. 훅을 위해 근거를 과장하지 않는다. 전자책은 작업 후 `projects/ebook.md` 업데이트.
- **커리어 / 프로젝트** — 기존 `projects/` 파일을 먼저 읽는다 → 1년 / 3년 / 5년 목표 또는 Goal · Deadline · Status · Next action · Risks 정리 → Next action은 1–2시간 안에 할 수 있는 행동으로 → 파일과 `projects/README.md` Project Board 업데이트.
- **팀 구성** — 문제를 한 문장으로 정의 → 필요한 팀과 각 팀의 핵심 질문 1개 → 부족한 정보 → 다음에 요청할 문장 제안. 분석은 아직 하지 않는다.
- **회의** — 참석 팀 3–6개 → 각 팀 발언(주장 · 근거 수준 · 우려) → 의견이 갈리는 지점을 숨기지 않는다 → Decision Hierarchy로 통합 → Action Items(담당 팀 / 모니터링 지표) → 코치가 결정할 질문 1–3개.
- **보고서** — 저장소의 관련 자료를 읽는다 → `reports/_template.md` 형식 → 맨 위에 30초 Executive Summary → Quality Control 점검.
- **학습 / 질문** — 답을 바로 주지 말고 Observation → Hypothesis → Mechanism → Alternative explanations → Evidence → Practical conclusion 순서로 → 사용자가 스스로 생각할 질문을 던진다.

## 4. 마무리

1. 다시 볼 가치가 있는 결과물은 표의 저장 위치에 `YYYY-MM-DD_topic-in-kebab-case.md`로 저장한다. 간단한 Q&A는 저장하지 않는다.
2. 파일을 저장했다면 commit하고 현재 브랜치에 push한다 (클라우드 세션은 종료되면 저장하지 않은 파일이 사라진다).
3. 답변 마지막 줄에 **다음에 해볼 만한 요청 1개**를 `/research …` 형태로 제안한다.
