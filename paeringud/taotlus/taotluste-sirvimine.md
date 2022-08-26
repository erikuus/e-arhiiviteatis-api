---
description: Päringu dokumentatsioon
---

# Taotluste sirvimine

## <mark style="color:green;">GET</mark> ska/application/list

{% code overflow="wrap" %}
```

{{apiBaseUrl}}/ska/application/list?token={{accessToken}}&created={{searchDate}}&applicant_firstname={{searchString}}&applicant_lastname={{searchString}}&applicant_id_nr={{idNumber}}&content={{contentKeyword}}&department_id={{departmentId}}&employee_id={{employeeId}}
```
{% endcode %}

Väljastab taotluste nimekirja otsiparameetrite alusel, mida võib, aga ei pea kasutama. Maksimaalselt väljastatakse 100 taotluse andmed. Taotlused on järjestatud koostamise aja järgi kasvavalt (ASC).

### Parameetrid (query params)

\*-ga märgitud on kohustuslikud

| NIMI                 | TÜÜP (PIKKUS) | SELGITUS                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |   |
| -------------------- | ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | - |
| token \*             | String        | [juurdepaeaesukood.md](../../juurdepaeaesukood.md "mention")                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |   |
| created              | Date          | <p>Taotluse koostamise aeg<br><br><em>NB! Lubatud formaat on</em> <code>dd.MM.yyyy</code></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |   |
| applicant\_firstname | String        | Taotleja eesnimi (lubatud metamärgid)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |   |
| applicant\_lastname  | String        | Taotleja perekonnanimi (lubatud metamärgid)                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |   |
| applicant\_id\_nr    | String        | Taotleja isikukood                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |   |
| content              | String        | <p>Taotluse sisu võtmesõna<br><br><em>NB! Toimivad järgmised võtmesõnad:</em><br><em></em><code>study</code> <em>- õppimine</em><br><em></em><code>work</code> <em>- töötamine</em><br><em></em><code>farm</code> <em>- talus töötamine</em><br><em></em><code>military</code> <em>- sõjaväeteenistus</em><br><em></em><code>rear</code> <em>- viibimine nõukogude tagalas</em><br><em></em><code>prison</code> <em>- vangilaagris ja asumisel viibimine</em><br><em></em><code>work_camp</code> <em>- töölaagris, koonduslaagris või sõjavangilaagris viibimine</em><br><em></em><code>ww2_estonia</code> <em>- II maailmasõja ajal Eestisse toomine</em><br><em></em><code>ww2_germany</code> <em>- II maailmasõja ajal Saksamaale saatmine</em><br><em></em><code>other</code> <em>- muud märkused ja täiendused</em></p> |   |
| department\_id       | Integer       | <p>Üksuse identifikaator, kus taotlus koostati<br><br><em>NB! Üksuse identifikaatori saamise kohta vaata</em> <a data-mention href="../ueksus/ueksuse-loomine.md">ueksuse-loomine.md</a><em>ja</em> <a data-mention href="../ueksus/ueksuse-leidmine.md">ueksuse-leidmine.md</a><em></em></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |   |
| employee\_id         | Integer       | <p>Töötaja identifikaator, kes taotluse koostas<br><br><em>NB! Töötaja identifikaatori saamise kohta vaata</em> <a data-mention href="../toeoetaja/toeoetaja-loomine.md">toeoetaja-loomine.md</a> <em>ja</em> <a data-mention href="../toeoetaja/toeoetaja-leidmine.md">toeoetaja-leidmine.md</a></p>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |   |

{% hint style="info" %}
Otsingu metamärgid: \* - tähistab mistahes hulka märke; ? - tähistab ühte märki. Näiteks: otsing "eri\*" leiab "Eri", "Erik", "Erika"; otsing "eri?" leiab eelmainitutest ainult "Erik".
{% endhint %}

### Päringu näide (cUrl)

{% code overflow="wrap" %}
```shell
curl --location --request GET 'https://www.ra.ee/vau/index.php/api/ska/application/list?token=846a0a7bc2be5e66cba566b0fcaeac3f&applicant_firstname=er*&applicant_lastname=uu?&content=study' \
```
{% endcode %}

### Vastuse näide

Taotluste nimekirja väljastamine õnnestub.

```json
{
    "responseStatus": "ok",
    "applicationListView": [
        {
            "id": 16623,
            "Koostatud": "26.08.2022 14:50",
            "Eesnimi": "Erik",
            "Perekonnanimi": "Uus",
            "Isikukood": "37307302715",
            "Taotluse sisu": "Õppimine",
            "Töötaja": "Erik Uus",
            "Üksus": "Test osakond"
        },
        {
            "id": 16595,
            "Koostatud": "09.08.2022 15:02",
            "Eesnimi": "Erik",
            "Perekonnanimi": "Uus",
            "Isikukood": "37307302715",
            "Taotluse sisu": "Õppimine; Sõjaväeteenistus",
            "Töötaja": "Erik Uus",
            "Üksus": "Test osakond"
        }
    ]
}
```

{% hint style="info" %}
Taotluste andmed väljastatakse eestikeelsete väljanimedega, nii et neid on võimalik kasutajaliideses vahetult kuvada.
{% endhint %}

{% hint style="info" %}
Pane tähele, et ülaltoodud näites on dokumentatsiooni autor märkinud nii taotleja kui töötaja andmeteks oma isikuandmed. Seda on tehtud ainult seepärast, et näite koostamine oleks lihtsam.
{% endhint %}

Mitte ühtegi taotlust ei leitud.

```json
{
    "responseStatus": "ok",
    "applicationListView": []
}
```
