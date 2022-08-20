---
description: Mis on API juurdepääsukood? Kuidas seda saada? Kui kaua see kehtib?
---

# Juurdepääsukood

Kõigile API päringutele tuleb ühe parameetrina lisada juurde ajutiselt kehtiv juurdepääsukood ehk _access token_. Näiteks:

```
{{apiBaseUrl}}/ska/application/view?token=71e0d98f1ab52c225d655359190b6844&id=16610
```

kus _token_ on _"_71e0d98f1ab52c225d655359190b6844".

_Tokeni_ väljastab päring, mis kontrollib kasutajanime ja salasõna järgi, kas kasutaja on olemas.

{% content-ref url="broken-reference" %}
[Broken link](broken-reference)
{% endcontent-ref %}

### Vastus

Eelnimetatud päringu vastus näitab ka seda, kui kaua token kehtib. Näiteks:

```json
{
    "responseStatus": "ok",
    "userId": 3,
    "userFirstname": "Erik",
    "userLastname": "Uus",
    "userEmail": "erik.uus@ra.ee",
    "accessToken": "71e0d98f1ab52c225d655359190b6844",
    "tokenLifetime": 3600,
    "requestUnixTime": 1660724872
}
```

ütleb, et _token_ "71e0d98f1ab52c225d655359190b6844" kehtib 3600 sekundit alates päringu esitamise hetkest, mille UNIX ajatempel on 1660724872.

_Tokeni_ kasutamisel päringutes võivad esineda järgmised vead.&#x20;

### **Viga 2010**

_Kui token_ on aegunud või sellist tokenit andmebaasis ei eksisteeri, on päringu vastus:

```json
{
    "responseStatus": "error",
    "errorCode": 2010,
    "errorMessage": "Access token is invalid or expired"
}
```

Sellisel juhul tuleb lihtsalt pärida uus _token_ [Broken link](broken-reference "mention").

### **Viga 2011**

Kui andmebaasis puudub info selle kohta, millisele kasutajale token kuulub, vastab päring:

```json
{
    "responseStatus": "error",
    "errorCode": 2011,
    "errorMessage": "Access token has no user"
}
```

See on API viga, mida ideaalis ei tohiks kunagi juhtuda.

### Viga 2012

Kui token on olemas ja kehtib, aga see kuulub kasutajale, kellel puudub käesoleva API-mooduli kasutusõigus, on päringu vastus:

```json
{
    "responseStatus": "error",
    "errorCode": 2012,
    "errorMessage": "User does not have the proper credential to access this action",
    "userName": "erik"
}
```

Sellisel juhul tuleb esitada [juurdepaeaesutaotlus.md](juurdepaeaesutaotlus.md "mention")

### Viga 2013

Kui päringule ei ole lisatud _tokenit_, vastab päring:

```json
{
    "responseStatus": "error",
    "errorCode": 2013,
    "errorMessage": "No access token"
}
```

Sellisel juhul tuleb pärida _token_ [Broken link](broken-reference "mention") __ ja lisada see __ päringule_._