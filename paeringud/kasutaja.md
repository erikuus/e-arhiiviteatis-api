---
description: Päringute dokumentatsioon
---

# Kasutaja

{% swagger method="post" path="/user/verify" baseUrl="{{apiBaseUrl}}" summary="Juurdepääsukoodi pärimine" %}
{% swagger-description %}
Kõigile päringutele tuleb ühe parameetrina lisada juurde ajutiselt kehtiv juurdepääsukood ehk 

_token_

. Tokeni väljastab päring, mis kontrollib kasutajanime ja salasõna järgi, kas kasutaja on olemas.
{% endswagger-description %}

{% swagger-parameter in="body" name="username" type="String" required="true" %}
VAU-s registreeritud kasutajanimi&#x20;

VAU kohta loe siit [juurdepaeaesutaotlus.md](../juurdepaeaesutaotlus.md "mention")
{% endswagger-parameter %}

{% swagger-parameter in="body" type="String" name="password" required="true" %}
VAU-s registreeritud salasõna
{% endswagger-parameter %}

{% swagger-response status="200: OK" description="OK" %}
```json
{
    "responseStatus": "ok",
    "userId": 3,
    "userFirstname": "Erik",
    "userLastname": "Uus",
    "userEmail": "erik.uus@ra.ee",
    "accessToken": "c7234cb8fd247d668062c55a6b1c4be2",
    "tokenLifetime": 3600,
    "requestUnixTime": 1660032944
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="error 1010" %}
```javascript
{
    "responseStatus": "error",
    "errorCode": 1010,
    "errorMessage": "Is not POST request"
}
```
{% endswagger-response %}

{% swagger-response status="200: OK" description="error 1011" %}
```javascript
{
    "responseStatus": "error",
    "errorCode": 1011,
    "errorMessage": "Could not verify user",
    "errors": {
        "password": [
            "Vale salasõna"
        ]
    }
}
```
{% endswagger-response %}
{% endswagger %}
