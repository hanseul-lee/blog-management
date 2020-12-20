---
title: "[git] git 명령어 정리"
categories: [Fastcampus, git]
tags: [github,git]
thumbnailImage: git.jpeg
date: 2020-12-17 13:56:47
---

<!-- more -->
git 명령어를 보다 유용하게 사용하기 위해 자주 사용하는 명령어를 정리하였습니다.
<!-- excerpt -->
<!-- toc -->

git 명령어를 보다 유용하게 사용하기 위해 자주 사용하는 명령어를 정리하였습니다. 

<br>

# 전체 흐름 요약

```
            -add->      -commit->     -push->
+-------------+-------------+------------+-------------+
| Working dir |    Index    | Local repo | Remote repo |
+-------------+-------------+------------+-------------+
         <-checkout-                 <-fetch-
```
<br>

1. github에 **원격 저장소** 생성한다.
  - **원격 저장소 (Remote repository)** : github와 같이 외부 서버의 원격 프로젝트 저장소

2. **로컬 저장소**의 **작업 디렉토리**에서 파일을 작성한다.
  - **로컬 저장소 (Local repository)** : 본인의 컴퓨터에 저장된 프로젝트 저장소
  - **작업 디렉토리(Working directory)**: 실제 파일이 위치한 디렉토리.

3. `git add [파일이름]` 또는 `git add .`을 통해 변경된 파일들을 **스테이징**해 **Index** 영역에 등록한다.
  - **스테이징(Staging)**: 확정할 변경 사항을 준비시키는 것.
  - **인덱스(Index)**: 확정할 준비가 된 변경 사항들이 모인 영역.

4. `git commit -m "commit message"` 명령으로 스테이징된(Staged) 변경 사항을 commit해 로컬 저장소에 등록한다.
  - **Commit**: 인덱스의 변경 사항들을 확정하는 것. 

5. 원격 저장소를 clone 해 로컬 저장소와 연결한다. 이후 push해 커밋된 변경사항들을 원격 저장소에 게시한다.
  - **Push**: 확정된 변경 사항을 원격 저장소에 게시하는 것.
  - **origin**: 로컬 저장소의 원본 원격 저장소
```
git clone [내 repo 주소]
git push -u origin main
```


<br>

# git cheat sheet

참고로 git 명령어를 사용함에 있어 다음과 같은 git cheat sheet를 사용하면 보다 유용하게 명령어를 파악할 수 있다.
<br>

{% image center cheatSheet.png 800px git cheat sheet %}

<br>

---
**Reference**
- [https://git-scm.com/docs](https://git-scm.com/docs)
- [https://parksb.github.io/article/28.html](https://parksb.github.io/article/28.html)
- [https://github.blog/2015-07-29-git-2-5-including-multiple-worktrees-and-triangular-workflows/](https://github.blog/2015-07-29-git-2-5-including-multiple-worktrees-and-triangular-workflows/)


