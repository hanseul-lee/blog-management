---
title: '[JS연습] Darkmode 구현하기'
categories: [StudyLog, JS연습]
tags: [javascript]
thumbnailImage: js.png
date: 2020-12-10 20:04:01
---

<!-- more -->

[JS연습] Darkmode 구현

- 20-12-10 수업내용 복습 및 정리
  <!-- excerpt -->
  <!-- toc -->

# Darkmode 코드

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Light / Dark Mode - Toggle button</title>
    <link
      href="https://fonts.googleapis.com/css?family=Open+Sans:300,400"
      rel="stylesheet"
    />
    <link
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.8.2/css/all.min.css"
      rel="stylesheet"
    />
    <style>
      body {
        font-family: 'Open Sans';
        font-weight: 300;
        /* display: none; */
      }
      .title {
        color: #db5b33;
        font-weight: 300;
        text-align: center;
      }
      .toggle-button {
        position: relative;
        width: 100px;
        height: 50px;
        margin: 0 auto;
        cursor: pointer;
      }
      /* 토글 버튼 내부의 원 */
      .toggle-button > .toggle-button-switch {
        position: absolute;
        top: 2px;
        left: 2px;
        width: 46px;
        height: 46px;
        background-color: #fff;
        border-radius: 100%;
        transition: left 0.3s;
      }
      /* 토글 버튼의 바탕 */
      .toggle-button > .toggle-button-text {
        overflow: hidden;
        background-color: #3dbf87;
        border-radius: 25px;
        box-shadow: 2px 2px 5px 0 rgba(50, 50, 50, 0.75);
        transition: background-color 0.3s;
      }
      /* 토글 버튼의 텍스트 */
      .toggle-button > .toggle-button-text > .toggle-button-text-on,
      .toggle-button > .toggle-button-text > .toggle-button-text-off {
        float: left;
        width: 50%;
        line-height: 50px;
        color: #fff;
        text-align: center;
      }
      article {
        width: 960px;
        margin: 50px auto 0;
        font-size: 1.5em;
      }

      /* Dark Theme */
      body.dark {
        background-color: #232323;
      }
      body.dark .toggle-button > .toggle-button-switch {
        left: 52px;
      }
      body.dark .toggle-button > .toggle-button-text {
        background-color: #fc3164;
      }
      body.dark article {
        color: #fff;
      }
    </style>
  </head>
  <body>
    <h1 class="title">Light / Dark Mode - Toggle Button</h1>
    <div class="toggle-button">
      <div class="toggle-button-switch"></div>
      <div class="toggle-button-text">
        <div class="toggle-button-text-on">
          <i class="far fa-sun fa-lg"></i>
        </div>
        <div class="toggle-button-text-off">
          <i class="far fa-moon fa-lg"></i>
        </div>
      </div>
    </div>
    <article>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum optio ab
      porro magni in sunt ipsam, doloremque minima, itaque sapiente consequatur,
      repellat velit voluptatum accusantium aperiam. Nostrum sunt reprehenderit
      nemo!
    </article>
    <script>
      window.addEventListener('DOMContentLoded', () => {
        document.body.classList.toggle('dark', localStorage.getItem('theme'));
      });
      const $toggleButton = document.querySelector('.toggle-button');
      $toggleButton.onclick = () => {
        document.body.classList.toggle('dark');
        const theme = localStorage.getItem('theme');
        if (theme) {
          localStorage.removeItem('theme');
        } else {
          localStorage.setItem('theme', 'dark');
          document.body.classList.add('dark');
        }
      };
    </script>
  </body>
</html>
```

# 수업 내용 복습 및 정리

### 1. 코드 시작 전 세팅

```bash
  $ cd <project-folder>
  # package.json 생성
  $ npm init -y
  # install eslint & friends
  $ npm install eslint eslint-config-airbnb-base eslint-plugin-import eslint-plugin-html --save-dev

  # 이 후 프로젝트 루트에 .eslintrc.json 파일을 생성하고 필요에 따라 아래와 같이 룰셋을 변경
```

- [.eslintrc.json 룰셋 참고 - poiemaweb](https://poiemaweb.com/eslint#5-eslintrcjson)
- 만약 새로운 폴더 생성 시, package.json과 .eslintrc.json파일 복사 후 package.json의 name을 바꿔주고 `npm i` 해주면 됨.

<Br>

### 2. CSS vs JS

- CSS로 처리할 수 있다면 최대한 JS보단 CSS로 처리하려고 할 것
  왜냐하면 CSS의 반응 속도가 JS보다 더 빠르기 때문
- ex)
  Light모드와 Dark모드 변경사항을 CSS에 담고 JS에서는 class추가, 제거로 제어할 것
  ~~JS 내부에서 변경사항 일일히 적어주기~~ (X)

### 3. html body선택하기

- `document.querySelector('.body')`가 아니라 `document.body`로 하는 것이 더 간결하고 좋음

### 4. Local storage

- [MDN - LocalStrage 참고](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage) <br>+) 예제만 보지말고 위의 정의부터 꼼꼼히 다 살펴볼 것
- **HTTP vs Session**
  토글한 Darkmode 상태를 창을 닫고 나서 다시 접속할 때에도 기억하고 싶다면 Storage을 사용하자.
  (쿠키와 DB는 배보다 배꼽이 큰 격이므로 배제한다.)

  - HTTP 통신 : 단방향 (무전기) / Storage : 양방향
    - HTTP 통신의 특징은 Connectionless와 Stateless이다.
      - Connectionless(비연결지향)
        클라이언트에서 서버에 요청을 보내면 서버는 클라이언트에 응답을 하고 접속을 끊음.
      - Stateless(상태정보유지안함)
        HTTP통신은 요청을 응답하고 접속을 끊기 때문에 클라이언트 상태정보를 알 수 없음.
    - Storage
      localStorage의 데이터는 만료되지 않고 sessionStorage의 페이지를 닫을 때 사라진다.

(Reference : [MDN - LocalStrage](https://developer.mozilla.org/ko/docs/Web/API/Window/localStorage), [[WEB] 쿠키, 세션이란?](https://chrisjune-13837.medium.com/web-%EC%BF%A0%ED%82%A4-%EC%84%B8%EC%85%98%EC%9D%B4%EB%9E%80-aa6bcb327582))

<br>

### 5. 모든 페이지가 렌더링되고 다크 모드 적용되는 현상 해결하기

전역에 다크 모드 적용을 감지하고 이를 적용하는 코드를 작성하면 화면이 한 번 라이트 모드로 적용된 후 뒤이어 다크 모드로 변경된다. 이를 해결하기 위해 다음과 같은 2가지 방법을 사용할 수 있다.

1. `window.onload`
2. `window.DOMContentLoded`

1의 window.onload는 **DOMContentLoaded 이벤트가 발생한 이후, 브라우저의 모든 리소스(이미지, 폰트, script 등)의 로딩이 완료되었을 때** 발생하고, 2의 DOMContentLoaded는 **HTML 문서의 로드와 파싱이 완료되어 DOM 생성이 완료되었을 때** 발생한다. 따라서 결론만 말하자면 2의 DOMContentLoadedrk가 훨씬 빠르게 발생하고 유용하다.

먼저 `window.onload`를 사용하는 방법을 살펴보면 다음과 같다.

```js
// CSS
body { display: none; }

// JS
window.onload = () => {
  document.body.classList.toggle('dark', localStorage.getItem('theme'))
  document.body.style.display = 'block';
}
```

하지만 css에서 display:none을 해주지 않으면 기존처럼 렌더링이 모두 완료된 화면이 먼저 보이기 때문에 아래와 같이 `DOMContentLoaded`를 사용하는 것이 보다 간편하고 바람직하다. 참고로 DOMContentLoaded는 addEventListener를 통해서만 사용가능하다.

```js
window.addEventListener('DOMContentLoded', () => {
  document.body.classList.toggle('dark', localStorage.getItem('theme'));
});
```

<br>

### 6. 브라우저 기본 다크모드 감지하기

- [A Complete Guide to Dark Mode on the Web](https://css-tricks.com/a-complete-guide-to-dark-mode-on-the-web/)
  나아가 위 사이트를 통해 브라우저에서 기본으로 다크모드를 설정했을 때 이를 감지해 자동으로 적용하는 코드(`prefers-color-scheme`)에 대해 알아 볼 수 있다.
