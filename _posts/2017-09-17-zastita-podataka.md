---
layout: category-post
title:  "Zaštita podataka"
date:   2017-09-17 00:00:00 -0000
categories: template
---

Kada korisnik zatraži uklanjanje osobnih podataka ili osjetljivih osobnih podataka, npr. ako korisnik želi da uklonimo njegovo ime kompletno sa stranice:

1. procijeni predmet, uz referencu na Zakon o zaštiti osobnih podataka; nemoj automatski pretpostaviti da nešto treba sakriti, procijeni štetu načinjenu osobi koja je predmet osobnih podataka; imaj na umu da **osjetljivi** osobni podaci zahtijevaju brzu akciju i uklanjanje
2. pokušaj saznati zašto želi ukloniti svoje ime, objasni da je portal trajna arhiva predmeta, objasni tehničke poteškoće uklanjanja svih podataka (ako je potrebno)
3. kada korisnik inzistira na uklanjanju osobnih podataka, anonimiziraj ime korisnika tako da ostaviš inicijale u korisničkom računu kako ne bi bilo zbunjujuće u postojećim predmetima ove osobe, a kada je potrebno zaštiti osobne podatke svugdje napravi cenzuru imena i u sadržaju predmeta
4. ako je teško cenzurirati osobne podatke, npr. uklanjanje osobnih podataka iz slike ili PDF-a; traži pravne osobe da ponovno pošalju odgovor s cenzuriranim osobnim podacima (ovo je ujedno dobar trening da u budućnosti nauče da moraju cenzurirati osobne podatke)
5. kada se tekst cenzurira, dobro je ostaviti komentar ispod predmeta s razlogom cenzure
6. pošalji obavijest korisniku koji je tražio uklanjanje negovih podataka:

```
Dragi ________,
obaviještavam vas da smo postupili sukladno vašem zahtjevu za uklanjanje vaših osobnih podataka s portala {{ site.portal.name }}.

Portal {{ site.portal.name }} prikuplja najnužnije osobne podatke potrebne za slanje predmeta pritužbe putem ovog internetskog servisa uz privolu korisnika. Korisnik može povući privolu koje je ranije dao za prikuplajnje osobnih podataka.

Vaši osobni podaci su uklonjeni odnosno anonimizirani na portalu. Podaci potrebni za normalan rad portala nisu mjenjani te i dalje možete pristupiti s vašom e-mail adresom na portal.

Lijep pozdrav,
[tvoje ime], volonter na {{ site.portal.name  }}
```
