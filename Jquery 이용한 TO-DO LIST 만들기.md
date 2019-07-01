# Jquery 이용한 TO-DO LIST 만들기 - 190701

- Bootstrap를 이용해 페이지 레이아웃
- CSS를 이용해 스타일 적용
- 입력창에 할 일 추가하면  밑에 추가
- JQuery 이용해 기능 추가 
  - 할 일 추가
  - FINISH/ REMOVE 버튼
  - REMOVE - 할일 삭제
  - FINISH - 글씨에 줄 긋기, 글씨색 변경, 완료한 시간 표시



~~~html
<!DOCTYPE html>
<html lang="ko">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">

    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">

    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css"
        integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js"
        integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo"
        crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js"
        integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1"
        crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js"
        integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM"
        crossorigin="anonymous"></script>



    <title>Document</title>

    <style>
        .container {
            background-color: rgb(191, 223, 161);
            color: black;
            padding: 0px;
            border: 0px;
            text-align: center
        }

        .main-body {
            background-color: aliceblue;
            color: black;
        }


        .checkbox {
            border: 1px solid black;
            padding: 20px;
            margin: 10px;

        }
    </style>

</head>


<body>
    <div class="container">
        <div class="jumbotron">
            <div class="row">
                <div class="col"></div>

                <div class="col-sm-8">

                    <h1>To Do List</h1>

                        <div class="input-todo">
                        <input type="text" class="submit" size="30" placeholder="Title..." id="new_todo" required>
                        <button class="btn-default" id="add">ADD</button>
                        </div>
                </div>
                <div class="col"></div>

            </div>
        </div>
    </div>



    <div class="row">
        <div class="col"></div>
        <div class="col-sm-8">
            <div class="main-body"></div>
        </div>
        <div class="col"></div>
    </div>

    <script>

        $(function () {
            $("#add").click(function () {
                let data = $('#new_todo').val();
                console.log(data);
                $(".main-body").append("<p class=checkbox>" + data + "<button class='btn remove' style='float: right;'>REMOVE</button>" +
                    "<button class='btn finish'style='float: right;'>FINISH</button>" + "<p>");
            });
        });



        $('input[type=text]').keydown(function (key) {
            if (key.keyCode == 13) {
                let data = $('#new_todo').val();
                console.log(data);
                $(".main-body").append("<p class=checkbox>" + data + "<button class='btn remove' style='float: right;'>REMOVE</button>" +
                    "<button class='btn finish'style='float: right;'>FINISH</button>" + "<p>");
            }
        });



        $(document).on("click", ".remove", function () {
            $(this).parent().remove();
        });



        $(document).on("click", ".finish", function () {


            $(this).parent().css("text-decoration", "line-through");
            $(this).parent().css("color", "#E59866");

            var date = new Date();

            $(this).parent().append("<p class=timestamp> (@" + date + ") </p>")
            // if ($(this).siblings.attr('class') !="timestamp")

        });


    </script>

</body>

</html>
~~~

