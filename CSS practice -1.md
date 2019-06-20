## CSS Introduction

~~~ html


<html lang="ko">

<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.0/css/all.css" 
    integrity="sha384-lZN37f5QGtY3VHgisS14W3ExzMWZxybE1SJSEsQp9S+oqd12jhcu+A56Ebc1zFSJ" 
    crossorigin="anonymous">
    <link href="https://fonts.googleapis.com/css?family=Noto+Sans&display=swap" rel="stylesheet">

   <title>Practice icon with CSS</title>

   <style>

       body {
        font-family: 'Noto Sans', sans-serif;
       }

       .parent {
           width: 1000px;
           display: table;
           margin: 0 auto;
           text-align: center;
           
       }

       .box {
           display: table-cell;
           height: 300px;
       }

       .box-a {
           background: white;
           width: 33%;
       }

       .box-b {
           background: white;
       }
       
       .box-c {
           background: white;
           width: 33%;
           text-align: center;
       }

      
    h1  {
        text-align: center;
    }


    #p1 { 
        text-align: center;
        color:grey;
    }


    #p2 { 
        text-align: center;
    }


    #p3 { 
        text-align: center; 
    }


   </style>
</head>

<body>
    <h1>SERVICES</h1>
    <p id="p1"><i>These are our main services we provide</i></p>
    <br>

   <div class="parent">
       <div class="box box-a">
           <i class="fas fa-shield-alt" style="font-size:80px;color:#F7DC6F;"></i><br>
           <p id="p2"><b>E-COMMERCE</b></p>
           Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus vestibulum vulputate nisi. Nunc finibus diam eu posuere euismod. </p>
       </div>


       <div class="box box-b">
           <i class="fas fa-shopping-cart" style="font-size:80px;color:#F7DC6F;"></i><br>
           <p id="p2"><b>RESPONSIVE-DESIGN</b></p>
           <p id="p3">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus vestibulum vulputate nisi. Nunc finibus diam eu posuere euismod.</p>
       </div>


       <div class="box box-c">   
           <i class="fas fa-laptop" style="font-size:80px;color:#F7DC6F;"></i><br>
           <p id="p2"><b>WEB SECURITY</b></p>
           <p id="p3">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus vestibulum vulputate nisi. Nunc finibus diam eu posuere euismod. </p>
       </div>
   </div>

</body>

</html>

~~~

![](C:\Users\student\Pictures\css pract.PNG)

