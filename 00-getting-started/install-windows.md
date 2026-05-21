---
title: 2️⃣ Windows 설치
parent: 0. 시작 전 준비
nav_order: 2
---

# Windows에 Claude Code 설치
{: .fs-7 }

Windows 10 / 11 · 소요 시간 10~15분
{: .fs-5 .fw-300 }

---

## 사전 확인

- [ ] Windows 10 (1909 이상) 또는 Windows 11
- [ ] 관리자 권한 (또는 IT팀 사전 협의)
- [ ] 약 2GB 디스크 여유 공간

## 1단계 — Node.js 설치

Claude Code는 Node.js 18 이상이 필요합니다.

1. [https://nodejs.org](https://nodejs.org) 접속
2. **LTS 버전** 다운로드 (왼쪽 큰 버튼)
3. 다운로드된 `.msi` 파일 실행 → 모든 옵션 기본값으로 **Next** 진행
4. 설치 완료 후 **재부팅** (PATH 환경변수 적용)

### 설치 확인

PowerShell을 열고 (시작 메뉴 → "powershell" 검색):

```powershell
node --version
```

`v20.x.x` 같은 버전이 표시되면 성공.

{: .warning }
> **"node를 인식할 수 없습니다" 오류?**
> 재부팅 후에도 안 되면 [트러블슈팅](../troubleshooting/#node-인식-안-됨-windows)을 참고하세요.

## 2단계 — Claude Code 설치

PowerShell에서:

```powershell
npm install -g @anthropic-ai/claude-code
```

설치가 끝나면 다음 명령으로 확인:

```powershell
claude --version
```

## 3단계 — 첫 실행 및 로그인

```powershell
claude
```

브라우저가 열리며 Claude 로그인 페이지로 이동합니다. [계정 발급](../account-setup/)에서 만든 계정으로 로그인하세요.

로그인 완료 후 터미널로 돌아오면 `>` 프롬프트가 표시됩니다.

## 4단계 — 워크샵 폴더 만들기

워크샵 동안 작업할 폴더를 미리 만들어두세요.

```powershell
mkdir C:\workshop
cd C:\workshop
claude
```

---

설치 완료! 다음: [동작 확인 체크리스트 →](../checklist/)
