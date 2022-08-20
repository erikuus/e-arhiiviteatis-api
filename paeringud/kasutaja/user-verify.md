---
description: Päringu dokumentatsioon
---

# user/verify

{% swagger method="post" path="" baseUrl="{{apiBaseUrl}}/user/verify" summary="Kasutaja kontrollimine ja tokeni väljastamine" %}
{% swagger-description %}
Kõigile päringutele tuleb ühe parameetrina lisada juurde ajutiselt kehtiv kood ehk 

_token_

. Tokeni väljastab päring, mis kontrollib kasutajanime ja salasõna järgi, kas kasutaja on olemas.
{% endswagger-description %}

{% swagger-parameter in="body" name="username" type="String" required="true" %}
VAU-s registreeritud kasutajanimi 
{% endswagger-parameter %}

{% swagger-parameter in="body" type="String" name="password" required="true" %}
VAU-s registreeritud salasõna



_VAU kohta loe siit_ [juurdepaeaesutaotlus.md](../../juurdepaeaesutaotlus.md "mention")
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

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}
