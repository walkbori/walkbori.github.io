---
title: "Jekyll 테마 Chirpy Starter (2) 댓글기능 : Giscus 설치"
date: 2024-10-26 17:25:24 +0900
categories: [Blog, Chirpy]
tags: [Blog, Coding, Github, Chirpy, Giscus]
image: /assets/posts/blog.png
---

> 이 글은 `Chirpy v7.2.0 Starter` 버전 기준으로 작성되었으며, Github 환경입니다.
{: .prompt-info }

공식사이트에 따르면 Jekyll은 심플한, 블로그 지향적, 정적사이트 생성도구입니다. 여기서 정적사이트라는 것은 데이터베이스가 없다는 것이고 덕분에 댓글기능을 사용하기 위해서는 추가 작업이 필요합니다. Chirpy는 `_config.yml`에 Disqus, Utterances, Giscus 세가지 댓글 시스템을 제시합니다.

### 댓글 시스템 비교

|항목|Giscus|Utterances|Disqus|
|---|---|---|---|
|저장소|Github<br>Discussions|Github<br>Issues|Disqus|
|로그인|Github<br>Only|Github<br>Only|소셜로그인<br>지원|
|비회원|X|X|O|
|대댓글|O|X|O|
|광고|X|X|O|

### Giscus 설치

Giscus는 Disqus에 비해서 폐쇄적이나 DATA가 외부가 아닌 내부에서 관리되고 광고가 없고 가볍다는 것이 강점입니다. 설치 방법은 다음과 같습니다.

#### 1. Github 저장소 생성

1. 댓글 저장용 Repository 생성 : Repository name을 입력하고 `Public`선택후 <kbd>Create repository</kbd>버튼 클릭
![alt text](/assets/posts/2024/10/github1.png)

2. 생성된 Repository의 <kbd>Setting > General > Features</kbd>탭에서 Discusssions 활성화(채크만) 
![alt text](/assets/posts/2024/10/github2.png)

3. 댓글 저장용 Discussions 카테고리 생성  
![alt text](/assets/posts/2024/10/github3.png){:width="400px" height="auto"}
_3.1 우측상단 <kbd>연필</kbd>버튼 클릭_
![alt text](/assets/posts/2024/10/github4.png)
_3.2 우측상단 <kbd>New category</kbd>버튼 클릭_
![alt text](/assets/posts/2024/10/github5.png)
_3.3 Discussion Format을 `Announcement`로 선택후 우측하단 <kbd>Create</kbd>버튼 클릭_

> 새로운 카테고리가 필수는 아닙니다. `Announcements`카테고리를 활용할수 있지만, 가능하면 디폴트 항목은 그대로 남겨두기 위해 새롭게 만들었습니다. 만약, 이 과정을 생략한다면 후단의 Jekyll 설정시 `Announcements`를 선택하면 됩니다.
{: .prompt-tip }


#### 2. Giscus App 설치

4. [Giscuss Apps 페이지](https://github.com/apps/giscus){:target="_blank"}에서 <kbd>Install</kbd>버튼 클릭
![alt text](/assets/posts/2024/10/github6.png)

5. 대상 Repository로 `Only select repository > 1번에서 생성한 Repository` 선택후 <kbd>Install</kbd>버튼 클릭
![alt text](/assets/posts/2024/10/github7.png){:width="500px" height="auto"}

#### 3. Jekyll 설정 참조정보 생성

1. [Giscus 설정 가이드 페이지](https://giscus.app/ko){:target="_blank"}로 이동

2. 다른 부분은 그대로 두고 `저장소`는 githubID/giscous용으로 생성한 Repository, `Discusstions 카테고리`는 앞선 단계에서 만들었던 Giscus용 카테고리 선택(만들지 않은 경우 `Announcements`선택)

> 가이드 페이지는 상단에서 옵션을 선택하면 맨 하단에 코드를 자동생성해줄 뿐 그 자체로는 블로그에 영향을 미치지 않습니다. 이 코드를 복사하여 본인의 블로그에 넣거나, 필요한 설정 값만을 참조하여 반영해야 비로서 본인의 블로그에 적용이 됩니다. Chirpy는 설정값만 `_config.yml`에 반영하면 됩니다.
{: .prompt-tip }
![alt text](/assets/posts/2024/10/github8.png)
![alt text](/assets/posts/2024/10/github9.png)

#### 4. Jekyll 설정 반영

전단계에서 생성한 참조정보를 참고하여 `_config.yml`에서 해당부분을 작성하면 됩니다. 너무 세세한 부분의 설정값에 대한 설명은 생략하였습니다.

```html
<script src="https://giscus.app/client.js"
        data-repo="walkbori/giscus"
        data-repo-id="R_abcd"
        data-category="comments"
        data-category-id="DIC_abcd"
        data-mapping="pathname"
        data-strict="0"
        data-reactions-enabled="0"
        data-emit-metadata="0"
        data-input-position="bottom"
        data-theme="preferred_color_scheme"
        data-lang="ko"
        crossorigin="anonymous"
        async>
</script>
```
{: file="전단계에서 생성한 참조정보" }

```yml
comments:
  provider: giscus
  # ... 중략
  giscus:
    repo: walkbori/giscus # data-repo
    repo_id: R_abcd       # data-repo-id
    category: comments    # data-category
    category_id: DIC_abcd # data-category-id
    mapping:              # data-mapping(디폴트값과 동일하여 비워둠)
    strict:               # data-strict (디폴트값과 동일하여 비워둠)
    input_position:       # data-input-position   (디폴트값과 동일하여 비워둠)
    lang: ko              # data-lang             (디폴트값은 `site.lang`) 
    reactions_enabled: 0  # data-reactions-enabled(디폴트값은 1)
```
{: file="_config.yml의 Giscus 설정부분" }

> `lang:`값을 비워두지 않고 `ko`로 써두는 이유는 `site.lang`값이 정확하게 `ko`와 일치하지 않는 경우 오류가 발생하기 때문입니다. [Jekyll 테마 Chirpy Starter (1) 설치 및 언어설정](/posts/blog-install)을 따라서 블로그를 생성한 경우라면 `site.lang`값이 `ko-KR`인 상태입니다. 만약, `lang:`값을 비워두고 싶다면 `_config.yml`에서 `lang:`값을 `ko`로 변경하고, `_data/locales/`에 위치한 `ko-KR.yml`파일명을 `ko.yml`로 변경하면 됩니다.    
{: .prompt-tip }