---
description: Miks see API on loodud ja mida sellega teha saab?
---

# Sissejuhatus

## Veebirakendus

Alates 2013. aastast on Sotsiaalkindlustusameti töötajad saanud kasutada Rahvusarhiivi loodud ja Rahvusarhiivi domeenis asuvat veebirakendust [https://www.ra.ee/eteatis/](https://www.ra.ee/eteatis/), et taotleda sealtkaudu Rahvusarhiivilt e-arhiiviteatisi.

Nimetatud veebirakendus võimaldab luua, muuta ja kustutada e-arhiiviteatise taotlusi, kasutajaid (SKA töötajaid, kes taotlusi koostavad) ja üksuseid (SKA osakondi, millesse töötajad kuuluvad). Loodud taotlustele on võimalik lisada faile ja lõplikult vormistatud taotlused saab saata Rahvusarhiivi, nii et need laekuvad Rahvusarhiivi arhiiviteatiste menetlemise moodulisse.

Veebirakendus on selles mõttes autonoomne, et selle kasutajad (SKA töötajad) saavad kõiki vajalikke tegevusi teha ilma välise abita (Rahvusarhiivi töötajate abita).&#x20;

**Veebirakenduse ekraanivaated**

![](.gitbook/assets/E-arhiiviteatis-Avaleht.png) ![](.gitbook/assets/E-arhiiviteatis-Uus-taotlus.png)

![](.gitbook/assets/E-arhiiviteatis-Vaata-taotlust.png) ![](.gitbook/assets/E-arhiiviteatis-Taotlused.png)

![](<.gitbook/assets/E-arhiiviteatis-Halda-töötajaid (1).png>) ![](.gitbook/assets/E-arhiiviteatis-Halda-üksusi.png)

## API

E-arhiiviteatise taotlemise API, mida käesolev lehekülg dokumenteerib, dubleerib ülalmainitud veebirakenduse kõiki funktsioone.&#x20;

API kaudu saab luua, muuta ja kustutada e-arhiiviteatise taotlusi, kasutajaid (SKA töötajaid, kes taotlusi koostavad) ja üksuseid (SKA osakondi, millesse töötajad kuuluvad). Loodud taotlustele on võimalik lisada faile ja lõplikult vormistatud taotlused saab saata Rahvusarhiivi, nii et need laekuvad Rahvusarhiivi arhiiviteatiste menetlemise moodulisse.

Niisiis on selle API abil võimalik luua mistahes teise infosüsteemi osana mistahes domeeni alla kasutajaliides, mis sarnaneb Rahvusarhiivi loodud rakendusega[ https://www.ra.ee/eteatis/](https://www.ra.ee/eteatis/).

API kasutab sama _backendi_ ja salvestab andmeid samasse baasi, kuhu veebirakenduski. API kaudu loodud taotlusi saab vaadata veebirakenduses ja vastupidi — veebirakenduses loodud taotluste andmeid saab pärida API kaudu. Pikemas perspektiivis kaob veebirakendus ära ja jääb ainult API. &#x20;

**API Postman ekraanivaade**

![](.gitbook/assets/postman.png)
