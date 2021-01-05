---
title: "[git] hexo를 이용한 github blog 포스팅하기"
date: 2020-08-19 15:25:33
tags: [github,git]
categories:
  - StudyLog
  - git
thumbnailImage: git.jpeg
---

<!-- more -->
hexo를 이용해 Github에 만든 blog에 글을 포스팅하는 방법을 알아봅시다.
<!-- excerpt -->


> Github에 만든 blog에 글을 포스팅하는 방법을 알아봅시다.

<br>

1. 포스트 생성

   ```js
   hexo new post "yyyy-mm-dd-My new post"
   ```

2. 문서 작성

   - git bash 나 vscode 둘 다 가능하다.
   - md파일 markdown 사용해 작성해야 한다. 

3. 서버에 전송

   ```jsx
   hexo clean && hexo generate //서버에 전송
   hexo g //축약형
   ```

4. 서버에서 확인

   ```jsx
   hexo server // http://localhost:4000 에서 확인
   hexo s // 축약형

   hexo s -o // 서버 생성 및 새창에서 열기
   ```

5. git에 전송

   ```jsx
   hexo clean && hexo deploy // 깃에 전송
   hexo d // 축약형
   ```

   참고로 나중에 generate과 deploy를 빨리 하기 위해 다음과 같은 축약형을 알아두면 편리하다.
   ```js
   hexo g -d
   ```


   이제 서버가 아닌 github blog주소에서 확인 가능하다
   => [hanseul-lee.github.io/](hanseul-lee.github.io/)
