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

### Where to use Web sockets
- WebSockets is not a full-on replacement for the HTTP protocol so Whenever you need continuously real time data stream over the internet, whether it be client-to-server or server-to-client only then you should use Websocket.
- Without page refresh we are getting live data like -
      - Trading
      - Live scores

### Where NOT to use Websocket:
- Whenever you need old data or data only once you should not use Websocket rather you should use HTTP protocol.

## AJAX vs WebSocket
- When the traditional request-response is required then, Ajax can be used
- When there is real-time communication involved and fast results are needed, then web sockets can be used.
- In Ajax when you send a request, server sends response for that request and connection ends.
- In WebSockets when you establish a connection with server, then you can communicate between client and server as much you want and it keeps connection alive.
- 
