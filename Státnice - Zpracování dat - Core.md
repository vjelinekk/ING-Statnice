# 1. Přehled a klasifikace databázových systémů a technologií pro správu a zpracování dat. Požadavky kladené na SŘBD a jeho vlastnosti. Konceptuální modelování, relační a jiné modely dat. Normální formy, aktivní databáze, principy transakčního zpracování, konzistence databáze.
## Přehled a klasifikace databázových systémů a technologií pro správu a zpracování dat.
- **Klasifikace:**
	- **Datový model:**
		- Relační (*MySQL*)
		- Postrelační/NoSQL (*MongoDB*)
			- Sloupcová
			- Souborová
			- Grafová
			- Key-Value
		- Objektově orientované (*ObjectDB*)
	- **Počet uživatelů:**
		- Single (*SQLite*)
		- Multi (*MySQL*)
	- **Použití:**
		- OLTP (*MySQL*)
		- OLAP (*Google BigQuery*)
	- **Lokace:**
		- Centralizované (*PostgreSQL*)
		- Distribuované (*Cassandra*)
	- **Typ dat:**
		- Obecná (*MongoDB*)
		- Časová (*Influx*)
		- Stream (*Kafka*)
		- Prostorová (*PostGIS*)
		- Multimédia (*Milvus*)
	- **Využívání prostředků:**
		- Micro (*SQLite*)
		- Mobile (*Couchbase* Lite)
		- Real-time (*eXtremeDB*)
		- In-memory (*Redis*)
- **Technologie:**
	- ETL
	- ELT
## Požadavky kladené na SŘBD a jeho vlastnosti.
- **SŘBD** = sada nástrojů umožňující přístup do databáze
- **Požadavky:**
	- Perzistence
	- Sdílitelnost dat
	- Redundance pod kontrolou
	- Integrita dat
		- Entitní
		- Referenční
		- Doménová
	- Bezpečnost a ochrana
	- Transakční zpracování
- **Vlastnosti:**
	- ACID – Atomicity, Consistency, Isolation, Durability
	- DDL – Data Definition Language (CREATE, ALTER, DROP)
	- DML – Data Manipulation Language (INSERT, UPDATE, DELETE)
	- DQL – Data Query Language (SELECT)
	- Podpora procedur a views
## Konceptuální modelování, relační a jiné modely dat.
- **Tří-úrovňová architektura ANSI/SPARC**
	- ![[Pasted image 20260531194908.png]]
- **Konceptuální modelování**
	- První fáze návrhu DB
	- Popis reality (pro zákazníka i programátora)
	- Nezávislost na SW
	- ER, ERA UseCase Diagramy
- **Relační modelování**
	- Transformace konceptuálního modelu do konkrétního datového modelu
	- Organizování dat do tabulek
- **Jiné modely dat**
	- JSON
	- XML
	- Definováno podle potřeb
## Normální formy, aktivní databáze, principy transakčního zpracování, konzistence databáze.
- **Normální formy:**
	 - 1. NF – Sloupce obsahují pouze atomické hodnoty
	 - 2. NF – Všechny neklíčové atributy jsou zcela závislé na celém primárním klíči
	 - 3. NF – Každý neklíčový atribut v tabulce musí záviset na klíči, na celém klíči a na ničem jiném než na klíči
	 - BCNF – Každý atribut v tabulce musí záviset na klíči, na celém klíči a na ničem jiném než na klíči
	 - 4. NF – Vícehodnotové závislosti musí být závislé pouze na PK
	 - 5. NF – Tabulku nelze popsat jako výsledek joinu jiných tabulek
- **Aktivní databáze** = typ DB systémů, které jsou schopny automaticky reagovat na události
	- Trigger
	- Uložené procedury
	- Hlídání integrity a byznys pravidel
	- Automatické logování a audit
- **Principy transakčního zpracování**
	- ACID – Atomicity, Consistency, Isolation, Durability
- **Konzistence DB** = stav, kdy všechna data v DB odpovídají předem definovaným pravidlům, zákonitostem a integritním omezení
# 2. Big Data management, CAP theorem, distribuce, škálování, replikace, transakce v distribuovaném prostředí. Způsoby analýzy, návrhu a tvorby datových modelů a systémů pracujících s rozsáhlými daty.
## Big Data management, CAP theorem, distribuce, škálování, replikace, transakce v distribuovaném prostředí.
### Big Data Management
- V
	- Volume
	- Variety
	- Velocity
	- Veracity
	- Value
	- Validity
	- Volatility
- Příklady:
	- Soc. sítě
	- IoT
	- E-commerce
	- Finance
- NoSQL
	- Sloupcové
	- Key-Value
	- Dokumentové
	- Grafové
- OLAP, OLTP, BI, CI (Competitive Intelligence), ELT, ETL
### CAP
- Consistency, Availability, Partition Tolerance
- ![[CAP.excalidraw]]
### Distribuce, škálování, replikace, transakce v distribuovaném prostředí
- **Distribuovaný systém** = propojení množina nezávislých uzlů, který poskytuje uživateli dojem jednotného systému
- **Distribuované DBS** = DBS + počítačové sítě
- Koncepce DDBS
	- ![[Pasted image 20250524183118.png]]
- **Škálování** = přidávání zdrojů podle potřeby
	- Horizontální
	- Vertikální
- **Replikace** = kopírování dat na více uzlů
	- Úplná replikace
	- Plně redundantní DB
	- Strategie aktualizací
		- Synchronní
		- Asynchronní
		- ![[Pasted image 20250524204607.png]]
- **Transakce v distribuovaném prostředí:**
	- **Transakce** = sled operací, který se provede buď celý nebo vůbec
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
	- Nejde ACID
	- Musíme BASE
		- Basically Available
		- Soft State
		- Eventually Consistent
## Způsoby analýzy, návrhu a tvorby datových modelů a systémů pracujících s rozsáhlými daty.
- OLAP, BI
- Map-Reduce
- Hadoop
	- HDFS
		- ![[Pasted image 20250524180554.png]]
- NoSQL vs Multimodel vs Polystores
# 3. Zpracování strukturovaných a nestrukturovaných dat. Nerelační/postrelační databáze – BASE vs. ACID, druhy a vlastnosti NoSQL databází. Data s více modely, multi-model databáze. 
## Zpracování strukturovaných a nestrukturovaných dat.
- **Strukturované data** = data s pevně definovaným datovým modelem
	- Relační DB
	- Limitace při velkých objemech
- **Semi-strukturované data** = data mají jasně danou vnitřní hierarchii ale nemají pevně daný datový model
- **Nestrukturované data** = data nejsou definované žádným modelem
	- Multimodel DB vs Polystores
	- Data Lakes
## Nerelační/postrelační databáze – BASE vs. ACID, druhy a vlastnosti NoSQL databází.
- NoSQL
	- Horizontální škálování
	- Sloupcové, dokumentové, grafové, key-value
- ACID – Atomicity, Consistency, Isolation, Durability
	- Relační
- BASE – Basically Available, Soft State, Eventually Consistent
	- NoSQL
	- Distribuované
- ACID vs BASE
	- ![[Pasted image 20250524133326.png]]
## Data s více modely, multi-model databáze.
- **Multimodel DB** = jedna aplikace pro různé modely dat
	- ArangoDB
- 3 pohledy:
	- One size cannot fit all
	- One size can fit all
	- One size can fit a bunch
- Polystores
	- **Loosely Coupled:**
		- ![[Pasted image 20250525164730.png]]
	- **Tightly Coupled:**
		- ![[Pasted image 20250525172210.png]]
	- **Hybrid:**
		- ![[Pasted image 20250525172605.png]]
# 4. Principy a nástroje Business Intelligence, vrstvy pro analýzu dat. Přístupy k vytváření datových skladů a datových tržišť. Architektura datového skladu, jeho implementace.
## Principy a nástroje Business Intelligence, vrstvy pro analýzu dat.
- **BI** = sada nástrojů a technik s cílem získávat insight k lepšímu rozhodování
- - ![[Pasted image 20260602224630.png]]
- **Principy BI:**
	- Zpracování velkého množství dat
	- Předávání relevantních informací ve správný čas
- **Nástroje BI:**
	- ERP
	- DSA
	- ODS
	- EAI
	- DW, DL
	- ETL
	- OLAP, OLTP
	- Data Mining
- **Vrstvy:**
	- ![[Pasted image 20260608163207.png]]
## Přístupy k vytváření datových skladů a datových tržišť.
- ETL, ELT
- DW
	- Velký třesk (Inmon)
		- Výhody: single source of truth, konzistence, kvalita
		- Nevýhody: riziko selhání, počáteční náklady, dlouhá impl.
	- Přírůstková (Kimball)
		- Výhody: levnější na začátku, rychlejší, flexibilita
		- Nevýhody: nekonzistence, redundance, náročnější správa
	- ![[DBM2-zkouska 2025-12-30 16.19.56.excalidraw]]
- DM
	- Závislé na DW
	- Nezávislé na DW (může více ETL)
## Architektura datového skladu, jeho implementace.
- ![[DBM2-zkouska 2025-12-30 15.01.32.excalidraw|1000]]
- **Implementace**
	1. Analýza požadavků
	2. Návrh datového modelu
	3. Návrh ETL/ELT
	4. Implementace úložiště
	5. Implementace analytické vrstvy
	6. Provoz a údržba
# 5. Modelování dat v datových skladech, dimenzionální model. Hierarchie dimenzí, typy a vlastnosti atributů, typy vztahů. Charakteristiky tabulek faktů a dimenzí, transformace mezi jednotlivými modely.
## Modelování dat v datových skladech, dimenzionální model.
- V DW se využívá dimenzionální modelování
- Druhy:
	- Obchodní – definice co sledujeme z pohledu businessu
	- Logický – určuje strukturu dat
	- Fyzický – implementace logického modelu na konkrétní technologii
- Schéma hvězdy
- Schéma sněhové vločky
## Hierarchie dimenzí, typy a vlastnosti atributů, typy vztahů.
- **Hierarchie dimenzí**
	- ![[Pasted image 20251229220620.png]]
- **Typy a vlastnosti atributů**
	- Nominální, ordinální, binární, numerické
	- ![[Pasted image 20260608164555.png]]
- **Typy vztahů**
	- 1:N
	- M:N
	- Hierarchické
## Charakteristiky tabulek faktů a dimenzí, transformace mezi jednotlivými modely.
- **Tabulka faktů** = ukládají se tam pozorované ukazatele
	- Typy ukazatelů:
		- Aditivní (cena)
		- Semi-aditivní (počet na skladě)
		- Neaditivní (text)
	- Typy tabulek:
		- Transakční
		- Snímková
		- Akumulovaná
- **Dimenzionální tabulky** = zachycuje úhly pohledu na sledované ukazatele
	- Př.: čas, zákazník, produkt, smlouva
	- SCD
		- Přepsání (1)
		- Nový řádek (2)
		- Nový sloupec (3)
- Hvězdy => Vločky
	- Normalizace
- Vločky => Hvězdy
	- Denormalizace
# 6. Metadata pro správu datového skladu, metadata zdrojových dat, datového skladu a datové pumpy, metadata pro data a funkce na pozadí datového skladu, metadata pro koncového uživatele, standardizace metadat.
- - ![[Pasted image 20260608163207.png]]
- **Metadata pro správu datového skladu**
	- Auditiy
	- Statistiky využití
	- Plánování úloh
	- Správa uživatelů
- **Metadata zdrojových dat**
	- Technický popis systémů, ze kterých data bereme
	- Schémata produkčních DB
	- Datové typy sloupců
	- Struktura souborů, API
- **Metadata datového skladu**
	- Popis vnitřní struktury skladu
	- Popis staging area
	- Popis dimenzí a tabulek faktů
- **Metadata datové pumpy**
	- Mapování – co se mapuje na co
	- Transformační pravidla
	- ETL Run-time logy
- **Metadata pro data a funkce na pozadí datového skladu**
	- Agregační pravidla
	- Strategie partitioningu
	- Indexace
	- Archivace a purging
- **Metadata pro koncového uživatele**
	- Byznys Glossary
	- Jména sloupců, tabulek
	- Vlastníci dat
	- Indikátory kvality
- **Standardizace metadat**
	- Umožňují jednodušší vyměňování informací mezi DW
	- Common Warehouse Metamodel
# 7. Plnění datového skladu, datová pumpa, proces ETL (extrakce, transformace a vložení dat). Kvalita dat, metody čištění dat.
## Plnění datového skladu, datová pumpa, proces ETL (extrakce, transformace a vložení dat).
- ETL
- Datová pumpa = implementace ETL
- ![[Pasted image 20260102220508.png]]
- Vývoj:
	- Batch processing => Data Pipelining => Data Partitioning => Parallel Dataflow => Parallel Dataflow with Auto Repartioning
## Kvalita dat, metody čištění dat.
- **Kvalita dat** = měřítko toho jak moc jsou data přesná, úplná a konzistentní
- **Základní postupy:**
	- Standardizace
	- De-duplikace
	- Doplnění chybějících hodnot
- **Metody:**
	- Zahození nekompletního záznamu
	- Doplnění hodnot (průměr, konstanty, predikce, AI)
	- Oprava chybných hodnot
	- Shlukování, regrese