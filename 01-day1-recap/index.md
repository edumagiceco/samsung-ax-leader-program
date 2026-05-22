---
title: 1. Day 1 (5/20) 안내
nav_order: 2
permalink: /01-day1-recap/
---

# Day 1 (5/20) 안내
{: .fs-8 }

5/20에 무엇을 했는지 한눈에 보기 + 다시 따라하기 위한 위치 안내.
{: .fs-5 .fw-300 }

---

## 5/20 하루 흐름

| 시간 | 무엇을 했나 | 강사 | 자료 위치 |
|---|---|---|---|
| 10:00-10:15 | 오리엔테이션 + 데이터 보안 | 최재규 · 삼성전자판매 | PBT LMS |
| 10:15-12:30 | AI 기술 트렌드 강의 5챕터 + AI 하네스 A to Z | 최재규 | PBT LMS (임원교육 오전세션 PDF) |
| 14:00-15:30 | **Claude Cowork 실습** (AI 비서 · 영수증 정리) | 권상윤 | 본인 노트북 결과물 + PBT LMS |
| 15:40-17:50 | **Claude Code 하네스 실습 3종** ⭐ | 안병희 · 최재규 | 본인 PC `C:\claude-practice\` |
| 17:50-18:00 | AI 업무 정의서 워크시트 안내 | 최재규 | [→ 6. AX 과제 브리프 워크북](../07-ax-brief-workbook/) |

## 강의 자료는 어디에?

{: .important }
> **5/20 강의 슬라이드·실습 가이드·오리엔테이션 자료는 PBT LMS에 있습니다.**
>
> [https://pbt.co.kr/](https://pbt.co.kr/) → 'AX 리더 실전 프로그램 with 삼성전자판매' 캠페인 → 좌측 '캠페인 활동'
>
> 이 사이트는 회고가 아니라 **본인이 5/27까지 본인 일에 적용하기 위한 작업실**입니다.

---

## 5/20에 사용한 3개 하네스 — 다시 따라하기

본인 PC `C:\claude-practice\`에 이미 다운로드되어 있을 겁니다. 만약 없으면 [2. 환경 다시 점검](../02-environment/)을 보세요.

### 🔵 실습 1: customer-support
시니어 고객 응대 매뉴얼 자동화

```
폴더: C:\claude-practice\customer-support
실행: /customer-support 6,70대 스마트폰 고객을 위한 응대 매뉴얼 작성해줘
산출물: customer-support\_workspace\ 안의 3개 파일
구성: 5 agents (cs-analyst, cs-reviewer, escalation-manager, faq-builder, response-specialist)
     + 3 skills (csat-analyzer, customer-support, escalation-flowchart)
모드: Sonnet 4.6 · 작업량 낮음
```

### 🟢 실습 2: real-estate-analyst
신규 출점 후보지역 검토

```
폴더: C:\claude-practice\real-estate-analyst
실행: /real-estate-analyst 서울 성수동에 삼성스토어 입점을 기획하고 있어. 입지분석과 리스크 평가를 진행해줘
산출물: real-estate-analyst\_workspace\ 안의 4개 파일
구성: 5 agents (location-analyst, market-researcher, profitability-analyst, report-writer, risk-assessor)
     + 3 skills (cap-rate-calculator, location-scoring, real-estate-analyst)
모드: Sonnet 4.6 · 작업량 낮음
```

### 🟣 실습 3: harness-lab ⭐
하네스를 생성하는 하네스 — **5/27 본인 하네스 MVP 제작의 핵심 도구**

```
폴더: C:\claude-practice\harness-lab
실행: /harness-lab [본인이 만들고 싶은 하네스 한 줄 설명]
산출물: harness-lab 폴더 안에 새 하네스 자동 생성
구성: 실행 시 동적 생성 (도메인에 맞는 5+3 자동 설계)
모드: 자동 모드 · Opus 4.7 1M · 작업량 매우 높음
```

→ Harness-Lab 풀가이드는 별도 섹션: [→ 4. Harness-Lab](../04-harness-lab/)

---

## 다음 단계

5/21-26 작업과 5/27 발표 준비에 활용할 수 있는 섹션입니다.

| 다음 액션 | 어디로 |
|---|---|
| 환경이 갑자기 안 될 때 | [2. 환경 다시 점검](../02-environment/) |
| 하네스 구조 이해하고 싶을 때 | [3. 하네스 구조 이해](../03-harness-anatomy/) |
| 본인 부서용 하네스 만들기 | [4. Harness-Lab ⭐](../04-harness-lab/) |
| 부서별 참고 사례 둘러보기 | [5. 부서별 영감 라이브러리](../06-team-inspiration/) |
| 5/27 발표 7개 항목 안내 | [6. AX 과제 브리프 안내](../07-ax-brief-workbook/) |
| 강의장·운영 채널 안내 | [7. 부록](../09-appendix/) |

---

[← 홈](../) · [환경 점검으로 →](../02-environment/)
