---
title: Jekyll 테마 Chirpy Starter (1) 설치 및 언어설정
date: 2024-10-15 14:08:17 +0900
categories: [Blog, Chirpy]
tags: [Blog, Coding, Github, Chirpy]
media_subpath: /assets/posts/2024
image: blog.png
---

> 이 글은 `Chirpy v7.2.0 Starter` 버전 기준으로 작성되었으며, Github 환경입니다.
{: .prompt-info }


### 테마설치

[Chirpy Starter](https://github.com/cotes2020/chirpy-starter)의 설치는 아주 간단해서 [공식문서](https://chirpy.cotes.page/posts/getting-started/){:target="_blank"}만으로도 충분하지만 한번더 정리합니다.

1. `https://github.com/cotes2020/chirpy-starter`{: .filepath}로 이동
2. 오른쪽 상단에 <kbd>Use this template▾</kbd> 버튼 클릭
3. **Repository name**에 `githubID.github.io`{: .filepath}를 입력하고 오른쪽 하단에 <kbd>Create repository</kbd> 버튼 클릭
4. `https://github.com/githubID/githubID.github.io`{: .filepath}로 이동 후 <kbd><> Code</kbd>탭에서 상태 확인
![alt text](/10/github0.png){: width="350px" height="auto" }
_완료되면 초록색 체크표시가 된다_

5. `https://githubID.github.io`{: .filepath}로 접속했을 때 블로그가 보이면 성공

※ 위와 같이 하였으나 여전히 블로그가 보이지 않는 경우 아래 작업이 필요합니다. 아래 작업후 `잠시 대기 후` 블로그가 뜨는지 확인바랍니다. 만약 새로고침 하여도 변경이 없는 경우는 완전새로고침(<kbd>Ctrl</kbd> + <kbd>F5</kbd>)로도 확인해 보시기 바랍니다.

![alt text](/10/github11.png){:width="500px" height="auto"}
_1. Github 상단 <kbd>Action</kbd>에서 <kbd>New workflow</kbd>버튼 클릭_

![alt text](/10/github12.png){:width="500px" height="auto"}
_2. Jekyll로 검색한후 `Jekyll`만 써 있는 것의 <kbd>Configure</kbd> 버튼 클릭_

![alt text](/10/github13.png){:width="700px" height="auto"}
_3. 넘어간 화면에서 <kbd>Commit changes</kbd> 버튼 클릭(다음에 뜨는 팝업도 동일)_

> **Starer** vs. **일반**  
Starter에서 출발하여 여러 기능을 추가하고 UI나 Style 등을 조정한 것이 일반버전입니다. 공식문서를 포함한 대부분의 설명은 일반버전 기준으로 작성되고 있습니다.
{: .prompt-tip }

### 언어설정

일반버전의 경우 처음부터 `ko-KR.yml`파일이 존재하므로 `_config.yml`에서 `lang:`값만 en에서 ko-KR로 변경하면됩니다. 그러나 Starter의 경우 해당파일과 폴더가 존재하지 않기 때문에 아래의 과정을 거쳐야 합니다.

1. 일반버전 Repository에서 [해당파일](https://github.com/cotes2020/jekyll-theme-chirpy/blob/master/_data/locales/ko-KR.yml){:target="_blank"}의 코드를 복사하여 편집기에서 `ko-KR.yml`로 저장 
2. `ko-KR.yml`파일을 `_data/locales`에 넣기(locales폴더는 없을 것이므로 생성)
3. root폴더의 `_config.yml`파일의 `lang:`에 대한 값을 en에서 ko-KR로 변경
- `_data/locales`의 언어파일명과 `_config.yml`파일의 `lang:`에 대한 값이 동일해야함