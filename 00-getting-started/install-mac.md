---
title: 2️⃣ Mac 설치
parent: 0. 시작 전 준비
nav_order: 3
---

# Mac에 Claude Code 설치
{: .fs-7 }

macOS 12 (Monterey) 이상 · 소요 시간 10분
{: .fs-5 .fw-300 }

---

## 사전 확인

- [ ] macOS 12 이상
- [ ] 본인 사용자 비밀번호 (관리자 권한)
- [ ] 약 1GB 디스크 여유 공간

## 1단계 — Homebrew 설치 (이미 설치되어 있으면 건너뛰기)

터미널을 엽니다 (Cmd+Space → "terminal" 검색).

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

설치 중 비밀번호 입력 요청이 나옵니다 (Mac 로그인 비밀번호).

### 설치 확인

```bash
brew --version
```

## 2단계 — Node.js 설치

```bash
brew install node
```

설치 확인:

```bash
node --version
```

`v20.x.x` 같은 버전이 표시되면 성공.

## 3단계 — Claude Code 설치

```bash
npm install -g @anthropic-ai/claude-code
```

```bash
claude --version
```

## 4단계 — 첫 실행 및 로그인

```bash
claude
```

기본 브라우저가 열리며 Claude 로그인 페이지로 이동합니다. [계정 발급](../account-setup/)에서 만든 계정으로 로그인.

## 5단계 — 워크샵 폴더 만들기

```bash
mkdir -p ~/workshop
cd ~/workshop
claude
```

---

## Apple Silicon (M1/M2/M3) 사용자 참고

Apple Silicon Mac은 모든 단계가 동일하게 작동합니다. 다만 Homebrew가 `/opt/homebrew`에 설치되므로, PATH가 자동으로 설정되지 않을 수 있습니다. 첫 설치 후 터미널을 재시작하세요.

---

설치 완료! 다음: [동작 확인 체크리스트 →](../checklist/)
