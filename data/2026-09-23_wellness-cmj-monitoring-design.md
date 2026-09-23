# Wellness + CMJ 모니터링 시트 설계

- Date: 2026-09-23
- Teams: Data & Performance Analytics (02) · Fatigue & Recovery (07)
- 연결 문서: `recovery/2026-09-23_football-recovery-evidence-and-protocol.md` (7. Monitoring)
- 파일:
  - `data/wellness-cmj-tracker.xlsx` — 실제로 쓰는 템플릿 (예시 행 P00 1개)
  - `data/wellness-cmj-tracker_example.xlsx` — 가상 선수 3명의 4주치 예시 데이터 (학습용)

## 1. 목적

경기 후 회복 상태를 **선수 개인 기준(baseline)**과 비교해서, 훈련 볼륨을 조정할지 판단하는 데 쓸 **대화 신호**를 만든다. 선수 상태를 진단하는 도구가 아니다.

## 2. 변수와 수집 빈도 (MVP)

| 변수 | 척도 | 빈도 | 근거 |
|------|------|------|------|
| 수면의 질, 피로, 근육통, 기분, 스트레스 | 각 1–5점 (5 = 매우 좋음), 합계 5–25 | 매일 아침 훈련 전 | McLean et al. 2010 형식 |
| 수면 시간 | 시간 (h) | 매일 | 참고용 (판정에는 쓰지 않음) |
| CMJ | cm, 3회 측정 | 주 1–2회 (MD-4, MD+2) | 판정은 **3회 평균**. Claudino et al. 2017 메타분석에서 평균이 최고값보다 민감했다 |

## 3. 데이터 구조

| 시트 | 열 |
|------|-----|
| 선수 | 선수 코드 · 포지션 · 연령/팀 · 메모 |
| Wellness | 날짜 · 선수 코드 · MD 코드 · 수면 시간 · 5개 항목 → (자동 계산) 합계 · baseline 평균·SD·기록 수 · z-score · 피로·근육통 낮음 · 상태 |
| CMJ | 날짜 · 선수 코드 · MD 코드 · 1–3차 → (자동 계산) 최고 · 평균 · baseline · 변화 % · 상태 |
| 대시보드 | 선수별 최근 wellness와 CMJ, 플래그 수, 권고 |
| 설정 | 기준값 (기간, 최소 기록 수, 임계값) |

- 입력 칸은 노란색, 자동 계산 칸은 회색이다.
- 입력 규칙이 걸려 있다: 1–5 정수, 선수 코드 목록, MD 코드 목록.

## 4. 분석 방법

- **Wellness:** 선수 본인의 직전 28일 기록으로 평균과 표준편차를 구해 z-score를 계산한다. baseline 기록이 5개 미만이면 판정하지 않고 "baseline 수집 중"으로 표시한다.
- **CMJ:** 선수 본인의 직전 56일 평균 대비 % 변화를 계산한다. baseline 기록이 3개 미만이면 판정하지 않는다.

## 5. 결정 규칙 (현장 경험에 기반한 출발점이며, 연구로 검증된 기준이 아니다)

| 플래그 | 조건 (설정 시트에서 변경 가능) |
|--------|------------------------------|
| ① Wellness 낮음 | z-score ≤ −1.0 |
| ② 선수 호소 | 피로 또는 근육통 ≤ 2점 |
| ③ CMJ 저하 | baseline 대비 5% 이상 낮음 (최근 wellness 기준 7일 안의 측정만 포함) |

- 플래그 **2개 이상** → 고강도 볼륨 조정 + 선수와 대화
- **1개** → 관찰
- **0개** → 계획대로

## 6. 해석할 때 주의할 점

- **MD+1과 MD+2에는 wellness가 정상적으로 낮다.** baseline에는 모든 요일이 섞여 있어서, 경기 직후에는 "낮음"이 자주 뜬다. 예시 파일에서도 MD+2에 세 선수 모두 "낮음"이 나왔다. 그래서 판정은 **MD 코드와 함께** 본다.
  - 경기 후에 예상되는 저하인가?
  - 아니면 MD-4나 MD-3까지 이어지는가? 이어진다면 더 중요한 신호다.
  - 다음 개선 후보: 같은 MD 코드끼리 비교하는 baseline. 데이터가 한 시즌 정도 쌓여야 가능하다.
- **CMJ 5% 기준은 임시값이다.** 휴식 상태에서 같은 날 또는 이틀 연속 반복 측정해 팀의 측정 오차(CV)를 구하고, 그 값으로 바꾼다.
- **처음 4주는 baseline을 쌓는 기간이다.** 측정 시간, 준비운동, 측정 도구를 일정하게 유지한다.
- **설문 응답의 질이 판정의 질을 결정한다.** 선수가 솔직하게 답할 수 있어야 한다. 답했더니 벌을 받는다고 느끼면 응답이 왜곡된다.

## 7. 검증

- LibreOffice로 다시 계산했을 때 수식 14,440개, 오류 0개였다.
- 예시 파일의 baseline 평균·SD·기록 수와 CMJ baseline을 Python(pandas)으로 따로 계산해 비교했다. 불일치 0건 (Wellness 82행, CMJ 15행).

## References

- McLean BD, et al. (2010). Neuromuscular, endocrine, and perceptual fatigue responses during different length between-match microcycles in professional rugby league players. *IJSPP*, 5(3), 367–383. [권·호·페이지 unverified]
- Claudino JG, Cronin J, et al. (2017). The countermovement jump to monitor neuromuscular status: a meta-analysis. *J Sci Med Sport*, 20(4), 397–402. https://pubmed.ncbi.nlm.nih.gov/27663764/
