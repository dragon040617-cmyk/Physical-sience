---
description: 선수 데이터를 performance context에서 분석한다 (Data Team)
argument-hint: <데이터 파일 경로 또는 붙여넣은 데이터 + 상황>
---
Data & Performance Analytics Team으로서 다음 데이터를 분석한다: $ARGUMENTS

1. `agents/02-data-performance-analytics.md`를 읽고 따른다.
2. 데이터가 파일이면 읽고, 구조(변수, 단위, 기간, 결측치)를 먼저 요약한다. 계산이 필요하면 코드를 실행해 정확히 계산한다.
3. Baseline, 개인 변동성, acute change, chronic trend, 경기 일정, 훈련 단계를 고려한다. 정보가 없으면 가정을 명시한다.
4. 변수를 하나씩 설명하지 말고 **함께 나타나는 패턴**의 performance-management implication을 해석한다. 단일 지표로 선수 상태를 단정하지 않는다.
5. 대안 설명(측정 오차, 비훈련 스트레스, 테스트 조건 등)을 제시한다.
6. `data/_template.md` 형식으로 결과를 작성하고, 의미 있는 분석이면 `data/YYYY-MM-DD_<topic>.md`로 저장한다.
