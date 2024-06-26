# Player-injuries

Ideea principala a acestui studiu a pornit de la un subiect comun, fotbalul, si am decis sa analizam daca numarul accidentarilor din Premier League, pentru sezonul 2020-2021, ar fi avut o anumita influenta asupra echipelor concurente si, implicit, a pozitionarii lor finale in clasament.

Fisierul csv principal a fost constituit din datele, preluate de pe anumite site-uri ce inregistreaza astfel de statistici si organizat pe coloane, in acest fel:

- **TeamName** = numele echipelor din Premier League
- **Abbreviation** = abrevierea numelor acestor echipe
- **PlayerNumbers** = numărul jucătorilor din lot
- **InjuredPlayers** = numărul jucătorilor accidentați din lot
- **Ankle** = numărul accidentărilor din zona gleznelor
- **Back** = numărul accidentărilor din zona spatelui
- **Calf** = numărul accidentărilor din zona gambelor
- **COVID19** = numărul jucătorilor infectați cu acest virus
- **Foot** = numărul accidentărilor din zona picioarelor (tot ce ține de partea lor inferioară)
- **Groin** = numărul accidentărilor din zona inghinală
- **Hamstring** = numărul accidentărilor suferite asupra tendonului, aflat între șold și genunchi
- **Head** = numărul accidentărilor din zona craniană
- **Knee** = numărul accidentărilor din zona genunchilor
- **Knock** = numărul accidentărilor suferite în urma unor simple lovituri
- **Muscles** = numărul accidentărilor care afectează toți mușchii din corp
- **Shoulder** = numărul accidentărilor din zona umerilor
- **Thigh** = numărul accidentărilor din zona coapselor
- **OthCauses** = numărul accidentărilor apărute din alte cauze (boli, lipsă de pregătire fizica etc.)
- **OthMembers** = numărul accidentărilor în zone minore (abdoment, șold, mână, gât etc.)

Scriptul de python a fost organizat in urmatoarele puncte, pentru a fi mai usor de implementat ideile ce tin de aceasta analiza:

1. Citire si editare a fisierului original
2. Creare DataFrame cu procentele fiecarui tip de accidentare, raportat la nr total al lor, pt fiecare echipa in parte
3. Creare DataFrame pentru totalul fiecarei categorii in parte
4. Analiza pe grafice
5. Creare DataFrame cu noile date si clasamentul campionatului

## I. Citire si editare a fisierului original

Am importat fisierul csv in python si am creat o noua coloana, numita "InjuryNumbers", care sa contina nr total al accidentarilor pentru fiecare echipa in parte. Am realizat acest lucru, deoarece nr jucatorilor accidentati nu poate coincide cu nr accidentarilor la fiecare echipa, pt ca un jucator se poate accidenta de mai multe ori si poate suferi de acelasi tip de accidentare sau de unele diferite. Coloana a fost adaugata ca fiind a 4-a in tabel si, apoi, datele s-au salvat intr-un nou fisier ("Injuries_Updated.csv"). Mai departe, am afisat echipele in functie de "Injury Numbers" in functie de valorile lor descrescatoare, ca sa vedem daca exista vreo diferenta fata de pozitionarea lor in clasamentul final. De asemenea, am vrut sa vedem care categorii de accidentari sunt mai pronuntate la fiecare echipa, asa ca am construit un grafic stacked bar. De altfel, am creat o lista de tip Series, prin care sa observam categoriile de accidentari importante pentru fiecare echipa.

## II. Creare DataFrame cu procentele

In continuare, am dorit sa vedem care este procentajul fiecarei accidentari, raportat la numarul total al lor, pentru fiecare echipa in parte, asa ca am creat o functie, care sa returneze aceste valori intr-o matrice, iar apoi sa fie alocate aceste valori pt fiecare echipa. Noile date au fost salvate in "Percentages per teams.csv", iar variantele lor aproximate la 2 zecimale s-au salvat in "Aprox. Percentages per teams.csv". Pentru a evita anumite probleme de recunoastere a variabilelor, am reimportat datele salvate in ultimul fisier csv si apoi am facut 2 grafice de tip stacked bar orizontale, pentru a observa procentajele fiecarui tip de accidentare de la toate echipele. Primul grafic proiecteaza doar o singura bara, deoarece este construit incat sa afiseze datele doar pt o singura echipa, din input fiind scrisa abrevierea acelei echipe. Al doilea grafic proiecteaza toate echipele si procentele accidentarilor de la fiecare echipa in parte.

## III. Creare DataFrame pentru totalul fiecarei categorii in parte

Mai departe, am importat datele din "Injuries_Updated.csv", am creat un rand nou, pt fiecare coloana, care sa afiseze totalul valorilor lor (asta pt coloanele numerice), si le-am salvat in "Injuries_with_TOTAL.csv". Apoi, am vrut sa vedem care este procentajul fiecarui tip de accidentare, raportat la total. Pentru acest lucru, am copiat din dataframe-ul precedent doar randul cu total, raportat la "InjuryNumbers" si categoriile de accidentari, si am creat o noua coloana, numita "Percent", pentru a fi salvate respectivele procente. De altfel, coloana referitoare la categorii am numit-o "Categories", iar randul referitor la "InjuryNumbers" a fost sters, pentru a se putea realiza un grafic corespunzator acestor date.

## IV. Analiza pe grafice

In continuare, am construit mai multe grafice. Pentru a observa procentele aferente fiecarei categorii, raportat la numarul total de accidentari, am creat un bar-chart si un treemap. Luand in considerare numarul total al accidentarilor, in functie de tipurile lor, am creat un grafic bar-chart, pt valorile fiecarui tip principal de accidentare dintr-o echipa. Astfel, am proiectat valorile pt categoriile 'Ankle','Knock' si 'Thigh', ca sa vedem cat de mult variaza acestea in functie de echipa. De asemenea, am construit un grafic heatmap pt corelatia dintre accidentari, alaturi de un alt bar-chart, pt procentajul jucatorilor accidentati. De altfel, pentru a realiza ultimul grafic mentionat, am creat in dataframe-ul original o coloana numita "Player_Inj_Perc", pentru a fi salvate valorile procentuale respective.

explicatie corelograma: Valoarea lui r - situata intre -1 (corelatie liniara inversa perfecta) si 1 (corelatie liniara directa si perfecta); 
pt 0 = lipsa legaturii dintre variabile

## V. Creare DataFrame cu noile date si clasamentul campionatului

Mai departe, din DataFrame-ul original, am extras coloanele necesare si am realizat 2 sortari descrescatoare, aplicate in functie de "TeamName": prima pt "InjuryNumbers", la care s-a adaugat coloana "Inj_Numb_Pos" cu pozitiile echipelor in functie de aceasta sortare, iar cea de-a doua pt "Player_Inj_Perc", pt care s-a creat o coloana noua tot pt pozitiile echipelor, numita "Player_Inj_Perc_Pos". Desigur, respectivele coloane s-au salvat in 2 variabile diferite, de tip dataframe (prima cu numarul de accidentari, cea de-a doua pt procentajul jucatorilor accidentati). Apoi, printr-un dictionar, am creat un dataframe, ce contine o parte din clasamentul Premier League pt sezonul 2020-2021. La acest dataframe, s-au adaugat datele din celelalte 2 dataframe-uri create recent, astfel creand un tabel final, pentru a vedea daca exista vreo legatura intre numarul accidentarilor, procentajul jucatorilor accidentati si pozitia finala a echipelor la finalul campionatului.

## Am dăugat și câteva observații privind vulnerabilitățile și potențialele probleme în codul prezentat:

1. La citirea fișierului CSV inițial nu sunt specificate encoding-ul și separator-ul. Dacă fișierul are alt encoding (ex. UTF-8 cu BOM) sau separator (ex. ";") ar putea apărea erori.

2. Codul se bazează pe existența anumitor coloane în fișierul CSV de intrare (ex. `injuries_list`). Dacă structura fișierului se modifică, va genera erori.

3. La crearea graficului stacked bar pentru o singură echipă, numele echipei este citit de la tastatură fără validare. Dacă se introduc valori inexistente, va genera erori.

4. Etichetele de pe axa X a unor grafice (ex. stacked bar) se pot suprapune dacă sunt prea lungi, reducând lizibilitatea. Ar fi util de gestionat dimensiunea fontului și rotația etichetelor.

5. Nu sunt tratate potențiale excepții la salvarea fișierelor CSV de ieșire (ex. directory inexistent, lipsă permisiuni).

6. Crește complexitatea prin prelucrarea întregului DataFrame la fiecare calcul de procente/totaluri. Ar fi mai eficient de filtrat/agregat doar coloanele necesare.

7. Unele grafice au hardcodate culori, dimensiuni, locații de legendă etc. E preferabil să fie calculate dinamic sau configurabile.

8. Codul e dependent de ordinea coloanelor din DataFrame la selectarea unui subset (ex. `iloc[:, 0:4]`). Dacă se modifică ordinea coloanelor, rezultatele vor fi afectate.

9. Indexarea cu numere hardcodate (ex. la calculul procentajelor per total) este predispusă la erori dacă se modifica inputul.

10. Lipsa comentariilor și descrierilor ale funcțiilor/variabilelor îngreunează citirea și înțelegerea scopului anumitor secțiuni de cod.

## Contribuție

Per total, codul ar putea fi îmbunătățit prin validarea inputului, tratarea excepțiilor, creșterea configurabilității, reducerea dependenței de structura datelor de intrare și documentarea mai detaliată a scopului pașilor. Dar funcțional, realizează transformările și produce graficele descrise.

Contribuțiile sunt binevenite! Simțiți-vă liberi să deschideți un issue sau să trimiteți un pull request pentru a sugera îmbunătățiri sau a raporta probleme.


## Configurare:
1. Clonează repository-ul:
	git clone https://github.com/ionescuionut1708/Player-injuries
2. Instalează dependențele:
	pip install -r requirements.txt
3. Rulează aplicația:
	python main.py
