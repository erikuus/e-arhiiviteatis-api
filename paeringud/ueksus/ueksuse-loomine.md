---
description: Päringu dokumentatsioon
---

# Üksuse loomine

## <mark style="color:orange;">POST</mark> ska/department/create

```
{{apiBaseUrl}}/ska/department/create?token={{accessToken}}
```

Loob uue üksuse ja tagastab selle identifikaatori.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |

### Sisend (body raw json)

\*-ga märgitud on kohustuslikud

| NIMI       | TÜÜP (PIKKUS) | SELGITUS               |   |
| ---------- | ------------- | ---------------------- | - |
| name \*    | String (256)  | Üksuse nimi            |   |
| address \* | String (256)  | Üksuse aadress         |   |
| zip \*     | String (16)   | Üksuse postiindeks     |   |
| email \*   | String (128)  | Üksuse e-posti aadress |   |
| phone \*   | String (16)   | Üksuse telefoninumber  |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request POST 'https://www.ra.ee/vau/index.php/api/ska/department/create?token=bd266e2a556dc5331917d86252262c30' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Test osakond",
    "address": "Tammsaare 8-25, Tartu",
    "zip": "51006",
    "email": "erik.uus@ra.ee",
    "phone": "+372 5322 5388"
}'
```
{% endcode %}

### Vastuse näide

Uue üksuse loomine õnnestub ja tagastatakse loodud üksuse identifikaator.

```json
{
    "responseStatus": "ok",
    "departmentId": 30
}
```

### Veateated

**error 4050** - üksust ei saa luua, kuna sisendväärtused ei valideeru&#x20;

```json
{
    "responseStatus": "error",
    "errorCode": 4050,
    "errorMessage": "Could not create department",
    "errors": {
        "name": [
            "Nimi ei tohi olla tühi."
        ],
        "email": [
            "E-post ei ole korrektne e-posti aadress."
        ]
    }
}
```

**error 4051** - päringu _raw body_ ei sisalda _JSON_ _stringi_

```json
{
    "responseStatus": "error",
    "errorCode": 4051,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 4052** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 4052,
    "errorMessage": "Is not POST request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
