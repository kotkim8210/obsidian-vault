---
type: moc
tags:
  - moc
created: 2026-11-09
---

# Home

## 엘렌코스 사고 검증법

GPT를 소크라테스식 심문관으로 쓰는 방법. 출발점은 [[엘렌코스 사고 검증법]].

### 바로 쓰기

1. GPT에 고민을 충분히 설명한다.
2. [[프롬프트 1 - 소크라테스 엘렌코스 심문]] 붙여넣기 → 질문에 답하기 → "아포리아" 선언까지.
3. [[프롬프트 2 - 소크라테스가 남기는 말]] 붙여넣기 → 세 줄 + 이번 주 액션 3개.
4. `Sessions/` 폴더에 [[아포리아 세션 기록]] 템플릿으로 노트를 만들어 기록한다.
5. 같은 전제가 반복해서 무너지면 [[프롬프트 3 - 삼중 아포리아 마스터 프롬프트]].

### 출처

- [[하버드 교수가 쓰는 GPT-6 활용법 - GPT 연대경영]]

## 세션 집계 (Dataview 플러그인 필요)

```dataview
TABLE WITHOUT ID
  file.link AS "세션",
  topic AS "주제",
  assumption_broken AS "무너진 전제",
  aporia AS "아포리아"
FROM "Sessions"
WHERE type = "session"
SORT date DESC
```

반복해서 무너지는 전제 (3회 이상이면 핵심 편향):

```dataview
TABLE length(rows) AS "횟수", rows.file.link AS "세션"
FROM "Sessions"
WHERE type = "session" AND assumption_broken
GROUP BY assumption_broken
SORT length(rows) DESC
```

## 폴더

| 폴더 | 내용 |
|---|---|
| `Methods/` | 방법 설명 |
| `Prompts/` | 복사해 쓰는 프롬프트 원문 |
| `Templates/` | 세션 기록 템플릿 (설정 → 핵심 플러그인 → 템플릿 폴더를 `Templates`로 지정) |
| `Sessions/` | 세션 기록 (첫 세션 때 만들면 됨) |
| `Sources/` | 출처 노트와 캡처 |
