---
description: Päringu dokumentatsioon
---

# Failinime muutmine

## <mark style="color:blue;">PUT</mark> ska/file/rename

```
{{apiBaseUrl}}/ska/file/rename?token={{accessToken}}&id={{fileId}}
```

Muudab failinime identifikaatori alusel.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                     |   |
| -------- | ------- | ------------------------------------------------------------ | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| id \*    | Integer | Faili identifikaator                                         |   |

Faili identifikaatori saamise kohta vaata [faili-lisamine.md](faili-lisamine.md "mention")

### Sisend (body raw json)

\*-ga märgitud on kohustuslikud

| NIMI            | TÜÜP (PIKKUS) | SELGITUS                                                                                                                                                         |   |
| --------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| employee\_id \* | Integer       | Töötaja identifikaator, kes failinime muudab                                                                                                                     |   |
| file\_name \*   | String (256)  | Failinimi, mis võib sisaldada ainult täppideta tähti, numbreid ja sidekriipsu. Lubatud on järgmised failinime laiendused: bdoc, ddoc, asice, pdf, jpeg, jpg, png |   |

Töötaja identifikaatori saamise kohta vaata [toeoetaja-loomine.md](../toeoetaja/toeoetaja-loomine.md "mention") ja [toeoetaja-leidmine.md](../toeoetaja/toeoetaja-leidmine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request PUT 'https://www.ra.ee/vau/index.php/api/ska/file/rename?token=24aad44bab3b258b06e809cc53e9083e&id=400' \
--header 'Content-Type: application/json' \
--data-raw '{
    "employee_id": 301,
    "file_name": "test1.jpg"
}'
```
{% endcode %}

### Vastuse näide

Failinime muutmine õnnestub.

```json
{
    "responseStatus": "ok"
}
```

### Veateated

**error 6040** - failinime ei saa muuta (määratlemata tehnilistel põhjustel)

```json
{
    "responseStatus": "error",
    "errorCode": 6040,
    "errorMessage": "Could not rename file"
}
```

**error 6041** - failinime ei saa muuta, kuna sisendväärtused ei valideeru

```json
{
    "responseStatus": "error",
    "errorCode": 6041,
    "errorMessage": "Could not rename file",
    "errors": {
        "file_name": [
            "Failinimi \"test1.jpg\" on juba kasutuses."
        ],
        "employee_id": [
            "Töötaja \"0\" ei eksisteeri."
        ]
    }
}
```

**error 6042** - päringu _raw body_ ei sisalda _JSON_ _stringi_

```json
{
    "responseStatus": "error",
    "errorCode": 6042,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 6043** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 6043,
    "errorMessage": "Is not PUT request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
