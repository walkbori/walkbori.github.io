---
title: Jekyll 테마 Chirpy Starter (6) 초안작성(draft)
date: 2024-11-10 13:36:57 +0900
categories: [Blog, Chirpy]
tags: [Blog, Draft]
media_subpath: /assets/posts/2024
image: blog.png
---

> 이 글은 `Chirpy v7.2.0 Starter` 버전 기준으로 작성되었으며, Github 환경입니다.
{: .prompt-info }

Jekyll에서 `_post`안에 있는 문서는 발행됩니다. 발행되지 않게 하라면 [Front Matter](https://chirpy.cotes.page/posts/write-a-new-post/#front-matter){:target="_blacnk"}에 `published: false`를 추가하면 됩니다. 문제는 이렇게 하면 로컬에서도 보이지 않습니다. 로컬에서는 보이고 웹에서는 보이지 않게 하려면 아래 방법을 쓰면 됩니다.

1. 작성한 글(마크다운문서)을 `_draft`폴더에 넣는다(Starter에는 해당 폴더가 없으니 새로 생성).
2. 로컬에서 Jekyll 서버 구동 명령어 뒤에 `--drafts`를 붙인다.

```
bundle exec Jekyll serve --drafts
```
Jekyll 로컬 서버와 관련해서는 [Jekyll 테마 Chirpy Starter (4) 로컬서버](/posts/blog-local-server)를 참조바랍니다.