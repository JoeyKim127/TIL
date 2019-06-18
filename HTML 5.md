## HTML 5

#### - HTML basic structure

~~~ html
<!DOCTYPE html>
<html>ㅗ씌

    <head>
        <title>Hello</title>   
    </head>
    
</html>
~~~



#### - HTML metadata

~~~ html
<!DOCTYPE html>
<html>
<head>
    <title>HTML 메타정보</title>
    <meta charset="UTF-8">
    <meta name="author" content="Hong">
    <meta name="keywords" content="HTML, CSS3, JavaScript, JQuery">
    <meta name="description" content="Web Programming">
    <meta http-equiv="refresh" content="10.http://cafe.naver.com/go2web">
    <base href="http://w3.org/" target="_blank">
</head>
<body> 
    <p>헤드 태그 내 메타정보에는 웹 문서를 만든 이, 검색 시 키워드, 문서에 대한 설명, 문서 내 기본 디렉토리 등이 포함됩니다</p>
    <p>이 문서는 10초 후 저자 카페로 이동합니다</p>
    <a href="">여기를 클릭하면 기본 디렉토리로 설정된 www.w3.org 사이트로 이동합니다.</a>

</body>
</html>
~~~



#### - HTML spaces

~~~ html
<!DOCTYPE HTML>
<html>
<head>
    <title>공백처리 문제</title>
</head>

<body>

    html 5에서는
    탭, 엔터             스페이스바와 같은  

    <br> &nbsp; &nbsp;&nbsp;&nbsp;  키보드 값을 인식하지 않는다

</body>

</html>
~~~



#### - HTML style

~~~ html
<!DOCTYPE HTML>
<html>

<head>
    <title>Title Page</title>
</head>

<body style="background-color:lightpink;">
        <h1 style="color:darkorange;", style="font-size: 100px">This is a heading</h1>
        <p style="background-color:red;">This is a paragraph.</p>

        <h1 style="font-family:verdana;">This is a heading</h1>s
        <p style="font-family:courier;">This is a paragraph.</p>

        <h1 style="font-size:300%;">This is a heading</h1>
        <p style="font-size:160%;">This is a paragraph.</p>

        <h1 style="font-size:100px;", style="color:white;">This is a heading</h1>
        <p style="font-size:80px;">This is a paragraph.</p>

        <h1 style="text-align:center;">Centered Heading</h1>
        <p style="text-align:center;">Centered paragraph.</p>



</body>

</html>
~~~



#### - HTML quote

~~~ html
<!DOCTYPE HTML>
<html>

<head>
    <title>Title Page</title>
</head>

<body>
    <h1>quote test</h1>
    <blockquote cite="http://www.worldwildlife.org/who/index.html">
        For 50 years, WWF has been protecting the future of nature.
        The world's leading conservation organization,
        WWF works in 100 countries and is supported by
        1.2 million members in the United States and
        close to 5 million globally.
    </blockquote>

     <p>The <abbr title="World Health Organization">WHO</abbr> was founded in 1948.</p>

    <address>
        Written by John Doe.<br> 
        Visit us at:<br>
        Example.com<br>
         Box 564, Disneyland<br>
        USA
    </address>

    <p><cite>The Scream</cite> by Edvard Munch. Painted in 1893.</p>
</body>

</html>
~~~



#### - HTML images

~~~ html
<!DOCTYPE html>
<html>
<body>

        <h1>color rgba test</h1>
        <h1 style="background-color:rgba(255, 99, 71, 0);">rgba(255, 99, 71, 0)</h1>
<h1 style="background-color:rgba(255, 99, 71, 0.2);">rgba(255, 99, 71, 0.2)</h1>
<h1 style="background-color:rgba(255, 99, 71, 0.4);">rgba(255, 99, 71, 0.4)</h1>
<h1 style="background-color:rgba(255, 99, 71, 0.6);">rgba(255, 99, 71, 0.6)</h1>
<h1 style="background-color:rgba(255, 99, 71, 0.8);">rgba(255, 99, 71, 0.8)</h1>
<h1 style="background-color:rgba(255, 99, 71, 1);">rgba(255, 99, 71, 1)</h1>

<p>You can make transparent colors by using the RGBA color value.</p>



<h1>color name test</h1>
<h1 style="border: 4px solid skyblue;">Hello World</h1>
<h1 style="border: 4px solid tomato;">Hello World</h1>
<h1 style="border: 4px solid mediumslateblue;">Hello World</h1>
<h1 style="border: 4px solid forestgreen;">Hello World</h1>

<h1 style="background-color:rgb(255, 0, 0);">rgb(255, 0, 0)</h1>
<h1 style="background-color:rgb(0, 0, 255);">rgb(0, 0, 255)</h1>
<h1 style="background-color:rgb(60, 179, 113);">rgb(60, 179, 113)</h1>
<h1 style="background-color:rgb(238, 130, 238);">rgb(238, 130, 238)</h1>
<h1 style="background-color:rgb(255, 165, 0);">rgb(255, 165, 0)</h1>
<h1 style="background-color:rgb(106, 90, 205);">rgb(106, 90, 205)</h1>

<p>In HTML, you can specify colors using RGB values.</p>

</body>
</html>

~~~



#### - HTML lists

~~~ html
<!DOCTYPE html>
<html>
<body>

<h2>An Unordered HTML List</h2>

<ul>
  <li>Coffee</li>
  <li>Tea
    <ul>
      <li>Black tea</li>
      <li>Green tea</li>
    </ul>
  </li>
  <li>Milk</li>
</ul> 

<h2>An Ordered HTML List</h2>

<ol type="1">
  <li>Apples</li>
  <li>Bananas</li>
  <li>Lemons</li>
   <li>Oranges</li>
</ol>
 
<h2>A Description HTML List</h2>

<dl>
  <dt>첫 번째 아이템</dt>
  <dd>-HTML</dd>
  <dt>두 번째 아이템</dt>
  <dd>-CSS3 </dd>
   <dt>세 번째 아이템</dt>
  <dd>-JavaScript </dd>
</dl>


</body>
</html>
~~~

