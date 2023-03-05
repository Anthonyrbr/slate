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


## Request sign

```python
import requests
import json

url = "https://api.signaltech.com.ec/sign/request"

payload = json.dumps({
  "given_name": "test",
  "surname_1": "test",
  "surname_2": "test",
  "id_document_type": "IDC",
  "id_document_country": "EC",
  "serial_number": "12345678A",
  "email": "testsignal@signaltech.com.ec",
  "mobile_phone_number": "+593000000000",
  "residence_address": "testing",
  "residence_city": "QUITO",
  "residence": "EC",
  "document_front": "base64",
  "document_rear": "base64",
  "document_owner": "base64",
  "documents_to_sign": "base64"

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
  "given_name": "test",
  "surname_1": "test",
  "surname_2": "test",
  "id_document_type": "IDC",
  "id_document_country": "EC",
  "serial_number": "12345678A",
  "email": "testsignal@signaltech.com.ec",
  "mobile_phone_number": "+593000000000",
  "residence_address": "testing",
  "residence_city": "QUITO",
  "residence": "EC",
  "document_front": "base64",
  "document_rear": "base64",
  "document_owner": "base64",
  "documents_to_sign": "base64"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "given_name": "test",
  "surname_1": "test",
  "surname_2": "test",
  "id_document_type": "IDC",
  "id_document_country": "EC",
  "serial_number": "12345678A",
  "email": "testsignal@signaltech.com.ec",
  "mobile_phone_number": "+593000000000",
  "residence_address": "testing",
  "residence_city": "QUITO",
  "residence": "EC",
  "document_front": "base64",
  "document_rear": "base64",
  "document_owner": "base64",
  "documents_to_sign": "base64"
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
    "status": true,
    "pk": 23483,
    "uid": "752f7d65-c60d-44c6-aed0-559de55bd0a0",
    "details": [
        {
            "requestDetails": {
                "citizen_tax_number": null,
                "paperless_mode": true,
                "organization_rol": null,
                "birth_country": null,
                "birth_city": null,
                "external_profile": null,
                "mobile_phone_number": "+59300000000",
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
                "profile": "",
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
                        "issuer": "",
                        "data": "base64",
                        "subject": ""
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
                "email": "testsignal@signaltech.com.ec",
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
                "surname_2": "test",
                "surname_1": "test",
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
                "serial_number": "12345678A",
                "scratchcard": "1144247",
                "registration_authority": 35,
                "responsible_serial": null,
                "id_document_type": "IDC",
                "empowerment": null,
                "responsible_registry_data": null,
                "id_responsible_document_country": null,
                "entity_owner": null,
                "pk": 23483,
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
                "given_name": "signal",
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
        },
        "upload" : {
            "status": "200 OK",
            "details": "752f7d65-c60d-44c6-aed0-559de55bd0a0"
        },
        "otp": {
            "status": true,
            "response": {
                "status": "200 OK",
                "details": "OTP generated"
            }
        }
    ]
}
```

This endpoint creates a request to sign a document.

### HTTP Request

`POST https://api.signaltech.com.ec/sign/request`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
given_name <br/>`string` | true | The first or given name of the person submitting the information.
surname_1 <br/>`string` | true | The primary or first surname of the person submitting the information.
surname_2 <br/>`string` | false | The secondary or second surname of the person submitting the information, if applicable.
id_document_type <br/>`string` | true | Document types allowed for the user identification:<br/><b>IDC</b> - Identification based on national identity card number. Default when this field is not specified.<br/><b>PAS</b> - Identification based on passport number<br/><b>PNO</b> - Identification based on national personal number (national civic registration number)<br/><b>TIN</b> - Tax Identification Number according to the European Commission<br/><b>CI</b> - Tax Identification Number according to the European Commission<br/><b>CE</b> - Tax Identification Number according to the European Commission
id_document_country <br/>`string` | true | The user's id document country two-letters code (ISO 3166-1 alpha-2). Default "ES" if field is not included.
serial_number <br/>`string` | true | The unique serial number or identification number associated with the identification document.
email <br/>`string` | true | The email address of the person submitting the information.
mobile_phone_number <br/>`string` | true | The mobile phone number of the person submitting the information.
residence_address <br/>`string` | false | The physical address of the person's residence, if applicable.
residence_city <br/>`string` | false | The city or town where the person's residence is located, if applicable.
residence <br/>`string` | false | The country where the person's residence is located, if applicable.
document_front <br/>`binary` | true | Front side image of the user's identification document (JPEG or PNG).
document_rear <br/>`binary` | true | Rear side image of the user's identification document (JPEG or PNG)
document_owner <br/>`binary` | true | A selfie image of the user holding the identifying document below his/her chin (JPEG or PNG)
documents_to_sign <br/>`binary` | true | Any documents that the person needs to sign as part of the verification process (PDF).

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
        "profile": "",
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
        "email": "john_smithlop@signaltech.com.ec",
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

`GET https://api.signaltech.com.ec/sign/:pk`

### URL Parameters

Parameter | Description
--------- | -----------
pk <br/>`string` | The unique PK (primary key) code generated during the request to identify and track the file.

## Sign

```python
import requests
import json

url = "https://api.signaltech.com.ec/sign"

payload = json.dumps({
  "secret": "408356",
  "pk": "23483"
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
    "secret": "408356",
    "pk": "23483"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "secret": "408356",
  "pk": "23483"
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
    "status": "true",
}
```

This endpoint start the sign proccess on the docs.

### HTTP Request

`POST https://api.signaltech.com.ec/sign`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ---------
secret <br/>`string` | true | The secret code sent during the request to authenticate and verify the request.
pk <br/>`string` | true | The unique PK (primary key) code generated during the request to identify and track the request.

## Retrieve document

```python
import requests
import json

url = "https://api.signaltech.com.ec/sign/retrieve"

payload = json.dumps({
  "pk": "23480",
  "type": "signed",
  "uid": "da4b4561-382b-407b-8347-60a8ea286039"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/sign/retrieve' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "pk": "23480",
    "type": "signed",
    "uid": "da4b4561-382b-407b-8347-60a8ea286039"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "pk": "23480",
  "type": "signed",
  "uid": "da4b4561-382b-407b-8347-60a8ea286039"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/sign/retrieve", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": true,
    "message": "file retrieved successfully",
    "url": "path to file"
}
```

This endpoint retrieve the signed docs and send it as binary files.

### HTTP Request

`POST https://api.signaltech.com.ec/sign/retrieve`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ---------
pk <br/>`string` | true | The unique PK (primary key) code generated during the request to identify and track the file.
uid <br/>`string` | true | The unique identifier (UID) of the file uploaded during the request.
type <br/>`string` | true | Indicates whether the file is an original or signed document, and is represented as either "original" or "signed".

## Download document

```python
import requests
import json

url = "https://api.signaltech.com.ec/sign/download"

payload = json.dumps({
  "pk": "23480",
  "type": "signed",
  "uid": "da4b4561-382b-407b-8347-60a8ea286039"
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/sign/download' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    "pk": "23480",
    "type": "signed",
    "uid": "da4b4561-382b-407b-8347-60a8ea286039"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  "pk": "23480",
  "type": "signed",
  "uid": "da4b4561-382b-407b-8347-60a8ea286039"
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/sign/download", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "application/octet-stream"
}
```

This endpoint retrieve the signed docs and send it as binary files.

### HTTP Request

`POST https://api.signaltech.com.ec/sign/download`

### URL Parameters

Parameter | Required | Description
--------- | ----------- | ---------
pk <br/>`string` | true | The unique PK (primary key) code generated during the request to identify and track the file.
uid <br/>`string` | true | The unique identifier (UID) of the file uploaded during the request.
type <br/>`string` | true | Indicates whether the file is an original or signed document, and is represented as either "original" or "signed".

# Biometric

## Request Accesspoint

```python
import requests
import json

url = "https://api.signaltech.com.ec/biometric"

payload = json.dumps({
  
})
headers = {
  'Authorization': 'Bearer <token>',
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)

```

```shell
curl --location --request POST 'https://api.signaltech.com.ec/biometric' \
--header 'Authorization: Bearer <token>' \
--header 'Content-Type: application/json' \
--data-raw '{
    
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Authorization", "Bearer <token>");
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  
});

var requestOptions = {
  method: 'POST',
  headers: myHeaders,
  body: raw,
  redirect: 'follow'
};

fetch("https://api.signaltech.com.ec/biometric", requestOptions)
  .then(response => response.text())
  .then(result => console.log(result))
  .catch(error => console.log('error', error));
```

> The above command returns JSON structured like this:

```json
{
    "status": 200,
    "url": ""
}
```

This endpoint retrieve a temporal url to use biometric service.

### HTTP Request

`POST https://api.signaltech.com.ec/biometric`