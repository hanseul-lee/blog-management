---
title: "[React] 컴포넌트 스타일링"
categories: [StudyLog, React]
tags: [React]
thumbnailImage: React.jpg
date: 2020-12-20 09:49:03
comments: true
---

<!-- more -->
리액트는 Vue, Angular와는 다르게 스타일이 스코핑되지 않는다는 문제점을 가지고 있다. 따라서 이를 해결하기 위해 리액트에서 컴포넌트를 스타일링하는 다양한 방식을 알아보자.
<!-- excerpt -->


리액트는 Vue, Angular와는 다르게 스타일이 스코핑되지 않는다는 문제점을 가지고 있다. 즉, CSS가 캡슐화되지 않아 예기치 못한 문제가 발생하기 쉽고 이를 자동화시켜주기 위해 다양한 방법들이 제시되었다. 리액트에서 컴포넌트를 스타일링하는 방법으로는 크게 다음과 같은 4가지로 나눌 수 있다.

<br>

1. **일반 CSS**
2. **Sass**
3. **CSS Module**
4. **styled-components**

# 1. 일반 CSS

일반 CSS로 CSS 스타일링을 하는 방법은 2가지가 있다.

<br>

1. 네이밍 규칙 이용
BEM과 같이 이름을 지을 때 일종의 규칙을 준수하여 작성

2. CSS Selector
CSS class의 상속 관계를 이용해 스타일 적용
```css
/* App.css */

/* 기존 */
.App-logo {
  color: #fff;
}

/* CSS Selecotr 사용 */
.App .logo {
  color: #fff;
}
```

<br>

# 2. Sass
**Sass**(Syntactically Awesome StyleSheets)는 CSS 전처리기로 CSS의 한계와 단점을 보완하여 보다 가독성이 높고 코드의 재사용에 유리한 CSS를 생성하기 위해 탄생했다.

- Sass에서는 두 가지 확장자 .scss와 .sass를 지원하는데 기존 CSS와 작성방법이 비슷한 .scss를 사용하는 것을 권장한다.
- 스타일 코드를 계층적으로 구조화해 가독성이 높고, 스타일 코드의 재활용성을 높여주거나 설정을 커스터마이징하는 다양한 기능 및 라이브러리를 제공한다는 장점 또한 지니고 있다.

먼저 node-sass 라이브러리를 설치한다.
```bash
$ npm install node-sass
$ npm start
```

이 후 .scss 파일에 sass문법을 적용해 스타일링을 해가면 기존 CSS를 사용하는 것보다 훨씬 가독성 좋은 스타일링을 구현할 수 있다.

```scss
/* App.scss */

.App {
  text-align: center;

  .logo {
    height: 40vmin;
    pointer-events: none;
  }
}
```

<br>

# 3. CSS Module

- 클래스 이름을 [filename]\_[classname]\_\_[hash] 형태로 자동 변환해 이름의 중첩을 방지.
- 자동으로 변환되므로 클래스 네이밍 시 BEM과 같이 복잡하게 규칙 정하지 않고 마음대로 사용 가능함.
- `.module.css` 확장자로 파일 저장 시 CSS Module 적용됨.

### classnames
- class를 조건부로 설정할 때 유용한 라이브러리



<br>

# 4. styled-components
- 자바스크립트 파일 안에 스타일을 선언하는 방식(CSS-in-JS)
- 스타일을 선언하며 바로 컴포넌트 생성 가능
- Tagged 템플릿 리터럴

<br>

---
**Reference**
- 김민준, 리액트를 다루는 기술
- [poiemaweb.com/](poiemaweb.com/)