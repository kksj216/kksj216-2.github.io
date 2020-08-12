---
layout: post

title: Fork한 저장소를 원본 저장소와 동기화하기

tags: [git]

color: rgb(204,153,153)
author: sujin
---



Github에서 저장소를 fork하고, 원본 저장소의 변경내용을 fork한 내 저장소에 반영하기 위한 방법을 정리한다. 

<br>

## 방법

1. Fork한 저장소를 로컬로 clone 한다. 
2. 로컬에 있는 Fork저장소에 remote를 설정해준다. 
3. Fork저장소에 원본 저장소를 Merge한다. 

<br>

<br>

## 실제사용 예시

- Fork 한 저장소를 로컬로 clone

![gitclone](/assets/img/gitimage/clone.PNG)

<br>

- 로컬 저장소로 이동

![cd](/assets/img/gitimage/cd.PNG)

<br>

- 현재 설정된 리모트 저장소 조회

![remote](/assets/img/gitimage/gitremote-v.PNG)

<br>

- 리모트 저장소 추가

![remoteadd](/assets/img/gitimage/gitremoteadd.PNG)

<br>

- 리모트 저장소 확인 

![remote2](/assets/img/gitimage/gitremote-v2.PNG)

<br>

- 리모트 저장소 fetch

![fetch](/assets/img/gitimage/gitfetch.PNG)

<br>

- 리모트 저장소 Merge

![merge](/assets/img/gitimage/gitmerge.PNG)

<br>

- Fork 저장소로 push

![push](/assets/img/gitimage/gitpush.PNG)

<br>