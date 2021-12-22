---
layout: single
title: "카테고리 추가"
toc: true
toc_sticky: true
toc_label: "On This Page"
categories:
    - Blog
---

<br>

# 1. 일단 나 혼자 만들어보기 !!



 > 되는지 안되는지 1차 테스트 
 <font color='red'>- 실패</font>

 >되는지 안되는지 2차 테스트 
 <font color='red'>- 실패</font>

 >되는지 안되는지 3차 테스트
 <font color='orange'>- 카테고리가 추가된건 맞다. 근데 사이드바 생성이 이상하게 됨</font>

> 몇 시간 째 보고 있는데 아직 오류가 남아있다.
- 왼쪽 사이드바에 카테고리는 보이는데 링크는 구현이 안 됐다......


> 링크 구현에 성공했다. 근데 링크에 또 오류가 있다.

- 링크를 클릭해서 이동하면 글이 안보인다..........

아 해결됐다. archive-single.html ==> archive-single2.html 로 수정

기본 구조에 대해 공부 좀 해야겠다고 느꼈다..

<br>

# 2. 카테고리 추가 가이드

시작하기에 앞서 모든 코드들은 <mark style = 'background-color : fff5b1'>@ansohxxn</mark>님의 글을 인용 했다는 점을 염두하자 !!

<br>

## 2-1. __pages 폴더에 categories 폴더 생성_

<br>

먼저 _pages 폴더에 categories 라는 폴더를 생성한 다음,

자신이 원하는 카테고리의 markdown 파일을 categories 폴더 내에 만들어준다 !!

ex)
    
    category-blog.md
    category-c.md
    category-cpp.md

와 같은 이름명으로 파일을 생성한다.

<br>

![image](https://user-images.githubusercontent.com/96330958/147082891-b95e0b3a-4305-4164-b4f6-28d6777e8faf.png)

이런 식으로 만들어주면 된다 !!

<br>

- <font color = 'red'> 만약 _pages 라는 폴더 자체가 없다면, 그냥 직접 new file 누르고 _pages 라는 폴더를 만들면 된다.  </font> 

<br>

## 2-1. _생성한 md 파일에 코드 삽입_

<br>

생성한 category-cpp.md 파일에 다음과 같은 코드를 붙여넣자 !!

```java
---
title: "C++ 프로그래밍" // 페이지의 이름
layout: archive
permalink: categories/cpp
author_profile: true // 페이지에서 자신의 프로필을 보이게 할 것인지 !!
sidebar_main: true // 변수값 !! 
---


{% assign posts = site.categories.Cpp %}
{% for post in posts %} {% include archive-single2.html type=page.entries_layout %} {% endfor %}
```

<br>

## 2-2. __includes 폴더 내에 archive-single2.html 파일 생성_

<br>

![image](https://user-images.githubusercontent.com/96330958/147084348-d5b34de4-e04b-4c6c-b803-4297e0bd5af3.png)

<br>

이런 식으로 생성해주면 된다 !!

또한 생성한 archive-single2.html 파일에 아래 코드를 붙여넣자 !!

<br>


```java

{% if post.header.teaser %}
  {% capture teaser %}{{ post.header.teaser }}{% endcapture %}
{% else %}
  {% assign teaser = site.teaser %}
{% endif %}

{% if post.id %}
  {% assign title = post.title | markdownify | remove: "<p>" | remove: "</p>" %}
{% else %}
  {% assign title = post.title %}
{% endif %}

<div class="{{ include.type | default: "list" }}__item">
    <article class="archive-item">
        <div>
            <span>
              <a href="{{ post.url }}">{{post.title}}</a>
            </span>
            <small> 
              <i class="fas fa-fw fa-calendar-alt" aria-hidden="true"> </i>{{ post.date | date: " %Y.%m.%d" }} 
              {% if site.category_archive.type and post.categories[0] and site.tag_archive.type and post.tags[0] %}
                {%- include post__taxonomy.html -%}
              {% endif %}
            </small>
        </div>
      </article>
</div>

```

<br>

## 2-3. __includes 폴더 내에 post__taxonomy.html 파일 생성_

<br>

참고로 post__taxonomy.html 이 파일 이름 .. <font color = 'red'> 언더바 두 개이다. </font>

실수하지 말자 !!

<br>

![image](https://user-images.githubusercontent.com/96330958/147085073-75361356-492a-4708-b2e8-8a5d7f9c8e14.png)

<br>

post__taxonomy.html 파일을 만들어줬다면, 아래 코드를 붙여넣고 commit 하자 !!

<br>


```java

{%- if site.category_archive.type and post.categories[0] -%}
    {%- case site.category_archive.type -%}
        {%- when "liquid" -%}
        {%- assign path_type = "#" -%}
        {%- when "jekyll-archives" -%}
        {%- assign path_type = nil -%}
    {%- endcase -%}

    {% case site.tag_archive.type %}
        {% when "liquid" %}
            {% assign path_type = "#" %}
        {% when "jekyll-archives" %}
            {% assign path_type = nil %}
    {% endcase %}

    {%- if site.category_archive.path and site.tag_archive.path -%}
        {%- capture post_categories -%}{%- for category in post.categories -%}{{ category | downcase }}|{{ category }}{%- unless forloop.last -%},{%- endunless -%}{%- endfor -%}{%- endcapture -%}
        {%- assign category_hashes = post_categories | split: ',' | sort -%}
        {% capture post_tags %}{% for tag in post.tags %}{{ tag | downcase }}|{{ tag }}{% unless forloop.last %},{% endunless %}{% endfor %}{% endcapture %}
        {% assign tag_hashes = post_tags | split: ',' | sort %}
        <span class="page__taxonomy">
            <span itemprop="keywords">
                {%- for hash in category_hashes -%}
                    {%- assign keyValue = hash | split: '|' -%}
                    {%- capture category_word -%}{{ keyValue[1] | strip_newlines }}{%- endcapture -%}
                    <a href="{{ category_word | slugify | prepend: path_type | prepend: site.category_archive.path | relative_url }}" class="page__taxonomy-item-category" rel="tag">{{ category_word }}</a>{%- unless forloop.last -%}<span class="sep"> </span>{%- endunless -%}
                {%- endfor -%}
                {% for hash in tag_hashes %}
                    {% assign keyValue = hash | split: '|' %}
                    {% capture tag_word %}{{ keyValue[1] | strip_newlines }}{% endcapture %}
                    <a href="{{ tag_word | slugify | prepend: path_type | prepend: site.tag_archive.path | relative_url }}" class="page__taxonomy-item-tag" rel="tag">{{ tag_word }}</a>{% unless forloop.last %}<span class="sep"> </span>{% endunless %}
                {% endfor %}
            </span>
        </span>
    {%- endif -%}
{%- endif -%}

```

<br>

## 2-4. __includes 폴더에 nav_list_main 파일 생성_

<br>

```java

{% assign sum = site.posts | size %}

<nav class="nav__list">
  <input id="ac-toc" name="accordion-toc" type="checkbox" />
  <label for="ac-toc">{{ site.data.ui-text[site.locale].menu_label }}</label>
  <ul class="nav__items" id="category_tag_menu"> 

      <!--전체 글 수-->

      <li>
            📂 <span style="font-family:'Cafe24Oneprettynight';">전체 글 수</style> <span style="font-family:'Coming Soon';">{{sum}}</style> <span style="font-family:'Cafe24Oneprettynight';">개</style> // 원한다면 자신이 원하는 문구로 꾸밀 수 있음 !!
            //나는 전체 글 수 --> Total number of posts 로 바꿨다 !!
      </li>
      <li>
        <!--span 태그로 카테고리들을 크게 분류 ex) C/C++/C#-->
        <span class="nav__sub-title">C/C++/C#</span>
            <!--ul 태그로 같은 카테고리들 모아둔 페이지들 나열-->
            <ul>
                <!--Cpp 카테고리 글들을 모아둔 페이지인 /categories/cpp 주소의 글로 링크 연결-->
                <!--category[1].size 로 해당 카테고리를 가진 글의 개수 표시--> 
                {% for category in site.categories %}
                    {% if category[0] == "Cpp" %}
                        <li><a href="/categories/cpp" class="">C ++ ({{category[1].size}})</a></li>
                    {% endif %}
                {% endfor %}
            </ul>
            <ul>
                {% for category in site.categories %}
                    {% if category[0] == "STL" %}
                        <li><a href="/categories/stl" class="">C++ STL & 표준 ({{category[1].size}})</a></li>
                    {% endif %}
                {% endfor %}
            </ul>
        <span class="nav__sub-title">Coding Test</span>
            <ul>
                {% for category in site.categories %}
                    {% if category[0] == "Algorithm" %}
                        <li><a href="/categories/algorithm" class="">알고리즘 구현 (with C++) ({{category[1].size}})</a></li>
                    {% endif %}
                {% endfor %}
            </ul>
            <ul>
                {% for category in site.categories %}
                    {% if category[0] == "Programmers" %}
                        <li><a href="/categories/programmers" class="">프로그래머스 ({{category[1].size}})</a></li>
                    {% endif %}
                {% endfor %}
            </ul>
      </li>
  </ul>
</nav>

```

<br> 

nav_list_main 파일이 카테고리의 부제목을 정해준다 !!

자신이 원하는 부제목으로 마음껏 수정해주도록 하자.

<br>

## 2-5. __includes 폴더 내에 있는 siderbar.html 파일 수정

<br>

```java
  {% if page.sidebar_main %}
    {% include nav_list_main %}
  {% endif %}
  ```

  위와 같은 코드를 맨 아래에 붙여넣어주자 !!

  이 코드는 위에서 작성한 nav_list_main을 왼쪽 사이드바에 반영하는 코드이다 !!

  <br>

  ## 2-6. __config.yml_ 폴더 수정

  <br> 

  깃허브 블로그를 처음 시작했을 때 접했던 폴더일 것이다 !!

  254 번째 줄을 아래와 같이 코드를 수정해주자 !!

  <br>

  ```java

# Defaults
defaults:
  # _posts
  - scope:
      path: ""
      type: posts
    values:
      layout: single
      author_profile: true
      read_time: true
      comments: true
      share: true
      related: true
      mathjax: true
      sidebar_main: true

  ```

     siderbar_main: true

을 사용해서 사이드바가 활성화 되게끔 해주면 된다.

<br>

## 3. 이해했는가?

<br>

난 이해 못 했다. ^^ 

그래도 꽤나 공부가 된 것 같다 !!!