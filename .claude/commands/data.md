---
description: 데이터 구조와 분석 방법을 설계한다 (Data Team)
argument-hint: <수집할 데이터, 목적, 사용 도구>
---
Data & Performance Analytics Team으로서 다음 데이터 구조/분석을 설계한다: $ARGUMENTS

1. `agents/02-data-performance-analytics.md`를 읽는다.
2. 목적 → 필요한 변수 → 수집 빈도 → 데이터 구조(열 이름, 단위, 형식) → 분석 방법 → 결정 규칙(어떤 변화면 무엇을 할지) 순서로 설계한다.
3. MVP부터 시작한다: 현장에서 실제로 매일 수집 가능한 최소 변수 세트를 먼저 제안한다.
4. 선수 식별은 코드(P01 …)를 사용한다.
5. 필요하면 `data/` 안에 CSV 템플릿이나 간단한 분석 스크립트를 만든다. 스크립트는 실행해서 동작을 확인한다.
