<p align="center">
  <img src="https://img.shields.io/badge/Goofi_Talk-AI_FAQ_Chatbot_SaaS-000000?style=for-the-badge&labelColor=000000" alt="Goofi Talk" height="40" />
</p>

<p align="center">
  <strong>멀티테넌트 AI FAQ 챗봇 SaaS 플랫폼</strong><br/>
  <sub>서브도메인 기반 회사 전환 | 4단계 스마트 검색 (AI Fallback 포함) | 관리자 대시보드</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript_5.9-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white" alt="Supabase" />
  <img src="https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude AI" />
  <img src="https://img.shields.io/badge/TanStack_Query_v5-FF4154?style=flat-square&logo=reactquery&logoColor=white" alt="TanStack Query" />
  <img src="https://img.shields.io/badge/Tailwind_CSS_v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS" />
  <img src="https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white" alt="NGINX" />
  <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare" />
  <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" alt="Playwright" />
</p>

<p align="center">
  <a href="https://goofitalk.co.kr"><img src="https://img.shields.io/badge/Landing_Page-06B6D4?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Landing Page" /></a>&nbsp;
  <a href="https://kcie.goofitalk.co.kr"><img src="https://img.shields.io/badge/Chatbot_Demo-000000?style=for-the-badge&logo=chatbot&logoColor=white" alt="Chatbot Demo" /></a>&nbsp;
  <a href="https://goofitalk.co.kr/admin"><img src="https://img.shields.io/badge/Admin_Page-8B5CF6?style=for-the-badge&logo=shield&logoColor=white" alt="Admin Page" /></a>
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

## 목차

- [도입 배경](#도입-배경)
- [Problem & Solution](#problem--solution)
- [주요 기능](#주요-기능)
- [기술 스택](#기술-스택)
- [아키텍처](#아키텍처)
- [기술적 의사결정](#기술적-의사결정)
- [AI 기반 개발](#ai-기반-개발)
- [프로젝트 구조](#프로젝트-구조)
- [코드 품질](#코드-품질)

---

## 도입 배경

건설산업교육원에서 근무하면서 고객센터로 들어오는 **월 수백 건 이상의 반복 FAQ 문의**를 직접 목격했습니다. 수강신청 방법, 교육 일정, 수료증 발급 같은 동일한 질문이 매일 반복되고 있었고, 이에 대응하는 인력과 시간이 지속적으로 소모되고 있었습니다.

이 문제를 해결하기 위해 **채널톡**을 도입 후보로 검토했습니다. 실제로 채널톡을 방문하여 서비스를 상세히 살펴봤지만, **월 구독 비용이 교육기관 예산 대비 부담**이 되었습니다. 단순 FAQ 응답 자동화가 주 목적인데, 채널톡이 제공하는 CRM, 마케팅 자동화 등 부가 기능까지 포함된 가격 구조는 과도했습니다.

그래서 결정했습니다 -- **FAQ 챗봇에 특화된 서비스를 직접 만들자.**

```
현장에서 발견한 문제                  기존 솔루션 검토                     직접 개발 결정
+---------------------+            +---------------------+            +---------------------+
| 고객센터 반복 FAQ     |            | 채널톡 도입 검토      |            | Goofi Talk 개발      |
| 월 수백 건 이상       |  ------->  | 방문 및 서비스 분석   |  ------->  | FAQ 특화 챗봇 SaaS    |
| 동일 질문 매일 반복    |            | 월 구독 비용 부담     |            | 비용 절감 + 맞춤 기능  |
+---------------------+            +---------------------+            +---------------------+
```

단순히 비용을 아끼는 것에서 끝나지 않았습니다. 직접 만들면서 **건설산업교육원의 실제 운영 환경에 맞는 기능**을 넣을 수 있었고, 이를 다른 기관에도 제공할 수 있도록 **멀티테넌트 SaaS 구조**로 확장했습니다.

---

## Problem & Solution

| Problem | Solution | Impact |
|:--------|:---------|:-------|
| 반복 FAQ 문의로 인한 고객센터 부하 | 대화형 챗봇 셀프 서비스 | CS 인력 의존도 감소 |
| 비개발자의 콘텐츠 관리 어려움 | Drag & Drop FAQ CRUD 관리자 페이지 | 운영자 자율 관리 가능 |
| 단순 키워드 검색의 낮은 정확도 | 4단계 검색 + 한글 초성 검색 + AI Fallback | 검색 커버리지 극대화 |
| Supabase 장애 시 서비스 중단 | 정적 데이터 자동 폴백 + On-demand 지연 로딩 | Zero-downtime 보장 |
| Admin 페이지 전환 시 매번 로딩 발생 | TanStack Query v5 캐싱 + mutation 기반 무효화 | 즉시 렌더링 |
| 단일 고객사 한정 서비스 | 서브도메인 기반 멀티테넌트 SaaS | N개 회사 동시 서비스 |

---

## 주요 기능

<table>
  <tr>
    <td width="50%">
      <img src="https://img.shields.io/badge/-Core-3178C6?style=flat-square" alt="Core" /><br/>
      <strong>4단계 스마트 검색</strong><br/>
      질문 전문 검색 -- 서브카테고리 키워드 -- 카테고리 키워드 -- AI Fallback
    </td>
    <td width="50%">
      <img src="https://img.shields.io/badge/-AI-D97757?style=flat-square" alt="AI" /><br/>
      <strong>AI Fallback (Claude API)</strong><br/>
      검색 실패 시 Edge Function + RAG로 자연어 답변 생성
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-검색-10B981?style=flat-square" alt="검색" /><br/>
      <strong>한글 초성 검색</strong><br/>
      <code>ㅅㄱ</code> 입력만으로 <code>수강신청</code> 관련 질문 검색 가능
    </td>
    <td>
      <img src="https://img.shields.io/badge/-SaaS-8B5CF6?style=flat-square" alt="SaaS" /><br/>
      <strong>멀티테넌트 SaaS</strong><br/>
      서브도메인 기반 회사 전환, 회사별 독립 FAQ / 설정 / 분석
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-관리자-F59E0B?style=flat-square" alt="관리자" /><br/>
      <strong>관리자 대시보드</strong><br/>
      FAQ CRUD, DnD 정렬, AI 설정, 분석, TanStack Query 서버 상태 캐싱
    </td>
    <td>
      <img src="https://img.shields.io/badge/-복원력-EF4444?style=flat-square" alt="복원력" /><br/>
      <strong>오프라인 폴백</strong><br/>
      Supabase 연결 실패 시 정적 FAQ 데이터로 자동 전환
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-인프라-009639?style=flat-square" alt="인프라" /><br/>
      <strong>서버 직접 구축</strong><br/>
      가비아 호스팅 + NGINX + Cloudflare CDN/SSL
    </td>
    <td>
      <img src="https://img.shields.io/badge/-테스트-2EAD33?style=flat-square" alt="테스트" /><br/>
      <strong>E2E 테스트</strong><br/>
      Playwright 21개 테스트 (챗봇 플로우, 관리자 인증, Smoke)
    </td>
  </tr>
</table>

---

## 기술 스택

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
      <img src="https://img.shields.io/badge/-상태_관리-764ABC?style=for-the-badge" alt="상태 관리" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Zustand_5-764ABC?style=flat-square&logo=npm&logoColor=white" />
      <sub>(클라이언트 상태, 5개 독립 스토어)</sub>&nbsp;
      <img src="https://img.shields.io/badge/TanStack_Query_v5-FF4154?style=flat-square&logo=reactquery&logoColor=white" />
      <sub>(서버 상태 캐싱)</sub>
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
      <img src="https://img.shields.io/badge/-빌드-646CFF?style=for-the-badge" alt="빌드" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white" />
      <img src="https://img.shields.io/badge/React_Router_v7-CA4245?style=flat-square&logo=reactrouter&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-테스트-2EAD33?style=for-the-badge" alt="테스트" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white" />
      <img src="https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white" />
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-인프라-009639?style=for-the-badge" alt="인프라" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white" />
      <sub>(리버스 프록시, SPA 라우팅, gzip)</sub>&nbsp;
      <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" />
      <sub>(SSL/TLS, CDN, DDoS)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-배포-1a1a2e?style=for-the-badge" alt="배포" />
    </td>
    <td>
      <sub>가비아 호스팅 서버 + SCP 직접 배포 (빌드 -- 업로드 -- NGINX 서빙)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-라이브러리-FF6F61?style=for-the-badge" alt="라이브러리" />
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
      <img src="https://img.shields.io/badge/-개발_도구-191919?style=for-the-badge" alt="개발 도구" />
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

## 아키텍처

```
Cloudflare (DNS / SSL 종단 / CDN 캐싱 / DDoS 방어)
*.goofitalk.co.kr --> 서브도메인 라우팅
         |
         v
+-----------------------------------------+
|   가비아 호스팅 서버 (NGINX)               |
|   리버스 프록시 / SPA 라우팅 (try_files)   |
|   gzip 압축 / 정적 파일 서빙               |
|   /var/www/chatbot/                       |
+--------------------+--------------------+
                     |
                     v
+--------------------+---------------------------------------+
|   React SPA (Vite 7)                                       |
|                                                            |
|   챗봇 (Zustand)              관리자 (/admin)               |
|   - messageStore              - TanStack Query v5 캐싱      |
|   - navigationStore           - useQuery / useMutation      |
|   - searchStore               - staleTime: Infinity         |
|                               - mutation 기반 캐시 무효화    |
|   useChatHandlers             - FAQ CRUD / DnD 정렬         |
|   useChatSearch               - AI 설정 / 분석 대시보드      |
|   handleSend (AI Fallback)    - 역할: superadmin/admin/     |
|                                 viewer                      |
+--------------------+---------------------------------------+
                     |
+--------------------+---------------------------------------+
|   Supabase                                                 |
|                                                            |
|   PostgreSQL    Auth    Storage                             |
|                                                            |
|   Edge Functions:                                          |
|   +-- chat-ai (RAG + Claude API)                           |
|   +-- signup-with-company                                  |
|   +-- list-company-users                                   |
|                                                            |
|   연결 실패 --> src/data/faq/ 정적 데이터 자동 폴백          |
+------------------------------------------------------------+
```

---

## 기술적 의사결정

> 각 의사결정의 **문제 -- 고려한 방안 -- 결정 -- 결과**는 **[기술_설계_노트.md](./기술_설계_노트.md)** 에서 확인할 수 있습니다.

| 의사결정 | 문제 | 해결 | 결과 |
|:---------|:-----|:-----|:-----|
| [4단계 스마트 검색](./기술_설계_노트.md#1-4단계-스마트-검색-설계) | AI 전수 처리 시 비용 폭증 | 규칙 기반 3단계 + AI Fallback 4단계 | 1~3단계 ~100ms, AI 호출 비용 대폭 절약 |
| [한글 초성 검색](./기술_설계_노트.md#2-한글-초성-검색-알고리즘-직접-구현) | `ㅅㄱ` -> `수강신청` 매칭 불가 | 유니코드 수학 공식 직접 구현 (59줄, 의존성 0) | 한글 11,172자 완벽 지원 |
| [이중 상태 설계](./기술_설계_노트.md#3-zustand--tanstack-query-이중-상태-설계) | 클라이언트/서버 상태 혼재, 불필요한 리렌더링 | Zustand 5-Store + TanStack Query 역할 분리 | 페이지 전환 시 캐시 히트로 즉시 렌더링 |
| [Tree Diff/Save](./기술_설계_노트.md#4-tree-diffsave-패턴-faq-편집-최적화) | FAQ 1개 수정에 1000개 쿼리 발생 | Git 스타일 diff 알고리즘 | 변경분만 DB 반영 (쿼리 1개) |
| [RAG + 멀티테넌트 격리](./기술_설계_노트.md#5-rag--멀티테넌트-격리) | 멀티테넌트 AI 데이터 격리 | 회사별 FAQ 동적 주입 + 6중 보안 계층 | 회사 추가 시 코드 수정 0 |
| [Supabase 폴백](./기술_설계_노트.md#6-supabase-폴백--on-demand-지연-로딩) | 서버 장애 시 서비스 중단 | 정적 데이터 자동 폴백 + 2단계 지연 로딩 | Zero-downtime 보장 |
| [번들 최적화](./기술_설계_노트.md#7-vite-번들-최적화) | 챗봇 유저가 Admin 코드까지 로드 | React.lazy + Vite manualChunks | ~58% 번들 크기 절감 |
| [서버 인프라 직접 구축](./기술_설계_노트.md#8-서버-인프라-직접-구축) | 매니지드 플랫폼 의존, 인프라 학습 부재 | 가비아 + NGINX + Cloudflare 직접 구성 | SSH/파일권한/SELinux 실무 경험 |

---

## AI 기반 개발

> 상세 내용: [기술_설계_노트.md #9](./기술_설계_노트.md#9-ai-기반-개발-프로세스)

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

## 프로젝트 구조

```
chatbot/
|
|-- src/
|   |-- App.tsx                        # 라우팅 + 서브도메인 멀티테넌트
|   |
|   |-- chatbot/                       # 챗봇 모듈
|   |   |-- components/                #   채팅 UI (메시지, 입력, 네비게이션, 검색 결과)
|   |   |-- hooks/                     #   use-chat-handlers, use-chat-search,
|   |   |                              #   use-chat-message
|   |   |-- stores/                    #   Zustand x3 (message, navigation, search)
|   |   +-- utils/                     #   초성 검색, 카테고리 아이콘, 이미지 줌
|   |
|   |-- admin/                         # 관리자 모듈
|   |   |-- pages/                     #   FAQ, 분석, 설정, AI 설정, 회사 관리
|   |   |-- components/                #   트리 편집, DnD, 차트, 설정 폼
|   |   |-- hooks/queries/             #   TanStack Query 훅 (FAQ, 분석, 설정, 회사)
|   |   |-- contexts/                  #   AdminContext (역할 기반 접근 제어)
|   |   +-- lib/                       #   admin-api, tree-diff, tree-save, query-client
|   |
|   |-- hooks/                         # 공유 훅 (use-faq-data, use-company)
|   |-- lib/                           # 공유 라이브러리 (supabase, ai-client,
|   |                                  #   faq-fetcher, sanitize)
|   |-- config/                        # 회사 설정, 상수
|   |-- types/                         # TypeScript 타입 정의
|   |-- data/faq/                      # 정적 FAQ 데이터 (오프라인 폴백)
|   |-- pages/landing/                 # 랜딩 페이지 섹션 컴포넌트
|   +-- components/ui/                 # shadcn 기반 공통 UI
|
|-- supabase/
|   |-- functions/                     # Edge Functions (chat-ai, signup, users)
|   +-- migrations/                    # DB 마이그레이션 SQL
|
|-- e2e/                               # Playwright E2E 테스트
|   |-- chatbot/                       #   챗봇 플로우 테스트 (10개)
|   |-- admin/                         #   관리자 인증/FAQ 테스트 (7개)
|   |-- smoke/                         #   페이지 로드 확인 (3개)
|   +-- helpers/                       #   셀렉터, 대기 헬퍼, 인증 fixture
|
+-- .claude/                           # Claude Code 설정 (AI 개발 도구)
    |-- agents/                        #   AI 서브에이전트 정의
    |-- skills/                        #   커스텀 슬래시 명령어
    |-- rules/                         #   프로젝트 코딩 규칙
    +-- docs/                          #   Claude Code 가이드
```

---

## 코드 품질

| 영역 | 내용 |
|:-----|:-----|
| ![](https://img.shields.io/badge/단위_테스트-Vitest-6E9F18?style=flat-square&logo=vitest&logoColor=white) | 한글 초성 검색, Tree Diff 등 핵심 로직 검증 |
| ![](https://img.shields.io/badge/E2E_테스트-Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white) | 21개 테스트 -- 챗봇 플로우, 관리자 인증, Smoke |
| ![](https://img.shields.io/badge/에러-ErrorBoundary-EF4444?style=flat-square) | 런타임 에러 시 화이트 스크린 방지 |
| ![](https://img.shields.io/badge/접근성-ARIA_Labels-0EA5E9?style=flat-square) | `role="log"`, `role="group"`, `aria-label` 적용 |
| ![](https://img.shields.io/badge/타입_안전성-Strict_Mode-3178C6?style=flat-square&logo=typescript&logoColor=white) | `any` 타입 제거, 전체 코드베이스 `strict` 모드 |
| ![](https://img.shields.io/badge/보안-DOMPurify+RLS-10B981?style=flat-square) | XSS 방어, Supabase RLS, 세션 격리 |
| ![](https://img.shields.io/badge/Git_Hooks-Husky-1a1a2e?style=flat-square&logo=git&logoColor=white) | pre-commit lint-staged 자동 실행 |

---

<p align="center">
  <sub>Built with</sub>&nbsp;
  <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code" />&nbsp;
  <sub>by a solo full-stack developer</sub>
</p>
