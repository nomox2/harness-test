# CourtView Harness — 실행 설정 (R6)

| 항목 | 내용 |
|---|---|
| 실행 명령어 | `/harness run` |
| 입력값 전달 | `Harness/config.yaml` 에 미리 작성, 에이전트가 읽음 |
| 산출물 저장 위치 | `Harness/outputs/` |
| 실행 결과 관리 | 실행마다 `outputs/YYYY-MM-DD/` 폴더로 분리 |

## 폴더 구조

```
Harness/
├── HARNESS.md           ← 진입점
├── config.yaml          ← 실행마다 여기만 수정
├── gate-report.md       ← A5 가이드 검토 결과
├── R2-purpose.md
├── R3-pipeline.md
├── R4-agents.md
├── R5-gates.md
├── R6-config.md
├── R7-overview.md
└── outputs/
    └── YYYY-MM-DD/
        ├── references.md   ← A1 산출물
        ├── analysis.md     ← A2 산출물
        └── screen-spec.md  ← A2 산출물
```

## config.yaml 기본 형식

```yaml
service_name: CourtView
prd: docs/prd.md
design: docs/DESIGN.md
```
