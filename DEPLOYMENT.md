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

향후 사례 누적되면 패턴 분석 가능.
