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
# 8. Principy zpracování přirozeného jazyka – tokenizace, stemming, Porterův algoritmus, lematizace, parsing, slovníky. Modely pro reprezentaci a zpracování rozsáhlých nestrukturovaných dat, vektorový model dokumentu.
## Principy zpracování přirozeného jazyka – tokenizace, stemming, Porterův algoritmus, lematizace, parsing, slovníky.
- **word** = řetězec tak jak se vyskytuje v textu
- **term** = normalizované slovo
- **token** = konkrétní výskyt **word** nebo **term** v dokumentu
- **Normalizace** = převedení různých tvarů jednoho slova na jednotný tvar
- **Tokenizace** = rozdělení dokumentu na tokeny
- **Stemming** = heuristická normalizační technika
	- **Porterův algoritmus:**
		- Stemmer pro angličtinu
		- Aplikování 5 fází přepisovacích pravidel
- **Lematizace** = převádění slov do základního tvaru (gramaticky správně)
	- Inflexní morfologie = zachování významu slova
	- Derivační morfologie = nemusí zachovat význam slova
- **Slovník** = struktura obsahující všechny slova vyskytující se v datovém korpusu
- **Invertovaný index** = datová struktura, která mapuju termy na dokumenty ve kterých se vyskytují
	- `term => [doc1, doc2, ...]`
	- Hash mapy
	- Stromy
- **Oprava překlepů:**
	- **Isolated Word Spelling Correction**
		- **Edit Distance:**
			-  ![[edit_dist.excalidraw]]
			- Insert, Delete, Replace
		- **K-gramový index**
	- **Context-Sensitive Spelling Correction**
		1. **Získáme kandidátní opravy**
		2. **Vytváříme všechny možné kombinace**
		3. **Každou variantu spustíme jako dotaz**
		4. **Vybereme variantu s nejvíce výsledky**
	- **Soundex**
## Modely pro reprezentaci a zpracování rozsáhlých nestrukturovaných dat, vektorový model dokumentu.
### Binární matice sousednosti

|         | dokument 1 | dokument 2 | ... | dokument N |
| ------- | ---------- | ---------- | --- | ---------- |
| slovo 1 | 1          | 0          | ... | 0          |
| slovo 2 | 0          | 1          | ... | 1          |
| ...     | 0          | 0          | ... | 1          |
| slovo M | 1          | 1          | ... | 1<br>      |
| slovo 1 | 20         | 2          | ... | 31         |
### Matice četností
|         | dokument 1 | dokument 2 | ... | dokument N |
| ------- | ---------- | ---------- | --- | ---------- |
| slovo 1 | 20         | 2          | ... | 31         |
| slovo 2 | 12         | 133        | ... | 9          |
| ...     | 4          | 53         | ... | 23         |
| slovo M | 8          | 7          | ... | 90         |
### BoW
- Neřeší pořadí slov v dokumentu
- **TF** = počet výskytů termu v dokumentu
- **DF** = v kolika dokumentech se term vyskytuje
- **IDF** = $\frac{N}{DF}$, $N$ = počet dokumentů
#### TF-IDF
- Vektorová reprezentace
- Vektorový prostor má stejný počet dimenzí jako termů
### Vektorový model dokumentu
- ![[doc_vector_space.excalidraw]]
- Každý dokument je reprezentován jako **vektor reálných čísel** v mnohorozměrném prostoru $\mathbb{R}^{|V|}$
- **Cosinova podobnost:**
$$
\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|} = \frac{\sum_{i=1}^{n}a_i \cdot b_i}{\sqrt{\sum_{i=1}^{n}a_i^2} \cdot \sqrt{\sum_{i=1}^{n}b_i^2}}
$$
- Normalizujeme aby se dalo spočítat Cosinova podobnost jenom pomocí $A \cdot B$, protože $||A|| = 1$ a $||B|| = 1$
# 9. Vyhledávání v rozsáhlých textových/nestrukturovaných datech – booleovský model, indexování. Podobnost dotazu s dokumentem, vyhodnocování relevance. Systémy odpovídání otázek. Multimedia Information retrieval.
## Vyhledávání v rozsáhlých textových/nestrukturovaných datech – booleovský model, indexování.
### Booleovský model
- Použití operací: `AND, OR, NOT`
- Operace využívá nad **invertovaným indexem**
- Příklad:
	```
	"slovo1": [1, 2, 5, 7],
	"slovo2": [3, 5, 11],
	"slovo3": [2, 5, 11]
	```
	- Dotaz: `slovo1 AND slovo3`
	- Výsledek: dokumenty 2, 5
- Vrací pouze množinu relevantních dokumentů **NENÍ SEŘAZENÁ PODLE RELEVANCE**
- **Famine** = výsledek dotazu nebude nic protože je dotaz moc specifický
- **Feast** = výsledkem dotazu je obrovská množina
- Optimalizace => odstraňování `NOT`, levá mn. menší jak pravá
### Indexování
- **Invertovaný index**
	- Biword index
	- Positional index (u docID je uložena i pozice v dokumentu)
	- Kombinovaný (Biword + Klasika nebo Biword + Positional)
	- Permuterm
	- K-gram
- Hash Mapy
- Stromy
- **Způsob tvorby:**
	- BSBI
	- SPIMI
- **Komprese:**
	- Komprese termů
	- Komprese postings listů
		- Ukládání mezer
		- VBA
		- Gamma kódy
## Podobnost dotazu s dokumentem, vyhodnocování relevance.
### BoW
- Neřeší pořadí slov v dokumentu
- **TF** = počet výskytů termu v dokumentu
- **DF** = v kolika dokumentech se term vyskytuje
- **IDF** = $\frac{N}{DF}$, $N$ = počet dokumentů
#### TF-IDF
- Vektorová reprezentace
- Vektorový prostor má stejný počet dimenzí jako termů
### Vektorový model dokumentu
- ![[doc_vector_space.excalidraw]]
- Každý dokument je reprezentován jako **vektor reálných čísel** v mnohorozměrném prostoru $\mathbb{R}^{|V|}$
- **Cosinova podobnost:**
$$
\text{cosine\_similarity}(A, B) = \frac{A \cdot B}{\|A\| \|B\|} = \frac{\sum_{i=1}^{n}a_i \cdot b_i}{\sqrt{\sum_{i=1}^{n}a_i^2} \cdot \sqrt{\sum_{i=1}^{n}b_i^2}}
$$
- Normalizujeme aby se dalo spočítat Cosinova podobnost jenom pomocí $A \cdot B$, protože $||A|| = 1$ a $||B|| = 1$
- **LSA**
	- $A = U \Sigma V^T$
	- $U$ – term-to-concept matice
		- Řádky jsou termy
		- Sloupce jsou skrytá témata (např. sport, rakety)
	- $\Sigma$ – diagonální matice singulárních hodnot
		- Čísla na diagonále představují důležitost jednotlivých témat
	- $V^T$ – document-to-concept matice
		- Řádky jsou skrytá témata (např. sport, rakety)
		- Sloupce jsou jednotlivé dokumenty

### Jaccardův koeficient
$$
		\text{JACCARD}(A,B) = \frac{|A \cap B|}{|A \cup B|} = \frac{|A \cap B|}{|A| + |B| - |A \cap B|}
$$
## Systémy odpovídání otázek.
### Retrieval Augmented Generation (RAG)
- **RAG** = načtení relevantních dokumentů k danému kontextu a následná generace odpovědi pomocí LLM
#### RAG schéma
![[RAG-schema.excalidraw|600x200]]
- **Chunker** = rozdělení textu na menší kousky
	- ![[chunks-vs-docs.excalidraw|800x100]]
- **Embedder** = převod chunků na vektory
- **Retriever** = hledá relevantní chunky k dotazu
- **LLM** = na základě chunků a dotazu vrátí odpověď
## Multimedia Information retrieval.
- **Content Based Image Retrieval (CBIR):**
	- ![[CBIR.excalidraw]]
- **Globální vlastnosti** = reprezentace celého obrázku jedním vektorem
- **Lokální vlastnosti** = množina vlastností z různých částí obrázku
	- Scale Invariant Feature Transform (SIFT)
		- - ![[Pasted image 20260604194045.png]]
		- ![[Pasted image 20260610164703.png]]
	- **Local Binary Patterns (LBP)**
		- ![[LBP.excalidraw|500x200]]
# 10. Klasifikace textů, výběr vlastností. Shlukování textů, volba počtu shluků. Extrakce informací z textů.
## Klasifikace textů, výběr vlastností.
- **Klasifikace** = přiřazení předdefinovaných tříd objektům podle jejich obsahu
- **Příklady aplikací:**
	- Detekce spamu
	- Kategorizace zpráv
	- Analýza sentimentu
- **Formální definice:**
	- $X$ – dokumenty
	- $Y$ – kategorie
	- $H: X \rightarrow Y$ – klasifikátor
	- $d \in X: H(d) \in Y$
- **Metody klasifikace:**
	- Ruční
	- Rule-based
	- ML
- **Typy klasifikací:**
	- Binární
	- Multi-class
	- Multi-label
- **Feature Extraction**
	- = jak upravit surové data do podoby, které se pak dává do klasifikátoru
	- **Reprezentace:**
		- BoW
		- TF-IDF
		- Sémantické vektory
- **Příklady klasifikátorů:**
	- **Naivní Bayes**
	- **Vector Space**
		- kNN
		- Nearest Centroid
## Shlukování textů, volba počtu shluků.
- **Shlukování** = metoda rozdělování dat do skupin
- **Využití v IR:**
	- Vložíme dotaz
	- IR systém vrátí N dokumentů
	- IR systém v nich udělá shluky
	- Výsledek vyhledávání je kategorizován
- **Hard vs Soft**
	- Hard = dokument spadá právě do jedné třídy
	- Soft = dokument spadá s ppstí. X do jedné třídy a s ppstí. Y do druhé
- **Flat vs Hierarchické**
	- **Flat** = konečné rozdělení dat na shluky bez hierarchie
	- **Hierarchické** = vytváří postupnou strukturu shluků ve formě stromu (dendrogramu)
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
			- Vzdálenost bodů ve shluku od centroidů
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
## Extrakce informací z textů.
- Uděláme shlukování
- Pojmenujeme shluky
- Získáme informace
- Snažíme se z nestrukturovaných dat udělat strukturované/semi-strukturované
## Evaluace
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
## Ranked evaluace
### Mean Average Precision (MAP)
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

| Pozice | Dokument | Relevantní a na správné pozici? | # Relevantních nalezených do této pozice | Precision   |
| ------ | -------- | ------------------------------- | ---------------------------------------- | ----------- |
| 1      | D1       | ✅ Ano                           | 1                                        | 1/1 = 1.00  |
| 2      | D2       | ❌ Ne                            | 1                                        |             |
| 3      | D3       | ✅ Ano                           | 2                                        | 2/3 ≈ 0.667 |
| 4      | D5       | ❌ Ne                            | 2                                        |             |
| 5      | D4       | ✅ Ano                           | 3                                        | 3/5 = 0.6   |
**Q2:**

| Pozice | Dokument | Relevantní a na správné pozici? | # Relevantních nalezených do této pozice | Precision   |
| ------ | -------- | ------------------------------- | ---------------------------------------- | ----------- |
| 1      | D5       | ❌ Ne                            | 0                                        |             |
| 2      | D4       | ✅ Ano                           | 1                                        | 1/2 = 0.5   |
| 3      | D2       | ✅ Ano                           | 2                                        | 2/3 ≈ 0.667 |
|        | D3       | ❌ Ne                            | 2                                        |             |
$$
AveP_1 = \frac{1 + \frac{1}{3} + \frac{3}{5}}{3} = 0.756
$$

$$
AveP_2 = \frac{\frac{1}{2} + \frac{2}{3}}{2} = 0.583
$$

$$
MAP = \frac{AveP_1 + AveP_2}{2} = \frac{0.756 + 0.583}{2} = 0.6695
$$