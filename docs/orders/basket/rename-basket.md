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

## Error Response
```json
{
	"data": {},
	"error_code": 48001,
	"message": "`name` Basket name restricted to 20 characters",
	"status": "error"
}
```




## Code Examples

=== "python - http.client"

    ``` python
    # you an use any other module as well such as requests, urllib, etc.,

    import http.client
	import json

	conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
	payload = json.dumps({
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
	})
	headers = {
	'x-device-type': 'WEB',
	'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
	'content-type': 'application/json'
	}
	conn.request("PUT", "/api/v1/basket", payload, headers)
	res = conn.getresponse()
	data = res.read()
	print(data.decode("utf-8"))

    ```


=== "JavaScript - fetch"
    ``` javascript
    // You can also use other methods such as `axios`,`jQuery`, `XHR`, etc..
    var myHeaders = new Headers();
	myHeaders.append("x-device-type", "WEB");
	myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
	myHeaders.append("content-type", "application/json");

	var raw = JSON.stringify({
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
	});

	var requestOptions = {
	method: 'PUT',
	headers: myHeaders,
	body: raw,
	redirect: 'follow'
	};

	fetch("https://pacetrader.pacefin.in/api/v1/basket", requestOptions)
	.then(response => response.text())
	.then(result => console.log(result))
	.catch(error => console.log('error', error));
    
    ```

=== "C#-HttpClient"
    ``` csharp
    // You can also use other libraries such as RestSharp, etc..

    var client = new HttpClient();
	var request = new HttpRequestMessage(HttpMethod.Put, "https://pacetrader.pacefin.in/api/v1/basket");
	request.Headers.Add("x-device-type", "WEB");
	request.Headers.Add("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
	request.Headers.Add("content-type", "application/json");
	var content = new StringContent("{\r\n  \"basket_id\": \"<BasketId>\",\r\n  \"name\": \"<BasketName>\"\r\n}", null, "application/json");
	request.Content = content;
	var response = await client.SendAsync(request);
	response.EnsureSuccessStatusCode();
	Console.WriteLine(await response.Content.ReadAsStringAsync());


    ```

=== "cURL"
    ``` bash
    curl --location --request PUT 'https://pacetrader.pacefin.in/api/v1/basket' \
	--header 'x-device-type: WEB' \
	--header 'x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
	--header 'content-type: application/json' \
	--data '{
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
	}'

    ```

=== "Dart"

    ``` dart
    var headers = {
	'x-device-type': 'WEB',
	'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
	'content-type': 'application/json'
	};

	var request = http.Request('PUT', Uri.parse('https://pacetrader.pacefin.in/api/v1/basket'));
	request.body = json.encode({
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
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

	url := "https://pacetrader.pacefin.in/api/v1/basket"
	method := "PUT"

	payload := strings.NewReader(`{`+"
	"+`
	"basket_id": "<BasketId>",`+"
	"+`
	"name": "<BasketName>"`+"
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
    PUT /api/v1/basket HTTP/1.1
	Host: pacetrader.pacefin.in
	x-device-type: WEB
	x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg
	content-type: application/json
	Content-Length: 60

	{
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
	}

    ```

=== "Java-OkHttp"

    ``` java
    // You can also use other libraries such as Unirest, etc..

   	OkHttpClient client = new OkHttpClient().newBuilder()
	.build();
	MediaType mediaType = MediaType.parse("application/json");
	RequestBody body = RequestBody.create(mediaType, "{\r\n  \"basket_id\": \"<BasketId>\",\r\n  \"name\": \"<BasketName>\"\r\n}");
	Request request = new Request.Builder()
	.url("https://pacetrader.pacefin.in/api/v1/basket")
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
	curl_easy_setopt(curl, CURLOPT_URL, "https://pacetrader.pacefin.in/api/v1/basket");
	curl_easy_setopt(curl, CURLOPT_FOLLOWLOCATION, 1L);
	curl_easy_setopt(curl, CURLOPT_DEFAULT_PROTOCOL, "https");
	struct curl_slist *headers = NULL;
	headers = curl_slist_append(headers, "x-device-type: WEB");
	headers = curl_slist_append(headers, "x-authorization-token: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
	headers = curl_slist_append(headers, "content-type: application/json");
	curl_easy_setopt(curl, CURLOPT_HTTPHEADER, headers);
	const char *data = "{\r\n  \"basket_id\": \"<BasketId>\",\r\n  \"name\": \"<BasketName>\"\r\n}";
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
	'path': '/api/v1/basket',
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
	"name": "<BasketName>"
	});

	req.write(postData);

	req.end();

    ```


=== "Objective-C - NSURLSession"

    ``` objective-c
    #import <Foundation/Foundation.h>

	dispatch_semaphore_t sema = dispatch_semaphore_create(0);

	NSMutableURLRequest *request = [NSMutableURLRequest requestWithURL:[NSURL URLWithString:@"https://pacetrader.pacefin.in/api/v1/basket"]
	cachePolicy:NSURLRequestUseProtocolCachePolicy
	timeoutInterval:10.0];
	NSDictionary *headers = @{
	@"x-device-type": @"WEB",
	@"x-authorization-token": @"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg",
	@"content-type": @"application/json"
	};

	[request setAllHTTPHeaderFields:headers];
	NSData *postData = [[NSData alloc] initWithData:[@"{\r\n  \"basket_id\": \"<BasketId>\",\r\n  \"name\": \"<BasketName>\"\r\n}" dataUsingEncoding:NSUTF8StringEncoding]];
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

	let postData = ref "{\r\n  \"basket_id\": \"<BasketId>\",\r\n  \"name\": \"<BasketName>\"\r\n}";;

	let reqBody = 
	let uri = Uri.of_string "https://pacetrader.pacefin.in/api/v1/basket" in
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
	CURLOPT_URL => 'https://pacetrader.pacefin.in/api/v1/basket',
	CURLOPT_RETURNTRANSFER => true,
	CURLOPT_ENCODING => '',
	CURLOPT_MAXREDIRS => 10,
	CURLOPT_TIMEOUT => 0,
	CURLOPT_FOLLOWLOCATION => true,
	CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
	CURLOPT_CUSTOMREQUEST => 'PUT',
	CURLOPT_POSTFIELDS =>'{
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
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
	`n  `"basket_id`": `"<BasketId>`",
	`n  `"name`": `"<BasketName>`"
	`n}"

	$response = Invoke-RestMethod 'https://pacetrader.pacefin.in/api/v1/basket' -Method 'PUT' -Headers $headers -Body $body
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
	"name": "<BasketName>"
	}';

	res <- VERB("PUT", url = "https://pacetrader.pacefin.in/api/v1/basket", body = body, add_headers(headers))

	cat(content(res, 'text'))

    ```


=== "Ruby - Net::HTTP"

    ``` ruby

    require "uri"
	require "json"
	require "net/http"

	url = URI("https://pacetrader.pacefin.in/api/v1/basket")

	https = Net::HTTP.new(url.host, url.port)
	https.use_ssl = true

	request = Net::HTTP::Put.new(url)
	request["x-device-type"] = "WEB"
	request["x-authorization-token"] = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg"
	request["content-type"] = "application/json"
	request.body = JSON.dump({
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
	})

	response = https.request(request)
	puts response.read_body


    ```

=== "Shell - httpie"

    ``` shell
    # You can also use other libraries such as `curl`, `wget`, etc..

    printf '{
	"basket_id": "<BasketId>",
	"name": "<BasketName>"
	}'| http  --follow --timeout 3600 PUT 'https://pacetrader.pacefin.in/api/v1/basket' \
	x-device-type:'WEB' \
	x-authorization-token:'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg' \
	content-type:'application/json'

    ```

=== "Swift-URLSession"

    ```swift
    
    let parameters = "{\r\n  \"basket_id\": \"<BasketId>\",\r\n  \"name\": \"<BasketName>\"\r\n}"
	let postData = parameters.data(using: .utf8)

	var request = URLRequest(url: URL(string: "https://pacetrader.pacefin.in/api/v1/basket")!,timeoutInterval: Double.infinity)
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