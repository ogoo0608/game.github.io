---
layout: single
title: "깃허브 상단에 검색창 구현하기"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Blog
---

<br>

갑자기 깃허브 상단에 검색창을 추가하고 싶다는 생각이 들었다.

블로그에 검색창이 없으면 섭하지 않은가 ..

암튼 오늘은 검색창을 구현해 볼 것이다 !!

<br>

## 1. __pages_ 폴더에 search.md 파일 생성

<br>

가장 먼저 _pages 폴더에 new file 을 누른 후 search.md 라는 파일을 생성해준다.

그 다음 아래와 같은 코드를 붙여넣어주자.

<br>

```js
    ---
    title: Search
    layout: search
    permalink: /search/
    ---
```

<br>

## 2. navigation.yml 파일 수정

<br>

그 다음으로는 navigation.yml 파일을 수정해주면 된다.

이 파일은 상단 메뉴바를 구성하는 파일이다 !!

<br>

```js
# main links
main:
  - title: "Home"
    url: https://ogoo0608.github.io/
  # - title: "Sample Posts"
  #   url: /year-archive/
  # - title: "Sample Collections"
  #   url: /collection-archive/
  # - title: "Sitemap"
  #   url: /sitemap/
  ```

  <br>

  처음에는 이렇게 되어 있을텐데, 하단 부분에 아래와 같은 코드를 붙여넣어주자.

  <br>


```js
    - title: "Search"
    url: /search/
```

<br>

놀랍게도 끝이다 !! 매우 간단하다.