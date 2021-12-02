---
title:  "[Github Blog 제작기] 2. 깃허브 블로그와 유용한 툴 소개"
excerpt: "블로그를 본격적으로 시작하기에 앞서 필용한 도구들과 환경설정"

categories:
  - Github Blog
tags:
  - [Blog, HTML, Jekyll, Liquid, Minimal Mistake]

last_modified_at: 2021-11-30
---

# 개요

[식빵맘님의 방식](https://ansohxxn.github.io/blog/i-made-my-blog/#1-github-%EC%97%90%EC%84%9C-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EC%9A%A9%EC%9C%BC%EB%A1%9C-%EC%93%B8-%EC%83%88%EB%A1%9C%EC%9A%B4-repository-%EB%A5%BC-%EC%83%9D%EC%84%B1%ED%95%9C%EB%8B%A4)도 좋고 어떤 방법으로든 좋으니 로컬 저장소에 본인의 저장소를 만들어보자. 게시글을 만들고 블로그를 꾸미려면 원격 저장소만을 사용하는 것은 너무 불편하다.

또한 Ruby, gem, bundle 을 다운받아 로컬 서버를 실행시켜 commit을 하지 않아도 블로그가 어떻게 변했는지 확인할 수 있도록 할 것이다. 이것도 꼭 필요한 것은 아니지만 적용된 화면을 확인하기 위해서 commit이 강제되는 것과 원하는 대로 변경이 되지 않았을 때 피로감이 굉장하기 때문이다.

# 1. 로컬 저장소 만들기

👉[테디노트님의 유튜브 동영상](https://www.youtube.com/watch?v=ACzFIAOsfpM&t=621s) 시청 및 [깃 다운로드](https://git-scm.com/) 필수
{: .notice--custom-purple}
본인의 경우 Git을 다운로드 받으면서 Git Bash도 같이 다운로드를 받았다.

+ ## 파일 생성

원하는 위치에 새 폴더를 만든 뒤 cmd에서 해당 폴더에 들어가서 `git init`을 실행하자.
본인의 경우 [Git Bash](https://git-scm.com/)를 사용하여 리눅스 명령어를 사용할 필요 없이 바로 해당 파일에서 터미널을 실행시켰다.

![image](https://user-images.githubusercontent.com/19484971/143220965-85976188-f3b0-4f87-8797-7af36a1bf3a2.png){: width="500" .align-center .border-grey}

<br/>

만약 잘 실행이 되었다면 아래와 같이 `.git`파일이 생성되었을 것이다.

![image](https://user-images.githubusercontent.com/19484971/143218401-bb42da5d-9a52-47de-a664-f242d7260f12.PNG){: width="500" .align-center .border-grey}

<br/>

+ ## 원격 저장소와 연결

이번에는 터미널에 `git remote add 이름 원격저장소HTTPS`를 입력한다.
`원격저장소HTTPS`는 각자가 만든 원격 저장소에서 확인이 가능하다.

![image](https://user-images.githubusercontent.com/19484971/143228628-49442369-ac2d-4f3e-816c-4198b88c02e9.PNG){: width="40%" height="40%" .align-center .border-grey}

📌이름은 꼭 origin으로 설정하자! 이후 _config.yal 파일에서 jekyll 설정을 할 때 소소한 도움이 된다.
{: .notice--warning}

`git remote -v`를 입력해서 잘 연결이 되었는지 확인이 가능하다.
필자의 경우 이름을 origin이라고 하고 아래와 같이 입력하여 잘 작동하였다.

![image](https://user-images.githubusercontent.com/19484971/143228835-62707f7e-e9ee-4841-b013-9fd07e3c63e0.PNG){: width="400" .align-center .border-grey}

+ ## 원격 저장소 pull

마지막으로 `git pull --set-upstream 이름 master`를 입력해보자! 그러면 다운로드를 받는 화면이 보이고 잠시후 파일에 원격 저장소에 있던 파일들이 다운로드 된 것을 확인할 수 있다.

![image](https://user-images.githubusercontent.com/19484971/143229464-e97182ea-d6c9-4d91-83c8-143b9d46643f.PNG){: width="500" .align-center .border-grey}

# 2. 로컬 서버 실행해보기

+ ## Ruby 설치

원본 글은 [이곳](https://ansohxxn.github.io/blog/i-made-my-blog/#3-ruby-%EC%84%A4%EC%B9%98)에서 찾아볼 수 있다.

Jekyll은 Ruby라는 언어로 만들어졌기 때문에 jekyll을 설치하기 위해선 Ruby를 먼저 설치해야 한다고 한다. 루비 인스톨러 다운로드 페이지 <https://rubyinstaller.org/downloads/> 여기서 WITH DEVIKIT 중 가장 위에 있는 것을 다운받아 실행시킨다.

✨ 인스톨러를 실행할때 아랫 문장을 체크하면 직접 환경 변수 설정 해야 하는 수고로움을 생략할 수 있다.

- [x] Add Ruby executables to your PATH


+ ## Jekyll 과 Bundler 설치

> Bundler는 루비 프로젝트에 필요한 gem들의 올바른 버전을 추적하고 설치해서 일관된 환경을 제공하는 도구이다.

cmd에 `gem install jekyll bundler`을 실행시킨다,`jekyll -v` 명령어를 수행하여 jekyll이 잘 설치되었는지 확인해본다.

### Bundler 설치 에러

필자의 경우 `gem install jekyll bundler`실행시 에러가 발생하였다. 검색 결과 `Gemfile`이라는 파일에 특정 코드를 넣어야 한다고 하여 해당 코드를 추가하였다.

```
source "https://rubygems.org"
gemspec

gem 'wdm', '>= 0.1.0' if Gem.win_platform? // 추가!
```

이후 다시 삭제 후 `gem install jekyll bundler`을 실행하였더니 정상적으로 설치가 진행되었다.

필자의 ruby, gem, jekyll, bundler의 버전은 다음과 같다.

![버전 확인](https://user-images.githubusercontent.com/19484971/143286503-094ee4b3-32b3-4870-a0aa-8b0b911ea5f5.PNG){: width="400" .align-center}

+ ## 서버 실행

cmd에 `bundle exec jekyll serve`를 실행시키면 드디어 로컬 환경에서 jekyll 서버가 가동된다. 웹 브라우저를 켜고 <http://127.0.0.1:4000> 로 접속하면 바로 블로그를 확인할 수 있으며 파일을 수정하거나 생성, 삭제할 때마다 자동으로 빠르게 서버에 반영된다.

또한 에러나 경고문이 보이기 때문에 문구를 보고 해결하면 좋다.   
예시를 위해 사진을 올리겠다.

![에러 화면](https://user-images.githubusercontent.com/19484971/143287833-404cce0d-ffff-4ae1-846f-34ff80d04ac8.PNG){: width="600" .align-center}

노란 글로 쓰여있는 것은 경고, 빨간 글로 쓰여있는 것은 에러이다.
경고는 고치지 않아도 문제는 없지만, 에러의 경우 고치지 않으면 (당연히) 서버가 열리지 않는다.

영어만 쓰여있기 때문에 당황스러울 수 있으나 읽어보면 의외로 해결방법을 친절히 알려주고 있음을 알 수 있다. 에러 3번째 줄을 잘 보면 `알 수 없는 변수 "$notice-colo"가 52번째 줄 37번째에 있고 파일 ../_notices.scss에서 찾을 수 있다.` 라고 적혀있다. 필자가 예시를 위해 일부러 변수명을 오타낸 위치를 정확히 보여주고 있다.

# 3. 텍스트 에디터 선택

파일을 관리하기 위해서 단순히 파일 탐색기를 사용하면.. 슬프다.. 마크다운 미리보기 기능이 있는 적당한 텍스트 에디터를 선택하자!

본인의 경우에는 [Atom](https://atom.io/)을 선택했지만, [Visual Studio Code](https://code.visualstudio.com/)가 더 편리하다는 말을 이곳 저곳에서 들었다. 만약 마크다운 문법이 어려운 사람이라면 [Typora](https://typora.io/)라는 마크다운 에디터를 사용할 수도 있겠지만, 기본적으로 html 형식 파일은 인식을 못하는 것을 보아 필자는 추천하기 주저된다. 마크다운 문법은 상대적으로 쉬운 편이니 공부를 해서 사용법을 아는 것을 추천한다.   
개인적으로 마크다운 문법을 가장 잘 깔끔하게 잘 정리했다고 생각하는 [블로그 링크](https://velog.io/@starry3ones/MarkDown-%EC%82%AC%EC%9A%A9%EB%B2%95)를 남기겠다.

어쨋든 텍스트 에디터를 선택하였다면 마크다운 미리보기 기능은 기본 기능이 아니기 때문에 관련 패키지나 라이브러리를 다운받아야 한다. 필자는 검색해서 나온 [블로그](https://tikepjt.tistory.com/47)를 통해 마크다운 미리보기 기능을 넣어서 사용하고 있다.

![image](https://user-images.githubusercontent.com/19484971/143238158-0fbcb90a-6851-472f-a07b-f833b9eddba9.PNG){: .align-center}

~~빨간줄 태러와 가끔 텍스트가 잘리는 이상한 버그 때문에 바꿀 의향이 점점 차오르고 있다...~~   

+ 추가

결국 VScode로 변경하였다, 한글에 대한 버그와 더불어 자잘한 알 수 없는 버그들 때문에 사용이 너무 어려워서 바꾸었더니, 깃허브 관리 기능도 편리하고 버그도 없어서 사용하기 좋다.👍

# 마치며

👏와! 가장 하기 귀찮은 환경설정이 마침내 끝났다!
다음 블로그 게시글은 게시글의 작성 팁을 작성하였다. 해당 글에서도 적용된 이모티콘이나 이미지 추가에 대한 방법 등등을 정리해놓았다.

오타가 있는지 해당 글을 다시 확인하고 싶지만 새벽 3시가 되기전에 자고 싶으므로 오타는 미래의 나에게 맡긴다!😴
~~후우..~~
