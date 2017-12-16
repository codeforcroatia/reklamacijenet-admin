---
layout: post
title:  "Upravljanje predmetima"
date:   2017-09-29
---

Alaveteli olakšava korisnicima u slanju pisanih predmeta - prigovora. Ti kao administrator trebaš znati nekoliko stvari koje možeš raditi s poslanim predmetom. 

Predmet se kreira automatski kada korisnik podnese (i kada je potrebno) potvrdi slanje predmeta. Alaveteli ga tada šalje na email adresu odgovorne pravne osobe i rukuje zaprimljene odgovore po predmetu. Taj se postupak odvija bez bilo kakve intervencije administratora, ali ponekada ćeš trebati izmijeniti neke dijelove predmeta, odnosno izmijeniti način na koji će Alaveteli rukovati njime.

# U kojem je statusu predmet?

Svaki predmet prolazi kroz niz promjena stanja koja pokazuju njegov napredak kroz vrijeme. Uobičajeno će novi predmet biti u `waiting_response` (čeka odgovor) statusu dok se nešto ne dogodi što će utjecati na promjenu statusa, na primjer kada predmet zaprimi novi odgovor.

Ipak, status se ne može uvijek prepoznati automatski zato jer je potrebno donijeti odluku o odgovoru koje je tijelo dostavilo za pojedini predmet. Za takve statuse, Alaveteli poziva podnositelja predmeta da označi status predmeta, na primjer kada stigne odgovor, podnositelj može promijeniti status zahtjeva u `successful` (uspješan), `partially_successful` (djelomično uspješan) ili `not_held` (ne pojeduju informacije - kada odgovorna pravna osoba odgovori da oni ne raspolažu informacijom ili ne mogu pomoći).

Ako je predmet čekao više od tri tjedna da ga izvorni podnositelj zahtjeva pregleda i ocijeni status i još nije postavljen status, Alaveteli će dopustiti da bilo koji drugi korisnik pregleda predmet i procijeni u kojem je statusu predmet i postavi status.

Kao dio unutarnje obrade zapisa, Alaveteli ne zapisuje samo "opisano stanje" (“described state”) predmeta već također bilježi da li se nešto dogodilo od kada je zadnji put ažuriran i kada se nešto izmjeni postavlja predmet u "čeka ocjenu" (“awaiting description”) status.

# Zastara predmeta

Kada nema aktivnosti na predmetu nekoliko mjeseci (zadano to je postavljeno na šest mjeseci), Alaveteli će automatski promjeniti u tom predmetu "Allow new responses from" (dozvoli nove odgovore od) postavku u `authority_only` (samo izvorna pravna osoba). Bilo koji dolazni email biti će odbačen ako ne dolazi s email adrese pravne osobe kojoj je poslan predmet.

Ako prođe još mjeseci bez aktivnosti (zadano to je postavljeno na jednu godinu), tom predmetu "Allow new responses from" (dozvoli nove odgovore od) postavka biti će promjenjena u `nobody` (nitko). Svi odgovori bez obzira s koje adrese dolaze biti će odbačeni. Možemo reći da je taj predmet zatvoren i ne očekuju se više odgovori nakon proteka tolikog vremena neaktivnosti.

Po zadanim postavkama, bilo koji odgovor biti će odbijen s povratnom porukom koja objašnjava da je predmet zatvoren jer je star s prijedlogom da pošiljatelj može direktno kontaktirati administratore.

Administratori mogu izmjeniti ovo ponašanje tako da u metapodacima predmeta izmjene "Allow new responses from" (dozvoli nove odgovore od) postavku natrag u normalnu vrijednost u bilo kojem trenutku. Alternativno, možete izmjeniti kako će Alaveteli rukovati odbačene poruke, u postavci predmeta "Handle rejected responses" (rukovanje odbačenim odgovorima); na primjer slanjem odbačenog odgovora u Holding pen.

Pogledaj niže više o mjenjanju stvari u predmetu te kako izmjeniti postavke predmeta.

Administrator sustava (system administrator) može izmjeniti broj mjeseci nakon kojih će predmet biti zabranjeno zaprimanje odgovora kroz postavku `RESTRICT_NEW_RESPONSES_ON_OLD_REQUESTS_AFTER_MONTHS` u konfiguraciji sustava putem Linux terminala.

# Mjenjanje stvari u predmetu

Za mjenjanje bilo kojih postavki predmeta, idite u administracijsko sučelje, kliknite na "Requests" (predmeti), zatim kliknite na naslov predmeta kojeg želite mjenjati. Kliknite na "Edit metadata" tipku.

| Što možeš mijenjati                 | Detalji |
| ----------------------------------- | ------- |
| Naslov                              | Naslov predmeta je prikazan na stranici predmeta, ali isto se koristi u URL-u (URL je tekst naslova s malim slovima, točke su uklonjene i ako je potrebno dodaje se broj za razlikovanje ako postoji više istih naslova - to zovemo "slug"). 
Zapamtite da mjenjanje naslova mjenja i URL, a zato jer se slug mjenja - stari URL više neće raditi i posjetitelji koji će koristiti stari URL dobiti će 404 grešku (nije pronađeno). |
| Tko može vidjeti?                   | Promijenite **Prominence** (vidljivost) postavku na jednu od sljedećih:
- `normal`
- `backpage`: predmet je vidljiv svima putem URL-a, ali neće biti prikazan na popisu ili na rezultatima pretrage
- `requester_only`: predmet je vidljiv samo osobi koja je napisala predmet
- `hidden`: predmet se ne prikazuje nikome, vidljiv je samo ulogiranim administratorima |
| Tko može odgovoriti?                | Postavka **Allow new responses from** (dozvoli nove odgovore od) može biti:
- `anybody`
- `authority_only`: odgovori su dozvoljeni ali samo ako dolaze od iste pravne osobe kojima je poslan predmet tj. od domene s koje je odgovor već ranije bio zaprimljen
- `nobody`: ničiji odgocori neće biti prihvaćeni za ovaj predmet
Bilo koji odgovor od pošiljatelja koji je odbijen ovom postavkom biti će odbačen (vidi sljedeće). 
Ova postavka se može promijeniti automatski kada je predmeti zastare. |
| Što se dogodi odbačenim odgovorima? | Postavka **Handle rejected responses** (rukovanje odbačenim odgovorima) određuje što će se dogoditi odgovorima koji nisu dozvoljeni (vidi u prethodi opis):
- `bounce`: odgovori su vraćeni natrag pošiljatelju
- `holding pen`: odgovori se svrstavaju u holding pen kako bi ih administratori mogli pregledati
- `blackhole`: odgovori se uništavaju slanjem u "crnu rupu" |
| U kojem je statusu?                 | are neat      |
| Jesu li komentari dozvoljeni?       | are neat      |
| Tagovi (ključne riječi za pretragu) | are neat      |


What state is it in?	See more about request states, which can be customised for your installation.
You can force the state of the request by choosing it explicitly. Change the Described state setting.

You may also need to set Awaiting description if, having changed the state, you want the original requester to update the description. For example, if the state depends on the information within the response, and you want the requester to classify it — see What state is the request in? above.

Are comments allowed?	The Are comments allowed? setting simply allows you to choose to allow or forbid annotations and comments on this request.
Note that this won’t hide any annotations that have already been left on the reques — it only prevents users adding new ones.

Tags (search keywords)	Enter tags, separated by spaces, that are associated with this request. A tag can be either a simple keyword, or a key-value pair (use a colon as the separator, like this: key:value).
Tags are used for searching. Users and administators both benefit if you tag requests with useful keywords, because it helps them find specific requests — especially if your site gets busy and there are very many in the database.

Although it’s a little more complex than tags on requests, categories also use tags: see more about tags for a little more information.

Resending a request or sending it to a different authority#

If you have corrected the email address for an authority, you can resend an existing request to that authority to the new email address. Alternatively, a user may send a request to the wrong authority. In that situation, you can change the authority on the request and then resend it to the correct authority.

To resend a request, go to the admin interface, click on Requests, then click on the name of the request you want to change. Go to the Outgoing messages heading. Click the chevron next to the first outgoing message, which is the initial request. A panel of information about that message will appear. Click on the Resend button.

To send a request to a different authority, go to the admin interface, click on Requests, then click on the name of the request you want to change. In the Request metadata section, there is a line which shows the authority. Click the move… button next to it. Enter the url_name of the authority that you want to send the request to.

Users, requests and authorities all have url_names. This can be found in the metadata section of their admin page. The url_name makes up the last part of the URL for their public page. So, for a request with the url_name “example_request”, the public page URL will be /request/example_request.
Now click the Move request to authority button. You will see a notice at the top of the page telling you that the request has been moved. You can now resend the request as above.

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
