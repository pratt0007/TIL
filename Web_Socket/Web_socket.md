# Web Socket
- WebSocket is a full-duplex (two-way communication) protocol that is used in the same scenario of client-server communication.
- It is a stateful protocol, which means the connection between client and server will keep alive until it is terminated by either client or server, after closing the connection by either of the client and server, the connection is terminated from both the end.
- WebSockets do not use the http:// or https:// scheme (because they do not follow the HTTP protocol)
- Rather, WebSocket URIs use a new scheme ws: (or wss: for a secure WebSocket).
## How web socket works
![image](https://github.com/pratt0007/TIL/assets/100209212/d6c14fa5-264c-4626-a320-2c4c609e752f)
- Client sends regular HTTP request with an additional header to be requested.
- The Server gets the HTTP request and notices the request for the Upgrade header.
- This lets the Server know that we are requesting for a WebSocket connection.
- If all goes well persistent connection established between client and server. Connection can be closed either by client or server.

![image](https://github.com/pratt0007/TIL/assets/100209212/62480d24-beb8-4ccc-88ea-64f5cf8a2f45)
