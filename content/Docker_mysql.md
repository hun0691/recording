## 1. docker maria 이미지 다운로드 & 컨테이너 실행
```
docker run -d -p 33333:3306 -e MYSQL_ROOT_PASSWORD=root mariadb
```

## 2. docker container 정보 확인 

```
docker ps -a 
```

## 3. mariadb 접속 및 database 생성

```
docker exec -it 프로세스_ID bash 
```

```
mysql -u root 
create database test
```
