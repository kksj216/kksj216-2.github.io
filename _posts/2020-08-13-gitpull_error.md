---
layout: post
title: git pull할 때 발생하는 에러 해결 
tags: [git]
color: rgb(204,153,153)
author: sujin
---



git pull을 할 때 발생하는 에러를 어떻게 해결했는지 정리한다. 

<br>

> error: Your local changes to the following files would be overwritten by merge:
>     [파일들...]
> Please, commit your changes or stash them before you can merge.
> error: The following untracked working tree files would be overwritten by merge:
>     [파일들...]
> Please move or remove them before you can merge.

<br>

 첫번째 에러의 경우에는 

```powershell
git stash
git pull
```

을 해서 해결할 수 있다. 

<br>

 두번째 에러는 몇가지 방법이 있다. 이 에러에서 파일들은 untracked 파일이기 때문에 git stash를 해도 해결되지 않는다. 

1. **add 하고 나서 stash한다.** 

```powershell
git add -A
git stash
```

2. **untracked 파일까지 stash해주는 옵션을 쓴다.** 

``` powershell
git stash --all
```

*** `git stash pop` 을 하면 untracked였던 파일은 un

저장되어 있는 작업중 가장 최근 stash를 가져온다.

3. **워킹 디렉토리 안의 untracked 파일을 모두 지운다.** 

```powershell
git clean [option]
```

<br>



** 캡쳐사진에서 git add는 생략되었음. 

![gitstash](/assets/img/gitimage/gitstash.png)

![gitpull](/assets/img/gitimage/gitpull.png)