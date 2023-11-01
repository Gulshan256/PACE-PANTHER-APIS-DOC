# Rename Basket
You can rename a basket order by specifying the basket order identifier and the 



| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | basket order | https://pacetrader.pacefin.in/api/v1/basket | Rename a basket order |

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
| `name` | `string` | The new name of the basket order.|


#### Request Body
```json
{
  "basket_id": "<BasketId>",
  "name": "<NewBasketName>"
}
```

## Response
```json
{
    basket_id: "0786e757-2e8f-44b2-9559-deeac2e00114"
    basket_type: "NORMAL"
    login_id: "NA003"
    name: "bhavana"
    order_type: "ALL"
    orders: []
    product_type: "ALL"
    message: "Basket name updated successfully"
    status: "success"
}
```

# Error Response
```json
{
  "data": {},
  "error_code": 48001,
  "message": "`name` Basket name restricted to 20 characters",
  "status": "error"
}
```
