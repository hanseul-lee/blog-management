---
title: "[React] 리액트 라우터로 SPA 개발하기"
categories: [StudyLog, React]
tags: [React]
thumbnailImage: React.jpg
date: 2021-01-05 13:33:09
updated:
---

<!-- more -->

<!-- excerpt -->
<!-- toc -->

### 프로젝트 생성 및 라이브러리 설치

```jsx
$ npx create-react-app router-tutorial
$ cd router-tutorial
$ npm i react-router-dom
```

### 라우터 적용 - BrowserRouter로 감싸기

```jsx
// src/index.js
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
	<BrowserRouter>
		<App />
	</BrowserRouter>
	documnet.getElementById('root');
)
```

### **Route 컴포넌트로 특정 주소에 연결**

정확한 path만을 명시하려면 `exact`를 붙여준다.

```jsx
<Route path="주소규칙" component={보여줄 컴포넌트} />

<Route path="/profile" exact component={Profile} />
```

### Link

`<a>` 태그와 비슷하지만 페이지 전환되지 X

```jsx
<Link to="주소">내용</Link>

<Link to="/profile">프로필</Link>
```

### URL parameter와 query

페이지에 유동적인 값을 전달할 때 사용

- **parameter**
특정 아이디나 이름을 사용하여 조회할 때
ex.  `/profile/lemon`

<br>

- **query**
특정 키워드를 검색하거나 페이지에 필요한 옵션을 전달할 때
ex. `/about?details=ture` <br>
location의 search값에서 조회 가능
search에서 특정 값을 읽어오려면 문자열 → 객체 형태로 변환해야 함
쿼리 문자열을 객체로 변환할 때 qs 라이브러리 사용 `npm install qs`

**쿼리의 파싱 결과값**은 항상 **문자열**이라는 것에 주의할 것 (숫자는 parseInt사용)

```jsx
import qs form 'qs';

const query = qs.parse(location.search, {
  ignoreQueryPrefix: true                  // 문자열 맨 앞의 ? 생략
})
```

<br>

### 서브라우트(sub Route)

라우트 내부에 또 라우트를 정의하는 것

<br>

### withRouter

HoC(High-order Component)로 라우트로 사용된 컴포넌트가 아니더라도 history, location, match에 접근가능하게 해 줌

```jsx
import { withRouter } from 'react-router-dom';
```

<br>

### Switch

여러 Route를 감싸서 그 중 일치하는 단 하나의 라우트만을 렌더링
Not Found 페이지도 구현 가능

<br>

---
**Reference**
- 김민준, 리액트를 다루는 기술
