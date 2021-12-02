---
title:  "[Github Blog 제작기] 3. Minimal Mistake 의 설정파일(_config.yml) 총 정리 ❗️스크롤 압박"
excerpt: "필요없는 파일을 지우고 블로그 설정을 알아보자!"

categories:
  - Github Blog
tags:
  - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

last_modified_at: 2021-11-29
---

# 개요

블로그 게시글을 올리기 전에 필요없는 파일 삭제와 블로그 설정을 변경을 먼저 진행하는 것이 순서에 맞겠다는 생각이 들어서 빠르게 살펴보고 게시글 만드는 것으로 넘어가보려고 했는데.. 목차보면 알겠지만 가이드를 참고하면서 엄청난 길이의 포스팅이 되어버렸다. 하하!🤗

전부 확인할 필요는 없고 목차를 보고 필요한 설정만 적용하는 것을 추천한다! 해당 글은 [Quick-Start Guide](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide)를 참고하여 쓰여졌음을 밝힌다.

# 1. 필요없는 파일 삭제🔥

Minimal Mistakes의 공식 [Quick-Start Guide #remove-the-unnecessary](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/#remove-the-unnecessary)에 따르면 아래의 파일들은 필요가 없으니 삭제하라고 쓰여있지만, 그 중 2개는 jekyll 서버를 사용할 때 꼭 필요한 파일로 지우면 안된다. 이 때문에 필자는 jekyll 서버를 실행시킬 때 에러를 2번 더 보아야만 했다.😒

    .editorconfig // 지우면 안되는 파일 1
    .gitattributes
    .github
    /docs
    /test
    CHANGELOG.md
    minimal-mistakes-jekyll.gemspec // 지우면 안되는 파일 2
    README.md
    screenshot-layouts.png
    screenshot.png

# 2. 블로그 설정 변경

파일 내부에 _config.yml이라는 이름의 설정 파일을 알아보고 수정할 것이다. 파일의 내용을 간단히 수정하는 것 만으로도 자신만의 블로그를 꾸미는 첫걸음이 된다.

설정파일을 바꾸면 jekyll 서버를 꼭 끄고 켜주어야만 적용이 되는 것을 기억하자!☝️
{: .notice--warning}

## 테마 설정

### theme

Ruby gem 버전의 테마를 사용하는 사람들은 아래의 줄을 활성화 시키라고 하는데, 필자는 깃허브에서 Fork 기능을 사용해서인지 딱히 사용하지 않아도 상관이 없었다. 깃허브를 통해 Minimal Mistakes 테마를 선택한 사람들이라면 무시해도 상관 없는 것 같다.

    # theme                  : "minimal-mistakes-jekyll"
    # remote_theme           : "mmistakes/minimal-mistakes"

### minimal_mistakes_skin

Minimal Mistakes에는 `default`, `air`, `aqua`, `contrast`, `dark`, `dirt`, `neon`, `mint`, `plum`, `sunrise` 10가지 스킨이 있다. [Quick-Start Guide #skin](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#skin)에 각 스킨 미리보기 화면이 있으니 참고해서 원하는 스킨으로 바꾸자. 단순히 스킨을 하나씩 바꿔보면서 직접 확인하는 것도 하나의 재미이다.😀

    minimal_mistakes_skin    : "default"
    # "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

## 사이트 설정

### locale (로컬라이징)

각 나라에 맞는 코드를 넣으면 해당 나라에 맞는 로컬라이징을 지원해준다. 한국의 코드는 ko-KR 이다!👏   
만약 다른 언어가 좋다! 하시는 분들은 [코드 테이블](https://docs.microsoft.com/en-us/previous-versions/commerce-server/ee825488(v=cs.20)?redirectedfrom=MSDN)을 참고하길 바란다.

    locale                   : "ko-KR"

다양한 곳에서 영어가 한글이 된 것을 확인할 수 있지만, 가장 눈에 띄는 변화는 블로그의 메인페이지의 `Recent Posts`가 `최근 포스트`라는 문구로 바뀐 점일 것이다. `최근 포스트`등의 로컬라이징이 마음에 안들어서 글자를 바꾸고 싶다면 UI 택스트 데이터 파일을 변경하면 되는데 해당 내용은 다음으로 넘기고 지금은 설정에만 집중하겠다.

### title, title_separator, subtitle

위의 세 설정은 같이 설명하는 것이 더 편하기에 한꺼번에 예시를 보이겠다. 사이트의 제목과 부제목은 파악이 쉬운데... 구분자는 어디에서 쓰이는  솔직히 찾기 어려웠다.

    title                    : "이것은 사이트 제목입니다"
    title_separator          : "|구분자|"
    subtitle                 : "이것은 사이트 부제목입니다"

![사이드 제목 예시](https://user-images.githubusercontent.com/19484971/143521126-19e23ccc-16ac-47cd-9a95-549179915366.png){: .border-grey}

구분자는 게시글에 들어갔을 때, 탭 설명창(Tab Hover Cards)에서 볼 수 있었다. ❔왜 이때만 보이는지는 잘 모르겠다;;

### name

말그대로 사이트 작성자의 이름이 들어가는 부분, 그런데 의외로 예상과는 다른 위치에 들어간다.

    name                     : "이것은 작성자 이름입니다"

![작성자 이름 예시](https://user-images.githubusercontent.com/19484971/143524332-3b08f76f-abc7-4cde-b8ff-888b3a96bb21.png)

왜 여기로 들어가는지는 필자도 잘 모르겠다, 웹 공부를 덜해서 잘 모르는 건가..❔

### description

사이트에 대한 간단한 설명을 넣는 부분이다. 웹 페이지에 나타나는 부분 없이 변수에만 저장이 되어있는 것을 페이지 소스에서 확인할 수 있었다. html에서 해당 변수를 사용하지 않은 것 같다. 만약 해당 글을 가지고 커스텀 한다면 참고하기를 바란다.

    description              : "이것은 사이트 설명문 입니다"

![페이지 소스](https://user-images.githubusercontent.com/19484971/143526158-e46234d4-0c20-4303-ae2f-7e818e3e226e.PNG){: .border-grey}

### url

블로그의 호스트를 설정하는 부분으로 깃허브를 통해 호스팅을 하고있다면 `"https://닉네임.github.io"`과 비슷한 내용이 들어간다. 이 부분을 잘못 설정한다면 블로그를 아예 못 찾아가게 된다.

필자의 경우 아래와 같이 사용하고 있다.

    url                      : "https://ii200400.github.io"

### baseurl

공식 홈페이지에서도 Jekyll 커뮤니티에서 약간의 혼란을 빚는 옵션이라고 쓰여있다.🤣     
설명을 위해 [특정 블로그 링크](https://byparker.com/blog/2014/clearing-up-confusion-around-baseurl/)를 제공해주었는데 내용은 아래와 같다.

가장 기본이 되는 페이지(index.html)을 보여줄 때 위의 url 뒤에 붙는 주소이다. 그렇다면 그냥 url에 `"https://닉네임.github.io/someurl"`을 사용하면 될 것 같은데 굳이 이렇게 따로 작성하는 이유는 바로! __jekyll 서버 때문이다.__

한 개발자가 아래와 같이 설정했다고 가정을 하겠다.

    url                      : "https://ii200400.github.io/someurl"
    baseurl                  : ""

그러면 깃허브 서버를 통한 홈페이지는 `https://ii200400.github.io/someurl/`을 통해 접근할 수 있고 jekyll 로컬 서버를 통한 홈페이지는 `http://127.0.0.1:4000`을 통해 접근할 수 있다.

아.. 무언가 불편함을 느낀 개발자가 설정을 수정하여 아래와 같이 바꾸었다면🤔

    url                      : "https://ii200400.github.io"
    baseurl                  : "/someurl"

깃허브 서버를 통한 홈페이지는 `https://ii200400.github.io/someurl/`을 통해 접근할 수 있고 jekyll 로컬 서버를 통한 홈페이지 또한 `http://127.0.0.1:4000/someurl/`을 통해 접근할 수 있게 된다.👍

### repository

해당 설정은 어디에서 사용되는지는 모르겠지만 작성을 정확히 하지 않으면 Jekyll 서버에서 에러가 생길수도 있다고 한다. 형식은 `"깃허브 닉네임/깃허브 레포지토리 이름"`으로 깃허브 블로그 레포지토리를 확인하면 쉽다.

![repository 설정](https://user-images.githubusercontent.com/19484971/143536774-b95df98a-fad0-4d8b-8c1c-7404949928c8.PNG){: width="400" .align-center}

    repository               : "ii200400/ii200400.github.io"

각자가 만든 레포를 확인하고 설정에 넣어주면 된다!👍

❗️해당 설정을 작성을 정확히 하지 않거나 원격 저장소와 `origin`으로 연결을 하지 않으면 Jekyll 서버에서 에러가 생긴다.
{: .notice--danger}

### teaser

영화 티저 영상의 그 티저이다. 관련 게시글 목록에서 게시글에 대한 티저 이미지를 설정한다. 아래의 테스트 이미지(test.PNG)를 사용하여 아래와 같이 적용시켜보겠다. 보통 이미지들은 assets 파일에 넣으므로 테스트 이미지를 해당 파일에 넣고 진행했다.

![테스트 이미지](https://user-images.githubusercontent.com/19484971/143539160-66bfbd88-1265-4283-8737-8d763df8edcc.PNG){: width="50" .align-center}

    teaser                   : "/assets/test.PNG"

![teaser 확인](https://user-images.githubusercontent.com/19484971/143543572-7d64e5f6-f610-4a59-9270-92961b723e74.PNG){: .border-grey}

게시글 하단부와 footer 사이에서 관련 게시글 목록을 확인할 수 있다. 즉, 게시글을 작성하지 않았다면 확인할 수 없다.😢    
필자의 경우 블로그를 이쁘게 꾸미기 보다는 정리를 위해서 만든 것이므로 사용하지 않았다.

**500x300 크기의 이미지를 추천**하며 비율이 맞지 않으면 ✂️잘린다.
{: .notice--danger}

💡티저 이미지는 각 게시물마다 [YFM(YAML Front Matter)](/github%20blog/github-blog-post-writing/#yfmyaml-front-matter)을 통해 따로 지정해줄 수 있다.
{: .notice--warning}

### logo, masthead_title

`logo`는 이름 그대로 로고 이미지를 설정할 수 있다는 것을 알 수 있는데  `masthead_title`는 무엇인지 몰라서 찾아보니 `title`을 덮어쓴다는(override) 정도의 가이드 밖에 없었다.

위에서 사용한 예시 이미지를 그대로 사용해서 아래와 같이 적용시켜보면

    logo                     : "/assets/test.PNG"
    masthead_title           : "masthead_title!"

![logo, masthead_title 예시](https://user-images.githubusercontent.com/19484971/143555587-5c030fcb-b6d2-445b-848e-beae3d9314df.PNG)
{: width="400" .align-center .border-grey}

이렇게 된다... `masthead_title`는 정말 무슨 기능인지 모르겠다;;🤨   
참고로 다른 블로거분 중에서는 `title`과 `subtitle`을 공란으로 두고 로고만 사용하는 것도 보았다.

이미지의 **추천 크기는 88x88** 이다.
{: .notice--warning}

### breadcrumbs (사이트 경로) (Beta)

현재 페이지의 경로를 페이지 윗부분에 보여준다.

    breadcrumbs            : true

![breadcrumbs 예](https://user-images.githubusercontent.com/19484971/143559351-5d556170-debb-433a-9d81-4a9f742a87b8.PNG){: .align-center .border-grey}

문제는 `breadcrumbs`가 페이지에 항상 적용되지는 않는다는 것이다. 이 기능이 베타인 이유이기도 한 것 같다. 적용이 확실히 되기 위해서 가이드는 2가지 방법을 소개해주었다.✍️

#### 1. category based permalink 사용

[YFM(YAML Front Matter)](/github%20blog/github-blog-post-writing/#yfmyaml-front-matter)를 통해 각 게시물에 permalink를 적용시킬 수 있다, 각 게시물에 페이지의 경로를 일일이 작성해주어야 해서 필자는 아래의 방법을 사용한다.

#### 2. pages 생성 혹은 jekyll-archives plugin 사용

카테고리들을 만들어 관련 게시물들을 모아두는 방식으로 2가지 방법으로 구현할 수 있다.

`_pages` 라는 파일에 `archive`들을 만들어 카테고리를 정리하는 방법과 [jekyll-archives](https://github.com/jekyll/jekyll-archives)라는 플러그인을 활용하여 태그나 카테고리를 기반으로 자동 정리하는 방법이다.

필자는 `jekyll-archives`을 사용하려다가 생각과는 다르게 작동하는 것을 확인하고 `_pages` 폴더에 `archive`들을 만들어 카테고리를 정리하는 방법을 사용하고 있다. [다른 게시글 링크 추가 요망]()에서 소개할 예정이므로 조금 기다려주길 바란다.🙏

만약 `jekyll-archives`에 관심이 있다면 [아카이브 설정 가이드](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#archive-settings)를 참고하자.

### date_format, words_per_minute

[게시글 업데이트 날짜 및 읽는 시간 표시](/github%20blog/github-blog-config-setting/#show_date-read_time)와 같이 병행해야 적용이 잘 되었는지 확인이 가능하다.

`date_format`은 게시물 날짜를 표시할 형식을, `words_per_minute`은 분당 읽는 문자 수를 지정한다. `date_format`은 기본적으로 설정에 있지 않기 때문에 해당 줄을 ✒️추가해주어야 한다. 이 때문인지 날짜 형식을 html을 직접 바꿔서 수정한 블로거가 참 많았다. 꼭 설정에서 간단하게 수정하기를 바란다.

📅[루비의 날짜 표기 형식](https://www.shortcutfoo.com/app/dojos/ruby-date-format-strftime/cheatsheet)을 보고 직접 날짜 형식을 지정해줄 수 있다.

    date_format              : "%Y년 %m월 %d일"
    words_per_minute         : 200

![date_format 예시](https://user-images.githubusercontent.com/19484971/143603306-b475df91-53af-4799-968e-654270ab1da5.PNG){: .border-grey}

### comments provider (댓글 엔진)

댓글 기능을 어떤 provider를 통해서 구현할지 설정하는 곳이다. 각 provider에 따른 적용 방법은 [가이드를 참고](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#comments)하여 각자 원하는 방법을 골라서 구현해보자.

필자의 경우 `utterances`를 사용할 예정이다. (언제 넣을지는 아무도 모른다.😅)

### atom_feed

feed 라는 것을 커스텀할 수 있다. 기본적으로 `feed.xml`을 사용하고 있다는데 현 페이지의 <head> 요소 부터 footer를 포함한 전체 내용을 보여준다고 한다.

    atom_feed:
      path                   : # 어떤 feed를 사용할지, 기본값은 feed.xml
      hide                   : # feed 아이콘을 숨길지, 기본값은 false

참고로 feed 이미지는 이것이다.

![feed image](https://user-images.githubusercontent.com/19484971/143670994-e7c28a14-4235-4a07-bcea-99369a68d980.PNG)

### search, search_full_content, search_provider

검색에 관한 설정이다. 검색 엔진은 기본적으로는 `Lunr`가 적용되지만 원한다면 `Algolia`나 `Google Custom Search Engine`을 사용할 수 있다고 한다. 자세한 사항은 [Site search 가이드](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#site-search)를 참고바란다.

    search                   : # 검색 엔진 사용 여부, 기본값은 false
    search_full_content      : # 검색시 본문 전체를 대상으로 할지, 기본값은 false
    search_provider          : # 어떤 검색 엔진을 사용할지, 기본값은 lunr (default)이며 algolia, google 사용가능

📝`search_full_content`을 false로 두고 검색을 하면 포스트의 앞 50자들만 검색 대상에 들어간다고 한다. ture로 설정하면 본문 전체를 대상으로 하지만 느려진다.
{: .notice--warning}

> ![masthead-search](https://user-images.githubusercontent.com/19484971/143670185-726f5724-6ef5-4dc3-86cf-217a946c5d9f.gif)   
출처 - [minimal-mistakes/docs](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#site-search)

## SEO 설정

  > 검색 엔진 최적화(영어: search engine optimization, SEO)는 검색 엔진으로부터 웹사이트나 웹페이지에 대한 웹사이트 트래픽의 품질과 양을 개선하는 과정이다.   
  출처 - [wiki/검색_엔진_최적화](https://ko.wikipedia.org/wiki/%EA%B2%80%EC%83%89_%EC%97%94%EC%A7%84_%EC%B5%9C%EC%A0%81%ED%99%94)

`google`, `bing`, `naver` 등 다양한 검색엔진을 통해 블로그를 찾아올 수 있도록 블로그 소유권을 인증하는 설정같다.🤔 이 또한 각 검색엔진에 따라 인증을 각기 해주어야 하므로 [SEO 가이드를 참고](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#google-search-console)하길 바란다.

📝Google Analytics를 통해 사이트 인증을 이미 확인한 경우에는 `google_site_verification` 설정을 꼭 할 필요는 없다.
{: .notice--warning}

## 소셜 공유 설정

필자가 SNS을 하나도 하지 않는 관계로 테스트를 하나도 할 수 없었다. SNS와 연결하여 블로그를 운영하고 싶은 사람이라면 [social sharing 가이드](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#twitter-cards-and-facebook-open-graph)를 확인하자.

블로그와 SNS를 연결했을 시 아래와 같은 화면을 볼 수 있다고 한다.👇

> ![facebook-share-example](https://user-images.githubusercontent.com/19484971/143674028-99c4242b-9ff9-4b4e-b6d5-cd090686e156.jpg)   
헤더 이미지가 있는 Twitter 공유 페이지   
출처 - [minimal-mistakes/docs](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#open-graph-default-image)

> ![mm-twitter-card-summary-large](https://user-images.githubusercontent.com/19484971/143674030-63803862-34bb-4f46-9300-2decf20d99bb.jpg)   
헤더 이미지가 있는 Facebook 공유 페이지   
출처 - [minimal-mistakes/docs](https://mmistakes.github.io/minimal-mistakes/docs/configuration/#open-graph-default-image)

## analytics 설정

>  애널리틱스(Analytics)는 데이터 또는 통계의 체계적인 계산전 분석이다. 데이터의 유의미한 패턴의 발견, 해석, 의사소통을 위해 사용된다.   
출처 - [wiki/애널리틱스](https://ko.wikipedia.org/wiki/%EC%95%A0%EB%84%90%EB%A6%AC%ED%8B%B1%EC%8A%A4)

위키가 영문위키를 구글번역했는지 말이 이상하다, 의미상 데이터 패턴이나 통계를 파악하여 어떤 문제를 해결하는데 도움이 되도록 한다는 의미같다.🤔

어쨋든 해당 설정은 `analytics`을 사용할지, 어떤 `Analytics Provider`를 사용할지에 관한 설정이다. 커스텀을 제외한 모든 `Analytics Provider`는 모두 구글에서 제공하기 때문인지 `provider`와 `tracking_id`만 기입하면 되어 설정이 복잡해보이지는 않는다.

아래는 Minimal Mistakes에서 제공하는 analytics 설정 예시이다.

    analytics:
      provider: "google-gtag"
      google:
        tracking_id: "UA-1234567-8"
        anonymize_ip: false # default

필자는 우선 `google`을 적용해보고 다른 것들도 사용해볼 예정이다. (마찬가지로 언제 넣을지는 아무도 모른다.😅)

## 작성자 설정

이름 그대로 작성자에 대한 정보를 기입하는 부분이다. 작성자 소개 아래에 다양한 아이콘과 함께 링크를 넣을 수 있다. 아이콘은 [Font Awesome icon](https://fontawesome.com/icons?d=gallery)에서 원하는 아이콘을 골라 사용하면 된다.

예를 들어 아래와 같이 amazon 아이콘을 선택하고 해당 class(fab fa-amazon)를 `icon`에 넣어 설정을 적용시키면 아래와 같다.

![Font Awesome icon 예시](https://user-images.githubusercontent.com/19484971/143678117-738fda81-d07f-4a6c-9884-fda519192950.PNG){: width="400" .align-center .border-grey}

    author:
      name             : "게으른 너구리"
      avatar           : # 작성자의 이미지 파일 경로, ex) "/assets/images/test.jpg"
      bio              : "귀찮은 일은 모두 컴퓨터에게 맡기고 쉬고싶은 너구리입니다."
      location         : "South Korea"
      links:
        - label: "amazon" # 아이콘 옆에 쓰일 문구
          icon: "fab fa-amazon"
          url: # 아이콘을 클릭했을 때 사용될 URL 링크

![작성자 설정 예시](https://user-images.githubusercontent.com/19484971/143678204-f3964296-debc-4974-85eb-655550e84c04.PNG){: width="300" .align-center .border-grey}

💡한 블로그에 여러 작성자가 있는 경우 포스트마다 [YFM(YAML Front Matter)](/github%20blog/github-blog-post-writing/#yfmyaml-front-matter)을 통해 다른 작성자를 표시할 수 있다.
{: .notice--warning}

## footer 설정

작성자 설정의 links와 설정하는 방법이 똑같아 생략하겠다.😝 작성자 소개 부분과 footer 부분의 link 형식을 다르게 하고 싶은 사람들을 위해서 `author`의 `links`와 별개로 있는 것 같다.

## 포스트 설정 (Front Matter Defaults)

포스팅 [YFM(YAML Front Matter)](/github%20blog/github-blog-post-writing/#yfmyaml-front-matter)의 기본값을 설정한다. 2021년 11월 28일 기준으로 약필자의 약간의 설명이 포함된 minimal-mistakes에서 추천하는 `post`의 `Front Matter Defaults`는 아래와 같다.

    defaults:
      # _posts
      - scope: # 해당 설정을 적용시킬 파일들을 지정
          path: ""
          type: posts
        values: # 파일들이 가지는 YFM 기본값
          layout: single # 사용할 html 파일 지정
          author_profile: true # 작성자 프로파일 표기 여부
          read_time: true # 포스트 읽는 시간 표기 여부
          comments: true # 댓글 엔진 사용시 댓글 사용 여부
          share: true # SNS 공유 버튼 사용 여부
          related: true # 관련 포스트 목록 사용여부

정말 다양한 설정이 가능하지만 개인적으로 추천할 `values`들을 소개하면서 진행하겠다. 원하는 내용이 있다면 설정을 진행하면 된다.

### scope

`scope`에서는 `values`를 적용시킬 📁파일들을 지정한다.

#### path

`path`에는 설정을 적용시킬 폴더나 파일를 지정한다. `path`의 기본값은 `""`과 같다. 즉, `_config.yml` 파일이 있는 경로의 모든 파일을 대상으로 지정한다.

❗️`glob patterns`라는 정규표현 비슷한 패턴을 활용하여 지정할 수도 있지만 특히 윈도우에서 최적화가 되어있지 않아 생기는 문제가 많다고 하여 사용하는 것은 전혀 추천하지 않는다.
{: .notice--danger}

#### type

`type`에는 `path`에 있는 파일 중 특정한 종류의 파일들만을 지정한다.

여기서 파일의 종류는 정확히는 모르겠지만 [jekyll의 Front Matter Defaults 가이드](https://jekyllrb.com/docs/configuration/front-matter-defaults/)와 [minimal-mistakes docs의 _config.yml](https://github.com/mmistakes/minimal-mistakes/blob/master/docs/_config.yml)을 토대로 개인적으로 유추해보면... `_includes`나 `_layouts`같은 `_파일명`으로 적혀진 폴더 내의 파일을 의미하는 것 같다. 해당 폴더를 jekyll에서는 `collection`이라고 칭하며 사용자가 직접 만들 수 있다는 듯이 언급한다.    

한 깃허브에 각각 파일을 나누어 여러 블로그를 만들어 사용하면 `path`와 `type` 모두를 사용할 지도 모르지만, 필자는 해당하지 않으므로 `type`만을 활용하고 있다.

### values

`scope`에서 지정된 파일들이 가질 YFM 기본값들을 나열한다. 사용자들도 원하는 키-값을 만들어 적용할 수 있다. 자세한 내용은 [YFM 커스텀](http://localhost:4000/github%20blog/github-blog-post-writing/#yfm-%EC%BB%A4%EC%8A%A4%ED%85%80) 참고

#### layout

게시글을 어떤 html 파일로 보여줄지에 대한 설정, Minimal Mistakes에서는 기본적으로 `_layouts`의 `single.html`을 지정하는 설정이 들어가고 목록을 보여주는 화면이라면 `archive.html`를 사용하는 것도 볼 수 있다.

[Jekyll의 front-matter-defaults 가이드](https://jekyllrb.com/docs/configuration/front-matter-defaults/)에 따르면 사용자들이 직접 `_layouts`에 html 파일을 만들어 커스텀을 할 수 있다고 언급되는데 필자는 못하였다.🤔

#### author_profile

[작성자 프로파일](/github%20blog/github-blog-config-setting/#%EC%9E%91%EC%84%B1%EC%9E%90-%EC%84%A4%EC%A0%95) 표기 여부이다. `false`로 지정하면 작성자 프로파일이 있던 부분이 공백으로 변하기만 하고 본문이 넓어지지는 않는다.

![author_profile false](https://user-images.githubusercontent.com/19484971/143796129-811292d8-e1b3-475b-9020-29b82650507a.PNG){: .width="600" .align-center .border-grey}

#### show_date, read_time

게시글이 작성된 날짜와 게시글을 읽는데 걸리는 예상 시간의 표기 여부 설정이다. 날짜 형식과 읽는 시간 조정에 대한 설정은 [다른 설정](/github%20blog/github-blog-config-setting/#date_format-words_per_minute)을 조정해야한다. `read_time`는 값만 바꾸면 되고 `show_date`의 경우 기본 설정에는 키가 없어 사용자가 직접 추가해주어야 한다. 

    defaults:
      # _posts
      - scope:
          path: ""
          type: posts
        values:
          layout: single
          show_date: true
          read_time: true # 추가!

#### share

공유하기 기능이 있는 버튼의 표시 여부를 결정한다.

![share 예시](https://user-images.githubusercontent.com/19484971/143800042-74c2314d-ce92-43c8-85c0-40d058d72a1d.PNG){: .width="600" .align-center .border-grey}

#### related

참고 포스팅 목록의 표시 여부를 결정한다.

![related 예시](https://user-images.githubusercontent.com/19484971/143800393-b096e7a1-9052-4233-91d9-116f8dc8cd79.PNG){: .width="600" .align-center .border-grey}

#### toc (목차)

toc(Table of contents) 표시 여부를 결정한다.

![toc 예시](https://user-images.githubusercontent.com/19484971/143800598-8bc893c5-1279-4929-a972-e50259f3368f.PNG){: .width="300" .align-center .border-grey}

#### toc_sticky

toc(목차)가 우측 화면에서 항상 볼 수 있도록 고정된다. 즉, 스크롤을 내려도 목차를 볼 수 있다.

#### classes

html에서 body에 class를 추가해주는 설정이다.

예시:

    classes:
        - landing
        - dark-theme

결과:

    <body class="layout--splash landing dark-theme">

다양한 class를 넣을 수 있지만 가장 커스텀에 잘 쓰이는 class 중 하나만 소개하고 넘어가려고 한다. 아래와 같은 설정을 추가하면 본문 부분의 화면이 넓어지게 만들 수 있다.

    classes: wide

![wide 예시](https://user-images.githubusercontent.com/19484971/143805159-7892fdbc-d2d7-4b80-a36d-15d14598c630.PNG){: .width="600" .align-center .border-grey}

💡위의 예시 사진처럼 `toc`을 사용하면서 `wide`를 적용하게되면 `toc`이 제목과 본문 글 사이에 고정된다.
{: .notice--warning}

# 마치며

없던 영어 울렁증도 생길 것 같다..🥴 간단하게 하려고 했는데 설정 하나하나 흥미가 생겨 거의 설정 가이드를 4일동안 정독을 해버리고 말았다. ~~가이드에서 다른 가이드 링크 걸어두는 것은 정말 반칙이었다.~~ 대신 설정에 대해서 상당히 잘 알게 되었다, 다른 블로그에서 어렵게 바꾸던 형식을 설정으로 간단히 바꿀 수 있는 것도 있었다.

다음에는 정말로 YFM(YAML Front Matter) 설명을 곁들인 게시글을 작성할 것이다. 다음 게시글을 쓰는데 얼마나 걸릴지 모르겠지만 빠르게 작성하길 희망하면서 미래의 나에게 맡기겠다.😁

+ 추가

Atom에서 VScode로 텍스트 에디터를 바꾸었다. 툴을 잘 바꾸는 편이 아닌데 사용하다가 한글에 대한 버그가 걸려서 텍스트가 사라지면 3줄씩도 사라지고 ctrl+z로도 복구를 못하는 경우가 꽤 많아 화나서 바꾸었다. 아직까지 VScode에 대한 사용은 원활하다!👍