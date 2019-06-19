## HTML Form practice

~~~ html
<!DOCTYPE HTML>
<html>

<head>
    <style>
        table,
        th,
        td {
            border: 1px solid black;
            padding: 1px;
        }

        table {
            border-spacing: 1px;
        }
    </style>
</head>

<body>

          

    <table style="width:800px">

        <tr>
            <th>이름</th>
            <td>
                <form>
                    <input type="text">
                </form>
            </td>
        </tr>

        <tr>
            <th>주민등록번호</th>
            <td>
                <form>
                    <input type="text"> -
                    <input type="text">
                </form>
            </td>
        </tr>

        <tr>
            <th>생년월일</th>
            <td>
                <form>
                    <input type="date" name="bday"></form>
            </td>
        </tr>

        <tr>
            <th>아이디</th>
            <td>
                <form> <input type="text"></form>
            </td>
        </tr>

        <tr>
            <th>비밀번호</th>
            <td>
                <form>
                    <input type="text">영문/숫자포함 8자 이상
                </form>
            </td>
        </tr>

        <tr>
            <th>비밀번호 확인</th>
            <td>
                <form><input type="text"></form>
            </td>
        </tr>

        <tr>
            <th>취미</th>
            <td>
                <form>
                    <select name="hobby">
                        <option value="선택하세요" selected>선택하세요</option>
                        <option value="음악감상">음악감상</option>
                        <option value="운동">운동</option>
                        <option value="독서">독서</option>
                        <option value="컴퓨터">컴퓨터</option>
                        <option value="요리">요리</option>
                        <option value="악기연주">악기연주</option>
                    </select>
                </form>
            </td>
        </tr>

        <tr>
            <th>이메일</th>
            <td>
                <input type="text"> @
                <input type="text">

                <select name="email">
                    <option value="직접입력" selected>직접입력</option>
                    <option value="naver.com">naver.com</option>
                    <option value="daum.com">daum.com</option>
                    <option value="nate.com">nate.com</option>
                    <option value="gmail.com">gmail.com</option>
                </select>
            </td>
        </tr>

        <th>주소</th>
        <td>
            <input type="text">
            <button type="button">주소찾기</button><br>
            <input type="text" value=" 상세입력">


        </td>
        </tr>

        <tr>
            <th>전화번호</th>
            <td>
                <form><input type="text"></form>
            </td>
        </tr>

        <tr>
            <th>핸드폰 번호</th>
            <td>
                <form><input type="text"></form>
            </td>
        </tr>

        <tr>
            <th>직업</th>
            <td>
                <select name="occupation">
                    <option value="선택하세요" selected>선택하세요</option>
                    <option value="학생">학생</option>
                    <option value="엔지니어">엔지니어</option>
                    <option value="판사">판사</option>
                    <option value="선생님">소방관</option>
                    <option value="가수">가수</option>
                    <option value="선생님">선생님</option>
                </select>
            </td>
        </tr>

        <th>메일/sns 정보 수신</th>
        <td>
            <form>
                <input type="checkbox" name="수신" value="수신">수신
                <input type="checkbox" name="수신거부" value="수신거부">수신거부
            </form>
        </td>
        </tr>

        <tr>
            <th>회원종류</th>
            <td>
                <form>
                    <input type="checkbox" name="일반회원" value="일반회원">일반회원
                    <input type="checkbox" name="기업회원" value="기업회원">기업회원
                    <input type="checkbox" name="기관회원" value="기관회원">기관회원
                    <input type="checkbox" name="관리자" value="관리자">관리자
                </form>
            </td>
        </tr>

        <tr>
            <th>정보공개여부</th>
            <td>
                <select name="privacy">
                    <option value="선택하세요" selected>선택하세요</option>
                    <option value="공개">공개</option>
                    <option value="비공개">비공개</option>
                </select>
            </td>
        </tr>

        <tr>
            <td colspan="2" style="text-align:center;">
                <input type="button" onclick="alert('가입축하드립니다!')" value="회원가입">
                <input type="button" onclick="alert('회원가입 취소')" value="취소">
            </td>
        </tr>

    </table>

</body>

</html>
~~~



