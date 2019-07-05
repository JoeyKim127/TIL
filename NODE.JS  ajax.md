## NODE.JS  ajax 

ajax 이용해 데이터 테이블에 넣기

- server javascript

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

<!--Userlist의 데이터를 json형태({abc:123} 이렇게)로 localhost:3000/userdata로 보내주세욥--!>
app.get('/userdata', (req,res) => {
    res.json(Userlist);
})

<!--localhost:3000/userlist를 입력하면 'user_list.html'를  띄어주세욥--!>   
app.get('/userlist', (req,res) => {
    res.render('user_list.html');
});

~~~



- user_list.html

~~~ html
<!-- ajax를 이용해 자료 표 안에 넣기 -->


<body>
    <!-- 먼저 데이터를 넣을 표 만들기(id="user") -->
    <div>
            <table class='table table-striped' id="user">


                <tr>
                    <th>FirstName</th>
                    <th>DoB</th>
                    <th>Nationality</th>
                    <th>Email</th>
                    <th>numOfVisits</th>
                </tr>
                
    <script>

<!--serializeobject 함수 사용해서 새로운 데이터 표 안에 넣기--!>
        function serializeObject($form) {
            var unindexed_array = $form.serializeArray();
            var indexed_array = {};

            $.map(unindexed_array, function (n, i) {
                indexed_array[n['name']] = n['value'];
            });

            return indexed_array;
        }

<!-- server javascript안에 있는 var= Userlist 데리고 오는 방법--!>
        $(function () {
            $.ajax({
                type: 'GET',
                url: '/userdata', <!--ajax를 이용해서 가져올 데이터는 /userdata에 있다--!>
                success: function (data) {
                    console.log('success');
                    console.log(data);
                    $.each(data, function (i, item) {
                        <!--표 id="user" 뒤에 append 해주세욥--!>
                        $("#user").append(`
                <tr>
    
                <td>${item.FirstName}</td>
                <td>${item.DoB}</td>
                <td>${item.Nationality}</td>
                <td>${item.Email}</td>
                <td>${item.numOfVisits}</td>
                </tr>`
                        ).trigger("create");
                    });
                },
                error: function (err) {
                    console.log('err');
                }
            });

        
<!--Submit 누르면 새로고침 없이 새로 입력한 데이터 표 안에 넣기--!>
    <!--하지만 추가하면 위의 Userlist의 내용이 계속 추가되니 오류 고치기!!!--!>
        $('#submit').click(function () {

            let newData = serializeObject($('form[name=regform]'));;

            $.ajax({
                type: 'POST',
                url: '/api/regcar',
                dataType: 'json',
                data: newData,
                success: function (data) {
                    console.log('success');
                    console.log(data);
                    $.each(data, function (i, item) {
                        <!--표 id="user" 뒤에 append 해주세욥--!>
                    $("#user").append(`
                <tr>
    
                <td>${item.FirstName}</td>
                <td>${item.DoB}</td>
                <td>${item.Nationality}</td>
                <td>${item.Email}</td>
                <td>${item.numOfVisits}</td>
                </tr>` )
            });
                },
                error: function (err) {
                    console.log('err');
                }
            });
        })
}) 

    </script>

</body>

~~~





