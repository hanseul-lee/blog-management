---
title: '[git] fork한 repo에서 wiki 업데이트 후, upstream에 반영하기'
categories: [StudyLog, git]
tags: [gitHub, git]
thumbnailImage: git.jpeg
updated:
---

<!-- more -->

fork한 repo에서 wiki 업데이트 후, upstream에 반영하는 방법을 알아보자.

<!-- excerpt -->

# GitHub wiki란

GitHub 공식문서에서 wiki란 README에서 간략히 소개한 프로젝트에 대해 보다 상세한 추가 설명을 덧붙인 문서라는 설명을 볼 수 있다.

{% image center wiki.jpg GitHub Docs - About wiki %}
<Br>

# Pull request로 upstream에 wiki 반영이 불가능하다고?

README밖에 모르던 내가 wiki의 존재를 알게 되고 파이널 프로젝트의 방대한 README를 정리해 wiki를 만들고 이를 대폭 수정하기로 했다. 따라서 우선 fork한 내 레포에서 먼저 README와 wiki를 정리해 반영했다. 이 후 pull request로 upstream에 반영하려 하니 wiki의 변경사항이 하나도 반영되지 않아 멘붕에 빠졌다.

stackoverflow를 찾아보니 실제로 git에서 pull request를 통해 upstream의 wiki를 업데이트가 불가능하다고 한다.

{% image center wiki2.jpg https://stackoverflow.com/questions/10642928/how-to-pull-request-a-wiki-page-on-github %}

직접 일일히 옮겨야 하나 고민하던 찰나 나와 같은 고민을 하고 있던 다음과 같은 글([Merge Wiki Changes From A Forked Github Repo](https://gist.github.com/larrybotha/10650410))을 발견하고 성공적으로 upstream에 내 wiki를 반영할 수 있었다.

<br>

# fork한 repo에서 wiki 업데이트 후, upstream에 반영하기

방법은 간단하다.
아래와 같이 OREPO의 wiki를 클론 한 후 FREPO의 위키를 merge 후 다시 OREPO에 push해 반영해주면 된다.
<br>

- **OREPO** : original repo - 내 경우엔 orginiztion의 repo
- **FREPO** : the forked repo - fork 후 wiki가 업데이트 된 내 repo

<Br>

```bash
$ git clone [OREPO].wiki.git
$ cd [OREPO].wiki.git

# squashing all FREPO changes
$ git pull [FREPO].wiki.git master

$ git push origin master
```

나는 OREPO의 owner이기도 해서 issue 생성없이 바로 반영했는데 혹시 오픈소스나 새로운 프로젝트에 기여하는 경우라면 issue를 남기고 이를 알리는 것이 선행되어야 한다. 또한, FREPO를 fork 한 후, OREFO가 새롭게 업데이트 된 경우라면 추가적인 방법을 따라야 하는데 이는 위 링크에서 확인가능하다.

사실 중간에 개인 organization으로 연습하던 중 계속 오류가 나서 일일히 복붙해서 옮겨야하나 고민의 시간에 빠졌었는데 다시 마음을 고쳐먹고 매달려 성공하고 나니 너무 뿌듯했다. 나와 같은 고민을 하며 방법을 찾아헤매는 또다른 개발자들에게 조금이나마 이 글이 도움이 되었으면 좋겠다.

<Br>

### Reference.

- [[Stackoverflow] How to pull request a wiki page on GitHub?](https://stackoverflow.com/questions/10642928/how-to-pull-request-a-wiki-page-on-github)
- [Merge Wiki Changes From A Forked Github Repo](https://gist.github.com/larrybotha/10650410)
- [[GitHub Docs] About wikis](https://docs.github.com/en/communities/documenting-your-project-with-wikis/about-wikis)
