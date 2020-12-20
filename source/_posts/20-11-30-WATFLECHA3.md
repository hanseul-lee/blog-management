---
title: "[미니 프로젝트] WATFLICHA - 2차 구현 TIL (2주차 : 20.11.30 ~ 20.12.06)"
categories: [project]
tags: [프로젝트, WATFLICHA, Fastcampus]
thumbnailImage: WATFLICHA-logo.png
date: 2020-12-03 01:21:23
---

<!-- more -->
[미니 프로젝트] WATFLICHA - 2차 구현 TIL
( 2차 구현 2주차: 20.11.30 ~ 20.12.06 )
<!-- excerpt -->

# WATFLICHA 2차 구현 TIL
( 2차 구현 2주차: 20.11.30 ~ 20.12.06 )


## 20-11-30 월요일

- **페이지 구현 내용**
  1. 정보수정 페이지 리팩토링 진행중
  - 기본적인 레이아웃 및 이벤트 위임으로 focusout 됐을 때 input창 border 색 변화 틀 구현
  - 수정 활성화 연필 아이콘 추가
  ```js
  $penIcon.onclick = e => {
    $modiIfName.toggleAttribute('disabled');
  }
  ```
  - 이름 수정 기능 구현 완료
  - 비밀번호 수정 기능 구현중

<Br>

## 20-12-02 수요일

 - **페이지 구현 내용**
  1. 정보수정 페이지 리팩토링 진행중
  - submit 버튼 클릭 이벤트 완성
    - 에러 존재하는 지 확인
    - 에러 없을 시 localStorage로 바뀐 정보 보내기(이름, 장르)
    - 에러 없을 시 DB로 바뀐 정보 보내기(이름, 비밀번호, 장르)
  - 비밀번호 변경 input 디버깅중

<br>

### **오늘의 배운점**


1. input창에 스페이스 바 입력 방지
  trim()을 써서 거르는 것보다 아예 입력을 막는 방법이 더 유용하다는 것을 배웠다.
  ```js
  child.onkeydown = e => {
    const kcode = e.keyCode;
    if(kcode === 32) return false;
  }
  ```

<br>

  2. key값으로 매개변수 넣고 싶을 때 점 표현식이 아닌 대괄호 표현식으로!!
  key 매개변수에는 '문자'로 넣어주기
  ```js
  showChangedInput(name, input)  // (X)
  showChangedInput('name', input) // (O)

  const showChangedInput = (key, input) => {
    if (input.value !== user[key]) {
      showGreenInput(input);
     // 이하 생략
  }

  showChahngedInput('name', input)
  ```

<br>

  3. fetch가 onfocusout 안에 있으면 focusout 됐을 때 계속해서 호출되므로 전역이나 조건을 주고 한번만 불러주고 변수 가져와 사용하기!

<br>

  4. 화살표 함수에서 return이 없으면 {} 로 꼭 묶어주기!!
  예를 들어, 아래처럼 반복문 안에 if문 넣어주고 싶을 때 =>(화살표 함수) 뒤 {}를 안 해줘서 계속 에러가 나왔었다.
  ```js
  [...$pw].forEach(input => {
      if (input.classList.contains('changedColor')) {
        input.classList.remove('changedColor');
        input.nextElementSibling.textContent = ''
      } else if (input.classList.contains('errorColor')) {
        input.classList.remove('errorColor');
        input.nextElementSibling.textContent = ''
      }
  ```

<br>

  5. 값 변경 이벤트 ([poiemaweb 참고](https://poiemaweb.com/fastcampus/event#25-%EA%B0%92-%EB%B3%80%EA%B2%BD-%EC%9D%B4%EB%B2%A4%ED%8A%B8))
  {% image center 값변경이벤트.jpg %}

  - oninput :input(text, checkbox, radio), select, textarea 요소의 값이 입력되었을 때.
  - onchange: input(text, checkbox, radio), select, textarea 요소의 값이 변경되었을 때.

<br>

  6. 같은 form 밑의 자식 구조로 되어있지 않을 때
  `[...$iconInput.children]`이 아니라 `div.querySelector('input')`으로! 
  ```js
  if ([...$modiIfForm.children].find(input => input.classList.contains('errorColor')) 
  || [...$iconInput].find(div => div.querySelector('input').classList.contains('errorColor'))
  ```
  
<br>

  7. 뒤로가기
  
  ```js
  $cancleBt.onclick = () => {
    window.history.back(); // 방법1
    window.history.go(-1); // 방법2
  }
  ```

<br>

  8. 깔끔하게 만드는 것에 목숨걸지 말 것
일단 완성한 다음에 리팩토링하는 게 더 중요하다


## 20-12-03 목요일

## 20-12-04 금요일

## 20-12-05 & 20-12-06 토,일요일