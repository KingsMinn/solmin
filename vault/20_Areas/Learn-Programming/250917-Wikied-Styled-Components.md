---
title: "CSS-in-JS: Styled Components와 SSR의 상충 관계"
date: 2025-09-17
updated: 2025-09-17
tags:
  - status/growing
  - type/memoir
published: false
aliases: []
---
# [[250918-CSS-in-JS]]: [[Styled Components]]와 [[SSR]]의 상충 관계
[깃허브](https://github.com/KingsMinn/Wikied-Distribution?tab=readme-ov-file#css-in-js-styled-components%EC%99%80-ssr%EC%9D%98-%EC%83%81%EC%B6%A9-%EA%B4%80%EA%B3%84)

- **문제 정의:** 팀원 모두가 `Styled Components`에 익숙했지만, CSS-in-JS [[라이브러리]]의 [[런타임]] 특성은 [[Next.js]]의 SSR 환경에서 초기 로딩 시 스타일이 적용되지 않는 깜빡임 현상과 성능 저하를 유발하는 기술적 문제가 있었음.
- **해결 과정:**
    - **대안 분석:**
        1. 팀의 학습 곡선을 고려하여 익숙한 `Styled Components`를 유지하고 문제를 해결하는 방법
        2. [[250918-Tailwind|Tailwind CSS]]와 같이 Next.js와 더 잘 맞는 다른 스타일링 솔루션을 도입하는 방법
        
        프로젝트의 짧은 기간을 고려하여 1을 선택하되, 문제 해결 과정을 통해 팀의 기술적 이해도를 높이는 것을 목표로 함.
        
    - **최종 선택:** [[next.config]]에서 [[compiler]]에 styledComponents를 추가하고, 빌드 시점에 서버에서 생성된 스타일을 [[클라이언트]]에 미리 주입하는 방식으로 SSR 환경에서의 스타일 문제를 해결함.
- **결과:** 팀원들이 익숙한 기술 스택을 유지하면서도 Next.js 환경에서 발생하는 기술적 문제를 성공적으로 해결함. 이 과정을 통해 팀 전체가 CSS-in-JS와 서버 사이드 렌더링의 동작 원리에 대해 더 깊이 이해하는 계기가 됨.
- **확장:** 이 경험을 통해, 향후 Next.js 프로젝트에서는 [['Zero-Runtime' CSS-in-JS|제로 런타임 CSS-in-JS]] 라이브러리나 `Tailwind CSS`를 사용하는 것이[[ 프레임워크]]의 철학에 더 부합하며 장기적인 성능과 유지보수성 측면에서 더 유리하다는 기술적 결론을 내림. 