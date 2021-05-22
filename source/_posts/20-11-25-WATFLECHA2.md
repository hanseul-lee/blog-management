---
title: "[프로젝트] WATFLICHA - 2차 구현 TIL (1주차 : 20.11.23 ~ 20.11.29)"
categories: [project]
tags: [프로젝트, WATFLICHA, Fastcampus]
thumbnailImage: WATFLICHA-logo.png
date: 2020-11-25 11:19:35
---

<!-- more -->
[미니 프로젝트] WATFLICHA - 2차 구현 TIL
( 2차 구현 1주차: 20.11.23 ~ 20.11.29 )
<!-- excerpt -->

# WATFLICHA 2차 구현 TIL
( 2차 구현 1주차: 20.11.23 ~ 20.11.29 )

## 20-11-23 월요일
- 2차 구현 계획 세우기
  1. search 페이지 더보기 구현
  2. genre 페이지 구현 및 main 과 연동
  3. 발표 당시 피드백 내용 고치기(회원가입 및 회원수정)
  4. 기타 자잘한 CSS 및 코드 수정

## 20-11-23 화요일

- **페이지 구현 내용**
  1. serch 페이지 구현 방향성 설정
  2. 2의 genre 페이지 구현 및 main 과 연동을 위해 모듈 사용을 시도해봤지만 계속해서 오류가 나왔다. 모듈 사용이 익숙하지 않고 전역이 아닌 비동기 코드로 모듈을 export했기 때문이라고 생각했는데 해결 방법을 최대한 더 찾기로 했다. 만약 못 찾으면 그 대신 최후의 수단으로 localStorage를 사용하기로 했다.

## 20-11-23 수요일

- **git organization 생성**
기존 git fork해서 사용하는 방식으로는 내 repo에 commit로그가 찍히지 않는 단점이 있었다. 따라서 2차 구현을 위해 더 쉽게 merge하고 commit로그 반영도 함께 하기 위해 [git organization(WATFLECHA)](https://github.com/Fastcampus-project-WATFLECHA/WATFLECHA)을 생성했다.

<br>

- **페이지 구현 내용**
1. search 페이지 더보기 구현
  - 버튼 클릭 시 i++ 되며 API의 다음 페이지 렌더링
  - 만약 API의 배열길이가 20이 아니면, 즉 마지막 페이지이면 버튼 display = none
{% image center 더보기.png 600px search 페이지 더보기 기능%}
<br>

2. main의 nav 클릭 시 장르 id를 genre로 연동
main의 nav 클릭 시 장르 id를 가진 url 쿼리를 생성하고 이를 genre에서 가져와 API에 연동해 렌더링 하도록 구현<br>
main과 genre를 연동해 정보를 주고받을 수 있도록 하는 방법을 찾느라 정말 애를 많이 먹었다. 
크게 다음과 같이 3가지 방법을 생각했었는데 모두 조금씩 걸리는 부분이 있었다.
  1) localStorage 사용 
  but localStorage는 사용자 설정을 영구적으로 기억해야 할 필요가 있을 때(로그인 정보 등) 사용하는 목적이 크므로 보류
  2) DB 사용 
  but 페이지 이동을 위해 굳이 DB를 낭비시키고 싶지 않음
  3) 모듈로 만들어 import, export 사용 
  but 모듈을 비동기로 사용하는 방법에서 막힘

따라서 금용님께 조언을 얻어 url의 query를 가져와 이용하는 방법을 도입하기로 했다.
먼저 각 main.html과 genre.html의 장르 메뉴의 a 태그에 다음과 같이 장르 API에서 추출한 고유 id를 쿼리로 넣어주었다.

```html
<ul class="genre-list">
  <li id="action"><a href="./genre.html?id=28">액션</a></li>
  <li id="animation"><a href="./genre.html?id=16">애니메이션</a></li>
  <li id="romance"><a href="./genre.html?id=10749">로맨스</a></li>
  <li id="thriller"><a href="./genre.html?id=53">스릴러</a></li>
  <li id="sf"><a href="./genre.html?id=878">SF</a></li>
</ul>
```
그 후 genre.js에서 다음과 같이 쿼리의 id정보를 빼내는 방식을 사용해 이를 API에 넣어주었다. [MDN의 URL](https://developer.mozilla.org/ko/docs/Web/API/URL)을 살펴보면 다음과 같이 url 내 쿼리에 접근할 수 있는 방법이 나와있다.

```js
// https://some.site/?id=123
const parsedUrl = new URL(window.location.href);
console.log(parsedUrl.searchParams.get("id")); // "123"
```
- `new url()` : URL() 생성자는 매개변수로 제공한 URL을 나타내는 새로운 URL 객체를 반환
- `URL.searchParams` : URL 인터페이스의 searchParams 읽기 전용 속성은 URL 내의 GET 디코딩 된 쿼리 매개변수에 접근할 수 있는 URLSearchParams 객체를 반환

<br>

이를 참고해 다음과 같이 코드를 작성했다.

```js
const parsedUrl = new URL(window.location.href);
const urlId = parsedUrl.searchParams.get("id");

(async () => {
  const resDiscover = await fetch(`https://api.themoviedb.org/3/discover/movie?api_key=${api_key}&language=ko&sort_by=popularity.desc&include_adult=false&include_video=false&page=1&with_genres=${urlId}`);
  const { results: movies } = await resDiscover.json();
// 이하 생략
})();
```

3. login 페이지 아이디 저장 버튼 HTML, CSS 수정
버튼 크기 확대 및 label과 id 연동해 함께 클릭하도록 수정
4. join 페이지 취소하기 버튼 CSS 수정
회원가입과 취소하기 버튼 색 다르게 구분하도록 수정
회원가입 세부조건 추가는 수정중

{% image center 회원가입버튼.png 300px 회원가입 취소버튼과 구분 %}

<br>

## 20-11-23 목요일

- **페이지 구현 내용**
  1. 회원가입 페이지 리팩토링 진행중

- 장르 페이지 페이지네이션 회의 with 어진
- genre.js 암묵적 전역 이해

## 20-11-23 금요일

- **페이지 구현 내용**
  1. 회원가입 페이지 리팩토링 진행중
input 창 focusout 됐을 때 이름, 아이디, 비밀번호 및 비밀번호 확인 조건 충족여부 확인하는 함수 구현

## 20-11-23 토요일

- **페이지 구현 내용**
  1. 회원가입 페이지 리팩토링 완성
어제 만든 input창 이벤트를 input창 각각에 주는 것이 아니라 반복문을 통해 한번에 조건 충족시킬 수 있도록 깔끔하게 바꿈 

{% image center before.jpg 1000px input 리팩토링 전과 후 코드 비교 %}

  리팩토링 전 : onsubmit, 즉 회원가입 버튼 눌렀을 때만 조건 충족 여부 검사 후 alert이 보여짐
  리팩토링 진행중 : onblur 시, 실시간으로 각 input마다 조건 충족 여부 검사후 alert이 보여짐
  리팩토링 후 : onblur 시, 실시간으로 모든 input 반복문으로 순회 후 조건 충족 여부 검사

<br>

  2. signUp과 modiIf 페이지 CSS 통일

<br>

- 새로 배운 것
1. 정규표현식으로 아이디 및 비밀번호 충족 시키는 조건 만들기
  ```js
  // 아이디 조건확인 및 중복확인
  const checkValidId = async (input) => {
    try {
      // 조건확인
      // 정규표현식 조건 : 4자이상 영어와 숫자
      const regId = /^[A-Za-z0-9+]{4,15}$/g;
      if(!regId.test(input.value)) {
        showErrorInput(input);
        input.nextElementSibling.textContent = '아이디는 4~12자 이상, 영어와 숫자로 입력해 주세요.';
        return;
      } else {
        showCorrectInput(input);
      }
  // 이하 생략
  ```
2. querySelectorAll로 지정된 요소를 순회하며 조건 만족 시켜주기
  ```JS
  const $signUpInput = document.querySelectorAll('.signUp-input');

  [...$signUpInput].forEach(input => {
    input.onblur = () => {
      checkblank(input);
      if (input.id === 'id') checkValidId(input);
      if (input.id === 'pw') checkValidPw(input);
      if (input.id === 'repw') checkValidRepw(input);
    }
  });
  ```
3. option의 value와 text 값 가져오기
  ```JS
  if ($preference.options[$preference.selectedIndex].value === 'none') {
  $preference.nextElementSibling.textContent = '선호 장르를 선택해 주세요';
  ```
4. form 요소 데이터를 한꺼번에 DB로 전송하기
  ```js
  const formData = new FormData($signUpForm);
  const signUp = {};

  for (const pair of formData) {
    signUp[pair[0]] = pair[1];
  }

  fetch('/users', {
    method:'POST',
    headers: { 'content-Type': 'application/json'},
    body: JSON.stringify(signUp)
  });
  ```
<br>

## 20-11-29 일요일

- **페이지 구현 내용**
  1. 정보수정 페이지 리팩토링 시작
signUp과 modiIf 페이지 CSS통일
