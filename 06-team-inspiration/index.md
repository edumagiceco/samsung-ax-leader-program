---
title: 5. 부서별 영감 라이브러리
nav_order: 6
has_children: true
permalink: /06-team-inspiration/
---

# 부서별 영감 라이브러리
{: .fs-8 }

부서별로 참고할 수 있는 하네스 사례 모음.
{: .fs-5 .fw-300 }

---

## 어떤 자료인가?

5/27 프로젝트 준비 시 **부서 도메인에 가까운 하네스가 어떻게 구성되는지** 참고할 수 있도록 정리한 사례입니다.

- 출처: [revfactory/harness-100](https://github.com/revfactory/harness-100) 사례 중 삼성전자판매 6팀 부서 도메인과 관련 있는 30개 선별
- 형식: 5/20 customer-support·real-estate-analyst와 같은 패턴 (5 agents + 3 skills)
- 참고용 자료이며, 본인 팀에서 어떻게 활용할지는 자유 판단

---

## 6 카테고리

| 카테고리 | 관련 부서 | 사례 수 |
|---|---|---|
| [5.1 AX 추진·전략](./ax-strategy/) | AX G | 5개 |
| [5.2 영업·매장·고객](./sales-stores/) | 영업팀 8지점·CE/백화점/Retail 전략 | 5개 |
| [5.3 재경·재무·감사](./finance/) | 재경팀 | 5개 |
| [5.4 HR·안전·지원](./hr-safety-support/) | 인사·안전환경·지원팀 | 5개 |
| [5.5 정보·보안·인프라](./info-security/) | 정보전략·정보보호 G | 5개 |
| [5.6 경영진단·KPI](./evaluation-kpi/) | 경영진단 G | 5개 |

**총 30개 참고 사례** (작성 예정)

---

## 각 카드의 구성

각 사례는 다음 정보를 담고 있습니다.

```
- 어떤 도메인의 하네스인가
- Agents 5명 구성 (도메인 전문가 4 + reviewer 1)
- Skills 3개 구성 (orchestrator + 확장 2)
- 비민감 데이터 활용 시 고려할 점
- 검증 시 일반적으로 보는 항목
```

5/20 customer-support·real-estate-analyst와 동일한 구조이며, 사실 정보 위주입니다.

---

## 활용 방향 (선택)

사례를 어떻게 활용하실지는 자유입니다. 일반적인 활용 방향은 다음과 같습니다.

- 본인 도메인과 유사한 사례의 agents·skills 구성 참고
- harness-100 원본을 통한 추가 사례 탐색
- Harness-Lab으로 본인 도메인 하네스 생성 시 시드 명령 작성에 참고

---

## 관련 정보

- [4. Harness-Lab](../04-harness-lab/) — 본인 도메인 하네스 생성 도구
- [harness-100 원본 레포](https://github.com/revfactory/harness-100) — 100개 전체 사례

---

[← Harness-Lab](../04-harness-lab/) · [AX 과제 브리프로 →](../07-ax-brief-workbook/)
