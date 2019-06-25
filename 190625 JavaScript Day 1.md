## JavaScript Day 1

- input
- function
- if statement
- event



- event 실습

~~~ html
<!DOCTYPE html>
<html lang="ko">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Document</title>
<style>

.ball {
   width: 50px;
   height: 50px;
   border-radius: 50px;
   display: inline-block;
}

#b1 {
   background-color: blueviolet;
}

#b2 {
   background-color: bisque;
}

#b3 {
   background-color: blue;
}

#b4 {
   background-color: red; 
}

#b5 {
   background-color: yellowgreen; 
}

</style>
</head>

<body>
   <h1> 1. MouseClick 이벤트 처리 </h1>
   <p>경품 추첨! 원하는 공을 클릭하세요!</p><br><br>

<div class="ball" id="b1" onclick="alert('당첨')"></div>
<div class="ball" id="b2" onmouseover="alert('꽝')"></div>
<div class="ball" id="b3" onmousedown="alert('실패')"></div>
<div class="ball" id="b4" ></div>
<div class="ball" id="b5"></div>

   <script>

      document.getElementById("b4").onclick=function() {
        alert('꽝입니다.');
      };

      document.getElementById("b5").onclick=function() {
        alert('다음기회에...!!!');
      };

   </script>


</body>
</html>

~~~



- if statement 기초 실습

  ~~~ html
  <!DOCTYPE html>
  <html lang="ko">
  <head>
     <meta charset="UTF-8">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <meta http-equiv="X-UA-Compatible" content="ie=edge">
     <title>Document</title>
  </head>
  
  <body>
     <h3> 시간에 따라 다른 인사</h2>
  
     
      <p id="hello">Good Evening!</p>
  
     <script>
  if (new Date().getHours() ,18 ) {
         document.getElementById("hello").innerHTML = "Good day!"
  }
  
      </script>
  
  </body>
  </html>
  ~~~

  