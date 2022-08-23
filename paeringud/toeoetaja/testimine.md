---
description: Päringu dokumentatsioon
---

# Testimine

## <mark style="color:green;">GET</mark> ska/employee/test

```
{{apiBaseUrl}}/ska/employee/test?token={{accessToken}}
```

Testib, kas töötajat puudutav päringute grupp on kättesaadav. Normaaljuhul pole see vajalik, aga kui mingil tehnilisel põhjusel töötajat puudutav päringute grupp muutub kättesaamatuks, näiteks annavad kõik päringud vastuseks Internal Server Error, saab selle päringu kaudu tuvastada, millal päringud muutuvad jälle kättesaadavaks.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/employee/test?token=bd266e2a556dc5331917d86252262c30' \
```
{% endcode %}

### Vastuse näide

Päringute grupp on kättesaadav.

```json
{
    "responseStatus": "ok"
}
```

### Veateade

Päringute grupp ei ole serveri sisemise vea tõttu kättesaadav.

```json
{
    "responseStatus": "error",
    "errorCode": 500,
    "errorMessage": "EmployeeController do not have a method \"test\"."
}
```
