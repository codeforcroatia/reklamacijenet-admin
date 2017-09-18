---
layout: post
title:  "Redovno održavanje"
date:   2017-09-17
---

### Administratorske ovlasti i administrativno sučelje

Administrativno sučelje se nalazi na URL putanji `/admin`. Tom dijelu portala mogu pristupati samo korisnici koji su administratori.

Za dodavanje novih administratora, obrati se voditelju projekta.

Uz ovlast pristupanja administrativnom sučelju portala, korisnici koji su administratori imaju dodatne ovlasti na korisničkom dijelu portala. Administratori mogu:

* kategorizirati bilo koji predmet
* vidjeti predmete koji su potpuno sakriveni
* otvoriti "admin" linkove koji se nalaze na stranici individualnih predmeta, komentara, korisnika i pravnih osoba.

### Poruke u holding penu

Alaveteli smješta dolazne poruke u "Holding pen" ako se njihova `To:` e-mail adresa ne može automatski asocirati s postojećim predmetom u sustavu.

Dva su najčešća razloga za to:

* predmet je zatvoren i ne prihvaća nove dolazne poruke
* u e-mail adresi postoji greška (npr. kada je pošiljatelj pisao email adresu možda je pogrešno napisao jedna ili više znakova u e-mail adresi)

Kada se to dogodi, poruka čeka u holding penu dok je administrator ne premjesti u ispravan predmet, ili je obriše.

Da to učiniš, ulogiraj se u administrativno sučelje. Ako postoji poruka u holding penu, ispod "Things to do" vidjeti ćeš **Put misdelivered responses with the right request**. Klikni na tu poruku - dobiti ćeš popis poruka koje trebaju pažnju administratora. Klikni na jednu od njih da vidiš detalje.

*Ako poruka ne pripada niti jednom predmetu, možeš je obrisati. Klikni na tipku "Destory message". Oprez, jednom obrisana poruka se više ne može vratiti.*

Kada otvoriš detalje neke poruke u holding penu, vidjeti ćeš da je Alaveteli pokušao pronaći pravilan predmet za tu poruku. Ako je točno pretpostavio, i ako je taj odgovor dio pretostavljenog predmeta, *title_url* će biti će popunjen - klikni tipku **Redeliver to another request**.

Ako Alaveteli nije mogao pretpostaviti točan predmet, ili ako je krivo pretpostavio, pogledaj u sirovoj e-mail poruci `To:` adresu i sadržaj poruke. Sada trebaš zaključiti kojem predmetu ono pripada. Oblik e-mail adrese koju Alaveteli generira izgleda ovako `[INCOMING_EMAIL_PREFIX]+request-[id]-[idhash]@[DOMAIN]` odnosno `foi+request-3-691c8388@example.com`. 

U tom obliku, prvi broj nakon dijela `request-` je redni broj (id) predmeta. Možeš potražiti predmete u administrativnom sučelju putem linka **Requests** u admin toolbaru. Kada pronađeš pravilan predmet, kopiraj jedno od dvoje: *id* ili *url_title*.

> **Kako pronaći *id* ili *url_title* nekog predmeta?**
> 
>* *id* predmeta nalazi se nakon `/show/` u URL-u predmeta u administrativnom sučelju. Na primjer, ako je URL `/admin/request/show/118`, tada je *id* `118`. Slično tome ako želiš u administrativnom sučelju vidjeti detalje predmeta s *id*-jem `119`, možeš ga pogledati na URL-u `/admin/request/show/119`.
> 
>* *url_title* nekog predmeta nalazi se nakon `/request/` u URL-u kada gledaš neki predmet na javnoj stranici na portalu vidljivu korisnicima. Na URL-u `/request/how_many_vehicles`, *url_title* je `how_many_vehicles`.

Sada kada ste identificirali predmet kojem pripada poruka, vratite se na holding pen stranicu. Pod "Actions" dolazne poruke umetnite *id* ili *url_title*. Kliknite na tipku **Redeliver to another request**.

Ta poruka je sada asocirana s pravilnim predmetom. Više se ne nalazi u holding penu, već se prikazuje ispod pravilnog predmeta na javnom dijelu stranice s predmetom.

### ODBACIVANJE SPAMA KOJI DOLAZI U HOLDING PEN

### Stvaranje, mijenjanje i upload podataka pravnih osoba

Postoje tri načina na koja se mogu promijeniti podaci pravnih osoba:

* *Create* (Kreiranje) — nova pravna osoba se može stvoriti u administrativnom sučelju. Klikni na **Authorities** te zatim na tipku **New Public Authority**
* *Edit* (Uređivanje) — nakon stvaranja nove pravne osobe, e-mail adresa i drugi podaci se mogu uređivati u administratorskom sučelju. Potrebno je kliknuti na link **Authorities**, pronaći željenu pravnu osobu te kliknuti na **edit**.
* *Upload* (Slanje) — moguće je kreirati ili urediti više pravnih osoba istovremeno uploadanjem datoteke koja sadrži podatke u vrijednostima koje su međusobno odijeljene zarezom, tj. u CSV formatu. Ovo se može koristiti za stvaranje novih pravnih osoba, ali i za uređivanje već postojećih pravnih osoba. Potrebno je kliknuti na **Authorities** te zatim na tipku **Import from CSV**. Pogledajte ostatak ovog poglavlja priručnika za više detalja vezanih za slanje datoteke.

Mogućnost uploada može biti od velike koristi – posebno prilikom formiranja Alaveteli stranice – jer je čest slučaj da se podaci, poput kontakt podataka pravnih osoba, prikupljaju u tablicama. Mogućnost uploada čini jednostavnim inicijalan upload podataka na stranicu. Također omogućava ažuriranje podataka ukoliko se podaci promijene nakon što su uploadani. 

Kako bi se podaci u tablici iskoristili za ažuriranje pravnih osoba na Reklamacije.net, potrebno ih je izvesti, tj. kliknuti na Export tablice u CSV formatu. Ovo je datoteka koju je kasnije moguće modificirati i uploadati.

Prvi red CSV datoteke treba početi sa znakom # (znak indicira da ovaj red ne sadrži podatke) i mora sadržavati popis stupaca za podatke koji se nalaze u slijedećim redovima. Imena stupaca moraju:
- biti u prvom redu
- točno se podudarati sa očekivanim nazivom te sadržavati name i request_email (pogledati tablicu koja se nalazi niže)
- pojavljivati se u istom redoslijedu kao i pripadajuće stavke u redovima podataka koji slijede

Većina programa za uređivanje tablica će samostalno kreirati CSV datoteku uz pretpostavku da se oprezno specificira točan naziv na vrhu svakog stupca. Potrebno je koristiti nazive točno onako kako su prikazani – ako Alaveteli uoči neprepoznatljivo ime stupca, uvoz podataka neće biti moguć.

| naziv stupca            | i18n sufix?  | napomene                                     |
|-------------------------|--------------|----------------------------------------------|
| `name`                  | da           | *Ovaj stupac mora biti prisutan.* Puno ime pravne osobe. Ako se podudara s postojećom pravnom osobom, ta pravna osoba će biti ažurirana — u suprotnom, kreirat će se nova pravna osoba. |
| `request_email`         | da           | *Ovaj stupac mora biti prisutan, ali može ostati prazan.* E-mail na koji se šalju pritužbe. |
| `short_name`            | da           | Neke pravne osobe su poznate pod skraćenim imenom. |
| `notes`                 | da           | Napomene, javno objavljeno (može sadržavati HTML). |
| `publication_scheme`    | da           | Ne koristi se. |
| `disclosure_log`        | da           | Ne koristi se. |
| `home_page`             | da           | URL internetske stranice pravne osobe. |
| `tag_string`            | ne           | Oznake odvojene razmakom. |

...



