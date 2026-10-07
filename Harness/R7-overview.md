# CourtView Harness — 전체 설계 요약 (R7)

## 목적 (R2)

| 항목 | 내용 |
|---|---|
| 매번 달라지는 입력 | 서비스 이름, `prd.md`, `DESIGN.md` |
| 실행 주체 | 본인(디자이너), Claude Code CLI |
| 완료 기준 | UI 키스크린 2~3개가 Figma에 생성되고, 가이드 위반 항목이 0개다 |
| 관계자 컨펌 방식 | 하네스가 멈추고 사람이 승인 후 재개 |

## 파이프라인 (R3)

| 단계 | 작업 | 산출물 | 게이트 |
|---|---|---|---|
| 1 | uibowl에서 레퍼런스 수집 | `references.md` | — |
| 2–3 | 분석 초안 + 화면 설계 문서 작성 | `analysis.md`, `screen-spec.md` | 내가 수정 후 승인 |
| 4 | Figma 키스크린 2~3개 제작 | 프레임 + 컴포넌트 + 컬러 토큰 | 관계자 컨펌 → 재개 |
| 5–6 | 토큰·컴포넌트 + 화면 디자인 | 디자인 토큰, 컴포넌트, 화면 디자인 | — |
| 7 | 가이드 검토 | `Harness/gate-report.md` | hex 하드코딩 1개 이상 → 위반 |

## 에이전트 (R4)

| 에이전트 | 담당 단계 | 사용 도구 | 출력 |
|---|---|---|---|
| A1 · 레퍼런스 수집 | 1 | uibowl MCP | `references.md` |
| A2 · 분석 + 설계 | 2–3 | prd.md, references.md 읽기 | `analysis.md`, `screen-spec.md` |
| A3 · Figma 제작 | 4 | Figma MCP | 키스크린 2~3개 |
| A4 · 토큰·컴포넌트 + 화면 디자인 | 5–6 | Figma MCP | 디자인 토큰, 컴포넌트, 화면 디자인 |
| A5 · 가이드 검토 | 7 | DESIGN.md 읽기 | `Harness/gate-report.md` |

## 게이트 (R5)

| 게이트 | 위치 | 재개 방식 |
|---|---|---|
| G1 | A2 완료 후 | 터미널에서 `y` 입력 |
| G2 | A3 완료 후 | 관계자 확인 후 터미널에서 `y` 입력 |

## 실행 설정 (R6)

| 항목 | 내용 |
|---|---|
| 실행 명령어 | `/harness run` |
| 입력값 전달 | `Harness/config.yaml` |
| 산출물 저장 | `Harness/outputs/YYYY-MM-DD/` |

## 구현할 파일 목록 (R7)

| 파일 | 역할 |
|---|---|
| `Harness/HARNESS.md` | 진입점 — 에이전트 실행 지침서 |
| `Harness/config.yaml` | 실행 입력값 템플릿 |
| `Harness/gate-report.md` | A5 가이드 검토 결과 |
| `Harness/outputs/YYYY-MM-DD/references.md` | A1 — uibowl 레퍼런스 수집 결과 |
| `Harness/outputs/YYYY-MM-DD/analysis.md` | A2 — 분석 + 반영 포인트 |
| `Harness/outputs/YYYY-MM-DD/screen-spec.md` | A2 — 화면 설계 문서 초안 |
