---
title: Jekyll 테마 Chirpy Starter (5) 커스텀 도메인
date: 2024-11-06 19:56:57 +0900
categories: [Blog, Chirpy]
tags: [Blog, Domain] 
image: /assets/posts/blog.png
---

> 이 글은 `Chirpy v7.2.0 Starter` 버전 기준으로 작성되었으며, Github 환경입니다.
{: .prompt-info }

Jekyll 블로그가 설치되는 Github Pages는 `githubID.github.io`{: .filepath}라는 주소를 기본 제공합니다. Github는 개발자들에게 필수적인 사이트라 주소에 github.io가 들어간다면 개발자로서의 정체성을 표시하는 수단이 될수도 있습니다. 다만, (1) 주소가 길어지고 (2) 아이디명으로 제한되며 (3) 사이트를 이전할 경우 동일한 주소를 유지할 수 없다는 단점이 있습니다.

저는 동일한 주소를 유지하기 위해 `커스텀 도메인`을 연결했습니다. 커스텀 도메인을 연결하더라도 기존 주소도 살아 있습니다. 다만, 경우에 따라 기존 주소로 접속시 예상치 못한 오류가 발생할수도 있으니 일관된 주소를 쓰는 것이 좋습니다. 커스텀 도메인을 Github에 연결하는 방법은 다음과 같습니다.

### 도메인 DNS A레코드 추가  

`A레코드` 추가하는 것은 도메인을 Github Pages의 IP 주소에 연결하는 것입니다. 아래는 현재 A레코드이나 추후 변경될수도 있으므로 사용시점에 [이페이지](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site){:target="blank"}에서 재확인 바랍니다. 참고로 도메인 구매업체에 따라서 A레코드 입력가능 개수가 달라 한두개만 입력가능한 경우도 있습니다.

```
185.199.108.153
185.199.109.153
185.199.110.153
185.199.111.153
```
{: file="Github Pages A records" }

### Github Pages에 도메인 연결

Github의 <kbd>Setting > Pages > Custom domain</kbd>탭에서 도메인을 입력합니다. 도메인을 처음 입력하면 입력란 하단에 노란색으로 확인중이라는 메시지가 뜨다가 확인이 완료되면 성공메시지가 나옵니다. 이후에 맨 하단에 `Enforce HTTPS`를 채크해 보안을 강화합니다.

![alt text](/assets/posts/2024/11/github.png)
_이 페이지를 찾아올때마다 자동으로 DNS check를 다시 시작한다._

이후 `_config.yml`에서 기존주소를 신규 도메인인으로 변경합니다. 기본주소 설정은 그 외에는 없을 거라고 생각되나 필요한 부분이 있다면 추가로 수정합니다.