## Fetch positions netwise

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| GET           | `Fetch Positions Netwise`    | https://pacetrader.pacefin.in/api/v1/positions?client_id=<ClientId>&type=historical       | Fetch positions netwise          |

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
| `type` | `string` | `historical` |


### Request Body
```json
{
    "client_id": "<clientid>",
    "type": "historical"
}
```

```json

Response
  {
     "data": [
     {     
     "average_buy_price": 40520,
     "average_price": 0,
     "average_sell_price": 40538,
     "buy_amount": 40520,
     "buy_quantity": 1,
     "cf_buy_amount": 0,
     "cf_buy_quantity": 0,
     "cf_sell_amount": 0,
     "cf_sell_quantity": 0,
     "client_id": "DEMO1",
     "close_price": 0,
     "exchange": "MCX",
     "instrument_token": 222895,
     "ltp": 40520,
     "multiplier": 1,
     "net_amount": 18,
     "net_quantity": 0,
     "previous_close": 40697,
     "pro_cli": "CLIENT",
     "prod_type": 0,
     "product": "NRML",
     "realized_mtm": 0,
     "segment": "FutOpt",
     "sell_amount": 40538,
     "sell_quantity": 1,
     "symbol": "GOLDGUINEA",
     "token": 222895,
     "trading_symbol": "GOLDGUINEA20NOVFUT",
     "v_login_id": "DEMO1"
     }]
     "message": "",
     "status": "success"
  }
```


# Error Response

```json
{
    "data":{
    }
    "error_code": 44000,
    "message": "`type` is invalid",
    "status": "error"
}
```




### Code Examples

=== "python - http.client"
    ``` python
    import http.client
    import json

    conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
    payload = ''
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }
    conn.request("GET", "/api/v1/positions?client_id=%3CClientId%3E&type=historical", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))

    ```

=== "python - requests"
    ``` python
    import requests
    import json

    url = "https://pacetrader.pacefin.in/api/v1/positions?client_id=<ClientId>&type=historical"

    payload={}
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }

    response = requests.request("GET", url, headers=headers, data=payload)

    print(response.text)

    ```

=== "javascript - fetch"
    ``` javascript
    var myHeaders = new Headers();
    myHeaders.append("x-device-type", "WEB");
    myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    myHeaders.append("content-type", "application/json");

    var requestOptions = {
    method: 'GET',
    headers: myHeaders,
    redirect: 'follow'
    };

    fetch("https://pacetrader.pacefin.in/api/v1/positions?client_id=<ClientId>&type=historical", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
    ```

=== "javascript - jquery"
    ``` javascript
    var settings = {
    "url": "https://pacetrader.pacefin.in/api/v1/positions?client_id=<ClientId>&type=historical",
    "method": "GET",
    "timeout": 0,
    "headers": {
        "x-device-type": "WEB",
        "x-authorization-token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg",
        "content-type": "application/json"
    },
    };

    $.ajax(settings).done(function (response) {
    console.log(response);
    });
    
    ```

=== "javascript - XHr"
    ``` javascript
    // WARNING: For GET requests, body is set to null by browsers.

    var xhr = new XMLHttpRequest();
    xhr.withCredentials = true;

    xhr.addEventListener("readystatechange", function() {
    if(this.readyState === 4) {
        console.log(this.responseText);
    }
    });

    xhr.open("GET", "https://pacetrader.pacefin.in/api/v1/positions?client_id=%3CClientId%3E&type=historical");
    xhr.setRequestHeader("x-device-type", "WEB");
    xhr.setRequestHeader("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    xhr.setRequestHeader("content-type", "application/json");

    xhr.send();

    ```
