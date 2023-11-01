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




## Example Code

=== "python - http.client"
   
    ``` python
    # you an use any other module as well such as requests, urllib, etc.,

    import http.client
    import json

    conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
    payload = json.dumps({
    "basket_id": "<BasketId>",
    "name": "<BasketName>",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 506.5,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "trading_symbol": "SBIN-EQ",
        "order_side": "BUY",
        "user_order_id": 10002,
        "underlying_token": "3045",
        "series": "EQ",
        "oms_order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "exchange_order_id": "",
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": False,
        "execution_type": "BO"
    },
    "order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
    })
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }
    conn.request("PUT", "/api/v1/basket/order", payload, headers)
    res = conn.getresponse()
    data = res.read()
    print(data.decode("utf-8"))

    ```


=== "JavaScript"

    ``` javascript

    // You can also use other methods such as `axios`,`jQuery`, `XHR`, etc..
    var myHeaders = new Headers();
    myHeaders.append("x-device-type", "WEB");
    myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    myHeaders.append("content-type", "application/json");

    var raw = JSON.stringify({
    "basket_id": "<BasketId>",
    "name": "<BasketName>",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 506.5,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "trading_symbol": "SBIN-EQ",
        "order_side": "BUY",
        "user_order_id": 10002,
        "underlying_token": "3045",
        "series": "EQ",
        "oms_order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "exchange_order_id": "",
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    },
    "order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
    });

    var requestOptions = {
    method: 'PUT',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
    };

    fetch("https://pacetrader.pacefin.in/api/v1/basket/order", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));

    ```


=== "C#"
    ``` csharp
    // You can also use other libraries such as RestSharp, etc..

    var client = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Put, "https://pacetrader.pacefin.in/api/v1/basket/order");
    request.Headers.Add("x-device-type", "WEB");
    request.Headers.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    request.Headers.Add("content-type", "application/json");
    var content = new StringContent(" {\r\n    \"basket_id\":\"<BasketId>\",\r\n    \"name\":\"<BasketName>\",\r\n    \"order_info\":\r\n {\r\n      \"exchange\":\"NSE\",\r\n      \"instrument_token\":3045,\r\n      \"client_id\":\"<ClientId>\",\r\n      \"order_type\":\"LIMIT\",\r\n      \"price\":506.5,\r\n      \"quantity\":1,\r\n      \"disclosed_quantity\":0,\r\n      \"validity\":\"DAY\",\r\n      \"product\":\"MIS\",\r\n      \"trading_symbol\":\"SBIN-EQ\",\r\n      \"order_side\":\"BUY\",\r\n      \"user_order_id\":10002,\r\n      \"underlying_token\":\"3045\",\r\n      \"series\":\"EQ\",\r\n      \"oms_order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\",\r\n      \"exchange_order_id\":\"\",\r\n      \"trigger_price\":0,\r\n      \"stop_loss_value\":0,\r\n      \"square_off_value\":0,\r\n      \"trailing_stop_loss\":0,\r\n      \"is_trailing\":false,\r\n      \"execution_type\":\"BO\"\r\n },\r\n  \"order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\"\r\n}", null, "application/json");
    request.Content = content;
    var response = await client.SendAsync(request);
    response.EnsureSuccessStatusCode();
    Console.WriteLine(await response.Content.ReadAsStringAsync());


    ```

=== "cURL"
    ``` bash
    curl --location --request PUT 'https://pacetrader.pacefin.in/api/v1/basket/order' \
    --header 'x-device-type: WEB' \
    --header 'x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
    --header 'content-type: application/json' \
    --data ' {
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
    }'
    ```

=== "Dart"
    ``` dart

    var headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    };
    var request = http.Request('PUT', Uri.parse('https://pacetrader.pacefin.in/api/v1/basket/order'));
    request.body = json.encode({
    "basket_id": "<BasketId>",
    "name": "<BasketName>",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 506.5,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "trading_symbol": "SBIN-EQ",
        "order_side": "BUY",
        "user_order_id": 10002,
        "underlying_token": "3045",
        "series": "EQ",
        "oms_order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "exchange_order_id": "",
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    },
    "order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
    });
    request.headers.addAll(headers);

    http.StreamedResponse response = await request.send();

    if (response.statusCode == 200) {
    print(await response.stream.bytesToString());
    }
    else {
    print(response.reasonPhrase);
    }


        
    ```

=== "Go-Native"
	
    ``` go

    package main

    import (
    "fmt"
    "strings"
    "net/http"
    "io/ioutil"
    )

    func main() {

    url := "https://pacetrader.pacefin.in/api/v1/basket/order"
    method := "PUT"

    payload := strings.NewReader(` {`+"
    "+`
        "basket_id":"<BasketId>",`+"
    "+`
        "name":"<BasketName>",`+"
    "+`
        "order_info":`+"
    "+`
    {`+"
    "+`
        "exchange":"NSE",`+"
    "+`
        "instrument_token":3045,`+"
    "+`
        "client_id":"<ClientId>",`+"
    "+`
        "order_type":"LIMIT",`+"
    "+`
        "price":506.5,`+"
    "+`
        "quantity":1,`+"
    "+`
        "disclosed_quantity":0,`+"
    "+`
        "validity":"DAY",`+"
    "+`
        "product":"MIS",`+"
    "+`
        "trading_symbol":"SBIN-EQ",`+"
    "+`
        "order_side":"BUY",`+"
    "+`
        "user_order_id":10002,`+"
    "+`
        "underlying_token":"3045",`+"
    "+`
        "series":"EQ",`+"
    "+`
        "oms_order_id":"a5d13c1f-f99c-4230-ad19-9ed8e826ee74",`+"
    "+`
        "exchange_order_id":"",`+"
    "+`
        "trigger_price":0,`+"
    "+`
        "stop_loss_value":0,`+"
    "+`
        "square_off_value":0,`+"
    "+`
        "trailing_stop_loss":0,`+"
    "+`
        "is_trailing":false,`+"
    "+`
        "execution_type":"BO"`+"
    "+`
    },`+"
    "+`
    "order_id":"a5d13c1f-f99c-4230-ad19-9ed8e826ee74"`+"
    "+`
    }`)

    client := &http.Client {
    }
    req, err := http.NewRequest(method, url, payload)

    if err != nil {
        fmt.Println(err)
        return
    }
    req.Header.Add("x-device-type", "WEB")
    req.Header.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg")
    req.Header.Add("content-type", "application/json")

    res, err := client.Do(req)
    if err != nil {
        fmt.Println(err)
        return
    }
    defer res.Body.Close()

    body, err := ioutil.ReadAll(res.Body)
    if err != nil {
        fmt.Println(err)
        return
    }
    fmt.Println(string(body))
    }
            
    ```

=== "HTTP"
    ``` http
    PUT /api/v1/basket/order HTTP/1.1
    Host: pacetrader.pacefin.in
    x-device-type: WEB
    x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg
    content-type: application/json
    Content-Length: 799

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

=== "Java-OkHttp"
    ``` java
    // You can also use other libraries such as Unirest, etc..

    OkHttpClient client = new OkHttpClient().newBuilder()
    .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, " {\r\n    \"basket_id\":\"<BasketId>\",\r\n    \"name\":\"<BasketName>\",\r\n    \"order_info\":\r\n {\r\n      \"exchange\":\"NSE\",\r\n      \"instrument_token\":3045,\r\n      \"client_id\":\"<ClientId>\",\r\n      \"order_type\":\"LIMIT\",\r\n      \"price\":506.5,\r\n      \"quantity\":1,\r\n      \"disclosed_quantity\":0,\r\n      \"validity\":\"DAY\",\r\n      \"product\":\"MIS\",\r\n      \"trading_symbol\":\"SBIN-EQ\",\r\n      \"order_side\":\"BUY\",\r\n      \"user_order_id\":10002,\r\n      \"underlying_token\":\"3045\",\r\n      \"series\":\"EQ\",\r\n      \"oms_order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\",\r\n      \"exchange_order_id\":\"\",\r\n      \"trigger_price\":0,\r\n      \"stop_loss_value\":0,\r\n      \"square_off_value\":0,\r\n      \"trailing_stop_loss\":0,\r\n      \"is_trailing\":false,\r\n      \"execution_type\":\"BO\"\r\n },\r\n  \"order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\"\r\n}");
    Request request = new Request.Builder()
    .url("https://pacetrader.pacefin.in/api/v1/basket/order")
    .method("PUT", body)
    .addHeader("x-device-type", "WEB")
    .addHeader("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg")
    .addHeader("content-type", "application/json")
    .build();
    Response response = client.newCall(request).execute();

    ```

=== "C - Libcurl"
    ``` c
    CURL *curl;
    CURLcode res;
    curl = curl_easy_init();
    if(curl) {
    curl_easy_setopt(curl, CURLOPT_CUSTOMREQUEST, "PUT");
    curl_easy_setopt(curl, CURLOPT_URL, "https://pacetrader.pacefin.in/api/v1/basket/order");
    curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
    curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
    struct curl_slist *headers = NULL;
    headers = curl_slist_append(headers, "x-device-type: WEB");
    headers = curl_slist_append(headers, "x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    headers = curl_slist_append(headers, "content-type: application/json");
    curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
    const char *data = " {\r\n    \"basket_id\":\"<BasketId>\",\r\n    \"name\":\"<BasketName>\",\r\n    \"order_info\":\r\n {\r\n      \"exchange\":\"NSE\",\r\n      \"instrument_token\":3045,\r\n      \"client_id\":\"<ClientId>\",\r\n      \"order_type\":\"LIMIT\",\r\n      \"price\":506.5,\r\n      \"quantity\":1,\r\n      \"disclosed_quantity\":0,\r\n      \"validity\":\"DAY\",\r\n      \"product\":\"MIS\",\r\n      \"trading_symbol\":\"SBIN-EQ\",\r\n      \"order_side\":\"BUY\",\r\n      \"user_order_id\":10002,\r\n      \"underlying_token\":\"3045\",\r\n      \"series\":\"EQ\",\r\n      \"oms_order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\",\r\n      \"exchange_order_id\":\"\",\r\n      \"trigger_price\":0,\r\n      \"stop_loss_value\":0,\r\n      \"square_off_value\":0,\r\n      \"trailing_stop_loss\":0,\r\n      \"is_trailing\":false,\r\n      \"execution_type\":\"BO\"\r\n },\r\n  \"order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\"\r\n}";
    curl_easy_setopt(curl, CURLOPT_POSTFIELDS, data);
    res = curl_easy_perform(curl);
    }
    curl_easy_cleanup(curl);


    ```

=== "node.js - Native"
    ``` javascript
    // You can also use other libraries such as `axios`,`jQuery`, `request` `Unirest`, etc.. this example uses `node.js` native`

    var https = require('follow-redirects').https;
    var fs = require('fs');

    var options = {
    'method': 'PUT',
    'hostname': 'pacetrader.pacefin.in',
    'path': '/api/v1/basket/order',
    'headers': {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
    },
    'maxRedirects': 20
    };

    var req = https.request(options, function (res) {
    var chunks = [];

    res.on("data", function (chunk) {
        chunks.push(chunk);
    });

    res.on("end", function (chunk) {
        var body = Buffer.concat(chunks);
        console.log(body.toString());
    });

    res.on("error", function (error) {
        console.error(error);
    });
    });

    var postData = JSON.stringify({
    "basket_id": "<BasketId>",
    "name": "<BasketName>",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 506.5,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "trading_symbol": "SBIN-EQ",
        "order_side": "BUY",
        "user_order_id": 10002,
        "underlying_token": "3045",
        "series": "EQ",
        "oms_order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "exchange_order_id": "",
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    },
    "order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
    });

    req.write(postData);

    req.end();

    ```


=== "Objective-C - NSURLSession"
    ``` objective-c
    #import <Foundation/Foundation.h>

    dispatch_semaphore_t sema = dispatch_semaphore_create(0);

    NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://pacetrader.pacefin.in/api/v1/basket/order"]
    cachePolicy:NSURLRequestUseProtocolCachePolicy
    timeoutInterval:10.0];
    NSDictionary *headers = @{
    @"x-device-type": @"WEB",
    @"x-authorization-token": @"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg",
    @"content-type": @"application/json"
    };

    [request setAllHTTPHeaderFields:headers];
    NSData *postData = [[NSData alloc] initWithData:[@" {\r\n    \"basket_id\":\"<BasketId>\",\r\n    \"name\":\"<BasketName>\",\r\n    \"order_info\":\r\n {\r\n      \"exchange\":\"NSE\",\r\n      \"instrument_token\":3045,\r\n      \"client_id\":\"<ClientId>\",\r\n      \"order_type\":\"LIMIT\",\r\n      \"price\":506.5,\r\n      \"quantity\":1,\r\n      \"disclosed_quantity\":0,\r\n      \"validity\":\"DAY\",\r\n      \"product\":\"MIS\",\r\n      \"trading_symbol\":\"SBIN-EQ\",\r\n      \"order_side\":\"BUY\",\r\n      \"user_order_id\":10002,\r\n      \"underlying_token\":\"3045\",\r\n      \"series\":\"EQ\",\r\n      \"oms_order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\",\r\n      \"exchange_order_id\":\"\",\r\n      \"trigger_price\":0,\r\n      \"stop_loss_value\":0,\r\n      \"square_off_value\":0,\r\n      \"trailing_stop_loss\":0,\r\n      \"is_trailing\":false,\r\n      \"execution_type\":\"BO\"\r\n },\r\n  \"order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\"\r\n}" dataUsingEncoding:NSUTF8StringEncoding]];
    [request setHTTPBody:postData];

    [request setHTTPMethod:@"PUT"];

    NSURLSession *session = [NSURLSession sharedSession];
    NSURLSessionDataTask *dataTask = [session dataTaskWithRequest:request
    completionHandler:^(NSData *data, NSURLResponse *response, NSError *error) {
    if (error) {
        NSLog(@"%@", error);
        dispatch_semaphore_signal(sema);
    } else {
        NSHTTPURLResponse *httpResponse = (NSHTTPURLResponse *) response;
        NSError *parseError = nil;
        NSDictionary *responseDictionary = [NSJSONSerialization JSONObjectWithData:data options:0 error:&parseError];
        NSLog(@"%@",responseDictionary);
        dispatch_semaphore_signal(sema);
    }
    }];
    [dataTask resume];
    dispatch_semaphore_wait(sema, DISPATCH_TIME_FOREVER);

    ```

=== "ocaml-Cohttp"
    ``` ocaml
    open Lwt
    open Cohttp
    open Cohttp_lwt_unix

    let postData = ref " {\r\n    \"basket_id\":\"<BasketId>\",\r\n    \"name\":\"<BasketName>\",\r\n    \"order_info\":\r\n {\r\n      \"exchange\":\"NSE\",\r\n      \"instrument_token\":3045,\r\n      \"client_id\":\"<ClientId>\",\r\n      \"order_type\":\"LIMIT\",\r\n      \"price\":506.5,\r\n      \"quantity\":1,\r\n      \"disclosed_quantity\":0,\r\n      \"validity\":\"DAY\",\r\n      \"product\":\"MIS\",\r\n      \"trading_symbol\":\"SBIN-EQ\",\r\n      \"order_side\":\"BUY\",\r\n      \"user_order_id\":10002,\r\n      \"underlying_token\":\"3045\",\r\n      \"series\":\"EQ\",\r\n      \"oms_order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\",\r\n      \"exchange_order_id\":\"\",\r\n      \"trigger_price\":0,\r\n      \"stop_loss_value\":0,\r\n      \"square_off_value\":0,\r\n      \"trailing_stop_loss\":0,\r\n      \"is_trailing\":false,\r\n      \"execution_type\":\"BO\"\r\n },\r\n  \"order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\"\r\n}";;

    let reqBody = 
    let uri = Uri.of_string "https://pacetrader.pacefin.in/api/v1/basket/order" in
    let headers = Header.init ()
        |> fun h -> Header.add h "x-device-type" "WEB"
        |> fun h -> Header.add h "x-authorization-token" "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
        |> fun h -> Header.add h "content-type" "application/json"
    in
    let body = Cohttp_lwt.Body.of_string !postData in

    Client.call ~headers ~body `PUT uri >>= fun (_resp, body) ->
    body |> Cohttp_lwt.Body.to_string >|= fun body -> body

    let () =
    let respBody = Lwt_main.run reqBody in
    print_endline (respBody)

    ```


=== "PHP - cURL"
    ``` php
    //you can also use other libraries such as `Guzzle`, `HTTP_Request2`, `pcel_http`, etc..
    <?php

    $curl = curl_init();

    curl_setopt_array($curl, array(
    CURLOPT_URL => 'https://pacetrader.pacefin.in/api/v1/basket/order',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_ENCODING => '',
    CURLOPT_MAXREDIRS => 10,
    CURLOPT_TIMEOUT => 0,
    CURLOPT_FOLLOWLOCATION => true,
    CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
    CURLOPT_CUSTOMREQUEST => 'PUT',
    CURLOPT_POSTFIELDS =>' {
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
    }',
    CURLOPT_HTTPHEADER => array(
        'x-device-type: WEB',
        'x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type: application/json'
    ),
    ));

    $response = curl_exec($curl);

    curl_close($curl);
    echo $response;

    ```

=== "Powershell-RestMethod"
    ``` powershell
    $headers = New-Object "System.Collections.Generic.Dictionary[[String],[String]]"
    $headers.Add("x-device-type", "WEB")
    $headers.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg")
    $headers.Add("content-type", "application/json")

    $body = " {
    `n    `"basket_id`":`"<BasketId>`",
    `n    `"name`":`"<BasketName>`",
    `n    `"order_info`":
    `n {
    `n      `"exchange`":`"NSE`",
    `n      `"instrument_token`":3045,
    `n      `"client_id`":`"<ClientId>`",
    `n      `"order_type`":`"LIMIT`",
    `n      `"price`":506.5,
    `n      `"quantity`":1,
    `n      `"disclosed_quantity`":0,
    `n      `"validity`":`"DAY`",
    `n      `"product`":`"MIS`",
    `n      `"trading_symbol`":`"SBIN-EQ`",
    `n      `"order_side`":`"BUY`",
    `n      `"user_order_id`":10002,
    `n      `"underlying_token`":`"3045`",
    `n      `"series`":`"EQ`",
    `n      `"oms_order_id`":`"a5d13c1f-f99c-4230-ad19-9ed8e826ee74`",
    `n      `"exchange_order_id`":`"`",
    `n      `"trigger_price`":0,
    `n      `"stop_loss_value`":0,
    `n      `"square_off_value`":0,
    `n      `"trailing_stop_loss`":0,
    `n      `"is_trailing`":false,
    `n      `"execution_type`":`"BO`"
    `n },
    `n  `"order_id`":`"a5d13c1f-f99c-4230-ad19-9ed8e826ee74`"
    `n}"

    $response = Invoke-RestMethod 'https://pacetrader.pacefin.in/api/v1/basket/order' -Method 'PUT' -Headers $headers -Body $body
    $response | ConvertTo-Json

    ```



=== "R-httr"
    ``` r
    // You can also use other libraries such as `curl`, `resty`, etc..

    library(httr)

    headers = c(
    'x-device-type' = 'WEB',
    'x-authorization-token' = 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type' = 'application/json'
    )

    body = '{
    "basket_id": "<BasketId>",
    "name": "<BasketName>",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 506.5,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "trading_symbol": "SBIN-EQ",
        "order_side": "BUY",
        "user_order_id": 10002,
        "underlying_token": "3045",
        "series": "EQ",
        "oms_order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "exchange_order_id": "",
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    },
    "order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
    }';

    res <- VERB("PUT", url = "https://pacetrader.pacefin.in/api/v1/basket/order", body = body, add_headers(headers))

    cat(content(res, 'text'))

    ```


=== "Ruby - Net::HTTP"
    ``` ruby

    require "uri"
    require "json"
    require "net/http"

    url = URI("https://pacetrader.pacefin.in/api/v1/basket/order")

    https = Net::HTTP.new(url.host, url.port)
    https.use_ssl = true

    request = Net::HTTP::Put.new(url)
    request["x-device-type"] = "WEB"
    request["x-authorization-token"] = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
    request["content-type"] = "application/json"
    request.body = JSON.dump({
    "basket_id": "<BasketId>",
    "name": "<BasketName>",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 506.5,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "trading_symbol": "SBIN-EQ",
        "order_side": "BUY",
        "user_order_id": 10002,
        "underlying_token": "3045",
        "series": "EQ",
        "oms_order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "exchange_order_id": "",
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    },
    "order_id": "a5d13c1f-f99c-4230-ad19-9ed8e826ee74"
    })

    response = https.request(request)
    puts response.read_body


    ```

=== "Shell - httpie"
    ``` shell
    # You can also use other libraries such as `curl`, `wget`, etc..

    printf ' {
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
    }'| http  --follow --timeout 3600 PUT 'https://pacetrader.pacefin.in/api/v1/basket/order' \
    x-device-type:'WEB' \
    x-authorization-token:'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
    content-type:'application/json'

    ```

=== "Swift-URLSession"
    ```swift
    
    let parameters = " {\r\n    \"basket_id\":\"<BasketId>\",\r\n    \"name\":\"<BasketName>\",\r\n    \"order_info\":\r\n {\r\n      \"exchange\":\"NSE\",\r\n      \"instrument_token\":3045,\r\n      \"client_id\":\"<ClientId>\",\r\n      \"order_type\":\"LIMIT\",\r\n      \"price\":506.5,\r\n      \"quantity\":1,\r\n      \"disclosed_quantity\":0,\r\n      \"validity\":\"DAY\",\r\n      \"product\":\"MIS\",\r\n      \"trading_symbol\":\"SBIN-EQ\",\r\n      \"order_side\":\"BUY\",\r\n      \"user_order_id\":10002,\r\n      \"underlying_token\":\"3045\",\r\n      \"series\":\"EQ\",\r\n      \"oms_order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\",\r\n      \"exchange_order_id\":\"\",\r\n      \"trigger_price\":0,\r\n      \"stop_loss_value\":0,\r\n      \"square_off_value\":0,\r\n      \"trailing_stop_loss\":0,\r\n      \"is_trailing\":false,\r\n      \"execution_type\":\"BO\"\r\n },\r\n  \"order_id\":\"a5d13c1f-f99c-4230-ad19-9ed8e826ee74\"\r\n}"
    let postData = parameters.data(using: .utf8)

    var request = URLRequest(url: URL(string: "https://pacetrader.pacefin.in/api/v1/basket/order")!,timeoutInterval: Double.infinity)
    request.addValue("WEB", forHTTPHeaderField: "x-device-type")
    request.addValue("eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg", forHTTPHeaderField: "x-authorization-token")
    request.addValue("application/json", forHTTPHeaderField: "content-type")

    request.httpMethod = "PUT"
    request.httpBody = postData

    let task = URLSession.shared.dataTask(with: request) { data, response, error in 
    guard let data = data else {
        print(String(describing: error))
        return
    }
    print(String(data: data, encoding: .utf8)!)
    }

    task.resume()



    ```

