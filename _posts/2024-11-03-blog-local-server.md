---
title: Jekyll 테마 Chirpy Starter (4) 로컬서버
date: 2024-11-03 12:42:17 +0900
categories: [Blog, Chirpy]
tags: [Blog, Coding, Chirpy, Ruby, Server, CMD]
image: /assets/posts/blog.png
---

> 이 글은 `Chirpy v7.2.0 Starter` 버전 기준으로 작성되었으며, Github 환경입니다.
{: .prompt-info }

Jekyll은 변경사항이 있을 때마다 commit과 push를 하거나 직접 Github에서 수정해야 합니다. 문제는 (1) 불필요한 변경내역이 많아지고 (2) 변경결과를 확인하기까지 시간이 걸린다는 점입니다. 로컬서버를 만들어 미리 확인한다면 이러한 문제를 해결할 수 있습니다. 찾아본 방법은 Ruby를 이용한 방법과 Docker를 이용한 방법입니다.

## 로컬서버 구성방법 선택하기

Ruby를 설치하는 방법과 Docker를 이용하는 방법의 특징은 아래와 같습니다.

- Ruby를 이용 : Ruby만 설치하면 되고 이후에도 Ruby만 조작
- Docker를 이용 : Docker외 플러그인 등 설치필요하며 Docker외 에디터까지 조작

여기서 설명할 방법은 Ruby를 이용한 방법입니다. 관련된 글들을 많이 찾아보았는데 Ruby에 대한 글들의 설명은 일관성이 있어 참고하기 용이했지만, Docker에 대한 글들은 작성자마다 방법이 조금씩 달라 비개발자 입장에서 참고하기 어려웠습니다. Docker는 좀더 숙성된 후에 시도해 보는 것이 좋겠습니다.

## Ruby를 이용하여 로컬서버 구성하기

### 1. Ruby설치

1. 공식사이트에서 Ruby [다운로드](https://rubyinstaller.org/downloads/){:target="_blank"}  
![alt text](/assets/posts/2024/11/ruby.png){: width="550px" height="auto" }
_WITH DEVKIT 최신 버전을 받으면 된다_

2. 설치 
 
![alt text](/assets/posts/2024/11/ruby2.png){: width="550px" height="auto" }
_2.1 'I accept the License' 선택후 <kbd>Next</kbd>_

![alt text](/assets/posts/2024/11/ruby3.png){: width="550px" height="auto" }
_2.2 모두 채크후 <kbd>Install</kbd>_

![alt text](/assets/posts/2024/11/ruby4.png){:width="550px" height="auto" }
_2.3 모두 채크후 <kbd>Next</kbd>_

![alt text](/assets/posts/2024/11/ruby5.png){:width="550px" height="auto" }
_2.4 설치진행 대기_

![alt text](/assets/posts/2024/11/ruby6.png){:width="550px" height="auto" }
_2.5 채크후 <kbd>Finish</kbd>_

![alt text](/assets/posts/2024/11/ruby7.png){:width="550px" height="auto" }
_2.6 아무것도 입력하지 말고 그냥 <kbd>엔터</kbd>_

![alt text](/assets/posts/2024/11/ruby8.png){:width="550px" height="auto" }
_2.7 다음 질문에도 그냥 <kbd>엔터</kbd>(창이 닫힘)_

![alt text](/assets/posts/2024/11/ruby9.png){:width="550px" height="auto" }
_2.8 명령프롬프트 실행후 `ruby -v` 입력하여 설치확인_

### 2. CMD에서 bundle 설치 및 서버 실행

 `Jekyll Chirpy Starter`가 로컬에 저장된 상태에서의 과정입니다. 명령어는 명령프롬프트(CMD)에서 Jekyll폴더로 이동후 실행해야 합니다.

```
1. 구동을 위한 라이브러리 설치
gem install jekyll bundler

2. bundler에서 Chirpy에 필요한 bundle 설치
bundle install

3. 서버실행
bundle exec jekyll serve

4. 실행확인(http://127.0.0.1:4000/로 접속)
※ CMD에서 서버를 실행하면 맨 하단 바로 위줄에 Server address:에 표시되는 주소
```
![alt text](/assets/posts/2024/11/cmd.png){:width="500px" height="auto" }
_Jekyll 폴더로 이동후 1번 실행 후 2번 입력_

![alt text](/assets/posts/2024/11/cmd2.png){:width="500px" height="auto" }
_2번을 실행하면 wdm 관련 error가 발생한다._

![alt text](/assets/posts/2024/11/cmd3.png){:width="700px" height="auto" }
_Jeyll의 Gemfile을 수정(하단 안내)_

> ~~bundler 설치과정에서 `wdm`오류가 발생합니다. 이는 Jekyll폴더의 `Gemfile`에서 `gem "wdm", "~> 0.1.1"`을 `gem "wdm", "~> 0.1"`로 수정후 저장하고 다시 실행하면 해결됩니다.~~ `7.1.1`에서 발생하던 버그가 `7.2.0`부터는 발생하지 않게 개선되었습니다.
{: .prompt-info }

![alt text](/assets/posts/2024/11/cmd4.png){:width="500px" height="auto" }
_2번을 재실행하여 설치성공 후 3번 실행_

![alt text](/assets/posts/2024/11/cmd5.png){:width="500px" height="auto" }
_서버 실행에 성공한 모습_

![alt text](/assets/posts/2024/11/cmd6.png){:width="500px" height="auto" }
_로컬서버에서 블로그에 접속 성공한 화면_



### 3. 배치 파일(Batch File) 작성

로컬에서 블로그를 확인하기 위해서는 매번 CMD로 서버를 구동해야 합니다. CMD의 경우 새로 열면 기본주소가 `C:\Users\계정>`이므로 매번 Jekyll폴더로 이동후 명령어로 서버를 실행해야 합니다. 이는 매우 번거로운 일이므로 bat파일을 만들어 해당파일실행으로 편하게 구동할수 있습니다. 예시 코드는 아래와 같고 확장자를 `.bat`으로 저장하면됩니다.

```
cd D:\walkbori.github.io
bundle exec Jekyll serve
```
> **bat 파일을 작업표시줄에 등록하는 방법**  
bat파일 또는 bat파일의 바로가기도 작업표시줄에 등록이 불가능합니다. 다만, bat파일의 바로가기의 `속성 > 바로가기 > 대상(T)`의 값 앞에 `C:\Windows\System32\cmd.exe /c `를 추가하면 등록 가능합니다.
{: .prompt-tip }