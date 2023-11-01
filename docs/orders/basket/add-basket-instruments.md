# Add basket Instrument
This API used to add Instrument in the created baskets. We can add only limited number of instruments in the basket and repeated instrument can't be added.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | basket order | https://pacetrader.pacefin.in/api/v1/basket/order | Add an instrument to a basket order |

## Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | multipart/form-data |


## parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `basket_id` | `string` | The unique identifier of the basket order.|
| `name` | `string` | The name of the basket order.|
| `order_info` | `object` | The details of the order.|
| `order_info.exchange` | `string` | The exchange of the instrument.|
| `order_info.instrument_token` | `string` | The unique identifier of the instrument.|
| `order_info.client_id` | `string` | Your unique client identifier for the order.|
| `order_info.order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `order_info.price` | `integer` | The price of the order.|
| `client_id` | `string` | Your unique client identifier for the order.|
| `device` | `string` | The device type for the order (WEB, MOBILE).|
| `disclosed_quantity` | `integer` | The disclosed quantity of the order.|
| `exchange` | `string` | The exchange of the instrument.|
| `execution_type` | `string` | The execution type for the order (REGULAR, SPECIAL).|
| `instrument_token` | `string` | The unique identifier of the instrument.|
| `order_side` | `string` | The order side for the order (BUY, SELL).|
| `order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `price` | `integer` | The price of the order.|
| `product` | `string` | The product type for the order (CNC, MIS, NRML).|
| `quantity` | `integer` | The quantity of the order.|
| `series` | `string` | The series of the instrument.|
| `trading_symbol` | `string` | The trading symbol of the instrument.|
| `trigger_price` | `integer` | The trigger price of the order.|
| `underlying_token` | `string` | The unique identifier of the instrument.|
| `user_order_id` | `integer` | The unique identifier of the order.|
| `validity` | `string` | The validity of the order (DAY, IOC).|


## Request Body
```json

{
    "basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
    "name": "Demo",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": "3045",
        "client_id": "NA003",
        "order_type": "MARKET",
        "price": 0
    },
    "client_id": "NA003",
    "device": "WEB",
    "disclosed_quantity": 0,
    "exchange": "NSE",
    "execution_type": "REGULAR",
    "instrument_token": "3045",
    "order_side": "BUY",
    "order_type": "MARKET",
    "price": 0,
    "product": "MIS",
    "quantity": 1,
    "series": "EQ",
    "trading_symbol": "SBIN-EQ",
    "trigger_price": 0,
    "underlying_token": "3045",
    "user_order_id": 10002,
    "validity": "DAY"
}
```

## Response
```json
{
  "data":{
      "basket_id":"72fa28f8-7c08-4a4d-ba7a-fedd461744a1",
      "basket_type":"NORMAL",
      "login_id":"DEMO1",
      "name":"h",
      "order_type":"ALL",
  "orders":[
     {
        "order_id":"a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "order_info":{
           "sl_trigger_price":0.0,
           "spread_token":null,
           "exchange_time":0,
           "last_activity_reference":0,
           "exchange":"NSE",
           "target_price_type":"absolute",
           "leg_order_indicator":null,
           "mode":"NEW",
           "average_price":0,
           "trigger_price":0,
           "sl_order_quantity":0,
           "deposit":0,
           "order_type":"LIMIT",
           "is_trailing":false,
           "product":"MIS",
           "trailing_stop_loss":0.0,
           "underlying_token":"3045",
           "user_order_id":10002,
           "rejection_code":0,
           "order_tag":"",
           "filled_quantity":0,
           "quantity":1,
           "trade_price":0,
           "client_id":"DEMO1",
           "average_trade_price":0,
           "trading_symbol":"SBIN-EQ",
           "series":"",
           "lot_size":0,
           "disclosed_quantity":0,
           "instrument_token":3045,
           "pro_cli":"CLIENT",
           "contract_description":{

           },
           "validity":"DAY",
           "remaining_quantity":0,
           "rejection_reason":"",
           "segment":"",
           "price":506.5,
           "market_protection_percentage":0,
           "stop_loss_value":0.0,
           "nnf_id":0,
           "order_status_info":"",
           "login_id":null,
           "sl_order_price":0.0,
           "execution_type":"BO",
           "square_off_value":0.0,
           "order_side":"BUY",
           "order_entry_time":0,
           "exchange_order_id":"",
           "device":null,
           "oms_order_id":"",
           "order_status":null,
           "square_off":false
        }
     }
  ],
  "product_type":"ALL"
 },
  "message":"Order added in the basket h.",
  "status":"success"
 }
```

## Error Response
```json
{
     "data": {},
     "error_code": 46001,
     "message": "Instrumetn already added",
     "status": "error"
  }
```
