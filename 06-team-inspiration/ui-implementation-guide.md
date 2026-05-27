---
title: 5.7 UI 구현 실습 예시
parent: 5. 부서별 영감 라이브러리
nav_order: 7
permalink: /06-team-inspiration/ui-implementation-guide/
---

# 5.7 UI 구현 실습 예시
{: .fs-7 }

5.1~5.6 카테고리에서 대표 하네스 1개씩을 골라, 실제 업무 화면처럼 보이는 UI 프로토타입으로 구현해 보는 실습 가이드.
{: .fs-5 .fw-300 }

---

## 이 페이지에서 하는 것

각 하네스 사례는 원래 `agents`와 `skills`의 작업 구조를 설명합니다. 이 페이지에서는 그 구조를 **사용자가 조작할 수 있는 화면**으로 바꾸는 연습을 합니다.

- 하네스의 입력값을 UI의 폼·필터·업로드 영역으로 바꾸기
- 하네스의 agents 작업 단계를 UI의 탭·칸반·진행 상태로 바꾸기
- 하네스의 산출물을 UI의 표·차트·보고서·체크리스트로 바꾸기
- 사내 실제 데이터가 아닌 더미 데이터로 화면 흐름만 구현하기

## 중요한 전제: 지금 만드는 UI는 무엇인가?

{: .important }
이 페이지의 UI 예시는 **Claude Code 실행 결과를 실시간으로 호출하는 운영 시스템**이 아닙니다. 수업에서는 먼저 더미 데이터로 화면 구조를 만들고, 그 다음 Claude Code가 만든 JSON/Markdown 산출물을 붙이면 실제 연동 UI가 된다는 구조를 이해합니다.

구분해서 보면 다음과 같습니다.

| 구분 | 수업 중 구현 | 90일 PoC에서 확장 |
|---|---|---|
| 데이터 | 더미 데이터 | 승인된 실제 또는 비식별 업무 데이터 |
| Claude Code 결과 | 화면에 들어갈 예시 결과를 가정 | Claude Code가 생성한 `*.json`, `*.md` 파일을 읽어 표시 |
| UI 역할 | 입력, 결과, 근거, 리스크, 승인 위치를 보여주는 프로토타입 | 실제 업무 담당자가 결과를 검토하고 승인하는 실행 화면 |
| 승인 | 버튼과 상태값으로 구조만 표현 | 승인자, 로그, 수정 요청, 재실행 이력까지 기록 |

수업에서 설명할 핵심 문장은 다음입니다.

```text
오늘 만드는 UI는 Claude Code 결과를 실시간으로 호출하는 완성 시스템이 아닙니다.
1단계는 더미 데이터로 업무 화면을 만들고,
2단계는 Claude Code가 만든 JSON/Markdown 산출물을 화면에 붙이는 구조를 이해합니다.
실제 사내 데이터 연결과 승인 워크플로우는 90일 PoC에서 다룹니다.
```

### 실제 연동 구조는 이렇게 확장됩니다

```text
Claude Code 실행
  ↓
하네스 산출물 파일 생성
  - risk-register-output.json
  - test-results.md
  - review-log.md
  ↓
웹 UI가 산출물 파일을 읽음
  ↓
화면에 결과, 근거, 리스크, 승인 상태 표시
  ↓
사람이 승인 / 보류 / 수정 요청 선택
```

{: .note }
샘플 프롬프트 위의 **샘플 프롬프트 복사** 버튼을 누르면 해당 프롬프트 전체가 클립보드에 복사됩니다.

---

## 대표 예시 6개

| 카테고리 | 선별한 하네스 | UI로 만들 화면 | 선별 이유 |
|---|---|---|---|
| [5.1 AX 추진·전략](../ax-strategy/) | [47 strategy-framework](../ax-strategy/47-strategy-framework) | 전략 프레임워크 워크벤치 | OKR·BSC·SWOT·로드맵을 한 화면 흐름으로 연결하기 좋음 |
| [5.2 영업·매장·고객](../sales-stores/) | [48 sales-enablement](../sales-stores/48-sales-enablement) | 영업 제안 생성 콘솔 | 고객 분석→제안서→스크립트→팔로업 흐름이 명확함 |
| [5.3 재경·재무·감사](../finance/) | [51 investor-report](../finance/51-investor-report) | IR 리포트 빌더 | KPI·재무 수치·시장 동향·전략 메시지를 통합하기 좋음 |
| [5.4 HR·안전·지원](../hr-safety-support/) | [61 competency-modeler](../hr-safety-support/61-competency-modeler) | 역량 모델링 보드 | 직무·역량·루브릭·개발 계획을 단계별 UI로 표현하기 좋음 |
| [5.5 정보·보안·인프라](../info-security/) | [28 security-audit](../info-security/28-security-audit) | 보안 감사 대시보드 | 취약점·위험도·개선 권고·증빙 상태를 시각화하기 좋음 |
| [5.6 경영진단·KPI](../evaluation-kpi/) | [42 bi-dashboard](../evaluation-kpi/42-bi-dashboard) | KPI 대시보드 설계 도구 | KPI 정의·차트·자동 보고 흐름이 UI 실습에 적합함 |

---

## 공통 실습 절차

### 1. 실습 폴더 준비

Claude Code 작업 폴더 주소:

```text
C:\claude-practice\ui-prototypes
```

이 폴더를 만든 뒤 Claude Desktop의 Code 탭에서 이 주소를 열고 실습합니다. 카테고리별로 결과물이 섞이지 않도록, 각 프롬프트 안에는 생성될 결과 폴더의 전체 주소도 함께 적어두었습니다.

### 2. Claude Desktop Code 탭에서 폴더 선택

1. New session을 시작합니다.
2. 실습 폴더를 선택합니다.
3. 하단 상태바에 선택한 폴더명이 보이는지 확인합니다.

### 3. 아래 샘플 프롬프트 중 하나를 복사해 실행

각 프롬프트는 다음 결과를 만들도록 작성되어 있습니다.

```text
<실습명>/
├── index.html
├── styles.css
└── app.js
```

외부 빌드 도구 없이 `index.html`을 브라우저로 열 수 있는 정적 UI 프로토타입을 기준으로 합니다.

### 4. 결과 확인

생성된 폴더에서 `index.html`을 열어 다음을 확인합니다.

- 첫 화면에서 어떤 업무를 처리하는 UI인지 즉시 보이는가
- 입력 영역, 처리 단계, 산출물 영역이 분리되어 있는가
- 더미 데이터만 사용했는가
- 버튼·탭·필터 등 최소한의 상호작용이 동작하는가

---

## 프롬프트 작성 공식

샘플 프롬프트는 모두 같은 구조를 따릅니다.

```text
1. 역할 지정: "너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다."
2. 하네스 설명: 어떤 agents와 skills를 화면으로 바꿀지 설명
3. 구현 범위: index.html, styles.css, app.js로 정적 구현
4. 화면 요구사항: 레이아웃, 입력, 상태, 결과, 검증 영역
5. 데이터 규칙: 실제 사내 데이터 금지, 더미 데이터 사용
6. 완료 기준: 파일 생성, 실행 방법, 자체 점검 결과 출력
```

---

## 5.1 AX 추진·전략: strategy-framework

### 만들 UI

**전략 프레임워크 워크벤치**를 만듭니다. 사용자가 사업 과제와 목표를 입력하면, OKR·BSC·SWOT·로드맵·리뷰 상태가 한 화면에서 연결되어 보이는 UI입니다.

### 실행 방법

Claude Desktop Code 탭에서 실습 폴더를 연 뒤 아래 프롬프트를 붙여넣고 실행합니다.

```text
너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.

[Claude Code 실행 위치]
- Claude Desktop Code 탭에서 다음 폴더를 열고 이 프롬프트를 실행한다: C:\claude-practice\ui-prototypes
- 생성할 결과 폴더: C:\claude-practice\ui-prototypes\strategy-framework-ui

현재 폴더 안에 strategy-framework-ui 폴더를 만들고, 외부 빌드 도구 없이 브라우저에서 바로 열 수 있는 정적 UI 프로토타입을 구현해줘.

구현 파일은 다음 3개로 제한해줘.
- index.html
- styles.css
- app.js

주제는 "전략 프레임워크 워크벤치"다.
아래 하네스 구조를 실제 사용자가 조작할 수 있는 UI로 바꿔줘.

하네스 예시:
- 카테고리: 5.1 AX 추진·전략
- 사례: 47 strategy-framework
- 다루는 영역: OKR 설계, BSC 매핑, SWOT 분석, 비전·미션 선언문
- Agents:
  - OKR 설계자: Objectives·Key Results 구조 설계
  - BSC 분석가: Balanced Scorecard 4 perspective 매핑
  - SWOT 전문가: 내·외부 환경 분석
  - 전략문서작성자: 통합 전략 문서 작성
  - reviewer: 프레임워크 간 일관성 교차 검증
- Skills:
  - 오케스트레이터: 분석 결과를 통합 전략 문서로 연결
  - OKR-BSC 매핑 방법론: OKR과 BSC 간 정합성 점검
  - 시나리오 평가 방법론: 전략 옵션 비교·우선순위 기준

UI 요구사항:
1. 첫 화면 상단에 전략 과제명, 기간, 담당 조직을 입력하는 영역을 만들어줘.
2. 본문은 OKR, BSC, SWOT, Roadmap, Review 탭으로 구성해줘.
3. OKR 탭에는 Objective 카드와 KR 진행률 바를 보여줘.
4. BSC 탭에는 재무, 고객, 프로세스, 학습/성장 4개 관점의 매핑 표를 보여줘.
5. SWOT 탭에는 Strength, Weakness, Opportunity, Threat 4분면을 보여줘.
6. Roadmap 탭에는 분기별 실행 과제 타임라인을 보여줘.
7. Review 탭에는 reviewer가 확인할 누락, 중복, 정합성 체크리스트를 보여줘.
8. "샘플 전략 불러오기" 버튼을 누르면 더미 데이터가 채워지게 해줘.
9. "전략 초안 생성" 버튼을 누르면 오른쪽 패널에 요약 보고서가 생성되는 것처럼 보여줘.

디자인 요구사항:
- 업무용 대시보드처럼 차분하고 읽기 쉬운 화면으로 만들어줘.
- 카드 안에 또 다른 카드를 중첩하지 말아줘.
- 모바일에서도 표와 카드가 깨지지 않도록 반응형으로 만들어줘.
- 실제 삼성 또는 사내 데이터는 넣지 말고, 모두 가상의 더미 데이터로 작성해줘.

완료 후 다음을 출력해줘.
- 생성한 파일 목록
- index.html을 여는 방법
- 구현한 상호작용 목록
- 더미 데이터만 사용했는지 자체 점검 결과
```

### 확인 포인트

- OKR과 BSC가 서로 매핑되어 보이는가
- SWOT 결과가 로드맵과 연결되는가
- reviewer 체크리스트가 단순 장식이 아니라 검토 기준으로 보이는가

### risk-register로 설명하는 실제 연동 예시

AX 추진·전략 카테고리에서는 [88 risk-register](../ax-strategy/88-risk-register)도 30분 미니 랩 예시로 쓰기 좋습니다. 리스크 관리대장은 입력, AI 결과, 검증 기준, 사람 승인 상태가 분명하기 때문입니다.

교육 중에는 더미 데이터로 UI를 만들지만, 실제 연동 단계에서는 Claude Code가 아래 같은 파일을 만들고 UI가 이 파일을 읽는 구조로 확장할 수 있습니다.

```json
{
  "project": "AX 전략 리스크 관리 보드",
  "generatedBy": "Claude Code risk-register harness",
  "risks": [
    {
      "category": "운영",
      "risk": "부서별 입력 기준이 달라 리스크 평가 점수가 흔들릴 수 있음",
      "probability": 3,
      "impact": 4,
      "response": "평가 척도와 예시를 먼저 합의한 뒤 파일럿 팀 1곳에서 검증",
      "owner": "AX 추진 담당자",
      "approvalStatus": "확인 필요"
    }
  ],
  "reviewChecklist": [
    "리스크 카테고리 누락 여부",
    "평가 척도 일관성",
    "실행 책임자 명시 여부"
  ]
}
```

이때 웹 화면은 AI가 만든 결과를 그대로 확정하는 곳이 아니라, 담당자가 근거와 리스크를 확인하고 **승인 / 보류 / 수정 요청**을 선택하는 검토 화면입니다.

---

## 5.2 영업·매장·고객: sales-enablement

### 만들 UI

**영업 제안 생성 콘솔**을 만듭니다. 고객 상황을 입력하면 고객 분석, 제품 제안, 상담 스크립트, 팔로업 메시지가 단계별로 정리되는 UI입니다.

### 실행 방법

Claude Desktop Code 탭에서 실습 폴더를 연 뒤 아래 프롬프트를 붙여넣고 실행합니다.

```text
너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.

[Claude Code 실행 위치]
- Claude Desktop Code 탭에서 다음 폴더를 열고 이 프롬프트를 실행한다: C:\claude-practice\ui-prototypes
- 생성할 결과 폴더: C:\claude-practice\ui-prototypes\sales-enablement-ui

현재 폴더 안에 sales-enablement-ui 폴더를 만들고, 외부 빌드 도구 없이 브라우저에서 바로 열 수 있는 정적 UI 프로토타입을 구현해줘.

구현 파일은 다음 3개로 제한해줘.
- index.html
- styles.css
- app.js

주제는 "영업 제안 생성 콘솔"이다.
아래 하네스 구조를 실제 매장·영업 담당자가 사용할 수 있는 UI로 바꿔줘.

하네스 예시:
- 카테고리: 5.2 영업·매장·고객
- 사례: 48 sales-enablement
- 다루는 영역: 고객 페르소나·니즈 분석, 제안서 초안, 프레젠테이션 스크립트, 사후 팔로업
- Agents:
  - 고객 분석가: 페르소나·니즈·예산·결정 기준 정리
  - 제안서 작성자: 제품 조합·견적 초안 작성
  - 프레젠터: 매장·법인 응대 스크립트 작성
  - 팔로업 매니저: 사후 메시지·일정 관리
  - reviewer: 산출물 톤·정합성 교차 검증
- Skills:
  - 오케스트레이터: 분석→제안→발표→팔로업 흐름 조율
  - 견적 산출 방법론: 패키지 할인·번들·할부 계산 기준
  - 응대 화법 방법론: 강·중·약 클로징 스크립트 패턴

UI 요구사항:
1. 왼쪽에는 고객 유형, 예산 범위, 관심 제품군, 구매 시점, 상담 메모를 입력하는 패널을 만들어줘.
2. 가운데에는 고객 분석, 제안 구성, 상담 스크립트, 팔로업 4단계 진행 상태를 보여줘.
3. 오른쪽에는 제안서 미리보기 패널을 만들어줘.
4. "샘플 상담 불러오기" 버튼을 누르면 더미 상담 정보가 입력되게 해줘.
5. "제안 생성" 버튼을 누르면 추천 패키지, 예상 견적, 상담 멘트, 팔로업 메시지가 표시되게 해줘.
6. 견적은 실제 가격이 아니라 가상의 상대 금액과 예시 금액으로만 표시해줘.
7. reviewer 영역에는 가격 합계 확인, 고객 니즈 반영, 톤 검토 체크리스트를 보여줘.

디자인 요구사항:
- 반복 상담 업무에 쓰기 좋은 조밀한 업무 화면으로 만들어줘.
- 버튼에는 명확한 아이콘 또는 짧은 동사를 사용해줘.
- 긴 텍스트가 버튼이나 카드 밖으로 넘치지 않게 처리해줘.
- 실제 고객 이름, 연락처, 사내 가격 정책은 절대 넣지 말고 모두 더미 데이터로 작성해줘.

완료 후 다음을 출력해줘.
- 생성한 파일 목록
- index.html을 여는 방법
- 구현한 상호작용 목록
- 더미 데이터만 사용했는지 자체 점검 결과
```

### 확인 포인트

- 입력한 고객 정보가 제안 결과에 반영되는 것처럼 보이는가
- 제안서·스크립트·팔로업이 같은 영업 흐름 안에 있는가
- 실제 고객 개인정보나 가격 정책처럼 보이는 정보가 없는가

---

## 5.3 재경·재무·감사: investor-report

### 만들 UI

**IR 리포트 빌더**를 만듭니다. 가상의 실적 지표, KPI, 시장 동향, 전략 업데이트를 조합해 분기 보고서 초안을 구성하는 UI입니다.

### 실행 방법

Claude Desktop Code 탭에서 실습 폴더를 연 뒤 아래 프롬프트를 붙여넣고 실행합니다.

```text
너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.

[Claude Code 실행 위치]
- Claude Desktop Code 탭에서 다음 폴더를 열고 이 프롬프트를 실행한다: C:\claude-practice\ui-prototypes
- 생성할 결과 폴더: C:\claude-practice\ui-prototypes\investor-report-ui

현재 폴더 안에 investor-report-ui 폴더를 만들고, 외부 빌드 도구 없이 브라우저에서 바로 열 수 있는 정적 UI 프로토타입을 구현해줘.

구현 파일은 다음 3개로 제한해줘.
- index.html
- styles.css
- app.js

주제는 "IR 리포트 빌더"다.
아래 하네스 구조를 재경·재무 담당자가 더미 수치로 보고서 초안을 구성하는 UI로 바꿔줘.

하네스 예시:
- 카테고리: 5.3 재경·재무·감사
- 사례: 51 investor-report
- 다루는 영역: 분기·연간 실적, KPI 대시보드, 시장 동향, 전략 업데이트, 리스크 공시
- Agents:
  - 재무 분석가: 실적·재무비율·전년 대비 분석
  - KPI 설계자: 핵심 KPI 대시보드 구성
  - 시장 분석가: 산업·경쟁 동향
  - 전략 작성자: 향후 전략·가이던스
  - reviewer: 공시 기준·표현 정합성 점검
- Skills:
  - 오케스트레이터: 실적→KPI→시장→전략 통합 흐름
  - 공시 표현 방법론: IR 메시지 톤·규제 표현 기준
  - 비교 분석 방법론: YoY·QoQ·peer 비교 패턴

UI 요구사항:
1. 상단에는 보고 기간, 보고서 유형, 작성 상태를 보여줘.
2. 왼쪽에는 더미 실적 입력 표를 만들어줘. 매출, 영업이익, 성장률, 재고 회전율 같은 예시 지표를 사용해줘.
3. 가운데에는 KPI 카드, YoY/QoQ 비교 막대, 시장 동향 요약을 보여줘.
4. 오른쪽에는 IR 메시지 초안과 리스크 표현 검토 영역을 보여줘.
5. "더미 분기 데이터 불러오기" 버튼을 누르면 가상의 숫자가 채워지게 해줘.
6. "보고서 초안 생성" 버튼을 누르면 Executive Summary, KPI 해석, 시장 코멘트, 다음 액션이 표시되게 해줘.
7. reviewer 영역에는 수치 합계, 전년 대비 계산, 공시 표현 주의 문구 체크리스트를 보여줘.

디자인 요구사항:
- 재무 보고 UI이므로 숫자 정렬과 표 가독성을 우선해줘.
- 차트는 HTML/CSS/JS만으로 간단히 구현해줘. 외부 차트 라이브러리는 쓰지 말아줘.
- 미공시 실적처럼 보이는 실제 기업 수치나 회사 내부 정보는 넣지 말아줘.
- 모든 숫자와 회사명은 가상의 더미 데이터임을 화면 하단에 명시해줘.

완료 후 다음을 출력해줘.
- 생성한 파일 목록
- index.html을 여는 방법
- 구현한 상호작용 목록
- 더미 데이터만 사용했는지 자체 점검 결과
```

### 확인 포인트

- 숫자 입력, KPI 카드, 보고서 초안이 한 흐름으로 연결되는가
- 공시 표현 검토가 별도 영역으로 보이는가
- 실제 재무 수치로 오해할 정보가 없는가

---

## 5.4 HR·안전·지원: competency-modeler

### 만들 UI

**역량 모델링 보드**를 만듭니다. 직무 활동을 입력하면 필요한 역량, 행동 지표, 평가 루브릭, 개발 계획이 연결되는 UI입니다.

### 실행 방법

Claude Desktop Code 탭에서 실습 폴더를 연 뒤 아래 프롬프트를 붙여넣고 실행합니다.

```text
너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.

[Claude Code 실행 위치]
- Claude Desktop Code 탭에서 다음 폴더를 열고 이 프롬프트를 실행한다: C:\claude-practice\ui-prototypes
- 생성할 결과 폴더: C:\claude-practice\ui-prototypes\competency-modeler-ui

현재 폴더 안에 competency-modeler-ui 폴더를 만들고, 외부 빌드 도구 없이 브라우저에서 바로 열 수 있는 정적 UI 프로토타입을 구현해줘.

구현 파일은 다음 3개로 제한해줘.
- index.html
- styles.css
- app.js

주제는 "역량 모델링 보드"다.
아래 하네스 구조를 HR·지원 담당자가 직무별 역량 체계를 설계하는 UI로 바꿔줘.

하네스 예시:
- 카테고리: 5.4 HR·안전·지원
- 사례: 61 competency-modeler
- 다루는 영역: 직무 분석, 역량 사전, 평가 루브릭, 개발 계획
- Agents:
  - 직무 분석가: 직무 수행 활동·필요 역량 도출
  - 역량 사전 작성자: 행동 지표·수준 정의
  - 루브릭 설계자: 평가 기준·점수 척도
  - 개발 계획 수립자: 역량 갭별 학습 경로
  - reviewer: 직무·역량·평가 일관성 검증
- Skills:
  - 오케스트레이터: 직무→역량→루브릭→개발 흐름
  - 행동 지표 방법론: 행동 기반 척도 설계
  - 개발 경로 방법론: 70-20-10·학습 카탈로그 매핑

UI 요구사항:
1. 상단에는 직무명, 직무군, 적용 대상, 버전 상태를 입력하는 영역을 만들어줘.
2. 본문은 직무 활동, 역량 사전, 평가 루브릭, 개발 계획 4개 컬럼으로 구성해줘.
3. 각 컬럼은 카드 목록 형태로 보여주되, 카드 안에 카드를 중첩하지 말아줘.
4. "샘플 직무 불러오기" 버튼을 누르면 가상의 직무 활동과 역량 예시가 채워지게 해줘.
5. "역량 모델 생성" 버튼을 누르면 역량 정의, 행동 지표, 1~5수준 루브릭, 개발 추천이 표시되게 해줘.
6. reviewer 영역에는 직무 활동과 역량의 매핑 누락, 평가 가능성, 개발 계획 연결성 체크리스트를 보여줘.
7. 개인정보나 실제 평가 등급을 입력하는 필드는 만들지 말아줘.

디자인 요구사항:
- HR 담당자가 반복적으로 검토하기 좋은 보드형 업무 UI로 만들어줘.
- 상태 배지는 Draft, Review, Approved 정도의 더미 상태만 사용해줘.
- 모바일에서는 4개 컬럼이 세로로 자연스럽게 쌓이게 해줘.
- 실제 임직원 이름, 평가 결과, 조직 개편 정보는 넣지 말아줘.

완료 후 다음을 출력해줘.
- 생성한 파일 목록
- index.html을 여는 방법
- 구현한 상호작용 목록
- 더미 데이터만 사용했는지 자체 점검 결과
```

### 확인 포인트

- 직무 활동이 역량과 루브릭으로 자연스럽게 이어지는가
- 평가보다는 역량 체계 설계 화면으로 보이는가
- 개인정보 입력을 유도하지 않는가

---

## 5.5 정보·보안·인프라: security-audit

### 만들 UI

**보안 감사 대시보드**를 만듭니다. 자산 점검, 취약점 위험도, 개선 권고, 증빙 상태를 통합 관리하는 UI입니다.

### 실행 방법

Claude Desktop Code 탭에서 실습 폴더를 연 뒤 아래 프롬프트를 붙여넣고 실행합니다.

```text
너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.

[Claude Code 실행 위치]
- Claude Desktop Code 탭에서 다음 폴더를 열고 이 프롬프트를 실행한다: C:\claude-practice\ui-prototypes
- 생성할 결과 폴더: C:\claude-practice\ui-prototypes\security-audit-ui

현재 폴더 안에 security-audit-ui 폴더를 만들고, 외부 빌드 도구 없이 브라우저에서 바로 열 수 있는 정적 UI 프로토타입을 구현해줘.

구현 파일은 다음 3개로 제한해줘.
- index.html
- styles.css
- app.js

주제는 "보안 감사 대시보드"다.
아래 하네스 구조를 정보보호 담당자가 점검 현황을 검토하는 UI로 바꿔줘.

하네스 예시:
- 카테고리: 5.5 정보·보안·인프라
- 사례: 28 security-audit
- 다루는 영역: 자산·취약점 스캔, 코드 분석, 침투 테스트, 보고서 작성
- Agents:
  - 취약점 스캐너: 자산·서비스 스캔·CVE 매핑
  - 코드 분석가: 정적 분석·시큐어 코딩 점검
  - 침투 테스터: 시나리오 기반 모의 침투
  - 보안 컨설턴트: 우선순위·개선 권고
  - reviewer: 위험도·증빙 정합성 검증
- Skills:
  - 오케스트레이터: 스캔→분석→테스트→권고 흐름
  - 위험도 평가 방법론: CVSS·우선순위 매트릭스
  - 개선 권고 방법론: 단기·중기·장기 분류

UI 요구사항:
1. 상단에는 감사 범위, 점검 기간, 전체 위험 점수, 완료율을 보여줘.
2. 왼쪽에는 더미 자산 목록과 위험도 필터를 만들어줘.
3. 가운데에는 취약점 테이블을 만들어줘. 항목은 가상의 ID, 심각도, 영향 범위, 상태, 담당 역할로 구성해줘.
4. 오른쪽에는 개선 권고 패널과 증빙 체크리스트를 보여줘.
5. "더미 감사 결과 불러오기" 버튼을 누르면 가상의 취약점 목록이 표시되게 해줘.
6. "개선 우선순위 계산" 버튼을 누르면 Critical, High, Medium 순으로 재정렬되고 권고 문구가 표시되게 해줘.
7. reviewer 영역에는 위험도 기준, 재현 증빙, 책임자·기한 명시 여부를 체크하는 항목을 보여줘.

디자인 요구사항:
- 보안 정보가 과장되거나 공격 절차처럼 보이지 않게, 관리·감사 중심 UI로 만들어줘.
- 실제 IP, 도메인, 시스템명, CVE 상세 악용 절차는 넣지 말아줘.
- 모든 자산명과 취약점 ID는 가상의 더미 데이터로 작성해줘.
- 색상만으로 위험도를 구분하지 말고 텍스트 라벨도 함께 보여줘.

완료 후 다음을 출력해줘.
- 생성한 파일 목록
- index.html을 여는 방법
- 구현한 상호작용 목록
- 더미 데이터만 사용했는지 자체 점검 결과
```

### 확인 포인트

- 보안 공격 방법이 아니라 감사·개선 관리 화면으로 보이는가
- 위험도와 개선 우선순위가 명확히 구분되는가
- 실제 시스템 정보처럼 보이는 값이 없는가

---

## 5.6 경영진단·KPI: bi-dashboard

### 만들 UI

**KPI 대시보드 설계 도구**를 만듭니다. KPI 정의, 데이터 소스, 시각화 카드, 자동 보고 설정을 한 화면에서 구성하는 UI입니다.

### 실행 방법

Claude Desktop Code 탭에서 실습 폴더를 연 뒤 아래 프롬프트를 붙여넣고 실행합니다.

```text
너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.

[Claude Code 실행 위치]
- Claude Desktop Code 탭에서 다음 폴더를 열고 이 프롬프트를 실행한다: C:\claude-practice\ui-prototypes
- 생성할 결과 폴더: C:\claude-practice\ui-prototypes\bi-dashboard-ui

현재 폴더 안에 bi-dashboard-ui 폴더를 만들고, 외부 빌드 도구 없이 브라우저에서 바로 열 수 있는 정적 UI 프로토타입을 구현해줘.

구현 파일은 다음 3개로 제한해줘.
- index.html
- styles.css
- app.js

주제는 "KPI 대시보드 설계 도구"다.
아래 하네스 구조를 경영진단 담당자가 KPI와 보고 화면을 설계하는 UI로 바꿔줘.

하네스 예시:
- 카테고리: 5.6 경영진단·KPI
- 사례: 42 bi-dashboard
- 다루는 영역: 데이터 소스·웨어하우스, KPI 정의, 시각화, 자동 보고
- Agents:
  - 데이터 엔지니어: 소스·웨어하우스 매핑
  - KPI 설계자: KPI 정의·계산 공식
  - 대시보드 빌더: 시각화·레이아웃
  - 보고서 자동화: 정기 보고 양식·전송
  - reviewer: KPI 정의·계산 정합성 검증
- Skills:
  - 오케스트레이터: 데이터→KPI→대시보드→보고 흐름
  - KPI 표준 방법론: KPI 정의서·메타데이터 패턴
  - 시각화 방법론: 차트 선택·색상·접근성 기준

UI 요구사항:
1. 상단에는 대시보드명, 대상 조직, 갱신 주기, 데이터 상태를 보여줘.
2. 왼쪽에는 데이터 소스 목록과 KPI 정의 입력 영역을 만들어줘.
3. 가운데에는 KPI 카드, 추세 차트, 목표 대비 실적 막대, 이상치 알림을 보여줘.
4. 오른쪽에는 자동 보고 설정과 reviewer 검증 체크리스트를 보여줘.
5. "샘플 KPI 불러오기" 버튼을 누르면 더미 KPI와 더미 차트 데이터가 채워지게 해줘.
6. "대시보드 구성" 버튼을 누르면 선택한 KPI가 카드와 차트에 반영되는 것처럼 보여줘.
7. reviewer 영역에는 KPI 공식, 원천 데이터, 갱신 주기, 접근성 기준 체크 항목을 보여줘.

디자인 요구사항:
- 실제 운영 대시보드처럼 정보 밀도가 있으면서도 한눈에 스캔 가능하게 만들어줘.
- 외부 차트 라이브러리는 사용하지 말고 HTML/CSS/JS로 간단한 차트를 만들어줘.
- 실제 사내 KPI 수치, 조직별 실적, 고객 데이터는 넣지 말아줘.
- 모든 값은 더미 데이터이며 화면 하단에 "실습용 예시 데이터"라고 표시해줘.

완료 후 다음을 출력해줘.
- 생성한 파일 목록
- index.html을 여는 방법
- 구현한 상호작용 목록
- 더미 데이터만 사용했는지 자체 점검 결과
```

### 확인 포인트

- KPI 정의와 차트가 같은 지표를 가리키는가
- 자동 보고 설정과 reviewer 검증이 업무 흐름 안에 있는가
- 대시보드가 단순 그래픽이 아니라 의사결정 화면처럼 보이는가

---

## 실습 후 개선 프롬프트

1차 결과를 확인한 뒤에는 아래 프롬프트로 화면 품질을 한 번 더 높일 수 있습니다.

```text
Claude Desktop Code 탭에서 방금 만든 결과 폴더를 열고 실행한다.
예: C:\claude-practice\ui-prototypes\strategy-framework-ui

방금 만든 UI를 검토해서 다음 기준으로 개선해줘.

1. 첫 화면에서 사용자가 해야 할 일이 5초 안에 이해되는지 확인해줘.
2. 입력 영역, 처리 단계, 산출물 영역이 명확히 분리되도록 레이아웃을 다듬어줘.
3. 버튼, 탭, 필터, 체크리스트의 상호작용이 실제로 동작하는지 점검해줘.
4. 모바일 화면에서 텍스트가 겹치거나 버튼 밖으로 넘치지 않게 수정해줘.
5. 실제 사내 데이터처럼 보이는 값이 있다면 모두 더미 데이터로 바꿔줘.
6. 수정 후 변경한 파일과 확인 방법을 요약해줘.
```

---

## 최종 체크리스트

UI 구현이 끝나면 아래 항목을 확인합니다.

| 점검 항목 | 확인 기준 |
|---|---|
| 하네스 구조 반영 | agents의 역할이 화면 섹션이나 작업 단계로 표현되어 있는가 |
| 산출물 표현 | 보고서, 표, 차트, 체크리스트 등 최종 결과가 보이는가 |
| 상호작용 | 샘플 데이터 불러오기, 생성, 필터, 탭 전환 중 1개 이상이 동작하는가 |
| 더미 데이터 | 실제 고객·사원·재무·보안·KPI 데이터가 없는가 |
| 반응형 | 브라우저 폭을 줄여도 텍스트와 버튼이 겹치지 않는가 |
| 실행 가능성 | `index.html`을 열었을 때 별도 설치 없이 화면이 보이는가 |

---

<style>
  .ui-prompt-copy-toolbar {
    display: flex;
    justify-content: flex-end;
    margin: 1rem 0 0.35rem;
  }

  .ui-prompt-copy-button {
    border: 1px solid #d2d8e5;
    border-radius: 6px;
    background: #ffffff;
    color: #1f2a44;
    cursor: pointer;
    font-size: 0.84rem;
    font-weight: 700;
    line-height: 1;
    padding: 0.55rem 0.75rem;
  }

  .ui-prompt-copy-button:hover {
    border-color: #1f5eff;
    color: #0b45d9;
  }

  .ui-prompt-copy-button.is-copied {
    border-color: #16834a;
    color: #16834a;
  }

  .ui-prompt-copy-button.is-error {
    border-color: #b42318;
    color: #b42318;
  }
</style>

<script>
  (function () {
    function fallbackCopy(text) {
      return new Promise(function (resolve, reject) {
        var copied = false;
        var textarea = document.createElement('textarea');

        function onCopy(event) {
          if (event.clipboardData) {
            event.clipboardData.setData('text/plain', text);
            event.preventDefault();
            copied = true;
          }
        }

        textarea.value = text;
        textarea.setAttribute('readonly', '');
        textarea.style.position = 'fixed';
        textarea.style.top = '-9999px';
        textarea.style.left = '-9999px';
        document.body.appendChild(textarea);
        textarea.focus();
        textarea.select();

        document.addEventListener('copy', onCopy);

        try {
          var ok = document.execCommand('copy');
          if (ok || copied) {
            resolve();
          } else {
            reject(new Error('copy command was blocked'));
          }
        } catch (error) {
          reject(error);
        } finally {
          document.removeEventListener('copy', onCopy);
          document.body.removeChild(textarea);
        }
      });
    }

    function copyToClipboard(text) {
      var clipboard = window.navigator && window.navigator.clipboard;

      if (clipboard && window.isSecureContext) {
        return clipboard.writeText(text).catch(function () {
          return fallbackCopy(text);
        });
      }
      return fallbackCopy(text);
    }

    function isSamplePrompt(text) {
      return text.indexOf('너는 업무용 UI 프로토타입을 만드는 프론트엔드 디자이너이자 개발자다.') === 0 ||
        text.indexOf('Claude Desktop Code 탭에서 방금 만든 결과 폴더를 열고 실행한다.') === 0;
    }

    function selectCodeBlock(code) {
      var selection = window.getSelection && window.getSelection();
      if (!selection) return;

      var range = document.createRange();
      range.selectNodeContents(code);
      selection.removeAllRanges();
      selection.addRange(range);
    }

    function enhancePromptBlocks() {
      var blocks = document.querySelectorAll('.language-text.highlighter-rouge');

      blocks.forEach(function (block) {
        var code = block.querySelector('pre code');
        if (!code) return;

        var text = (code.innerText || code.textContent || '').trimEnd();
        if (!isSamplePrompt(text)) return;
        if (block.previousElementSibling && block.previousElementSibling.classList.contains('ui-prompt-copy-toolbar')) return;

        var toolbar = document.createElement('div');
        toolbar.className = 'ui-prompt-copy-toolbar';

        var button = document.createElement('button');
        button.type = 'button';
        button.className = 'ui-prompt-copy-button';
        button.textContent = '샘플 프롬프트 복사';
        button.setAttribute('aria-label', '샘플 프롬프트를 클립보드에 복사');

        button.addEventListener('click', function () {
          copyToClipboard(text).then(function () {
            button.classList.remove('is-error');
            button.classList.add('is-copied');
            button.textContent = '복사 완료';
            window.setTimeout(function () {
              button.classList.remove('is-copied');
              button.textContent = '샘플 프롬프트 복사';
            }, 1600);
          }).catch(function () {
            selectCodeBlock(code);
            button.classList.add('is-error');
            button.textContent = '복사 차단 - Ctrl+C';
          });
        });

        toolbar.appendChild(button);
        block.parentNode.insertBefore(toolbar, block);
      });
    }

    if (document.readyState === 'loading') {
      document.addEventListener('DOMContentLoaded', enhancePromptBlocks);
    } else {
      enhancePromptBlocks();
    }
  }());
</script>

---

[← 5. 부서별 영감 라이브러리](../) · [4. Harness-Lab](../../04-harness-lab/)
