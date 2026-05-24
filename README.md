# persona-system

> Claude Code 환경 위에 자체완결적인 AI 페르소나 시스템을 구축한다.

## 핵심 결정

- **메타포**: AI 페르소나 = 외부 전문 컨설턴트. 의뢰인 = Joo. 결정·창작권은 의뢰인에게 있다.
- **운영 방식**: 1차 단계에서는 MD 정의 파일로 운영한다. Sub-agent 마이그레이션은 검증 후 결정.
- **자체완결성**: 외부 user skills에 의존하지 않는다. 필요한 도구는 프로젝트 안에 복사 보유한다. 외부 변경이 이 프로젝트에 영향을 주지 못한다.

페르소나는 분야 전문가로 정의되며, 환경 이식 시 5개 Customization Zone으로 적응한다.

## 디렉토리

```
persona-system/
├── README.md                 # 이 문서 — 프로젝트 한 줄·핵심 결정·디렉토리·동기화
├── OPERATIONS.md             # 호출 메커니즘·매핑 표·신규 페르소나 안내
├── CREATING-NEW-PERSONA.md   # 신규 페르소나 생성 표준 절차 (시스템 v0.2)
├── DEPLOYMENT.md             # 페르소나 환경 이식 표준 절차 (시스템 v0.3)
│
├── employees/                # 페르소나 정의
│   ├── content-strategist-essence.md
│   └── research-strategist-hypothesis.md
│
├── output-standards/         # 산출물 표준 템플릿
│   └── draft-with-rationale.md
│
├── templates/                # 페르소나 생성용 양식·템플릿·검증 테스트
│   ├── new-persona-input.md
│   ├── persona-definition-template.md
│   └── persona-validation-tests.md
│
├── skills/                   # 프로젝트 내부 스킬 (외부 의존 끊긴 복사본)
│   ├── content-os/
│   ├── idea-brainstorm/
│   ├── blog-writer/
│   └── question-design/
│
└── docs/
    └── process/              # 설계 과정의 사고 흔적 (운영 시 참조용)
```

## 사용 예시

자연어로 페르소나를 호출한다. 형식은 `[페르소나 식별] + [의뢰 내용] + [산출물 표준 지정]`.

```
콘텐츠 전략가에게 의뢰: Quiet Notes 첫 글 도입부.
draft-with-rationale 포맷으로.
```

전체 식별 키워드·호출 패턴은 `OPERATIONS.md` 참조.

## 새 페르소나 만들기

새 페르소나는 즉흥 설계가 아닌 표준 절차로 만든다. 입력 양식·정의 템플릿·검증 테스트는 `templates/`에 있고, 전체 절차는 [`CREATING-NEW-PERSONA.md`](./CREATING-NEW-PERSONA.md) 참조.

## 다기기 동기화

이 프로젝트는 GitHub `yongjooseok/persona-system`에 보관된다. 여러 Mac에서 작업하려면 각 기기에서 동일 경로에 clone한 뒤 `git pull` / `git push`로 동기화한다.

iCloud Drive 등 파일 동기화 도구는 사용하지 않는다 (`.git` 충돌 위험).

### 처음 설정 (각 기기에서 1회)
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

충돌 발생 시: 보통 `git pull` 시점에 감지된다. Claude Code에게 충돌 해결을 위임할 수 있다. 충돌 빈도가 높으면 한 기기에서만 작업하는 패턴으로 운영한다.
