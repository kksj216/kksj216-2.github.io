







![image-20201026010823924](/Users/sujin/Library/Application Support/typora-user-images/image-20201026010823924.png)

![image-20201026010855248](/Users/sujin/Library/Application Support/typora-user-images/image-20201026010855248.png)

handongpwd.pem 이 저장되어 있는 /Users/sujin/Desktop/2020-2 에서, **ssh -i "handongpwd.pem" ubuntu@ec2-54-167-240-74.compute-1.amazonaws.com** 로 접속한다. 

첫번째 캡쳐와 같이 unprotected private key file 이라고 뜨는 경우에는 chmod 400으로 권한을 바꿔주면 된다. 

![image-20201026011014575](/Users/sujin/Library/Application Support/typora-user-images/image-20201026011014575.png)



접속했으면 

![image-20201026011111025](/Users/sujin/Library/Application Support/typora-user-images/image-20201026011111025.png)

![image-20201026011212307](/Users/sujin/Library/Application Support/typora-user-images/image-20201026011212307.png)



서버에서 나갔다가 다시 들어와야 하는데 번거로우니까 **env**를 실행한다.  

![image-20201026011831530](/Users/sujin/Library/Application Support/typora-user-images/image-20201026011831530.png)

![image-20201026011914159](/Users/sujin/git/kksj216.github.io/_posts/image-20201026011914159.png)

언어가 설정된 것을 확인할 수 있다. 



jdk 설치 

![image-20201026012117851](/Users/sujin/Library/Application Support/typora-user-images/image-20201026012117851.png)

최신버전을 찾아서 다운로드 주소를 복사해서 위와 같이 설치하면, tar.gz파일이 생긴다. 

![image-20201026012230426](/Users/sujin/Library/Application Support/typora-user-images/image-20201026012230426.png)

파일 압축을 풀어준다. 

![image-20201026012501620](/Users/sujin/Library/Application Support/typora-user-images/image-20201026012501620.png)

![image-20201026013536913](/Users/sujin/Library/Application Support/typora-user-images/image-20201026013536913.png)

.bash_profile에 경로 설정해준다. 

![image-20201026014143713](/Users/sujin/Library/Application Support/typora-user-images/image-20201026014143713.png)

![image-20201026014210094](/Users/sujin/Library/Application Support/typora-user-images/image-20201026014210094.png)

자바 잘 설치되었는지 버전확인 

![image-20201026014521282](/Users/sujin/Library/Application Support/typora-user-images/image-20201026014521282.png)

![image-20201026015353636](/Users/sujin/Library/Application Support/typora-user-images/image-20201026015353636.png)

git 설치

![image-20201026015420984](/Users/sujin/Library/Application Support/typora-user-images/image-20201026015420984.png)

![image-20201026015438303](/Users/sujin/Library/Application Support/typora-user-images/image-20201026015438303.png)

레포지토리를 클론한다. 

git clone https://github.com/kksj216/my-project 

cd my-project

chmod 775 mvnw 

./mvnw clean package 

![image-20201026020933942](/Users/sujin/Library/Application Support/typora-user-images/image-20201026020933942.png)



tomcat 설치 

![image-20201026022447028](/Users/sujin/Library/Application Support/typora-user-images/image-20201026022447028.png)

![image-20201026022556301](/Users/sujin/Library/Application Support/typora-user-images/image-20201026022556301.png)

![image-20201026022658926](/Users/sujin/Library/Application Support/typora-user-images/image-20201026022658926.png)



![image-20201026022812932](/Users/sujin/Library/Application Support/typora-user-images/image-20201026022812932.png)

./startup.sh 실행을 하고 접속하면 tomcat화면이 떠야하는데 안뜬다!!!ㅜㅠㅠㅠㅠ 어디에서 문제인거지? (1) 방화벽 문제 (2) 톰켓이 제대로 다운로드 안된 문제? 



![image-20201026193756508](/Users/sujin/Library/Application Support/typora-user-images/image-20201026193756508.png)

심볼릭 링크 건거 말고 압축푼 파일에서 바로 ./startup.sh실행했더니 된다..





![image-20201026194239425](/Users/sujin/Library/Application Support/typora-user-images/image-20201026194239425.png)

![image-20201026194912383](/Users/sujin/Library/Application Support/typora-user-images/image-20201026194912383.png)

./mvnw clean package를 실행하면 war파일이 생긴다. 그 파일을 ~/apache-tomcat-8.5.59/webapps 에 ROOT로 만들어주기 

![image-20201026202723145](/Users/sujin/Library/Application Support/typora-user-images/image-20201026202723145.png)

![image-20201026195032364](/Users/sujin/Library/Application Support/typora-user-images/image-20201026195032364.png)

![image-20201026195113717](/Users/sujin/Library/Application Support/typora-user-images/image-20201026195113717.png)

![image-20201026201603039](/Users/sujin/Library/Application Support/typora-user-images/image-20201026201603039.png)

실행을 하면 

![image-20201026201620150](/Users/sujin/Library/Application Support/typora-user-images/image-20201026201620150.png)

에러가 뜬다... 

past10브랜치로 한거다. 코드내에 문제가 있는거같다? mapping이 어딘가 잘못된것같은데 

마스터로 한번 해보자. 근데 내기억에 마스터도 같은 에러가 났던 것 같은데 .. 

1. 브랜치를 master로 
2. **./mvnw clean package** 로 war파일 생성 
3. ~/apache-tomcat-8.5.59/webapps에 있는 ROOT 지우고 (**rm -rf ROOT**) 
4. My-project/target에 있는 my-project-1.0을 ~/apache-tomcat-8.5.59/webapps 옮긴 후, (**mv my-project-1.0 ~/apache-tomcat-8.5.59/webapps**)
5. ~/apache-tomcat-8.5.59/webapps로 들어간 my-project-1.0을 ROOT로 바꿔준다. (**mv my-project-1.0/ ROOT**)



코드에 mapping에 문제가 있는 것 같다. 내가 뭘 바꾼거지? 12일 전에 form.html 변경한 기록이 있는데, 빈칸 하나 추가된 것 밖에 없다..

master도 같은 에러. 

past10에서 application.properties에 마지막 두 라인 주석처리하고 해보는데 -> 그래도 똑같은 에러다라아

