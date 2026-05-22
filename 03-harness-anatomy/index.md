---
title: 3. 하네스 구조 이해
nav_order: 4
permalink: /03-harness-anatomy/
---

# 하네스 구조 이해
{: .fs-8 }

5/20에 본 3개 하네스가 모두 같은 구조입니다. **이 구조를 알면 본인 부서용 하네스를 직접 만들 수 있습니다.**
{: .fs-5 .fw-300 }

---

## `.claude/` 폴더 구조

모든 하네스는 다음 구조를 따릅니다.

```
<하네스 이름>/
└── .claude/
    ├── CLAUDE.md              ← 이 하네스는 무엇이고 어떻게 쓰는지
    ├── agents/                ← AI 직원 5명의 명함
    │   ├── <전문가-1>.md
    │   ├── <전문가-2>.md
    │   ├── <전문가-3>.md
    │   ├── <전문가-4>.md
    │   └── <reviewer>.md      ← 교차 검증·통합 담당
    └── skills/
        ├── <도메인>/skill.md  ← 오케스트레이터 (전체 흐름 조율)
        └── <확장 스킬>/
            └── skill.md       ← 특정 에이전트의 전문성 확장 (방법론)
```

## 5/20에 본 3개 하네스 비교

| 부위 | customer-support | real-estate-analyst | harness-lab |
|---|---|---|---|
| 도메인 | 시니어 고객 응대 매뉴얼 | 신규 출점 후보지역 검토 | 하네스 자체 생성 |
| Agents 5명 | cs-analyst<br>cs-reviewer<br>escalation-manager<br>faq-builder<br>response-specialist | location-analyst<br>market-researcher<br>profitability-analyst<br>report-writer<br>risk-assessor | (실행 시 동적 생성) |
| Skills | csat-analyzer<br>customer-support (오케스트레이터)<br>escalation-flowchart | cap-rate-calculator<br>location-scoring<br>real-estate-analyst (오케스트레이터) | (실행 시 동적 생성) |
| 실행 명령 | `/customer-support [요청]` | `/real-estate-analyst [요청]` | `/harness-lab [도메인] 하네스 만들어줘` |

→ **공통점**: 모두 도메인 전문가 4명 + reviewer 1명 + 오케스트레이터 1개 + 확장 스킬 2개 = **5+3 = 표준 패턴**

---

## 각 부위 자세히 보기 (작성 중)

- 3.1 CLAUDE.md 표준 템플릿 — 본인 하네스의 첫 페이지를 이렇게 씁니다
- 3.2 Agents 작성법 — 도메인 전문가 4명의 명함 만들기
- 3.3 Skills 작성법 (오케스트레이터) — 5명을 어떻게 순서대로 일하게 할지
- 3.4 Skills 작성법 (확장 스킬) — 특정 방법론을 한 곳에 모으기
- 3.5 Reviewer 에이전트 — 왜 항상 5번째에 필요한가

{: .note }
> 이 섹션의 상세 내용은 Phase 2에서 채워집니다. 지금은 위 비교표를 보면서 **본인이 만들 하네스는 이 패턴을 따라가면 된다**는 점만 기억하세요.

---

## 본인 하네스를 만들기 전 자가 점검

다음에 답할 수 있다면 [4. Harness-Lab](../04-harness-lab/)으로 넘어가도 됩니다.

- [ ] 내가 매일 하는 일 중 **자동화하고 싶은 일 1가지**
- [ ] 그 일을 처리할 때 필요한 **전문성 4가지** (예: 시장조사·수익성·리스크·보고서)
- [ ] **검증을 누구에게 받고 싶은가** (reviewer의 역할)
- [ ] 결과물이 어떤 **파일 형태**여야 하나 (DOCX·MD·표 등)

위 4가지가 정리되면 본인 하네스의 뼈대가 완성됩니다.

---

[← 환경 점검](../02-environment/) · [Harness-Lab으로 →](../04-harness-lab/)
