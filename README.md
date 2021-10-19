# aws-websocket-client

### Features
```
- Add Socket.io like wrapper to AWS WebSocket client
- Very lightweight plugin with no dependencies :-)
- Easy to use
```

### Download
```
npm install aws-websocket-client
```

### Requirements
```
NodeJS serverless needs to have aws-websocket-server installed.
npm i aws-websocket-server
```

### How to Use
```
import io from 'aws-websocket-client'
const URL = 'wss://{apiId}.execute-api.{region}.amazonaws.com/{stage}' // AWS websocket endpoint
const socket = new io(URL,{
    debug: true,
    messageChannel: 'sendMessage',
    restartMax: 3, // Optional, max retries to reconnect to ws server, default 0, means continous retry at given reconnectTime
    reconnectTime: 3 * 1000, // Optional, Tries to reconnect every 3 seconds on server disconnect
});
```

### Connect to Websocket
```
socket.connect();
```

### Subscribe channel
```
// Channel name can be single string or array of channels eg: ["room 1", "room 2"]
let channelName = 'room 1';
socket.subscribe(channelName);
```

### Unsubscribe channel
```
// Channel name can be single string or array of channels eg: ["room 1", "room 2"]
let channelName = 'room 1';
socket.unsubscribe(channelName);
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