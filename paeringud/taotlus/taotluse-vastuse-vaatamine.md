---
description: Päringu dokumentatsioon
---

# Taotluse vastuse vaatamine

## <mark style="color:green;">GET</mark> ska/employee/view

```
{{apiBaseUrl}}/ska/employee/view?token={{accessToken}}&id={{employeeId}}
```

Väljastab töötaja andmed identifikaatori alusel.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                     |   |
| -------- | ------- | ------------------------------------------------------------ | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| id \*    | Integer | Töötaja identifikaator                                       |   |

Töötaja identifikaatori saamise kohta vaata [toeoetaja-loomine.md](../toeoetaja/toeoetaja-loomine.md "mention") ja [toeoetaja-leidmine.md](../toeoetaja/toeoetaja-leidmine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/employee/view?token=ea2397458ba644c6fd2d70b05adb6661&id=301'
```
{% endcode %}

### Vastuse näide

Töötaja andmete väljastamine õnnestub.&#x20;

```json
{
    "responseStatus": "ok",
    "employeeDetailView": {
        "Eesnimi": "Erik",
        "Perekonnanimi": "Uus",
        "E-post": "erik.uus@ra.ee",
        "Telefon": "+372 5322 5388",
        "Üksus": "Test osakond"
    }
}
```

{% hint style="info" %}
Töötaja andmed väljastatakse eestikeelsete väljanimedega, nii et neid on võimalik kasutajaliideses vahetult kuvada.
{% endhint %}

### Veateade

**error 5010** - töötajat ei leitud (määratud identifikaatoriga töötajat andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 5010,
    "errorMessage": "The requested employee does not exist."
}
```

{% hint style="info" %}
Pane tähele, et selles näites "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 OK".
{% endhint %}
