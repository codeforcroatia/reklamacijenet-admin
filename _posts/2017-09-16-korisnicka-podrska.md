---
layout: post
title:  "Korisnička podrška"
date:   2017-09-16
---

Ovdje ćemo objasniti učestale oblike korisničke podrške a namjenjeno je za razvoj i treninge tima za podršku.

# Rješavanje nedostavljenih e-mailova

E-mailovi ne dolaze do pravnih osoba iz više razloga:
* primateljev poslužitelj je označio e-mail spamom i nije ga proslijedio u primateljev inbox
* e-mail je završio u primateljevoj spam mapi radi klijentske postavke za spam
* primatelj je konfigurirao filter za dolazne mailove radi kojih poruka nije dostavljena u inbox
* primateljev poslužitelj ne zna za e-mail adresu na koju šaljemo poruku
* primateljev poslužitelj ne može isporučiti poruku u inbox jer je zapunjen

Prvi razlog je vrlo učestao. Rješenje je poslati standardan template e-mail poruke IT odjelu na poslužiteljskoj strani i zatražiti da whitelistaju e-mail poruke koje dolaze s našeg poslužitelja; i naravno, poslati poruku izvornom primatelju o akciji koju ste poduzeli. Alaveteli admin sučelje ima mogućnost "resend" za ponovno slanje e-mail poruke.

Administrator će tek postati svjestan ovog problema tek kada predmetu istekne rok a da primatelj nije odgovorio. Ponekada će primateljev poslužitelj vratiti natrag izvorni e-mail, te će predmet biti prikazan u administratorskom sučelju kao "needs admin attention" tj. potrebna je pažnja administratora.

# Molba za uklanjanje podataka

## Kazneno djelo

Ovo znači kada nam netko kaže da je podatak prikazan na stranici kazneno djelo. Ovo se može razlikovati od zemlje do zemlje ovisno o vrsti podataka. U Hrvatskoj ovakva vrsta molbe za uklanjanje sadržaja može biti djela protiv časti i ugleda ili govor mržnje.

### Akcija

* e-mailom dostavi obavijest na glavnu mailing listu za podršku, tako da postoji službeni zapis
* postupi prema standardnom zakonskom propisu, npr. možda ćeš trebati privremeno sakriti poruku ili predmet dok debatirate o svojstvu poruke, čak ako ti misliš da treba ostati vidljiv, prokonzultiraj se s cijelim timom, ili ćeš možda uspijeti cenzurirati sporne dijelove bez potrebe skrivanja cijele poruke
* dokumentiraj cijelu konverzaciju i poduzete akcije
* traži dodatne pravne savjete ako je potrebno, npr. možda ćeš dobiti procjenu rizika koji kaže da možeš ponovno objaviti poruku, ili pokazati dijelove uz cenzuru ostatka poruke

## Copyright

Pošiljatelj poruke će ponekada tvrditi da u njihovim odgovorima ima materijala koji je zaštićen copyrightom. Također mogu reći da poruka sadrži "komercijalno osjetljive podatke."

### Akcija

* u slučaju kada postoji se radi o kaznenom djelu, pogledaj gore
* za sve ostalo, pokušaj tretirati kao zagovaračko pravo na temelju toga jer predmet može kreirati bilo tko i svi njihovi podaci su javni, a pravna osoba može pokazati kako učinkovito rješava predmete

**Primjer e-maila pravnoj osobi**

```

```

## Osobni podaci

Ovo uključuje sve od slučajno otkrivenih osobnih podataka poput informacija koje mogu identificirati neku fizičku osobu do imena korisnika stranice koji kasnije dobije "Google remorse."

### Akcija

* procijeni predmet, uz referencu na Zakon o zaštiti osobnih podataka; nemoj automatski pretpostaviti da nešto treba sakriti, procijeni štetu načinjenu osobi koja je predmet osobnih podataka; imaj na umu da osjetljivi osobni podaci zahtijevaju brzu akciju i uklanjanje
* portal smatra da [neke informacije u javnom interesu][take-down] ne treba skrivati
* ako korisnik želi da uklonimo njegovo ime kompletno sa stranice, prvo pokušaj: saznati zašto želi ukloniti svoje ime, objasni da je portal trajna arhiva predmeta, objasni tehničke poteškoće (ako je potrebno)
* ako korisnik koji želi da uklonimo njegovo ime kompletno sa stranice inzistira na uklanjanju: anonimiziraj ime korisnika tako da ostaviš inicijale u korisničkom računu kako ne bi bilo zbunjujuće u postojećim predmetima ove osobe, a gdje je potrebno zaštiti osobne podatke napravi cenzuru imena i u sadržaju predmeta
* ako je teško cenzurirati osobne podatke, npr. uklanjanje osobnih podataka iz slike ili PDF-a; traži ih da ponovno pošalju odgovor s cenzuriranim osobnim podacima (ovo je ujedno dobar trening da u budućnosti nauče da moraju cenzurirati osobne podatke)
* kada se tekst cenzurira, dobro je ostaviti komentar ispod predmeta s razlogom cenzure

# Pogrešno dostavljene poruke

To su e-mailovi koji pristignu na adresu tima za podršku, ali ne bi smjeli. Dvije su vrste:

* korisnici koji kontaktiraju portal misleći da pričaju s pravnim osobama
* korisnici koji pišu na adresu tima za podršku korisnicima umjesto puem online obrasca; obično jer su napravili odgovor na email koji su dobili od sustava umjesto da su odgovor pisali na linku iz e-mail poruke

### Akcija

Odgovori korisniku s detaljnim uputama kamo treba ići da napiše svoj odgovor pravilnom primatelju.

**Primjer odgovora korisniku**

```
Dragi _______, 
odgovor ste uputili timu volontera koji održavaju portal {{ site.portal.name }}. 
Vaš odgovor možete poslati pravnoj osobi klikom na link iz emaila, te zatim na link "Napisati odgovor" koji se nalazi ispod predmeta.

Lijep pozdrav,
[tvoje ime] - volonter na {{ site.portal.name }}
```

# Korisnik treba savjet

Dva najučestalija primjera su:

* korisnik nije siguran kome poslati predmet
* želi znati najbolji način da sastavi poruku predmeta

**Primjer odgovora korisniku**

```
Dragi _______, 
savjetujem vam da pošaljete predmet "XZY" pravnoj osobi jer je "Caffe XYZ" brand dio te pravne osobe.

Lijep pozdrav,
[tvoje ime] - volonter na {{ site.portal.name }}
```

# Korisnik treba pomoć

Korisnik može tražiti općenitu pomoć iz više razloga:

* povukao je prigovor, ali je ponovno otvoren nakon odgovora pravne osobe
* predlaže ispravke u imenu pravne osobe ili detaljima javne osobe
* odgovor je automatski dodan ispod pogrešnog predmeta

# Korisnici koji krše uvjete korištenja

Neki korisnici kontinuirano zlorabe stranicu. Alaveteli portal treba imati politiku zabrane korištenja portala, npr. upozorenje prvi puta te informiranje o politici moderiranja itd.

# Greške importa e-mailova

Ovo se obično dogodi jako rijetko. Izvor problema je blokiranje baze podataka kada su dva e-maila zaprimljena za isti predmet u isto vrijeme, a ponekada je problem u IO timeoutu ako je server zauzet. Kada se dogodi e-mail import problem, rukovatelj e-mailom (Exim) će poslati izlazni kod 75 i pokušati će ponovno dostaviti e-mail. E-mail će biti dostavljen na adresu tima za podršku, indicirajući da se dogodio problem, sa greškom i dolaznim e-mailom u prilogu poruke. Obično Exim pokuša ponoviti dostavu poruke Alaveteli aplikaciji. U rijetkim slučajevima to en učini, a kada se to dogodi, to možeš ti učiniti tako da uvezeš raw poruku ručno bez prvog "From" reda, i pipeaš sadržaj u skriptu rukovatelja e-pošte: `cat missing_mail.txt | script/mailin`.

[take-down]:    #tbd
