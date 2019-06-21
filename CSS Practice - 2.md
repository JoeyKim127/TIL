### HTML & CSS Practice 2

~~~ html
<!DOCTYPE HTML>
<html>

<head>
    <title>Chatina</title>

    <style>
    * {
        box-sizing: border-box;
    }

    .margin{
        background-color: gray;
        color: white;
        padding: 25px;
        width: auto;
        background-size: cover;
        
    }

    .sidebar{
        float: left;
        background-color:white;
        width: 25%;
        height: 300px;
        padding:15px;
    }

    .text-area {
        float: right;
        background-color:white;
        width: 75%;
        height: 300px;
        padding:15px
    }
    
    button {
        background-color: goldenrod;
        color: white;
        width: 200px;
        height: 35px;
        padding: 5px;
        text-align: center;
        cursor: pointer;
        font-size: 20px;
        margin-top: 25px;
        margin-left: 40px;
        
    }

    .menu li:hover {
  background-color: #0099cc;
    }

    </style>

</head>

<body>
   
<div>
    <h1 class="margin" style="font-size:40px">Chatina</h1>
</div>

<div class="sidebar">
    <div class="button">
        <button>The Flight</button>
    </div>

    <div>
        <button>The City</button>
    </div>

    <div>
        <button>The Island</button>
    </div>

    <div>
        <button>The Food</button>
    </div>

   
</div>

<div class="text-area">
    <h3 style="font-size: 50px">The City</h3>
    <p style="font-size: 20px">Chania is the capital of the Chania region on the island of Crete. 
        The city can be divided in two parts, the old town and the modern city.
         You will learn more about web layout and responsive web pages in a later chapter.</p>
</div>


<div class="margin">
    <h5 style="font-size: 15px">Footer text</h5>
</div>


</body>

</html>
~~~

