---

layout: post

title: Git이란? 

tags: [git]

color: rgb(204,153,153)

---

Git이 무엇인지, 그리고 Git과 관련된 간단한 용어를 정리한다.  

![git](/assets/img/gitimage/git.png)

<br>

# 1. Git이 뭘까? 

Git은 VCS(Version Control System) 즉, 버전 관리 시스템의 한 종류로 개발자들에게 버전관리를 하는 데에 도움을 준다. 

예를 들어, 'report.txt'를 만들었다가 내용을 수정하면 'report_final.txt'와 같은 식으로 수정할 수 있다. 여기에서 또 수정을 하게 되면 'report_final2.txt' 처럼 수정을 한다. 이런 방식은 비효율적이고, 전문적으로 버전을 관리하기 위해  깃을 사용한다. 

<br><br>

# 2. Git의 장점

- 여러 명이 동시에 작업을 할 수 있다. 

- 중앙저장소가 손상되어도 원상복구할 수 있다. 
- 분산 버전 관리이기 때문에 인터넷이 연결되지 않은 곳에서도 개발을 할 수 있고, 개인프로젝트인 경우에도 체계적인 개발을 할 수 있게 된다. 

<br><br>

# 3. Git과 Github

Git은 분산 버전 관리 시스템으로, 소스 코드를 효율적으로 관리할 수 있게 해주는 형상관리도구이다. 

Github은 Git을 사용하는 프로젝트를 지원하는 웹호스팅 서비스이다. Git을 업로드할 수 있는 웹사이트로, 개발자들의 버전 제어 및 공동 작업을 위한 플랫폼이다. 

<br><br>

# 4. Git의 기본 용어

- __Repository__: 저장소를 의미하고, 히스토리, 태그, 소스의 가지치기 혹은 branch에 따라 버전을 저장한다. 저장소를 통해 작업자가 변경한 모든 히스토리를 확인할 수 있다.

<br>

- __Working Tree__: 저장소를 어느 한 시점을 바라보는 작업자의 현재 시점이다. 

<br>

- __Staging Area__: 저장소에 커밋하기 전에 commit을 준비하는 위치이다. 

<br>

- __Commit__: 변경된 작업 상태를 점검을 마치면 확정하고 저장소에 저장하는 작업이다. 

<br>

- __Head__: 현재 작업중인 Branch를 가리키는 것이다. 

<br>

- __Branch__: 가지 또는 분기점을 의미한다. 작업을 하다가 현재상태를 복사하여 Branch에서 작업을 한 후에 완전하다 싶을 때 marge를 하여 작업한다. 

<br>

- __Merge__: 다른 Branch의 내용을 현재 branch로 가져와 합치는 작업이다. 

<br>

- __Push__: 로컬 저장소의 내용 중 원격저장소에 반영되지 않은 커밋을 원격 저장소로 보내는 과정이다. 

<br>

- __Pull__: push와 반대로 원격 저장소에 있는 내용 중 로컬 저장소에 반영되지 않은 내용을 가져와서 로컬저장소에 저장하는 과정이다. 이를 통해 다른 팀원이 변경하고 push한 내용을 로컬 저장소로 가져올 수 있다. (push과정에서 충돌이 일어나서 거절된 경우에는 pull을 통해 원격저장소의 변경내용을 반영한 뒤 다시 push를 시도해야 한다.)

<br>

<br>

# 5. Git의 기초 명령어

- __git init__: 깃 저장소를 초기화한다.

<br>

- __git status__: 저장소 상태를 체크한다. 어떤 파일이 저장소안에 있는지, 커밋이 필요한 변경사항이 있는지, 현재 저장소의 어떤 브랜치에서 작업하고 있는지 등을 볼 수 있다. 
  - __git status -s__: 상태를 짧게 보여준다. 

<br>

- __git clone__: 원격 저장소의 저장소를 내 로켈에서 이용할 수 있도록 그대로 복사해서 가져온다. 

<br>

- __git add__: 저장소에 새 파일을 추가하는 것이 아니라, 깃이 이 파일들을 지켜보게 한다. 

<br>

- __git commit -m "messages"__: :star: 파일을 수정한 후 변경된 내용을 저장한다. 

<br>

- __git show__: commit 정보를 보여준다. 

<br>

- __git push__: 로컬에서 작업하고 내가 날린 commit 을 깃헙에서도 온라인으로 보고싶다면 push를 해야 한다. 

<br>

- __git pull__: 로컬에서 작업할 때 작업하고 있는 저장소의 최신버전을 원할 때 사용한다. 

<br>

- __git log__: 커밋내역을 확인하고 싶을 때 사용한다. 
  - __git log --oneline__: 커밋내역을 각 간단하게 한줄로 보여준다. 
  - __git log --pretty=oneline__: 한줄로 보여준다. 
  - __git log --graph__: 커밋 내역을 그래프로 보여준다.  

<br>

- __git diff__: working directory에 있는 modified 상태 파일과 staging area에 있는 파일 사이의 변경내용을 보여준다. [ working directory : staging area ]
  - __git diff #### ????__: 두 버전 사이에 변경내용을 보여준다. _[ commited1 : commited2 ]_
  - __git diff --staged__: staging area에 있는 파일과 commit되어 있는 파일을 비교한다. _[ staging area : commited ]_

<br>

- __git reset (file)__: staged 되어 있는 파일을 unstage시킨다.  _[ staged -> unstaged ]_

![gitreset](/assets/img/gitimage/gitreset.PNG)

<br>

- __git checkout (file)__: working directory에서 파일을 변경했던 것을 commited 파일로 되돌려준다. checkout하고나면 working directory에서 변경했던 것은 다시 가져올 수 없다. _[ commited -> working directory ]_

![gitcheckout](/assets/img/gitimage/gitcheckout.PNG)

<br>

- __git branch branch_name__ : 여러 협업자와 작업하고 자신만의 변경을 원할 때 이 명령어로 새로운 branch를 만들고 자신만의 변경사항과 파일 추가 등의 commit 타임라인을 만든다. 

<br>

- __git checkout branch_name__: 현재 위치하고 있지 않은 저장소를 체크아웃한다. 체크하길 원하는 저장소로 옮겨갈 수 있다. master 브랜치로 가고 싶으면 git checkout master를 사용하면 된다. 

<br>

- __git master branch_name__: branch에서 작업을 끝내고 모든 협업자가 볼 수 있는 master 브랜치로 병합할 수 있다. 

<br>

- __git blame (file)__: 파일의 커밋정보를 줄 단위로 보여준다. 

![gitblame](/assets/img/gitimage/gitblame.PNG)

<br>



![gitstatus](https://seonkyukim.github.io/assets/images/2019-02-24-git-status/04.png)

<br>