# Spread Marketdata by websocket

## Introduction
This API is used to get Spread market data. In response provides data of Spread market like field, its type and Byte position.

## Spread Marketdata by websocket

### Overview
Spread Marketdata by websocket is a protocol that provides full-duplex communication channels over a single TCP connection. It is designed to be implemented in web browsers and web servers, but it can be used by any client or server application. The Spread Marketdata by websocket protocol makes possible more interaction between a browser and a web site, facilitating live content and the creation of real-time marketdata.

### WebSocket URL
The Spread Marketdata by websocket URL is the URL used to establish a Spread Marketdata by websocket connection with the server. The Spread Marketdata by websocket URL has the following format:
```
wss://pacetrader.pacefin.in/ws/v1/feeds/?login_id=<client_id>&access_token=<token>
```

### Subscription Payload
The subscription payload is the payload used to subscribe to the Spread Marketdata by websocket. The subscription payload has the following format:
```
  {
    "a": "subscribe",
    "v": [
        [
        2,
        "61226-48519"
        ]
    ],
    "m": "spreaddata"
    }
```


### Subscription Payload Description
- **a** - Action to be performed. In this case, it is `"subscribe"`.
- **v** - Array of instruments to be subscribed. Each instrument is an array of two elements. The first element is the exchange segment and the second element is the spread token.
- **m** - Message type. In this case, it is `"spreaddata"`

### Response Message
The response message is the message sent by the server in response to the subscription payload.

| Field |	Type  |	Byte position | Description |
| --- | --- | --- | --- |
exchange	|`int8`	 | `1-2` |    Exchange code |
instrumentToken1 |	`int32` |	`2-6` | Instrument token 1 |
instrumentToken2 |	`int32` |	`6-10` | Instrument token 2 |
exchangeTimestamp | `int32`	| `10-14 ` | Exchange timestamp |
totalBuyers | `int32`|	`14-18` | Total buyers | 
totalSellers |	`int32`	| `18-22` | Total sellers |
buyers	|`int32` |	`22-42` | Buy customers | 
bidPrices	`int32` |	`42-62` | Bid prices |
bidQtys	 |`int32`	| `62-82` |	Bid quantities |
sellers	| `int32`	| `82-102` | Sell customers |
askPrices |	`int32`	|`102-122` | Ask prices |
askQtys	| `int32` |	`122-142` | Ask quantity
volume	|`int32`|`142-146` | Ask volume |
totalTradeValue	|`int64` | `146-154`| Ask total trade value |
totalBuyQty	|`int64`|	`154-162` | Ask total buy quantity |
totalSellQty |	`int64` |	`162-170` | Ask total sell quantity |
open |	`int32`	| `170-174` | Ask open quantity |
high |	`int32` |	`174-178` | Ask high quantity |
low	 | `int32`	| `172-182` | Ask low quantity |
ltp	 | `int32` |	`172-182` | Ask last traded price |
lastTradedPrice	|`int32`	|`182-186`| Ask last trade price |
ltt	 |`int32` | `182-186` | Ask last trade price |
lowDpr	|`int32` | `186-190` | Ask lowest traded price |
highDpr	| `int32` |	`190-194` | Ask highest traded price |
closePrice | `int32`	| `194-198` | Ask close price |
close	| `int32` |	`194-198` | Ask close price |
averageTradePrice|`int32` |	`198-206` | Ask average trade price |