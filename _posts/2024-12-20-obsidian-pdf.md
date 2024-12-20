---
title: "Obsidian 내장 PDF Viewer에서 글자가 찌그러져 보이는 경우[미해결]"
date: 2024-12-20 20:30:14 +0900
categories: [Coding, Others]
tags: [Obsidian, PDF]
media_subpath: /assets/posts/2024
image: blog.png
---

Obsidian에서 PDF는 별도 프로그램 실행없이 내장뷰어를 통해서 볼수 있다. 그러나, PPT 등에서 Export한 PDF의 경우 글자가 찌그러져 보이는 현상이 발생했다. [Obsidian Forum](https://forum.obsidian.md/t/blurry-pdfs/66289)과 [Github](https://github.com/RyotaUshio/obsidian-pdf-plus/issues/97)에서 유사한 문제에 대한 논의를 살펴보니 자체 PDF Rendering 파일인 pdf.js를 수정하여 해결한 경우가 있었다.

- 방법1. `pdfPage.getViewport({ scale: 1 })`을 `pdfPage.getViewport({ scale: 4 })`로 수정
- 방법2. `window.devicePixelRatio||1`을 `window.devicePixelRatio||2`로 수정

수정해야할 구체적인 파일은 `pdf.viewer.min.js`인데 경로는 아래와 같습니다. 해당 파일은 obsidian.asar이라는 파일에 패킹되어 있다. VSCode에서 해당 파일을 열고 수정 후 저장까지 되는 듯 하지만, 다시 열어보면 저장이 되지 않기 때문에 언패킹을 해서 수정하고 다시 리패킹을 해야한다.

- 파일경로 : Obsidian > resources > obsidian.asar
- 언패킹후 : lib > pdfjs > pdf.viewer.min.js

언패킹은 명령어를 통한 방법이 있으나 익숙하지 않아 [7-zip](https://www.7-zip.org/)을 이용한 방법을 사용했다. 찾아본 글에는 7-zip를 설치하고 asar플러그인을 추가로 설치하는 방법을 제시하였으나, 7-zip기본만 설치하고 VSCode에서 asar플러그인(VSCode Archive, YuTengjing)을 설치하여 처리했다. 사용법은 VSCode플러그인 페이지에 소개되어 있어 생략.

방법1과 방법2를 모두 실험해 보았으나, 처음에는 해결된건가 싶었는데 착각이었고 문제는 해결되지 않았다. 테스트한 환경은 윈도우 11과 윈도우 10이며, 다음 사람을 위해 기록을 남겨둔다.