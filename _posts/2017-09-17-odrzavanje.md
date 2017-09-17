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

