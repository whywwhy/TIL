# Socket.io

### 1️⃣ Socket.io란?
<hr/>

socket.io는 양방향 통신을 하기 위해 웹소켓 기술을 활용하는 라이브러리

Socket.io는 웹소켓(WebSocket)을 기반으로 동작, <br/>
웹소켓이 지원되지 않는 브라우저에서는 폴링(Polling) 방식을 사용하여 실시간 통신을 구현

Socket.io는 현재 바로 사용할 수 있는 기술!

 Socket.io는 JavaScript를 이용하여 브라우저 종류에 상관없이 실시간 웹을 구현할 수 있도록 한 기술

 Socket.io는 WebSocket, FlashSocket, AJAX Long Polling, AJAX Multi part Streaming, IFrame, JSONP Polling을 하나의 API로 추상화한 것
 
  브라우저와 웹 서버의 종류와 버전을 파악하여 가장 적합한 기술을 선택하여 사용하는 방식

- 표준 기술이 아니며, 라이브러리
- 소켓 연결 실패 시 fallback을 통해 다른 방식으로 알아서 해당 클라이언트와 연결을 시도함
- 방 개념을 이용해 일부 클라이언트에게만 데이터를 전송하는 브로드캐스팅이 가능함

### 어떤걸 써야 하나?
- 서버에서 연결된 소켓(사용자)들을 세밀하게 관리해야 하는 서비스 -> <br/>`Broadcasting 기능`이 있는 socket.io를 쓰는게 유지보수 측면에서 훨씬 이점 많음
- 가상화폐 거래소 같이 데이터 전송이 많은 경우 -> <br/> 빠르고 비용이 적은 표준 WebSocket을 이용
- socket.io로 구성된 서버에게 소켓 연결을 하기 위해서는 클라이언트측에서 반드시 `socket.io-client라이브러리`를 이용해야 함

### 2️⃣ Socket.io 사용
<hr/>

Socket.io -> 브라우저에서는 JavaScript, 서버에서는 Node.js 를 사용한다.

```
npm install socket.io
// npm을 이용하여 Socket.io를 웹 서버에 설치
```

```
// 80 포트로 소켓을 연다
var io = require('socket.io').listen(80);

// connection이 발생할 때 핸들러를 실행한다.
io.sockets.on('connection', function (socket) {  
// 클라이언트로 news 이벤트를 보낸다.
    socket.emit('news', { hello: 'world' });

// 클라이언트에서 my other event가 발생하면 데이터를 받는다.
socket.on('my other event', function (data) {  
        console.log(data);
    });
});

//설치 후 서버 스크립트를 작성
```

스크립트를 nohup 등을 이용하여 백그라운드로 실행
- nohup 사용 -> hang-up signal이 발생해도 스크립트의 동작이 멈추지 X

클라이언트 -> Socket.io 패키지에 있는 클라이언트 스크립트를 이용

```
<script src="/socket.io/socket.io.js"></script>  
<script>  
// localhost로 연결한다.
var socket =  
  io.connect('http://localhost');

// 서버에서 news 이벤트가 일어날 때 데이터를 받는다.
socket.on('news',  
  function (data) {
    console.log(data);
  //서버에 my other event 이벤트를 보낸다.
    socket.emit('my other event', 
      { my: 'data' });
});
</script>  
```

socket.io 공식문서 |  https://socket.io/ 