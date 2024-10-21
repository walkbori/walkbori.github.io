---
title: 블로그 역사
date: 2024-10-21 19:59:12 +0900
categories: 유지보수
tags: 기록
---

## 설치 

### 기본설치 V7.1.1

1. Github에 Jekyll을 활용하여 블로그를 만들기로 하고 테마를 물색하다.
2. 테마는 [Chirpy](https://chirpy.cotes.page/)로 정하다.
3. 공식에서 [안내](https://chirpy.cotes.page/posts/getting-started/)하는 옵션 중에서 군더더기 없는 starter 버전을 설치하기로 하다.
4. 안내에 따라 [해당 페이지](https://github.com/cotes2020/chirpy-starter)로 가서 'Use this template'를 눌러 설치하다.
5. 설치 저장소이름(Repository name)은 '본인id.github.io'로 써야한다. Create repository를 누르고 잠시후 본인id.github.io로 접속해서 블로그가 뜨면 성공이다.

### 로컬서버 설치

1. 로컬서버는 필수사항은 아니나 여러모로 편리하다. 예를 들어 로컬에서 수정하고 웹에 반영하는 경우 반영되기 까지 수분이 걸리고, Github특성상 하나하나 변경 기록이 모두 남는다. 역시 로컬 환경이 가장 좋은점은 수정할 점을 몇초안으로 바로 확인할수 있다는 점이다.
2. Jekyll은 Ruby라는 언어로 만들어졌으므로 이를 설치해야 한다. 루비 설치는 다운로드 받은 파일을 설치하는 것으로 끝나지 않는다. 바로 로컬에서 '명렴프롬프트'등을 이용해서 진행되는데 본인은 이에 대한 지식이 전혀 없으므로 인터넷의 여러글을 참고하였다. 열댓개의 글을 조합하여 진행하였는데 대부분은 진행이 순조로웠으나 마지막에 딱 하나가 걸렸다. "wdm 0.1.1"과 관련된 메세지인데 다시 말하지만 프로그램밍 지식은 없다. 하지만 어찌어찌 찾아 나가다 보니 Chirpy의 Gemfile에서 0.1.1을 0.1로 바꾸어 주면 되는 것이었다. 해당 수정내용은 [이글](https://github.com/jekyll/jekyll/commit/3a8b2822f148671214e370e7b4e58f5063dd3462)을 참조바란다.
3. 루비 등 설치가 모두 끝나면 명령프롬프트에서 해당 폴더로 이동한 상태에서 "bundle exec jekyll serve"라고 입력하면 서버가 구동되고 "http://127.0.0.1:4000/"로 접속하면 로컬블로그를 볼 수 있다.
4. 중간과정은 블로그를 다시 만들거나, 컴퓨터를 포멧한다면 기록하면서 해봐야할듯하다.

### 기타

- 관리를 위해서 assets하위에 posts를 만들고 그 하위에 포스트명과 동일한 폴더를 만들어서 이미지를 넣었다(넣기로 했다).
- 글을 쓸때는 Front Matter라는 것을 넣어야 한다. 여러 옵션이 있는데 어떤 옵션을 쓸지 정해야 겠다.
- 메뉴 등의 한글화를 위해서 _config.yml에서 안내하는데로 _data에 하위 locales폴더를 만들고, 한글언어 파일은 [박성진](https://github.com/denev6/denev6.github.io/tree/master/_data/locales)님의 저장소에서 ko-KR파일만 가져왔다. 그리고 _config.ylml에서 'lang:' 값을 en에서 ko로 변경했다. 복사해온 파일명도 ko-KR.yml인데 ko.yml로 변경했다. 이렇게 한 이유는 giscus라는 코멘트프로그램을 쓸때 ko가 아니라 ko-KR로 되어 있으면 에러가 나는 경우가 있어서다.