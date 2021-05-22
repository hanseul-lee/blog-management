---
title: "[프로젝트] SweetyPie - Airbnb 클론코딩 TIL (3주차: 21.02.15 ~ 21.02.21)"
categories: [project]
tags: [Fastcampus, 프로젝트, SweetyPie]
thumbnailImage: logo.png
date: 2021-02-15 23:26:21
updated:
---

<!-- more -->
SweetyPie - Airbnb 클론코딩 TIL (3주차: 21.02.15 ~ 21.02.21)
- 21.02.17(수) ~ 21.02.27(일) : 홍대 에어비앤비 합숙
- api 연동 및 개별 페이지 통합

<!-- excerpt -->
<!-- toc -->

## 21.02.17(수) ~ 21.02.27(일) : 홍대 에어비앤비 합숙

### 1일차 - 21.02.15 월요일

- 오늘 한 것
    - Payment에서 RoomDetailGuestEditPopup 구현
        - UI 구현
        - 성인, 어린이, 유아 클릭 시, url query에 변경사항 실시간 반영 로직 구현
        (참고: [https://www.fbchandra.com/developers/add-remove-query-string-url-without-reloading-page](https://www.fbchandra.com/developers/add-remove-query-string-url-without-reloading-page) )
- 오늘의 이슈
  - 팀 로고 정하기!
    백엔드 재복님이 갑자기 너무 예쁜 디자인의 로고 5개를 만들어서 투표에 올리셨다. 각자 원하는 걸 투표했는데 정말 센스있고 예뻐서 감동받았다. 최종 후보에 오른 5가지 중에 가장 인기가 많았던 아래 로고가 우리 SweetyPie의 로고로 뽑혔다.
    {% image center logo_PK.png %}

<br>

### 2일차 - 21.02.16 화요일

- 오늘 한 것
    - Payment에서 RoomDetailGuestEditPopup에서 totalGuest 계산 및 url 반영 구현
        - 문제점 : setState가 비동기로 작동하므로 url에 반영이 한 박자 늦어짐.
        => totoalGuest를 직접 url에 반영해 빼오지 말고, 필요한 부분에서 url의 adult, child, infant를 더해서 계산할 것

<br>

- 우영강사님 트러블 슈팅(14:00 ~ 14:50)
    - release 단계에서 하는 것 - ex. gulf를 통한 테스트 자동화
    - commit을 잘게 잘라서 할 것
    이는 나중에 회사에서 업무 시, 인사 고과 평가에서도 좋음
    git organization의 Insights -> Contributions에 들어가면 아래와 같이 각 팀원 별 commit과 같은 기여도를 한 눈에 파악할 수 있다.

  {% image center commit.png 900px git organization -> Insights -> Contributions %}

    - release finish할때 commit창 3번 떠야 함
    - pull request의 이슈close는 미처 파악하지 못한 이슈를 정리, 이슈에 대한 명시 용도로 사용하고 git project에서 실시간 진행 사항을 반영할 것
    - 저번 hard reset을 통한 교훈을 얻은 것으로 우리 프로젝트의 역할은 다했다
        => 실제 프로젝트에서 탕비실에 갈 일은 없겠구나~ 감사하게 생각할 것~
    - 내 주언어가 JS일때 node.js로 코테가 진행될 수 있으므로 조금씩 다른 부분이 있을 때 당황할 수 있으므로 잘 준비해 놓아야 함.
    - 중간발표 준비
      - 중간발표.md로 간략히 정리
      - 백엔드와 융화되어 발표할 수 있도록 준비할 것

<br>

### 3일차 - 21.02.17 수요일

- 오늘 한 것
    - 네비게이션 Header 스크롤 이동 기능 구현
    이렇게 컴포넌트에 id넣는게 아니라 컴포넌트 내부 최상위 div에 적용할 것!!!
    {% image center id.png 600px %}

<br>

- 중간 발표 준비
    - [중간발표.md](https://github.com/hanseul-lee/SweetyPie_Frontend/blob/main/%EC%A4%91%EA%B0%84%EB%B0%9C%ED%91%9C.md) 파일 템플릿 생성 및 내용 작성
    - 백엔드와 각 페이지 별 기능 및 api 설명 데모 시연 연습
<br>
- 중간발표 피드백
  - mark 강사님
    - 완성도는 프론트엔드에서 나옴 
    따라서 앞으로는 최대한 디테일을 올리는 방향으로, 시간 여유롭다고 다른 걸 추가하지 말 것
  - 백엔드 강사님
    - 팀 로고 정한 게 너무 좋음
      책같은 거 쓸 때 동물 고르는 게 더 중요
      ex) 조시룽 - 책 1년동안 쓰면 동물 고르는 건 2년ㅋㅋㅋ

<br>

### 4일차 - 21.02.18 목요일

- 오늘 할 것
    - [x]  Review - 리뷰 모달 완성
    - [x]  Calendar - 지우기 기능 구현
    - [x]  Calendar - url의 checkIn, checkOut 가져와 표시 기능 구현
    - [ ]  Payment - 달력모달 넣기
    - [ ]  Payment - 달력모달과 CalendarDetail 컴포넌트 연동
    - [x]  Payment - 1박 당 7%로 수수료 변경
    - [ ]  ~~GuestPopup - 인원수에 따라 버튼 조정~~
    - [x]  Payment - 입력된 값에 따라 버튼 조정

    ---

    - [ ]  -박 나오는 것 고치기
    - [x]  예약하기 클릭 시 url에 정보 담아 예약페이지로 이동
    - [x]  이슈 템플릿 만들기

- 오늘 배운 것
  - null의 type은 object
  ```js
  typeof null  //object
  ```

  - url 쿼리 쉽게 가져다 쓰기
    ```js
    let url = new URL(window.location.href);
    url.searchParams.delete('checkIn');
    url.searchParams.delete('checkOut');
    history.push(url.search);
    ```
<br>

- 오늘의 이슈
    - 우리 팀 커버곡 : Pink Sweat$ - At My Worst
    오늘 영서가 튼 노래가 좋아서 이곡 뭐야? 했더니 저번에도 내가 좋아서 물어봤던 노래였다. 재민이도 좋아하는 노래고 가사도 너무 달달해서 바로 우리팀 SweetyPie 커버곡으로 정했다. 이제 로고에 이어 노래까지 완성~
{% image center music2.png 700px 우리 팀 단체로 프로필 뮤직 맞춘 모습 %}


### 5일차 - 21.02.19 금요일

- 오늘 할 것
    - [x]  GuestPopup - 인원수에 따라 버튼 조정 (이어서)
    url과 state의 인원수 값 역시 초기화 되도록 하기
    - [x]  GuestPopup, 달력 - URLSearchParams로 리팩토링
    - [x]  Payment - 달력모달 넣기
    - [ ]  ~~Payment - 달력모달과 CalendarDetail 컴포넌트 연동~~
    - [x]  -박 나오는 것 고치기
    - [ ]  lazyloading 구현
    ---
    - [ ]  예약하기 버튼 클릭 시 url에 adultNum,childNum,infantNum 중 존재하지 않는 값에 null이 아니라 0넣어주기

<br>

- 오늘 배운 것
  - url.searchParams 이용해서 쉽게 url 파라미터 가져오기
    - 수정 전 코드
      {% image center url.png 600px %}
      
      <br>

    - 수정 후 코드
      {% image center url2.png 600px %}

<br>

### 6,7일차 - 21.02.20,21 토,일요일

- 주말에 할 것
    - [x]  meta 태그 설정하기
    - [ ]  ~~북마크 api 요청(POST, DELETE)~~
    - [x]  Payment - 달력모달과 CalendarDetail 컴포넌트 연동 에러 고치기(이어서)
    - [x]  예약하기 버튼 클릭 시 url에 adultNum,childNum,infantNum 중 존재하지 않는 값에 null이 아니라 0넣어주기
    - [ ]  ~~Header - 스크롤 시 nav Header보이게 하기~~
    - [ ]  ~~lazyloading 구현~~
    - [ ]  ~~환불 모달 만들기~~
    - [ ]  후기 0개 일 때, 레이아웃 만들기

<br>
