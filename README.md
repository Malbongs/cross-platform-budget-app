# 크로스플랫폼 가계부 앱

> Log a purchase, and a mascot reacts. A cross-platform gamification budget app built from a single codebase — Web, iOS, and Android.

![React](https://img.shields.io/badge/React-19-61DAFB?logo=react&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-7-646CFF?logo=vite&logoColor=white)
![Capacitor](https://img.shields.io/badge/Capacitor-8-119EFF?logo=capacitor&logoColor=white)
![Platforms](https://img.shields.io/badge/Platforms-Web%20%7C%20iOS%20%7C%20Android-blueviolet)
![i18n](https://img.shields.io/badge/i18n-KO%20%7C%20EN%20%7C%20JA-informational)
![Offline](https://img.shields.io/badge/Offline-First-success)
![Solo Dev](https://img.shields.io/badge/Solo-Developer-orange)

## Overview

A cross-platform budget tracker with a gamification twist: every time you record spending, a mascot character reacts. I built it solo, shipping one codebase to three platforms — a live web app, iOS, and Android. It runs fully offline with no account and no server, so nothing ever leaves the device.

## Key Features

- **Mascot-driven gamification** — the character responds to your spending with 8 distinct facial expressions.
- **Fully offline, no account** — all data lives on-device; privacy-friendly by design.
- **Client-side PDF reports** — multi-page spending reports generated entirely in the browser, no server round-trip.
- **System-level sharing** — export and share reports through the native OS share sheet.
- **Trilingual** — full Korean / English / Japanese localization.
- **One codebase, three platforms** — Web, iOS, and Android from a single source.

## Tech Stack

| Area | Technology |
|---|---|
| UI | React 19, Vite 7 (ESM) |
| Native wrapper | Capacitor 8 (iOS / Android) |
| Native plugins | Preferences (local storage), Filesystem + Share (PDF system share), SplashScreen, StatusBar, AdMob |
| PDF | jsPDF + html2canvas (client-side) |
| Storage | localStorage / Capacitor Preferences (platform-branched) |
| i18n | 3 locales (KO / EN / JA) |
| Tooling | Puppeteer (screenshot automation), sharp (icon generation) |
| Delivery | Web deploy + Android AAB build |

## Architecture

A single React + Vite codebase serves as the source of truth. On the web it deploys straight to a CDN host; for mobile, Capacitor 8 wraps the same build into native iOS and Android shells.

```
React 19 + Vite 7 (single source)
        │
        ├─► Web ──────────────► live web deploy
        │
        └─► Capacitor 8 wrap
                ├─► iOS
                └─► Android (AAB)
```

Storage and platform features branch automatically at runtime: the web path uses `localStorage`, while native builds use Capacitor Preferences — so the app behaves correctly everywhere without forking the code.

## Scale

- **~3,168 LOC** in `src`
- **4 screens**
- **24+ inline SVG icons** and **8 mascot expressions**
- **3 languages** (KO / EN / JA)
- **1 developer** — design, build, native integration, and release

## Technical Highlights

- **True single-source, tri-platform delivery.** One codebase covers a live web deployment plus iOS and Android — with web/native runtime branching so nothing breaks on any platform.
- **Three native integrations.** Local storage, PDF system sharing, and ads wired through Capacitor plugins.
- **Serverless PDF generation.** Multi-page reports are built entirely client-side — no backend required.
- **Offline-first, account-free.** No server, no login, no data collection — privacy by architecture.
- **Automated release infrastructure.** Puppeteer-driven store screenshot generation and sharp-based icon generation, alongside trilingual i18n.

## My Role

Solo developer — end to end. I owned product direction, the React 19 + Vite 7 frontend, the Capacitor native wrapping for iOS and Android, all three native plugin integrations, the client-side PDF report engine, trilingual localization, and the release automation (screenshots, icons, web deploy, AAB build).
