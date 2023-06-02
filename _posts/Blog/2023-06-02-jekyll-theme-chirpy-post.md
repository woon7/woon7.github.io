---
title: "[Blog] Chirpy Jekyll Theme 포스트 작성"
date: 2023-06-02 +0900
categories: [Blog]
tags: [blog, jekyll, chirpy, github, post, markdown]
---


### Introduction
---
블로그를 만들었으니 간단하게 포스트를 작성해보자.


### .md 파일 생성
---
1. `username.github.io/_posts/` 디렉토리 밑에 새로운 디렉토리를 생성한다.
    - 필자의 경우에는 `Blog` 디렉토리를 만들었다.
    - 생성된 디렉토리는 Categories에 자동으로 등록된다.
2. 생성한 디렉토리로 들어가 `.md` 파일을 생성한다.


### Jekyll Front Matter 작성
---
우리가 만든 블로그는 Jekyll 기반이기 때문에 포스트를 작성하는 경우에 Front Matter를 반드시 작성해야 한다.

- Front Matter 예제
    ```md
    ---
    title: "[Blog] Chirpy Jekyll Theme Google 검색 노출하기"
    date: 2023-06-02 +0900
    categories: [Blog]
    tags: [blog, jekyll, chirpy, post, markdown]
    ---

    ### 제목
    ---
    내용

    - Markdown 문법으로 하고 싶은 말을 해보아요.
    ```


### Markdown 문법으로 글 작성하기
---
[마크다운(Markdown) 사용법](https://gist.github.com/ihoneymon/652be052a0727ad59601)을 숙지하고 원하는 글을 작성해보자.