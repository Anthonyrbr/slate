---
title: Signal API Reference

language_tabs: # must be one of https://github.com/rouge-ruby/rouge/wiki/List-of-supported-languages-and-lexers
  - shell
  - python
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Signal API
---

# Introduction

Welcome to the Signal API! You can use our API to access Signal API endpoints, which can get information on various services.

We have language bindings in Shell, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Token

> To authorize, use this code:

```python
import requests
import json

url = "https://api.signaltech.com.ec"

headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers)

print(response.text)
```

```shell
# With shell, you can just pass the correct header with each request
curl --location --request POST 'https://api.signaltech.com.ec' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> Make sure to replace `<token>` with your API token.

Signal uses API Tokens (JWT) to allow access to the API. You can register a new Signal API key at our [developer portal](https://signaltech.com.ec/developers).

Signal expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <token>`

<aside class="notice">
You must replace <code>token</code> with your personal API key.
</aside>

# Authentication

## Login

```python
import requests
import json

url = "https://api.signaltech.com.ec/auth/login"

payload = json.dumps({
  "username": "usertest",
  "password": "passwordtest"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/auth/login' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "usertest",
    "password": "passwordtest"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "username": "usertest",
  "password": "passwordtest"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/auth/login", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "message": "authorization completed",
    "token": "<session token>"
}
```

This endpoint retrieves a session token.

### HTTP Request

`POST https://api.signaltech.com.ec/auth/login`

### Request Parameters

Parameter | Required | Description
--------- | ------- | -----------
username | true | username of the user that authenticates.
password | true | password of the user that authenticates.

<aside class="success">
200 — is the status code that is returned on success login
</aside>

## Details

```python
import requests
import json

url = "https://api.signaltech.com.ec/auth/details"

payload = json.dumps({
  "token": "<token to retrieve>"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/auth/details' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "token": "<token to retrieve>"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "token": "<token to retrieve>"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/auth/details", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "user": {
        "_id": "63ffe4e7e8ceaa6ff55f4e92",
        "name": "test",
        "lastname": "test lastname",
        "role": "Superadmin",
        "coll_username": "usertest",
        "coll_password": "encryted password",
        "email": "test@signaltech.com.ec",
        "otp": null,
        "isactive": true,
        "deactivation": null,
        "isrestored": false,
        "onboarding": {},
        "createdAt": "2023-03-01T23:51:03.096Z"
    },
    "expires": 1680394669,
    "iat": 1677716269
}
```

This endpoint retrieves a specific user.

### HTTP Request

`POST https://api.signaltech.com.ec/auth/details`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ---------
token | true | token that will be validated

## Sign up

```python
import requests
import json

url = "https://api.signaltech.com.ec/auth/signup"

payload = json.dumps({
  "username": "usertest",
  "password": "passwordtest",
  "name": "test",
  "lastname": "test lastname",
  "email": "test@signaltech.com.ec"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/auth/signup' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "username": "usertest",
    "password": "passwordtest",
    "name": "test",
    "lastname": "test lastname",
    "email": "test@signaltech.com.ec"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "username": "usertest",
  "password": "passwordtest",
  "name": "test",
  "lastname": "test lastname",
  "email": "test@signaltech.com.ec"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/auth/signup", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "message": "registration completed",
    "user": {
        "acknowledged": true,
        "insertedId": "63ffe4e7e8ceaa6ff55f4e92"
    }
}
```

This endpoint register a specific user.

### HTTP Request

`POST https://api.signaltech.com.ec/auth/signup<ID>`

### URL Parameters

Parameter | Required | Type | Description
--------- | ----------- | ---------- | ----------
username | true | string | username to authenticate
password | true | string | user password
name | true | string | user's name
lastname | true | string | user's lastname
email | true | string | user's email

## Forgot password

```python
import requests
import json

url = "https://api.signaltech.com.ec/auth/forgot-password"

payload = json.dumps({
  "email": "test@signaltech.com.ec"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/auth/forgot-password' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "test@signaltech.com.ec"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "email": "test@signaltech.com.ec"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/auth/forgot-password", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  
}
```

This endpoint restore a specific user password.

### HTTP Request

`POST https://api.signaltech.com.ec/auth/forgot-password`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

## Restore user account


```python
import requests
import json

url = "https://api.signaltech.com.ec/auth/restore"

payload = json.dumps({
  "email": "test@signaltech.com.ec",
  "otp": 320067,
  "newPassword": "123"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/auth/restore' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "email": "test@signaltech.com.ec",
    "otp": 320067,
    "newPassword": "123"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "email": "test@signaltech.com.ec",
  "otp": 320067,
  "newPassword": "123"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/auth/restore", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

# Analytics

## List transactions

```python
import requests

url = "https://api.signaltech.com.ec/analytics/list-transactions"

payload={}
headers = {
  'Authorization': 'Bearer <token>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request GET 'https://api.signaltech.com.ec/analytics/list-transactions' \
--header 'Authorization: Bearer <token>'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/analytics/list-transactions", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{

}
```

This endpoint get a list of transactions.

### HTTP Request

`POST https://api.signaltech.com.ec/analytics/list-transactions`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

## Filter transactions

```python
import requests
import json

url = "https://api.signaltech.com.ec/analytics/filter"

payload = json.dumps({
  "start": "2023-02-09T04:06:24.856+00:00",
  "end": "2023-02-11T04:06:24.856+00:00"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/analytics/filter' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "start": "2023-02-09T04:06:24.856+00:00",
    "end": "2023-02-11T04:06:24.856+00:00"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "start": "2023-02-09T04:06:24.856+00:00",
  "end": "2023-02-11T04:06:24.856+00:00"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/analytics/filter", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`POST https://api.signaltech.com.ec/analytics/filter`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

# Roles

## Create

## List

# Onboarding

## Create

## OTP Verification

# Clients

## Create

## List

## Update

## Delete

# IWS Biometric

## Generate

# Sign

## Status

```python
import requests

url = "https://api.signaltech.com.ec/sign"

payload={}
headers = {
  'Authorization': 'Bearer <token>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request GET 'https://api.signaltech.com.ec/sign' \
--header 'Authorization: Bearer <token>'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/sign", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": "200 OK",
    "details": "Hello"
}
```

This endpoint shows the status of the service.

### HTTP Request

`GET https://api.signaltech.com.ec/sign`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

## Request sign

```python
import requests
import json

url = "https://api.signaltech.com.ec/sign"

payload = json.dumps({
  "given_name": "signal",
  "surname_1": "test",
  "surname_2": "test",
  "id_document_type": "IDC",
  "id_document_country": "EC",
  "serial_number": "12345678A",
  "email": "testsignal@uanataca.ec",
  "mobile_phone_number": "+593000000000",
  "registration_authority": "35",
  "profile": "ECPFDSCF",
  "residence_address": "AV. MARIANA DE JESUS",
  "residence_city": "QUITO",
  "residence": "EC",
  "document_front": "base64",
  "document_rear": "base64",
  "document_owner": "base64"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/sign' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "given_name": "signal",
    "surname_1": "test",
    "surname_2": "test",
    "id_document_type": "IDC",
    "id_document_country": "EC",
    "serial_number": "12345678A",
    "email": "testsignal@uanataca.ec",
    "mobile_phone_number": "+593000000000",
    "registration_authority": "35",
    "profile": "ECPFDSCF",
    "residence_address": "AV. MARIANA DE JESUS",
    "residence_city": "QUITO",
    "residence": "EC",
    "document_front": "base64",
    "document_rear": "base64",
    "document_owner": "base64"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "given_name": "signal",
  "surname_1": "test",
  "surname_2": "test",
  "id_document_type": "IDC",
  "id_document_country": "EC",
  "serial_number": "12345678A",
  "email": "testsignal@uanataca.ec",
  "mobile_phone_number": "+593000000000",
  "registration_authority": "35",
  "profile": "ECPFDSCF",
  "residence_address": "AV. MARIANA DE JESUS",
  "residence_city": "QUITO",
  "residence": "EC",
  "document_front": "base64",
  "document_rear": "base64",
  "document_owner": "base64"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/sign", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`POST https://api.signaltech.com.ec/sign<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

## Request details

```python
import requests

url = "https://api.signaltech.com.ec/sign/:pk"

payload={}
headers = {
  'Authorization': 'Bearer <token>'
}

response = requests.request("GET", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request GET 'https://api.signaltech.com.ec/sign/:pk' \
--header 'Authorization: Bearer <token>'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");

var requestOptions = {
  method: 'GET',
  headers: myHeaders,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/sign/:pk", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": "200 OK",
    "details": {
        "citizen_tax_number": null,
        "paperless_mode": true,
        "organization_rol": null,
        "birth_country": null,
        "birth_city": null,
        "external_profile": null,
        "mobile_phone_number": "+59399999999",
        "residence_state": null,
        "title": null,
        "ext_recognition_data": null,
        "process_application": null,
        "country_name": "EC",
        "approving_user": {
            "pk": 49,
            "request": 2425,
            "permission_profile": 943,
            "registration_authority": 33
        },
        "birth_province": null,
        "birth_state": null,
        "residence_postal_code": null,
        "id_document_number": null,
        "smartcard_sn": null,
        "secure_element": 2,
        "organization_state": null,
        "communication_language": "",
        "id_document_expiry": null,
        "responsible_legal_documents": null,
        "id_document_issuer": null,
        "profile": "ECPFDSCF",
        "organization_address": null,
        "provider_registration_number": null,
        "sex": null,
        "registering_user": {
            "pk": 49,
            "request": 2425,
            "permission_profile": 943,
            "registration_authority": 33
        },
        "enrollment_success_url": null,
        "description": null,
        "organization_tax_number": null,
        "administrative_unit": null,
        "organization_name": null,
        "approving_rao": {
            "is_identificator": false,
            "id_document_description": "",
            "certificate": {
                "profile": "PFnubeNC",
                "status": 0,
                "valid_from": "2022-11-23T16:49:00Z",
                "valid_to": "2025-11-22T16:49:00Z",
                "valid": "VALID",
                "revokation_reason": null,
                "serial_number": "531d5f96ec8c6dac",
                "issuer": "C=ES, L=Barcelona (see current address at www.uanataca.com/address), O=UANATACA S.A., OU=TSP-UANATACA, CN=UANATACA CA1 2016 STAGING, 2.5.4.97=VATES-A66721499",
                "data": "base64",
                "subject": "CN=RAO Ecuador One-Shot SandBox, 2.5.4.5=IDCEC-99999999R, 2.5.4.42=RAO Ecuador One-Shot, 2.5.4.4=SandBox, OU=BES DPR:https://www.uanataca.com/, C=ES"
            },
            "registration_authority": [],
            "registration_authority_master": 33,
            "id_document_number": "99999999R",
            "given_name": "RAO Ecuador One-Shot",
            "surname_2": "",
            "pk": 36,
            "surname_1": "SandBox",
            "id_document_issuer": ""
        },
        "responsible_citizenship": null,
        "organization_country": null,
        "email": "john_smithlop@uanataca.com",
        "producing_user": null,
        "responsible_second_surname": null,
        "responsible_name": null,
        "professional_id_number": null,
        "residence_address": null,
        "responsible_legal_level": null,
        "residence_district": null,
        "entity_owner_serial_number": null,
        "configuration_data": {},
        "id_responsible_document_type": null,
        "residence_city": null,
        "subscriber_responsible_serial": null,
        "organization_city": null,
        "surname_2": "test 2",
        "surname_1": "test 1",
        "identification_rao": null,
        "fix_phone_number": null,
        "id_responsible_document_number": null,
        "validity_time": "1",
        "registration": null,
        "organization_province": null,
        "organization_identifier": null,
        "videoid_mode": false,
        "subscriber": null,
        "birth_canton": null,
        "special_conditions": null,
        "serial_number": "123456789",
        "scratchcard": "1144225",
        "registration_authority": 35,
        "responsible_serial": null,
        "id_document_type": "IDC",
        "empowerment": null,
        "responsible_registry_data": null,
        "id_responsible_document_country": null,
        "entity_owner": null,
        "pk": 22885,
        "circumstances": null,
        "responsible_position": null,
        "producing_rao": null,
        "organization_email": null,
        "limit": null,
        "residence": "EC",
        "residence_canton": null,
        "citizenship": null,
        "videoid_data": null,
        "organizational_unit_3": null,
        "organizational_unit_2": null,
        "organizational_unit_1": null,
        "organization_postal_code": null,
        "responsible_email": null,
        "given_name": "test",
        "id_responsible_document_issuer": null,
        "organization_url": null,
        "status": "ENROLLREADY",
        "id_document_description": null,
        "certificate_set": [],
        "residence_province": null,
        "responsible_first_surname": null,
        "id_document_country": "EC",
        "id_document_release": null,
        "complement_number": null,
        "birth_district": null,
        "birth_date": null,
        "representation": null
    }
}
```

This endpoint retrieve a request details.

### HTTP Request

`GET https://api.signaltech.com.ec/sign`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

## List requests

## Get contract