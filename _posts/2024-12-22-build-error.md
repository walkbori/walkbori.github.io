---
title: Jekyll Build Error
date: 2024-12-22 13:22:42 +0900
categories: [Coding, Others]
tags: [Blog, Coding, Github, Build]
media_subpath: /assets/posts/2024
image: blog.png
---

갑자기 아래와 같은 Build 오류가 발생하였습니다.

```
Run ruby/setup-ruby@8575951200e472d5f2d95c625da0c7bec8217c42
  with:
    ruby-version: 3.1
    bundler-cache: true
    cache-version: 0
Error: The current runner (ubuntu-24.04-x64) was detected as self-hosted because the platform does not match a GitHub-hosted runner image (or that image is deprecated and no longer supported).
In such a case, you should install Ruby in the $RUNNER_TOOL_CACHE yourself, for example using https://github.com/rbenv/ruby-build
You can take inspiration from this workflow for more details: https://github.com/ruby/ruby-builder/blob/master/.github/workflows/build.yml
$ ruby-build 3.1.4 /opt/hostedtoolcache/Ruby/3.1.4/x64
Once that completes successfully, mark it as complete with:
$ touch /opt/hostedtoolcache/Ruby/3.1.4/x64.complete
It is your responsibility to ensure installing Ruby like that is not done in parallel.
```

관련 이슈글에 달린 글중에 [이 내용](https://github.com/ruby/setup-ruby/issues/595#issuecomment-2396187213)을 따라 
`Workflow file`을 수정했고, 해결되었습니다.

```yml
# 수정전
      - name: Setup Ruby
        uses: ruby/setup-ruby@8575951200e472d5f2d95c625da0c7bec8217c42 # v1.161.0
        
# 수정후
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1
```