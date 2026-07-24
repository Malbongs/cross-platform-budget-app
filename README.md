# 크로스플랫폼 가계부 앱

> 소비를 기록하면 마스코트가 반응하는 게이미피케이션 가계부 앱 — 하나의 코드베이스로 웹·iOS·안드로이드에 배포했습니다.

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![Capacitor](https://img.shields.io/badge/Capacitor-8-119EFF?logo=capacitor&logoColor=white)
![Platforms](https://img.shields.io/badge/Platforms-Web%20%7C%20iOS%20%7C%20Android-blueviolet)
![i18n](https://img.shields.io/badge/i18n-KO%20%7C%20EN%20%7C%20JA-informational)
![Offline](https://img.shields.io/badge/Offline-First-success)
![Solo Dev](https://img.shields.io/badge/Solo-Developer-orange)

## 개요

소비를 기록할 때마다 마스코트 캐릭터가 반응하는 게이미피케이션 가계부 앱입니다. 혼자서 하나의 코드베이스로 세 플랫폼 — 실서비스 웹, iOS, 안드로이드 — 에 모두 배포했습니다. 서버도 계정도 없이 완전히 오프라인으로 동작해서, 데이터가 기기 밖으로 나가지 않습니다.

## 핵심 기능

- **마스코트 게이미피케이션** — 캐릭터가 소비 내역에 따라 8종의 서로 다른 표정으로 반응
- **완전 오프라인, 계정 불필요** — 모든 데이터를 기기에 저장, 설계부터 프라이버시 친화적
- **클라이언트 사이드 PDF 리포트** — 서버 왕복 없이 브라우저에서 멀티페이지 소비 리포트 생성
- **시스템 공유** — OS 네이티브 공유 시트로 리포트 내보내기·공유
- **3개국어** — 한국어 / 영어 / 일본어 완전 지원
- **원 코드베이스, 3플랫폼** — 웹·iOS·안드로이드를 단일 소스로

## 기술 스택

| 영역 | 기술 |
|---|---|
| UI | React 19, Vite 7 (ESM) |
| 네이티브 래핑 | Capacitor 8 (iOS / Android) |
| 네이티브 플러그인 | Preferences(로컬 저장), Filesystem + Share(PDF 시스템 공유), SplashScreen, StatusBar, AdMob |
| PDF | jsPDF + html2canvas (클라이언트 사이드) |
| 저장소 | localStorage / Capacitor Preferences (플랫폼 분기) |
| 다국어 | 3개 로케일 (KO / EN / JA) |
| 툴링 | Puppeteer(스크린샷 자동화), sharp(아이콘 생성) |
| 배포 | 웹 배포 + Android AAB 빌드 |

## 아키텍처

React + Vite 단일 코드베이스가 소스의 기준입니다. 웹은 CDN 호스트에 바로 배포하고, 모바일은 Capacitor 8이 같은 빌드를 네이티브 iOS·안드로이드 셸로 감쌉니다.

```
React 19 + Vite 7 (단일 소스)
        │
        ├─► 웹 ──────────────► 실서비스 웹 배포
        │
        └─► Capacitor 8 래핑
                ├─► iOS
                └─► Android (AAB)
```

저장소와 플랫폼 기능은 런타임에 자동으로 분기됩니다. 웹은 `localStorage`, 네이티브는 Capacitor Preferences를 사용해 — 코드를 갈라내지 않고도 어느 환경에서나 올바르게 동작합니다.

## 규모

- **약 3,168 LOC** (`src` 기준)
- **화면 4개**
- **인라인 SVG 아이콘 24종+**, **마스코트 표정 8종**
- **3개국어** (KO / EN / JA)
- **개발 인원 1명** — 기획·구현·네이티브 통합·릴리즈 전부

## 기술 하이라이트

- **진짜 단일 소스, 3플랫폼 배포** — 하나의 코드베이스로 실서비스 웹 + iOS + 안드로이드를 커버하고, 웹/네이티브 런타임 분기로 어느 플랫폼에서도 깨지지 않습니다.
- **네이티브 통합 3종** — 로컬 저장, PDF 시스템 공유, 광고를 Capacitor 플러그인으로 연결.
- **서버리스 PDF 생성** — 멀티페이지 리포트를 전부 클라이언트 사이드에서 생성, 백엔드가 필요 없습니다.
- **오프라인 우선, 계정 없음** — 서버·로그인·데이터 수집 없이 아키텍처 자체가 프라이버시 친화적.
- **릴리즈 자동화 인프라** — Puppeteer 기반 스토어 스크린샷 생성, sharp 기반 아이콘 생성, 3개국어 다국어까지.

## 나의 역할

기획부터 끝까지 1인 개발. 프로덕트 방향 설정, React 19 + Vite 7 프론트엔드, iOS·안드로이드 Capacitor 네이티브 래핑, 네이티브 플러그인 3종 통합, 클라이언트 사이드 PDF 리포트 엔진, 3개국어 지원, 릴리즈 자동화(스크린샷·아이콘·웹 배포·AAB 빌드)까지 전 영역을 직접 설계하고 구현했습니다.
