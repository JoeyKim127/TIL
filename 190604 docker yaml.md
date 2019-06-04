## Docker 190604

- docker build-- dockerfile을 이용해서  docker image 를 만든다

--> 명령어 - t 이릉 부여



- --name: container에 이름 부여(하지만 안해도 랜덤으로 이름 부여)



~~~ 
특정 이름의 컨테이너를 조회
# docker container ls -a --filter="name=ooo"

특정 이름의 컨테이너를 삭제
# docker container rm -f $(docker container ls -aq --filter="name=ooo")

특정 이름의 컨테이너를 중지하고 해당 이름의 컨테이너를 실행
# docker container rm -f $(docker container ls -aq --filter="name=ooo") ; docker container run --name ooo IMAGE_NAME
~~~



-p hostport : container port 호스트의 포트를 해당하는 컨테이너로 매핑

-v 호스트의 특정 디렉토리를 container path로 연결



~~~ 
root@server:~/docker# curl http://localhost:9090 --> 파일 내용 확인
Hello Docker ...!!!root@server:~/docker# curl http://localhost:9090


root@server:~/docker# docker container cp 904:/echo/main.go ./main2.go

root@server:~/docker# ls
Dockerfile  Dockerfile.go  index.html  main.go  main2.go  mainpract.go

root@server:~/docker# gedit main2.go ---> 파일 수정하기

root@server:~/docker# docker container cp ./main2.go 904:/echo/main.go --> 호스트의 ./main2.go파일울 /echo/main.go 파일로 복사

root@server:~/docker# curl http://localhost:9090 ---> 내용 미반영 그래서 stop and restart
Hello Docker ...!!!root@server:~/docker# 

root@server:~/docker# docker container stop 904
904

root@server:~/docker# docker container start 904
904

root@server:~/docker# curl http://localhost:9090
안녕 도커...!!!root@securl http://localhost:909

~~~



### 도커 YMAL

-  YAML 설치하기 

~~~ 
 140 curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
  141  chmod +x /usr/local/bin/docker-compose
  142  docker-compose --version
~~~



- change directory

~~~ 
  143  pwd
  144  cd ~
  145  cd docker
  
  # make docker yaml 
  146 gedit docker-compose.yaml
  
  version: "3"
services: 
    echo:
       build: .
       ports: 
        - 9090:8080
        
 162  docker-compose up 
 
 # if Error occurs saying
 failed: port is already allocated

  168  docker container ps 
  169  docker container rm -f 2e3  --> delete the port that is being used
~~~



- upload more than 1 echo

~~~ 
 172 gedit docker-compose.yaml

 version: "3"
services: 
    echo:
       build: .
       ports: 
        - 8080 --> when many ports need to be set, do no define ports
    echo2:
       build: .
       ports:
        - 9091:8080
~~~



- upload 10 echos

~~~ 
 172* docker-compose up --scale echo=10 
  
  # stop ctrl+C
  # remove echo
  183  docker-compose down
  184  docker-compose up -d
  185  docker-compose down -d
~~~

