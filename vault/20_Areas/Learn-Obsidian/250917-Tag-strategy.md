---
title: "태그 전략: '주제'가 아닌 '상태'와 '종류'를 기록하라"
date: 2025-09-17
updated: 2025-09-17
tags:
published: false
aliases: []
---
# 태그 전략: '주제'가 아닌 '상태'와 '종류'를 기록하라
많은 사람들이 저지르는 실수가 `#React`, `#JavaScript` 같은 '주제'를 태그로 다는 것입니다. 이러면 태그가 수백 개로 늘어나 관리가 불가능해집니다.

**규칙: 주제는 `[[링크]]`로, 태그는 '상태(Status)'와 '종류(Type)'에만 사용합니다.**

- #### 상태 태그 (Status Tags): 노트의 '생애 주기'를 표현
    - `#status/seed` 🌱: 이제 막 떠오른, 다듬어지지 않은 아이디어 씨앗.
    - `#status/growing`🌿: 내용을 채워나가고 있는, 성장 중인 노트.
    - `#status/evergreen`🌳: 여러 번의 수정을 거쳐 완성된, 나의 핵심적인 지식이 담긴 노트.
- #### 종류 태그 (Type Tags): 노트의 '정체성'을 표현
    - `#type/blog-post`: 블로그 발행을 위한 글.
    - `#type/meeting-note`: 회의록.
    - `#type/book-summary`: 책 요약.
    - `#type/person`: 인물 정보.
        

이렇게 하면, 나중에 Dataview 플러그인으로 "모든 블로그 글 중에서(#type/blog-post), 아직 아이디어 단계인 것들만(#status/seed) 보여줘" 같은 강력한 필터링이 가능해집니다.