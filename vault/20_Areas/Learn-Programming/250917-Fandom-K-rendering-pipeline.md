---
title: "성능 최적화: 60fps를 위한 렌더링 파이프라인 구축"
date: 2025-09-17
updated: 2025-09-17
tags:
published: false
aliases: []
---
# 성능 최적화: 60fps를 위한 렌더링 파이프라인 구축
[깃허브](https://github.com/KingsMinn/Fandom-K?tab=readme-ov-file#%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94-60fps%EB%A5%BC-%EC%9C%84%ED%95%9C-%EB%A0%8C%EB%8D%94%EB%A7%81-%ED%8C%8C%EC%9D%B4%ED%94%84%EB%9D%BC%EC%9D%B8-%EA%B5%AC%EC%B6%95)
![[download.webp]]

- **문제 정의:** 프로젝트의 핵심인 랜딩 페이지는 다수의 스크롤 기반 애니메이션으로 구성되어 있었으나, 초기 구현 시 `scroll` 이벤트의 과다 발생으로 인한 잦은 리렌더링과 [[reflow/repaint]]로 인해 심각한 성능 저하가 발생함. 개발자 도구 분석 결과, 애니메이션 처리 속도가 4.45초에 달하며 사용자 경험을 심각하게 해치는 수준이었음.
- **해결 과정:**
    - **대안 분석:**
        1. 순수 JS와 CSS `transform`을 통한 직접 구현
        2. [[GSAP]]
        3. [[Framer Motion]]
        
        1은 이벤트 [[Throttling]]과 GPU 가속(`translate3d`)을 적용했으나 복잡한 연산에 한계가 있었음. [[React]] 환경과의 호환성을 고려하여 3. Framer Motion을 최종 선택함.
        
    - **최종 선택:**
        1. **애니메이션 로직 분리:** `Framer Motion`의 `useScroll`, `useTransform` 훅을 활용하여 스크롤 진행도와 애니메이션 값을 분리 및 관리함.
        2. **이벤트 최적화:** [[requestAnimationFrame]]을 통해 `throttle`을 적용하여 비디오 프레임 재생과 같은 무거운 작업을 16ms(60fps) 간격으로 제한, 불필요한 이벤트 콜백을 제거함.
- **결과:** 랜딩페이지의 애니메이션 처리 속도를 4.45초에서 0.47초로 약 9.47배 향상시키며 60fps의 안정적인 애니메이션을 달성함.
- **확장:** 향후 [[Intersection Observer]]를 활용한 이미지 지연 로딩을 도입한다면 초기 로딩 성능을 더욱 극대화할 수 있을 것으로 예상함.