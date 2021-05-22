---
title: "[프로젝트] SweetyPie - Airbnb 클론코딩 TIL (1주차: 21.02.01 ~ 21.02.07)"
categories: [project]
tags: [Fastcampus, 프로젝트, SweetyPie]
thumbnailImage: logo.png
date: 2021-02-02 23:05:05
updated:
---

<!-- more -->
SweetyPie - Airbnb 클론코딩 TIL (1주차: 21.02.01 ~ 21.02.07)
- 전반적인 UI 작업
- git 초기화 및 project 셋팅

<!-- excerpt -->
<!-- toc -->

### 1일차 - 21.02.01 월요일

- git

  ```
  $ git flow init
  $ git flow feature start RoomDetail
  $ git checkout develop
  $ npm ci // npm i를 대체하면서 모든 걸 통합해주는 것
  $ nvm use 14.15.1
  ```

- index.css

  ```
  html {
    height: 100%;
    font-size: 10px;
  }
  @import url('https://cdn.jsdelivr.net/gh/moonspam/NanumBarunGothic@latest/nanumbarungothicsubset.css');
  *,
  *::before,
  *::after {
    box-sizing: border-box;
  }
  a {
    color: inherit;
    text-decoration: none;
  }
  .a11y-hidden,
  legend {
    overflow: hidden;
    position: absolute;
    clip: rect(0 0 0 0);
    /* IE 6,7 */
    clip: rect(0, 0, 0, 0);
    width: 1px;
    height: 1px;
    margin: -1px;
    border: 0;
    padding: 0;
  }
  .clearfix::after {
    content: '';
    display: block;
    clear: both;
  }
  ```

- git rebase

{% image center rebase.png %}

```
$ git pull origin develop --rebase
```

<br>

### 2일차 - 21.02.02 화요일

- roomDetail 컴포넌트 구현
  - Title.jsx
  - Photos.jsx - 구현중
  - Introduction.jsx
  - Icons.jsx
  - Description.jsx
  - Beds.jsx
  - CalendarDetail.jsx
  - Payment.jsx - 구현중

- 해야할 것
  1. Payment.jsx 구현 마무리
  2. react potals 이용한 팝업창 구현 & 이해하기 (https://ko.reactjs.org/docs/portals.html)
  3. roomDetail 나머지 아랫부분 구현 완성
  4. DB에서 받아온 accommodationDesc 개행 문자마다 개행 처리해주기
  5. 금액 세자리수마다 , 찍어주기
  6. 금액 소수점 버리기 적용하기

<br>

### 3일차 - 21.02.03 수요일

- 오늘 한 것

  1. 금액 소수점 버리기 적용하기 
     `Math.round()`: 인수로 전달된 숫자의 소수점 이하를 반올림한 정수 반환

     `toFixed()`: 숫자를 반올림하여 문자열로 반환, 인수 생략 시 기본값 0

     ```javascript
     // Number.prototype.toFixed
     
     const fees = (price * 0.07).toFixed();
     const fees = Math.round(price * 0.07)
     ```

  2. Payment에서 자식 엘리먼트들이 div에 종속되지 않는 문제 해결
  3. 동찬오빠와 전체 레이아웃 비율 통일
  4. PM 트러블 슈팅 (3시 ~ 3시 50분)

     - Github 이슈관리 체크
     - 문서화 
       꼭 문서화로 남길 것!! 
       Technical writer
       - github 해당 이슈 댓글 관리로 관리할 것 
       - README.md 템플릿으로 작성해놓고 실시간으로 추가하고 수정할 것
       - API관리 - 나중에 backend에서 만들어주면 POSTMAN으로 확인할 것

     - git commit - 컴포넌트 단위로 잘게 쪼개서 commit할 것
     - git - reset보다는 revert
     - git - rebase 지양할 것
     - 각 스프린트가 끝나면 메인 브랜치에 완성된 프로덕트 커밋 찍을 것
       `$ git flow release start(finish) {version_name}`

     - 페이스를 꾸준히 유지할 것 - 정해진 시간에 자고, 일어난 이후에 계속 키보드에 손을 잡고 있을 것

  5. git revert
     이전에 작업했던 기록들을 `git add .`로 처리한 걸 다시 컴포넌트 별로 commit하기 위해 git revert를 사용했다.

     ```bash
     $ git reflog // 이전 기록 확인
     $ git revert HEAD@{번호} // 돌아가고 싶은 번호로 revert
     ```

  6. git revert 취소

     ```bash
     $ git reflog // 이전 기록 확인
     $ git reset --hard HEAD@{번호} // 원하는 곳으로 이동
     ```

    {% image center revert.png %}

  7. Mark 강사님 트러블 슈팅 (19시 ~ 19시 30분)


<br>

### 4일차 - 21.02.04 목요일

- roomDetail 컴포넌트 구현
  - Map
  - Host
  - ThingsToKnow
  - Payment - 금액 소수점 3째자리 콤마(,)찍기 함수 추가

  ```javascript
    function numberWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
    }
  ```

- ReviewProfile - 날짜 년, 월만 나오게 하기

  ```javascript
  const createdDate = '2021 - 02 - 06'
  {createdDate.split(' -')[0]}년 {createdDate.split(' -')[1]}월
  ```

- 해야할 것
  - Map, Calendar - API 연결
  - ThingsToKnow - 링크에 SVG 화살표 넣고 팝업창 구현
  - Payment - 날짜, 인원 팝업 만들기 & 연결
  - DB data 연동 제대로 변수 넣었는지 확인

<br>

### 5일차 - 21.02.05 금요일

- github merge로 1주차 스프린트 

  ```bash
  $ git flow feature finish RoomDetail
  $ git push origin develop
  내 레포에서 pull request
  
  이후
  $ git remote add upstream 주소
  $ git pull upstream develop
  $ npm ci
  ```

- github rebase 관련 이슈

- 트러블슈팅 - Mark강사님 (18:00 ~ 18:50)
  - DOM에 접근해 data를 쓰려면 -> dataset 사용해볼 것
  - 컴포넌트에도 ref를 달 수 있음 -> forwardRef

<br>

### 6,7일차 - 21.02.06, 21.02.07 토, 일요일

- google map API 연습
- 팝업 UI 구현중
- 팀 회식❤