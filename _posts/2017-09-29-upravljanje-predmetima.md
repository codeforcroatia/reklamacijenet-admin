---
layout: post
title:  "Upravljanje predmetima"
date:   2017-09-29
---

Alaveteli olakšava korisnicima u slanju pisanih predmeta - prigovora. Vi kao administrator trebate znati nekoliko stvari koje možete raditi s poslanim predmetom. 

Predmet se kreira automatski kada korisnik podnese (i kada je potrebno) potvrdi slanje predmeta. Alaveteli ga tada šalje na email adresu odgovorne pravne osobe i rukuje zaprimljene odgovore po predmetu. Taj se postupak odvija bez bilo kakve intervencije administratora, ali ponekada ćete trebati izmijeniti neke dijelove predmeta, odnosno izmijeniti način na koji će Alaveteli rukovati njime.

# U kojem je statusu predmet?

Svaki predmet prolazi kroz niz promjena stanja koja pokazuju njegov napredak kroz vrijeme. Uobičajeno će novi predmet biti u `waiting_response` (čeka odgovor) statusu dok se nešto ne dogodi što će utjecati na promjenu statusa, na primjer kada predmet zaprimi novi odgovor.

Ipak, status se ne može uvijek prepoznati automatski zato jer je potrebno donijeti odluku o odgovoru koje je tijelo dostavilo za pojedini predmet. Za takve statuse, Alaveteli poziva podnositelja predmeta da označi status predmeta, na primjer kada stigne odgovor, podnositelj može promijeniti status zahtjeva u `successful` (uspješan), `partially_successful` (djelomično uspješan) ili `not_held` (ne pojeduju informacije - kada odgovorna pravna osoba odgovori da oni ne raspolažu informacijom ili ne mogu pomoći).

Ako je predmet čekao više od tri tjedna da ga izvorni podnositelj zahtjeva pregleda i ocijeni status i još nije postavljen status, Alaveteli će dopustiti da bilo koji drugi korisnik pregleda predmet i procijeni u kojem je statusu predmet i postavi status.

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
| U kojem je statusu?                 | Pogledajte stranicu o [statusima predmeta](#TBD1) za vaše prilagođene statuse.<br>Možete umjetno promijeniti status predmeta izričitom promjenom statusa u neki od ponuđenih. Promjenite **Described state** postavku.<br>Možda ćete trebati i izmjeniti **Awaiting description** ako je promjena statusa predmeta utjecala na potrebu ažuriranja zahtjeva od strane izvornog podnositelja. Na primjer, kada status ovisi o informaciju u odgovoru i želite da podnositelj razvrsta status predmeta, pogledajte *What state is the request in?* iznad. |
| Jesu li komentari dozvoljeni?       | Postavka **Are comments allowed?** vam omogućava da dopustite ili zabranite dodavanje pribilješki za ovaj predmet.<br>Zapamtite da zabrana dodavanja komentara neće sakriti već postojeće komentare u ovom predmetu — ona samo zabranjuje dodavanje novih komentara. |
| Tagovi (ključne riječi za pretragu) | Unesite tagove (oznake, ključne riječi) odvojene razmacima koje se mogu logički povezati uz neki predmet. Tag može biti jednostavna riječ, par ključa i vrijednosti (key-value pair, koristite dvotočku za odjeljivanje, poput `key:value`).<br>Tagovi se mogu koristiti prilikom pretrage. Oni su korisni i korisnicima i administratorima ako su predmeti označeni korisnim tagovima, zato jer će to pomoći prilikom pretrage specifičnih predmeta - posebno ako stranica ima mnogo predmeta u bazi podataka.<br>Iako su malo kompleksnije od tagova na predmetima, kategorije isto koriste tagove: pogledajte [više o tagovima](#TBD2). |

# Ponavljanje slanja predmeta ili slanje na drugog primatelja

Ako ste ispravili email adresu pravne osobe, možete ponoviti slanje postojećeg predmeta istoj pravnoj osobi na novu email adresu. Ili u drugom slučaju, korisnik je možda poslao predmet krivoj pravnoj osobi. U tom slučaju, možete izmjeniti pravnu osobu na koju je naslovljen predmet i tada ponoviti slanje čime će biti poslano na pravilnog primatelja.

Za ponavljanje slanja predmeta odnosno pojedinačne poruke, idite na administracijsko sučelje, kliknite na **Requests**, tada kliknite na ime zahtjeva kojeg želite izmjeniti. Idite na naslov **Outgoing messages**. Kliknite na strelicu kraj prve odlazne poruke tj. izvorna poruka u predmetu. Prikazati će se općenite informacije o poruci. Kliknite **Resend**.

Za slanje predmeta nekoj drugoj pravnoj osobi, idite na administracijsko sučelje, kliknite na **Requests**, tada kliknite na ime zahtjeva kojeg želite izmjeniti. U **Request metadata** dijelu nalazi se redak koji pokazuje izvornog primatelja predmeta. Kliknite **move…** tipku koja se nalazi kraj naziva pravne osobe. Unesite **url_name** pravne osobe kojoj želite poslati predmet.

> Korisnici, predmeti i pravne osobe svi imaju `url_name` (url nazive). Može se pronaći u metadata dijelu na njihovoj administracijskoj stranici. URL naziv čini zadnji dio URL-a njihove javne stranice. Znači, za predmet kojem je `url_name` "primjer_predmeta" javni URL biti će `/request/primjer_predmeta`.

Sada kliknite na tipku **Move request to authority**. Vidjeti ćete obavijest na vrhu stranice da je predmet premješten. Sada možete ponoviti slanje na novog primatelja kako je gore objašnjeno.

# Skrivanje predmeta

Hiding a request#

You can hide an entire request. Typically you do this if it’s not a valid Freedom of Information request (for example, a request for personal information), or if it is vexatious.

Go to the admin interface, click on Requests, then click on the title of the request you want. You can hide it in one of two ways:

Hide the request and notify the requester
Hide the request without notifying the requester
Responses to a hidden request will be accepted in the normal way, but because they are added to the request’s page, they too will be hidden.

Hide the request and notify the requester#
Scroll down to the Actions section of the request’s admin page. Choose one of the options next to Hide the request and notify the user:

Not a valid FOI request
A vexatious request
Choosing one of these will reveal an email form. Customise the text of the email that will be sent to the user, letting them know what you’ve done. When you’re ready, click the Hide request button.

Hide the request without notifying the requester#
As well as hiding the request from everyone, you can also use this method if you want to make the request only visible to the requester.
In the Request metadata section of the request’s admin page, click the Edit metadata button. Change the Prominence value to one of these:

requester_only: only the requester can view the request
hidden: nobody can see the request, except administrators.
If you want to hide the request, do not chooose backpage as the prominence. The backpage option stops the request appearing in lists and searches so that it is effectively only visible to anyone who has its URL — but it does not hide the request.
When you’re ready, click the Save changes button at the bottom of the Edit metadata section. No email will be sent to the requester to notify them of what you’ve done.

Deleting a request#

You can delete a request entirely. Typically, you only need to do this if someone has posted private information. If you delete a request, any responses that it has already received will be destroyed as well.

Deleting a request destroys it. There is no “undo” operation. If you're not sure you want to do this, perhaps you should hide the request instead.
Go to the admin interface, click on Requests, then click on the title of the request you want to delete. Click the Edit metadata button. Click on the red Destroy request entirely button at the bottom of the page.

Responses to a deleted request will be sent to the holding pen.
