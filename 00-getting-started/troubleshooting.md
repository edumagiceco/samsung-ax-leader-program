---
title: 4️⃣ 트러블슈팅
parent: 0. 시작 전 준비
nav_order: 5
---

# 트러블슈팅
{: .fs-7 }

설치·실행 중 자주 발생하는 문제와 해결법
{: .fs-5 .fw-300 }

---

## Node 인식 안 됨 (Windows)

**증상**: `node`, `npm`, `claude` 명령이 "인식할 수 없습니다" 오류

**해결**:
1. PowerShell 종료 → 재시작
2. 그래도 안 되면 PC **재부팅**
3. 재부팅 후에도 안 되면 PATH 환경변수 확인:
   - 시작 메뉴 → "환경 변수" 검색 → 시스템 환경 변수 편집
   - **Path**에 `C:\Program Files\nodejs\` 가 있는지 확인
4. 없으면 Node.js 재설치 (관리자 권한으로 실행)

## 사내 방화벽 차단

**증상**: `npm install` 시 timeout 또는 ERR_NETWORK

**해결**:
1. **테더링으로 시도** — 본인 휴대폰 핫스팟에 노트북 연결 후 재설치
2. 사내 네트워크 필수면 IT팀에 **npm registry proxy 설정** 요청
3. 회사 정책상 외부 npm 차단되면 [claude.ai](https://claude.ai) 웹 버전으로 대체

## 권한 거부 (Mac)

**증상**: `npm install -g` 시 EACCES 오류

**해결**:
```bash
sudo npm install -g @anthropic-ai/claude-code
```

또는 더 안전한 방법으로 npm prefix 변경:
```bash
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
source ~/.zshrc
npm install -g @anthropic-ai/claude-code
```

## 로그인 페이지가 안 열림

**증상**: `claude /login` 실행해도 브라우저가 안 뜸

**해결**:
1. 브라우저를 미리 열어두고 다시 시도
2. 콘솔에 나오는 URL을 **수동 복사 → 브라우저 주소창 붙여넣기**
3. 그래도 안 되면 회사 보안 솔루션이 자동 실행을 막는 것. 수동 URL 방식으로 우회

## "Rate limit exceeded" 메시지

**증상**: 몇 번 대화 후 갑자기 사용 불가

**해결**:
- **Free 플랜**의 일일 한도 초과. Pro 플랜으로 업그레이드하거나 24시간 대기
- 워크샵 당일은 **Pro 플랜 필수**

## 한글이 깨져 보임 (Windows)

**증상**: 터미널에서 한글이 `?`로 표시

**해결**:
PowerShell에서:
```powershell
chcp 65001
```

영구 적용하려면 PowerShell 프로필 편집:
```powershell
notepad $PROFILE
```
파일에 `chcp 65001 > $null` 추가.

## Claude Code가 너무 느림

**증상**: 응답까지 30초 이상 걸림

**해결**:
1. 인터넷 속도 측정 — [fast.com](https://fast.com)에서 10Mbps 이상이어야 쾌적
2. VPN 사용 중이면 해제
3. 같은 매장 다수 동시 사용 시 속도 저하 가능 — 워크샵 시간에는 본사 백본 회선 사용 권장

## 매장 PC라 설치 권한이 없음

**증상**: 관리자 비밀번호를 모름

**해결**:
1. **본인 노트북 지참** (가장 빠름)
2. 본사 IT팀에 **임시 설치 권한 요청** (D-7 이전)
3. 설치 불가 시 [claude.ai](https://claude.ai) **웹 버전**으로 부분 참여

웹 버전으로는 Day 1의 70%, Day 2의 50% 정도 따라올 수 있습니다.

## 그래도 안 되면

D-5 (수요일) **IT팀 사전 지원 데스크**에서 1:1 도움을 받으세요.

- 장소: [별도 공지]
- 시간: 13:00 - 17:00
- 준비물: 본인 노트북, 사번

---

[← 동작 확인으로 돌아가기](../checklist/) · [홈으로](../../)
