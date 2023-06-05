---
title: "[Blog] Chirpy Jekyll Theme (1) - Windows 환경에서 GitHub Pages 블로그 생성"
date: 2023-06-01 01:00:00 +0900
categories: [Blog]
tags: [blog, jekyll, chirpy, github, windows]
---


### Introduction
---
Windows 환경에서 Chirpy 테마를 적용해서 GitHub Pages를 만드려고 하면 무슨 일에서인지 잘 되지 않는다.  
여러 삽질 끝에 배포에 성공한 방법을 공유하고자 한다.


### Installation
---
1. 관리자 모드에서 Windows PowerShell을 켜서 다음 명령을 실행한다.
    ```ps
    wsl --install
    ```
    - wsl 명령어를 인식하지 못하면 Windows를 최신 버전으로 업데이트 해주는 것이 좋다.

2. Microsoft Store에 들어가 Windows Terminal 앱을 설치 및 실행한다. (Optional)
    - 윈도우 환경에서 터미널을 편하게 사용할 수 있어서 추천

3. Ubuntu를 실행하고 다음을 차례대로 입력한다.
    ```sh
    sudo apt-get update
    sudo apt-get install ruby-full build-essential zlib1g-dev
    echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
    echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
    echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
    source ~/.bashrc
    gem install jekyll bundler
    ```
    - Ubuntu 접속에 실패하는 경우
      - Windows 기능 켜기/끄기 -> Hyper-V 활성화
      - BIOS -> 가상화 기술 활성화


### Create a new repository
---
1. [chirpy-starter](https://github.com/cotes2020/chirpy-starter/)를 방문해서 새로운 Repository를 생성한다.
    1. Use this template 클릭
    2. Create a new repository 클릭
    3. Repository name에 `username`.github.io 입력
    4. Create repository from template 클릭
    5. 생성된 Repository의 Git 주소 복사

2. Ubuntu로 돌아가서 git clone 실행
    ```sh
    git clone https://github.com/{username}/{username}.github.io.git
    ```


### Initialization
---
1. Clone한 Repository의 루트 디렉토리에서 다음 명령 실행
    ```sh
    bundle
    ```

2. Repository의 루트 디렉토리에 있는 _config.yml에 다음 항목 수정
    - title
    - tagline
    - description
    - url: https://`username`.github.io
    - github
      - username
    - social
      - name
      - email
      - links
    - avatar: Repository 루트 디렉토리 기준 이미지 경로 지정


### Local execution
---
1. Repository의 루트 디렉토리에서 다음 명령 실행
    ```sh
    bundle exec jekyll s
    ```

2. http://localhost:4000 접속


### Push to remote repository
---
1. GitHub 설정
    1. https://github.com/`username`/`username`.github.io/settings/actions 접속
        -  Actions permissions - Allow all actions and reusable workflows 선택
    2. https://github.com/`username`/`username`.github.io/settings/pages 접속
        - Build and deployment - Source에서 GitHub Actions 선택

2. Repository에서 다음 명령 실행
    ```sh
    git add .
    git commit -m "Initial commit"
    git push
    ```

3. https://github.com/`username`/`username`.github.io/actions 에서 배포 현황 확인

4. 배포 완료 후 https://`username`.github.io/ 접속해서 최종 결과 확인

5. 인증 문제로 Push가 안되는 경우 (Optional)
    1. [GitHub - Personal access tokens](https://github.com/settings/tokens) 접속
    2. Generate new token (classic)
    3. Scope 허용
        - repo
        - workflow
        - read:org
        - gist
    4. token 값 복사 및 백업
    5. 다시 push 시도, pw에 token 값 입력
    6. 매번 token 값 입력하기 귀찮으면 다음 명령 실행
        ```sh
        git config credential.helper store
        ```


### References
---
- [Create a free static website using Github Pages and Jekyll](https://dev.to/yashnigam/create-a-free-static-website-using-github-pages-and-jekyll-41a9)
