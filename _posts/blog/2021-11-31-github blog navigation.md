---
title:  "[Github Blog 제작기] 5. 상단 네비게이션과 아카이브"
excerpt: "상단 네비게이션을 아카이브를 활용하여 구현해보자!"

categories:
  - Github Blog
tags:
  - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

last_modified_at: 2021-11-31
---

# Navigation (네비게이션)

Jekyll에서는 최대한 많은 네비게이션 링크를 보여주는 디자인 패턴인 `priority plus`으로 `masthead` 링크를 보여준다고 한다. 글보다 사진으로 보는 것이 더 쉽다.

>![mm-priority-plus-masthead](https://user-images.githubusercontent.com/19484971/143985134-83b20769-a60c-47eb-bc23-277cda7c116f.gif){: .width="600" .align-center}   
출처 - [minimal-mistakes/docs/navigation/](https://mmistakes.github.io/minimal-mistakes/docs/navigation/#masthead)

Jekyll의 `_data` 폴더의 `navigation.yml` 파일을 통해서 네비게이션을 쉽게 구현할 수 있다. 



💡가장 중요한 링크를 가장 먼저 작성하자! 메뉴 토글로 축약되지 않고 항상 보인다.
{: .notice--warning}

# 마치며

다음 게시글은 너무 못 생긴 블로그를 그나마 시원하게 만들 css들을 조금 소개할 예정이다. 웹을 이미 알고 있는 사람들의 경우 이미 적용했을 가능성도 있지만 필자처럼 웹 개발자가 아닌 경우에는 도움이 되는 글이 될 것이다!