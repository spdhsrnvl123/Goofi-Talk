<p align="center">
  <img src="https://img.shields.io/badge/Goofi_Talk-AI_FAQ_Chatbot_SaaS-000000?style=for-the-badge&labelColor=000000" alt="Goofi Talk" height="40" />
</p>

<p align="center">
  <strong>Multi-tenant AI FAQ Chatbot SaaS Platform</strong><br/>
  <sub>subdomain-based company routing | 4-step smart search with AI Fallback | admin dashboard</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript_5.9-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white" alt="Supabase" />
  <img src="https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude AI" />
  <img src="https://img.shields.io/badge/Tailwind_CSS_v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" alt="Playwright" />
  <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare" />
</p>

<p align="center">
  <a href="https://chatbot-taupe-two-95.vercel.app"><img src="https://img.shields.io/badge/Live_Demo-000000?style=for-the-badge&logo=vercel&logoColor=white" alt="Live Demo" /></a>&nbsp;
  <a href="https://goofitalk.co.kr"><img src="https://img.shields.io/badge/Landing_Page-06B6D4?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Landing Page" /></a>&nbsp;
  <a href="https://chatbot-taupe-two-95.vercel.app/admin"><img src="https://img.shields.io/badge/Admin_Page-8B5CF6?style=for-the-badge&logo=shield&logoColor=white" alt="Admin Page" /></a>
</p>

---

## Overview

**Goofi Talk**은 기업 고객센터의 반복 FAQ 문의를 줄이기 위해 기획부터 배포까지 **1인 풀스택으로 개발**한 AI FAQ 챗봇 SaaS 플랫폼입니다.

서브도메인 기반 멀티테넌트 구조로 하나의 코드베이스에서 여러 회사에 독립적인 FAQ 챗봇 서비스를 제공합니다. 기존 3단계 규칙 기반 검색에 Claude AI Fallback을 추가하여, 매칭 실패 시에도 AI가 FAQ 컨텍스트를 바탕으로 자연어 답변을 생성합니다.

> <!-- 아래에 실제 스크린샷 또는 GIF를 삽입하세요 -->
> **[TODO]** 챗봇 동작 화면 GIF 또는 스크린샷 삽입
>
> ```
> 권장 구성: 챗봇 대화 화면 + 관리자 대시보드 + 모바일 반응형
> 도구 추천: Kap(macOS) / ScreenToGif(Windows) / Chrome DevTools Recorder
> ```

---

## Table of Contents

- [Problem & Solution](#problem--solution)
- [Key Features](#key-features)
- [Tech Stack](#tech-stack)
- [Architecture](#architecture)
- [Technical Decisions](#technical-decisions)
- [AI-Powered Development](#ai-powered-development)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)

---

## Problem & Solution

| Problem | Solution | Impact |
|:--------|:---------|:-------|
| 반복 FAQ 문의로 인한 고객센터 부하 | 대화형 챗봇 셀프 서비스 | CS 인력 의존도 감소 |
| 비개발자의 콘텐츠 관리 어려움 | Drag & Drop FAQ CRUD 관리자 페이지 | 운영자 자율 관리 가능 |
| 단순 키워드 검색의 낮은 정확도 | 4단계 검색 + 한글 초성 검색 + AI Fallback | 검색 커버리지 극대화 |
| Supabase 장애 시 서비스 중단 | 정적 데이터 자동 폴백 + On-demand 지연 로딩 | Zero-downtime 보장 |
| 단일 고객사 한정 서비스 | 서브도메인 기반 멀티테넌트 SaaS | N개 회사 동시 서비스 |

---

## Key Features

<table>
  <tr>
    <td width="50%">
      <img src="https://img.shields.io/badge/-Core-3178C6?style=flat-square" alt="Core" /><br/>
      <strong>4-Step Smart Search</strong><br/>
      질문 전문 검색 → 서브카테고리 키워드 → 카테고리 키워드 → AI Fallback
    </td>
    <td width="50%">
      <img src="https://img.shields.io/badge/-AI-D97757?style=flat-square" alt="AI" /><br/>
      <strong>AI Fallback (Claude API)</strong><br/>
      검색 실패 시 Edge Function + RAG로 자연어 답변 생성
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-Search-10B981?style=flat-square" alt="Search" /><br/>
      <strong>Korean Chosung Search</strong><br/>
      <code>ㅅㄱ</code> 입력만으로 <code>수강신청</code> 관련 질문 검색 가능
    </td>
    <td>
      <img src="https://img.shields.io/badge/-SaaS-8B5CF6?style=flat-square" alt="SaaS" /><br/>
      <strong>Multi-Tenant SaaS</strong><br/>
      서브도메인 기반 회사 전환, 회사별 독립 FAQ / 설정 / 분석
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-Admin-F59E0B?style=flat-square" alt="Admin" /><br/>
      <strong>Admin Dashboard</strong><br/>
      FAQ CRUD, DnD 정렬, AI 설정, 검색/클릭 분석, 실시간 미리보기
    </td>
    <td>
      <img src="https://img.shields.io/badge/-Resilience-EF4444?style=flat-square" alt="Resilience" /><br/>
      <strong>Offline Fallback</strong><br/>
      Supabase 연결 실패 시 정적 FAQ 데이터로 자동 전환
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-Embed-0EA5E9?style=flat-square" alt="Embed" /><br/>
      <strong>Widget Embed</strong><br/>
      설정 페이지에서 삽입 코드 자동 생성, 위치 커스터마이징
    </td>
    <td>
      <img src="https://img.shields.io/badge/-Test-2EAD33?style=flat-square" alt="Test" /><br/>
      <strong>E2E Testing</strong><br/>
      Playwright 21개 테스트 (챗봇 플로우, 관리자 인증, Smoke)
    </td>
  </tr>
</table>

---

## Tech Stack

<table>
  <tr>
    <td align="center" width="140">
      <img src="https://img.shields.io/badge/-Frontend-61DAFB?style=for-the-badge" alt="Frontend" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black" />
      <img src="https://img.shields.io/badge/TypeScript_5.9-3178C6?style=flat-square&logo=typescript&logoColor=white" />
      <img src="https://img.shields.io/badge/Tailwind_CSS_v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" />
      <img src="https://img.shields.io/badge/shadcn/ui-000000?style=flat-square&logo=shadcnui&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-State-764ABC?style=for-the-badge" alt="State" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Zustand_5-764ABC?style=flat-square&logo=npm&logoColor=white" />
      <sub>(5 independent stores)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Backend-3FCF8E?style=for-the-badge" alt="Backend" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white" />
      <sub>(PostgreSQL + Auth + Storage + Edge Functions)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-AI-D97757?style=for-the-badge" alt="AI" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white" />
      <sub>(Edge Function <code>chat-ai</code> + RAG)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Build-646CFF?style=for-the-badge" alt="Build" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white" />
      <img src="https://img.shields.io/badge/React_Router_v7-CA4245?style=flat-square&logo=reactrouter&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Testing-2EAD33?style=for-the-badge" alt="Testing" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" />
      <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Infra-F38020?style=for-the-badge" alt="Infra" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" />
      <img src="https://img.shields.io/badge/Vercel-000000?style=flat-square&logo=vercel&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Libraries-FF6F61?style=for-the-badge" alt="Libraries" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/TipTap-1a1a2e?style=flat-square&logo=tiptap&logoColor=white" />
      <img src="https://img.shields.io/badge/dnd--kit-1a1a2e?style=flat-square" />
      <img src="https://img.shields.io/badge/Recharts-22B5BF?style=flat-square" />
      <img src="https://img.shields.io/badge/Framer_Motion-0055FF?style=flat-square&logo=framer&logoColor=white" />
      <img src="https://img.shields.io/badge/DOMPurify-1a1a2e?style=flat-square" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Dev_Tools-191919?style=for-the-badge" alt="Dev Tools" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=anthropic&logoColor=white" />
      <img src="https://img.shields.io/badge/Shrimp_Task_MCP-191919?style=flat-square" />
      <img src="https://img.shields.io/badge/Husky-1a1a2e?style=flat-square&logo=git&logoColor=white" />
      <img src="https://img.shields.io/badge/ESLint-4B32C3?style=flat-square&logo=eslint&logoColor=white" />
    </td>
  </tr>
</table>

---

## Architecture
<img width="1408" height="768" alt="image" src="https://github.com/user-attachments/assets/43394298-ccdc-4351-8b51-01e072f25737" />


---

## Technical Decisions

> 각 의사결정의 **문제 -- 고려한 방안 -- 결정 -- 결과**는 **[TECHNICAL_DECISIONS.md](./TECHNICAL_DECISIONS.md)** 에서 확인할 수 있습니다.

| 의사결정 | 문제 | 해결 | 결과 |
|:---------|:-----|:-----|:-----|
| [4단계 스마트 검색](./TECHNICAL_DECISIONS.md#1-4단계-스마트-검색-설계) | AI 전수 처리 시 비용 폭증 | 규칙 기반 3단계 + AI Fallback 4단계 | 1~3단계 ~100ms, AI 호출 비용 대폭 절약 |
| [한글 초성 검색](./TECHNICAL_DECISIONS.md#2-한글-초성-검색-알고리즘-직접-구현) | `ㅅㄱ` -> `수강신청` 매칭 불가 | 유니코드 수학 공식 직접 구현 (59줄, 의존성 0) | 한글 11,172자 완벽 지원 |
| [5-Store 분리 설계](./TECHNICAL_DECISIONS.md#3-zustand-5-store-분리-설계) | 단일 스토어에서 불필요한 리렌더링 | Zustand 도메인별 분리 + 셀렉터 훅 | `isTyping` 변경 시 MessageBubble만 리렌더 |
| [Tree Diff/Save](./TECHNICAL_DECISIONS.md#4-tree-diffsave-패턴-faq-편집-최적화) | FAQ 1개 수정에 1000개 쿼리 발생 | Git 스타일 diff 알고리즘 | 변경분만 DB 반영 (쿼리 1개) |
| [RAG + 멀티테넌트 격리](./TECHNICAL_DECISIONS.md#5-rag--멀티테넌트-격리) | 멀티테넌트 AI 데이터 격리 | 회사별 FAQ 동적 주입 + 6중 보안 계층 | 회사 추가 시 코드 수정 0 |
| [Supabase 폴백](./TECHNICAL_DECISIONS.md#6-supabase-폴백--on-demand-지연-로딩) | 서버 장애 시 서비스 중단 | 정적 데이터 자동 폴백 + 2단계 지연 로딩 | Zero-downtime 보장 |
| [번들 최적화](./TECHNICAL_DECISIONS.md#7-vite-번들-최적화) | 챗봇 유저가 Admin 코드까지 로드 | React.lazy + Vite manualChunks | ~58% 번들 크기 절감 |

---

## AI-Powered Development

> 상세 내용: [TECHNICAL_DECISIONS.md #8](./TECHNICAL_DECISIONS.md#8-ai-기반-개발-프로세스)

이 프로젝트는 **Claude Code** + **Shrimp Task MCP**를 활용한 AI 기반 개발 워크플로우로 진행했습니다. 핵심은 AI가 프로젝트의 컨벤션을 정확히 준수하도록 **600줄 이상의 규칙 파일을 시스템화**한 것입니다.

```
.claude/
|-- agents/    code-reviewer, test-runner-fixer, fullstack-specialist, planner
|-- skills/    /commit, /status, /explain (custom slash commands)
|-- rules/     Zustand patterns, security rules, 13 prohibited patterns (600+ lines)
+-- docs/      Claude Code guides
```

<details>
<summary><strong>Shrimp Task MCP Workflow</strong></summary>

```
plan_task --> analyze_task --> split_tasks --> execute_task --> verify_task
```

각 태스크는 분석 -> 구현 -> 검증 단계를 거쳐야 완료 처리되며, 완료된 태스크는 `ROADMAP.md`에 자동 반영됩니다.

</details>

---

## Project Structure

```
chatbot/
|
|-- src/
|   |-- App.tsx                        # routing + subdomain multi-tenant
|   |
|   |-- chatbot/                       # chatbot module
|   |   |-- components/                #   chat UI (messages, input, nav, results)
|   |   |-- hooks/                     #   use-chat-handlers, use-chat-search,
|   |   |                              #   use-chat-message
|   |   |-- stores/                    #   Zustand x3 (message, navigation, search)
|   |   +-- utils/                     #   chosung search, category icons, image zoom
|   |
|   |-- admin/                         # admin module
|   |   |-- pages/                     #   FAQ, analytics, settings, AI config,
|   |   |                              #   company management
|   |   |-- components/                #   tree editor, DnD, charts, settings form
|   |   |-- contexts/                  #   AdminContext (role-based access control)
|   |   +-- lib/                       #   admin-api, tree-diff, tree-save, admin-theme
|   |
|   |-- hooks/                         # shared hooks (use-faq-data, use-company)
|   |-- lib/                           # shared libs (supabase, ai-client,
|   |                                  #   faq-fetcher, sanitize)
|   |-- config/                        # company config, constants
|   |-- types/                         # TypeScript type definitions
|   |-- data/faq/                      # static FAQ data (offline fallback)
|   |-- pages/landing/                 # landing page sections
|   +-- components/ui/                 # shadcn-based common UI
|
|-- supabase/
|   |-- functions/                     # Edge Functions (chat-ai, signup, users)
|   +-- migrations/                    # DB migration SQL
|
|-- e2e/                               # Playwright E2E tests
|   |-- chatbot/                       #   chatbot flow tests (10)
|   |-- admin/                         #   admin auth/FAQ tests (7)
|   |-- smoke/                         #   page load checks (3)
|   +-- helpers/                       #   selectors, wait helpers, auth fixture
|
+-- .claude/                           # Claude Code config (AI dev tools)
    |-- agents/                        #   AI sub-agent definitions
    |-- skills/                        #   custom slash commands
    |-- rules/                         #   project coding rules
    +-- docs/                          #   Claude Code guides
```

---

## Code Quality

| Area | Details |
|:-----|:--------|
| ![](https://img.shields.io/badge/Unit_Test-Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white) | 한글 초성 검색, Tree Diff 등 핵심 로직 검증 |
| ![](https://img.shields.io/badge/E2E_Test-Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white) | 21개 테스트 -- 챗봇 플로우, 관리자 인증, Smoke |
| ![](https://img.shields.io/badge/Error-ErrorBoundary-EF4444?style=flat-square) | 런타임 에러 시 화이트 스크린 방지 |
| ![](https://img.shields.io/badge/A11y-ARIA_Labels-0EA5E9?style=flat-square) | `role="log"`, `role="group"`, `aria-label` 적용 |
| ![](https://img.shields.io/badge/Type_Safety-Strict_Mode-3178C6?style=flat-square&logo=typescript&logoColor=white) | `any` 타입 제거, 전체 코드베이스 `strict` 모드 |
| ![](https://img.shields.io/badge/Security-DOMPurify+RLS-10B981?style=flat-square) | XSS 방어, Supabase RLS, 세션 격리 |
| ![](https://img.shields.io/badge/Git_Hooks-Husky-1a1a2e?style=flat-square&logo=git&logoColor=white) | pre-commit lint-staged 자동 실행 |
