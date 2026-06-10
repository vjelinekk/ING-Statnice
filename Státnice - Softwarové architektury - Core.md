# 5. Struktura a funkcionality operačního systému. Jádro operačního systému, účel, typy jader a rozdíly mezi nimi. Subsystémy OS. Režim jádra a uživatelský režim, příklad využití bottom half při obsluze blokujících operaci s I/O periferií.
## Struktura a funkcionality operačního systému.
- OS = SW vrstva spravující HW
- Obecně využívají vrstevnatou architekturu
	1. HW
	2. Kernel
	3. User-Space (někdy nemusí)
- **Bottom-Up (Správce prostředků):**
	- PC má omezené zdroje (čas CPU, RAM, disk, síť)
	- OS zajišťuje spravedlivé přidělování těchto zdrojů
- **Top-Down (Rozšířený stroj):**
	- OS slouží jako abstrakce HW
	- Místo disku máme soubory, místo CPU procesy, ...
## Jádro operačního systému, účel, typy jader a rozdíly mezi nimi.
- **Kernel** = řídíc program sloužící jako prostředník mezi HW a SW
- **Účel:**
	- Abstrakce HW
	- Přidělování zdrojů
	- Bezpečnost a izolace
- **Typy:**
	- Mono (rychlejší, náchylnější k pádu)
	- Mikro (pomalejší, méně náchylné k pádu)
	- Hybrid (něco mezi)
## Subsystémy OS.
- **Správa procesů**
	- Program = spustitelná sekvence bytů
	- Proces = instance běžícího programu
	- Vlákno = jednotka plánování CPU
		- Vlákna sdílí paměťový prostor
	- Plánovač = část jádra OS, která přiděluje čas na CPU jednotlivým vláknům/procesům
	- Druhy plánování:
		- Preemptivní = můžu proces zastavit kdy chci
		- Nepreemptivní = proces musí doběhnout
	- ![[Pasted image 20260601111920.png]]
	- Uniprocessor = právě jedno vlákno běží na právě jednom CPU jádře
	- Kooperativní multitasking (yield)
	- Preemptivní multitasking
	- PCB
	- TCB
	- User Thread X Kernel Thread
		- ![[Pasted image 20260525181751.png]]
	- Plánování vláken:
		- RR
		- RR s prioritami
		- O(1)
		- CFS
		- EEVDF
- **Správa paměti**
	- Přidělování paměti procesům/vláknům
	- Algoritmy pro trackování přidělování paměti:
		- Bitmapa
		- Seznam
		- Buddy systémy
	- Algoritmy pro hledání volného místo:
		- First-fit
		- Next-fit
		- Worst-fit
		- Best-fit
	- MMU
	- Segmentace
		- Báze + offset
	- Stránkování
		- CR3 – adresa na které je uložena TS
		- ![[Pasted image 20240205142104.png]]
		- Algoritmy při výpadku stránky:
			- FIFO
			- LRU
			- NRU
				- třída 0: R = 0, M = 0
				- třída 1: R = 0, M = 1
				- třída 2: R = 1, M = 0
				- třída 3: R = 1, M = 1
			- Second Chance
				- ![[Pasted image 20240205160933.png]]
		- PFF
	- Dynamické linkování
		- ![[Pasted image 20260609111055.png]]
- **Správa souborů**
	- Soubor = pojmenovaná sekvence bytů
	- Adresář = speciální druh souboru
	- Typy souborů:
		- Obyčejné
		- Adresáře
		- Speciální
	- MBR (BIOS)
		- ![[Pasted image 20260601133215.png]]
	- EUFI (GPT)
		- ![[Pasted image 20240203150912.png]]
	- Způsoby alokace
		- Kontinuální
		- FAT
		- INode
			- ![[Pasted image 20240204122654.png]]
			- ![[Pasted image 20240203204222.png]]
		- NTFS
			- ![[Pasted image 20240203202028.png]] 
- **Správa I/O**
	- Blokové (disk)
	- Znakové (sériová komunikace)
	- - ![[Pasted image 20260524212921.png]]
	- **VFS**
		- ![[Pasted image 20260524211430.png]]
	- **Installable FS**
		- ![[Pasted image 20260524213905.png]]
	- Používá **IO Request Packet (IRP)**
		- Struktura pro komunikace mezi ovladačem zařízení a kernelem
		- ![[Pasted image 20260524213147.png]]
	- PIC
	- APIC
## Režim jádra a uživatelský režim, příklad využití bottom half při obsluze blokujících operaci s I/O periferií.
- Režim jádra – provádění privilegovaných instrukcí
	- Ochrana HW
- Uživatelský režim – uživatelské aplikace (Google Chrome, ...)
- ![[Pasted image 20260524223650.png]]
# 6. Procesy, program jako proces, realizace lehkých vláken. Meziprocesová komunikace a synchronizace na symetrickém multiprocesoru.
## Procesy, program jako proces, realizace lehkých vláken.
- Program = spustitelná sekvence bytů
- Proces = instance běžícího programu
- Vlákno = jednotka plánování CPU
	- Vlákna sdílí paměťový prostor
- TCB
- PCB
- **Realizace:**
	- - ![[Pasted image 20260525181751.png]]
	- Výhody – méně přepínání kontextu
## Meziprocesová komunikace a synchronizace na symetrickém multiprocesoru.
- MP Config
	- CPU Bootstrap bit
	- CPU Enabled bit
	- Local APIC ID
- SMP Boostrap x86:
	1. **Power-On / RESET signál:** Základní deska pustí proud do procesoru a všechna hardwarová jádra naskočí v základním Real Módu na stejné počáteční instrukci.
	2. **Hardwarová arbitrace:** Jádra si mezi sebou přes interní sběrnici (APIC bus) bleskově vyjednají, kdo bude hlavní (BIOS v této chvíli ještě vůbec neběží).
	3. **Rozdělení rolí:** Jedno vítězné jádro získá status **BSP** (Bootstrap Processor) a zapíše se mu to do MSR registru; všechna ostatní jádra (AP – Application Processors) hardware okamžitě uspí do stavu **Wait-for-SIPI**.
	4. **Spuštění BIOSu na BSP:** Pouze vítězné jádro (BSP) skočí na hardwarovou adresu resetovacího vektoru (`0xFFFFFFF0`) a začne vykonávat kód BIOSu/UEFI (POST testy, inicializace RAM).
	5. **Sestavení ACPI tabulek:** BIOS prozkoumá základní desku, zjistí počet fyzických AP jader a zapíše jejich seznam a vlastnosti do konfiguračních tabulek v RAM (**ACPI / MP Tables**).
	6. **Příprava trampolíny:** BIOS nakopíruje do nízké paměti RAM (pod 1 MB) malý spouštěcí kód zvaný **Trampolína**, protože spící AP jádra se později probudí v Real Módu a nedosáhla by do vysoké paměti.
	7. **Načtení jádra OS:** BIOS předá štafetu zavaděči a ten načte do paměti jádro operačního systému (Kernel), které začíná běžet monoprocesorově pouze na jádře BSP.
	8. **Čtení konfigurace:** Jádro OS běžící na BSP si přečte ACPI tabulky vytvořené BIOSem a zjistí přesný počet spících AP jader, která je potřeba probudit.
	9. **Příprava prostředků v RAM:** Jádro OS alokuje v paměti datové struktury pro ostatní jádra – zejména pro každé budoucí AP jádro připraví jeho **vlastní unikátní jádrový zásobník (Kernel Stack)** a společné tabulky stránek.
	10. **Příprava pasti (Spinlock):** Jádro OS vytvoří v RAM globální synchronizační proměnnou (`ap_status = 0`), přičemž BSP se uzamkne do čekacího cyklu (`while(ap_status == 0)`) a neustále ji kontroluje.
	11. **INIT IPI:** BSP pošle přes svůj Local APIC spícím AP jádrům inicializační signál (Inter-Processor Interrupt), který resetuje jejich interní registry, ale ještě je nespustí.
	12. **STARTUP IPI (SIPI):** Ihned poté BSP pošle signál SIPI obsahující adresu trampolíny v low-memory, což spící AP jádra definitivně probudí.
	13. **Start v Real Módu:** Všechna probuzená AP jádra vyskočí ze spánku a začnou souběžně vykonávat kód připravené trampolíny v Real Módu.
	14. **Načtení dočasné GDT:** Kód trampolíny načte provizorní tabulku segmentů (GDT), kterou jim BSP v paměti předem nachystalo.
	15. **Skok do Chráněného / Dlouhého módu:** AP jádra nastavením příslušných bitů v registrech `CR0` a `EFER MSR` přepnou svůj procesorový režim do 32-bitového (Protected) nebo 64-bitového (Long) módu.
	16. **Aktivace stránkování:** AP jádra vezmou adresu hlavního adresáře stránek systému (ponechanou v RAM od BSP) a nahrají ji do svého registru **`CR3`**, čímž aktivují virtuální paměť.
	17. **Získání vlastního zásobníku:** AP jádro přečte své hardwarové Local APIC ID, podle něj si z připravené tabulky vytáhne adresu svého unikátního jádrového zásobníku a nahraje ji do registru **`RSP`** (Stack Pointer).
	18. **Inicializace Local APIC:** Každé samostatné AP jádro si zapne svůj vlastní řadič přerušení a nastaví interní časovače.
	19. **Nahlášení úspěchu:** AP jádro skočí do C-kódu inicializace a pomocí **atomické instrukce** přepíše sdílenou proměnnou v RAM (změní `ap_status` z 0 na 1).
	20. **Uvolnění BSP:** BSP uvidí v RAM změnu na hodnotu 1, vyskočí ze svého čekacího cyklu (spinlocku) a ví, že dané AP jádro úspěšně žije (proces se opakuje pro každé další probouzené jádro).
	21. **Vstup do plánovače (SMP provoz):** Inicializovaná AP jádra skočí do hlavní smyčky jádra OS a zapnou se do stavu Idle (vykonávají instrukci `hlt`), kde čekají, až jim scheduler operačního systému začne přidělovat kód aplikací a uživatelská vlákna.
- **Synchronizace**
	- SpinLock
		- **Zamykání:**
			```asm
		mov edx, DWORD(-1)
		
		spin: mov eax, [lockState]
			  test eax, eax
			  jnz spin
			  
			  lock cmpxchg [lockState], edx
			  test eax, eax
			  jnz spin
			```
			- Šetření energií – procesor nachvíli uspíme než abychom furt dokola dělali loop
	- Counting Semaphore
		- **operace P:**
		```
		P():
			if counter > 0:
				counter--
			else:
				zablokuj vlánko a přidej do q
		```
		- **operace V:**
		```
		V():
			if f není prázdná:
				vzbuď proces a odeber z fronty
			else:
				counter++
		```
		- Producent konzument
	- Mutex
	- Bariéra
- **Meziprocesová komunikace**
	- Pipe
	- Messages
		- Synchronní – `SendMessage()`
		- Asynchronní – `PostMessage()`
		- Princip:
			1. Ovladač HW zachytí kliknutí a předá ho subsystému Windows (`win32k.sys)
			2. Windows zjistí na kterým oknem se mys nacházela a kterému procesu okno patří
			3. Window zabalí informaci do MSG struktury a dá jí do fronty zpráv vlákna tvořící grafické okno
			- V grafickém vláknu běží tzv. **message loop**
	- Signals
		1. **Označení bitu:** Vlákno A zavolá `kill()`, kernel pouze zapíše bit čekajícího signálu do struktury vlákna B a Vlákno A běží dál.
		2. **Detekce:** Vlákno B je později přerušeno (např. časovačem) a kernel si před návratem do user-mode všimne jeho nastaveného bitu signálu.
		3. **Odskočení na obsluhu:** Kernel zálohuje aktuální registry vlákna B na jeho uživatelský stack (**Signal Frame**), změní ukazatel instrukcí (IP) na adresu obslužné funkce a spustí ji.
		4. **Obnova:** Obsluha skončí voláním `sigreturn`, kernel načte původní stav registrů ze _Signal Framu_, smaže bit a vrátí vlákno B přesně tam, kde bylo přerušeno.
	- Sdílená paměť
	- Dvojí kopírování
	- Randezvous
	- Fronta zpráv:
		- ![[Pasted image 20240204143132.png]]
# 7. Systémy reálného času, programování s omezenými prostředky. Virtualizace.
## Systémy reálného času, programování s omezenými prostředky.
- **RTOS** = včasnost provedení úkolu je stejně důležitá jako správnost (dodržování deadlines)
- **Požadavky:**
	- Determinismus
	- Odolnost vůči chybám
	- Plánování s explicitními časovými omezeními
	- Zohlednit peak load
- **Zdroje nedeterminismu:**
	- Cache
	- Stránkování
	- I/O
	- Synchronizace
	- Plánovač
	- Rekurze
- **Typy:**
	- Non (klasika OS)
	- Soft (nesplnění deadline != katastrofa)
	- Hard (nesplnění deadline = katastrofa)
- **Terminologie:**
	- Task = prováděná činnost
	- Job = sekvence tasků
	- Resource = zdroj (pasivní, aktivní)
	- Schedule = plán
- **Druhy tasků:**
	- Periodický (přichází v periodě $P_i$)
	- Aperiodický (nesplnění deadline nevadí)
	- Sporadický (nesplnění deadline vadí)
- **Plánování tasků**
	- Vhodnost algoritmů
	- Cyklický plánovač
	- Prioritní schéma
- Inverze priorit
- Rate Monotonic Analysis
- Rate Monotonic Schedule
	$$
		U = \sum_{i=1}^{n} \frac{C_i}{P_i} \leq n(\sqrt[n]2 - 1)
	$$
- Response Time Test
	$$
		R_0 = \sum_{j=1}^{i} C_j 
	$$
	$$
		R_{k+1} = C_i + \sum_{j=1}^{i - 1} C_j \times \text{ceil} (\frac{R_k}{P_j})
	$$
- Earliest Deadline First
- ![[Pasted image 20260609153600.png]]
- **Programování s omezenými prostředky:**
	- Vyhnout se výjimkám
	- Alokovat vše co jde na začátku
	- Správné ukončení (`malloc()` => `free()`)
	- Konečné využití paměti (`int pole[100]`)
	- **Volba jazyka:**
		- Asm, C, C++, Rust
## Virtualizace.
- **Virtualizace** = technologie umožňující pouštět více OS na jednom HW
- **Emulace** = SW napodobování chování cizí HW architektury
- **Hypervizor** = hostitel, který spouští VM
- ![[Pasted image 20260526175735.png]]
- Popek-Goldbergovo pravidlo
	- 3 typy instrukcí:
		- Privilegované – jde vykonávat pouze v CPL0
		- Senzitivní – mění HW konfiguraci
		- Klasické
- Binární překlad
- Paravirtualizace – OS ví, že je virtualizován
- VT-x
	- Shadow Page Table
	- Extended Page Tables
- VT-D
# 8. Překladače vyšších programovacích jazyků, struktura a činnost překladače. Lexikální, syntaktická a semantická analýza, její varianty (tj. rekurzivní sestup, shora dolů a zdola nahoru).
## Překladače vyšších programovacích jazyků, struktura a činnost překladače.
- **Základní typy:**
	- Assembler
	- Compiler
	- Interpret
- **Celé zpracování programu**
	- ![[Pasted image 20260526200134.png]]
- Struktura a činnost překladače
	- ![[Pasted image 20260526200005.png]]
- Vícevrstvý překladač
	- ![[Pasted image 20260526200228.png]]
- Vnitřní jazyky překladače
	- Jazyk trojic
	- Jazyk čtveřic
## Lexikální, syntaktická a semantická analýza, její varianty (tj. rekurzivní sestup, shora dolů a zdola nahoru).
### Lexikální
- Vstup: text
- Výstup: tokeny
- Token = nejmenší logická jednotka programu
- Lexém = konkrétní hodnota v vstupním textu (hodnota tokenu)
- Regulární gramatiky
	- G = {N, T, S, P}
- Deterministický konečný automat
	- DKA = {Q, $q_0 \in Q$, $F \subset Q$, $\Sigma$, $\delta$}
- Hledáme nejdelší možný řetězec, který lze akceptovat
### Syntaktická
- Vstup: proud tokenů
- Výstup: derivační strom, AST, tabulka symbolů
- **Základní pojmy:**
	- **Levá derivace** = expanduje neterminál nejvíce vlevo
	- **Pravá derivace** = expanduje neterminál nejvíce vpravo
	- **Větná forma** = řetězec $\alpha$ se označuje jako větná forma pokud $S \Rightarrow^* \alpha, \alpha \in (N \cup T^*)$
	- **Věta/slovo** = řetězec $\alpha$ se označuje jako věta, pokud $S \Rightarrow^* \alpha, \alpha \in T^*$
	- **Fráze** = řetězec $\lambda = \alpha \beta \gamma$ je větnou formou, pak je podřetězec $\beta$ frází větné formy pokud $S \Rightarrow^* \alpha A \gamma$ a $A \Rightarrow^* \beta$
		- **Jednoduchá fráze** = fráze kde $A \rightarrow \beta$
	- **L-fráze** = nejlevější jednoduchá fráze
- Bezkontextová gramatika
	- G = {N, T, S, P}
- Zásobníkový automat
	- - ![[Pasted image 20260527110003.png]]
	- PDA = {Q, $\Sigma$, $\Gamma$, $z_0$, $q_0$, $F \subset Q$, $\delta$}
- Shora dolu
	- Rekurzivní sestup
	- PDA – LL(1)
		- Expanze
		- Redukce (srovnání)
	- Greinbachová normální forma => pro ní lze vždy udělat LL(1)
	- First
	- Follow
	- Je LL(1)?
		- Nesmí mít levou rekurzi
		- $FIRST(\alpha FOLLOW(A)) \cap FIRST(\beta FOLLOW(A)) = \emptyset$
			- $\alpha \in (N \cup T)^*$
			- $A \in N$
	- First-first kolize
		- Levá faktorizace
			- $A \rightarrow \alpha \alpha_1 | \alpha \alpha_2 | \dots$
			- $A \rightarrow \alpha A'$
			- $A' \rightarrow \alpha_1 | \alpha_2 | ...$
	- First-follow kolize
		- Odstranění $\epsilon$ pravidel
		- Pohlcení terminálu
	- Silná vs Obecná
	- Příklad:
		- ![[Pasted image 20260603085224.png]]
- Zdola nahoru
	- Operace:
		- Shift
		- Reduce
	- LR
	- Zpracovává větší třídu jazyků než LL
	- LR(0)
		- Stačí mi pouze zásobník k rohodnutí
		- Graf LR položek
			- . na konci => shift
			- . uprostřed => redukuju
	- Když mám kolizi v grafu:
		- SLR(1) => k rozhodnutí používám i 1 znak na vstupu
		- Follow v kolizním pravidlu u toho pravidla, kde mám dělat reduce
	- Když se ani s přečtením vstupu nedokážu rozhodnout:
		- LALR(1)
		- Vytvářím si Look aheady
		- Pokud ve follow množině je ten look ahead tak podle toho pravidla udělám reduce
### Sémantická
- Vstup: AST
- Výstup: víme, že program má jasný smysl
- Základní vlastnosti:
	- Odmítnout co nejvíce špatných programů
	- Přijmout co nejvíce správných programů
	- Shromáždění užitečných informací
- Způsoby implementace:
	- Atributovaná gramatika
	- Rekurzivní procházení AST
- Vyhodnocování atribut
	- Syntetizované atributy
		- ![[Pasted image 20260527221000.png]]
	- Dědičné atributy
		- ![[Pasted image 20260527221526.png]]
- Statický vs Dynamický rozsah
- Tabulka symbolů
	- Mapování jména na deskriptor
	- Operace: vlož rozsah, odstraň rozsah, najdi rozsah, najdi symbol, vlož symbol
	- Zpracování identifikátorů
	- Při debuggování bývá dostupná za běhu
- Typová kontrola
	- Silný typový systém = nikdy nedovolí typovou chybu
	- Slabý typový systém = za běhu může dojít k typové chybě
	- Odvozování typů:
		- Explicitní
		- Implicitní
# 9. Formální prostředky pro popis vyšších programovacích jazyků – gramatiky a jejich členění, vlastnosti gramatik, způsoby zápisu gramatik a nástroje pro jejich zpracování, využití gramatiky k tvorbě překladače.
- Gramatika = G = (N, T, S, P)
	- $P: (N \cup T)^*N(N \cup T) \rightarrow (N \cup T)^*$
- Jazyk = L(G) = {$w \in T^*$|$S \overset{*}{\implies} w$}
- **Členění gramatik:**
	- Typ 0 – $(N \cup T)^*N(N \cup T) \rightarrow (N \cup T)^*$
		- Turingův stroj
	- Typ 1 – $\alpha A \beta \rightarrow \alpha \gamma \beta$
		- Lin. omez. Turingův stroj (velikost paměť je $k \cdot n$, kde $n$ je velikost vstupu)
	- Typ 2 – $A \rightarrow \alpha$
		- Nedeter. zásobníkový automat
	- Typ 3 – $A \rightarrow aB, A \rightarrow a$
		- Konečný automat
- **Vlastnosti:**
	- Jednoznačnost X Víceznačnost
		- Nutná podmínka jednoznačnosti:
			- Má levou a pravou rekurzi $\implies$ není jednoznačná
	- Rekurzivita
	- Redukovanost
		- Neproduktivní symboly
		- Nedosažitelné symboly
- **Způsoby popisu + nástroje pro zpracování:**
	- Typ 3
		- Gramatika, KA, Regex
		- KA = {$Q, q_0 \in Q, F \subset Q, \Sigma, \delta$}
		- NKA
		- Každý NKA lze převést na DKA
	- Typ 2
		- Gramatika, PDA, BNF
		- PDA = {$Q, \Sigma, \Gamma, q_0 \in Q, z_0 \in \Gamma, \delta$}
- **Využití gramatik pro tvorbu překladače:**
	- Typ 3
		- Lexikální analýza
		- Spojování automatů do jednoho velkého
	- Typ 2
		- Syntaktická analýza
		- Shora dolu
			- Rekurzivní sestup
			- PDA – LL(1)
				- Expanze
				- Redukce (srovnání)
			- Greinbachová normální forma => pro ní lze vždy udělat LL(1)
			- First
			- Follow
			- Je LL(1)?
				- Nesmí mít levou rekurzi
				- $FIRST(\alpha FOLLOW(A)) \cap FIRST(\beta FOLLOW(A)) = \emptyset$
					- $\alpha \in (N \cup T)^*$
					- $A \in N$
			- First-first kolize
				- Levá faktorizace
					- $A \rightarrow \alpha \alpha_1 | \alpha \alpha_2 | \dots$
					- $A \rightarrow \alpha A'$
					- $A' \rightarrow \alpha_1 | \alpha_2 | ...$
			- First-follow kolize
				- Odstranění $\epsilon$ pravidel
				- Pohlcení terminálu
			- Silná vs Obecná
			- Příklad:
				- ![[Pasted image 20260603085224.png]]
		- Zdola nahoru
			- Operace:
				- Shift
				- Reduce
			- LR
			- Zpracovává větší třídu jazyků než LL
			- LR(0)
				- Stačí mi pouze zásobník k rohodnutí
				- Graf LR položek
					- . na konci => shift
					- . uprostřed => redukuju
				- Příklad:
					- ![[Pasted image 20260610085426.png]]
					- ![[Pasted image 20260610085433.png]]
			- Když mám kolizi v grafu:
				- SLR(1) => k rozhodnutí používám i 1 znak na vstupu
				- Follow v kolizním pravidlu u toho pravidla, kde mám dělat reduce
			- Když se ani s přečtením vstupu nedokážu rozhodnout:
				- LALR(1)
				- Vytvářím si Look aheady
				- Pokud ve follow množině je ten look ahead tak podle toho pravidla udělám reduce
# 10. Způsob překladu různých programových konstrukcí vyšších jazyků, překlad příkazů, zpracování deklarací, práce s objekty, volání podprogramů. Přidělování paměti. Interpretační zpracování.
## Způsob překladu různých programových konstrukcí vyšších jazyků, překlad příkazů, zpracování deklarací, práce s objekty, volání podprogramů. 
- Vstup: AST
- Výstup: instrukce
- Jazyk čtveřic, trojic
- **Generování instrukcí** – odvíjí se od cílové platformy
- **Generování kódu** – podobné jako rekurzivní sestup
- **Překlad příkazů:**
	- Zpracování konstant
	- Zpracování aritmetiky
	- Zpracování podmínek
- **Zpracování deklarací:**
	- Nepotřebuje explicitní instrukce
	- Stačí vymezit místo v paměti pro proměnnou
- **Práce s objekty:**
	- Polymorfismus
	- **Class Instance Record (CIR)**
		- ![[Pasted image 20260529114030.png]]
	- **Tabulka skoků**
		- Jedna pro každou třídu
		- ![[Pasted image 20260603143906.png]]
- **Volání podprogramů:**
	- Aktivační záznam:
		- Statický ukazatel (kdo deklaroval)
		- Dynamický ukazatel (kdo volal)
		- Návratovou adresu
	- Báze (BP)
	- Vrchol (SP)
	- ![[Pasted image 20260529105300.png]]
	- **Předávání parametrů:**
		- Výsledkem
		- Referencí
		- Hodnotou
	- **Předávání podprogramů:**
		- Ad-hoc (prostředí kde je funkce předaná)
		- Hluboká (prostředí kde je funkce definovaná)
		- Mělká (prostředí kde je funkce vykonaná/volaná)
## Přidělování paměti. 
- Typicky rozdělena na:
	- Oblast pro program
	- Oblast pro statický data
	- Oblast pro zásobník
	- Oblast pro haldu
	- ![[Pasted image 20260529120738.png]]
- **Druhy:**
	- Statické
	- Dynamické
- **Ukládání pole:**
	- ![[Pasted image 20260610120316.png]]
	- Po řádcích
		- $K_1$ = velikost
		- $K_k = H_{k-1} \times K_{k-1}$
		- $a[i_1, i_2, i_3, \dots, i_n] = \sum_{k = 1}^{n-1}(i_k * K_K)$
	- Po sloupcích
		- $K_1$ = velikost
		- $K_k = (H_{k-1} - D_{k-1} + 1) \times K_{k-1}$
		- $a[i_1, i_2, i_3, \dots, i_n] = \sum_{k = 1}^{n}((i_k - D_k) * K_K)$
- **Ukládání struktur**
	- Několik položek různých typů seskupených dohromady
	- ![[Pasted image 20260529130024.png]]
- **Alokace dynamické paměti:**
	- **Typy podle zprávy:**
		- Explicitní (malloc)
		- Implicitní (new)
	- **Sledování volného místa:**
		- **Implicitní seznamy:**
			- Spojový seznam všech bloků (volných i obsazených)
			- Př.: na začátku mám paměť o velikosti 100 bytů, někdo udělá `malloc(20)` a v paměti vznikne seznam o dvou blocích, kde jeden má 20 bytů a druhý 80 a je označen jako volný
			- ![[Pasted image 20260529155724.png]]
		- **Explicitní seznamy:**
			- Spojový seznam pouze volných bloků
			- ![[Pasted image 20260529155800.png]]
		- **Oddělené explicitní seznamy:**
			- Různé spojové seznamy pro různě velké třídy bloků
		- **Bloky řazené podle velikosti:**
			- Vyvážený strom s ukazateli na další bloky s délkou jako s klíčem
	- **Algoritmy:**
		- First-fit
		- Next-fit
		- Best-fit
- **Fragmentace:**
	- Interní
	- Externí
- **Garbage kolekce:**
	- Mark and Sweep
	- Stop and Copy
	- Java
		- ![[Pasted image 20260529172545.png]]
		- Pro minor používá Stop and Copy
		- Pro major používá Mark and Sweep
## Interpretační zpracování.
- Celý proces je stejný jako u překladače
- ![[Pasted image 20260610121410.png]]
- Rozdíl je pouze v závěrečné fázi
	- Překladač generuje kód – vytváří soubor s intrukcemi pro CPU
	- Interpret vykonává program rovnou