---
description: Päringu dokumentatsioon
---

# Töötaja leidmine

## <mark style="color:green;">GET</mark> ska/employee/find

```
{{apiBaseUrl}}/ska/employee/find?token={{accessToken}}&email={{employeeEmail}}
```

Väljastab töötaja identifikaatori töötaja e-posti aadressi alusel.&#x20;

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| email    | String | Töötaja e-posti aadress (tõstutundetu)                       |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/employee/find?token=24aad44bab3b258b06e809cc53e9083e&email=erik.UUS@gmail.COM' \
```
{% endcode %}

### Vastuse näide

Üksuse identifikaatori väljastamine õnnestub.

```json
{
    "responseStatus": "ok",
    "employeeId": 301
}
```

### Veateade

**error 5020** - üksust ei leitud (määratud nimega üksust andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 5020,
    "errorMessage": "The requested employee does not exist."
}
```

{% hint style="info" %}
Pane tähele, et selles näites "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 OK".
{% endhint %}
