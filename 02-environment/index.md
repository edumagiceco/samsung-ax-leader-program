---
title: 2. 개발환경 설정
nav_order: 3
permalink: /02-environment/
---

# 개발환경 설정 (Win11)
{: .fs-8 }

5/20에 세팅한 환경이 갑자기 안 될 때, 또는 1주차 사이 새로 만지려는데 헷갈릴 때 — 여기서 다시 확인하세요.
{: .fs-5 .fw-300 }

---

## 점검 순서

이 순서로 한 번에 훑어보면 5분 안에 다시 정상화됩니다.

### 1단계 — Claude Desktop 설치 확인
- 다운로드 위치: [https://claude.com/ko/download](https://claude.com/ko/download)
- Windows용 다운로드 클릭 → Setup 파일 실행
- 로그인: Google 계정 또는 본인 메일

### 2단계 — Cowork 탭 활성화
- Cowork 탭 클릭 → "활성화" 버튼
- "지금 다시 시작" → PC 재시작

### 3단계 — Claude Code 환경 (Git for Windows)
- Code 탭 클릭 → "Git 다운로드" 안내가 나오면
- [https://git-scm.com/install/windows](https://git-scm.com/install/windows) 에서 다운로드 → Next 클릭으로 설치
- **환경변수 설정**: 시스템 환경 변수 편집 → 사용자 변수 새로 만들기
  - 변수 이름: `CLAUDE_CODE_GIT_BASH_PATH`
  - 변수 값: `C:\Program Files\Git\bin\bash.exe`

### 4단계 — Claude Desktop 재시작
{: .warning }
> **반드시 파일 → 종료**로 종료하세요. 우측 상단 X 버튼 클릭하면 백그라운드에서 살아 있어 환경변수가 적용되지 않습니다.

검색창에서 "Claude" 검색하여 다시 실행 → Code 탭 클릭 → **"로컬 세션에는 Git이 필요합니다" 메시지가 안 보이면 정상**

### 5단계 — 모드·모델·작업량 설정

| 실습 | 모드 | 모델 | 작업량 |
|---|---|---|---|
| customer-support | 권한 요청 또는 자동 | Sonnet 4.6 | 낮음 |
| real-estate-analyst | 권한 요청 또는 자동 | Sonnet 4.6 | 낮음 |
| **Harness-Lab** | **자동 모드** | **Opus 4.7 1M** | **매우 높음** |

### 6단계 — 실습 폴더 확인
- 위치: `C:\claude-practice`
- 폴더명 한글·특수문자 금지
- 안에 다음 3개가 있어야 정상:
  - `customer-support/`
  - `real-estate-analyst/`
  - `harness-lab/`

### 7단계 — 실습용 하네스 다시 다운로드

위 3개 폴더가 없거나 손상되었을 때 재다운로드 방법:

```
https://github.com/MagicecoleAI/max-samsung-harness-samples.git 에서 프로젝트 다운로드해줘
```

위 프롬프트를 Claude Desktop의 Code 탭(폴더 = `C:\claude-practice`)에서 실행하면 자동 다운로드됩니다.

---

## 자주 발생하는 트러블슈팅

### "로컬 세션에는 Git이 필요합니다"가 계속 보여요
1. 환경변수 `CLAUDE_CODE_GIT_BASH_PATH` 정확히 입력했는지 확인 (`C:\Program Files\Git\bin\bash.exe`)
2. Claude Desktop을 **파일 → 종료**로 완전히 종료 후 재시작
3. 그래도 안 되면 PC 재부팅

### Cowork·Code 탭이 안 보여요
- Claude Desktop 최신 버전 확인 (좌측 상단 메뉴 → 도움말 → 업데이트 확인)
- Max 또는 Pro 플랜 결제 상태 확인

### 폴더 경로 오류
- 폴더명·경로에 한글이 있으면 오류 발생
- `C:\claude-practice` 처럼 영어만 사용

### 한글 입력이 깨져요
- Win11 영역 설정 → 시간 및 언어 → 언어 → 한국어 → UTF-8 활성화

### 권한 요청이 너무 자주 떠요
- 작업량을 "낮음" → "보통"으로 올리면 일부 권한이 자동 처리됨
- 또는 모드를 "자동 모드"로 변경

---

## 그래도 안 되면

- 📱 [카카오 오픈채팅방](https://open.kakao.com/o/g0ligxvi)에 화면 캡처와 함께 질문
- 📧 운영자 멘토링 요청 (5/22-25)

---

[← 홈](../) · [Day 1 회고로 →](../01-day1-recap/)
