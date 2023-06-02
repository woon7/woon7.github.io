---
title: "[Blog] Chirpy Jekyll Theme 커스터마이징"
date: 2023-06-02 01:00:00 +0900
categories: [Blog]
tags: [blog, jekyll, chirpy, github]
---


### Introduction
---
[chirpy-starter](https://github.com/cotes2020/chirpy-starter/)를 이용해서 GitHub Pages 블로그를 생성했다.

그러나 뭔가 맘에 들지 않는 부분들이 보인다. 전체적인 틀은 유지한 상태에서 입맛에 맞게 수정을 해보자.


### Gems 파일 위치 확인 및 테마 구성 요소 확인
---
블로그가 정상적으로 빌드 및 배포가 되었는데 Git Repository Root Directory에 테마에 필요한 구성요소들이 [jekyll-theme-chirpy](https://github.com/cotes2020/jekyll-theme-chirpy)와 다르게 보이지 않는다. 커스터마이징 하기 위해 수정해야 하는 파일들을 Git Repository Root Directory로 가져오는 작업이 필요하다.

1. [이전 글](https://woon7.github.io/posts/jekyll-theme-chirpy-windows/)에서 bundle 명령을 실행해 테마 사용을 위한 의존성들을 설치했다. Gemfile이 위치한 Git Repository Root Directory에서 다음 명령을 실행해 설치된 위치를 확인해보자.
    ```sh
    bundle info --path jekyll-theme-chirpy
    ```
    - 필자의 경우에는 `/root/gems/gems/jekyll-theme-chirpy-6.0.1`이라고 나온다.

2. 해당 디렉토리에 들어가서 다음 디렉토리들을 Git Repository Root Directory에 복사한다.
    > gems 디렉토리에서 의존성을 가져오지만 Root Directory에 해당 파일이 존재하면 Override한다.
    - _includes: 페이지를 구성하는 컴포넌트들이 정의되어있는 디렉토리
    - _layouts: 페이지 레이아웃 구성이 정의되어있는 디렉토리
    - _sass: 페이지 스타일 정의가 들어있는 디렉토리


### 사용하지 않는 소셜 링크 삭제하기
---
필자는 Twitter를 하지 않기 때문에 메뉴 하단과 Footer에 연결돼있는 Twitter 링크를 삭제해보겠다.

1. 먼저 `_config.yml`에 Twitter와 관련된 항목들을 주석처리한다.
    > Footer에 있는 Social Name에 연결되어 있는 링크 변경

    ``` yml
    # twitter:
    #   username: twitter_username # change to your twitter username

    social:
    # It will be displayed as the default author of the posts and the copyright owner in the Footer -> 필자는 GitHub 링크를 연결되게 했다.
    links:
        # The first element serves as the copyright owner's link
        - https://github.com/woon7 # change to your github homepage
        # - https://twitter.com/username # change to your twitter homepage
    ```

2. `_data/contact.yml`에 다음 항목을 주석처리한다.
    > Twitter 아이콘 삭제
    
    ``` yml
    # - type: twitter
    #   icon: "fab fa-twitter"
    ```


### Footer에 보기 싫은 테마 설명 삭제하기
---
다 좋은데 테마 설명이 은근 거슬린다. 지워버리자.

1. `_includes/footer.html`에 다음 항목을 주석처리한다.

    ![footer.html](/assets/img/2023-06-02-jekyll-theme-chirpy-customizing-1.png)

2. 어느 정도 깔끔해졌지만 css로 인해 자동 생성되는 `-`문자와 여백이 거슬린다. `_sass/addon/commons.scss`에 다음 항목을 주석처리한다.
    ```scss
    footer {
        p {
        width: auto;
    //      &:last-child {
    //        &::before {
    //          content: '-';
    //          margin: 0 0.75rem;
    //          opacity: 0.8;
    //        }
    //      }
        }
    }
    ```
