# WebSocket
## Overview
WebSocket is a protocol that provides full-duplex communication channels over a single TCP connection. It is designed to be implemented in web browsers and web servers, but it can be used by any client or server application. The WebSocket protocol makes possible more interaction between a browser and a web site, facilitating live content and the creation of real-time game.

## WebSocket API

### WebSocket URL
The WebSocket URL is the URL used to establish a WebSocket connection with the server. The WebSocket URL has the following format:
```
wss://pacetrader.pacefin.in/ws/v1/feeds/?login_id=<client_id>&access_token=<token>
```


### Features
- **Real-time data** - The WebSocket protocol enables real-time data transfer. The server can send data to the client whenever it wants, without the client requesting it, and vice versa.
- **Low latency** - The WebSocket protocol reduces latency compared to other protocols such as HTTP, which needs to poll the server for changes.





