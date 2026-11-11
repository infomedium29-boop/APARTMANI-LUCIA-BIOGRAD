# APARTMANI LUCIA — NOVI DEMO WEB / Medium29

**Status:** demonstracijski projekt za slanje vlasniku na pregled, **nije produkcijska verzija**.
Statički HTML/CSS/JS, bez frameworka, spremno za GitHub + Cloudflare Pages.

## 1. Brza objava na GitHub / Cloudflare Pages

1. Raspakirajte ZIP, otvorite mapu `LUCIA_BIOGRAD_NEW` i prenesite **sadržaj mape** u korijen novog GitHub repozitorija (datoteka `index.html` mora biti u korijenu repozitorija).
2. Cloudflare → Workers & Pages → Create application → Pages → Connect to Git.
3. Odaberite GitHub repozitorij. Framework preset: **None**. Build command: **prazno / none**. Build output directory: **`.`** (točka: korijen repozitorija).
4. Deploy. Dobit ćete adresu tipa `naziv.pages.dev`. Projekt već ima `robots.txt` i `X-Robots-Tag: noindex` za pregled bez indeksiranja na Googleu.
5. Testirajte početnu, unutarnje stranice, HR/EN/DE, navigaciju, WhatsApp i obrasce.

**Ne unosite produkcijske podatke ili dozvole prije potvrde vlasnika.**

## 2. Najvažniji uvjeti prije nego web postane aktivan

- **Obrazac je demonstracijski dok u `js/main.js` ne dodate pravi `WEB3FORMS_ACCESS_KEY`.** Trenutačno **ne šalje** e-mail upite; ne prikazuje lažni uspjeh. WhatsApp, e-mail poveznica i `tel:` su dostupni odmah. Po unosu ključa obvezno napravite stvarno testno slanje.
- **Originalne fotografije vlasnika nisu dostavljene.** Privremeno se za privatni demo učitavaju stvarne fotografije povezane s objektom, **s URL-ova postojećih javnih oglasa**. Te fotografije **nisu uključene u ZIP kao lokalni AVIF** i mogu biti blokirane hotlink zaštitom. Dizajnirani lokalni AVIF placeholderi prikazuju se ako URL nije dostupan. Za javnu objavu vlasnik/nositelj autorskih prava treba dostaviti fotografije i odobriti njihovo korištenje.
- Krajolici u `assets/img/seascape-illustration.avif` i `promenade-illustration.avif` su **ilustrativni mediteranski vizuali**, nisu dokumentarne fotografije točne lokacije/objekta i označeni su kao demo.
- **Cijene i stanje zauzetosti nisu potvrđeni**, pa se na webu ne izmišljaju. Kalendar se može koristiti za slanje *upita*, ali ne predstavlja sustav automatskih rezervacija. Zauzeti dani se mogu ručno dodati u JSON.
- **Brend:** u ovom demu korišten je radni naziv *Apartmani Lucia Biograd*. Oglasi koriste i Lucija / Vila Lucia; vlasnik mora potvrditi službeni naziv.
- **Fontovi:** CSS je pripremljen za Fraunces + Inter, ali zbog prava distribucije u ZIP-u nema datoteka fontova; u pregledniku se koriste serif/sans fallbacki. Nakon dobivanja pravilno licenciranih WOFF2 datoteka mogu se dodati lokalno.
- **SEO:** canonical/hreflang i sitemap imaju namjerni placeholder `https://example.invalid/`. Demo je `noindex`. Kada potvrdimo konačnu domenu, treba zamijeniti placeholder, ukloniti `noindex` samo za produkciju i obnoviti `robots.txt` / `_headers`.
- Pravila kuće, privatnost i kolačići su **nacrti**, nisu pravni savjet ni pravni tekstovi spremni za javnu upotrebu.

## 3. Što je izrađeno

- 39 stranica: 13 po jeziku (HR, EN, DE) — naslovnica, pregled apartmana, A-1/A-2/A-3/A-4, cijene/dostupnost, galerija, Biograd/okolica, kontakt, pravila kuće, privatnost i kolačići. Dodatno globalni `404.html`.
- Jedna `css/style.css` s paletom A — Jadran i responzivnim komponentama.
- Jedan `js/main.js` s animacijama, mobilnim izbornikom, WhatsApp prefillom, pristupačnim lightboxom, validacijom upita, kalendarom i podrškom za lokalne JSON podatke.
- Lokalne AVIF ilustracije i AVIF neutralni placeholdere. Autentični kadrovi iz oglasa učitavaju se privremeno s vanjskih izvora **samo radi privatnog pregleda**.
- Podaci iz oglasa: adresa Marka Marulića 3a, broj +385 91 240 4046, `apartmenthouse.lucia@gmail.com`, četiri jedinice / 2+2, plaža Dražica približno 5 min hoda. Detalji se potvrđuju s vlasnikom.
- Cloudflare sigurnosna zaglavlja i noindex za demo, privremeni sitemap, favicon, meta opisi, hreflang i strukturirani podaci bez izmišljenih ocjena ili cijena.

## 4. Unos cijena i zauzetih datuma

**`data/prices.json`** — u sezonskim zapisima popunite `start`, `end` (YYYY-MM-DD), `nightlyEUR` (broj) i `minNights` (broj) kada vlasnik potvrdi. JavaScript tek tada prikazuje konkretnu cijenu; prazna polja ostaju „Na upit”. Ako se cijene razlikuju po apartmanu, treba proširiti strukturu i tablicu.

**`data/availability.json`** — pod `units.A-1.unavailable`, `units.A-2.unavailable` itd. dodajte blokirane datume, npr. `["2027-07-15", "2027-07-16"]`. Kalendar ih označava kao zauzete kada je odabrana ta jedinica. Svi ostali dani **ostaju nepotvrđeni**, ne prikazuju se kao dokazano slobodni.

## 5. Originalne fotografije i kvaliteta

Ovaj ZIP ne sadrži fotografije preuzete s tuđih portala jer vlasnik još nije dostavio originale i dozvolu. Popis privremenih URL-ova, izvora i planiranih kadrova je u `PHOTO-SOURCES-AND-APPROVAL.csv`. Trebamo tražiti izvorne fotografije iz kamere / telefona, bez dodatne kompresije. Za produkciju iz njih napraviti kvalitetne AVIF + WebP datoteke (npr. hero 1920/1280 px, kartice 960/640 px) i postaviti lokalne `<picture>` izvore s `srcset`.

Za pojedine A-1, A-2, A-3, A-4 nije potvrđeno koja fotografija prikazuje koji apartman, zbog toga njihove detaljne stranice sada namjerno imaju označen vizualni placeholder. Kartice prikazuju fotografije povezane s objektom uz napomenu da raspored potvrđuje vlasnik.

## 6. Kratka kontrolna lista prije produkcije

1. Službeni naziv Lucia/Lucija i sve četiri jedinice, kapacitet i kvadrature.
2. Originalne fotografije, dozvola objave i dodjela fotografija točnim jedinicama.
3. Aktuelni cjenik po apartmanu/sezoni i minimalan boravak.
4. Ručno uređivanje dostupnosti ili integracija channel managera.
5. Potvrda broja, WhatsApp/Viber aktivacije, e-maila, vremena odgovora.
6. Pravi Web3Forms ključ, anti-spam, test slanja u inbox, privacy tekst.
7. Službeni OIB, registracija objekta, kategorizacija, kućni red, uvjeti otkazivanja i podaci za prigovor.
8. Konačna domena, canonical/hreflang/sitemap, robots.txt, uklanjanje noindexa.
9. Odobrenje recenzija i provjera trenutne Booking ocjene.
10. Analytics samo uz odgovarajuće pravne postavke; provjera mobilne brzine na javnoj domeni.

## 7. Tehnička napomena

Kod je pripremljen prema specifičnom briefu, bez frameworka i bez nepotrebnog JS-a. Ciljevi Lighthouse 95+, LCP ispod 2 s i WCAG 2.2 AA **nisu certificirani**; završni audit izvodimo na stvarnoj produkcijskoj domeni nakon što unesemo originalne slike i podesimo hosting.
