---
title:  "[Github Blog 제작기] 4. 게시글 작성 방법"
excerpt: "게시글 작성 형식과 YFM, 이모지, 텍스트 강조 방법 등 게시글 작성에 대한 팁을 정리해보았다!✨"

categories:
  - Github Blog
tags:
  - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

last_modified_at: 2021-11-30

my_var: "짜잔!" # 예시를 위해 추가!
---

# 개요

게시글을 만들때 사용되는 YAML front matter(이하 YFM)과 다양한 글 작성 방법을 소개할 것이다.

이 아래의 내용들은 [minimal-mistakes utility](https://mmistakes.github.io/minimal-mistakes/docs/utility-classes/#link),[minimal-mistakes Authors](https://mmistakes.github.io/minimal-mistakes/docs/authors/) 그리고 [Jekyll posts](https://jekyllrb.com/docs/posts/), [Jekyll front-matter](https://jekyllrb.com/docs/front-matter/)를 참고했음을 밝힌다.

# 파일 만들기

`_post` 폴더 내에서 특정한 이름을 가진 것들만을 게시물로 인식한다. `_post` 폴더를 만들고 아래의 형식에 맞게 파일을 생성하자. 🤔한글은 잘 인식이 안되었던 것으로 기억한다, 파일명은 꼭 영어로 작성하도록 하자.

    YEAR-MONTH-DAY-title.md
    ex)
    2011-12-31-new-years-eve-is-awesome.md
    2012-09-12-how-to-write-a-blog.md

필자의 경우 관리를 위해 `_post` 내의 폴더 내에서 폴더를 하나 더 만들어 게시글을 나눠 관리하고 있다.
![posts](https://user-images.githubusercontent.com/19484971/144011396-2dfb5e21-b7e6-441c-bbb3-3aba292cceec.PNG){: .width="600" .align-center .border-grey}


# YFM(YAML front matter)

게시글 파일을 만든 이후에는 가장 첫 줄부터 YAML front matter을 작성해야 한다. 공식 YAML 문서에 쓰여진 YAML 소개는 다음과 같다.👇

    %YAML 1.2
    ---
    YAML: YAML Ain't Markup Language™

    What It Is:
      YAML is a human-friendly data serialization
      language for all programming languages.

데이터를 직렬화할 때 사용하는 언어라고 소개가 되어있다, 해당 언어를 활용해서 게시물에 대한 기본값을 설정하는 것을 YAML front matter이라고 말하고 줄여서 YFM이라고 한다.

YFM은 `---`로 시작하고 끝나며 중간에는 다양한 `키: 값`형식의 데이터가 들어간다. 해당 게시물에서 사용한 YFM는 아래와 같다.

    ---
    title:  "[Github Blog 제작기] 4. 게시글 작성과 상단 네비게이션"
    excerpt: "간단한 게시글과 함께 상단 네비게이션을 만들고 카테고리와 태그 화면을 확인한다."

    categories:
      - Github Blog
    tags:
      - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

    last_modified_at: 2021-11-29
    ---

중복되거나 항상 사용하는 YFM은 이전 게시물의 📄`_config.yml`에서 [Front Matter Defaults 설정](/github%20blog/github-blog-config-setting/#%ED%8F%AC%EC%8A%A4%ED%8A%B8-%EC%84%A4%EC%A0%95-front-matter-defaults)으로 관리하는 것이 더 편리하다. 필자는 `toc`, `toc_sticky`, `comments`, `show_date` 등은 `_config.yml`에서 관리하여 게시물에서 따로 작성하지는 않는다.

아래는 각 게시물에서 자주 사용되는 YFM이다.

## title

게시물의 제목을 적는다.

## excerpt

게시물에 대한 설명을 적는다.

## categories

게시물의 카테고리를 적는다. 여러 개를 동시에 넣는 것은 가능하나 한 줄에 한꺼번에 적으면 에러가 난다. 이유는 잘 모르겠다.

    (X)
    categories:
      - [Test, Github Blog]
    (O)
    categories:
      - Github Blog
      - Test

## tags

게시물의 태그를 적는다. 여러 개를 동시에 넣는 것이 가능하다.

    (O)
    tags:
      - [Blog, HTML, Jekyll]
    (O)
    tags:
      - Blog
      - HTML
      - Jekyll

## date

게시물의 작성 날짜를 넣는다. 파일명에 들어가는 연월일이 자동적으로 기본값이 되기 때문에 파일명을 정확히 작성하였다면 생략해도 된다.

물론 `0000-00-00T00:00:00-05:00`형식으로 국제표준시간까지 정확하게 작성할 수도 있다.

## last_modified_at

게시물의 최근 수정일을 적는다. 형식은 `date`와 같다. 필자는 `date`보다 수정일을 보이는 것을 더 선호하여 더 자주쓴다.

## 기타

위에서 소개한 내용 외에도 `teaser`, `comments`, 

Jekyll에서 사용하는 변수들은 더 확인하고 싶다면 [Jekyll page-variables](https://jekyllrb.com/docs/variables/#page-variables)를 참고하자!

## YFM 커스텀

 `키: 값` 형식으로 사용자가 직접 원하는 키와 값을 지정하여 자유롭게 커스텀을 할 수 있다. 예시는 아래와 같다.

    ---
    title:  "[Github Blog 제작기] 4. 게시글 작성과 상단 네비게이션"
    excerpt: "간단한 게시글과 함께 상단 네비게이션을 만들고 카테고리와 태그 화면을 확인한다."

    categories:
      - Github Blog
    tags:
      - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

    last_modified_at: 2021-11-29

    my_var: "짜잔!" # 추가!

    author: # 추가!
      name             : "게으른 너구리1"
      avatar           : # path of avatar image, e.g. "/assets/images/bio-photo.jpg"
      bio              : "귀찮은 일은 모두 컴퓨터에게 맡기고 쉬고싶은 너구리입니다22."
      location         : "South Korea333"
    ---
    
필자의 게시물은 single.html을 활용하므로 예시를 위해 잠시 수정한다.

![YFM 예제를 위한 single 수정](https://user-images.githubusercontent.com/19484971/143820830-c02ae26f-0d53-4df2-b227-7d856224da6a.PNG){: width="600" .align-center}

결과는 아래와 같이 나온다.

![YFM 결과](https://user-images.githubusercontent.com/19484971/143829460-91e41223-327f-43c9-8164-4f22dcf2e31b.PNG){: width="600" .align-center .border-grey}

물론.. 게시글 본문에 `{{page.my_var}}`을 사용할 수도 있다.
![캡처2](https://user-images.githubusercontent.com/19484971/144003325-b60b334d-6f13-4e1c-98b3-efd21b024fea.PNG){: width="400"}

html 파일의 `site.--`이나 `page.--` 등의 변수들은 모두 YFM을 통해 설정이 가능하며 원하는 값을 넣어 커스텀하는 것도 가능하다는 것을 알 수 있다!✨   

## YFM 작성자 설정

위에서는 게시물에 직접 작성자에 대한 정보가 들어갔지만, 이를 더 쉽게 관리할 수 있는 방법이 있다.

`_data` 폴더에 `authors.yml` 파일을 만들어 작성자의 정보를 관리하는 것이다. `_config.yml`에서 `author`을 작성한 것 처럼 아래와 같이 작성자에 대한 정보를 기입하자.

    # /_data/authors.yml

    Billy Rick:
      name        : "Billy Rick"
      bio         : "What do you want, jewels? I am a very extravagant man."
      avatar      : "/assets/images/bio-photo-2.jpg"
      links:
        - label: "Email"
          icon: "fas fa-fw fa-envelope-square"
          url: "mailto:billyrick@rick.com"
        - label: "Website"
          icon: "fas fa-fw fa-link"
          url: "https://thewhip.com"
        - label: "Twitter"
          icon: "fab fa-fw fa-twitter-square"
          url: "https://twitter.com/extravagantman"

    Cornelius Fiddlebone:
      name        : "Cornelius Fiddlebone"
      bio         : "I ordered what?"
      avatar      : "/assets/images/bio-photo.jpg"
      links:
        - label: "Email"
          icon: "fas fa-fw fa-envelope-square"
          url: "mailto:cornelius@thewhip.com"
        - label: "Twitter"
          icon: "fab fa-fw fa-twitter-square"
          url: "https://twitter.com/rhymeswithsackit"

그리고 게시글의 YFM에 작성자의 이름만 적어주면 된다.👍

    author: Billy Rick

# 본문 작성

기본적으로 MarkDown(마크다운) 문법을 사용하여 블로그 게시글을 작성한다. 마크다운 문법에 관해서는 정리가 잘 된 블로그가 많으니 필자는 따로 정리하지 않겠다. 추천하는 [블로그 링크](https://velog.io/@starry3ones/MarkDown-%EC%82%AC%EC%9A%A9%EB%B2%95)를 올려두고 넘어가겠다.

## 이미지 추가

본문에 이미지를 첨부할 때 꼭 주의할 점이 있다, 이미지를 블로그 운영 중인 레포지토리에 저장을 하면 안된다. 이유는 단순히 크기가 크기 때문인데, 깃허브를 기반으로하는 블로그는 1GB가 넘으면 안되는 제약사항이 있기 때문이다.

이때 깃허브를 활용하여 이미지를 첨부하는 방법이 있다. Issue 혹은 Commit으로 들어가면 Comment를 남기는 부분에 이미지를 드로그 앤 드롭하면 나오는 경로를 그대로 복사/붙여넣기 하면 된다.

![이미지 예시](https://user-images.githubusercontent.com/19484971/143887052-e63f54f9-6dc0-44d2-b6de-d206e167d230.PNG){: width="400" .align-center .border-grey}

### 이미지 크기와 위치 지정

이미지의 크기와 위치를 지정하는 방법은 이미지 링크 뒤에 `{: width="크기" .align-[center/left/right]}`을 추가하면 된다. 바로 위의 이미지의 경우는 아래와 같이 적어놓았다.

    ![이미지 예시](https://user-images.githubusercontent.com/19484971/143887052-e63f54f9-6dc0-44d2-b6de-d206e167d230.PNG)
    {: width="400" .align-center .border-grey}

크기의 경우 `{: width="00%"}`로 해도 되지만 페이지 크기가 변동할 때마다 사진 크기가 바뀌는 것을 좋아하지 않아 필자는 크기를 지정하는 편이다. `.border-grey`는 이미지 주변에 [회색 테두리를 만드는 방법 링크 추가 요망]()인데 해당 기법은 css를 직접 수정해야 적용이 가능하다. 이것은 이후 포스팅에서 다룰 예정이다.

## Emoji(이모지)✨

> Emojis는 iOS, Android, macOS, Windows, Linux and ChromeOS에서 사용될 수 있습니다. Twitter, Facebook, Slack, Instagram, Snapchat, Slack, GitHub, Instagram, WhatsApp 그리고 더 많은 곳에서 emojis를 복사/붙여넣기 해보세요!   
[getemoji](https://getemoji.com/)

> 일본의 휴대전화 문자 메시지에서 시작되어 지금은 대부분의 스마트폰 및 PC 등 다양한 환경에서 사용되는 그림 문자.   
[https://namu.wiki/w/이모지](https://namu.wiki/w/%EC%9D%B4%EB%AA%A8%EC%A7%80)

간단하게 거의 대부분의 플렛폼에서 자유롭게 사용할 수 있는 이모티콘이다! 
윈도우10의 경우 `윈도우+.`, 맥북이면 `command+control+spaceBar`으로 바로 이모지를 넣을 수 있다.

![Emoji 예시](https://user-images.githubusercontent.com/19484971/143882217-b12312a2-5f9d-4dfe-9b83-40a4cdd12ac7.PNG){: width="400" .align-center}

## button

텍스트를 버튼 모양으로 바꿀 수 있다.

Text
{: .btn}

    Text
    {: .btn}

Text
{: .btn .btn--primary}

    Text
    {: .btn .btn--primary}

Text
{: .btn .btn--success}

    Text
    {: .btn .btn--success}

Text
{: .btn .btn--warning}

    Text
    {: .btn .btn--warning}

Text
{: .btn .btn--danger}

    Text
    {: .btn .btn--danger}

Text
{: .btn .btn--info}

    Text
    {: .btn .btn--info}

Text
{: .btn .btn--inverse}

    Text
    {: .btn .btn--inverse}

Text
{: .btn .btn--light-outline}
👆위에 텍스트가 있는데 안보인다, 커서를 올려보자.

    Text
    {: .btn .btn--light-outline}

필자의 경우 텍스트에 사용하지는 않고 링크에 사용하는데, 특히 카테고리와 태그에 사용한다. 만약 '위의 색이 마음에 안든다!' 하면 직접 원하는 색상이나 모양을 css에 넣어 [원하는 버튼 링크 추가 요망]()을 만들면 된다.

가이드에 따르면 [버튼의 크기도 변경](https://mmistakes.github.io/minimal-mistakes/docs/utility-classes/#buttons)할 수 있다고 하는데 필자는 적용이 되지 않는다;;😢

## notice

텍스트를 강조하는 블록을 만들 수 있다.

`{: .notice}`
{: .notice}

`{: .notice--primary}`
{: .notice--primary}

`{: .notice--info}`
{: .notice--info}

`{: .notice--warning}`
{: .notice--warning}

`{: .notice--success}`
{: .notice--success}

`{: .notice--danger}`
{: .notice--danger}

가끔 주위사항이나 팁을 쓸 때 사용하게 된다. notice에 생각보다 큰 문제가 있는데.. 바로 테마마다 notice 블록 색상이 달라지는 것이다. 때문에 개인적으로는 [notice에 관한 css를 수정 링크 추가 요망]()해서 사용하고 있다.

# 마치며

더 좋은 방법이 있을지도 모르지만 필자가 찾은 방법은 모두 메모해두었다. 개인적으로 적용시킨 css까지 정리하고 싶었지만, 너무 글이 길어질 것 같고 차라리 css에 대해 정리하는 글을 적는 것이 좋을 것 같아 해당 내용은 이후의 포스팅으로 미루게 되었다.

다음 게시글은 상단 네비게이션을 만드는 방법을 적을 것이다. 사실 해당 게시글에 같이 적으려고 했는데 생각보다 글이 길어져서 나누게 되었다.😅
