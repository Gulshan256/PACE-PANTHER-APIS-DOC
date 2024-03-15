# Compact Marketdata by websocket

## Introduction
This API is used to get Compact market data. In response provides data of Compact market like field, its type and Byte position.


## Compact Marketdata by websocket

### Overview
Compact Marketdata by websocket is a protocol that provides full-duplex communication channels over a single TCP connection. It is designed to be implemented in web browsers and web servers, but it can be used by any client or server application. The Compact Marketdata by websocket protocol makes possible more interaction between a browser and a web site, facilitating live content and the creation of real-time marketdata.

### WebSocket URL
The Compact Marketdata by websocket URL is the URL used to establish a Compact Marketdata by websocket connection with the server. The Compact Marketdata by websocket URL has the following format:
```
wss://pacetrader.pacefin.in/ws/v1/feeds/?login_id=<client_id>&access_token=<token>
```

### Subscription Payload
The subscription payload is the payload used to subscribe to the Compact Marketdata by websocket. The subscription payload has the following format:
```
 {
  "a": "subscribe",
  "v": [
  [
        1,
        22
  ],
  [
        1,
        1330
  ]
  ],
  "m": "compact_marketdata"
  }
``` 
### Subscription Payload Description
- a - Action to be performed. In this case, it is `"subscribe"`.
- **v** - Array of instruments to be subscribed. Each instrument is an array of two elements. The first element is the exchange segment and the second element is the instrument token.
- **m** - Message type. In this case, it is `"compact_marketdata"`



### Response Message
The response message is the message sent by the server in response to the subscription payload. 

| Field |	Type  |	Byte position | Description |
| --- | --- | --- | --- |
exchange |	`int8`  |	`1-2 `|	Exchange code |
instrumentToken |`int32` |	`2-6` |	Instrument token |
ltp |	`int32` |	`6-10`    |	Last traded price |
change | `int32` | `10-14` |	Change in price |
ltt	| `int32`	| `14-18 `|	Last traded time |
lowDpr	| `int32`	 | `18-22` |	Lowest traded price |
highDpr |	`int32` |	`22-26` |	Highest traded price |
currentOpenInterest	| `int32` | `26-30` |	Current open interest |
initialOpenInterest | `int32`	| `30-34` |	Initial open interest |
bidPrice |	`int32` |	`34-38` |	Bid price |
askPrice |	`int32` |	`38-42` |	Ask price |

