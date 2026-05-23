# Persona System Project — Claude Code 인계 문서 v3.2

> v3.1 → v3.2 변경:
> - 작업 위치 변경: `~/Desktop/persona-system/` → **`~/work/persona-system/`**
> - 이유: 데스크탑 정리, 향후 다른 프로젝트와 일관된 위치
> - Phase 0 Step 재구조화: clone하면 디렉토리·7개 파일 자동 복원 → Step 2~3 불필요

---

## 0. 버전 히스토리

| 버전 | 변경 |
|---|---|
| v1 | 초기 인계 문서 |
| v2 | 5개 결정 반영 |
| v3 | 자체완결성 원칙 도입 |
| v3.1 | Phase 0 실행 디테일 보강 |
| v3.2 | **작업 위치 `~/work/`, Phase 0 재구조화** (이 문서) |

---

## 1. 프로젝트 정의

### 한 줄
**Claude Code 환경 위에 자체완결적인 AI 페르소나 시스템을 구축한다.**

### 자체완결성 (Self-contained) 원칙
- 외부 user skills 의존 안 함
- 필요한 도구는 프로젝트 안에 복사 보유
- 외부 변경이 이 프로젝트에 영향 못 줌

### 1차 범위
- 페르소나 정의 파일 표준 포맷
- 산출물 표준 파일 표준 포맷
- 프로젝트 내부 스킬 보유
- 디렉토리 구조 / 명명 규칙
- 자연어 호출 메커니즘
- 운영 매뉴얼 (README + OPERATIONS)
- 첫 페르소나 1명 + 첫 산출물 표준 1개 배치

### 비범위
- 멀티 에이전트 협업
- 메모리·학습 시스템
- LLM 자동 페르소나 생성
- 평가·품질 측정 자동화
- 외부 스킬과의 자동 동기화

---

## 2. 핵심 결정 사항

### 2.1 저장·작업 위치 (v3.2 변경)
- **GitHub 레포 (메인)**: `yongjooseok/persona-system` (Public)
- **로컬 작업 위치**: `~/work/persona-system/` (모든 Mac 공통)
- **3대 Mac 연동 방식**: 각 Mac에서 `git clone` → `git pull`/`push`로 동기화
- iCloud Drive 사용 안 함 (`.git` 충돌 위험)

### 2.2 메타포: 전문가 (Expert)
- AI = 외부 전문 컨설턴트, 의뢰인 = 로그
- 최종 결정·창작 권위는 로그

### 2.3 운영 방식: MD 정의 파일 (1차)

### 2.4 호출 메커니즘: 자연어
```
"콘텐츠 전략가에게 의뢰: Quiet Notes 첫 글 도입부.
draft-with-rationale 포맷으로."
```

### 2.5 외부 스킬과의 관계 (자체완결성)

```
[프로젝트 내부]                          [외부 user skills - 미사용]
~/work/persona-system/skills/            ~/.claude/skills/ 등
├── content-os/        ← 1회 복사 ←     ├── content-os/
├── idea-brainstorm/                     ├── idea-brainstorm/
├── blog-writer/                         ├── blog-writer/
└── question-design/                     └── question-design/
   (이후 양쪽 독립 진화)
```

### 2.6 페르소나 구성 6요소
Role / Goal / Backstory / Tools / **Lens** / **Algorithm**
(Lens·Algorithm 생략 금지)

### 2.7 산출물 4원칙
결정 가능성 / 추적 가능성 / 수정 가능성 / 대안 가시성

### 2.8 이미 만들어진 자산
- 콘텐츠 전략가 본질형 v0.1 (이전 명칭: 見) — 박웅현 풍 차용
- draft-with-rationale v0.1 — 산출물 표준 1호

(둘 다 정의는 `docs/process/4_…`, `docs/process/5_…`에 있음. Phase 0에서 추출·배치)

---

## 3. 디렉토리 구조 (확정)

```
~/work/persona-system/                       # GitHub: yongjooseok/persona-system
├── README.md
├── OPERATIONS.md
│
├── employees/
│   └── content-strategist-essence.md
│
├── output-standards/
│   └── draft-with-rationale.md
│
├── skills/
│   ├── content-os/
│   │   └── SKILL.md
│   ├── idea-brainstorm/
│   │   └── SKILL.md
│   ├── blog-writer/
│   │   └── SKILL.md
│   └── question-design/
│       └── SKILL.md
│
└── docs/
    └── process/                             # 원본 7개 (사고 흔적, 이미 push됨)
        ├── 0_1_persona-operation-comparison.md
        ├── 0_2_multi-persona-collaboration-patterns.md
        ├── 1_dimensions-to-explore.md
        ├── 2_metaphor-deep-dive.md
        ├── 3_expert-content-strategist-persona-depth.md
        ├── 4_content-strategist-v0.1.md
        └── 5_draft-with-rationale-v0.1.md
```

---

## 4. 호출 메커니즘 상세

### 형식
`[페르소나 식별] + [의뢰 내용] + [산출물 표준 지정]`

### 식별 키워드 (OPERATIONS.md에 명시)

| 자연어 | 매핑 |
|---|---|
| "콘텐츠 전략가" / "본질형 전략가" / "본질형" | `employees/content-strategist-essence.md` |
| "draft-with-rationale" / "초안+근거" | `output-standards/draft-with-rationale.md` |
| `@skills/content-os` (정의 파일 내부 표기) | `./skills/content-os/SKILL.md` |
| `@skills/idea-brainstorm` | `./skills/idea-brainstorm/SKILL.md` |
| `@skills/blog-writer` | `./skills/blog-writer/SKILL.md` |
| `@skills/question-design` | `./skills/question-design/SKILL.md` |

---

## 5. Claude Code의 첫 작업 (Phase 0) — v3.2 재구조화

**현재 상태 (Step 0 — 이미 완료):**
- `~/work/persona-system/`에 GitHub 레포 클론 완료
- 디렉토리 구조 (employees/, output-standards/, skills/, docs/process/) 존재
- `docs/process/`에 7개 원본 파일 존재
- `employees/`, `output-standards/`, `skills/` 빈 상태

### Step 1: 외부 user skills 4개 복사

**위치 자가 탐색:**
```bash
find ~/.claude ~/Library/Application\ Support/Claude -type d \
  \( -name "content-os" -o -name "idea-brainstorm" \
  -o -name "blog-writer" -o -name "question-design" \) 2>/dev/null
```

**탐색 결과별 행동:**
- 4개 모두 찾으면 → 각 폴더를 `./skills/`로 `cp -r` 복사
- 일부만 찾으면 → 못 찾은 스킬에 대해 로그에게 위치 질문
- 모두 못 찾으면 → 로그에게 외부 스킬 저장 위치 전체 질문

**복사 명령 예시:**
```bash
cd ~/work/persona-system
cp -r <발견된 경로>/content-os ./skills/
cp -r <발견된 경로>/idea-brainstorm ./skills/
cp -r <발견된 경로>/blog-writer ./skills/
cp -r <발견된 경로>/question-design ./skills/
```

원본은 그대로 둠.

### Step 2: 페르소나 정의 배치 + 이름 변경

`docs/process/4_content-strategist-v0.1.md`의 §2 페르소나 정의 부분을 추출해서 `employees/content-strategist-essence.md`로 생성. 다음 변경 적용:

- frontmatter:
  - `codename: 見 (gyeon)` → `codename: essence`
- 페르소나 호칭:
  - `見` → `콘텐츠 전략가 — 본질형`
- Tools 섹션:
  - `@skills/team-builder` **제거** (양산 메커니즘이지 페르소나 도구 아님)
  - 나머지 4개(`@skills/content-os` 등)는 표기 유지
- Voice 섹션의 자기 호칭 부분 점검·수정

### Step 3: 산출물 표준 배치

`docs/process/5_draft-with-rationale-v0.1.md`의 §3 템플릿 부분만 추출해서 `output-standards/draft-with-rationale.md`로 생성.
메타·근거·샘플(§1, §2, §4 등)은 `docs/process/`에 남김.

### Step 4: 운영 문서 작성

**README.md** 포함 내용:
- 프로젝트 한 줄 정의
- 핵심 결정 사항 요약 (메타포, 운영 방식, 자체완결성)
- 디렉토리 안내
- 사용 예시 1개
- 다기기 동기화 방법 (git pull/push)

**OPERATIONS.md** 포함 내용:
- 호출 메커니즘 (자연어 형식)
- §4의 식별 키워드 매핑 표
- 첫 의뢰 예시
- 자체완결성 원칙 강조 (외부 경로 참조 금지)
- 신규 페르소나 추가 절차 (간략)

### Step 5: 커밋 → push

```bash
cd ~/work/persona-system
git add .
git commit -m "Phase 0: Add internal skills + first persona + standards + operations"
git push origin main
```

의미 단위로 분할 커밋 권장:
- Commit 1: Copy internal skills from user skills
- Commit 2: Add first persona (content-strategist-essence)
- Commit 3: Add first output standard (draft-with-rationale)
- Commit 4: Add README + OPERATIONS

---

## 6. 의도적 미결정

| 항목 | 미결정 이유 | 결정 시점 |
|---|---|---|
| 산출물 평가 기준 | 1건 가동 후 자연 도출 | Phase 1 후 |
| 메모리·시간성 | 페르소나 1명 검증 후 | Phase 2 |
| 협업 패턴 | 2명 이상 시 의미 | Phase 2 후 |
| Sub-agent 마이그레이션 | MD 운영 검증 후 | Phase 3 |
| team-builder 도입 | 페르소나 양산 필요 시점 | Phase 3 |

---

## 7. 핵심 원칙 (Claude Code가 일관되게 지킬 것)

### 자체완결성
- 외부 의존성 추가 금지
- 새 스킬·자산이 필요하면 프로젝트 안으로 복사
- 외부 참조 표기(`~/.claude/...`, 절대 경로) 금지

### 인식론적 정직성
- 추정·가정은 명시
- 실존 인물 차용 시 차용 범위·차용 안 한 것 명시

### 메타포 정합성
- 모든 페르소나 = "전문가" 메타포
- 권위·결정·창작권 = 의뢰인(로그)
- Boundaries 섹션에 "결정하지 않는 것" 명시

### 페르소나 깊이 의무
- 6요소 모두 채움 (특히 Lens·Algorithm)
- 자기 검토 체크리스트 포함

### 산출물 4원칙
- 결정·근거·수정·대안 모두 포함

### YAGNI
- 지금 필요한 것만
- 빈 폴더·빈 가이드 안 만듦
- 2번째 사례 생길 때 추상화

---

## 8. 참고 자료

`docs/process/`에 보관. 기본 컨텍스트엔 안 들어감.

| 파일 | 참조 시점 |
|---|---|
| 0_1_persona-operation-comparison | Sub-agent 마이그레이션 검토 시 |
| 0_2_multi-persona-collaboration-patterns | 협업 패턴 도입 시 |
| 1_dimensions-to-explore | 미결정 차원 결정 시 |
| 2_metaphor-deep-dive | 새 메타포 검토 시 |
| 3_expert-content-strategist-persona-depth | 신규 페르소나 6요소 설계 시 |
| 4_content-strategist-v0.1 | 첫 페르소나 v0.1.1 패치 시 |
| 5_draft-with-rationale-v0.1 | 산출물 표준 추가 시 |

---

## 9. Claude Code에게 던질 첫 지시 (그대로 복붙 가능)

```
작업 위치: ~/work/persona-system/

이 문서(persona-system-handoff-v3.2.md)에 따라 Phase 0 Step 1~5를 진행한다.

현재 상태:
- GitHub clone 완료
- docs/process/에 7개 원본 파일 존재
- employees/, output-standards/, skills/ 빈 상태

각 Step 완료 후 결과 보고. 의문점은 진행 전 질문.

특히 주의:
- Step 1: 외부 스킬 4개를 find 명령으로 자가 탐색.
         못 찾으면 진행 전에 로그에게 질문.
- Step 2: 페르소나 정의에서 team-builder 제거, 이름 변경 반영
- Step 4: README, OPERATIONS에 자체완결성 원칙 명시
         (외부 경로 참조 금지, 다기기 동기화는 git pull/push)
- Step 5: 의미 단위로 분할 커밋 후 push

자체완결성 원칙 위반 가능성 발견 시 작업 멈추고 보고.
```

---

## 10. 다기기 동기화 가이드 (v3.2 신규)

### 처음 설정 (모든 Mac에서 1회)
```bash
mkdir -p ~/work && cd ~/work
git clone https://github.com/yongjooseok/persona-system.git
```

### 매번 작업 시작 전
```bash
cd ~/work/persona-system
git pull
```

### 매번 작업 종료 후
```bash
git add .
git commit -m "변경 내용 요약"
git push
```

### 충돌 발생 시
- 보통 `git pull` 시점에 감지
- Claude Code에게 충돌 해결 위임 가능
- 충돌 빈도 높으면 1대 Mac에서만 작업하는 패턴으로 운영

---

## 11. 불확실 지점

- 외부 user skills의 정확한 로컬 위치는 환경 의존. Step 1의 find 명령으로 자가 탐색.
- 자연어 페르소나 식별 정확도 미검증. 모호하면 OPERATIONS.md에 호출 패턴 더 엄격하게 명시.
- "본질형" 명칭은 추천. 다른 안 가능.
- 다기기 동시 작업 시 충돌 빈도는 실측 필요. 보통은 드물지만 같은 파일 동시 편집 시 발생.
