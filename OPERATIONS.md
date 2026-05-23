# OPERATIONS

페르소나 시스템 운영 매뉴얼.

---

## 1. 호출 메커니즘

### 형식
```
[페르소나 식별] + [의뢰 내용] + [산출물 표준 지정]
```

세 요소가 모두 들어가야 의뢰가 완결된다.
- **페르소나 식별** — 어떤 전문가에게 의뢰하는지
- **의뢰 내용** — 무엇을 만들어야 하는지
- **산출물 표준 지정** — 어떤 포맷으로 받을지

산출물 표준 지정이 빠지면 페르소나가 의뢰인에게 되묻는다.

---

## 2. 식별 키워드 매핑

| 자연어 | 매핑 |
|---|---|
| "콘텐츠 전략가" / "본질형 전략가" / "본질형" | `employees/content-strategist-essence.md` |
| "draft-with-rationale" / "초안+근거" | `output-standards/draft-with-rationale.md` |
| `@skills/content-os` (정의 파일 내부 표기) | `./skills/content-os/SKILL.md` |
| `@skills/idea-brainstorm` | `./skills/idea-brainstorm/SKILL.md` |
| `@skills/blog-writer` | `./skills/blog-writer/SKILL.md` |
| `@skills/question-design` | `./skills/question-design/SKILL.md` |

식별 키워드가 모호하면 호출 패턴을 더 엄격하게 명시한다 (전체 이름 사용, 파일명 직접 호출 등).

---

## 3. 첫 의뢰 예시

```
콘텐츠 전략가에게 의뢰: Quiet Notes 'Claude Code 실전 100' 시리즈 첫 글 도입부 (약 300자).
AdSense 친화적이되 AI 콘텐츠 느낌 안 나게.
draft-with-rationale 포맷으로.
```

이 한 줄에 세 요소가 모두 있다:
- 식별: "콘텐츠 전략가"
- 의뢰 내용: 도입부 + 길이 + 제약
- 산출물 표준: "draft-with-rationale"

---

## 4. 자체완결성 원칙 (지킬 것)

이 프로젝트는 **외부 경로를 절대 참조하지 않는다**.

- 정의 파일 안에서 `~/.claude/...` 같은 외부 user skills 경로를 쓰지 않는다
- 새 스킬·자산이 필요하면 외부에 의존하지 않고 프로젝트 안으로 복사한다
- 외부 도구가 바뀌어도 이 프로젝트는 깨지지 않아야 한다

위반이 발견되면 작업을 멈추고 보고한 뒤 내부화한다.

---

## 5. 신규 페르소나 추가 절차

새 페르소나가 필요할 때 다음 4단계를 따른다.

1. **6요소로 정의 작성** — Role / Goal / Backstory / Tools / Lens / Algorithm. Lens·Algorithm 생략 금지.
2. **파일 배치** — `employees/<persona-codename>.md`로 저장. frontmatter에 `type: persona`, `codename: <영문 식별자>` 포함.
3. **자체완결성 점검** — 외부 경로 참조가 없는지 확인. 새 스킬 필요 시 `skills/` 아래로 복사.
4. **OPERATIONS.md 갱신** — 위 §2 매핑 표에 자연어 식별 키워드 추가.

산출물 표준이 새로 필요한 경우엔 `output-standards/`에 템플릿 1개를 추가하고 매핑 표에 등록한다. 추상화는 두 번째 사례가 생길 때 시작한다 (YAGNI).
