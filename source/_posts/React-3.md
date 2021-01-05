---
title: "[React] 컴포넌트"
categories: [StudyLog, React]
tags: [React]
thumbnailImage: React.jpg
date: 2021-01-01 13:34:02
updated:
---

<!-- more -->
리액트는 컴포넌트를 기반으로 데이터를 주고 받는다. 컴포넌트는 일종의 UI조각으로 컴포넌트의 생성과 외부에서 정보를 주는 props, 컴포넌트 내부의 변경할 수 있는 state에 대해 알아보자.
<!-- excerpt -->
<!-- toc -->

# 컴포넌트(Component)
: 일종의 UI 조각
<br>

{% image center 1.png component %}

<br>

- 컴포넌트 생성 방법 : ① 함수, ② class
현재는 함수형과 Hook을 함께 사용할 것을 권장함
- **컴포넌트 이름은 항상 대문자로 시작**
- class 형태 컴포넌트에서는 `render`함수와 내부에서 JSX를 return해줘야 함
- `ReactDOM.render(element, 루트노드)` : 컴포넌트를 페이지에 렌더링
(브라우저 상에서 리액트 컴포넌트를 보여줄 때)

### props

- 컴포넌트 외부에서 컴포넌트에게 주는 데이터
부모 컴포넌트가 자식 컴포넌트에게 주는 값 (읽기전용)
- {props}**.defaultProps** : props 기본값 설정
- {props}**.children:** 컴포넌트 태그 사이 내용  ex. `<Hello>리액트</Hello>`
- {props}.**propTypes:** props의 필수 타입 지정
- {props}.**isRequired :** 필수 propTypes 설정

<br>

```jsx
import PropTypes from 'prop-types';

MyComponent.propTypes = {
  name: PropTypes.string,
  favoriteNumber: PropTypes.number.isRequired
}
```

- 클래스형 컴포넌트에서는 render함수에서 this.props로 사용

<br>

### state

- 컴포넌트 내부에서 변경할 수 있는 데이터
- 동적인 데이터를 다룰 때 사용

- `setState(), useState()` : state 값 변경 시 사용
(주의) 직접 state값을 변경해주면 안됨! 반드시 세터함수 이용

<br>

{% image center 2.png 600px props와 state %}
{% image center 3.png 600px render함수 %}
<br>

---
**Reference**
- 김민준, 리액트를 다루는 기술
- [https://slides.com/woongjae](https://slides.com/woongjae)