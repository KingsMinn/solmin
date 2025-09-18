---
title: Tailwind
date: 2025-09-18
updated: 2025-09-18
tags:
  - status/growing
  - type/web
published: false
aliases: []
---
# Tailwind
- **정의:** `flex`, `pt-4`, `text-center` 처럼, **하나의 [[CSS]] 속성만을 담당하는 매우 작은 '유틸리티 클래스'** 들을 미리 수천 개 만들어두고, [[250918-HTML]]/[[JSX]]의 `className` 속성에서 이들을 '조립'하여 스타일을 만드는 방식입니다.
- **핵심 철학:** "CSS를 새로 작성하지 마라. 대신, 이미 존재하는 벽돌(유틸리티)을 조합해서 무엇이든 만들어라." 이것을 **'유틸리티 우선(Utility-First)'** 이라고 부릅니다.
- **작동 방식:** 당신이 HTML/JSX 파일에 사용한 클래스 이름들을, 빌드 시점에 Tailwind의 JIT(Just-In-Time) [[컴파일러]]가 **전부 스캔**합니다. 그리고 당신이 **사용한 클래스에 해당하는 CSS 규칙들만**을 골라서 아주 가볍고 최적화된 최종 `.css` 파일을 생성합니다. (내부적으로는 [[PostCSS]]를 사용하므로, [[CSS-in-CSS]]의 기술을 활용하는 셈이죠!)

[[250918-CSS-War|엥 이 방법 너무 근본없는데;]]