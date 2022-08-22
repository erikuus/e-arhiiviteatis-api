---
description: Päringu dokumentatsioon
---

# Üksuse vaatamine

## <mark style="color:green;">GET</mark> ska/department/view

```
{{apiBaseUrl}}/ska/department/view?token={{accessToken}}&id={{departmentId}}
```

Väljastab üksuse andmed identifikaatori alusel.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                     |   |
| -------- | ------- | ------------------------------------------------------------ | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| id \*    | Integer | Üksuse identifikaator                                        |   |

Üksuse identifikaatori saamise kohta vaata [ueksuse-loomine.md](ueksuse-loomine.md "mention")ja [ueksuse-otsimine.md](ueksuse-otsimine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/department/view?token=bd266e2a556dc5331917d86252262c30&id=30'
```
{% endcode %}

### Vastuse näide

Üksuse andmete väljastamine õnnestub.&#x20;

```json
{
    "responseStatus": "ok",
    "departmentDetailView": {
        "Nimi": "Test osakond",
        "Aadress": "Tammsaare 8-25, Tartu",
        "Postiindeks": "51006",
        "E-post": "erik.uus@ra.ee",
        "Telefon": "+372 5322 5388"
    }
}
```

{% hint style="info" %}
Üksuse andmed väljastatakse eestikeelsete väljanimedega, nii et neid on võimalik kasutajaliideses vahetult kuvada.
{% endhint %}

### Veateade

**error 4010** - üksust ei leitud (määratud identifikaatoriga üksust andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 4010,
    "errorMessage": "The requested department does not exist."
}
```

{% hint style="info" %}
Pane tähele, et selles näites "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 OK".
{% endhint %}
