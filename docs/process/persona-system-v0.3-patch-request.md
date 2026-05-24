# persona-system v0.3 패치 통합 요청서

작업 위치: `~/work/persona-system/`

---

## 배경

Plan팀에 리서치 페르소나 가설형 v0.1 이식 사례에서 시스템 정체성 재정의 필요성 발견:
- 페르소나는 분야 전문가로 정의되어야 함 (불완전한 골격 X)
- 다만 실제 운영 환경(팀·도구·산출물 양식)은 환경마다 다름
- 환경별 특수성은 이식 시점에 5개 Customization Zone으로 조정

v0.3는 이 패러다임을 시스템에 정착시킨다.

## 작업 범위

5개 파일 패치 + 1개 파일 신설 + 2개 운영 문서 업데이트.

전체 작업이 한 패러다임 적용이므로 일관성 확보를 위해 한 번에 진행.
단, 의미 단위 분할 커밋으로 history는 명확히 유지.

---

# Step 1. 페르소나 정의 템플릿 패치

파일: `templates/persona-definition-template.md`

## 변경 1-1: Meta 섹션에 "알려진 한계" 항목 추가

위치: 기존 Meta 섹션의 "다음 작업" 항목 **직전**

추가 내용:

```markdown
- **알려진 한계 (Known Limitations)**: (신규)
  - [v0.1 시점에 의도적으로 미해결한 사항]
  - [페르소나가 책임지지 않는 것 — 환경 적응으로 해결될 영역]
  - 예: "Algorithm은 단발 의뢰 기준. 사이클·환류는 Zone 5 환경 적응으로 위임"
```

## 변경 1-2: Customization Zones 섹션 신설

위치: Meta 섹션 **다음** (페르소나 본문 끝)

추가 내용:

```markdown
## Customization Zones (환경 적응 영역)

이 페르소나는 분야 전문가로 정의된다. 다만 실제 운영 환경
(팀·도구·산출물 양식 등)은 환경마다 다르므로, 다음 5개 Zone은 
이식 시점에 환경에 맞춰 조정한다.

각 Zone은 "분야 보편(보존)"과 "환경 적응(이식 시 결정)"로 구분된다.

### Zone 1: Output Format (산출물 양식)
- **분야 보편**: [이 페르소나 산출물의 핵심 4원칙 — 결정·근거·수정·대안]
- **환경 적응**: 환경의 기존 양식·템플릿·평가 체크리스트에 맞춤

### Zone 2: Fact Integrity (사실 무결성 규율)
- **분야 보편**: 추측·확신·인용 구분 의무, 모름은 모름으로 표시, 
  LLM 추론과 사실 구분
- **환경 적응**: 환경의 구체 마커 체계·검증 룰·LLM 면제 여부에 맞춤

### Zone 3: Tools & Permissions (도구·권한)
- **분야 보편**: 이 페르소나가 필요로 하는 도구의 종류 
  (검색·요약·생성·분석 등)
- **환경 적응**: 환경의 권한 매트릭스·구체 도구·거버넌스 정책에 맞춤

### Zone 4: Operating Context (운영 환경 인식)
- **분야 보편**: [단독 운영 / 팀 환경 / 배치 시 결정 — 본 페르소나 기본 가정]
- **환경 적응**: 환경 아키텍처·상하류 핸드오프·내부 협업 구조 인식 추가

### Zone 5: Feedback Loop (환류 메커니즘)
- **분야 보편**: 환류 유무 명시 (있음 / 없음). 있음 시 일반 형태
- **환경 적응**: 환경의 구체 환류 메커니즘·산출물 양식·회수 절차 통합

---

> **참조**: 페르소나를 환경에 이식하는 표준 절차는 `DEPLOYMENT.md` 참조.
```

---

# Step 2. CREATING-NEW-PERSONA.md 패치

파일: `CREATING-NEW-PERSONA.md`

## 변경 2-1: §3 6요소 설계 가이드에 Customization Zones 설계 항목 추가

위치: §3 끝부분

추가 내용:

```markdown
### Customization Zones 설계 (필수)

분야 전문가로 페르소나를 정의한 뒤, 5개 Customization Zone을 작성한다.
Zones는 "분야 보편(보존)"과 "환경 적응(이식 시 결정)"을 명시하여 
환경 이식 시 어디를 조정해야 하는지 사전에 표시한다.

5개 Zone:
- Zone 1: Output Format (산출물 양식)
- Zone 2: Fact Integrity (사실 무결성 규율)
- Zone 3: Tools & Permissions (도구·권한)
- Zone 4: Operating Context (운영 환경 인식)
- Zone 5: Feedback Loop (환류 메커니즘)

각 Zone의 정의·작성 방법은 `templates/persona-definition-template.md` 참조.

**약점 신호**: 모든 Zone을 "환경 적응에 위임"으로만 채움 → 페르소나가 
분야 전문가로 정의된 게 아님. 분야 보편 부분에 페르소나의 전문성이 
구체적으로 드러나야 함.
```

## 변경 2-2: §3 6요소 표 아래 보조 항목 추가

위치: 기존 6요소 표 **아래**

추가 내용:

```markdown
| 추가 섹션 | 설계 가이드 | 약점 신호 |
|---|---|---|
| **Customization Zones** | 5개 Zone 모두 작성. 분야 보편/환경 적응 분리 명시 | Zone 모두 "환경에 위임"만 — 전문성 정의 부재 |
| **Meta — 알려진 한계** | 설계 시점에 의도적으로 미해결한 사항 명시 | "없음"만 표기 — 자기 인식 부재 |
```

## 변경 2-3: §4 v0.1 이후 패치 절차 본문 교체

기존 §4 본문 전체를 다음으로 **교체**:

```markdown
## 4. v0.1 이후 패치 절차

페르소나 v0.1이 배치된 뒤 실전 의뢰로 약점 발견 시:

**마이너 패치 (v0.1.1, v0.1.2...)** — 같은 파일 직접 수정
- Backstory 구체 사건 보강
- Voice 피하는 표현 추가
- Boundaries 항목 추가·수정
- Zone의 분야 보편 부분 보강
- Tools 추가

**메이저 패치 (v0.2)** — 변경 사유를 Meta에 기록
- Algorithm 단계 추가·삭제·재설계
- Lens 우선순위 재배치
- Customization Zones 추가·삭제·재정의
- 페르소나 정체성 변경

원본 v0.1 백업은 git history로 충분. 별도 파일 보관 안 함 (YAGNI).

**환경 적응(Zone 커스텀화)은 패치가 아니다.** 환경별 적응 사항은 
환경 측에 보관. 페르소나 원본은 분야 전문가 정의 유지.
(상세는 `DEPLOYMENT.md` 참조)
```

## 변경 2-4: §7 체크리스트에 항목 2개 추가

위치: 기존 8개 항목 **끝**

추가 내용:

```markdown
- [ ] **Customization Zones 5개 모두 작성됐는가** (신규)
- [ ] **Meta의 "알려진 한계" 항목이 작성됐는가** (신규)
```

본문에 "8개 모두 통과" 같은 표현 있으면 → **"10개 모두 통과"** 로 변경.

---

# Step 3. DEPLOYMENT.md 신설

파일: `DEPLOYMENT.md` (루트, 신규)

전체 내용 (그대로 작성):

```markdown
# Persona Deployment Guide

페르소나를 환경(팀·프로젝트·운영 컨텍스트)에 이식할 때 따르는 표준 절차.

## 1. 이 문서의 역할

- **CREATING-NEW-PERSONA.md**: 페르소나를 만드는 방법
- **DEPLOYMENT.md** (이 문서): 페르소나를 환경에 이식·적응시키는 방법

페르소나는 분야 전문가로 정의된다. 그러나 실제 운영 환경(팀의 자산·도구·산출물 양식)은 환경마다 다르다. 이식 시점에 5개 Customization Zone을 환경에 맞춰 조정한다.

## 2. 이식이 필요한 시점

- persona-system의 페르소나를 새로운 환경에 처음 배치할 때
- 같은 페르소나를 다른 환경에 추가 배치할 때
- 페르소나 v0.1.x → v0.2 메이저 패치 후 재배치할 때

## 3. 이식 절차 (5단계)

### Step 1 — 환경 자산 파악

이식할 환경의 기존 자산을 전수 조사한다:

- 운영 가이드 (guides/, docs/)
- 작업 템플릿 (templates/)
- 참조 정책 (reference/, policy/)
- 평가 기준 (evaluations/, quality checks)
- 기존 산출물 사례 (output/)
- 시스템 메커니즘 (아키텍처·환류·자기진화 등)

환경이 단독 운영(자산 부재) → "환경 자산 없음" 명시 후 Step 4로.

### Step 2 — 5개 Zone 검토

페르소나 정의의 Customization Zones 섹션과 환경 자산을 매핑한다.

| Zone | 환경 자산 매핑 | 적응 작업 |
|---|---|---|
| Zone 1: Output Format | 환경의 산출물 템플릿 | 페르소나 산출물을 환경 양식에 맞춤 |
| Zone 2: Fact Integrity | 환경의 사실 무결성 규율·체크리스트 | 페르소나의 일반 규율을 환경의 구체 규율에 맞춤 |
| Zone 3: Tools & Permissions | 환경의 권한 매트릭스·도구 정책 | Tools 섹션을 환경 정합으로 재정렬 |
| Zone 4: Operating Context | 환경 아키텍처·핸드오프 구조 | 페르소나의 환경 인식 추가 |
| Zone 5: Feedback Loop | 환경의 환류 시스템 | 페르소나 산출물을 환류 메커니즘에 통합 |

### Step 3 — 추가 갭 점검

5개 Zone 외 영역에서 갭이 발견될 수 있다. 이때 분류:

- **Critical**: 1회 가동 시 즉시 발현, 환경 신뢰성 손상 위험
- **Major**: 운영 가능하나 품질·일관성 저하
- **Minor**: 운영 안정 후 검토

Critical 발견 시 Step 4·5 진행 전 적응 작업 우선 처리.

### Step 4 — 적응 작업 실행

각 Zone별 적응 결정:

| 결정 | 처리 |
|---|---|
| 환경 적응 | 환경 자산에 맞춰 페르소나의 환경별 사본 수정 |
| 환경 자산 수정 | 환경의 가이드·템플릿 보강 |
| 양쪽 모두 | 위 두 가지 동시 |
| 갭 수용 | 운영 중 패치 (Minor에 한함) |

**원본 페르소나는 수정하지 않는다.** 환경별 사본을 만들어 적응한다.

- 원본 위치: `persona-system/employees/`
- 환경별 사본 위치: 환경의 personas/ 디렉토리 (예: `research/Plan/personas/`)

### Step 5 — 드라이런 → 가동

1. 적응된 페르소나로 가상 의뢰 1건 실측
2. 5개 Zone이 환경에서 자연스럽게 작동하는지 검증
3. 추가 갭 발견 시 Step 4로 복귀
4. 통과 시 저위험 실전 의뢰 1회로 정식 가동

## 4. 원본 ↔ 환경 사본 관계

- 한 번 이식되면 원본과 환경 사본은 **독립 진화**
- 원본 v0.2 패치 발생 시 환경 사본 자동 동기화 X (적응 사항 손실 위험)
- 원본 패치의 이점을 받고 싶으면 환경이 **수동 재배포 + 재적응** 결정
- 동기화 여부는 환경 자율

## 5. 환경 사본의 보관

환경 사본은 환경 측 레포에 보관한다.

위치 예시:
`[환경 레포]/[팀명]/personas/[페르소나명].md`

환경 사본에는 적응 사항을 git commit으로 기록:

`personas: Adapt [페르소나명] for [환경명] (Zones 2,3,4)`

## 6. 이식 이력 추적 (선택)

이식이 누적되면 어느 환경에 어떤 페르소나가 배치됐는지 추적 필요.

3개 이상 환경에 이식된 시점에 `deployments.md` 또는 별도 디렉토리에 기록 시작.
2개 이하면 git history로 충분.

## 7. 사례 기록

### 사례 1 — 리서치 전략가 가설형 → Plan팀
- 시점: 2026-05
- 환경: research/Plan (research 레포)
- 적응 Zone: 1, 2, 3, 4, 5 (모든 Zone)
- 핵심 적응:
  - Zone 1: Plan팀 9-섹션 템플릿 채택
  - Zone 2: First Principle ([?] 5코드 + 30초 룰) 수용
  - Zone 3: tier 권한 매트릭스 정합 (NotebookLM·MCP 제거)
  - Zone 4: 4계층 아키텍처 인식
  - Zone 5: §9 Gap Report 환류 통합
- 참조: research 레포의 changelog 또는 commit history

향후 사례 누적되면 패턴 분석 가능.
```

---

# Step 4. 견 v0.1.1 패치

파일: `employees/content-strategist-essence.md`

## 변경 4-1: frontmatter version

`version: 0.1` → **`version: 0.1.1`**

## 변경 4-2: Meta 섹션에 "알려진 한계" 항목 추가

위치: Meta 섹션의 "다음 작업" **직전**

추가 내용:

```markdown
- **알려진 한계 (Known Limitations)**:
  - Backstory가 추상적 — 실제 사건·작업 사례 부족 (v0.1 시점 의도적 미루기)
  - Algorithm 8단계는 초안 의뢰 기준. 검수 의뢰는 별도 알고리즘 필요 (미설계)
  - Output Standards 4종 중 1종(draft-with-rationale)만 설계됨
  - Voice "피하는 표현" 리스트가 제한적 — 실전 누적으로 확장 필요
  - 박웅현 차용 범위의 경계 — Algorithm은 사후 재구성이므로 실제 박웅현의 
    사고 순서와 100% 일치 보장 안 됨
```

## 변경 4-3: Meta "다음 작업" 항목 교체

기존 "다음 작업" 내용을 다음으로 **교체**:

```markdown
- **다음 작업**:
  - 실전 의뢰로 v0.1.1 → v0.1.2 검증·보강
  - 검수 의뢰용 Algorithm 분기 설계 (필요 발생 시)
  - 추가 Output Standards 설계 (실전에서 필요 발생 시)
```

## 변경 4-4: Customization Zones 섹션 신설

위치: Meta 섹션 **다음**

추가 내용:

```markdown
## Customization Zones (환경 적응 영역)

이 페르소나는 콘텐츠 전략 분야 전문가로 정의된다. 다만 실제 운영 환경
(팀·도구·산출물 양식 등)은 환경마다 다르므로, 다음 5개 Zone은 이식 시점에 
환경에 맞춰 조정한다.

각 Zone은 "분야 보편(보존)"과 "환경 적응(이식 시 결정)"로 구분된다.

### Zone 1: Output Format (산출물 양식)
- **분야 보편**: 산출물 4원칙 — 결정 가능성·추적 가능성·수정 가능성·대안 가시성. 
  의뢰인이 검토·결정·편집할 수 있는 형태. 산출 옆에 "왜 이렇게 썼는가" 근거 첨부
- **환경 적응**: 환경의 기존 산출물 양식·평가 체크리스트·필드 규칙에 맞춤. 
  단독 환경에서는 `output-standards/draft-with-rationale.md` 그대로 사용

### Zone 2: Fact Integrity (사실 무결성 규율)
- **분야 보편**: "형용사를 의심한다" — 진부함·과장·미사여구 회피. 본질 추출 후 
  검증되지 않은 수식어 자동 제거. 의뢰인의 자료에서 도출된 것과 페르소나의 
  해석을 구분 명시
- **환경 적응**: 환경의 구체 마커 체계·검증 룰·인용 형식에 맞춤. 환경에 
  사실 무결성 정책이 있으면 그것 채택

### Zone 3: Tools & Permissions (도구·권한)
- **분야 보편**: 콘텐츠 전략에 필요한 도구 종류 — 구조화(@skills/content-os), 
  발상(@skills/idea-brainstorm), 작성(@skills/blog-writer), 의뢰인 질문 설계
  (@skills/question-design). 모두 프로젝트 내부 스킬
- **환경 적응**: 환경에 추가 도구·권한 매트릭스가 있으면 그에 맞춰 Tools 재정렬. 
  외부 도구 사용 시 환경 거버넌스 정책 정합 확인

### Zone 4: Operating Context (운영 환경 인식)
- **분야 보편**: 단독 운영 기본 가정. 의뢰인 1명 ↔ 페르소나 1명. 
  단발 의뢰 처리 후 다음 의뢰
- **환경 적응**: 팀 환경(파이프라인·계층 등)에 이식 시 상하류 핸드오프 인식 추가. 
  콘텐츠팀(리서처·전략가·카피라이터·편집자) 구성 시 다른 역할과의 협업 
  인터페이스 명시

### Zone 5: Feedback Loop (환류 메커니즘)
- **분야 보편**: 환류 없음. 단발 의뢰 페르소나로 설계됨. 의뢰인이 결정·편집한 
  결과가 자동으로 다음 의뢰에 반영되지 않음
- **환경 적응**: 환경에 환류 시스템(자기진화·학습 누적 등)이 있으면 통합 검토. 
  의뢰 누적 패턴을 페르소나가 학습해야 한다면 환경 측에서 메커니즘 설계

---

> **참조**: 페르소나를 환경에 이식하는 표준 절차는 `DEPLOYMENT.md` 참조.
```

---

# Step 5. README.md 업데이트

파일: `README.md`

## 변경 5-1: 디렉토리 구조에 DEPLOYMENT.md 추가

기존 트리 구조의 `CREATING-NEW-PERSONA.md` 다음 줄에 다음 추가:

```
├── DEPLOYMENT.md             # 페르소나 환경 이식 표준 절차 (시스템 v0.3)
```

## 변경 5-2: 시스템 소개 부분에 v0.3 패러다임 1줄 추가

README의 시스템 소개 적절한 위치에 다음 1줄 추가:

```
페르소나는 분야 전문가로 정의되며, 환경 이식 시 5개 Customization Zone으로 적응한다.
```

---

# Step 6. OPERATIONS.md 업데이트

파일: `OPERATIONS.md`

## 변경 6-1: "페르소나를 환경에 이식할 때" 섹션 신설

위치: 기존 "새 페르소나가 필요할 때" 섹션 **다음**

추가 내용:

```markdown
## 페르소나를 환경에 이식할 때

페르소나를 외부 팀·환경에 배치할 때는 단순 복사가 아닌 환경 적응 절차를 거친다.
5개 Customization Zone을 환경에 맞춰 조정한다.

상세 절차: `DEPLOYMENT.md` 참조.
```

---

# Step 7. 분할 커밋 → push

의미 단위로 5개 커밋:

| # | 커밋 메시지 | 포함 변경 |
|---|---|---|
| 1 | `docs: Add DEPLOYMENT guide (v0.3 patch)` | DEPLOYMENT.md 신설 |
| 2 | `templates: Add Customization Zones to persona definition template` | persona-definition-template.md 패치 |
| 3 | `docs: Update CREATING-NEW-PERSONA for Zones and patch versioning` | CREATING-NEW-PERSONA.md 패치 |
| 4 | `employees: Patch 콘텐츠 전략가 본질형 to v0.1.1 (Zones + Known Limitations)` | content-strategist-essence.md 패치 |
| 5 | `docs: Update README and OPERATIONS for v0.3` | README.md, OPERATIONS.md 패치 |

각 커밋 후 push.

---

# 점검 의무

각 Step 완료 후 다음 점검:

1. **자체완결성 원칙** — 외부 경로 참조 0건
2. **"분야 전문가" 프레임 유지** — "70~80%", "골격" 같은 표현 금지
3. **CREATING vs DEPLOYMENT 역할 분담 명확** — 양산 vs 이식
4. **견 v0.1.1의 분야 전문성 보존** — Algorithm·Lens·Voice·Backstory 변경 없음

위반 가능성 발견 시 작업 멈추고 보고.

---

# 보류 사항 (이번 작업에서 안 함)

- **가설형 v0.1.1 패치** — Plan팀 트랙 1 (확장 패치 A 7건) 완료 후 별도 작업
  - 이유: Plan팀의 실제 적응 결과를 Zones에 정확히 반영 가능
- **research-brief.md 산출물 표준 설계** — 가설형 v0.1.1 패치와 함께 별도 작업

---

# 작업 완료 후 보고 내용

1. 5개 커밋 push 성공 여부
2. 각 Step별 점검 의무 4종 결과
3. 시스템 v0.2 → v0.3 변경 요약
4. 발견된 약점·이상 (있다면)
