---
title: CSS-in-CSS
date: 2025-09-18
updated: 2025-09-18
tags:
  - status/growing
  - type/web
published: false
aliases: []
---
# CSS-in-CSS
- **정의:** 표준 CSS에는 없는 편리한 기능(변수, 중첩, 믹스인 등)을 가진 '슈퍼 CSS' 문법으로 스타일을 작성하는 방식입니다.
- **대표 주자:** Sass/SCSS, PostCSS
- **핵심 철학:** CSS는 CSS답게 작성하되, 개발을 더 편리하게 해주는 '슈퍼파워'를 부여한다.
- **작동 방식:** 개발자가 작성한 `.scss` 같은 파일을, 웹사이트를 빌드하는 시점(`npm run build`)에 컴파일러가 읽어서, 모든 브라우저가 이해할 수 있는 **표준 `.css` 파일로 변환**합니다.
- **비유:** **'레고 블록을 직접 디자인하는 3D 프린터'**. 당신이 더 멋진 모양의 레고 블록(Sass 문법)을 디자인하면, 3D 프린터(컴파일러)가 그것을 실제 조립에 사용할 수 있는 표준 레고 블록(`.css` 파일)으로 '출력'해주는 방식입니다.

[[250918-CSS-module|CSS 모듈(Module)]] 
[[250918-CSS-preprocessor|CSS 전처리기(Preprocessor)]]
[[250918-CSS-in-JS|CSS-in-JS도 있음]]
[[250918-Styling-managements|CSS 관리하기]]