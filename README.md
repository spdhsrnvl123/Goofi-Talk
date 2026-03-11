# 건설산업교육원 FAQ 챗봇

> 건설산업교육원의 자주 묻는 질문에 대화형 채팅 인터페이스로 자동 응답하는 SPA 웹 애플리케이션

<br/>

## 링크

| 구분 | URL |
|------|-----|
| **운영 서비스** | [chatbot.con.or.kr](http://chatbot.con.or.kr) |
| **최신 버전 (Vercel)** | [chatbot-taupe-two-95.vercel.app](https://chatbot-taupe-two-95.vercel.app) |
| **관리자 대시보드** | [chatbot-taupe-two-95.vercel.app/admin](https://chatbot-taupe-two-95.vercel.app/admin) |

<br/>

## 프로젝트 소개

건설산업교육원 고객센터에 반복적으로 들어오는 FAQ 문의를 줄이기 위해 **기획부터 배포까지 1인 풀스택으로 개발**한 대화형 FAQ 챗봇입니다.

사용자는 카테고리 탐색, 키워드 검색, 한글 초성 검색을 통해 원하는 답변을 빠르게 찾을 수 있으며, 비개발자도 FAQ를 직접 관리할 수 있는 **관리자 대시보드**를 함께 제공합니다.

### 해결한 문제

| 문제 | 해결 방법 |
|------|----------|
| 반복 FAQ 문의로 인한 고객센터 부하 | 대화형 챗봇으로 셀프 서비스 지원 |
| 비개발자의 콘텐츠 관리 어려움 | 드래그 앤 드롭 기반 FAQ CRUD 관리자 페이지 제공 |
| 단순 키워드 검색의 낮은 정확도 | 3단계 검색 + 한글 초성 검색으로 검색 품질 향상 |
| Supabase 장애 시 서비스 중단 위험 | 정적 데이터 자동 폴백 + On-demand 지연 로딩으로 무중단 서비스 보장 |

### 주요 특징

- **3단계 스마트 검색** — 질문/답변 전문 검색 → 서브카테고리 키워드 매칭 → 카테고리 키워드 매칭 순으로 최적의 결과 제공
- **한글 초성 검색** — `ㅅㄱ` 입력만으로 `수강신청` 관련 질문 검색 가능
- **관리자 대시보드** — FAQ CRUD, 드래그 앤 드롭 정렬, 검색/클릭 분석, 실시간 챗봇 미리보기
- **오프라인 폴백** — Supabase 연결 실패 시 정적 FAQ 데이터로 자동 전환
- **멀티 브랜드 지원** — 회사별 테마 색상, 로고, 인사말 커스터마이징
- **테스트 커버리지** — Vitest 기반 26개 단위 테스트로 핵심 로직(초성 검색, Tree Diff) 검증
- **접근성(A11y)** — ARIA role/label 적용, 시맨틱 마크업으로 스크린 리더 지원
- **SEO 최적화** — Open Graph 메타 태그, 시맨틱 HTML, `lang="ko"` 설정

<br/>

## 스크린샷

> 챗봇 메인 화면

<!-- 스크린샷 추가 예정: 챗봇 메인 UI -->

> 관리자 대시보드 — FAQ 관리

<!-- 스크린샷 추가 예정: FAQ CRUD 관리 화면 -->

> 관리자 대시보드 — 분석

<!-- 스크린샷 추가 예정: 검색 통계 차트 -->

<br/>

## 기술 스택

| 구분 | 기술 |
|------|------|
| **프론트엔드** | React 19, TypeScript, Tailwind CSS v4 |
| **상태 관리** | Zustand 5 (3개 독립 스토어) |
| **백엔드 / DB** | Supabase (PostgreSQL + Auth + Storage) |
| **라우팅** | React Router v7 (Lazy Loading) |
| **리치 텍스트** | TipTap (StarterKit + Underline + Color + Link + Image) |
| **DnD** | @dnd-kit/core, @dnd-kit/sortable |
| **차트** | Recharts |
| **HTML 보안** | DOMPurify (XSS 방어) |
| **테스트** | Vitest (26개 단위 테스트) |
| **빌드** | Vite |
| **배포** | Vercel / SCP (운영 서버 직접 배포) |

<br/>

## 아키텍처

```
┌──────────────────────────────────────────────────────────┐
│                     사용자 (챗봇)                          │
│            카테고리 탐색 / 키워드 검색 / 초성 검색            │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────────────┐
│                   React SPA (Vite)                        │
│                                                          │
│  ┌─────────────┐  ┌──────────────┐  ┌────────────────┐  │
│  │ messageStore│  │navigationStore│  │  searchStore   │  │
│  │  (메시지)   │  │  (탐색 위치)  │  │  (검색 결과)   │  │
│  └──────┬──────┘  └──────┬───────┘  └───────┬────────┘  │
│         └────────────────┼──────────────────┘            │
│                          ▼                               │
│              useChatHandlers (이벤트 조율)                 │
│              useChatSearch  (3단계 검색)                   │
│              useChatMessage (타이핑 애니메이션)             │
│                                                          │
│  ┌───────────────────────────────────────────────────┐   │
│  │              관리자 페이지 (/admin)                  │   │
│  │  FAQ CRUD · DnD 정렬 · 분석 대시보드 · 회사 설정    │   │
│  └───────────────────────────────────────────────────┘   │
└───────────────────────┬──────────────────────────────────┘
                        │
                        ▼
┌──────────────────────────────────────────────────────────┐
│                     Supabase                             │
│  PostgreSQL (FAQ 데이터, 검색 로그, 클릭 분석)             │
│  Auth (관리자 인증)                                       │
│  Storage (이미지 업로드)                                   │
│                                                          │
│  연결 실패 시 → src/data/faq/ 정적 데이터 자동 폴백        │
└──────────────────────────────────────────────────────────┘
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
addBotMessage({ text: "카테고리를 선택하세요", displayType: "menu" })
addBotMessage({ text: "검색 결과입니다", displayType: "searchResults" })
```

**왜 이 패턴을 선택했나?**
- 채팅 UI 특성상 메시지마다 다른 UI를 렌더링해야 하는데, `if/switch` 분기가 늘어나면 유지보수가 어려워짐
- `displayType`을 데이터로 선언하면, 새 UI 유형 추가 시 컴포넌트만 매핑하면 됨
- 이전 메시지의 UI를 숨기는 `clearAllDisplayTypes()` 패턴으로, 항상 최신 메시지만 인터랙티브하게 유지

### 3. Zustand 3-Store 분리 설계

**왜 3개로 분리했나?**

| 고려한 방안 | 문제점 |
|------------|--------|
| 단일 전역 스토어 | 메시지 추가 시 검색/네비게이션 컴포넌트까지 리렌더링 |
| Context API | 빈번한 상태 변경(타이핑 애니메이션 등)에서 성능 병목 |
| **역할별 3-Store** | 각 스토어 변경이 해당 구독자만 리렌더링 (채택) |

```
messageStore     → 채팅 메시지, 타이핑 상태 (변경 빈도: 높음)
navigationStore  → 현재 카테고리/서브카테고리 (변경 빈도: 중간)
searchStore      → 검색 결과, 필터된 카테고리 (변경 빈도: 낮음)
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
- Vitest로 diff 계산 로직의 정확성을 검증 (10개 테스트 케이스)

### 6. 코드 품질 관리

단순히 기능을 구현하는 것을 넘어, **프로덕션 수준의 품질**을 확보하기 위해 다각도로 개선했습니다.

| 영역 | 적용 내용 |
|------|----------|
| **테스트** | Vitest 기반 26개 단위 테스트 — 한글 초성 검색(`isChosungMatch`, `extractChosung`, `isQuestionMatched`) 13개 + Tree Diff(`computeTreeDiff`, `isTempId`, `isDiffEmpty`) 13개 |
| **에러 복원력** | `ErrorBoundary` 컴포넌트로 런타임 에러 시 화이트 스크린 방지 — "다시 시도" / "새로고침" 옵션 제공. 개발 환경에서는 에러 메시지 표시 |
| **SEO** | Open Graph 메타 태그(`og:title`, `og:description`, `og:type`), `meta description`, `theme-color`, `lang="ko"` 설정 |
| **접근성** | 메시지 영역에 `role="log"`, 카테고리/질문 그룹에 `role="group"`, 검색 결과에 `role="region"`, 입력/버튼에 `aria-label` |
| **타입 안전성** | `any` 타입 제거 → `MenuItem` 등 명시적 타입으로 교체, 전체 코드베이스 `strict` 모드 |
| **보안** | DOMPurify로 HTML 답변 살균(XSS 방어), Supabase RLS(Row Level Security) 적용 |

<br/>

## 핵심 기능 상세

### 1. 3단계 스마트 검색

```
사용자 입력
  │
  ├─ 1단계: 질문/답변 전문 검색 (초성 검색 포함)
  │   └─ 매칭 시 → 관련 질문 목록 표시 ✓
  │
  ├─ 2단계: 서브카테고리 키워드 매칭
  │   └─ 매칭 시 → 해당 서브카테고리 표시 ✓
  │
  ├─ 3단계: 카테고리 키워드 매칭
  │   └─ 매칭 시 → 필터된 카테고리 메뉴 표시 ✓
  │
  └─ 매칭 없음 → 전체 메뉴 + 안내 메시지
```

### 2. 관리자 대시보드

| 기능 | 설명 |
|------|------|
| **FAQ 관리** | 카테고리/서브카테고리/질문 CRUD + 드래그 앤 드롭 정렬 |
| **실시간 미리보기** | FAQ 편집 시 우측에 챗봇 UI 실시간 반영 |
| **분석 대시보드** | 검색어 통계, 인기 질문 TOP 10, 일별 검색 추이 차트 |
| **회사 설정** | 브랜드 색상, 로고, 인사말, 연락처 커스터마이징 |
| **이미지 업로드** | 답변에 이미지 첨부 (Supabase Storage) |
| **시드 기능** | 정적 데이터를 Supabase에 일괄 업로드 |

### 3. DisplayType 기반 UI 렌더링

봇 메시지의 `displayType` 필드 하나로 메시지 하단에 렌더링할 UI 컴포넌트를 결정하는 **선언적 UI 패턴**을 사용합니다.

| displayType | 렌더링 UI |
|-------------|----------|
| `menu` | 카테고리 버튼 (2×3 그리드) |
| `subCategories` | 서브카테고리 버튼 |
| `questions` | 질문 버튼 목록 |
| `answer` | 답변 + 네비게이션 버튼 |
| `searchResults` | 매칭 질문 목록 |
| `subCategoryResults` | 매칭 서브카테고리 목록 |

<br/>

## 프로젝트 구조

```
src/
├── pages/                  # 페이지 컴포넌트
├── components/
│   ├── chat/               # 챗봇 UI
│   │   ├── input/          # 텍스트 입력, 자동완성
│   │   ├── message/        # 메시지 버블, 타이핑 애니메이션, 이미지 모달
│   │   ├── navigation/     # 카테고리·서브카테고리·질문 버튼, 네비게이션
│   │   └── search/         # 검색 결과, 서브카테고리 결과
│   ├── layout/             # 헤더 레이아웃
│   ├── error-boundary.tsx  # 런타임 에러 복원 컴포넌트
│   └── ui/                 # shadcn 기반 공통 UI (button, dialog, form 등)
├── hooks/                  # 커스텀 훅 (검색, 메시지, 네비게이션)
├── stores/                 # Zustand 스토어 (3개)
├── types/                  # TypeScript 타입 정의
├── data/faq/               # 정적 FAQ 데이터 (오프라인 폴백)
├── lib/                    # Supabase 클라이언트, 분석 로깅, HTML 살균, slug 유틸
├── utils/                  # 초성 검색, 아이콘 유틸
├── config/                 # 브랜드 설정, 연락처
└── admin/                  # 관리자 페이지
    ├── pages/              # 로그인, FAQ, 분석, 설정
    ├── components/
    │   ├── layout/         # AdminLayout, Sidebar, 로고
    │   ├── faq/            # 트리 편집, DnD, 폼, 실시간 미리보기
    │   ├── analytics/      # 통계 카드, 검색 차트, 인기 질문
    │   └── settings/       # 회사 설정 폼, 미리보기
    ├── contexts/           # 관리자 역할 컨텍스트 (admin/viewer/guest)
    ├── hooks/              # 인증 훅 + 역할 판별
    └── lib/                # Admin API, 시드, 이미지 업로드, Tree Diff/Save
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
npm run test         # Vitest 단위 테스트 (26개)
npm run test:watch   # 워치 모드

# 린트
npm run lint

# 운영 서버 배포
./deploy.sh
```

### 환경 변수

```env
VITE_SUPABASE_URL=your_supabase_url
VITE_SUPABASE_ANON_KEY=your_supabase_anon_key
```

<br/>

## 라우팅

| 경로 | 페이지 | 설명 |
|------|--------|------|
| `/` | ChatbotPage | 메인 챗봇 인터페이스 |
| `/admin/login` | LoginPage | 관리자 로그인 |
| `/admin/faq` | FaqPage | FAQ 관리 (기본) |
| `/admin/analytics` | AnalyticsPage | 분석 대시보드 |
| `/admin/settings` | SettingsPage | 회사 설정 |
