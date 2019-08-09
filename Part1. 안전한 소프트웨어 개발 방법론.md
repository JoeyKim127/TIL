190809 개발보안 day2



## Part1. 안전한 소프트웨어 개발 방법론

### ch1 시큐어코딩의 개요



#### SANS TOP25 Most Dangerous Software Errors

1. #### 구성요소간 안전하지 않은 상호작용 6개



22위 Open Redirect =  신뢰되지 않은  url 주소로 자동 접속 연결

외부 입력값을 제한 없이 redirect 주소로 사용하는 경우 발생

Redirect: 원래 온 요청을 다른 요청으로 대체하는 것

- 문제점
  - 의도하지 않은  외부 사이트로  redirection아 발생할 수 있음
  - 피싱과 같은 공격에 이용이 된다

~~~ 
mypage.jsp
---------------------------------------------
String url = request.getParameter("url");
response.sendRedirect(url);
---------------------------------------------

요청: mypage.jsp?url=main.jsp  ==> main.jsp로 이동이 된다
응답: main.jsp
~~~



2. #### 위험한 자원관리 8개

경로추적

- 외부입력값을 경로 조작 문자열 포함 여부를 확인하지 않고 내부 파일 참조에 사용하는 경우 발생
  - 권한 밖의 파일에 접근이 가능
  - 지정된 경로 밖의 파일에 접근이 가능

~~~ 
download.jsp
-------------------------------------------------------
String fname = request.getParameter("file_name");
File f = new File("/upload/data/2019/08" + fname);
-------------------------------------------------------

정상요청: download.jsp?file_name=abc.gif => 
~~~



18위: 잠재적으로 위험한 함수 사용하는 것 - banned function



23위 형식 문자열(Format String)을 통제하지 않는 것

- 형식 문자열: 데이터의 출력 형식을 지원





3. #### 방어 미비(11개)

5위 CWE-306  핵심 기능에 대해 인증을 누락



8위 정보에 대한 직접적인 유출을 방지하기 위해

암호화

- 안전한 알고리즘 
- 키 길이 사용
- 키 관리





### 시큐어 코딩

- 정해준 롤에 따라 코드를 작성하면 특정 취약점을 제거할 수 있는 코딩 기법
- 특정 취약점이 발생하지 않도록 코드를 작성하는 규칙의 모음

~~~ 

String input = request.getParameter("age");
if (input.equals("32")) 
request.getParameter(param_name)

요청 파라미터 목록에서 param_name에 해당하는 파라미터의 값을 문자열로 반환하는 메소드
단, 요청 파라미터 목록에 해당 파라미터가 존재하지 않으면  NULL을 반환한다

~~~



