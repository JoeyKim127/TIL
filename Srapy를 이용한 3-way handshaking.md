##### Srapy를 이용한 3-way handshaking



- IP 정보 받아와서 확인하기

  ~~~ 
  ip = IP()
  ip.display()
  ~~~

  

- 목적지 IP  주소를 KALI#1으로 변경 후 IP정보 확인

  ~~~
  ip.dst = "192.168.111.129"
  ip.display()
  ~~~



- TCP  정보 가져와서 확인

~~~ 
tcp = TCP()
tcp.display()
~~~



- 출발지 포트번호를 랜덤하게 생성 후 tcp 정보 확인

  ~~~ 
  tcp.sport = RandNum(1024,65535)
  tcp.display()
  ~~~

  

- syn 패킷 생성

~~~ 
syn = ip/tcp
~~~



- syn  패킷 전송 후 첫 응답이 올 때까지 대기

~~~ 
syn_ack = sr1(syn)
~~~



- syn_ack  패킷 확인

~~~ 
syn_ack.display()
~~~



- ack   패킷 생성

~~~ 
ack = ip/TCP(sport=syn_ack[TCP].dport, dport=80, flags="A", seq=syn_ack[TCP].ack, ack=syn_ack[TCP].seq+1)
~~~



-  ack패킷 전송

~~~ 
send(ack)
~~~



##### TCP SYNC FLOODING

- sync 패킷을 계속해서 전달
- 공격을 알아볼 수 있는 방법: syn는 계속 오지만  ackf를 다시 보내고 있지 않다
- 

