# cancel GTT order
This API is used to delete the existing gtt order. The gtt order list should not be empty.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | gtt order | https://pacetrader.pacefin.in/api/v1/event/gtt/<ClientId>/<Id> | Cancel a GTT order |

## Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

## parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `id` | `string` | The unique identifier of the order.|



#### Request Body
```json
{
    "client_id": "<ClientId>",
    "id": "<Id>"
}
```

## Response
```json
{
    "data": {
        "id": "5d712b9f-53c6-4eb9-af55-733fae0a19a2"
        },
    "message": "event cancelled succesfully",
    "status": "success"
}
```

## Error response
```json
{
    "data": {},
    "error_code": 45000,
    "message": "Error from backend: (500)-event id not found",
    "status": "error"
}
```