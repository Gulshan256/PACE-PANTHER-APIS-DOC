# Edit basket Instrument
This API used to edit the basket instrument present in the basket. In this we are able to edit the basket instrument details like quantity.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | basket order | https://pacetrader.pacefin.in/api/v1/basket/order | Edit an instrument in a basket order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | multipart/form-data |

#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `basket_id` | `string` | The unique identifier of the basket order.|
| `name` | `string` | The name of the basket order.|
| `order_info` | `object` | The details of the order.|
| `order_info.exchange` | `string` | The exchange of the instrument.|
| `order_info.instrument_token` | `integer` | The unique identifier of the instrument.|
| `order_info.client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `order_info.order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `order_info.price` | `float` | The price of the order.|
| `order_info.quantity` | `integer` | The quantity of the order.|
| `order_info.disclosed_quantity` | `integer` | The disclosed quantity of the order.|
| `order_info.validity` | `string` | The validity of the order (DAY, IOC).|
| `order_info.product` | `string` | The product type for the order (CNC, MIS, NRML).|
| `order_info.trading_symbol` | `string` | The trading symbol of the instrument.|
| `order_info.order_side` | `string` | The order side for the order (BUY, SELL).|
| `order_info.user_order_id` | `integer` | The unique identifier of the order.|
| `order_info.underlying_token` | `string` | The unique identifier of the instrument.|
| `order_info.series` | `string` | The series of the instrument.|
| `order_info.oms_order_id` | `string` | The unique identifier of the order.|
| `order_info.exchange_order_id` | `string` | The unique identifier of the order.|
| `order_info.trigger_price` | `float` | The trigger price of the order.|
| `order_info.stop_loss_value` | `float` | The stop loss value of the order.|
| `order_info.square_off_value` | `float` | The square off value of the order.|
| `order_info.trailing_stop_loss` | `float` | The trailing stop loss value of the order.|
| `order_info.is_trailing` | `boolean` | The trailing stop loss value of the order.|
| `order_info.execution_type` | `string` | The execution type for the order (REGULAR, SPECIAL).|
| `order_id` | `string` | The unique identifier of the order.|

#### Request Body
```json
 {
    "basket_id":"<BasketId>",
    "name":"<BasketName>",
    "order_info":
 {
      "exchange":"NSE",
      "instrument_token":3045,
      "client_id":"<ClientId>",
      "order_type":"LIMIT",
      "price":506.5,
      "quantity":1,
      "disclosed_quantity":0,
      "validity":"DAY",
      "product":"MIS",
      "trading_symbol":"SBIN-EQ",
      "order_side":"BUY",
      "user_order_id":10002,
      "underlying_token":"3045",
      "series":"EQ",
      "oms_order_id":"a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
      "exchange_order_id":"",
      "trigger_price":0,
      "stop_loss_value":0,
      "square_off_value":0,
      "trailing_stop_loss":0,
      "is_trailing":false,
      "execution_type":"BO"
 },
  "order_id":"a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
}
```

## Response
```json
{

    "data": {
        "basket_id": "b993d276-4fe9-4050-ab80-6ab1f5f9863f",
        "basket_type": "NORMAL",
        "login_id": "NA003",
        "name": "test",
        "order_type": "ALL",
"orders": [
  {
    "order_id": "a38f3470-2a26-4f88-839c-7d4e1987c97a",
    "order_info": {

      "instrument_token": 3045,
      "validity": "DAY",
      "pro_cli": "CLIENT",
      "exchange": "NSE",
      "product": "MIS",
      "trigger_price": 0,
      "client_id": "NA003",
      "mode": "NEW",
      "contract_description": {},
      "last_activity_reference": 0,
      "rejection_reason": "",
      "oms_order_id": "",
      "trading_symbol": "SBIN-EQ",
      "order_entry_time": 0,
      "trade_price": 0,
      "rejection_code": 0,
      "nnf_id": 0,
      "execution_type": "REGULAR",
      "quantity": 1,
      "price": 0,
      "series": "",
      "user_order_id": 10002,
      "filled_quantity": 0,
      "exchange_order_id": "",
      "order_status_info": "",
      "trailing_stop_loss": null,
      "disclosed_quantity": 0,
      "login_id": null,
      "target_price_type": "absolute",
      "lot_size": 0,
      "order_type": "MARKET",
      "square_off": false,
      "exchange_time": 0,
      "is_trailing": false,
      "spread_token": null,
      "average_price": 0,
      "order_tag": "",
      "market_protection_percentage": 0,
      "average_trade_price": 0,
      "order_side": "BUY",
      "order_status": null,
      "device": null,
      "deposit": 0,
      "leg_order_indicator": null,
      "stop_loss_value": null,
      "underlying_token": "3045",
      "square_off_value": null,
      "remaining_quantity": 0,
      "segment": ""
    }
  },
],
"product_type": "ALL"
 },
  "message": "Order updated successfully.",
  "status": "success"
}
```

## Error Response

```json
 {
  "data": {},
  "error_code": 48004,
  "message": "`order_info` order price cannot be zero in SL/LIMIT order",
  "status": "error"
}
```