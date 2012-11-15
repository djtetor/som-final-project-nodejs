var app = require('express').createServer()
  , io = require('socket.io').listen(app);

app.listen(1234);

app.get('/', function (req, res) {
  res.sendfile(__dirname + '/index.html');
});

io.sockets.on('connection', function (socket) {
	socket.emit('news', { hello: 'Hello World' });
	socket.on('mensaje',function(data){
		console.log(data);	
		socket.emit('mensaje', { mensaje: 'El usuario dijo: '+data.mensaje });
		socket.broadcast.send(data.mensaje);
//		socket.broadcast.json.send({ mensaje: 'objeto json' });
	});
});

