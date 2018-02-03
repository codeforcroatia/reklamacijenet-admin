---
layout: category-post
title:  "Prijava o zaprimanju spama u predmetu"
date:   2017-09-16 00:00:00 -0000
categories: template
---
Kada korisnik prijavi da je neželjena poruka pristigla u postojeći predmet, a ako je predmet već riješen, potrebno je ukloniti neželjenu poruku i spriječiti dolazak novih neželjenih poruka.

Koraci:
1. U administraciji predmeta zabraniti zaprimanje novih odgovora
2. Sakriti dolaznu neželjenu poruku i staviti komentar za razlog skrivanja "Uklonjena je neželjena poruka."
3. Odgovoriti korisniku:

```
Dragi _______, 
hvala vam na prijavi! Ovo se ponekada dogodi ako e-mail adresa predmeta procuri. Ne brinite - vaša osobna email adresa je sigurna, ovdje se radi o jedinstvenoj adresi jednog specifičnog predmeta. Uklonili smo neželjenu poruku i zabranili dolazak novih odgovora po ovom predmetu, te neće više biti novih dolaznih poruka po ovom predmetu. Ako trebate slati povratnu poruku pravnoj osobi, učinite to tako da kreirate novi prigovor.

Lijep pozdrav,
[tvoje ime] - volonter na {{ site.portal.name }}
```
