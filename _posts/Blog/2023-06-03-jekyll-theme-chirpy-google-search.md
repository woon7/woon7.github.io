---
title: "[Blog] Chirpy Jekyll Theme Google 검색 노출하기"
date: 2023-06-03 +0900
categories: [Blog]
tags: [blog, jekyll, chirpy, google, sitemap]
---


### Introduction
---
기껏 이쁘게 블로그를 꾸미고 소통을 위한 댓글 기능까지 추가했건만 손님이 찾아오지 않는다면 무슨 소용이겠는가?  
구글에게 내 블로그를 소개해주자.


### Google Search Console에 사이트 소유권 등록
---
1. [Google Search Console](https://search.google.com/search-console/about) 접속
2. `시작하기` 클릭 -> URL 접두어에 사이트 주소 입력 -> `계속` 클릭
3. 소유권 확인 -> 다른 확인 방법 -> HTML 태그 -> `복사` 클릭
    - 해당 화면 그대로 두고 다음 작업
4. `_config.yml`에 메타태그 삽입
    ```yml
    google_site_verification: {복사한 메타태그 삽입}
    ```
5. git push
6. 배포 완료 대기
7. 메타태그 복사한 화면 복귀 -> `확인` 클릭
    - `소유권이 확인됨` 표시가 안되면 잠깐 대기 후 재시도


### sitemap.xml 등록
---
1. Google Search Console -> Sitemaps -> 새 사이트맵 추가에 `sitemap.xml` 입력 -> `제출` 클릭
2. 제출된 사이트맵에서 성공 여부 확인


### 검색 노출 여부 확인
---
안타깝게도 사이트맵을 등록한다고 바로 검색되지는 않는다.  
3일 정도 지난 후에 구글 창에 `site:username.github.io`를 입력해 검색해보자.


### References
---
- [Jekyll 테마에서 구글 검색 노출 등록하기](https://www.irgroup.org/posts/jekyll-google-search/)
