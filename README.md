# ImageSearch - Searchy2

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 1.5.5.

# Angular 4 aplikacija 
- upisom teksta u search bar (na engleskom) pretražuje i vrača set slika i metadata podatke istih<br /><br />

Aplikacija se sastoji od osnovne(app-root) komponente, image-list komponente, i image servisa<br /><br />

Unutar App-root komponente se nalazi sadržaj koji se uvijek prikazuje, ukoliko se bira određena komponenta se rješava putem router outleta no doduše u ovoj aplikaciji nije potreban pošto ima samo 1 komponenta, te neki osnovni podatci o appu (title, logo, ...)<br /><br />

# Komponenta image-list
se sastoji od 3 djela: 1. Search 2. Progress bar 3. List of images<br />
--HTML--<br />
1.Search se sastoji od inputa polja i buttona, input polje je dvosmjerno vezan putem [(ngModel)]  "searchQuery" te klikom na button poziva funkciju searchImages te kao parametar šalje input searchQuery.<br />
--TS--<br />
unutar TS se nalazi konstruktor koji stvaranjem nasljeđuje ImageService, sve potrebne varijable i arrayi, te funkcije<br />
      searchImages dobiva parametar searchQuery te vraća rezultat funkcije getImage (funckija servisa image.service)
   

# Servis Image.service
sadrži varijable API_KEY, API_URL i URL što je api_url + api_key + '&q=' //stoji za query<br />
konstruktor nasljeđuje angularov Http<br />
 --getImage--<br />
je funkcija koja dobiva parametar query što je searchQuery te vraća putem angularovog httpa funkcijom get(url + query +limit koliko slika) koja vraća slike i metadata istih ograničenih brojem i specificiranih searchQueryem<br />
i to vračeno funckijom .map(res=>res.json()) stvara array za rezultat te pretvara u json oblik<br />
te vraća taj json kao rezultat

# Komponenta image-list
 --TS--<br />
subscribeom je napravljen basic handle za success i error, te ukoliko je success, dobiveni data se postavlja u images varijablu.<br />
 --HTML--<br />
putem ngFor-a prolazi kroz slike te ih prezentira putem korištenjem angular material (komponente za angular-layout,button,cards itd) te masonry za dinamičko pozicioniranje<br />
prikazuje se slika (image.webformatURL), user (image.user), tags (image.tags), komentari (image.comments) te broj like-ova (image.likes)



# dodatni komentari:
-slika favicona zbog zaštite copyrighta (iako nema smisla jer traže da se to koristi) se ne prikazuju te sam ih uklonio<br />
-izrada aplikacije je relativno jednostavna zbog ne imanja back-enda nikakvog<br />
-problemi sa verzioniranjem masonrya <br />

# sljedeći projekti:
Jednostavna APP korištenjem MEAN stacka (radio i prije, nikad do deploya)<br />
Napredna -||-<br />

# dodatni dodatni komentari:
firebase (angularfire2) ima problema sa novom verzijom angulara(testirano 5.0.5 ne radi, 5.1.0 ne testirano)<br />
masonry ima problem sa novom verzijom angular compilera (rješenje-starija verzija cli)<br />
  -official statment "krivo korištenje modula odnosno linkanje" ali ostale rade<br />



