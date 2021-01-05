---
title: "[React] JSX 문법"
categories: [StudyLog, React]
tags: [React]
thumbnailImage: React.jpg
date: 2020-12-18 01:01:01
---

<!-- more -->
리액트에서 JSX 문법을 사용해 XML형태 코드를 Javascript로 손쉽게 변환할 수 있다. JSX 문법의 규칙에 대해 자세히 알아보자.
<!-- excerpt -->

**JSX(Javascript XML)** : 리액트에서 XML형태 코드를 Javascript로 변환
<br>

- 최상위 요소는 하나만 존재해야 함
- 최상위 요소 리턴하는 경우, () 로 감싸야 함
- 태그는 꼭 닫아야 하고,  자식요소가 없을 시 self closing을 사용함.
  - `<p>Hello, World</p>`
  - `<br />`
- 2개 이상의 엘리먼트는 무조건 하나의 태그로 감싸야 함
만약, 불필요한 div 생성 시, Fragment 사용(태그 이름 없이 작성)
```jsx
<>
  <div>2개 이상의</div>
  <p>태그는 감싸자</p>
</>
```
<br>

- JSX내부에서 Javascript 변수를 표현할 땐 {}로 감싸야 함
```jsx
const name = '이렇게';
return <div>JavaScript 값을 보여줄 땐, {name}</div>
```
<br>

- 인라인 style은 객체 형태로 작성하고, camelCase로 네이밍 함.
- class를 설정 할 때는 `class`가 아닌 `className`으로 설정해야 함.
```jsx
const style = {
  background: 'grey';
}
return (
  <div style={style}>
    <div className="my-style">
      style과 className
    </div>
  </div>
)
```
<br>

- JSX 내부 주석 : `{/* 내부 주석은 이렇게*/}`
태그 내부 주석 : `// 태그 내 주석은 이렇게`


---
**Reference**
- 김민준, 리액트를 다루는 기술
