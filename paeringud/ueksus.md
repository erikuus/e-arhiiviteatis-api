---
description: Päringute dokumentatsioon
---

# Üksus

E-arhiiviteatise taotlusel tuleb kahes kohas määrata Sotsiaalkindlustusameti üksus:

* Juhul kui teatise tellijaks ja riigilõivu tasujaks ei ole isik, vaid Sotsiaalkindlustusameti üksus, tuleb taotlust luues määrata, milline üksus.
* Iga taotluse puhul tuleb määrata üksus, kuhu arhiiviteatis meilitsi edastatakse.

{% content-ref url="taotlus.md" %}
[taotlus.md](taotlus.md)
{% endcontent-ref %}

Samuti tuleb iga töötaja puhul määrata, millisesse üksusesse ta kuulub.

{% content-ref url="toeoetaja.md" %}
[toeoetaja.md](toeoetaja.md)
{% endcontent-ref %}

**Veebirakenduse ekraanivaated**

![](../.gitbook/assets/E-arhiiviteatis-Uus-taotlus.png) ![](../.gitbook/assets/E-arhiiviteatis-Uus-töötaja.png)

## Päringud

{% swagger method="get" path="/department/test" baseUrl="{{apiBaseUrl}}/ska" summary="Kättesaadavuse testimine" %}
{% swagger-description %}
Testib, kas üksust puudutav päringute grupp on kättesaadav. Normaaljuhul pole see vajalik, aga kui mingil tehnilisel põhjusel üksust puudutav päringute grupp muutub kättesaamatuks, näiteks annavad kõik päringud vastuseks 

_Internal Server Error_

, saab selle päringu kaudu tuvastada, millal päringud muutuvad jälle kättesaadavaks.
{% endswagger-description %}

{% swagger-parameter in="query" name="token" required="true" %}


[juurdepaeaesukood.md](../juurdepaeaesukood.md "mention")


{% endswagger-parameter %}

{% swagger-response status="200: OK" description="OK" %}
```javascript
{
    "responseStatus": "ok"
}
```
{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="error 500" %}
```javascript
{
    "responseStatus": "error",
    "errorCode": 500,
    "errorMessage": "DepartmentController do not have a method \"send\"."
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger method="post" path="/department/create" baseUrl="{{apiBaseUrl}}/ska" summary="Üksuse loomine" %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="query" name="token" required="true" %}


[juurdepaeaesukood.md](../juurdepaeaesukood.md "mention")


{% endswagger-parameter %}

{% swagger-parameter in="body" %}

{% endswagger-parameter %}

{% swagger-parameter in="body" %}

{% endswagger-parameter %}
{% endswagger %}
