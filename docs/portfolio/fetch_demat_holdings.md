## Fetch Demat Holdings

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| GET           | `Fetch Demat Holdings`    | https://pacetrader.pacefin.in/api/v1/holdings?client_id=<ClientId> | Fetch demat holdings          |

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


### Request Body
```json
{
    "client_id": "<clientid>",
}
```


### Response
```json
 {
     "data":{
      "holdings": [
        {
        "branch_code": "",
        "buy_avg": 240.2,
        "buy_avg_mtm": 277.7500000000006,
        "client_id": "DEMO1",
        "exchange": "NSE",
        "free_quantity": 55,
        "instrument_details":{
        "exchange": 1,
        "instrument_name": "EQ",
        "instrument_token": 3045,
        "trading_symbol": "SBIN-EQ"
        }
        "isin": "INE062A01020",
        "ltp": 245.25,
        "pending_quantity": 0,
        "pledge_quantity": 0,
        "previous_close": 240.2,
        "quantity": 55,
        "symbol": "SBIN",
        "t0_price": 0,
        "t0_quantity": 0,
        "t1_price": 0,
        "t1_quantity": 0,
        "t2_price": 0,
        "t2_quantity": 0,
        "today_pledge_quantity": 0,
        "token": 3045,
        "trading_symbol": "SBIN",
        "transaction_type": "",
        "used_quantity": 0
        }]
     }
     "message": "",
     "status": "success"
 }
```

### Error Response
```json
  {
     "data":{
     }
     "error_code": 44000,
     "message": "`type` is invalid",
     "status": "error"
  }

```

____________________________________________________________________________________________________________________



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
    conn.request("GET", "/api/v1/holdings?client_id=%3CClientId%3E", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))

    ```

=== "python - requests"
    ``` python
    import requests
    import json

    url = "https://pacetrader.pacefin.in/api/v1/holdings?client_id=<ClientId>"

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

    fetch("https://pacetrader.pacefin.in/api/v1/holdings?client_id=<ClientId>", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
    ```

=== "javascript - jquery"
    ``` javascript
    var settings = {
    "url": "https://pacetrader.pacefin.in/api/v1/holdings?client_id=<ClientId>",
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

    xhr.open("GET", "https://pacetrader.pacefin.in/api/v1/holdings?client_id=%3CClientId%3E");
    xhr.setRequestHeader("x-device-type", "WEB");
    xhr.setRequestHeader("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    xhr.setRequestHeader("content-type", "application/json");

    xhr.send();
    ```
