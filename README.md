# Goofi Talk — 멀티테넌트 AI FAQ 챗봇

![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![TypeScript](https://img.shields.io/badge/TypeScript_5.9-3178C6?style=flat-square&logo=typescript&logoColor=white)
![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)
![Claude AI](https://img.shields.io/badge/Claude_API-D97757?style=flat-square&logo=anthropic&logoColor=white)
![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS_v4-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)
![Vite](https://img.shields.io/badge/Vite_7-646CFF?style=flat-square&logo=vite&logoColor=white)
![TanStack Query](https://img.shields.io/badge/TanStack_Query_v5-FF4154?style=flat-square&logo=reactquery&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat-square&logo=playwright&logoColor=white)
![NGINX](https://img.shields.io/badge/NGINX-009639?style=flat-square&logo=nginx&logoColor=white)
![Cloudflare](https://img.shields.io/badge/Cloudflare-F38020?style=flat-square&logo=cloudflare&logoColor=white)

> 서브도메인 기반 멀티테넌트 AI FAQ 챗봇 — 4단계 스마트 검색(규칙 기반 3단계 + AI Fallback), 관리자 대시보드, 회사별 독립 서비스를 제공하는 풀스택 SPA

**[랜딩 페이지](https://goofitalk.co.kr) · [챗봇 데모](https://kcie.goofitalk.co.kr) · [관리자 페이지](https://goofitalk.co.kr/admin)**

---

## 왜 만들었나

건설산업교육원에서 근무하면서 고객센터에 매일 같은 질문이 반복되는 걸 직접 봤습니다. 수강신청 방법, 교육 일정, 수료증 발급 — 답변이 정해져 있는 질문인데 매번 전화로 안내하고 있었습니다.

채널톡 같은 외부 솔루션을 검토했지만, FAQ 특화 기능이 부족하고 비용도 부담이었습니다. **차라리 우리 현장에 맞는 걸 직접 만들자**고 판단했고, 기획부터 배포까지 혼자 진행했습니다. 이후 다른 기관에도 제공할 수 있도록 멀티테넌트 구조로 확장했습니다.

| 문제 | 해결 |
| --- | --- |
| 반복 FAQ 문의로 고객센터 부하 | 대화형 챗봇으로 셀프 서비스 |
| 외부 솔루션 비용 부담 + FAQ 특화 기능 부족 | FAQ에 집중한 자체 서비스 기획·개발 |
| 비개발자의 콘텐츠 관리 어려움 | 드래그 앤 드롭 FAQ CRUD 관리자 페이지 |
| 단순 키워드 검색의 낮은 정확도 | 4단계 검색 + 한글 초성 매칭 + AI Fallback |
| 단일 기관 한정 서비스 | 서브도메인 기반 멀티테넌트로 확장 |

---

## 주요 기능

### 챗봇

- **4단계 스마트 검색** — 질문 전문 검색 → 서브카테고리 키워드 → 카테고리 키워드 → AI Fallback
- **한글 초성 검색** — `ㅅㄱ` 입력으로 `수강신청` 관련 질문 검색
- **AI Fallback (Claude API)** — 검색 실패 시 회사 FAQ를 시스템 프롬프트에 주입하여 자연어 답변 생성
- **오프라인 폴백** — Supabase 연결 실패 시 정적 FAQ 데이터로 자동 전환

### 관리자

- **FAQ CRUD** — 카테고리/서브카테고리/질문 트리 구조, @dnd-kit 드래그 앤 드롭 정렬
- **리치 텍스트 편집** — TipTap 에디터 + Supabase Storage 이미지 업로드
- **분석 대시보드** — 검색 로그, 클릭 분석, AI 호출 통계 (Recharts)
- **AI 설정** — 회사별 모델 선택, 커스텀 시스템 프롬프트, AI 활성화 토글
- **역할 기반 접근 제어** — superadmin / admin / viewer 3역할
- **위젯 임베드** — iframe 삽입 코드 자동 생성, 위치 커스터마이징

### 멀티테넌트

- **서브도메인 기반 회사 전환** — `kcie.goofitalk.co.kr`, `aifa.goofitalk.co.kr`
- **회사별 데이터 격리** — 모든 쿼리에 `company_id` 필터
- **셀프서비스 온보딩** — 서비스 신청 → 슈퍼관리자 승인 → 서브도메인 추가 (코드 수정 0)

---

## 기술 스택

| 구분 | 기술 |
| --- | --- |
| **프론트엔드** | React 19, TypeScript 5.9, Tailwind CSS v4, shadcn/ui |
| **상태 관리** | Zustand 5 (클라이언트 UI 상태) + TanStack Query v5 (서버 데이터 캐싱) |
| **백엔드** | Supabase (PostgreSQL 9테이블 + Auth + Storage + Edge Functions 6개) |
| **AI** | Anthropic Claude API — Edge Function에서 FAQ 컨텍스트 주입 방식 |
| **라우팅** | React Router v7 (Lazy Loading) |
| **빌드** | Vite 7 (manualChunks 분할) |
| **리치 텍스트** | TipTap (StarterKit + Underline + Color + Link + Image) |
| **DnD** | @dnd-kit/core, @dnd-kit/sortable |
| **차트** | Recharts |
| **애니메이션** | framer-motion |
| **보안** | DOMPurify (XSS 방어), Supabase 클라이언트 세션 격리 |
| **테스트** | Vitest (단위 127개) + Playwright (E2E 20개) |
| **인프라** | 가비아 호스팅 서버 + NGINX (리버스 프록시, SPA 라우팅, gzip) |
| **CDN / 보안** | Cloudflare (SSL/TLS, CDN 캐싱, DNS, DDoS 방어) |
| **배포** | deploy.sh — 빌드 → SCP 업로드 → NGINX 서빙 |
| **AI 개발 도구** | Claude Code + Shrimp Task MCP |

---

<img width="1408" height="768" alt="Gemini_Generated_Image_b8ydsrb8ydsrb8yd" src="https://github.com/user-attachments/assets/a6a1ba82-6d68-4fd2-9ccc-3ca350210c42" />

---

## 기술적 도전

### 1. 4단계 스마트 검색 — AI 비용을 줄이면서 검색 품질 유지

모든 질문을 AI로 보내면 비용이 폭증합니다. 규칙 기반 3단계로 먼저 처리하고, AI는 최후 수단으로만 호출합니다.

```
사용자 입력
  │
  ├─ 1단계: 질문 전문 ilike 검색 (DB)
  │     "수강신청 방법" → 직접 매칭
  │
  ├─ 2단계: 서브카테고리 키워드 + 초성 매칭
  │     "ㅅㄱ" → 초성 추출 → "수강" 포함 질문 검색
  │
  ├─ 3단계: 카테고리 키워드 매칭
  │     "교육" → 교육 카테고리 전체 질문 반환
  │
  └─ 4단계: AI Fallback (Claude API)
        회사 FAQ 전체를 시스템 프롬프트에 주입 → 자연어 답변
        ※ 1~3단계 모두 실패 + AI 활성화 상태에서만 호출
```

### 2. 한글 초성 검색

한글 유니코드 구조(`AC00` ~ `D7A3`)를 분석해 초성을 추출합니다. DB의 `ilike`로는 초성 매칭이 불가능하기 때문에 클라이언트에서 처리합니다.

```
유니코드 공식: (초성 × 21 + 중성) × 28 + 종성 + 0xAC00

"수강신청" → 초성 추출 → "ㅅㄱㅅㅊ"
사용자 입력 "ㅅㄱ" → 전방 매칭으로 검색 성공
```

### 3. AI 컨텍스트 주입 — 벡터 RAG가 아닌 단순 방식을 선택한 이유

이 프로젝트는 pgvector + 임베딩 기반 RAG가 아니라, **회사 FAQ 전체를 시스템 프롬프트에 직렬화해 주입하는 방식**을 사용합니다.

| 항목 | 벡터 RAG | 컨텍스트 주입 (현재) |
|------|---------|--------------------|
| 인프라 | pgvector + 임베딩 파이프라인 | 일반 SQL SELECT |
| 사전 처리 | FAQ 변경 시마다 임베딩 재생성 | 없음 |
| 토큰 비용 | 관련 청크만 주입 → 대규모에 유리 | FAQ 100개 기준 ~수천 토큰 |
| 적합한 규모 | 수천~수만 건 | **수십~수백 건 (현재 규모)** |
| 구현 복잡도 | 높음 | 낮음 |

현재 고객사의 FAQ는 100개 이하이므로 이 방식이 합리적입니다. FAQ가 수백 건을 넘어 토큰 비용이 문제가 되면 pgvector 기반으로 마이그레이션할 계획입니다.

**Edge Function(`chat-ai`) 설계:**
- Anthropic Prompt Caching(`cache_control: ephemeral`)으로 시스템 프롬프트 캐싱
- 모델 분기: 회사별 구독 플랜 → 회사 AI 설정 → 기본값 순으로 모델 결정
- IP 기반 Rate Limiting (분당 20회)
- 토큰 사용량 로깅 (input/output/cached tokens)
- 세션 격리: `supabase-public.ts` (persistSession: false) 사용

### 4. TanStack Query v5 — Admin 서버 상태 캐싱

Admin에서 `useState` + `useEffect`로 데이터를 fetch하면, 페이지 전환할 때마다 로딩이 발생합니다. TanStack Query를 도입해 캐싱과 무효화를 체계적으로 관리했습니다.

```typescript
// Query Key Factory — 계층적 키로 세밀한 캐시 무효화
const adminKeys = {
  all: ["admin"],
  categories: (companyId) => [...adminKeys.all, "categories", companyId],
  suggestions: (companyId) => [...adminKeys.all, "suggestions", companyId],
};

// staleTime: Infinity — mutation이 캐시 갱신을 전담
// → 페이지 전환 시 캐시 히트로 즉시 렌더링
```

### 5. Tree Diff 기반 FAQ 저장

FAQ 1개를 수정했는데 전체 트리를 DB에 저장하는 건 낭비입니다. 원본 트리와 편집 트리를 비교해서 변경된 노드만 서버에 보냅니다.

```typescript
// 1. 편집은 메모리 내 트리에서 수행
// 2. 저장 시 isTreeEqual()로 원본과 비교
// 3. computeTreeDiff()로 변경분만 추출 → { created, updated, deleted }
// 4. 변경분만 DB에 반영
```

### 6. 서브도메인 기반 멀티테넌트

```
사용자 접속
  → getSubdomainSlug() — hostname에서 서브도메인 추출
    ├── kcie.goofitalk.co.kr → "kcie"
    ├── aifa.localhost → "aifa"
    ├── *.vercel.app → null (플랫폼 도메인 제외)
    └── example.co.kr → null (한국 2차 도메인 처리)

새 회사 추가:
  1. /apply 페이지에서 서비스 신청 (셀프서비스)
  2. 슈퍼관리자가 승인 (원클릭)
  3. NGINX에 서브도메인 1줄 추가
  → 애플리케이션 코드 수정 0줄
```

### 7. 서버 인프라 직접 구축

Vercel 같은 매니지드 서비스에 의존하지 않고, 가비아 호스팅 서버에 NGINX를 직접 구축했습니다.

```
배포: npm run build → SCP 업로드 → NGINX 서빙
NGINX: try_files (SPA 라우팅) + gzip + 서브도메인 와일드카드
보안: Cloudflare DNS 프록시 → SSL 종단 + CDN + DDoS 방어
```

---

## AI 기반 개발 프로세스

이 프로젝트는 **Claude Code**를 코드 생성 도구가 아닌, 체계적인 개발 워크플로우로 활용했습니다. 프로젝트 규칙과 컨텍스트를 파일로 관리하여 AI가 프로젝트 컨벤션을 이해한 상태에서 작업합니다.

### 프로젝트 구조

```
.claude/
├── agents/                          # AI 서브에이전트 6개
│   ├── code-reviewer.md             #   코드 리뷰 자동화
│   ├── test-runner-fixer.md         #   테스트 실행 + 실패 시 자동 수정
│   ├── react-supabase-fullstack.md  #   React + Supabase 풀스택 전문가
│   ├── tanstack-query-migrator.md   #   TanStack Query 마이그레이션
│   ├── development-planner.md       #   ROADMAP.md 관리
│   └── prd-generator.md             #   PRD 문서 생성
├── skills/                          # 커스텀 슬래시 명령어 4개
│   ├── git-commit/                  #   /commit — 변경사항 분석 후 커밋
│   ├── frontend-design/             #   /frontend-design — UI 컴포넌트 생성
│   ├── readme/                      #   /readme — README 자동 생성
│   └── roadmap-check/               #   /roadmap-check — 진행률 확인
├── rules/                           # 프로젝트 규칙 6개 파일
│   ├── 01-project-overview.md       #   기술 스택, Decision 트리
│   ├── 02-coding-conventions.md     #   코드 스타일, 보안, 금지사항 12개
│   ├── 03-chatbot-patterns.md       #   채팅 패턴, 검색 로직 (globs 조건부)
│   ├── 04-admin-patterns.md         #   관리자 패턴, FAQ 관리 (globs 조건부)
│   ├── 05-infrastructure.md         #   Edge Functions, Vite 번들 (globs 조건부)
│   └── 06-testing.md                #   E2E 테스트 규칙 (globs 조건부)
└── docs/                            # Claude Code 가이드
```

### 컨텍스트 윈도우 최적화

AI는 매 요청마다 프로젝트 규칙을 읽습니다. 규칙 파일 6개를 YAML frontmatter `globs` 기반 조건부 로딩으로 구성하여, **작업 중인 파일과 관련된 규칙만 로드**합니다.

- **항상 로드** (01, 02): 프로젝트 개요, 코드 스타일, 보안 규칙
- **조건부 로드** (03~06): 챗봇 파일 작업 시 → 03, Admin 파일 작업 시 → 04, ...

### Shrimp Task MCP

MCP 기반 태스크 관리로 구조화된 워크플로우를 강제합니다.

```
plan_task → analyze_task → split_tasks → execute_task → verify_task
                                                            │
                                                  ROADMAP.md 자동 업데이트
```

---

## 프로젝트 구조

```
chatbot/
├── src/
│   ├── chatbot/                  # 챗봇 모듈
│   │   ├── components/           #   채팅 UI (메시지, 입력, 검색 결과)
│   │   ├── hooks/                #   use-chat-handlers, use-chat-search, use-chat-message
│   │   ├── stores/               #   Zustand 3개 (message, navigation, search)
│   │   └── utils/                #   초성 검색, 카테고리 아이콘
│   │
│   ├── admin/                    # 관리자 모듈
│   │   ├── pages/                #   FAQ, 분석, AI 설정, 회사 관리
│   │   ├── components/           #   트리 편집, DnD, 차트, 설정 폼
│   │   ├── hooks/queries/        #   TanStack Query 훅
│   │   ├── contexts/             #   AdminContext (역할 기반 접근 제어)
│   │   └── lib/                  #   admin-api, tree-diff, tree-save
│   │
│   ├── hooks/                    # 공유 훅 (use-faq-data, use-company)
│   ├── lib/                      # supabase, ai-client, faq-fetcher, sanitize
│   ├── config/                   # 회사 설정, 상수
│   ├── types/                    # TypeScript 타입 정의
│   ├── data/faq/                 # 정적 FAQ 데이터 (오프라인 폴백)
│   ├── pages/landing/            # 랜딩 페이지
│   └── components/ui/            # shadcn 기반 공통 UI
│
├── supabase/
│   ├── functions/                # Edge Functions 6개
│   └── migrations/               # DB 마이그레이션
│
├── e2e/                          # Playwright E2E 테스트 (7개 spec, 20개 테스트)
├── docs/                         # 프로젝트 문서 (PRD, 기술 결정, ROADMAP)
└── CLAUDE.md                     # 프로젝트 메인 지침
```

---

## 코드 품질

| 영역 | 내용 |
| --- | --- |
| **단위 테스트** | Vitest 127개 — 초성 검색, Tree Diff, slug 유틸, 날짜 포맷 |
| **E2E 테스트** | Playwright 20개 — 챗봇 플로우, 관리자 인증, Smoke |
| **보안** | DOMPurify XSS 방어, Supabase 클라이언트 세션 격리 (관리자/챗봇 분리) |
| **에러 복원력** | ErrorBoundary, Supabase 폴백, AI 호출 실패 시 안내 메시지 |
| **접근성** | `role="log"`, `role="group"`, `aria-label` |
| **타입 안전성** | strict 모드, any 타입 제거 |
| **코드 품질** | Husky pre-commit 훅 + lint-staged |

