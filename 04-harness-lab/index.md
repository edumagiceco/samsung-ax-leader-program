---
title: 4. Harness-Lab
nav_order: 5
permalink: /04-harness-lab/
---

# Harness-Lab
{: .fs-8 }

5/20에 사용한 세 번째 하네스. **하네스를 생성하는 하네스**로, 5/27 프로젝트에서 활용 가능한 도구입니다.
{: .fs-5 .fw-300 }

---

## Harness-Lab이란?

5/20에 본 customer-support·real-estate-analyst는 누군가가 미리 만들어 둔 하네스를 다운로드해서 사용했습니다. Harness-Lab은 **그 "미리 만드는 단계"를 자동화하는 하네스**입니다.

명령 한 줄로 폴더·agents·skills·orchestrator가 자동 생성됩니다.

---

## 권장 설정

다른 두 실습과 다른 모드 설정이 필요합니다.

| 항목 | 값 |
|---|---|
| 모드 | 자동 모드 |
| 모델 | Opus 4.7 1M |
| 작업량 | 매우 높음 |

설정 위치: Claude Desktop Code 탭 하단 상태바 클릭

---

## 실행 절차 (5/20 진행 동일)

### 1. harness-lab 폴더 준비
- `C:\claude-practice\max-samsung-harness-samples\harness-lab` 폴더를 복사
- `C:\claude-practice\harness-lab`에 붙여넣기

### 2. Claude Desktop에서 폴더 선택
- New session → 폴더 선택 → `C:\claude-practice\harness-lab` 선택
- 하단에 `harness-lab` 표시 확인

### 3. 실행 명령 형식

```
/harness-lab [만들고 싶은 하네스 한 줄 설명]
```

5/20 시연 예시:
```
/harness-lab 가족 여행 준비 하네스 만들어줘
```

### 4. 생성 결과 확인
- `harness-lab` 폴더 안에 새 하위 폴더가 생성됨 (예: `trip-planning/`)
- 그 안에 `.claude/agents/`, `.claude/skills/`가 자동 작성됨

### 5. 생성된 하네스 실행

New session → 폴더 선택 → 새로 만들어진 폴더 선택 → 실행

```
/<생성된 오케스트레이터> [구체적 요청]
```

5/20 시연 예시:
```
/trip-planning-orchestrator 제주도 2박3일 가족여행 계획 세워줘
```

---

## 생성되는 구조

명령 한 번으로 다음이 자동 생성됩니다.

```
<생성된 폴더>/
└── .claude/
    ├── agents/                ← 도메인 전문가 5명
    │   ├── <전문가-1>.md
    │   ├── <전문가-2>.md
    │   ├── <전문가-3>.md
    │   ├── <전문가-4>.md
    │   └── <reviewer>.md
    └── skills/
        ├── <오케스트레이터>/skill.md
        ├── <확장 스킬 1>/skill.md
        └── <확장 스킬 2>/skill.md
```

5/20 시연(가족 여행 하네스)에서 생성된 실제 결과:

- **Agents**: budget-safety-reviewer · family-needs-collector · itinerary-planner · packing-checklist-writer · trip-researcher
- **Skills**: budget-safety-review · family-needs-collection · itinerary-design · packing-checklist · trip-planning-orchestrator · trip-research

---

## 참고 사항

- 시드 명령이 구체적일수록 결과가 풍부해집니다 (도메인·역할·산출물 형태가 명확하면 더 상세한 하네스 생성)
- Opus 4.7 1M · 매우 높음 설정을 안 하면 실패할 수 있습니다 (토큰 사용량 큼)
- 생성된 하네스도 customer-support·real-estate-analyst와 동일한 구조를 따릅니다

---

## 관련 정보

- [3. 하네스 구조 이해](../03-harness-anatomy/) — `.claude/`, agents, skills 표준 구조
- [1. Day 1 (5/20) 안내](../01-day1-recap/) — customer-support·real-estate-analyst 실행 명령어 카드

---

[← 하네스 구조](../03-harness-anatomy/) · [영감 라이브러리로 →](../06-team-inspiration/)
