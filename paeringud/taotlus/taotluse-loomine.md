---
description: Päringu dokumentatsioon
---

# Taotluse loomine

## <mark style="color:orange;">POST</mark> ska/application/create

```
{{apiBaseUrl}}/ska/application/create?token={{accessToken}}
```

Loob uue taotluse ja tagastab selle identifikaatori.

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI     | TÜÜP   | SELGITUS                                                     |   |
| -------- | ------ | ------------------------------------------------------------ | - |
| token \* | String | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention") |   |

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

```shell
curl --location --request POST 'https://www.ra.ee/vau/index.php/api/ska/application/create?token=db9a1afb27d892ad3303095ce580f9cc' \
--header 'Content-Type: application/json' \
--data-raw '{
    "Application": {
        "applicant_firstname": "Erik",
        "applicant_lastname": "Uus",
        "applicant_birthday": "30.07.1973",
        "applicant_address": "Tammsaare 8-25",
        "applicant_id_nr": "37307302715",
        "applicant_zip": "51006",
        "applicant_phone": "+37253225388",
        "applicant_email": "erik.uus@gmail.com",
        "applicant_names_info": "Uks, Uss",
        "applicant_department_id": null,
        "study_comments": "Märkused, täiendused",
        "work_pension_info": "Õigus sooduspensionile, vajalike tingimuste kirjeldus",
        "work_comments": "Märkused, täiendused",
        "farm_info": "Maakond, vald, talu nimi, aeg",
        "military_info": "Kirjeldus; Eesti Kaitseväes teenimise puhul märkida väeosa ja teenimise aeg, Saksa sõjaväes teenimise puhul kõik teadaolevad andmed",
        "rear_info": "Kirjeldus; kellega koos tagalasse saadeti (andmed vanemate kohta) ja märkida kõik teadaolevad andmed",
        "prison_info": "Kirjeldus; kellega koos laagrisse/asumisele saadeti (andmed vanemate kohta), millal ja kelle poolt karistatud, karistuse kandmise aeg ja koht, vabanemise aeg",
        "work_camp_info": "Laagri nimetus, kinnipidamise ja vabastamise aeg",
        "ww2_estonia_info": "Kirjeldus; kellega koos toodi (andmed vanemate kohta), toomise aeg ja koht, laagrite nimed ja kinnipidamisaeg, kuhu suunati elama ja tööle",
        "ww2_germany_info": "Kirjeldus; kellega koos saadeti (andmed vanemate kohta), kust ja millal saadeti, laagrite nimed, töökohad Saksamaal, Eestisse naasmise aeg ja koht",
        "other_comments": "Märkused, täiendused",
        "taxnotice_delivery_method": "DELIVERY_EMAIL",
        "copy_delivery_method": "DELIVERY_EMAIL",
        "employee_id": null,
        "department_id": null
    },
    "Study": [
        {
            "institution": "Nõo Keskkool",
            "period": "1980 - 1991",
            "specialty": ""
        },
        {
            "institution": "Tartu Ülikool",
            "period": "1991 - 1995",
            "specialty": "usuteadus"
        }
    ],
    "Work": [
        {
            "institution": "Rahvusarhiiv",
            "period": "2006 - 2022",
            "specialty": "programmeerija"
        },
        {
            "institution": "Babahh OÜ",
            "period": "2014 - 2018",
            "specialty": "programmeerija"
        }
    ]
}'
```

### Vastuse näide

Taotluse loomine õnnestub ja tagastatakse loodud taotluse identifikaator.

```json
{
    "responseStatus": "ok",
    "applicationId": 16610
}
```

### Veateated

**error 3050** - taotlust ei saa luua, kuna sisendväärtused ei valideeru&#x20;

```json
{
    "responseStatus": "error",
    "errorCode": 3050,
    "errorMessage": "Could not create application",
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

**error 3051** - päringu _raw body_ ei sisalda _JSON_ _stringi_ või selles puudub _Application_ objekt

```json
{
    "responseStatus": "error",
    "errorCode": 3051,
    "errorMessage": "Request body is invalid or empty"
}
```

**error 3052** - vale meetod

```json
{
    "responseStatus": "error",
    "errorCode": 3052,
    "errorMessage": "Is not POST request"
}
```

{% hint style="info" %}
Pane tähele, et neis näidetes "responseStatus" on "error", aga vastuse "HTTP response status code" on "200 __ OK".&#x20;
{% endhint %}
