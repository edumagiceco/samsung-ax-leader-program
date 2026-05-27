---
title: 5.1 AX 추진·전략
parent: 5. 부서별 영감 라이브러리
nav_order: 1
has_children: true
permalink: /06-team-inspiration/ax-strategy/
---

# 5.1 AX 추진·전략
{: .fs-7 }

AX G에서 참고할 수 있는 5개 하네스 사례.
{: .fs-5 .fw-300 }

---

## 관련 부서
- AX G

## 도메인 특징
- 전사 전략·시나리오·로드맵 등 장기 관점의 분석·기획 업무
- 부서 간 협업·조율이 필요한 다영역 통합 자료
- 정량 지표와 정성 평가를 함께 다루는 보고서

## UI 실습에서 꼭 구분할 점

{: .important }
이 카테고리의 UI 예시는 **Claude Code 실행 결과를 실시간 API로 가져오는 완성 시스템**이 아닙니다. 27일 수업에서는 하네스 사례를 바탕으로, Claude Code가 만들 수 있는 산출물이 웹 화면에서 어떻게 보여야 하는지 더미 데이터로 먼저 확인합니다.

수업에서 보는 흐름은 다음 두 단계를 구분합니다.

| 단계 | 수업에서 하는 일 | 산출물 |
|---|---|---|
| 1단계: UI 프로토타입 | 하네스 사례를 읽고 더미 데이터로 업무 화면을 만든다 | `index.html`, `styles.css`, `app.js` |
| 2단계: Claude Code 산출물 연동 구조 | Claude Code가 만든 JSON/Markdown 결과를 화면에 붙이는 구조를 이해한다 | `risk-register-output.json`, `test-results.md`, `review-log.md` |

즉, 30분 미니 랩의 목표는 **하네스 산출물 → 웹 실행 화면 → 사람 승인 구조**를 이해하는 것입니다. 실제 사내 데이터 연결, 자동 실행, 승인 워크플로우 연동은 90일 PoC에서 별도로 다룹니다.

## 5개 참고 사례

| # | 사례 | 한 줄 설명 |
|---|---|---|
| [47](./47-strategy-framework) | strategy-framework | OKR·BSC·SWOT 등 전략 프레임워크 통합 작성 |
| [52](./52-scenario-planner) | scenario-planner | 핵심 변수 기반 시나리오 매트릭스·영향 분석 |
| [88](./88-risk-register) | risk-register | 리스크 식별·평가·대응 전략·모니터링 대장 |
| [64](./64-knowledge-base-builder) | knowledge-base-builder | 조직 지식관리 체계·위키·검색 인덱스 |
| [99](./99-sustainability-audit) | sustainability-audit | ESG·지속가능성 감사·개선 계획 |

---

[← 영감 라이브러리](../) · [전체 카테고리](../#6-카테고리)
