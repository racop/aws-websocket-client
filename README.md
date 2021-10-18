# aws-websocket-client

### Features
```
- Add Socket.io like wrapper to AWS WebSocket client
- Very lightweight plugin with no dependencies :-)
- Easy to use
```

### Download
```
npm install aws-websocket-client -S
```

### Requirements
```
NodeJS serverless needs to have aws-websocket-server installed.
npm i aws-websocket-server -S
```

### How to Use
```
import io from 'aws-websocket-client'
const URL = 'wss://{apiId}.execute-api.{region}.amazonaws.com/{stage}' // AWS websocket endpoint
const socket = new io(URL,{
    debug: true,
    messageChannel: 'sendMessage',
    restartMax: 3, // Maximum retries to connect to websocket server, if fails then clear websocket [0 means infinite]
    reconnectTime: 2 * 1000, // Tries to reconnect every 3 seconds on server disconnect
});
```

### Connect to Websocket
```
socket.connect()
```

### Subscribe channel
```
let channelName = 'group 1';
socket.subscribe()
```

### Unsubscribe channel
```
let channelName = 'group 1';
socket.unsubscribe()
```

### Send Message to an event
```
// message should be object
// Emit on hello event
socket.emit("hello", message);
```


### Listen to an event
```
// Listen to hello event 
socket.on('hello',(data)=>{
    // Data is object
    // Do someting with data here
    console.log(data);
})
```

### Disconnect socket
```
socket.disconnect();
```