# Trygg Tallrik — instruktioner för appens olika delar

Den här filen beskriver vad varje skärm i appen gör och hur man använder den. Tänkt som en snabbreferens för den som ska testa, demonstrera eller vidareutveckla appen.

---

## 1. Välkomstskärmen

![Skärmbild: Välkomstskärmen](docs/screenshots/01-valkomstskarm.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/01-valkomstskarm.png`)*

Första skärmen den som öppnar appen utan inloggning ser. Kort presentation av appen och tre funktioner (sök restauranger, se allergenhantering, läsa gästrecensioner).

Två knappar:
- **Skapa konto** → till registreringen
- **Logga in** → till inloggningen

## 2. Skapa konto

![Skärmbild: Skapa konto](docs/screenshots/02-skapa-konto.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/02-skapa-konto.png`)*

Formulär med tre fält:
- **Ditt namn** — visningsnamnet som syns i appen (t.ex. i hälsningen på hemskärmen och som initial i avataren)
- **E-postadress**
- **Lösenord** — minst 8 tecken. En styrkemätare visar Svag / Medel / Stark medan man skriver.

Vid registrering skapas kontot i Supabase och en bekräftelse visas ("Konto skapat!"). Man skickas sedan till inloggningen — kontot är alltså inte automatiskt inloggat efter registrering.

## 3. Logga in

![Skärmbild: Logga in](docs/screenshots/03-logga-in.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/03-logga-in.png`)*

E-post och lösenord. Vid fel visas ett felmeddelande från Supabase (t.ex. fel lösenord eller obekräftad e-post). Vid lyckad inloggning går man till hemskärmen.

## 4. Hemskärmen

![Skärmbild: Hemskärmen](docs/screenshots/04-hemskarm.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/04-hemskarm.png`)*

Startsidan efter inloggning. Innehåller:
- Hälsning med användarens namn
- En rad med "Säker från:"-taggar som visar de allergener användaren har valt i sin profil (visas bara om man har valt några)
- Fyra rutor att navigera från:
  - **Sök restaurang** → sökskärmen
  - **Lämna recension** → recensionsskärmen
  - **Mina recensioner** → historik över egna recensioner
  - **Mina allergier** → allergiprofilen

Överst i alla huvudskärmar finns en avatar (användarens initial) uppe till höger — ett tryck på den går direkt till kontoinställningarna.

## 5. Sök restaurang

![Skärmbild: Sök restaurang (karta och lista)](docs/screenshots/05-sok-restaurang.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/05-sok-restaurang.png`)*

Sökning sker mot Google Places, begränsat till en radie på 1,5 km från användarens plats (kräver att platsbehörighet ges).

- Skriv ett sökord (restaurangnamn, kök eller maträtt) och tryck **Sök**.
- Växla mellan **Karta**- och **Lista**-vy med knapparna högst upp.
- I kartvyn visas restauranger som markörer; tryck på en markör och sedan på texten i bubblan för att öppna restaurangsidan.
- I listvyn visas namn, Googles betyg och appens eget **allergibetyg** i en tabell. Tryck på en rad för att öppna restaurangsidan.

Allergibetyget som visas i listan är **personligt**: det räknas bara ut från recensioner skrivna av andra användare som delar *alla* ens egna allergener (se avsnitt 10 nedan). Har man inga allergener valda i sin profil visas i stället snittet av alla recensioner. Träffar med ett allergibetyg sorteras överst.

## 6. Restaurangsidan (detaljvy)

![Skärmbild: Restaurangsidan](docs/screenshots/06-restaurangsida.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/06-restaurangsida.png`)*

Öppnas från sök- eller kartresultat. Visar:
- Namn och adress
- Tre badges: Googles betyg, Trygg Tallriks totala snitt (alla recensioner, oviktat), och antal recensioner
- Knapp **Lämna recension** som går vidare till recensionsformuläret med restaurangen redan ifylld
- **Betyg per allergen** — ett snitt för varje allergen som förekommer i restaurangens recensioner, oavsett vem som skrivit dem. Ens egna allergener är gulmarkerade/grönmarkerade så de syns extra tydligt.
- En lista med samtliga recensioner: betyg, datum, allergentaggar och eventuell kommentar.

## 7. Lämna recension

![Skärmbild: Lämna recension](docs/screenshots/07-lamna-recension.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/07-lamna-recension.png`)*

Nås antingen via hemskärmens ruta eller "Lämna recension" på en restaurangsida.

1. **Sök restaurang** — skriv minst två tecken för att få förslag från Google Places, tryck på ett förslag för att välja restaurangen. Väljer man via restaurangsidan är detta redan ifyllt.
2. **Betygsläge** — två lägen att välja mellan:
   - **Enkel**: ett samlat betyg 1–5 stjärnor för hela besöket.
   - **Avancerad**: separat betyg 1–5 för var och en av de allergener man själv har i sin profil (kräver att man lagt in allergener under Profil, annars visas en text om det). Slutbetyget som sparas är genomsnittet av de allergenbetyg man satt.
3. **Kommentar** (valfritt) — fritext.
4. **Lägg till recension** sparar recensionen. Den taggas automatiskt med de allergener man själv har i sin profil — det är dessa taggar som används i allergibetygen på sök- och restaurangsidorna.

## 8. Mina recensioner

![Skärmbild: Mina recensioner](docs/screenshots/08-mina-recensioner.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/08-mina-recensioner.png`)*

Lista över alla recensioner den inloggade användaren själv har skrivit, nyast först: restaurangnamn, adress, betyg, ev. kommentar och datum. Är listan tom uppmanas man att lägga till sin första recension via startsidan.

## 9. Mina allergier (profil)

![Skärmbild: Mina allergier](docs/screenshots/09-mina-allergier.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/09-mina-allergier.png`)*

Här väljer man vilka allergener/intoleranser som gäller en själv. Varje allergen visas som en tryckbar pill med en kort förklarande text bredvid. Valda allergener markeras. Antal valda visas ("X av Y valda"). Tryck **Spara allergier** för att spara.

Detta val styr:
- vilka allergener ens egna recensioner taggas med (se avsnitt 7)
- vilket allergibetyg man ser i sökresultaten (se avsnitt 10)
- vilka rader som markeras som "mina" på restaurangsidan

## 10. Kontoinställningar

![Skärmbild: Kontoinställningar](docs/screenshots/10-kontoinstallningar.png)
*(placeholder — lägg till skärmbild på `docs/screenshots/10-kontoinstallningar.png`)*

Nås via avataren uppe till höger på valfri huvudskärm.

- **Användarnamn** — byt visningsnamn.
- **E-postadress** — byte kräver bekräftelse via mejl innan det aktiveras.
- **Support & feedback** — länk till tryggtallrik.se.
- **Logga ut**.
- **Radera konto** — kräver tre steg: (1) tryck "Radera mitt konto" för att öppna panelen, (2) bocka i att man förstår att det inte går att ångra, (3) tryck "Radera mitt konto permanent" och bekräfta i den native dialogrutan som visas. Kontot och all personlig data raderas permanent; tidigare recensioner finns kvar men blir anonyma (kopplingen till profilen tas bort).

## 11. Hur allergibetyget räknas ut

![Illustration: Hur allergibetyget räknas ut](docs/screenshots/11-allergibetyg-forklaring.png)
*(placeholder — lägg till en illustration/exempel på `docs/screenshots/11-allergibetyg-forklaring.png`)*

Två olika beräkningar används i appen:

**I sökresultaten (personligt betyg):**
Bara recensioner från andra användare vars allergiprofil täcker *alla* ens egna allergener räknas med. Exempel: har man valt gluten och laktos räknas bara recensioner från personer som har minst gluten *och* laktos i sin profil. Har man inga allergener valda visas i stället snittet av alla recensioner för restaurangen.

**På restaurangsidan (per-allergen-snitt):**
Här visas i stället ett separat snitt för *varje* allergen som förekommer bland restaurangens recensioner, oavsett vem som skrivit dem — så man kan se hur restaurangen bedöms specifikt för t.ex. nötallergi respektive laktosintolerans.

---

*Se README.md för teknisk projektstruktur, installation och databasschema.*
