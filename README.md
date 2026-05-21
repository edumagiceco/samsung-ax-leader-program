# 삼성전자판매 AI 워크샵

매장 영업·CS·마케팅·운영 직군을 위한 **2일 하네스 실습 워크샵** 가이드 사이트.

> [revfactory/harness-100](https://github.com/revfactory/harness-100) 사례를 매장 직군 워크샵 형태로 재구성한 자료입니다.

## 구성

- **2일 워크샵**: Day 1 학습 + Day 2 프로젝트 발표
- **5개 직군 트랙**: 영업 / CS / 마케팅 / 운영 / 보고
- **19개 사례**: Top 5 풀실습 + 14개 데모 가이드

## 사이트 구조

```
00-getting-started/   D-7 사전 설치 가이드 (Win/Mac, 트러블슈팅)
01-harness-intro/     하네스 10분 입문
02-tracks/            5개 직군 × 19개 사례
03-projects/          Day 2 프로젝트 키트
04-staff-guide/       운영진용 큐시트
05-after-workshop/    30일 챌린지·FAQ
```

## 로컬 개발

```bash
bundle install
bundle exec jekyll serve
# http://localhost:4000 접속
```

## 배포

`main` 브랜치에 push 하면 GitHub Actions가 자동으로 GitHub Pages에 배포합니다.

배포 활성화 방법:
1. GitHub 레포 Settings → Pages
2. Source: **GitHub Actions** 선택
3. 첫 push 후 약 1~2분 대기

## 라이선스

MIT
