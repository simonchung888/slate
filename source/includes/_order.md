# Order

## Order List

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/list` |
| Method | `post` |
| Use | to get the order list in the company. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "orders": [{
    "number": "AAAA160401000002OD",
    "currency": "JPY",
    "total": 24288,
    "order_status": "Cancelled",
    "payment_status": "Closed",
    "transaction_id": "",
    "create_at": 1459491797,
    "refund_at": 1459491797,
    "retailer": {
      "id": 1,
      "name": "Company A"
    },
    "agent": {
      "id": 1,
      "given_name": "QQ",
      "family_name": "Wang",
      "email": "a@gamil.com"
    }
  },{
    "number": "AAAA160401000001OD",
    "currency": "CHF",
    "total": 284.04,
    "order_status": "Open",
    "payment_status": "Open",
    "create_at": 1459491797,
    "refund_at": 1459491797,
    "retailer": {
      "id": 1,
      "name": "Company A"
    },
    "agent": {
      "id": 1,
      "given_name": "QQ",
      "family_name": "Wang",
      "email": "a@gamil.com"
    }
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | order number |
| currency | string | payment currency |
| total | double | order total price |
| order_status | string | order status |
| payment_status | string | payment status |
| transaction_id | string | transaction id  |
| create_at | timestamp | create time (s) |
| refund_at | timestamp | refund time (s) |
| **retailer** | **object** |  |
| *id* | integer | company id |
| *name* | string | company name |
| **agent** | **object** |  |
| *id* | integer | user id |
| *given_name* | string | user given name |
| *family_name* | string | user family name |
| *email* | string | user email |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**|


## Create Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/create` |
| Method | `post` |
| Use | to create order. App uploads cart data to backend, backend create order and send order id to app |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "cart_id":"C00001",
  "type": "credir_card"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| cart_id | integer | cart  id |
| type | string | "credit_card" or “cash" or "PayPal" |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "order_number":"AAAA160509000001OD",
  "payment_method": "PayPal",
  "qrcode": ""
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| order_number | string | order number |
| payment_method | string | payment method, "credit_card" or “cash" or "PayPal" |
| qrcode | string | payment link for PayPal, others is null |

<aside class="warning">
Failure
</aside>

```json
{
  "products": [
    "AAAA0000000001",
    "AAAB0000000001"
  ],
  "err_name":"product invalid"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:** cannot sell in the company|
|||**repeat:**  the order already been created. |
|||**no products:** can’t order if no product in the cart |
|||**product invalid:** some products which had be deleted, but its still in the cart. Server will return these product number to data. |


## Order Payment

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/payment/` |
| Method | `post` |
| Use | to complete order. App uploads transaction id to backend, so that backend can verify data with payworks |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "C00001",
  "transaction_id": "UXI2KS784JOC9A0"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | order number |
| transaction_id | string | transaction id with payworks |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**|
|||**order not exist:**  order is not exist|
|||**not retailer order:**|
|||**repeated:** transaction is exist|
|||**paid:** order has been paid |
|||**confirming:**  order is confirming|
|||**closed :** order has been closed|
|||**refunded:** order has been refunded|
|||**request timeout:** the api request too late|


## Cancel Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/cancel` |
| Method | `post` |
| Use | to cancel order which not payment yet or some error happened in payment. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "C00001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | order number |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**|
|||**order not exist:**  order is not exist|
|||**paid:** order has been paid |
|||**confirming:**  order is confirming|
|||**closed :** order has been closed|
|||**refunded:** order has been refunded|


## Refund

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/refund` |
| Method | `post` |
| Use | to refund order. App uploads transaction id to backend, so that backend can verify data with payworks |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "transaction_id": "UXI2KS784JOC9A0",
  "order_number": "C00001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| transaction_id | string | transaction id with payworks to refund order which using cash to pay, if transaction id is empty |
| order_number | string | order number |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:**|
|||**order not exist:**  order is not exist|
|||**refund expired:** after the order has been created over 30 days, it can't refund|
|||**repeated:** transaction is exist|
|||**confirming:**  order is confirming|
|||**closed :** order has been closed|
|||**refunded:** order has been refunded|
|||**open:**  initial order status|
|||**order not paid:**  order not paid yet|
|||**timeout:** cannot connect to server of third-party-payment |
|||**transaction not found:** the transaction not be found from third-party-payment |
|||**invalid tansaction id:** the transaction data which get from third-party-payment, its status error, abort or not refund|


## Order   Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/detail` |
| Method | `post` |
| Use | to get the order detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "AAAA160401000001OD"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | order number |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
  "number": "AAAA160401000003OD",
  "currency": "JPY",
  "subtotal": 25300,
  "totalDiscount": 886,
  "total": 24414,
  "order_status": "Open",
  "payment_status": "Open",
  "payment_method": null,
  "transaction_id": null,
  "create_at": 1459491885,
  "refund_at": 1459491885,
  "retailer": {
    "id": 1,
    "name": "Company A"
  },
  "agent": {
    "id": 1,
    "given_name": "QQ",
    "family_name": "Wang",
    "email": "a@gmail.com"
  },
  "products": [{
    "number": "AAAA0000000004PD",
    "company": {
      "id": 1,
      "name": "Company Test"
    },
    "item": {
      "id": 1,
      "number": "Test-Item-1",
      "name": "Test Item 1"
    },
    "variant": {
      "id": 2,
      "name": "Variant Test"
    },
    "price": 100,
    "discount": 15,
    "discount_price": 85,
    "product_status": "initial"
  },{
    "product_num": "AAAA0000000005PD",
    "company": {
      "id": 1,
      "name": "Company Test"
    },
    "item": {
      "id": 1,
      "number": "Test-Item-1",
      "name": "Test Item 1"
    },
    "variant": {
      "id": 2,
      "name": "Variant Test"
    },
    "price": 100,
    "discount": 15,
    "discount_price": 85,
    "product_status": "initial"
  }],
  "histories": [{
    "order_status": "Open",
    "payment_status": "Open",
    "comment": "",
    "create_at": 1461312001,
    "user": {
      "id": 1,
      "given_name": "QQ",
      "family_name": "Wang"
    }
  },{
    "order_status": "Error",
    "payment_status": "Closed",
    "comment": "request timeout",
    "create_at": 1461312055,
    "user": {
      "id": 1,
      "given_name": "QQ",
      "family_name": "Wang"
    }
  }],
  "shipping_address": {
    "title": null,
    "given_name": null,
    "family_name": null,
    "phone": null,
    "email": null,
    "street": null,
    "city": null,
    "state": null,
    "code": null,
    "country": null
  },
  "billing_address": {
    "title": null,
    "given_name": null,
    "family_name": null,
    "phone": null,
    "email": null,
    "street": null,
    "city": null,
    "state": null,
    "code": null,
    "country": null
  },
  "invoices": [{
    "number": "AAAA170329000006IN",
    "brand": {
      "id": 1,
      "name": "Company A"
    },
    "create_at": 1490776038,
    "comment": "AAAA170329000001OD",
    "download": "http://192.168.1.116/BrandCloud/order/AAAA170329000001OD/invoice/AAAA170329000006IN/download"
  }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| number | string | order number |
| currency | string | payment currency |
| total | double | order total price |
| order_status | string | order status |
| payment_status | string | payment status |
| payment_method | string | payment method |
| transaction_id | string | transaction id |
| create_at | timestamp | create time |
| refund_at | timestamp | refund time |
| **retailer** | **object** | |
| *id* | integer | company  id |
| *name* | string | company name |
| **agent** | **object** |  |
| *id* | integer | user id |
| *given_name* | string | sell agent’s given name |
| *family_name* | string | sell agent’s family name |
| **＊_address** | **object** | billing_address, shipping_address |
| *given_name* | string | recipient’s given_name |
| *family_name* | string | recipient’s family_name |
| *phone* | string | recipient’s phone number |
| *title* | integer | recipient’s title (0=Mr. 1=Ms.) |
| *email* | string | recipient’s email |
| *street* | string | recipient’s address |
| *city* | string | recipient’s address |
| *state* | string | recipient’s address |
| *code* | string | recipient’s address |
| *country* | string | recipient’s address |
| **products** | **array** |  |
| *number* | string | product number |
| **company** | **object** | company of product |
| *id* | string | company id of product |
| *name* | string | company name of product |
| **item** | **object** | item of product |
| *id* | integer | item id of products |
| *number* | string | item number of product |
| *name* | string | item name of product |
| **variant** | **object** | variant of product |
| *id* | string | variant id of product |
| *name* | string | variant name of product |
| *price* | double | product price |
| *discount* | integer | product discount |
| *discount_price* | double | product discount price |
| *product_status* | string | the location of work flow of product |
| **histories** | **array** |  |
| *order_status* | *string* | order status |
| *payment_status* | *string* | payment status |
| *comment* | string |  record the exception message when order been changed |
| *create_at* | timestamp | order status changed time |
| **user** | **object** | who do this action |
| *id* | integer | user id |
| *given_name* | string | user’s given name |
| *family_name* | string |  user’s family name |
| **invoices** | **array** | invoices list|
| *number* | string | invoice number|
| *brand* | *object* | invoice creator |
| *id* | integer | company id |
| *name*| string | company name |
| *create_at* | timestamp | creating time of invoice |
| *comment* | *string* | order number |
| *download* | *string* | downloading url of invoice, visit the url need to add header Authorization and value is api_key |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**no permission:** cannot sell in the company|
|||**order not exist:** order number is incorrect|


## Send PayPal Payment Link

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/paypal/send` |
| Method | `post` |
| Use | to send PayPal Payment link to consumer. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "email": "a@gmail.com",
    "order_number": "AAAA0000000789OD"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| email | string | consumer email |
| order_number | string | order number which consumer want to pay by PayPal buy no scanner |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type |
||| **does not signin:** user does not signin |
||| **order not exist:** invalid order number |
||| **invalid email:** invalid email |
||| **invalid payment:** only PayPal can use this api |
||| **paid:** order has been paid |
||| **confirming:**  order is confirming |
||| **closed :** order has been closed |
||| **refunded:** order has been refunded |


## Transaction Result

### Description

| Title | Description |
| -------: | :---- |
| URL | `transaction/{token}/result` |
| Method | `get` |
| Use | to get the information for PayPal payment. |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "token": "e4cbcdc2faff41a7e311"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| token | string | a temporary token for payment. |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"date": 1459491797,
	"status": "success",
	"odrer": {
		"number": "AAAA170329000001OD",
		"payment_method": "PayPal",
		"transaction": "123546876",
		"currency": "EUR",
		"total": 100,
		"retailer": "TW Shop",
		"payer": "a@gmail.com"
	}
}
```

```json
{
	"date": 1459491797,
	"status": "fail",
	"fail": {
		"refused_by": "PayPal",
		"code": "012",
		"description": "card expired"
	}
}
```

```json
{
	"date": 1459491797,
	"status": "info"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| date | timestamp | payment date |
| status | string | payment status, success or fail or info <br /> the order parameter will appear if the status is success otherwise, the fail parameter will appear |
| **odrer** | **object (option)** | order information |
| *number* | string | order number |
| *payment_method* | string | payment method of order |
| *transaction* | string | transaction id of order |
| *currency* | string | payment currency |
| *total* | number | total price of payment |
| *retailer* | string | seller's company name |
| *payer* | string | payer email |
| **fail** | **object (option)** | fail information |
| *refused_by* | string | By whom was this action refused, Server or PayPal |
| *code* | string | fail code of PayPal |
| *description* | string | fail description |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name":"log expired"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | the name of the wrong type |
||| **result not exist:** order number invalid |


## Query Refund Requirement Of Order

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/order/refund/query` |
| Method | `post` |
| Use | To check the order meets refund requirement |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
  "api_key": "e4cbcdc2faff41a7e311",
  "order_number": "C00001"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| order_number | string | Order number |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| (Nothing return) | - | - |

<aside class="warning">
Failure
</aside>

```json
{
  "error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
|||**lack of parameters:** the request does not include the necessary parameters|
|||**does not signin:** user does not signin|
|||**not select company yet:** user need change current company|
|||**company not exist:** currenct company not exist|
|||**not company member:** the user is not the company member|
|||**order not exist:**  order is not exist|
|||**refund expired:** after the order has been created over 30 days, it can't refund|
|||**confirming:**  order is confirming|
|||**closed :** order has been closed|
|||**refunded:** order has been refunded|
|||**open:**  initial order status|