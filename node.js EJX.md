## Node.js ejx 실습

### EJS 이용해 데이터 테이블에 넣는 방법 



- Server js

~~~ javascript
<!-- insert userlist data--!>

var Userlist = [{
    FirstName: 'John',
    DoB: '25-05-93',
    Nationality: 'UK',
    Email: 'john324@gmail.com',
    numOfVisits: 25,
},

{
    FirstName: 'Mary',
    DoB: '09-07-99',
    Nationality: 'South Korea',
    Email: 'mary907@gmail.com',
    numOfVisits: 47,
},
{
    FirstName: 'Bob',
    DoB: '19-05-79',
    Nationality: 'Spain',
    Email: 'bob000@gmail.com',
    numOfVisits: 29,
}

];

<!--Server app.get javascript--!>
app.get('/userdata', (req,res) => {
    res.json(Userlist);
})


app.get('/userlist', (req,res) => {
    res.render('user_list.html', {Userlist: Userlist});
    
});

~~~



- user_list.html

~~~ html

<body>
    <div class="container">

        <div class="jumbotron">
            <h1>User List</h1>
        </div>

<div>

<form method="POST" name="regform">
    <input type="text" name="FirstName" value="First Name" onfocus="this.value=''">
    <input type="text" name="DoB" value="Date of Birth" onfocus="this.value=''">
    <input type="text" name="Nationality" value="Nationality" onfocus="this.value=''">
    <input type="text" name="Email" value="Email" onfocus="this.value=''">
    <input type="text" name="numOfVisits" value="number Of Visits" onfocus="this.value=''">
    <input type="button" id="submit" name="submit" value="Submit" > 
</form>

</div>

        <div>
            <table class='table table-striped' id="user">


                <tr>
                    <th>FirstName</th>
                    <th>DoB</th>
                    <th>Nationality</th>
                    <th>Email</th>
                    <th>numOfVisits</th>
                </tr>

                <% for (let i=0; i<Userlist.length; i++)  { %>
                    <tr>
                    <td><%= Userlist[i].FirstName %></td>
                    <td><%= Userlist[i].DoB %></td>
                    <td><%= Userlist[i].Nationality %></td>
                    <td><%= Userlist[i].Email %></td>
                    <td><%= Userlist[i].numOfVisits %></td>
</tr>
                    <% } %>
            </table>
        </div>

   
    </div>
    
    </body>
    
    </html>
~~~







### EJS를 이용해 3개의 파일(header,body,footer) 합치는 방법

- server 

~~~html

app.get('/main',(req,res) => {
    res.render('main.html');
});

~~~



- main.html (C:\work\node js\chapter6\views)

~~~ html
<!DOCTYPE html>
<html lang="ko">

<head>

        <!-- Latest compiled and minified CSS -->
        <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css">

        <!-- jQuery library -->
        <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>

        <!-- Popper JS -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js"></script>

        <!-- Latest compiled JavaScript -->
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"></script>

        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>

        <!--footer.ejs를 여기에 추가한다(파일경로가 inc속 footer 파일)--!>
        <% include ./inc/header.ejs %> 

</head>

<body>
        <h1>this is body</h1>

    <!--footer.ejs를 여기에 추가한다(파일경로가 inc속 footer 파일)--!>
        <% include ./inc/footer.ejs %> 

</body>

</html>
~~~



- footer.ejs (C:\work\node js\chapter6\views\inc)
  - 여기에 그냥 html 파일 적으면 된다

~~~ html
<hr>
<h>This is footer</h>
~~~



- header.ejs (C:\work\node js\chapter6\views\inc)
  - 여기에 그냥 html 파일 적으면 된다

~~~html
<hr>
<h>This is header</h>
~~~

