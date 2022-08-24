---
description: Päringu dokumentatsioon
---

# Taotluse saatmine

## <mark style="color:blue;">PUT</mark> ska/employee/create

```
{{apiBaseUrl}}/ska/employee/update?token={{accessToken}}&id={{employeeId}}
```

Muudab töötaja andmeid identifikaatori alusel.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                     |   |
| -------- | ------- | ------------------------------------------------------------ | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| id \*    | Integer | Töötaja identifikaator                                       |   |

Töötaja identifikaatori saamise kohta vaata [toeoetaja-loomine.md](../toeoetaja/toeoetaja-loomine.md "mention") ja [toeoetaja-leidmine.md](../toeoetaja/toeoetaja-leidmine.md "mention")

### Sisend (body raw json)

\*-ga märgitud on kohustuslikud

| NIMI              | TÜÜP (PIKKUS) | SELGITUS                                   |   |
| ----------------- | ------------- | ------------------------------------------ | - |
| firstname \*      | String (128)  | Töötaja eesnimi                            |   |
| lastname \*       | String (128)  | Töötaja perekonnanimi                      |   |
| email \*          | String (128)  | Töötaja e-posti aadress                    |   |
| phone \*          | String (16)   | Töötaja telefoninumber                     |   |
| department\_id \* | Integer       | Üksuse identifikaator, kuhu töötaja kuulub |   |

Üksuse identifikaatori saamise kohta vaata [ueksuse-loomine.md](../ueksus/ueksuse-loomine.md "mention")ja [ueksuse-leidmine.md](../ueksus/ueksuse-leidmine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request PUT 'https://www.ra.ee/vau/index.php/api/ska/employee/update?token=ea2397458ba644c6fd2d70b05adb6661&id=268' \
--header 'Content-Type: application/json' \
--data-raw '{
    "firstname": "Erik_",
    "lastname": "Uus_",
    "email": "erik.uus@gmail.com",
    "phone": "+372 5322 5389",
    "department_id": 16
}'
```
{% endcode %}

### Vastuse näide

Töötaja muutmine õnnestub.

```json
{
    "responseStatus": "ok"
}
```

### Veateated

**error 5040** - töötajat ei saa muuta, kuna sisendväärtused ei valideeru&#x20;

```json
{
    "responseStatus": "error",
    "errorCode": 5040,
    "errorMessage": "Could not update employee",
    "errors": {
        "firstname": [
            "Eesnimi ei tohi olla tühi."
        ],
        "department_id": [
            "Üksus \"16000\" ei eksisteeri."
        ],
        "email": [
            "E-post ei ole korrektne e-posti aadress."
        ]
    }
}
```

**error 5041** - päringu _raw body_ ei sisalda _JSON_ _stringi_

```json
{
    "responseStatus": "error",
    "errorCode": 5041,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 5042** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 5042,
    "errorMessage": "Is not PUT request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
