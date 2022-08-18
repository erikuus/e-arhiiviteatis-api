---
description: Päringu dokumentatsioon
---

# user/verify

{% swagger method="post" path="" baseUrl="{{apiBaseUrl}}/api/user/verify" summary="Kasutaja kontrollimine ja tokeni väljastamine" %}
{% swagger-description %}
Kõigile päringutele tuleb ühe parameetrina lisada juurde ajutiselt kehtiv kood ehk token. Tokeni väljastab päring, mis kontrollib kasutajanime ja salasõna järgi, kas kasutaja on olemas.
{% endswagger-description %}

{% swagger-parameter in="body" name="username" type="String" required="true" %}
Rahvusarhiivi kliendiportaalis
{% endswagger-parameter %}

{% swagger-parameter in="body" type="String" name="password" required="true" %}

{% endswagger-parameter %}
{% endswagger %}
