---
layout: category-post
title:  "Promjena e-mail adrese pravne osobe"
date:   2017-09-17 00:00:00 -0000
categories: template
---

Za početak, ako je ovo pravna osoba, treba [provjeriti stranicu te pravne osobe][1] na [{{ site.portal.name }} portalu][2] jer je možda i tamo potrebno izmijeniti e-mail adresu.

Nakon promijene e-mail adrese pravne osobe, potrebno je obavijestiti korisnika koji je predložio izmjenu e-mail adrese:

```
Dragi _______,
hvala na prijedlogu za ažuriranje e-mail adrese. Adresa pravne osobe je ažurirana u slijedeću e-mail adresu: [nova e-mail adresa] te će se nove pritužbe slati na tu e-mail adresu.

Molimo vas da nam javite ukoliko želite da ponovno pošaljemo druge predmete na novu e-mail adresu.

Slijedeći predmet je ponovno poslan na novu adresu: _______

Lijep pozdrav,
[tvoje ime], volonter na {{ site.portal.name }}
```

Ukoliko nema odgovora na predmet koji je ponovno poslan pravnoj osobi ili se e-mail poruka ne može isporučiti, moguće je da e-mail poruka nije prošla kroz anti-spam software na primateljevom poslužitelju. U tom slučaju se savjetuje da sa druge e-mail adrese pošalješ e-mail pravnoj osobi kako bi se osiguralo da e-mailovi poslani s portala {{ site.portal.name }} mogu proći kroz njihov anti-spam software:

```
Poštovani,
e-mail poruke poslane s našeg poslužitelja nisu isporučeni primatelju na vašoj strani.

Bili bi veoma zahvalni kada bi mogli sa svojim informatičkim odjelom provjeriti da e-mailovi primljeni od {{ site.portal.name }} nisu završili u spamu te da postavite domenu {{ site.portal.domain }} u vašu whitelistu.

Lijep pozdrav,
[tvoje ime], volonter na {{ site.portal.name }}
```

[1]:  {{ site.portal.url }}/body/list/all
[2]:  {{ site.portal.url }}
