---
title: 9. 앞으로 진행할 활동
nav_order: 10
permalink: /09-next-activities/
---

# 앞으로 진행할 활동
{: .fs-8 }

수업에서 만든 AI 하네스를 한 번의 실습으로 끝내지 않고, 실제 팀 업무에 맞게 계속 학습·개선하기 위한 후속 활동 가이드입니다.
{: .fs-5 .fw-300 }

---

## 1. 수업 후 4주 학습 루틴

AI 하네스는 한 번 만든 프롬프트가 아니라, **업무 기준·자료·검증·승인·기록을 반복 개선하는 운영 구조**입니다. 수업 후에는 아래 순서로 작게 반복하는 것이 좋습니다.

| 주차 | 목표 | 할 일 | 남길 산출물 |
|---|---|---|---|
| 1주차 | 수업 내용 재현 | Day 2에서 만든 하네스 폴더를 다시 열고 같은 테스트 질문을 실행 | `test-results.md` 보강 |
| 2주차 | 우리 팀 업무에 맞게 수정 | `CLAUDE.md`, Skill, 금지정보, Reviewer 기준을 팀 표현으로 바꿈 | `CLAUDE.md`, `SKILL.md` 개선본 |
| 3주차 | UI·승인 구조 추가 | 결과를 웹 화면 또는 스토리보드로 바꾸고 승인/보류/수정 요청 상태를 표시 | UI 캡처, 승인 기준 |
| 4주차 | PoC 후보 정리 | 실제 적용 가능성, 필요한 자료 승인, 리스크, 기대 효과를 정리 | 4주 검증 결과, 90일 PoC 후보 |

{: .important }
처음부터 자동화 범위를 크게 잡지 마세요. 좋은 후속 활동은 “작은 업무 장면 1개”를 정하고, 같은 질문을 반복 실행하면서 결과 품질을 높이는 방식입니다.

---

## 2. 매주 반복할 하네스 개선 질문

매주 팀 회의에서 아래 질문만 확인해도 하네스 품질이 좋아집니다.

| 점검 질문 | 확인할 것 |
|---|---|
| AI가 맡을 일과 사람이 승인할 일이 분리되어 있는가? | 결과 초안과 최종 판단이 섞이지 않았는지 |
| 입력 자료가 비민감 자료로 충분히 재현되는가? | 고객정보·실적·영업기밀 없이 구조 검증이 가능한지 |
| 답변 금지 또는 확인 필요 기준이 명확한가? | 오안내, 개인정보, 근거 부족, 예측 단정 방지 |
| 테스트 질문이 성공/부분성공/실패를 구분하는가? | 좋은 질문뿐 아니라 실패 유도 질문도 있는지 |
| 결과가 화면에서 검토 가능한가? | 근거, 리스크, 승인 상태가 UI 또는 문서에 보이는지 |

---

## 3. PBT LMS 활용 방법

[PBT LMS](https://pbt.co.kr/)는 공식 강의자료와 제출·공지 확인 채널입니다. 이 사이트는 보조 자료이므로, 최종 공지와 공식 자료는 PBT를 우선 확인합니다.

| 용도 | 활용 방법 |
|---|---|
| 강의자료 복습 | `AX 리더 실전 프로그램 with 삼성전자판매` 캠페인에서 슬라이드와 실습자료 확인 |
| 과제 정리 | Day 2 발표자료, 4주 검증 계획, 팀별 산출물을 제출하거나 보관 |
| 공지 확인 | 일정, 제출 방식, 추가 안내가 바뀌면 PBT 공지를 우선 확인 |
| 개인 복습 | 본인이 놓친 개념을 다시 보고 팀 하네스에 반영 |

PBT에 올릴 때는 파일명을 아래처럼 통일하면 이후 추적이 쉽습니다.

```text
[팀명]_AX과제브리프_YYYYMMDD.md
[팀명]_하네스테스트로그_YYYYMMDD.md
[팀명]_4주검증계획_YYYYMMDD.md
```

---

## 4. 오픈채팅방 활용 방법

[카카오톡 오픈채팅방](https://open.kakao.com/o/g0ligxvi)은 실습 중 막힌 지점, 환경 문제, 하네스 개선 질문을 빠르게 공유하는 채널입니다.

질문할 때는 아래 형식을 권장합니다.

```text
[팀/부서]
[질문 유형] 환경 / 하네스 / UI / 테스트 / 발표
[하려던 일]
[막힌 지점]
[이미 시도한 것]
[공유 가능한 캡처 또는 오류 메시지]
```

{: .warning }
오픈채팅방에는 실제 고객 개인정보, 실제 매출·마진·프로모션 조건, 내부 전략 문서 원문을 올리지 않습니다. 필요한 경우 값은 더미 데이터로 바꾸고, 구조만 공유합니다.

---

## 5. 먼저 볼 공식 참고 웹페이지

공식 문서는 기능 이름과 사용법이 계속 바뀌므로, 블로그나 영상보다 먼저 확인하는 것이 좋습니다.

| 구분 | 추천 링크 | 볼 때의 관점 |
|---|---|---|
| Anthropic Claude 문서 | [Claude API Docs](https://docs.anthropic.com/) | Claude의 기본 사용 방식, 모델·도구·안전 기준 확인 |
| Claude Code 문서 | [Claude Code Docs](https://code.claude.com/docs/en/overview) | Claude Code로 파일·코드·프로젝트를 다루는 방식 학습 |
| Anthropic News | [Anthropic News](https://www.anthropic.com/news) | Claude, Claude Code, 조직용 기능 업데이트 확인 |
| Anthropic Engineering | [Anthropic Engineering](https://www.anthropic.com/engineering) | 실제 엔지니어링 사례와 시스템 설계 관점 학습 |
| OpenAI Developers | [OpenAI Developers](https://developers.openai.com/) | OpenAI API, Codex, Apps SDK, Agents 관련 입구 |
| OpenAI API Docs | [OpenAI API Docs](https://platform.openai.com/docs) | 모델, 도구 사용, 구조화 출력, 에이전트 구현 참고 |
| OpenAI Cookbook | [OpenAI Cookbook](https://cookbook.openai.com/) | 실제 코드 예제, 에이전트·평가·검색 구현 패턴 학습 |
| OpenAI News | [OpenAI News](https://openai.com/news/) | 최신 제품 발표와 활용 사례 확인 |

---

## 6. 블로그를 읽는 방법

블로그는 “새 기능 소개”로만 읽지 말고, 우리 팀 하네스에 반영할 운영 질문으로 바꿔 읽습니다.

| 읽을 때 볼 것 | 우리 팀에 던질 질문 |
|---|---|
| Agent, tool, connector 기능 | 우리 하네스에서 AI가 읽을 자료와 쓰면 안 되는 자료는 무엇인가? |
| Code agent 사례 | Claude Code가 만들어야 할 산출물 파일은 무엇인가? |
| Evaluation, guardrail 사례 | 우리 하네스의 실패 기준과 중단 기준은 무엇인가? |
| UI, app, workflow 사례 | 결과를 사람이 승인하기 좋은 화면은 어떤 구조인가? |

추천 읽기 순서:

1. 공식 문서에서 기능의 현재 이름과 제약 확인
2. 공식 블로그에서 활용 사례 확인
3. Cookbook이나 예제 코드에서 구현 패턴 확인
4. 우리 팀 하네스의 `CLAUDE.md`, `SKILL.md`, `reviewer.md`에 반영

---

## 7. 추천 YouTube 채널

영상은 전체 흐름을 잡는 데 좋지만, 실제 적용은 반드시 공식 문서와 팀 테스트 로그로 확인합니다.

| 채널 | 추천 이유 | 활용 방법 |
|---|---|---|
| [OpenAI](https://www.youtube.com/@OpenAI) | OpenAI 주요 발표와 데모 확인 | 제품 방향과 사용 사례 파악 |
| [OpenAI Developers](https://www.youtube.com/@OpenAIDevelopers) | 개발자용 API·앱·에이전트 영상 | 기술 담당자가 구현 감을 잡을 때 |
| [Anthropic](https://www.youtube.com/@anthropic-ai) | Claude와 Claude Code 관련 발표·데모 | Claude Code 활용 흐름 확인 |
| [Andrej Karpathy](https://www.youtube.com/@AndrejKarpathy) | LLM·딥러닝 기초를 원리부터 설명 | 기술 리더가 개념 기반을 다질 때 |
| [Latent Space](https://www.youtube.com/@LatentSpacePod) | AI Engineer 관점의 장기 인터뷰·토론 | 에이전트, RAG, 제품화 흐름 이해 |
| [AI Engineer](https://www.youtube.com/@aiDotEngineer) | AI 엔지니어링 컨퍼런스·실무 사례 | 하네스/에이전트의 산업 적용 사례 참고 |
| [LangChain](https://www.youtube.com/@LangChain) | 에이전트·RAG·워크플로우 구현 사례 | 도구 연결과 멀티스텝 앱 구조 참고 |
| [Hugging Face](https://www.youtube.com/@huggingface) | 오픈소스 모델·데이터셋·트랜스포머 생태계 | 모델과 데이터 생태계 감 잡기 |
| [DeepLearning.AI](https://www.youtube.com/@Deeplearningai) | Andrew Ng 계열의 실무 AI 교육 | 비개발자·기획자도 따라가기 쉬운 개념 복습 |
| [3Blue1Brown](https://www.youtube.com/@3blue1brown) | 수학·신경망 원리를 시각적으로 설명 | 원리를 직관적으로 이해하고 싶을 때 |

---

## 8. 팀별 후속 활동 산출물

수업 후에는 아래 5개만 남겨도 90일 PoC 논의가 쉬워집니다.

```text
team-harness/
├── CLAUDE.md
├── SKILL.md
├── reviewer.md
├── test-results.md
└── four-week-plan.md
```

추가로 UI까지 진행한 팀은 아래 파일도 남깁니다.

```text
ui-prototype/
├── index.html
├── styles.css
├── app.js
└── sample-output.json
```

`sample-output.json`은 실제 Claude Code 연동 전 단계의 더미 산출물입니다. 실제 PoC에서는 Claude Code가 만든 JSON/Markdown 파일을 UI가 읽는 구조로 확장합니다.

---

## 9. 다음 미팅에서 공유할 1분 보고 양식

팀별로 아래 1분 보고를 준비하면 후속 논의가 빨라집니다.

```text
우리 팀은 [업무 장면]을 하네스 후보로 정했다.
AI가 맡을 일은 [AI 역할]이고, 사람이 승인할 일은 [승인 항목]이다.
현재 테스트 질문은 [개수]개이며, 가장 큰 실패 원인은 [실패 원인]이다.
다음 4주 동안 [첫 사용자/파일럿 부서]와 함께 [검증 방식]을 해보려 한다.
필요한 지원은 [자료 승인 / 보안 검토 / UI 개선 / 추가 멘토링]이다.
```

---

[← 바이브코딩 UI](../08-vibecoding-ui/) · [부록으로 →](../09-appendix/) · [홈](../)

