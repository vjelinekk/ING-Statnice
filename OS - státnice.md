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