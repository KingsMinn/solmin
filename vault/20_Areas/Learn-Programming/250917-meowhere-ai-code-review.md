---
title: 250917-meowhere-ai-code-review
date: 2025-09-17
updated: 2025-09-17
tags:
  - status/growing
  - type/memoir
published: false
aliases: []
---
# 협업 프로세스: AI를 활용한 코드 품질 관리
**문제 정의:** 팀 프로젝트에서 코드 컨벤션 위반이나 사소한 오타 같은 휴먼 에러는 협업 효율을 저해하는 원인 중 하나임. 코드 리뷰 과정에서 이를 자동으로 피드백해주는 시스템이 필요하다고 판단함.
- **해결 과정:**
    - **최종 선택:** `GitHub`내의 `Gemini Code Assist` 코드 리뷰 기능을 실험적으로 도입함. 팀의 코드 컨벤션과 규칙을 프롬프트로 제공하고, Pull Request 발생 시 자동으로 코드 품질을 검사하도록 설정함.
- **결과:** AI가 1차적인 코드 리뷰어 역할을 수행하여, 팀원들은 핵심 로직 구현에 집중할 수 있었음.