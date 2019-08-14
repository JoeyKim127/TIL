#### Java운영체제 명령어 삽입 (Command Injection)

어플리케이션에서 운영제체 명령어 실행 부분이 존재하는 경우,

외부 입력값을 검증, 제한하지 않고, 운영체제 명령어 또는 명령어의 일부로 사용하는 경우 발생

Runtime.getRuntime().exec(______); ← ______ 명령어를 해당 시스템의 쉘에서 실행

외부 입력값을 검증, 제한 없이 운영체제 명령어로 사용하는 경우 

⇒ 공격자가 파라미터를 조작, 변경해서 계획되지 않은(의도하지 않은) 명령어가 실행

⇒ 해당 시스템의 제어권을 탈취

~~~ java

String pcmd = request.getParameter("cmd");

Runtime.getRuntime().exec(pcmd);

정상요청 : ../doSomething.jsp?cmd=dir 

비정상요청 : ../doSomething.jsp?cmd=ipconfig 

~~~



외부 입력값을 검증, 제한 없이 운영체제 명령어의 일부(=파라미터)로 사용하는 경우

~~~ java

String fname = request.getParameter("file_name");
Runtime.getRuntime().exec("type c:\data\ " + fname);
<-- c:/data/ 아래 있는 특정 파일의 내용 출력

개발자가 의도했던 정상 요청 : ../doSomething.jsp?file_name=abc.txt
공격자가 조작한 비성장 요청 : ../doSomething.jsp?file_name=abc.txt & ipconfig

~~~







~~~ java
@RequestMapping(value = "/test/xpath_test.do", method = RequestMethod.POST)
	@ResponseBody
	public String testXpathInjection(HttpServletRequest request) {
		StringBuffer buffer = new StringBuffer();
		String name = request.getParameter("name");
		buffer.append("실행결과: ");
		TestUtil util = new TestUtil();
		buffer.append(util.readXML(name));
		return buffer.toString();
	}

	@RequestMapping(value = "/test/command_test.do", method = RequestMethod.POST)
	@ResponseBody
	public String testCommandInjection(HttpServletRequest request, HttpSession session) {
		StringBuffer buffer = new StringBuffer();
		
		
		// 진단결과
		//외부에서 전달된 data 파라미터 값을 검증, 저헨하지 않고,
		// 운영체게 명령어 실행에 사용하고 있다
		// --> 운영체제 명령어 삽입 취약접을 가지고 있다
		// 대응방법:
		// 1. 사용 가능한 명령어를 미리 정의하고
		// 2. 정의된 범위 내개서 명령어가 실행될 수 있도록 한다
		// ** 내부 처리에 사용되는 명령어가 외부에서 직접 전달되지 않도록 한다
		// ** 외부에서 전달 된 닶이 내부  처리에 직접 사용되지 않도록 한다.
        // ** 내부에서는 코드에 해당하는 명령어 대체해서 사용한다(내부에서 사용하는 코드는 외부에 노출되면 안된다) 
        
        // ==> 허용 목록 기반의 입력값 제한과 내부 처리를 감추는 캡슐화를 동시에 감출 수 있다
        
        //코드 수정
        //1. 사용 가능한 명령어를 정의 
        String[] allowedCommands = {"type", "dir"};
        //2. 처리에 사용되는 명령어가 전달
        // AS-IS: 처리에 사용되는 명령어가 전달
        //TO-BE: 화면에서는 코드가 전달되고, 처리에서는 명령어로 대체해서 처리
        String data = request.getParameter("data");
        
        try {
        data = allowedCommands[Inter,parseInt(data)];
        } catch (exception = ) {
            return_"잘못된 접근입니다";
        }
        
        
        
        
		String data = request.getParameter("data");
		if (data != null && data.equals("type")) {
			data = data + " " + request.getSession().getServletContext().getRealPath("/") + "files\\file1.txt";
		}

		Process process;
		String osName = System.getProperty("os.name");
		String[] cmd;
        
~~~

