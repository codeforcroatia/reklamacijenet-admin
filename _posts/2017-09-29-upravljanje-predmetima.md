---
layout: post
title:  "Upravljanje predmetima"
date:   2017-09-29
---

Alaveteli olakšava korisnicima u slanju pisanih predmeta - prigovora. Vi kao administrator trebate znati nekoliko stvari koje možete raditi s poslanim predmetom. 

Predmet se kreira automatski kada korisnik podnese (i kada je potrebno) potvrdi slanje predmeta. Alaveteli ga tada šalje na email adresu odgovorne pravne osobe i rukuje zaprimljene odgovore po predmetu. Taj se postupak odvija bez bilo kakve intervencije administratora, ali ponekada ćete trebati izmijeniti neke dijelove predmeta, odnosno izmijeniti način na koji će Alaveteli rukovati njime.

# U kojem je statusu predmet?

Svaki predmet prolazi kroz niz promjena stanja koja pokazuju njegov napredak kroz vrijeme. Uobičajeno će novi predmet biti u `waiting_response` (čeka odgovor) statusu dok se nešto ne dogodi što će utjecati na promjenu statusa, na primjer kada predmet zaprimi novi odgovor.

Ipak, status se ne može uvijek prepoznati automatski zato jer je potrebno donijeti odluku o odgovoru koje je tijelo dostavilo za pojedini predmet. Za takve statuse, Alaveteli poziva podnositelja predmeta da označi status predmeta, na primjer kada stigne odgovor, podnositelj može promijeniti status predmeta u `successful` (uspješan), `partially_successful` (djelomično uspješan) ili `not_held` (ne pojeduju informacije - kada odgovorna pravna osoba odgovori da oni ne raspolažu informacijom ili ne mogu pomoći).

Ako je predmet čekao više od tri tjedna da ga izvorni podnositelj predmeta pregleda i ocijeni status i još nije postavljen status, Alaveteli će dopustiti da bilo koji drugi korisnik pregleda predmet i procijeni u kojem je statusu predmet i postavi status.

Kao dio unutarnje obrade zapisa, Alaveteli ne zapisuje samo "opisano stanje" ("described state") predmeta već također bilježi da li se nešto dogodilo od kada je zadnji put ažuriran i kada se nešto izmjeni postavlja predmet u "čeka ocjenu" ("awaiting description") status.

# Zastara predmeta

Kada nema aktivnosti na predmetu nekoliko mjeseci (zadano to je postavljeno na šest mjeseci), Alaveteli će automatski promjeniti u tom predmetu **Allow new responses from** (dozvoli nove odgovore od) postavku u `authority_only` (samo izvorna pravna osoba). Bilo koji dolazni email biti će odbačen ako ne dolazi s email adrese pravne osobe kojoj je poslan predmet.

Ako prođe još mjeseci bez aktivnosti (zadano to je postavljeno na jednu godinu), tom predmetu **Allow new responses from** (dozvoli nove odgovore od) postavka biti će promjenjena u `nobody` (nitko). Svi odgovori bez obzira s koje adrese dolaze biti će odbačeni. Možemo reći da je taj predmet zatvoren i ne očekuju se više odgovori nakon proteka tolikog vremena neaktivnosti.

Po zadanim postavkama, bilo koji odgovor biti će odbijen s povratnom porukom koja objašnjava da je predmet zatvoren jer je star s prijedlogom da pošiljatelj može direktno kontaktirati administratore.

Administratori mogu izmjeniti ovo ponašanje tako da u metapodacima predmeta izmjene **Allow new responses from** (dozvoli nove odgovore od) postavku natrag u normalnu vrijednost u bilo kojem trenutku. Alternativno, možete izmjeniti kako će Alaveteli rukovati odbačene poruke, u postavci predmeta **Handle rejected responses** (rukovanje odbačenim odgovorima); na primjer slanjem odbačenog odgovora u Holding pen.

Pogledaj niže više o mjenjanju stvari u predmetu te kako izmjeniti postavke predmeta.

Administrator sustava (system administrator) može izmjeniti broj mjeseci nakon kojih će predmet biti zabranjeno zaprimanje odgovora kroz postavku `RESTRICT_NEW_RESPONSES_ON_OLD_REQUESTS_AFTER_MONTHS` u konfiguraciji sustava putem Linux terminala.

# Mjenjanje stvari u predmetu

Za mjenjanje bilo kojih postavki predmeta, idite u administracijsko sučelje, kliknite na **Requests** (predmeti), zatim kliknite na naslov predmeta kojeg želite mjenjati. Kliknite na **Edit metadata** tipku.

| Što možeš mijenjati                 | Detalji |
| ----------------------------------- | ------- |
| Naslov                              | Naslov predmeta je prikazan na stranici predmeta, ali isto se koristi u URL-u (URL je tekst naslova s malim slovima, točke su uklonjene i ako je potrebno dodaje se broj za razlikovanje ako postoji više istih naslova - to zovemo "slug").<br>Zapamtite da mjenjanje naslova mjenja i URL, a zato jer se slug mjenja - stari URL više neće raditi i posjetitelji koji će koristiti stari URL dobiti će 404 grešku (nije pronađeno). |
| Tko može vidjeti?                   | Promijenite **Prominence** (vidljivost) postavku na jednu od sljedećih:<br>- `normal`<br>- `backpage`: predmet je vidljiv svima putem URL-a, ali neće biti prikazan na popisu ili na rezultatima pretrage<br>- `requester_only`: predmet je vidljiv samo osobi koja je napisala predmet<br>- `hidden`: predmet se ne prikazuje nikome, vidljiv je samo ulogiranim administratorima |
| Tko može odgovoriti?                | Postavka **Allow new responses from** (dozvoli nove odgovore od) može biti:<br>- `anybody`<br>- `authority_only`: odgovori su dozvoljeni ali samo ako dolaze od iste pravne osobe kojima je poslan predmet tj. od domene s koje je odgovor već ranije bio zaprimljen<br>- `nobody`: ničiji odgocori neće biti prihvaćeni za ovaj predmet<br>Bilo koji odgovor od pošiljatelja koji je odbijen ovom postavkom biti će odbačen (vidi sljedeće).<br>Ova postavka se može promijeniti automatski kada je predmeti zastare. |
| Što se dogodi odbačenim odgovorima? | Postavka **Handle rejected responses** (rukovanje odbačenim odgovorima) određuje što će se dogoditi odgovorima koji nisu dozvoljeni (vidi u prethodi opis):<br>- `bounce`: odgovori su vraćeni natrag pošiljatelju<br>- `holding pen`: odgovori se svrstavaju u holding pen kako bi ih administratori mogli pregledati<br>- `blackhole`: odgovori se uništavaju slanjem u "crnu rupu" |
| U kojem je statusu?                 | Pogledajte stranicu o [statusima predmeta](#TBD1) za vaše prilagođene statuse.<br>Možete umjetno promijeniti status predmeta izričitom promjenom statusa u neki od ponuđenih. Promjenite **Described state** postavku.<br>Možda ćete trebati i izmjeniti **Awaiting description** ako je promjena statusa predmeta utjecala na potrebu ažuriranja predmeta od strane izvornog podnositelja. Na primjer, kada status ovisi o informaciju u odgovoru i želite da podnositelj razvrsta status predmeta, pogledajte *What state is the request in?* iznad. |
| Jesu li komentari dozvoljeni?       | Postavka **Are comments allowed?** vam omogućava da dopustite ili zabranite dodavanje pribilješki za ovaj predmet.<br>Zapamtite da zabrana dodavanja komentara neće sakriti već postojeće komentare u ovom predmetu — ona samo zabranjuje dodavanje novih komentara. |
| Tagovi (ključne riječi za pretragu) | Unesite tagove (oznake, ključne riječi) odvojene razmacima koje se mogu logički povezati uz neki predmet. Tag može biti jednostavna riječ, par ključa i vrijednosti (key-value pair, koristite dvotočku za odjeljivanje, poput `key:value`).<br>Tagovi se mogu koristiti prilikom pretrage. Oni su korisni i korisnicima i administratorima ako su predmeti označeni korisnim tagovima, zato jer će to pomoći prilikom pretrage specifičnih predmeta - posebno ako stranica ima mnogo predmeta u bazi podataka.<br>Iako su malo kompleksnije od tagova na predmetima, kategorije isto koriste tagove: pogledajte [više o tagovima](#TBD2). |

# Ponavljanje slanja predmeta ili slanje na drugog primatelja

Ako ste ispravili email adresu pravne osobe, možete ponoviti slanje postojećeg predmeta istoj pravnoj osobi na novu email adresu. Ili u drugom slučaju, korisnik je možda poslao predmet krivoj pravnoj osobi. U tom slučaju, možete izmjeniti pravnu osobu na koju je naslovljen predmet i tada ponoviti slanje čime će biti poslano na pravilnog primatelja.

Za ponavljanje slanja predmeta odnosno pojedinačne poruke, idite na administracijsko sučelje, kliknite na **Requests**, zatim kliknite na ime predmeta kojeg želite izmjeniti. Idite na naslov **Outgoing messages**. Kliknite na strelicu kraj prve odlazne poruke tj. izvorna poruka u predmetu. Prikazati će se općenite informacije o poruci. Kliknite **Resend**.

Za slanje predmeta nekoj drugoj pravnoj osobi, idite na administracijsko sučelje, kliknite na **Requests**, zatim kliknite na ime predmeta kojeg želite izmjeniti. U **Request metadata** dijelu nalazi se redak koji pokazuje izvornog primatelja predmeta. Kliknite **move…** tipku koja se nalazi kraj naziva pravne osobe. Unesite **url_name** pravne osobe kojoj želite poslati predmet.

> Korisnici, predmeti i pravne osobe svi imaju `url_name` (url nazive). Može se pronaći u metadata dijelu na njihovoj administracijskoj stranici. URL naziv čini zadnji dio URL-a njihove javne stranice. Znači, za predmet kojem je `url_name` "primjer_predmeta" javni URL biti će `/request/primjer_predmeta`.

Sada kliknite na tipku **Move request to authority**. Vidjeti ćete obavijest na vrhu stranice da je predmet premješten. Sada možete ponoviti slanje na novog primatelja kako je gore objašnjeno.

# Skrivanje predmeta

Možete sakriti cijele predmete. Tipično, ovo ćete koristiti kada podnesak nije valjan (na primjer kada ne pripada pod zakonsku definiciju predmeta za vaš portal), ili kada sadrži elemente zabranjene zakonom (na primjer govor mržnje).

Idite u administracijsko sučelje, kliknite na **Requests**, zatim kliknite na naslov predmeta. Možete sakriti na dva načina: 

- Sakrijte predmet i obavijestite podnositelja predmeta
- Sakrijte predmet bez obaviještavanja podnositelja predmeta

Odgovori na sakriveni predmet biti će prigvaćeni uobičajeno, i oni će biti sakriveni kao i cijeli predmet.

## Skrivanje predmeta i obaviještavanje podnositelja

Spustite se do *Actions* dijela na administracijskoj stranici predmeta. Izaberite od ponuđenih mogućnosti kraj **Hide the request and notify the user**:

- *Not a valid FOI request* (predmet nije valjan predmet pod nadležnim zakonom)
- *A vexatious request* (protivan je pravilima korištenja stranice odnosno krši zakonske propise, npr. govor mržnje)

Izborom jedne od ovih mogućnosti prikazati će obrazac za email poruku. Po potrebi izmjenite tekst email poruke koji će biti poslan korisniku, obaviještavajući korisnika što ste učinili i s kojim razlogom. Kada ste gotovi, kliknite **Hide request** tipku.

## Skrivanje predmeta bez obaviještavanja podnositelja

> Osim skrivanja predmeta ovaj postupak možete koristiti ako želite da predmet bude vidljiv samo podnositelju.

Na administracijskoj stranici predmeta u dijelu *Request metadata*, kliknite na **Edit metadata** tipku. Promijenite *Prominence* (vidljivost) vrijednost u jednu od ponuđenih:

- `requester_only` - samo će podnositelj moći vidjeti stranicu predmeta
- `hidden` - nitko neće vidjeti stranicu predmeta, osim administratora.

> Ako želite sakriti predmet, nemojte izabrati `backpage` kao vidljivost. `backpage` postavka skriva predmet sa stranica s listama i pretrage pa je ustvari predmet vidljiv svatkome tko ima URL tog predmeta ali ne zabranjuje pristup tom predmetu. 

Kada ste gotovi, kliknite na **Save changes** tipku na dnu dijela *Edit metadata*. Podnositelju neće biti poslana nikakava obavijest u promjenama koje napravite na predmetu.

# Brisanje predmeta

Predmet možete obrisati u potpunosti. Tipično, ovo činite samo u izvanrednim slučajevima kada drugi postupci ne mogu riješiti problem. Ako obrišete predmet, svi odgovori koji su zaprimljeni za taj predmet biti će isto obrisani.

> Brisanje predmeta ga u potpunosti uništava. Ne postoji povratka nakon ovog postupka. Ako niste sigurni da baš ovo želite učiniti, možda ipak trebate samo sakriti predmet.

Idite na administracijsko sučelje, kliknite na **Requests**, zatim kliknite na ime predmeta kojeg želite izmjeniti. Kliknite na **Edit metadata** tipku. Kliknite na crvenu **Destroy request entirely** tipku na dnu stranice.

Odgovori zaprimljeni za obrisani predmet biti će poslani u holding pen.
