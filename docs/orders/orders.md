<style>
.wy-table-responsive table td {
white-space: normal;
}
</style>

# Orders

## Understanding Different Types of Orders

In the world of securities trading, orders play a pivotal role as they instruct brokers or brokerage firms to buy or sell securities on behalf of investors. These orders represent the fundamental units in the securities market and come in various categories, allowing investors to impose specific conditions on when and at what price their orders should be executed. Here's an overview of these order types:

1. Regular Orders : These orders are executed immediately when buyers are willing to pay a higher price for a security than its current market value. However, if a buyer wishes to wait until the market price reaches a certain level (e.g., Rs. 512), they can place a Market SL Trigger Order with a trigger price of Rs. 512.

2. AMO (After Market Orders) : AMO orders enable buyers and sellers to place buy/sell orders after regular market hours. The closing price is a crucial consideration when entering an AMO order.

3. Conditional Orders : Conditional orders are more complex and involve specific criteria. These are typically used in advanced trading strategies and include:
a). BO (Bracket Order) : A bracket order allows traders to place stop-loss and target orders alongside a regular order. The stop-loss order minimizes losses, while the target order ensures profitability.
b). CO (Cover Order) : Cover orders include a stop-loss order along with a regular order, intended to manage losses if the price moves against the trader's expectations. When buying a CO order, the limit price must be higher than the stop-loss trigger price, and when selling, the limit price should be lower.
c). SO (Spread Order) : This strategy involves buying one contract while simultaneously selling another, which may be the same or have a different underlying asset. It entails taking both long and short positions with different expiry periods.

4. Basket Orders : Basket orders streamline the process by allowing multiple orders to be placed at once. Traders can create multiple orders for the same or different securities, grouping them together for simultaneous placement. This efficient approach saves time compared to executing each order individually.

5. GTT (Good Till Triggered) Orders : GTT orders stand for "good till trigger." They enable you to place buy or sell orders at a predetermined limit price. These orders execute only if the market price reaches the specified trigger price before the GTT order expires.

6. Orderbook : The orderbook contains comprehensive data related to your orders and trades. It encompasses successful and unsuccessful orders, trade history, pending orders, and completed orders, providing a comprehensive record of your trading activities.

Understanding these order types is essential for effective trading and investment in the securities market. Each order type offers distinct advantages and is suitable for different trading strategies and scenarios.


## Regular Orders

### Placing a Regular Orders
A regular order is designed to be executed immediately at the current market price. It is the simplest type of order and is suitable for traders who wish to buy or sell securities at the current market price. Regular orders are also known as market orders.



| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | place order | https://pacetrader.pacefin.in/api/v1/orders | Place a regular order |


#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json




#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `device` | `string` | WEB.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `excution_type` | `string` | The type of execution for the order (REGULAR).|
| `instrument_token` | `integer` | The unique token identifying the trading instrument.|
| `order_side` | `string` | BUY or SELL.|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `float` | The price at which the order is placed.|
| `product` | `string` | The product code (MIS, CNC, NMRL).|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `trigger_price` | `integer` | The trigger price for conditional orders|
| `user_order_id` | `string` | <UserOrderId>|
| `validity` | `string` | The order validity type (Day, IOC).|



#### Request Body
```json
{
  "amo":false,
  "client_id": "<ClientId>",
  "device":"WEB",
  "disclosed_quantity": 0,
  "exchange": "NSE",
  "execution_type": "REGULAR",
  "instrument_token": "22",
  "order_side": "BUY",
  "order_type": "LIMIT",
  "price": 500,
  "product": "CNC",
  "quantity": 1,
  "trigger_price": 0,
  "user_order_id":"<UserOrderId>",
  "validity": "DAY"
}
```

<style>
    /* .code-example {
        display: none;
    } */
    /* default to python */
    

    #code-examples {
        margin-top: 20px;
    }

    #code-examples h2 {
        margin-bottom: 10px;
    }

    #code-examples pre {
        background-color: #f4f4f4;
        border-radius: 5px;
        padding: 10px;
    }

    #code-examples pre code {
        font-family: monospace;
    }

</style>


#### <h2> Code Examples:</h2>
<div id="code-examples">
        <label for="language-select">Select a Programming Language:</label>
    <select id="language-select">
        <option value="python">Python-http.client</option>
        <option value="javascript">JavaScript-Fetch</option>
    </select>
    <pre id="python-code" class="code-example">

        ```python
        import requests
        import json

        url = "https://pacetrader.pacefin.in/api/v1/orders"

        payload = json.dumps({
        "amo": False,
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "REGULAR",
        "instrument_token": "22",
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 500,
        "product": "CNC",
        "quantity": 1,
        "trigger_price": 0,
        "user_order_id": "<UserOrderId>",
        "validity": "DAY"
        })

        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }

        response = requests.request("POST", url, headers=headers, data=payload)

        print(response.text)

        ```
    </pre>

    <pre id="javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "amo": false,
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "REGULAR",
        "instrument_token": "22",
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 500,
        "product": "CNC",
        "quantity": 1,
        "trigger_price": 0,
        "user_order_id": "<UserOrderId>",
        "validity": "DAY"
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
            
    </pre>

</div>

<script>
    document.getElementById('language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });
</script>




<!-- === "python"
    ```python
        import requests
        import json

        url = "https://pacetrader.pacefin.in/api/v1/orders"

        payload = json.dumps({
        "amo": False,
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "REGULAR",
        "instrument_token": "22",
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 500,
        "product": "CNC",
        "quantity": 1,
        "trigger_price": 0,
        "user_order_id": "<UserOrderId>",
        "validity": "DAY"
        })

        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }

        response = requests.request("POST", url, headers=headers, data=payload)

        print(response.text)

    ```

=== "JavaScript"
    ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "amo": false,
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "REGULAR",
        "instrument_token": "22",
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 500,
        "product": "CNC",
        "quantity": 1,
        "trigger_price": 0,
        "user_order_id": "<UserOrderId>",
        "validity": "DAY"
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

    ```
 -->



<!-- start modify order -->

### Modify a Regular Order
You can modify a regular order by changing its price or quantity. However, you cannot modify the order type or product type. To modify an order, you must first cancel it and then place a new order with the desired changes.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | modify order | https://pacetrader.pacefin.in/api/v1/orders | Modify a regular order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json






#### parameters
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
| `excution_type` | `string` | The type of execution for the order (REGULAR).|


#### Request Body
```json
{
  
    "exchange": "NSE",
    "instrument_token": 22,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": "50.50",
    "quantity": 1,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "200018000000003",
    "exchange_order_id": "200018000000003",
    "filled_quantity": 1,
    "remaining_quantity": 5,
    "last_activity_reference": 10,
    "trigger_price": 0,
    "execution_type": "REGULAR"

}
```




#### <h2> Code Examples:</h2>

<div id="regular-modify-code-examples">
        <label for="regular-modify-language-select">Select a Programming Language:</label>
    <select id="regular-modify-language-select">
        <option value="regular-modify-python">Python-http.client</option>
        <option value="regular-modify-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="regular-modify-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "exchange": "NSE",
        "instrument_token": 22,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": "50.50",
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "200018000000003",
        "exchange_order_id": "200018000000003",
        "filled_quantity": 1,
        "remaining_quantity": 5,
        "last_activity_reference": 10,
        "trigger_price": 0,
        "execution_type": "REGULAR"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("PUT", "/api/v1/orders", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="regular-modify-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "exchange": "NSE",
        "instrument_token": 22,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": "50.50",
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "200018000000003",
        "exchange_order_id": "200018000000003",
        "filled_quantity": 1,
        "remaining_quantity": 5,
        "last_activity_reference": 10,
        "trigger_price": 0,
        "execution_type": "REGULAR"
        });

        var requestOptions = {
        method: 'PUT',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
            
    </pre>

</div>

<script>
    document.getElementById('regular-modify-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });
</script>

<!-- end modify order -->



<!-- start cancel order -->

### Cancel a Regular Order
You can cancel a regular order at any time before it is executed. To cancel an order, you must specify the order ID. You can retrieve the order ID from the orderbook.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | cancel order | https://pacetrader.pacefin.in/api/v1/orders/<oms_order_id>?client_id=<ClientId>&execution_type=REGULAR | Cancel a regular order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json



#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `excution_type` | `string` | The type of execution for the order (REGULAR).|


#### Request Body
```json
{
  

}
```

#### <h2> Code Examples:</h2>

<div id="regular-cancel-code-examples">
        <label for="regular-cancel-language-select">Select a Programming Language:</label>
    <select id="regular-cancel-language-select">
        <option value="regular-cancel-python">Python-http.client</option>
        <option value="regular-cancel-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="regular-cancel-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/orders/<oms_order_id>?client_id=%3CClientId%3E&execution_type=REGULAR", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="regular-cancel-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = "";

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/<oms_order_id>?client_id=<ClientId>&execution_type=REGULAR", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('regular-cancel-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });
</script>

<!-- end cancel order -->

## AMO (After Market Orders)
This order type enables you to place buy/sell orders after regular market hours. The closing price is a crucial consideration when entering an AMO order. 

### Placing an AMO (After Market Orders)
You can place an AMO order after regular market hours. The closing price is a crucial consideration when entering an AMO order.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | place order | https://pacetrader.pacefin.in/api/v1/orders | Place an AMO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json



#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `device` | `string` | WEB.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `excution_type` | `string` | The type of execution for the order (AMO).|
| `instrument_token` | `integer` | The unique token identifying the trading instrument.|
| `order_side` | `string` | BUY or SELL.|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `float` | The price at which the order is placed.|
| `product` | `string` | The product code (MIS, CNC, NMRL).|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `trigger_price` | `integer` | The trigger price for conditional orders|
| `user_order_id` | `string` | <UserOrderId>|
| `validity` | `string` | The order validity type (Day, IOC).|



#### Request Body
```json
{
  "client_id": "<ClientId>",
  "device":"WEB",
  "disclosed_quantity": 0,
  "exchange": "NSE",
  "execution_type": "AMO",
  "instrument_token": "22",
  "order_side": "BUY",
  "order_type": "LIMIT",
  "price": 500,
  "product": "CNC",
  "quantity": 1,
  "trigger_price": 0,
  "user_order_id":"<UserOrderId>",
  "validity": "DAY"
}
```

#### <h2> Code Examples:</h2>

<div id="amo-place-code-examples">
        <label for="amo-place-language-select">Select a Programming Language:</label>
    <select id="amo-place-language-select">
        <option value="amo-place-python">Python-http.client</option>
        <option value="amo-place-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="amo-place-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "AMO",
        "instrument_token": "22",
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 500,
        "product": "CNC",
        "quantity": 1,
        "trigger_price": 0,
        "user_order_id": "<UserOrderId>",
        "validity": "DAY"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/orders", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="amo-place-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "AMO",
        "instrument_token": "22",
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 500,
        "product": "CNC",
        "quantity": 1,
        "trigger_price": 0,
        "user_order_id": "<UserOrderId>",
        "validity": "DAY"
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('amo-place-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });
</script>


<!-- start modify order -->

### Modify an AMO (After Market Orders)

You can modify an AMO order by changing its price or quantity. However, you cannot modify the order type or product type. To modify an order, you must first cancel it and then place a new order with the desired changes.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | modify order | https://pacetrader.pacefin.in/api/v1/orders | Modify an AMO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token)`
content-type | application/json



#### parameters
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
| `excution_type` | `string` | The type of execution for the order (AMO).|

#### Request Body
```json
{

    "exchange": "NSE",
    "instrument_token": 22,
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": "50.50",
    "quantity": 1,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "oms_order_id": "200018000000003",
    "exchange_order_id": "200018000000003",
    "filled_quantity": 1,
    "remaining_quantity": 5,
    "last_activity_reference": 10,
    "trigger_price": 0,
    "execution_type": "AMO"
}

```

#### <h2> Code Examples:</h2>

<div id="amo-modify-code-examples">

    <label for="amo-modify-language-select">Select a Programming Language:</label>
    <select id="amo-modify-language-select">
        <option value="amo-modify-python">Python-http.client</option>
        <option value="amo-modify-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="amo-modify-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "exchange": "NSE",
        "instrument_token": 22,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": "50.50",
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "200018000000003",
        "exchange_order_id": "200018000000003",
        "filled_quantity": 1,
        "remaining_quantity": 5,
        "last_activity_reference": 10,
        "trigger_price": 0,
        "execution_type": "AMO"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("PUT", "/api/v1/orders", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="amo-modify-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "exchange": "NSE",
        "instrument_token": 22,
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": "50.50",
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "oms_order_id": "200018000000003",
        "exchange_order_id": "200018000000003",
        "filled_quantity": 1,
        "remaining_quantity": 5,
        "last_activity_reference": 10,
        "trigger_price": 0,
        "execution_type": "AMO"
        });

        var requestOptions = {
        method: 'PUT',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>

<script>
    document.getElementById('amo-modify-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end modify order -->


<!-- start cancel order -->

### Cancel an AMO (After Market Orders)

You can cancel an AMO order at any time before it is executed. To cancel an order, you must specify the order ID. You can retrieve the order ID from the orderbook.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | cancel order | https://pacetrader.pacefin.in/api/v1/orders/<oms_order_id>?client_id=<ClientId>&execution_type=AMO | Cancel an AMO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json

<!-- Parameters
Field
Type
Description
clint_id
string
Your unique client identifier for the order.
excution_type
string
The type of execution for the order (AMO). -->

#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `excution_type` | `string` | The type of execution for the order (AMO).|

#### Request Body
```json
{
    "client_id": "<ClientId>",
    "execution_type": "AMO"
}
```

#### <h2> Code Examples:</h2>

<div id="amo-cancel-code-examples">
        <label for="amo-cancel-language-select">Select a Programming Language:</label>
    <select id="amo-cancel-language-select">
        <option value="amo-cancel-python">Python-http.client</option>
        <option value="amo-cancel-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="amo-cancel-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "execution_type": "AMO"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/orders/<oms_order_id>?client_id=%3CClientId%3E&execution_type=REGULAR", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="amo-cancel-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "execution_type": "AMO"
        });

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/<oms_order_id>?client_id=<ClientId>&execution_type=REGULAR", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('amo-cancel-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });
</script>


<!-- end cancel order -->

<!--  start Conditional Orders -->

## Conditional Orders

Conditional orders are advanced orders that are executed only when certain conditions are met. You can place conditional orders to buy or sell a security when the market price reaches a specified trigger price. You can also place conditional orders to buy or sell a security when the market price reaches a specified trigger price and the market price is expected to rise or fall further.


### BO (Bracket Orders)
A bracket order is a conditional order that is designed to help limit your loss and lock in a profit by "bracketing" an order with two opposite-side orders. A BUY order is bracketed by a high-side sell limit order and a low-side sell stop order. A SELL order is bracketed by a high-side buy stop order and a low side buy limit order. Bracket orders are designed to help limit your loss and lock in a profit by "bracketing" an order with two opposite-side orders. A BUY order is bracketed by a high-side sell limit order and a low-side sell stop order. A SELL order is bracketed by a high-side buy stop order and a low side buy limit order.

#### Placing a BO (Bracket Orders)
You can place a BO order during regular market hours. The closing price is a crucial consideration when entering a BO order.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | place order | https://pacetrader.pacefin.in/api/v1/orders/kart | Place a BO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token) `
content-type | application/json


#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `device` | `string` | WEB.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `excution_type` | `string` | The type of execution for the order (BO).|
| `instrument_token` | `integer` | The unique token identifying the trading instrument.|
| `is_trailing` | `string` | A boolean flag (true or false) indicating whether the order include trailing stop loss.|
| `order_side` | `string` | BUY or SELL.|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `float` | The price at which the order is placed.|
| `product` | `string` | The product code (MIS, CNC, NMRL).|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `square_off_value` | `integer` | The square-off value for the bracket order.|
| `stop_loss_value` | `integer` | The stop loss value for the bracket order.|
| `trailing_stop_loss` | `string` | The percentage or value for trailing stop loss.|
| `trigger_price` | `integer` | The trigger price for conditional orders.|
| `user_order_id` | `string` | <UserOrderId>.|
| `validity` | `string` | The order validity type (Day, IOC).|

#### Request Body
```json
 {
    "client_id": "<ClientId>",
    "device": "WEB",
    "disclosed_quantity": 0,
    "exchange": "NSE",
    "execution_type": "BO",
    "instrument_token": "3045",
    "is_trailing": true,
    "order_side": "BUY",
    "order_type": "LIMIT",
    "price": 456.95,
    "product": "MIS",
    "quantity": 1,
    "square_off_value": 1,
    "stop_loss_value": 1,
    "trailing_stop_loss": "0.05",
    "trigger_price": 0,
    "user_order_id": 10002,
    "validity": "DAY"
 }
```

#### <h2> Code Examples:</h2>

<div id="bo-place-code-examples">
    <label for="bo-place-language-select">Select a Programming Language:</label>
    <select id="bo-place-language-select">
        <option value="bo-place-python">Python-http.client</option>
        <option value="bo-place-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="bo-place-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "BO",
        "instrument_token": "3045",
        "is_trailing": True,
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 456.95,
        "product": "MIS",
        "quantity": 1,
        "square_off_value": 1,
        "stop_loss_value": 1,
        "trailing_stop_loss": "0.05",
        "trigger_price": 0,
        "user_order_id": 10002,
        "validity": "DAY"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/orders/kart", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
            
        ```
    </pre>

    <pre id="bo-place-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "device": "WEB",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "execution_type": "BO",
        "instrument_token": "3045",
        "is_trailing": true,
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 456.95,
        "product": "MIS",
        "quantity": 1,
        "square_off_value": 1,
        "stop_loss_value": 1,
        "trailing_stop_loss": "0.05",
        "trigger_price": 0,
        "user_order_id": 10002,
        "validity": "DAY"
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('bo-place-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });
</script>



<!-- start modify order -->

### Modify a BO (Bracket Orders)

You can modify a BO order by changing its price or quantity. However, you cannot modify the order type or product type. To modify an order, you must first cancel it and then place a new order with the desired changes.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | modify order | https://pacetrader.pacefin.in/api/v1/orders/kart | Modify a BO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token)`
content-type | application/json



#### parameters
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



#### Request Body
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


#### <h2> Code Examples:</h2>

<div id="bo-modify-code-examples">
    <label for="bo-modify-language-select">Select a Programming Language:</label>
    <select id="bo-modify-language-select">
        <option value="bo-modify-python">Python-http.client</option>
        <option value="bo-modify-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="bo-modify-python-code" class="code-example">

        ```python

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
    </pre>

    <pre id="bo-modify-javascript-code" class="code-example">

        ```JavaScript
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
    </pre>

</div>

<script>
    document.getElementById('bo-modify-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end modify order -->


<!-- start cancel order -->

### Cancel a BO (Bracket Orders)

You can cancel a BO order at any time before it is executed. To cancel an order, you must specify the order ID. You can retrieve the order ID from the orderbook.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | cancel order | https://pacetrader.pacefin.in/api/v1/orders/kart/<oms_order_id> | Cancel a BO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json

<!-- Parameters -->

#### parameters

| Parameter | Type | Description |
|-------------- | ------- | ------- |


#### Request Body
```json
{
    "client_id": "<ClientId>",
    "exchange_order_id": "1100000000006951",
    "execution_type": "BO",
    "leg_order_indicator": "ENTRY",
    "oms_order_id": "20220106-106",
    "status": "CONFIRMED"
}
```

#### <h2> Code Examples:</h2>

<div id="bo-cancel-code-examples">
        <label for="bo-cancel-language-select">Select a Programming Language:</label>
    <select id="bo-cancel-language-select">
        <option value="bo-cancel-python">Python-http.client</option>
        <option value="bo-cancel-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="bo-cancel-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "exchange_order_id": "1100000000006951",
        "execution_type": "BO",
        "leg_order_indicator": "ENTRY",
        "oms_order_id": "20220106-106",
        "status": "CONFIRMED"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/orders/kart/<oms_order_id>", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="bo-cancel-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "exchange_order_id": "1100000000006951",
        "execution_type": "BO",
        "leg_order_indicator": "ENTRY",
        "oms_order_id": "20220106-106",
        "status": "CONFIRMED"
        });

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart/<oms_order_id>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
            
        ```

    </pre>

</div>

<script>
    document.getElementById('bo-cancel-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>



<!-- end cancel order -->

<!--  start Conditional Orders -->

### CO (Cover Orders) 
A cover order is a conditional order that is designed to help limit your loss and lock in a profit by "covering" an order with two opposite-side orders. A BUY order is covered by a high-side sell limit order and a low-side sell stop loss order. A SELL order is covered by a high-side buy stop loss order and a low side buy limit order.

#### Placing a CO (Cover Orders)
You can place a CO order during regular market hours. The closing price is a crucial consideration when entering a CO order.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | place order | https://pacetrader.pacefin.in/api/v1/orders/kart | Place a CO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token) `
content-type | application/json





#### parameters
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
| `order_side` | `string` | BUY or SELL.|
| `device` | `string` | WEB.|
| `user_order_id` | `string` | <UserOrderId>.|
| `execution_type` | `string` | The type of execution for the order (CO).|
| `stop_loss_value` | `integer` | The stop loss value for the cover order.|
| `trailing_stop_loss` | `int` | The percentage or value for trailing stop loss.|


#### Request Body
```json
 {
    "exchange": "NSE",
    "instrument_token": "1624",
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 91.3,
    "quantity": 1,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "MIS",
    "order_side": "BUY",
    "device": "WEB",
    "user_order_id": 10002,
    "execution_type": "CO",
    "stop_loss_value": 2,
    "trailing_stop_loss": 0
 }
```

#### <h2> Code Examples:</h2>

<div id="co-place-code-examples">
    <label for="co-place-language-select">Select a Programming Language:</label>
    <select id="co-place-language-select">
        <option value="co-place-python">Python-http.client</option>
        <option value="co-place-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="co-place-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "exchange": "NSE",
        "instrument_token": "1624",
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 91.3,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "order_side": "BUY",
        "device": "WEB",
        "user_order_id": 10002,
        "execution_type": "CO",
        "stop_loss_value": 2,
        "trailing_stop_loss": 0
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/orders/kart", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
                
        ```

    </pre>

    <pre id="co-place-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "exchange": "NSE",
        "instrument_token": "1624",
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 91.3,
        "quantity": 1,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "MIS",
        "order_side": "BUY",
        "device": "WEB",
        "user_order_id": 10002,
        "execution_type": "CO",
        "stop_loss_value": 2,
        "trailing_stop_loss": 0
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
            
        ```
    </pre>

</div>

<script>
    document.getElementById('co-place-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end place order -->


<!-- start modify order -->

### Modify a CO (Cover Orders)

You can modify a CO order by changing its price or quantity. However, you cannot modify the order type or product type. To modify an order, you must first cancel it and then place a new order with the desired changes.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | modify order | https://pacetrader.pacefin.in/api/v1/orders/kart | Modify a CO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token)`
content-type | application/json





#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `exchange_order_id` | `string` | The order identifier on the exchange.|
| `execution_type` | `string` | The type of execution for the order (CO).|
| `filled_quantity` | `integer` | The quantity of the order has been filled|
| `instrument_token` | `integer` | The unique token identifying the trading instrument.|
| `last_active_reference` | `integer` | The reference to the last activity related to the order.|
| `oms_order_id` | `string` | The unique order management system order identifier|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `float` | The price at which the order is placed.|
| `product` | `string` | The product code (MIS, CNC, NMRL).|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `remaining_quantity` | `integer` | The remaining quantity to be filled.|
| `stop_loss_value` | `integer` | The stop loss value for the cover order.|
| `trailing_stop_loss` | `integer` | The percentage or value for trailing stop loss.|
| `validity` | `string` | The order validity type (Day, IOC).|

#### Request Body
```json
{
    "client_id": "<ClientId>",
    "disclosed_quantity": 0,
    "exchange": "NSE",
    "exchange_order_id": "1100000000007793",
    "execution_type": "CO",
    "filled_quantity": 0,
    "instrument_token": 3045,
    "last_activity_reference": 1325941635181246200,
    "oms_order_id": "20220106-114",
    "order_type": "LIMIT",
    "price": 456.95,
    "product": "MIS",
    "quantity": "3",
    "remaining_quantity": 2,
    "stop_loss_value": 0,
    "trailing_stop_loss": 0,
    "validity": "DAY"
}
```

#### <h2> Code Examples:</h2>

<div id="co-modify-code-examples">
    <label for="co-modify-language-select">Select a Programming Language:</label>
    <select id="co-modify-language-select">
        <option value="co-modify-python">Python-http.client</option>
        <option value="co-modify-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="co-modify-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "exchange_order_id": "1100000000007793",
        "execution_type": "CO",
        "filled_quantity": 0,
        "instrument_token": 3045,
        "last_activity_reference": 1325941635181246200,
        "oms_order_id": "20220106-114",
        "order_type": "LIMIT",
        "price": 456.95,
        "product": "MIS",
        "quantity": "3",
        "remaining_quantity": 2,
        "stop_loss_value": 0,
        "trailing_stop_loss": 0,
        "validity": "DAY"
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
    </pre>

    <pre id="co-modify-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "exchange_order_id": "1100000000007793",
        "execution_type": "CO",
        "filled_quantity": 0,
        "instrument_token": 3045,
        "last_activity_reference": 1325941635181246200,
        "oms_order_id": "20220106-114",
        "order_type": "LIMIT",
        "price": 456.95,
        "product": "MIS",
        "quantity": "3",
        "remaining_quantity": 2,
        "stop_loss_value": 0,
        "trailing_stop_loss": 0,
        "validity": "DAY"
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
    </pre>

</div>

<script>
    document.getElementById('co-modify-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end modify order -->


<!-- start cancel order -->

### Cancel a CO (Cover Orders)

You can cancel a CO order at any time before it is executed. To cancel an order, you must specify the order ID. You can retrieve the order ID from the orderbook.


| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | cancel order | https://pacetrader.pacefin.in/api/v1/orders/kart/<oms_order_id> | Cancel a CO order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | (Your authorization token)
content-type | application/json

<!-- Parameters -->

#### parameters

| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `exchange_order_id` | `string` | The order identifier on the exchange.|
| `execution_type` | `string` | The type of execution for the order (CO).|
| `leg_order_indicator` | `string` | The leg order indicator (ENTRY, TARGET, STOPLOSS).|
| `oms_order_id` | `string` | The unique order management system order identifier|



#### Request Body
```json
{
    "client_id": "<ClientId>",
    "exchange_order_id": "1100000000007793",
    "execution_type": "CO",
    "leg_order_indicator": "ENTRY",
    "oms_order_id": "20220106-114"
}
```

#### <h2> Code Examples:</h2>

<div id="co-cancel-code-examples">
        <label for="co-cancel-language-select">Select a Programming Language:</label>
    <select id="co-cancel-language-select">
        <option value="co-cancel-python">Python-http.client</option>
        <option value="co-cancel-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="co-cancel-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "exchange_order_id": "1100000000007793",
        "execution_type": "CO",
        "leg_order_indicator": "ENTRY",
        "oms_order_id": "20220106-114"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/orders/kart/<oms_order_id>", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```
    </pre>

    <pre id="co-cancel-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "exchange_order_id": "1100000000007793",
        "execution_type": "CO",
        "leg_order_indicator": "ENTRY",
        "oms_order_id": "20220106-114"
        });

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart/<oms_order_id>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('co-cancel-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end cancel order -->


<!--  start Spread Order -->
### Spread Orders

A spread order is a combination of various orders across different trading segments. It is a combination of two or more orders with different order types, product types, and prices. The spread order is executed as a single order. The spread order is executed only when all the orders in the spread are executed. The spread order is executed only when all the orders in the spread are executed.

#### Placing a Spread Order
You can place a spread order during regular market hours. The closing price is a crucial consideration when entering a spread order.


| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | place order | https://pacetrader.pacefin.in/api/v1/orders/kart | Place a spread order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token) `
content-type | application/json


#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `instrument_token` | `string` | The unique token identifying the trading instrument.|
| `clint_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `float` | The price at which the order is placed.|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `validity` | `string` | The order validity type (Day, IOC).|
| `product` | `string` | The product code (MIS, CNC, NMRL).|
| `order_side` | `string` | BUY or SELL.|
| `device` | `string` | WEB.|
| `user_order_id` | `integer` | <UserOrderId>.|
| `execution_type` | `string` | The type of execution for the order (SPD).|

#### Request Body
```json
{
    "exchange": "NFO",
    "instrument_token": "53181-49939",
    "client_id": "<ClientId>",
    "order_type": "LIMIT",
    "price": 0,
    "quantity": 50,
    "disclosed_quantity": 0,
    "validity": "DAY",
    "product": "NRML",
    "order_side": "BUY",
    "device": "WEB",
    "user_order_id": 10002,
    "execution_type": "SPD"
}
```

#### <h2> Code Examples:</h2>

<div id="spread-place-code-examples">
    <label for="spread-place-language-select">Select a Programming Language:</label>
    <select id="spread-place-language-select">
        <option value="spread-place-python">Python-http.client</option>
        <option value="spread-place-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="spread-place-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "exchange": "NFO",
        "instrument_token": "53181-49939",
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 0,
        "quantity": 50,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "NRML",
        "order_side": "BUY",
        "device": "WEB",
        "user_order_id": 10002,
        "execution_type": "SPD"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/orders/kart/", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="spread-place-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "exchange": "NFO",
        "instrument_token": "53181-49939",
        "client_id": "<ClientId>",
        "order_type": "LIMIT",
        "price": 0,
        "quantity": 50,
        "disclosed_quantity": 0,
        "validity": "DAY",
        "product": "NRML",
        "order_side": "BUY",
        "device": "WEB",
        "user_order_id": 10002,
        "execution_type": "SPD"
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart/", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        ```
    </pre>

</div>

<script>
    document.getElementById('spread-place-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>




<!-- end place order -->


<!-- start modify order -->

### Modify a Spread Order

You can modify a spread order by changing its price or quantity. However, you cannot modify the order type or product type. To modify an order, you must first cancel it and then place a new order with the desired changes.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | modify order | https://pacetrader.pacefin.in/api/v1/orders/kart/ | Modify a spread order |

#### Headers
| Header | Value |
|-------------- | ------- |
x-device-type | WEB
x-auth-token | `(Your authorization token)`
content-type | application/json



#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `disclosed_quantity` | `integer` | The portion of the quantity to be disclosed.|
| `exchange` | `string` | The exchange where the order is placed (NSE, BSE, NFO, CDS, MCX).|
| `exchange_order_id` | `string` | The order identifier on the exchange.|
| `execution_type` | `string` | The type of execution for the order (SPD).|
| `instrument_token` | `integer` | The unique token identifying the trading instrument.|
| `is_trailing` | `boolean` | The trailing stop loss value.|
| `oms_order_id` | `string` | The unique order management system order identifier|
| `order_type` | `string` | The type of order (LIMIT, MARKET, SL, SLM).|
| `price` | `string` | The price at which the order is placed.|
| `prod_type` | `string` | The product code (MIS, CNC, NRML).|
| `product` | `string` | The product code (SPD).|
| `quantity` | `integer` | The quantity of the security to be bought or sold.|
| `square_off_value` | `integer` | The square off value for the spread order.|
| `stop_loss_value` | `integer` | The stop loss value for the spread order.|
| `trailing_stop_loss` | `integer` | The trailing stop loss value for the spread order.|
| `trigger_price` | `integer` | The trigger price for the spread order.|
| `validity` | `string` | The order validity type (Day, IOC).|


#### Request Body
```json
{
    "client_id": "<ClientId>",
    "disclosed_quantity": 0,
    "exchange": "NSE",
    "exchange_order_id": "1100000000007793",
    "execution_type": "CO",
    "filled_quantity": 0,
    "instrument_token": 3045,
    "last_activity_reference": 1325941635181246200,
    "oms_order_id": "20220106-114",
    "order_type": "LIMIT",
    "price": 456.95,
    "product": "MIS",
    "quantity": "3",
    "remaining_quantity": 2,
    "stop_loss_value": 0,
    "trailing_stop_loss": 0,
    "validity": "DAY"
}
```

#### <h2> Code Examples:</h2>

<div id="spread-modify-code-examples">
    <label for="spread-modify-language-select">Select a Programming Language:</label>
    <select id="spread-modify-language-select">
        <option value="spread-modify-python">Python-http.client</option>
        <option value="spread-modify-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="spread-modify-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<ClientId>",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "exchange_order_id": "1100000000007793",
        "execution_type": "CO",
        "filled_quantity": 0,
        "instrument_token": 3045,
        "last_activity_reference": 1325941635181246200,
        "oms_order_id": "20220106-114",
        "order_type": "LIMIT",
        "price": 456.95,
        "product": "MIS",
        "quantity": "3",
        "remaining_quantity": 2,
        "stop_loss_value": 0,
        "trailing_stop_loss": 0,
        "validity": "DAY"
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

    </pre>

    <pre id="spread-modify-javascript-code" class="code-example">

        ```JavaScript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<ClientId>",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "exchange_order_id": "1100000000007793",
        "execution_type": "CO",
        "filled_quantity": 0,
        "instrument_token": 3045,
        "last_activity_reference": 1325941635181246200,
        "oms_order_id": "20220106-114",
        "order_type": "LIMIT",
        "price": 456.95,
        "product": "MIS",
        "quantity": "3",
        "remaining_quantity": 2,
        "stop_loss_value": 0,
        "trailing_stop_loss": 0,
        "validity": "DAY"
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
    </pre>

</div>

<script>
    document.getElementById('spread-modify-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end modify order -->

<!-- start cancel order -->

### Cancel a Spread Order

You can cancel a spread order at any time before it is executed. To cancel an order, you must specify the order ID. You can retrieve the order ID from the orderbook.


| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | cancel order | https://pacetrader.pacefin.in/api/v1/orders/kart/ | Cancel a spread order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

<!-- Parameters




 -->

#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `leg_order_indicator` | `string` | The leg order indicator (ENTRY, TARGET, STOPLOSS).|
| `oms_order_id` | `string` | The unique order management system order identifier|
| `status` | `string` | The status of the order (CONFIRMED, CANCELLED).|
| `execution_type` | `string` | The type of execution for the order (SPD).|
| `exchange_order_id` | `string` | The order identifier on the exchange.|


#### Request Body
```json
{
    "client_id": "<Client1>",
    "leg_order_indicator": "ENTRY",
    "oms_order_id": "20210226-92",
    "status": "CONFIRMED",
    "execution_type": "SPD",
    "exchange_order_id": "10095"
}
```


#### <h2> Code Examples:</h2>

<div id="spread-cancel-code-examples">
    <label for="spread-cancel-language-select">Select a Programming Language:</label>
    <select id="spread-cancel-language-select">
        <option value="spread-cancel-python">Python-http.client</option>
        <option value="spread-cancel-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="spread-cancel-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "client_id": "<Client1>",
        "leg_order_indicator": "ENTRY",
        "oms_order_id": "20210226-92",
        "status": "CONFIRMED",
        "execution_type": "SPD",
        "exchange_order_id": "10095"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/orders/kart/", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="spread-cancel-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "client_id": "<Client1>",
        "leg_order_indicator": "ENTRY",
        "oms_order_id": "20210226-92",
        "status": "CONFIRMED",
        "execution_type": "SPD",
        "exchange_order_id": "10095"
        });

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart/", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
        
        
        ```
    </pre>

</div>

<script>
    document.getElementById('spread-cancel-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end cancel order -->


<!-- start orderbook -->

## Orderbook

The orderbook API allows you to retrieve the list of orders placed by you. You can retrieve the orderbook for a specific order or for all orders placed by you.

### Pending Orders

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET`       | orderbook | https://pacetrader.pacefin.in/api/v1/orders?type=pending&client_id=<ClientId> | Retrieve the list of pending orders |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |



#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `type` | `string` | The type of order (pending).|
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|


#### Request Body
```json
{
    "type": "pending",
    "client_id": "<ClientId>"
}
```

#### <h2> Code Examples:</h2>

<div id="orderbook-pending-code-examples">
    <label for="orderbook-pending-language-select">Select a Programming Language:</label>
    <select id="orderbook-pending-language-select">
        <option value="orderbook-pending-python">Python-http.client</option>
        <option value="orderbook-pending-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="orderbook-pending-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("GET", "/api/v1/orders?type=pending&client_id=%3CClientId%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```

    </pre>

    <pre id="orderbook-pending-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders?type=pending&client_id=<ClientId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('orderbook-pending-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end pending order -->

<!-- start Completed Orders -->

### Completed Orders

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET`       | orderbook | https://pacetrader.pacefin.in/api/v1/orders?type=completed&client_id=<ClientId> | Retrieve the list of completed orders |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |


#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `type` | `string` | The type of order (completed).|
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|

#### Request Body
```json
{
    "type": "completed",
    "client_id": "<ClientId>"
}
```

#### <h2> Code Examples:</h2>

<div id="orderbook-completed-code-examples">
    <label for="orderbook-completed-language-select">Select a Programming Language:</label>
    <select id="orderbook-completed-language-select">
        <option value="orderbook-completed-python">Python-http.client</option>
        <option value="orderbook-completed-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="orderbook-completed-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("GET", "/api/v1/orders?type=completed&client_id=%3CClientId%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="orderbook-completed-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders?type=completed&client_id=<ClientId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>

<script>
    document.getElementById('orderbook-completed-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end completed order -->

<!-- start Trade Book -->

### Trade Book

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET`       | orderbook | https://pacetrader.pacefin.in/api/v1/trades?client_id=<ClientId> | Retrieve the list of trade orders |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |


#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|

#### Request Body
```json
{
    "client_id": "<ClientId>"
}
```

#### <h2> Code Examples:</h2>

<div id="orderbook-trade-code-examples">
    <label for="orderbook-trade-language-select">Select a Programming Language:</label>
    <select id="orderbook-trade-language-select">
        <option value="orderbook-trade-python">Python-http.client</option>
        <option value="orderbook-trade-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="orderbook-trade-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("GET", "/api/v1/trades?client_id=%3CClientId%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="orderbook-trade-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/trades?client_id=<ClientId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
            
        ```
    </pre>

</div>

<script>
    document.getElementById('orderbook-trade-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end trade book -->

<!-- start Order History -->

### Order History

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET`       | orderbook | https://pacetrader.pacefin.in/api/v1/order/<oms_order_id>/history?client_id=<ClientId> | Retrieve the list of orders |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |


#### parameters

| Parameter | Type | Description |
|-------------- | ------- | ------- |
|client_id | `string` | Your unique client identifier for the order <ClientId>.|

#### Request Body
```json
{
    "client_id": "<ClientId>"
}
```

#### <h2> Code Examples:</h2>

<div id="orderbook-history-code-examples">
    <label for="orderbook-history-language-select">Select a Programming Language:</label>
    <select id="orderbook-history-language-select">
        <option value="orderbook-history-python">Python-http.client</option>
        <option value="orderbook-history-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="orderbook-history-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("GET", "/api/v1/order/<oms_order_id>/history?client_id=%3CClientId%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="orderbook-history-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/order/<oms_order_id>/history?client_id=<ClientId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>

<script>
    document.getElementById('orderbook-history-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end order history -->



## Basket Order

A basket order is a collection of multiple orders that are placed simultaneously. You can place a basket order for multiple orders of the same instrument or for multiple orders of different instruments. You can place a basket order for up to 100 orders.

### Create a Basket Order

You can create a basket order by specifying the details of each order in the basket. You can place a basket order for up to 100 orders.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | basket order | https://pacetrader.pacefin.in/api/v1/basket | Create a basket order |



#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | multipart/form-data |



#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `login_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `name` | `string` | The name of the basket order.|
| `type` | `string` | The type of basket order (NORMAL, HEDGE).|
| `product_type` | `string` | The product type for the basket order (CNC, MIS, NRML).|
| `order_type` | `string` | The order type for the basket order (LIMIT, MARKET, SL, SLM).|

#### Request Body
```json
{
  "login_id": "<ClientId>",
  "name": "<BasketName>",
  "type": "NORMAL", 
  "product_type": "ALL", 
  "order_type": "ALL"
}
```

#### <h2> Code Examples:</h2>

<div id="basket-create-code-examples">
    <label for="basket-create-language-select">Select a Programming Language:</label>
    <select id="basket-create-language-select">
        <option value="basket-create-python">Python-http.client</option>
        <option value="basket-create-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-create-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "login_id": "<ClientId>",
        "name": "<BasketName>",
        "type": "NORMAL",
        "product_type": "ALL",
        "order_type": "ALL"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/basket", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="basket-create-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "login_id": "<ClientId>",
        "name": "<BasketName>",
        "type": "NORMAL",
        "product_type": "ALL",
        "order_type": "ALL"
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/basket", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('basket-create-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end create basket order -->

<!-- start Fetch Basket -->

### Fetch Basket Order

You can fetch the details of a basket order by specifying the basket order identifier.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET`       | basket order | https://pacetrader.pacefin.in?login_id=<LoginId>| Fetch the details of a basket order |


#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | multipart/form-data |



<!-- PARAMS
login_id
<LoginId>

string
 -->

#### Request Body
```json
{
    "login_id": "<LoginId>"
}
```

#### <h2> Code Examples:</h2>

<div id="basket-fetch-code-examples">
    <label for="basket-fetch-language-select">Select a Programming Language:</label>
    <select id="basket-fetch-language-select">
        <option value="basket-fetch-python">Python-http.client</option>
        <option value="basket-fetch-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-fetch-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("GET", "/?login_id=%3CLoginId%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="basket-fetch-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in?login_id=<LoginId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('basket-fetch-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end fetch basket order -->

<!-- start Delete Baskett -->

### Delete Basket Order

You can delete a basket order by specifying the basket order identifier.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | basket order | https://pacetrader.pacefin.in?basket_id=<BasketID>| Delete a basket order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | multipart/form-data |


<!-- 
PARAMS
basket_id
<BasketID>
 -->

#### Request Body

```json
{
    "basket_id": "<BasketID>"
}
```

#### <h2> Code Examples:</h2>

<div id="basket-delete-code-examples">
    <label for="basket-delete-language-select">Select a Programming Language:</label>
    <select id="basket-delete-language-select">
        <option value="basket-delete-python">Python-http.client</option>
        <option value="basket-delete-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-delete-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/?basket_id=%3CBasketID%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```

    </pre>

    <pre id="basket-delete-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in?basket_id=<BasketID>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));
            
        ```
    </pre>

</div>

<script>
    document.getElementById('basket-delete-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end delete basket order -->

<!-- start Add Basket Instrument -->

### Add Basket Instrument

You can add an instrument to a basket order by specifying the basket order identifier and the instrument details.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | basket order | https://pacetrader.pacefin.in/api/v1/basket/order | Add an instrument to a basket order |

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


#### Request Body
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

#### <h2> Code Examples:</h2>

<div id="basket-add-code-examples">
    <label for="basket-add-language-select">Select a Programming Language:</label>
    <select id="basket-add-language-select">
        <option value="basket-add-python">Python-http.client</option>
        <option value="basket-add-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-add-python-code" class="code-example">

        ```python
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

    </pre>

    <pre id="basket-add-javascript-code" class="code-example">

        ```javascript
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
    </pre>

</div>

<script>
    document.getElementById('basket-add-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end add basket instrument -->

<!-- start Edit Basket Instrument -->

### Edit Basket Instrument

You can edit an instrument in a basket order by specifying the basket order identifier and the instrument details.

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

#### <h2> Code Examples:</h2>

<div id="basket-edit-code-examples">
    <label for="basket-edit-language-select">Select a Programming Language:</label>
    <select id="basket-edit-language-select">
        <option value="basket-edit-python">Python-http.client</option>
        <option value="basket-edit-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-edit-python-code" class="code-example">

        ```python
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
    </pre>

    <pre id="basket-edit-javascript-code" class="code-example">

        ```javascript
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

    </pre>

</div>

<script>
    document.getElementById('basket-edit-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end edit basket instrument -->

<!-- start Delete Basket Instrument -->

### Delete Basket Instrument

You can delete an instrument from a basket order by specifying the basket order identifier and the instrument details.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | basket order | https://pacetrader.pacefin.in/api/v1/basket/order?basket_id=<BasketId>&name=<BasketName>&order_id=<OrderId> | Delete an instrument from a basket order |

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
| `name` | `string` | The name of the basket order.|
| `order_id` | `string` | The unique identifier of the order.|



#### Request Body
```json
{
  "basket_id": "<BasketId>",
  "name": "<BasketName>",
  "order_id": "<OrderId>"
}
```

#### <h2> Code Examples:</h2>

<div id="basket-delete-instrument-code-examples">
    <label for="basket-delete-instrument-language-select">Select a Programming Language:</label>
    <select id="basket-delete-instrument-language-select">
        <option value="basket-delete-instrument-python">Python-http.client</option>
        <option value="basket-delete-instrument-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-delete-instrument-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "basket_id": "<BasketId>",
        "name": "<BasketName>",
        "order_id": "<OrderId>"
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/basket/order?basket_id=%3CBasketId%3E&name=%3CBasketName%3E&order_id=%3COrderId%3E", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```
    </pre>

    <pre id="basket-delete-instrument-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "basket_id": "<BasketId>",
        "name": "<BasketName>",
        "order_id": "<OrderId>"
        });

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/basket/order?basket_id=<BasketId>&name=<BasketName>&order_id=<OrderId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```
    </pre>

</div>

<script>
    document.getElementById('basket-delete-instrument-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end delete basket instrument -->


<!-- start Rename Basket -->

### Rename Basket

You can rename a basket order by specifying the basket order identifier and the new name.

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

#### <h2> Code Examples:</h2>

<div id="basket-rename-code-examples">
    <label for="basket-rename-language-select">Select a Programming Language:</label>
    <select id="basket-rename-language-select">
        <option value="basket-rename-python">Python-http.client</option>
        <option value="basket-rename-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-rename-python-code" class="code-example">

        ```python
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
    </pre>

    <pre id="basket-rename-javascript-code" class="code-example">

        ```javascript
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

    </pre>

</div>

<script>
    document.getElementById('basket-rename-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end rename basket -->

<!-- start Execute Basket -->

### Execute Basket

You can execute a basket order by specifying the basket order identifier and the instrument details.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | basket order | https://pacetrader.pacefin.in/api/v1/orders/kart | Execute a basket order |

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
| `execution_type` | `string` | The execution type for the order (REGULAR, SPECIAL).|
| `name` | `string` | The name of the basket order.|
| `square_off` | `boolean` | The square off value of the order.|


#### Request Body
```json
{
    "basket_id": "<BasketId>",
    "execution_type": "NML",
    "name": "<BasketName>",
    "square_off": false
}
```

#### <h2> Code Examples:</h2>

<div id="basket-execute-code-examples">
    <label for="basket-execute-language-select">Select a Programming Language:</label>
    <select id="basket-execute-language-select">
        <option value="basket-execute-python">Python-http.client</option>
        <option value="basket-execute-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="basket-execute-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "basket_id": "<BasketId>",
        "execution_type": "NML",
        "name": "<BasketName>",
        "square_off": False
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/orders/kart", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="basket-execute-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "basket_id": "<BasketId>",
        "execution_type": "NML",
        "name": "<BasketName>",
        "square_off": false
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/orders/kart", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>


<script>
    document.getElementById('basket-execute-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>



<!-- end execute basket -->

<!-- start GTT Orders -->

## GTT Orders

### Create GTT Order

You can create a GTT order by specifying the instrument details and the trigger details.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `POST`       | gtt order | https://pacetrader.pacefin.in/api/v1/event/gtt | Create a GTT order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `action_type` | `string` | The action type for the GTT order (single_order, basket_order).|
| `expiry_time` | `string` | The expiry time for the GTT order. (yyyy-mm-dd)|
| `order` | `object` | The details of the order.|
| `order.client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `order.device` | `string` | The device type for the order (web).|
| `order.disclosed_quantity` | `integer` | The disclosed quantity of the order.|
| `order.exchange` | `string` | The exchange of the instrument. (NSE, BSE)|
| `order.instrument_token` | `integer` | The unique identifier of the instrument.|
| `order.market_protection_percentage` | `integer` | The market protection percentage of the order.|
| `order.order_side` | `string` | The order side for the order (BUY, SELL).|
| `order.order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `order.price` | `float` | The price of the order.|
| `order.product` | `string` | The product type for the order (CNC, MIS, NRML).|
| `order.quantity` | `integer` | The quantity of the order.|
| `order.sl_order_price` | `integer` | The stop loss order price of the order.|
| `order.sl_order_quantity` | `integer` | The stop loss order quantity of the order.|
| `order.sl_trigger_price` | `integer` | The stop loss trigger price of the order.|
| `order.trigger_price` | `integer` | The trigger price of the order.|
| `order.user_order_id` | `integer` | The unique identifier of the order.|


#### Request Body
```json
{
    "action_type": "single_order",
    "expiry_time": "2022-10-17",
    "order": {
        "client_id": "DEMO1",
        "device": "web",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "instrument_token": "11536",
        "market_protection_percentage": 0,
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 3611.45,
        "product": "CNC",
        "quantity": 1,
        "sl_order_price": 0,
        "sl_order_quantity": 0,
        "sl_trigger_price": 0,
        "trigger_price": 3611.45,
        "user_order_id": 10002
    }
}
```

#### <h2> Code Examples:</h2>

<div id="gtt-create-code-examples">
    <label for="gtt-create-language-select">Select a Programming Language:</label>
    <select id="gtt-create-language-select">
        <option value="gtt-create-python">Python-http.client</option>
        <option value="gtt-create-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="gtt-create-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "action_type": "single_order",
        "expiry_time": "2022-10-17",
        "order": {
            "client_id": "DEMO1",
            "device": "web",
            "disclosed_quantity": 0,
            "exchange": "NSE",
            "instrument_token": "11536",
            "market_protection_percentage": 0,
            "order_side": "BUY",
            "order_type": "LIMIT",
            "price": 3611.45,
            "product": "CNC",
            "quantity": 1,
            "sl_order_price": 0,
            "sl_order_quantity": 0,
            "sl_trigger_price": 0,
            "trigger_price": 3611.45,
            "user_order_id": 10002
        }
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("POST", "/api/v1/event/gtt", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="gtt-create-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "action_type": "single_order",
        "expiry_time": "2022-10-17",
        "order": {
            "client_id": "DEMO1",
            "device": "web",
            "disclosed_quantity": 0,
            "exchange": "NSE",
            "instrument_token": "11536",
            "market_protection_percentage": 0,
            "order_side": "BUY",
            "order_type": "LIMIT",
            "price": 3611.45,
            "product": "CNC",
            "quantity": 1,
            "sl_order_price": 0,
            "sl_order_quantity": 0,
            "sl_trigger_price": 0,
            "trigger_price": 3611.45,
            "user_order_id": 10002
        }
        });

        var requestOptions = {
        method: 'POST',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/event/gtt", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>


<script>
    document.getElementById('gtt-create-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>



<!-- end create gtt order -->

<!-- start Fetch GTT Order -->

### Fetch GTT Order

You can fetch a GTT order by specifying the GTT order identifier.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `GET`       | gtt order | https://pacetrader.pacefin.in/api/v1/event/gtt/<ClientId> | Fetch a GTT order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `client_id` | `string` | Your unique client identifier for the order <ClientId>.|


#### Request Body
```json
{
    "client_id": "<ClientId>"
}
```

#### <h2> Code Examples:</h2>

<div id="gtt-fetch-code-examples">
    <label for="gtt-fetch-language-select">Select a Programming Language:</label>
    <select id="gtt-fetch-language-select">
        <option value="gtt-fetch-python">Python-http.client</option>
        <option value="gtt-fetch-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="gtt-fetch-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("GET", "/api/v1/event/gtt/<ClientId>", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```
    </pre>

    <pre id="gtt-fetch-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'GET',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/event/gtt/<ClientId>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>


<script>
    document.getElementById('gtt-fetch-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>

<!-- end fetch gtt order -->


<!-- start Cancel GTT Order -->

### Cancel GTT Order

You can cancel a GTT order by specifying the GTT order identifier.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `DELETE`       | gtt order | https://pacetrader.pacefin.in/api/v1/event/gtt/<ClientId>/<Id> | Cancel a GTT order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |

#### parameters
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

#### <h2> Code Examples:</h2>

<div id="gtt-cancel-code-examples">
    <label for="gtt-cancel-language-select">Select a Programming Language:</label>
    <select id="gtt-cancel-language-select">
        <option value="gtt-cancel-python">Python-http.client</option>
        <option value="gtt-cancel-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="gtt-cancel-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = ''
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("DELETE", "/api/v1/event/gtt/<ClientId>/<Id>", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))
        ```
    </pre>

    <pre id="gtt-cancel-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var requestOptions = {
        method: 'DELETE',
        headers: myHeaders,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/event/gtt/<ClientId>/<Id>", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>


<script>
    document.getElementById('gtt-cancel-language-select').addEventListener('change', function () {
        var selectedLanguage = this.value;
        document.querySelectorAll('.code-example').forEach(function (codeExample) {
            codeExample.style.display = 'none';
        });

        document.getElementById(selectedLanguage + '-code').style.display = 'block';
    });

</script>


<!-- end cancel gtt order -->

<!-- start Modify GTT Order -->

### Modify GTT Order

You can modify a GTT order by specifying the GTT order identifier and the new details.

| Request Type | APIs    | Endpoint                               | Description                     |
|-------------- | ------- | -------------------------------------- | --------------------------------- |
| `PUT`       | gtt order | https://pacetrader.pacefin.in/api/v1/event/gtt | Modify a GTT order |

#### Headers
| Header | Value |
|-------------- | ------- |
| x-device-type | WEB |
| x-auth-token | (Your authorization token) |
| content-type | application/json |


#### parameters
| Parameter | Type | Description |
|-------------- | ------- | ------- |
| `expiry_time` | `string` | The expiry time for the GTT order. (yyyy-mm-dd)|
| `order` | `object` | The details of the order.|
| `order.client_id` | `string` | Your unique client identifier for the order <ClientId>.|
| `order.device` | `string` | The device type for the order (web).|
| `order.disclosed_quantity` | `integer` | The disclosed quantity of the order.|
| `order.exchange` | `string` | The exchange of the instrument. (NSE, BSE)|
| `order.instrument_token` | `string` | The unique identifier of the instrument.|
| `order.market_protection_percentage` | `integer` | The market protection percentage of the order.|
| `order.order_side` | `string` | The order side for the order (BUY, SELL).|
| `order.order_type` | `string` | The order type for the order (LIMIT, MARKET, SL, SLM).|
| `order.price` | `float` | The price of the order.|
| `order.product` | `string` | The product type for the order (CNC, MIS, NRML).|
| `order.quantity` | `integer` | The quantity of the order.|
| `order.sl_order_price` | `integer` | The stop loss order price of the order.|
| `order.sl_order_quantity` | `integer` | The stop loss order quantity of the order.|
| `order.sl_trigger_price` | `integer` | The stop loss trigger price of the order.|
| `order.trigger_price` | `float` | The trigger price of the order.|
| `order.user_order_id` | `integer` | The unique identifier of the order.|


#### Request Body
```json
{
    "expiry_time": "2022-10-17",
    "order": {
        "client_id": "DEMO1",
        "device": "web",
        "disclosed_quantity": 0,
        "exchange": "NSE",
        "instrument_token": "11536",
        "market_protection_percentage": 0,
        "order_side": "BUY",
        "order_type": "LIMIT",
        "price": 3611.45,
        "product": "CNC",
        "quantity": 1,
        "sl_order_price": 0,
        "sl_order_quantity": 0,
        "sl_trigger_price": 0,
        "trigger_price": 3611.45,
        "user_order_id": 10002
    }
}
```

#### <h2> Code Examples:</h2>

<div id="gtt-modify-code-examples">
    <label for="gtt-modify-language-select">Select a Programming Language:</label>
    <select id="gtt-modify-language-select">
        <option value="gtt-modify-python">Python-http.client</option>
        <option value="gtt-modify-javascript">JavaScript-Fetch</option>
    </select>
    <pre id="gtt-modify-python-code" class="code-example">

        ```python
        import http.client
        import json

        conn = http.client.HTTPSConnection("pacetrader.pacefin.in")
        payload = json.dumps({
        "expiry_time": "2022-10-17",
        "order": {
            "client_id": "DEMO1",
            "device": "web",
            "disclosed_quantity": 0,
            "exchange": "NSE",
            "instrument_token": "11536",
            "market_protection_percentage": 0,
            "order_side": "BUY",
            "order_type": "LIMIT",
            "price": 3611.45,
            "product": "CNC",
            "quantity": 1,
            "sl_order_price": 0,
            "sl_order_quantity": 0,
            "sl_trigger_price": 0,
            "trigger_price": 3611.45,
            "user_order_id": 10002
        }
        })
        headers = {
        'x-device-type': 'WEB',
        'x-authorization-token': 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg',
        'content-type': 'application/json'
        }
        conn.request("PUT", "/api/v1/event/gtt", payload, headers)
        res = conn.getresponse()
        data = res.read()
        print(data.decode("utf-8"))

        ```

    </pre>

    <pre id="gtt-modify-javascript-code" class="code-example">

        ```javascript
        var myHeaders = new Headers();
        myHeaders.append("x-device-type", "WEB");
        myHeaders.append("x-authorization-token", "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJibGFja2xpc3Rfa2V5IjoiQ0xJRU5UMTpURGYvZ1RKUUNFSytsWGJ1L21yenF3IiwiY2xpZW50X2lkIjoiQ0xJRU5UMSIsImNsaWVudF90b2tlbiI6InlKeDI0dFdmUUlsSnloUnVWbVVKeXciLCJkZXZpY2UiOiJ3ZWIiLCJleHAiOjE2NjQ0Mzk3ODE2NTZ9.LP70t5kXSBtO0iflzG2lo3lvs8wj9_HpHRjOPSHSBpg");
        myHeaders.append("content-type", "application/json");

        var raw = JSON.stringify({
        "expiry_time": "2022-10-17",
        "order": {
            "client_id": "DEMO1",
            "device": "web",
            "disclosed_quantity": 0,
            "exchange": "NSE",
            "instrument_token": "11536",
            "market_protection_percentage": 0,
            "order_side": "BUY",
            "order_type": "LIMIT",
            "price": 3611.45,
            "product": "CNC",
            "quantity": 1,
            "sl_order_price": 0,
            "sl_order_quantity": 0,
            "sl_trigger_price": 0,
            "trigger_price": 3611.45,
            "user_order_id": 10002
        }
        });

        var requestOptions = {
        method: 'PUT',
        headers: myHeaders,
        body: raw,
        redirect: 'follow'
        };

        fetch("https://pacetrader.pacefin.in/api/v1/event/gtt", requestOptions)
        .then(response => response.text())
        .then(result => console.log(result))
        .catch(error => console.log('error', error));

        ```

    </pre>

</div>



