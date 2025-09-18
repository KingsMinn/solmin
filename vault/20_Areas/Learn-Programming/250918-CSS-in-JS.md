---
title: CSS-in-JS
date: 2025-09-17
updated: 2025-09-17
tags:
  - status/growing
  - type/web
published: false
aliases: []
---
# CSS-in-JS
CSS-in-JS는 단어 그대로 [[자바스크립트]] 코드에서 [[CSS]]를 작성하는 방식을 말합니다. 2014년 페이스북 개발자인 Christopher Chedeau aka Vjeux가 처음 소개하였습니다.  

- **정의:** 스타일 규칙을 `.js` 또는 `.tsx` 파일 안에, 자바스크립트 객체나 템플릿 리터럴 형태로 작성하는 방식입니다.
- **대표 주자:** [[Styled Components]], [[Emotion]]
- **핵심 철학:** 컴포넌트의 로직과 스타일은 한곳에 있어야 한다 ([[Co-location]]). 자바스크립트의 모든 힘(변수, 함수, 조건문)을 스타일링에 활용한다.
- **작동 방식:** 브라우저가 페이지를 로드할 때([[런타임]]) 또는 서버에서 미리([[SSR]]), **자바스크립트가 실행되어** `<style>` 태그를 동적으로 생성하고, 그 안에 CSS 규칙을 주입합니다.
- **비유:** **'런타임에 조립하는 레고 키트'**. 사용자에게 '레고 블록과 설명서(JS 코드)'를 보내주면, 사용자의 집(브라우저)에서 설명서를 읽으며 실시간으로 레고 모델(CSS)을 조립하는 방식입니다.

![Styles defined in a separate file :(JS,HTML), CSS / Behaviour, Markup and styles encapsulated in a single file(JS, HTML, CSS)](https://image.samsungsds.com/kr/insights/web_component_img03.jpg?queryString=20250214030334)

Vjeux는 CSS를 작성하는 어려움을 다음과 같이 설명하였으며 CSS-in-JS로 이들 이슈를 모두 해결할 수 있다고 강조했습니다.
- Global namespace: 글로벌 공간에 선언된 이름의 명명 규칙 필요  
- Dependencies: CSS간의 [[의존 관계]]를 관리
- Dead Code Elimination: 미사용 코드 검출  
- Minification: 클래스 이름의 최소화  
- Sharing Constants: JS와 CSS의 상태 공유
- Non-deterministic Resolution: CSS 로드 우선 순위 이슈  
- Isolation: CSS와 JS의 상속에 따른 격리 필요 이슈
  
그리고 기존 CSS 관리의 어려움을 해결한 페이스북의 사례를 소개하였습니다. 이후 개념이 발전하면서 많은 [[라이브러리]]가 등장했습니다.  

![2017년부터 2021년까지 css-in-js 라이브러리의 다운로드 수 추이는 styled-components, jss, emotion, aphrodite, radium, glamorous, styletron 순으로 높은 것으로 나타남](https://image.samsungsds.com/kr/insights/web_component_img04.jpg?queryString=20250214030334)

이 중 가장 대표적인 CSS-in-JS 라이브러리인 [[Styled Components]]를 살펴보겠습니다. Styled Components는 CSS-in-JS 스타일링을 위한 [[프레임워크]]입니다. 자바스크립트의 태그가 지정된 [[템플릿 리터럴]]과 CSS의 기능을 사용하여 구성 요소에 반응하는 스타일을 제공합니다. 장점은 다음과 같습니다.
- CSS 모델을 문서 레벨이 아닌 컴포넌트 레벨로 추상화하는 모듈성
- CSS-in-JS는 JavaScript 환경을 최대한 활용
- 자바스크립트와 CSS 사이의 상수와 함수를 공유
- 현재 사용 중인 스타일만 DOM에 포함
- 짧은 길이의 유니크 한 클래스를 자동으로 생성하는 코드 경량화

단점으로는
- 러닝 커브(Learning Curve)
- 새로운 의존성 발생
- 별도의 라이브러리 설치에 따른 번들 크기 증대
- CSS-in-CSS에 비해 느린 속도

등을 들 수 있습니다. Styled Components는 스타일링을 위한 코드 사용량이 줄어들고 CSS 문법에 친화적입니다. 이는 아래 예시를 보면 알 수 있습니다.

[[250918-Styling-managements|스타일 관리법]]
[[250918-CSS-in-CSS|CSS-in-CSS]]