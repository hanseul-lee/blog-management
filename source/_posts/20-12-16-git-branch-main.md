---
title: "[git] Default 브랜치명 변경하기 (master -> main)"
categories: [StudyLog, git]
tags: [github,git]
thumbnailImage: git.jpeg
date: 2020-12-17 11:26:36
---

<!-- more -->
github의 default의 브랜치명을 master에서 main으로 변경하는 방법을 알아봅시다.
<!-- excerpt -->

# github의 default 브랜치가 main으로 바뀌다

{% image center main.jpg 600px %}
<br>

2020년 10월, [github 공식 블로그](https://github.blog/changelog/2020-10-01-the-default-branch-for-newly-created-repositories-is-now-main/)는 default 브랜치의 명칭이 main으로 바뀌었음을 알렸다. 이는 이전부터 꾸준히 진행된 논쟁인 master/slave, balcklist/whitelist와 같이 인종차별적인 단어의 문제를 개선하려는 움직임에서 시작되었다. 따라서 github 역시 이러한 움직임에 동참하여 default 브랜치를 기존 `master`에서 `main`으로 변경하였고 올해 말부터 master로 생성했던 기존 브랜치의 이름 또한 원할하게 변경 가능하게 작업중이라고 한다.

<br>

# 기존 Repository의 Default branch 이름을 변경하고 싶다면?

따라서 기존 Repository에서 master로 만들어져있는 default 브랜치 이름을 main으로 변경하고 싶다면 다음과 같이 바꿀 수 있다.

<br>

### step1. 
- git branch 명령어 "-m/-M" 옵션을 사용해 브랜치 이름을 변경하고 remote 저장소에 push
```bash
$ git branch -m master main
$ git push -u origin main
```

### step2. 
- Github Repository 설정 변경

{% image center step2.jpg 950px %}

<br>

### step3. 
- 기존 브랜치 삭제

{% image center step3.jpg 950px %}

이를 통해 기존 master로 되어있는 default 브랜치명을 main으로 바꿀 수 있다.

<br>

---
**Reference**

- [github blog](https://github.blog/changelog/2020-10-01-the-default-branch-for-newly-created-repositories-is-now-main/)
- [github/renaming](https://github.com/github/renaming/#later-this-year)
- [https://kyeoneee.tistory.com/72](https://kyeoneee.tistory.com/72)
