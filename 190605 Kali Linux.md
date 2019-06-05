



​            계층                주요정보             데이터 전송 단위           주요 프로토골

=============    ==========      =================      =============

응용 = 프로세스          메세지                                                         약 65000개

전송                             포트번호          데이터그램/세그먼트           UDP/TCP

네트워크 = 인터넷       ip 주소                        패킷                           IP, ICMP

데이터링크                  mac  주소                  프레임                    Ethernet, PPP

물리 



물리 계층 +  데이터링크 계층 = 네트워크 인터페이스/접근



TCP의 3 handshaking: 연결을 수립하는 과정

TCP의4 handshaking: 종료를 수립하는 과정



Tear drop 공격

: IP 헤더의 프래그먼트 오프셋을 조작하여 수신측에서 분할된 패킷을 재조립할 수 없도록 하는 공격 기법



실기 시험:

도커 이미지를 다운 받아서 내 도커 허브에 올리면 그 홈페이지가 뜨는거



리눅스: shell 만들어서 크롬에 등록하기





## KALI

#### 포트 스캐닝 방법



- TCP Open Scan: tcp 연결과정(3 way handshacking)을 통해서 해당 포트의 실행/사용 여부 확인

  - 해당 포트가 유효한 경우 :  SYN --> SYN/ACK --> ACK ==> 연결/세션 수립되면서 로그 기록이 남아서 나중에 추적이 가능하기 떄문에 공격자에게 불리함

  - 해당 포트 무효한 경우 :  SYN --> RST/ACK



- Stealth Scan: 기록을 남기기 않는 포트 스캐닝 방법
  - TCP Half Open Scan(=TCP SYN Open Scan): 해당 포트가 유효한 경우 : SYN --> SYNC/ACK --> (RST) ==> 연결이 수립되니 않기 때문에 로그가 남지 않는다-
  - 해당 포트가 무효하면 : SYN --> RST/ACK



- FIN Scan : Fin을 줘서 반응을 살피는 방법

  - 해당 포트가 유효한 경우 : FIN --> 무응답
  - 해당 포트가 무효한 경우 : SYN --> RST/ACK

  

- XMAS Scan

  - 해당 포트가 유효한 경우 : FIN + PSH + URG --> 무응답
  - 해당 포트가 무효한 경우 : FIN + PSH + URG --> RST/ACK

  

- NULL Scan

  - 해당 포트가 유효한 경우 : NULL--> 무응답
  - 해당 포트가 무효한 경우 : NULL --> RST/ACK

  

#### nmap(network map)

- 네트워크에 연결되어 있는 호스트의 정보를 파악하는 도구
- nmap을 이용해서 네트워크에 연결되어 있는 호스트의 ip, os, service 등을 확인할 수 있다. 

- nmap --help

  SCAN TECHNIQUES:

    -sS/sT/sA/sW/sM: TCP SYN/Connect()/ACK/Window/Maimon scans

    -sU: UDP Scan

    -sN/sF/sX: TCP Null, FIN, and Xmas scans

    --scanflags <flags>: Customize TCP scan flags

    -sI <zombie host[:probeport]>: Idle scan

    -sY/sZ: SCTP INIT/COOKIE-ECHO scans

    -sO: IP protocol scan

    -b <FTP relay host>: FTP bounce s

  

#### 실습

- TCP Open Scan

  ~~~ 
  root@kali:~# nmap -sT 192.168.111.129 -p 80
  root@kali:~# nmap -sT 192.168.111.129 -p 8080
  ~~~

- TCP Half Open Scan

  ~~~ 
  root@kali:~# nmap -sS 192.168.111.129 -p 80
  root@kali:~# nmap -sS 192.168.111.129 -p 8080
  ~~~

- Fin Scan

  ~~~ 
  root@kali:~# nmap -sF 192.168.111.129 -p 80
  root@kali:~# nmap -sF 192.168.111.129 -p 8080
  ~~~

- XMAS Scan

  ~~~ 
  root@kali:~# nmap -sX 192.168.111.129 -p 80
  root@kali:~# nmap -sX 192.168.111.129 -p 8080
  ~~~

- Null Scan

  ~~~ 
  root@kali:~# nmap -sN 192.168.111.129 -p 80
  root@kali:~# nmap -sN 192.168.111.129 -p 8080
  ~~~



Kali #1           192.168.111.129

Kali #2           192.168.111.130

Window        192.168.111.131



#### ARP(Address Resolution protocol)

ARP spoofing 방어

arp cache table에 gateway mac 주소를 정적으로 설정



Windows

1. arp -s GATEWAY_IP GATEWAY_MAC

2. netst interface ip delete neighbors "NETWORK_CARD_NAME" "GATEWAY_IP"

3. netst interface ip add neighbors "NETWORK_CARD_NAME" "GATEWAY_IP"



Kali #1           192.168.111.129

Kali #2           192.168.111.130

Window        192.168.111.131



@Kali2 

\# arpspoof -i eth0 -t VICTIM_IP(WINXP) GATEWAY_IP

~~~ 
# arpspoof -i eth0 -t 192.168.111.131 192.168.111.2
~~~

---> Window XP cmd

~~~ 
C:\Documents and Settings\Administrator>arp -a

Interface: 192.168.111.131 --- 0x2
  Internet Address      Physical Address      Type
  192.168.111.2         00-50-56-34-96-a1     dynamic
  192.168.111.130       00-50-56-34-96-a1     dynamic

~~~

인터넷이 안되고 두개의 ip가 뜬다



--> Kali2에서 

~~~ 
~# fragrouter -B1
~~~

ip도 안뜨고 다시 인터넷이 된다





#### MTM (Man in The Middle)

- 두 호스트 간에 통신을 하고 있을 때, 중간자 사이에 끼어서 통신 내용을 도청, 조작하는 공격



##### DNS Spoofing

1. Kali #2에서 ettercap 실행

~~~ 
root@kali:~# gedit /etc/ettercap/etter.dns
root@kali:~# ettercap -G
~~~



2. Sniff > Unified sniffing > eth 0 ⇐ 스니핑할 NIC를 지정

   Hosts > Scan for hosts ⇐ 해당 LAN에 존재하는 호스트를 검색

​       Hosts > Hosts list ⇐ 검색 결과를 확인



3. 공격 대상을 지정

   target1 => Gateway (192.168.111.2)

   target2 => WinXP (192.168.111.140)

   Apr spoofing ⇒ 공격자를 공격 대상 사이에 위치 ⇒ WinXP <---> Kali#2 <---> Gateway

   Mitm > ARP Spoofing > Sniff remote connections 



4. DNS Spoofing 공격

   Plugins > Manage the plugins > dns_spoof 

5. 잘 실행되었는지 확인!

    Kali#2에서 service apache2 start

   ​	firefox로 www.naver.com

   WinXP에서 http://www.naver.com으로 접속을 시도 

   Kali#2에서 제공하는 웹 페이지가 보이면 공격



#### Scapy

- 파이썬으로 작성된 패킷 조작 도구
- 패킷 디코딩, 전송, 캡처, 수정 등 다양한 기능을 제공



-  Kali#2에서 실행

~~~ 
root@kali:~# scapy
~~~



- 지원하는 프로토골 확인

  ~~~ 
  root@kali:~# ls()
  AH         : AH
  ARP        : ARP
    :
  
  ~~~



- TCP 헤더 정보를 출력

  ~~~ 
  root@kali:~# ls(TCP)
  sport      : ShortEnumField            = (20)
  dport      : ShortEnumField            = (80)
  seq        : IntField                  = (0)
  ack        : IntField                  = (0)
  dataofs    : BitField (4 bits)         = (None)
  reserved   : BitField (4 bits)         = (0)
  flags      : FlagsField (8 bits)       = (2)
  window     : ShortField                = (8192)
  chksum     : XShortField               = (None)
  urgptr     : ShortField                = (0)
  options    : TCPOptionsField           = ({}
  
  ~~~

  

- 현재 설정되어 있는 TCP  정보 출력

~~~~ 
root@kali:~# TCP() .display()
###[ TCP ]###
  sport= ftp_data
  dport= http
  seq= 0
  ack= 0
  dataofs= None
  reserved= 0
  flags= S
  window= 8192
  chksum= None
  urgptr= 0
  options= {}

~~~~



- 사용 가능한 기능을 확인

  ~~~ 
  root@kali:~# sc() 
  
  arpcachepoison: Poison target's cache with (your MAC,victim's IP) couple
  
    arping     : Send ARP who-has requests to determine which hosts are up
  
    bind_layers         : Bind 2 layers on some specific fields' values
  
    bridge_and_sniff    : Forward traffic between two interfaces and sniff packets exchanged
  
    corrupt_bits        : Flip a given percentage or number of bits from a string
  ~~~