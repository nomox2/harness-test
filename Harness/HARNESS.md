# CourtView Harness — 실행 지침서

## 시작 전 확인
1. `Harness/config.yaml`을 읽어 `service_name`, `prd`, `design` 값을 확인한다.
2. 오늘 날짜로 `Harness/outputs/YYYY-MM-DD/` 폴더를 만든다.
3. `docs/story-service.md`, `docs/story-work.md`를 읽어 서비스 맥락을 파악한다.

---

## A1 · 레퍼런스 수집

**도구:** uibowl MCP  
**작업:** config의 `service_name`을 기반으로 경쟁사 UI 레퍼런스를 검색한다.  
**출력:** `outputs/YYYY-MM-DD/references.md` — 이미지 URL 목록

---

## A2 · 분석 + 화면 설계

**도구:** `prd.md`, `references.md` 읽기  
**작업:**
1. prd.md와 references.md를 읽고 우리 서비스에 반영할 포인트를 분석한다.
2. 분석 내용을 바탕으로 화면 설계 문서 초안을 작성한다.

**출력:**
- `outputs/YYYY-MM-DD/analysis.md` — 분석 내용 및 반영 포인트
- `outputs/YYYY-MM-DD/screen-spec.md` — 화면 설계 문서 초안

### 🔴 G1 — 사람 승인 필요
```
A2가 완료되었습니다.
outputs/YYYY-MM-DD/analysis.md 와 screen-spec.md 를 확인하고 수정하세요.
계속하려면 y를 입력하세요.
```
> `y` 입력 전까지 다음 단계로 넘어가지 않는다.

---

## A3 · Figma 키스크린 제작

**도구:** Figma MCP  
**작업:** screen-spec.md를 읽고 390×844 사이즈로 키스크린 2~3개를 순서대로 제작한다.  
각 화면: 프레임 1개 + 컴포넌트 배치 + `DESIGN.md`의 컬러 토큰 적용  
**출력:** Figma 파일 내 키스크린 프레임 2~3개

### 🔴 G2 — 관계자 컨펌 필요
```
A3가 완료되었습니다.
Figma 키스크린을 관계자에게 공유하고 컨펌을 받으세요.
컨펌 후 y를 입력하세요.
```
> `y` 입력 전까지 다음 단계로 넘어가지 않는다.

---

## A4 · 토큰·컴포넌트 + 화면 디자인

**도구:** Figma MCP  
**작업:** 컨펌된 키스크린을 기반으로 디자인 토큰과 컴포넌트를 제작하고 화면 디자인을 완성한다.  
**출력:** Figma 파일 내 디자인 토큰, 컴포넌트, 화면 디자인

---

## A5 · 가이드 검토

**도구:** `DESIGN.md` 읽기  
**작업:**
1. `DESIGN.md`에서 정의된 색상 토큰 목록을 추출한다.
2. 산출물 파일에서 토큰으로 참조되지 않은 하드코딩 hex값(`#` 으로 시작)을 탐색한다.
3. 위반 항목을 목록으로 정리한다.

**판정 기준:** 하드코딩 hex값이 1개 이상 → 위반 / 0개 → 통과  
**출력:** `Harness/gate-report.md`

---

## 완료 기준

- [ ] Figma에 키스크린 2~3개 생성됨
- [ ] `gate-report.md` 위반 항목 0개 (통과)
