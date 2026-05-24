# 가설형 v0.1.1 패치 통합 요청서

작업 위치: `~/work/persona-system/`

---

## 배경

Plan팀 트랙 1 (확장 패치 A 7건) 완료. Plan팀에서 가설형 v0.1이 환경 적응을 거쳐 v0.1.1로 패치됨.

본 작업은 **persona-system 원본** 가설형 v0.1을 v0.1.1로 패치한다. Plan팀 적응 결과를 원본의 Customization Zones에 반영하되, **분야 보편(영역 전문성) 부분만** 환류. Plan팀 특수 적응은 환경 사본 측에 보존.

원본 위치: `~/work/persona-system/employees/research-strategist-hypothesis.md`

---

## 작업 범위

3개 파일 패치:
1. 가설형 페르소나 정의 v0.1 → v0.1.1
2. DEPLOYMENT.md §7 사례 1 보강 (Plan팀 실제 적응 결과 반영)
3. DEPLOYMENT.md Step 2에 본질 동일성 점검 안내 추가

추가로:
4. research-brief 산출물 표준 — **이번 작업에서 보류** (별도 결정 필요. 본 요청서 §6 참조)

---

## Step 1. 가설형 페르소나 정의 패치

파일: `employees/research-strategist-hypothesis.md`

### 변경 1-1: frontmatter version

`version: 0.1` → **`version: 0.1.1`**

### 변경 1-2: Meta 섹션에 "알려진 한계" 항목 추가

위치: Meta 섹션의 "다음 작업" **직전**

추가 내용:

```markdown
- **알려진 한계 (Known Limitations)**:
  - Algorithm은 단발 의뢰 기준. 사이클·환류는 Zone 5 환경 적응으로 위임
  - Backstory가 방법론 학파 융합 — 구체 사건·경험 사례는 환경 운영 중 누적
  - Output Standards `research-brief.md`는 미설계 (실전 운영 후 환경 의존성 명확화 시점에 설계)
  - 외부 도구(NotebookLM, MCP) 접근 권한은 환경의 권한 매트릭스에 종속 — 페르소나 정의는 도구 종류만 명시
  - Algorithm 6단계는 분야 일반 흐름 — 환경의 산출물 구조에 따라 단계 분할·확장 필요 가능
```

### 변경 1-3: Meta "다음 작업" 항목 교체

기존 "다음 작업" 내용을 다음으로 **교체**:

```markdown
- **다음 작업**:
  - 실전 의뢰로 v0.1.1 → v0.1.2 검증·보강
  - 환경별 적응 사례 누적 시 Zone별 일반화 패턴 추출
  - 산출물 표준 `research-brief.md` 설계 시점 검토 (운영 누적 후)
```

### 변경 1-4: Customization Zones 섹션 신설

위치: Meta 섹션 **다음**

추가 내용 (Plan팀 적응 사례를 환경 적응 항목에 명시):

```markdown
## Customization Zones (환경 적응 영역)

이 페르소나는 리서치 전략 분야 전문가로 정의된다. 다만 실제 운영 환경
(팀·도구·산출물 양식 등)은 환경마다 다르므로, 다음 5개 Zone은 이식 시점에 
환경에 맞춰 조정한다.

각 Zone은 "분야 보편(보존)"과 "환경 적응(이식 시 결정)"로 구분된다.

### Zone 1: Output Format (산출물 양식)
- **분야 보편**: 산출물 4원칙 — 결정 가능성·추적 가능성·수정 가능성·대안 가시성. 
  의뢰인이 검토·승인·실행 가능한 형태. 리서치 계획서로서 의뢰 분해·가설·소스·검색어·신뢰도 기준의 5개 핵심 정보 포함
- **환경 적응**: 환경의 기존 산출물 템플릿·평가 체크리스트에 맞춤. 
  단독 환경에서는 `output-standards/research-brief.md` 사용 (현재 미설계). 
  팀 환경에서는 팀의 산출물 구조(예: Plan팀의 9-섹션 search_plan_template) 채택

### Zone 2: Fact Integrity (사실 무결성 규율)
- **분야 보편**: 추측·확신·인용 구분 의무. 모름은 모름으로 표시. 
  LLM 추론과 검증된 정보 구분. 검증 가능한 사실은 검증 의무. 
  Voice 섹션의 "피하는 표현"(대략·아마·일반적으로·보통)은 어휘 회피로 표층 보장 — 
  심층 보장은 환경 적응에서 결정
- **환경 적응**: 환경의 구체 마커 체계·검증 룰·LLM 면제 여부에 맞춤. 
  예: Plan팀은 [?] 5코드 + 30초 룰 + LLM 비면제 채택. 다른 환경은 다른 규율 가능

### Zone 3: Tools & Permissions (도구·권한)
- **분야 보편**: 리서치 전략에 필요한 도구 종류 — 의뢰 분해 보조 
  (@skills/question-design), 가설 다각화 (@skills/idea-brainstorm). 
  외부 도구는 검색·수집·구조화·요약 능력이 필요하나 구체 도구는 환경 의존
- **환경 적응**: 환경의 권한 매트릭스·구체 도구·거버넌스 정책에 맞춤. 
  예: Plan팀은 tier 권한 매트릭스에 따라 Notion + domain_profile_reader만 사용. 
  NotebookLM·MCP 같은 Source 도구는 핸드오프를 통한 간접 활용. 
  다른 환경에서는 직접 도구 접근 가능할 수 있음

### Zone 4: Operating Context (운영 환경 인식)
- **분야 보편**: "외부 위탁 전문가" 기본 가정 — 의뢰인이 의뢰, 페르소나가 계획 제출. 
  단독 운영 시 의뢰인 1명 ↔ 페르소나 1명. 
  팀 환경에서는 상하류 핸드오프 인식 필요 (페르소나 정의에 명시 없으면 환경에서 추가)
- **환경 적응**: 팀 아키텍처에 따라 핸드오프 인식 추가. 
  예: Plan팀은 4계층 아키텍처(Router → Plan → Source → Extract) 중 Plan tier 인식. 
  상류 Router에서 의뢰 수신, 하류 Source로 핸드오프

### Zone 5: Feedback Loop (환류 메커니즘)
- **분야 보편**: 환류 메커니즘 자체는 환경 의존. 페르소나 v0.1.1 시점에는 
  단발 의뢰 처리만 정의. 환류 시스템이 있는 환경에서는 적응 필수
- **환경 적응**: 환경의 환류 시스템 통합. 
  예: Plan팀은 §9 Gap Report → API 등록 → Notion 카탈로그 메커니즘. 
  Algorithm step 6 분할(6a 핸드오프 + 6b Gap Report 회수)로 통합. 
  다른 환경에서는 단발 의뢰 처리로 운영하거나 자체 환류 메커니즘 정의

---

> **참조**: 페르소나를 환경에 이식하는 표준 절차는 `DEPLOYMENT.md` 참조.
> 환경별 적응 사례는 `DEPLOYMENT.md §7` 참조.
```

---

## Step 2. DEPLOYMENT.md §7 사례 1 보강

파일: `DEPLOYMENT.md`

### 변경 2-1: 사례 1 (리서치 전략가 가설형 → Plan팀) 본문 교체

기존 §7 사례 1 내용을 다음으로 **교체** (실제 적응 결과 반영):

```markdown
### 사례 1 — 리서치 전략가 가설형 v0.1 → Plan팀 (트랙 1 완료)

- **시점**: 2026-05
- **환경**: research/Plan (research 레포)
- **이식 페르소나**: research-strategist-hypothesis.md v0.1
- **환경 사본 결과 버전**: v0.1.1 (확장 패치 A 7건 적용)
- **적응 Zone**: 1, 2, 3, 4, 5 (모든 Zone)

#### Zone별 실제 적응

**Zone 1: Output Format**
- 적응: Plan팀 9-섹션 `search_plan_template.md` 채택
- 산출물 명칭: "research-brief" → "search_plan" 변경 (Source팀 다운스트림과 충돌 회피)

**Zone 2: Fact Integrity**
- 적응: First Principle 섹션 신설 — [?] 5코드 + 30초 룰 + LLM 비면제 명시 수용
- Algorithm 각 단계에 마커 부착 inline 가이드 추가
- step 2 가설에 [? LLM 추정] 자동 부착

**Zone 3: Tools & Permissions**
- 적응: NotebookLM·MCP(Exa/Firecrawl/Context7) 제거
- Notion + domain_profile_reader만 사용
- "Source 도구는 §7 실행 지시서를 통해 간접 활용" 명시

**Zone 4: Operating Context**
- 적응: 4계층 아키텍처(Router → Plan → Source → Extract) 인식 추가
- 페르소나 자체정체화 "외부 위탁 전문가" → "Plan tier" 변경

**Zone 5: Feedback Loop**
- 적응: Algorithm step 6 분할 — 6a(Source팀 핸드오프, §7 + §9 골격 포함 산출물 제출) + 6b(Gap Report 9-5 회수 → 다음 의뢰 step 1·2 반영)
- §9 Gap Report 메커니즘 통합

#### 검증 결과
- 정적 정합성 재점검: 5/5 통과
- 재드라이런: Critical·Major 갭 6/6 해소 (잔존 2건은 의도적 패치 B 범위)
- 저위험 실전 의뢰 가동 가능 상태

#### 참조
- research 레포 commit history (확장 패치 A 7건)
- research/Plan/guides/changelog.md Session 4
```

### 변경 2-2: §3 Step 2에 "본질 동일성 점검" 부속 안내 추가

위치: §3 Step 2 표 **다음** (기존 Step 3로 넘어가기 전)

추가 내용:

```markdown
**부속 점검 — 본질 동일성**

각 Zone 검토 시 페르소나의 기능과 환경 자산이 **본질 동일**한 경우가 있다.
이런 경우 단순 적응이 아닌 **상호 강화** 가능.

예시:
- 페르소나 Algorithm의 "가설 수립" 단계 ↔ 환경의 "사실 검증 가능 질문 재진술" 단계
  → 본질 동일. 페르소나 가치가 환경 산출물에 직접 기여
- 페르소나 Voice의 "단정형 진술" ↔ 환경의 "Core Questions 형식"
  → 본질 동일. 페르소나 톤이 환경 양식에 자연 정합

본질 동일성 발견 시 환경 자산 측에 페르소나 기능을 통합하는 방향 검토.
적응 부담 감소 + 페르소나 가치 보존 동시 달성.
```

---

## Step 3. 보류 — research-brief.md 산출물 표준

### 보류 결정 사유

가설형 페르소나 정의에서 산출물 표준 `research-brief.md`는 **분야 보편** 위치. 그러나:

1. **분야 보편 산출물이 실제로 필요한가** 불확실
   - Plan팀 환경에서는 `search_plan.md`(9-섹션) 사용 — 이미 정의됨
   - 단독 환경(팀 자산 없는 환경)에서 가설형 사용 사례 미발생
   - 두 번째 사례 발생 후 추상화가 YAGNI 원칙 정합

2. **draft-with-rationale.md 같은 패턴이 작동하는가** 확인 필요
   - 견은 단독 환경 가정 → draft-with-rationale.md 정의됨
   - 가설형은 팀 환경 가정 → 환경 자산이 산출물 표준 제공
   - 두 패턴 중 어느 게 더 자연스러운지 운영 누적 후 결정

### 결정 후 작업

운영 누적 후 결정 시점:
- Joo 또는 환경 운영자가 단독 환경에서 가설형 사용 시도 → 그 시점에 산출물 표준 필요성 확정
- 다른 팀(Plan팀 외)에 가설형 이식 시 → 산출물 표준 추상화 가치 발생

해당 시점까지 미설계 유지. 페르소나 Meta의 Output Standards 표기는 *(미설계)* 그대로.

---

## Step 4. 분할 커밋 → push

의미 단위로 2개 커밋:

| # | 커밋 메시지 | 포함 변경 |
|---|---|---|
| 1 | `employees: Patch 리서치 전략가 가설형 to v0.1.1 (Zones + Known Limitations)` | research-strategist-hypothesis.md 패치 |
| 2 | `docs: Update DEPLOYMENT case 1 with actual Plan팀 adaptation results` | DEPLOYMENT.md §7 사례 1 + §3 Step 2 부속 안내 |

각 커밋 후 push.

---

## 점검 의무

각 Step 완료 후 다음 점검:

1. **자체완결성 원칙** — 외부 경로 참조 0건. 외부 도구(NotebookLM, MCP)는 Tools 섹션의 명시적 종류 표기만, 실제 권한은 환경 적응에 위임
2. **"분야 전문가" 프레임 유지** — "70~80%", "골격" 같은 표현 금지
3. **분야 보편 vs 환경 적응 분리** — Plan팀 특수 적응(First Principle 5코드 등)이 분야 보편으로 누설되지 않음
4. **견 v0.1.1과 일관성** — Zones 구조·메타 항목 형식 일치
5. **DEPLOYMENT.md 사례 1 정확성** — Plan팀 보고와 일치하는 실제 적응 결과 반영

위반 가능성 발견 시 작업 멈추고 보고.

---

## 보류 사항 (이번 작업에서 안 함)

- **research-brief.md 산출물 표준 설계** — 운영 누적 후 결정 (§3 참조)
- **First Principle 헌법 격상** — 거부 결정 (Plan팀 보고의 의사결정 사항 2번에 대한 답)
  - 사유: 영역별 사실 무결성 규율은 다양해야 함. 단일 규율 강요는 분야 전문가 양산 원칙과 충돌
  - 대신 Zone 2 구조가 이 다양성을 보장. Plan팀의 First Principle은 가설형의 Plan팀 환경 사본에 보존
- **본질 동일성 스캔 절차화** — DEPLOYMENT.md Step 2에 부속 안내로만 통합 (별도 단계 신설 X)
  - 사유: 별도 단계 추가는 절차 복잡화. 부속 점검으로 충분

---

## 작업 완료 후 보고 내용

1. 2개 커밋 push 성공 여부 (커밋 해시 포함)
2. 점검 의무 5종 결과 (통과/위반)
3. 가설형 v0.1 → v0.1.1 변경 요약
4. DEPLOYMENT.md §7 사례 1의 정보 정확성 확인 (Plan팀 보고와 대조)
5. 발견된 약점·이상 (있다면)
