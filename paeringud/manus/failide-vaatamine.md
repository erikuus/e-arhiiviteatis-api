---
description: Päringu dokumentatsioon
---

# Failide vaatamine

## <mark style="color:green;">GET</mark> ska/file/list

{% code overflow="wrap" %}
```
{{apiBaseUrl}}/ska/file/list?token={{accessToken}}&application_id={{applicationId}}
```
{% endcode %}

Väljastab taotluse identifikaatori järgi sellele taotlusele lisatud failide nimekirja. Failid on järjestatud failinime järgi kasvavalt (ASC).

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI            | TÜÜP (PIKKUS) | SELGITUS                                                     |   |
| --------------- | ------------- | ------------------------------------------------------------ | - |
| token \*        | String        | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |
| application\_id | Integer       | Taotluse identifikaator, mille faile vaadatakse              |   |

Taotluse identifikaatori saamise kohta vaata [taotluse-loomine.md](../taotlus/taotluse-loomine.md "mention")

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl
```
{% endcode %}

### Vastuse näide

Failide nimekirja väljastamine õnnestub.

```json
{
    
}
```

{% hint style="info" %}
Failide andmed väljastatakse eestikeelsete väljanimedega, nii et neid on võimalik kasutajaliideses vahetult kuvada.
{% endhint %}

Mitte ühtegi faili ei leitud.

```json
{
    "responseStatus": "ok",
    "fileListView": []
}
```
