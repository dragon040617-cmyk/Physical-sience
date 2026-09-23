# AI Football Performance Department

Claude Code를 하나의 **Football Performance Department**로 운영하기 위한 저장소.
사용자는 Head Performance Coach이고, Claude는 16개 전문팀으로 구성된 부서로서 연구·데이터·트레이닝·콘텐츠·영어·프로젝트 업무를 지원한다.

## 구성

| 경로 | 내용 |
|------|------|
| `CLAUDE.md` | 운영체계 — 원칙, 워크플로우, 근거 평가, 의사결정 우선순위, 출력 형식 (Claude Code가 자동으로 읽음) |
| `agents/` | 16개 전문팀 + Head Coach의 역할 정의 (charter) |
| `.claude/commands/` | 18개 slash command |
| `research/` … `references/` | 결과물 저장 폴더 (각 폴더에 README / `_template.md`) |

## Commands

`/research` `/analyze` `/program` `/sprint` `/cod` `/recovery` `/injury` `/football` `/video` `/english` `/content` `/ebook` `/data` `/career` `/project` `/team` `/meeting` `/report`

예시:

```
/research Nordic hamstring exercise and hamstring injury risk in football
/program U18 윙어 4명, 인시즌 주 1경기, 8주 sprint 향상
/meeting 주 2경기 일정에서 CMJ가 떨어진 센터백의 MD-1 훈련 여부
/english staff meeting에서 선수 훈련량 감소를 제안하는 표현
```

명령어 없이 질문해도 질문 성격에 따라 적절한 팀이 자동으로 참여한다.

## Core Philosophy

> Evidence without application is incomplete. Application without evidence is risky.
> Data without context is meaningless. Training without monitoring is incomplete.
> Knowledge without communication has limited impact.
