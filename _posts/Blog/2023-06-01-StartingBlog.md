---
title: "[개발자 블로그] Windows 환경에서 Jekyll의 Chirpy 테마로 깃허브 블로그 만들기"
date: 2023-06-01 +0900
categories: [Blog]
tags: [blog, chirpy, jekyll, windows]
---

### Installation

1. 관리자 모드에서 Windows PowerShell을 켜서 다음 명령을 실행한다.
```ps
wsl --install
```

2. Microsoft Store에 들어가 Windows Terminal 앱을 설치 및 실행한다. (Optional)
- 윈도우 환경에서 터미널을 편하게 사용할 수 있어서 추천

3. Ubuntu를 실행하고 다음을 차례대로 입력한다.
```sh
sudo apt-get install ruby-full build-essential zlib1g-dev
echo '# Install Ruby Gems to ~/gems' >> ~/.bashrc
echo 'export GEM_HOME="$HOME/gems"' >> ~/.bashrc
echo 'export PATH="$HOME/gems/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
gem install jekyll bundler
```

4. [chirpy-starter](https://github.com/cotes2020/chirpy-starter/)를 방문해서 새로운 Repository를 생성한다.
    1. Use this template 클릭
    2. Create a new repository 클릭
    3. Repository name에 ***username***.github.io 입력
    4. Create repository from template 클릭
    5. 생성된 Repository의 Git 주소 복사

5. Ubuntu로 돌아가서 git clone 실행
```sh
git clone https://github.com/username/username.github.io.git
```

6. Repository의 루트 디렉토리에 있는 _config.yml에 다음 항목 수정
- title
- tagline
- description
- url: https://***username***.github.io
- github
  - username
- social
  - name
  - email
  - links
- avatar: Repository 루트 디렉토리 기준 이미지 경로 지정

### References
[Create a free static website using Github Pages and Jekyll](https://dev.to/yashnigam/create-a-free-static-website-using-github-pages-and-jekyll-41a9)