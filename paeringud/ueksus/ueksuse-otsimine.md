---
description: Päringu dokumentatsioon
---

# Üksuse otsimine

## <mark style="color:green;">GET</mark> ska/department/find

```
{{apiBaseUrl}}/ska/department/find?token={{accessToken}}&name={{departmentName}}
```

Väljastab üksuse identifikaatori üksuse nime alusel.&#x20;

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| name     | String | Üksuse nimi (tõstutundetu)                                   |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/department/find?token=ea2397458ba644c6fd2d70b05adb6661&name=ska menetlustalitus' \
```
{% endcode %}

### Vastuse näide

Üksuse identifikaatori väljastamine õnnestub.

```json
{
    "responseStatus": "ok",
    "departmentId": 17
}
```

### Veateade

**error 4020** - üksust ei leitud (määratud nimega üksust andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 4020,
    "errorMessage": "The requested department does not exist"
}
```

{% hint style="info" %}
Pane tähele, et selles näites "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 OK".
{% endhint %}
