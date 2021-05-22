---
title: "[프로젝트] SweetyPie - Airbnb 클론코딩 TIL (4주차: 21.02.22 ~ 21.02.26)"
categories: [project]
tags: [Fastcampus, 프로젝트, SweetyPie]
thumbnailImage: logo.png
date: 2021-02-22 23:26:27
updated:
---

<!-- more -->
SweetyPie - Airbnb 클론코딩 TIL (2주차: 21.02.08 ~ 21.02.14)
- 21.02.17(수) ~ 21.02.27(일) : 홍대 에어비앤비 합숙
- 배포 전 디테일한 작업 마무리, 모든 페이지 통합 및 netlify를 이용한 배포

<!-- excerpt -->
<!-- toc -->

## 21.02.17(수) ~ 21.02.27(일) : 홍대 에어비앤비 합숙

### 1일차 - 21.02.22 월요일
- 오늘 할 것
    - [ ]  북마크 api 요청(POST, DELETE) 에러 수정
    - [x]  ~~Payment - day 연동하기~~
    - [x]  ~~url과 인원수 연동하기~~
    - [x]  ~~후기 0개 일 때, 레이아웃 만들기~~
    - [x]  ~~Header - 스크롤 시 nav Header보이게 하기~~
    - [ ]  랜덤 프로필 사진
    - [x]  ~~url에 날짜 존재하지 않을 때 에러 고치기~~
<br>
    - [ ]  스켈레톤 UI 구현
    - [ ]  환불 모달 만들기
    
- 오늘 배운 것
    1. || → 더하기로 생각하기 
    && → 곱하기로 생각하기
<Br>

### 2일차 - 21.02.23 화요일

- 오늘 할 것
    - [x]  ~~북마크 api 요청(POST, DELETE) 에러 수정~~
    - [ ]  ~~팝업창 background 클릭 시 닫히게 하는 라이브러리 적용~~
    - [x]  ~~Header 합치기~~
    - [ ]  랜덤 프로필 사진
    - [ ]  모달창 close 애니메이션 적용
    - [ ]  모든 페이지에 헬멧 적용

    - [x]  ~~url과 인원수 팝업 내 연동 에러 고치기~~
<br>
    - [ ]  스켈레톤 UI 구현
    - [ ]  환불 모달 만들기

<br>

- **우영강사님 트러블슈팅 (10:00 ~ 10:50)**
  - 이 버전이 올라가는데 수행된 릴리즈 이슈 적기
  - 릴리즈 관련 이슈 해결 과정
```bash
$ git add .
$ git commit
$ git flow release start 0.3.1
$ git flow release finish 0.3.1
$ git push origin develop (develop)
$ git checkout main
$ git push origin main (main)
$ git push origin 0.3.1
```
  - run server할때 port 설정 주의할 것 
  `ENV.PORT || 4040` 로 설정하자
  - 배포 후 https 써보기

<br>

  - 발표 TIP
    - 아무것도 모르고 우리의 프로젝트를 처음 보는 사람에게 발표한다고 생각하고 준비할 것
    - 쭉 설명하고 화면 시연 (X) → 왔다갔다하더라도 기능별로 설명하고 시연
    - 프론트따로, 백엔드 따로(X) → 프론트와 백엔드가 함께 발표
    - 결론 ⇒ 
    프로젝트를 통해 느낀점 / 아쉬웠던 점 / 개선 할 점(다음프로젝트 때 보완할 것)
    - 발표기준 - 발표자료 / 구성 / 발표태도 / 어조
    - 마지막 릴리즈 때는 버전 1.0.0으로 올려줄 것

<Br>

- 오늘 배운 것
  - 폴더 이름 바꾸기
상위 폴더로 들어간 후 `git mv oldName newName`
만약 하위에 바꾸려고 하는 이름과 중복된 파일 이름이 존재한다면 에러가 뜰 수 있는데 이때 다른 이름으로 변경 후 다시 원하는 이름으로 한 번 더 고쳐주면 해결 가능함
```bash
// Main을 main으로 바꾸고 싶은데
// 해당 폴더 내에 main.jsx가 존재해서 에러가 발생할 때
$ git mv Main main123
$ git mv main123 main
```
cf. 참고: 
https://www.lesstif.com/gitbook/git-git-rename-file-or-folder-54952878.html
<Br>

  - 이미 push된 파일 gitignore 적용하기
```bash
$ git rm -r --cached .
$ git add .
$ git commit -m "Apply .gitignore"
$ git push
```
  cf. 참고: https://cjh5414.github.io/gitignore-update/
<Br>

- 배포 과정 중 에러
`npm run build`를 `CI= npm run build`로 고치기
cf. 참고: https://www.youtube.com/watch?v=i8jkGjIIHo8
<Br>

- manifast.json / opengraph / (structured data) ⇒ SEO에 good!
- robots.txt
Disallow에 /추가 → 모두 검색 방지 
```
# https://www.robotstxt.org/robotstxt.html
User-agent: *
Disallow: /
```
- https로 백엔드와 맞추기
      {% image center https.png 600px %}
- 예쁜숙소 - 7774, 7779, 10301, 10337,10506
<Br>

- 우영강사님 "이렇게 배우는 거죠 저도"
멘토와 같은 강사님께서 우리 트러블 슈팅을 하면서 하신 말씀이 기억에 남는다. 실력과 경력이 더 쌓이고 난 후에도 우영 강사님처럼 작은 순간마저 겸손하게 받아들이고 배워나가려는 자세를 갖춘 개발자로 성장할 수 있을까. 정말 정말 본받고 싶은 자세이다.

<Br>

### 3일차 - 21.02.24 수요일
- 오늘 할 것
    - [x]  ~~모달창 background 클릭 시 닫히게 하는 라이브러리 적용~~
    - [x]  ~~프로필 사진 수정~~
    - [ ]  모달창 close 애니메이션 적용
    - [x]  ~~모든 페이지에 헬멧으로 title 적용~~

    - [x]  ~~헤더에 예약하기 버튼 추가~~
    - [x]  ~~헤더 3단변신 구현~~
    - [ ]  url가져오기 부분 → useLocation으로 바꾸기
    - [x]  ~~footer 부분 스타일 고치기~~
    - [x]  ~~리뷰클릭시 프로필 이미지 이상하게 나오는 것 고치기~~
    - [x]  ~~북마크에서 하트누르면 바로 반영되게 하기~~
    - [x]  ~~airbnbHover 색깔 진하게 바꾸기~~
    - [ ]  Calendar 백그라운드 투명하지 않게 바꾸기
<Br>

    공통
    - [x]  ~~meta태그 통일~~
    - [x]  ~~주석 및 ESLint 에러 모두 고치기~~
<Br>

- **mark 강사님 트러블 슈팅 (18:00 ~ 18:50)**
    1. tailwind.config.js 에 그 전 tailwind 옮겨 넣기
    2. outpus.css 제거
    3. npm run build에서 minifiy, uglyfy 자동으로 해줌
    4. `npx serve -s build` (-s : SPA)
    ★-s 옵션을 붙이면 페이지가 존재하지 않을 때 자동으로 index.html으로 보내줌
    5. dependency관련 에러는 반드시 해결할 것
    6. let이 아니라 const 사용
    7. useMemo → 쓰지말고 useLocaion Hook으로 할 것
    8. useMemo → 쓰지말고 useLocaion Hook으로 할 것
    <Br>

    -  **최종 프로젝트 완성 시 중점으로 볼 것**
    1. 레이아웃이 안맞는 것(ex. max-width)
    코드를 보기 전 레이아웃이 깨져있으면 코드로 넘어가기도 싫음
    2. 기능적으로 문제가 없는지 팀원들끼리 코드 리뷰
    ex) ESLint Error, 컴포넌트를 제대로 나누는 것, url을 제대로 가져오지 않은 것 등
    3. 지금은 시간내에 완성도 있게 만드는 게 더 중요 - 발표할 때 우리 netlify로 배포한 것 보여주면서 테스트 해보라고 자신있게 만들 수 있을 정도로!
<Br>

### 4일차 - 21.02.25 목요일
- 오늘 할 것
    - [x]  ~~북마크 기능 리팩토링~~
- 고쳐야 할 것
    - [ ]  캘린더 팝업에서 오늘 이전 날짜 막기
    - [ ]  버튼 통일하기

- 오늘 배운 것
  - 북마크 기능
    - 수정 전
      {% image center before.png 600px 수정 전 %}
    - 수정 후
      {% image center after.png 600px 수정 후 %}

<Br>

### 5일차 - 21.02.26 금요일

- 최종발표 PPT 
  https://www.miricanvas.com/v/19j7u1
- Backend API POSTMAN 
  https://documenter.getpostman.com/view/14479786/TWDUrJpP#f3828b6b-8029-4da0-87e3-84cc50e8c029

<Br>

- 일정을 맞추는 건 생명선, 품질은 자존심
- 배포가 매일 이루어지는만큼 변경사항에 대한 소통이 바로바로 이루어져야 한다는 것을 배움 
by 복복
<br>

- 앞으로 인생에서 같이 일하는 사람이 누구냐가 정말 중요
- 항상 배울 수 있는 동료가 있는 회사를 꼭 선택할 것
- 2조 슬랙방이 제일 쾌할하고 활발했다고 생각했음 by Mark💛
