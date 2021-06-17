---
title: '[Git] gitHub에 new repository 생성하기'
categories: [StudyLog, Git]
tags: [gitHub, git]
thumbnailImage: git.jpeg
date: 2020-12-17 12:21:32
---

<!-- more -->

github에 new repository 생성하는 방법을 알아봅시다.

<!-- excerpt -->

## 1. GitHub Repository 생성

{% image center 1.jpg 700px %}

<br>

GitHub에서 다음과 같이 새로운 Repository name을 입력하고 Create repository 버튼을 눌러 새 Repository를 생성한다.

<Br>

## 2. Initialize repository

```bash
git init
```

위의 명령어를 통해 해당 프로젝트 폴더 내에 숨겨진 .git 폴더를 생성하고 이제 Git은 현재 repository에 대한 모든 변경 사항들을 추적 및 관리하게 된다.

<br>

## 3. 새로운 폴더(파일) 만들고 작업 생성

```bash
git add .
git commit -m "commit massage"
```

새로운 repository에 올릴 폴더(파일)을 만들고 코드를 작성한 뒤, add, commit을 해준다.

<br>

## 4. 원격 저장소와 연결 후 push

{% image center 4.jpg 700px repository 주소 복사하기 %}

생성된 repository에서 code 버튼을 누른 후, 이를 복사해 `git remote add origin [repository 주소]`명령으로 local과 remote repository를 연결해 준다.

- Local repository : 본인의 컴퓨터에 저장된 프로젝트 저장소
- Remote repository : 로컬이 아닌 외부 서버의 원격 프로젝트 저장소

이 후 `git remote -v | --verbose` 를 통해 원격 저장소 목록을 불러와 연결된 것을 확인할 수 있다. 이 후, 로컬에서 작업한 파일을 원격 저장소로 push 해주면 된다. -u(--set-upstream)를 통해 upstream origin 정보를 설정한 후에는 해당 브랜치에서 `git push`만 입력해줘도 push가 가능하다.

```bash
git remote add origin [repository 주소]
git remote -v
git push -u origin main
```

## error - fatal: refusing to merge unrelated histories

만약 git pull이나 push를 할 때 `fatal: refusing to merge unrelated histories` 에러가 뜨는 경우가 있다. 이는 로컬 저장소와 원격지의 저장소의 기록(History)을 비교했을 때 소스코드의 차이가 심한 저장소의 경우, 병합 오류가 날 것을 대비하여 오류 메시지를 띄우는 것이다. 다음과 같은 명령어를 통해 해결 할 수 있다.

```
$ git pull origin 브랜치명 --allow-unrelated-histories
```

<br>

---

**Reference**

- [https://git-scm.com/docs/git-remote](https://git-scm.com/docs/git-remote)
- [[Git] GitHub 레파지토리(Repository) 생성하고 소스 올리기
  ](https://velog.io/@kho5420/Git-GitHub-%EB%A0%88%ED%8C%8C%EC%A7%80%ED%86%A0%EB%A6%ACRepository-%EC%83%9D%EC%84%B1%ED%95%98%EA%B3%A0-%EC%86%8C%EC%8A%A4-%EC%98%AC%EB%A6%AC%EA%B8%B0)
- [https://parksb.github.io/article/28.html](https://parksb.github.io/article/28.html)
- [https://nochoco-lee.tistory.com/34?category=343045](https://nochoco-lee.tistory.com/34?category=343045)
- [https://ndb796.tistory.com/275](https://ndb796.tistory.com/275)
