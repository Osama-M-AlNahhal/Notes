WebSocket : for dealing with live transmission of data in streams for real time applications

# Getting Started
```js
const WebSocket = require('ws');
const server = new WebSocket.server({ port: 8080 });

server.on('connection', socket => {
	socket.on('message', message => {
		socket.send(`welcome to our shop mr. ${message.clientName}\nHow may i help you?`);
	});
});
```

