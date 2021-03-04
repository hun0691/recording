

# 1. 개요 

* Spring boot로 생성한 jar 파일을 클라우드 환경에 배포한다. (ZCP) 

>  사용 tool , frameWork 
```
1. spring boot
2. maven
3. docker 
4. kubernetes
5. kustomize 
```

* 대략적인 과정
```
1. Application 작성 및 jar 파일생성 
2. DockerFile 작성 , Docker 빌드(이미지 생성)
3. Docker images register
4. docker 이미지 클라우드 배포. 
```





## 1. Application 작성 및 jar 파일생성 

` 선행작업 : local 내 mysql 설치 (작성한 소스에 DB 접속하는 내용이 있어서..)` 


사전 spring boot 를 통해 실행가능한 jar 파일 형태의 코드들을 작성해줬다. 

단순히 로컬 PC에 설치된 DB에 접속후 데이터를 읽어오는 내용

```
cd C:\Users\Administrator\Desktop\factory\workspace\PIUH 
mvnw install 
```
>결과물 : C:\Users\Administrator\Desktop\factory\workspace\PIUH\target\PIUH-0.0.1-SNAPSHOT.jar

## 2. DockerFile 작성 및 

`선행작업 local 내 docker 설치되어야 함`


 빌드할 위치에 아래와 같은 Dockerfile 작성

 ### 2.1 Docker 파일
```
FROM openjdk:11-jdk-slim
VOLUME /tmp
ADD target/PIUH-0.0.1-SNAPSHOT.jar app.jar
ENV JAVA_OPTS=""
ENTRYPOINT exec java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar
```

 ### 2.2 Docker 파일 빌드
  

* 명령어 
```
docker build 빌드위치 -t 이미지명

#빌드위치에 Dockerfile이 필수로 있어야함
```

* 샘플코드
```
docker build . -t asf-registry.cloudzcp.io/piuh-pilot/jhson:0.0.1

# . dockerFile 이 위치하는 현재 디렉토리 
# C:\Users\Administrator\Desktop\factory\workspace\PIUH 
```

* 이미지 생성 확인
```
docker images

# REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
# asf-registry.cloudzcp.io/piuh-pilot/jhson   0.0.2               7e44254499d6        2 minutes ago       467MB
```

* 옵션 및 설명
```
-t 옵션 
 
 1.  -t 이미지명을 정하기 위해 사용
 2.  해당 작업에서 생성한 이미지를 원격저장소에 등록하려고 하기에 원격 이미지명과 동일하게 적용 필요 
 3. 도메인/레파지토리명/이미지명:버전(태그)  
     도메인 - asf-registry.cloudzcp.io
     레파지토리명 - piuh-pilot
     이미지명 : jhson
     버전(태그) : 0.0.1  
```


  ## 3. Docker images register 

 ### 3.1 이미지 저장소 로그인
  * 이미 로그인 된 상태라면 3.2 다음 단계로 넘어가도 된다.

  2번 작업으로 생성된 이미지를 repository에 등록하기 위해 harvor 로그인을 한다.
    
> harbor   - 소스처럼 이미지도 형상관리가 가능하다. dockerHub 는 public 환경이기에 private 환경을 제공하는 harbor를 사용


```
docker login 도메인주소

#샘플코드
docker login asf-registry.cloudzcp.io -u 계정 

# password 입력 (harbor 로그인 비밀번호가 아닌, CLI 전용 비밀번호 입력) 
# https://asf-registry.cloudzcp.io/harbor/projects  > 오른쪽 상단 프로파일 클릭 > User Profile 클릭 > CLI Secret 복사 & 붙여넣기

```

 ### 3.2 원격 저장소로 이미지 등록

```
docker push 이미지명(로컬에 저장된 이미지명)
docker push asf-registry.cloudzcp.io/piuh-pilot/jhson:0.0.2
```

* 로컬에 없는 이미지명을 push 할 경우 에러발생
```
PS C:\Users\Administrator\Desktop\factory\workspace\PIUH> docker images;
REPOSITORY                                  TAG                 IMAGE ID            CREATED             SIZE
asf-registry.cloudzcp.io/piuh-pilot/jhson   0.0.2               7e44254499d6        43 minutes ago      467MB
mariadb                                     latest              70e69b4a7bda        5 days ago          401MB
PS C:\Users\Administrator\Desktop\factory\workspace\PIUH> docker push asf-registry.cloudzcp.io/piuh-pilot/jhson:0.0.1
The push refers to repository [asf-registry.cloudzcp.io/piuh-pilot/jhson]
tag does not exist: asf-registry.cloudzcp.io/piuh-pilot/jhson:0.0.1
PS C:\Users\Administrator\Desktop\factory\workspace\PIUH> docker push asf-registry.cloudzcp.io/piuh-pilot/jhson:0.0.2
The push refers to repository [asf-registry.cloudzcp.io/piuh-pilot/jhson]
ad53451e1948: Pushed                                                                                                    ca2242fd4d13: Layer already exists                                                                                      513adf10febc: Layer already exists                                                                                      08664b16f94c: Layer already exists                                                                                      9eb82f04c782: Layer already exists                                                                                      0.0.2: digest: sha256:5d3592b9c2267d3eb82f73721a5895e3f89391f060f0d59ceba6ad1666d5945a size: 1372
```



## 4. docker 이미지 클라우드 배포. 

 ### 4.1 클라우드 로그인

   `사전작업 KUBECONFIG 환경변수 설정필요`
  > ZCP 로그인 -> 오른쪽상단 CLI Command 클릭 > kube.conf 정보 로컬 다운로드

### 4.2 클라우드에 kube 배포
 
  - 다양한 이미지가 존재하는 클라우드 환경이기에 kustomize 라는 프레임워크를 통해 배포한다.
  - kustomize 에 셋팅이 필요하나 아직 이해도가 부족하여 샘플용으로 설정해주신 프로젝트를 다운받았다.. 
   ```
   # 1. 설정파일 다운
   git clone https://asf-git.cloudzcp.io/piuh-pilot/piuh-configuration.git

   # 2. 윈도우용 kustomize binary 파일 다운로드(kustomize.exe)
   ```


  ## 5. etc 

 2.2 Docker 파일 빌드 결과로 생성된 이미지를 컨테이너로 띄웠을때 에러가 발생함
  

  why 

   컨테이너 실행시 app.jar 를 실행하게 했고, 작성한 app 내용중 DB 연결할때 localhost 로 연결하도록 되어있음.
  
  what 
   
  
   컨테이너 실행 시점에 localhost는 내 pc가 아닌 컨테이너 자체
 
  how 

   1. DB 접속시 localhost가 아닌 퍼블릭 환경을 이용한다. (ZDB 등)

   2. localhost를 이용한다. 

     2.1 컨테이너 내부에 localhost DB도 같이 생성한다.
     2.2 컨테이너가 localhost를 내 PC로 인식할 수 있게 해준다.



