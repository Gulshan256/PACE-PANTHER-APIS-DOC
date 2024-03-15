# Detailed Mrketdata by websocket

## Introduction
This API is used to get Detailed Market Data. In response provides data of Detailed Market like field, its type and Byte position.

## Detailed Marketdata by websocket

### Overview
Detailed Marketdata by websocket is a protocol that provides full-duplex communication channels over a single TCP connection. It is designed to be implemented in web browsers and web servers, but it can be used by any client or server application. The Detailed Marketdata by websocket protocol makes possible more interaction between a browser and a web site, facilitating live content and the creation of real-time marketdata.

### WebSocket URL
The Detailed Marketdata by websocket URL is the URL used to establish a Detailed Marketdata by websocket connection with the server. The Detailed Marketdata by websocket URL has the following format:
```
wss://pacetrader.pacefin.in/ws/v1/feeds/?login_id=<client_id>&access_token=<token>
```

### Subscription Payload
The subscription payload is the payload used to subscribe to the Detailed Marketdata by websocket. The subscription payload has the following format:
```
Subscription Payload
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
     "m": "marketdata"
    }
```

### Subscription Payload Description
- **a** - Action to be performed. In this case, it is `"subscribe"`.
- **v** - Array of instruments to be subscribed. Each instrument is an array of two elements. The first element is the exchange segment and the second element is the instrument token.
- **m** - Message type. In this case, it is `"marketdata"`


### Response Message
The response message is the message sent by the server in response to the subscription payload.

| Field |	Type  |	Byte position | Description |
| --- | --- | --- | --- |
mode  |	`int8`  |	`0-1` |	Mode of trading |
exchange |	`int8`	| `1-2` |	Exchange code |
instrumentToken |	`int32` |	`2-6 `|	Instrument token |
lastTradedPrice |	`int32` |	`6-10` |	Last trade price |
lastTradedTime	| `int32`	 | `10-14` | Last trade time |
lastTradedQuantity | `int32` |	`14-18`  | Last trade quantity |
volume | `int32`	| `18-22` | Volume |
bestBidPrice	| `int32`	 | `22-26` | Best bid price |
bestBidQuantity	| `int32`	| `26-30` | Best bid quantity |
bestAskPrice	| `int32` |	`30-34` | Best ask price |
bestAskQuantity |	`int32` |	`34-38` | Best ask quantity |
totalBuyQuantity |	`int64` |	`38-46` | Total bid quantity |
totalSellQuantity |	`int64` |	`46-54` | Total bid quantity |
averageTradePrice |	`int32` |	`54-58` | Average trade price |
exchangeTimestamp |	`int32` |	`58-62` | Exchange timestamp |
openPrice |	`int32` |	`62-66` | Open price |
highPrice | `int32` |	`66-70` | High bid price |
lowPrice  |	`int32` |	`70-74` | Low bid price |
closePrice|	`int32` |`74-78` |  Close bid price | 
yearlyHighPrice |	`int32`  |	`78-82` | Yearly high price |
yearlyLowPrice |	`int32` |	`82-86` | Yearly low price |
lowDPR	| `int32`	 | `86-90` | Low bid price |
HighDPR	|`int32` |	`90-94` | High bid price |
currentOpenInterest |	`int32` |	`94-98`| Current open interest |
initialOpenInterest |	`int32`	| `98-102` | Initial open interest |