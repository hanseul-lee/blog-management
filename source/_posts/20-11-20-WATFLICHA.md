---
title: "[미니 프로젝트] WATFLICHA - 영화 정보 사이트"
categories: [project]
tags: [WATFLICHA, Fastcampus]
thumbnailImage: WATFLICHA-logo.png
date: 2020-12-05 11:46:21
---

<!-- more -->

[미니 프로젝트]
WATFLICHA ( 1차 : 20.11.16 ~ 20.11.20 / 2차 : 20.11.22 ~ 20.12.06)

<!-- excerpt -->

> 패스트 캠퍼스 FE스쿨 Javascript 프로젝트에서 진행한 프로젝트 사이트 WATFLICHA입니다.
> [WATFLICHA github](https://github.com/hanseul-lee/WATFLECHA)

<br>

{% image center main.png %}

<br>

# 프로젝트 목표

> 넷플리스나 왓챠와 같은 OTT서비스를 클론 코딩 및 개선하여 WATFLECHA라는 영화 정보 사이트를 구현한다.

# 서비스 기능

### 1. 로그인 페이지

- 아이디, 비밀번호 값이 공백이거나, 회원가입 한 아이디가 없으면 에러 메세지를 출력해준다.
- 아이디 정보 저장 버튼을 체크했을 시, 한 번이라도 로그인하였다면 다음 로그인 화면에서 아이디가 남아있도록 했다.
- 아이디, 비밀번호를 올바르게 입력한 경우, 왓플릭차 메인페이지로 로그인되어 이동한다. 이때 이름, 아이디, 선호장르, 로그인 정보 저장 여부 및 현재 로그인 상태가 local storage에 담긴다.

### 2. 회원가입 페이지

- 이름, 아이디, 비밀번호 입력 창에 공백 또는 정해진 아이디, 비밀번호 생성 규칙에 맞지 않은 경우 에러 메세지를 출력해준다.
- 아이디와 비밀번호는 4 ~ 15자리 영문 혹은 숫자, 이름은 1자 이상 영문, 한글, 숫자를 입력할 수 있게 했다.
- 비밀번호와 재확인 입력창이 같지 않은 경우, 에러 메세지를 출력해준다.
- 선호 장르를 선택하지 않은 경우, 에러 메세지를 출력해준다.
- 모든 조건을 맞춘 경우, 입력한 이름, 아이디, 비밀번호, 선호 장르를 DB에 전송하고 회원가입이 완료된다.

### 3. 회원 정보 수정 페이지

- 이름, 비밀번호, 장르를 수정할 수 있다. (아이디는 수정 불가)
- 연필 아이콘 클릭 시 입력창에 값을 입력할 수 있다.
- DB에 담긴 기존 정보와 비교해 값이 변경된 경우, 입력창 색이 초록색으로 바뀐다.
- 입력한 아이디, 비밀번호, 이름이 정규표현식 조건과 맞지 않는다면 에러 메세지를 출력해준다.
- 기존 비밀번호 및 비밀번호와 재확인 입력창이 같지 않은 경우, 에러 메세지를 출력해준다.
- 모든 조건에 맞게 정보를 수정하였을 경우, 입력한 이름, 아이디, 비밀번호, 선호 장르를 DB와 local storage(비밀번호 제외)에 전송하고 회원가입이 완료된다.

### 4. 메인 페이지

- 메인화면 가장 위쪽에 화면이 꽉 차도록 영화 예고편을 무한 재생되도록 보여준다.
- 상단의 원하는 장르 클릭 시, 선택된 장르 페이지로 넘어간다.
- 영화 API에서 TOP20, 최신 영화 및 취향 저격 영화에 맞는 영화 목록을 불러와 슬라이드 형식으로 제공한다.
- 슬라이드의 이전, 다음 버튼 클릭 시, 좌우로 슬라이드가 넘어간다. 넘어간 슬라이드는 무한형식으로 일정 슬라이드를 넘어가면 처음이나 맨 끝으로 돌아간다.

### 5. 팝업 페이지

- 메인, 장르, 검색, 찜하기 페이지에서 원하는 영화를 클릭했을 때 팝업창이 보인다.
- 영화 API를 통해 제목, 평점, 예고편, 줄거리, 개봉일, 장르, 총 상영 시간, 출연 배우 정보가 렌더링 되도록 했다.
- 하트 버튼을 누르면 하트 애니메이션이 나타나고 '찜 완료!'로 표시가 되며, 북마크에 찜한 영화가 담긴다.
- 찜한 영화에서 다시 하트 버튼을 누르면 글자가 '찜하기'로 바뀌고 북마크에서 찜한 영화를 제거한다.

### 6. 장르 페이지

- 메인 페이지에서 선택한 장르의 영화들이 렌더링 된다.
- 장르 페이지에서 다른 장르 클릭 시, 선택한 장르의 영화들이 렌더링 된다.
- 페이지네이션을 구현해 사용자가 원하는 페이지로 이동할 수 있게 했다.

### 7. 검색 페이지

- 원하는 영화를 검색하면 검색 API에 의해 검색된 정보가 렌더링 된다.
- 더 보기 버튼 클릭 시, 다음 페이지가 아래에 이어 렌더링 되며 마지막 페이지라면 더 보기 버튼이 사라진다.

### 8. 북마크 페이지

- DB에 저장된 북마크 영화들을 볼 수 있다.
- 북마크 페이지에서 팝업창을 통해 원하는 영화의 북마크를 제거할 수 있다.

# 개발기간
---

1차 구현 : 20.11.16 - 20.11.20
2차 구현 : 20.11.22 - 20.12.06

# 기술스택 & 툴
---
### Front-End
- HTML
- CSS
- Javascript

### 협업
- git/github
- Slack

### 개발 프로세스
- Agile - Scrum

<br>

# 팀원
---

- [김어진](https://github.com/Alex-Eojin) - 기획, 2,3 페이지 HTML/CSS/JS,
  2차 구현(2,3 페이지 리팩토링, 6 장르 페이지 추가, 6,7 페이지 페이지네이션 추가)
- [박상언](https://github.com/parksaneon) - 기획, 4,5 페이지 HTML/CSS/JS, 전반적인 진행사항 QA역할
- [원진솔](https://github.com/do-mandoo) - 기획, 1 페이지 HTML/CSS/JS, github 관리
- [이한슬](https://github.com/hanseul-lee) - 기획, 5,7,8 페이지 HTML/CSS/JS,
  2차 구현(2,3 페이지 리팩토링, 6 장르 페이지 추가, 6,7 페이지 페이지네이션 추가)