---
description: Päringu dokumentatsioon
---

# Taotluse kustutamine

## <mark style="color:red;">DELETE</mark> ska/application/delete

```
{{apiBaseUrl}}/ska/application/delete?token={{accessToken}}&id={{applicationId}}
```

Kustutab taotluse identifikaatori alusel. Kustutada saab taotlust, mis ei ole veel Rahvusarhiivi saadetud.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                                                                                                                                    |   |
| -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention")                                                                                                                |   |
| id \*    | Integer | <p>Taotluse identifikaator<br><br><em>NB! Taotluse identifikaatori saamise kohta vaata</em> <a data-mention href="taotluse-loomine.md">taotluse-loomine.md</a><em></em></p> |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request DELETE 'https://www.ra.ee/vau/index.php/api/ska/application/delete?token=846a0a7bc2be5e66cba566b0fcaeac3f&id=16610' \
```
{% endcode %}

### Vastuse näide

Taotlus on kustutatud.

```json
{
    "responseStatus": "ok"
}
```

### Veateade

**error 3010** - taotlust ei leitud (määratud identifikaatoriga taotlust andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 3010,
    "errorMessage": "The requested application does not exist"
}
```

**error 3020** - taotlust ei saa kustutada, kuna taotlus on juba Rahvusarhiivi saadetud

```json
{
    "responseStatus": "error",
    "errorCode": 3020,
    "errorMessage": "The requested application is in sent status and could not be deleted"
}
```

**error 3021** - taotlust ei saa kustutada (määratlemata tehnilistel põhjustel)

```json
{
    "responseStatus": "error",
    "errorCode": 3021,
    "errorMessage": "Deleting application failed"
}
```

**error 3022** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 3022,
    "errorMessage": "Is not DELETE request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
