## Scrip Info
Allows user to search equities, commodities, etc., and shows them the information available for these.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET `         | `Scrip Info`    | https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity> | Get scrip info of an instrument |


### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json



string -->

### Request Parameters
| Parameter | Type | Description |
| --------- | ---- | ----------- |
| info | string | scrip |
| token | string | <InstrumentTokenOfEquity> |



### Request Body
```json
{
    "info": "scrip",
    "token": "<InstrumentTokenOfEquity>"
}
```

# response
```json
{
    "result":{
        "board_lot_quantity": 1,
        "change_in_oi": 0,
        "exchange": 1,
        "expiry": 0,
        "higher_circuit_limit": 32.8,
        "instrument_name": "EQ",
        "instrument_token": 10666,
        "isin": "INE160A01022",
        "lower_circuit_limit": 26.9,
        "multiplier": 1,
        "open_interest": 0,
        "option_type": "",
        "precision": 2,
        "series": "EQ",
        "strike": 0,
        "symbol": "PNB",
        "tick_size": 0.05,
        "trading_symbol": "PNB-EQ",
        "underlying_token": 10666,
        "raw_expiry": 0,
        "freeze": 355,
        "instrument_type": "0",
        "issue_rate": 0,
        "issue_start_date": "25-Apr-2002",
        "list_date": "25-Apr-2002",
        "max_order_size": 0,
        "price_numerator": 0,
        "price_denominator": 0,
        "comments": "ANNUAL GENERAL MEETING",
        "circuit_rating": "",
        "company_name": "PUNJAB NATIONAL BANK",
        "display_name": "PNB EQ",
        "raw_tick_size": 5,
        "is_index": false,
        "tradable": true,
        "max_single_qty": 0,
        "expiry_string": "",
        "local_update_time": "",
        "market_type": "",
        "price_units": "",
        "trading_units": "",
        "last_trading_date": "",
        "tender_period_end_date": "",
        "delivery_start_date": "",
        "price_quotation": 0,
        "general_denominator": "",
        "tender_period_start_date": "",
        "delivery_units": "",
        "delivery_end_date": "",
        "trading_unit_factor": 0,
        "delivery_unit_factor": 0,
        "book_closure_end_date": "3-Aug-2020",
        "book_closure_start_date": "28-Jul-2020",
        "no_delivery_date_end": "0",
        "no_delivery_date_start": "0",
        "re_admission_date": "0",
        "record_date": "0",
        "warning": "0",
        "dpr": "26.9000 - 32.8000",
        "trade_to_trade": false,
        "surveillance_indicator": 0,
        "partition_id": 0,
        "product_id": 0,
        "product_category": "",
        "month_identifier": 0
    }
    "error":{
        "code": 0,
        "message": ""
    }
}
```


### Error Response
```json 
{
    "error":{
        "code": 404,
        "message": "Resource Not Found"
    }
    "result": ""
}
```


____________________________________________________________________________________________________________________

### Code Examples

=== "python - http.client"
    ``` python
    # you an use any other module as well such as requests, urllib, etc.,
    import http.client
    import json

    conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
    payload = ''
    headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    }
    conn.request("GET", "/api/v1/contract/<Exchange>?info=scrip&token=%3CInstrumentTokenOfEquity%3E", payload, headers)
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

    var requestOptions = {
    method: 'GET',
    headers: myHeaders,
    redirect: 'follow'
    };

    fetch("https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>", requestOptions)
    .then(response => response.text())
    .then(result => console.log(result))
    .catch(error => console.log('error', error));
        
    ```

=== "C#"
    ``` csharp
    // You can also use other libraries such as RestSharp, etc..

    var client = new HttpClient();
    var request = new HttpRequestMessage(HttpMethod.Get, "https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>");
    request.Headers.Add("x-device-type", "WEB");
    request.Headers.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    request.Headers.Add("content-type", "application/json");
    var content = new StringContent(string.Empty);
    content.Headers.ContentType = new MediaTypeHeaderValue("application/json");
    request.Content = content;
    var response = await client.SendAsync(request);
    response.EnsureSuccessStatusCode();
    Console.WriteLine(await response.Content.ReadAsStringAsync());


    ```

=== "cURL"
    ``` bash
    curl --location 'https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=%3CInstrumentTokenOfEquity%3E' \
    --header 'x-device-type: WEB' \
    --header 'x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
    --header 'content-type: application/json'

    ```

=== "Dart"
    ``` dart

    var headers = {
    'x-device-type': 'WEB',
    'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
    'content-type': 'application/json'
    };
    var request = http.Request('GET', Uri.parse('https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>'));

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
    "net/http"
    "io/ioutil"
    )

    func main() {

    url := "https://pacetrader.pacefin.in/api/v1/contract/%3CExchange%3E?info=scrip&token=%3CInstrumentTokenOfEquity%3E"
    method := "GET"

    client := &http.Client {
    }
    req, err := http.NewRequest(method, url, nil)

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
    GET /api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity> HTTP/1.1
    Host: pacetrader.pacefin.in
    x-device-type: WEB
    x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg
    content-type: application/json
        
    ```


=== "Java"
    ``` java
    // You can also use other libraries such as Unirest, etc..

    OkHttpClient client = new OkHttpClient().newBuilder()
    .build();
    MediaType mediaType = MediaType.parse("application/json");
    RequestBody body = RequestBody.create(mediaType, "");
    Request request = new Request.Builder()
    .url("https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>")
    .method("GET", body)
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
    curl_easy_setopt(curl, CURLOPT_CUSTOMREQUEST, "GET");
    curl_easy_setopt(curl, CURLOPT_URL, "https://pacetrader.pacefin.in/api/v1/contract/%3CExchange%3E?info=scrip&token=%3CInstrumentTokenOfEquity%3E");
    curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
    curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
    struct curl_slist *headers = NULL;
    headers = curl_slist_append(headers, "x-device-type: WEB");
    headers = curl_slist_append(headers, "x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
    headers = curl_slist_append(headers, "content-type: application/json");
    curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
    res = curl_easy_perform(curl);
    }
    curl_easy_cleanup(curl);

    ```

=== "node.js - Native"
    ``` javascript
    // You can also use other libraries such as `axios`,`jQuery`, `request` `Unirest`, etc.. this example uses `node.js` native`

    var axios = require('axios');

    var config = {
    method: 'get',
    maxBodyLength: Infinity,
    url: 'https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>',
    headers: { 
        'x-device-type': 'WEB', 
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg', 
        'content-type': 'application/json'
    }
    };

    axios(config)
    .then(function (response) {
    console.log(JSON.stringify(response.data));
    })
    .catch(function (error) {
    console.log(error);
    });

    ```

=== "Objective-C - NSURLSession"
    ``` objective-c
    #import <Foundation/Foundation.h>

    dispatch_semaphore_t sema = dispatch_semaphore_create(0);

    NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://pacetrader.pacefin.in/api/v1/contract/%3CExchange%3E?info=scrip&token=%3CInstrumentTokenOfEquity%3E"]
    cachePolicy:NSURLRequestUseProtocolCachePolicy
    timeoutInterval:10.0];
    NSDictionary *headers = @{
    @"x-device-type": @"WEB",
    @"x-authorization-token": @"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg",
    @"content-type": @"application/json"
    };

    [request setAllHTTPHeaderFields:headers];

    [request setHTTPMethod:@"GET"];

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

    let reqBody = 
    let uri = Uri.of_string "https://pacetrader.pacefin.in/api/v1/contract/%3CExchange%3E?info=scrip&token=%3CInstrumentTokenOfEquity%3E" in
    let headers = Header.init ()
        |> fun h -> Header.add h "x-device-type" "WEB"
        |> fun h -> Header.add h "x-authorization-token" "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
        |> fun h -> Header.add h "content-type" "application/json"
    in
    Client.call ~headers `GET uri >>= fun (_resp, body) ->
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
    CURLOPT_URL => 'https://pacetrader.pacefin.in/api/v1/contract/%3CExchange%3E?info=scrip&token=%3CInstrumentTokenOfEquity%3E',
    CURLOPT_RETURNTRANSFER => true,
    CURLOPT_ENCODING => '',
    CURLOPT_MAXREDIRS => 10,
    CURLOPT_TIMEOUT => 0,
    CURLOPT_FOLLOWLOCATION => true,
    CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
    CURLOPT_CUSTOMREQUEST => 'GET',
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

    $response = Invoke-RestMethod 'https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>' -Method 'GET' -Headers $headers
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

    res <- VERB("GET", url = "https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>", add_headers(headers))

    cat(content(res, 'text'))

    ```

=== "Ruby - Net::HTTP"
    ``` ruby
    require "uri"
    require "json"
    require "net/http"

    url = URI("https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>")

    https = Net::HTTP.new(url.host, url.port)
    https.use_ssl = true

    request = Net::HTTP::Get.new(url)
    request["x-device-type"] = "WEB"
    request["x-authorization-token"] = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
    request["content-type"] = "application/json"

    response = https.request(request)
    puts response.read_body

    ```

=== "Shell - httpie"
    ``` shell
    # You can also use other libraries such as `curl`, `wget`, etc..

    http --follow --timeout 3600 GET 'https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=<InstrumentTokenOfEquity>' \
    x-device-type:'WEB' \
    x-authorization-token:'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
    content-type:'application/json'
    ```

=== "Swift-URLSession"
    ```swift
    var request = URLRequest(url: URL(string: "https://pacetrader.pacefin.in/api/v1/contract/<Exchange>?info=scrip&token=%3CInstrumentTokenOfEquity%3E")!,timeoutInterval: Double.infinity)
    request.addValue("WEB", forHTTPHeaderField: "x-device-type")
    request.addValue("eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg", forHTTPHeaderField: "x-authorization-token")
    request.addValue("application/json", forHTTPHeaderField: "content-type")

    request.httpMethod = "GET"

    let task = URLSession.shared.dataTask(with: request) { data, response, error in 
    guard let data = data else {
        print(String(describing: error))
        return
    }
    print(String(data: data, encoding: .utf8)!)
    }

    task.resume()

    ```
    