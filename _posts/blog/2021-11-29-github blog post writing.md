---
title:  "[Github Blog 제작기] 4. 게시글 작성 방법과 팁"
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

> %YAML 1.2
> ---
> YAML: YAML Ain't Markup Language™
>
> What It Is:
>   YAML is a human-friendly data serialization
>   language for all programming languages.

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

위에서 소개한 내용 외에도 `teaser`, `comments` 등 여러가지 설정을 적용할 수 있다. 변수들은 더 확인하고 싶다면 [Jekyll page-variables](https://jekyllrb.com/docs/variables/#page-variables) 혹은 [minimal-mistakes/docs](https://github.com/mmistakes/minimal-mistakes/tree/master/docs/_posts)를 참고하자!

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
![page.my_var](https://user-images.githubusercontent.com/19484971/144003325-b60b334d-6f13-4e1c-98b3-efd21b024fea.PNG){: width="400"}

html 파일의 `site.--`이나 `page.--` 등의 변수들은 모두 YFM을 통해 설정이 가능하며 원하는 값을 넣어 커스텀하는 것도 가능하다는 것을 알 수 있다!✨   

💡author에 대한 설정은 [minimal-mistakes authors 가이드](https://mmistakes.github.io/minimal-mistakes/docs/authors/)에서 더 편리한 방법을 확인할 수 있다. 한 블로그에 여러 작성자가 있다면 꼭 확인하자!
{: .notice--warning}

# 본문 작성

YFM 작성을 마쳤으면 기본적으로 MarkDown(마크다운) 문법을 사용하여 블로그 게시글 본문을 작성한다. 마크다운 문법에 관해서는 정리가 잘 된 블로그가 많으니 필자는 따로 정리하지 않겠다. 추천하는 [블로그 링크](https://velog.io/@starry3ones/MarkDown-%EC%82%AC%EC%9A%A9%EB%B2%95)를 올려두고 넘어가겠다.

본문을 작성할 때 코드를 올리는 경우도 있고 이미지를 업로드 하는 경우도 있을 것이다. 본문을 작성할 때 도움이 되는 방법에 대해서 간략하게 정리를 해보았다!🎉

## 이미지 추가

본문에 이미지를 첨부할 때 꼭 주의할 점이 있다, 이미지를 블로그 운영 중인 레포지토리에 저장을 하면 안된다. 이유는 단순히 크기가 크기 때문인데, 깃허브를 기반으로하는 블로그는 1GB가 넘으면 안되는 제약사항이 있기 때문이다.

이때 깃허브를 활용하여 이미지를 첨부하는 방법이 있다. Issue 혹은 Commit으로 들어가자. 내 것, 남 것 레포지토리 구별없이 그림의 빨간줄 위치를 클릭하면 해당 commit에 들어갈 수 있다. (필자는 혹시 등록할까 무서워 본인의 레포에서만 들어간다.)

![into commit](https://user-images.githubusercontent.com/19484971/144553596-4d874a30-9cfa-45b0-85f3-91f318e1c81d.PNG)

 아래로 쭉 스크롤을 하면 Comment를 남기는 부분이 있는데 이곳에 이미지를 드로그 앤 드롭하면 나오는 경로를 그대로 복사/붙여넣기 하면 된다.

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

간단하게 말하자면 거의 대부분의 플렛폼에서 자유롭게 사용할 수 있는 이모티콘이다! 윈도우10의 경우 `윈도우+.`, 맥북이면 `command+control+spaceBar`으로 바로 이모지를 넣을 수 있다.

![Emoji 예시](https://user-images.githubusercontent.com/19484971/143882217-b12312a2-5f9d-4dfe-9b83-40a4cdd12ac7.PNG){: width="400" .align-center}

## button

**링크**를 버튼 모양으로 바꿀 수 있다. 텍스트도 사용이 가능하기는 하나 크기는 조절되지 않는 것이 확인되었다. 예시는 아래와 같다.

| 버튼 유형   | 결과 | 클래스 | Kramdown(마크다운) 사용법 |
| ------        | ------- | ----- | ------- |
| Default       | [Text](#link){: .btn} | `.btn` | `[Text](#link){: .btn}` |
| Primary       | [Text](#link){: .btn .btn--primary} | `.btn .btn--primary` | `[Text](#link){: .btn .btn--primary}` |
| Success       | [Text](#link){: .btn .btn--success} | `.btn .btn--success` | `[Text](#link){: .btn .btn--success}` |
| Warning       | [Text](#link){: .btn .btn--warning} | `.btn .btn--warning` | `[Text](#link){: .btn .btn--warning}` |
| Danger        | [Text](#link){: .btn .btn--danger} | `.btn .btn--danger` | `[Text](#link){: .btn .btn--danger}` |
| Info          | [Text](#link){: .btn .btn--info} | `.btn .btn--info` | `[Text](#link){: .btn .btn--info}` |
| Inverse       | [Text](#link){: .btn .btn--inverse} | `.btn .btn--inverse` | `[Text](#link){: .btn .btn--inverse}` |
| Light Outline | [Text](#link){: .btn .btn--light-outline} | `.btn .btn--light-outline` | `[Text](#link){: .btn .btn--light-outline}` |

| 버튼 크기 | 결과 | 클래스 | Kramdown(마크다운) 사용법 |
| ----------- | ------- | ----- | -------- |
| X-Large     | [X-Large Button](#){: .btn .btn--primary .btn--x-large} | `.btn .btn--primary .btn--x-large` | `[Text](#link){: .btn .btn--primary .btn--x-large}` |
| Large       | [Large Button](#){: .btn .btn--primary .btn--large} | `.btn .btn--primary .btn--large` | `[Text](#link){: .btn .btn--primary .btn--large}` |
| Default     | [Default Button](#){: .btn .btn--primary} | `.btn .btn--primary` | `[Text](#link){: .btn .btn--primary }` |
| Small       | [Small Button](#){: .btn .btn--primary .btn--small} | `.btn .btn--primary .btn--small` | `[Text](#link){: .btn .btn--primary .btn--small}` |

만약 '위의 색이 마음에 안든다!' 하면 직접 원하는 색상이나 모양을 css에 넣어 [원하는 버튼 링크 추가 요망]()을 만들면 된다.

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

가끔 주위사항이나 팁을 쓸 때 사용하게 된다. minimal-mistakes의 notice에 생각보다 큰 문제가 있는데.. 바로 테마마다 notice 블록 색상이 달라지는 것이다. 때문에 개인적으로는 [notice에 관한 css를 수정 링크 추가 요망]()해서 사용하고 있다.

## GitHub Gist(요지)

깃허브에서 코드를 끌어오는 듯한 코드 삽입을 보고 방법을 찾아보았다. [한 블로그](https://blog.soobinpark.com/147)를 보고 따라해보았는데 여러 방법 중에서도 github gist를 활용한 코드가 깔끔하고 색도 너무 화려하지 않으면서 강조되는 것이 좋아서 추천한다.

### GitHub Gist란?

github gist는 짧은 코드나 메모 등을 기록 또는 공유 할 수 있도록 github에서 제공하는 무료 서비스라고 한다. [깃허브 공식 문서](https://docs.github.com/en/github/writing-on-github/editing-and-sharing-content-with-gists/creating-gists)에 따르면 모든 gist는 레포지토리이기 때문에 forked 나 clone도 가능하다고 한다.

### 1. Github Login

gist를 사용하려면 github 계정이 필수이다. [github gist](https://gist.github.com/)에 접속하여 github 계정으로 로그인을 한다. 이후 오른쪽 상단의 `+` 버튼을 누르면 새 gist를 작성하는 페이지로 이동한다.

![gist create button](https://user-images.githubusercontent.com/19484971/144540270-18634bcd-d392-4dbe-8f1b-836015609943.PNG){: width="200" .align-center .border-grey}

### 2. Gist 새 글 작성

만약 이미 로그인이 되어있다면 새 글을 작성하는 화면이 바로 보일 것이다. 

![new gist create](https://user-images.githubusercontent.com/19484971/144538862-96452eb9-b27c-45a8-a2ac-4bf2dd3ffea2.PNG){: width="600" .align-center .border-grey}

`Gist description...`에 작성하려는 gist에 대한 간단한 설명을, `Filename including extension...` 에 확장자를 포함한 파일명을 입력해주고 본문을 작성해준다.

작성을 마쳤다면 원하는 gist 유형을 선택하고 생성하자!

![gist create type](https://user-images.githubusercontent.com/19484971/144542998-470f34c5-7a55-49d0-b6ba-52b01c976a51.PNG){: width="300" .align-center .border-grey}

+ Create secret gist : 검색 엔진에 검색이 되지는 않지만 URL을 가지고 있는 모두가 볼 수 있는 gist
+ Create public gist : 모든 사람이 볼 수 있는 gist

### 3. Gist 공유하기

![gist embed](https://user-images.githubusercontent.com/19484971/144544691-c98724b5-06cc-4c83-8608-f8f476366a05.PNG){: width="600" .align-center .border-grey}

생성을 마치면 위와 같은 화면이 나올 것이다. 유형을 Embed로 선택하고 복사하여 코드를 올리고 싶은 곳에 붙여넣기만하면 아래와 같이 표현된다.

<script src="https://gist.github.com/ii200400/07a31068a6c7d86f88fefde60dcf0f1f.js"></script>

# 마치며

더 좋은 방법이 있을지도 모르지만 필자가 찾은 방법은 모두 메모해두었다. 개인적으로 적용시킨 css까지 정리하고 싶었지만, 너무 글이 길어질 것 같고 차라리 css에 대해 정리하는 글을 적는 것이 좋을 것 같아 해당 내용은 이후의 포스팅으로 미루게 되었다.

다음 게시글은 상단 네비게이션을 만드는 방법을 적을 것이다. 사실 해당 게시글에 같이 적으려고 했는데 생각보다 글이 길어져서 나누게 되었다.😅
