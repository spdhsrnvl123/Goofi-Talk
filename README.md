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
- [Technical Deep Dive](#technical-deep-dive)
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

```
Cloudflare (DNS / SSL / CDN / DDoS Protection)
*.goofitalk.co.kr --> subdomain routing
         |
         v
+------------------+          +-----------------------------------+
|   Browser        |          |   React SPA (Vite 7)              |
|                  |          |                                   |
|  subdomain       |--------->|   Chatbot        Admin (/admin)   |
|  detection       |          |   - messageStore - FAQ CRUD       |
|                  |          |   - navStore     - DnD Sort        |
|  aifa.goofitalk  |          |   - searchStore  - AI Settings    |
|  .co.kr          |          |                  - Analytics      |
+------------------+          |                  - Role: super    |
                              |                    admin/admin    |
                              |                    /viewer        |
                              +--------+----------+---------------+
                                       |          |
                              +--------v----------v---------------+
                              |   Supabase                        |
                              |                                   |
                              |   PostgreSQL  Auth  Storage        |
                              |                                   |
                              |   Edge Functions:                  |
                              |   +-- chat-ai (RAG + Claude API)  |
                              |   +-- signup-with-company          |
                              |   +-- list-company-users           |
                              |                                   |
                              |   Connection fail --> static       |
                              |   fallback (src/data/faq/)         |
                              +-----------------------------------+
```

---

## Technical Deep Dive

### 1. Korean Chosung Search

한글 유니코드 구조(`AC00` ~ `D7A3`)를 분석하여 초성 추출 알고리즘을 직접 구현했습니다.

```
Unicode Formula: (chosung x 21 + jungsung) x 28 + jongsung + 0xAC00

"수강신청" --> chosung extraction --> "ㅅㄱㅅㅊ"
User input "ㅅㄱ" --> prefix matching --> search success
```

단순 `includes()` 비교가 아닌 유니코드 오프셋 계산을 통해, 한글 자음 입력만으로도 자연스러운 검색을 지원합니다.

### 2. DisplayType-Based Declarative UI

봇 메시지에 `displayType` 필드를 두어, 렌더링할 UI 컴포넌트를 데이터로 선언하는 패턴을 설계했습니다.

```typescript
addBotMessage({ text: "카테고리를 선택하세요", displayType: "menu" });
addBotMessage({ text: "검색 결과입니다",       displayType: "searchResults" });
addBotMessage({ text: aiAnswer,              displayType: "aiAnswer", isAiResponse: true });
```

**Why this pattern?**
채팅 UI에서 메시지마다 다른 UI를 렌더링해야 하는 상황에서, `if/switch` 분기 대신 `displayType`을 데이터로 선언하면 새 UI 유형 추가 시 컴포넌트 매핑만 추가하면 됩니다. `clearAllDisplayTypes()` 패턴으로 항상 최신 메시지만 인터랙티브하게 유지합니다.

### 3. Zustand 5-Store Architecture

| Approach | Problem |
|:---------|:--------|
| Single global store | 메시지 추가 시 검색/네비게이션 컴포넌트까지 리렌더링 |
| Context API | 빈번한 상태 변경(타이핑 애니메이션 등)에서 성능 병목 |
| **Role-based 5-Store** | 각 스토어 변경이 해당 구독자만 리렌더링 **(adopted)** |

셀렉터 훅(`useMessages()`, `useIsTyping()` 등)을 통해 특정 필드만 구독하여 fine-grained subscription을 실현했습니다.

### 4. Supabase Fallback + On-demand Loading

```
fetchFaqData()
  |-- Success --> use Supabase DB data
  +-- Failure --> auto-switch to src/data/faq/ (zero downtime)

Lazy Loading:
  Initial  : fetch category list only (lightweight)
  On click : fetch subcategories + questions on-demand
  On search: server-side search, return only matched results
```

### 5. Tree Diff/Save Pattern

매 수정마다 전체 트리를 DB에 저장하면 불필요한 쿼리가 발생합니다. 메모리 내 트리 조작 후 저장 시 diff를 계산하여 최소 쿼리만 실행합니다.

```typescript
// 1. Edit in-memory tree
const editedTree = [...originalTree];

// 2. Compute diff on save
const diff = computeTreeDiff(originalTree, editedTree);
// --> { created: [...], updated: [...], deleted: [...] }

// 3. Apply only changes to DB
await saveTreeDiff(diff);
```

### 6. Claude AI + RAG Integration

```
All 3 search steps fail + aiEnabled === true
  --> askAi(companyId, userMessage)
    --> supabasePublic.functions.invoke("chat-ai")
      --> Edge Function: include company FAQ as context (RAG)
      --> Claude API call --> return AI response
```

**Design decisions:**
- **Session isolation** -- `supabasePublic` client (`persistSession: false`) 사용, 관리자 세션과 완전 분리
- **Timeout** -- 15s AbortController로 무한 대기 방지
- **Rate limit** -- Edge Function 내 IP 기반 분당 20회 제한
- **Graceful degradation** -- AI 호출 실패 시 "검색 결과 없음" 안내로 자연스럽게 폴백

### 7. Subdomain-Based Multi-Tenancy

```
User access
  --> getSubdomainSlug() : extract subdomain from hostname
        |-- aifa.localhost         --> "aifa"
        |-- aifa.goofitalk.co.kr   --> "aifa"
        |-- *.vercel.app           --> null (platform domain excluded)
        +-- example.co.kr          --> null (Korean 2nd-level domain)

companySlug priority:
  subdomain > ?company= query param > VITE_COMPANY_SLUG env var

On company switch --> reset all 5 Zustand stores
```

---

## AI-Powered Development

이 프로젝트는 **Claude Code** + **Shrimp Task MCP**를 활용한 AI 기반 개발 워크플로우로 진행했습니다.

### Claude Code Configuration

프로젝트 루트의 `.claude/` 디렉토리에 AI 에이전트 설정, 커스텀 스킬, 코딩 규칙을 체계적으로 구성하여, AI가 프로젝트의 컨벤션과 아키텍처를 정확히 이해한 상태에서 코드를 작성하도록 했습니다.

```
.claude/
|-- agents/                          # AI sub-agent definitions
|   |-- code-reviewer.md             #   automated code review
|   |-- test-runner-fixer.md         #   test run + auto-fix on failure
|   |-- react-supabase-fullstack.md  #   React + Supabase specialist
|   |-- development-planner.md       #   ROADMAP.md management
|   +-- prd-generator.md             #   PRD document generation
|
|-- skills/                          # custom slash commands
|   |-- commit.md                    #   /commit
|   |-- status/                      #   /status
|   +-- explain/                     #   /explain
|
|-- rules/                           # project coding rules (600+ lines)
|   +-- shrimp-rules.md             #   Zustand patterns, prohibitions, etc.
+-- docs/                            # Claude Code guides
```

<details>
<summary><strong>AI Agent Roles</strong></summary>

| Agent | Role | When Used |
|:------|:-----|:----------|
| `code-reviewer` | 버그, 보안, 컨벤션 위반 자동 검출 | 기능 구현/리팩토링 직후 |
| `test-runner-fixer` | 테스트 실행 후 실패 시 자동 분석 및 수정 | 코드 변경 후 |
| `react-supabase-fullstack` | React + Supabase 패턴 가이드, Edge Function 설계 | 풀스택 기능 구현 시 |
| `development-planner` | ROADMAP.md 업데이트 및 개발 단계 관리 | 태스크 완료 시 |

</details>

<details>
<summary><strong>Coding Rules (600+ lines)</strong></summary>

600줄 이상의 프로젝트 규칙을 정의하여 AI가 코드 작성 시 자동으로 준수하도록 했습니다:

- **Zustand selector hook pattern** -- 스토어 전체 구독 금지, `useMessages()` 등 세밀한 구독만 허용
- **Multi-file sync rule** -- FAQ 카테고리 추가 시 4개 파일 동시 수정 강제
- **Chat message pattern** -- 동기/비동기 패턴, `clearAllDisplayTypes()` 호출 순서 규칙
- **Security rules** -- HTML 살균 필수, Supabase 클라이언트 격리, 분석 로그 fire-and-forget
- **13 prohibited patterns** -- AI가 실수하기 쉬운 패턴을 명시적으로 차단

</details>

### Shrimp Task MCP Workflow

```
plan_task        requirement definition + tech analysis
     |
     v
analyze_task     codebase investigation + implementation strategy
     |
     v
split_tasks      decompose into sub-tasks (if needed)
     |
     v
execute_task     implement + test
     |
     v
verify_task      confirm test pass + update ROADMAP.md
```

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

---

## Getting Started

```bash
# Install dependencies
npm install

# Start dev server
npm run dev              # http://localhost:5173

# Build & test
npm run build            # tsc -b && vite build
npm run test             # Vitest unit tests
npm run test:e2e         # Playwright E2E tests
npm run lint             # ESLint
```

### Environment Variables

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_anon_key
VITE_COMPANY_SLUG=construction    # empty = subdomain/query param priority
```

---

<p align="center">
  <sub>Built with</sub>&nbsp;
  <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code" />&nbsp;
  <sub>by a solo full-stack developer</sub>
</p>
