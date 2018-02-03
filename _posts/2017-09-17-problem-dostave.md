---
layout: category-post
title:  "Neodgovoreni predmeti"
date:   2017-09-17 00:00:00 -0000
categories: template
---

Kada primjetiš da neka pravna osoba ne odgovara na uzastopne poruke, potrebno je istražiti razlog:

1. pogledaj e-mail logove
2. ako poruka nije uspješno poslana, ponovno je pošalji "Resend" i pričekaj odgovor poslužitelja u e-mail logu (možda ćeš tek sljedeći dan vidjeti log zapis za novoposlanu poruku)
3. poruka uspješno poslana - u slučaju da utvrdiš da neke pravne osobe uzastopno ne odgovaraju a s naše strane sve izgleda uredno, moguće je da je njihov e-mail poslužitelj označio našu poruku kao spam
4. kontaktiraj tu pravnu osobu:


```
Poštovani,
e-mail zapisi s našeg poslužitelja {{ site.portal.name }} potvrđuju da je [naziv pravne osobe] zaprimilo e-mail [datum]. Zaprimljen je odgovor od e-mail poslužitelja ove pravne osobe u kojem je navedeno:
"250 2.0.0 Message received OK" <[prepisati_iz_mail_loga_XXX] message>

Cjelokupni zapisi s poslužitelja kopirani su u prilogu ove poruke - proslijedite poruku vašem informatičkom odjelu, mogu im biti od pomoći.

Ako je poruka slučajno označena kao spam, predlažemo dodavanje domene {{ site.portal.domain }} na vašu listu pouzdanih kontakata kako se to ne bi ponovno dogodilo u budućnosti.

Također, ponovno smo poslali poruku.

Lijep pozdrav,
[tvoje ime], volonter na {{ site.portal.name }}
```
