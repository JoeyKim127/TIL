# npm express  연습하기

npm 소개

- 노드를 위한 패키지 매니저
- 노트 패키지 버전은 SemVer 방식을 따른다
- package json 버전 표시 방법



- Middleware 실습하기

~~~ javascript
const express = require('express');
const app = express();
const port = 3000;


app.use(function(req,res,next){

    console.log('사용자 미들웨어1');
    req.body2 = {}
    req.body2.id = 'hong';
    next();
});

app.use(function(req,res,next) {
        console.log('사용자 미들웨어2');
req.body2.name = 'gildong'
next();
    });

app.get('/', (req,res)  => {
    console.log('/ 요청받음');
    console.log(req.body2.id + ', ' + req.body2.name);
    res.send(`<h1>${req.body2.id}, ${req.body2.name}</h1>`)
});

app.listen(port, () => {
    console.log('Server listening...' + port);
});

~~~



