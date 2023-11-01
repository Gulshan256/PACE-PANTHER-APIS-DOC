# Modify GTT Orders
This API is used to modify the existing gtt orders. We can modify the price and trigger price etc.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | gtt order | https://pacetrader.pacefin.in/api/v1/event/gtt | Modify a GTT order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |


#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `expiry_time` | `string` | The expiry time for the GTT order. (yyyy-mm-dd)|
| `order` | `object` | The details of the order.|
| `order.client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `order.device` | `string` | The device type for the order (web).|
| `order.disclosed_quantity` | `integer` | The disclosed quantity of the order.|
| `order.exchange` | `string` | The exchange of the instrument. (NSE, BSE)|
| `order.instrument_token` | `string` | The unique identifier of the instrument.|
| `order.market_protection_percentage` | `integer` | The market protection percentage of the order.|
| `order.order_side` | `string` | The order side for the order (BUY, SELL).|
| `order.order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `order.price` | `float` | The price of the order.|
| `order.product` | `string` | The product type for the order (CNC, MIS, NRML).|
| `order.quantity` | `integer` | The quantity of the order.|
| `order.sl_order_price` | `integer` | The stop loss order price of the order.|
| `order.sl_order_quantity` | `integer` | The stop loss order quantity of the order.|
| `order.sl_trigger_price` | `integer` | The stop loss trigger price of the order.|
| `order.trigger_price` | `float` | The trigger price of the order.|
| `order.user_order_id` | `integer` | The unique identifier of the order.|


#### Request Body
```json
{
    "expiry_time": "2022-10-17",
    "order": {
        "client_id": "DEMO1",
        "device": "web",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "instrument_token": "11536",
        "market_protection_percentage": 0,
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 3611.45,
        "product": "CNC",
        "quantity": 1,
        "sl_order_price": 0,
        "sl_order_quantity": 0,
        "sl_trigger_price": 0,
        "trigger_price": 3611.45,
        "user_order_id": 10002
    }
}
```

## Response
```json
{
    "data": {
        "id": "673a20c8-80d5-4a0c-8a34-23f20fe79661"
    },
    "message": "gtt request modified successfully",
    "status": "success"
}
```

## Error Response
```json
{
    "data": {},
    "error_code": 45000,
    "message": "Error from backend: (1600)-cannot modify, no data found with this id",
    "status": "error"
}
```
