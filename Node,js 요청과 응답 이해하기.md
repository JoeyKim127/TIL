# Node,js 요청과 응답 이해하기



~~~ javascript
const http = require('http');

const server = http.createServer();
var port = 3000;

server.listen(port, function () {
    console.log('웹 서버 대기중... : %d', port);
});

server.on('connection', function (socket) {
    var addr = socket.address();
    console.log('클라이언트 : ' + addr.address + ":" + addr.port + '이 접속했습니다.');
});

server.on('close', function () {
    console.log('웹 서버 종료됨.');
});

server.on('request', function(req, res) {
    res.write('<h1>Hello world</h1>');
    
    res.end();
});
~~~

