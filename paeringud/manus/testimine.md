---
description: Päringu dokumentatsioon
---

# Testimine

## <mark style="color:green;">GET</mark> ska/file/test

```
{{apiBaseUrl}}/ska/file/test?token={{accessToken}}
```

Testib, kas manust puudutav päringute grupp on kättesaadav. Normaaljuhul pole see vajalik, aga kui mingil tehnilisel põhjusel manust puudutav päringute grupp muutub kättesaamatuks, näiteks annavad kõik päringud vastuseks Internal Server Error, saab selle päringu kaudu tuvastada, millal päringud muutuvad jälle kättesaadavaks.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |

### Päringu näide (cUrl)

<pre class="language-shell" data-overflow="wrap"><code class="lang-shell"><strong>curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/file/test?token=bd266e2a556dc5331917d86252262c30' \</strong></code></pre>

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
    "errorMessage": "FileController do not have a method \"test\"."
}
```
