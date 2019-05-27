

Cookie의 원칙

- 중요정보 X

- 암호화해서 전달

- 유효기간 지속시간  최소화

- Secure 속성 활성화-  >Https 통신을 할 경우에만 서보로 쿠키를 전달 

-  Https Only 속성을 활성화 한다 --> 웹 브라우져에서 클라이언트로서의 쿠키 접근을  방지

  현재 브라우저에 전달된 쿠키 확인

  javascript:alert(document.cookie)





http://abc.com/data/

1. default page <-- Web Server에 설정에서 찾아본다
2. 1번이 없을 경우, directory testing 옵션이 활성화 시킨다
3.  2번이 없다면 404 Not Found로 표시

이런 기능이 있는 이유

- 





가상 머신 안에 vmtool 설치 이유

- 가상 머신 안에 copy&paste한거 밖에서도 할 수 있음



vi 

- 명령어 모드

  - i(현위치부터 입력) or a 편집모드
  -  esc 누르면 나오기

  - : 라인 변경 모드 
  - dd 줄 지우기
  - x 한글자 지우기
  - q 빠져나오기
  - :q! 저장하지 않고 나오기
  - :wq 저장하고 나오기



사용자@ 호스트 이름 : 경로 #

root@server-b : ~# 

- #:
- $:



Run Level

0 power off

1 rescure

2 multi- user

3 multi- user

4 multi- user

5 graphical

6 reboot



종료하는 방법(터미널에서)

power off, shutdown -p now , halt -p, init 0

시스템 재부팅

shutdown -r now, reboot, init 6

로그아웃

logout, exit



가상콘솔

쉽게 가상의 모니터라고 생각하면 된다. 우분투는 총 7개의 가상콘솔을 제공한다

이동하는 단축키는 ctrl +alt+



default setting

- ln -sf /lib/systemd/system/multi-user.target /lib/systemd/system/default.target



ls -a 숨김파일까지 보기

- .test.swp(숨김파일 형태)

  

ls -al

- 숨김파일을 포함한 모든 파일 보기



마운트(리눅스 server환경에서)

-  물리적인 장치를 특정한 위치에 연결시켜주는 과정

1. 메뉴에서 VM-settings-  usb controller 추가 3.0

2. 하단에 san disk usb storge connect

3. mount 

   ~~~ 
   /dev/sdg1 on /media/root/MYANJINI@GM type vfat (rw,nosuid,nodev,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,showexec,utf8,flush,errors=remount-ro,uhelper=udisks2)
   
   ~~~

    여기서 mount 된거 확인하기

4. 디렉토리 변경

   ~~~ 
   cd /media/root/MYANJINI\@GM/
   ~~~

5. ls 눌러서 usb안에 파일 뭐 있는지 확인

6. 시스템 내 파일 usb에 복사

   ~~~ 
   cp -rf /home/* ./
   ~~~

7. ls 눌러서 복자 제대로 되었는지 확인

8. cd /눌러 디렉토리에서 나가고

9. 언마운트 

   ~~~ 
    umount /dev/sdg1
   ~~~

   



우분투 서버에서 작업한 과정을 사이트에 등록하시오





리눅스 기본 명령어(1)

- ls

  - window의 dir과 같은 역할로, 해당 디렉토리에 이쓴 파일 목록 나열
  - ls /etc/systemd

- cd

  - 디렉토리 이동

  - cd ../etc/systemd

- pwd

  - 현재 디렉토리의 전체 경로를 출력

- rm

  - 파일이나 디렉토리 삭제

- cp

  - 파일이나 디렉토리 복사
  - 복사해도 원본 남아 있음

- touch

  - 크기가 0인 새 파일 생성, 이미 존재하는 경우 수정 시간을 변경

- mv

  - 파일과 디렉토리의 이름을 변경하거나 위치 이동 시 사용
  - 이동하면 원본 자제가 이동함

- mkdir

  - 새로우 ㄴ디렉토리 생성
  - mkdir usb.txt

- rmdir
  - 디렉토리 삭제
- cat
  - 텍스트로 작성된 파일을 화면에 출력
- head, tail
  - 텍스트로 작성된 파일의 앞 10핼 또는 마지막 10행만 출력
- more
  - 텍스트 형식으로 작성된 파일을 페이지 단위로 화면에 출력
- less
  - 
- file
  - 해당 파일이 어떤 종류인지 표시
- clear
  - 현재 사용 중인 터미널 화면을 깨끗하게 지워준다



*** 문제

다음 명령어의 실행 결과가 나머지와 다른 것은?

1. root@server:/bin# ls
2. root@server:/bin# ls .
3. root@server:/bin# ls ./
4. root@server:/bin# ls /
5. root@server:/bin# ls /bin
6. root@server:/bin# ls /bin/*
7. root@server:/bin# ls /bin/





사용자 홈 디렉토리로 이동

1. root@server:/bin/test# cd
2. root@server:/bin/test# cd ~
3. root@server:/bin/test# cd $HOME



root@server:/tmp# touch aaa

root@server:/tmp# touch bbb

root@server:/tmp# touch ccc

root@server:/tmp# mkdir ddd

root@server:/tmp# ls

aaa ⇐ 파일

bbb ⇐ 파일

ccc ⇐ 파일

ddd ⇐ 디렉터리

root@server:/tmp# mv aaa bbb ccc ddd

root@server:/tmp# ls

ddd ⇐ aaa bbb ccc 파일이 사라진 것을 확인

root@server:/tmp# ls ./ddd

aaa  bbb  ccc ⇐ ddd 디렉터리에 aaa bbb ccc 파일이 옮겨진 것을 확인

root@server:/tmp# date > aaa

root@server:/tmp# cat aaa

\2019. 05. 27. (월) 17:29:34 KST

root@server:/tmp# date > bbb

root@server:/tmp# cat bbb

\2019. 05. 27. (월) 17:29:49 KST

cat all 명령어의 실행 결과가 아래와 같이 나오도록 all 파일을 생성해 보세요.

root@server:/tmp# cat all

\2019. 05. 27. (월) 17:29:34 KST

\2019. 05. 27. (월) 17:29:49 KST

정답

root@server:/tmp# cat aaa bbb > all

root@server:/tmp# cat all

\2019. 05. 27. (월) 17:29:34 KST

\2019. 05. 27. (월) 17:29:49 KST

