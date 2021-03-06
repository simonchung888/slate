# Company

## Search Companies

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/search` |
| Method | `post` |
| Use | To get relative companies by company name |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"search_text": "CC"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| search_text | string | A keyword about the company name |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
[{
	"id": 1,
	"name": "CC Shop",
	"cover_image": {
		"240p": "http://abc/xxx_240p.jpg",
		"480p": "http://abc/xxx_480p.jpg",
		"720p": "http://abc/xxx_720p.jpg",
		"1080p": "http://abc/xxx_1080p.jpg"
	},
	"owner": {
		"id": 1,
		"given_name": "Wang",
		"family_name": "Jianhua",
		"email": "a@gmail.com"
	}
}, {
	"id": 2,
	"name": "CC Bike",
	"cover_image": {},
	"owner": {
		"id": 1,
		"given_name": "Wang",
		"family_name": "Jianhua",
		"email": "a@gmail.com"
}
}]
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | number | The company id |
| name | string | The company name |
| **cover_image** | **object** | The company’s cover image <br /> If no set cover image, return empty |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| **owner** | **object** | The founder information of company |
| *id* | integer | The user id of founder |
| *given_name* | string | The given name of founder |
| *family_name* | string | The family name of founder |
| *email* | string | The email of founder |


<aside class="warning">
Failure
</aside>

```
{
	"error_name":"lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |



## Company List Of User

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/list` |
| Method | `post` |
| Use | to get all companies of user |
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
	"companies":[{
		"id": 2,
		"name": "CC Bike",
		"cover_img": {},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		},
		"selected": false,
		"currency": "EUR"
	}],
	"companies_with_option":[{
		"id": 3,
		"name": "CC Bike",
		"cover_img": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		},
		"selected": true,
		"currency": "CHF"
	}],
	"current_company":{
		"id": 2,
		"name": "CC Bike",
		"cover_img": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		},
		"owner": {
			"id": 1,
			"given_name": "Wang",
			"family_name": "Jianhua",
			"email": "a@gmail.com"
		},
		"selected": true,
		"currency": "CHF"
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **companies** | **array** | all companies in the system. Order by company name from A-Z |
| id | number | company’s id |
| name | string | company name |
| cover_image | **object** | company’s cover image.If no set cover image, return empty. **Include:** |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| owner | **object** | company owner's information. **Include:** |
| *id* | integer | owner's user id |
| *given_name* | string | owner given_name |
| *family_name* | string | owner family_name |
| *email* | string | owner email |
| selected | boolean | current company |
| currency | string | default currency of company |
| companies_with_option | array | companies which has signed with current companies. Content is same to above companies. |
| current_company | array | Current companies. Content is same to above companies. |



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



## Create Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/create` |
| Method | `post` |
| Use | To create company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"short_number": "AAAA",
	"name": "CC Bike",
	"website": "",
	"description": "",
	"street": "",
	"city": "",
	"state": "",
	"postal_code": "",
	"system_country_id": 228,
	"contact_given_name":  "Jianhua",
	"contact_family_name":  "Wang",
	"contact_job_title":  "coder",
	"contact_phone":  "0987654321",
	"contact_email":  "abc@gmail.com",
	"images":[{
		"name": "xxx.jpg",
		"cover": 1
	}, {
		"name": "xxx.jpg",
		"cover": 0
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| short_number | string | The company short number, four letter and uppercase |
| name | string | The company name |
| website | string (option) | The company website link |
| description | string (option) | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string (option) | The state of company |
| postal_code | string | The postal code of company |
| system_country_id | integer | The system country id |
| contact_given_name | string | The given name of contactor |
| contact_family_name | string | The family name of contactor |
| contact_job_title | string | The job title of contactor |
| contact_phone | string | The phone number of contactor |
| contact_email | string | The email of contactor |
| **images** | **array (option)** | The company images |
| *name* | string | The file name which get from API after uploded image |
| *cover* | boolean | The tag decide image is covered or not <br /> false: normal image <br /> true: cover image|


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | The company id |


<aside class="warning">
Failure
</aside>

```json
{
	"error_name": "illegal form input",
	"validation": {
		"name": ["dulicate"],
		"country": ["required"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
|||**lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **illegal form input:** The data validation failed |
| **validation** | **object** | The validation parameter will appear if the error_name is illegal form input |
| *short_number* | array | **required:** The data cannot be empty or null |
|||**dulicate:** The short number has already been taken|
|||**invalid value:** The short number not be allow to use|
| *name* | array | **required:** The data cannot be empty or null |
|||**dulicate:** The name has already been taken |
| *street* | array | **required:** The data cannot be empty or null |
| *city* | array | **required:** The data cannot be empty or null |
| *state* | array | **required:** The data cannot be empty or null |
| *postal_code* | array | **required:** The data cannot be empty or null |
| *country* | array | **invalid country:** The country not exist |
| *contact_given_name* | array | **required:** The data cannot be empty or null |
| *contact_family_name* | array | **required:** The data cannot be empty or null |
| *contact_job_title* | array | **required:** The data cannot be empty or null |
| *contact_phone* | array | **required:** The data cannot be empty or null |
| *contact_email* | array | **required:** The data cannot be empty or null |



## Get Company Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/detail` |
| Method | `post` |
| Use | To get the company detail |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": "1"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |


> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"short_number": "AAAA",
	"name": "CC Bike",
	"website": "",
	"description": "",
	"street": "",
	"city": "",
	"province": "",
	"postal_code": "",
	"country": {
        "id": 228,
        "name": "taiwan"
    },
	"contact_given_name": "XX",
	"contact_family_name": "X",
	"contact_job_title": "xxx",
	"contact_phone": "0987654321",
	"contact_email": "abc@gmail.com",
	"owner": {
		"id": 1,
		"given_name": "Wang",
		"family_name": "Jianhua",
		"email": "a@gmail.com"
	},
	"members": [{
		"id": 1,
		"given_name": "QQ",
		"family_name": "Wang",
		"email": "a@gmail.com",
		"administrator": 1,
		"manager": 1,
		"role": {
			"id": 1,
			"name": "Unsigned"
		}
	}],
	"role": [{
		"id": 1,
		"name": "Unsigned",
		"default": 1,
		"permissions": {
			"item": {
				"view": 0,
				"edit": 0,
				"delete": 0
			}
		},
			"product": {
				"view": 0,
				"edit": 0,
				"delete": 0
			},
			"option": {
				"view": 0,
				"edit": 0,
				"delete": 0
			},
			"order": {
				"view": 0,
				"edit": 0,
				"delete": 0
			},
			"sell": 0
	}],
	"images":[{
		"name": "xxx.jpg",
		"cover": true,
		"resource": {
			"240p": "http://abc/xxx_240p.jpg",
			"480p": "http://abc/xxx_480p.jpg",
			"720p": "http://abc/xxx_720p.jpg",
			"1080p": "http://abc/xxx_1080p.jpg"
		}
	}, {
		"name": "yyy.jpg",
		"cover": false,
		"resource": {
			"240p": "http://abc/yyy_240p.jpg",
			"480p": "http://abc/yyy_480p.jpg",
			"720p": "http://abc/yyy_720p.jpg",
			"1080p": "http://abc/yyy_1080p.jpg"
		}
	}],
	"currencies": [{
		"id": 1,
		"name": "EUR",
		"default": 1,
		"exchange_rate": 0,
		"display_precision_point": 2
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | company id|
| short_number | string | The company short number |
| name | string | The company name |
| website | string | The company website link |
| description | string | The company description |
| street | string | The street address of company |
| city | string | The city of company |
| state | string | The state of company |
| postal_code | string | The postal code of company |
| **country** | **object** | The country of company |
| *id* | integer | country id |
| *name* | string | country name |
| contact_given_name | string | The given name of contactor |
| contact_family_name | string | The family name of contactor |
| contact_job_title | string | The job title of contactor |
| contact_phone | string | The phone number of contactor |
| contact_email | string | The email of contactor |
| **images** | **array** | The company images |
| *name* | string | The image name |
| *cover* | boolean | Is cover image <br /> false: normal image <br /> true: cover image |
| **resource** | **object** | The resolution of picture |
| *240p* | string | picture url of 240 resolution (426x240) |
| *480p* | string | picture url of 480 resolution (854x480) |
| *720p* | string | picture url of 720 resolution (1280x720) |
| *1080p* | string | picture url of 1080 resolution (1920x1080) |
| **owner** | **object** | The information of company owner |
| *id* | integer | The user id |
| *given_name* | string | The user given name |
| *family_name* | string | The owner family name |
| *email* | string | The user email |
| **members** | **array** | The members of company |
| *id* | integer | The user id |
| *given_name* | string | The user given name |
| *family_name* | string | The user family name |
| *email* | string | The user email |
| **role** | **object** | member's role of company |
| *id* | integer | The role id in the company |
| *name* | string | The role name in the company |
| *administrator* | boolean | The administrator identify in the company |
| *manager* | boolean | The highest manager in the company |
| **roles** | **array** | roles of company |
| id | integer | role id |
| name | string | role name |
| default | boolean | default currency |
| permissions | **object** | permission of role |
| *item* | object | permission detail |
||| **view:**  [boolean] user can view |
||| **edit:**  [boolean] user can add and edit |
||| **delete:**  [boolean] user can delete |
| *product* | object | permission detail, as item. |
| *option* | object | permission detail, as item. |
| *order* | object | permission detail, as item. |
| *sell* | boolean | user can sell. |
| **currencies** | **array** | currencies which company own |
| *id* | number | The currency id of system|
| *name* | string | The currency name |
| *default* | boolean | The default currency of company |
| *exchange_rate* | number | The exchange rate of currency in the company|
| *display_precision_point* | integer | The precision point of currency. Display_precision_point > 0 indicate the digits of presicion <br /> ex: If the display_precision_point is 2, than the price should round to 9.12 from 9.119 |

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
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |



## Edit Company Profile

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/profile` |
| Method | `post` |
| Use | To edit company profile |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"name": "CC Bike",
	"website": "",
	"description": "",
	"street": "",
	"city": "",
	"state": "",
	"postal_code": "",
	"system_country_id": 228,
	"contact_given_name":  "Jianhua",
	"contact_family_name":  "Wang",
	"contact_job_title":  "coder",
	"contact_phone":  "0987654321",
	"contact_email":  "abc@gmail.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| name | string | The company name |
| website | string (option) | The company website link |
| description | string (option) | The company description |
| street | string | The street of company |
| city | string | The city of company |
| state | string (option) | The state of company |
| postal_code | string | The postal code of company |
| system_country_id | integer | The system country id |
| contact_given_name | string | The given name of contactor |
| contact_family_name | string | The family name of contactor |
| contact_job_title | string | The job title of contactor |
| contact_phone | string | The phone number of contactor |
| contact_email | string | The email of contactor |



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
	"error_name": "illegal form input",
	"validation": {
		"name": ["dulicate"],
		"country": ["required"]
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **not company member:** The user are not member in this company or no option with this company |
||| **company not exist:** The company not exist |
||| **no permission:** The permission deny |
|| |**illegal form input:** The data validation failed |
| **validation** | **object** | The validation parameter will appear if the error_name is illegal form input |
| *name* | array | **required:** The data cannot be empty or null |
|||**dulicate:** The name has already been taken |
| *street* | array | **required:** The data cannot be empty or null |
| *city* | array | **required:** The data cannot be empty or null |
| *state* | array | **required:** The data cannot be empty or null |
| *postal_code* | array | **required:** The data cannot be empty or null |
| *country* | array | **invalid country:** The country not exist |
| *contact_given_name* | array | **required:** The data cannot be empty or null |
| *contact_family_name* | array | **required:** The data cannot be empty or null |
| *contact_job_title* | array | **required:** The data cannot be empty or null |
| *contact_phone* | array | **required:** The data cannot be empty or null |
| *contact_email* | array | **required:** The data cannot be empty or null |



## Edit Company Images

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/image` |
| Method | `post` |
| Use | to edit company image |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"images":[{
			"name": "xxx.jpg",
			"cover": true
		}, {
			"name": "xxx.jpg",
			"cover": false
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| **images** | **array** | The company images |
| *name* | string | The file name which get from API after uploded image |
| *cover* | boolean | The tag decide image is covered or not <br /> false: normal image <br /> true: cover image|


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
	"error_name": "company not exist"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:** The permission deny |



## Add Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/add/member` |
| Method | `post` |
| Use | To add user into company as member |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| email | string | The user email |


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
	"error_name": "duplicate join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **duplicate join:** The user email is already joined to this company |
||| **user not exist:** The email is incorrent |



## Edit Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/member` |
| Method | `post` |
| Use | To edit authority of company member |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com",
	"role_id": 1,
	"adminstrator": false
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| email | string | The user email |
| role_id | integer | The role id of company |
| administrator | boolean | Is company administrator |


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
	"error_name": "not join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **not join:** The user email not join to this company |
||| **user not exist:** email is incorrent |
||| **role not exist:** role id is incorrent |



## Delete Company Member

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/delete/member` |
| Method | `post` |
| Use | To remove user from company member |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"email": "cc.lee@prophetdigits.com"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| email | string | The user email |

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
	"error_name": "not join"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string | The failed reason which HTTP code is 403 |
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **not join:** The user email not join to this company |
||| **user not exist:** email is incorrent |



## Create Company Role

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/create/role` |
| Method | `post` |
| Use | to create role into company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"name": "CEO"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| name | string | role name |


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
	"error_name": "no permission"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|



## Delete Company Role

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/delete/role` |
| Method | `post` |
| Use | to delete company role |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"role_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | string | company id |
| role_id | integer | role id of company |


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
	"error_name": "no permission"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  if the value of success is false, web backend needs to assign the name of  error, unless this parameter should be empty: Valid Value:|
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** user are not member in this company or no option with this company|
|||**company not exist:** company not exist|
|||**no permission:**  not company administrator|
|||**role not exist:** role id incorrent|
|||**default role:** default role cannot be deleted|



## Edit Company Currencies

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/edit/currency` |
| Method | `post` |
| Use | To edit company currencies |
| Notice ||


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1,
	"currencies": [{
		"currency_id": 1,
		"exchange_rate": 0.3,
		"default": true
	}]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |
| **currencies** | **array** | The company currencies |
| *currency_id* | integer | The currency id |
| *exchange_rate* | number | The default currency to specific currency exchange rate |
| *default* | boolean | Is default currency |


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
||| **lack of parameters:** Some required parameters missing in the request |
||| **does not signin:** The user does not signin |
||| **company not exist:** The company not exist |
||| **not company member:** The user are not member in this company or no option with this company |
||| **no permission:**  Not company administrator |
||| **duplicate default currency:** Two currencies is setted as the default currency |
||| **no default currency:** No currencies is setted as the default currency |



## Authority Of Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/auth` |
| Method | `post` |
| Use | to get authority of currency |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_id | integer | company_id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
	"manager": {
		"profile":{
			"edit": false
		},
		"member": {
			"edit": false,
			"delete": false
		},
		"role": {
			"edit": false,
			"delete": false
		},
		"currency": {
			"edit": false
		}
	},
	"role": {
		"item":{
			"view": true,
			"edit": false,
			"delete": false
		},
		"product": {
			"view": true,
			"edit": false,
			"delete": false
		},
		"option": {
			"view": true,
			"edit": false,
			"delete": false
		},
		"order": {
			"view": true,
			"edit": false,
			"delete": false
		},
		"sell": true
	}
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **manager** | **object** | user's authority in the company |
| *profile* | object | **edit:** [boolean] user can edit company profile|
|||**delete:** [boolean] user can delete member|
| *member* | object | **edit:** [boolean] user can add and edit member|
| *role* | object | **edit:** [boolean] user can add and edit role|
|||**delete:** [boolean] user can delete role|
| *currency* | object | **edit:** [boolean] user can add and edit currency|
| **role** | **object** | user permissions in the company |
| *item* | object | permission detail |
||| **view:**  [boolean] user can view |
||| **edit:**  [boolean] user can add and edit |
||| **delete:**  [boolean] user can delete |
| *product* | object | permission detail, as item. |
| *option* | object | permission detail, as item. |
| *order* | object | permission detail, as item. |
| *sell* | boolean | user can sell. |

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
|||**not company member:** doesn’t join to this company|
|||**no permission:** not company manager|


## Change Current Company

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/select/company` |
| Method | `post` |
| Use | change app’s global company to operate app functions |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
	"api_key": "e4cbcdc2faff41a7e311",
	"company_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | An unique token after user sign in, then user can use it to request data from API |
| company_id | integer | The company id |


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
|||**lack of parameters:** some input parameters missing, not in the request|
|||**does not signin:** user does not signin|
|||**not company member:** doesn’t join to this company|
|||**company not exist:** the company is not exist|


## Generate Company Short Number

### Description

| Title | Description |
| -------: | :---- |
| URL | `user/company/short_number/generate` |
| Method | `post` |
| Use | to get company short number which be generated by system |
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
	"short_number": "AAAA"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| short_number | string | short number of company |

<aside class="warning">
Failure
</aside>

```json
{
	"error_name": "illegal form input"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | String |  the name of the wrong type.|
|||Value:|
|||**lack of parameters:**  the request does not include the necessary parameters|
|||**does not signin:** user does not signin|



## Get Company Country List

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/country/list |
| Method | `post` |
| Use | to get countries of company |
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
    "countries": [{
        "company_country_id": 2,
        "id": 228,
        "name": "Taiwan",
        "importers": 2
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| **countries** | **array** | countries of company |
| *company_country_id* | integer | company country id |
| *id* | integer | country id |
| *name* | string | country name |
| *importers* | integer | importer number in the country |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |


## Get Company Country Detail

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/country/detail |
| Method | `post` |
| Use | to get detail of countries of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_country_id": 1
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_country_id | integer | company country id |

> Return Parameters

### Return Parameters

<aside class="success">
Success
</aside>

```json
{
    "id": 2,
    "country_id": 228,
    "fixed_vat": 10,
    "adjusted_vats": [{
        "id": 1,
        "name": "fruit",
        "rate": 5,
        "comment": "",
        "items": []
      }, {
        "id": 2,
        "name": "3C",
        "rate": 15,
        "comment": "",
        "items": [
          2,
          3
        ]
    }],
    "importers": [{
        "id": 2,
        "name": "Company B",
        "comment": "test2"
      }, {
        "id": 3,
        "name": "Company D",
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| id | integer | company country id |
| country_id | integer | country id |
| fixed_vat | integer | fixed vat |
| **adjusted_vats** | **array** | adjusted vats |
| *name* | *string* | name of adjusted vat |
| *rate* | *integer* | rate of adjusted vat |
| *comment* | *string* | comment of adjusted vat |
| **items** | **array** | a set of item id which has been assigned to this vat |
| **importers** | **array** | importers in country |
| *id* | *integer* | company id |
| *name* | *string* | company name |
| *comment* | *string* | comment for importer |

<aside class="warning">
Failure
</aside>

```json
{
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |


## Create Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/create/country |
| Method | `post` |
| Use | to create vat and importers to country of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "country_id": 1,
    "fixed_vat": 0,
    "adjusted_vats": [{
        "name": "",
        "rate": 0,
        "comment": "",
        "items": []
    }],
    "importers": [{
        "id": 1,
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| country_id | integer | country id |
| fixed_vat | integer | fixed vat rate |
| **adjusted_vats** | **array** | adjusted vats |
| *name* | *string* | name of adjusted vat |
| *rate* | *integer* | rate of adjusted vat |
| *comment* | *string* | comment of adjusted vat |
| **items** | **array** | a set of item id which has been assigned to this vat |
| **importers** | **array** | importers in country |
| *id* | *integer* | company id |
| *comment* | *string* | comment for importer |

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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **country not exist:** select invalid country in system |
||| **country has been exist:** duplicate vat of country |


## Edit Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/edit/country |
| Method | `post` |
| Use | to edit vat and  importers to country of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "id": 1,
    "country_id": 1,
    "fixed_vat": 0,
    "adjusted_vats": [{
        "name": "",
        "rate": 0,
        "comment": "",
        "items": []
    }],
    "importers": [{
        "id": 1,
        "comment": ""
    }]
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| id | integer | company country id |
| country_id | integer | country id |
| fixed_vat | integer | fixed vat rate |
| **adjusted_vats** | **array** | adjusted vats |
| *name* | *string* | name of adjusted vat |
| *rate* | *integer* | rate of adjusted vat |
| *comment* | *string* | comment of adjusted vat |
| **items** | **array** | a set of item id which has been assigned to this vat |
| **importers** | **array** | importers in country |
| *id* | *integer* | company id |
| *comment* | *string* | comment for importer |

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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |
||| **country not exist:** select invalid country in system |
||| **country has been exist:** duplicate vat of country |


## Delete Country

### Description

| Title | Description |
| -------: | :---- |
| URL | user/company/delete/country |
| Method | `post` |
| Use | to edit vat of company |
| Notice |  |


> Input Parameters

### Input Parameters

```json
{
    "api_key": "e4cbcdc2faff41a7e311",
    "company_country_id": 1,
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| api_key | string | Web backend gives user a unique token after user login in app, then user should use this token to request data from web backend. |
| company_country_id | integer | country id of company |

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
    "error_name": "lack of parameters"
}
```

| Parameter | Type | Description |
| -------: | :---- | :--- |
| error_name | string |  the name of the wrong type.|
||| **lack of parameters:**  the request does not include the necessary parameters |
||| **does not signin:** user does not signin |