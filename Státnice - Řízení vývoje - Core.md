# 1. Softwarový proces a jeho složky. Modely životního cyklu software, jejich vlastnosti. Iterativní vývoj software - prvky, postupy, fáze, varianty podle míry iterativnosti.
## Softwarový proces a jeho složky.
- **Proces** = sled činností převádějící vstupy na výstupy
- **SW proces** = sada nástrojů a technik pro vývoj, nasazení a údržbu SW
- **Složky:**
	- Role (developer, tester, manažer)
	- Artefakty (kód, dokumentace, logy)
	- Aktivity (vývoj, testování, nasazování)
- **Rozdělení:**
	- Řídící (organizace projektů uvnitř org.)
	- Hlavní (vedou k cíli SW projektu)
	- Podpůrné (podporují hlavní procesy)
## Modely životního cyklu software, jejich vlastnosti.
- **Dimenze:** Cyclicity, Rigidity, Ceremony
	- ![[Pasted image 20250603215840.png]]
- **Sekvenční:**
	- Waterfall
		- ![[Pasted image 20250603220207.png]]
	- V-Model
		- ![[Pasted image 20250603220253.png]]
- **Iterativní:**
	- Spirálový model
		- ![[Pasted image 20260611213511.png]]
	- RUP
		- ![[Pasted image 20250603220545.png]]
	- **Adaptivní:**
		- eXtreme Programming
		- SCRUM
			- ![[Pasted image 20250603221220.png]]
			- Stand Up
			- Scrum Master = zajišťuje dodržován SCRUM
			- Product Owner = maximalizace byznys hodnoty
			- Backlog, Product Backlog
			- Grooming
## Iterativní vývoj software - prvky, postupy, fáze, varianty podle míry iterativnosti.
- **Prvky:**
	- Iterace
	- Inkrement
	- Produktový backlog
- **Postupy:**
	- Rozdělení velkých projektů na malé
	- Retrospektivy
	- Grooming
	- Plánování iterací
	- Stand Ups
- **Fáze:**
	- Inception
	- Elaboration
	- Construction
	- Transition
- **Milníky:**
	- LCO – Life Cycle Objectives
	- LCA – Life Cycle Architecture
	- IOC – Initial Operational Capability
	- GA/REL – General Availability / Release
- **Varianty:**
	- **SCRUM**
		- **Role:** Team, PO, SM
		- **Ceremonie:** Sprint Planning, Daily SU, Sprint Review, Sprint Retro
		- **Artefakty:** Product Backlog, Spring Backlog, Sprint Goal
	- **XP**
# 2. Plánování a řízení softwarového projektu. Definování projektu, logický rámec a projektová charta projektu, zúčastněné osoby. Plán rozsahu projektu, odhadování pracnosti, časový plán a související metody, plán zdrojů a nákladů. Sledování a úpravy postupu projektu.
## Plánování a řízení softwarového projektu.
- **Projektový management** = aplikování znalostí, dovedností, nástrojů a technik během projektových aktivit s cílem dosáhnout požadovaných cílů
- **Proces** = známá opakovatelná činnost
- **Program** = více projektů
- **Projektový trojimperativ:**
	- ![[Pasted image 20260607182152.png]]
- **Řízení:**
	- Rozsahu
		- WBS
		- Funkční, nefunkční, změnové, glossary
		- MOSCOW
	- Času
		- Gantt
		- Kritická cesta
		- Precedence Diagramming Method (Finish-to-start)
	- Nákladů
		- TCO
		- Tangible, intangible, přímé, nepřímé, sunk
	- Kvalita
		- Six Sigma
		- DMAIC
	- Lidí
		- Vnitřní motivace
		- Vnější motivace
		- Belbin
	- Komunikace
		- Decentralizovaná, centralizovaná, hub and spoke, multiple hub and spoke, holistic
	- Obstarávání
		- Make or Buy
	- Rizik
		- Matice rizik
		- Mitigace rizik
	- Integrace
		- Projektová charta
		- Business Case
		- Change Control
## Definování projektu, logický rámec a projektová charta projektu, zúčastněné osoby.
- **Projekt** = dočasné úsilí s cílem vytvořit unikátní produkt
- **Cíl projektu** = stav, do kterého se chceme realizováním projektu dostat
	- Cíl = věcný + termínový + nákladový
	- **SMART** = Specific, Measurable, Assignable, Realistic, Timebound
- **Logický rámec** = základní přehledný pohled na projekt
	- Tvorba využívá brainstorming
	- ![[Pasted image 20250517110037.png]]
- **Projektová charta** = zakládací listina projektu symbolizující formální rozhodnutí projekt realizovat
- **Stakeholders** = zainteresovaná osoba
	- Vnitřní, vnější
	- ![[EITM - Teorie 2026-05-06 16.54.40.excalidraw|500x300]]
## Plán rozsahu projektu, odhadování pracnosti, časový plán a související metody, plán zdrojů a nákladů.
- **Product Scope** = co přesně musí produkt splňovat
- **Project Scope** = práce, která musí být v projektu vykonána
- **Fáze scope managementu**
	1. Plánování řízení rozsahu
	2. Sběr požadavků
	3. Definování rozsahu
	4. Vytváření WBS
	5. Ověřování rozsahu
	6. Řízení změn rozsahu
- Požadavky
- MoSCoW
- **Odhadování pracnosti:**
	- Kritická cesta
	- Ganttovy diagramy
	- Expertní odhad
	- Tříbodový odhad
- **Plánování zdrojů a kapacit**
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
- **Plánování nákladů**
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
	1. Create
	2. Build
	3. Form
	4. Enlist
	5. Enable
	6. Generate
	7. Sustain
	8. Institute
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
- ![[Pasted image 20250517141615.png]]
- **Ošetření rizik technikou 4T**
	- Tolerate = přijetí rizika, pokud je jeho dopad a ppst. v rozumných mezí
	- Terminate = úplné odstranění rizika tím, že se zastaví činnost, který riziko nese
	- Treat = přijití opatření ke snížení nebo kontrole dopadů
	- Transfer = přenést rizika na třetí stranu
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
- **EVM:**
	- ![[Pasted image 20260607192343.png]]
	- Technika hodnotící výkon a pokrok projektu z hlediska rozsahu, harmonogramu a zdrojů
	- **Základní vstupy:**
		- **Planned Values (PV)** = plánovaná hodnota
		- **Actual Costs (AC)** = vyčerpané prostředky
		- **Earned Value (EV)** = skutečně dosažená hodnota
		- **Cost Performance Index (CPI)** = zobrazuje nákladovou účinnost prováděné práce
			- $\text{CPI} = \frac{\text{EV}}{\text{AC}}$
				- Hodnota vyšší jak 1 => úspory
				- Hodnota nižší jak 1 => zdržení projektu
		- **Scheduled Performance Index (SPI)** = zobrazuje výkonnost prováděné práce v čase a dodržení harmonogramu
			- $\text{SPI} = \frac{\text{EV}}{\text{PV}}$
				- Hodnota vyšší jak 1 => jsme napřed
				- Hodnota nižší jak 1 => zdržení
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
- **Formální náležitosti a vlastnosti dokumentu**
	- Název dokumenty a ID
	- Datum vzniku a datum poslední aktualizace
	- Identifikace tvůrce
	- Seznam změn
	- Platnost a status dokumentu
## Multiprojektové řízení, projektová kancelář.
- **PPM** = Projet Portfolio Management
- Projekty jsou realizované v kontextu organizace
- Project Management musí vzít v úvahu celkovou situaci v organizaci
- ![[Pasted image 20260507205010.png]]
- **Organizační rámce:**
	- **Strukturální rámec** – role a odpovědnosti
		- **Základní organizační struktury:**
			- ![[Pasted image 20260507204358.png]]
	- **Rámec lidských zdrojů** – harmonie potřeb
	- **Politický rámec** – orgnaizace je koalice různých lidí
	- **Symbolický rámec** – kultura org.
- **Projektová kancelář**
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
- **Metody získávání požadavků:**
	- **Interaktivní** – rozhovory, spolupráce s uživateli
		- **On-site customer** = oborový expert
		- **Strukturovaný rozhovor** = připravené otázky
		- **Requirements workshop** = setkání se za účelem sběru a upřesnění požadavků
			1. Příprava
			2. Brainstorming
			3. Zápis
	- **Neinteraktivní** – studování dokumentace, hlášení problémů, konkurence
- **Analýza specifikace:**
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
	- **Business case** = ověření přínosů a návratnosti
	- **Technický koncept** = ověření proveditelnosti, varianty architektury, technologie, pipeline, prostředí, nasazení
	- **Způsob realizace** => greenfield, brownfield, prototyp
	- **MVP (Minimum Viable Product)** = nejmenší možná funkcionality, která jde nasadit a šlo sbírat zpětnou vazbu
	- **MMP (Minimum Marketable Product)** = nejmenší možná funkcionalita, která je užitečná pro zákazníka (přináší mu benefit)
## Související nástroje a modely.
- **UseCase Diagramy**
	- = sekvence akcí, které se systémem provádí uživatel a vedou k požadovaným výsledkům
	- **Hlavní části:**
		1. Standardní průběh
		2. Vstupní a výstupní podmínky
		3. Chybové stavy
- **User Story**
	- = co uživatel chce a proč
	- **As a ... I want to ... so that**
	- Obsahuje
		- Název
		- Prioritu
		- Typ
		- Popis
		- Akceptační kritéria
# 5. Definice a význam architektury software, složky architektury. Vztah architektury k požadavkům, kvalitativním charakteristikám software a postupu vývoje produktu.
## Definice a význam architektury software, složky architektury.
- **Architektura** = sada klíčových návrhových rozhodnutí o systému
- **Preskriptivní architektura** = architektura před implementací systému (as-intended)
- **Deskriptivní architektura** = architektura po implementaci systému (as-implemented)
- **Degradace architektury** = deskriptivní architektura se liší od preskriptivní
	- **Drift** = neúmyslné odchýlení se od preskriptivní architektury
	- **Eroze** = úmyslné odchýlení se od preskriptivní architektury
- **Komponenty** = prvky, které zapouzdřují zpracovávání (processing) a data
- **Konektory (connectors)** = prvky, které zajišťují interakce mezi komponentami
- **Konfigurace** = množina konkrétních asociací mezi komponentami a konektory
- **C4 Model:** Context, Container, Component, Code
## Vztah architektury k požadavkům, kvalitativním charakteristikám software a postupu vývoje produktu.
- Je to vztah vůči nefunkčním požadavkům
- **Nefunkční požadavek** = omezení na systém, které ovlivňuje jeho implementaci a dodání (škálovatelnost, komplexita, ...)
- CASED – Complexity, Adaptability, Scalability, Efficiency, Dependability
# 6. Činnosti při konstrukci produktu. Druhy a techniky testování, souvislost testování a jiných disciplín, automatizace. Konfigurační řízení a řízení změn, související postupy vč. CI/CD, vzory a nástroje. Specifika vývoje s použitím AI.
## Činnosti při konstrukci produktu.
- **Cíl:** splnit milník IOC
- **Designerské činnosti:**
	- Detailní návrh modulů a tříd
	- Návrh algoritmů a datových struktur
	- Návrh DB schémat
	- Příprava specifikací pro programátory
- **Programátorské činnosti:**
	- Implementace
	- Refaktorizace
	- Jednotkové testování
	- Integrace komponent
- **Testování a ověřování:**
	- Integrační testování
	- Systémové testování
	- Regresní testování
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
- **Konfigurační řízení:**
	- **Konfigurace** = z jakých prvků je systém poskládán
	- **SW konfigurace** = sestava prvků reprezentující určitou podobu systému
	- **Konzistentní konfigurace** = konfigurace, jejíž prvky jsou bezrozporné
	- **Úlohy SCM:**
		- ![[SCM.excalidraw]]
	- **Semver**
- **Řízení změn:**
	- **Proces správy změn:**
		- ![[proces-zmeny.excalidraw]]
		- **Change Control Manager** = člověk, který posuzuje kdy a proč přijmout požadavek a jestli je dokončen
		- **Change Control Board** = více CCM
	- **Tiket** = požadavek na změnu
		- **Obsahuje:** shrnutí, metadata, popis, konfigurace systému a SW, screenshot, vzorek dat, log, závažnost
		- **Stavy:** Verified => Resolved => Closed
- **Související postupy vč. CI/CD, vzory a nástroje**
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
- **Cíl:** dosažení milníku GA/REL
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
- ![[Pasted image 20250528223243.png]]
- **Druhy deployment prostředí:**
	- Dev
	- Testing
	- Staging
	- Prod
- **SW deployment** = instalace a nastavení SW na cílovém systému
- **SW provisioning** = kroky provádění před deploy
- **Strategie nasazování:**
	- Recreate
	- Blue-green
	- Canary
	- Rolling update
- **Řešení defektů a změn**
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
	- **Procesní** – charakteristiky postupu a organizace
- **Goal-Question-Metric (GQM):**
	- **Goal:** Co chceme zlepšit nebo dosáhnout?
	- **Question:** Jak poznáme, že jsme cíle dosáhli?
	- **Metric:** Co konkrétně změříme?
## Etika a profesionalita v sw inženýrství.
- Základním pilířem je **ACM/IEEE The Software Engineering Code of Ethics and Professional Practice**
	- **8 principů**:
		1. **Veřejný zájem** – SW inženýři musejí jednat v souladu s veřejným zájmem
		2. **Klient a zaměstnavatel** – jednat v jejich nejlepším zájmu
		3. **Produkt** – zajišťovat aby produkty splňovaly nejvyšší profesionální standardy
		4. **Úsudek** – zachovávat si nezávislý a profesionální úsudek
		5. **Management** – manažeři musí podporovat etický přístup k řízení vývoje
		6. **Profese** – rozvíjet integritu a pověst profese SW inženýrství
		7. **Kolegové** – být spravedlivý a ohleduplný ke svým kolegům
		8. **Sám sebe** – neustále se celoživotně vzdělávat
# 9. Role IT v organizaci, IT strategie a governance, základy COBIT. Enterprise architecture (EA), integrace systémů.
## Role IT v organizaci, IT strategie a governance, základy COBIT.
- **Role IT v org.**
	1. IT jako *strojovna*
	2. Poskytovatel služeb
	3. Součást byznysu
	4. Každý své IT
- **IT strategie** – zaměřena na technologie
	- **Vize** = ideální budoucí stav, kterého chce organizace dlouhodobě dosáhnout (*Kde chceme být?*)
	- **Záměr** = hlavní důvod existence organizace a smysl její současné činnosti (*Proč tu jsme a co děláme dnes?*)
	- **Cíl** = konkrétní, měřitelný a termínovaný milník, který musíme splnit, abychom naplnili vizi (*Co přesně a dokdy musíme dokázat?*)
		- ![[Pasted image 20260506142454.png]]
	- **Strategie** = plán a způsob rozložení sil a zdrojů k dosažení cílů
		- ![[EITM - Teorie 2026-05-06 13.59.24.excalidraw]]
	- **Taktika** = krátkodobý manévr nebo specifické akce v rámci dané strategie
	- **Pyramida strategického řízení:**
		- ![[Pasted image 20260506141011.png]]
	- **Integrovaný model procesu strategického řízení**
		- ![[EITM - Teorie 2026-05-06 15.41.44.excalidraw|600x300]]
	- **Analýza vnějšího prostředí:**
		- ![[EITM - Teorie 2026-05-06 16.10.41.excalidraw|500x300]]
		- STEP
	- **Analýza vnitřního prostředí:**
		- Matice BCG
			- ![[Pasted image 20260506163901.png]]
	- **Analýza zájmových skupin:** 
		- ![[EITM - Teorie 2026-05-06 16.54.40.excalidraw|500x300]]
- **IT Governance, COBIT**
	- **IT Governance** = soubor pravidel, vztahů a procesů, které pomáhají řídit organizaci tak, aby IT v maximální míře podporovala její strategické cíle
	- ![[Pasted image 20260509195522.png]]
	- **COBIT**
		- = Control Objectives for Information and Related Technologies
		- **COBIT Evoluce:**
			- ![[Pasted image 20260509201732.png]]
		- **Domény:**
			- Plan and Organize
			- Acquire and Implement
			- Deliver and Support
			- Monitor and Evaluate
		- **Principy COBIT:**
			1. Uspokojování potřeb stakehodlerů
			2. Oddělení mng. a gov.
			3. Jeden integrovaný framework
			4. Holistický přístup
			5. End-to-end pokrytí
		- ![[Pasted image 20260612215230.png]]
## Enterprise architecture (EA), integrace systémů.
- **EA** = modelování vztahu mezi organizací, byznysem a IT; koncepčně řízený rozvoj tohoto vztahu
- **Úrovně EA:**
	- ![[Pasted image 20260509191107.png]]
- **Enterprise Lifecycle**
	- ![[Pasted image 20260612215408.png]]
- **Integrace:**
	- Na datové vrstvě (ETL)
	- Na aplikační vrs
# 10. IT jako služba (XaaS), řízení IT formou ITSM a základy ITIL. Výběr a nákup řešení (vč. související legislativy), outsourcing.
## IT jako služba (XaaS), řízení IT formou ITSM a základy ITIL.
- **Cloud** = 
	1. Samoobsluha na vyžádání
	2. Široký síťový přístup
	3. Sdílení zdrojů
	4. Rychlá elisticita
	5. Měřená služba
- ![[Pasted image 20260508144440.png]]

- **ITSM** = IT Service Management
	- Strukturovaný přístup k plánování, poskytování, provozu a řízení IT služeb
- **ITIL** = Information Technlogy Infrastructure Library
	- Implementace ITSM
	- **Zahrnuje:**
		- Knihovnu
		- Oblast vzdělávání a certifikace odbornosti
		- Oblast poskytování konzultačních služeb
		- Oblast vývoje a implementace SW nástrojů pro podporu procesů ITSM
		- Mezinárodní platformu profesionálů a odborné veřejnosti
	- **Procesy:**
		- Operativní
			- ![[Pasted image 20260509183716.png]]
		- Taktické
			- ![[Pasted image 20260509184211.png]]
## Výběr a nákup řešení (vč. související legislativy), outsourcing.
- **Obchodní parametry dodávky:**
	- Cena
	- Velikost
	- Čas
	- Vhodnost řešení
	- Kvalita dodávky
	- Reputace dodavatele
- **Obchodní prostor:**
	- ![[EITM - Teorie 2026-05-07 19.10.45.excalidraw]]
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
- POT, POC
- Case Study
- Request For Information – odpověď Studie proveditelnost
- Request For Proposal – odpověď Nabídka
- **ZVZ:**
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
- **Outsourcing** = postoupení odpovědnosti za vybrané IT činnosti, procesy nebo celou infrastrukturu externímu poskytovateli služeb na základě dlouhodobé smlouvy
	- **Typy:**
		- Onshoring – stejná země
		- Nearshoring – blízký čas a kultura
		- Offshoring – vzdálená země
	- **Výhody:**
		- Snížení nákladů
		- Přístup k expertům
		- Škálovatelnost
		- SLA záruky
			- SLA = smlouva o poskytování služeb v dané kvalitě
	- **Nevýhody:**
		- Ztráta kontroly
		- Vendor Lock-in
		- Bezpečnostní rizika
		- Ztráta know-how
	- **Klíčové nástroje řízení:**
		- SLA
		- Service Catalogue – seznam všech služeb, které poskytovatel poskytuje
		- Governance – pravidelné schůzky a reporty