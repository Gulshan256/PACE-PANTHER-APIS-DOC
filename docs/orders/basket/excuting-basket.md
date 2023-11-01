# Execute Basket

You can execute a basket order by specifying the basket order identifier and the instrument details.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | basket order | https://pacetrader.pacefin.in/api/v1/orders/kart | Execute a basket order |

## Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

## parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `basket_id` | `string` | The unique identifier of the basket order.|
| `execution_type` | `string` | The execution type for the order (REGULAR, SPECIAL).|
| `name` | `string` | The name of the basket order.|
| `square_off` | `boolean` | The square off value of the order.|


## Request Body
```json
{
    "basket_id": "<BasketId>",
    "execution_type": "NML",
    "name": "<BasketName>",
    "square_off": false
}
```

## Response
```json
{

  "data": {
    "data": {
    "basket_id": "20211017-4",
    "message": "basket Order Placed Successfully"
    }
  },
    "message": "Order place successfully",
    "status": "success"
}
```

## Error Response
```json
{
    "data":{},
    "error_code":49002,
    "message":"instrument `SBIN-EQ` is disabled for hedging",
    "status":"error"
}
```