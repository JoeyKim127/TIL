## 190617 데이터베이스 서버 구축과 운영

### 도커안에 Telnet 서버 구축



Ubuntu Server 안에서 실행하기

- ubuntu 16.04  도커 실행

~~~ 
$ sudo docker run -it ubuntu:16.04
~~~

- 도커 안에서 필요한 파일 설치하기

~~~ 
root@f7cf7912c804:/# apt-get update  

# ifconfig 사용하기 위한 툴 설치
root@f7cf7912c804:/# apt-get install net-tools

# Telnet 설치 확인하기 --> 없다
root@f7cf7912c804:/# dpkg -l xinetd
dpkg-query: no packages found matching xinetd

# 그래서 Telnet 설치
root@f7cf7912c804:/# apt-get install -y xinetd telnetd

#디텍토리 변경 후 telnet 파일 생성
root@f7cf7912c804:/etc/xinetd.d# cd /etc/xinetd.d/
root@f7cf7912c804:/etc/xinetd.d# touch telnet

#컨테이너 안에서 vi 사용하기
root@f7cf7912c804:/etc/xinetd.d# apt-get install vim
root@f7cf7912c804:/etc/xinetd.d# vim telnet

# 작성하고 저장
service telnet
{
	disable = no
	flags = REUSE
	socket_type = stream
	wait = no
	user = root
	server = /usr/sbin/in.telnetd
	log_on_failure += USERID
}

# 그리고 재시작 
service xinetd restart 
또는
systemctl restart xinetd
~~~



- 사용자 추가

~~~ 
adduser teluser
pw teluser
~~~



- 원격 접속 확인

~~~ 
# ifconfig로 내 ip 확인
ifconfig

#ubuntu server에서 들어가고 teluser 계정으로 로그인
telnet (내 ip주소 입력)

# 파일 생성하기
touch test1234
~~~



- Telnet  서버 컨테이너 밖에서도 파일이 생성 되었는지 확인

~~~ 
# 디렉토리 변경
root@f7cf7912c804:~# cd /home/teluser/

# 확인하면 telnet 서버 안에서 만들었던 파일이 서버 밖에서 확인해도 파일 생성 확인 가능!
root@f7cf7912c804:/home/teluser# ls
test1234 
~~~



### OpenSSH 서버 구축하기

- telnet 서버에 openssh server와 같은 형식으로 만든다

~~~ 
# openSSH를 ubuntu 16.04 도커 컨테이너에 접속 후 openssh-server설치

sudo apt-get install -y openssh-server

# ssh 서버 재시작
service ssh restart

# ssh 서버 정상 작동 확인하기
ps -aux | grep ssh

# Ubuntu Server에서 Docker container을 통해 ssh 접속
ssh teluser@(ip address)
~~~



### 캐싱 전용 네임서버 구축





### MariaDB 실행하기



- Mariadb Ubuntu 16.04  도커 사용해서 실행하기 

  (이전에 실행한   ubuntu 16.04안에서 Mariadb를 다운받아 실행)

~~~ 
// docker ubuntu 실행

$ sudo docker run -it ubuntu:16.04

// repository 추가 

\# apt -y install software-properties-common dirmngr

\# apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 0xF1656F24C74CD1D8

\# add-apt-repository 'deb [arch=amd64] http://mirror.zol.co.zw/mariadb/repo/10.3/ubuntu xenial main'

\# apt update

// Mariadb server, client 설치

\# apt -y install mariadb-server mariadb-client
~~~



- Docker hub 를 통한 Mariadb 설치

  (mariadb라는 새로운 도터 컨테이너 실행)

~~~
$ sudo  docker run --name my-mariadb -e MYSQL_ROOT_PASSWORD=password -d mariadb:10-bionic
~~~



