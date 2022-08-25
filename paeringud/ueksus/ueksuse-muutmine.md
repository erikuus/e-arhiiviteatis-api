---
description: Päringu dokumentatsioon
---

# Üksuse muutmine

## <mark style="color:blue;">PUT</mark> ska/department/create

```
{{apiBaseUrl}}/ska/department/update?token={{accessToken}}&id={{departmentId}}
```

Muudab üksuse andmeid identifikaatori alusel.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                                                                                                                                                                                                            |   |
| -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention")                                                                                                                                                                                        |   |
| id \*    | Integer | <p>Üksuse identifikaator<br><br><em>NB! Üksuse identifikaatori saamise kohta vaata</em> <a data-mention href="ueksuse-loomine.md">ueksuse-loomine.md</a><em>ja</em> <a data-mention href="ueksuse-leidmine.md">ueksuse-leidmine.md</a><em></em></p> |   |

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
curl --location --request PUT 'https://www.ra.ee/vau/index.php/api/ska/department/update?token=bd266e2a556dc5331917d86252262c30&id=30' \
--header 'Content-Type: application/json' \
--data-raw '{
    "name": "Test osakond_",
    "address": "Tammsaare 8-25, Tartu_",
    "zip": "51006_",
    "email": "erik.uus@gmail.com",
    "phone": "+372 5322 5388_"
}'
```
{% endcode %}

### Vastuse näide

Üksuse muutmine õnnestub.

```json
{
    "responseStatus": "ok"
}
```

### Veateated

**error 4040** - üksust ei saa muuta, kuna sisendväärtused ei valideeru&#x20;

```json
{
    "responseStatus": "error",
    "errorCode": 4040,
    "errorMessage": "Could not update department",
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

**error 4041** - päringu _raw body_ ei sisalda _JSON_ _stringi_

```json
{
    "responseStatus": "error",
    "errorCode": 4041,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 4042** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 4042,
    "errorMessage": "Is not PUT request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
