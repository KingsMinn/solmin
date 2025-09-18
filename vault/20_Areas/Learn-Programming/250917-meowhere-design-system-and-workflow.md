---
title: 250917-meowhere-design-system-and-workflow
date: 2025-09-17
updated: 2025-09-17
tags:
  - status/growing
  - type/memoir
published: false
aliases: []
---
# 디자인 시스템 & 워크플로우 최적화
[깃허브](https://github.com/KingsMinn/Meowhere-Deploy?tab=readme-ov-file#%EB%94%94%EC%9E%90%EC%9D%B8-%EC%8B%9C%EC%8A%A4%ED%85%9C--%EC%9B%8C%ED%81%AC%ED%94%8C%EB%A1%9C%EC%9A%B0-%EC%B5%9C%EC%A0%81%ED%99%94)
![[Pasted image 20250918192229.png]]
![[Pasted image 20250918192233.png]]

- **문제 정의:** Figma 프로젝트와 개발자 코드가 분리되어 UI 일관성이 깨지고, SVG 아이콘 관리 비효율, 일관성 없는 애니메이션 등 개발자 경험과 사용자 경험 양쪽에서 문제가 발생함.
- **해결 과정:**
    - **Z-Index 시스템 설계:** 플로팅 UI 요소들의 계층 구조를 명확히 정의하고, 100단위의 간격을 둔 전역 `z-index` 시스템을 도입하여 충돌 문제를 원천적으로 해결함.
    - **SVG 컴포넌트 최적화:** 그래픽 디자인 경험을 활용, 상태에 따라 `path`만 조건부로 렌더링하는 단일 SVG 컴포넌트를 설계하여 아이콘 에셋 요청 수를 감소시키고 렌더링 비용을 최소화함.
    - **인터랙션 시스템 설계:** 모션그래픽 경험을 바탕으로, `cubic-bezier(0,.5,.5,1)`와 같이 목적에 따라 각기 다른 속도 곡선을 사용하는 애니메이션 시스템을 설계하고 팀에 전파하여 일관되고 쾌적한 UX를 제공함.
    - **Figma 최적화:** 분리되어 있던 Figma 컴포넌트들을 재구성하고 컬러, 폰트 스타일을 변수로 등록하여, 개발자가 한눈에 디자인 시스템을 파악하고 적용할 수 있도록 워크플로우를 개선함.
- **결과:** 디자인과 개발 간의 커뮤니케이션 비용 감소, UI 일관성 확보, 렌더링 성능 향상, 개발 속도 증대 등의 성과 달성
- **확장:** Figma 변수를 `Token Studio`**,** `Style Dictionary`와 같은 툴을 통해 자동으로 `tailwind.config.js` 파일로 변환하는 파이프라인을 만들어 완전한 디자인 시스템을 구축할 수 있음.