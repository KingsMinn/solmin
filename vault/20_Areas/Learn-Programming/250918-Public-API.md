---
title: Public API
date: 2025-09-18
updated: 2025-09-18
tags:
  - status/growing
  - type/web
published: false
aliases: []
---
# Public API
각 슬라이스와 세그먼트에는 퍼블릭 API가 있습니다. 퍼블릭 API는 index.js 또는 index.ts 파일로 표현되며, 이를 통해 슬라이스나 세그먼트에서 필요한 기능만 외부로 추출하고 불필요한 기능은 격리할 수 있습니다. 인덱스 파일은 진입점 역할을 합니다.

**공개 API 규칙**:

- **애플리케이션 슬라이스와 세그먼트는 공개 API 인덱스 파일에 정의된 슬라이스의 기능과 구성 요소만 사용합니다.**
- **공개 API에 정의되지 않은 슬라이스나 세그먼트의 내부 부분은 격리된 것으로 간주되며 슬라이스나 세그먼트 자체 내에서만 액세스가 가능합니다**.

공개 API는 가져오기 및 내보내기 작업을 간소화하므로 애플리케이션을 변경할 때 코드의 모든 곳에서 가져오기를 변경할 필요가 없습니다.

좋은 공개 API는 다른 코드를 사용하고 통합하는 것을 편리하고 신뢰할 수 있는 슬라이스로 만듭니다. 이는 다음 세 가지 목표를 설정하여 달성할 수 있습니다.

1. 나머지 애플리케이션은 리팩토링과 같은 슬라이스의 구조적 변경으로부터 보호되어야 합니다.
2. 슬라이스 동작의 이전 기대치를 깨는 상당한 변경 사항은 공개 API의 변경을 야기해야 합니다.
3. 슬라이스의 필요한 부분만 노출되어야 합니다.

💡**Cross Import**

일반적으로 이는 [레이어의 가져오기 규칙](https://feature-sliced.design/docs/reference/layers#import-rule-on-layers) 에 의해 금지되지만 , 종종 cross import에 대한 합법적인 이유가 있습니다. 이러한 목적을 위해 @x-notation이라고도 알려진 특별한 종류의 공개 API가 있습니다 . 엔티티 A와 B가 있고 엔티티 B가 엔티티 A에서 가져와야 하는 경우 엔티티 A는 엔티티 B에 대한 별도의 공개 API를 선언할 수 있습니다.

import type { EntityA } from "entities/A/@x/B";

내부 코드만을 위한 특별한 공개 API를 entities/A/@x에 만들어야합니다. cross import를 최소한으로 유지하고 **이 표기법은 엔터티 계층에서만 사용하세요** . 이 경우 교차 수입을 제거하는 것이 비합리적인 경우가 많습니다.

💡 인덱스 파일(Barrel 파일)을 사용하면 생기는 문제

1. **순환 참조**

세 개의 파일 , fileA.js, fileB.js, 이 fileC.js서로를 원형으로 가져오고 있습니다. 이러한 상황은 번들러가 처리하기 어려운 경우가 많으며, 어떤 경우에는 디버깅하기 어려운 런타임 오류가 발생할 수도 있습니다. 순환 임포트는 인덱스 파일 없이도 발생할 수 있지만, 인덱스 파일이 있으면 실수로 순환 임포트를 생성할 수 있는 명확한 기회가 있습니다.

```
// HomePage.jsx
import { loadUserStatistics } from "../"; // importing from pages/home/index.js
```

```
// index.js
export { HomePage } from "./ui/HomePage";
export { loadUserStatistics } from "./api/loadUserStatistics";
```

위와 같은 경우 index.js는 HomePage.jsx를 import하지만 HomePage.js는 index.js를 import하기 때문에 순환참조가 발생합니다.

이 문제를 방지하려면 다음 두 가지 원칙을 고려하세요. 두 개의 파일이 있고, 한 파일이 다른 파일에서 가져오는 경우:

- 동일한 슬라이스에 있다면, **반드시** 전체경로를 갖는 상대경로를 사용하여 import합니다. (index.js에서 가져오기 금지)
- 서로 다른 슬라이스에 있는 경우 항상 alias와 같은 절대 경로를 사용하여 import 합니다.

