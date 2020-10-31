---

layout: post
title: Tomcat 개발환경설정 (Mac)
tags: [web] [Mac]
color: rgb(204, 204, 255)

---

Tomcat 개발환경 설치 과정 정리

Mac에서 tomcat 설치하는 과정을 정리한다. Apache Tomcat사이트로 접속해서 다운로드하고 패키지 경로를 설정하여 사용하는 방법도 있다. 여기에서는 macOS용 패키지 관리자 Homebrew를 이용해서 설치하는 과정을 정리한다! Homebrew를 통해 설치한 이유는 환경변수 설정이 필요없고 관리가 용이하기 때문이다. 

<br>

# 개발환경 설정 - Tomcat (mac)

## Tomcat? 

tomcat은 ASP(Apache Software Foundation)에서 개발한 웹 어플리케이션 서버(WAS)이다. 

톰캣은 웹 서버와 연동하여 실행할 수 있는 자바 환경을 제공하여 자바서버 페이지 (JSP)와 자바 서블릿이 실행할 수 있는 환경을 제공하고 있다. 톰캣은 관리툴을 통해 설정을 변경할 수 있지만, XML 파일을 편집하여 설정할 수도 있다. 그리고, 톰캣은 HTTP 서버도 자체 내장하기도 한다.

<br>

- Apache Tomcat 설치 방법

![br-up](/assets/img/pp1/br-up.png)

> Homebrew 사용하기 전에 'brew update' 명령어로 최신버전으로 업데이트를 해준다. 

<br>

![br-search](/assets/img/pp1/br-search.png)

> 'brew search tomcat' 명령어를 이용하여 자신이 설치할 톰캣 버전을 확인한다. 목록에서 버전 8까지 있는 것을 확인할 수 있다. 이 글을 쓰는 시점에 가장 최신 버전은 9이다. 

<br>

![br-stop](/assets/img/pp1/inst-tom.png)

> 'brew install tomcat'명령어를 이용해서 최신 버전을 설치한다. (버전 6~8을 설치하고 싶으면 목록에서 나온 명칭을 그대로 입력해주면 된다. ex. "brew install tomcat@8" 명령어를 입력하면 버전 8이 설치됨)

<br>

![br-li](/assets/img/pp1/br-li.png)

> 'brew list'명령어를 이용하면 "tomcat"이 정상적으로 설치된 것을 확인할 수 있다!

<br>

<br>

- Apache Tomcat 설치 경로

![tom-fol](/assets/img/pp1/tom-fol.png)

![cellar](/assets/img/pp1/cellar.png)

> "/usr/local/Cellar" 디렉토리로 이동하면 자신이 설치한 tomcat이 있다. 자신이 설치한 버전에 따라서 폴더명이 다를 수 있다!! 

<br>

<br>

- Apache Tomcat 실행 및 종료

![tom-start](/assets/img/pp1/tom-start.png)

> "cd /usr/local/Cellar/tomcat/9.0.12/bin" 명령어를 이용하여톰캣 bin 디렉토리로 이동한다. 디렉토리를 이동한 후 ./catalina start 명령어를 이용하면 서버가 실행된다. 

<br>

![localh](/assets/img/pp1/localh.png)

> 브라우저를 실행시킨 후 주소 검색창에 "localhost:8080"을 입력 후 접속해서 위와 같은 화면이 나오면 정상적으로 서버가 구동되고 있는 것이다~!

<br>

![br-stop](/assets/img/pp1/br-stop.png)

> 터미널 창에 "./catalina stop" 명령어를 입력하면 서버가 종료된다. 
>
> 이제 "localhost:8080"에 접속하려고 하면 서버가 종료되었기 때문에 접속이 불가능하게 된다. 

<br>

<br>

### Summary

1. 터미널에서 "brew install tomcat" 명령어로 설치 

2. "/usr/local/Cellar/" 경로에 톰캣 설치완료

3. "./catalina start" 명령어로 톰캣 서버 실행

4. "./catalina stop" 명령어로 톰캣 서버 종료

<br>

참고한 블로그 - [https://whitepaek.tistory.com/12](https://whitepaek.tistory.com/12 ) 