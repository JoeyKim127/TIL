## JavaScript - day3

- For 조건문
- array





- Question 1

  : array에 입력된 크기만큼 * 출력

~~~ html
<body>
   <h1> Array Test</h1>
    <hr>

    <p id="line1"></p>
    <p id="line2"></p>
    <p id="line3"></p>
    <p id="line4"></p>

   <script>

       var num = [10,40,30,20];
       var line1 = num[0] + ": ";

       for(let i=0; i<=num[0]; i++) {
           //document.write("*")
           line1 += '*';
           // line1= line1 + '*'
       }
       line1 += "<br>";
       document.getElementById("line1").innerHTML = line1;

       
       var line2 = num[1] + ": ";
       for(let i=0; i<=num[1]; i++) {
           //document.write("*")
           line2 += '*';
       }
       line2 += "<br>";
       document.getElementById("line2").innerHTML = line2;


       var line3 = num[2] + ": ";
       for(let i=0; i<=num[2]; i++) {
           //document.write("*")
           line3 += '*';
       }
       line3 += "<br>";
       document.getElementById("line3").innerHTML = line3;


       var line4 = num[3] + ": ";
       for(let i=0; i<=num[3]; i++) {
           //document.write("*")
           line4 += '*';
       }
       line4 += "<br>";
       document.getElementById("line4").innerHTML = line4;
       </script>
~~~



- Question 2

  : 학생 점수 array를 이용해 표로 만들기

~~~ html
 <script>
     
var subjects = ["이름", "국어", "영어", "수학"];

    subjects.push("총점", "평균")

    var students = ["학생A", 50, 60, 70, "학생B", 58, 70, 95, "학생C",80, 100, 70];
    
   
    for(let i in subjects) {   
        document.write('<th>');
        document.write(subjects[i])  ;  
        document.write('</th>')   ; 
    }

    let Sum = 0;

    for(let j=0; j<3; j++) {

        document.write('<tr>'); 
        var student = students.slice(j*4,j*4+4);
        for (let k in student) {
            document.write('<td>');
            document.write(student[k]);
            document.write('</td>');
            if (k%4!=0) {
                Sum += student[k];
            }
        }
        document.write('<td>');
        document.write(Sum);
        document.write('</td>');
        document.write('<td>');
        document.write((Sum/3).toFixed(1));
        document.write('</td>');
        document.write('</tr>');
    };
    document.write('</table>')  

   </script>
~~~

