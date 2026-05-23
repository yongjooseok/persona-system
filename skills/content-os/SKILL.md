---
name: content-os
description: REF/RFE 기반 콘텐츠 자동화 시스템. 역기획 분석(샘플에서 전략/규칙 추출), 쇼츠 스크립트 생성, 검수 시 사용. "쇼츠 써줘", "샘플 분석해줘", "검수해줘", "REF 추출", "RFE 추출" 등의 요청에 활성화.
---

# Content OS - 콘텐츠 자동화 시스템

## 핵심 원칙

1. **기준 먼저, 도구 나중**: 샘플 분석 → REF/RFE → 콘텐츠 생성
2. **REF = "왜"**, **RFE = "어떻게"**: 분리 관리
3. **측정 가능하게**: "좋은" ❌ → "15자 이내" ✅

---

## 워크플로우

### A. 역기획 분석 시

```
샘플 수집 → RFE 추출 → REF 추출 → 프로필 저장
```

- RFE 추출: [knowledge/RFE-GUIDE.md](knowledge/RFE-GUIDE.md) 참조
- REF 추출: [knowledge/REF-GUIDE.md](knowledge/REF-GUIDE.md) 참조

### B. 쇼츠 생성 시

```
주제 입력 → 프로필 참조 → 스크립트 작성 → 검수
```

- 프로필: [knowledge/SHORTS-V1-PROFILE.md](knowledge/SHORTS-V1-PROFILE.md) 참조
- 검수: [knowledge/SHORTS-CHECKLIST.md](knowledge/SHORTS-CHECKLIST.md) 참조

---

## 쇼츠 v1 빠른 참조

### 스펙
| 항목 | 규칙 |
|------|------|
| 길이 | 18-20초 |
| 글자수 | 100-130자 |
| 줄 수 | 12-14줄 |
| 한 줄 | 5-18자 (가변) |
| 구성 | 훅(1줄) + 본문(10-12줄) + 마무리(1줄) |

### 훅 공식 (첫 줄)
```
□ "[명사]가 [동사]한다는"
□ "[대상]이 [상황]이라는"
□ "사람들이 [행동]하는 이유"
```

### 마무리 공식 (끝 줄)
```
□ 질문형: "~인가?", "~인데?"
□ 위트형: "~ㅋㅋ", "~ㄷㄷ"
□ 자조형: "나만 ~인가?ㅠㅠ"
```

### 필수 체크
```
□ 글자수 100-130자
□ 줄 수 12-14줄
□ 첫 줄 호기심 유발
□ 끝 줄 반전/위트
□ 반말 사용
□ 정보 + 감정 둘 다
```

---

## 검수 판정

| 결과 | 조건 |
|------|------|
| ✅ 통과 | 모든 필수 항목 통과 |
| ⚠️ 수정 | 필수 1-2개 미통과 |
| ❌ 재작성 | 필수 3개+ 미통과 |

---

## 참조 파일

| 파일 | 용도 |
|------|------|
| [INSTRUCTIONS.md](INSTRUCTIONS.md) | 전체 지침 |
| [knowledge/REF-GUIDE.md](knowledge/REF-GUIDE.md) | REF 추출 가이드 |
| [knowledge/RFE-GUIDE.md](knowledge/RFE-GUIDE.md) | RFE 추출 가이드 |
| [knowledge/SHORTS-V1-PROFILE.md](knowledge/SHORTS-V1-PROFILE.md) | 쇼츠 v1 프로필 |
| [knowledge/SHORTS-CHECKLIST.md](knowledge/SHORTS-CHECKLIST.md) | 검수 체크리스트 |
| [knowledge/TEMPLATES.md](knowledge/TEMPLATES.md) | 출력 템플릿 |
