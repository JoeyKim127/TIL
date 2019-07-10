# node.js - 로그인 기능





~~~ javascript
const express = require('express');
const path = require('path');
const app = express();
const port = 3000;
const cookieparser = require('cookie-parser');
const session = require('express-session');
const FileStore = require('session-file-store')(session);
const morgan = require('morgan');
const fs = require('fs');
const flash = require('connect-flash');

var hasher = require('pbkdf2-password')();


app.use ((req,res,next) => {
    console.log(req.url);
    next();
})


app.use(express.static(path.join(__dirname, 'public')));


app.use(function(req,res,next) {
    console.log(req.url);
    next();
});


app.use(cookieparser());


app.use(flash());


app.set('views', path.join(__dirname, 'views'));
app.set('view engine', 'ejs');
app.engine('html', require('ejs').renderFile);
app.use(morgan('dev'));


app.use(express.urlencoded({
    extended: false
}));


app.use(session({
    secret: '1A@W#E$E',
    resave: false,
    saveUninitialized: true,
    store: new FileStore()

 }));


var sampleUserList = {};


if (fs.existsSync('data/userlist.json')) {
    let rawdata = fs.readFileSync('data/userlist.json');
    sampleUserList = JSON.parse(rawdata);
    console.log(sampleUserList);
}


 app.post('/signup2', (req, res) => {
    console.log(req.body);
    // 회원가입
    let userid = req.body.userid;
    let password = req.body.password;
    let name = req.body.name;
    let email = req.body.email;
    console.log('userid = ', userid);
    console.log('password = ', password);
    console.log('name = ', name);
    console.log('email = ', email);

    hasher({
        password: req.body.password

    }, (err, pass, salt, hash) => {
        if(err) {
            console.log('ERR: ', err);
            res.redirect('/signin_form');
        }

        // 비밀번호는 유출의 위험 때문에 해쉬로 보낸다
        let user = {
            userid: userid,
            password: hash,
            salt: salt,
            name: name,
            email: email
        }
        // 여기 user로 정보 push
        //sampleUserList.push(user);

        sampleUserList[userid] = user;
        fs.writeFileSync('data/userlist.json', JSON.stringify (sampleUserList, null, 2));

        console.log('user added : ', user);
        res.redirect('/login_form');
    });
 });
 

    app.post('/login', (req, res) => {
  
        console.log(req.body);
        let userid = req.body.userid;
        let password = req.body.password;
        console.log('userid = ', userid);
        console.log('password = ', password);
        console.log('userlist = ', sampleUserList);
     
        let user = sampleUserList[userid];
     
        if (user) {
            hasher({
                password: password,
                salt: user.salt
            }, function (err, pass, salt, hash) {
                if (err) {
                    console.log('ERR : ', err);
                    req.flash('fmsg', '오류가 발생했습니다.');
                    res.redirect('login_form');
                   
                }
                if (hash === user.password) {
                    console.log('INFO : ', userid, ' 로그인 성공')
     
                    req.session.user = sampleUserList[userid];
                    req.session.save(function () {
                        res.redirect('/login_done')
                     
                    })
                    return;
                } else {
                    req.flash('fmsg', '패스워드가 맞지 않습니다.');
                    console.log('패스워드 오류');
                    res.redirect('/login_form')
                  
                }
            });
     
           
        } else {
            req.flash('fmsg', 'wrong.');
            res.redirect('/login_form')
            
        }
     });
     

app.get('/',(req,res) => {
    res.render('pract_index.html');
});


app.get('/login_form', (req,res) => {
    res.render('pract_login_form.html');
})


app.get('/login_done', (req,res) => {
    res.render('login_success.html');
});


app.get('/login_form', (req, res) => {

    res.render('login_form.html', {
        fmsg: req.flash('fmsg')
    })
 });
 

app.get('/signin_form', (req,res) => {
    res.render('pract_signin_form.html');
});


app.listen(port, () => {
    console.log('Server listening...' + port);
});

~~~

