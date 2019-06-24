## Bootstrap

- Bootstrap 이용해서 홈페이지 만들어보기



~~~ html
<!DOCTYPE HTML>
<html lang="en">

<head>
    <title>Hello!</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.0/css/bootstrap.min.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.1/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.4.0/js/bootstrap.min.js"></script>
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.7.0/css/all.css"
        integrity="sha384-lZN37f5QGtY3VHgisS14W3ExzMWZxybE1SJSEsQp9S+oqd12jhcu+A56Ebc1zFSJ" crossorigin="anonymous">


    <style>
        .jumbotron {
            background-color: #F9E79F;
            color: white;
            padding: 100px 25px;
        }

        .container-body {
            padding: 60px 50px;
        }

        .bg-grey {
            background-color: #F2F3F4;

        }

        .logo {
            font-size: 200px;
        }

        @media screen and (max-width: 768px) {
            .col-sm-4 {
                text-align: center;
                margin: 25px 0;
            }

        }
    </style>

</head>

<body>

    <div class="jumbotron text-center">
        <h1>YOUNGJO</h1>
        <p>Hello! I'm from South Korea;)</p>
        <form class="form-inline">
            <div class="input-group">
                <input type="email" class="form-control" size="50" placeholder="Email Address" required>
                <div class="input-group-btn">
                    <button type="button" class="btn btn-danger">Subscribe</button>
                </div>
            </div>
        </form>
    </div>

    <div class="container-body">

        <div class="row">

            <div class="col-sm-8">
                <h1>About Youngjo Kim</h1>
                <p>About Youngjo Kim</p>
                <button class="btn btn-default btn-lg">Send a message</button>
            </div>

            <div class="col-sm-4">
                <i class="fas fa-dog logo"></i>
            </div>

        </div>

    </div>


    <div class="container-body bg-grey">

        <div class="row">
            <div class="col-sm-4">
                <i class="fas fa-paw logo"></i>
            </div>

            <div class="col-sm-8">
                <h1>Values</h1>
                <p><strong>Misson:</strong>lorem ipsum..</p>
                <p><strong>Vision:</strong>lorem ipsum..</p>
            </div>

        </div>

    </div>

    <div class="container-body text-center">
        <h2>Hobbies</h2>
        <p>I like to...</p><br>

        <div class="row">
            <div class="col-sm-4">
                <i class="fas fa-swimmer" style="font-size:40px"></i>
                <h3>Swimming</h3>
                <p>I enjoy swimming</p>
            </div>
            <div class="col-sm-4">
                <i class="fas fa-laptop" style="font-size:40px"></i>
                <h3>Programming</h3>
                <p>I will become a famous promgrammer</p>
            </div>
            <div class="col-sm-4">
                <i class="fas fa-plane" style="font-size:40px"></i>
                <h3>Traveling</h3>
                <p>I love traveling around the world</p>
            </diV>
        </div><br>


        <div class="row">
            <div class="col-sm-4">
                <i class="fas fa-shopping-bag" style="font-size:40px"></i>
                <h3>Shopping</h3>
                <p>I like Shopping</p>
            </div>

            <div class="col-sm-4">
                <i class="fas fa-bicycle" style="font-size:40px"></i>
                <h3>Bike Riding</h3>
                <p>I like to ride bicycles</p>
            </div>

            <div class="col-sm-4"></div>
            <i class="fas fa-book-open" style="font-size:40px"></i>
            <h3>Reading</h3>
            <p>I like reading</p>
            </div>
        </div>
    </div>
</body>

</html>
~~~

