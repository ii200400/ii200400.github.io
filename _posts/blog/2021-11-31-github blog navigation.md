---
title:  "[Github Blog 제작기] 5. 상단 네비게이션과 아카이브"
excerpt: "상단 네비게이션을 아카이브를 활용하여 구현해보자!"

categories:
  - Github Blog
tags:
  - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

last_modified_at: 2021-12-03
---

# 개요

네비게이션에 대한 설명을 간략하게 진행하고 게시글을 정리하는데 큰 도움이 되는 카테고리 화면과 태그 화면 구현하는 방법을 보여줄 것이다!😎

결과적으로 카테고리 화면과 태그 화면 링크가 있는 네비게이션을 구현할 것이며 예시 결과물은 다음과 같다.

![카테고리 예시 사진](https://user-images.githubusercontent.com/19484971/144434450-58f62367-b672-444f-a2dc-e40829a9570b.PNG){: width="600" .align-center .border-grey}

![태그 예시 사진](https://user-images.githubusercontent.com/19484971/144434545-8f06c1a0-346e-4af9-aa90-d291c2535ec4.PNG){: 
width="600" .align-center .border-grey}

해당 게시물은 [minimal-mistakes pages](https://mmistakes.github.io/minimal-mistakes/docs/pages/)와 [minimal-mistakes navigation](https://mmistakes.github.io/minimal-mistakes/docs/navigation/), [minimal-mistakes layouts](https://mmistakes.github.io/minimal-mistakes/docs/layouts/#archive-layout), [jekyll-archives](https://github.com/jekyll/jekyll-archives)을 참고했음을 밝힌다.

# Navigation (네비게이션)

Jekyll에서는 최대한 많은 네비게이션 링크를 보여주는 디자인 패턴인 `priority plus`으로 `masthead` 링크를 보여준다고 한다. 글보다 사진으로 보는 것이 더 쉽다.

>![mm-priority-plus-masthead](https://user-images.githubusercontent.com/19484971/143985134-83b20769-a60c-47eb-bc23-277cda7c116f.gif){: width="600" .align-center}   
출처 - [minimal-mistakes/docs/navigation/](https://mmistakes.github.io/minimal-mistakes/docs/navigation/#masthead)

Jekyll의 `_data` 폴더의 `navigation.yml` 파일을 통해서 네비게이션을 쉽게 구현할 수 있다. `title`에 네비게이션 항목의 제목을 적고 `url`에 url을 적어놓는 것이 끝이다. 아래와 같이 `navigation.yml` 파일에 적어주자.

<script src="https://gist.github.com/ii200400/235e46fe6d475610a9d29814f475a7c5.js"></script>

블로그 오른쪽 위에 항상 있던 "Quick-Start Guide"라는 네이게이션이 바뀐 것을 볼 수 있지만, 아직은 눌러도 아무 화면도 보이지 않을 것이다. 해당 페이지는 `arcive`를 통해 구현할 수 있다. 바로 다음 단원으로 넘어가자!👇

💡가장 중요한 링크를 가장 먼저 작성하자! 메뉴 토글로 축약되지 않고 항상 보인다.
{: .notice--warning}

# archive (아카이브)

한글로는 보관소라고 직역된다, 깃허브 블로그에서는 일반적으로 게시글을 모아놓은 페이지를 의미하는 것 같다. 지금은 카테고리와 태그 아카이브를 만들어 위의 네비게이션과 연결이 되도록 만들 것이다. 

## Categories Archive

카테고리들이 정리된 페이지를 만들기 위해서는 우선 `_pages` 폴더를 만들고 `categories-archive.md` 파일을 만든다. 이때, 꼭 파일명이 똑같을 필요는 없다.

<script src="https://gist.github.com/ii200400/06c20feb09f888e7a83dff387534fc78.js"></script>

적용이 잘 되었다면 `permalink`에 설정한 주소로 이동하였을 때 아래와 같이 모든 카테고리가 보이는 정리된 화면이 나올 것이다.

![카테고리 예시2](https://user-images.githubusercontent.com/19484971/144558594-8e71d42a-e07a-459f-9ea7-0c48bc240d1d.PNG){: width="600" .align-center .border-grey}

필자의 블로그 카테고리가 하나 밖에 없어 좋은 예시가 되지 못한 것 같다. [minimal-mistakes/categories](https://mmistakes.github.io/minimal-mistakes/categories/) 페이지를 참고하자.

❗ `categories-archive.md` 파일의 `permalink`와 `navigation.yml` 파일의 `url`과 같아야 상단 네비게이션 버튼을 눌렀을 때 카테고리 화면이 불러온다.
{: .notice--danger}

## Category Archive

이번에는 카테고리 하나만 모아놓은 페이지를 만들어보자! `_pages` 폴더에 `category-archive.md` 파일을 만든다. 마찬가지로 파일명이 똑같을 필요는 없다.

<script src="https://gist.github.com/ii200400/d85157829536d4289573a13fa7f29fde.js"></script>

`taxonomy`에 꼭 게시물에 작성해준 YFM의 `categories` 중 하나를 입력해준다. 대소문자, 띄어쓰기 등 오타가 있다면 연관된 게시물을 모으지 못하므로 유의하자.

잘 적용이 되었다면 `permalink`에 적어놓은 url을 통해 아래와 같이 특정 카테고리만 모아놓은 화면을 볼 수 있다.

![카테고리 예시3](https://user-images.githubusercontent.com/19484971/144563865-e4ff1e9e-12f8-41a4-931d-7aa9586cbd38.PNG){: width="600" .align-center .border-grey}

## Tags, Tag Archive

`tags-archive.md`와 `tag-archive.md`도 카테고리와 비슷하게 해주면 된다.

<script src="https://gist.github.com/ii200400/18a454dba3154089b3a0887439ce1b1b.js"></script>

<script src="https://gist.github.com/ii200400/353d7e84ae170c1f9717e31cb5348d64.js"></script>

## Category, Tag Archive 링크 설정

게시물 아래의 태그나 카테고리 링크를 클릭하면 일반적으로는 `../categories/#카테고리명`으로 연결되지 `../categories/카테고리명`으로 연결되지 않을 것이다. 위에서 만든 페이지와 연결시키고 싶다면 `_config.yml`에서 아래와 같이 설정을 수정하자.

    category_archive:
    type: jekyll-archives # 수정! 카테고리 링크 주소를 변경하는 역할(category-list.html 참고)
    path: /categories/
    tag_archive:
    type: jekyll-archives  # 수정! 태그 링크 주소를 변경하는 역할(tag-list.html 참고)
    path: /tags/

## jekyll-archives plugin 후기

처음에 필자는 jekyll-archives plugin을 적용시켜서 블로그를 사용했는데 깃허브에서만 화면이 제대로 작동하지 않는 것을 확인하였다. 

검색을 해보니 **jekyll-archives plugin은 깃허브에서는 적용이 되지 않는다**고 한다. 여러가지 찾아보다가 [jekyll의 collection 기능으로 구현하는 방법](https://aneejian.com/automated-jekyll-archives-github-pages/#triggering-the-action-manually)도 찾았지만 이 방법은 jekyll를 잘 모르는 필자가 설정을 임의로 변경하는 방법을 몰라 그냥 결국 플러그인도 제거하고 `categories`와 `tags` 화면만 구현하여 사용하고 있다.😭

## ~~jekyll-archives plugin 사용~~

[jekyll-archives](https://github.com/jekyll/jekyll-archives)은 `tag-archive.md` 파일들과 `category-archive.md` 파일들을 자동으로 생성해주는 착한 플러그인이다. 하지만 `tags-archive.md`와 `categories-archive.md` 페이지는 만들어주지 않으므로 두 파일은 꼭 위의 글을 보고 직접 만들어주어야 한다.

### ~~jekyll-archives 설치~~

오랫만에 터미널을 열어서 아래의 명령어로 jekyll-archives를 설치해주자.

    gem install jekyll-archives

![캡처2](https://user-images.githubusercontent.com/19484971/144571518-3fade511-cdcb-4466-8dd8-cba6f036508e.PNG){: width="400" .align-center .border-grey}

### ~~Gemfile 수정~~

`Gemfile`이라는 확장자도 없는 파일에 아래의 명령어를 추가해준다.

    # Gemfile
    gem 'jekyll-archives' # 추가!

### ~~_config.yml 수정~~

<script src="https://gist.github.com/ii200400/bc047c7680071d772b86ea39d23cfe3d.js"></script>

이후 주소창에 각자 설정한 카테고리와 태그 명을 기반으로 url을 입력하여 찾아가보면 페이지가 자동으로 생성되어있는 것을 찾을 수 있다.

필자의 경우 `Github Blog`라는 카테고리를 사용하고 있으므로 `.../categories/Github-Blog/` 혹은 `.../categories/github-blog/`로 찾아갈 수 있었다.

### ~~다른 아카이브들~~

날짜에 따라서 아카이브를 생성할 수도 있는데 해당 게시글에서 모두 소개하기 어려우므로 [jekyll-archives 설정 가이드](https://github.com/jekyll/jekyll-archives/blob/master/docs/configuration.md) 링크를 남기고 생략하겠다.

## Defaults Front Matter 수정

수동으로 만든 `categories-archive.md` 파일과 `tags-archive.md` 파일에 사용자 프로파일을 보이고 화면을 넓게 사용하는 설정을 공통으로 사용하기 위해서 필자는 아래와 같이 `_config.yml`을 수정하였다.

<script src="https://gist.github.com/ii200400/927a1a2621c338c9a1db3c2ad153725f.js"></script>

그런데 이렇게 해도 `../categories/`와 `../tags/`에만 적용되고 `jekyll-archives`가 자동 생성한 아카이브들은 적용이 안되는 것을 볼 수 있다. 이 부분은 다른 파일을 수정해야 한다.

### ~~jekyll-archives 아카이브 설정~~

`jekyll-archives`가 자동 생성한 아카이브들은 html 파일에서 직접 설정해야 한다. `_config.yml`에서 `jekyll-archives` 설정 중 `layout`을 확인하고 해당하는 html 파일을 찾아가자 설정을 변경하지 않았다면 보통 `archive-taxonomy`일 것이다.

    layouts:
        category: archive-taxonomy
        tag: archive-taxonomy

`_layouts`의 `archive-taxonomy.html`파일에서 원하는 YFM을 넣어주면 된다. 필자는 아래의 YFM를 사용한다.

<script src="https://gist.github.com/ii200400/e48312d7e5dc86228fb055e9499f8c41.js"></script>

## Breadcrumbs 설정

`_config.yml` 총 정리 게시물에서도 언급했던 것이지만 breadcrumbs 설정을 사용하여 페이지의 경로를 보일 수 있다.

    breadcrumbs            : true

![breadcrumbs 예](https://user-images.githubusercontent.com/19484971/143559351-5d556170-debb-433a-9d81-4a9f742a87b8.PNG){: .align-center .border-grey}

### Breadcrumbs 라벨과 구분자

`_data/ui-text.yml` 파일에서 본인이 사용하는 언어에서 아래의 설정을 바꾸면 시작 링크의 라벨과 구분자("/")를 변경할 수 있다.

    breadcrumb_home_label : "Home"
    breadcrumb_separator  : "/"

# 마치며

상단 네비게이션 구성까지 마쳤다!🎉 조금은 블로그 같은 모습이 나오는데 아직 불편하고 아쉬운 점이 많다... 블로그 사이드바를 꾸미는 방법을 올릴까 생각도 하였지만 우선 블로그를 조금 꾸미고 진행하는 것으로 하려고 한다.

다음 게시글은 너무 못 생긴 블로그를 그나마 시원하게 만들 css들을 조금 소개할 예정이다. 웹을 이미 알고 있는 사람들의 경우 이미 적용했을 가능성도 있지만 필자처럼 웹 개발자가 아닌 경우에는 도움이 되는 글이 될 것이다!

~~블로그 구현이 너무 시간이 걸려서 회사에 입사를 한 후에 다시 작성을 시작할 것 같다.~~