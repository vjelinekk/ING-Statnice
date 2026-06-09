# 1. Softwarový proces a jeho složky. Modely životního cyklu software, jejich vlastnosti. Iterativní vývoj software - prvky, postupy, fáze, varianty podle míry iterativnosti.
## Softwarový proces a jeho složky.
- **Proces** = sled činností vedoucí k výsledku
	- Mění vstupy na výstupy
	- Je opakovatelný
- **SW Proces** = soubor činností, metod a nástrojů používaných k vývoji nasazení a údržbě SW
	- Transformuje požadavky uživatele v funkční SW produkt
	- Definuje **kdo, kdy, co, jak** má v projektu dělat
- **Rozdělení:**
	- Řídící (**Organizational Life Cycle Processes**)
		- Organizují a koordinují projekty uvnitř organizace
	- Hlavní (**Primary Life Cycle Processes**)
		- Přímo vedou k cíli SW projektu
	- Podpůrné (**Supporting Life Cycle Processes**)
		- Podporují hlavní procesy
### Složky SW procesu
- **Aktivity**
	- Co se dělá
	- Např.: vývoj, testování, nasazování
- **Role**
	- Kdo to dělá
	- Např.: vývojář, tester, Scrum Master
- **Artefakty**
	- Mezivýsledky
	- Např.: zdrojový kód, logy, dokumentace
## Modely životního cyklu software, jejich vlastnosti.
- Tří dimenze:
	- **Cyclicity** – jak cyklická aktivita je
	- **Rigidity** – flexibilita aktivity (jak snadné je něco změnit)
	- **Ceremony** – míra administrativy aktivity
- **Rozdělení podle dimenzí:** sekvenční, iterativní, adaptivní
	- ![[Pasted image 20250603215840.png]]
### Sekvenční
- Vše se plánuje dopředu
- Zaměřeno na celý rozsah projektu
- Vhodné pro:
	- Projekty se stabilními požadavky
	- Malé projekty
	- Využívané technologie jsou známé a ověřené
#### Waterfall
- Jeden z nejstarších modelů
- Výstupu jedné etapy jsou použity jako vstupy druhé etapy
- Etapy musí jít po sobě
- ![[Pasted image 20250603220207.png]]
#### V-Model
- Využívá se v projektech, kde finální produktu musí mít vysokou míru zaručení požadované kvality
- Při každé fázi projektu se připravují validační postupy
- Na konci každé fáze se verifikuje výstup
- Automotive
- ![[Pasted image 20250603220253.png]]
### Iterativní
- Hlavní aktivity se několikrát opakují
- Produkt je vyvíjen prostřednictvím iterací
- Vhodné pro:
	- Projekty s jasným kontextem
	- Rozsáhlé a komplexní problémy
#### Spirálový model
- ![[Pasted image 20250603220509.png]]
- **4 hlavní kvadranty:**
	1. Analýza možností (cíle, omezení, alternativy)
	2. Zhodnocení a prototypování
	3. Vývoj SW
	4. Plánování další iterace
#### RUP (Rational Unified Process)
- ![[Pasted image 20250603220545.png]]
- **Inception** = definice rozsahu projektu, identifikace stakeholderů, UC, kritéria úspěchu, rizika, odhad zdrojů, plán projektu
- **Elaboration** = analýza problémové oblasti, architektonický základ, plán projektu
- **Construction** = vyvíjení a integrace komponent a funkcí aplikace
- **Transition** = předání SW produktu
#### Adaptivní
- Proces se mění za běhu, reagujeme na změny
- Kontext a požadavky jsou *volné* => rozsah projektu malý
- Prioritou je **dodržet čas, nikoliv rozsah**
##### XP (Extreme Programming)
- Důraz na kvalitu kódu
- Typické principy:
	- Párové programování
	- Časté releasy
	- Silná spolupráce se zákazníkem
##### SCRUM
- ![[Pasted image 20250603221220.png]]
- Probíhá ve sprintech
- **Pojmy:**
	- Standup
	- Scrum Master
	- Product Owner
	- Team
	- Backlog
	- Product Backlog
	- Sprint Planning Meeting
	- Retrospektivy
## Iterativní vývoj software - prvky, postupy, fáze, varianty podle míry iterativnosti.
- Rozdělení velkých projektů na malé
- **Průběh iterace:**
	- Plánování
	- Zpřesnění požadavků
	- Implementace
	- Ověření
	- Validace zákazníkem
	- Zhodnocení týmu
- **Pravidla iterace:**
	- Běžící iterace je uzavřená vůči změnám
	- Pevný datum ukončení
- **Retrospektivy:**
	- Glad, sad, mad
	- Start, stop, continue
	- Liked, lacked, learned, longed for
- **Milníky:**
	- **LCO (Lifecycle Objectives)** = zahájení (definování cílů projektu, vize)
	- **LCA (Lifecycle Architecture)** = projektování (způsoby řešení, architektura)
	- **IOC (Initial Operational Capability)** = konstrukce (vytobit řešení, beta verze)
	- **GA/REL (General Availability/Release)** = nasazení
### Scrum
- **Role:**
	- **Team** – cca 7 lidí různých zaměření ideálně na full-time
		- Cross-functional
		- Self-organihing
		- Empowered
	- **Product Owner (PO)** – zastupuje zákazníka
		- Odpovědný za vídělečnost produktu
		- Definuje požadavky, priority, akceptace
		- Rozhoduje o datumu releasu a co má obsahovat
	- **ScrumMaster** – rozumí Scrumu
		- Dokáže řešit situace za provozu
		- Je firewallem pro tým
		- Není to team leader
- **Ceremonie:**
	- **Sprint Planning** – plánování obsahuj sprintu
	- **The Daily Scrum** – standup pro shrnutí v jaké rozpracovanosti tým je
	- **The Sprint Review** – demo schůzka s PO
	- **The Sprint Retrospective** – retrospektiva
- **Artefakty:**
	- **Product Backlog** – seznam požadavků na produkt
		- Vlastní a spravuje ho PO
	- **The Sprint Goal** – cíle sprintu hodnotné pro zákazníka
	- **Sprint Backlog** – plán úkolů na aktuální sprint
	- **Burndown Chart** – ukazuje v čase kolik práce ještě zbývá
		- ![[Pasted image 20250604121219.png]]
# 2. Plánování a řízení softwarového projektu. Definování projektu, logický rámec a projektová charta projektu, zúčastněné osoby. Plán rozsahu projektu, odhadování pracnosti, časový plán a související metody, plán zdrojů a nákladů. Sledování a úpravy postupu projektu.
## Plánování a řízení softwarového projektu.
- **Projekt** = dočasné úsilí s cílem vytvořit unikátní produkt, služby nebo výsledek
	- **Vlastnosti:**
		- Unikátní účel
		- Dočasný
		- Realizován s nemalým úsilím
		- Vyžaduje zdroje
		- Má sponzora a často i zákazníka
		- Zahrnuje nejistotu
- **Projektový management** = aplikování znalostí, dovedností, nástrojů a technik během projektových aktivit s cílem dosáhnout požadovaných cílů
- **Proces** = známá opakovatelná činnost
- **Program** = více projektů
- **Dilema project managementu:**
	- ![[Pasted image 20260508125059.png]]
- **Projektový trojimperativ:**
	- ![[Pasted image 20260607182152.png]]
- **Sponzor** = ten kdo dodává projektu zdroje
- **Stakeholder** = ten kdo je zainteresován na projektu nebo jím ovlivněn
- O úspěchu projektu rozhoduje splnění požadavků stakeholderů ne cílů
### Životní cyklus projektu
- = soubor fází projektu
- Typické fáze:
	1. Příprava, analýza, tvorba konceptu (*inception*)
	2. Návrh řešení (*elaboration*)
	3. Vlastní realizace (*construction*)
	4. Dokončení (*transition*)
- **Fáze a hlavní projektové artefakty:**
	- ![[Pasted image 20260508130343.png]]
- **Milník** = ukončení jednotlivé fáze
- **Druhy:**
	- **Prediktivní** – z rozsahu se odvíjí cena, plán jde odhadnout a vyjednat předem
		- Vodopádový model
			- ![[Pasted image 20260508130819.png]]
	- **Adaptivní** – na začátku nelze vytvořit detailní zadání nebo plán
		- Iterativní metodiky
		- Agile
		- SCRUM
		- ![[Pasted image 20260508130931.png]]
		- **RUP:**
			- ![[Pasted image 20260508130955.png]]
### Kritické faktory úspěchy projektu
- **Pozitivní faktory:**
	- Podpora vedení – **Top Management Commitment**
	- Zapojení uživatelů
	- Zkušený PM
	- Jasné cíle
	- Spolehlivé odhady
- **Negativní faktory:**
	- Nerealistické termíny
	- Měnící se požadavky
	- Málo zdrojů
	- Špatné projektové řízení
- **Charakteristika úspěšných projektů:**
	- Používají integrovaný přístup
	- Rozvíjejí projektové lídry
	- Využívají vhodné procesy
	- Vyhodnocují zdraví projektu pomocí metrik
### Role PM
- PM musí znát a umět:
	- Problematiku, standardy, předpisy
	- Projektové prostředí a nástroje
	- Řízení jako takové
	- Mezilidské vztahy
- Doporučené vlastnosti:
	- Hardskills
	- Softskills
	- Rozumět organizaci
### Metody řízení projektů
- ![[Pasted image 20260508132451.png]]
- **PRINCE2:**
	- **7 principů:**
		- ![[Pasted image 20260511134548.png]]
### Řízení rozsahu
- **Požadavky:**
	- MOSCOW
	- Priorita
	- **Druhy:**
		- ![[Pasted image 20260508132800.png]]
	- **Funkční:**
		- ![[Pasted image 20260508132847.png]]
	- **Nefukční:**
		- ![[Pasted image 20260508132905.png]]
- **WBS** = Work Breakdown Structure
- **Změnové řízení** = proces jak měnit za pochodu požadavky
### Řízení času
- Definování aktivit
- Uspořádání aktivit
- Odhad zdrojů
- Odhad trvání
- Sestavení plánu
- Řízení plánu
- **WBS**
- Milníky
- **Precende Diagramming Method (PDM):**
	- ![[Pasted image 20260508133159.png]]
- Ganttovy diagramy
- Critical Path Method
- Kanban
### Řízení nákladů
- TCO = Total Cost of Ownership – cena za celou dobu životnosti projektu
- **Tangible náklady** = snadno vyčíslitelné
- **Intangible náklady** = nelze vyčíslit
- **Přímé náklady** = náklady snadno spojitelné s projektem a činnostmi
- **Nepřímé náklady** = náklady nejsou přímo spojené s projektem
- **Sunk cost** = náklady za zrušení celého projektu někdy v budoucnosti
### Řízení lidí
- Získání co největšího užitku od zapojených lidí
- Proces zahrnuje:
	- Plánování
	- Nábor
	- Rozvoj
	- Řízení projektového týmu
- **Vnitřní motivace** = lidé za zapojují do aktivity z důvodu uspokojení, které jim přináší
- **Vnější motivace** = stimulace, je způsobena odměnou nebo stresem
- **Týmové role:**
	- ![[Pasted image 20260508134052.png]]
### Řízení kvality
- **Kvalita** = souhrn prvků, které přispívají k dosažení vyřčených nebo očekávaných potřeb
- QA
- Unit testy, UAT, Integrační testy, Systémové testy
- Pět nákladů souvisejících s kvalitou:
	- Cena za prevenci
	- Cena za ověření
	- Cena za vnitřní chybu
	- Cena za vnější chybu
	- Cena za vybavení
### Řízení rizik
- **Riziko** = nepříznivý faktor, který může a nemusí nastat
- Míra ppsti.
- Dopad
- Matice rizik:
	- ![[Pasted image 20260508134353.png]]
- **Seznam rizik:**
	- ![[Pasted image 20260508134435.png]]
### Řízení komunikace
- ![[Pasted image 20260508134513.png]]
- **RAM** = Responsibility Assignment Matrix
	- ![[Pasted image 20260508134541.png]]
### Řízení obstarávání
- **Nástroje a techiky:**
	- Make vs buy
	- Expertní odhad
	- Průzkum trhu
### Integrované řízení projektu
- **Metoda Net Present Value (NPV):**
	- Analyzuje čístý peněžní zisk nebo ztrátu přičemž nebere v úvahu budoucí vývoj projektu za uvažovaným okamžikem
	- Čím větší NPV tím lepší
	- $$NPV = \sum_{t=1}^{n} \frac{R_t}{(1 + i)^t} - I$$
- **Return on Investment (ROI):**
	- Vyjadřuje se v procentech
	- $$ROI = \frac{\text{Celkové přínosy (úspory)} - \text{Celkové náklady}}{\text{Celkové náklady}} \times 100 [\%]$$
- **Weighted Scoring Model (WSM):**
	- Systematický a celistvý přístup k výběru projektu
	- ![[Pasted image 20260508135744.png]]
## Definování projektu, logický rámec a projektová charta projektu, zúčastněné osoby.
- **Projekt** = časově omezené úsilý s cílem vytvořit výsledek (materiální, nemateriální) podle plánu, navržený, organizovaný, a realizovaným pod řízením někoho v zájmu vlastníka/zadavatele
	- Má unikátní cíl
- **Cíl projektu** = stav, do kterého se chceme realizováním projektu dostat
	- Cíl = věcný + termínový + nákladový
	- **SMART** = Specific, Measurable, Assignable, Realistic, Timebound
### Logický rámec
- **Logický rámec** = základní přehledný pohled na projekt
	- Tvorba využívá brainstorming
	- ![[Pasted image 20250517110037.png]]
### Projektová charta
- **Projektová charta** = zakládací listina projektu symbolizující formální rozhodnutí projekt realizovat
	- Výstup fáze zahájení projektu
- **Obsahuje:**
	- Účel projektu
	- Cíle projektu
	- Rozsah projektu
	- Stakeholders
	- Výstupy projektu
	- Časový rámec projektu
	- Rozpočet
	- Kritéria úspěchu
	- Rizika
### Stakeholders
- = zainteresovaná strana
- Kdo?
	- Členi týmu
	- Lidi ovlivněný projektem
	- Lidi ovlivňující projekt
- **Analýza stakeholders:**
	- ![[Pasted image 20250517100225.png]]
- **Komunikační strategie:**
	- ![[Pasted image 20250517100303.png]]
## Plán rozsahu projektu, odhadování pracnosti, časový plán a související metody, plán zdrojů a nákladů.
- **Product Scope** = co přesně musí produkt splňovat
- **Project Scope** = práce, která musí být v projektu vykonána
- **Projektová charta** = zakládací listina projektu symbolizující formální rozhodnutí projekt realizovat
	- Výstup fáze zahájení projektu
- **Fáze scope managementu**
	1. Plánování řízení rozsahu
	2. Sběr požadavků
	3. Definování rozsahu
	4. Vytváření WBS
	5. Ověřování rozsahu
	6. Řízení změn rozsahu
- Požadavky
- MoSCoW
### Odhadování pracnosti, časový plán a související metody
1. Definování aktivit
2. Sekvencování aktivit
	- ![[Pasted image 20250517112320.png]]
	- **Lead time** = aktivita začne dřív
	- **Lag time** = aktivita má zpoždění
	- Tvrdá, měkká a externí logika
3. Odhad potřebných zdrojů
4. Odhad doby trvání
	- Benchmarking
	- Parametrický odhad
	- Expertní odhad
	- Tříbodový odhad – optimistická, pesimistická a nepravděpodobnější varianta
5. Vytvoření časového rozvrhu
6. Kontrola časového rozvrhu
- **Kritická cesta CPM (Critical Path Method)**
	- Nejkratší doba realizace projektu
- **Critical Chaing** = rozšíření kritické cesty, které do plánování zahrnuje i omezené zdroje a používá centralizované buffery
- **WBS**
- Ganttovy diagramy
### Plán zdrojů a nákladů

#### Plánování zdrojů a kapacit
- **Hlavní zdroje:**
	- Lidská práce
	- Vybavení
	- Materiál
- **Postupy při plánování:**
	- Kvalifikovaný odhad
	- Analogie
	- Normy
	- Simulace
	- Kreativní techiky
- **RACI matice:**
	- R = responsible
	- A = accountable
	- C = consulted
	- I = informed
#### Plánování nákladů
- **Metody stanovení nákladů:**
	- Analogické odhady
	- Expertní odhady
	- Parametrické modelování
	- Odhad zdola nahoru
- **Přímé náklady** = osobní náklady pacovníků na projektu, náklady na materiál, nákud služeb, cesotvné, subdodávky
- **Nepřímé náklady** = náklady, které nejlze přiřadit ke konrétnímu projektu
	- Energie a provoz budov, daně, popaltky
- **Studentksý syndorm:**
	- Činnost se zahajuje až, když je to nezbytně nutné
- **Parkinsonův projektový zákon:**
	- Činnost trvá nejměné tak dlouho, jaký má odhad
## Sledování a úpravy postupu projektu.
- **Fáze řízení změny:**
	1. Indentifikace změny
	2. Implementace
	3. Ukončení
- ![[Pasted image 20250517132316.png]]
- **Proces změny (8 kroků změny dle Kottera):**
	- ![[Pasted image 20250517132423.png]]
# 3. Management projektových rizik. Hodnocení a kontrola projektu, analýza vytvořené hodnoty. Správa projektové dokumentace. Multiprojektové řízení, projektová kancelář.
## Management projektových rizik.
- ![[Pasted image 20250517135545.png]]
- **Zdroje projektových rizik:**
	- Externí
	- Interní
- **Klasifikace rizik dle růných hledisek:**
	- Dle oblasti
	- Dle pořadí výskytu
	- Dle odhadnutelnosti
	- Dle výskytu
- **Metody a nástroje identifikace rizik:**
	- Brainstorming
	- SWOT (Strengths, Weaknesses, Opportunities, Threats) analýza
	- Ishikawovy diagramy
		- ![[Pasted image 20250517141036.png]] 
	- Monte Carlo
		- Simulace
	- Event Tree Analysis
	- Paretův princip
		- 80% důsledků z 20% příčin
	- Delphi technika
- **Risk Breakdown Structure**
- Rozhodovací stromy
- **Metody pro analýzu rizik:**
	- Stanovení hodnoty rizika
		- $HR = P \times D$
			- $P$ – pravděpodobnost
			- $D$ – dopad
	- RIPRAN (Risk PRoject Analysis)
	- FRAP (Facilitated Risk Analysis Process)
		- ![[Pasted image 20250517141917.png]]
	- Simulace
	- Prediktivní modely
	- Oborové standardy
- ![[Pasted image 20250517141615.png]]
- **Ošetření rizik technikou 4T**
	- Tolerate = přijetí rizika, pokud je jeho dopad a ppst. v rozumných mezí
	- Terminate = úplné odstranění rizika tím, že se zastaví činnost, který riziko nese
	- Treat = přijití opatření ke snížení nebo kontrole dopadů
	- Transfer = přenést rizika na třetí stranu
- **Strategie pro příležitosti:**
	- Využít
	- Sdílet
	- Posílit
- **Registr rizik**
## Hodnocení a kontrola projektu, analýza vytvořené hodnoty.
- **Sledování pokroku:**
	- Sledování směrného plánu
	- Controlling a analýza odchylek
	- Analýza vytvořené hodnoty
	- Ganttův diagram
- **Metody měření a dohlížení:**
	- Týdenní report
	- Měsíční kvartální report
	- Controlling
### EVM (Earned Value Management)
- ![[Pasted image 20260607192343.png]]
- Technika hodnotící výkon a pokrok projektu z hlediska rozsahu, harmonogramu a zdrojů
- **Základní vstupy:**
	- **Planned Values (PV)** = plánovaná hodnota
	- **Actual Costs (AC)** = vyčerpané prostředky
	- **Earned Value (EV)** = skutečně dosažená hodnota
- **Project Performance Index (PPI)**
	- Zachycuje časovou výkonnost a nákladovou účinnost projektu
	- **Cost Performance Index (CPI)** = zobrazuje nákladovou účinnost prováděné práce
		- $\text{CPI} = \frac{\text{EV}}{\text{AC}}$
			- Hodnota vyšší jak 1 => úspory
			- Hodnota nižší jak 1 => zdržení projektu
	- **Scheduled Performance Index (SPI)** = zobrazuje výkonnost prováděné práce v čase a dodržení harmonogramu
		- $\text{SPI} = \frac{\text{EV}}{\text{PV}}$
		- Hodnota vyšší jak 1 => jsme napřed
		- Hodnota nižší jak 1 => zdržení
	- **Cost Variance**
		- $\text{CV} = \text{EV} - \text{AC}$
	- **Schedule Variance**
		- $\text{CV} = \text{EV} - \text{PV}$
	- **Budget at completion (BAC)**
	- **Estimated at completion (EAC)** = zachycuje aktuální odhad celkové výše rozpočtu
		- $\text{EAC} = \frac{\text{BAC}}{\text{CPI}}$
	- **Variance at completion (VAC)** = umožňuje pohled na předpokládané budoucí finanční zdraví projektu
		- $\text{VAC} = \text{BAC} - \text{EAC}$
	- **Estimate to completion (ETC)** = objem prostředlů nezbytný pro dokončení projektu
		- $\text{ETC} = \text{BAC} - \frac{\text{EV}}{\text{CPI}}$
	- **To-Complete PI (TCPI)** = požadovaná výkonnost projektu pro dokončení projektu v plánovaném rozpočtu
		- $\text{TCPI} = \frac{\text{BAC} - \text{EV}}{\text{BAC} - \text{AC}}$
## Správa projektové dokumentace.
- **Informace o projektu a jejich kritéria**
	- **Včasnost**
	- **Relevantnost**
	- **Srozumitelnost**
	- **Přesnost**
	- **Aktuálnost**
- **Typy dokumentace:**
	- **Projektová**
		- Určená pro řízení projektu
		- Vlastní jí PM
		- Příklady:
			- Projektový pán
			- Registr rizik
			- Akceptační protokoly
	- **Technická**
		- Výstup projektu (popisuje samotný produkt)
		- Určená pro koncové uživatele, administrátory nebo provozní tým
		- Příklady:
			- Uživatelská příručka, API dokumentace, architektura
- **Životní cyklus projektové dokumentace**
	1. **Iniciační fáze** – projektová charta
	2. **Plánovací fáze** – projektový plán, WBS, harmonogram, RACI, ...
	3. **Realizační fáze** – status reporty, Change Requests, zápisy z jednání
	4. **Ukončovací fáze** – akceptační protokoly, závěrečná zpráva
- **Formální náležitosti a vlastnosti dokumentu**
	- Název dokumenty a ID
	- Datum vzniku a datum poslední aktualizace
	- Identifikace tvůrce
	- Seznam změn
	- Platnost a status dokumentu
## Multiprojektové řízení, projektová kancelář.
- **PPM** = Projet Portfolio Management
- **Oblasti:**
	- ![[EITM - Teorie 2026-05-07 20.28.49.excalidraw|500x500]]
- Projekty jsou realizované v kontextu organizace
- Project Management musí vzít v úvahu celkovou situaci v organizaci
- ![[Pasted image 20260507205010.png]]
### Organizační rámce
- Organizační rámce umožňují náhled na organizace z několika základních perspektiv
- Pochopení může pomoci k dosažení porozumění potřeb a očekávání
#### Strukturální rámec
- Zaměřuje se na role, odpovědnosti, koordinace a řízení
- Organizační struktury pomáhají s definicí tohoto rámce
- **Základní organizační struktury:**
	- ![[Pasted image 20260507204358.png]]
#### Rámec lidských zdrojů
- Zaměřuje se na poskytování harmonie mezi potřebami zaměstnanců a organizace
#### Politický rámec
- Předpokládá, že organizace je koalice složená z různých zájmových skupin
- Konflikt a moc tvoří základní problém
### Symbolický rámec
- Zaměřuje se na symboliku a významy souvisejícíh událostí
- Kultura organizace
### Proces portfolie managementu
 ![[Pasted image 20260507205110.png]]
### Proces produktového managementu
![[Pasted image 20260507205206.png]]
### Projektová kancelář
- Přehled všech projektů
	- Zásobník projektů
	- Spuštěné projekty
	- Dokončené projekty
- Stav projektu
	- On time = bude dokončen podle plánu
	- On budget = vejde se do rozpočtu
- **Zahájení projektu:**
	- Defince projektu – rosah, cena, termín
	- Tým
	- Zdroje
	- Souběh projektů
	- Kickoff schůzka
- **Přiřazení zdrojů**
- **Monitoring**
	- Burdown Chart
	- Zdraví projektu
		- ![[Pasted image 20260507205541.png]]
# 4. Druhy požadavků na software. Metody získávání, analýzy a dokumentace (specifikace) požadavků. Související nástroje a modely.
## Druhy požadavků na software.
- ![[Pasted image 20260508132800.png]]
- **Požadavky** = co zákazník chce
- **Specifikace požadavků** = popis zadání tak, aby se z toho dalo vycházet při implementaci
- Co uživatel nepotřebuje není požadavek
- **Funkční:**
	- = co má SW umět
	- ![[Pasted image 20260508132847.png]]
- **Nefunkční:**
	- = jak se má systém chovat
	- ![[Pasted image 20260508132905.png]]
- **FURPS+**
	- Functionality
	- Usability
	- Reliability
	- Performance
	- Supportability
	- + – ostatní požadavky (např. na OS)
## Metody získávání, analýzy a dokumentace (specifikace) požadavků.
### Metody získávání požadavků
- **Interaktivní** – rozhovory, spolupráce s uživateli
	- **On-site customer** = oborový expert
	- **Strukturovaný rozhovor** = připravené otázky
	- **Requirements workshop** = setkání se za účelem sběru a upřesnění požadavků
		1. Příprava
		2. Brainstorming
		3. Zápis
- **Neinteraktivní** – studování dokumentace, hlášení problémů, konkurence
### Analýza a specifikace požadavků
- **Analýza** = roztřídění posbíraných informací, nalezení logických chyb a určení priorit
	- **Hlavní činnosti:**
		- Kontrola správnosti a úplnosti
		- Klasifikace a strukturování
		- Prioritizace
			- MoSCoW
				- Must have
				- Should have
				- Could have
				- Wont have
- **Dokumentace**
	- **Základní principy:**
		- Jednotlivé požadavky by měly být jednoznačně identifikovány
		- Požadavky se nesmí opakovat
		- Požadavky musí být srozumitelné
	- **Formy:**
		- Textový popis
		- Grafická notace
		- Strukturovaný dokument
	- **Vlastnosti požadavků:**
		- Jednoznačnost
		- Úplnost
		- Splnitelnost
		- Trasovatelnost
		- Ověřitelnost
	- **Vlastnosti celé specifikace:**
		- Úplnost
		- Bezespornost
		- Konzistence
		- Realizovatelnost
		- Ohraničitelnost
		
- **Business case** = ověření přínosů a návratnosti
- **Technický koncept** = ověření proveditelnosti, varianty architektury, technologie, pipeline, prostředí, nasazení
- **Způsob realizace** => greenfield, brownfield, prototyp
- **MVP (Minimum Viable Product)** = nejmenší možná funkcionality, která jde nasadit a šlo sbírat zpětnou vazbu
- **MMP (Minimum Marketable Product)** = nejmenší možná funkcionalita, která je užitečná pro zákazníka (přináší mu benefit)
- **Způsoby definice funkčních požadavků:**
	- **Klasicky:** SW má mít nějaké features a klauzule s použitím shall
		- Každý požadavek by měl mít svoje ID
	- **Objektově:** využití Use Cases
		- **Model užití** = aktéři + případy užití + dokumentace
	- **Agilně:** snaha o to říci co by produkt měl umět
		- **User story** = *as ... i want to ... so that ...*
		- **Epic** = množina **user stories**
- **Doménový model** = základní entity + vazby
	- Popis struktury problémové oblasti
	- **Nezávislý na technologie**
## Související nástroje a modely.
### UseCase Diagramy
- = sekvence akcí, které se systémem provádí uživatel a vedou k požadovaným výsledkům
- **Hlavní části:**
	1. Standardní průběh
	2. Vstupní a výstupní podmínky
	3. Chybové stavy
- **Výsledný model by pak měl být:**
	- Úplný
	- Přehledný a srozumitelný
	- Obsahovat textové popisy
### User Story
- = co uživatel chce a proč
- **As a ... I want to ... so that**
- Obsahuje
	- Název
	- Prioritu
	- Typ
	- Popis
	- Akceptační kritéria
# 5. Definice a význam architektury software, složky architektury. Vztah architektury k požadavkům, kvalitativním charakteristikám software a postupu vývoje produktu.
## Definice a význam architektury SW
- **Definice:**
	- Sada klíčových návrhových rozhodnutí a systému
	- Plán pro konstrukci a evoluci SW systému
	- Co, jak, kdy
- **Význam:**
	- Pokrývá všechny aspekty vyvíjeného systému:
		- Struktura
		- Chování
		- Interakce
		- Nefunkční požadavky
		- Implementace
- Architektura bývá často dočasná => vyvíjí a mění se v průběhu času
- **Preskriptivní architektura** = architektura před implementací systému (as-intended)
- **Deskriptivní architektura** = architektura po implementaci systému (as-implemented)
- **Degradace architektury** = deskriptivní architektura se liší od preskriptivní
	- **Drift** = neúmyslné odchýlení se od preskriptivní architektury
	- **Eroze** = úmyslné odchýlení se od preskriptivní architektury
### Základní součástí SW architektury
- **Komponenty** = prvky, které zapouzdřují zpracovávání (processing) a data
- **Konektory (connectors)** = prvky, které zajišťují interakce mezi komponentami
- **Konfigurace** = množina konkrétních asociací mezi komponentami a konektory
## Vztah architektury ke kvalitativním charakteristikám SW
- Je to vztah vůči nefunkčním požadavkům
- **Nefunkční požadavek** = omezení na systém, které ovlivňuje jeho implementaci a dodání (škálovatelnost, komplexita, ...)
### Výkonnost (efficiency)
- = schopnost SW splnit požadavky na výkon s využitím minimálních zdrojů
- **Komponenty:**
	- Dělat co nejmenší komponenty
	- Jednoduché rozhraní komponent
	- Oddělení datových a zpracovávajícíh (processing) komponent
- **Konektory:**
	- Pečlivý výběr konektorů
	- Opatrné používání *broadcast* konektorů
	- Využívání asynchronních interakcí
- **Konfigurace:**
	- Sdružování často interagujícíh komponent
	- Zvažování dopadu zvolených architektonických stylů
### Komplexita
- = jak moc je složité pochopit a ověřit návrh nebo implementaci komponent
- **Komponenty:**
	- Separation of concerns
	- Funkcionalita pouze v komponentách
	- Izolování processing komponent od formátu dat
- **Konektory:**
	- Konektory se věnují pouze interakci
	- Separation of concerns 
	- Chovat se ke konektorům explicitně (jasně definované konektory)
- **Konfigurace:**
	- Odstranění nepotřebných závislostí
	- Hierarchická dekompozice (rozdělení velkého systému na menší zvládnutelné části)
### Škálovatelnost
- = schopnost SW se přizpůsobovat novým požadavkům na velikost a rozsah
- **Komponenty:**
	- Single responsibility principle
	- Jednoduché a jasné rozhraní komponent
	- Zabránění zbytečné různorodosti
- **Konektory:**
	- Single responsibility principle
	- Používání nejjednodušších konektorů pro daný úkol
	- Konektory neobsahují funkcionality aplikace
- **Konfigurace:**
	- Vyhnutí se bottleneckům
	- Umožnění parelelního zpracování
	- Datové zdroje blízko datovým consumerům
### Adaptabilita
- = schopnost splnění nových požadavků a přizpůsobení se novým podmínkám
- **Komponenty:**
	- Single responsibility principle
	- Minimalizace závislosti mezi komponentama
	- Oddělení dat od metadat
- **Konektory:**
	- Single responsibility principle
	- Flexibilní konektory
	- Možnost spojování konektorů
- **Konfigurace:**
	- Explicitní konektory
	- Transparentnost distribuce (návrh skrývá, že jsou komponenty systému fyzicky oddělené)
### Spolehlivost (dependability)
- = kolekce vlastností systému, které nám umožňují se spolehnout, že systém funguje tak jak má
	- Reliability
	- Availability
	- Robustness
	- Fault-tolerant
	- Survivability
	- Safety
- **Komponenty:**
	- Pečlivá kontrola externích komponent
	- Vhodné řešení výjimek
	- Specifikace hlavních stavových invariant (neměnných podmínek) komponent
- **Konektory:**
	- Použití konektorů, které řídí závislosti komponent
	- Záruky interakcí
	- Podpora technik zvyšující důvěryhodnost pomocí pokročilých konektorů
- **Konfigurace:**
	- Odstranit Single points of failure
	- Zálohy
	- Health monitoring
# 6. Činnosti při konstrukci produktu. Druhy a techniky testování, souvislost testování a jiných disciplín, automatizace. Konfigurační řízení a řízení změn, související postupy vč. CI/CD, vzory a nástroje. Specifika vývoje s použitím AI.
## Činnosti při konstrukci produktu.
- **Hlavní náplň a cíle**
	- Upřesnění požadavků
	- Úpravy návrhu
	- Vývoj a testování modulů
	- Ověření vydávaných verzí
	- Řízení zdrojů a dohled
- **Designérské činnosti:**
	- Detailní návrh modulů a tříd
	- Návrh algoritmů a datových struktur
	- Návrh DB schémat
	- Příprava specifikací pro programátory
	- **Výstupy:**
		- Technická dokumentace
		- UML Diagramy
		- ERA modely
		- Specifikace algoritmů
- **Programátorské činnosti:**
	- Implementace
	- Refaktorizace
	- Jednotkové testování
	- Integrace komponent
- **Testování a ověřování (QA):**
	- Integrační testování
	- Systémové testování
	- Regresní testování
- **Změnové řízení:**
	- Řízení, schvalování a přesná dokumentace změn v zadání a požadavcích
	- Verzování a sledování změn
- **Celkový cíl:**
	- Splnit milník IOC (Initial Operational Capability)
		- Vyrobit řešení
		- Beta verze
## Druhy a techniky testování, souvislost testování a jiných disciplín, automatizace.
- **Kvalita SW** = míra, která udává jak SW splňuje požadavky
- **Typy kvality:**
	- Fitness for Purpose – uživatel dostává to co potřebuje
	- Absence chyb – SW je stabilní a bez zásadních vad
- **Druhy kvality:**
	- Vnější kvalita – to co vidí/vnímá koncový uživatel
	- Vnitřní kvalita – to co vidí programátor uvnitř kódu
- Geneze selhání SW:
	- **Omyl (error) => Defekt (bug) => Chybový stav (fault) => Selhání (failure)**
### Druhy testování
- Jednotkové testy
- Integrační testy
- Systémové testy
- End-to-End testy
- Akceptační testy
- Zátěžové a vykonnostní testy
### Techniky testování
- Black-box
- White-box
- Gray-box
### Souvislost testování a jiných disciplín
- Testování je provázané celým životním cyklem projektu
- **Analýza požadavků:**
	- Revize zadání
	- Nalezení logických sporů a netestovatelných požadavků
	- Techniky jako TDD, BDD
- **Architektura a návrh:**
	- Systém musí být navržen aby byl testovatelný
	- Dodržování SOLID principů
### Automatizace
- Rychlost a frekvence
- Spolehlivost
- Efektivita pro regresi
- ![[Pasted image 20260608230140.png]]
## Konfigurační řízení a řízení změn, související postupy vč. CI/CD, vzory a nástroje.
### Konfigurační řízení
- **Konfigurace** = z jakých prvků je systém poskládán
- **SW konfigurace** = sestava prvků reprezentující určitou podobu systému, musí obsahovat vše co je potřeba k vytvoření příslušné verze poduktu
- **Konzistentní konfigurace** = konfigurace, jejíž prvky jsou bezrozporné
- **Úlohy SCM:**
	- Určení a správa konfigurace
	- Zjišťování stavu systému
	- Správa sestavení a koordinace prací
	- ![[SCM.excalidraw]]
- **Druhy verzí:**
	- **Revize** = historická podoba
	- **Varianta** = alternativní podoba
- **Indentifikace konrétní verze:**
	- **Extenzionální verzování:**
		- Každá verze má jednozačné ID pro každý prvek
		- Jednoduchá implementace, problémy s větším počtu verzí
	- **Intenzionální verzování:**
		- Verze je popsána souborem atributů – každý atribut definuje verzi nějakého prvku
		- Nutný pro větší prostory verzí
- **semver:**
	- Sémantické verzování
	- `MAJOR.MINOR.PATCH + build`
	- `MAJOR` – Změna neni zpětně kompatibilní
	- `MINOR` – Změna je zpětně kombalitibní
	- `PATCH` – Změna implementace, která nemá vliv na API
	- `build` – nový build
### Řízení změn
- **Proces správy změn:**
	- ![[proces-zmeny.excalidraw]]
	- **Change Control Manager** = člověk, který posuzuje kdy a proč přijmout požadavek a jestli je dokončen
	- **Change Control Board** = více CCM
- **Tiket** = požadavek na změnu
	- **Obsahuje:** shrnutí, metadata, popis, konfigurace systému a SW, screenshot, vzorek dat, log, závažnost
	- **Stavy:** Verified => Resolved => Closed
- **Talkback** – na pozadí aplikace při chybě reportuje vývojářům sama
- **Systémy pro správu změn:**
	- **Bug tracking systémy** – evidence bugů (Flyspray, Bugzilla)
	- **Application Lifecycle Management** – správa celého projektu (Jira, Redmine)
### Související postupy vč. CI/CD, vzory a nástroje
- **DevOps** = Development & Operations
	- **Development:**
		- Product Manager
		- UI designer
		- SW architekt
		- Vývojár
		- Tester
	- **Operations:**
		- Administrátoři
		- Podpora
		- Release Manager
- **DevOps cyklus:**
	- ![[Pasted image 20250528222309.png]]
- **CI/CD linka:**
	- **CI** = Continuous Integration
	- **CD** = Continious Deployment/Delivery
	- Automatizovaný proces, který propojuje vývoj, testování a nasazení
	- ![[Pasted image 20250528223243.png]]
- **CICD pipeline** = automatizovaná sekvence kroků, které zajišťuje, že se změny v kódu bezpečně a spolehlivě dostanou od vývojáře až do produkce
	- **Skládá se z:**
		- Job
		- Vstup
		- Stages
		- Výstup
- **Základní princip:**
	- Automatizovaný proces
	- Několik fází (stages)
	- Vstupní a výstupní artefakty
	- **Struktura:**
		- ![[Pasted image 20250529221758.png]]
- **Vstupy:**
	- Zdrojový kód
		- Reference na VCS repo a tag větve/verze
	- Další SW artefakty
		- Resource balíčky
		- Interní komponenty
		- SW 3-tích stran / open-source komponenty
- **Výstupy:**
	- Dočasné artefakty (knihovny/resources)
	- Splněné/failnuté testy, notifikace, reporty
	- Nasazené a běžící aplikace/stránky
## Specifika vývoje s použitím AI.
- **Přínosy AI při konstrukci:**
	- Generování kódu a biolerplate
	- Automatizace vytváření testů
	- Refaktorizace a vysvětlení kódu
	- Rychlé vyhledávání informací
- **Rizika:**
	- Halucinace
	- Bezpečnost
	- Právní a autorské aspekty
	- Vliv na vnitřní kvalitu
# 7. Činnosti při předání a nasazení produktu, provozu a údržbě. Možnosti pro dodávání a nasazování, vztah k variantám sw procesu, řešení defektů a změn, principy DevOps. Vyřazení produktu z provozu. Uzávěrka projektu.
## Činnosti při předání a nasazení produktu, provozu a údržbě.
- V RUP je to fáze **transition**
	- Beta verze hotová
	- Předání produktu zákazníkovi
- Dosažení milníku GA (REL)
- **Artefakty:**
	- Release produktu
	- Podpůrné materiály
	- Baseline kompletní konfigurace release
- **Příprava vydání produktu:**
	- Field testing = testování v prostředí uživatele
	- Konverze a integrace dat = nahrazení dosavadního systému novým
	- Přejímka = akceptační řízení (vše co se musí stát aby zákazník řekl OK)
	- Informační kampaň
- **Provozní fáze projektu** = po dodání projektu => nejdelší fáze životního cyklu
	- **Cíl:** udržet užitečnost produktu a efektivitu
	- **Operations** = udržování produktu v provozu
	- **Support** = podpora koncových uživatelů (L1, L2, L3)
	- **Typy údržby:**
		- Corrective = oprava chyb
		- Adaptive = přizpůsobení změnám
		- Perfective = přidávání nových vlastností
		- Preventive = odstraňování tech. dluhu
## Možnosti pro dodávání a nasazování, vztah k variantám sw procesu, řešení defektů a změn, principy DevOps.
- **DevOps** = Development & Operations
	- **Development:**
		- Product Manager
		- UI designer
		- SW architekt
		- Vývojár
		- Tester
	- **Operations:**
		- Administrátoři
		- Podpora
		- Release Manager
- **DevOps cyklus:**
	- ![[Pasted image 20250528222309.png]]
- Tradiční IT model vs DevOps Model:
	- ![[Pasted image 20250528222443.png]]
- **CI/CD linka:**
	- **CI** = Continuous Integration
	- **CD** = Continious Deployment/Delivery
	- Automatizovaný proces, který propojuje vývoj, testování a nasazení
	- ![[Pasted image 20250528223243.png]]
- **Druhy deployment prostředí:**
	- **Development**
		- Využívají vývojáři
		- Neobsahuj data zákazníka
		- Nestabilní
		- Většinou běží na vývojářovo PC
	- **Testing**
		- Automatické nasazení
		- Využívá QA team
		- Neobsahuje data zákazníka
		- Může být nestabilní
		- Integrační testy
		- Automaticky nastaveno a zničeno
	- **Staging**
		- Vužívá QA a/nebo zákazník pro akceptační testování
		- Podmnožina dat z produkčního prostředí
	- **Production**
		- Využívají zákazníci
		- Připojeno na produkční služby
		- Všechny data z produkce
	- ![[Pasted image 20250528231618.png]]
- **SW deployment** = instalace a nastavení SW na cílovém systému 
	- Manuální instalace pomocí fyzického připojení k HW
	- Automatická instalace a VM v cloudu
- **SW provisioning** = kroky, prováděné před nasazením (deploy) aplikace
	- Instalace OS
	- Aktualizace balíčků
	- Instalace s konfigurace prerekvizit pro SW
	- Vytvoření uživatelů/skupin
	- Zabezpečení VM
- **Strategie nasazování:**
	- **Recreate:**
		- Zastav a znovu vytvoř aplikaci
		- Způsobí výpadek, ale je jednoduché na provedení
		- Rollback také způsobuje výpadek
	- **Blue-green deployment:**
		- Blue = původní prostředí
		- Green = nové aktualizované prostředí
		- **Princip:**
			- ![[blue-green.excalidraw]]
		- **Použití:**
			- Cloudové prostředí
			- Embedovaná a IoT zařízení
	- **Rolling update:**
		- Použitelné pouze v případě, že existuje několik instancí aplikace
			- Horizontální škálování
		- **Princip:**
			- Vyvoříme jednu instanci s novou verzí
			- Odstraníme jednu instanci se starou verzí
			- Opakujeme dokud nemají všechny instance novou verzi
	- **Canary update:**
		- Podobné jako rolling update
		- **Princip:**
			- Nasadíme update a postupně ho zpřístupňujeme více a více uživatelům
	- **Shadow deployment:**
		- Podobný jako blue-green deployment
		- **Princip:**
			- Nasadíme novou verzi a router posílá dotazy jak na novou verzi tak na tu starou
			- Odpovědi přicházejí pouze ze staré verze
		- **Využití:**
			- Testování a debugování nové verze
### Vztah k variantám SW procesu
- **Tradiční procesy:**
	- Charakteristika:
		- Rigorózní fázový přístup
		- Nasazení jako "Big Bang"
	- Dodávání:
		- Plně manuální
		- Tlusté instalační manuály
		- Vysoké riziko selhání
- **Agilní procesy:**
	- Charakteristika:
		- Iterativní přístup
		- Cílem každého sprintu je vytvořit potenciálně nasaditelný produktový inkrement
	- Dodávání:
		- CI/CD
		- DevOps
### Řešení defektů a změn
- **Změna** = Change Request = požadavek na úpravu stávající funkčnosti
	- Jira
- **Defekt** = odchylka mezi očekávaným chování a reálným chováním
	- Nástroje pro trackování – Bugzilla
- **Proces správy změn:**
	- ![[proces-zmeny.excalidraw]]
	- **Change Control Manager** = člověk, který posuzuje kdy a proč přijmout požadavek a jestli je dokončen
	- **Change Control Board** = více CCM
- **Tiket** = požadavek na změnu
	- **Obsahuje:** shrnutí, metadata, popis, konfigurace systému a SW, screenshot, vzorek dat, log, závažnost
	- **Stavy:** Verified => Resolved => Closed
- **Talkback** – na pozadí aplikace při chybě reportuje vývojářům sama
## Vyřazení produktu z provozu.
- **Důvody:**
	- Zastaralá tech.
	- Náhrada novým systémem
	- Nepotřebný
- **Postup:**
	1. Analýza vazeb na ostatní systémy
	2. Volba strategie vyřazení
	3. Testování náhrady
	4. Aktualizace dokumentace
	5. Migrace dat a uživatelů
	6. Archivace dat, kódu, dokumentace
	7. Vypnutí přístupů
	8. Odstranění systému
- **Strategie:**
	- BigBang
	- Po etapách
	- Souběh s novým
## Uzávěrka projektu.
- **Cíl:** formální ukončení projektu a shrnutí zkušeností
- Provedení interního auditu
- Uzavření v SCM, zálohování
# 8. Definice kvality v oblasti softwarového inženýrství. Techniky verifikace a validace, prevence a detekce defektů. Systémy řízení jakosti pro oblast software, související normy. Význam a principy měření software. Etika a profesionalita v sw inženýrství.
## Definice kvality v oblasti softwarového inženýrství.
- **Kvalitní SW:**
	- Kvalita = míra do jaké SW splňuje požadavky
	- Fitness for Purpose = dělá co uživatel potřebuje
	- Absence chyb = SW se dá používat
- **Druhy:**
	- Vnitřní = co vidí programátor
	- Vnější = co vidí uživatel
- **Dvě roviny:**
	- Kvalita produktu – vlasnosti produktu
		- FURPS+
			- Functionality
			- Usability
			- Reliability
			- Performance
			- Supportability
			- +
	- Kvalita procesů – dobré procesy => dobrý produkt
## Techniky verifikace a validace, prevence a detekce defektů.
- **Sedm principů testování:**
	1. Testování ukazuje přítomnost defektů
	2. Kompletní testování není možné
	3. Včasné testování šetří čas
	4. Defekty se shlukují
	5. Pesticidní paradox = neustálé opakování stejných testů dokola časem přestane odhalovat defekty
	6. Testování je závislé na kontextu
	7. Nepřítomnost defektů je klam
- Vlivem lidské chyby se do systému dostane **defekt**
- **Porucha (fault)** – nastane pokud se provede část kódu, která obsahuje defekt
- **Selhání (failure)** – projev poruchy, která způsobila:
	- Uvedení programu do nekorektního stavu
	- Běh nezamýšlenou cestou
- **Úrovně testování:**
	1. testování = debugging
	2. testování má prokázat, že SW funguje
	3. testování má prokázat, že SW nefunguje
	4. smyslem testování není prokazování ničeho konkrétního, ale snížení rizika
	5. testování je metodika/postup vedoucí k produkci SW s nízkou mírou rizika
- **Verifikace** = ověření zda SW splňuje specifikaci
- **Validace** = ověření zda SW dělá to co uživatel chce
- **Verifikační techniky:**
	- Pozitivní testy (test-to-pass)
	- Negativní testy (test-to-fail)
	- Unit testy
	- Integrační testy
	- Systémové testy
- **Validační techniky:**
	- Akceptační testy
	- Beta testování
	- Prototypování
	- Demonstrace a zpětná vazba
- **Prevence** = snažíme se předejít chybám
	- Code reviews
	- Standardy
	- Best-practices
	- Školení
- **Detekce** = odhalení defektů
	- Testování
	- Debugging
	- Loggování
	- Monitoring
## Systémy řízení jakosti pro oblast software, související normy.
- **Shift left** = posunutí aktivit, které zajišťují kontrolu kvality do dřívějších fází vývoje
- **QMS** = Quality Management System
	- Definuje organizační strukturu, procesy a zdroje potřebné pro zajištění kvality
	- V SW se nebavíme jen o kontrole kódu ale o kontrole celého procesu výroby
- **Složky QA systému:**
	- **Organizační prvky** – podpora vedení
	- **Dokumentace** – normy a záznamy
	- **Audit** – dokumentace postupů, důkaz o kvalitě pro zákazníky
- **Základní pojmy QA pro safety-critical systémy:**
	- **SIL (Safety Integrity Level)** = míra úrovně bezpečnostní integrity systému, která kvantifikuje jeho schopnost minimalizovat riziko selhání vedoucího k nebezpečné situaci
	- **Plán zajištění kvality**
	- **Varifikátor – Validátor – Hodnotitel**
- Zanášíme kontroly do všech fází projektu (Inception, Elaboration, Construction, Transition)
- **Normy:**
	- ISO 9000 = základní průvodce, který definuje principy, koncepty a slovník QMS
	- ISO 9001 = specifický, actionable standard obsahující konkrétní požadavky, které musí organizace splnit aby získala formální certifikaci
## Význam a principy měření software.
- **Metrika** = měřitelná charakteristika
- **Druhy metrik:**
	- **Produktové** – charakteristiky materiálů a mezivýsledků
		- Velikost – počet UC, LOC
		- Složitost a přehlednost
		- Spolehlivost
		- Kvalita
	- **Procesní** – charakteristiky postupu a organizace
		- Postup
			- Pracnost
			- Burndown
			- **Velocity** = kolik práce dokážeme zpracovat v iteraci (např. kolik user stories)
		- Kvalita
			- **Breakage** = průměrná váha změny
			- **Defect Discovery Rate** = jak rychle odhalujeme chyby
- **Goal-Question-Metric (GQM):**
	- **Goal:** Co chceme zlepšit nebo dosáhnout?
		- Př.: *Zvýšit kvalitu kódu.*
	- **Question:** Jak poznáme, že jsme cíle dosáhli?
		- Př.: *Kolik defektů bylo nalezeno při testování.*
	- **Metric:** Co konkrétně změříme?
		- Př.: *Počet nahlášených chyb na 1000 řádků kódu*
## Etika a profesionalita v sw inženýrství.
- Základním pilířem je **ACM/IEEE The Software Engineering Code of Ethics and Professional Practice**
	- **8 principů**:
		1. **Veřejný zájem** – SW inženýři musejí jednat v souladu s veřejným zájmem
			- Např.: Lidé jsou nejdůležitější. Nikdy neudělej program, který by mohl někomu ublížit.
		2. **Klient a zaměstnavatel** – jednat v jejich nejlepším zájmu
			- Např.: Hraj fér. Nekraď šéfovi nebo zákazníkovi jejich tajemství ani nápady.
		3. **Produkt** – zajišťovat aby produkty splňovaly nejvyšší profesionální standardy
			- Např.: Nedělej zmetky. Tvoje aplikace musí být bezpečná a pořádně odvedená.
		4. **Úsudek** – zachovávat si nezávislý a profesionální úsudek
			- Např.: Nenech se uplatit ani ukecat. Schval jen to, o čem bezpečně víš, že funguje.
		5. **Management** – manažeři musí podporovat etický přístup k řízení vývoje
			- Např.: Pokud jsi šéf, buď na lidi hodný, nenuť je k podvodům a chraň svůj tým.
		6. **Profese** – rozvíjet integritu a pověst profese SW inženýrství
			- Např.: Dělej ajťákům dobrou reklamu. Když najdeš chybu, nebuď padouch (hacker), ale pomoz ji opravit.
		7. **Kolegové** – být spravedlivý a ohleduplný ke svým kolegům
			- Např.: Pomáhej ostatním v týmu a nechval se za cizí nápady.
		8. **Sám sebe** – neustále se celoživotně vzdělávat
			- Např.: Pořád se uč nové věci, ať nezakrníš a tvoje práce za něco stojí.	
# 9. Role IT v organizaci, IT strategie a governance, základy COBIT. Enterprise architecture (EA), integrace systémů.
## Role IT v organizaci
### 1. IT jako *strojovna*
- Má fungovat, ale nic neřídí
- IT vnímáno čistě jako nákladové středisko
### 2. Poskytovatel služeb
- IT dodává služby s garantovanou kvalitou
- Konsolidace, outsourcing, integrace, procesy, ITIL
	- Konsolidace = slučování, zjednodušování (mám 50 starých PC => koupím 2 nové super výkoné PC)
### 3. Součást byznysu
- Rozpuštění IT do Line Of Business (LOB)
- IT oddělení proaktivně navrhuje jak pomocí technologií zvýšit zisk
### 4. Každý své IT
- Novodobý fenomén
- Často je to hrozba – bezpečnost, chaos
- Bez centrálního řízení, shadow IT
	- **Shadow IT** = veškerý HW, SW, aplikace, cloudové služby, které se ve firmě využívá bez vědomí, schválení a kontroly IT oddělení
### Strategie IT/IS
- **IT strategie** – zaměřena na technologie
- **IS strategie** – zaměřena na byznys
- **Pojmy:**
	- **Vize** = ideální budoucí stav, kterého chce organizace dlouhodobě dosáhnout (*Kde chceme být?*)
	- **Záměr** = hlavní důvod existence organizace a smysl její současné činnosti (*Proč tu jsme a co děláme dnes?*)
	- **Cíl** = konkrétní, měřitelný a termínovaný milník, který musíme splnit, abychom naplnili vizi (*Co přesně a dokdy musíme dokázat?*)
		- ![[Pasted image 20260506142454.png]]
	- **Strategie** = plán a způsob rozložení sil a zdrojů k dosažení cílů
		- ![[EITM - Teorie 2026-05-06 13.59.24.excalidraw]]
	- **Taktika** = krátkodobý manévr nebo specifické akce v rámci dané strategie
	- **Postup** = standardizovaný sled kroků, kterými se opakovaně řeší určitý typ problému nebo činnosti
	- **Metoda** = odborný nástroj nebo technika, kterou používáme k provedení úkolu nebo postupu
	- **Úkol** = jasně definována konkrétní práce pro konkrétního člověka s určeným termínem dokončené
- **Pyramida strategického řízení:**
	- ![[Pasted image 20260506141011.png]]
	- **Vize** – proč to děláme
	- **Strategie** – co budeme dělat abychom toho dosáhli
	- **Taktika** = jak to budeme dělat
- Dobrá strategie vede k úspěchu
- **Postup tvorby strategie:**
	1. Zachycení aktuální stavu IT (*Kde jsme teď?*)
	2. Analýza a informování (*Co to znamená?*)
	3. Definice IT vize (*Kde chcem být?*)
	4. Plán a model dodání (*Jak se tam dostaneme?*)
## IT Strategie
- **Pojmy:**
	- **Vize** = ideální budoucí stav, kterého chce organizace dlouhodobě dosáhnout (*Kde chceme být?*)
	- **Záměr** = hlavní důvod existence organizace a smysl její současné činnosti (*Proč tu jsme a co děláme dnes?*)
	- **Cíl** = konkrétní, měřitelný a termínovaný milník, který musíme splnit, abychom naplnili vizi (*Co přesně a dokdy musíme dokázat?*)
		- ![[Pasted image 20260506142454.png]]
	- **Strategie** = plán a způsob rozložení sil a zdrojů k dosažení cílů
		- ![[EITM - Teorie 2026-05-06 13.59.24.excalidraw]]
	- **Taktika** = krátkodobý manévr nebo specifické akce v rámci dané strategie
	- **Postup** = standardizovaný sled kroků, kterými se opakovaně řeší určitý typ problému nebo činnosti
	- **Metoda** = odborný nástroj nebo technika, kterou používáme k provedení úkolu nebo postupu
	- **Úkol** = jasně definována konkrétní práce pro konkrétního člověka s určeným termínem dokončené
- **Pyramida strategického řízení:**
	- ![[Pasted image 20260506141011.png]]
	- **Vize** – proč to děláme
	- **Strategie** – co budeme dělat abychom toho dosáhli
	- **Taktika** = jak to budeme dělat
### Integrovaný model procesu strategického řízení
- ![[EITM - Teorie 2026-05-06 15.41.44.excalidraw|600x300]]
### Proces formulace podnikové strategie
- ![[EITM - Teorie 2026-05-06 15.49.20.excalidraw|800x450]]
#### Analýza vnějšího prostředí
- Sada metod
- Nejzásadnější **Porterův model pěti sil**, **STEP**, **PESTEL**
#### Porterův model pěti sil
- ![[EITM - Teorie 2026-05-06 16.10.41.excalidraw|500x300]]
#### STEP analýza
- **Společenské faktory**
	- Způsob života lidí
	- Životní hodnoty lidí
	- Např. demografie, distribuce příjmů, životní styl
- **Technologické faktory**
	- Vývoj výrobních prostředků, materiálů a know-how
	- Např. vládní výdaje na vědu a výzkum, nové objevy, vynálezy, patenty
- **Ekonomické faktory**
	- Toky peněz, služeb, zboží, informací a energie
	- Např. inflace, nazaměstnanost, nabídka peněz
- **Politické faktory**
	- Např. stabilita vlády, daňová politika
#### PESTEL
- STEP + **Legal** + **Enviromental**
#### SWOT Analýza
- ![[EITM - Teorie 2026-05-06 17.01.30.excalidraw]]
#### TOWS
- ![[Pasted image 20260506171541.png|700x200]]
#### Analýza vnitřního prostředí podniku
- Např. **Analýza výsledků v jednotlivých funkcionálních oblastech:**
	- Výroba
	- Finance
	- Marketing
	- Úroveň řízení a lidské zdroje
	- Výzkum a vývoj
- **Portfolio metody**
	- **Kroky:**
		1. Vytvoření matice portfolia
		2. Zmapování konkurence a vyvození závěrů o atraktivitě portfolia
		3. Ohodnocení konkurenceschopnosti portfolia
		4. Určení hlavních úkolů a zvážení specifických příležitostí
		5. Určení zdrojů na podporu strategií
		6. Porovnání aktiv z hlediska ziskovosti
		7. Je portfolie v souladu s podnikovou strategií?
#### Matice BCG (Boston Consulting Group)
- ![[Pasted image 20260506163901.png]]
- ![[Pasted image 20260506163913.png]]
### Analýza zájmových skupin
1. **Kulturní kontext**
	- Porozumění hodnotám, které společnost uznává
	- Názory, hodnoty, mínění lidí v podniku
	- **Otázky:**
		1. *Jaké faktory uvnitř, nebo vně podniku mají největší vliv na očekávání interních zájmových skupin?*
		2. *Do jaké míry zohledňuje působení těchto faktorů současná strategie podniku?*
		3. *Jak budou tyto faktory ovlivňovat změny a doprovázející zavádění nové strategie*
	- **Druhy externích vlivů:**
		- Hodnoty společnosti
		- Organizované skupiny
2. **Politický kontext**
	- Očekávání jednotlivých zájmových skupiny
3. **Etický kontext**
- **Cíl:**
	- Identifikace relevantní zájmové skupiny
	- Identifikace a otestování předpokladů a zájmových skupinách
- **Typy předpokladů:**
	- Předpoklady podporující strategii
	- Předpoklady omezující strategii
- ![[EITM - Teorie 2026-05-06 16.54.40.excalidraw|500x300]]
### Typologie strategií
- ![[Pasted image 20260506171951.png]]
### Integrovaný model strategických alternativ
- ![[Pasted image 20260506172019.png]]
## IT Governance, COBIT
- **IT Governance**
	- = přístup a způsob řízení IT procesů v organizaci, který slaďuje informační systém a všechny informační technologie s globální strategií organizace
	- = soubor pravidel, vztahů a procesů, které pomáhají řídit organizaci tak, aby IT v maximální míře podporovala její strategické cíle
	- *"Dělání správných věcí"*
	- ![[Pasted image 20260509195522.png]]
### Governance vs. Řízení
- ![[Pasted image 20260509195854.png]]
- **Governance**
	- Odpovědnost nejvyššího vedení a statutárních orgánů v čele s předsedou představenstva
	- Evaluation
	- Direction
	- Monitoring
	- COBIT
- **Management**
	- Odpovědnost středního a nižšího vedení v čele s CEO
	- Plans
	- Builds
	- Runs and Monitors
	- ITIL
### COBIT
- = Control Objectives for Information and Related Technologies
- **COBIT Evoluce:**
	- ![[Pasted image 20260509201732.png]]
	- **Audit:** Jenom kontrolujeme, jestli IT systémy fungují bezpečně a podle pravidel.
	- **Control:** Nastavujeme mantinely a pravidla, aby se v IT nic nerozbilo. (postihy *- Štěpán Faragula 2026*)
	- **Management:** Aktivně řídíme práci IT týmu, aby dělal přesně to, co zbytek firmy potřebuje.
	- **IT Governance:** Hlídáme, aby IT investice měly smysl, přinášely hodnotu a nebyly moc riskantní.
	- **Governance of Enterprise IT:** Bereme IT jako pevnou součást celé firmy, kde nejvyšší šéfové určují směr a manažeři se starají o každodenní provoz.
- **Domény:**
	- Plan and Organize
	- Acquire and Implement
	- Deliver and Support
	- Monitor and Evaluate
- 37 procesů – COBIT 5
- ![[Pasted image 20260509201853.png]]
- Procesně orientovaný
- Vazba na:
	- IT zdroje
	- Požadavky businessu na vlastnosti informací
	- Cíle na IT Governance
- Klade důraz na kontroly
- Orientovaný na propojení různých úrovní cílů a jejich metrik
- Umožňuje hodnocení zralosti procesů
- Má definované vazby na jiné frameworky
#### Principy COBIT 5
- ![[Pasted image 20260509202124.png]]
#### COBIT Diagramy
- ![[Pasted image 20260509202301.png]]
### Balanced Scorecards (BSC)
- Vyrovnaný přehled výsledků
- Management založených na metrikách
- Prosazení strategických cílů
- ![[Pasted image 20260509212633.png]]
### Six Sigma
- Sbírka technik a nástrojů pro *"process improvement"*
- Zejména pro výrobní podniky
- Měřitelné statistické charakteristiky
- ![[Pasted image 20260509212754.png]]
- ![[Pasted image 20260509213220.png]]
- **6 kroků:**
	1. Definice **výrobku** nebo **služby**
	2. Identifikace **zákazníků** a zjištění jejich klíčových požadavků
	3. Určení vašich **potřeb** k poskytování výrobků a služeb tak, aby uspokojovaly zákazníka 
	4. Definice **postupu**, kterým vykonáváte vaši práci (sestrojení mapy procesu)
	5. **Zdokonalení** postupu, tak aby produkoval méně vad a omezení zbytečných činností
	6. **Neustálé** zdokonalování měřením, analýzou a řízením zdokonaleného procesu
## Enterprise architecture (EA), integrace systémů.
- **EA** = modelování vztahu mezi organizací, byznysem a IT; koncepčně řízený rozvoj tohoto vztahu
	- ![[Pasted image 20260509185310.png]]
- Sjednocení IT s byznysem
- Odpověď na všechny potřeby podniku
- Horizontální pohled – díváme se na podnik jako celek
- Implementace řízení informací
- ![[Pasted image 20260509191032.png]]
### Úrovně EA
- ![[Pasted image 20260509191107.png]]
### Součásti EA
- Metodologie a metodiky
- Správa metadat
- Standardy
- Plánování IT, řízení projektů
- Modelování
### Používané diagramy
#### Process Map Diagram
- ![[Pasted image 20260509191303.png]]
#### Organization Chart Diagram
- ![[Pasted image 20260509191322.png]]
#### Business Communication Diagram
- ![[Pasted image 20260509191345.png]]
#### Technology Infrastructure Diagram
- ![[Pasted image 20260509191441.png]]
### Projektová šablona
- ![[Pasted image 20260509191543.png]]
- Přidělení všech potřebných modelů do jednoho *"projektu"*
### Impact analýza
- Grafické znázornění závislostí mezi objekty
- Úprava praivdel pro analýzu
- Když v systému změním tuhle jednu věc, co všechno se kvůli tomu může rozbít nebo změnit?
### Enterprise Lifecycle
- ![[Pasted image 20260513155101.png]]
### Způsoby popisu EA
#### Zachmann Framework
- Taxonomie pro popis architektury systémů na enterprise úrovní
- ![[Pasted image 20260509192156.png]]
#### TOGAF (The Open Group Architecture Framework)
- Komplexní přístup k návrhu, plánování, implementaci a dohledu EA
- Holistický přístup
- 4 úrovně: byznys, aplikační, data a technologická
- Referenční model
- ![[Pasted image 20260509192518.png]]
#### IBM EA Consulting Method
- Metodika podporující kompletní řešení EA
- Poskytuje:
	- Standardní výstupy popisující vlastní architekturu
	- Dohled na koordinaci na programové i projektové úrovni
	- Dohled a koordinaci realizace změn architektury
### Architektury v rámci EA
#### Byznys architektura
- Jak byznys funguje
- Cíle byznysu
- Aktuální nedostatky
- Omezení a požadavky od IT
##### Strategic Capabilities Network (SCN)
- Identifikace kapacit a zdrojů potřebných pro dosažení a naplnění strategických cílů
##### Complete Business Model (CBM)
- Funkční model podniku
- Podnik popsán jako sada vzájemně propojených komponent
- Identifikace prioritních oblastí pomocí heat map
##### Business Process Model (BPM)
- Procesní model popisující základní entity a vztahy mezi nimi
- Události aktivity, role a data
- **Business Activity Model (BAM)**
	- Popis procesních aktivit
	- Použitelní pro vyhodnocení KPI (Key Performance Indicator)
- **Enterprise Information Model (EIM)**
	- Definuje a strukturuje informace potřebné pro podporu business aktivit podniku
- **Business Roles Model (BRM)**
	- Identifikuje role potřebné pro výkon procesních aktivit
	- Specifikuje znalosti a dovednosti potřebné pro činnosti jednotlivých rolí
#### Informační architektura
- Ovlivněna byznys architekturou
- Klasifikuje podnikové informace
- Jak se spravují informace
- Kde se ukládají data
- Datové schémata
- Dostupnost informací
- Bezpečnost informací
- ![[Pasted image 20260509194757.png]]
#### Aplikační architektura
- Vedlejší výsledek byznys a informační architektury
- Přizpůsobení systému firemním potřebám
- Vztahy a komunikace mezi systémy
- Jak systémy sdílí data
#### Technologická architektura
- Ovlivněna ostatníma architekturama
- Kolekce vybraných technologií a nástrojů pro implementaci architektury
## Integrace na datové vrstvě
- **Historie:**
	- Batch processing
		- ![[Pasted image 20260510155126.png]]
	- Vázáno na fyzická média
- **Přenos souborů:**
	- Data v textových souborech
	- Binární soubory
	- FTP, HTTP
- **Standardizace:**
	- Binární standardizace
		- WORD/DWORD
		- ASCII/EBDIC
	- Nutnost dalších standardizace datových struktur
### Datová pumpa
- Typicky SQL
- Různé programovací jazyky
- ![[Pasted image 20260510153725.png]]
	- `SELECT from DATABASE_A`
	- `INSERT INTO DATABASE_B`
### Základní postupy
- Přenos souborů
- Sdílený soubor
- Sdílená DB
- Replikace DB
- EDI (Electronic Data Interchange)
- ![[Pasted image 20260510153921.png]]
### Dokumentové standardy
- Jednoduché:
	- CSV
	- XML
- Průmyslové:
	- EDI
- Prioprietární
	- SAP IDOC
### ETL (Extract Transform Load)
- Potřeba propojení mnoha zdrojů a cílů dat
	- Master Data Management
	- Business Intelligence
- Podpora více typů DB a dalších zdrojů dat
- Rychlý vývoj
- Snadná údržba
- Dokumentace
- ![[Pasted image 20260510154243.png]]
- Např. IBM InfoSphere DataSage
### Data Pipelining
- ![[Pasted image 20260510155259.png]]
- Nepotřebujeme zapisovat na disk mezi operacemi
- Navazující proces můžeš začít před dokončením předchozího
- Vhodné pro Big Data
### Data Partitioning
- ![[Pasted image 20260510155834.png]]
- Rozdělení dat na části
- Každou část může zpracovávat jeden procesor
### Parallel Dataflow
- ![[Pasted image 20260510160601.png]]
- Limitace:
	- Partition jsou celou dobu stejné
	- Nepoužitelné v praxi
### Parallel Dataflow with Auto Repartitioning
- ![[Pasted image 20260510160757.png]]
## Integrace na aplikační vrstvě
- Řeší některé nevýhody integrace na datové vrstvě:
	- Problém zásahu do cizích systémů
	- Možné poškození integrity dat
	- Nevhodné pro systémy pod SLA třetí strany
- Využívají hlavně `interface`
- **Technologie:**
	- RPC (Remote Procedure Call)
	- RMI (Remote Method Invocation)
	- Web Services
	- Konektory, middleware
	- SOA (Service Oriented Architecture)
		- ![[Pasted image 20260510162421.png]]
### Service Oriented Architecture
- **Business drivery:**
	- Globalizace
	- E-Business
	- Připravenost na změnu
	- Ekonomické faktory
- SOA => úspora 30% - 40% ale ne hned
- ![[Pasted image 20260510164503.png]]
- **Smysl:**
	- Umožnění podnikům flexibilně a rychle reagovat na změnu
	- IT-Business alignment
- ![[Pasted image 20260510164731.png]]
#### Implementace - zespoda
1. Vytvoření WE
2. Propojení WS s funkcemi byznysu
3. Transformace byznysu
4. On-demand transformace
#### Implementace - shora
1. Navrhnutí byznys procesů
2. Transformace stávajících aplikací na služby
3. Integrace služeb s byznysem
## Enterprise Service Bus (ESB)
- Sjednocení komunikace mezi klienty a službami
- ![[Pasted image 20260510165127.png]]
- **Princip:**
	- Virtuální Peer-to-peer síť
## Service Integration Maturity Model (SIMM)
- ![[Pasted image 20260510165331.png]]
# 10. IT jako služba (XaaS), řízení IT formou ITSM a základy ITIL. Výběr a nákup řešení (vč. související legislativy), outsourcing.
## IT jako služba (XaaS)
- **Cloud** = 
	1. Samoobsluha na vyžádání
	2. Široký síťový přístup
	3. Sdílení zdrojů
	4. Rychlá elisticita
	5. Měřená služba
- ![[Pasted image 20260508144440.png]]
- ![[Pasted image 20260508142841.png]]
- 
- Nejznámější cloudy:
	- SaaS
	- PaaS
	- Soc. sítě
- Většinou freemium model
- Vysoká spolehlivost
- **Public cloud** = veřejná služba
- **Private cloude** = datacentrum, virtualizace
- Zjednodušuje používání různých služeb
- Outsourcing
- Odbornící budují velká datová centra
- Vysoká dostupnost dat
- Elasticita
- Celková dostupnost služeb
- Jenom pár velkých hráčů to může vyvíjet
- Vendor lock-in
- Adopce cloudu bude *"workload driven"*
	- ![[Pasted image 20260508145457.png]]
### Cloud vs. hosting
- ![[Pasted image 20260508143914.png]]
- Cloud => pay as you go
- ![[Pasted image 20260508145032.png]]
### Výhody cloudu
- Není počáteční investice
- Elasticita výkonu prostředí
- Vyšší spolehlivost
- Nestarání se o HW, licence, podpory
- ![[Pasted image 20260508145253.png]]
### Nevýhody cloudu
- Násobně vyšší cena
- 100% závislost na internetovém připojení
- Veškerá data mimo firmu a její kontrolu
- Vendor lock-in
- Nepredikovatelný vývoj cen
### Výhody nákupu vlastního serveru
- Nižší náklady
- Kontrola nad serverem a daty
- Jasné náklady
### Nevýhody nákupu vlastního serveru
- Nutnost starat se o HW, SW, ...
- Nutnost řešit vysokou dostupnost a zálohování
- Omezené možnosti skokového navýšení kapacity
### Migrace do cloudu
- Někdy stačí pouze převést data do cloudu
- Pro maximalizaci využítí je ideální kompletní migrace celých aplikací
### Typy cloudů
- ![[Pasted image 20260508145321.png]]
### Rizika cloudu
- Vendor lock-in
- Dostupnost konektivity
- Ochrana dat
- Legislativa
- Ukončení služeb
- Změna obchodního modelu
## Řízení IT formou ITSM a základy ITIL.
- **ITSM** = IT Service Management
	- Strukturovaný přístup k plánování, poskytování, provozu a řízení IT služeb
	- Na rozdíl od tradičního zaměření na HW a SW se zaměřuje na celkový přínos IT služeb
	- Obecný koncept
	- ![[EITM - Teorie 2026-05-09 17.48.58.excalidraw]]
- ![[Pasted image 20260509175417.png]]
### ITIL
- = **Information Technlogy Infrastructure Library**
- **Proč?**
	- IT organizace stráví hodně času těmito aktivitami:
		1. Zotavení po chybách (*incidents*), která naruší práci uživatelů
		2. Modifikací/výměnou IT komponent k zlepšení spolehlivosti nebo funkcionality eliminováním problémů (*issues, problems, errors*) spojených s těmito komponentami
		3. Přidáváním/modifikací/ubíráním (*changes*) IT komponent s cílem přidat novou nebo vylepšenou funkcionalitu
	- Počet *incidents, issues, problems, errors, changes* řešených IT přesahuje IT kapacitu
	- IT potřebuje způsob jak prioritizovat
	- Prioritizace musí přinášet co největší benefity pro organizaci
	- Umožňuje interpretaci technických činností do jazyka byznysu
- **Jak?**
	- Využití ITSM
	- Poskytnutí IT a zákazníkům schopnosti:
		1. Definice IT dodávek jako IT služby, které jsou popsány zákaznickým a uživatelským jazykem
		2. Definice jak budou IT služby dodávány uživatelům
		3. Pochopení dopadu na byznys pokud IT Služba selže
		4. Prioritizace IT aktivit podle dopadu
- **Zahrnuje:**
	- Knihovnu
	- Oblast vzdělávání a certifikace odbornosti
	- Oblast poskytování konzultačních služeb
	- Oblast vývoje a implementace SW nástrojů pro podporu procesů ITSM
	- Mezinárodní platformu profesionálů a odborné veřejnosti
- **Charakteristické rysy:**
	- Procesní řízení
	- Zákaznicky orientovaný přístup
	- Jednoznačná terminologie
	- Nazávislost na platformě
	- Public Domain
- **Charakteristika:**
	- Rozsáhlý, konzistentní a procesně orientovaný rámec pro oblast ITSM
	- Založený na ITSM best practices
	- De-facto mezinárodní standard pro ITSM
- **Důvody pro implementaci:**
	- Udržování kroku s vývojem technologií
	- Dodržování obchodních požadavků a požadavků uživatelů
	- Řízení nákladů, rozpočtů a zdrojů
- **Obsah:**
	- **Vydefinování procesů pro zajištění ITSM:**
		- Stanovení cílů, vstupů a výstupů a aktivit každého procesu
		- Stanové rolí a jejich odpovědností
		- Způsob měření kvality poskytovaných IT služeb a účinnosti ITSM procesů
		- Vzájemné vazby mezi procesy
		- Postupy auditu a zásady reportingu pro každý proces
	- **Zásady pro implementaci procesů ITSM:**
		- Přínosy každého procesu
		- Critical Success Factors
		- Náklady na implementaci a následný provoz
		- Zásady pro řízení podpůrné ICT infra.
		- Zásady bezpečnosti ICT infra.
- **Neřeší:**
	- Konkrétní podobu organizační struktury
	- Způsob obsazení rolí konkrétními pracovními pozicemi
	- Podobu a obsah pracovních procedur
	- Projektovou metodiku implementace ITSM (doporučuje PRINCE2)
#### Procesy
##### Operativní
- **Vazby:**
	- ![[Pasted image 20260509183716.png]]
- **Service Desk** – *"Single Point of Contact"* pro uživatele a zákazníky
- **Configuration Management** – podpora ostatních procesů poskytováním věrohodných iformací o konfiguračních položkách infrastruktury
	- **CMDB** = Configuration Management Database
- **Incident Management** – co nejrychlejší obnovení normálního provozu služby s minimalizací důsledků výpadku služby na provoz
- **Problem Management** – zabránění opakování incidentů souvisejících s poruchami
- **Change Management** – zajistit hladkou a nákladově efektivní implementaci pouze schválených změn
- **Release Management** – zajistit hladký a kontrolovaný průběh nasazení do produkce
##### Taktické
- **Vazby:**
	- ![[Pasted image 20260509184211.png]]
- **Service Level Management** – udržování a zlepšování kvality IT služeb
- **Capacity Management** – zajištění nákladově optimální kapacity ICT infra., která bude odpovídat současným i budoucím potřebám
- **Availability Management** – zajištění nákladově optimální dostupnosti IT služeb
- **IT Service Continuity Management** – zajištění funkčnosti ICT infra. po vážném a rozsáhlem výpadku
- **Financial Management for IT Services** – poskytování náklodově efektivní správcovství ICT majetku a zdrojů používaných při poskytování IT služeb
### Service Value System
- ![[Pasted image 20260509184613.png]]
### Service Value Chain
- ![[Pasted image 20260509184632.png]]
### SVS a SVC
#### 1. Systém hodnot služeb (Service Value System - SVS)
- SVS je **makropohled**. Je to celý ekosystém tvé firmy. Popisuje, jak všechny složky organizace spolupracují, aby proměnily příležitost/poptávku na začátku v reálnou hodnotu na konci.
- Pokud do systému vlevo vstoupí **Poptávka (Demand)** (zákazníkovi je zima), SVS zajistí, že vpravo vypadne **Hodnota (Value)** (zákazník má doma teplo). SVS se skládá z 5 prvků:
	- **Zásady (Guiding Principles):** Kultura tvé firmy. Například _„Zaměřte se na hodnotu“_ (Focus on value) – řidič nesype uhlí do bláta před domem, ale úhledně ho složí, protože ví, že hodnota pro babičku je čistý dvůr. _„Udržujte to jednoduché“_ (Keep it simple) – objednání uhlí zabere jeden telefonát.
	- **Správa (Governance):** Pravidla a legislativa. Hlídáš emisní limity náklaďáků, certifikaci ekologického paliva a finanční audit.
	- **Praktiky (Practices):** Tvoje nástroje a schopnosti. Správa majetku (údržba náklaďáků), správa incidentů (co když píchne guma?), nebo řízení vztahů se zákazníky (CRM systém s adresami babiček).
	- **Neustálé zlepšování (Continual Improvement):** Přechod na efektivnější náklaďáky nebo zavedení GPS sledování tras pro úsporu nafty.
	- **Řetězec hodnot služeb (Service Value Chain - SVC):** Samotné provozní srdce systému. Operační model, který si rozebereme hned teď.
#### 2. Řetězec hodnot služeb (Service Value Chain - SVC)
- SVC je **mikropohled**. Je to konkrétních 6 provozních činností uvnitř SVS, kterými musí projít každá jedna objednávka uhlí, aby byla úspěšně doručena.
- Když babička zavolá, že chce 2 tuny ořechu, tvoje SVC se roztočí v těchto krocích:
	1. **Zapojit (Engage):** Operátorka na lince zvedne telefon, vyslechne babičku, zapíše objednávku a domluví termín závozu. (Komunikace s vnějším světem).
	2. **Plánovat (Plan):** Vedoucí dopravy se podívá na příští týden a naplánuje optimální vytížení náklaďáků. (Strategické rozvržení zdrojů).
	3. **Navrhovat a transformovat (Design and Transition):** Zjistí se, že babička má úzkou bránu. Firma musí rozhodnout, že tam nepošle obří Tatru, ale malou multikáru, a připraví pro řidiče instrukce. (Přizpůsobení služby realitě).
	4. **Získat / vybudovat (Obtain / Build):** Na skladě se nastartuje nakladač a fyzicky nabere 2 tuny uhlí z velké hromady a nasype je na korbu multikáry. (Zajištění komponent služby).
	5. **Dodat a podporovat (Deliver and Support):** Řidič doveze uhlí k babičce, složí ho pásem přímo do sklepa, předá fakturu. Druhý den jí operátorka zavolá, jestli bylo vše v pořádku. (Samotné doručení hodnoty).
	6. **Zlepšovat (Improve):** Řidič nahlásí: „Ten pás na multikáře už vrže, musíme ho promazat.“ (Zpětná vazba pro další jízdy).
### Role
- Role jsou seskupeny podle Service Lifecycle stage
- **Service Strategy**
	- Demand Manager – porozumění požadavků zákazníka
	- Financial Manager – správa rozpočtu
- **Service Design**
	- Applications Analyst – návrh, testování a provoz služeb
	- Information Security Manager – zabezpečení dat a služeb
- **Service Transition**
	- Application Developer – tvorba a údržba služeb
	- Project Manager – plánování projektu
- **Service Operation**
	- 1st Level Support – řešení obecně známých problémů, nebo reportování problémů Levelu 2 (call centrum)
	- 2nd Level Support – řešení problémů nahlášených Levelem 1 (programátoři, admini)
	- 3rd Level Support – podpora od dodavatelů třetích stran
- **Continual Service Improvement**
	- Process Architect – zajišťuje správu procesů, tzn. to zda správně kooperují, jsou efektivní apod.
	- Process Owner – zajišťuje, že proces dělá to co má
## Výběr a nákup řešení
- **Obchodní parametry dodávky:**
	- Cena
	- Velikost
	- Čas
	- Vhodnost řešení
	- Kvalita dodávky
	- Reputace dodavatele
- **Obchodní prostor:**
	- ![[EITM - Teorie 2026-05-07 19.10.45.excalidraw]]
	- Zlepšení jednoho parametru obvykle znamená ústupek jinde
- **Rámcový proces výběru a nákupu:**
	1. Latentní potřeba
	2. Potřeba
	3. Studie proveditelnosti, analýza
	4. Vize řešení
	5. Požadavky na řešení
	6. RFI – Request For Information
	7. RFP – Request For Proposal
	8. Výběr
	9. RFQ – Request For Quote – cenová nabídka
	10. Podpis smlouvy
### Studie proveditelnosti
- **Zabývá se:**
	- Současným stavem
	- Seznam, analýza požadavků
	- Možné přístupy řešení
	- Popis variant
	- Analýza a mitigace rizik
	- Odhad nákladů a přínosů
	- PoT = Proof of Technology
		- Ověření kompatibility, bezpečnosti a výkonu
		- Bude technologie fungovat v našem podniku?
	- PoC = Proof of Concept
		- Ověření zda je možné řešení implemenovat
#### Rizika
- Ppst.
- Závažnost
- Dopad
- Mitigace
- Matice rizik:
	- ![[Pasted image 20260507192006.png]]
#### Hodnocení nabídek
- Metodický přístup
- Kritéria, škály hodnot
- Výpočet celkového hodnocení
- Tvrdá a měkká kritéria
#### Reference
- Zdroje informací:
	- Dodavatel
	- Komunita
	- Web
- Věrohodnost zdrojů
#### Obecná struktura
1. Obsah
2. Historie změn
3. Úvod
4. Účel
5. Rozsah
6. Reference
7. Executive summary
8. \[podrobná část]
9. Shrnutí – závěr
10. Přílohy
#### PoT
- Technologické nebo produktové demo
- Ukázka funkčnosti řešení
- Ověření pro dané prostředí
- Generická data
- Připraveno dodavatelem
- Obvykle zdarma
#### PoC
- Ověření vhodnosti řešení pro konkrétního zákazníka
- Ověření předpokladů TCO, ROI
- Identifikace problémových míst a rizik
- Reálná data
- Obvykle placené
### Obchodní dokumenty
- **Case Study**
	- Marketingový materiál
	- Obvykle na konkrétního zákazníka
- **Reference**
	- Slepá reference = neurčen zákazník *"významný telco operátor ČR"*
	- Zákaznická reference = vyjmenovaný zákazník
	- V zákoně o VZ nazýváno *"zakázka obdobného rozsahu"*
- **Certifikace**
	- Produktové
	- Obchodní
	- Sektorové
	- Certifikované řešení
	- Oborová certifikace – ISO
### Request For Information – RFI
- Zadavatel hledá řešení
- Často předchází RFP
- Odpovědí může být studie proveditelnosti
- Ceny pouze orientačně
- **Struktura:**
	- Zadavatel
	- Hormonogram procesu RFI, RFP
	- Definice problému
	- Rámcové požadavky
	- Cenová představa
	- Kritéria výběru
	- Harmonogram realizace
	- Požadavky na uchazeče
	- Struktura odpovědi
### Request For Proposal – RFP
- Žádost o kompletní nabídku
- Zadavatel chce realizovat nákup
- **Struktura:**
	- Zadavatel
	- Kontakty pro dotazy
	- Harmonogram procesu
	- Zadávací dokumentace
	- Požadavky na uchazeče
	- Požadavky na nabídku
#### Příklad nabídky na RFP
- Identifikace nabídky
- Disclaimer
- Kontakty na dodavatele
- Informace o dodovateli
- Manažerské shrnutí
- Popis (variant) řešení
- Diskuse (splnění) požadavků zadavatele
- Zkušenost dodavatele, reference
- Navrhovaný harmonogram realizace
### Zákon o veřejných zakázkách (ZVZ)
- Zákon 134/2016
- Definuje:
	- Postupy při zadání VZ
	- Soutěž o návrh
	- Veškeré dokumenty jsou veřejné
	- Zákaz diskriminace
- **Zásady zadávání VZ:**
	- Transparentnost, přiměřenost
	- Rovné zacházení s dodavateli a zákaz diskriminace
	- Zákaz omezení přístupu dodavatelů z EU
	- Sociálně, enviromentálně odpovědné zadávání
- **Veřejní zadavatelé:**
	- ČR
	- ČNB
	- Statní příspěvková organizace
	- Územní samosprávný prvek
	- Jiná právnická osoba
	- Centrální zadavetel
- **Druhy:**
	- Na dodávky
	- Na služby
	- Na stavební práce
- **Nadlimitní a podlimitní zakázky:**
	- Nadlimitní – stanoveno zvláštním předpisem
	- Podlimitní – mezi nadlimitní a malého rozsahz
	- Malého rozsahu
		- 2 000 000 Kč s DPH na služby
		- 6 000 000 Kč s DPH na stavby
	- Významné zakázky nad 300 mil. (schvaluje vláda) nebo 50 mil (schvaluje zastupitelstvo samosprávy)
- **Druhy řízení:**
	- **Zjednodušené podlimitní řízení**
		- Výzva musí obsahovat:
			1. Identifikační údaje veřejného zadavatele
			2. Informaci o druhu a předmětu veřejné zakázky
			3. Zadávací dokumentaci nebo podmínky přístupu či poskytnutí zadávací dokumentace podle § 48
			4. Lhůtu a místo pro podání nabídek 
			5. Požadavky na prokázání splnění kvalifikace podle § 62
			6. Údaje o hodnotících kritériích podle § 78, pokud nejsou uveden v zadávací dokumentaci
	- Otevřené řízení
	- Užší řízení
	- Jednací řízení s uveřejněním
	- Jednací rízení bez uveřejnění
	- Řízení se soutěžním dialogem
	- Řízení o inovačním partnerství
	- Koncesní řízení
	- Řízení pro zadání veřejné zakázky ve zjednodušeném režimu
- **Zadávací dokumentace:**
	- Obchodní podmínky
	- Platební podmínky
	- Objektivní podmínky, za níchž lze překročit výši nabídkové ceny
	- Technické podmínky
	- Požadavky na varianty nabídek
	- Požadavek na způsob zpracování nabídkové ceny
	- Podmínky a požadavky na zpracování nabídky
	- Způsob hodnocení nabídek podle hodnotícíh kritérií a jiné požadavky zadavatele na plnění veřejné zakázky
- **Základní způsobilosti § 74**
	- Nebyl odsouzen
	- Není v likvidaci
	- Nemá daňové nedoplatky
- **Profesní způsobilosti § 77**
	- Výpis z obchodního rejstříku
	- Doklad o oprávnění k podnikání dle zvláštních předpisů
	- Doklad o členství v komoře
	- Doklad o odborné způsobilosti
- **Ekonomická kvalifikace § 78**
	- Pojistná smlouva
	- Poslední rozvaha
	- Údaj o celkovém obratu
- **Technická kvalifikace § 79**
	- Seznam významných dodávek za poslední 3 roky s uvedním rozsahu a doby plnění
	- Seznam techniků nebo technických útvarů
	- Popis technického vybavení
	- Provedení kontroly výrobních zařízení
	- Vzorky
	- Doklady o shodě
- **Hodnotící kritéria:**
	- Pouze jedno – ekonomická výhodnost nabídky
	- Seznam dílčích kritérií
	- Relativní váha
	- Způsob výpočtu
- **Doručení nabídky:**
	- *"NEOTVÍRAT"*
	- Krycí list – uchazeč, cena
	- Komisní způsob
	- Veřejné, možnost účastí dodavatelů
	- Zápis o poddaných nabídkách a cenách