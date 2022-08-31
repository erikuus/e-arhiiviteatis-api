---
description: Päringu dokumentatsioon
---

# Taotluse muutmine

## <mark style="color:blue;">PUT</mark> ska/application/update

```
{{apiBaseUrl}}/ska/application/update?token={{accessToken}}&id={{applicationId}}
```

Muudab taotluse andmeid identifikaatori alusel. Muuta saab taotlust, mis ei ole veel Rahvusarhiivi saadetud.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP    | SELGITUS                                                                                                                                                                    |   |
| -------- | ------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| token \* | String  | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention")                                                                                                                |   |
| id \*    | Integer | <p>Taotluse identifikaator<br><br><em>NB! Taotluse identifikaatori saamise kohta vaata</em> <a data-mention href="taotluse-loomine.md">taotluse-loomine.md</a><em></em></p> |   |

### Sisend (body raw json)

JSON peab sisaldama vähemalt taotluse objekti `Application`:

```json
{
    "Application": {}
}
```

Kui taotlusele soovitakse lisada üks või mitu õppeastust ja/või töökohta, siis peab JSON sisaldama ka `Study` ja/või `Work` objekte:&#x20;

```json
{
    "Application": {},
    "Study": [{},{}],
    "Work": [{},{}]    
}
```

#### Application

\*-ga märgitud on kohustuslikud

| NIMI                           | TÜÜP (PIKKUS) | SELGITUS                                                                                                                                                                                                                                                                                                                               |   |
| ------------------------------ | ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| applicant\_firstname \*        | String (64)   | Taotleja eesnimi                                                                                                                                                                                                                                                                                                                       |   |
| applicant\_lastname \*         | String (64)   | Taotleja perekonnanimi                                                                                                                                                                                                                                                                                                                 |   |
| applicant\_birthday \*         | Date          | <p>Taotleja sünnikuupäev<br><br><em>NB! Lubatud formaat on</em> <code>dd.MM.yyyy</code></p>                                                                                                                                                                                                                                            |   |
| applicant\_address \*          | String (256)  | Taotleja aadress                                                                                                                                                                                                                                                                                                                       |   |
| applicant\_zip \*              | String (16)   | Taotleja aadressi postiindeks                                                                                                                                                                                                                                                                                                          |   |
| applicant\_phone               | String (64)   | Taotleja telefoninumber                                                                                                                                                                                                                                                                                                                |   |
| applicant\_email               | String (256)  | Taotleja e-posti aadress                                                                                                                                                                                                                                                                                                               |   |
| applicant\_id\_nr              | String(11)    | <p>Taotleja isikukood<br><br><em>NB! Veebirakenduse sisestusvormis isikukoodi ei ole, mistõttu seda pole ka seniste taotluste juures. Kuna Rahvusarhiivil on palju ka välismaiseid kliente, moodustatakse kliendikood nimest ja sünnikuupäevast. Isikukood on lisatud spetsiaalselt API jaoks ja seda saab kasutada otsingus.</em></p> |   |
| applicant\_names\_info         | String        | Taotleja nimemuutused ja erinevad nimekujud õppimise/töötamise ajal                                                                                                                                                                                                                                                                    |   |
| applicant\_department\_id      | Integer       | Üksuse identifikaator, juhul kui teatise tellijaks ja riigilõivu tasujaks ei ole isik, vaid üksus                                                                                                                                                                                                                                      |   |
| study\_comments                | String        | <p>Märkused, täiendused õppimise kohta<br><br><em>NB! Selle välja väärtus salvestatakse ainult siis, kui on määratud vähemalt üks õppeasutus, st</em> <code>JSON</code><em>-is on vähemalt üks</em> <code>Study</code> <em>objekt.</em>  </p>                                                                                          |   |
| work\_pension\_info            | String        | <p>Õigus sooduspensionile, vajalike tingimuste kirjeldus<br><br><em>NB! Selle välja väärtus salvestatakse ainult siis, kui on määratud vähemalt üks töökoht, st</em> <code>JSON</code><em>-is on vähemalt üks</em> <code>Work</code> <em>objekt.</em></p>                                                                              |   |
| work\_comments                 | String        | <p>Märkused, täiendused töötamise kohta<br><br><em>NB! Selle välja väärtus salvestatakse ainult siis, kui on määratud vähemalt üks töökoht, st</em> <code>JSON</code><em>-is on vähemalt üks</em> <code>Work</code> <em>objekt.</em></p>                                                                                               |   |
| farm\_info                     | String        | Talus töötamine: maakond, vald, talu nimi, aeg                                                                                                                                                                                                                                                                                         |   |
| military\_info                 | String        | Sõjaväeteenistus: Eesti Kaitseväes teenimise puhul väeosa ja teenimise aeg, Saksa sõjaväes teenimise puhul kõik teadaolevad andmed                                                                                                                                                                                                     |   |
| rear\_info                     | String        | Viibimine nõukogude tagalas: kellega koos tagalasse saadeti (andmed vanemate kohta) ja kõik muud teadaolevad andmed                                                                                                                                                                                                                    |   |
| prison\_info                   | String        | Vangilaagris ja asumisel viibimine: kellega koos laagrisse/asumisele saadeti (andmed vanemate kohta), millal ja kelle poolt karistatud, karistuse kandmise aeg ja koht, vabanemise aeg                                                                                                                                                 |   |
| work\_camp\_info               | String        | Töölaagris, koonduslaagris või sõjavangilaagris viibimine: laagri nimetus, kinnipidamise ja vabastamise aeg                                                                                                                                                                                                                            |   |
| ww2\_estonia\_info             | String        | II maailmasõja ajal Eestisse toomine: kellega koos toodi (andmed vanemate kohta), toomise aeg ja koht, laagrite nimed ja kinnipidamisaeg, kuhu suunati elama ja tööle                                                                                                                                                                  |   |
| ww2\_germany\_info             | String        | II maailmasõja ajal Saksamaale saatmine: kellega koos saadeti (andmed vanemate kohta), kust ja millal saadeti, laagrite nimed, töökohad Saksamaal, Eestisse naasmise aeg ja koht                                                                                                                                                       |   |
| other\_comments                | String        | Muud märkused ja täiendused taotluse kohta                                                                                                                                                                                                                                                                                             |   |
| taxnotice\_delivery\_method \* | String        | <p>Valik: kas taotleja soovib arhiivilt teadet riigilõivu tasumise kohta tavapostiga või e-postiga<br><br><em>NB! Lubatud väärtused on:</em><br><em></em><code>DELIVERY_POSTAL</code> <em>või</em> <code>DELIVERY_EMAIL</code></p>                                                                                                     |   |
| copy\_delivery\_method         | String        | <p>Valik: kas taotleja soovib koopiat arhiiviteatisest tavapostiga või e-postiga<br><br><em>NB! Lubatud väärtused on:</em><br><em></em><code>DELIVERY_POSTAL</code> <em>või</em> <code>DELIVERY_EMAIL</code></p>                                                                                                                       |   |
| employee\_id                   | Integer       | <p>Sotsiaalkindlustusameti töötaja, kes taotluse koostas/sisestas<br><br><em>NB! Töötaja identifikaatori saamise kohta vaata</em> <a data-mention href="../toeoetaja/toeoetaja-loomine.md">toeoetaja-loomine.md</a> <em>ja</em> <a data-mention href="../toeoetaja/toeoetaja-leidmine.md">toeoetaja-leidmine.md</a><em></em></p>       |   |
| department\_id                 | Integer       | <p>Sotsiaalkindlustusameti üksus, kuhu arhiiviteatis edastatakse<br><br><em>NB! Üksuse identifikaatori saamise kohta vaata</em> <a data-mention href="../ueksus/ueksuse-loomine.md">ueksuse-loomine.md</a><em>ja</em> <a data-mention href="../ueksus/ueksuse-leidmine.md">ueksuse-leidmine.md</a><em></em></p>                        |   |

#### Study

\*-ga märgitud on kohustuslikud

| NIMI           | TÜÜP (PIKKUS) | SELGITUS                      |   |
| -------------- | ------------- | ----------------------------- | - |
| institution \* | String (512)  | Õppeasutuse nimetus           |   |
| period \*      | String (512)  | Õppimise aeg (kuupäevaliselt) |   |
| specialty      | String (512)  | Eriala                        |   |

#### Work

\*-ga märgitud on kohustuslikud

| NIMI           | TÜÜP (PIKKUS) | SELGITUS                       |   |
| -------------- | ------------- | ------------------------------ | - |
| institution \* | String (512)  | Asutuse nimetus                |   |
| period \*      | String (512)  | Töötamise aeg (kuupäevaliselt) |   |
| specialty \*   | String (512)  | Eriala                         |   |

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request PUT 'https://www.ra.ee/vau/index.php/api/ska/application/update?token=db9a1afb27d892ad3303095ce580f9cc&id=16610' \
--header 'Content-Type: application/json' \
--data-raw '{
    "Application": {
        "applicant_firstname": "Erik",
        "applicant_lastname": "Uus",
        "applicant_id_nr": "37307302715",
        "applicant_birthday": "31.07.1973",
        "applicant_address": "Tammsaare 8-31",
        "applicant_zip": "51008",
        "applicant_phone": "",
        "applicant_email": "",
        "applicant_names_info": "",
        "applicant_department_id": null,
        "study_comments": "",
        "work_pension_info": "",
        "work_comments": "",
        "farm_info": "",
        "military_info": "military info",
        "rear_info": "",
        "prison_info": "",
        "work_camp_info": "",
        "ww2_estonia_info": "",
        "ww2_germany_info": "",
        "other_comments": "",
        "taxnotice_delivery_method": "DELIVERY_POSTAL",
        "copy_delivery_method": "DELIVERY_POSTAL",
        "employee_id": null,
        "department_id": null
    },
    "Study": [
        {
            "institution": "Nõo Keskkool",
            "period": "1981 - 1992",
            "specialty": ""
        },
        {
            "institution": "Tartu Ülikool",
            "period": "1992 - 1996",
            "specialty": "usuteadus"
        }
    ],
    "Work": [
        {
            "institution": "Rahvusarhiiv",
            "period": "2007 - 2023",
            "specialty": "programmeerija"
        },
        {
            "institution": "Babahh OÜ",
            "period": "2013 - 2019",
            "specialty": "programmeerija"
        }
    ]
}'
```
{% endcode %}

### Vastuse näide

Taotluse muutmine õnnestub.

```json
{
    "responseStatus": "ok"
}
```

### Veateated

**error 3010** - taotlust ei leitud (määratud identifikaatoriga taotlust andmebaasis ei ole)

```json
{
    "responseStatus": "error",
    "errorCode": 3010,
    "errorMessage": "The requested application does not exist"
}
```

**error 3040** - taotlust ei saa muuta, kuna taotlus on juba Rahvusarhiivi saadetud

```json
{
    "responseStatus": "error",
    "errorCode": 3040,
    "errorMessage": "The requested application is in sent status and could not be updated"
}
```

**error 3041** - taotlust ei saa muuta, kuna sisendväärtused ei valideeru&#x20;

```json
{
    "responseStatus": "error",
    "errorCode": 3041,
    "errorMessage": "Could not update application",
    "errors": [
        {
            "applicant_firstname": [
                "Eesnimi ei tohi olla tühi."
            ],
            "taxnotice_delivery_method": [
                "Mittelubatud väärtus."
            ],
            "employee_id": [
                "Töötaja peab olema arv."
            ],
            "department_id": [
                "Üksus \"0\" ei eksisteeri."
            ]
        }
    ]
}
```

**error 3042** - päringu _raw body_ ei sisalda _JSON_ _stringi_ või selles puudub _Application_ objekt

```json
{
    "responseStatus": "error",
    "errorCode": 3042,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 3043** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 3043,
    "errorMessage": "Is not PUT request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
