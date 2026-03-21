# Goofi Talk — AI FAQ 챗봇 SaaS 플랫폼

> 멀티테넌트 AI FAQ 챗봇 SaaS — 서브도메인 기반 회사 전환, 4단계 스마트 검색(AI Fallback 포함), 관리자 대시보드를 제공하는 SPA 웹 애플리케이션

<br/>

## 링크

| 구분                   | URL                                                                                    |
| ---------------------- | -------------------------------------------------------------------------------------- |
| **랜딩 페이지**        | [goofistalk.com](https://goofitalk.com)                                               |
| **서비스 신청**        | [goofistalk.com/apply](https://goofitalk.com/apply)                                   |
| **최신 버전 (Vercel)** | [chatbot-taupe-two-95.vercel.app](https://chatbot-taupe-two-95.vercel.app)             |
| **Vercel 관리자**      | [chatbot-taupe-two-95.vercel.app/admin](https://chatbot-taupe-two-95.vercel.app/admin) |

<br/>

## 프로젝트 소개

**Goofi Talk**은 기업 고객센터의 반복 FAQ 문의를 줄이기 위해 **기획부터 배포까지 1인 풀스택으로 개발**한 AI FAQ 챗봇 SaaS 플랫폼입니다.

서브도메인 기반 멀티테넌트 구조로 하나의 코드베이스에서 여러 회사에 독립적인 FAQ 챗봇 서비스를 제공합니다. 기존 3단계 규칙 기반 검색에 **Claude AI Fallback**을 추가하여, 매칭 실패 시에도 AI가 FAQ 컨텍스트를 바탕으로 자연어 답변을 생성합니다.

### 해결한 문제

| 문제                               | 해결 방법                                                          |
| ---------------------------------- | ------------------------------------------------------------------ |
| 반복 FAQ 문의로 인한 고객센터 부하 | 대화형 챗봇으로 셀프 서비스 지원                                   |
| 비개발자의 콘텐츠 관리 어려움      | 드래그 앤 드롭 기반 FAQ CRUD 관리자 페이지 제공                    |
| 단순 키워드 검색의 낮은 정확도     | 4단계 검색 + 한글 초성 검색 + AI Fallback으로 검색 품질 향상       |
| Supabase 장애 시 서비스 중단 위험  | 정적 데이터 자동 폴백 + On-demand 지연 로딩으로 무중단 서비스 보장 |
| 단일 고객사 한정 서비스            | 서브도메인 기반 멀티테넌트 SaaS로 확장                             |

### 주요 특징

- **4단계 스마트 검색** — 질문 전문 검색 → 서브카테고리 키워드 → 카테고리 키워드 → AI Fallback 순으로 최적의 결과 제공
- **AI Fallback (Claude API)** — 규칙 기반 검색 실패 시 Supabase Edge Function을 통해 Claude API + RAG 패턴으로 자연어 답변 생성
- **한글 초성 검색** — `ㅅㄱ` 입력만으로 `수강신청` 관련 질문 검색 가능
- **멀티테넌트 SaaS** — 서브도메인 기반 회사 전환 (`aifa.goofistalk.com`), 회사별 독립 FAQ/설정/분석
- **관리자 대시보드** — FAQ CRUD, 드래그 앤 드롭 정렬, AI 설정, 검색/클릭 분석, 실시간 챗봇 미리보기
- **슈퍼관리자** — 전체 회사 관리, 서비스 신청 승인/거절, 회사간 전환
- **관리자 테마** — Mauve/Blue/Dark 3종 CSS 변수 런타임 전환
- **오프라인 폴백** — Supabase 연결 실패 시 정적 FAQ 데이터로 자동 전환
- **서비스 신청 페이지** — 비개발자도 직접 회사를 등록하고 챗봇을 시작할 수 있는 셀프 서비스
- **테스트 커버리지** — Vitest 기반 단위 테스트로 핵심 로직(초성 검색, Tree Diff) 검증
- **접근성(A11y)** — ARIA role/label 적용, 시맨틱 마크업으로 스크린 리더 지원

<br/>

## 스크린샷

> 챗봇 메인 화면

<!-- 스크린샷 추가 예정: 챗봇 메인 UI -->

> 관리자 대시보드 — FAQ 관리

<!-- 스크린샷 추가 예정: FAQ CRUD 관리 화면 -->

> 관리자 대시보드 — 분석

<!-- 스크린샷 추가 예정: 검색 통계 차트 -->

> 랜딩 페이지 — Goofi Talk 서비스 소개

<!-- 스크린샷 추가 예정: 랜딩 페이지 -->

<br/>

## 기술 스택

| 구분             | 기술                                                    |
| ---------------- | ------------------------------------------------------- |
| **프론트엔드**   | React 19, TypeScript, Tailwind CSS v4                   |
| **상태 관리**    | Zustand 5 (5개 독립 스토어)                             |
| **백엔드 / DB**  | Supabase (PostgreSQL + Auth + Storage + Edge Functions) |
| **AI**           | Anthropic Claude API (Supabase Edge Function `chat-ai`) |
| **라우팅**       | React Router v7 (Lazy Loading)                          |
| **리치 텍스트**  | TipTap (StarterKit + Underline + Color + Link + Image)  |
| **DnD**          | @dnd-kit/core, @dnd-kit/sortable                        |
| **차트**         | Recharts                                                |
| **애니메이션**   | framer-motion (랜딩 페이지)                             |
| **타이포그래피** | @tailwindcss/typography (AI 답변 렌더링)                |
| **HTML 보안**    | DOMPurify (XSS 방어)                                    |
| **테스트**       | Vitest                                                  |
| **빌드**         | Vite                                                    |
| **배포**         | Vercel / SCP (운영 서버 직접 배포)                      |

<br/>

## 아키텍처

```
┌──────────────────────────────────────────────────────────────┐
│                     사용자 (브라우저)                           │
│   서브도메인 접속 → getSubdomainSlug() → companySlug 결정       │
│   ├─ companySlug 있음 → ChatbotWrapper (챗봇)                  │
│   └─ companySlug 없음 → LandingPage (서비스 소개)               │
└───────────────────────┬──────────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────────────────┐
│                   React SPA (Vite)                            │
│                                                              │
│  ┌───────────┐  ┌──────────────┐  ┌──────────┐              │
│  │messageStore│  │navigationStore│  │searchStore│              │
│  │  (메시지)  │  │  (탐색 위치)  │  │(검색 결과)│              │
│  └─────┬─────┘  └──────┬───────┘  └─────┬────┘              │
│        └───────────────┼────────────────┘                    │
│                        ▼                                     │
│           useChatHandlers (이벤트 조율)                        │
│           useChatSearch  (3단계 규칙 검색)                     │
│           handleSend     (4단계 AI Fallback)                  │
│           useChatMessage (타이핑 애니메이션)                    │
│                                                              │
│  ┌─────────────────────────────────────────────────────────┐ │
│  │              관리자 페이지 (/admin)                        │ │
│  │  FAQ CRUD · DnD 정렬 · AI 설정 · 분석 대시보드            │ │
│  │  회사 관리 (슈퍼관리자) · 테마 전환 · 회사 설정            │ │
│  │  역할: superadmin > admin > viewer                       │ │
│  └─────────────────────────────────────────────────────────┘ │
│                                                              │
│  ┌─────────────────────────────────────────────────────────┐ │
│  │              공개 페이지                                  │ │
│  │  랜딩 페이지 (/) · 서비스 신청 (/apply)                   │ │
│  └─────────────────────────────────────────────────────────┘ │
└───────────────────────┬──────────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────────────────┐
│                     Supabase                                  │
│  PostgreSQL (FAQ, 회사, 서비스 신청, 검색 로그, 클릭 분석)     │
│  Auth (관리자 인증, 역할: superadmin/admin/viewer)             │
│  Storage (이미지 업로드)                                      │
│                                                              │
│  Edge Functions:                                             │
│  ├── chat-ai           (RAG + Claude API, JWT 없음)           │
│  ├── signup-with-company (서비스 신청 처리, JWT 없음)           │
│  └── list-company-users  (사용자 목록, JWT 필요)               │
│                                                              │
│  연결 실패 시 → src/data/faq/ 정적 데이터 자동 폴백            │
└──────────────────────────────────────────────────────────────┘
```

<br/>

## 기술적 도전

### 1. 한글 초성 검색 구현

한글 유니코드 구조(`AC00` ~ `D7A3`)를 분석해 초성을 추출하는 알고리즘을 직접 구현했습니다.

```
유니코드 공식: (초성 × 21 + 중성) × 28 + 종성 + 0xAC00

"수강신청" → 초성 추출 → "ㅅㄱㅅㅊ"
사용자 입력 "ㅅㄱ" → 전방 매칭으로 검색 성공
```

단순 `includes()` 비교가 아닌 유니코드 오프셋 계산을 통해, 한글 자음 입력만으로도 자연스러운 검색을 지원합니다.

### 2. DisplayType 기반 선언적 UI 렌더링

봇 메시지에 `displayType` 필드를 두어, 메시지 아래에 렌더링할 UI 컴포넌트를 **데이터로 선언**하는 패턴을 설계했습니다. 조건 분기 없이 메시지 상태만 변경하면 UI가 자동 전환됩니다.

```typescript
// displayType 하나로 렌더링 컴포넌트 결정
addBotMessage({ text: "카테고리를 선택하세요", displayType: "menu" });
addBotMessage({ text: "검색 결과입니다", displayType: "searchResults" });
addBotMessage({ text: aiAnswer, displayType: "aiAnswer", isAiResponse: true });
```

**왜 이 패턴을 선택했나?**

- 채팅 UI 특성상 메시지마다 다른 UI를 렌더링해야 하는데, `if/switch` 분기가 늘어나면 유지보수가 어려워짐
- `displayType`을 데이터로 선언하면, 새 UI 유형 추가 시 컴포넌트만 매핑하면 됨
- 이전 메시지의 UI를 숨기는 `clearAllDisplayTypes()` 패턴으로, 항상 최신 메시지만 인터랙티브하게 유지

### 3. Zustand 5-Store 분리 설계

**왜 5개로 분리했나?**

| 고려한 방안        | 문제점                                               |
| ------------------ | ---------------------------------------------------- |
| 단일 전역 스토어   | 메시지 추가 시 검색/네비게이션 컴포넌트까지 리렌더링 |
| Context API        | 빈번한 상태 변경(타이핑 애니메이션 등)에서 성능 병목 |
| **역할별 5-Store** | 각 스토어 변경이 해당 구독자만 리렌더링 (채택)       |

```
messageStore     → 채팅 메시지, 타이핑 상태 (변경 빈도: 높음)
navigationStore  → 현재 카테고리/서브카테고리 (변경 빈도: 중간)
searchStore      → 검색 결과, 필터된 카테고리 (변경 빈도: 낮음)
faqDataStore     → FAQ 데이터, companyId, 추천검색어 (on-demand 갱신)
companyStore     → 회사 설정, AI 활성화 여부 (마운트 시 1회)
```

셀렉터 훅(`useMessages()`, `useIsTyping()` 등)을 통해 스토어의 특정 필드만 구독하여, Zustand의 **세밀한 구독(fine-grained subscription)** 기능을 최대한 활용했습니다.

### 4. Supabase 폴백 + On-demand 지연 로딩

#### 폴백 설계

외부 DB 의존성으로 인한 서비스 중단 위험을 낮추기 위해, Supabase 연결 실패 시 번들에 포함된 정적 데이터로 자동 전환하도록 설계했습니다.

```
fetchFaqData()
  ├─ 성공 → Supabase DB 데이터 사용
  └─ 실패 → src/data/faq/ 정적 데이터 자동 전환 (서비스 중단 없음)
```

#### On-demand 지연 로딩

초기 로드 시 전체 FAQ 데이터를 한 번에 가져오지 않고, **카테고리 선택 시 해당 서브카테고리와 질문만 로드**하는 지연 로딩 패턴을 구현했습니다.

```
초기 로드: 카테고리 목록만 fetch (경량)
카테고리 클릭 → 해당 서브카테고리 + 질문 on-demand fetch
검색 시 → 서버사이드 검색으로 필요한 결과만 반환
```

**트레이드오프**: 네트워크 요청 횟수는 증가하지만, 초기 페이지 로드 속도와 메모리 사용량을 개선했습니다.

### 5. Tree Diff/Save 패턴

관리자 FAQ 편집은 트리 구조(카테고리 → 서브카테고리 → 질문)를 다루는데, 매 수정마다 전체 트리를 DB에 저장하면 불필요한 쿼리가 발생합니다.

이를 해결하기 위해 **메모리 내 트리 조작 → 저장 시 diff 계산 → 최소 쿼리 실행** 패턴을 구현했습니다.

```typescript
// 1. 편집은 메모리 내 트리에서 수행
const editedTree = [...originalTree]; // 사용자가 자유롭게 수정

// 2. 저장 시 원본과 비교하여 변경분만 추출
const diff = computeTreeDiff(originalTree, editedTree);
// → { created: [...], updated: [...], deleted: [...] }

// 3. 변경분만 DB에 반영 (임시 ID는 INSERT 후 실제 ID로 교체)
await saveTreeDiff(diff);
```

**핵심 설계**:

- 임시 ID(`temp_*`) 체계로 새 항목과 기존 항목을 구분
- 순서 변경(DnD)도 `sort_order` 필드의 diff로 처리
- Vitest로 diff 계산 로직의 정확성을 검증

### 6. 코드 품질 관리

| 영역            | 적용 내용                                                                                         |
| --------------- | ------------------------------------------------------------------------------------------------- |
| **테스트**      | Vitest 기반 단위 테스트 — 한글 초성 검색, Tree Diff 등 핵심 로직 검증                             |
| **에러 복원력** | `ErrorBoundary` 컴포넌트로 런타임 에러 시 화이트 스크린 방지 — "다시 시도" / "새로고침" 옵션 제공 |
| **접근성**      | 메시지 영역에 `role="log"`, 카테고리/질문 그룹에 `role="group"`, 입력/버튼에 `aria-label`         |
| **타입 안전성** | `any` 타입 제거, 전체 코드베이스 `strict` 모드                                                    |
| **보안**        | DOMPurify로 HTML 답변 살균(XSS 방어), Supabase RLS(Row Level Security) 적용                       |

### 7. Claude AI + RAG 통합

기존 3단계 규칙 기반 검색에서 매칭이 없을 때, **Supabase Edge Function(`chat-ai`)**을 통해 Anthropic Claude API를 호출합니다.

```
검색 3단계 모두 실패 + aiEnabled 활성화
  → askAi(companyId, userMessage)
    → supabasePublic.functions.invoke("chat-ai")
      → Edge Function에서 해당 회사 FAQ 데이터를 컨텍스트로 포함 (RAG)
      → Claude API 호출 → AI 응답 반환
```

**설계 결정**:

- **세션 격리**: `supabasePublic` 클라이언트(persistSession: false)를 사용하여 관리자 로그인 세션과 완전 분리
- **타임아웃**: 15초 AbortController로 무한 대기 방지
- **Rate Limit**: Edge Function 내 IP 기반 분당 20회 제한
- **Graceful Degradation**: AI 호출 실패 시 기존 "검색 결과 없음" 안내로 자연스럽게 폴백

### 8. 서브도메인 기반 멀티테넌트

하나의 코드베이스로 여러 회사에 독립적인 챗봇 서비스를 제공하기 위해, **서브도메인 기반 회사 전환** 구조를 설계했습니다.

```
사용자 접속
  → getSubdomainSlug() — hostname에서 서브도메인 추출
    ├── aifa.localhost → "aifa"
    ├── aifa.goofistalk.com → "aifa"
    ├── *.vercel.app → null (플랫폼 도메인 제외)
    └── example.co.kr → null (한국 2차 도메인 처리)

companySlug 결정 우선순위:
  서브도메인 > ?company= query param > VITE_COMPANY_SLUG 환경변수

회사 전환 시 → 5개 스토어 전체 리셋 (resetXxxStore)
```

<br/>

## 핵심 기능 상세

### 1. 4단계 스마트 검색

```
사용자 입력
  │
  ├─ 1단계: 질문/답변 전문 검색 (초성 검색 포함)
  │   └─ 매칭 시 → 관련 질문 목록 표시
  │
  ├─ 2단계: 서브카테고리 키워드 매칭
  │   └─ 매칭 시 → 해당 서브카테고리 표시
  │
  ├─ 3단계: 카테고리 키워드 매칭
  │   └─ 매칭 시 → 필터된 카테고리 메뉴 표시
  │
  ├─ 4단계: AI Fallback (aiEnabled 활성화 시)
  │   └─ Claude API + RAG → AI 응답 표시 (displayType: "aiAnswer")
  │
  └─ 모두 실패 → 전체 메뉴 + 안내 메시지
```

### 2. 관리자 대시보드

| 기능                       | 설명                                                                                     |
| -------------------------- | ---------------------------------------------------------------------------------------- |
| **FAQ 관리**               | 카테고리/서브카테고리/질문 CRUD + 드래그 앤 드롭 정렬                                    |
| **실시간 미리보기**        | FAQ 편집 시 우측에 챗봇 UI 실시간 반영                                                   |
| **분석 대시보드**          | 검색어 통계, 인기 질문, 일별 검색 추이 차트                                              |
| **AI 설정**                | AI 활성화/비활성화, 모델 선택, temperature/max_tokens 조정, 시스템 프롬프트 커스터마이징 |
| **회사 설정**              | 브랜드 색상, 로고, 인사말, 연락처 커스터마이징                                           |
| **회사 관리** (슈퍼관리자) | 전체 회사 목록, 서비스 신청 승인/거절, 회사 삭제                                         |
| **테마 전환**              | Mauve/Blue/Dark 3종 관리자 UI 테마                                                       |

### 3. DisplayType 기반 UI 렌더링

봇 메시지의 `displayType` 필드 하나로 메시지 하단에 렌더링할 UI 컴포넌트를 결정하는 **선언적 UI 패턴**을 사용합니다.

| displayType          | 렌더링 UI                     |
| -------------------- | ----------------------------- |
| `menu`               | 카테고리 버튼 (2x3 그리드)    |
| `subCategories`      | 서브카테고리 버튼             |
| `questions`          | 질문 버튼 목록                |
| `answer`             | 답변 + 네비게이션 버튼        |
| `searchResults`      | 매칭 질문 목록                |
| `subCategoryResults` | 매칭 서브카테고리 목록        |
| `aiAnswer`           | AI 응답 + AI 배지 + 상담 안내 |

<br/>

## 프로젝트 구조

```
src/
├── main.tsx                    # 진입점
├── App.tsx                     # 라우팅 + 서브도메인 멀티테넌트 (ChatbotWrapper)
│
├── pages/                      # 공개 페이지
│   ├── landing-page.tsx        # Goofi Talk 서비스 소개 랜딩
│   └── landing/                # 랜딩 페이지 섹션 컴포넌트
│       ├── landing-nav.tsx, hero-section.tsx, features-section.tsx
│       ├── how-it-works-section.tsx, demo-section.tsx
│       ├── cta-section.tsx, footer-section.tsx
│
├── components/
│   ├── error-boundary.tsx      # 런타임 에러 복원 컴포넌트
│   └── ui/                     # shadcn 기반 공통 UI (button, dialog, form 등)
│
├── hooks/                      # 공유 커스텀 훅
│   ├── use-faq-data.ts         # FAQ 데이터 Zustand 스토어 + on-demand 로드
│   └── use-company.ts          # 회사 설정 Zustand 스토어 + 동적 로드
│
├── types/                      # TypeScript 타입 정의
├── data/faq/                   # 정적 FAQ 데이터 (오프라인 폴백)
│
├── lib/                        # 공유 라이브러리
│   ├── supabase.ts             # Supabase 클라이언트 (관리자 인증용)
│   ├── supabase-public.ts      # Supabase 공개 클라이언트 (세션 격리)
│   ├── ai-client.ts            # AI 챗봇 클라이언트 (Edge Function 호출)
│   ├── faq-fetcher.ts          # FAQ on-demand fetch + 검색 API
│   ├── analytics.ts            # 검색/클릭 로깅 (fire-and-forget)
│   ├── sanitize.ts             # DOMPurify HTML 살균 (XSS 방어)
│   ├── slug-utils.ts           # URL-safe slug 생성 유틸
│   └── utils.ts                # cn() 유틸 (clsx + tailwind-merge)
│
├── config/                     # 공유 설정
│   ├── companies.ts            # CompanyConfig 타입 + PLATFORM_CONFIG
│   ├── contact.ts              # 카카오톡 URL, 전화번호
│   └── constants.ts            # COMPANY_SLUG 상수
│
├── chatbot/                    # 챗봇 전용
│   ├── pages/                  # chatbot-page.tsx
│   ├── components/
│   │   ├── chat/
│   │   │   ├── input/          # 텍스트 입력, 자동완성
│   │   │   ├── message/        # 메시지 버블, ai-answer-actions.tsx
│   │   │   ├── navigation/     # 카테고리·질문 버튼, 네비게이션
│   │   │   └── search/         # 검색 결과, 서브카테고리 결과
│   │   └── layout/             # 헤더 레이아웃
│   ├── hooks/                  # use-chat-handlers, use-chat-search, use-chat-message
│   ├── stores/                 # Zustand 3개 (message, navigation, search)
│   └── utils/                  # 초성 검색, 아이콘, 이미지 줌
│
└── admin/                      # 관리자 페이지
    ├── pages/
    │   ├── login-page.tsx, faq-page.tsx, analytics-page.tsx, settings-page.tsx
    │   ├── companies-page.tsx      # 슈퍼관리자 회사 관리
    │   ├── signup-page.tsx         # 서비스 신청 (고객사 셀프서비스)
    │   └── ai-settings-page.tsx    # AI 모델/프롬프트 설정
    ├── components/
    │   ├── layout/             # AdminLayout (인증 가드), Sidebar, 로고
    │   ├── faq/                # 트리 편집, DnD, 폼, 실시간 미리보기
    │   ├── analytics/          # 통계 카드, 검색 차트, 인기 질문
    │   └── settings/           # 회사 설정 폼, 미리보기
    ├── contexts/               # AdminContext (superadmin/admin/viewer 역할)
    ├── hooks/                  # 인증 훅 + 역할 판별
    └── lib/
        ├── admin-api.ts        # Supabase CRUD API + 회사/신청 관리
        ├── admin-theme.ts      # 관리자 테마 (Mauve/Blue/Dark)
        ├── seed-data.ts, image-upload.ts
        └── tree-diff.ts, tree-save.ts

supabase/functions/             # Supabase Edge Functions
├── chat-ai/index.ts            # RAG + Claude API (JWT 없음)
├── signup-with-company/index.ts # 서비스 신청 처리 (JWT 없음)
└── list-company-users/index.ts  # 사용자 목록 (JWT 필요)
```

<br/>

## 실행 방법

```bash
# 의존성 설치
npm install

# 개발 서버 실행
npm run dev          # http://localhost:5173

# 프로덕션 빌드
npm run build

# 테스트 실행
npm run test         # Vitest 단위 테스트
npm run test:watch   # 워치 모드

# 린트
npm run lint

# 운영 서버 배포
./deploy.sh
```

### 환경 변수

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_anon_key
VITE_COMPANY_SLUG=construction    # 빈 값이면 서브도메인/query param 우선
```

<br/>

## 라우팅

| 경로               | 페이지         | 설명                                          |
| ------------------ | -------------- | --------------------------------------------- |
| `/`                | ChatbotWrapper | companySlug 유무에 따라 챗봇 또는 랜딩 페이지 |
| `/apply`           | SignupPage     | 서비스 신청 (고객사 셀프서비스 가입)          |
| `/admin/login`     | LoginPage      | 관리자 로그인                                 |
| `/admin/faq`       | FaqPage        | FAQ 관리 (기본)                               |
| `/admin/analytics` | AnalyticsPage  | 분석 대시보드                                 |
| `/admin/settings`  | SettingsPage   | 회사 설정                                     |
| `/admin/companies` | CompaniesPage  | 슈퍼관리자 회사 관리                          |
| `/admin/ai`        | AiSettingsPage | AI 설정 관리                                  |
| `/admin/signup`    | → `/apply`     | 리디렉션 (하위 호환)                          |

> `MAINTENANCE_HOSTS`에 포함된 호스트는 점검 페이지를 표시합니다. (운영 도메인 확정 후 설정)
