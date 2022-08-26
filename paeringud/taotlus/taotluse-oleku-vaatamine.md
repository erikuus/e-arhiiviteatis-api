---
description: Päringu dokumentatsioon
---

# Taotluse oleku vaatamine

## <mark style="color:green;">GET</mark> ska/application/status

```
{{apiBaseUrl}}/ska/application/status?token={{accessToken}}&id={{applicationId}}
```

Väljastab taotluse identifikaatori alusel info selle kohta, millises olekus on taotluse menetlemine Rahvusarhiivis.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                                                                                                                                    |   |
| -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention")                                                                                                                |   |
| id \*    | Integer | <p>Taotluse identifikaator<br><br><em>NB! Taotluse identifikaatori saamise kohta vaata</em> <a data-mention href="taotluse-loomine.md">taotluse-loomine.md</a><em></em></p> |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/application/status?token=db9a1afb27d892ad3303095ce580f9cc&id=16610'
```
{% endcode %}

### Vastuse näide

Taotluse menetlemise oleku väljastamine õnnestub.&#x20;

```json
{
    "responseStatus": "ok",
    "applicationStatus": {
        "code": "REJECTED",
        "text": "Tagasilükatud",
        "htmlMessage": "<p>Rahvusarhiivil ei ole võimalik päringule (Urmas Toom 08.11.2021 10:08) vastata, vastavaid dokumente ei ole Rahvusarhiivile üle antud. Soovitame pöörduda Tallinna Tööstushariduskeskuse poole (info@tthk.ee).</p><p>Lugupidamisega</p><p>Manilve Randala<br />Rahvusarhiiv<br /><span style=\"font-size:10px;color:#666666;\">Nooruse 3, 50411 Tartu <br />tel +372 7387 500 <br />eteatis@ra.ee<br />www.ra.ee</span><br /></p>"
    }
}
```

Taotlus võib olla järgmistes olekutes:

| CODE             | TEXT          | SELGITUS                                                                                                                                                                                                                                                                                                                                                                                   |   |
| ---------------- | ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | - |
| DRAFT            | Koostamisel   | Taotlus on salvestatud, aga Rahvusarhiivi saatmata. Seda saab veel muuta ja sellele saab lisada manusena faile.                                                                                                                                                                                                                                                                            |   |
| SUBMITTED        | Saabunud      | Taotlus on saadetud Rahvusarhiivi. See on saabunud Rahvusarhiivi arhiivipäringute haldamise moodulisse, aga seda ei ole seal veel menetlema hakatad. Taotlust ei saa enam muuta ega kustutada ja sellele ei saa lisada faile                                                                                                                                                               |   |
| REJECTED         | Tagasilükatud | <p>Rahvusarhiivil ei ole võimalik arhiiviteatist väljastada. Taotluse menetlemine Rahvusarhiivis on lõpetatud.<br><br><em>NB! Selle oleku puhul on</em> <code>htmlMessage</code> <em>väli päringu vastuses täidetud.</em></p>                                                                                                                                                              |   |
| FORWARDED        | Edastatud     | Taotlus on edastatud Tallinna Linnaarhiivi, kuna Rahvusarhiivil puuduvad dokumendid, mille alusel saaks koostada arhiiviteatise. Taotluse menetlemine Rahvusarhiivis on lõpetatud.                                                                                                                                                                                                         |   |
| ASSIGNED\_UNIT   | Määratud      | Rahvusarhiiv on hinnanud, et saab taotluse töösse võtta, ja on esimese sammuna määranud üksuse, kelle ülesandeks on seda taotlust menetleda.                                                                                                                                                                                                                                               |   |
| WAITING\_PAYMENT | Makse ootel   | Taotlejale on saadetud makseteade arhiiviteatise eest riigilõivu tasumiseks, aga makset ei ole veel laekunud, mistõttu arhiiviteatist ei ole hakatud veel koostama.                                                                                                                                                                                                                        |   |
| CANCELED         | Tühistatud    | <p>Taotlus on tühistatud. Taotluse menetlemine Rahvusarhiivis on lõpetatud.<br><br><em>NB! Põhjused võivad olla erinevad. Näiteks võib taotleja leida üles dokumendi, mida ta arvas mitte omavat.</em></p>                                                                                                                                                                                 |   |
| OUTDATED         | Aegunud       | Kui taotlus on olnud makse ootel 14 päeva, saadetakse taotlejale esimene meeldetuletus. Kui taotlus on olnud makse ootel 28 päeva, saadetakse taotlejale teine meeldetuletus. Kui taotlus on olnud makse ootel 42 päeva, märgitakse see aegunuks. Makselink, mis saadeti taotlejale e-kirjaga, enam ei toimi, aga kui makse laekub eraldi pangaülekandega, võetakse taotlus uuesti töösse. |   |
| PAID             | Makstud       | Taotleja on tasunud riigilõivu. Taotlus ootab töösse võtmist ehk arhivaarile edastamist.                                                                                                                                                                                                                                                                                                   |   |
| BEING\_PROCESSED | Töösse võetud | Taotlus on edastatud arhivaarile, kes koostab sellele vastuseks arhiiviteatise.                                                                                                                                                                                                                                                                                                            |   |
| READY            | Valmis        | <p>Arhiiviteatis on valmis.<br><br><em>NB! Kui taotlus on selles olekus, saab kasutada päringut</em> <a data-mention href="taotluse-vastuse-vaatamine.md">taotluse-vastuse-vaatamine.md</a></p>                                                                                                                                                                                            |   |
| COMPLETED        | Lõpetatud     | <p>Sotsiaalkindlustusameti osakonnale on saadetud e-kiri, mis sisaldab e-arhiiviteatise allalaadimise linki. Taotluse menetlemine Rahvusarhiivis on lõpetatud.<br><br><em>NB! Kui taotlus on selles olekus, saab kasutada päringut</em> <a data-mention href="taotluse-vastuse-vaatamine.md">taotluse-vastuse-vaatamine.md</a></p>                                                         |   |

### Veateade

**error 3010** - taotlust ei leitud (määratud identifikaatoriga taotlust andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 3010,
    "errorMessage": "The requested application does not exist"
}
```

{% hint style="info" %}
Pane tähele, et selles näites "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 OK".
{% endhint %}
