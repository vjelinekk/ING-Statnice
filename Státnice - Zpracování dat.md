# 1. Přehled a klasifikace databázových systémů a technologií pro správu a zpracování dat. Požadavky kladené na SŘBD a jeho vlastnosti. Konceptuální modelování, relační a jiné modely dat. Normální formy, aktivní databáze, principy transakčního zpracování, konzistence databáze.
## Přehled a klasifikace databázových systémů a technologií pro správu a zpracování dat.
- ![[Pasted image 20260531180703.png]]
### Podle počtu uživatelů
- **Single user DB** – DB běžící lokálně pro jednoho člověka (např. SQLite)
- **Multi user DB** – klasické produkční DB, kde tisíce uživatelů přistupují k datům naráz a server musí hlídat transakce
### Podle umístění
- **Centralizované** – všechna data a výpočetní výkon sedí na jednom serveru nebo clusteru
- **Distribuované** – DB je fyzicky rozprostřená na různých serverech po celém světě
- ![[Pasted image 20250524183118.png]]
### Podle datového modelu
- ![[Pasted image 20260531180728.png]]
- **Hierarchické a Síťové** – staré předrelační modely
- **Relační** – klasické SQL databáze
- **Objektově orientované** – z OO jazyků
	- **Myšlenka** – vezmeme celý objekt z paměti programu tak jak je a uložíme ho na disk
- **Semi-strukturální** – nemají tabulkové schéma ale strukturu nesou v sobě
	- Např.: JSON, XML databáze
- **Post relační** – objektově relační model
	- Používají se klasické SQL tabulky ale v jednom sloupci je možné ukládat složitější datové struktury
- **NoSQL** – velké technologická rodina obsahující několik podmodelů (tady by se dalo yappovat o tom samým jako v [[#3. Zpracování strukturovaných a nestrukturovaných dat. Nerelační/postrelační databáze – BASE vs. ACID, druhy a vlastnosti NoSQL databází. Data s více modely, multi-model databáze.| 3.]])
	1. Dokumentové
	2. Key-Value
	3. Sloupcové
	4. Grafové
### Podle typu použití (tady by se dalo yappovat o [[#4. Principy a nástroje Business Intelligence, vrstvy pro analýzu dat. Přístupy k vytváření datových skladů a datových tržišť. Architektura datového skladu, jeho implementace. | 4.]])
- **Operační DB (OLTP)** – provozní databáze
- **Analytické DB (OLAP)** – datové sklady, jezera, tržiště
### Podle typu dat
- **Časové** – drží historii změn v čase
- **Streamovací** – zpracování dat, které neustále tečou v real time
- **Prostorové** – geografické databáze chápající mapové souřadnice
- **Multimedia** – optimalizované pro ukládání a indexování audia, videa, ...
### Podle spotřeby zdrojů
- **Micro & Mobile DB** – ultraodlehčené DB navržené pro běh v zařízení s minimem RAM a slabým CPU
- **Real-Time DB** – systémy, u kterých je garantováno, že odezva na dotaz proběhne v přesně definovaném čase
- **In-Memory DB** – DB, který drží data primárně v RAM (Redis)
## Požadavky kladené na SŘBD a jeho vlastnosti.
- Podpora pro definici datových modelů
- Správa klíčů
### Perzistence
- Schopnost uchovávat data v nevolatilní paměti nezávisle na běhu aplikací nebo samotného DB serveru
### Sdílitelnost dat
- Umožnění přístup více různých uživatelů ke stejným datům
### Redundance pod kontrolou
- Využití normalizace k eliminaci duplicity
- Pokud je duplicita důležitá SŘBD o ní ví a hlídá jí
### Integrita dat
- Garance, že data uložená v DB jsou korektní, přesná a odrážejí reálný stav světa podle pravidel, která jsme systému nastavili
- **Druhy integrit:**
	- **Entitní integrita** – každá tabulka musí mít neprázdný PK
	- **Referenční integrita** – cízí klíč musí vždy ukazovat na existující záznam v mateřské tabulce
	- **Doménová integrita** – sloupec přijímá jen hodnoty daného typu/rozsahu
### Bezpečnost a ochrana soukromí
- K datům se dostanou pouze autentizovaní a autorizovaní uživatelé
### Transakční zpracování
- Schopnost sdružovat jednotlivé operace do logických celků (transakcí) a řídit jejich souběžné provádění
### ACID
- Základ transakčního zpracování relačních DB
- Skupina vlastností zaručující spolehlivé provádění transakcí a konzistenci dat
#### Vlastnosti
- **Atomicity** = série modifikací prováděných během transakce se provede buď celá, nebo je DB zanechána v původním stavu
	- Systém musí garantovat toto chování v každé situaci
- **Consistency** = každá transakce převede DB z jednoho konzistentního tvaru do druhého
	- Do DB jsou zapsána pouze data odpovídající integritním omezení
- **Isolation** = data měněná při transakci jsou pro ostatní uživatele DB viditelná v takovém stavu v jakém byli před začátkem transakce
- **Durability** = změny v DB vyvolané úspěšně dokončenou transakcí jsou trvale uložena na perzistentním úložišti
#### ACID na příkladech
- **A** – transakce k převodu prostředků z jednoho účtu na druhý zahrnuje kroky výběru z prvního účtu a vkladu na druhý účet, pokud se povede pouze operace výběru nechceme zůstat v tomto stavu
- **C** – DB sledující běžný účet může umožnit existenci jedinečných čísel šeků pro každou transakci
- **I** – pokladník, který chci vidět zůstatek musí být izolován od aktuálně probíhající transkace (výběr z účtu), zůstatek se mu zobrazí až po té co transakce doběhne
- **D** – zhroucení systému nebo jakékoli jiné selhání nesmí vést ke ztrátě výsledků transakce nebo obsahu DB
## Konceptuální modelování, relační a jiné modely dat.
### Tří-úrovňová architektura ANSI/SPARC
- ![[Pasted image 20260531194908.png]]

### Konceptuální modelování
- První fáze návrhu DB
- Cílem je popsat realitu tak aby tomu rozuměl jak zákazník tak programátor
- Model je zcela nezávislý na použitém SW
- Např.:
	- ER, ERA modely
	- UseCase Diagramy
### Relační modely
- Transformace konceptuálního modelu do konkrétního datového modelu
- Organizování dat do tabulek
- Řádky tabulek reprezentují záznamy
- Sloupce reprezentují atributy
- Primární klíče
- Cizí klíče
### Jiné modely dat
- JSON
- XML
- Model je definovaný podle potřeb ale má jasnou strukturu
## Normální formy, aktivní databáze, principy transakčního zpracování, konzistence databáze.
### Normální formy
- **Superklíč** = jakákoliv kombinace jednoho nebo více sloupců, která jednoznačně identifikuje řádek
- **Kandidátní klíč** = minimální možný superklíč
- **Primární klíč** = jeden konkrétní kandidátní klíč, který byl zvolen
- **Alternativní klíč** = ostatní kandidátní klíče, které nejsou primární
1. Všechny buňky musí obsahovat pouze atomické hodnoty
	- Možné poddefinice:
		- Není povoleno využívat pořadí řádků k předávání informací (databázi musí být jedno, v jakém pořadí řádky čte)
		- Není povoleno míchat datové typy v rámci stejného sloupce (v jednom sloupci nesmí být texty i čísla dohromady)
		- Není povoleno mít tabulku bez primárního klíče
		- Opakující se skupiny nejsou povoleny (to jsou ty naše známé seznamy, pole nebo sloupce typu `Product1, Product2, Product3`)
2. 1NF + všechny neklíčové sloupce musí být plně závislé na celém primárním klíči
	- Nebo
		- Každý atribut, který není součástí primárního klčíe relace R, silně funkčně závisí na primárním klíči relace R
3. 2NF + mezi neklíčovými sloupci nesmí existovat tranzitivní závislost (Každý neklíčový atribut v tabulce musí záviset na klíči, na celém klíči a na ničem jiném než na klíči)
	- BCNF = 3NF + prod každou netriviální závislost $X \rightarrow Y$ musí být $X$ superklíčem
		- Každý ~~neklíčový~~  atribut v tabulce musí záviset na klíči, na celém klíči a na ničem jiném než na klíči
4. BCNF + Jediné druhy **vícehodnotových závislostí** (multivalued dependency) povolené v tabulce jsou vícehodnotové závislosti na klíči
5. 4NF + Tabulku nesmí být možné popsat jako logický výsledek **spojení (joinu)** několika jiných tabulek dohromady (řeší se zde takzvaná závislost na spojení / join dependency)
### Aktivní databáze
- Typ DB systémů schopný sám automaticky reagovat na události, které v něm nastanou
- Nejčastěji se implementuje pomocí:
	- Triggers
	- Stored Procedures
- Využití:
	- Hlídání integrity a byznys pravidel
	- Automatické logování a audit
### Principy transakčního zpracování
- ACID
### Konzistence databáze
- Stav, kdy všechna data v DB odpovídají předem definovaným pravidlům, zákonitostem a integritním omezení
# 2. Big Data management, CAP theorem, distribuce, škálování, replikace, transakce v distribuovaném prostředí. Způsoby analýzy, návrhu a tvorby datových modelů a systémů pracujících s rozsáhlými daty.
## Big Data management, CAP theorem, distribuce, škálování, replikace, transakce v distribuovaném prostředí.
### Big Data management
#### Charakteristické vlastnosti
##### 3V
- Základní tři vlastnosti Big Data
- **Volume**
	- Objem dat je veliký
- **Variety**
	- Získáná data jsou různorodá
	- Např. můžeme mít textové dokumenty, obrázky, videa apod.
	- **Rozdělení:**
		- Strukturované
		- Semi-strukturované
		- Nestrukturované
		- Kombinace
- **Velocity**
	- Data jsou rychle generována, přenášena a zpracovávána
	- **Způsoby přenosu dat:**
		- Batch (dávky)
		- Near-time
		- Real-time
		- Stream
##### 4V
- 3V rozšířeny o **Veracity**
- **Veracity** = důvěryhodnost dat
- Schéma:
	- ![[Pasted image 20250524171535.png]]
##### nV
- Můžeme mít další V, které chrakterizují Big Data
- **Value** = hodnota (schopnost z dat vytěžit užitečné poznámky)
- **Validity** = správnost formátu a kontextu dat
- **Volatility** = nestálost dat
- V literatuře se uvádí až 14V
#### Příklady Big Data
- Sociální sítě – data z FB a IG
- IoT – data z různých sezorů
- E-commerce – recenze produktů, co lidí nakupují
- Finance – transakce, burzovní trhy
#### Alternativy zpracování
##### Klasické relační DB
- Klasické relační databáze nezvládají Big Data, kvůli omezené škálovatelnosti (pouze vertikální škálování) a jsou především vhodná na strukturované data
##### NoSQL DB
- Databáze umožňují horizontální škálování
- Jsou vhodné především na struktorované a semi-strukturované data
- Např. MongoDB, Cassandra
##### Distribuované systémy
- Paralelně zpracovávají data na N nodech
- Např. Apache Hadoop
### CAP teorém
- **=** **C**onsistency **A**vailability **P**artition Tolerance
- **Definice:** kongurentní a logický způsob hodnocení problémů spojených se zajištěném záruk podobných ACID v distribuovaných systémech poskytuje CAP teorém => najednou lze maximalizovat maximálně dva z CAP
#### Vlastnosti
- **Consistency** = každý uzel vidí ve stejný čas stejná data
	- Distribuovaný systém je považován za konzistentní v případě, že všechny operace čtení vrací verzi dat vloženou poslední operací zápisu do sdíleného úložiště
- **Availability** = každý požadavek obsloužen, úspěšně nebo neúspěšně
	- Systém by měl fungovat i když některé jeho servery havarují nebo jsou nedostupné
- **Partition Tolerance** = funkční navzdory chybám sítě nebo výpadkům uzlů
	- Systém je navržen tak, aby mohl pokračovat v práci i v případě, že se kvůli přerušení sítě rozdělí na několik samostatných částí
![[CAP.excalidraw]]
### Distribuce, škálování, replikace, transakce v distribuovaném prostředí
- **Distribuovaný systém** = propojení množiny nezávislých uzlů, který poskytuje uživateli dojem jednotného systému
- **Distribuované databázové systémy (DDBS)** = databázové systémy + počítačové sítě
#### Koncepce DDBS
![[Pasted image 20250524183118.png]]
- Mn. uzlů propojených komunikační sítí
	- Každý uzel je sám o sobě DBS
	- Z každého uzlu lze transparentně zpřístupnit data kdekoliv v síti
- **Požadavky na ideální DDBS:**
	- Uživateli se jeví systém jako nedistribuovaný
	- Lokální autonomie
	- Nespoléhání se na centrální uzel
	- Nepřetžitá činnost
	- Nezávislot na umístění dat (transparentnost)
	- Nezávislot na fragmentaci
	- Nezávislost na replikaci dat
	- Distribuované zpracování dotazu
	- Distribuovaná zpráva transakcí
	- Nezávislost na HW, OS, SŘBD, komunikační síti
#### Replikace
- Fragment relace je replikovaný, je-li uložen na více místech
- **Úplná replikace** = relace je umístěna na všech místech
- **Plně redundantní DB** = DB je umístěna na všech místech
- **Výhody:**
	- Dostupnost
	- Paralelismus
	- Redukce přenosů dat
- **Nevýhody:**
	- Složitější aktualizace
	- Zvýšená složitost řízení souběžného zpracování
- **Strategie aktualizací**
	- **Synchronní**
	- **Asynchronní**
	- ![[Pasted image 20250524204607.png]]
#### Fragmentace
- **Druhy:**
	1. Horizontální
		- Rozdělení tabulky na základě řádků
		- $F_i = \text{Selection}_{P_i} R$ – fragment je vytvořený pomocí výběrové podmínky na realcí $R$
		- $R = \bigcup_i^n F_i$ – relace je rovna sjednocení fragmentů
	2. Odvozená horizontální
		- Horizontální fragmentace jiné relace
		- $R<t_1 \theta t_2] S = (R [t_1 \theta t_2]S)$
	3. Vertikální
		- Rozdělení tabulky na základě sloupců
		- $F_i = R(A_i)$  
		- $R = F_1 \text{join} F_2 \dots \text{join} F_n$
	4. Smíšená
#### Správa transakcí
- **Transakce** = poslouponost operací, které se provedou buď všechny nebo žádná
- **Stavy podtransakcí:**
	- Active
	- Commited
	- Failed
	- ABorted
	- Ready to Commit
	- ![[Pasted image 20250524200537.png]]
- **Dvoufázový potvrzovací protokol:**
	1. Koordinátor zašle všem místům (kde se provádí transakce) zprávu s požadavkem na připravenost (PREPARE to COMMIT). Hlásí-li některé místo nepřipravenost, provede koordinátor ROLLBACK transakce ve svém místě a pošle zprávu všem místům na ABORT podtransakcí
	2. Ohlásí-li všechna místa úspěšnost (READY to COMMIT), tak koordinátor potvrdí transakci a její lokální části ve svém místě. Pak odešle zprávy s požadavkem na potvrzení (COMMIT) všem participantům.
#### ACID
- **=** **A**tomicity **C**onsistency **I**solation **D**urability
- Základ transakčního zpracování relačních DB
- Skupina vlastností zaručující spolehlivé provádění transakcí a konzistenci dat
##### Vlastnosti
- **Atomicity** = série modifikací prováděných během transakce se provede buď celá, nebo je DB zanechána v původním stavu
	- Systém musí garantovat toto chování v každé situaci
- **Consistency** = každá transakce převede DB z jednoho konzistentního tvaru do druhého
	- Do DB jsou zapsána pouze data odpovídající integritním omezení
- **Isolation** = data měněná při transakci jsou pro ostatní uživatele DB viditelná v takovém stavu v jakém byli před začátkem transakce
- **Durability** = změny v DB vyvolané úspěšně dokončenou transakcí jsou trvale uložena na perzistentním úložišti
##### ACID na příkladech
- **A** – transakce k převodu prostředků z jednoho účtu na druhý zahrnuje kroky výběru z prvního účtu a vkladu na druhý účet, pokud se povede pouze operace výběru nechceme zůstat v tomto stavu
- **C** – DB sledující běžný účet může umožnit existenci jedinečných čísel šeků pro každou transakci
- **I** – pokladník, který chci vidět zůstatek musí být izolován od aktuálně probíhající transkace (výběr z účtu), zůstatek se mu zobrazí až po té co transakce doběhne
- **D** – zhroucení systému nebo jakékoli jiné selhání nesmí vést ke ztrátě výsledků transakce nebo obsahu DB
#### BASE
- **=** **B**asicaly **A**vailable **S**oft-state **E**venetual consistency
- Preference dostupnosti, částečné degragace a výkonu před konzistencí a izolací
##### Vlastnosti
- **Basicaly Available** = aplikace pracuje bez přerušení
- **Soft-state** = aplikace nemusí být v každém okamžiku konzistentní
- **Eventual consistency** = aplikace bude v blíže neurčené době opět konzistentní
## Způsoby analýzy, návrhu a tvorby datových modelů a systémů pracujících s rozsáhlými daty.
### Map-Reduce
- **=** programovací model sloužící k zpracování/generování Big Data pomocí distribuovaných a paralelních algoritmů na clusterech
- **Princip:**
	1. Každý node použije `map` funkci na jeho data a zapíše výstupu této funkce do dočasného úložiště, master nody zajišťují to, že vytvořené výstupy nejsou redundantní. Při kroku `map` jsou vytvářeny dvojice klíčů a hodnot.
	2. Pracovní nody přerozdělí data na další nody podle klíčů tak, že každý node poté bude zpracovávat data pouze pro nějakou množinu klíčů.
	3. Pracovní nody provedou fázi `reduce` a data se postupně seskupují
![[Pasted image 20250524175824.png]]
### Hadoop
- Open-source SW framework
- Odvozen z Google MapReduce a Google File System (GFS)
- **Moduly:**
	- **Hadoop Common** – společné funkcionality
	- **Hadoop Distributed File System (HDFS)** – distribuovaný souborový systém
	- **Hadoop YARN** – framwork pro plánování úloh a řízení zdrojů clustrů
	- **Hadoop MapReduce** – systém pro paralelní zpracování velkých datasetů
#### HDFS
![[Pasted image 20250524180554.png]]
- **Princip:**
	1. **Soubor se rozdělí** na bloky po 128 MB → vznikne 8 bloků.
	2. **NameNode** rozhodne, na které **DataNody** se bloky uloží.
	3. Každý blok se **zreplikuje** (např. 3 kopie) a **uloží na různé servery**.
	4. Když chci soubor zpět, **NameNode** řekne, kde jsou bloky, a **DataNode** je pošlou.
### Návrh a tvorba
- Často se využívají NoSQL přístupy
#### Klíč-Hodnota (Key-Value)
- Inspirováno Amazons Dynamo
- **Datový model:** kolekce `key-value`
- Asociativní pole nebo hash tabulka s ukládáním hodnot podle unikátního klíče
- Jmenné prostory pro oddělení dat
- Rychlé vytvoření
- Rychlost práce s daty
- **Příklady:**
	- Redis
	- Dynomite
	- Voldemort
	- Tokyo
#### Sloupcové databáze (Column-oriented)
- Inspirováno Google Bigtable
- **Datový model:** rodiny sloupců  (Column family)
- Jsou vhodné pro analýzy dat a datové sklady
- **Příklady:**
	- Hbase
	- Hypertable
#### Dokumentové databáze (Document databases)
- Inspirováno Lotus Notes
- **Datový model:** kolekce semistrukrovaných dokumentů
- Místo s řádky pracují s dokumenty
- **Příklady:**
	- MongoDB
	- CouchDB
#### Grafové databáze (Graph databases)
- Inspirováno teorií grafů
- **Datový model:** vrcholy, hrany, key-value u oboud
- Každý vrchol obsahuje přímé odkazy na své sousedy
- Nejsou vhodné pro distribuované data
- **Traverzování** = návštěva všech vrcholů grafu
- **Sociogram** = grafické znázornění sociálních vztahů
- **Interest graph** = zjištění zda spolu uživatelé něco sdílejí
- **Příklady:**
	- Neo4J
	- VertexDB
	- DEX
# 3. Zpracování strukturovaných a nestrukturovaných dat. Nerelační/postrelační databáze – BASE vs. ACID, druhy a vlastnosti NoSQL databází. Data s více modely, multi-model databáze. 
## Zpracování strukturovaných a nestrukturovaných dat.
- Variety je jednou ze základních vlastností Big Data
- Zpracováváne data dělíme na:
	- **Strukturovaná data**
		- Vhodná pro klasické relační DB
		- Při enormních objemech naráží na limity vertikální škálovatelnosti (nelze donekonečna zvyšovat výkon jednoho serveru)
	- **Semi-strukturovaná data**
		- Obsahují vnitřní hierarchie, ale nemají tabulkové schéma
		- Formáty:
			- **JSON** – formát postavený na párech key-value
				- **BSON** – binární serializace pro rychlejší zpracování
			- **XML**
			- **RDF** – sémantický popis webu pomocí tzv. trojit (zdroj, vlastnost, hodnota)
		- Na tyto formáty jsou ideální NoSQL DB
	- **Nestrukturovaná data**
		- Texty, videa, obrázky
		- Vyžadují k efektivnímu uložení a analýze distribuované systémy, které paralelně zpracovávají data napříč více uzly
## Nerelační/postrelační databáze – BASE vs. ACID, druhy a vlastnosti NoSQL databází.
- **NoSQL** = Not only SQL
	- Popisuje volně specifikovanou třídu nerelačních datových úložišť
	- Někdy označováno jako **postrelační**
- Horizontální i vertikální škálovatelnost
	- **Vertiální škálování** = zvyšování výkonu jednoho serveru
	- **Horizontální škálování** = přidávání dalších serverů
	- **SQL** podporuje primárně **vertikální škálování**
### Charakteristika
- Optimalizovaná DB, kdy jsou využívány klíče i hodnoty
- Struktura ukládání dat je odlišná
	- Často využívá stromy nebo grafy
- Navyšující se popularita hlavně v segmentu **real-time web** a **big data**
- Často potlačují **konzistenci** ve prospěch **dostupnosti** a **toleranci k narušení sítě**
- Mezi bariéry patří např. nepřítomnost plnohodnotné podpory **transakčního modelu**
- **NoSQL** je termín zastřešující všechny DB a datová úložiště, které nedodržují principy **RDBMS**
	- **RDBMS** = Relational Database Management System
- **Charakteristiky:**
	- Bez schématu
	- Snadná podpora replikace
	- Jednoduché API
	- Případně konzistentní / BASE (ne ACID)
	- **Distributovatelnost**
![[Pasted image 20250524124554.png]]
### ACID
- **=** **A**tomicity **C**onsistency **I**solation **D**urability
- Základ transakčního zpracování relačních DB
- Skupina vlastností zaručující spolehlivé provádění transakcí a konzistenci dat
#### Vlastnosti
- **Atomicity** = série modifikací prováděných během transakce se provede buď celá, nebo je DB zanechána v původním stavu
	- Systém musí garantovat toto chování v každé situaci
- **Consistency** = každá transakce převede DB z jednoho konzistentního tvaru do druhého
	- Do DB jsou zapsána pouze data odpovídající integritním omezení
- **Isolation** = data měněná při transakci jsou pro ostatní uživatele DB viditelná v takovém stavu v jakém byli před začátkem transakce
- **Durability** = změny v DB vyvolané úspěšně dokončenou transakcí jsou trvale uložena na perzistentním úložišti
#### ACID na příkladech
- **A** – transakce k převodu prostředků z jednoho účtu na druhý zahrnuje kroky výběru z prvního účtu a vkladu na druhý účet, pokud se povede pouze operace výběru nechceme zůstat v tomto stavu
- **C** – DB sledující běžný účet může umožnit existenci jedinečných čísel šeků pro každou transakci
- **I** – pokladník, který chci vidět zůstatek musí být izolován od aktuálně probíhající transkace (výběr z účtu), zůstatek se mu zobrazí až po té co transakce doběhne
- **D** – zhroucení systému nebo jakékoli jiné selhání nesmí vést ke ztrátě výsledků transakce nebo obsahu DB
### BASE
- **=** **B**asicaly **A**vailable **S**oft-state **E**venetual consistency
- Preference dostupnosti, částečné degragace a výkonu před konzistencí a izolací
#### Vlastnosti
- **Basicaly Available** = aplikace pracuje bez přerušení
- **Soft-state** = aplikace nemusí být v každém okamžiku konzistentní
- **Eventual consistency** = aplikace bude v blíže neurčené době opět konzistentní
### Porovnání ACID a BASE

| **ACID**            | BASE                              |
| ------------------- | --------------------------------- |
| silná konzistence   | slabá konzistence                 |
| izolovanost         | dostupnost na prvním místě        |
| orientace na commit | přibližné odpovědi jsou OK        |
| vnořerné transakce  | jednodušší, rychlejší dodávka dat |
| dostupnost?         | agresivní (optimistické)          |
| složitá evoluce     | jednodušší evoluce                |
|                     |                                   |
![[Pasted image 20250524133326.png]]
### Dokumentové DB
- Typ NoSQL DB
- **Datový model:** kolekce semistrukturovaných dokumentů
- Místo s řadky pracují s dokumenty
- **Základní charakteristiky:**
	- Dokumenty jsou hlavní koncept
	- Dokumenty jsou:
		- Self-describing
		- Hiearchicky strukturované
	- Dokumenty v jedné kolekci jsou podobné
	- Dokumenty jsou reprezentovány jako množina key-value párů
- **Vhodné pro:**
	- Protokolování událostí
	- Systémy pro správu obsahu
	- Webová analýza nebo analýza v real-time
	- Aplikace pro elektronické obchodování
- **Nevhodné pro:**
	- Složité transakce zarhnující různé operace
	- Dotazy proti proměnlivé agregované struktuře
#### MongoDB
- Napsáno v jazyce C++
	- Open-source
- Multiplatformní
- Dokumenty JSON
- **Funkce:**
	- Vysoký výkon
	- Vysoký dostupnost – replikace + případná konzistence
	- Automatické škálování – automatický shardig napříč clusterem
	- Podpodra MapReduce
- Každá MongoDB má instanci více DB
- Každá DB může mít více kolekcí
- Při ukládání dokumentu je nutné vybrat databázi a kolekci
- **Srovnání terminologie:**
	- ![[Pasted image 20250525115957.png]]
- **Dokumenty:**
	- JSON, ale jsou uloženy jako BSON
	- Mají max. velikost 16 MB
		- Nástroj GridFS umožňuje větší soubory
	- `_id` je vyrazeno jako PK
- **Datový model:**
	- Dokumenty mají flexibilní schéma
	- Rozhodnutí mezi odkazy a vloženými dokumenty
- **Embedded:**
```JSON
{
  "_id": 1,
  "name": "Alice",
  "address": {
    "street": "Main St",
    "city": "Prague",
    "zip": "11000"
  }
}
```
- **Odkazy:**
```JSON
{
  "_id": 1,
  "name": "Alice",
  "address_id": ObjectId("123")
}

{
  "_id": ObjectId("123"),
  "street": "Main St",
  "city": "Prague",
  "zip": "11000"
}
```
### Key-Value DB
- **Datový model:** kolekce key-value
- Důraz na rychlost
- Většinou bývá in-memory
- Asociativní pole nebo hash tabulka
- Ukládání hodnot podle unikátního klíče
- Rychlé vytvoření, rychlá práce s daty
- Nejjenodušší typ NoSQL DB
- Vhodná pro jednoduché datové modely
- Vysoká vertikální škálovatelnost
- **Použití:**
	- Cache systémy (Redis)
	- Uložení session informací
	- Rychlý přístup ke konfiguračním datům
### Column DB
- **Datový model:** rodiny sloupců
- Data se ukládají do sloupců
- Jsou optimalizované pro analytické úkoly
- Vhodné pro datové sklady
- **Výhody:**
	- Rychlé dotazy na sloupci
	- Lepší komprese => data v jednom sloupci jsou homogenní
	- Vhodné pro analytiku
	- Paralelizace => můžeme pracovat s více sloupci najednou
	- Škálovatelnost
- **Nevýhody:**
	- Nevhodné pro časté zápisy celé řádky dat
	- Nevhodné pro OLTP (Online Transaction Processing)
	- Komplexnější aktualizace a mazání u více sloupců najednou
- **Příklady:**
	- Hbase, Hypertable
	- Apache Cassandra
### Grafové DB
- Patří do skupiny NoSQL DB
- **Vlastnosti:**
	- Vysoký výkon pro vztahové dotazy
	- Flexibilita a dynamické schéma
	- Vysoká dostupnost a škálovatelnost
- Nativně ukládají grafové struktury
- Eliminují problémy s uložením grafu (stromu) do relační DB
- Často tyto DB bývají veliké (miliardy vrcholů a hran, miliony grafů)
- **Datový model:** vrcholy, hrany, key-value u obou
- **Využití:**
	- Sociální sítě 
		- Doporučení, sdílení, analýza sentimentu
	- Detekce podvodů v real-time (Fraud Detection)
		- E-commerce, pojištovny
	- Podnikové sítě
		- QoS
	- Správa identit
#### Graph Partitioning
- ![[Pasted image 20250525113033.png]]
- **Cíl:** získat vybalancované části grafů
	- NP-hard problém
#### Neo4J
- Přímá podpora pro grafy
	- Datový mode, API, dotazovací jazyk
	- Implementováno jako linked listy na disku
	- Optimalizováno pro zpracování grafů
	- Trasnakce
- ACID transakce
- Umožňuje horizontální škálování
- Vysoký výkon a nízká latence
- **Datový model:**
	- ![[Pasted image 20250525114155.png]]
- **Architektura:**
	- ![[Pasted image 20250525114229.png]]
##### Dotazovací jazyk Cypher
- **Vytvoření uzlů:**
```Cypher
CREATE (a:Person {name: 'Alice'})
CREATE (b:Person {name: 'Bob'})
```
- **Vytvoření vztahu:**
```Cypher
MATCH (a:Person {name: 'Alice'}), (b:Person {name: 'Bob'})
CREATE (a)-[:FRIENDS_WITH]->(b)
```
- **Dotaz najdi všechny přátele Alice:**
```Cypher
MATCH (a:Person {name: 'Alice'})-[:FRIENDS_WITH]->(friend)
RETURN friend
```
## Data s více modely, multi-model databáze.
- **Motivace:** vytvoření jediné aplikace pro různé modely dat
- ![[Pasted image 20250525134023.png]]
- Multimodelové DB jsou navrženy tak, aby podporovali několik datových modelů na jednom integrovaném backendu
- **Příklady datových modelů:** dokumenty, grafy, relační, key-value
- **Příklad DB:** ArangoDB
### 3 Argumenty
#### 1. One size cannot fit all
- SQL analytika, real-time podpora rozhodování a datové sklady nemohou existovat v pouze jednom enginu
#### 2. One size can fit all
- OctopusDB navrhla jednu sjednocenou architekturu, které je vhodná na OLTP, OLAP, streamovací služby a scan-oriented databázové systémy
- **Princip:**
	- Všechny data se ukládají do centrálního logu
	- Podle logu se definuje několik typů možných pohledů na data
#### 3. One size can fit a bunch
- Do jednoho nástroje se dá spojit pouze několik druhů dat
### Polystores
- Nazývány také **Multistores**
- Poskytují integrovaný přístup k několika cloudovým datovým úložištím jako je NoSQL, HDFS a RDBMS
- Vhodné pro integraci strukturovaných (relačních) dat a Big Data
- Složitější než distribuované DB
#### Klasifikace Polystores
- Dělení podle úrovně provázanosti s využitými datovými úložišťmi:
	- Volně provázané (Loosely-coupled)
	- Silně provázané (Tightly-coupled)
	- Hybridní
#### Loosely-coupled Polystores
- Vzdáleně připomínají multidatabase systémy
	- Mediator-wrapper achitektura
	- Autonomní datové úložiště
	- Jeden společný interface pro všechny datová úložiště
- **Příklady:**
	- BigIntegrator – systém navržený pro integraci různorodých datových zdrojů pomocí jednotného dotazovacího rozhraní
	- Forward – výzkumný systém, který umožňuje integrované zpracování dat z více webových a databázových zdrojů v reálném čase
	- QoX – systém vyvinutý zaměřený na správu kvality služeb při dotazování nad heterogenními datovými úložišti
- **Architektura:**
	- ![[Pasted image 20250525164730.png]]
#### Tightly-coupled Polystores
- Využívá lokální rozhraní jednotlivých datových úložišť
- Používá jednotný dotazovací jazyk
- Umožňuje přesun dat mezi datovými úložišťmi
- **Příklad:**
	- Polybase – technologie od Microsoftu, která umožňuje SQL Serveru dotazovat se na externí zdroje dat (např. Hadoop nebo Azure Blob Storage) pomocí standardního T-SQL
	- HaddopDB – výzkumný projekt, který kombinuje výpočetní výkon Hadoopu s efektivitou relačních databází pro škálovatelné zpracování dat
	- Estocada – experimentální polystore systém zaměřený na efektivní plánování a vykonávání dotazů napříč různorodými datovými úložišti
- **Architektura:**
	- ![[Pasted image 20250525172210.png]]
### Hybrid Polystores
- Podporuje autonomii datových zdrojů jako v loosely-coupled systémech
- Využívá lokální rozhraní datových zdrojů jako v tightly-coupled systémech
- **Příklad:**
	- SparkSQL – modul Apache Spark, který umožňuje spouštět SQL dotazy nad strukturovanými daty a integrovat SQL s dalšími Spark API
	- ClodMdsQL – middleware umožňující spouštění dotazů v jazyce rozšířeném SQL nad více cloudovými databázemi v rámci polystore architektury
	- BigDaWG – polystore systém vyvinutý v MIT, který umožňuje provádět dotazy nad různými typy databází (relační, grafové, časové aj.) pomocí jednotného rozhraní.
- **Architektura:**
	- ![[Pasted image 20250525172605.png]]
#### 1. One size cannot fit all
- SQL analytika, real-time podpora rozhodování a datové sklady nemohou existovat v pouze jednom enginu
#### 2. One size can fit all
- OctopusDB navrhla jednu sjednocenou architekturu, které je vhodná na OLTP, OLAP, streamovací služby a scan-oriented databázové systémy
- **Princip:**
	- Všechny data se ukládají do centrálního logu
	- Podle logu se definuje několik typů možných pohledů na data
#### 3. One size can fit a bunch
- Do jednoho nástroje se dá spojit pouze několik druhů dat
# 4. Principy a nástroje Business Intelligence, vrstvy pro analýzu dat. Přístupy k vytváření datových skladů a datových tržišť. Architektura datového skladu, jeho implementace.
## Principy a nástroje Business Intelligence, vrstvy pro analýzu dat.
### Principy BI
- = **sada** technologických **procesů** pro sbírání, spravování a analýzu dat organizace s **cílem získávat insight**, který lze využít pro **business strategie a operace**
- = sběr a analýza dat, jejímž cílem je lepší porozumění a reakce na změny, kterým organizace neustále čelí
- **Principy:**
	- Zpracování velkých objemů dat => výsledek zpracování pomáhá k rozhodování při řízení procesů
	- Výsledek zpracování musít být relevantní informace, která je předána ve správném čase
	- Základní zdroj dat bývají ERP systémy (relační DB)
- ![[Pasted image 20260602224630.png]]
### Nástroje BI
- ERP systémy
- Dočasná úložiště (**DSA:** Data Staging Area)
- Operativní úložiště (**ODS:** Operational Data Store)
- Transformační nástroje (**ETL:** Extraction Transformation Loading)
	- Pouští ve specifické časy a získává velké množství dat najednou
- Integrační nástroje (**EAI:** Enterprise Application Integration)
	- Vykonává se pokaždé události (event) v zdrojových systémech (např. vznik nové objednávky)
- DW
- Datová tržiště
- OLAP
- Reportingové nástroje
- EIS (Executive Information System)
- Data Mining
### Vrstvy BI
- ![[Pasted image 20260608163207.png]]
- **Zdroje dat:**
	- ERP, CRM, ...
- **Integrační vrstva:**
	- **EAI** = Enterprise Application Integration
		- Slouží k propojení nekompatibilních systémů/SW
	- **ETL** = Extract Transform Load
		- Integrační process, který kombinuje, čistí a organizuje data z několika zdrojů do jednoho
- **Staging Area:**
	- = DSA
	- Odkládací prostor před zpracování
- **Data Warehouse:**
	- Datový sklad
	- **Operativní úložiště** = ODS = Operational Data Store
		- Rychlé operativní reporty nad aktuálními daty
- **Datové tržiště:**
	- **Datové úložiště** – podmnožiny datového skladu
- **Prezentační vrstva:**
	- **Reporting** = statické přehledy
	- **OLAP** = kostky
	- **Dolování dat** = porkočilá analýza
## Přístupy k vytváření datových skladů a datových tržišť.
### Datový sklad
- Jádro BI
- Analytická databáze (obvykle relační) vytvořena ze dvou a více zdrojů dat
- Umožňují holistický přístup
- *"Schéma při zápisu"* = datové typy, indexy a vztahy jsou zavedeny již v datech tak jak jsou data uložena v DW
#### Cíle DW
- Zajistit:
	- Dostupnost firemních informací
	- Konzistenci firemních informací
- Vytvořit adaptivní a pružný zdroj informací
- Zabezpečit ochranu firemních informací
- Vytvořit základnu pro firemní podporu rozhodování
#### DW procesy
- Hlavní proces při tvorbě DW
- Podprocesy:
	- Extrakce
	- Transformace
	- Načtení a tvorba indexů
	- Data Quality Assurance
#### Datové tržiště
- Obsahují data orientovaná na konkrétní oblast
- Podmnožina DW
- **Druhy:**
	- Závislá na DW (vznikají z DW)
	- Nezávislá na DW (odvozovaná z provozní DB či externích zdrojů)
- **Důvody pro použití:**
	- Menší nárok na úložiště
	- Rychlejší odpovědi na dotazy
	- Menší náklady na provoz
- DM často obsahuje shrnuté a vybrané údaje namísto nebo navíc k podobným údajům v DW
### Přísupty
- ![[DBM2-zkouska 2025-12-30 16.19.56.excalidraw]]
#### Metoda velkého třesku (Inmon)
- ![[Pasted image 20260102124157.png]]
- Vybudování datového skladu najednou pro všechny oddělení
- Dlouhý vývoj bez výsledků
- Snaha o dokonalý model celého podniku najednou
- **Výhody:**
	- Single source of truth
	- Vysoká konzistence a kvalita dat
	- Nízká redundantnost
- **Nevýhody:**
	- Vysoké riziko selhání
	- Vysoké počáteční náklady
	- Dlouhá doba realizace
#### Přírůstková metoda (Kimball)
- ![[Pasted image 20260102124214.png]]
- Datový sklad se stavý postupně po jednotlivých tržiští
- Datová tržiště jsou propojena pomocí sdílených dimenzí (**Conformed Dimensions**) => to zajišťuje, že pojmy jako *zákazník* nebo *produkt* znamenají to samé ve všech tržiští
- **Výhody:**
	- Rychlé výsledky (Time-To-Market)
	- Nižší počáteční investice
	- Flexibilita
- **Nevýhody:**
	- Riziko nekonzistence
	- Náročnější správa celku
	- Redundance
### ETL
- = Extract Transform Load
- Integrační process, který kombinuje, čistí a organizuje data z několika zdrojů do jednoho
- ![[Pasted image 20251230231640.png]]
- Každý ETL nástroj musí umět:
	1. Zpracovávat různorodá data obvykle fyzicky umístěná na různých místech
	2. Navrhovat transformace pro přenos dat mezi různými datovými formáty
- Příklad:
	- **Datová pumpa:**
		- ![[Pasted image 20251230231930.png]]
- ![[Pasted image 20260602223816.png]]
#### Datová pumpa
- = ETL
- ![[Pasted image 20260102220508.png]]
- Tříkrokový proces
##### Proces
1. Fáze – Extract
	- Nezpracovaná data se čtou a shromažďují z různých zdrojů v různých formátech
	- Je nutno chápat v jaké formě a formátu jsou data a systémy, které data generují
	- Je potřeba rozhodnout jak často se připojovat ke zdroji dat
	- **Výzvy:**
		- **Oprávnění** – mají sítě a systémy přístup a práva k datům
		- **Integrita a přesnost**
		- **Ztráta dat** – dokážeme data získat než projdou svou životností
		- **Dostupnost a škálovatelnost** – máme dostatek úložiště a výpočetní kapacity
2. Fáze – Transform
	- Obchodní pravidla se v této fázi používají k **čištění dat**
	- Provádění operací s data za účelem **agregace**
	- **Formátování dat**
	- Na konci kroku jsou data ve správně formě pro uložení do DW
	- **Aktivity:**
		- Odvození vypočtených hodnot na základě nezpracovaných dat
		- Přeuspořádání nebo transpozice dat
		- Přidání metadat
		- Odstranění redundance
		- Kódování/dekódování
		- Ověřování
	- **Výzvy:**
		- Výpočetní výkon a dostupné zdroje
3. Fáze – Load
	- Data se načtou do datového úložiště
	- Proces může být: 
		- Jednoduchý => nestrukturovaný textový soubor
		- Složitý => datové sklady
	- Proces se značně liší podle obchodních požadavků
##### Metody čistění dat
- Standardizace
- De-duplikace
- Doplnění chybějících hodnot
#### ETL vs. ELT
- **ELT** = Extract Load Transform
	- Alternativní proces
	- Zdrojová data se přímo načtou do DB a následně dochází k transformaci
	- Populární díky cloudové infrastruktuře
		- K transformaci lze využít výpočetní výkon a rozsah cloudu
	- Big Data, Hadoop
	- Vhodné pro velké data
### OLTP
- = **O**nline **T**ansaction **P**rocessing
- Provozní systémy
- Real-time vykonávání vysokého počtu databázových transakcí
- Transakce provádí mnoho uživatelů najednou
- Zpracování transakcí musí být extrémně rychlé
- Neustálá dostupnost (24/7)
- Normalizace (3. NF)
- ACID (Atomicity Consistency Isolation, Durability)
- Př.: bankovní transakce, eshopy, ...
### OLAP
- = **O**nline **A**nalytical **P**rocessing
- Analytické systémy
- Vykonávání rychlých a komplexních dotazů
- Multi-dimenzionální analýza nad velkými objemy dat
- Využívá se v BI
- **FASMI**:
	- Fast – do 30 sekund
	- Analysis – flexibilita (ad-hoc dotazy)
	- Shared – stejné výsledky pro všechny (konzistence dat)
	- Multidimensional – dimenzionální modelování
	- Information – důraz na zpracování velkého objemu dat
#### OLAP Kostka (MOLAP)
- ![[Pasted image 20251229220620.png]]
- Rozšíření klasické tabulky o další vrstvy (dimenze)
##### Operace nad kostkou
- **Roll-up (Sbalení):** Jdeme v hierarchii **nahoru** (Město → Region). Detaily mizí, čísla se sčítají (agregují).
- **Drill-down (Detail):** Jdeme v hierarchii **dolů** (Země → Město). Rozpad velkých celků na podrobnosti.
- **Slice (Řez):** Výběr **jednoho** konkrétního plátku. Zafixujeme jednu dimenzi (např. pouze „Pondělí“).
- **Dice (Výřez):** Výběr **pod-kostky**. Omezení více dimenzí naráz (např. jen „Chleba a Sýr“ v „Plzni“).
- **Pivot (Otočení):** Prohození os (řádky za sloupce). Data jsou stejná, mění se jen pohled na tabulku.
- ![[Pasted image 20251229222751.png]]
#### ROLAP
- = Relational OLAP
- Multi-dimenzionální datová analýza nad daty v relační databázi
- SQL dotazy musí být komplexní
- Menší výkon
#### HOLAP
- = Hybrid OLAP 
- Kombinace MOLAP a ROLAP
## Architektura datového skladu, jeho implementace.
### Architektura
- ![[DBM2-zkouska 2025-12-30 15.01.32.excalidraw|1000]]
#### Schéma hvězdy
- ![[Pasted image 20260102145157.png]]
- **Výhody:**
	- Přehlednější pro uživatele
	- Snadněji udržovatelné
	- Méně joinů
- **Nevýhody:**
	- Obsahuje redundanci
	- Zabírá více místa
#### Schéma sněhové vločky
- ![[DBM2-zkouska 2026-01-02 14.53.55.excalidraw|1000]]
- **Výhody:**
	- Méně redundance => šetří místo na disku
	- Usnadňuje údržbu složitých hiearchií
- **Nevýhody:**
	- Méně přehledné
	- Náročnější na údržbu
	- Více joinů
### Implementace
- ETL
- ELT
# 5. Modelování dat v datových skladech, dimenzionální model. Hierarchie dimenzí, typy a vlastnosti atributů, typy vztahů. Charakteristiky tabulek faktů a dimenzí, transformace mezi jednotlivými modely.
## Modelování dat v datových skladech, dimenzionální model.
### Problematika modelování dat v datových skladech
- V DW se využívá technika dimenzionální modelování
- Dimenzionální modelování je zásadně odlišné oproti klasickému ERA modelování
- **ERA:**
	- Normalizace
	- Odstranění redundance
	- Málo srozumitelné človeku
	- Optimalizován na vkládání dat a update
- **Dimenzionální:**
	- Důraz na srozumitelnost pro uživatele
	- Standardní struktura: **fakta a dimenze**
	- Základní přístup: **denormalizace, redundance**
	- Optimalizováno pro vyhledávání dat a analýzy
### Pojmy obchodní, logický a fyzický model
- **Obchodní (konceptuální) model**
	- Definujeme co budeme sledovat z pohledu businessu
	- Nezabývá se technologiemi, ale pojmy jako je *Zákazník, Produkt, Čas*
- **Logický model**
	- Určuje strukturu dat
	- Volba konkrétního přístupu (např. dimensionální)
- **Fyzický model**
	- Implementace logického modelu na konkrétní technologii
	- Řeší datové typy, index, partitioning, fyzické umístění na disku
### Schéma hvězdy
- ![[Pasted image 20260102145157.png]]
- **Výhody:**
	- Přehlednější pro uživatele
	- Snadněji udržovatelné
	- Méně joinů
- **Nevýhody:**
	- Obsahuje redundanci
	- Zabírá více místa
### Schéma sněhové vločky
- ![[DBM2-zkouska 2026-01-02 14.53.55.excalidraw|1000]]
- **Výhody:**
	- Méně redundance => šetří místo na disku
	- Usnadňuje údržbu složitých hiearchií
- **Nevýhody:**
	- Méně přehledné
	- Náročnější na údržbu
	- Více joinů
## Hierarchie dimenzí, typy a vlastnosti atributů, typy vztahů.
### Hierarchie dimenzi
- ![[Pasted image 20251229220620.png]]
- Dimenzionální tabulka v sobě nese různé hierarchie – vztahy 1:M mezi atributy dimenze
- Hierarchie mají vždy stromovou strukturu
- Př.:
	- Rok => Kvartál => Měsíc => Den
- Umožňují provádění operací Drill-down a Roll-up
- **Typy:**
	- Jednoduché – stromové
	- Složité – modelování pomocí pomocných tabulek
### Typy a vlastnosti atributů
- Atributy slouží jako popisné prvky, klíče a filtry v analytických dotazech
- Obecně:
	- **Textové** – např. názvy produktů
	- **Číselné** – např. ceny, množství
	- **Datum a čas**
	- **Logické**
- Další dělení:
	- Nominální – atributy k rozlišení objektů (např. jméno)
	- Ordinální – jejich hodnoty lze smysluplně seřadit
	- Binární
	- Numerické
		- Intervalově škálované
		- Poměrové
### Typy vztahů
- **1:N** – každý fakt spojen s jednou hodnotou z dimenze
- **M:N** – pomocná tabulky pokud je jeden fakt spojen s více hodnotami v jedné dimenzi
- **Hierarchické** – hierarchické uspořádání v dimenzi
## Charakteristiky tabulek faktů a dimenzí, transformace mezi jednotlivými modely.
### Tabulka faktů
- Uchování informací o sledovaných ukazatelích
- Typicky obsahuje cizí klíče na dimenzionální tabulky
- Typické ukazatele:
	- Počet prodaných ks
	- Hodnota prodaného zboží
	- Počet zákazníků
- Většinou uloženy číselné údaje, které lze agregovat
#### Typy ukazatelů
- **Aditivní** – agregovatelné (sčítáním) přes všechny dimenze)
	- Př.: 
		- Počet prodaných ks
			- Mám dimenze: čas, region, produkt
			- Počet prodaných ks můžu sečíst přes každou dimenzi
- **Semiaditivní** – agregovatelné (sčítáním) jen přes některé dimenze
	- Př.:
		- Stav zásob v ks
			- Mám dimenze: čas, region, produkt
			- Nemůžu sčítat přes čas protože, to že mám v pondělí na skladě 10 ks a v úterý taky 10 ks neznamená, že mám celkem 20 ks
- **Neaditivní** – neagregovatelné
#### Typy tabulek
- **Transakční**
	- Zachycuje jednotlivé transkace/akce v daný časový okamžik
- **Snímková**
	- Zachycuje stav k určitému časovému okamžiku (periodicky)
- **Akumulovaná**
	- Zachycuje stav v daný okamžik
### Dimenzionální tabulky
- Zachycují úhel pohledu na sledované ukazatele
- Představují *"číselníky"*
- Typické dimenze:
	- Čas
	- Zákazník
	- Produkt
	- Smlouva
- Každá dimenzionální tabulka obsahuje jedno ID a popisné atributy
- Tabulky jsou denormalizované
- ![[Pasted image 20260102153811.png]]
- Tabulky mohou obsahovat hierarchické vztahy
- **SCD**
	- **Typ 1 (Přepsání):** Stará hodnota se přepíše novou. Historie se neuchovává.
	- **Typ 2 (Nový řádek):** Vytvoří se nový záznam s novým umělým klíčem. Původní záznam zůstává platný pro stará fakta. Toto je nejpoužívanější technika pro zachování historie.
	- **Typ 3 (Nový sloupec):** Přidá se sloupec pro "původní hodnotu". Umožňuje sledovat jen poslední změnu
### Transformace mezi jednotlivými modely
- Mezi schématy Hvězda a Sněhová vločka:
	- Hvězda => Sněhová vločka – musíme normalizovat
	- Sněhová vločka => hvězda – musíme denormalizovat
# 6. Metadata pro správu datového skladu, metadata zdrojových dat, datového skladu a datové pumpy, metadata pro data a funkce na pozadí datového skladu, metadata pro koncového uživatele, standardizace metadat.
- **Metadata** = data o datech
## Metadata pro správu datového skladu
- Slouží správcům DB a operátorům k tomu, aby sklad běžel, byl bezpečný a optimálně fungoval
- Obsahují:
	- **Auditní logy**
		- Informace o tom kdo, kdy a k jakým datům přistupoval
	- **Statistiky využití**
		- Velikost tabulek, zaplnění disků, rychlost exekuce jednotlivých SQL
	- **Plánování úloh**
		- Kdy se mají spouštět jaké skripty, závislost mezi úlohami
	- **Správa uživatelů**
		- Definice rolí, přístupových práv a bezpečnostních politik
## Metadata zdrojových dat, datového skladu a datové pumpy
- Popisují fyzickou strukturu systémů a kompletní datovou cestu
- Nejdůležitější část pro inženýry a vývojáře
- **Metadata zdrojových dat:**
	- Technický popis systémů, ze kterých data bereme 
		- Schémata produkčních DB, datové typy sloupců, struktura CSV souborů či API
- **Metadata datového skladu:**
	- Popis vnitřní struktury skladu
		- Jak vypadá staging area, jak jsou navržené dimenze a tabulky faktů
- **Metadata datové pumpy**
	- **Mapování**
		- Který sloupec ze zdroje padá do kterého sloupce v DW
	- **Transformační pravidla**
		- Jak se data čistí a mění
			- Např. převod kódů měn
	- **ETL Run-time logs**
		- Statistiky z pumpy
			- Např. kolik řádků se dnes v noci úspěšně přeneslo
## Metadata pro funkce na pozadí datového skladu
- Zaměření na vnitřní mechanismy, optimalizace a údržbu dat na pozadí skladu
- **Obsahují:**
	- **Agregační pravidla**
		- Definice toho jak se ze surových dat počítají agregace a materilizované pohledy
	- **Strategie partitioningu**
		- Jak jsou tabulky fyzicky rozřezané na disku
	- **Indexace**
		- Popis indexů, které zrychlují vyhledávání na pozadí
	- **Archivace a Purging**
		- Pravidla pro životní cyklus dat
## Metadata pro koncového uživatele
- Slouží k tomu aby uživatelé a datový analytici mohli porozumět datům
- Business jména sloupců, tabulek
- Hierarchie
- Skupiny požadavků
- Vlastníci dat
- Indikátor kvality dat
## Standardizace
- V DW se typicky kombinují nástroje od různých výrobců
- Nutnost umožnění výměny mezi těmito systémy
- **Standardy:**
	- **Common Warehouse Metamodel**
		- Celosvětový standard
		- Definuje jednotný matematický a logický model pro popis celého DW
# 7. Plnění datového skladu, datová pumpa, proces ETL (extrakce, transformace a vložení dat). Kvalita dat, metody čištění dat.

## Plnění datového skladu
- Bulk load X Insert
	- Bulk load bývá optimalizovanější pro vkládání velkého množství dat
- Strategie indexů při plnění:
	- Pokud se tabulka při nahrávání zvětší o víc jako 10-20% je vhodné index zahodit a vytvořit poté znovu
- Inkrementální X Full-load
### Datová pumpa
- = ETL
- ![[Pasted image 20260102220508.png]]
- Tříkrokový proces
### Proces
#### 1. Fáze – Extract
- Nezpracovaná data se čtou a shromažďují z různých zdrojů v různých formátech
- Je nutno chápat v jaké formě a formátu jsou data a systémy, které data generují
- Je potřeba rozhodnout jak často se připojovat ke zdroji dat
- **Výzvy:**
	- **Oprávnění** – mají sítě a systémy přístup a práva k datům
	- **Integrita a přesnost**
	- **Ztráta dat** – dokážeme data získat než projdou svou životností
	- **Dostupnost a škálovatelnost** – máme dostatek úložiště a výpočetní kapacity
#### 2. Fáze – Transform
- Obchodní pravidla se v této fázi používají k **čištění dat**
- Provádění operací s data za účelem **agregace**
- **Formátování dat**
- Na konci kroku jsou data ve správně formě pro uložení do DW
- **Aktivity:**
	- Odvození vypočtených hodnot na základě nezpracovaných dat
	- Přeuspořádání nebo transpozice dat
	- Přidání metadat
	- Odstranění redundance
	- Kódování/dekódování
	- Ověřování
- **Výzvy:**
	- Výpočetní výkon a dostupné zdroje
#### 3. Fáze – Load
- Data se načtou do datového úložiště
- Proces může být: 
	- Jednoduchý => nestrukturovaný textový soubor
	- Složitý => datové sklady
- Proces se značně liší podle obchodních požadavků
## Kvalita dat, metody čištění dat.
- Základní postupy:
	- Standardizace
	- De-duplikace
	- Doplnění chybějících hodnot
- **Techniky:**
	- **Položky obsahující neúplné chybějící hodnoty:**
		- Zahození celého nekompletního záznamu
		- Doplnění pomocí vypočítaného průměru, nebo předem stanovenou konstantou
		- Predikce
	- **Položky obsahující chybné hodnoty:**
		- Binding – hodnoty se opravují na základě jejich okolí
		- Shlukování, regrese
	- **Problémy při integraci z více zdrojů:**
		- Řešení konfliktů hodnot atributů u ekvivalentních entit
		- Odstraňování redundance
		- Generalizace (nahrazení dat nižší úrovně za úroveň vyšší)
## Alternativa pro Big Data
### ETL vs. ELT
- **ELT** = Extract Load Transform
	- Alternativní proces
	- Zdrojová data se přímo načtou do DB a následně dochází k transformaci
	- Populární díky cloudové infrastruktuře
		- K transformaci lze využít výpočetní výkon a rozsah cloudu
	- Big Data, Hadoop
	- Vhodné pro velké data# 8. Principy zpracování přirozeného jazyka – tokenizace, stemming, Porterův algoritmus, lematizace, parsing, slovníky. Modely pro reprezentaci a zpracování rozsáhlých nestrukturovaných dat, vektorový model dokumentu.
# 8. Principy zpracování přirozeného jazyka – tokenizace, stemming, Porterův algoritmus, lematizace, parsing, slovníky.
- **Základní defninice:**
	- **word** = oddělený řetězec znaků v takové formě v jaké se objevuje v textu
	- **term** = normalizované slovo
	- **token** = konkrétní výskyt **word** nebo **term** v dokumentu
		- Př.: *Kočka běží. Kočka skočila*
			- 4 tokeny
	- **type** = většinou to samé jako **term**, unikátní tvar slova
		- Př.: *Kočka běží. Kočka skočila*
		- 3 typy
	- **Třídy ekvivalence:**
		- Soundex = fonetická ekvivalence
		- Thesauri = sémantická ekvivalence
### Normalizace
- = převedení různých tvarů jednoho slova na jednotný tvar
- Třídy ekvivalence slov
- Při normalizaci může nastat problém pokud máme více jazyků
	- Př.:
		- *PETER WILL NICHT MIT* => MIT $=$ mit
		- *He got his PhD from MIT* => MIT $\neq$ mit
### Asymetrická expanze
- = opak normalizace
- Rozšiřujeme význam jednotlivých slov
	- Př.: window => window, windows
- Přesnější ale méně efektivní
### Tokenizace
- = rozdělení dokumentu na tokeny
- **Problémy:**
	- Jedno nebo více slov
		- Hawlett-Packard => 2 tokeny nebo 1?
	- Čísla
		- 3/20/91 => jedno číslo nebo každé číslo zvlásť?
		- Starší IR systémy neindexovali čísla
	- Neoddělování slova mezerami
	- Čtení textu z prava do leva, nebo dokonce obousměrně
	- Diakritika, akcenty
	- Malá a velká písmena
	- Stop slova = často se vyskytující slova, která nepomáhají s vyhledáváním
### Stemming
- Heuristická metoda
- Jedna z normalizačních technik
- Napodobuje lematizaci
- Osekává slova
- Závislý na jazyku
- Př.:
	- **Vstup**: gooning, gooner
	- **Výstup:** goon
#### Porterův algoritmus
- Nejpoužívanější stemmer pro angličtinu
- Postupně aplikuje 5 fází přepisovacích pravidel
- Vždy vybírá pravidlo s nejdelší shodou
- ![[Pasted image 20260529185624.png]]
#### Zvyšuje stemming efektivitu?
- Někdy jo někdy ne
- **Kdy stemming pomáhá:**
	- V dotazu jsou pouze slova, které jsou variantami stejného základu
- **Kdy stemming škodí:**
	- V dotazu jsou slova, u kterých stemming změní jejich význam nebo kontext
### Lematizace
- = redukce slov do jejich základního tvaru
- Např.:
	- auto auta => auto
	- am, are, is => be
- Provádí gramaticky správné převedení do na základní tvar slova
- Bere v úvahu i gramatický kontext
	- Mnohdy přesnější jak stemming
	- Výpočetně náročnější
#### Inflexní VS Derivační morfologie
- **Inflexní**
	- Slova mají stejný význam ale jiný tvar
	- Př.: cutting => cut
- **Derivační**
	- Slova mají rozdílný význam, tvar i slovní druh
	- Př.: destruction => destroy
### Parsing
- = automatizovaný proces, který provádí extrakci čistého textu z různých formátů
1. **Constituency Parsing:** Rozděluje větu hierarchicky na ucelené fráze/konstituenty (jmenná fráze NP, slovesná fráze VP). Sleduje pozici slov.
	- Příklad věty: "Pepa pije pivo."
```
        [S - Celá věta]
         /           \
    [NP - Podmět]   [VP - Přísudek]
         |             /         \
      (Pepa)    [V - Sloveso]  [NP - Předmět]
                       |              |
                    (pije)          (pivo)
```
2. **Dependency Parsing:** Nezajímá se o fráze, ale buduje strom přímých gramatických závislostí mezi samotnými slovy. Centrem (kořenem) je obvykle hlavní sloveso.

	- Příklad věty: "Ziki vlastní lihovar."
	```
            [vlastní] (Kořen / Sloveso)
             /     \
            /       \
  (nsubj)  /         \  (obj)
          ▼           ▼
       [Ziki]     [lihovar]
	```
	- (Vysvětlivky vztahů: nsubj = jmenný podmět/subject, obj = předmět/object)
### Slovníky
- Datová struktura pro efektivní ukládání a správu term
	- **Term vocabulary** = data
		- Např.: konkrétní slova
	- **Dictionary** = struktura, ve které jsou data organizovaná
- **Hlavní účel:**
	- Rychlé vyhledávání termů během zpracování dotazu
	- Mapování slov na jejich pozice v invertovaném indexu
- Pro každý term se uchovává víc věcí:
	- Document frequency
	- Pointer na postings list
- **Nejčastější implementace:**
	- Hash tabulka
	- Strom
#### Hash tabulka
- Každý term je zahashován
- Snažíme se vyhnout kolizím
- **Výhody:**
	- Vyhledávání je O(1)
- **Nevýhody:**
	- Nejdou rozeznat drobné rozdíly mezi slovy (*resume* vs *résumé*)
	- Žádné prefixové/sufixové vyhledávání
	- Nutnost přehashovat při zvětšování slovníku
#### Stromy
- Řeší problém s prefix u hash map
- Vyhledávání je pomalejší $O(\log(n))$
	- Platí pouze pro vybalancované stromy
- Nejjednodušší strom – binární strom
- Využívají se hlavně B-stromy kvůli odstranění rebalancování
- **Wildcard dotazy:**
	- *mon\**: najdi všechny dokumenty, které obsahují term začínající na *mon*
		- Pro B-stromy jednoduché
		- Hledáme všechny termy $t$ v rozsahu $mon \leq t \lt moo$
	- *\*mon*: najdi všechny dokumenty, které obsahují term končící na *mon*
		- U B-stromů je nutné mít druhý strom, který obsahuje termy po zpátku
		- V něm nalezneme všechny termy $t$ v rozsahu $nom \leq t \lt non$
	- Problém pokud je * uprostřed (řešení Permuterm nebo K-gram index)
- **Permuterm index**
	![[permuterm_tree.excalidraw]]
	- Př.: pro hel\*o hledáme o$hel*
	- **Problém:** index je víc jak $4\times$ větší než obyčejný B-strom
- **K-gram index**
	- Šetří paměť více, než permuterm index
	- Vytvoříme všechny k-gramy jednoho termu
	- Př.:
		- *April is the cruelest month*
		- `$a ap pr ri il l$ $i is s$ $t th he e$ $c cr ru ue el le es st t$ $m mo on nt th h$`
	- Udržujeme invertovaný index k-gramů, který mapuju k-gram na původní slovo
	- Dotaz: mon\* může být vyhledán jako: `$m AND mo AND on`
		- Vrátí všechny termy začínající prefixem mon
		- Můžeš vracet i false positives např. MOON
	- Je nutné provést post-filtraci
- **Permuterm vs K-gram index**
	- K-gram index šetří pamětí
	- Permuterm index nevyžaduje post-filtraci
## Modely pro reprezentaci a zpracování rozsáhlých nestrukturovaných dat, vektorový model dokumentu.
### Reprezentace (AI Generated, možná bych tady zkusil yappovat o věcech z 1,2,3)
- NoSQL datové modely
- Nestrukturovaná data nejde uložit do SQL DB
- **Dokumentová prezentace**
- **Sloupcová prezentace**
- **Grafová prezentace**
- **Data Lakes**
#### Binární matice sousednosti

|         | dokument 1 | dokument 2 | ... | dokument N |
| ------- | ---------- | ---------- | --- | ---------- |
| slovo 1 | 1          | 0          | ... | 0          |
| slovo 2 | 0          | 1          | ... | 1          |
| ...     | 0          | 0          | ... | 1          |
| slovo M | 1          | 1          | ... | 1<br>      |
#### Matice četností
|         | dokument 1 | dokument 2 | ... | dokument N |
| ------- | ---------- | ---------- | --- | ---------- |
| slovo 1 | 20         | 2          | ... | 31         |
| slovo 2 | 12         | 133        | ... | 9          |
| ...     | 4          | 53         | ... | 23         |
| slovo M | 8          | 7          | ... | 90         |
#### Bags-of-words model
- Neřeší pořadí slov v dokumentu
- Př.: *kočka leze dírou* je to samé jako *dírou kočka leze*
- **Term Frequency ($TF$)**: $TF_{t,d} = \text{počet výskytů termu t v dokumentu d}$
	- Využívání přímo hodnoty $TF$ není přesné
		- Důvod:
			- Pokud se nějaký term vyskytuje v jednou dokumentu 10 a v druhém 1 neznamená to, že první dokument je 10x víc relevantní
- **Weighted Term Frequency ($WTF$)**: $\text{WTF}_{t,d} = 1 + \log(\text{TF}_{t,d})$
	- Hodnota snižuje vliv velké četnosti termu
- **Document Frequency ($DF$)**: $DF_t = \text{počet dokumentů, kde se term t vykystuje}$
	- Opak informativnosti termu $t$
- **Inversed Document Frequency $IDF$:** $IDF_t = \log(\frac{N}{DF_t})$, kde $N$ je celkový počet dokumentů
	- Zvyšuje vliv termů s menší četností
### Zpracování
- Nejlepší by bylo vytvářet celý index v RAM => nejde dat je moc
- Jsou nutné algoritmy, které umí dobře využít disky
#### BSBI (Block Sort-Based Indexing)
- BSBI funguje na principu: **„Nasypej surová data do paměti, na konci je hromadně setřiď a pak z nich vyrob index.“**
	1. **Překlad na čísla:** Alokátor má v paměti velký globální slovník. Každému novému slovu přiřadí ID číslo (_„pes“_ $\rightarrow$ 1, _„pivo“_ $\rightarrow$ 2). Celý text tak převede na čísla
	2. **Plnění RAM:** Čte dokumenty a do paměti RAM ukládá prosté dvojice čísel `(TermID, DocID)`. Jak slova přicházejí v textu, tak padají do jednoho obřího lineárního pole. V tuto chvíli v paměti **neexistuje žádný invertovaný index**, jen miliony nesetříděných dvojic za sebou
	3. **Hromadný QuickSort:** Když je paměť plná, alokátor spustí nad celým tím obřím polem klasický třídicí algoritmus (např. QuickSort). Seřadí ty miliony dvojic primárně podle `TermID` a sekundárně podle `DocID`
	4. **Zápis:** Teprve z tohoto setříděného pole bleskově vytvoří strukturu indexu (postings listy) a spláchne ji na disk jako jeden soubor (blok)
- Musíme se držet mapování termID na term
	- Pokud bude index moc velký tak se ani to mapování nevejde do RAM
	- Alternativa: nepoužívat mapování => zvětšení dočasných souborů na disku
#### SPIMI (Single-Pass In-Memory Indexing)
- SPIMI funguje na principu: **„Žádné ukládání dvojic, žádný velký sort na konci. Stavěj funkční invertovaný index v paměti od prvního slova.“**
	1. **Práce s textem:** SPIMI nepotřebuje žádný předem připravený globální slovník čísel. Pracuje přímo se samotnými slovy (stringy)
	2. **Průběžná stavba indexu:** Čte první dokument. Vidí slovo _„pes“_. Podívá se do své hashovací tabulky v RAM.
	    - Pokud tam slovo není, vytvoří pro něj nový klíč a otevře pod ním nový, prázdný postings list (pole), kam zapíše aktuální `DocID` $\rightarrow$ `"pes" -> [D1]`
	    - Pokud už tam slovo je, rovnou skočí na konec jeho postings listu a připíše tam aktuální `DocID`
	    - **Výsledek:** Invertovaný index ti v RAM vzniká a roste **průběžně, krok za krokem**, s každým přečteným slovem. Žádné samostatné dvojice v paměti nehnijí
	3. **Konec RAM a abecední flush:** Když paměť signalizuje, že je plná, alokátor nemusí třídit miliony prvků. Postings listy už má hotové a seřazené (protože ID dokumentů jdou přirozeně vzestupně, jak dokumenty čte). Udělá pouze to, že vezme klíče slovníku (slova), bleskově je seřadí podle abecedy a tento hotový sub-index vysype na disk
#### Distribuované indexování
- **Master** rozděluje práci na paralelní úkoly, které dává **slaves**
- Dva typy paralelních úkolů:
	- **Parsers**
	- **Inverters**
- **MapReduce**
	- **Parsers**
		- **Master** přidělí části dokumentů jednotlivým **parser** strojům, které nic nedělají
		- **Parser** čte dokumenty a vytváří (term, docID) dvojice
		- Parser zapisuje data do **j term-partitions**
	- **Inverters**
		- Bere dvojice (term, docID) pro každou **j term-partition**
		- Seřadí a zapisuje do **postings listu**
	- **Dataflow**
		- ![[Pasted image 20250406233653.png|600x300]]
#### Dynamické indexování
- **Jednoduchý přístup**
	- Máme uložený jeden velký index na disku
	- Pro nové dokumenty je v paměti malý pomocný index
	- Periodicky mergujeme pomocný index s indexem na disku
	- **Problémy při slučování:**
		- Časté slučování může zpomalit vyhledávání
		- Slučování není nákladné pokud je pro každý postings list samostatný soubur, ale to vede k mnoha souborům a neefektivitě
	- **Řešení:**
		- Kompromis:
			- Velké postings listy jsou rozděleny do více souborů
			- Malé postings listy jsou seskupeny do jednoho souboru
- **Logaritmické slučování**
	- Rozkládá náklady na slučování indexů v čase, což snižuje dopad na dobu odezvy pro uživatele
	- **Princip:**
		- V RAM máme malý, dynamický index označený jako $Z_0$
		- Na disku mám připravené pozice pro indexy $I_0, I_1 \dots$
		- Každý index $I_i$ má kapacitu přesně $2^i \times |Z_0|$
			1. **Pokud je pozice $I_0$ volná (bit 0):** Index $Z_0$ se prostě zapíše na disk jako $I_0$. Paměť $Z_0$ se vymaže a přijímá další data. (Stav disku: `0001`)
			2. **Pokud na pozici $I_0$ už index existuje (bit 1):** Nastává kolize. Vezmeme $Z_0$ z paměti a existující $I_0$ z disku. **Slijeme je dohromady** (Merge Sortem) do jednoho dvojnásobného bloku.
			    - Podíváme se na pozici $I_1$. Pokud je volná, uložíme tento slitý blok tam jako $I_1$. Původní $I_0$ z disku smažeme. (Stav disku: `0010`)
			3. **Kaskádový přenos (Chain Reaction):** Pokud by byla plná i pozice $I_1$, vezmeme ten nový slitý blok, vezmeme existující $I_1$, opět je slijeme do čtyřnásobného bloku a zkusíme ho uložit na pozici $I_2$. Tento proces putuje nahoru, dokud nenajde volnou pozici, přesně jako když přičteš `1` k číslu `0111` $\rightarrow$ vznikne `1000`
#### Crawlery
- **Základní operace:**
	- Fronta s uloženými URL seed stránek
	- Smyčka:
		- Výběr URL z fronty
		- Načti stránku
		- Načti URL, které jsou na stránce
		- Přidej načtené URL do fronty
	- **Základní předpoklad:** web je dobře prolinkovaný
- **Požadavky na Crawler:**
	- Škálovatelnost
	- Výběr vhodných podmnožin stránek
	- Odstranění duplikací
	- Detekce spamu a pastí
	- Slušnost
	- Čerstvost
- **Protokol Robots.txt** = říká Crawleru, které stránky v rámci domény může navštívit
- **Základní architektura**
	- ![[crawler_arch.excalidraw|{width=100%}]]
-  **Architektura distribuovaného Crawleru**
	- ![[crawler_distrubuted_arch.excalidraw|{width=100%}]]
- Každý server s crawlerem může být na jiné lokaci
- **URL Frontier**
	- ![[url_frontier.excalidraw|{width=100%}]]
	- = datová struktura, která udržuje s spravuje URL, které zatím Crawler nezpracoval, ale někdy v budoucnu je bude zpracovávat
	- Struktura musí opět zajistit **slušnost** crawleru a **čerstvost** dat
		- **Architektura:**
			- ![[url_frontier_architecture.excalidraw]]
			- **Prioritizátor** nejprve rozdělí URLs do předních front podle jejich priorit
			- Následně jsou z předních front vybrány URLs k zpracování v zadních frontách
				- Ze, které přední fronty se výbírá může být provedeno např. pomocí RoundRobin, náhodně, nebo nějakým sofitikovanšjsím způsobem
			- Vybrané URLs z předních front se předávají do zadních front
				- Každá zadní fronta reprezentuje jednoho hosta (např. fronta 1 reprezentuje www.instagram.com)
				- Celkový počet $B$ zadních front se odvíjí od počtu vláken crawleru (většinou $B = 3 \times \texttt{počet vláken}$)
			- **Halda** obsahuje jeden záznam pro každého hosta ze zadní fronty
				- Záznam obsahuje nejbližší čas $t_e$, ve kterém může být proveden nový request na hosta
				- ![[url_frontier_heap.excalidraw]]
### Vektorový model dokumentu
- ![[doc_vector_space.excalidraw]]
- Každý dokument je reprezentován jako **vektor reálných čísel** v mnohorozměrném prostoru $\mathbb{R}^{|V|}$
	- Jednotlivé osy prostoru jsou termy ze slovníku $|V|$
	- Jednotlivé body v prostoru jsou dokumenty
- **Vlastnosti prostoru:**
	- Vysoká dimenzionalita
	- Řídké vektory
- **Klíčová myšlenka:**
	1. Převést uživatelský dotaz na vektor ve stejném prostoru jako dokumenty
	2. Hodnocení dokumentů podle jejich blízkosti k dotazu
#### Podobnost vektorů
- **Eukleidovská vzdálenost:**
	- Není vhodná, protože i když mají vektory stejný směr ale rozdílnou délku jejich vzdálenost může být velká
- **Cosinova podobnost:**
	- Je vhodná, protože počítá zda vektory ukazují stejný směrem, tj. mají podobný význam
	- Vztah:
$$
\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|} = \frac{\sum_{i=1}^{n}a_i \cdot b_i}{\sqrt{\sum_{i=1}^{n}a_i^2} \cdot \sqrt{\sum_{i=1}^{n}b_i^2}}
$$
#### Normalizace vektorů
- Je vhodné vektory normalizovat na jednotkovou kružnici
$$
\|A\| = \sqrt{\sum a_i^2}
$$
- Tím se zjednoduší výpočet cosinovo podobnosti na pouhé skalární násobení vektorů
- **Problém s pouhou normalizací na jednotkovou kružnici**
	- Pokud vektory normalizujeme pouze na jednoutkovou kružnic, tak krátké dokumenty mají větší šanci, že budou vyhodnoceny jako relevatnější pro nějaký dotaz
	- Řeší se to tak, že místo normalizace na jednotkovou kružnici se nalezne nějaký pivot podle, kterého se normalizuje
		- $norm = a \cdot |\vec{d}| + (1-a)\text{piv}$
	- Tím se stane normalizace závislá na délce dokumentů a tudíž kratší dokumenty nebudou ve výhodě
# 9. Vyhledávání v rozsáhlých textových/nestrukturovaných datech – booleovský model, indexování. Podobnost dotazu s dokumentem, vyhodnocování relevance. Systémy odpovídání otázek. Multimedia Information retrieval.
## Vyhledávání v rozsáhlých textových/nestrukturovaných datech – booleovský model, indexování.
- **Nestrukturovaná data** = nemají předem definovaný pevný datový model (multimédia)
- **Textová data** = data reprezentovaná ve formě sekvence znaků (řetězců), které jsou kódovány v nějakém standardu
	- Strukturovaný text – CSV
	- Semi-strukturovaný text – JSON, XML, HTML
	- Nestruktorovaný text – volně psaný text
- **Vyhledávání obecně:**
	- Možné nad dokumenty/objekty/entitami, které jsou strojově čitelné
	- **Nástroje:**
		- Fulltextové vyhledávače, index
		- Databáze
	- **Aplikace v praxi:**
		- Webové vyhledávače
		- GIS
	- Kompletní vyhledávací systém
		- ![[complete_search_system.excalidraw]]
- **Wildcard dotazy:**
	- *mon\**: najdi všechny dokumenty, které obsahují term začínající na *mon*
		- Pro B-stromy jednoduché
		- Hledáme všechny termy $t$ v rozsahu $mon \leq t \lt moo$
	- *\*mon*: najdi všechny dokumenty, které obsahují term končící na *mon*
		- U B-stromů je nutné mít druhý strom, který obsahuje termy po zpátku
		- V něm nalezneme všechny termy $t$ v rozsahu $nom \leq t \lt non$
	- Problém pokud je * uprostřed (řešení Permuterm nebo K-gram index)
- **Frázové dotazy**
	- Kolem $10\%$ dotazů na webu jsou frázové dotazy
	- Takové dotazy ale nejsou vhodné pro standardní invertovaný index
		- Př.:
			- Uživatel zadá query: *stanford university*
			- Očekává, že dostane výsledky o Stanford univerzitě
			- Ale, jestliže existuje dokument *The inventor Stanford Ovshinsky never went to university*, v klasickém booleovském vyhledávání dostane uživatel i tento výsledek
	- Kvůli těmto dotazů je nutné invertovaný index upravit na:
		- **biword index**
		- **positional index**
### Booleovský model
- Použití operací: `AND, OR, NOT`
- Operace využívá nad invertovaným indexem
- Příklad:
	```
	"slovo1": [1, 2, 5, 7],
	"slovo2": [3, 5, 11],
	"slovo3": [2, 5, 11]
	```
	- Dotaz: `slovo1 AND slovo3`
	- Výsledek: dokumenty 2, 5
- Složité vytvořit dotazy, které najdu pouze požadované dokumenty
- Problém s vyhledáváním:
	- **feast** – nalezeno až moc dokumentů
	- **famine** – nenalezen žádný dokument
- **Optimalizace:**
	- Minimalizace NOT operací v dotazech
	- Při slučování mít levou množinu menší jak pravou
- Pro seřazení výsledků by se dal teoreticky použít Jaccard
### Indexování
- **Motivace**
	- **Omezení HW (Proč potřebujeme index):**
		- Data jsou rychleji přístupná v RAM než na disku
		- Ztráta času – když potřebujeme načíst data z disku můžeme ztratit čas pohybem hlavičky na správné místo disku
		- Blokové čtení – data se z disku do paměti zapisují po celých blocích
		- Cena za spolehlivost – je levnější zajistit odolnost vůči chybám na cluster z menších zařízení, než na jednom giga-PC
	- **Cíl indexování:**
		- Místo prohledávání celých textů vytvoříme datovou strukturu (index)
		- Vyhledávač se díky tomu vyhne drahým operacím
#### Datové struktury pro index
- **Hash Mapy**
	- Každý term ja zahashován
	- Snažíme se vyhnout kolizím
	- **Výhody:**
		- Vyhledávání O(1)
	- **Nevýhody:**
		- Nejdou rozpoznat drobné rozdíly mezi slovy
		- Žádné prefixové/sufixové vyhledávání
		- Nutnos přehashovat při zvětšování
- **Stromy**
	- Řeší problém s prefixy
	- Vyhledávání $O(\log(n))$
	- B-Stromy
#### Typy indexů
##### Invertovaný index
- Hash mapa, kde jsou klíčem jednotlivé terms a hodnoty jsou dokumenty, kde se term vyskytuje
	- Př.:
```
inverted_index = {
	"slovo1": [1, 5, 10, 12, 16],
	"slovo2": [6, 8, 20, 60],
	...
	"slovoN": [1, 4, 10]
}
```
- ID dokumetů = postings list – chceme jako spojový seznam (jednoduché a rychlé řazení + operace hledání průniku)
- **Algoritmus nalezení průniku dokumentů**
	- Pokud máme seřazené pole ID dokumkentů je možné nalézt průnik v čase $O(n)$
	- ![[intersect_inverted_index.excalidraw]]
	- **Urychlení pomocí skip pointerů**
		- V seznamu ukazatelů se nastaví krok pevné délky, který se následně budu používat na přeskakování
			- => vytvoří se tzv. **skip list**
		- Vyhledávání funguje stejně jako v případě prostého hledání průniku, ale po urychlení si využije **skip list**
		- Je třeba najít ideální velikost jednoho **skipu**
			- Jednoduchá heuristika $\sqrt{P}$, kde $P$ je délka seznamu ID dokumentů 
		- Na dnešních CPU urychlení není příliš veliké
###### Biword index
- Indexují se po sobě jdoucí páry termů
- **Př.:**
	- *Friends, Romans, Countryman* => "friends roman", "romans countrymen"
- Lehčí vyhledávání dvouslovných frází
- Př. vyhledávání:
	- Fráze: *stanford university palo alto*
	- Hledáme průnik všech dokumentů, které mají jako klíč:
		- "stanford university"
		- "universtity palo"
		- "palo alto"
- **Rozšířený Biword index**
	- Analyzujeme každý dokument a jednotlivým slovům přiřadíme slovní druh
	- Rozdělíme termy na např. podstatná jména (**N**) a spojovací slova jako je *in, of, ...* (**X**)
	- Nyní označíme každé slovo ve tvaru **NX\*N\***** jako rozšířené Biword
		- Např.:
			- *catcher in the rye* (**NXXN**)
	- Rozšířené Biword dáme do indexu
	- Dotazy jsou následně zpracovány pomocí rozšířeného indexu
	- **Nevýhody:**
		- Index může obsahovat nežádoucí slovní spojení
		- Index se bude extrémně zvětšovat
###### Positional index
- Efektivnější alternativy k biword indexu
- V indexu jsou uloženy, jak ID dokemntů, kde se slovo nachází, tak jeho pozice
- Př.:
	- Dotaz: *to be*
	- **Index**:
	    ```
		"to": {[
		    1: [7, 18, 33],
		    2: [8, 16, 190]
		]}
		"be": {[
		    1: [17, 25],
		    2: [17, 191]
		]}
	    ```
	- Z indexu je vidět, že slova *to be* jdou po sobě v dokumentu 2
- Index lze také využít k vyhledávání v okolí slov
	- Př.: 
		- Dotaz: *employment /4 place*
		- Význam: najdi všechny dokumenty, kde jsou od sebe slova *employment* a *place* vzdáleny 4 slova
		- Pozice slov v dokumentu X:
		```
		"employment": [2, 10, 20],
		"place": [5, 15]
		```
		- Všechny dvojice: `(2,5); (2,15); (10,5); (10,15); (20,5); (20,15)`
			- Z nich hledáme dvojice, kde jejich rozdíl v absolutní hodnotě je $\leq 4$
###### Kombinovaný index
- Kombinace biword a positional indexu
- Mnoho bislov je velice častých, např.: *Michael Jackson*
- Hledání takových bislov v biword indexu je výrazně rychlejší než použití positional
- Index využívá biword index pro častá bislova a positional index pro všechno ostatní
###### Permuterm index
- ![[permuterm_tree.excalidraw]]
	- Př.: pro hel\*o hledáme o$hel*
	- **Problém:** index je víc jak $4\times$ větší než obyčejný B-strom
###### K-gram index
- Šetří paměť více, než permuterm index
- Vytvoříme všechny k-gramy jednoho termu
- Př.:
	- *April is the cruelest month*
	- `$a ap pr ri il l$ $i is s$ $t th he e$ $c cr ru ue el le es st t$ $m mo on nt th h$`
- Udržujeme invertovaný index k-gramů, který mapují k-gram na původní slovo
- Dotaz: mon\* může být vyhledán jako: `$m AND mo AND on`
	- Vrátí všechny termy začínající prefixem mon
	- Můžeš vracet i false positives např. MOON
- Je nutné provést post-filtraci
#### Způsoby tvorby indexů
##### BSBI (Block Sort-Based Indexing)
- BSBI funguje na principu: **„Nasypej surová data do paměti, na konci je hromadně setřiď a pak z nich vyrob index.“**
	1. **Překlad na čísla:** Alokátor má v paměti velký globální slovník. Každému novému slovu přiřadí ID číslo (_„pes“_ $\rightarrow$ 1, _„pivo“_ $\rightarrow$ 2). Celý text tak převede na čísla
	2. **Plnění RAM:** Čte dokumenty a do paměti RAM ukládá prosté dvojice čísel `(TermID, DocID)`. Jak slova přicházejí v textu, tak padají do jednoho obřího lineárního pole. V tuto chvíli v paměti **neexistuje žádný invertovaný index**, jen miliony nesetříděných dvojic za sebou
	3. **Hromadný QuickSort:** Když je paměť plná, alokátor spustí nad celým tím obřím polem klasický třídicí algoritmus (např. QuickSort). Seřadí ty miliony dvojic primárně podle `TermID` a sekundárně podle `DocID`
	4. **Zápis:** Teprve z tohoto setříděného pole bleskově vytvoří strukturu indexu (postings listy) a spláchne ji na disk jako jeden soubor (blok)
- Musíme se držet mapování termID na term
	- Pokud bude index moc velký tak se ani to mapování nevejde do RAM
	- Alternativa: nepoužívat mapování => zvětšení dočasných souborů na disku
##### SPIMI (Single-Pass In-Memory Indexing)
- SPIMI funguje na principu: **„Žádné ukládání dvojic, žádný velký sort na konci. Stavěj funkční invertovaný index v paměti od prvního slova.“**
	1. **Práce s textem:** SPIMI nepotřebuje žádný předem připravený globální slovník čísel. Pracuje přímo se samotnými slovy (stringy)
	2. **Průběžná stavba indexu:** Čte první dokument. Vidí slovo _„pes“_. Podívá se do své hashovací tabulky v RAM.
	    - Pokud tam slovo není, vytvoří pro něj nový klíč a otevře pod ním nový, prázdný postings list (pole), kam zapíše aktuální `DocID` $\rightarrow$ `"pes" -> [D1]`
	    - Pokud už tam slovo je, rovnou skočí na konec jeho postings listu a připíše tam aktuální `DocID`
	    - **Výsledek:** Invertovaný index ti v RAM vzniká a roste **průběžně, krok za krokem**, s každým přečteným slovem. Žádné samostatné dvojice v paměti nehnijí
	3. **Konec RAM a abecední flush:** Když paměť signalizuje, že je plná, alokátor nemusí třídit miliony prvků. Postings listy už má hotové a seřazené (protože ID dokumentů jdou přirozeně vzestupně, jak dokumenty čte). Udělá pouze to, že vezme klíče slovníku (slova), bleskově je seřadí podle abecedy a tento hotový sub-index vysype na disk
##### Distribuované indexování
- **Master** rozděluje práci na paralelní úkoly, které dává **slaves**
- Dva typy paralelních úkolů:
	- **Parsers**
	- **Inverters**
- **MapReduce**
	- **Parsers**
		- **Master** přidělí části dokumentů jednotlivým **parser** strojům, které nic nedělají
		- **Parser** čte dokumenty a vytváří (term, docID) dvojice
		- Parser zapisuje data do **j term-partitions**
	- **Inverters**
		- Bere dvojice (term, docID) pro každou **j term-partition**
		- Seřadí a zapisuje do **postings listu**
	- **Dataflow**
		- ![[Pasted image 20250406233653.png|600x300]]
##### Dynamické indexování
- **Jednoduchý přístup**
	- Máme uložený jeden velký index na disku
	- Pro nové dokumenty je v paměti malý pomocný index
	- Periodicky mergujeme pomocný index s indexem na disku
	- **Problémy při slučování:**
		- Časté slučování může zpomalit vyhledávání
		- Slučování není nákladné pokud je pro každý postings list samostatný soubur, ale to vede k mnoha souborům a neefektivitě
	- **Řešení:**
		- Kompromis:
			- Velké postings listy jsou rozděleny do více souborů
			- Malé postings listy jsou seskupeny do jednoho souboru
- **Logaritmické slučování**
	- Rozkládá náklady na slučování indexů v čase, což snižuje dopad na dobu odezvy pro uživatele
	- **Princip:**
		- V RAM máme malý, dynamický index označený jako $Z_0$
		- Na disku mám připravené pozice pro indexy $I_0, I_1 \dots$
		- Každý index $I_i$ má kapacitu přesně $2^i \times |Z_0|$
			1. **Pokud je pozice $I_0$ volná (bit 0):** Index $Z_0$ se prostě zapíše na disk jako $I_0$. Paměť $Z_0$ se vymaže a přijímá další data. (Stav disku: `0001`)
			2. **Pokud na pozici $I_0$ už index existuje (bit 1):** Nastává kolize. Vezmeme $Z_0$ z paměti a existující $I_0$ z disku. **Slijeme je dohromady** (Merge Sortem) do jednoho dvojnásobného bloku.
			    - Podíváme se na pozici $I_1$. Pokud je volná, uložíme tento slitý blok tam jako $I_1$. Původní $I_0$ z disku smažeme. (Stav disku: `0010`)
			3. **Kaskádový přenos (Chain Reaction):** Pokud by byla plná i pozice $I_1$, vezmeme ten nový slitý blok, vezmeme existující $I_1$, opět je slijeme do čtyřnásobného bloku a zkusíme ho uložit na pozici $I_2$. Tento proces putuje nahoru, dokud nenajde volnou pozici, přesně jako když přičteš `1` k číslu `0111` $\rightarrow$ vznikne `1000`
#### Komprese indexu
- Šetření pamětí
- Zvýšení rychlosti
- **Ztrátová vs Bezztrátová komprese**
	- Jako ztrátová komprese může být brán i preprocessing
	- Bezztrátová komprese = všechny informace jsou zachovány
- **Velikost slovníku:**
	- Nejde přesně určit, je veliký alespoň $10^{37}$
	- **Heapsův zákon:**
		- $M = k \cdot T^b$
			- $M$ – velikost slvoníku
			- $T$ – počet tokenů
			- $k,b$ – konstanty, kd $30 \leq k \leq 100, b \approx 0.5$
- **Četnost výskytů termů:**
	- **Zipfův zákon:**
		- $i$-tý nejčastější term má frekvenci proporcionální k $\frac{1}{i}$
##### Komprese termů
- **Slovník jako řetězec**
	- ![[Pasted image 20250407100547.png]]
	- Potřebné místo pro jeden záznam: $4 + 4 + 3$ = $11$ bytů
- **Slovník jako řetězec bloků**
	- ![[Pasted image 20250407100901.png]]
	- Pokud máme velikost bloku např.: $k = 4$ (4 slova v jednom bloku)
	- Využíváme 3 byty pro jeden ukazatel + 4 byty pro indikaci délky jednotlivých termů
	- Uštříme: $12 - (3 + 4) = 5$ bytů každý blok
	- Hledání termů je o trošku pomalejší
- **Front Coding**
	- ![[Pasted image 20250407101430.png]]
##### Komprese postingů
- Seznam postingů je alespoň $10 \times$ větší jak slovník
- **Ukládání mezer místo docID**
	- Každej seznam postingů je vzestupně sežazený podle docID
	- **Princip:** ukládáme mezery mezi jednotlivými docID
	![[Pasted image 20250407102750.png]]
	- Používáme mezeri, které jsou menší jak 20 bitů
- **Variable Length Encoding**
	- **Cíl:** 
		- Pro vzácné termy použijeme 20 bitů na každou mezeru
		- Pro časté termy použijeme pouze pár bítů na každou mezeru
	- **Variable Byte (VB) code**
		- **Princip kódování:**
			- **Kódování docID**: Každý `docID` je zakódován jako **gap** (rozdíl mezi předchozím `docID` a aktuálním)
			- **Pokračovací bit (c)**: První bit je použit pro označení zda číslo pokračuje, na dalších 7 bitech je gap
				- Pokud gap nezapadne do 7 bitů, použije se více bajtů
		- **Příklad kódování a dekódování**:
			- **Kódování:**
				- Pokud máme `docIDs = 824, 829, 215406`, použijeme **gap** kódování, kde první číslo je přímo `docID` a každý další `docID` je kódován jako rozdíl mezi tímto číslem a předchozím
					1. **docID 824** (první docID):
					    - **Gap**: 824 (první číslo je vždy přímo `docID`)
					    - Kódování: `00000110 10111000` (binarizace čísla 824)
					2. **docID 829** (gap = 5):
					    - **Gap**: 829 - 824 = 5
					    - Kódování: `10000101` (binarizace gapu 5)
					3. **docID 215406** (gap = 214577):
					    - **Gap**: 215406 - 829 = 214577
					    - Kódování: `00001101 00001100 10110001` (binarizace gapu 214577)
			- **Dekódování**:
				- Po zakódování můžeme pomocí gapů a binárního kódu zpětně rekonstruovat původní `docIDs`.
				- **Jak dekódovat**:
					1. **První číslo**: `00000110 10111000` → `824` (první docID).
					2. **Gaps**:
						- **Gap 5**: `10000101` → přičteme k 824 → `829`.
						- **Gap 214577**: `00001101 00001100 10110001` → přičteme k 829 → `215406`.

| Pořadí | Gaps   | VB kód                       | Výpočet docID             |
| ------ | ------ | ---------------------------- | ------------------------- |
| 1.     | –      | `00000110 10111000`          | **824** (první docID)     |
| 2.     | 5      | `10000101`                   | 824 + 5 = **829**         |
| 3.<br> | 214577 | `00001101 00001100 10110001` | 829 + 214577 = **215406** |
- **Gamma kódy**
	- **Unární kód:**
		- Tolik jedniček jako je veliké číslo + nula na konec
		- 10 = $11111111110$
		- $2 = 110$
	- **Princip:**
		- Mějme nějaké číslo např.: $13$
		- Toto číslo převedeme do bin: $1101$
		- Uřízneme první bit a získávem tzv. **offset** = $101$
		- Určíme délku offset **length** = $3$
		- Převedeme délku do unárního kódování **unary length** = $1110$
		- Výsledný kód je **unary length + offset** = $1110101$
	- **Vlasnosti:**
		- **Prefix-Free:** validní kódové slovo neni prefixem jiného kódového slova
	- **Nevýhody:**
		- Kódy nejsou word-aligned tudíž se zhoršuje rychlost
		- I když je kódování efektivní, VB je jednoduší a vyžaduje poměrně málo paměti navíc
### Neuronové sítě pro IR
- Učení se hustých reprezentací pro vyhledávání
#### Siamské sítě
- Zakódování dotazu a dokumentu zvlášť pomocí stejného **encoder**
- Vypočte se cosinova podobnost mezi embeddingama pro rankování dokumentů
- Sdílené váhy
- ![[siamese-networks.excalidraw]]
#### Cross-Encoder
- Dotaz i dokumentu je předán najednou
- Model vrátí podobnost pomocí FFNN
- Natrénováno na označených párech
- Často lepší jak **siamské sítě**
- Nepočítá cosinovu podobnost
- ![[cross-encoder.excalidraw]]
- **Limitace:**
	- Nedokáže zpracovat samostatné věty => neprodukuje znovupoužitelné embeddingy vět
	- Nemá předpočítané reprezentace dokumentů
	- Náročné na výpočet + pomalé oproti siamským sítím
- **Typické použití:**
	- Použití siamské sítě pro získání top $k$ kandidátů
	- Rerankování pomocí cross-encoderu
#### Pre-trained Sentence Encoders
- Předtrénované modely dotrénovány specificky pro reprezentaci vět tak aby lépe zachycovali sémantický význam
- Např.: Sentence-BERT, BGE, GTE
- **Strategie předtrénování**
	- Páry dotaz-odpověď
	- Trénování na frázích
	- Title-content matching
	- Mezi-jazykové vyhledávání
#### Reprezentace vět bez učitele
1. **SimCSE** (_Simple Contrastive Sentence Embedding_)
	- **Cíl**: Naučit model, aby podobné věty měly podobné vektorové reprezentace (embeddingy), a naopak odlišné věty měly odlišné
	- **Jak to funguje?**
	    - Vezme stejnou větu, dvakrát ji prožene modelem (**použije dropout** – viz níže)
	    - Díky náhodnosti dropoutu dostane **2 mírně odlišné embeddingy téže věty**
	    - Tyto embeddingy slouží jako **"pozitivní pár"** pro kontrastivní učení (model se učí, aby byly co nejbližší)
	    - Jako **"negativní pár"** použije embeddingy jiných náhodných vět (učí se, aby byly vzdálené)
	- **Výhoda**: Nepotřebuje ručně označená data (např. že věty _"Jak se máš?"_ a _"Máš se dobře?"_ jsou si podobné)
2. **Dropout**
	- Technika, kdy se během trénování **náhodně vypne část neuronů** v síti (např. 10%)
	- Díky tomu dostaneš pro stejnou větu **lehce různé embeddingy** při různých průchodech
	- Např.:
	    - První průchod: _"Kočka leží na stole"_ → embedding `[0.1, 0.5, -0.3]`
	    - Druhý průchod (s jiným dropoutem): → embedding `[0.12, 0.48, -0.29]`
	- Model se učí, že tyto dva vektory reprezentují stejný význam
3. **Alternativní metody**
	- Pokud nechceš používat dropout, můžeš vytvářet variace vět jinak:
	    - **Word deletion**: Náhodně smaž některá slova (např. _"Kočka leží na ___"_)
	    - **Word replacements**: Nahraď slova synonymy nebo náhodnými slovy
	- Cíl je stejný: vytvořit **odolné a univerzální reprezentace**
4. **Proč je to užitečné?**
	- **Nepotřebuješ štítky**: Funguje i na datech bez anotací (např. běžný text z webu)
	- **Vhodné pro low-resource jazyky**: Kde není dostatek označených dat
	- **Univerzální embeddingy**: Lze použít pro různé úlohy (klasifikace, vyhledávání, atd.)
- **Příklad použití**:
	- Chceš vyhledávat podobné věty v databázi
	- SimCSE naučí model, že:
	    - _"Kolik stojí tato kniha?"_ a _"Jaká je cena této publikace?"_ mají podobné embeddingy
	    - Zatímco _"Kde je knihovna?"_ bude mít embedding vzdálený
#### Softmax Cross-Entropy pro vyhledávání
- Bere vyhledávání jako klasifikační problém
- Mějme:
	- $q_i$ – dotaz
	- $\{d_1^+, \dots, d_N^+\}$ – relevantní dokumenty
- Definujeme skóre $s(q_i, d_k^+)$ a počítáme softmax:
	- $P(d_k^+|q_i) = \frac{\exp(s(q_i, d_k^+))/\tau}{\sum_{j=1}^N \exp(s(q_i, d_k^+))/\tau}$
- Optimalizujeme cross-entropy loss:
	- $\mathcal{L}(q_i, d_i^+) = - \log P(d_i^+|q_i)$
- **Rozšíření o hard negatives**
	- $\mathcal{L}(q_i, d_i^+, d_i^-) = \frac{\exp(s(q_i, d_k^+))/\tau}{\sum_{j=1}^N (\exp(s(q_i, d_k^+))/\tau) + (\exp(s(q_i, d_k^-))/\tau})$
#### Triplet Loss
- Pro eukleidovskou vzdálenost se snažíme minimalizovat vzdálenost mezi $q$ a $d^+$ a maximalizujeme vzdálenost mezi $q$ a $d^-$
- Pro cosinovu podobnost:
	- $\mathcal{L}(q_i, d_i^+, d_i^-) = \max(\delta(q_i, d_i^+) - \delta(q_i, d_i^-) + \epsilon, 0)$
	- ![[triplet-loss.excalidraw]]
## Podobnost dotazu s dokumentem, vyhodnocování relevance.
- **Klíčový cíl:**
	- Dostávat nejrelevantnější dokumenty na první místa
	- **Asymetrie pozornosti:**
		- Uživatelé věnují dramaticky více času čtení anotací u prvních 3-4 výsledků než u spodní části první stránky
	- **Efekt prvního místa:**
		- Distribuce reálných prokliků je extrémně vychýlená ve prospěch absolutního vítěze:
			- V 50 % případů uživatel klikne hned na první odkaz
			- První pozice má tak silnou autoritu, že na ni klikne 30 % uživatelů, i když je daný výsledek nerelevantní
### Jaccardův koeficient
- Metrika určující míru podobnosti mezi dvěma množinama
- **Definice:**
	- $A$ a $B$ jsou dvě množiny
	- $\text{JACCARD}(A,A) = 1$
	- $\text{JACCARD}(A,A) = 0$, když $A \cap B = \emptyset$
	- **Obecně:**
$$
		\text{JACCARD}(A,B) = \frac{|A \cap B|}{|A \cup B|} = \frac{|A \cap B|}{|A| + |B| - |A \cap B|}
$$
- Př.:
	- Dotaz: *ides of March* = $A$
	- Dokument: *Caesar died in March* = $B$
$$
\text{JACCARD}(A, B) = \frac{1}{6}
$$
- **Nevýhody:**
	- Nezohledňuje četnost termů (TF)
	- Jaccardův koeficient ignoruje fakt, že méně častá (vzácná) slova nesou mnohem více informace než slova častá (obyčejná)
### Eukleidovská vzdálenost
- Není vhodná, protože i když mají vektory stejný směr ale rozdílnou délku jejich vzdálenost může být velká
$$
	d(A,B) = \sqrt{\sum_{i=1}^n(b_i - a_i)^2}
$$
### Cosinova podobnost
- Je vhodná, protože počítá zda vektory ukazují stejný směrem, tj. mají podobný význam
	- Vztah:
$$
\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|} = \frac{\sum_{i=1}^{n}a_i \cdot b_i}{\sqrt{\sum_{i=1}^{n}a_i^2} \cdot \sqrt{\sum_{i=1}^{n}b_i^2}}
$$
### Bags-of-words model
- Neřeší pořadí slov v dokumentu
- Př.: *kočka leze dírou* je to samé jako *dírou kočka leze*
- **Term Frequency ($TF$)**: $TF_{t,d} = \text{počet výskytů termu t v dokumentu d}$
	- Využívání přímo hodnoty $TF$ není přesné
		- Důvod:
			- Pokud se nějaký term vyskytuje v jednou dokumentu 10 a v druhém 1 neznamená to, že první dokument je 10x víc relevantní
- **Weighted Term Frequency ($WTF$)**: $\text{WTF}_{t,d} = 1 + \log(\text{TF}_{t,d})$
	- Hodnota snižuje vliv velké četnosti termu
- **Document Frequency ($DF$)**: $DF_t = \text{počet dokumentů, kde se term t vykystuje}$
	- Opak informativnosti termu $t$
- **Inversed Document Frequency $IDF$:** $IDF_t = \log(\frac{N}{DF_t})$, kde $N$ je celkový počet dokumentů
	- Zvyšuje vliv termů s menší četností
### Vector Space Model
- ![[doc_vector_space.excalidraw]]
- Každý dokument je reprezentován jako **vektor reálných čísel** v mnohorozměrném prostoru $\mathbb{R}^{|V|}$
	- Jednotlivé osy prostoru jsou termy ze slovníku $|V|$
	- Jednotlivé body v prostoru jsou dokumenty
- **Vlastnosti prostoru:**
	- Vysoká dimenzionalita
	- Řídké vektory
- **Klíčová myšlenka:**
	1. Převést uživatelský dotaz na vektor ve stejném prostoru jako dokumenty
	2. Hodnocení dokumentů podle jejich blízkosti k dotazu
### TF-IDF
- **$TF-IDF$:** $TF-IDF_{t,d} = (1 + \log(TF_{t,d}) \times \log(\frac{N}{DF_t})) = TF_{t,d} \times IDF_t$
- Využívá počty z BOW
- Vytváří vektorovou reprezentaci
- **Term Frequency ($TF$)**: $TF_{t,d} = \text{počet výskytů termu t v dokumentu d}$
	- Využívání přímo hodnoty $TF$ není přesné
		- Důvod:
			- Pokud se nějaký term vyskytuje v jednou dokumentu 10 a v druhém 1 neznamená to, že první dokument je 10x víc relevantní
- **Weighted Term Frequency ($WTF$)**: $\text{WTF}_{t,d} = 1 + \log(\text{TF}_{t,d})$
	- Hodnota snižuje vliv velké četnosti termu
- **Document Frequency ($DF$)**: $DF_t = \text{počet dokumentů, kde se term t vykystuje}$
	- Opak informativnosti termu $t$
- **Inversed Document Frequency $IDF$:** $IDF_t = \log(\frac{N}{DF_t})$, kde $N$ je celkový počet dokumentů
	- Zvyšuje vliv termů s menší četností
### LSA (Latent Semantic Analysis)
- Metoda, která extrahuje a reprezentuje význam slov a dokumentů v málo-dimenzionální prostoru
- K redukci dimenzionality se využívá Singular Value Decomposition (SVD)
- Metoda předpokládá, že slova použitá ve stejném kontextu mají podobný význam
- Pokud používáme redukci dimenzionality na term-document matici, LSA bere jako kontext celý dokument
#### Vlastní rozklad matice
$$
A = Q\Lambda Q^{-1}
$$
- $A$ – původní matice
- Q – matice z vlastních vektorů (jako sloupce)
- $\Lambda$ – matice z vlastních čísel na diagonále
- $Q^{-1}$ – matice z vlastní vektorů (jako řádky)
#### Singular Value Decomposition
- Rozdělí matici $A$ na tři matice
	- $A = U \Sigma V^T$
		- Matice $U$ je matice vlastních vektorů z $A^TA$ – **levé singulární vektory**
		- Matice $V^T$ je matice vlastních vektorů z $AA^T$ – **pravé singulární vektory**
		- Matice $\Sigma$ je diagonální matice **singulárních hodnot** (odmocniny vlastních čísel)
- Ponecháním pouze $k$ největší hodnot z matice $\Sigma$ můžeme zredukovat dimenzi původní matice a tím odstranit ne tak důležité data
- SVD minimalizuje Frobénovu vzdálenost mezi původní a upravenou maticí $\| A - A_k \|_F$ => redukce je optimální
	- $\|A\|_F = \sqrt{\sum_{i = 1}^{m} \sum_{j = 1}^{n} |a_{ij}|^2}$
#### SVD v rámci LSA
- Mejme term-document matici $A$
	- Řádky jsou dokumenty
	- Sloupce jsou slova
- Aplikujeme na ní SVD:
	- $A_{V\times D} = U_{V\times V}\Sigma_{V\times D} V_{D\times D}^T$
	- $V$ – velikost slovníku
	- $D$ – počet dokumentů
	- $U_{V\times V}$ – term-to-concept matice
		- Řádky jsou dokumenty
		- Sloupce jsou skrytá témata (např. sport, porno)
	- $\Sigma_{V\times D}$ – diagonální matice singulárních hodnot
		- Čísla na diagonále představují důležitost jednotlivých témat
	- $V_{D\times D}^T$ – document-to-concept matice
		- Řádky jsou skrytá témata (např. sport, porno)
		- Sloupce jsou jednotlivá slova
- Vybereme $k$ největších hodnot z $\Sigma_{V \times D}$, čímž zredukujeme dimenzionalitu
- Termy jsou reprezentovány: $U_k\Sigma_k$
- Dokumenty jsou reprezentovány: $\Sigma_k V_{k}^T$
- Redukovanou reprezentaci nových dokumentů získáme: $x_k = U^Tx$
- Redukovanou reprezentaci slov získáme: $x_k=x^TV_k$
#### LSA algoritmus
1. Pro každé query se načtou všechny dokumenty (předpočítané vektory $\Sigma_k V_k^T$)
2. Reprezentace dotazu a každého dokumentu jako sémantický vektor ($\hat{q} = U_k^Tq$)
3. Výpočet cosinovo podobnosti mezi dotazem a všemi dokumenty
4. Seřazení dokumentů a vracení nejlepších výsledků
### Efektivní získání top K dokumentů
#### Využití haldy
- Použití min/max haldy
- Konstrukce haldy vyžaduje $O(n)$ operací, kde $n$ je počet dokumentů
- Získání $K$ nejlepších má poté složitost $O(K \log(n))$
- Pokud $n \gg K$ tak je celková složitost $O(n)$
#### Heuristika
- Heuristicky zmenšíme prostor, ve kterém vyhledáváme
##### Document-at-time
- Řadíme dokumenty podle nezávislého měřítka relevance (např. PageRank)
- **Kompozitní skóre dokumentu:**
$$
	    score(q,d)=g(d)+cos⁡(q,d
$$
	- Kombinuje PageRank s cosinovo podobností mezi dotazem a dokumentem
##### Term-at-time
- **Princip:**
	- Každý dotazní term se zpracovává po jednom. Postupně procházíme všechny dokumenty v postings listu pro každý term dotazu
- **Postup:**
	1. **Inicializace:** Vytvoříme pole `Scores[]` pro skóre dokumentů a `Length[]` pro délky dokumentů
	2. **Zpracování termů:** Pro každý term $t$ v dotazu:
		- Spočítáme váhu pro dotaz $(\text{wt},q)$ a získáme postings list pro term
	3. **Aktualizace skóre:** Pro každý dokument `d` v postings listu přičteme součin váhy termu pro dokument a dotaz
	4. **Normalizace skóre:** Po zpracování všech termínů normalizujeme skóre dokumentů dělením jejich délkou
	5. **Výběr top k:** Na závěr vyberem top $k$ dokumentů s nejvyšší skóre
#### KD Stromy
- K-dimenzionální binární vyhledávací strom
- Př.:
![[kd_tree.excalidraw]]
- Vyhledávání v KD Stromu:
![[kd_tree_find.excalidraw]]
- Nalezené nejbližší sousedy si můžeme ukládat např. do seřazeného pole nebo do haldy
- Takto najdeme k nejbližších sousedů a u nich následně budem počítat podobnosti => nemusíme počítat podobnosti pro všechny
- Čím vyšší je počet dimenzí tím je algoritmus pomalejší
#### Locality Sensitive Hashing
- Rozdělíme prostor na $n$ hyper-rovin
- Vygenerujeme hash klíč pro každý dokument následujícím způsobem:
	- Hash klíč je binární vektor o délce $n$
	- Každý prvek vektoru reprezentuje jednu hyper-rovinu
	- Pokud je bod na jedné straně hyper-roviny (skalárn součin $\gt 0$) bit je $1$, pokud je na druhé straně (skalární součin $\leq 0$) bit je $0$
- Takto získáme hash tabulku pro všechny dokumenty
- Při vyhledávání dotazu následně spočteme jeho binární vektor a porovnávání podobnosti provedem pouze s vektory, které jsou pod stejným hashem
- **Problém:** dokumenty, ktteré leží blízko hyper-roviny
	- **Řešení:** vytvoříme $m$ hash tabulke pro různé hyper-roviny
## Systémy odpovídání otázek.
### Jazykový model
- = pravděpodobnostní model, který predikuje pravděpodobnost sekvence slov
- Formálně model predikuje sjednocenou pravděpodobnost sekvence tokenů:
	- $P(w_1, w_2, \dots, w_n)$
- **Chain-rule:**
	- $P(w_1,w_2,\dots w_n) = \prod_{i=1}^n P(w_i | w_1 \dots w_{i-1})$
	- Př.:
		- $P(\text{"simple"}) \cdot P(\text{"language"}|\text{"simple"}) \cdot P(\text{"model"}|\text{"simple", "language"})$
#### N-Gramový jazykový model
- Limituje kontext slov
	1. **Unigram**
		- $P(\text{"simple"}) \cdot P(\text{"language"}) \cdot P(\text{"model"})$
	2. **Bigram**
		- $P(\text{"simple"}) \cdot P(\text{"language"}|\text{"simple"}) \cdot P(\text{"model"}|\text{"language"})$
	3. **Trigram**
		- $P(\text{"simple"}) \cdot P(\text{"language"}|\text{"simple"}) \cdot P(\text{"model"}|\text{"simple", "language"})$
- **Kolik parametrů musí 3-gramový jazykový model predikovat?**
	- $|V|^3$, kde $V$ je velikost slovníku
		- **Proč?**
			- Pro každé slovo bereme v potaz všechny dvojice slov, které se před ním mohou nacházet $|V| \times |V|$
			- A to děláme pro všechny slova, proto $|V| \times |V| \times |V| = |V|^3$
#### Class-based jazykový model
- Mapování slov na třídy (word-to-class mapping)
	- $C = \{c_1, c_2, \dots, c_m\}$, $m \ll |V|$ (počet tříd je výrazně menší než velikost slovníku)
- Výpočet odhadu pravdědopobnosti:
$$
P(w_i|w_{i-1}, \dots, w_{i-n+1}) = P(w_i|c_i) \cdot \prod_{i=1}^n P(c_i|c_{i-1} \dots c_{i-n+1})
$$
- Nyní se predikuje $|V| \cdot m + m^3$ parametrů
##### Brown Clustering
- Vytoření clusterů, tak aby pravděpodobnosti co nejvíce odpovídali tomu co bychom získali využitím n-gramového modelu
- Hierarchické aglomerativní shlukování
- **Optimalizační kritérium**: Cílem je maximalizovat pravděpodobnost celého textu (trénovacího korpusu) v rámci **class-based n-gramového jazykového modelu** (pro zjednodušení použijeme bigramový model):
	- $P = \prod_{i=1}^{N} P(w_i \mid c_i) \cdot P(c_i \mid c_{i-1})$
- V praxi spíše minimalizujeme tzv. cross-entropy:
	- $- \frac{1}{N} \sum_{i=1}^{N} \log \left( P(w_i \mid c_i) \cdot P(c_i \mid c_{i-1}) \right)$
- **Algoritmus:**
	1. Odhadneme pravděpodobnosti standardního bi-gramového modelu
	2. Každé slovo budu jedna třída
	3. Sloučíme dvě třídy tak, že minimalizujeme cross-entropy
	4. Opakuj krok 3. dokud nedostaneme požadovaný počet clusterů
- **Cíl algoritmu**
	- Automaticky organizovat slova do **hierarchických shluků** (stromu) na základě jejich výskytu v kontextech. Nepotřebuje znát význam slov – stačí mu statistika z textu
	- **Příklad Korpusu**
		- Mějme 3 věty:
			1. _Kočka loví myš._
			2. _Pes honí kočku._
			3. _Myš utíká před psem._
	- **Klíčové Kroky Algoritmu**
		- **Inicializace**
			- Každé slovo je zpočátku samostatný shluk:  
				- `{kočka}`, `{loví}`, `{myš}`, `{pes}`, `{honí}`, `{utíká}`, `{před}`, `{psem}`
	- **Analýza Bigramů (Kontextů)**
		- Algoritmus sleduje, **jaká slova následují po jiných slovech**:
			- `[START] → kočka`, `[START] → pes`, `[START] → myš`
			- `kočka → loví`, `pes → honí`, `loví → myš`, `honí → kočku`, ...
	- **Iterativní Slučování Shluků**
	- V každém kroku slučujeme **dvojici shluků**, které mají **nejpodobnější kontexty**:
		1. **iterace**: Sloučíme `{kočka, pes}`
		    - _Proč?_ Obě slova se vyskytují **pouze po `[START]`** (žádný jiný kontext).
		2. **iterace**: Sloučíme `{loví, honí}`
		    - _Proč?_ Nyní obě následují po shluku `{kočka, pes}` (původně "kočka" → "loví", "pes" → "honí").
		3. **iterace**: Sloučíme `{myš, psem}`
		    - _Proč?_ "Myš" se vyskytuje po `[START]` i `{loví, honí}`, "psem" po `{před}` – podobné "cílové" role.
		4. **iterace**: Sloučíme `{utíká, před}`
		    - _Proč?_ Obě se vyskytují v kontextech pohybu ("utíká" po "myš", "před" po "utíká").
	- **Výsledný Strom a Kódy**
		- ![[Státnice - Zpracování dat 2026-05-30 19.47.40.excalidraw]]
		- **Binární kódy slov** (0 = levá větev, 1 = pravá):
			- `kočka → 00`
			- `pes → 01`
			- `myš → 10`
			- `psem → 11`
			- `loví → 000`
			- `honí → 001`
			- `utíká → 110`
			- `před → 111`
	- **Proč Algoritmus Postupuje Právě Takto?**
		- **Priorizuje nejjednoznačnější shody**: Nejprve slučuje slova s **identickými kontexty** (např. "kočka" a "pes").
		- **Komplexní kontexty řeší později**: Slova jako "myš" (více kontextů) čekají, až se jejich okolí zjednoduší.
		- **Výsledek odpovídá lingvistickým kategoriím** (zvířata, akce), i když algoritmus nezná význam slov!
### Neural Language Model
- Využívá neuronové sítě k odhadu pravděpodobnosti textu
- Využívají se architektury jako:
	- Feed-Forward Neural Networks (FFNNs)
	- Recurrent Neural Networks (RNNs)
	- Long Short-Term Memory (LSTM)
	- Transformers network
- Modely dokáží generovat husté, vektory, které reprezentují složité vztahy mezi slovy v rámci velkých slovníků
- Modely dokáží predikovat slova podle okolního kontextu
#### Word2Vec
- FFNN
- Nejjednodušší NN architektura
- Používá Skip-gram nebo Continuous Bag of Words (CBOW)
	- **Skip-gram** – predikce okolních slov na základě jednoho slova
	- **CBOW** – predikce slova na základě okolních slov
- Výsledné vektory zachycují sémantiku slov
- **Negative Sampling v Word2Vec:**
	- **Cíl:** Zrychlit trénování modelu Word2Vec a snížit výpočetní nároky při učení vektorových reprezentací slov
	- **Problém:** Výpočet pravděpodobností pro všechna slova ve slovníku (pomocí softmax) je výpočetně náročný
	- **Řešení:** **Negative sampling** místo výpočtu pravděpodobností pro všechna slova vybírá náhodné **negativní příklady**, která nejsou v daném kontextu, a učí model rozlišovat mezi pozitivními a negativními páry slov
	- **Postup:**
	    1. **Pozitivní příklady** jsou slova, která se vyskytují ve stejném kontextu (např. "král" a "trůn")
	    2. Pro každý pozitivní pár se **náhodně vybírá několik negativních příkladů** (např. "král" a "auto")
	    3. Model se učí, že pozitivní páry by měly být v podobném kontextu, zatímco negativní páry ne
	- **Výhody:** Rychlejší trénování, snížené výpočetní nároky, efektivnější učení vektorových reprezentací
#### Doc2Vec
- Rozšíření Word2Vec, které generuje vektory reprezentující celé dokumenty
#### Contextualized Neural Networks
- **Cíl:** Generování slovních vektorů, které se přizpůsobují kontextu, ve kterém slova vystupují
- **Typy modelů:** Kontextualizované modely zahrnují **recurrent neural networks (RNN)** a **Transformer-based models** (např. BERT, GPT)
- **Rozdíl oproti statickým vektorům:** Na rozdíl od statických embeddingů jako **Word2Vec**, které jsou fixní pro každé slovo, **kontextualizované embeddingy** se mění v závislosti na okolních slovech v dané větě
- **Získání embeddingu:** Kontextualizované vektory jsou získávány z **skrytého stavu** hlubokého sekvenčního modelu, který je **positional-aware** (na rozdíl od **bag-of-words** přístupu, kde není brán ohled na pořadí slov)
- **Trénink:** Modely jsou stále trénovány na úkolu jazykového modelu (např. predikce dalšího slova ve větě)
#### Siamese Networks
- **Cíl:** Siamese sítě (také nazývané jako modely s dvěma věžemi) jsou navrženy k učení podobnosti mezi dvěma vstupy porovnáním v společném prostorovém prostoru rysů
- **Použití:** Jsou užitečné zejména v úlohách **sémantické podobnosti**, jako je **detekce parafrází** a **vyhledávání dokumentů**
- **Struktura sítě:** Síť se skládá ze dvou **identických podsítí**, které zpracovávají vstupní dvojice a počítají skóre podobnosti
- **Sdílení vah:** Podsítě mohou sdílet váhy některých vrstev podle typu vztahu:
    1. **Všechny váhy jsou sdíleny:** Symetrický vztah, stejný formát (např. textové dokumenty v přirozeném jazyce).
    2. **Některé váhy jsou sdíleny:** Asymetrický vztah, stejný nebo podobný formát (např. dotaz a dokument).
    3. **Žádné váhy nejsou sdíleny:** Úplně odlišné formáty (např. obrázek a textový popis).
### Large Language Model (LLM)
![[Pasted image 20250407203402.png]]
- **Language Model** = pravděpodobností model, který odahaduje pravděpodobnost dalšího slova
- 2 fáze:
	- 1. trénink – učíme se souvislosti
	- 2. inference – závislosti používáme
- **prompt engeneering** = vytváření dotazů, které z LLM dostávájí co nejlepší odpovědi
- **agenti:**
	- ![[Pasted image 20250407204432.png|400x200]]
		- **Enviroment** – DB, API
		- **Senzor** – select nad DB, API call
		- **Agent** – LLM Chat + function call
		- **Action** – insert, update, delete, API call
### Retrieval Augmented Generation (RAG)
- **RAG** = načtení relevantních dokumentů k danému kontextu a následná generace odpovědi pomocí LLM
#### RAG schéma
![[RAG-schema.excalidraw|600x200]]
#### RAG jako SW produkt
- Systém je nasazen na produkci proto musí:
	- Mít nejaktuálnější data
	- Malá odezva na dotaz => náročné protože, provádí více úkonů, než samotný IR nebo chatbot
- Systém musí umožňovat jednoduchý vývoj
	- Měřitelný => nutnost pro průběžné zlepšování
	- Sběr dat z provozu => nutnost pro průběžné zlepšování
	- Modularita => jednoduchost vyměnit jednotlivé komponenty (chunker, embedder, retriever, ...)
#### Modularita
- Při změně embedderu nebo jiné komponenty je nutné zvážit:
	- Náklady na čas a přepočet
	- Změnu chování systému
	- Potřebu verzování dat a komponent
	- Validaci, že výstupy dávají stále smysl
#### Data Scrape – Data Layer
- Společné rozhraní pro **QAgen** a **RAG**
	- **QAgen** = Question Answer Generator – systém generující testující otázky a odpovědi
- Možnost pravidelné aktualizace
	- **Snapshot** = časová značka
		- Umožňuje uživateli/vývojáři zjistit s jakými daty RAG pracoval
#### Chunker
- **Úkol:** rozdělování textu na menší kousky
- **Hotová řešení:**
	- **markdown** = rozdělení podle struktury v `.md`
	- **sentence** = rozdělení podle vět (např. každé 3 věty)
	- **window** = rozdělení podle počtu tokenů nebo slov (např. každých 200 slov)
- Volba **chunkeru** má dopady na RAG
	- kratší chunky => víc dotazů na embedding model, ale lepší přesnost → více chunků → víc položek v indexu → větší paměťové nároky
- ![[chunks-vs-docs.excalidraw|800x100]]
#### Embedder
- **Úkol:** převod textů na vektory
- Může mít různé vlasnosti:
	- výkon => kvalitnější embeddingy
	- rychlost
		- $\downarrow$ rychlost => $\uparrow$ lepší embeddingy
		- $\uparrow$ rychlost => $\downarrow$ horší embeddingy
		- hledáme optimální hladinu
	- cena => využívání placených API vs. vlastní
#### Retriever
- **Úkol:** získání relevantních dokumentů pro daný dotaz
#### Testování
##### Testovací data
| Část              | Co testujeme           | Jak?                                   |
| ----------------- | ---------------------- | -------------------------------------- |
| IR (retrieval)    | Relevance dokumentů    | Gold data + metriky (Recall@k, MRR...) |
| Generování        | Kvalita odpovědi       | BLEU/ROUGE, nebo LLM-hodnotitel        |
| LLM moderation    | Bezpečnost, pravdivost | LLM jako „soudce“, heuristiky          |
| Celý systém (RAG) | Spolupráce IR + LLM    | „Integrační testy“                     |
##### Tvorba testovacích data
- Lidé
	- Drahé
	- Těžko opakovatelné
- Stroj
	- Možnost opakovat
	- Věrohodnější
##### Formát testovacích dat
- D = document
- Q = question
- A = answer
- S = span
- Asymetrie problému
	- Sample doc => generate question => generate answer + span
	- D => Q
	- Q,D => A,S
#### Evaluace
- **Metriky pro IR:**
	- Doc level/Chunk level
	- Hit rate
	- MRR = mean reciprocal rank
		- $\text{MRR} = \frac{1}{|Q|} \sum_{i=1}^{|Q|} \frac{1}{\text{rank}_i}$
	- Precision
	- Recall
#### E2E evaluace
- Tradiční => Bleu Rouge
- **LLM as a Judge**
	- **Faithfulness** – věrohodnost
	- **Relevancy**
	- **Hallucination** – $\text{Hallucination} = \frac{Number of Contradicted Contexts}{Total Number of Contexts}$
	- **Toxicity** – $\text{Toxicity} = \frac{Number of Toxic Opinions}{Total Number of Opinions}$
#### Context Embeddings
- Embedding pro chunk – navíc obohcený o dokument
- Může pomoci při sémantické reprezentaci
- Můžeme jinak embeddovat otázku/dokument
#### Prefix embeddings
- Embedduje společně s nějakým prefixem, který dodává dodatečné informace
	- Např.:
		- document: ...
		- question: ...
- Může se jinak embeddovat otázka a jinak dokument
#### Korektivní RAG
- Vyhodnucuje kvalitu IR a generovaných odpovědí
- Odpověď nesplňuje metriky => zlepšení odpovědi (nebo odpoví, že odpověď není známá)
- Může zvyšovat latenci
#### Agentní RAG
- Proces klasického RAG: dotaz => vyhledání => odpověď 
- **Proces agentního RAG:** interaktivní
	- Rozdělí úkol na více kroků
	- Aktivně rozhoduje co má dělat dál
	- Volí nástroje podle potřeby (volání externího API, ...)
	- Aktualizuje svůj plán
- Delší odezva
## Multimedia Information retrieval.

### Content-Based Image Retrieval (CBIR)
- Image-based dotaz
- Vyhledávání podle vizuálních vlastností získaných z obrázku
- ![[CBIR.excalidraw]]
#### Získání vlastností
- Globální vs. lokální vlasnosti
- Vlasnosti získané pomocí neuronových sítí – embeddings
- ![[cbir-feature.excalidraw]]
#### Globální vlastnosti
- Vektorová reprezentace celého obrázku
- Jednoduchá, krátká reprezentace
- Jenoduše ovlivnitelná škálováním, rotací, atd...
- Feature matching:
	- **Histogramová intersekce**
		- $\text{HI}(f,r) = 1 - \sum_i \min(f_i, r_i)$
	- **$\chi^2$ statistika**
		- $\chi^2(f,r) = \sum_{i=1}^n \frac{(f_i - r_i)^2}{2(f_i + r_i)}$
	- **Cosinova podobnost**
#### Lokální vlastnosti
- Množina vlastností z různých částí obrázku
- Robustnější
- Rozdělení podle reguárního gridu
- Body vlastností určeny pomocí **feature detector**
- Popis vlastností:
	- Scale Invariant Feature Transform (SIFT)
	- Local Binary Patterns (LBP)
	- Patterns of Oriented Edge Magnitued (POEM)
	- Gabor filters
- Detektory hlavních bodů:
	- SIFT, ORB
	- Harris corner
##### Matching
- Raw vlastnost – vypočítané algoritmem rovnou
- Bag of Features (BoF, Bag of Visual Words)
	- Extrakce vlastností ze všech obrázku v DB
	- Codebook – shlukování vektorů do předdefinovaného počtu shluků
	- Reprezentace – histogram vizuální slov v jednom obrázku
- Matching pomocí BoF – jednoduchá metrika jako HI
- Matching pomocí raw vlastností
	- Může obsahovat poziční informace
	- Nalezení nejbližší vlastnosti v porovnávaném obrázku
	- Suma vzdáleností nejbližších vlastností
##### Scale Invariant Feature Transform (SIFT)
- Detekce klíčových bodů (key-points) a popis vlastností
- Invariantní k natočení obrázku, školávání a osvětlení
- Používá se pro: spojování obrázku s překrývajícím se obsahem do jednoho (panorama stiching), rozpoznávání obličejů, vyhledávání obrázků
- ![[Pasted image 20260604194045.png]]
- **Princip:**
	1. Vytvoření scale-space (měřítkové pyramidy)
		- Je to vlastně $n$ čím dál tím víc rozmazaných verzí původního obrázku
	2. Mezi každou dvojící vrstev v scale-space vypočítám tzv. *Difference of Gaussians (DoG)*
		- Proč?
			- V oblastech, kde je obrázek jednobarevný (např. čistá bílá zeď), je hodnota pixelů v obou rozmazaných kopiích stejná. Když je od sebe odečtete, získáte **nulu (černou barvu)**.
			- V oblastech, kde byla **ostrá hrana, přechod nebo bod**, se menší rozmazání zachovalo jinak než to větší. Po odečtení v těchto místech zůstane **vysoká hodnota (svítivá stopa)**.
	3. Pro každý pixel v DoG najdu maximum/minimum pomocí následujícího postupu:
		- Vezmu si jeden pixel a všechny body kolem něj (3x3 matice)
		- Vezmu 3x3 matice i z vrstvy nad a pod
		- Pokud je můj vybraný pixel maximum/minimum označím ho jako key-point
	4. Vezmu okolí key-pointu (4x4) a spočítám tam gradienty
	5. Pro každou buňku z okolí key-pointu vytvořím histogram orientací – 16 histogramů
	6. Mám 16 histogramů a celkem 8 směrů => $16 \times 8 = 128$ hodnot
	7. Tím získám vektory popisující key-pointy
##### Local Binary Patterns (LBP)
- **Princip:**
	1. Vyberu pixel v obrázku
	2. Vezmu si jeho okolní pixely (3x3)
	3. Všechny okolní pixely, které mají hodnutu větší jak hodnotu zvoleného pixelu dostanou 1 a ostatní dostanou 0
	4. Opakuji pro všechny pixely
- ![[LBP.excalidraw|500x200]]
### Vlastnosti naučené pomocí neuronových sítí
#### Barlow Twins
- Ze vstupní dávky obrázků se vytvoří dvě různé verze každého obrázku
- Obě verze projdou stejnou neuronovou sítí (se stejnou architekturou a sdílenými váhami)
- Dostaneme dvě sady **embeddingů** (vektorových reprezentací)
- Vypočítá se **cross-korelační matice** mezi těmito embeddingy – zkoumá, jak moc jsou jednotlivé dimenze embeddingů ze dvou verzí korelované
- ![[Pasted image 20250515220622.png]]
### Image-to-text Retrieval (ITR)
- **Cross-modal** vyhledávání = pracujeme s různými typy modality dat (text, obrázek)
- Vyhledáváme obrázky podle textových popisů
- Techniky z *computer vision* (strojového vidění) a NLP
- Získání vlastností a zarovnání
- ![[Pasted image 20250515220910.png]]
#### Contrasive Language-Image Pre-training (CLIP)
1. **Vstup: páry obrázek + popis**
	- CLIP se učí z velkého množství párů obrázků a jejich popisů (captionů)
	- Každý pár má: obrázek + text, který ho popisuje
2. **Dvě sítě: jedna pro obrázek, druhá pro text**
	- Pro obrázek: CNN nebo Vision Transformer, který vytvoří vektorovou reprezentaci (embedding)
	- Pro text: Transformerový model (např. podobný BERT nebo GPT), který vytvoří embedding textu
3. **Společný embedding space**
	- Oba embeddingy (obrázek i text) jsou vektorové reprezentace ve stejném prostoru
	- Podobné obrázky a jejich popisy mají embeddingy blízko sebe
4. **Contrastive loss**
	- Tréninková ztráta je tzv. **contrastive loss**:
	    - Snaží se maximalizovat podobnost (např. kosinovou) mezi správnými páry (obrázek + správný text)
	    - A zároveň minimalizovat podobnost mezi nesprávnými páry (obrázek + nesprávný text)
- ![[Pasted image 20250515223408.png]]
##### Compose Image Retrieval (CoIR)
- Dotaz je složen z obrázku a textu
- **CLIP** model
- Může mít lepší výsledky jak image search
- ![[Pasted image 20250515223501.png]]
### Vyhledávání audia
- Podobný přístup jako vyhledávání obrázků
#### Mel-Frequency Cepstral Coefficients
- ![[Pasted image 20250515224230.png]]
- **Princip:**
	- 🎧 **Vezmeš krátký úsek zvuku** – třeba 20 ms
	- 🔊 **Zjistíš, jaké frekvence v něm jsou** (pomocí Fourierovy transformace)
	- 🎵 **Převedeš ty frekvence na tzv. Melovu stupnici** – ta lépe odpovídá tomu, jak člověk vnímá výšku tónu (např. nízké frekvence slyšíme „jemněji“ než vysoké)
	- 📉 **Změříš, kolik energie je v jednotlivých frekvenčních pásmech**
	- 🔁 **Z toho uděláš tzv. cepstrální koeficienty** – což je taková „komprese“ tvaru spektra do několika čísel
#### Chromatické vlastnosti
- chromatická stupnice
- 12-ti složkový vektor – kolik energie je v které třídě tónu (C – B)
- Short-term Fourier Transform (STFT)
- Chroma Energy Normalized (CENS)
- ![[Pasted image 20250515224412.png]]

## Evaluace (pro jistotu)
- **Důležité míry:**
	- Rychlost odpovědi
	- Velikost indexu
	- Pěkné UI
	- **Relevance**
- **Důležité míry podle uživatelů:**
	- Hledač:
		- Míra návratnosti k vyhledávacímu enginu
	- Inzerent:
		- Prokliky
	- Kupující:
		- Čas na nákup
	- Prodejce:
		- Profit
	- CEO:
		- Profit společnosti
- **Relevance k dotazu vs. Relevance k vyhledávané informaci**
	- I když jsou výsledky relevantní k dotazu nemusí odpovídat na to co uživatel vyhledával
	- Důležitější je relevance k vyhledávané informaci
### Precision, Recall, F1-score, Accuracy
- ![[Pasted image 20250516191715.png]]
- **Precision** = P = $\frac{\#(\text{získané relevantní výsledky})}{\#(\text{získané výsledky})}$ = $\frac{TP}{(TP + FP)}$
- **Recall** = R = $\frac{\#(\text{získané relevantní výsledky})}{\#(\text{všechny relevantní výsledky})}$ = $\frac{TP}{(TP + FN)}$
- **F-score** = $\frac{1}{\alpha\frac{1}{P} + (1-\alpha)\frac{1}{R}} = \frac{(\beta^2 + 1)PR}{\beta^2P+R}$
	- $\alpha \in [0, 1]$
	- $\beta \in [0, \infty]$
	- Nejčastěji se používá balancované F-skóre, kde $\beta = 1$ nebo $\alpha = 0.5$
		- To je harmonický průměr
		- $\frac{1}{F} = \frac{1}{2}(\frac{1}{P}+\frac{1}{R})$
		- Proč používáme harmonický průměr a ne aritmetický?
			- Kdybych vrátili vše tak by bylo F skóre rovno 50% což je příliš
	- Jak ovlivňuje $\beta$ váhu recall a precision?
		- $\lim_{\beta \to \infty} \frac{(\beta^2 + 1)PR}{\beta^2P+R} = \frac{\beta^2 PR + PR}{\beta^2 P + R} = R$
		- $\lim_{\beta \to 0} \frac{(\beta^2 + 1)PR}{\beta^2P+R} = \frac{\beta^2 PR + PR}{\beta^2 P + R} = P$
		- Čím větší je beta tím víc záleží na Recall
- **Accuracy** = $\frac{\# \text{všechny relevantní}}{\# \text{všechny dokumenty}}$ = $\frac{(TP+TN)}{(TP + FP + FN + TN)}$
	- Počítání přenosti v IR není ideální protože:
		- Mějme například celkem $10000$ dokumentů
		- Pro jeden dotaz je například relevantních pouze $20$ dokumentů
		- Pokud moje IR vrátí všechny nerelevantní dokumenty: $9980$ bude přenost: $\frac{9980}{10000} = 99,8\%$, ale přitom moje IR nefunguje dobře
### Ranked evaluace
#### Precision-Recall křivka
- Precision/Recall/F se měří pro unranked množiny
- Můžeme to jednoduše upravit pro ranked seznamy
- **Příklad:**

| Pořadí | Dokument | Relevantní? |
| ------ | -------- | ----------- |
| 1      | Doc A    | Ano         |
| 2      | Doc B    | Ne          |
| 3      | Doc C    | Ano         |
| 4      | Doc D    | Ne          |
| 5      | Doc E    | Ano         |

| Prefix (top-k)        | Relevantní v prefixu | Precision = (# relevantních / k) | Recall = (# relevantních / 3) |
| --------------------- | -------------------- | -------------------------------- | ----------------------------- |
| 1 (Doc A)             | 1                    | 1 / 1 = 1.0                      | 1 / 3 ≈ 0.33                  |
| 2 (Doc A, B)          | 1                    | 1 / 2 = 0.5                      | 1 / 3 ≈ 0.33                  |
| 3 (Doc A, B, C)       | 2                    | 2 / 3 ≈ 0.67                     | 2 / 3 ≈ 0.67                  |
| 4 (Doc A, B, C, D)    | 2                    | 2 / 4 = 0.5                      | 2 / 3 ≈ 0.67                  |
| 5 (Doc A, B, C, D, E) | 3                    | 3 / 5 = 0.6                      | 3 / 3 = 1.0                   |
- ![[Pasted image 20250516204439.png]]
#### ROC (Receiver Operating Characteristic curve) křivka
- ![[Pasted image 20250516205923.png]]
- ROC graf pomáhá najít ideální práh, který vyvažuje mezi tím, kolik relevantních najdeš (TPR) a kolik chybně vrátíš nerelevantních (FPR)
	- Práh = hodnota cosine podobnosti podle, které byli dokumenty seřazeny
	- V levém dolním rohu jso výsledky pro vyšší prahové hodnoty a v pravém horním rohu jsou hodnoty pro nižší
		- => Proto nás zajímá levý dolní roh hlavně
### Standardní benchmarkovací organizace a nástroje
#### Cranfield
- **Cranfield je jeden z prvních testovacích souborů pro vyhodnocování vyhledávání informací (IR)**  
    - Byl to průkopnický projekt, který umožnil poprvé přesně kvantifikovat, jak dobře vyhledávače fungují
- **Vznikl koncem 50. let v UK**
- Obsahuje:
    - 1398 abstraktů z časopisu o aerodynamice (tedy relativně malé množství dokumentů)
    - 225 dotazů (queries)
    - Kompletní hodnocení relevance každého dotazu vůči každému dokumentu — tedy u každého dotazu je jasné, které dokumenty jsou relevantní a které ne.
- **Nevýhody:**
    - Dnes je tento dataset příliš malý na to, aby reprezentoval reálné vyhledávání
    - Navíc je tematicky úzce zaměřený (aerodynamika), takže neodpovídá obecnějším scénářům
#### TREC
- = Text Retrieval Conference
- Je to skupina různých benchmarků pro testování relevance
#### Další
- GOV2
	- Další TREC/NIST kolekce
	- 25 milionů webových stránek
- NTCIR
	- Pro jazyky ve východní Asii a pro mezi-jazykové vyhledávání
- Cross Language Evaluation Forum (CLEF)
	- Zaměřuje se na jazyky z centrální Evropy a mezi-jazykové vyhledávání
### Kappa metrika
- Metrika určující jak moc se hodnotitelé relevance dokumentů shodují
- Je navržena pro kategorizaci, tedy pro situace, kdy hodnotitelé přiřazují položky do diskretních tříd (např. relevantní/nerelavantní)
- $\kappa = \frac{P(A) - P(E)}{1 - P(E)}$
	- $P(A)$ – proporce toho jak často se hodnotitelé shodují
	- $P(E)$ – pravděpodobnost, že se hodnotitelé shodnou kdyby hodnotili náhodně
- Pokud $\kappa$ je v intervalu $[\frac{2}{3}, 1.0]$ shoda je dostačující
	- Pokud jsou hodnoty menší je třeba změnit metodologie určování relevance
#### Příklad
![[Pasted image 20250516212330.png]]
- $P(A) = \frac{300 + 70}{400} = \frac{370}{400} = 0.925$
- $P(\text{nonrelevant}) = \frac{80 + 90}{400 + 400} = \frac{170}{800} = 0.2125$
- $P(\text{relevant}) = \frac{320 + 310}{400 + 400} = \frac{630}{800} = 0.7878$
- $P(E) = P(\text{nonrelevant})^2 + P(\text{relevant})^2 = 0.2121^2 + 0.7878^2 = 0.665$
- $\kappa = \frac{0.925 - 0.665}{1 - 0.665} = 0.776$ (**akceptovatelná shoda**)
#### Dopad neshody mezi hodnotiteli
- Jsou výsledky IR bezvýznamné pokud se hodnotitelé hodně neshodují?
	- **NE**
### Evaluace velkých vyhledávacích enginů
- Recall se blbě měří na webu
- Existují lepší metriky než jenom precision a recall
	- MAP, DCG
- Vyhledávací enginy používají i non-relevance-based metriky:
	- Prokliky na první odkaz
	- A/B testování
#### Mean Average Precision (MAP)
- Vyjadřuje **průměrnou přesnost**, se kterou systém vrací **relevantní dokumenty na předních pozicích**, **napříč více dotazy**
- Čím **vyšší MAP**, tím **lepší systém** – relevantní dokumenty se nachází vysoko ve výsledcích
$$
\text{MAP} = \frac{\sum_{q=1}^Q \text{AveP(q)}}{Q}
$$
$$
\text{AveP} = \frac{\sum_{i=1}^p P_i \times \text{rel}_i}{\text{rel\_docs}}
$$
	- $Q$ – počet dotazů
	- $\text{rel\_docs}$ – počet relevantních dokumentů
	- $\text{AveP}(q)$ – průměrná precision
##### Příklad
**Q1:**

| Pozice | Dokument | Relevantní? | # Relevantních nalezených do této pozice | Precision   |
| ------ | -------- | ----------- | ---------------------------------------- | ----------- |
| 1      | D1       | ✅ Ano       | 1                                        | 1/1 = 1.00  |
| 2      | D2       | ❌ Ne        | 1                                        |             |
| 3      | D3       | ✅ Ano       | 2                                        | 2/3 ≈ 0.667 |
| 4      | D5       | ❌ Ne        | 2                                        |             |
| 5      | D4       | ✅ Ano       | 3                                        | 3/5 = 0.6   |
**Q2:**

| Pozice | Dokument | Relevantní? | # Relevantních nalezených do této pozice | Precision   |
| ------ | -------- | ----------- | ---------------------------------------- | ----------- |
| 1      | D5       | ❌ Ne        | 0                                        |             |
| 2      | D4       | ✅ Ano       | 1                                        | 1/2 = 0.5   |
| 3      | D2       | ✅ Ano       | 2                                        | 2/3 ≈ 0.667 |
|        | D3       | ❌ Ne        | 2                                        |             |
$$
AveP_1 = \frac{1 + \frac{1}{3} + \frac{3}{5}}{3} = 0.756
$$

$$
AveP_2 = \frac{\frac{1}{2} + \frac{2}{3}}{2} = 0.583
$$

$$
MAP = \frac{AveP_1 + AveP_2}{2} = \frac{0.756 + 0.583}{2} = 0.6695
$$
#### Discounted Comulative Gain
- Metrika používaná při **hodnocení kvality řazení výsledků**
$$
\text{DCG}_p = \sum_{i=1}^p \frac{\text{rel}_i}{\log_2 (i+1)}
$$
$$
\text{nDCG}_p = \frac{\text{DCG}_p}{\text{IDCG}_p}
$$
	- $\text{rel}_i$ – relevance ítého dokumentu
	- $\text{nDCG}_p$ – normalizované $\text{DCG}$
	- $\text{IDCG}_p$ – ideální $\text{DCG}$
# 10. Klasifikace textů, výběr vlastností. Shlukování textů, volba počtu shluků. Extrakce informací z textů.
## Klasifikace textů, výběr vlastností.
- **Klasifikace** = přiřazení předdefinovaných kategorií objektům podle jejich obsahu
- Příklady aplikací:
	- Filtrování spamu
	- Kategorizace zpráv
	- Analýza sentimentu
### Formální definice
- **Máme:**
	- Prostor dokumentů $\mathcal{X}$, kde každý dokument je reprezentován jako vektor vlastností
	- Fixní množina $n$ tříd $\mathcal{Y} = \{ y_1, \dots, y_n\}$
	- Trénovací množina $\mathcal{D}$ s označenými dokumenty $(d,y) \in \mathcal{X} \times \mathcal{Y}$
- **Cíl:**
	- Vytvořit klasifikátor $\mathcal{H}$, který mapuje dokumenty na třídy
		- $\mathcal{H}: \mathcal{X} \rightarrow \mathcal{Y}$
	- Klasifikátor se většinou učí na množině $\mathcal{D}$ s využitím statistiky nebo strojového učení
		- $d \in \mathcal{X}: \mathcal{H}(\mathcal{d}) \in \mathcal{Y}$
### Metody klasifikace
#### Ruční
- Velmi přesné (pokud prováděno experty)
- S narůstajícím množství dat ale pomalé a drahé
#### Rule-based
- Definovány sady pravidel, která přesně definují dané třídy
- Často kombinováno s Boolean searchem
	- Např.: Google Alerts – definována klíčová slova a filtrování nového dokumentu na základě (ne)relevantnosti
- Velmi přesný přístup, pokud jsou pravidle postupem času upravována/přizpůsobována odborníkem
- Čase těžké na údržbu a drahé
#### Algoritmická
- Common sense
#### ML-Based
- Klasifikace založena na strojovém učení – pravidla se odvozují z trénovacích dat => strojové učení rozpoznává vzorce v datech (**supervised learning**)
- Statistické a neuronové metody zvyšují přesnost klasifikace
### Typy klasifikací
- **Binární**: dvě kategorie
- **Multi-class klasifikace:** víc jak dvě kategorie
- **Multi-label klasifikace:** jeden dokument může být be více kategoriích
### Překážky v textové klasifikace
- Vysoko-dimenzionální vstupní prostor
- Nejasnosti v textu
- Nerovnoměrná data
- Měnící se jazyk
- Dlouhý kontext
- Overfitting
- Underfitting
## Výběr vlastností
- Dokumenty jsou znázorněny ve vysoko-dimenzionálním prostoru, kde každá dimenze odpovídá jednomu termu
- Mnoho slov se vyskytuje jen zřídka a nemusí přinášet užitečné informace
- Vzácnější, zavádějící (noise features) slova mohou vést k overfittingu
- K zvýšení přesnosti a efektivity můžeme odebrat zbytečné znaky
- Příklady:
	- **Frequency-based:** ponechat pouze ty nejčastější termy
	- **Mutual Information:** měřit, do jaké míry term přispívá ke klasifikaci do dané třídy
		- Pokud je term A plně nezávislý na třídě B, pak MI = 0
	- **Chi-square Test:** Identifikace slov silně spojená s danou třídou
	- **Redukce dimenzionality:** Techniky jako PCA, LSA, které zredukují prostor termů
### Reprezentace textu jako vlastnosti
- **BoW** – pracuje s textem jako s neuspořádanou sekvencí slov
	- *pes kousl muže* = *muž kousl psa*
- **TF-IDF** – nastavuje důležitost slova podle jeho frekvence a vzácnosti
- **Continuous Vectors** – slova/dokumenty jsou reprezentovány jako spojité vektory
## Příklady klasifikátorů
### Naivní Bayesův klasifikátor
- **Probabilistický model:**
	- Počítá $P(y|d)$ pomocí Bayesova teorému
	- $y_{NB} = \text{argmax}_{y \in \mathcal{Y}} P(y) \cdot \prod_{i=0}^{n_d} P(f_i|y)$
		- $P(y)$ – apriorní ppst.
		- $n_d$ – délka dokumentu
		- $P(f_i|y)$ – podmíněná ppst. výskytu vlastnosti (termu) $f_i$ v dokumentu třídy $y$
- Naivní – předpokládá, že výskyt jednoho slova nijak nezávisí na výskytu ostatních slov
- **Smoothing:**
	- Odstraňuje problém nulové ppsti. u slov, která se nevyskytovala v trénovacích datech
### Vector Space klasifikace
- Dokumenty jsou reprezentovány jako body ve vektorovém prostoru
- ![[vector-space-class.excalidraw]]
#### Nearest Centroid
- Centroid $\mu$ reprezentuje každou třídu
	- **Centroid** = průměr všech vektorů $v(d)$ dokumentů $D_y$ ve třídě $y$
		- $\mu(y) = \frac{1}{|D_y|} \sum_{d \in D_y} v(d)$
- Dokumenty jsou zařezeny do třídy podle nejbližšího centroidu
	- $y_R = \text{argmin}_{y_j} |\mu(y_j) - v(d)|$
#### kNN klasifikace
- $k$ nejbližších sousedů
- **Contiguity hypothesis** – testovací dokument $d$ je podobný jako trénovací dokumenty v blízkosti $d$ 
- Menší $k$: model je citlivý na hluk => overfitting
- Větší k: může vést k underfittingu
#### Neuronové sítě
- Řeší problémy běžných algoritmů:
	- Vektory s velkým množstvím dimenzí
	- BoW přístup
- Řešení – **Continuous Vectors:**
	- Každé slovo vyjádřené vektorem
	- Věta vyjádřena několika vektory
##### Neuron
- Základní jednotka neuronových sítí
- $a = g\left( \sum_{i=0}^{n} w_i x_i + b \right) = g(w^Tx+b)$
- ![[neuron.excalidraw|500x200]]
##### Feed-Forward Neural Network (FFNN)
- N vrstev neuronů
- Každá vrstva progresivně transformuje vstup
- Pro multi-class nebo multi-leve klasifikaci může výstupní vrstva obsahovat více neuronů, každý reprezentující pravděpodobnostní skóre pro jednu třídu
- ![[FFNN.excalidraw]]
- **Problémy:**
	1. Vstupy musí být fixní délky
		- BoW, TF-IDF: reprezentuje text jako jeden vektor fixní délky
		- Word embeddings: produkují sekvenci vektorů (jeden pro každé slovo), vyžaduje agregaci pro sentence-level klasifikaci
		- **Řešení:**
			- Agregace word vektorů na fixní délku (např. průměr, suma, max) – často ztráta informace
			- Využití sequence-aware modelů, které zpracují celý vstup bez potřeby apriorní agregace
	2. Nevědomí o pořadí slov nebo jejich struktuře
		- **Řešení:**
			- Využití sequence-aware architektur:
				- Recurrent Neural Networks (RNNs), Transformery
				- Convolutional Neural Networks (CNNs) – zachycují lokální paterny slov (např. n-gramy)
##### Ztrátová funkce (Loss function)
- Vyjadřuje chybu mezi správným výstupem $y$ a predikcí $\hat{y}$
- Ztrátová funkce $\mathcal{L}$ je pro jednu instanci (jeden trénovací případ)
	- $\mathcal{L}(y,\hat{y}) = (y - \hat{y})$
	- Mohou být i jiné varianty loss funkce
		- Pojmy:
			- $q$ – dotaz
			- $d^+$ – relevantní dokument
			- $s$ – podobnost
			- dataset $\mathcal{D} = \{(q_i,d_i^+)\}_{i=1}^M$
		- **MSE loss**
			- $\mathcal{L}(q_i,\hat{d_i^+}) = (q_i - \hat{d_i^+})^2$
		- **Cosine similarity loss**
			- $\mathcal{L}(q_i,\hat{d_i^+}, r_i) = (s(q_i - \hat{d_i^+}) - r)^2$
		- **Contrastive learning loss**
			- $\mathcal{L}(q_i,\hat{d_i^+}) = -\log \frac{\exp(s(q_i,d_i^+))/\tau}{\sum_{j=1}^N \exp(s(q_i,d_i^+))/\tau }$
- Cenová funkce (cost funcion) $\mathcal{C}$ je pro kolekci $M$ dokumentů
	- $C = \frac{1}{M} \sum_{i=1}^M \mathcal{L}(y_i, \hat{y_i}$
- **Cíl:** minimalizovat loss funkci
- Neuronové sítě jsou trénovány pomocí **backpropagation**
- **Backpropagation** = algoritmus, který počítá gradienty loss funkce k aktualizaci vah a minimalizaci chyb v predikci
##### Klasifikace pomocí neuronových sítí
1. Definice vstupu – ideálně word embeddings
2. Volitelně pro lepší výsledky – zpracování vstupu pomocí RNN, Transformerů, CNN – transformace vstupu na single sentence vektor
3. Definice FFNN s vstupy z kroků (1) nebo (2)
4. Získání predikce třídy
	- Multi-class: **softmax** normalizuje výstupy na pravděpodobnosti
		- $p_i = \frac{e^{z_i}}{\sum_j e^{z_j}}$
			- $z_i$ – skóre pro třídu $i$
	- Multi-label: threshold – vezmeme třídu všech neuronů s větší aktivační hodnotou než nějaký práh (např. 0.5)
	- Binary: jeden z předchozích přístupů
##### Architektura transformerů
- **Language models:** predikují slova podle kontextu
- **Enkodér:** generuje kontextualizované tokenové reprezentace podle vstupního textu
- **Dekodér:** generuje text
- Tokenizace: používá podslova (**subwords**) – to umožňuje zpracovat OOV (Out of vocabulary) slova
- ![[Pasted image 20250514224234.png]]
- **Příklad generování odpovědi**:
	1. Vstup: _"Jak se máš?"_ → encoder vytvoří kontext.
	2. Dekodér začne s **\[START]**:
	    - Krok 1: vybere _"Dobře"_ (nejvyšší pravděpodobnost).
	    - Krok 2: z _"\[START] Dobře"_ vybere _"a"_.
	    - Krok 3: z _"\[START] Dobře a"_ vybere _"ty?"_.
	    - Konec: **\[START] Dobře a ty? \[END]**.
##### Pre-trained Language Models
- Před-trénované na velkých datasetech – úkoly jako predikce dalšího slova
- Před-trénování = model získá obecnou znalost jazyka, kterou lze využít pro další úkoly a lepší fine-tuning
- **Encoder-only models:** BERT, RoBERTa – používány pro klasifikaci, extrakci vlastností z textu
- **Decoder-only models:** GPT, LLaMA – generace text, používané pro doplnění
- **Encoder-decoder models:** T5, BART – sequence-to-sequence úkoly (překlad, sumarizace)
##### Transformery pro klasifikaci
- **Encoder-only:** vyžaduje pouze sentence-leve reprezentaci
	- Model **přečte celou větu/text** a vytvoří **kontextové reprezentace tokenů**
	- **Potřebujeme reprezentaci celé věty** – nikoliv jen jednotlivých slov
	- Dva běžné způsoby:
		1. **\[CLS] token** – speciální token na začátku vstupu, který „nasaje“ význam celé věty. 
	    → Používá se jeho embedding jako reprezentace věty
		2. **Mean pooling** – zprůměrujeme embeddingy všech tokenů
	- Výsledek: **jeden vektor**, který reprezentuje celou větu
	- Tento vektor se pošle do jednoduché **feed-forward neuronové sítě (FFNN)**, která na konci dává výstupní třídu (např. pozitivní / negativní)
- **Decoder-only / Encoder-decoder**
	- Textová klasifikace je **formulována jako generování výstupu** – tedy místo „třída: 1“ se model naučí **vygenerovat text**, např. „positive“
## Shlukování textů, volba počtu shluků.
- **Shlukování** = metoda rozdělování do skupin
- Učení bez učitele
- **Optimalizace vyhledávání**
	- Seskupování podobných dokumentů
- **Personalizace**
	- Rozpoznání preferencí a přizpůsobení výsledků vyhledávání
- **Zlepšení relevance**
	- Získání relevantnějších výsledků podle historie dotazů
- **Hard vs Soft shlukování**
	- **Hard** = dokument spadá právě do jedné třídy
	- **Soft** = dokument spadá s ppstí. X do jedné třídy, s ppstí. Y do druhé
- **Flat vs Hierarchické shlukování**
	- **Flat** = začínáme v náhodném rozpoložení, iterativně zlepšujeme (k-means)
	- **Hierarchické** = vytváříme hierarchii shluků
### Algoritmy – flat
#### K-means
- Rychlé a jednoduché
- $k$ – počet shluků
- **Algoritmus:**
	1. Výběr centroidů
	2. Každý bod je přiřazen nejbližšímu centroidu
	3. Posouvání centroidů
	4. Opakování (2) a (3) dokud nemáme daný počet shluků
- Hledání optimálního $k$
	- ![[Pasted image 20260531155118.png]]
		- $\text{WSS} = \sum_{j=1}^k \sum_{i \in S_j} ||x_i - \mu_j ||^2$
- K-median, K-medoids
### Algoritmy – hierarchické
- **Dvě metody:**
	- **Aglomerativní:**
		- Každý bod je na začátku označen jako shluk
		- Body se postupně spojují
	- **Divizní:**
		- Na začátku je jeden velký shluk, který se postupně rozděluje
- **Metriky vzdáleností:**
	1. **Single-Linkage** = nejbližší dvojice bodů
	2. **Complete-Linkage** = nejvzdálenější dvojice bodů
	3. **Average-Linkage** = průměr všech vzdáleností
	- ![[hiera-cluster.excalidraw|500x200]]
#### Dendrogram
- Stromová struktura znázorňující slučování shluků v čase
![[dendrogram.excalidraw]]
#### DBSCAN
- Density-Based Spatial Clustering
- Schopný detekovat outliery
- **Algoritmus:**
	1. Vyber bod
	2. Projdi okolní body
	3. Pokud je v okolí dostatečný počet bodů vytvoř z nich shluk
	4. Jakmile je shluk vytvořen pokračuj dalším nenavštíveným bodem
### Redukce dimenzionality
- **Důvody:**
	- Vizualizace (projekce do 2D)
	- Komprese datA
- **Algoritmy:**
	- PCA – rychlé, lineární metoda
	- t-SNE – pomalejší, ne-lineární metoda, lepší pro komplexní data
#### Principal Component Analysis (PCA)
- Projekce $\text{n-dim} \rightarrow \text{k-dim}$ ($k \lt n$)
- Cílem ja najít ortogonální osy, které maximalizují rozptyl
- ![[Pasted image 20250515011244.png]]
#### T-Distributed Stochastic Neighbor Embedding (T-SNE)
- Zajišťuje, že body, které jsou blízko sebe v mnoho-dimenzionálním prostoru budou blízko sebe i v málo-dimenzionálním prostoru
- **Algoritmus:**
	1. **Spočítá podobnosti v původním prostoru (např. 100D)**
		- Pro každý pár bodů spočítá, jak blízko jsou si — blízké body mají vysokou pravděpodobnost, že jsou si "sousedé".
		- Tyto podobnosti jsou převedeny na **pravděpodobnosti sousedství** pomocí **Gaussova rozdělení** (normal distribution).
	2. **Náhodně inicializuje body v nízkodimenzionálním prostoru (např. 2D)**
	3. **Spočítá podobnosti v novém prostoru (2D)**
		- Podobně jako výše, ale použije se **Studentovo t-rozdělení s jedním stupněm volnosti** místo Gaussova. (To má delší „ocásky“ a lépe odděluje vzdálené body.)
	4. **Minimalizuje rozdíl mezi těmito dvěma podobnostmi**
		- Pomocí **Kullback-Leibler divergence** porovná rozložení podobností v původním a novém prostoru.
		- Cílem je, aby body, které byly blízko ve vysoké dimenzi, zůstaly blízko i ve 2D.
		- Optimalizuje se gradientním sestupem (gradient descent).
- ![[t-sne.excalidraw]]
## Extrakce informací z textů.
- Proces automatického získávání strukturovaných dat z nestrukturovaného textu
- Na rozdíl od vyhledávání, které vrací celé dokumenty, IE vrací konkrétní fakta
- Dvě vrstvy:
	- **Přípravná (Lingvistická)**
	- **Extrakční (Sémantická)**
### Přípravná fáze (Preprocessing a Syntaktická analýza)
- Slouží k tomu, aby model pochopil gramatickou strukturu věty
- Sama o sobě informace neextrahuje
1. **Part-of-Speech Tagging (POS Tagging)**
	- **Popis:** Označí každé slovo ve větě jeho slovním druhem
	- **Využití:** Pomáhá dalším modelům rozlišit kontext
2. **Syntaktická analýza (Parsing):**
	- **Popis:** Analýza gramatické struktury vět a určení vztahů mezi slovo
	- **Přístupy:** 
		- Dependency parsing (strom závislostí)
		- Constituency parsing (hierarchické frázové bloky)
###  Extrakční fáze (Sémantická analýza)
- Vytěžování informací
1. **Rozpoznávání pojmenovaných entit (Named Entity Recognition – NER):**
	- **Popis:** Identifikace a klasifikace klíčových objektů v textu
	- **Kategorie:**
		- Osoby
		- Organizace
		- Lokace
		- Čas
		- Částky
2. **Vytěžování vztahů (Relation Extraction):**
	- **Popis:** Identifikuje sémantické vztahy mezi nalezenými entitami
		- Vztahy jsou nejčastěji reprezentovány jako triplet: `(Subjekt, Predikát, Objekt)`
3. **Rezoluce koreference (Coreference Resolution):**
	- **Popis:** Spojení různých výrazů a zájmen v textu, které odkazují na stejnou entitu
4. **Extrakce událostí / Vyplňování šablon (Event Extraction / Slot Filling):**
	- **Popis:** Komplexní naplnění předdefinované tabulky na základě určité události detekované v textu
### Metody realizace
1. **Regex**
	- Rule-based přístup
2. **ML, Statistické modely**
	- Algoritmy (např. **CRF – Conditional Random Files** nebo neuronové sítě) berou text jako sekvenci tokenů a učí se z anotovaných dat tipovat správné značky
3. **LLM (Zero-shot/Fer-shot)**
	- Využití LLM