# Metode i tehnike testiranja programske podrške - Test opterećenja
Ovaj repozitorij sadrži potrebne projektne datoteke za analizu testova opterećenja 5 najkorištenijih web-stranica za verzioniranje koda:
- Github
- Gitlab
- Bitbucket
- SourceForge
- Google Cloud

Testovi su obavljeni koristeći alat Jmeter.

## Alati za verzioniranje koda
### Github
Github je alat za verzioniranje koda koji je nastao 2008. godine od strane tvrtke Logical Awesome LLC. Uz uobičajne alate karakteristične za verzioniranje koda, omogućuje kontrolu nad pristupu repozitorijima te dodatne alate za suradnju nad istim repozitorijima poput praćenje pogrešaka, zahtjevi za dodatnim značajkama, wiki-stranice za repozitorije i ostali. 2018. godine, Microsoft je kupio Github te omogučio korisnicima koji besplatno koriste Github da stvaraju privatne repozitorije.
### Gitlab
Gitlab kao alat za verzioniranje je nastao 2014. godine primarno kao alat za pomoć pri remote radu. Uz značajne alate za verzioniranje koda, sadrži dodatne alate koji olakšavaju rad od kuće te pruža jednostavno sučelje za korištenje što omogućuje početnicima lakše snalaženje koristeći Gitlab te lakši početak. Repozitoriji spremljeni na Gitlab ne mogu biti veći od 10 gigabajta.
### Bitbucket
Bitbucket je alat za verzioniranje tvrtke Atlassian koji je nastao 2008. godine. Uz glavne značajke alata za verzioniranje, sadrži bolju integraciju s ostalim proizvodima Atlassiana. Među prvima je omogućavao privatne repozitorije besplatnim korisnicima.
### SourceForge
SourceForge je besplatni web alat za verzioniranje koda koji je potpuno besplatan za sve korisnike. Uz verzioniranje koda, omogućava praćenje pogrešaka, mirroranje preuzimanja, wiki-stranicu za dokumentaciju, forume za korisnike te sučelje za recenziranje projekata. Od svih alata za verzioniranje, najpoznatiji je u zajednici programera koji prave modifikacije za video igre.
### Google Cloud
Platforma Google Cloud-a nije striktno namjenjena za verzioniranje koda. Uz to, služi kao baza podataka, analitički alat te alat za strojno učenje. Logistički gledano, sve usluge koje nudi Google usko su integrirane pod Google Cloud.

## Testovi opterećenja
Testovi opterećenja su testovi u kojem se programska podrška namjerno gura do ekstremnih uvijeta na način da se optereti podacima odnosno zahtjevima. Pri takvom testiranju vrši se automatsko testiranje za koje je potreban nekakav alat koji može kreirati virtualne korisnike te podržava kreiranje skripti za svakog korisnika (popis koraka koji se automatski izvrašavju pri slanju zahtjeva, npr. popunjavanje POST zahtjeva HTTPa nekim podacima). Iako su rijetki slučajevi da se programska podrška nalazi u krajnjem slučaju preopterećenosti pri normalnim uvijetima, do takvih uvijeta se dolazi i malicioznim namjerama korisnika koji npr. mogu izvršiti DDOS napad na neki server. U tom slučaju naša programska podrška bi trebala implementirati odbijanje previše zahtjeva jednog klijenta odjednom.
<br />
<br />
<p align="center">
  <img width="460" src="https://jmeter.apache.org/images/logo.svg">
</p>
<br />
<br />
Testovi opterećenja za ovaj rad su napravljeni koristeći Apacheov JMeter program napravljen u Java programskom jeziku koji daje jednostavno grafičko korisničko sučelje da kreiranje testova opterećenja.
<br />
<br />
<p align="center">
  <img src="https://github.com/bencevicbruno/MTTPP_Test_opterecenja/blob/main/README/jmeter_gui.png"><br />
  <p>Izgled korisničkog sučelja JMeter programa.</p>
</p>
<br />
<br />
## Podešavanje testova<br />
Testovi su podešeni na jednostavan način - svaki zahtjev koji se šalje zapravo je običan GET zahtjev HTTP protokola koji se šalje na index stranicu svakog od alata za verzioniranje koda. Nakon toga je podešena grupa niti koja pravi 500 niti (korisnika) s ramp-up periodom od 10 sekundi. U svakom testu se koristi isti korisnik te se svi testovi samo jednom ponavljaju. Rezultati koji se spremaju su detalji svakog zahtjeva (poput veličina u bitovima, poslani bitovi, broj pogrešaka ako su se dogodile) te detalji odziva zahtjeva (povratni kod i povratna poruka, npr. 200 OK za svaki uspiješan odziv na zahtjev).<br />
<br />
Uz detalje zahtjeva i odziva, sprema se vrijeme potrebno za dobivanje odziva, prosječno vrijeme odziva, throughput (propusnost) te devijacija vremena odziva koje je za svaki od alata u nastavku analiziran.