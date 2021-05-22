---
title: "[프로젝트] SweetyPie - Airbnb 클론코딩 TIL (2주차: 21.02.08 ~ 21.02.14)"
categories: [project]
tags: [Fastcampus, 프로젝트, SweetyPie]
thumbnailImage: logo.png
date: 2021-02-08 23:26:14
updated:
---

<!-- more -->
SweetyPie - Airbnb 클론코딩 TIL (2주차: 21.02.08 ~ 21.02.14)
- 21.02.10(수) ~ 21.02.14(일) : 설연휴 연남동 에어비앤비 합숙
- UI 작업 마무리 및 api 연동 시작

<!-- excerpt -->
<!-- toc -->
## 21.02.10(수) ~ 21.02.14(일) : 설연휴 연남동 에어비앤비 합숙

### 이번 주 해야할 것

- 상세보기 페이지 (슬)
    - 건강 및 환불 모달 구현 (월)
    - 반응형 Header
    - 지도 UI 구현 -> 검색한 위치 렌더링
    - API 요청해서 정보 받아오기 (GET)
    - 달력 UI 구현 -> 선택한 날짜 정보 받아오기
    - 달력 UI 구현 -> 여행 일정에 따른 예약 기능 구현

<br>

### **1일차 - 21.02.08 월요일**

- 백엔드, 프론트엔드 2주차 스프린트 회의
    - 각자 진행사항 및 이번주 예정 계획 발표
    - 백엔드 업무 이해 안되는 부분 질문
    (입력한 데이터를 잘 정리해서 검증, 예쁘게 가공해서 넣어놓고 보내주고)
- 오늘 한 일
    - 모달창 구현
        - safetyModal - 레이아웃 완성, onShowModal 애니메이션 적용
        - reviewModal - 레이아웃 구현 중
        - 스크롤
- 배운 점
    - 동찬오빠 말투 - 같은 말을 하더라도 부드럽게 하는 것
    ex) 재민이한테 이슈 작성이 늦어서 이를 요청하는 상황	
      재민아 이슈 작성 좀 지금 해줘 (X)
      → 재민아 시간나면 혹시 이슈 작성 좀 해줄 수 있겠니~?
      → 재민아 시간나면 혹시 이슈 작성 좀 부탁해도 될까? <br>

      나 역시도 같은 말이라도 왠지 동찬오빠가 해주면 기분 나쁜 적이 없고 항상 부드럽게 넘어가게 되었던 것 같다. 
      함께 일하고 싶은 사람이 되기 위해 제일 중요한 것 중 하나이면서 내가 부족한 부분이 바로 이런 작은 부분에서의 세심함이라 생각한다.

<br>

### 2일차 - 21.02.09 화요일

- 오늘 한 일
    - RoomDetailHeader 레이아웃 구현
    - Map에 구글지도 API 렌더링
- 배운 점
    - Potal을 쓰는 경우
    - 이벤트 버블링통해 이벤트 조절
    ex. onCloseModal을 최상위 요소에만 적용하고 버블링 통해 나머지 요소에 적용될 수 있게 하기
    - 요소에 data-name 달고 target.dataset.name으로 조절
    [https://developer.mozilla.org/ko/docs/Web/API/HTMLElement/dataset](https://developer.mozilla.org/ko/docs/Web/API/HTMLElement/dataset)
    - onClick 내 화살표 함수 이해하기
      ```js
      <button
         className="flex items-center underline text-#717171"
         onClick={() => onShowModal('refund')}
      >
      ```
<br>
- 우영강사님 트러블슈팅(16:00 ~ 16:50)
    - release
        배포를 위한 용도
        auth 디버깅용 패스워드 찍었을 때 가리는 용도
        css comfile 같은 것 등등
        배포를 위한 작업이 끝나면 
        <br>

        merge commit 2번뜸
        1st - main 
        2nd - develop 
        <br>

        v0.0.1 과 같은 식으로 네이밍 할 것
        두번째 자리는 베타버전 - 사용자가 사용할 수준의 개발이 이뤄졌을때
<br>
    - 코딩 컨벤션 수정 - git issue와 pull request 연결
      ```markdown
      $ git commit

      docs: Create README.md 

      resloved: #1 // 최종 커밋할 때만 작성

      // 이후 :wq 누르고 나가기
      ```
      - (주의) `git commit -m` 하지 말고 `git commit` 한 후 들어가서 내용 수정할 것
      - 만약 최종 커밋 때 이슈 번호 다는 것 까먹었다면 pull request 내용 란에 작성해서 연동도 가능

    - 코드리뷰 예시
      {% image center 코드리뷰_01.png %} <br>
      {% image center 코드리뷰_02.png %}

    - Windows 꿀팁
      [https://docs.microsoft.com/en-us/windows/powertoys/](https://docs.microsoft.com/en-us/windows/powertoys/)
      [https://docs.microsoft.com/en-us/windows/wsl/](https://docs.microsoft.com/en-us/windows/wsl/)

<br>

- Mark강사님 트러블슈팅(20:00 ~ 20:50)
    - (질문1) Potal을 쓰면 좋은 이유, 모달 생성시 z-index에 대한 이해
        => potal을 쓰는 게 다 좋은 게 아니다
        사실 컴포넌트를 이용해 모달은 만드는 게 더 많이 사용하는 방법임
        모달이 index.html에서 `<div id='modal'>`이 root보다 더 아래에 있으므로 우선순위가 위임
        따라서 z-index를 조절하는 게 아님
        우리가 이를 조절하려면 tailwind.config에서 모달의 z-index를 조절할 것
    - (질문2) Hash로 header nav 이동방법
    React에서 Link가 아닌 a태그를 직접적으로 사용해도 되는지?
        => a태그로 이동하자!
        [https://github.com/ReactTraining/react-router/issues/394](https://github.com/ReactTraining/react-router/issues/394)
      ```jsx
      // src > components > roomDetail > RoomDetailHeader.jsx

      const RoomDetailHeader = ({ scrollHeader }) => {
        // nav 메뉴 클릭 시 해당 컴포넌트로 스크롤 이동
        const onScrollNav = e => {
          e.preventDefault();
          const id = e.target.href.split('#')[1];
          const scrollTargetId = document.getElementById(id);
          window.scrollTo({
            left: 0,
            top: scrollTargetId.offsetTop - 89,
            behavior: 'smooth',
          });
        };

        return (
          <div >
            <div>
              <a href="#photos" onClick={onScrollNav}>
                사진
              </a>
      ```

<br>

### 3일차 - 21.02.10 수요일

- 이슈 잘게 쪼개서 branch 생성하기 위해 현재까지의 작업 git organization merge
    => 여기서 git rebase 및 git reset --hard 로 인한 문제 발생😡😡😡
    cf) 참고 자료
    [https://www.google.com/search?q=Not+possible+to+fast-forward%2C+aborting.&oq=Not+possible+to+fast-forward%2C+aborting.&aqs=chrome..69i57j0j0i30j0i30i395j0i5i30i395l3j69i60.479j1j1&sourceid=chrome&ie=UTF-8](https://www.google.com/search?q=Not+possible+to+fast-forward%2C+aborting.&oq=Not+possible+to+fast-forward%2C+aborting.&aqs=chrome..69i57j0j0i30j0i30i395j0i5i30i395l3j69i60.479j1j1&sourceid=chrome&ie=UTF-8)
    [https://stackoverflow.com/questions/13106179/fatal-not-possible-to-fast-forward-aborting/43460847](https://stackoverflow.com/questions/13106179/fatal-not-possible-to-fast-forward-aborting/43460847)
    [https://junwoo45.github.io/2019-10-23-rebase/](https://junwoo45.github.io/2019-10-23-rebase/)
    [https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0](https://git-scm.com/book/ko/v2/Git-%EB%B8%8C%EB%9E%9C%EC%B9%98-Rebase-%ED%95%98%EA%B8%B0)
<br>

- github 순서 다시 정리
```
팀장 레포에서 이슈 생성

git flow feature start 브랜치명(새 작업 브랜치 생성)
코드 작성

git add
git commit
> feat: 로그인 모달 구현 (#123)

git flow feature finish 브랜치명 (작업 브랜치 닫고 develop으로 이동)

만약 conflict 발생 시
git pull upstream develop (내쪽에서 conflict 해결)
git push origin develop

Github에서 Pull request
1. 제목 및 내용에 이슈 및 작업 내용 상세히 작성
2. 내용 마지막에 closed: #123
3. 풀리퀘 올린 후, 옆에 Labels, Projects, Milestone, Linked issues 꼭 지정
```
<br>

- 우영강사님 트러블슈팅 (00:10 ~ 1:00)
  - git reset --hard로 인해 
  저번 주 금요일 merge한 후, 내 local에 저장되었던 모든 commit과 작업 내역들이 날라갔다.
    - git push origin develop으로 내 origin에 log를 찍지 않았기 때문에 복구 방법은 X
    - Reabse 과정에서 문제가 생긴다면 rebase abort를 해야한다.
    → abort를 한다면 reabase 하기 전으로 돌아간다
    - 만약 git pull upstream develop에서 또 fast-foword 에러가 난다면 rebase로 해결하지말고
    `git fetch upstream develop` -> `git merge FETCH_HEAD` 로 처리할 것
    pull = fetch + merge

  사실 처음에 얘기를 듣고 예전에 연남동 때처럼 모든게 정지된 것처럼 굳거나 당황하지는 않았다. 오히려 웃으면서 아~ 정말요~? 이랬는데 강사님께서 계속 괜찮다고, 너무 걱정하지 말라고, 액땜한 거라고, 실무에서도 실수할 수 있는 걸 미리 겪어서 다행이라고(만약 그렇다면 탕비실로.....ㅎ) 말씀해 주셨다. 심지어 이어서 1시간 가량 깃 관련 질문하고 끝난 이후에 동찬오빠한테 우리 에어비앤비 주소도 물어보고 치킨 기프티콘까지 보내주셨다ㅠㅠㅠ감동ㅠㅠㅠ
  덕분에 한 걸음 뒤로 물러나지긴 해도 깃에 대해 이해도 좀 더 높아지고 조심해야 할 reset --hard에 대해서도 확실히 경각심을 갖게 되었다.
<br>

  - **git pull request와 issue 연결**하는 방법 제대로 하고 있는지 확인
  - git pull upstream develop 후 conflict 해결 후 commit message
  '머지 컨플릭, 풀리퀘번호, 이슈번호 해결했다'는 내용 담을 것
  - **pull request message**
  내용에 closed 외에 이슈 내용에 대해 '**어떻게**' 해결했는지에 대한 코멘트 상세히 작성할 것!!!
  - **이슈를 잘게 나눠서 save point를 많이 만들어두는것이 좋다**
  이슈 상세히 작성하고 이에 따른 브랜치 만들 때 팁
  **브랜치 이름 -> 겹치지 않는 첫 대문자 이후 기능을 설명할 두 단어 정도 붙여라**
  ex) Main에서 리스트 만드는 작업 시, M_makeList

<br>

### 4일차 - 21.02.11 목요일

- 배운 점
  - `npm start`할 때 다음과 같은 에러가 나는 건 conflict 해결 안 된 게 남아있다는 것
  따라서 conflict 해결하고 다시 npm start 할 것
  {% image center 2021-02-11.png %} <Br>

  - git 파일이름 변경
  ```markdown
  $ git mv ./src/assets/Svg.js ./src/assets/svg.js
  ```
    오른쪽 클릭 후 변경하는 게 아니라 bash에서 위 커멘드로 입력해 주어야 commit 해서 이력남기기 가능
 <br>

  - 동찬오빠 redux module과 코드 보면서 미들웨어, 사가, 스토어 및 전체적인 구조와 흐름에 대한 이해
    - 직접 saga를 도입해서 api와 연결하기 전에 궁금한 점에 대해 집요하게 오빠에게 물어봤는데 시간을 보니 어느새 3시간 넘게 얘기를 하고 있었다. 이해가 안되는 부분에 대해 끈질기게 질문했는데 하나하나 이해될 때까지 설명해 주려고 한 동찬오빠에게 너무 고맙고 감사하다.
    - 내가 get한 정보를 store에 관리해야하는 이유 -> 다른 팀원들이 사용하기 때문(ex. 결제페이지에서 해당 room 정보 받아오기)

<br>

### 5일차 - 21.02.12 금요일

- 오늘 한 것
    - roomDetail saga 및 API 연동중
    - roomDetail saga 연동 오류 해결
- 배운 점
    - 스토어에 있는 상태들은 container에서 useSelector로 가져올 것
    - payload로 room_id를 보낸다. 왜냐하면 url room_id에 따라 DB를 보내주기 때문!
    - 유효성 검사의 중요성 (roomDetail saga 연동 오류 해결)

    ⇒ 각 컴포넌트에서 api로 받아오는 정보들이 props로 전달되는데 saga 과정에서 loading이 false과 되기 전에 실행이 된다면 data와 연동되기 전에 코드가 실행되어 에러가 뜬다.
    따라서 `loading === false && (props...)` 와 같은 유효성검사를 받드시 시행해 주어야 data가 제대로 받아온 후 컴포넌트의 렌더링이 진행될 수 있다. 

<br>

### 6,7일차 - 21.02.13,14 토, 일요일

- 오늘 한 것
    - roomDetail API 연동
    - safetyModal 구현
    - Map API 연동

<Br>

- 백엔드와 ZOOM 미팅(18:30 ~ 19:30)
    - 문제점
        1. 백엔드와 프론트의 업무가 다르다는 이유로 우리의 업무사항을 시시각각 공유하지 못한 것. 나아가 설 연휴 및 에어비앤비로 따로 떨어져 작업했기 때문에 이러한 점이 더욱 심화되었음.
        2. 백엔드 분들이 맡은 부분을 정확히 파악하지 못함. 따라서 백엔드 팀장님인 재복님께만 계속해서 질문함. 이로인해 소통의 양극화가 심해짐.
        3. api를 연동하는 데 있어 어디까지가 백엔드의 영역이고 어디까지가 프론트의 영역인지를 파악하는데 서로 어려움을 겪음. 프론트쪽에서 api에 대해 수정하고 싶은 부분이 있을 때 바로바로 백엔드 분들께 수정 사항에 대해 요청했는데, 이 부분에 있어 백엔드 분들의 어려움을 충분히 고려하지 않았음.
    - 해결과정 및 결론
        - zoom 회의를 통해 백엔드 분들의 문제점과 불만사항에 대해 정중하게 얘기를 듣고 생각하는 시간을 가짐.
        - api를 연동하는 데 있어 어디까지가 프론트 선에서 해결가능한지 우선적으로 생각하고 요청해보기로 함.
        - 이번 주 이후 학원 외에 에어비앤비에서 작업함에 있어 진행사항에 대해 소통이 원할하지 못할 경우를 대비해 오늘 진행한 일과 더불어 앞으로 남은 일에 대해 매일 정리해 slack에 공유하기로 함.

<br>
