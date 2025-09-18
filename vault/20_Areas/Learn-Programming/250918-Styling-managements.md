---
title: 웹 스타일링 관리
date: 2025-09-18
updated: 2025-09-18
tags:
  - status/growing
  - type/web
published: false
aliases: []
---
# 웹 스타일링 관리
[[HTML(Hypertext Markup Language)]]이 처음 등장한 1991년에는 [[CSS(Cascading Style Sheets)]]가 없었습니다.

웹 이용자들이 늘어나면서 디자인에 대한 요구가 커졌고 웹 고안자들은 HTML을 꾸며주는 언어의 필요성을 공감하게 되었습니다. 그렇게 해서 1996년 CSS가 발표되었습니다.

하지만 웹이 점점 복잡해지고 동적 기능 요구가 증가하면서 HTML과 CSS만으로는 화면의 모든 스타일을 제어할 수 없는 상황에 이르게 됩니다.

이를 해결하기 위한 여러 가지 웹 [[애플리케이션]] 스타일 구성 방식이 나타났으며 크게 두 갈래로 나뉘어집니다. [[250918-CSS-in-JS|CSS-in-JS]]와 [[250918-CSS-in-CSS|CSS-in-CSS]]가 그것입니다.

근데 [[250918-Tailwind|유틸리티 CSS가 등장함]]

## CSS-in-JS vs CSS-in-CSS (퍼포먼스 비교)
[[Styled Components]]에서 확인한 결과입니다. 첫 번째 페이지 전환에 358ms가 소요됨
[[250918-CSS-module]]에서 확인한 결과입니다. 첫 번째 페이지 전환에 90.5ms가 소요되었습니다.

Styled Components에 비해서 시간이 줄어들었습니다. CSS 파일이 추출되는 CSS 모듈 방식은 자바스크립트 해석 과정이 따로 없기 때문에 페이지가 훨씬 빨리 전환됩니다.  

## 마치며
CSS는 1996년에 도입된 이래 사용 효율성을 높이는 방향으로 발전해왔습니다.

![CSS, SASS, BEM, CSS Modules, Styled Components](https://image.samsungsds.com/kr/insights/web_component_img09.jpg?queryString=20250214030334)

앞서 CSS-in-CSS와 CSS-in-JS를 간단히 살펴보았지만 어떤 방식이 더 낫다고 쉽게 말할 수는 없습니다.
다만 본인의 경험에 비추어 봤을 때 작업자의 성향이나 판단이 필요한 부분이나 개발 효율성에 중점을 둔 컴포넌트 위주의 프로젝트라면 CSS-in-JS를 고려하는 것이 좋습니다. 필요한 컴포넌트 페이지의 CSS 스타일 요소만 로딩하기 때문입니다. 반면 사용자 편의에 방점을 둔 인터렉티브한 웹 프로젝트라면 랜더링 시 모든 CSS 스타일 요소를 로딩하는 CSS-in-CSS 방식을 권장하는 바입니다.

[우리가 CSS-in-JS와 헤어지는 이유](https://junghan92.medium.com/%EB%B2%88%EC%97%AD-%EC%9A%B0%EB%A6%AC%EA%B0%80-css-in-js%EC%99%80-%ED%97%A4%EC%96%B4%EC%A7%80%EB%8A%94-%EC%9D%B4%EC%9C%A0-a2e726d6ace6)