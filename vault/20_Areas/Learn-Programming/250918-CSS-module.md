---
title: CSS 모듈
date: 2025-09-18
updated: 2025-09-18
tags:
  - status/growing
  - type/web
published: false
aliases: []
---
# CSS 모듈
CSS 모듈은 CSS를 모듈화 하여 사용하는 방식입니다. CSS 클래스를 만들면 자동으로 고유한 클래스네임을 만들어서 scope를 지역적으로 제한합니다. 모듈화된 CSS를 번들러로 불러오면 다음과 같이 사용자가 정의했던 클래스네임과 고유한 클래스네임으로 이뤄진 객체가 반환됩니다.  

****![Cat.css(.meow{ color:orange; }) -> CSS Modules Compiler -> CSS(.cat_meow_J3xk{ color: orange; })](https://image.samsungsds.com/kr/insights//web_component_img01.jpg?queryString=20250214030334)CSS 모듈 컴파일 과정

이처럼 CSS 모듈은 동일 프로젝트 소스 안에 CSS 클래스 이름이 중복되어도 새로운 이름이 입혀져 중복 및 관리의 위험성이 적고 CSS 네이밍 규칙이 간소화 됩니다. 다만 한 곳에서 모든 것을 작성하지 않기 때문에 별도로 많은 CSS 파일을 만들어 관리해야 하는 단점이 있습니다. 
