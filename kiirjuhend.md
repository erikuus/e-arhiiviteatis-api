---
description: Konkreetsed näited, kuidas kasutada API põhifunktsioone
---

# Kiirjuhend

{% hint style="info" %}
See kiirjuhend seletab näidete varal API põhilisi funktsioone. Me ei süvene siin detailidesse ega kommenteeri päringute kõiki parameetreid, kuna need on põhjalikult dokumenteeritud järgnevatel lehekülgedel. Siin me loome kiirelt uue osakonna ja lisame sinna uue töötaja. Seejärel loome selle töötaja nimel uue taotluse, lisame sellele faili ja saadame taotluse Rahvusarhiivi. Lõpuks kuvame me taotluse detailvaate ja pärime, mis olekus on taotluse menetlemine. Me vaatame paralleelselt, kuidas need tegevused kajastuvad veebirakenduse kasutajaliideses. Me teeme seda kõike test-keskkonnas.&#x20;
{% endhint %}

## Juurdepääsu taotlemine

Käesolev API on üks moodul Rahvusarhiivi suuremast API-süsteemist. API kasutaja autentimine ja autoriseerimine toimub kõigi moodulite puhul ühtmoodi.&#x20;

Kõigepealt tuleb luua konto Rahvusarhiivi virtuaalses uurimissaalis: [https://www.ra.ee/vautest/index.php/et/account/create](https://www.ra.ee/vautest/index.php/et/account/create).&#x20;

Seejärel tuleb saata API kasutamise taotlus e-kirjaga aadressil admin.vau@ra.ee. Kirjale tuleb lisada registreeritud kasutajanimi ja selgitus, millist API-moodulit ja milleks soovitakse kasutada. Selle kiirjuhendi jaoks registreerin ma kasutaja "erik" ja taotlen ligipääsu e-arhiiviteatise API-moodulile.&#x20;

Kui Rahvusarhiivi administraator rahuldab mu taotluse ja annab kasutajale "erik" vastava õiguse, saan ma oma kasutajanime ja salasõna kasutades teha kõiki e-arhiiviteatise API päringuid.&#x20;

Kui ma unustan oma salasõna, saan teha uue siin: [https://www.ra.ee/vautest/index.php/et/account/forgotPassword](https://www.ra.ee/vautest/index.php/et/account/forgotPassword)

## Tokeni pärimine

Kõigile päringutele tuleb ühe parameetrina lisada juurde ajutiselt kehtiv kood ehk _token_. Kui _token_ puudub või on aegunud, päring ei õnnestu.

_Tokeni_ pärimiseks käivitame me järgmise päringu:

```
curl --location --request POST '{{apiBaseUrl}}/api/user/verify' \
--form 'username="erik"' \
--form 'password="•••••••"'
```

{% hint style="info" %}
See ja kõik järgnevad päringu näited on cUrl formaadis. Muutuja \{{apiBaseUrl\}} on käesoleva kiirjuhendi kontekstist https://www.ra.ee/vautest/index.php/. Tärnide asemel tuleb kasutada salasõna, mis registreeriti Rahvusarhiivi virtuaalses uurimissaalis ja mis on seotud kontoga, millele Rahvusarhiivi administraator andis API kasutamise eriõiguse.
{% endhint %}

Päringu vastuseks on JSON:

```json
{
    "responseStatus": "ok",
    "userId": 3,
    "userFirstname": "Erik",
    "userLastname": "Uus",
    "userEmail": "erik.uus@ra.ee",
    "accessToken": "71e0d98f1ab52c225d655359190b6844",
    "tokenLifetime": 3600,
    "requestUnixTime": 1660724872
}
```

## Osakonna loomine

Kasutades eelnevas vastuses saadud _token_it, käivitame päringu:

```
curl --location --request POST '{{apiBaseUrl}}/api/ska/department/create?token=71e0d98f1ab52c225d655359190b6844' \
--data-raw '{
    "name": "Test osakond",
    "address": "Tammsaare 8-25, Tartu",
    "zip": "51006",
    "email": "erik.uus@ra.ee",
    "phone": "+372 5322 5388"
}'
```

Päringu vastuseks on JSON:

```json
{
    "responseStatus": "ok",
    "departmentId": 36
}
```

Veebirakenduse näeb loodud osakond välja nii:

![](<.gitbook/assets/E-arhiiviteatis-Halda-üksusi (1).png>)
