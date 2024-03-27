# Player-injuries

Ideea principala a acestui studiu a pornit de la un subiect comun, fotbalul, si am decis sa analizam daca numarul accidentarilor din Premier League, pentru sezonul 2020-2021, ar fi avut o anumita influenta asupra echipelor concurente si, implicit, a pozitionarii lor finale in clasament.

Fisierul csv principal a fost constituit din datele, preluate de pe anumite site-uri ce inregistreaza astfel de statistici si organizat pe coloane, in acest fel:

- `TeamName` = numele echipelor din Premier League
- `Abbreviation` = abrevierea numelor acestor echipe
- `PlayerNumbers` = numărul jucătorilor din lot
- `InjuredPlayers` = numărul jucătorilor accidentați din lot
- `Ankle` = numărul accidentărilor din zona gleznelor
- `Back` = numărul accidentărilor din zona spatelui
- `Calf` = numărul accidentărilor din zona gambelor
- `COVID19` = numărul jucătorilor infectați cu acest virus
- `Foot` = numărul accidentărilor din zona picioarelor (tot ce ține de partea lor inferioară)
- `Groin` = numărul accidentărilor din zona inghinală
- `Hamstring` = numărul accidentărilor suferite asupra tendonului, aflat între șold și genunchi
- `Head` = numărul accidentărilor din zona craniană
- `Knee` = numărul accidentărilor din zona genunchilor
- `Knock` = numărul accidentărilor suferite în urma unor simple lovituri
- `Muscles` = numărul accidentărilor care afectează toți mușchii din corp
- `Shoulder` = numărul accidentărilor din zona umerilor
- `Thigh` = numărul accidentărilor din zona coapselor
- `OthCauses` = numărul accidentărilor apărute din alte cauze (boli, lipsă de pregătire fizica etc.)
- `OthMembers` = numărul accidentărilor în zone minore (abdoment, șold, mână, gât etc.)

Scriptul de python a fost organizat in urmatoarele puncte, pentru a fi mai usor de implementat ideile ce tin de aceasta analiza:

### I. Citire si editare a fisierului original

- Importarea fisierului csv in python si crearea unei noi coloane, "InjuryNumbers", pentru nr total al accidentarilor pentru fiecare echipa.

### II. Creare DataFrame cu procentele fiecarui tip de accidentare, raportat la nr total al lor, pt fiecare echipa in parte

- Crearea unei functii care returneaza procentajul fiecarei accidentari raportat la numarul total al lor pentru fiecare echipa.

### III. Creare DataFrame pentru totalul fiecarei categorii in parte

- Importarea datelor din "Injuries_Updated.csv" si adaugarea unui rand nou pentru afisarea totalului valorilor coloanelor numerice.

### IV. Analiza pe grafice

- Constructia de diverse grafice pentru a analiza si vizualiza datele colectate.

### V. Creare DataFrame cu noile date si clasamentul campionatului

- Crearea unui tabel final care sa compare numarul accidentarilor, procentajul jucatorilor accidentati si pozitia finala a echipelor in campionat.

explicatie corelograma: Valoarea lui r - situata intre -1 (corelatie liniara inversa perfecta) si 1 (corelatie liniara directa si perfecta); pt 0 = lipsa legaturii dintre variabile
