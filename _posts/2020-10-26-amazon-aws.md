---
layout: post

title: Amazon AWS로 spring프로젝트 배포

tags: [web]

color: rgb(204,153,153)



---

spring프로젝트를 Amazon aws ec2를 통해 배포하는 과정이다. 아마존에서 서버생성하는 과정은 생략한다. (YouTube '생활코딩' 참고) 

<br>

내가 배포하려던 프로젝트에 에러가 있었어서 제대로 확인하지 못했음. 그래서 서버로 올리는 과정까지 참고하기!

<br>



![aws-1](/assets/img/amazon-aws/aws-1.png)

![aws-2](/assets/img/amazon-aws/aws-2.png)

handongpwd.pem 이 저장되어 있는 /Users/sujin/Desktop/2020-2 에서, **ssh -i "handongpwd.pem" ubuntu@ec2-54-167-240-74.compute-1.amazonaws.com** 로 접속한다. 

첫번째 캡쳐와 같이 unprotected private key file 이라고 뜨는 경우에는 chmod 400으로 권한을 바꿔주면 된다. 

![aws-3](/assets/img/amazon-aws/aws-3.png)



접속했으면 

![aws-4](/assets/img/amazon-aws/aws-4.png)

![aws-5](/assets/img/amazon-aws/aws-5.png)



서버에서 나갔다가 다시 들어와야 하는데 번거로우니까 **env**를 실행한다.  

![aws-6](/assets/img/amazon-aws/aws-6.png)

![aws-7](/assets/img/amazon-aws/aws-7.png)

언어가 설정된 것을 확인할 수 있다. 



jdk 설치 

![aws-8](/assets/img/amazon-aws/aws-8.png)

최신버전을 찾아서 다운로드 주소를 복사해서 위와 같이 설치하면, tar.gz파일이 생긴다. 

![aws-9](/assets/img/amazon-aws/aws-9.png)

파일 압축을 풀어준다. 

![aws-10](/assets/img/amazon-aws/aws-10.png)

![aws-11](/assets/img/amazon-aws/aws-11.png)

.bash_profile에 경로 설정해준다. 

![aws-12](/assets/img/amazon-aws/aws-12.png)

![aws-13](/assets/img/amazon-aws/aws-13.png)

자바 잘 설치되었는지 버전확인 

![aws-14](/assets/img/amazon-aws/aws-14.png)

![aws-15](/assets/img/amazon-aws/aws-15.png)

git 설치

![aws-16](/assets/img/amazon-aws/aws-16.png)

![aws-17](/assets/img/amazon-aws/aws-17.png)

레포지토리를 클론한다. 

git clone https://github.com/kksj216/my-project 

cd my-project

chmod 775 mvnw 

./mvnw clean package 

![aws-18](/assets/img/amazon-aws/aws-18.png)



tomcat 설치 

![aws-19](/assets/img/amazon-aws/aws-19.png)

![aws-20](/assets/img/amazon-aws/aws-20.png)

![aws-21](/assets/img/amazon-aws/aws-21.png)



![aws-22](/assets/img/amazon-aws/aws-22.png)

./startup.sh 실행을 하고 접속하면 tomcat화면이 떠야하는데 안뜬다!!!ㅠㅠㅠㅠ 어디에서 문제인거지? (1) 방화벽 문제 (2) 톰켓이 제대로 다운로드 안된 문제? 



![aws-23](/assets/img/amazon-aws/aws-23.png)

심볼릭 링크 건거 말고 압축푼 파일에서 바로 ./startup.sh실행했더니 된다..





![aws-24](/assets/img/amazon-aws/aws-24.png)

![aws-25](/assets/img/amazon-aws/aws-25.png)

./mvnw clean package를 실행하면 war파일이 생긴다. 그 파일을 ~/apache-tomcat-8.5.59/webapps 에 ROOT로 만들어주기 

![aws-26](/assets/img/amazon-aws/aws-26.png)

![aws-27](/assets/img/amazon-aws/aws-27.png)

![aws-28](/assets/img/amazon-aws/aws-28.png)

![aws-29](/assets/img/amazon-aws/aws-29.png)

실행을 하면 

![aws-30](/assets/img/amazon-aws/aws-30.png)

에러가 뜬다... (여기까지가 서버로 올리는 과정임!)

past10브랜치로 한것임. 코드내에 문제가 있는거같다? mapping이 어딘가 잘못된것같은데 

마스터로 한번 해보자. (내기억에 마스터도 같은 에러가 났던 것 같음..)

1. 브랜치를 master로 
2. **./mvnw clean package** 로 war파일 생성 
3. ~/apache-tomcat-8.5.59/webapps에 있는 ROOT 지우고 (**rm -rf ROOT**) 
4. My-project/target에 있는 my-project-1.0을 ~/apache-tomcat-8.5.59/webapps 옮긴 후, (**mv my-project-1.0 ~/apache-tomcat-8.5.59/webapps**)
5. ~/apache-tomcat-8.5.59/webapps로 들어간 my-project-1.0을 ROOT로 바꿔준다. (**mv my-project-1.0/ ROOT**)



코드에 mapping에 문제가 있는 것 같다. 내가 뭘 바꾼거지? 12일 전에 form.html 변경한 기록이 있는데, 빈칸 하나 추가된 것 밖에 없다..

master도 같은 에러. 

past10에서 application.properties에 마지막 두 라인 주석처리하고 해보는데 -> 그래도 똑같은 에러다라아

