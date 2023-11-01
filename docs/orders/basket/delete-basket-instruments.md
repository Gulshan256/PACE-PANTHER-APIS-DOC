# Delete basket Instrument
This API used to delete basket Instrument inside the basket. This requires basketId to delete the basket instrument in the basket.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | basket order | https://pacetrader.pacefin.in/api/v1/basket/order?basket_id=<BasketId>&name=<BasketName>&order_id=<OrderId> | Delete an instrument from a basket order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `basket_id` | `string` | The unique identifier of the basket order.|
| `name` | `string` | The name of the basket order.|
| `order_id` | `string` | The unique identifier of the order.|



#### Request Body
```json
{
  "basket_id": "<BasketId>",
  "name": "<BasketName>",
  "order_id": "<OrderId>"
}
```

## Error Response
```json
{
  
}
```