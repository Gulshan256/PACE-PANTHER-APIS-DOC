# Add basket Instrument
This API used to add Instrument in the created baskets. We can add only limited number of instruments in the basket and repeated instrument can't be added.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | basket order | https://pacetrader.pacefin.in/api/v1/basket/order | Add an instrument to a basket order |

## Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | multipart/form-data |


## parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `basket_id` | `string` | The unique identifier of the basket order.|
| `name` | `string` | The name of the basket order.|
| `order_info` | `object` | The details of the order.|
| `order_info.exchange` | `string` | The exchange of the instrument.|
| `order_info.instrument_token` | `string` | The unique identifier of the instrument.|
| `order_info.client_id` | `string` | Your unique client identifier for the order.|
| `order_info.order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `order_info.price` | `integer` | The price of the order.|
| `client_id` | `string` | Your unique client identifier for the order.|
| `device` | `string` | The device type for the order (WEB, MOBILE).|
| `disclosed_quantity` | `integer` | The disclosed quantity of the order.|
| `exchange` | `string` | The exchange of the instrument.|
| `execution_type` | `string` | The execution type for the order (REGULAR, SPECIAL).|
| `instrument_token` | `string` | The unique identifier of the instrument.|
| `order_side` | `string` | The order side for the order (BUY, SELL).|
| `order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `price` | `integer` | The price of the order.|
| `product` | `string` | The product type for the order (CNC, MIS, NRML).|
| `quantity` | `integer` | The quantity of the order.|
| `series` | `string` | The series of the instrument.|
| `trading_symbol` | `string` | The trading symbol of the instrument.|
| `trigger_price` | `integer` | The trigger price of the order.|
| `underlying_token` | `string` | The unique identifier of the instrument.|
| `user_order_id` | `integer` | The unique identifier of the order.|
| `validity` | `string` | The validity of the order (DAY, IOC).|


## Request Body
```json

{
    "basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
    "name": "Demo",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": "3045",
        "client_id": "NA003",
        "order_type": "MARKET",
        "price": 0
    },
    "client_id": "NA003",
    "device": "WEB",
    "disclosed_quantity": 0,
    "exchange": "NSE",
    "execution_type": "REGULAR",
    "instrument_token": "3045",
    "order_side": "BUY",
    "order_type": "MARKET",
    "price": 0,
    "product": "MIS",
    "quantity": 1,
    "series": "EQ",
    "trading_symbol": "SBIN-EQ",
    "trigger_price": 0,
    "underlying_token": "3045",
    "user_order_id": 10002,
    "validity": "DAY"
}
```

## Response
```json
{
  "data":{
      "basket_id":"72fa28f8-7c08-4a4d-ba7a-fedd461744a1",
      "basket_type":"NORMAL",
      "login_id":"DEMO1",
      "name":"h",
      "order_type":"ALL",
  "orders":[
     {
        "order_id":"a5d13c1f-f99c-4230-ad19-9ed8e826ee74",
        "order_info":{
           "sl_trigger_price":0.0,
           "spread_token":null,
           "exchange_time":0,
           "last_activity_reference":0,
           "exchange":"NSE",
           "target_price_type":"absolute",
           "leg_order_indicator":null,
           "mode":"NEW",
           "average_price":0,
           "trigger_price":0,
           "sl_order_quantity":0,
           "deposit":0,
           "order_type":"LIMIT",
           "is_trailing":false,
           "product":"MIS",
           "trailing_stop_loss":0.0,
           "underlying_token":"3045",
           "user_order_id":10002,
           "rejection_code":0,
           "order_tag":"",
           "filled_quantity":0,
           "quantity":1,
           "trade_price":0,
           "client_id":"DEMO1",
           "average_trade_price":0,
           "trading_symbol":"SBIN-EQ",
           "series":"",
           "lot_size":0,
           "disclosed_quantity":0,
           "instrument_token":3045,
           "pro_cli":"CLIENT",
           "contract_description":{

           },
           "validity":"DAY",
           "remaining_quantity":0,
           "rejection_reason":"",
           "segment":"",
           "price":506.5,
           "market_protection_percentage":0,
           "stop_loss_value":0.0,
           "nnf_id":0,
           "order_status_info":"",
           "login_id":null,
           "sl_order_price":0.0,
           "execution_type":"BO",
           "square_off_value":0.0,
           "order_side":"BUY",
           "order_entry_time":0,
           "exchange_order_id":"",
           "device":null,
           "oms_order_id":"",
           "order_status":null,
           "square_off":false
        }
     }
  ],
  "product_type":"ALL"
 },
  "message":"Order added in the basket h.",
  "status":"success"
 }
```

## Error Response
```json
{
     "data": {},
     "error_code": 46001,
     "message": "Instrumetn already added",
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
	"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
	"name": "Demo",
	"order_info": {
		"exchange": "NSE",
		"instrument_token": "3045",
		"client_id": "NA003",
		"order_type": "MARKET",
		"price": 0
	},
	"client_id": "NA003",
	"device": "WEB",
	"disclosed_quantity": 0,
	"exchange": "NSE",
	"execution_type": "REGULAR",
	"instrument_token": "3045",
	"order_side": "BUY",
	"order_type": "MARKET",
	"price": 0,
	"product": "MIS",
	"quantity": 1,
	"series": "EQ",
	"trading_symbol": "SBIN-EQ",
	"trigger_price": 0,
	"underlying_token": "3045",
	"user_order_id": 10002,
	"validity": "DAY"
	})
	headers = {
	'x-device-type': 'WEB',
	'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
	'content-type': 'application/json'
	}
	conn.request("POST", "/api/v1/basket/order", payload, headers)
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
	"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
	"name": "Demo",
	"order_info": {
		"exchange": "NSE",
		"instrument_token": "3045",
		"client_id": "NA003",
		"order_type": "MARKET",
		"price": 0
	},
	"client_id": "NA003",
	"device": "WEB",
	"disclosed_quantity": 0,
	"exchange": "NSE",
	"execution_type": "REGULAR",
	"instrument_token": "3045",
	"order_side": "BUY",
	"order_type": "MARKET",
	"price": 0,
	"product": "MIS",
	"quantity": 1,
	"series": "EQ",
	"trading_symbol": "SBIN-EQ",
	"trigger_price": 0,
	"underlying_token": "3045",
	"user_order_id": 10002,
	"validity": "DAY"
	});

	var requestOptions = {
	method: 'POST',
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
	var request = new HttpRequestMessage(HttpMethod.Post, "https://pacetrader.pacefin.in/api/v1/basket/order");
	request.Headers.Add("x-device-type", "WEB");
	request.Headers.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
	request.Headers.Add("content-type", "application/json");
	var content = new StringContent("{\r\n    \"basket_id\": \"0786e757-2e8f-44b2-9559-deeac2e00114\",\r\n    \"name\": \"Demo\",\r\n    \"order_info\": {\r\n        \"exchange\": \"NSE\",\r\n        \"instrument_token\": \"3045\",\r\n        \"client_id\": \"NA003\",\r\n        \"order_type\": \"MARKET\",\r\n        \"price\": 0\r\n    },\r\n    \"client_id\": \"NA003\",\r\n    \"device\": \"WEB\",\r\n    \"disclosed_quantity\": 0,\r\n    \"exchange\": \"NSE\",\r\n    \"execution_type\": \"REGULAR\",\r\n    \"instrument_token\": \"3045\",\r\n    \"order_side\": \"BUY\",\r\n    \"order_type\": \"MARKET\",\r\n    \"price\": 0,\r\n    \"product\": \"MIS\",\r\n    \"quantity\": 1,\r\n    \"series\": \"EQ\",\r\n    \"trading_symbol\": \"SBIN-EQ\",\r\n    \"trigger_price\": 0,\r\n    \"underlying_token\": \"3045\",\r\n    \"user_order_id\": 10002,\r\n    \"validity\": \"DAY\"\r\n}", null, "application/json");
	request.Content = content;
	var response = await client.SendAsync(request);
	response.EnsureSuccessStatusCode();
	Console.WriteLine(await response.Content.ReadAsStringAsync());



    ```

=== "cURL"
    ``` bash
    curl --location 'https://pacetrader.pacefin.in/api/v1/basket/order' \
	--header 'x-device-type: WEB' \
	--header 'x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
	--header 'content-type: application/json' \
	--data '{
		"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
		"name": "Demo",
		"order_info": {
			"exchange": "NSE",
			"instrument_token": "3045",
			"client_id": "NA003",
			"order_type": "MARKET",
			"price": 0
		},
		"client_id": "NA003",
		"device": "WEB",
		"disclosed_quantity": 0,
		"exchange": "NSE",
		"execution_type": "REGULAR",
		"instrument_token": "3045",
		"order_side": "BUY",
		"order_type": "MARKET",
		"price": 0,
		"product": "MIS",
		"quantity": 1,
		"series": "EQ",
		"trading_symbol": "SBIN-EQ",
		"trigger_price": 0,
		"underlying_token": "3045",
		"user_order_id": 10002,
		"validity": "DAY"
	}'
    ```

=== "Dart"
    ``` dart

    var headers = {
	'x-device-type': 'WEB',
	'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
	'content-type': 'application/json'
	};
	var request = http.Request('POST', Uri.parse('https://pacetrader.pacefin.in/api/v1/basket/order'));
	request.body = json.encode({
	"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
	"name": "Demo",
	"order_info": {
		"exchange": "NSE",
		"instrument_token": "3045",
		"client_id": "NA003",
		"order_type": "MARKET",
		"price": 0
	},
	"client_id": "NA003",
	"device": "WEB",
	"disclosed_quantity": 0,
	"exchange": "NSE",
	"execution_type": "REGULAR",
	"instrument_token": "3045",
	"order_side": "BUY",
	"order_type": "MARKET",
	"price": 0,
	"product": "MIS",
	"quantity": 1,
	"series": "EQ",
	"trading_symbol": "SBIN-EQ",
	"trigger_price": 0,
	"underlying_token": "3045",
	"user_order_id": 10002,
	"validity": "DAY"
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
	method := "POST"

	payload := strings.NewReader(`{`+"
	"+`
		"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",`+"
	"+`
		"name": "Demo",`+"
	"+`
		"order_info": {`+"
	"+`
			"exchange": "NSE",`+"
	"+`
			"instrument_token": "3045",`+"
	"+`
			"client_id": "NA003",`+"
	"+`
			"order_type": "MARKET",`+"
	"+`
			"price": 0`+"
	"+`
		},`+"
	"+`
		"client_id": "NA003",`+"
	"+`
		"device": "WEB",`+"
	"+`
		"disclosed_quantity": 0,`+"
	"+`
		"exchange": "NSE",`+"
	"+`
		"execution_type": "REGULAR",`+"
	"+`
		"instrument_token": "3045",`+"
	"+`
		"order_side": "BUY",`+"
	"+`
		"order_type": "MARKET",`+"
	"+`
		"price": 0,`+"
	"+`
		"product": "MIS",`+"
	"+`
		"quantity": 1,`+"
	"+`
		"series": "EQ",`+"
	"+`
		"trading_symbol": "SBIN-EQ",`+"
	"+`
		"trigger_price": 0,`+"
	"+`
		"underlying_token": "3045",`+"
	"+`
		"user_order_id": 10002,`+"
	"+`
		"validity": "DAY"`+"
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
    POST /api/v1/basket/order HTTP/1.1
	Host: pacetrader.pacefin.in
	x-device-type: WEB
	x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg
	content-type: application/json
	Content-Length: 711

	{
		"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
		"name": "Demo",
		"order_info": {
			"exchange": "NSE",
			"instrument_token": "3045",
			"client_id": "NA003",
			"order_type": "MARKET",
			"price": 0
		},
		"client_id": "NA003",
		"device": "WEB",
		"disclosed_quantity": 0,
		"exchange": "NSE",
		"execution_type": "REGULAR",
		"instrument_token": "3045",
		"order_side": "BUY",
		"order_type": "MARKET",
		"price": 0,
		"product": "MIS",
		"quantity": 1,
		"series": "EQ",
		"trading_symbol": "SBIN-EQ",
		"trigger_price": 0,
		"underlying_token": "3045",
		"user_order_id": 10002,
		"validity": "DAY"
	}
        
    ```

=== "Java-OkHttp"
    ``` java
    // You can also use other libraries such as Unirest, etc..

    OkHttpClient client = new OkHttpClient().newBuilder()
	.build();
	MediaType mediaType = MediaType.parse("application/json");
	RequestBody body = RequestBody.create(mediaType, "{\r\n    \"basket_id\": \"0786e757-2e8f-44b2-9559-deeac2e00114\",\r\n    \"name\": \"Demo\",\r\n    \"order_info\": {\r\n        \"exchange\": \"NSE\",\r\n        \"instrument_token\": \"3045\",\r\n        \"client_id\": \"NA003\",\r\n        \"order_type\": \"MARKET\",\r\n        \"price\": 0\r\n    },\r\n    \"client_id\": \"NA003\",\r\n    \"device\": \"WEB\",\r\n    \"disclosed_quantity\": 0,\r\n    \"exchange\": \"NSE\",\r\n    \"execution_type\": \"REGULAR\",\r\n    \"instrument_token\": \"3045\",\r\n    \"order_side\": \"BUY\",\r\n    \"order_type\": \"MARKET\",\r\n    \"price\": 0,\r\n    \"product\": \"MIS\",\r\n    \"quantity\": 1,\r\n    \"series\": \"EQ\",\r\n    \"trading_symbol\": \"SBIN-EQ\",\r\n    \"trigger_price\": 0,\r\n    \"underlying_token\": \"3045\",\r\n    \"user_order_id\": 10002,\r\n    \"validity\": \"DAY\"\r\n}");
	Request request = new Request.Builder()
	.url("https://pacetrader.pacefin.in/api/v1/basket/order")
	.method("POST", body)
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
	curl_easy_setopt(curl, CURLOPT_CUSTOMREQUEST, "POST");
	curl_easy_setopt(curl, CURLOPT_URL, "https://pacetrader.pacefin.in/api/v1/basket/order");
	curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
	curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
	struct curl_slist *headers = NULL;
	headers = curl_slist_append(headers, "x-device-type: WEB");
	headers = curl_slist_append(headers, "x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
	headers = curl_slist_append(headers, "content-type: application/json");
	curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
	const char *data = "{\r\n    \"basket_id\": \"0786e757-2e8f-44b2-9559-deeac2e00114\",\r\n    \"name\": \"Demo\",\r\n    \"order_info\": {\r\n        \"exchange\": \"NSE\",\r\n        \"instrument_token\": \"3045\",\r\n        \"client_id\": \"NA003\",\r\n        \"order_type\": \"MARKET\",\r\n        \"price\": 0\r\n    },\r\n    \"client_id\": \"NA003\",\r\n    \"device\": \"WEB\",\r\n    \"disclosed_quantity\": 0,\r\n    \"exchange\": \"NSE\",\r\n    \"execution_type\": \"REGULAR\",\r\n    \"instrument_token\": \"3045\",\r\n    \"order_side\": \"BUY\",\r\n    \"order_type\": \"MARKET\",\r\n    \"price\": 0,\r\n    \"product\": \"MIS\",\r\n    \"quantity\": 1,\r\n    \"series\": \"EQ\",\r\n    \"trading_symbol\": \"SBIN-EQ\",\r\n    \"trigger_price\": 0,\r\n    \"underlying_token\": \"3045\",\r\n    \"user_order_id\": 10002,\r\n    \"validity\": \"DAY\"\r\n}";
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
	'method': 'POST',
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
	"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
	"name": "Demo",
	"order_info": {
		"exchange": "NSE",
		"instrument_token": "3045",
		"client_id": "NA003",
		"order_type": "MARKET",
		"price": 0
	},
	"client_id": "NA003",
	"device": "WEB",
	"disclosed_quantity": 0,
	"exchange": "NSE",
	"execution_type": "REGULAR",
	"instrument_token": "3045",
	"order_side": "BUY",
	"order_type": "MARKET",
	"price": 0,
	"product": "MIS",
	"quantity": 1,
	"series": "EQ",
	"trading_symbol": "SBIN-EQ",
	"trigger_price": 0,
	"underlying_token": "3045",
	"user_order_id": 10002,
	"validity": "DAY"
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
	NSData *postData = [[NSData alloc] initWithData:[@"{\r\n    \"basket_id\": \"0786e757-2e8f-44b2-9559-deeac2e00114\",\r\n    \"name\": \"Demo\",\r\n    \"order_info\": {\r\n        \"exchange\": \"NSE\",\r\n        \"instrument_token\": \"3045\",\r\n        \"client_id\": \"NA003\",\r\n        \"order_type\": \"MARKET\",\r\n        \"price\": 0\r\n    },\r\n    \"client_id\": \"NA003\",\r\n    \"device\": \"WEB\",\r\n    \"disclosed_quantity\": 0,\r\n    \"exchange\": \"NSE\",\r\n    \"execution_type\": \"REGULAR\",\r\n    \"instrument_token\": \"3045\",\r\n    \"order_side\": \"BUY\",\r\n    \"order_type\": \"MARKET\",\r\n    \"price\": 0,\r\n    \"product\": \"MIS\",\r\n    \"quantity\": 1,\r\n    \"series\": \"EQ\",\r\n    \"trading_symbol\": \"SBIN-EQ\",\r\n    \"trigger_price\": 0,\r\n    \"underlying_token\": \"3045\",\r\n    \"user_order_id\": 10002,\r\n    \"validity\": \"DAY\"\r\n}" dataUsingEncoding:NSUTF8StringEncoding]];
	[request setHTTPBody:postData];

	[request setHTTPMethod:@"POST"];

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

	let postData = ref "{\r\n    \"basket_id\": \"0786e757-2e8f-44b2-9559-deeac2e00114\",\r\n    \"name\": \"Demo\",\r\n    \"order_info\": {\r\n        \"exchange\": \"NSE\",\r\n        \"instrument_token\": \"3045\",\r\n        \"client_id\": \"NA003\",\r\n        \"order_type\": \"MARKET\",\r\n        \"price\": 0\r\n    },\r\n    \"client_id\": \"NA003\",\r\n    \"device\": \"WEB\",\r\n    \"disclosed_quantity\": 0,\r\n    \"exchange\": \"NSE\",\r\n    \"execution_type\": \"REGULAR\",\r\n    \"instrument_token\": \"3045\",\r\n    \"order_side\": \"BUY\",\r\n    \"order_type\": \"MARKET\",\r\n    \"price\": 0,\r\n    \"product\": \"MIS\",\r\n    \"quantity\": 1,\r\n    \"series\": \"EQ\",\r\n    \"trading_symbol\": \"SBIN-EQ\",\r\n    \"trigger_price\": 0,\r\n    \"underlying_token\": \"3045\",\r\n    \"user_order_id\": 10002,\r\n    \"validity\": \"DAY\"\r\n}";;

	let reqBody = 
	let uri = Uri.of_string "https://pacetrader.pacefin.in/api/v1/basket/order" in
	let headers = Header.init ()
		|> fun h -> Header.add h "x-device-type" "WEB"
		|> fun h -> Header.add h "x-authorization-token" "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
		|> fun h -> Header.add h "content-type" "application/json"
	in
	let body = Cohttp_lwt.Body.of_string !postData in

	Client.call ~headers ~body `POST uri >>= fun (_resp, body) ->
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
	CURLOPT_CUSTOMREQUEST => 'POST',
	CURLOPT_POSTFIELDS =>'{
		"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
		"name": "Demo",
		"order_info": {
			"exchange": "NSE",
			"instrument_token": "3045",
			"client_id": "NA003",
			"order_type": "MARKET",
			"price": 0
		},
		"client_id": "NA003",
		"device": "WEB",
		"disclosed_quantity": 0,
		"exchange": "NSE",
		"execution_type": "REGULAR",
		"instrument_token": "3045",
		"order_side": "BUY",
		"order_type": "MARKET",
		"price": 0,
		"product": "MIS",
		"quantity": 1,
		"series": "EQ",
		"trading_symbol": "SBIN-EQ",
		"trigger_price": 0,
		"underlying_token": "3045",
		"user_order_id": 10002,
		"validity": "DAY"
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
	`n    `"basket_id`": `"0786e757-2e8f-44b2-9559-deeac2e00114`",
	`n    `"name`": `"Demo`",
	`n    `"order_info`": {
	`n        `"exchange`": `"NSE`",
	`n        `"instrument_token`": `"3045`",
	`n        `"client_id`": `"NA003`",
	`n        `"order_type`": `"MARKET`",
	`n        `"price`": 0
	`n    },
	`n    `"client_id`": `"NA003`",
	`n    `"device`": `"WEB`",
	`n    `"disclosed_quantity`": 0,
	`n    `"exchange`": `"NSE`",
	`n    `"execution_type`": `"REGULAR`",
	`n    `"instrument_token`": `"3045`",
	`n    `"order_side`": `"BUY`",
	`n    `"order_type`": `"MARKET`",
	`n    `"price`": 0,
	`n    `"product`": `"MIS`",
	`n    `"quantity`": 1,
	`n    `"series`": `"EQ`",
	`n    `"trading_symbol`": `"SBIN-EQ`",
	`n    `"trigger_price`": 0,
	`n    `"underlying_token`": `"3045`",
	`n    `"user_order_id`": 10002,
	`n    `"validity`": `"DAY`"
	`n}"

	$response = Invoke-RestMethod 'https://pacetrader.pacefin.in/api/v1/basket/order' -Method 'POST' -Headers $headers -Body $body
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
	"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
	"name": "Demo",
	"order_info": {
		"exchange": "NSE",
		"instrument_token": "3045",
		"client_id": "NA003",
		"order_type": "MARKET",
		"price": 0
	},
	"client_id": "NA003",
	"device": "WEB",
	"disclosed_quantity": 0,
	"exchange": "NSE",
	"execution_type": "REGULAR",
	"instrument_token": "3045",
	"order_side": "BUY",
	"order_type": "MARKET",
	"price": 0,
	"product": "MIS",
	"quantity": 1,
	"series": "EQ",
	"trading_symbol": "SBIN-EQ",
	"trigger_price": 0,
	"underlying_token": "3045",
	"user_order_id": 10002,
	"validity": "DAY"
	}';

	res <- VERB("POST", url = "https://pacetrader.pacefin.in/api/v1/basket/order", body = body, add_headers(headers))

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

	request = Net::HTTP::Post.new(url)
	request["x-device-type"] = "WEB"
	request["x-authorization-token"] = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
	request["content-type"] = "application/json"
	request.body = JSON.dump({
	"basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
	"name": "Demo",
	"order_info": {
		"exchange": "NSE",
		"instrument_token": "3045",
		"client_id": "NA003",
		"order_type": "MARKET",
		"price": 0
	},
	"client_id": "NA003",
	"device": "WEB",
	"disclosed_quantity": 0,
	"exchange": "NSE",
	"execution_type": "REGULAR",
	"instrument_token": "3045",
	"order_side": "BUY",
	"order_type": "MARKET",
	"price": 0,
	"product": "MIS",
	"quantity": 1,
	"series": "EQ",
	"trading_symbol": "SBIN-EQ",
	"trigger_price": 0,
	"underlying_token": "3045",
	"user_order_id": 10002,
	"validity": "DAY"
	})

	response = https.request(request)
	puts response.read_body


    ```

=== "Shell - httpie"
    ``` shell
    # You can also use other libraries such as `curl`, `wget`, etc..

    printf '{
    "basket_id": "0786e757-2e8f-44b2-9559-deeac2e00114",
    "name": "Demo",
    "order_info": {
        "exchange": "NSE",
        "instrument_token": "3045",
        "client_id": "NA003",
        "order_type": "MARKET",
        "price": 0
    },
    "client_id": "NA003",
    "device": "WEB",
    "disclosed_quantity": 0,
    "exchange": "NSE",
    "execution_type": "REGULAR",
    "instrument_token": "3045",
    "order_side": "BUY",
    "order_type": "MARKET",
    "price": 0,
    "product": "MIS",
    "quantity": 1,
    "series": "EQ",
    "trading_symbol": "SBIN-EQ",
    "trigger_price": 0,
    "underlying_token": "3045",
    "user_order_id": 10002,
    "validity": "DAY"
	}'| http  --follow --timeout 3600 POST 'https://pacetrader.pacefin.in/api/v1/basket/order' \
	x-device-type:'WEB' \
	x-authorization-token:'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
	content-type:'application/json'

    ```

=== "Swift-URLSession"
    ```swift
    
    let parameters = "{\r\n    \"basket_id\": \"0786e757-2e8f-44b2-9559-deeac2e00114\",\r\n    \"name\": \"Demo\",\r\n    \"order_info\": {\r\n        \"exchange\": \"NSE\",\r\n        \"instrument_token\": \"3045\",\r\n        \"client_id\": \"NA003\",\r\n        \"order_type\": \"MARKET\",\r\n        \"price\": 0\r\n    },\r\n    \"client_id\": \"NA003\",\r\n    \"device\": \"WEB\",\r\n    \"disclosed_quantity\": 0,\r\n    \"exchange\": \"NSE\",\r\n    \"execution_type\": \"REGULAR\",\r\n    \"instrument_token\": \"3045\",\r\n    \"order_side\": \"BUY\",\r\n    \"order_type\": \"MARKET\",\r\n    \"price\": 0,\r\n    \"product\": \"MIS\",\r\n    \"quantity\": 1,\r\n    \"series\": \"EQ\",\r\n    \"trading_symbol\": \"SBIN-EQ\",\r\n    \"trigger_price\": 0,\r\n    \"underlying_token\": \"3045\",\r\n    \"user_order_id\": 10002,\r\n    \"validity\": \"DAY\"\r\n}"
	let postData = parameters.data(using: .utf8)

	var request = URLRequest(url: URL(string: "https://pacetrader.pacefin.in/api/v1/basket/order")!,timeoutInterval: Double.infinity)
	request.addValue("WEB", forHTTPHeaderField: "x-device-type")
	request.addValue("eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg", forHTTPHeaderField: "x-authorization-token")
	request.addValue("application/json", forHTTPHeaderField: "content-type")

	request.httpMethod = "POST"
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

