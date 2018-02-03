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

### Odbacivanje spama koji dolazi u holding pen

Alaveteli sadrži listu spam adresa. Bilo koja dolazna poruka koja se nalazi na toj listi, a koja bi inače bila zaprimljena u holding pen, bit će odbijena te se neće prikazati u administracijskom sučelju.

Ako vidite spam poruku u holding penu, provjerite da li je poruka poslana na određenu e-mail adresu. Ukoliko je, ta e-mail adresa je postala “meta” za spam te ju trebate dodati na listu spam adresa. Iz tog razloga, Alaveteli će automatski odbaciti bilo koju poruku koja dolazi s te adrese.

E-mail adresa koja nije povezana s prigovorom (odnosno, ona čije poruke dolaze u holding pen) postaje meta za spam kada ju prikupe spammeri. Postoji nekoliko razloga zašto takva nevažeća adresa postoji. Na primjer, možda je krivo upisana prilikom ručnog odgovora. Naše iskustvo sa vođenja projekta Imamo pravo znati je da sa sigurnošću možete odbaciti e-mail koji dolazi na takve adrese jednom kada su ciljani na ovaj način. Legitimni e-mailovi koji dolaze u holding pen obično imaju jedinstvene greške (na primjer, nedostajanje zadnjeg znaka u e-mail adresi zbog pogreške prilikom kopiranja ili lijepljenja) i priroda životnog ciklusa pritužbe znači da obično nisu korišteni za spam dok nisu efektivno mrtvi.

Za dodavanje e-mail adrese na listu spam adresa, potrebno je kopirati e-mail adresu sa primljene poruke i zalijepiti ju na listu spam adresa. Najjednostavniji način za napraviti to je klikom na **Summary** na vrhu administratorskog sučelja te potom klikom na **Put misdelivered responses with the right requests** kako bi ste vidjeli sadržaj holding pena.

> Ako nema poruka u holding penu, Alaveteli neće prikazati ovaj link. Odlično — nema krivo dostavljenih odgovora koji trenutačno zahtjevaju vašu pažnju!

Unutar holding pena moguće je vidjeti popis e-mailova koje je potrebno pregledati – kliknite na naslov e-maila kako bi ste vidjeli cijelu poruku i njene detalje. Kopirajte `To:` e-mail adresu i pod Actions kliknite na link **Spam Addresses**. Zalijepite e-mail adresu u područje unosa teksta i kliknite tipku **Add Spam Address**.

Možete vidjeti listu spam adresa (odnosno, svih poznatih ciljanih-spam e-mail adresa) u bilo koje vrijeme putem administracijskog sučelja preko `/admin/spam_addresses`. 

Bilo koja e-mail adresa se može maknuti sa ove liste klikom na tipku **Remove** pokraj e-maila. Naravno, ovo neće obnoviti poruke koje su bile odbijene, ali Alaveteli neće odbiti nove poruke poslane na ovu adresu.

Uzmite u obzir da ako konstantno vidite spam poruke u holding penu, kontaktirajte system administratora koji će možda trebati implementirati (ili povećati) anti-spam mjere na vašem MTA.

### Stvaranje, mijenjanje i upload podataka pravnih osoba

Postoje tri načina na koja se mogu promijeniti podaci pravnih osoba:

* *Create* (Kreiranje) — nova pravna osoba se može stvoriti u administrativnom sučelju. Klikni na **Authorities** te zatim na tipku **New Public Authority**.
* *Edit* (Uređivanje) — nakon stvaranja nove pravne osobe, e-mail adresa i drugi podaci se mogu uređivati u administratorskom sučelju. Potrebno je kliknuti na link **Authorities**, pronaći željenu pravnu osobu te kliknuti na **edit**.
* *Upload* (Slanje) — moguće je kreirati ili urediti više pravnih osoba istovremeno uploadanjem datoteke koja sadrži podatke u vrijednostima koje su međusobno odijeljene zarezom, tj. u CSV formatu. Ovo se može koristiti za stvaranje novih pravnih osoba, ali i za uređivanje već postojećih pravnih osoba. Potrebno je kliknuti na **Authorities** te zatim na tipku **Import from CSV**. Pogledajte ostatak ovog poglavlja priručnika za više detalja vezanih za slanje datoteke.

Mogućnost uploada može biti od velike koristi – posebno prilikom formiranja Alaveteli stranice – jer je čest slučaj da se podaci, poput kontakt podataka pravnih osoba, prikupljaju u tablicama. Mogućnost uploada čini jednostavnim inicijalan upload podataka na stranicu. Također omogućava ažuriranje podataka ukoliko se podaci promijene nakon što su uploadani. 

Kako bi se podaci u tablici iskoristili za ažuriranje pravnih osoba na {{ site.portal.name }}, potrebno ih je izvesti, tj. kliknuti na Export tablice u CSV formatu. Ovo je datoteka koju je kasnije moguće modificirati i uploadati.

Prvi red CSV datoteke treba početi sa znakom # (znak indicira da ovaj red ne sadrži podatke) i mora sadržavati popis stupaca za podatke koji se nalaze u slijedećim redovima. Imena stupaca moraju:
- biti u prvom redu
- točno se podudarati sa očekivanim nazivom te sadržavati name i `request_email` (pogledati tablicu koja se nalazi niže)
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

Da pojasnimo:
- Postojeće pravne osobe se ne mogu preimenovati uploadanjem: ako trebate to učiniti, koristite administracijsko sučelje radi uređivanja postojećih podataka i promijenite ime pravne osobe u internetskom sučelju.
- Kada pravna osoba već postoji odnosno polje `name` se potpuno podudara s nazivom postojeće pravne osobe, i ako je neko polje prazno, import će ostaviti postojeću vrijednost tog polja nepromijenjenom — odnosno, ti podaci na stranici se neće promijeniti. To znači da je potrebno uključiti samo podatke koje želite ažurirati.
- Stupac `i18n suffix` može prihvatiti internacionalna imena. Dodajte točku te zatim jezični kod, na primjer: `name.hr` za hrvatski jezik (hr). Ovo mora biti regija koja je definirana u popisu mogućih jezika u konfiguraciji aplikacije. Ako ne specificirate i18n suffix, zadani jezik za Reklamacije.net će biti pretpostavljen na zadanu vrijednost.
- Možete specificirati prazan unos u CSV datoteci tako da ne stavljate znakove između zareza.
- Ako unos sadrži zarez, stavite ga u dvostruke navodnike kao u nastavku: `"Comma, Inc"`.
- Ako unos sadrži dvostruke navodnike, svaki od njih morate zamijeniti sa dva navodnika (dakle, `"` postaje `""`) te staviti cijeli unos u dvostruke navodnike: `"U ""navodnicima"""` (bit će uvezeno kao `U "navodnicima"`).

Na primjer, niže su navedeni podaci u CSV formatu, spremni za upload, za tri pravne osobe. Prvi red uvijek definira imena stupaca. Slijedeća tri reda sadrže podatke (jedan red za svaku pravnu osobu):

```
#name,short_name,short_name.es,request_email,notes
XYZ Library Inc.,XYZ Library,XYX Biblioteca,info@xyz.example.com,
Ejemplo Town Council,,Ayuntamiento de Ejemplo,etc@example.com,Lorem ipsum.
"Comma, Inc.",Comma,,comma@example.com,"e.g. <a href=""x"">link</a>"
```

Imajte na umu da ako "Ejemplo Town Council" već postoji na stranici, prazan unos u polju `short_name` će ostaviti postojeću vrijednost za taj stupac nepromijenjenom.

Ukoliko želite uploadati CSV datoteku, potrebno je ulogirati se u administrativno sučelje i kliknuti na **Authorities** te potom na **Import from CSV file** i izabrati pripremljenu datoteku.

Specificirajte **What to do with existing tags?** s jednom od slijedećih opcija:
- *zamijeni postojeće oznake novima* - Za svaku pravnu osobu koju se ažurira, sve postojeće oznake će biti maknute i zamijenjene novima iz CSV datoteke
- *dodaj nove oznake postojećima* - Postojeće oznake će ostati nepromijenjene, a oznake iz CSV datoteke će biti nadodane.
  
Možete dodati **Tag to add entries to / alter entries for**. Ta oznaka će biti primijenjena na svaku pravnu osobu koja se uvozi iz CSV datoteke.

Predlažemo da prvo kliknete na probno pokretanje **Dry run** - ono će proći kroz datoteku i prikazati promijene koje će napraviti u bazi podataka, bez promijene podataka. Provjerite izvještaj: on prikazuje do kojih promjena bi došlo da su podaci zaista učitani nakon čega slijedi poruka:

`Dry run was successful, real run would do as above.`

Ukoliko ne vidite ništa iznad tog reda, to znači da probno pokretanje nije uzrokovalo predložene promijene. 

Ukoliko je sve bilo OK prilikom probnog pokretanja, kliknite **Upload**. Ovo će ponoviti proces, ali ovaj put će napraviti promijene u bazi podataka stranice. Ako uočite grešku poput `invalid email`, moguće da je e-mail adresa krivo unesena ili (vjerojatnije) da CSV datoteka ne sadrži stupac `request_email`.

### Kreiranje tablice s postojećim pravnim osobama

Možete lako napraviti tablicu koja sadrži pravne osobe koje već postoje na stranici. Ako kombiniranirate sa mogućnošću uploada opisanu iznad ovo može biti praktičniji način ažuriranja podataka od uređivanja podataka u administracijskom sučelju. 

Kako bi izvezli postojeće podatke pravnih osoba, potrebno je biti na naslovnoj stranici Reklamacije.net (ne administracijskoj) te klikniti **View Authorities**. Zatim kliknite **List of all authorities (CSV)** kako bi dobili CSV datoteku u kojoj možete raditi promijene korištenjem programa za uređivanje tablica te ju uploadati prema gornjim uputama.

Bit će potrebno maknuti neke stupce koji nisu podržani u uvozu podataka te možda promijeniti neke nazive – pogledajte nazive stupaca gore. Također, uočite da, u pravilu, izvezena tablica ne sadrži stupac `request_email`. Ako želite ažurirati e-mail adrese, potrebno je u tablicu ručno dodati stupac naziva `request_email` te popuniti e-mail adrese za svaku pravnu osobu koju je potrebno ažurirati. Pravne osobe koje nemaju unesenu vrijednost u nekom stupcu, zadržat će postojeću vrijednost za taj atribut.

>Kada izvozi pravne osobe u CSV formatu, Alaveteli nikada ne uključuje pravne osobe koje imaju oznaku `site_administration`. Ako pokrećete razvojni server sa inicijalnim uzorkom podataka, jedini primjer pravne osobe pod nazivom “Internal admin authority" ima ovu oznaku. Stoga, ako kliknete **List of all authorities (CSV)**, dobit ćete CSV datoteku koja ne sadrži podatke. Morate dodati vlastite pravne osobe (bez oznake `site_administration`) prije nego ih možete izvesti.

### Zabrana pristupa korisniku

U slučaju objavljivanja neželjenih sadržaja, korisniku se može zabraniti pristup stranici (na primjer tzv. *spammeru* ili *trolleru*). Potrebno je prijaviti se u administracijsko sučelje na `/admin` te u gornjem djelu ekrana kliknuti na **Users**. 

Pronađite korisnika kojem želite zabraniti pristup stranici i kliknite na njegovo ime te potom na **Edit**.

Potrebno je objasniti zašto je korisniku zabranjen pristup stranici upisom određenog teksta u polje *Ban text*. Imajte na umu da je taj tekst javno dostupan na profilu korisnika. Zatim kliknite na **Save** i korisniku će biti zabranjen pristup stranici (obično se kaže da je korisnik *banan*).

### Brisanje korisnika

Korisnik se ne može u potpunosti obrisati sa Alaveteli stranice, ali ako zaista trebate označiti korisnički profil suvišnim, možete to napraviti na slijedeći način:

- pronaći korisnika u administratorskom sučelju i kliknuti **Edit**
- izmijeniti ime korisničkog računa u `[suvišan račun]` i maknuti bilo kakav opis
- ako korisnik ima profilnu sliku, potrebno je kliknuti na **Clear photo** kako bi se slika maknula
- pronaći *Url name* korisničkog računa i postaviti njegovu e-mail adresu da se poklapa s njime, pomoću domene `invalid`, na primjer `url_name@invalid`
- nakon što ste kliknuli **Save**, prijavite se kao taj korisnik klikom na gumb **Log in as…**
- kliknite na **Change your password** te potom potvrdite lozinku klikom na **Send me the email** — kolikom na taj link, poslat će se e-mail sa linkom za potvrdu lozinke, ali e-mail poruka neće nigdje otići (jer je e-mail domena `@invalid`)… ali, možete pristupiti tom linku odlaskom na profilnu stranicu korisnika putem administracijskog sučelja te klikom na link *e-mail token* u njihovom posljednjem *Post redirect-u*
- promijeni lozinku korisnika u nasumičan niz 
- ako je korisniku zabranjen pristup korisničkom računu (vidi gore), promijenite tekst u polju *Ban text* u nešto neutralno

### Anonimnost korisnika

Ponekad je nužno ukloniti detalje korisnika sa Alaveteli stranice kako se ti detalji ne bi pronašli preko internetskih pretraživača. Kako bi se to napravilo, prvo slijedite korake koji su isti kao i prilikom brisanja korisnika, zamjenjujući *name* sa `[ime uklonjeno]`. Zatim, potrebno je ukloniti bilo kakve reference na korisnika sa stranice. Ukoliko imate puno pritužbi na stranici, ovo može biti veliki posao. 

- Možete dodati cenzuru kako bi ste uklonili ime korisnika sa pritužbi te zamijeniti ime sa `[ime uklonjeno]`. Ovo zahtijeva čitanje svih pritužbi. Potražite imena (i možda skraćenice) u referentnim brojevima itd. Možda će biti nužno doraditi pravila cenzure kako bi ste osigurali da su sve forme imena obuhvaćene cenzurom. Pogledajte više o uređivanju. 
- Provjerite komentare te ih po potrebi uredite radi uklanjanje imena.

### Omogućivanje korisniku da podnese više pritužbi

Alaveteli ima postavke konfiguracije za maksimalan broj predmeta po korisniku po danu `MAX_REQUESTS_PER_USER_PER_DAY`, a koji određuje maksimalan broj predmeta koje običan korisnik može poslati tijekom jednog dana. Ukoliko korisnik tijekom 24 sata pokuša poslati veći broj prigovora od tog broja, dobit će poruku koja će ga obavijestiti o dosezanju limita u broju prigovora, ali i potaknuti da nas kontaktiraju putem kontakt podataka ako smatra da ima dobar razlog tražiti da se ograničenje broja prigovora poveća.

Ukoliko želite povećati limit za podnošenje predmeta za određenog korisnika, potrebno je pristupiti administracijskom sučelju, kliknuti na **Users** te potom na ime odabranog korisnika. Zatim je potrebno kliknuti na gumb **Edit** i označiti kućicu **No rate limit** te kliknuti **Save**.

### Skupni predmeti

Ponekad jedan korisnik želi poslati pritužbu većem broju pravnih osoba što se naziva skupnim predmetima (*batch requests*). U pravilu, Alaveteli ne dozvoljava korisnicima slanje skupnih predmeta.

> Smatramo da se skupni predmeti mogu zloupotrijebiti — korisnici mogu poslati loše smišljene ili uznemiravajuće prigovore koje mogu zasmetati pravnim osobama ili naštetiti reputaciji ove stranice. Međutim, dobro smišljene skupne prigovori mogu biti od velike koristi u borbi zaštite potrošača.
>
> Preporučujemo dozvoljavanje slanja skupnih predmeta korisnicima za koje je uočeno da su poslali veći broj dobro sastavljenih prigovora različitim pravnim osobama.
>
> Korisnici mogu izabrati koje pravne osobe će uključiti u skupne predmete. Također, mogu poslati prigovor svakoj pravnoj osobi na stranici. Preporuča se ovo dozvoliti samo korisnicima kojima vjerujete.

Kako bi omogućili slanje skupnih predmeta, system administrator prvo treba postaviti `ALLOW_BATCH_REQUESTS` u `true` u general.yml konfiguraciji aplikacije. 

Ova postavka još nikome ne dozvoljava slanje skupnih predmeta. Slanje skupnih predmeta se konfigurira zasebno za svakog pojedinog korisnika kojemu želite omogućiti ovu opciju. Kako bi to učinili, potrebno je otići na administracijsko sučelje, kliknuti na **Users** te zatim na ime korisnika kojem želite omogućiti slanje skupnih pritužbi. Kliknite gumb **Edit** i označite kućicu **Can make batch requests** i kliknite **Save**. 

Ako ste korisniku omogućili sanje skupnih predmeta, kada krenu slati prigovore, uz kućicu gdje mogu izabrati pravnu osobu, vidjet će link  za slanje skupnih predmeta (*make a batch request*). Kada je pritužba poslana, Alaveteli će napraviti stranicu predmeta s popisom prigovora poslanih svakoj pravnnoj osobi kao da je korisnik slao individualne prigovore.

### Ponovno slanje predmeta ili slanje predmeta drugoj pravnoj osobi

Ako ste ispravili e-mail adresu pravne osobe, možete ponovno poslati postojeću prigovor toj pravnoj osobi na novi e-mail. Također, korisnik može poslati pritužbu krivoj pravnoj osobi. U tom slučaju, možete promijeniti pravnu osobu u pritužbi te ponovno poslati pritužbu pravnoj osobi. Za upute pogledajte *ponovno slanje pritužbe ili slanje pritužbe drugoj pravnoj osobi*.

### Skrivanje predmeta

Ako prigovor sadrži uznemiravajući, odnosno neprikladan sadržaj te ako nije u skladu sa Zakonom o zaštiti potrošača, može se sakriti. Skriveni predmet ostaje vidljiv podnositelju pritužbe i drugim administratorima. Za upute, pogledajte *[skrivanje predmeta][1]*.

Skriveni predmeti mogu normalno zaprimiti odgovor, ali će odgovor također biti skriven.

### Brisanje predmeta

Prigovor se može obrisati sa portala {{ site.portal.name }}. Za detaljnije upute, pogledajte [brisanje predmeta][2]. 
Odgovori na obrisane predmete će biti zaprimljeni u holding pen.

### Skrivanje primljene ili poslane poruke

Ponekad je potrebno sakriti određenu primljenu ili poslanu poruku, posebno u slučaju ako je netko u poruku uključio osobne podatke. To je moguće napraviti u administracijskom sučelju poruke.

Administracijskom sučelju poruke možete pristupiti putem linka iz dijela “Outgoing messages” ili “Incoming messages” sa administraciske stranice specifičnog predmeta ili direktno sa javne stranice predmeta klikom na link **admin** u poruci. Kada pristupite administracijskom sučelju poruke, možete promijeniti njeno isticanje (*prominence*). 

Postavite **prominence** u **hidden** kako bi sakrili poruku od svih osim od administratora ili u **requester_only** kako bi omogućili da poruku vidi podnositelj prigovora (i administratori). Ukoliko možete, dodajte tekst u polje **Reason for prominence**. To će biti prikazano na mjestu gdje se nalazila poruka na stranici pritužbe kako bi se znalo zašto je poruka sakrivena.

### Brisanje primljene ili poslane poruke

Primljene i poslane poruke također mogu biti potpuno obrisane. Ovo je obično primjenjivo samo u slučaju sadržaja, poput spam poruka, kojima se neće više trebati pristupati. Inače, predlažemo sakrivanje poruka.

Kao i kod sakrivanja, ovo se može napraviti u administracijskom sučelju poruke.

Administracijskom sučelju poruke možete pristupiti putem linka iz dijela “Outgoing messages” ili “Incoming messages” sa administraciske stranice specifičnog predmeta ili direktno sa javne stranice predmeta klikom na link **admin** u poruci.

Kada pristupite administracijskom sučelju poruke, možete je obrisati korištenjem gumba **Destroy message** u slučaju da se radi o primljenoj poruci ili korištenjem gumba **Destroy outgoing message** ako se radi o poslanoj poruci.

> Koristite s oprezom!

### Uređivanje poslane poruke

U nekim slučajevima je potrebno urediti poslanu poruku. Primjerice, ako je korisnik u nju slučajno uključio privatne informacije koje ne želi javno objaviti na stranici. Možete slijediti jedan od **admin** linkova sa javne stranice predmeta ili pronaći predmet u administracijskom sučelju putem izbornika **Requests**. Spustite se do sekcije "Outgoing Messages" i kliknite **Edit**. Na slijedećoj stranici možete urediti poruku te snimiti nastale promjene. Izmijenjena verzija će se pojaviti na Alaveteli stranici, a neizmijenjena verzija je već poslana pravnoj osobi.

### Uređivanje ili skrivanje komentara
	
Komentari su jednostavniji od prigovora ili poruka jer postoje samo na stranici predmeta, tj. nisu poslani nigdje. Ako predmet ima komentare, oni će biti prikazani u administracijskom sučelju tog predmeta. Spustite se niže na stranici do popisa komentara, a svaki pojedini komentar možete uređivati klikom na njegov naslov.

Predlažemo da vaše promijene učinite eksplicitnima. Primjerice, ako uklanjate osobne podatke, umjesto da ih samo obrišete, radije ih zamijenite sa nečim što indicira što je uklonjeno: `[uklonjena je osobna informacija]`.

Kad god je moguće, trebate naznačiti što je uklonjeno i, ako je potrebno obrazloženje, zašto je to trebalo biti sakriveno.

Možete sakriti (ili otkriti) komentar odabirom odgovarajuće stavke, pod nazivom **Visible**, iz drop-down liste. Nakon što ste završili sa promjenama, kliknite **Save**.

Također je moguće sakriti (ili otkriti) komentare u skupnim predmetima. Spustite se na donji dio stranice do popisa komentara u administracijskom sučelju predmeta i označite kućice za one komentare koje želite izmijeniti. Zatim kliknite **Hide selected** ili **Unhide selected**.

### Skrivanje određenog teksta iz predmeta upotrebom cenzure

Cenzuriranje se može odnositi na predmet ili na korisnika. Ta pravila definiraju dijelove teksta koji će se odstraniti iz predmeta i svih povezanih datoteka, npr. prilozi u primljenim porukama; ili iz svih predmeta povezanih s određenim korisnikom, te tekst koji zamijenjuje cenzurirani dio teksta.

U binarnoj datoteci, tekst koji zamjenjuje cenzurirani tekst će uvijek biti niz znakova ‘x’ koji su duljinom identični tekstu koji zamjenjuju kako bi se očuvala duljina datoteke. Cenzuriranje datoteka ne radi konzistentno jer je teško napraviti cenzuru koje će se u potpunosti poklapati sa sadržajem priložene datotetke stoga uvijek provjerite rezultate. Cenzurirajte stvarni tekst i označite kućicu **View as HTML**; ovo je trenutačno (rujan, 2013.) generirana forma necenzuriranog PDF-a ili druge binarne datoteke.

Možete cenzurirati korištenjem redovnih izraza (RegEx - regular expressions) označavanjem kućice **Is it regexp replacement?** u admnistracijskom sučelju za cenzuriranje. U suprotnom će se doslovno samo zamijeniti bilo koje pojavljivanje unesenog teksta.

Poput cenzura koje se temelje na običnom tekstu, cenzura za redovne RegEx izraze će biti prepisana binarnim datotekama koje su povezane sa predmetom. Stoga, redovni RegEx izraz koji je prilično slab u odnosu na ono sa čime se treba slagati, može imati neočekivane posljedice ako se također preklapa sa slijedom znakova u binarnoj datoteci. Također, kompleksni ili slabi redovni izrazi mogu biti vrlo zahtjevni za korištenje (u nekim slučajevima mogu otežati cijelo korištenje aplikacije), stoga:
- ograničite RegEx primjenu na slučajeve koji se inače ne mogu lako pokriti
- neka budu što jednostavniji i konkretniji.

Kako bi cenzurirali dio prigovora, potrebno je pristupiti administracijskom sučelju predmeta, otići na dno stranice te kliknuti na gumb **New censor rule (for this request only)**. Na slijedećoj stranici unesite tekst koji želite zamijeniti, npr. "određena privatna informacija," tekst s kojim privatnu informaciju želite zamijeniti, npr. `[osobna informacija]` te je potrebno dodati komentar kako bi drugi administratori znali zašto je informacija sakrivena.

Za dodavanje cenzure korisniku, kako bi se cenzura odnosila na svaki predmet koji korisnik napravi, pristupite stranici korisnika preko administracijskog sučelja. Stranici korisnika možete pristupiti klikom na **Users** na administracijskom izborniku te pronalaskom željenog korisnika ili preko administratorskog linka za odabranog korisnika sa javnog sučelja.

Kada se nalazite u administracijskom sučelju korisnika, na dnu stranice kliknite na gumb **New censor rule**. Na slijedećoj stranici unesite tekst koji želite zamijeniti, npr. "moje pravo ime je Bruce Wayne," tekst s kojim želite zamijeniti privatnu informaciju, npr. `[osobna informacija]` te je potrebno dodati komentar kako bi drugi administratori znali zašto je informacija sakrivena.

[1]: skrivanje templatea
[2]: brisanje predmeta
