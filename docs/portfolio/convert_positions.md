## Convert Positions


| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT `         | `Convert Positions`    | https://pacetrader.pacefin.in/api/v1/position/convert | Convert positions          |

### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json




### Request Parameters
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `client_id` | `string` | ClientId `<clintid>` |
| `exchange` | `string` | NSE,BSE,NFO,CDS,MCX |
| `instrument_token` | `int` | 3045 (example) |
| `product` | `string` | CNC,MIS,NRML |
| `new_product` | `string` | CNC,MIS,NRML |
| `quantity` | `int` | 100 |
| `validity` | `string` | DAY or IOC |
| `order_side` | `string` | SELL or BUY |


### Request Body
```json
{
    "client_id": "<ClientId>",
    "exchange": "NSE",
    "instrument_token": 3045,
    "product": "MIS",
    "new_product": "CNC",
    "quantity": 100,
    "validity": "DAY",
    "order_side": "SELL"
}
```

### Response
```json
{
    "data": {},
    "message": "Conversion completed",
    "status": "success"
}
```

### Error Response
```json
{
    "data": {
    },
    "error_code": 45000,
    "message": "Error from backend: (1013)-template is not assigned for this client",
    "status": "error"
}
```


### Code Examples

=== "python - http.client"
    ``` python
    import http.client
    import json

    conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
    payload = json.dumps({
    "client_id": "<ClientId>",
    "exchange": "NSE",
    "instrument_token": 3045,
    "product": "MIS",
    "new_product": "CNC",
    "quantity": 100,
    "validity": "DAY",
    "order_side": "SELL"
    })
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }
    conn.request("PUT", "/api/v1/position/convert", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))

    ```

=== "python - requests"
    ``` python
    import requests
    import json

    url = "https://pacetrader.pacefin.in/api/v1/position/convert"

    payload = json.dumps({
    "client_id": "<ClientId>",
    "exchange": "NSE",
    "instrument_token": 3045,
    "product": "MIS",
    "new_product": "CNC",
    "quantity": 100,
    "validity": "DAY",
    "order_side": "SELL"
    })
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }

    response = requests.request("PUT", url, headers=headers, data=payload)

    print(response.text)
    
    ```



=== "javascript - fetch"
    ``` javascript
    var myHeaders = new Headers();
    myHeaders.append("x-device-type", "WEB");
    myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    myHeaders.append("content-type", "application/json");

    var raw = JSON.stringify({
    "client_id": "<ClientId>",
    "exchange": "NSE",
    "instrument_token": 3045,
    "product": "MIS",
    "new_product": "CNC",
    "quantity": 100,
    "validity": "DAY",
    "order_side": "SELL"
    });

    var requestOptions = {
    method: 'PUT',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
    };

    fetch("https://pacetrader.pacefin.in/api/v1/position/convert", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
    ```

=== "javascript - jquery"
    ``` javascript
    var settings = {
    "url": "https://pacetrader.pacefin.in/api/v1/position/convert",
    "method": "PUT",
    "timeout": 0,
    "headers": {
        "x-device-type": "WEB",
        "x-authorization-token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg",
        "content-type": "application/json"
    },
    "data": JSON.stringify({
        "client_id": "<ClientId>",
        "exchange": "NSE",
        "instrument_token": 3045,
        "product": "MIS",
        "new_product": "CNC",
        "quantity": 100,
        "validity": "DAY",
        "order_side": "SELL"
    }),
    };

    $.ajax(settings).done(function (response) {
    console.log(response);
    });
    
    ```

=== "javascript - XHr"
    ``` javascript
    var data = JSON.stringify({
    "client_id": "<ClientId>",
    "exchange": "NSE",
    "instrument_token": 3045,
    "product": "MIS",
    "new_product": "CNC",
    "quantity": 100,
    "validity": "DAY",
    "order_side": "SELL"
    });

    var xhr = new XMLHttpRequest();
    xhr.withCredentials = true;

    xhr.addEventListener("readystatechange", function() {
    if(this.readyState === 4) {
        console.log(this.responseText);
    }
    });

    xhr.open("PUT", "https://pacetrader.pacefin.in/api/v1/position/convert");
    xhr.setRequestHeader("x-device-type", "WEB");
    xhr.setRequestHeader("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    xhr.setRequestHeader("content-type", "application/json");

    xhr.send(data);
    ```



