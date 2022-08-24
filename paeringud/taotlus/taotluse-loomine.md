---
description: Päringu dokumentatsioon
---

# Taotluse loomine

## <mark style="color:orange;">POST</mark> ska/application/create

```
{{apiBaseUrl}}/ska/application/create?token={{accessToken}}
```

Loob uue taotluse ja tagastab selle identifikaatori.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |

### Sisend (body raw json)

JSON peab sisaldama vähemalt taotluse objekti `Application`:

```json
{
    "Application": {}
}
```

Kui taotlusele soovitakse lisada üks või mitu õppeastust või töökohta, siis peab JSON sisaldama ka `Study` ja/või `Work` objektide nimekirja:&#x20;



\*-ga märgitud on kohustuslikud

| NIMI              | TÜÜP (PIKKUS) | SELGITUS |   |
| ----------------- | ------------- | -------- | - |
| Application \*    | String (128)  |          |   |
| lastname \*       | String (128)  |          |   |
| email \*          | String (128)  |          |   |
| phone \*          | String (16)   |          |   |
| department\_id \* | Integer       |          |   |

Üksuse identifikaatori saamise kohta vaata [ueksuse-loomine.md](../ueksus/ueksuse-loomine.md "mention")ja [ueksuse-leidmine.md](../ueksus/ueksuse-leidmine.md "mention")

Töötaja identifikaatori saamise kohta vaata [toeoetaja-loomine.md](../toeoetaja/toeoetaja-loomine.md "mention") ja [toeoetaja-leidmine.md](../toeoetaja/toeoetaja-leidmine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request POST 'https://www.ra.ee/vau/index.php/api/ska/employee/create?token=ea2397458ba644c6fd2d70b05adb6661' \
--header 'Content-Type: application/json' \
--data-raw '{
    "firstname": "Erik",
    "lastname": "Uus",
    "email": "erik.uus@ra.ee",
    "phone": "+372 5322 5388",
    "department_id": 30
}'
```
{% endcode %}

### Vastuse näide

Uue töötaja loomine õnnestub ja tagastatakse loodud üksuse identifikaator.

```json
{
    "responseStatus": "ok",
    "employeeId": 301
}
```

### Veateated

**error 5050** - töötajat ei saa luua, kuna sisendväärtused ei valideeru&#x20;

```json
{
    "responseStatus": "error",
    "errorCode": 5050,
    "errorMessage": "Could not create employee",
    "errors": {
        "firstname": [
            "Eesnimi ei tohi olla tühi."
        ],
        "email": [
            "E-post ei ole korrektne e-posti aadress."
        ]
    }
}
```

**error 5051** - päringu _raw body_ ei sisalda _JSON_ _stringi_

```json
{
    "responseStatus": "error",
    "errorCode": 5051,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 5052** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 5052,
    "errorMessage": "Is not POST request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
