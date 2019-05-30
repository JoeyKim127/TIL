## Linux Shell 명령어

C:\User\0000 디렉터리

buffer overflow 외부에서 들어온 메모리가 내부 메모리보다 큰 경우
commend injection 외부 입력값이 내부프로그램 명령어 또는 명령 프로그램으로 사용될 경우,의도하지 않은 프로그램이 실행됨 --> 시스템의 악영향을 줄 수 있다
sql injestion 



#### 변수의 기본
- 변수를 사용하기 전에 미리 선언하지 않으며, 변수에 처음 값이 할당되면서 자동으로 변수가 생성
- 모든 변수는 "문자열(string)"으로 취급
- 변수 이름은 대소문자로 구분
- 변수를 대입할 때 -" 좌우에는 공백이 없어야 함



#### Shell

변수의 입력과 출력
- "$" 문자가 들어간 글자를 출력한다면, ''로 묶어주거나 "\(역슬래시)"를 붙임

- 변수를 ""로 묶어도 되고,, 묶지 않아도 된다

  


#### 숫자연산
- 변수에 대입된 값은 모두 문자열로 취급

- 수식은 백틱(')으로 묶어주어 한다

  

#### Parameter 변수

- 파라미터 변수는 $0,$1 $2의 형태를 가진다
- 전체 파라미터는 $*로 표현



#### 기본문 if
- 형식
 - if 조건
   then
     참일 경우 실행
    if

~~~ 
if ["woo" is ["woo "]
then
	echo "TRUE"
else
	echo "FALSE"
fi
exit0
~~~



#### 파일과 관련된 조건


case~seac

-if문은 참과 거짓의 두 경우만 사용가능
- 여러 가지 경우의 수가 있다면 case 문

and는 두개 다 참-
|-->or
정규식




#### for ~in문

- 반복뮨 --> 일정한 조건을 만족할 때 까지 변수 반복
- 실습해보기

~~~ 
#!/bin/bash
for i in  1 2 3 4 5 6 7 8 9

# for ((i=2 ; i<10 ; i ++ ))

do

for j in 1 2 3 4 5 6 7 8 9
do

```
echo "$i * $j = "`expr $i \* $j`  
```

done

echo ""
done

for i in 1 2 3 4 5 6 7 8 9 
do 

for j in 1 2 3 4 5 6 7 8 9
do

```
echo -n "$j * $i =" `expr $i \* $i `" "
```

done

echo ""
done

exit 0

#선생님 

# for (( j = 1 ; j < 10 ; j ++ ))

# do

```
# for (( i = 2 ; i < 10 ; i ++ ))
# do

	# printf " %s x %s = %s \t" $q $j `expr $i \* $j`
# done
# printf "\n"
```

# done

# exit 0
~~~



#### While

 - 조건이 true인 경우에 계속 반복

- 문제. quiz.sh 을 작성하시오.
  임의의 숫자를 생성 : rand
  사용자가 숫자를 입력해서 1)에서 생성한 숫자를 맞추는 게임
  만약, 사용자가 입력한 숫자가 1)에서 생성한 숫자와 다르면, 크다, 작다 메시지를 출력하고, 맞으면 정답 메시지를 출력하고 종료한다.
  맞추는 회수는 10회로 제한한다.
  10회를 초과하면 실패 메시지를 출력하고 종료한다.

~~~ 
#!/bin/bash
r=$(rand)

count=0
while [ $count -lt 10 ]
do
	echo 숫자를 입력하세요.
	read num

```
if [ $num -eq $r ]
then
	echo 정답입니다.
	exit 0
fi

if [ $num -lt $r ] 
then
	echo 더 큰 수를 입력하세요.
else 
	echo 더 작은 수를 입력하세요.
fi
count=`expr $count + 1`
```

done
echo 회수를 초과했습니다.
exit 1
~~~



#### export

- 외부 변수로 선언해 준다. 선언한 변수를 다른 프로그램에서도 사용할 수 있도록 해줌

  

#### printf
- 형식을 지정해서 출력

  

#### set 과 $

- 리눅스 명령어를 결과로 사용하기 위해서는 $ 형식을 잘 사용해야 한다
- 결과를 파리미터로 사용하고자 할 때는 set과 함께 사용

~~~ 
#!/bin/sh

echo "오늘 날짜는 $(date) 입니다."

set $(date)

echo "오늘은 $4 요일 입니다."

exit 0

~~~



#### shift

- 파라미터 변수를 왼쪽으로 한 단계씩 아래로 이동시킨다

  