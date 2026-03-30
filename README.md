<p align="center">
  <img src="https://img.shields.io/badge/Goofi_Talk-AI_FAQ_Chatbot_SaaS-000000?style=for-the-badge&labelColor=000000" alt="Goofi Talk" height="40" />
</p>

<p align="center">
  <strong>멀티테넌트 AI FAQ 챗봇 SaaS 플랫폼</strong><br/>
  <sub>현장 문제 발견 → 채널톡 방문·견적 → 자체 기획·개발 → 실서비스 배포</sub>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/TypeScript_5.9-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript" />
  <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white" alt="Supabase" />
  <img src="https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude AI" />
  <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code" />
  <img src="https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white" alt="NGINX" />
  <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" alt="Cloudflare" />
</p>

<p align="center">
  <a href="https://goofitalk.co.kr"><img src="https://img.shields.io/badge/Landing_Page-06B6D4?style=for-the-badge&logo=googlechrome&logoColor=white" alt="Landing Page" /></a>&nbsp;
  <a href="https://kcie.goofitalk.co.kr"><img src="https://img.shields.io/badge/Chatbot_Demo-000000?style=for-the-badge&logo=chatbot&logoColor=white" alt="Chatbot Demo" /></a>&nbsp;
  <a href="https://goofitalk.co.kr/admin"><img src="https://img.shields.io/badge/Admin_Page-8B5CF6?style=for-the-badge&logo=shield&logoColor=white" alt="Admin Page" /></a>
</p>

---

## Overview

**Goofi Talk**은 기업 고객센터의 반복 FAQ 문의를 줄이기 위해 **기획부터 배포까지 1인으로 진행**한 AI FAQ 챗봇 SaaS 플랫폼입니다.

현장에서 문제를 발견하고, 채널톡을 직접 방문·견적 비교한 뒤, FAQ에 특화된 서비스를 직접 기획·설계하여 실서비스에 배포했습니다. 서브도메인 기반 멀티테넌트 구조로 하나의 코드베이스에서 여러 회사에 독립적인 FAQ 챗봇을 제공합니다.

개발은 **Claude Code + Shrimp Task MCP + MCP 서버 4개**를 활용한 AI 기반 워크플로우로 진행했으며, AI의 컨텍스트 윈도우 비용을 최적화하고 에이전트를 역할별로 분리하는 등 **AI를 시스템으로 관리하는 방식**으로 프로젝트를 완성했습니다.

<img width="800" alt="chatbot" src="https://github.com/user-attachments/assets/63df802b-cefb-404a-9b8e-db19dcd11f79" />

---

## 목차

- [도입 배경](#도입-배경)
- [Problem & Solution](#problem--solution)
- [주요 기능](#주요-기능)
- [서비스 설계 결정](#서비스-설계-결정)
- [AI 활용 전략](#ai-활용-전략)
- [기술 스택](#기술-스택)
- [아키텍처](#아키텍처)
- [프로젝트 구조](#프로젝트-구조)

---

## 도입 배경

건설산업교육원에서 근무하면서 고객센터로 들어오는 **월 수백 건 이상의 반복 FAQ 문의**를 직접 목격했습니다. 수강신청 방법, 교육 일정, 수료증 발급 같은 동일한 질문이 매일 반복되고 있었습니다.

이 문제를 해결하기 위해 **채널톡을 직접 방문하여 서비스를 분석하고 견적을 수령**했습니다. 그러나 월 구독 비용이 교육기관 예산 대비 과했고, 채널톡이 제공하는 CRM/마케팅 기능은 우리에게 필요하지 않았습니다. 우리에게 필요한 건 **FAQ 자동 응답**뿐이었습니다.

그래서 결정했습니다 — **FAQ 챗봇에 특화된 서비스를 직접 만들자.**

```
현장에서 발견한 문제                  기존 솔루션 검토                     직접 개발 결정
+---------------------+            +---------------------+            +---------------------+
| 고객센터 반복 FAQ     |            | 채널톡 직접 방문      |            | Goofi Talk 기획      |
| 월 수백 건 이상       |  ------->  | 서비스 분석 + 견적    |  ------->  | FAQ 특화 챗봇 SaaS    |
| 동일 질문 매일 반복    |            | CRM 중심, 비용 과다   |            | 비용 절감 + 맞춤 기능  |
+---------------------+            +---------------------+            +---------------------+
```

직접 만들면서 **건설산업교육원의 운영 환경에 맞는 기능**을 설계할 수 있었고, 이를 다른 기관에도 제공할 수 있도록 **멀티테넌트 SaaS 구조**로 확장했습니다.

---

## Problem & Solution

| Problem | Solution | Impact |
|:--------|:---------|:-------|
| 반복 FAQ 문의로 인한 고객센터 부하 | 대화형 챗봇 셀프 서비스 | CS 인력 의존도 감소 |
| 외부 솔루션(채널톡) 비용 부담 | FAQ 특화 자체 서비스 기획·개발 | 연간 수백만 원 절감 |
| 비개발자의 콘텐츠 관리 어려움 | Drag & Drop FAQ CRUD 관리자 페이지 | 운영자 자율 관리 가능 |
| 단순 키워드 검색의 낮은 정확도 | 4단계 검색 + AI Fallback (비용 최적화 설계) | 검색 커버리지 극대화 |
| 단일 고객사 한정 서비스 | 서브도메인 기반 멀티테넌트 SaaS | N개 회사 동시 서비스 |
| AI API 비용 폭증 우려 | 규칙 기반 3단계로 먼저 처리, AI는 최후 수단 | API 호출 비용 대폭 절감 |

---

## 주요 기능

<table>
  <tr>
    <td width="50%">
      <img src="https://img.shields.io/badge/-Core-3178C6?style=flat-square" alt="Core" /><br/>
      <strong>4단계 검색 설계</strong><br/>
      규칙 기반 3단계(무료) + AI Fallback(유료) — 비용 최적화 구조
    </td>
    <td width="50%">
      <img src="https://img.shields.io/badge/-AI-D97757?style=flat-square" alt="AI" /><br/>
      <strong>AI Fallback (Claude API)</strong><br/>
      검색 실패 시 회사별 FAQ를 AI에 전달하여 맥락 기반 답변 생성
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-SaaS-8B5CF6?style=flat-square" alt="SaaS" /><br/>
      <strong>멀티테넌트 SaaS</strong><br/>
      서브도메인 기반 회사 전환, 회사별 독립 FAQ / 설정 / 분석
    </td>
    <td>
      <img src="https://img.shields.io/badge/-관리자-F59E0B?style=flat-square" alt="관리자" /><br/>
      <strong>관리자 대시보드</strong><br/>
      FAQ CRUD, DnD 정렬, AI 설정, 분석 대시보드, 역할 기반 접근 제어
    </td>
  </tr>
  <tr>
    <td>
      <img src="https://img.shields.io/badge/-기획-10B981?style=flat-square" alt="기획" /><br/>
      <strong>PRD 35개 기능 · DB 9개 테이블</strong><br/>
      Guest · 회사관리자 · 슈퍼관리자 3종 사용자 시나리오 설계
    </td>
    <td>
      <img src="https://img.shields.io/badge/-인프라-009639?style=flat-square" alt="인프라" /><br/>
      <strong>서버 직접 구축</strong><br/>
      가비아 호스팅 + NGINX + Cloudflare CDN/SSL
    </td>
  </tr>
</table>

---

## 서비스 설계 결정

> 각 의사결정의 상세 내용은 **[기술_설계_노트.md](./기술_설계_노트.md)** 에서 확인할 수 있습니다.

| 설계 결정 | 문제 | 해결 | 결과 |
|:---------|:-----|:-----|:-----|
| [4단계 검색 설계](./기술_설계_노트.md#1-4단계-스마트-검색-설계) | 모든 질문을 AI로 처리하면 비용 폭증 | 규칙 기반 3단계(무료)로 먼저 처리, AI는 최후 수단 | API 비용 대폭 절감 |
| [상태 관리 설계](./기술_설계_노트.md#3-zustand--tanstack-query-이중-상태-설계) | Admin 페이지 전환 시 같은 데이터 반복 호출 | UI 상태와 서버 데이터 분리, 캐싱으로 재요청 방지 | 페이지 전환 시 즉시 렌더링 |
| [FAQ 편집 설계](./기술_설계_노트.md#4-tree-diffsave-패턴-faq-편집-최적화) | FAQ 1개 수정해도 전체를 다시 저장 | 변경분만 골라서 저장하는 구조 (Git 원리 착안) | 1000개 중 1개만 수정하면 1개만 저장 |
| [멀티테넌트 격리](./기술_설계_노트.md#5-rag--멀티테넌트-격리) | A회사 FAQ가 B회사에 노출되면 안 됨 | 회사 ID 필터 + AI에 해당 회사 FAQ만 전달 + 세션 분리 | 새 회사 추가 시 코드 수정 0 |
| [검색 비용 최적화](./기술_설계_노트.md#1-4단계-스마트-검색-설계) | 채널톡 대비 비용 절감이 핵심 목표 | 한글 초성 검색 등 클라이언트 로직으로 무료 처리 범위 확대 | 대부분 질문을 비용 0원으로 처리 |
| [서버 인프라 직접 구축](./기술_설계_노트.md#8-서버-인프라-직접-구축) | 매니지드 플랫폼 의존, 인프라 학습 부재 | 가비아 + NGINX + Cloudflare 직접 구성 | SSH/리버스프록시/SSL 실무 경험 |

---

## AI 활용 전략

이 프로젝트는 **Claude Code**를 단순 코드 생성 도구가 아닌, **시스템화된 AI 워크플로우**로 활용하여 진행했습니다.

### 컨텍스트 윈도우 비용 최적화

AI는 매 요청마다 프로젝트 규칙을 읽어야 하지만, 긴 문서를 매번 읽으면 비용이 폭증합니다.

```
Before: CLAUDE.md 530줄 → 매 요청마다 전부 읽음 (비용 낭비)
After:  CLAUDE.md 53줄 (핵심만) + docs/ 6개 상세 문서 (필요 시만 참조)
결과:   컨텍스트 윈도우 ~90% 절감
```

### Shrimp Task Manager (vs Taskmaster AI)

Taskmaster AI는 프로젝트 초기부터 사용해야 효과적이지만, Goofi Talk은 이미 개발 중간 단계였습니다. **중도 투입이 가능한 Shrimp Task MCP**를 선택하여, 태스크별 분석→구현→검증 3단계를 강제하고, 완료된 태스크는 ROADMAP.md에 자동 반영하도록 구성했습니다.

```
plan_task → analyze_task → split_tasks → execute_task → verify_task
```

### AI에게 "일 잘 시키는" 4가지 도구

| 도구 | 활용 방식 |
|:-----|:---------|
| **Skills** | `/commit`, `/status` 등 커스텀 명령어로 반복 프롬프트 제거, 컨텍스트 절약 |
| **Agents 8종** | code-reviewer, planner, test-runner 등 역할별 분리. 탐색 에이전트를 먼저 실행하여 메인 컨텍스트 오염 방지 |
| **Rules** | 금지 패턴 13개, 코딩 컨벤션 규칙으로 AI 실수 사전 차단 |
| **Frontend-Design** | 랜딩/로그인/Admin 전면 리디자인에 적용, 프로덕션급 UI 생성 |

### MCP 서버 4개 연동

| MCP 서버 | 활용 방식 |
|:---------|:---------|
| **Supabase** | 테이블 설계 · 마이그레이션 · 데이터 삽입 · 스키마 검증 |
| **Playwright** | E2E 테스트 자동 검증 (21개 테스트) |
| **Context7** | React 19, TanStack Query v5 등 최신 문서 실시간 참조 |
| **shadcn** | 최적 UI 컴포넌트 선택 및 설치 |

### AI로 만든 제품이 AI를 서비스

```
개발 과정: Claude Code (AI) → 코드 생성 · 검토 · 테스트
    ↓
제품 내부: Claude API → RAG 기반 FAQ 자연어 답변 생성
    ↓
분석:     AI Fallback 비율로 FAQ 콘텐츠 품질 측정
```

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
      <sub>(UI 상태)</sub>&nbsp;
      <img src="https://img.shields.io/badge/TanStack_Query_v5-FF4154?style=flat-square&logo=reactquery&logoColor=white" />
      <sub>(서버 데이터 캐싱)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-Backend-3FCF8E?style=for-the-badge" alt="Backend" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white" />
      <sub>(PostgreSQL 9테이블 + Auth + Storage + Edge Functions 6개)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-AI-D97757?style=for-the-badge" alt="AI" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white" />
      <sub>(RAG 기반 FAQ 응답 생성)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-인프라-009639?style=for-the-badge" alt="인프라" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white" />
      <sub>(리버스 프록시, SPA 라우팅)</sub>&nbsp;
      <img src="https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white" />
      <sub>(SSL/TLS, CDN)</sub>
    </td>
  </tr>
  <tr>
    <td align="center">
      <img src="https://img.shields.io/badge/-AI_개발도구-191919?style=for-the-badge" alt="AI 개발도구" />
    </td>
    <td>
      <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=anthropic&logoColor=white" />
      <img src="https://img.shields.io/badge/Shrimp_Task_MCP-191919?style=flat-square" />
      <sub>(태스크 관리)</sub>&nbsp;
      <img src="https://img.shields.io/badge/MCP_Servers_x4-191919?style=flat-square" />
      <sub>(Supabase, Playwright, Context7, shadcn)</sub>
    </td>
  </tr>
</table>

---

## 아키텍처

<img width="800" alt="architecture" src="https://github.com/user-attachments/assets/a9d5843a-51da-40fb-8081-a73af3fc5cc9" />

---

## 프로젝트 구조

```
chatbot/
│
├── src/
│   ├── chatbot/              # 챗봇 모듈 (대화 UI, 검색 로직, 상태 관리)
│   ├── admin/                # 관리자 모듈 (FAQ CRUD, 분석, 설정, 회사 관리)
│   ├── pages/landing/        # 랜딩 페이지
│   ├── hooks/                # 공유 훅 (FAQ 데이터, 회사 설정)
│   ├── lib/                  # 공유 라이브러리 (Supabase, AI 클라이언트)
│   ├── config/               # 회사 설정, 상수
│   ├── types/                # TypeScript 타입 정의
│   └── data/faq/             # 정적 FAQ 데이터 (폴백)
│
├── supabase/
│   ├── functions/            # Edge Functions 6개 (chat-ai, signup, users 등)
│   └── migrations/           # DB 마이그레이션 SQL
│
├── e2e/                      # Playwright E2E 테스트 21개
│
└── .claude/                  # AI 워크플로우 설정
    ├── agents/               #   역할별 에이전트 8종
    ├── skills/               #   커스텀 명령어 (/commit, /status)
    ├── rules/                #   금지 패턴 13개, 코딩 컨벤션
    └── docs/                 #   프로젝트 상세 문서 6개
```

---

<p align="center">
  <sub>기획 · 설계 · AI 활용 · 배포 · 운영 by</sub>&nbsp;
  <strong>이태형</strong>&nbsp;
  <sub>|</sub>&nbsp;
  <sub>AI 워크플로우:</sub>&nbsp;
  <img src="https://img.shields.io/badge/Claude_Code-D97757?style=flat-square&logo=anthropic&logoColor=white" alt="Claude Code" />&nbsp;
  <sub>+</sub>&nbsp;
  <img src="https://img.shields.io/badge/Shrimp_Task_MCP-191919?style=flat-square" alt="Shrimp" />
</p>
