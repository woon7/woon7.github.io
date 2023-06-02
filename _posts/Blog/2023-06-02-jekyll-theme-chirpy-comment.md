---
title: "[Blog] Chirpy Jekyll Theme Comment 기능 추가하기"
date: 2023-06-02 +0900
categories: [Blog]
tags: [blog, jekyll, chirpy, github, comment, utterances]
---


### Introduction
---
테마에 댓글 기능이 원래 존재했었는데 유료화 이슈가 있는지 제대로 동작하지 않는다. 무료로 댓글 기능을 사용할 수 있게 해주는 Utterances를 GitHub Remote Repository에 설치해보자.


### GitHub Remote Repository에 Utterances 설치
---
1. [GitHub Marketplace - Utterances](https://github.com/marketplace/utterances)에 접속
2. Set up a plan -> Install it for free
3. Billing information 입력 후 Install
4. Only select repositories -> `username`.github.io 선택
5. Install


### Chirpy에 Utterances 연동하기
---
1. [Utterances Wiki](https://utteranc.es/) 접속
2. Configuration - Repository - repo: 밑 Textbox에 `username`/`username`.github.io 입력
3. Enable Utterances 밑에 Script 복사
    ```html
    <script src="https://utteranc.es/client.js"
            repo="username/username.github.io"
            issue-term="pathname"
            theme="github-light"
            crossorigin="anonymous"
            async>
    </script>
    ```
4. `_layouts/post.html` 끝 부분에 복사한 Script 삽입
5. 블로그를 띄우면 Post 밑에 댓글 기능이 생긴 것을 확인할 수 있다. Comment를 달아보자.


### Comment 관리하기
---
1. Comment가 정상적으로 입력되면 댓글 최상단에 1 Comment라는 문구가 뜬다. 눌러보자.
2. GitHub Issues 페이지에서 utterances-bot에 의해 자동 생성된 Issue를 발견할 수 있다.
3. 해당 페이지에서 Comment 관리를 할 수 있다.


### References
---
- [Jekyll 테마에 utterances 댓글 연동하기](https://www.irgroup.org/posts/utternace-comments-system/)
