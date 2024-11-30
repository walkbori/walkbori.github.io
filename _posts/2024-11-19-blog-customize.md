---
title: Jekyll 테마 Chirpy Starter (7) 기타설정
date: 2024-11-19 18:51:46 +0900
categories: [Blog, Chirpy]
tags: [Blog, Customize]
media_subpath: /assets/posts/2024
image: blog.png
---

> 이 글은 `Chirpy v7.2.0 Starter` 버전 기준으로 작성되었으며, Github 환경입니다.
{: .prompt-info }

Jekyll 테마 Chirpy Starter와 관련된 주요한 조정은 [Jekyll 테마 Chirpy Starter (6) 초안작성(draft)](/posts/blog-draft)로 끝났습니다. 이 글에는 그 외에 부수적인 조정사항을 기록하며 변경사항이 있을 때마다 수시로 업데이트 됩니다.

### Syntax 왼쪽 상단 원 색상

아무설정도 하지 않을 경우 Syntax 표시기의 왼쪽 상단 원 3개는 회색인데 여기에 색상을 넣는 방법입니다. 먼저 `_sass > base > _syntax.scss`를 색상코드를 아래와 같이(본 블로그) 또는 본인이 원하는 색상으로 입력하면 됩니다. #으로 시작하는 코드가 색상코드이며 순차로 왼쪽·가운데·오른쪽 원입니다.

```scss
      &::before {
        content: '';
        display: inline-block;
        margin-left: $dot-margin;
        width: v.$code-dot-size;
        height: v.$code-dot-size;
        border-radius: 50%;
        background-color: #EB6150;
        box-shadow: (v.$code-dot-size + v.$code-dot-gap) 0 0
        #F3B63B,
          (v.$code-dot-size + v.$code-dot-gap) * 2 0 0
          #54BB44;
      }
```
{: file="_sass/base/_syntax.scss" }

### TOC(목차) 펼치기

TOC는 Table of Contents의 약자로 본 블로그 오른쪽에 표시되는 목차를 의미합니다. 기본세팅은 해당위치로 이동하기 전까지 하위 목차는 접혀 있는데 이것을 처음부터 펼치는 [방법](https://github.com/cotes2020/jekyll-theme-chirpy/discussions/1706)입니다. 해당파일(Syntax제목참조)에 아래의 코드를 추가하면됩니다.

```scss
.is-collapsed {
  max-height: none !important;
}
```
{: file="assets/css/jekyll-theme-chirpy.scss" }

### 채크박스 색상 바꾸기

아래 예시는 light버전이고 dark버전은 typography-dark.scss에서 조정하면됩니다.

- [x] 예시

```scss
--checkbox-checked-color: #02bc7d; /* 원본색상 #07a8f7 */
```
{: file="_sass/themes/_light.scss" }

### 프리뷰 이미지 본문만 안나오게 하기

목록(블로그 접속 첫화면의 글목록)에서는 이미지가 보이고, 본문에서는 보이지 않게 하려면 `_layouts/post.html`파일을 수정해야 합니다. Starter에는 해당 폴더가 없으므로 [Jekyll 테마 Chirpy Starter (3) 폰트설정](/posts/blog-font)를 참조하여 해당 폴더 및 파일을 추가하고 해당부분을 아래와 같이 주석처리합니다.

```html
<!-- div class="mt-3 mb-3">
  # 중략
</div -->
```
{: file="_layouts/post.html" }

### 아카이브(기록)에 표시된 연도의 닷표시 위치 조정

[여기](/archives)로 가면 월과 연도가 표시되는데, 월의 경우 점이 라인과 일치하나 연의 경우 가운데가 빈 점이 라인과 일치하지 않습니다. 원본테마는 일치할 것이나, 본 블로그는 일치하지 않는데 아마도 기본 폰트를 바꾸었기 때문인 것으로 보입니다. 수정하는 법은 간단합다. 아래에서 표시한 부분의 수치를 고쳐가면 맞추면 됩니다.

```scss
    /* Year dot */
    &::after {
      content: '';
      display: inline-block;
      position: relative;
      border-radius: 50%;
      width: 12px;
      height: 12px;
      left: 13.2px; /* 이곳수치 조정, 원래값은 21.5px */
      border: 3px solid;
      background-color: var(--timeline-year-dot-color);
      border-color: var(--timeline-node-bg);
      box-shadow: 0 0 2px 0 #c2c6cc;
      z-index: 1;
    }
```
{: file="_sass/pages/_archives.scss" }

### 각주 폰트크기 조절

각주는 어떠한 항목에 대한 설명을 글의 맨 끝에서 보충합니다.[^1] 아무설정도 하지 않으면 각주의 글자 크기와 본문 글자 크기가 같아서 보기에 좋지 않습니다. 이를 수정하기 위해서는 아래와 `/* 폰트사이즈 */` 부분을 추가 하면 됩니다. 그 외에 저는 문서 끝단 각주모음 위에 본문과의 구별을 위해 선을 하나 넣었습니다. 일부러 선 길이는 본문 넓이의 30%로 설정했습니다.

```scss
.footnotes > ol {
  padding-left: 2rem;
  margin-top: 0.5rem;
  font-size: 0.9em; /* 폰트사이즈 */
  margin-top:0; /* 문서끝단 각주위의 선 */

  > li {
    &:not(:last-child) {
      margin-bottom: 0.3rem;
    }

    @extend %sup-fn-target;

    > p {
      margin-left: 0.25em;

      @include mt-mb(0);
    }
  }
}

/* 문서끝단 각주위의 선 */
.footnotes:before {
  content: "";
  border-bottom: 1px solid #d3d3d3;
  width: 30%;
  display: block;
  margin:0px;
  padding:0px;
} /* 여기까지 */
```
{: file="_sass/base/typography.scss" }

[^1]: 이러한 것이 각주입니다.

### 글자 또는 문장 강조하기(글자배경)

해당파일 맨 하단에 아래 코드를 추가하고, 글을 작성할때는 `<span class="txt_bg">내용</span>`으로 묶어 줍니다. <span class="txt_bg">이렇게</span> 나옵니다.

```scss
/* Light */
.txt_bg {background:linear-gradient(180deg,#00ff0000 70%,#e6f9ea 30%);}
/* Dartk */
.txt_bg {background:linear-gradient(180deg,#00ff0000 70%,#7c7d7c 30%);}
```
{: file="_sass/themes/_light.scss&_dark.scss" }

> `_base.scss`등에 추가하면 light/dart mode 모두 같은 색상으로 나옵니다. 위의 코드는 light모드와 dark 모드의 색상을 다르게 하기위해 각각의 모드 파일에 분리하여 넣은 경우입니다. 주의할 점은 코드를 마지막에 그냥 넣는 것이아니라 마지막 중괄호`}`안에 넣어야 제대로 작동합니다. 
{: .prompt-tip }


### more/less 아이콘 변경 (details & summary tag)

버튼을 누르면 접기와 펼치기가 되는 `details`와 `summary`에 사용되는 기호 또는 아이콘, 문구 설정입니다. `_sass/base/_base.scss` 맨 하단에 아래 내용을 추가하고, 필요에 따라서 설정을 변경합니다.

```scss
/* 기본 화살표 숨기기 */
summary {
  list-style: none;
  cursor: pointer;
}

summary::-webkit-details-marker {
  display: none; /* 크롬, 사파리 */
}

summary::marker {
  display: none; /* 파이어폭스, 최신 브라우저 */
}

/* 커스텀 아이콘 추가 */
summary::before {
  content: "🔻More: "; /* 원하는 기호로 변경 */
  font-size: 16px;
  font-weight: 600;
  margin-right: 10px;
  display: inline-block;
  transform: rotate(0deg);
  transition: transform 0.3s ease;
}

/* 열렸을 때 아이콘 회전 */
details[open] summary::before {
  content: "🔺Less: "; /* 원하는 기호로 변경 */
  font-weight: 600;
/*  transform: rotate(90deg);  90도 회전(필요시 사용) */
}
```
{: file="_sass/base/_base.scss" }

<br><br><br>
이 외에 변경 사항이 수시로 추가&수정됩니다.