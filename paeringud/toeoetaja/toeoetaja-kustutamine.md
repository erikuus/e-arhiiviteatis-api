---
description: Päringu dokumentatsioon
---

# Töötaja kustutamine

## <mark style="color:red;">DELETE</mark> ska/employee/delete

```
{{apiBaseUrl}}/ska/employee/delete?token={{accessToken}}&id={{employeeId}}
```

Kustutab töötaja identifikaatori alusel. Tegemist on n-ö SOFT DELETE kustutamisega, mis tähendab seda, et andmed jäävad andmebaasi alles ja need on jätkuvalt nähtavad taotluste juures, aga kustutatud töötaja identifikaatorit ei saa enam päringutes kasutada.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                     |   |
| -------- | ------- | ------------------------------------------------------------ | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| id \*    | Integer | Töötaja identifikaator                                       |   |

Töötaja identifikaatori saamise kohta vaata [toeoetaja-loomine.md](toeoetaja-loomine.md "mention") ja [toeoetaja-leidmine.md](toeoetaja-leidmine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request DELETE 'https://www.ra.ee/vau/index.php/api/ska/employee/delete?token=24aad44bab3b258b06e809cc53e9083e&id=301' \
--data-raw ''
```
{% endcode %}

### Vastuse näide

Töötaja on kustutatud.

```json
{
    "responseStatus": "ok"
}
```

### Veateade

**error 5010** - töötajat ei leitud (määratud identifikaatoriga töötajat andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 5010,
    "errorMessage": "The requested employee does not exist."
}
```

**error 5030** - töötaja kustutamine ebaõnnestus

```json
{
    "responseStatus": "error",
    "errorCode": 5030,
    "errorMessage": "Could not delete employee"
}
```

**error 5031** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 5031,
    "errorMessage": "Is not DELETE request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
