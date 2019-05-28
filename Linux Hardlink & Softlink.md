##### 링크

- 하드링크
  - 하드링크파일 하나면 생성되며 같은 inode를 사용
  - 명령 : # ln - 
- 심볼릭 링크
  - 새로운 inode2를 만들고 테이터는 원본 파일을 연결하는 효과
  - 명령 : # ln -s 링크 대상 파일이름 링크파일이름

~~~ 
#서버로 실행
root@server:/home# cd ~

root@server:~# mkdir linktest
root@server:~# cd linktest/

#linktest 내 내용 작성하기(insert)
root@server:~/linktest# vi basefile 

#내용 확인하기
root@server:~/linktest# cat basefile
원본 파일 입니다

root@server:~/linktest# ln basefile hardlink
root@server:~/linktest# ln -s basefile softlink

root@server:~/linktest# cat hardlink
원본 파일 입니다
root@server:~/linktest# cat softlink
원본 파일 입니다

root@server:~/linktest# ls -il
합계 8
656543 -rw-r--r-- 2 root root 24  5월 28 10:46 basefile
656543 -rw-r--r-- 2 root root 24  5월 28 10:46 hardlink
656542 lrwxrwxrwx 1 root root  8  5월 28 10:47 softlink -> basefile


# 상위 파일로 basefile 옮기기
root@server:~/linktest# mv basefile ../

root@server:~/linktest# ls -il
합계 4
656543 -rw-r--r-- 2 root root 24  5월 28 10:46 hardlink
656542 lrwxrwxrwx 1 root root  8  5월 28 10:47 softlink -> basefile
root@server:~/linktest# cat hardlink
원본 파일 입니다
root@server:~/linktest# cat softlink
cat: softlink: 그런 파일이나 디렉터리가 없습니다

(hardlink는 indoe에 연결되어 있기 때문에 파일이 이동해도 링크가 연결되어 있지만
softlink는 원본 파일이 이동하게 되면 링크가 끊어져 버리기 때문에 작동 안함)

#파일을 다시 원래 위치로 이동
root@server:~/linktest# mv ../basefile ./

root@server:~/linktest# ls  -il
합계 8
656543 -rw-r--r-- 2 root root 24  5월 28 10:46 basefile
656543 -rw-r--r-- 2 root root 24  5월 28 10:46 hardlink
656542 lrwxrwxrwx 1 root root  8  5월 28 10:47 softlink -> basefile

#다시 softlink가 작동한다!!

~~~

