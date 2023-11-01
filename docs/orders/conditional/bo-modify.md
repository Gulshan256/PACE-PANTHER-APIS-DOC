# Modify a BO (Bracket Orders)

You can modify a BO order by changing its price or quantity. However, you cannot modify the order type or product type. To modify an order, you must first cancel it and then place a new order with the desired changes.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | modify order | https://pacetrader.pacefin.in/api/v1/orders/kart | Modify a BO order |

## Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token)`
content-type | application/json



## parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `instrument_token` | `integer` | The unique token identifying the trading instrument.|
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `float` | The price at which the order is placed.|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `validity` | `string` | The order validity type (Day, IOC).|
| `product` | `string` | The product code (MIS, CNC, NMRL).|
| `osm_order_id` | `string` | The unique order management system order identifier|
| `exchange_order_id` | `string` | The order identifier on the exchange.|
| `filled_quantity` | `integer` | The quantity of the order has been filled|
| `remaining_quantity` | `integer` | The remaining quantity to be filled.|
| `last_active_reference` | `integer` | The reference to the last activity related to the order.|
| `trigger_price` | `integer` | The trigger price for conditional orders|
| `stop_loss_vlaue` | `integer` | The stop loss value for the bracket order|
| `square_off_value` | `integer` | The square-off value for the bracket order|
| `trailing_stop_loss` | `integer` | The percentage or value for trailing stop loss|
| `is_trailing` | `bool` | A boolean flag (true or false) indicating whether the order include trailing stop loss|
| `excution_type` | `string` | The type of execution for the order (BO).|



## Request Body
```json
{
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
}
```

## Sucess Response
```json
{
    "status": "success",
    "message": "Order modified successfully",
    "data": {
        
    }
}
```

## Failed Response
```json
{
    "status": "failed",
    "message": "Order modification failed",
    "data": null
}
```



## Code Example


=== "python - http.client"
    ``` python
    # you an use any other module as well such as requests, urllib, etc.,

    import http.client
    import json

    conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
    payload = json.dumps({
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": False,
    "execution_type": "BO"
    })
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }
    conn.request("PUT", "/api/v1/orders/kart", payload, headers)
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
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
    });

    var requestOptions = {
    method: 'PUT',
    headers: myHeaders,
    body: raw,
    redirect: 'follow'
    };

    fetch("https://pacetrader.pacefin.in/api/v1/orders/kart", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
    
    ```


=== "C#"
    ``` csharp
    // You can also use other libraries such as RestSharp, etc..

    var client = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Put, "https://pacetrader.pacefin.in/api/v1/orders/kart");
    request.Headers.Add("x-device-type", "WEB");
    request.Headers.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    request.Headers.Add("content-type", "application/json");
    var content = new StringContent("{\r\n    \"exchange\": \"NSE\",\r\n    \"instrument_token\": 3045,\r\n    \"client_id\": \"<ClientId>\",\r\n    \"order_type\": \"LIMIT\",\r\n    \"price\": 456.95,\r\n    \"quantity\": 3,\r\n    \"disclosed_quantity\": 0,\r\n    \"validity\": \"DAY\",\r\n    \"product\": \"MIS\",\r\n    \"oms_order_id\": \"20220106-88\",\r\n    \"exchange_order_id\": \"1100000000004797\",\r\n    \"filled_quantity\": 0,\r\n    \"remaining_quantity\": 2,\r\n    \"last_activity_reference\": 1325938440097498600,\r\n    \"trigger_price\": 0,\r\n    \"stop_loss_value\": 0,\r\n    \"square_off_value\": 0,\r\n    \"trailing_stop_loss\": 0,\r\n    \"is_trailing\": false,\r\n    \"execution_type\": \"BO\"\r\n}", null, "application/json");
    request.Content = content;
    var response = await client.SendAsync(request);
    response.EnsureSuccessStatusCode();
    Console.WriteLine(await response.Content.ReadAsStringAsync());


    ```

=== "cURL"
    ``` bash
    curl --location --request PUT 'https://pacetrader.pacefin.in/api/v1/orders/kart' \
    --header 'x-device-type: WEB' \
    --header 'x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
    --header 'content-type: application/json' \
    --data '{
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 456.95,
        "quantity": 3,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "20220106-88",
        "exchange_order_id": "1100000000004797",
        "filled_quantity": 0,
        "remaining_quantity": 2,
        "last_activity_reference": 1325938440097498600,
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    }'

    ```

=== "Dart"
    ``` dart

    var headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    };
    var request = http.Request('PUT', Uri.parse('https://pacetrader.pacefin.in/api/v1/orders/kart'));
    request.body = json.encode({
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
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

=== "Go"
    ``` go
    package main

    import (
    "fmt"
    "strings"
    "net/http"
    "io/ioutil"
    )

    func main() {

    url := "https://pacetrader.pacefin.in/api/v1/orders/kart"
    method := "PUT"

    payload := strings.NewReader(`{`+"
    "+`
        "exchange": "NSE",`+"
    "+`
        "instrument_token": 3045,`+"
    "+`
        "client_id": "<ClientId>",`+"
    "+`
        "order_type": "LIMIT",`+"
    "+`
        "price": 456.95,`+"
    "+`
        "quantity": 3,`+"
    "+`
        "disclosed_quantity": 0,`+"
    "+`
        "validity": "DAY",`+"
    "+`
        "product": "MIS",`+"
    "+`
        "oms_order_id": "20220106-88",`+"
    "+`
        "exchange_order_id": "1100000000004797",`+"
    "+`
        "filled_quantity": 0,`+"
    "+`
        "remaining_quantity": 2,`+"
    "+`
        "last_activity_reference": 1325938440097498600,`+"
    "+`
        "trigger_price": 0,`+"
    "+`
        "stop_loss_value": 0,`+"
    "+`
        "square_off_value": 0,`+"
    "+`
        "trailing_stop_loss": 0,`+"
    "+`
        "is_trailing": false,`+"
    "+`
        "execution_type": "BO"`+"
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
    PUT /api/v1/orders/kart HTTP/1.1
    Host: pacetrader.pacefin.in
    x-device-type: WEB
    x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg
    content-type: application/json
    Content-Length: 595

    {
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 456.95,
        "quantity": 3,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "20220106-88",
        "exchange_order_id": "1100000000004797",
        "filled_quantity": 0,
        "remaining_quantity": 2,
        "last_activity_reference": 1325938440097498600,
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
    }
        
    ```

=== "Java"
    ``` java
    // You can also use other libraries such as Unirest, etc..

    OkHttpClient client = new OkHttpClient().newBuilder()
    .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "{\r\n    \"exchange\": \"NSE\",\r\n    \"instrument_token\": 3045,\r\n    \"client_id\": \"<ClientId>\",\r\n    \"order_type\": \"LIMIT\",\r\n    \"price\": 456.95,\r\n    \"quantity\": 3,\r\n    \"disclosed_quantity\": 0,\r\n    \"validity\": \"DAY\",\r\n    \"product\": \"MIS\",\r\n    \"oms_order_id\": \"20220106-88\",\r\n    \"exchange_order_id\": \"1100000000004797\",\r\n    \"filled_quantity\": 0,\r\n    \"remaining_quantity\": 2,\r\n    \"last_activity_reference\": 1325938440097498600,\r\n    \"trigger_price\": 0,\r\n    \"stop_loss_value\": 0,\r\n    \"square_off_value\": 0,\r\n    \"trailing_stop_loss\": 0,\r\n    \"is_trailing\": false,\r\n    \"execution_type\": \"BO\"\r\n}");
    Request request = new Request.Builder()
    .url("https://pacetrader.pacefin.in/api/v1/orders/kart")
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
    curl_easy_setopt(curl, CURLOPT_URL, "https://pacetrader.pacefin.in/api/v1/orders/kart");
    curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
    curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
    struct curl_slist *headers = NULL;
    headers = curl_slist_append(headers, "x-device-type: WEB");
    headers = curl_slist_append(headers, "x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    headers = curl_slist_append(headers, "content-type: application/json");
    curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
    const char *data = "{\r\n    \"exchange\": \"NSE\",\r\n    \"instrument_token\": 3045,\r\n    \"client_id\": \"<ClientId>\",\r\n    \"order_type\": \"LIMIT\",\r\n    \"price\": 456.95,\r\n    \"quantity\": 3,\r\n    \"disclosed_quantity\": 0,\r\n    \"validity\": \"DAY\",\r\n    \"product\": \"MIS\",\r\n    \"oms_order_id\": \"20220106-88\",\r\n    \"exchange_order_id\": \"1100000000004797\",\r\n    \"filled_quantity\": 0,\r\n    \"remaining_quantity\": 2,\r\n    \"last_activity_reference\": 1325938440097498600,\r\n    \"trigger_price\": 0,\r\n    \"stop_loss_value\": 0,\r\n    \"square_off_value\": 0,\r\n    \"trailing_stop_loss\": 0,\r\n    \"is_trailing\": false,\r\n    \"execution_type\": \"BO\"\r\n}";
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
    'path': '/api/v1/orders/kart',
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
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
    });

    req.write(postData);

    req.end();

    ```


=== "Objective-C - NSURLSession"
    ``` objective-c
    #import <Foundation/Foundation.h>

    dispatch_semaphore_t sema = dispatch_semaphore_create(0);

    NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://pacetrader.pacefin.in/api/v1/orders/kart"]
    cachePolicy:NSURLRequestUseProtocolCachePolicy
    timeoutInterval:10.0];
    NSDictionary *headers = @{
    @"x-device-type": @"WEB",
    @"x-authorization-token": @"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg",
    @"content-type": @"application/json"
    };

    [request setAllHTTPHeaderFields:headers];
    NSData *postData = [[NSData alloc] initWithData:[@"{\r\n    \"exchange\": \"NSE\",\r\n    \"instrument_token\": 3045,\r\n    \"client_id\": \"<ClientId>\",\r\n    \"order_type\": \"LIMIT\",\r\n    \"price\": 456.95,\r\n    \"quantity\": 3,\r\n    \"disclosed_quantity\": 0,\r\n    \"validity\": \"DAY\",\r\n    \"product\": \"MIS\",\r\n    \"oms_order_id\": \"20220106-88\",\r\n    \"exchange_order_id\": \"1100000000004797\",\r\n    \"filled_quantity\": 0,\r\n    \"remaining_quantity\": 2,\r\n    \"last_activity_reference\": 1325938440097498600,\r\n    \"trigger_price\": 0,\r\n    \"stop_loss_value\": 0,\r\n    \"square_off_value\": 0,\r\n    \"trailing_stop_loss\": 0,\r\n    \"is_trailing\": false,\r\n    \"execution_type\": \"BO\"\r\n}" dataUsingEncoding:NSUTF8StringEncoding]];
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

    let postData = ref "{\r\n    \"exchange\": \"NSE\",\r\n    \"instrument_token\": 3045,\r\n    \"client_id\": \"<ClientId>\",\r\n    \"order_type\": \"LIMIT\",\r\n    \"price\": 456.95,\r\n    \"quantity\": 3,\r\n    \"disclosed_quantity\": 0,\r\n    \"validity\": \"DAY\",\r\n    \"product\": \"MIS\",\r\n    \"oms_order_id\": \"20220106-88\",\r\n    \"exchange_order_id\": \"1100000000004797\",\r\n    \"filled_quantity\": 0,\r\n    \"remaining_quantity\": 2,\r\n    \"last_activity_reference\": 1325938440097498600,\r\n    \"trigger_price\": 0,\r\n    \"stop_loss_value\": 0,\r\n    \"square_off_value\": 0,\r\n    \"trailing_stop_loss\": 0,\r\n    \"is_trailing\": false,\r\n    \"execution_type\": \"BO\"\r\n}";;

    let reqBody = 
    let uri = Uri.of_string "https://pacetrader.pacefin.in/api/v1/orders/kart" in
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
    CURLOPT_URL => 'https://pacetrader.pacefin.in/api/v1/orders/kart',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_ENCODING => '',
    CURLOPT_MAXREDIRS => 10,
    CURLOPT_TIMEOUT => 0,
    CURLOPT_FOLLOWLOCATION => true,
    CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
    CURLOPT_CUSTOMREQUEST => 'PUT',
    CURLOPT_POSTFIELDS =>'{
        "exchange": "NSE",
        "instrument_token": 3045,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 456.95,
        "quantity": 3,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "20220106-88",
        "exchange_order_id": "1100000000004797",
        "filled_quantity": 0,
        "remaining_quantity": 2,
        "last_activity_reference": 1325938440097498600,
        "trigger_price": 0,
        "stop_loss_value": 0,
        "square_off_value": 0,
        "trailing_stop_loss": 0,
        "is_trailing": false,
        "execution_type": "BO"
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

    $body = "{
    `n    `"exchange`": `"NSE`",
    `n    `"instrument_token`": 3045,
    `n    `"client_id`": `"<ClientId>`",
    `n    `"order_type`": `"LIMIT`",
    `n    `"price`": 456.95,
    `n    `"quantity`": 3,
    `n    `"disclosed_quantity`": 0,
    `n    `"validity`": `"DAY`",
    `n    `"product`": `"MIS`",
    `n    `"oms_order_id`": `"20220106-88`",
    `n    `"exchange_order_id`": `"1100000000004797`",
    `n    `"filled_quantity`": 0,
    `n    `"remaining_quantity`": 2,
    `n    `"last_activity_reference`": 1325938440097498600,
    `n    `"trigger_price`": 0,
    `n    `"stop_loss_value`": 0,
    `n    `"square_off_value`": 0,
    `n    `"trailing_stop_loss`": 0,
    `n    `"is_trailing`": false,
    `n    `"execution_type`": `"BO`"
    `n}"

    $response = Invoke-RestMethod 'https://pacetrader.pacefin.in/api/v1/orders/kart' -Method 'PUT' -Headers $headers -Body $body
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
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
    }';

    res <- VERB("PUT", url = "https://pacetrader.pacefin.in/api/v1/orders/kart", body = body, add_headers(headers))

    cat(content(res, 'text'))

    ```


=== "Ruby - Net::HTTP"
    ``` ruby

    require "uri"
    require "json"
    require "net/http"

    url = URI("https://pacetrader.pacefin.in/api/v1/orders/kart")

    https = Net::HTTP.new(url.host, url.port)
    https.use_ssl = true

    request = Net::HTTP::Put.new(url)
    request["x-device-type"] = "WEB"
    request["x-authorization-token"] = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
    request["content-type"] = "application/json"
    request.body = JSON.dump({
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
    })

    response = https.request(request)
    puts response.read_body

    ```

=== "Shell - httpie"
    ``` shell
    # You can also use other libraries such as `curl`, `wget`, etc..

    printf '{
    "exchange": "NSE",
    "instrument_token": 3045,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 456.95,
    "quantity": 3,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "20220106-88",
    "exchange_order_id": "1100000000004797",
    "filled_quantity": 0,
    "remaining_quantity": 2,
    "last_activity_reference": 1325938440097498600,
    "trigger_price": 0,
    "stop_loss_value": 0,
    "square_off_value": 0,
    "trailing_stop_loss": 0,
    "is_trailing": false,
    "execution_type": "BO"
    }'| http  --follow --timeout 3600 PUT 'https://pacetrader.pacefin.in/api/v1/orders/kart' \
    x-device-type:'WEB' \
    x-authorization-token:'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
    content-type:'application/json'

    ```

=== "Swift-URLSession"
    ```swift
    
    let parameters = "{\r\n    \"exchange\": \"NSE\",\r\n    \"instrument_token\": 3045,\r\n    \"client_id\": \"<ClientId>\",\r\n    \"order_type\": \"LIMIT\",\r\n    \"price\": 456.95,\r\n    \"quantity\": 3,\r\n    \"disclosed_quantity\": 0,\r\n    \"validity\": \"DAY\",\r\n    \"product\": \"MIS\",\r\n    \"oms_order_id\": \"20220106-88\",\r\n    \"exchange_order_id\": \"1100000000004797\",\r\n    \"filled_quantity\": 0,\r\n    \"remaining_quantity\": 2,\r\n    \"last_activity_reference\": 1325938440097498600,\r\n    \"trigger_price\": 0,\r\n    \"stop_loss_value\": 0,\r\n    \"square_off_value\": 0,\r\n    \"trailing_stop_loss\": 0,\r\n    \"is_trailing\": false,\r\n    \"execution_type\": \"BO\"\r\n}"
    let postData = parameters.data(using: .utf8)

    var request = URLRequest(url: URL(string: "https://pacetrader.pacefin.in/api/v1/orders/kart")!,timeoutInterval: Double.infinity)
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