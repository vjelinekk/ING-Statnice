# 1. Definice a význam architektury software, vztah ke kvalitativním charakteristikám software. Architektonické styly, účel, jednotlivé styly, dopady na vlastnosti software.
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
## Architektonické styly, účel, jednotlivé styly, dopady na vlastnosti software.
- ![[Pasted image 20260519153033.png]]
- **Architektonický styl** = pojmenovaná kolekce architekturálních rozhodnutí, která:
	- definuje obecnou struktury a principy systému
	- popisuje rodinu systémů se společnými charakteristikami
- **Architektonický vzor** = ověřené řešení pro konkrétní, opakující se architektonický problém
- Styl vs. Vzor analogie:
	- Styl je plán města (definuje, kde jsou obytné zóny, křižovatky apod.)
	- Vzor je pak např. Kruhový objezd (osvědčené řešení konkrétního problému)
- **Účel:**
	- Slouží jako slovník prvků návrhu
		- Definuje: typy komponent a konektorů
		- Např.: pipes, filtry, objekty, servery
	- Množina pravidel konfigurací
		- Topologické omezení
	- Sémantická interpretace
		- Kompozice prvků návrhů mají definovaný význam
### Hlavní program a subrutiny
- ![[Pasted image 20260519171839.png]]
- Dekompozice je založena na oddělení jednotlivých funkčních processing kroků
- **Komponenty:**
	- Hlavní program
	- Subrutiny
- **Konektory:**
	- Volání procedur
- **Topologie:**
	- Orientovaný graf
	- Hierarchické a statická organizace komponent
- **Výhody:**
	- Modularita
	- Subrutiny jde jednoduše vyměnit
- **Nevýhody:**
	- Špatně škáluje
- **Využití:**
	- Malé aplikace
### Objektově orientovaný styl
- ![[Pasted image 20260519172346.png]]
- Stav je zapouzdřen společně s operacemi nad objektem
- **Komponenty:**
	- Objekty
- **Konektory:**
	- Zprávy
	- Volání metod
- **Topologie:**
	- Různorodá
- **Výhody:**
	- Integrity datových operací
	- Abstrakce
- **Nevýhody:**
	- Objekty musí znát identitu (referenci/ukazatel) využívaných objektů
- **Využití:**
	- Vztahy mezi entitami jsou důležité
	- Komplexní a dynamické struktury
### Vrstevnatý (Layered) styl
- ![[Pasted image 20260519172724.png]]
- Seřazená sekvence vrstev, kde je každá vrstva server (pro vrstvu pod sebou) a klient (pro vrstvu nad sebou) 
- **Komponenty:**
	- Vrstvy složené z subkomponent
- **Konektory:**
	- Volání procedur
- **Topologie:**
	- Lineární
- **Výhody:**
	- Jasná struktura závislostí
	- Nižší vrstvy jsou nezávislé na vyšších
- **Nevýhody:**
	- Sinkhole Anti-pattern (průchod požadavku vrstvami bez provedení jakékoliv byznys logiky)
- **Využití:**
	- Operační systémy
	- TCP/IP, ISO/OSI
### Client-Server
- ![[Pasted image 20260519175747.png]]
- Klient pošle request serveru, který vykoná operaci/odpoví
- **Komponenty:**
	- Klienti
	- Servery
- **Konektory:**
	- Vzdálené volání funkcí
	- Síťové protokoly
- **Topologie:**
	- Dvou úrovňová
- **Výhody:**
	- Centralizované výpočty a data na serveru
- **Nevýhody:**
	- Single point of failure
- **Využití:**
	- Místa, kde je vyžadována centralizace
	- Klienti vykonávají pouze jednoduché UI úkoly
### Batch Sequential styl
- ![[Pasted image 20260519180255.png]]
- Oddělené programy jsou postupně spuštěny; data se předávají jako agregát mezi programy
- **Komponenty:**
	- Nezávislé programy
- **Konektory:**
	- Přenašeči dat mezi programy
- **Topologie:**
	- Lineární
- **Výhody:**
	- Opakovatelné vykonání
	- Jednoduchost
- **Nevýhody:**
	- Nemožnost souběžného zpracování
- **Využití:**
	- Zpracování transakcí
### Pipe and Filter
- ![[Pasted image 20260519180603.png]]
- Oddělené programy jsou postupně spuštěny (potenciálně i souběžně); data se předávají jako stream z jednoho programu do druhého
- **Komponenty:**
	- Nezávislé programy (filtry)
- **Konektory:**
	- Směrovači streamů (pipes, roury)
- **Topologie:**
	- Pipeline
- **Výhody:**
	- Nezávislost filtrů
	- Jednoduchá struktura data streamů
- **Nevýhody:**
	- Vysoká režie na transformaci dat (při předávání mezi filtry)
- **Využití:**
	- UNIX shell
	- Zpracování signálů
	- Distribuované systémy
### Blackboard styl
- ![[Pasted image 20260519181049.png]]
- Nezávislé programy komunikují skrze jedno společné datové úložiště
- **Komponenty:**
	- Blackboard
	- Komponenty operující nad blackboardem
- **Konektory:**
	- Volání funkcí
	- Databázové dotazy
	- Přímé odkazy do paměti
- **Topologie:**
	- Hvězda
- **Výhody:**
	- Komplexní strategie pro komplexní problémy
- **Nevýhody:**
	- Bottleneck synchronizační režie
	- Netederminismus
- **Využití:**
	- Problem-solving architektury
### Rule-Based styl
- ![[Pasted image 20260519181445.png]]
- Inferenční engine parsuje vstup od uživatele a určuje zda je to fakt/pravidlo nebo dotaz
	- Pokud je to fakt/pravidlo vloží ho do znalostní báze
	- Pokud je to dotaz použije fakty a pravidla pro jeho zodpovězení
- **Komponenty:**
	- UI
	- Inferenční engine
	- Znalostní databáze (Knowledge base)
- **Konektory:**
	- Volání funkcí
	- Sdílená paměť
- **Topologie:**
	- Těsně provázané (tightly coupled) tři vrstvy
- **Výhody:**
	- Chování aplikace se dá jednoduše upravit přidáním/odebráním pravidel z znalostní DB
- **Nevýhody:**
	- Konflikty v pravidlech
- **Využití:**
	- Expertní systémy
	- Prolog
# 2. Doménově specifické architektury (cloud, edge, AI, bezpečné systémy, ...), hlavní složky, dopady na vlastnosti (výkon, spolehlivost, integrace, cena, bezpečnost). Produktové řady, variabilita software na úrovni architektury. Modelem řízený vývoj (MDD, MDA) - účel a koncept, role UML, způsoby realizace.
## Doménově specifické architektury (cloud, edge, AI, bezpečné systémy, ...), hlavní složky, dopady na vlastnosti (výkon, spolehlivost, integrace, cena, bezpečnost).
- **Tři klíčové faktory:**
	- Doména – je nutná pro zúžení prostoru problému (problem space) a efektivní řízení procesu vývoje
	- Byznys – cíle byznysu (jako minimalizace nákladů) jsou hlavním drivem pro využití DSSE
	- Technologie – je potřeba mít dostupné různé druhy technologií a postupů abychom dokázali řešit problémy v naší doméně
- **Domain-Specific Software Engineering (DSSE)**
	- Tradiční přístup SW inženýrství se soustředí na vytváření řešení from scratch pro každý nový problém
	- U DSSE využíváme získané zkušenosti na řešení opakujících se problémů
	- Soustředíme se na řešení pouze "rozdílů" mezi novým systémem a již existujícími řešení
- **Rozdíly v přístupech:**
	- **Tradiční SW inženýrství:**
		- ![[Pasted image 20260519184627.png]]
	- **SW inženýrství založené na architekturách:**
		- ![[Pasted image 20260519184654.png]]
	- **DSSE:**
		- ![[Pasted image 20260519184711.png]]
- **Použití DSSE:**
	- Vytvoření množiny artefaktů, které jsou více specifické než obecné SW architektury
- **Výsledky použití DSSE:**
	- Doménový model (množina artefaktů zachycující informace o doméně)
	- Domain Specific Software Architecture (DSSA)
### DSSA
- **Skládá se z:**
	- Referenční architektury
	- Knihovny komponent
	- Aplikační konfigurační metoda
### Cloud Architektura (Cloud Native)
- Zdroj: https://aws.amazon.com/what-is/cloud-native/
- Vývoj, nasazování a správa aplikací v cloudovém prostředí
- Umožňuje vytváření škálovatelných, flexibilních a odolných aplikací
- **Hlavní složky:**
	- Neměnná infrastruktura
	- Microservices
	- API
	- Service Mesh – vrstva zajišťující komunikaci mezi microservices
	- Kontejnery
- **Dopady:**
	- Výkon – horizontální škálování
	- Spolehlivost – vysoká (zóny dostupnosti, Circuit Breaker)
	- Integrace – asynchronní Event-Driven přes Message Brokery
	- Cena – odvíjí se od množství využívaných zdrojů
	- Bezpečnost – využívá se Zero Trust Architecture
### Edge Architektura
- Přesun výpočetní kapacity, ukládání a síťových prvků co nejblíže ke zdroji dat (např. IoT Senzory)
- **Hlavní složky:**
	- Edge Nodes
	- Odlehčená běhová prostředí
	- Lokální časové databáze – speciální DB pro ukládání a čtení time-stamped dat
	- Senzorové sítě – distribuované systémy autonomních uzlů, spolupracující na monitorování fyzikálních veličin
- **Dopady:**
	- Výkon – extrémně nízká latence komunikace, ale výpočetní síla uzlů je menší
	- Spolehlivost – lokální autonomie
	- Integrace
		- East-West – komunikace mezi jednotlivými různými edge nodes
		- North-South – ukládání dat do centrálního cloudu
	- Cena – vyšší investiční náklady na lokální HW, ale úspory za síťový přenos
	- Bezpečnost – vysoké riziko fyzického napadení uzlu
### AI Architektura
- Systémový návrh pro trénování, průběžné nasazování a monitorování modelů SU v produkci
- **Hlavní složky:**
	- Trénovací pipeline
	- Feature Store
	- Model Registry
	- DW a DL
	- Inference Engine
- **Dopady:**
	- Výkon – mnoho GPU + optimalizovaný kód
	- Spolehlivost – křeká, datový drift
	- Integrace – ETL
	- Cena – velice drahé
	- Bezpečnost – riziko data poisoning a advesarial attacks
### Bezpečné systémy
- Architektura pro domény, kde selhání SW může znamenat smrt člověka
- **Hlavní složky:**
	- Trusted Computing Base (TCB)
	- Determenistické HW sběrnice
	- Mechanismy redundance
	- HW časovače
- **Dopady:**
	- Výkon – omezený (žadné dymaické paměti, apod.), RTOS
	- Spolehlivost – extrémní
	- Integrace – téměř nemožná
	- Cena – byrokracie kolem certifikací vývoj zdražuje
	- Bezpečnost – Safety + Security
## Produktové řady, variabilita software na úrovni architektury.
- **Produktová řada** = množina souvisejícíh produktů, které sdílejí podobné vlastnosti, často na úrovni architektury
	- Velmi silný přístup v SWE
	- Je to součástí solution space
	- ![[Pasted image 20260520202615.png]]
	- Např.:
		- ![[Pasted image 20260520202700.png]]
## Modelem řízený vývoj (MDD, MDA) - účel a koncept, role UML, způsoby realizace.
- **MDD** = paradigma SWE, ve kterém primárním artefaktem vývojového procesu není zdrojový kód ale formální model
	- Zdrojový kód je vnímám jako vedlejší produkt
	- Zdrojový kód je možné vygenerovat z modelu
- **MDA** = způsob návrhu SW, kde oddělujeme specifikaci systémových funkcionalit od implementace na konkrétní platformě
	- **Hlavní koncepty:**
		- ![[Pasted image 20260520203917.png]]
- **Role UML** – umoňuje nám z UML diagramů generovat kód
- **Způsoby realizace:**
	- Low-Code platformy
	- API First přístup
# 3. Modularita software, skrývání informace, koncept softwarových komponent, kontrakt. Vazby a komunikace mezi moduly, způsoby řešení závislostí, koncept a typy konektorů. Technologické realizace, vazba na konstrukce programovacích jazyků.
## Modularita software, skrývání informace, koncept softwarových komponent, kontrakt.
### Modularita
- = vlastnost SW, která vyjadřuje míru, do jaké je systém dekomponován do modulů, které jasně plní definované dílčí odpovědnosti
	- **Kritéria modularity:**
		- Lokality of Change
		- Nezávislý vývoj modulů
		- Srozumitelnost
		- Encapsulation
		- Nezávislost na operacích
	- **Jednotky modularity:**
		- *"Well defined concern, well defined interface"*
		- Nezávislý vývoj, údržba
		- Znovupoužitelnost
### Skrývání informace
- Každý modul by měl být navržen tak aby zapouzdřoval a skrýval konkrétní návrhové rozhodnutí, která se mohou v budoucnu změnit
- **Principy:**
	1. Specifikace musí poskytnou všem uživatelům všechny informace potřebné k korektnímu použití programu a nic víc
	2. Specifikaci musí poskytnou vývojáři všechny potřebné informace k vytvoření programu a žádné informace na víc (např. jak by se to mělo implementovat)
	3. Specifikaci musí být možné strojově testovat na konzistenci a správnost
- **Prakticky:**
	- Veřejný interface
	- Privátní implementace
### Separation of Concerns
- **Problém:**
	- Kód/modul/vrstva se musí starat o hodně nesouvisejících úloh
- **Přístup:**
	- Rozděl a panuj
- **Princip:**
	- Rozdělení provázaných prvků do separátních features s minimální překrytím
- MVC
- AOP
	- Oddělení Cross-cutting concerns od hlavní byznys logiky aplikace (např. logování, cachování, ...)
	- **Pojmy:**
		- Aspekt = kód zapouzdřující cross-cutting concern
		- Join point = bod během exekuce programu, kde lze "vstoupit"
		- Pointcut = predikát definující Join points
		- Advice = kód, který se má vykonat
		- Weaving = spojení aspektů s cílovým kódem (compile-time, load-time, run-time)
```Java
// 1. CÍLOVÁ TŘÍDA (Byznys logika)
@Service
public class PaymentService {
    // Metoda je prosta jakéhokoliv logování nebo měření času
    public void zpracujPlatbu(String cisloUctu, double castka) {
        System.out.println("Zpracovávám platbu " + castka + " pro účet " + cisloUctu);
        // ... uložení do DB ...
    }
}

// 2. ASPEKT (Průřezový zájem)
@Aspect
@Component
public class PerformanceLoggingAspect {

    // POINTCUT: Regulární výraz určující, KDY se má aspekt aplikovat.
    // Zde: Na jakoukoliv veřejnou metodu uvnitř třídy PaymentService.
    @Pointcut("execution(public * cz.zcu.kiv.swis.PaymentService.*(..))")
    public void serviceMethods() {} // Prázdná metoda sloužící jako identifikátor

    // ADVICE (Around): Kód, který obalí cílovou metodu (Join point)
    @Around("serviceMethods()")
    public Object measureExecutionTime(ProceedingJoinPoint joinPoint) throws Throwable {
        long start = System.currentTimeMillis();
        
        // Zde propouštíme řízení dál - zavolá se skutečná byznys metoda
        Object proceed = joinPoint.proceed(); 
        
        long executionTime = System.currentTimeMillis() - start;
        System.out.println("AOP LOG: Metoda " + joinPoint.getSignature().getName() + 
                           " trvala " + executionTime + " ms.");
        
        return proceed;
    }
}
```
### Koncept SW komponent
- **SW Komponenta** = jednotka kompozice s kontraktem specifikovaným rozhraní a explicitními kontextovými závislostmi, které lze nasadit nezávisle a je předmětem kompozice třetí strany
- SW může být označen jako komponenta právě tehdy když platí, že je:
	1. Black-box SW element
	2. Dobře definované rozhraní
	3. Kompizotovatelné a nasaditelná třetí stranou
	4. Splňující model
- **SW Komponentový model je:**
	- Sémantika komponent
	- Syntaxe komponent
	- Kompozice komponent
### Kontrakt
- = rozhraní s garancemi o chování a významu = formální dohoda mezi volajícím a volaným
- **Úrovně kontraktu:**
	- ![[Pasted image 20260521181919.png]]
## Vazby a komunikace mezi moduly, způsoby řešení závislostí, koncept a typy konektorů.
### Vazby a komunikace mezi moduly
- **Vazba (coupling)** = míra vzájemné závislosti mezi dvěma moduly
	- Existuje mnoho druhů vazeb nejčastěji se rozdělují na:
		- Tight Coupling = vysoká provázanost
		- Loose Coupling = nízká provázanost
	- **Některé druhy:**
		- Content Coupling = modul A přímo upravuje vnitřní paměť modulu B
		- Global Coupling = moduly komunikují přes globální proměnné
		- Control Coupling = modul A posílá modulu B flag, který mu říká jak se má interně chovat (znamená to, že A zná interní logiku B)
- **Typy komunikace:**
	- Synchronní
	- Asynchronní
### Způsoby řešení závislostí
- **Lookup:**
	- **Problém** = jak najít providera
	- **Princip:**
		1. Provider zveřejní endpoint
		2. Klient najde providera a nabinduje se na endpoint
- **Injection:**
	- **Problém** = jak se zbavit boilerplatu
	- Využívá princip Inversion of Control
	- **Princip:**
		1. Provider zaregistruje endpoint
		2. Klient deklaruje závislost
		3. DI kontejner je propojí (resolve)
- **Deferred:**
	- **Problém** = volající je znám pouze za run-time
	- Late Binding
	- Lazy Loading
	- Nevytváříme všechny závislosti komponenty ale pouze zástupné objekty, které se resolvnou až když jsou potřeba
### Koncept a typy konektorů
- **Konektor** = slouží pro interakce mezi komponentami
- **Výhody použití:**
	- Rozdělení výpočtu od interakce
	- Minimalizace závislostí mezi komponentami
	- Heterogenita
- **Role:**
	- Komunikace – přenos dat
	- Koordinace – předání řízení
	- Konverze – transformace interakce z jedné komponenty na druhou
	- Usnadnění (Facilitation) – efektivnější interakci
- **Typy:**
	- Procedure call – klasické volání funkcí/metod
		- ![[Pasted image 20260521192052.png]]
	- Event – poslouchá zda nastala nějaká událost a pokud ano rozešle notifikaci (eventy se často předávají pomocí message brokera)
		- ![[Pasted image 20260521192105.png]]
	- Data access – komunikace s datovým úložištěm (SQL)
		- ![[Pasted image 20260521192119.png]]
	- Linkage – spojení a udržení komponent během operace (Web Socket)
		- ![[Pasted image 20260521192131.png]]
	- Stream – přenos velkého množství dat mezi komponentami (často využívá dalších konektorů data, event)
		- ![[Pasted image 20260521192144.png]]
	- Arbitrator – více komponent se snaží přistupovat k jednomu místu (Load Balancer)
		- ![[Pasted image 20260521192155.png]]
	- Adaptor – umožňuje komunikaci mezi komponentami, které nebyli navrženy tak aby spolu komunikovali (API gateways)
		- ![[Pasted image 20260521192210.png]]
	- Distributor – distribuce dat/úkolů/... mezi několik komponent (Publish-Subscribe)
		- ![[Pasted image 20260521192222.png]]
## Technologické realizace, vazba na konstrukce programovacích jazyků.
- DI kontejnery
- Public interfaces
- Private methods
# 4. Způsoby dokumentace a vizualizace architektury, koncept pohledů. Analýza architektury software, ověření kvality architektury rozsáhlého softwarového systému – kritéria, metody, formy testování a přístup "executable architecture".
## Způsoby dokumentace a vizualizace architektury, koncept pohledů.
- Obecně se využívá:
	- Popis přirozeným jazykem
	- Diagramy
- **Model vs. Vizualizace**
	- **Model** = artefakt zachycující nějaké nebo všechny principální rozhodnutí, které tvoří architekturu
	- **Vizualizace** = způsob jak jsou modely zobrazeny a jak stakeholdeři interagují s těmito zobrazeními
	- **Konkrétní příklad:**
		- Model – abstrakce reálného systému podle architektonického stylu (venkovský dům se stodolou)
		- Vizualizace – výkres
- **Co by měla vizualizace zobrazovat:**
	- Statický vs. Dynamický aspekt
	- **Druhy pohledů:**
		- Bird-eye – ukazuje systém jako blackbox, který interaguje s dalšími systémy
		- Overview – ukazuje jednotlivé DB, aplikace, služby, message brokery, definuje vysoko stupňovou komunikace a architektonické styly
		- Detail – vnitřní struktura, třídy, rozhraní, ERA
- Nápad => Realita => Model => Vizualizace
- **Druhy vazeb:**
	- ![[Pasted image 20260522192601.png]]
- **Kanonická vizualizace** = nejočekávanější způsob jakým se vizuálně reprezentuje určitý typ dat
- **View** = podmnožina návrhových rozhodnutí v architektuře 
- **Viewpoint** = perspektiva, ze které získáme view (pohled manažera/architekta)
#### Druhy vizualizací
- **Textové:**
	- Zobrazují architekturu skrze klasické textové soubory
		- Většinou podle nějakého syntaktického formátu
		- Může to být i přirozený jazyk
	- Dekorace: fonty, barvy, tučný/kurzíva, tabulky, bullet listy
	- Např.: AADL (Architecture Analysis & Design Language)
	- **Výhody:**
		- Hustota informací (celá architektura v jednom souboru)
		- Dobré pro lineární nebo hierarchické struktury
		- Hodně dostupných editorů a nástrojů
	- **Nevýhody:**
		- Může být špatně srozumitelná a overwhelming
		- Nevhodná pro grafové informace
		- Learning curve na syntaxy/sémantiku
- **Ad-Hoc Grafické:**
	- Zobrazuje architekturu jako grafické symboly
	- Většinou maj grafické symboly přiřazený význam (ale nemusí)
	- Např.: vizualizace pro stakeholdery, semi-formální vizualizace, PPT notation, tabule
	- **Výhody:**
		- Jednodušeji srozumitelné pro člověka než text
		- Jednoduché a rychlé na vytvoření
		- Zvládají ne-hierarchické vazby
	-  **Nevýhody:**
		- Sémantická nejednoznačnost
- **UML a podobné:**
	- Kanonická 
	- Jasně definovaná vizuální syntaxe a sémantika
	- Předpokládá jistý model (OOP)
	- Je možné převést do XML
	- **Výhody:**
		- Kanonické
		- Potlačuje nejednoznačnost
		- Dobře se s nimi interaguje
	- **Nevýhody:**
		- Cena a údržba podpůrných nástrojů
		- Těžko se přidává nová sémantika
		- Žádný standard pro interakce
		- Nefunguje dobře pro větší modely
- **Hybridní:**
	- Spojení textu a symbolů
	- ![[Pasted image 20260522200202.png]]
- **Vizualizace vlivu:**
	- Zobrazují důsledek/efekt rozhodnutí v architektuře
	- ![[Pasted image 20260522201730.png]]
- **2.5D/3D:**
	- 2D předává moc málo informací
	- **Výhody:**
		- Blíže k lidskému prostorovému myšlení
		- Kombinuje strukturální a kvantitativní informace
	- **Nevýhody:**
		- Jednoduše se v tom může člověk ztratit
		- Nutná podpora HW a nástrojů
## Analýza architektury software, ověření kvality architektury rozsáhlého softwarového systému – kritéria, metody, formy testování a přístup "executable architecture".
- Ne-funkční požadavky => architektura => analýza
- **Evaluace architektury** = určování kvality (fit for purpose)
- **Analýza architektury** = určování vlastností systému
- **Hlediska relevantní pro analýzu architektury:**
	- Cíl analýzy
	- Rozsah analýzy
	- Hlavní analyzovaný aspekt architektury
	- Úroveň formality modelů
	- Typ analýzy
	- Úroveň automatizace
### Analýza architektury
- = aktivita hledání důležitých vlastností systému s využitím architektury
- **Kategorie technik analýzy:**
	- Model-based
	- Simulation-based
	- Prototype- and code-based
	- Inspection- and review-based
	- Statická analýza
	- Dynamická analýza
	- Analýza řízená scénáři
#### Model-Based
- Manipulace s popisem architektury k objevení vlastností architektury
- Tool-driven
- Užitečná zejména pro určení "tvrdých" vlastností
	- Např.: hodnoty vybrané metriky
- Většinou se soustředí pouze na jeden aspekt
#### Simulation-Based
- Vyžaduje vytvoření executable modelu
- Simulace musí mít identické chování jako implementace systému
- Z některých modelů ani není možné vytvářet tyto simulace
### Architekturální a Simulační modely
- ![[Pasted image 20260523115001.png]]
### Evaluace SW architektury
- 4 hlavní metriky:
	- Completeness
	- Consistency
	- Compatibility
	- Correctness
#### Completeness
- Je to interní i externí cíl
- **Externí:**
	- Podporuje architektura všechny funkční a ne-funkční požadavky?
	- Složitosti:
		- Komplexita systémových požadavků a architektur
		- Využití mnohoa notací pro zachycení všech komplexních požadavků
- **Interní:**
	- Byli namodelovány všechny prvky?
	- Byli zachyceny všechny návrhové rozhodnutí?
#### Consistency
- Vnitřní vlastnost architektury
- Dimenzi konzistence:
	- Název
		- Komponenty, konektory, služby, eventy, ...
		- Může být ne-triviální na úrovni architektury
	- Rozhraní
		- Zahrnuje konzistenci pojmenování
		- Parametry komponent
		- ![[Pasted image 20260522211613.png]]
	- Chování
		- Názvy a rozhraní interagujícíh komponent se může shodovat ale chování jsou odlišná
	- Interakce
		- Názvy, rozhraní a chování interagujícíh komponent je správné ale jejich interakce stejnak nefunguje
		- Např.:
			- Komponenta pro práci se souborem co poskytuje: `open()`, `read()`, `close()`
			- Klientská komponenta zavolá `read()` bez toho aby nejdřív udělala `open()` a padne to
	- Zjemňování (Refinement)
		- Zachování konzistenci při zdetailňování architektury
		- ![[Pasted image 20260522214030.png]]
#### Compatibility
- Zajišťuje, že model splňuje požadavky (guidelines) a omezení na:
	- Styl
	- Referenční architekturu
	- Architektonický standard
#### Correctness
- Externí vlastnost architektury
- Zaručuje že:
	- Model plně splňuje systémovou specifikaci
	- Implementace splňuje architekturu
### Evaluace a analýza architektury při vývoji
- **Přístupy:**
	- Inspekce návrhu (schůzka, kde ostatní vývojáři/manažeři validují návrh, Lame Waterfall)
	- Try before build
	- Early risk analysis (Spirálový model)
	- Model based (MDD)
	- Testování a Executable architektura (xUP)
	- Text-Implement-Refactor (Agile/TDD)
#### ATAM
- = Architectural Trade-off Analysis Method
- Založeno na scénářích
- Human-centric přístup, který se snaží identifikovat rizika v brzkých fází vývoje
- Soustředí se hlavně na ne-funkční požadavky
- **Proces:**
	- ![[Pasted image 20260523120000.png]]
# 5. Struktura a funkcionality operačního systému. Jádro operačního systému, účel, typy jader a rozdíly mezi nimi. Subsystémy OS. Režim jádra a uživatelský režim, příklad využití bottom half při obsluze blokujících operaci s I/O periferií.
## Struktura a funkcionality operačního systému
- **Struktura:**
	- Typicky vrstevnatá struktura
	- **Obecně by se dalo říct, OS se řídí touto strukturou:**
		1. HW
		2. Kernel Space
		3. User Space
	- Výjimkou mohou být třeba RTOS, kde často nechceme overhead s přepínáním mezi User Space a Kernel Space
- **Funkcionalita:**
	- Dva pohledy na OS:
		- **Bottom-Up (Správce prostředků):**
			- PC má omezené zdroje (čas CPU, RAM, disk, síť)
			- OS zajišťuje spravedlivé přidělování těchto zdrojů
		- **Top-Down (Rozšířený stroj):**
			- OS slouží jako abstrakce HW
			- Místo disku máme soubory, místo CPU procesy, ...
## Jádro operačního systému, účel, typy jader a rozdíly mezi nimi
- **Kernel** = ústřední řídicí program, sloužící jako prostředník HW a SW
	- Při bootstrapu OS je jádro nahráno do RAM, kde zůstane po celý běh OS
- **Účel:**
	- Abstrakce HW
	- Přidělování zdrojů
	- Zajištění bezpečnosti a izolace
- **Typy jader:**
	- ![[Pasted image 20260524135754.png]]
	- **Monolithic:**
		- ![[Pasted image 20260523145821.png]]
		- Jádro obsahuje veškeré služby OS
		- Máme dva podtypy: 
			- **Pure Monolithic** – veškerý kód OS je zkompilován do jednoho statického binární souboru
			- **Modern Monolithic** – všechny ovladače a subsystémy běží v jednom sdíleném adresním prostoru a CPL0 ale není to jeden statický binární soubor
		- Redukuje množství nutných context switchů a posílání zpráv mezi procesy => rychlejší než Microkernel
		- Velké množství kódu v CPL0 => jádro je náchylnější k fatálním bugům
	- **Microkernel:**
		- ![[Pasted image 20260523150011.png]]
		- Většina služeb jádra běží v user space
		- Jádro poskytuje pouze základní služby (správa paměti, plánování, IPC)
		- Jádro je víc responsivní
		- Větší stabilita jádra
		- Vhodné pro distribuované OS
		- Možné problémy při bootování (Jádro potřebuju načíst ovladač pro čtení z pevných disků ale k tomu potřebuje ovladač k čtení z pevných disků 🤦)
	- **Hybrid:**
		- Kombinace Mono a Micro
	- **Exokernel:**
		- ![[Pasted image 20260523150906.png]]
		- Minimalistická architektura
		- Neabstrahuje HW
		- Veškerou zátěž s abstrakcí HW přesouvá do user space
		- Např.: jádro nemá funkci jako je `fopen`, jednoduše přidělí procesů fyzické bloky a ten si na nima provede vlastní abstrakci
## Subsystémy OS
### Správa procesů
- **Proces** = instance běžícího programu
- **Vlákno** = jednotka plánování CPU
- Ve většině moderních OS je proces wrapper na vlákna
- Vlákna v procesu sdílejí stejný adresní prostor
- **Nepreemptivní plánování** = jádro nemůže vláknu násilně sebrat čas na CPU
	- First Come First Serve
	- Shortest Job First
- **Preemptivní plánování** = jádro může libovolně brát vláknům čas na CPU
	- Shortest Remaining Time
	- Multilevel Feedback
- **Time Slicing – Uniprocessor**
	- Právě jedno vlákno běží na jednom CPU jádře
	- Pro napodobení konkurence musíme vlákna přepínat
	- U time slicingu rozdělujeme čas na CPU do jednotlivých kvant
- **Kooperativní multitasking** – jádro nechává vlákna využívat CPU dokud se ho nevzdají `yield`
- **Preemptivní multitasking** – časovač generuje přerušení a jádro na něj reaguje
- **Process Control Block** – obsahuje informace o procesu (adresní prostor, PID)
- **Kontext vláken**
	- Při přepínání vláken, jádro vždy uloží aktuální kontext než nahraje ten nový
	- Kontext je definovaný proměnnými (registry, stack, paměť)
	- **Thread Control Block (TCB)**
		- Struktura, kterou spravuje jádro a obsahuje informace o vlákně
		- Obsahuje:
			- Obsah registrů
			- Prioritu
			- Stav
			- Ukazatel na PCB
			- Další specifické informace
- **User Thread** = vlákna jsou spravována v user space (CPL3)
- **Kernel Thread** = vlákna jsou spravována v kernel space (CPL0)
- **Základní stavy vláken:**
	- ![[Pasted image 20260524154557.png]]
- **Window SMP stavy vláken:**
	- ![[Pasted image 20260601111920.png]]
- **Plánování vláken:**
	- **Round Robin**
		- Bez priorit
		- Kvanta
		- Krátké kvanta => víc času se stráví na kontext switchech
		- Dlouhé kvanta => horší responzivita OS
	- **Round Robin s prioritama**
	- **Plánovač Linuxu**
		- Důležité procesy dostávají delší kvanta
		- Kvanta se přizpůsobují podle využití CPU
		- Snaží se udržet tasky na stejném jádře (core)
		- O(1) plánovač => Completely Fair Scheduler => EEVDF
		- **CFS:**
			- **Základní smyčka plánovače (Core Loop)**
				1. Plánovač najde v červeno-černém stromu uzel úplně nejvíce vlevo (čekající proces s nejmenším `vruntime`).
				2. Vyjme tento proces ze stromu a spustí ho na procesoru.
				3. Při dalším tiknutí hardwarového časovače jádro změří, jak dlouho proces reálně běžel.
				4. Jádro tento čas přepočítá podle priority (hodnoty _Nice_) a přičte ho k `vruntime` běžícího procesu.
				5. Jádro se podívá do stromu a zkontroluje, zda tam neleží proces s menším `vruntime`, než má teď ten běžící.
				6. Pokud má běžící proces stále nejmenší `vruntime`, pokračuje dál v běhu na procesoru (návrat na krok 3).
				7. Pokud má některý čekající proces menší `vruntime`, jádro běžící proces okamžitě zastaví (preempce).
				8. Zastavený proces je vložen zpět do červeno-černého stromu (díky zvýšenému `vruntime` se propadne více doprava).
				9. Cyklus se opakuje a plánovač vybírá nový proces (návrat na krok 1).
			- **Řešení I/O operací (Spánek a probuzení)**
				10. Pokud běžící proces začne čekat na disk nebo síť, je uspán, okamžitě vyřazen ze stromu a plánovač skočí na krok 1.
				11. Jakmile data dorazí, proces se probudí a jádro mu uměle posune jeho `vruntime` těsně pod aktuální minimum stromu.
				12. Probudivší se proces je vložen zpět do stromu a díky nízkému `vruntime` se brzy dostane na procesor.
### Správa paměti
- Přidělování paměti procesům
- **Algoritmy pro správu paměti:**
	- Bitmapy
	- Seznamy
	- Buddy systémy
- **Způsoby hledání místa v paměti:**
	- First-Fit
	- Next-Fit
	- Best-Fit
	- Worst-Fit
	- Quick-Fit
- **MMU** = mapování virtuální adresy na fyzickou
- **Stránkování**
	- **Tabulka stránek:**
		- ![[Pasted image 20240205142104.png]]
		- **Algoritmy při výpadku stránky:**
			- FIFO
			- Least Recently Used
			- Not Recently Used
				- **4 kategorie:**
					- třída 0: R = 0, M = 0
					- třída 1: R = 0, M = 1
					- třída 2: R = 1, M = 0
					- třída 3: R = 1, M = 1
				- Vyhodí stránku z nejnižší neprázdné třídy
			- Second Chance:
				- ![[Pasted image 20240205160933.png]]
			- Clock:
				- Jako Second Chance ale v kruhovém seznamu
	- Page Fault Frequency
	- ![[Pasted image 20260525131535.png]]
	- **TLB** = mapování mezi číslem stránky a rámcem
- Segmentace
#### Dynamické linkování
- Propojení programu s externíma knihovnami, o kterých se ví už při kompilaci
- Lazy binding pomocí tabulek PLT a GOT
- V přeloženém programu není žádný skok na danou funkci ale pouze značka, která se při spuštění programu nahradí
- **PIC** = Position Independent Code = adresy jsou relativní k program counter
#### Dynamic Loading
- Připojení externího kódu o kterém program při spuštění neměl tušení
- Používají se speciální funkce na nalezení a vložení programu
	- `dlopen()` – načti program a dej do RAM
	- `dlsym()` – vyhledání funkce v programu
### Správa souborů
- Část OS poskytující mechanismy pro ukládání a přístupu k datům
- Jedná se o perzistentní ukládání
#### Soubory
- **Soubor** = pojmenovaná sekvence bytů
	- **Typy:**
		 - **Obyčejné soubory:**
			- Data zapsaná aplikacemi
			- Textové nebo binární
		- **Adresáře:**
			- Udržují strukturu FS
		- **Speciální:**
			- Znakové soubory (`/dev/tty`)
			- Blokové soubory (`/dev/sda`)
			- Pojmenované roury
			- Symbolické odkazy
#### Pevný disk
- **Cluster** = nejmenší alokovatelná jednotka skládající se ze sektorů (skupina 1 a více sektorů)
- **Sektor** = základní adrestovatelná fyzická jednotka na disku
- **LBA** = jeden sektor na disku
- **CHS (Cylinder-Head-Sector, Stopa-Hlava-Sektor):**
	- Uvedeme stopu, hlavu disku, číslo sektoru na stopě
- **LBA (Logical Block Adressing)**
	- Čísluje sektory na disku lineárně
#### Oddíly
- **Dělení disku na oddíly**
	- **Master Boot Record (MBR)** – na počátku disku
		- **Master Partition Table (MPT)**
		- Umožňuje 4 primární oddíly
			- **Chceme-li víc:** 
				- Uděláme 3 primární a 1 extended
				- Extended jde dělit na další
		- Struktura MBR
			- ![[Pasted image 20260601133215.png]]
	- **GUID Partition Table (GPT)**
		- Nelimituje na 4 oddíly
		- **Používá:** Mac OS, Windows
		- Struktura GPT
			- ![[Pasted image 20240203150912.png]]
		- Záložní kopie uložena na konci disku
		- Velikost = 512B LBA = 34x512B = 16KB
		- **LBA (Logival Block Addressing)** = logický blok
			- Lineární číslování bloků od 0
#### Způsoby alokace
- **Kontinuální**
- **FAT**
	- ![[Pasted image 20240203195324.png]]
- NTFS
- INode (Ext)
	- ![[Pasted image 20240204122654.png]]
	- ![[Pasted image 20240203204222.png]]
	- **hard link:**
		- ![[Pasted image 20240203212305.png]]
	- **soft link:**
		- ![[Pasted image 20240203212902.png]]
### Správa I/O
#### Blokové a Znakové zařízení
- **Blokové** = zařízení přenáší data v blocích (např.: disky)
- **Znakové** = zařízení přenáší data po znacích (byte) (např.: sériová komunikace)
- ![[Pasted image 20260524212921.png]]
#### VFS
- ![[Pasted image 20260524211430.png]]
- UNIX abstrakce
#### Installable FS
- Windows VFS
- 3 druhy ovladačů:
	- **FS**
	- **Mini Filter – interface pro antiviry**
		- **Filter Manager**
			- ![[Pasted image 20260524213905.png]]
	- **FS FilterDrive – modifikace existujícího FS**
- Používá **IO Request Packet (IRP)**
	- Struktura pro komunikace mezi ovladačem zařízení a kernelem
	- ![[Pasted image 20260524213147.png]]
- **Fast I/O**
	- Zrychlení synchronních operací
	- Využívání cache
	- Vynechá FS a HW
#### Procesy a Soubory
- Každý proces má svůj root a working dir (uloženo v `fs_struct` v PCB)
- File Descriptor
	- 1 – stdout
	- 2 – stderr
#### I/O Subsystém – obecný princip
1. Po zavolání OS API, OS vytvoří I/O request, a přesměruje ho do I/O subsystému
2. Volající vlákno je zablokované dokud se nedokončí požadavek
3. I/O je ve frontě dokud zařízení nedostane požadavek
4. Ovladač zařízení buď vykoná obsluhu nebo přesměruje požadavek dál
5. Po dokončení požadavku je vlákno odblokováno
#### PIC
- Programmable Interrupt Controller
- ![[Pasted image 20260524220329.png]]
#### APIC
- Víc IRQ než PIC
- Umožňuje SMP
- ![[Pasted image 20260524220647.png]]
## Režim jádra a uživatelský režim, příklad využití bottom half při obsluze blokujících operaci s I/O periferií
- **Kernel Space (CPL0)**
	- Zde běží jádro OS
	- CPU umožňuje provádět priviligované instrukce
	- Přímý přístup k HW
- **User Space (CPL3)**
	- Zde běží uživatelské aplikace
	- Nelze provádět priviligované instrukce
	- Přístup k HW lze provádět jen přes systémová volání
- Z CPL3 do CPL0 se dostaneme pomocí volání INT nebo syscall/sysenter
	- `syscall` – nepoužívá IDT => je rychlejší
- Jak se poprvé dostat z CPL0 do CPL3?
	- IRET/IRETQ
- **Top Half**
	- Extrémně rychlá obsluha IRQ
	- Handler provede pouze absolutní minimum potřebné práce
		- Zbytek práce je zařazen do fronty na pozdější zpracování
- **Bottom Half**
	- Běžící démoni/servery v jádře
	- Periodicky zpracovávají události, které vyvolá Top Half
	- **Druhy:**
		- Kritické – SoftIRQ v Linuxu
			- Staticky alokováno k daném CPU jádru
			- Obsluha časově kritických událostí (časovač, síťovka)
			- SoftIRQ stejného typu mohou být spuštěny najednou na různých jádrech
			- Jedne SoftIRQ vykonává Tasklets
		- Plánované – Tasklet
			- Statická i dynamická alokace
			- Vykonávají se na stejné jádře, které je naplánovalo
- ![[Pasted image 20260524223650.png]]
- **Polling** – furt dokola testujeme zda doběhla akce
- **IO Uring**
	- ![[Pasted image 20260524224215.png]]
- **DMA** – přenášení dat z IO zařízení do RAM pomocí specializovaného HW
# 6. Procesy, program jako proces, realizace lehkých vláken. Meziprocesová komunikace a synchronizace na symetrickém multiprocesoru.
## Procesy, program jako proces, realizace lehkých vláken.
- **Program** = spustitelný kód (sekvence instrukcí)
- **Proces** = instance běžícího programu
- **Vlákno** = jednotka plánování CPU
	- Pro programátoru je to funkce
	- Proces vlastní vlákna
- **Thread Control Block (TCB)**
	- Ukládá si kernel
	- Obsahuje:
		- Obsah registrů
		- Prioritu
		- Stav
		- Ukazatel na PCB
		- Další specifické informace
- **Windows User Thread**
	- ![[Pasted image 20260525163749.png]]
- **MP Config:**
	- ![[Pasted image 20260525164639.png]]
- **SMP Bootstrap x86:**
	1. Po zapnutí jsou všechny jádra v real-mode
	2. BIOS vybere Bootstrap Processor (BSP) a zastaví všechny ostatní jádra (to jsou Auxiliary Processor (AP))
	3. BSP vykonávající kód hledá MP configy ostatních jader
	4. Pokud žádné nenajde načte jednoprocesorový kernel
	5. Pokud je najde inicializuje BSP APIC (protected/long mode)
	6. BSP vzbudí ostatní AP pomocí Ini-IPI (Inter-Processor Interrupt)
	7. Vzbuzené AP se přepne do protected/long mode a synchronizuje se s BSP
	8. Jakmile jsou všechny AP synchronizována s BSP, BSP začne používat Local APIC
	9. Dokončení inicializace jádra
- **SMP Scheduling Pitfalls:**
	- Můžeme plánovat vlákna na jaké chceme jádra
	- Ale tím si kazíme využívání cache v rámci jádra a zpomalujeme běh
- **crt0**
- **PCB**
- `fork()`, `execve()`, `clone()`
- **Zombie** = proces, který skončil a nevrátil return code tudíž, jeho rodič o tom neví
### Realizace lehkých vláken
- Situace kdy nad jedním vláknem kernelu (CPL0) běží několik vláken v user space (CPL3)
- Redukuje overhead s změnou CPL
- ![[Pasted image 20260525181751.png]]
## Meziprocesová komunikace a synchronizace na symetrickém multiprocesoru.
### SMP Synchronizace
- U SMP mají jádra pouze jeden způsob synchronizace => atomické instrukce
	- `Add`, `Sub`, `CompareExchange` aka TestAndSet
	- Instrukce prefixuje pomocí `lock`, což uzamkne sběrnici (dřív fyzicky, dnes pomocí protokolu MESI)
	- Instrukce `mov` může být také atomická pokud přesouvá data zarovnaná na word (např. velikost eax)
- **SplinLock**
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
	- **Odemykání:**
		```asm
		mov DWORD PTR [lockState], 0
		```
- **Counting Semaphore**
	- Abstraktní datový typ, který řídí přístup ke sdílenému zdroji
	- Semafor neví nic o sdíleném zdroji
	- Semafor obsahuje pouze:
		- Limit – kolik vláken může využívat zdroj najednou
			- Binární semafor – limit = 1
		- Čítač – kolik vláken je u zdroje
		- Fronta – kolik vláken čeká
	- **Operace:**
		- **Acquire:**
			- `wait`, `down`, `P`
			- Vlákno chce dovnitř => čítač se sníží o 1 pokud to jde jinak je vloženo do fronty čekačůA
			- **Spinlock:**
				```asm
				spin:  
					mov eax, [counter]
					mov edx, eax
					sub edx, 1
					jns trylock
					call doblock
				trylock:
					lock cmpxchg [counter], edx
					jnz spin
				```
			- **TryAcquire** – nemusíme přepínat do CPL0
				```asm
				tryacquire:
					mov eax, [counter]
					mov edx, eax
					sub edx, 1
					
					js failed
					
					lock cmpxchg [counter], edx
					jnz tryacquire
					
					mov al, 1
					ret
				failed:
					mov al, 0
					ret	
				```
		- **Release:**
			- `signal`, `up`, `V`
			```
			release:
				mov eax, 1
				lock xadd [counter], eax        
				
				test eax, eax
				js dounblock
				
				ret                             

			dounblock:
			    call dounblock_os
			```
	- **Producent-Konzument**
	```
		writers = N
		readers = 0
		mutex = 1
		
		producent:
			P(writers)
			P(mutex)
				insert()
			V(mutext)
			V(readers)	
			
		konzument:
			P(readers)
			P(mutex)
				pop()
			V(mutex)
			V(writers)
	```
- **Mutex**
	- Má vlastníka (může ho odemknout jenom to vlákno, které ho zamklo)
### Meziprocesová komunikace
- **Pipe**
	- Buffer se dvěma konci
	- Pro každý konec je file descriptor, jeden konec je pro zápis druhý pro čtení
	- Využítá Producer-Konzument přístupu
- **Messages**
	- Komunikace mezi GUI Windows procesy
	- **Princip:**
		1. Ovladač HW zachytí kliknutí a předá ho subsystému Windows (`win32k.sys)
		2. Windows zjistí na kterým oknem se mys nacházela a kterému procesu okno patří
		3. Window zabalí informaci do MSG struktury a dá jí do fronty zpráv vlákna tvořící grafické okno
		- V grafickém vláknu běží tzv. **message loop**
	- `PostMessage` – asynchronní (neblokující)
	- `SendMessage` – synchronní (blokující)
- **Signals**
	- POSIX
	- Fungují jako asynchronní SW přerušení
	- Registrace a doručení signálu probíhá na úrovní jádra
	- Pro každé vlákno/proces jádro uchovává:
		- Uživatelské signal handlery
		- Spinlock pro ochrany přístupu k signálům
		- 64-bitová maska ignorovaných signálů
		- 64-bitová maska signálů čekajícíh na zpracování
		- Double-ended fronta s čekajícími signály
	- **Příklad:**
		- Vlákno A zavolá funkci `kill(4200, 10)` (kill vlákno B)
			1. Dojde k systémovému volání (CPL0)
			2. Kernel najde strukturu vlákna B
			3. Kernel nastaví bit 10 na 1
			4. Systémové volání skončí a vlákno A (CPL3) pokračuje v běhu
		- V tuhle chvíli se ve vlákně B nic neděje
		- Vlákno B dostane svůj čas na CPU
		- Vlákno B vykonává svou práci a najednou přijde třeba tick timeru a přepne se do CPL0
			1. Vlákno B je pozastaveno a dochází k vykonávání kódu v Kernelu
			2. Kenerl se chystá předat řízení zpět do CPL3 ale nejdřív se koukne do struktury vlákna B a vidí tam, že čeká na zpracování nějakého signálu
		- Kernel ví, že vlákno B má pro signál 10 zaregistrovanou oblsuhu
			1. Kernel vezme obsah registrů vlákna B a uloží je na uživatelský stack (vytvoří tzv. Signal Frame)
			2. Kernel vezme instruction pointer a natvrdo do něj dá adresu té obsluhy signálu
		- Kernel předá řízení zpět user procesu (CPL3)
		- V CPL3 se vykoná obluha signálu
		- Zavolá `sigreturn`
		- Dojde k přepnutí do CPL0
		- Kernel načte pro CPL3 ten Signal Frame a vymaže ten bit v masce
		- Kenrel přepne zpět do CPL3 a vlákno B pokračuje tam kde skončilo
# 7. Systémy reálného času, programování s omezenými prostředky. Virtualizace.
## Systémy reálného času
- = včasnost provedení úkolu je stejně důležitá jako správnost výsledku
- Výpočetně náročné úloze se hodí vyšší výkon (paměť, CPUs)
	- Pokud je úloha schopná dodržet limity, není důvod ke zvyšování výkonu
- RTS velmi často běží na embedded zařízení s omezenou pamětí a výkonem
- RTS využívá tzv. **cost funkci**, která vyčísluje dopad nedodržení termínu
### Požadavky na RTOS
- Plánování s explicitními časovými omezeními
- Předvídatelnost
	- Záruka dodržení deadline
	- Upozornění předem pokud deadline nelze dodržet
- Odolnost vůči chybám
	- Přesně definované chování v případě poruchy
- Zohlednit peak load (systém se nesmí začít laggovat při velké zátěži)
- Udržovatelnost
### Zdroje nedeterminismu
- Cache
- CPU
- I/O → IRQ
- Synchronizace
- Memory Management
- Spouštění procesů
- Plánovač
- Rekurze
### Typy real-time OS
#### Non-real time
- Tradiční OS
- Vlákna se vykonávají maximální možnou rychlostí
- Uživatele zajímá nejkratší doba dokončení
- **Mylná domněnka:** rychlý systém = vhodný pro real time výpočty
#### Soft-real time
- Výpočet nemusí být dokončen co nejdřív ale včas
- Nedodržení termínu vede k selhání
	- Lze tolerovat
	- Např.: zkreslený obraz při videokonferenci
- **Firm-real time** – občasné nedodržení termínu
#### Hard-real time
- Nedodržení termínu = katastrofa
- Např.: airbag, brzda, jaderný reaktor
### Terminologie
- **Task** = postupně prováděná činnost
- **Job** = série jednoho nebo více tasků
- **Resource** = zdroj, který potřebujeme
	- **Aktivní** – procesor
	- **Pasivní** – mutex, semafor, bariéra
- **Schedule** = plán provádění úloh
	- Přiřazení zdrojů jednotlivým úlohám
	- Proveditelný schedule = pořadí provádění úloh, kdy jsou všechny omezení splněna
### Druhy tasků
- **Periodický** – pevně nastaveno na periodické provádění $P_i$
	- Pevná doba mezi příchody
	- Aktivuje se s konstantním ratem
	- Všechny instance mají stejnou dobu výpočtu
	- Např.: čtení teploty motoru každých 20 ms
- **Aperiodický** – opakovaně aktivované bez pravidelné aktivace
	- Zpracování externí události (ISR, inicializace, uživatelský vstup)
	- Náhoda mezi příchody
	- Tolerovatelné zpoždění
		- Ideálně ale nulové
	- Nemůže ublížit žádnému hard deadline tasku
	- Např.: přeskočení skladby v autě
- **Sporadický** – neperiodické tasky oddělené minimální dobou mezi příchody
	- Zpracování externí události
	- Hard deadline – pokud bude delay nastane katastrofa
	- Např.: sešlápnutí brzdy
### Plánování tasků
- **Vhodnost algoritmů**
	- Musíme znát nejhorší čas dokončení (např. HeapSort je předvídatelný oproti QuickSortu)
	- Je lepší se vyhnout evolučním algoritmům (vysoká míra nejistoty)
- Dobré plánování je základem všeho
- Cyklický plánovač
	```c
	while(1) {
	    // --- Minor Cycle 1 (0ms až 20ms) ---
	    Cekaj_Na_Hardwarovy_Tik_Casovace(); // Procesor spí a čeká na tik (např. 20ms)
	    Spust_Task_A();
	    Spust_Task_B();
	    Spust_Task_C();
	
	    // --- Minor Cycle 2 (20ms až 40ms) ---
	    Cekaj_Na_Hardwarovy_Tik_Casovace();
	    Spust_Task_A();
	    // (Task B ani C v tomto tiku neběží, mají čas)
	
	    // --- Minor Cycle 3 (40ms až 60ms) ---
	    Cekaj_Na_Hardwarovy_Tik_Casovace();
	    Spust_Task_A();
	    Spust_Task_B();
	
	    // --- Minor Cycle 4 (60ms až 80ms) ---
	    Cekaj_Na_Hardwarovy_Tik_Casovace();
	    Spust_Task_A();
	    // Na konci tohoto cyklu uběhlo 80ms a smyčka while(1) začíná znovu od Minor Cycle 1!
	}
	```
- Prioritní schéma
	- Odstraňuje nedostatky cyklického plánovače
	- Př.:
		- Mám jenom jedno CPU jádro
		- Mám v autě tři programy:
			- Rádio (nízká priorita)
			- Klimatizace (střední priorita)
			- Brzdy (nejvyšší priorita)
		- CPU pořád hlídá seznam úkolů:
			1. Jedem v klidu, brzda ani klimatizace nic nepotřebují, procesor může věnovat čas rádiu
			2. Teplota v autě stoupne a zapne se klimatizace (protože má prioritu CPU okamžitě stopne rádio)
			3. Krize => musíme začít brzdit => CPU zastaví ostatní a dá prioritu programu brzd
- **Inverze priorit:**
	- Máme tasky:
		- A (vysoká priorita, spí)
		- B (střední priorita, spí)
		- C (nízká priorita, aktivní)
	- Nastane situace:
		- C se vykonává a zamkne kritickou sekci pomocí mutexu `lock(mutex)`
		- Najednou je vzbuzen tak A a kvůli vyšší prioritě se začne vykonávat
		- Task A chce ale přistoupit ke stejné KS, která je aktuálně zamčena taskem C
		- Task A se uspí (čeká na KS) a v tu chvíli se probere task B
		- Task B dostane prioritu oproti C a začne vykonávat nějaký dlouhý úkol
		- No ale kvůli tomu se task s vysokou prioritou nedostane na řadu
	- **Řešení:**
		1. Dědičnost priorit
			- Úloha v KS (v našem příkladu task C) dostane dočasně nejvyšší prioritu ze všech tasků zaseklých na KS aby ho nepředběhl task B
			- Možný problém:
				- Řetězení blokovaných úloh
					- ![[Pasted image 20260602085052.png]]
		2. Priority Ceiling
			- Úloha v KS dostane maximální prioritu, ze všech úkolů, které mohou k této KS přistoupit
#### Rate Monotonic Analysis (RMA)
- Přiřazuje úkolům priority tak aby:
	- Rate Monotonic Scheduler (RMS) našel proveditelný plán (RMA kontroluje zda RMS může uspět)
- Priorita je nepřímo úměrná periodě $\text{priorita} \sim \frac{1}{perioda}$
- **Ratio Grid**
	- Pokud mají úkoly náhodné periody tak podle Lui-Layland existuje bezpečný plán, kde využití CPU je míň jak 70%
	- Při použití Ratio Gridu kdy periody jsou harmonické (jsou to násobky nějaké základní frekvence a jejich poměry jsou celočíselné) tak tato pesimistická hranici se mění na 100%
- **Terminologie:**
	- **Arrival Time** $A_i$ (čas příchodu) – čas kdy je $i$-tý task připraven k provedení
	- **Computation Time** $C_i$ (doba výpočtu) – doba potřebná k dokončení $i$-tého tasku
	- **Absolute deadline** $d_i$ – čas, do kterého by měl být $i$-tý task splněn
	- **Start, finish a release times** $s_i$, $f_i$, $r_i$
	- **Period** $P_i$ – interval mezi dvěma po sobě jdoucími $i$-tými tasky
- **RMS**	
	$$
		U = \sum_{i=1}^{n} \frac{C_i}{P_i} \leq n(\sqrt[n]2 - 1)
	$$
	- Pokud podmínka platí tak je 100% záruka, že všechny úkoly v systému stihnou svoje deadlines
	- Pokud podmínka neplatí je výsledek nejistota
- **Response Time Test**
	$$
		R_0 = \sum_{j=1}^{i} C_j 
	$$
	$$
		R_{k+1} = C_i + \sum_{j=1}^{i - 1} C_j \times \text{ceil} (\frac{R_k}{P_j})
	$$
	- Používá se pokud RMS není jistý
	- Iterujeme dokud $R_k$ nepřestane růst
	- Jestliže $R_k < d_i$  pak $i$-tý task lze naplánovat
	- ![[Pasted image 20260602103510.png]]
- **Earliest Deadline First**
	- Zohledňuje aperiodické a sporadické úkoly
	- Dynamické plánování na základě priorit
		- Tasky jsou v prioritní frontě
		- Vždy se vybírá task s nejbližší deadline $d_i$
		- Pokud je kolize vybere se podle priority
	- Splnitelný plán existuje pokud platí:
$$
	\sum_{i=1}^{n} \frac{C_i}{P_i} \leq 1
$$
## Programování s omezenými prostředky
- Formální metody:
	- Programovací standardy (MISCRA C, ANSI C)
	- Kontrola modelu (UPAAL)
	- Temporální logika (způsob jak matematicky zapsat co se v programu musí nebo nesmí stát v čase)
- Omezené prostředky
	- Správné ukončení
		- Např.: `malloc()` => `free()`, `open()` => `close()`
	- Absence vyjímek za běhu programu
		- Např.: dělení nulou => radši `if`
	- Konečné využití paměti
		- Např.: `User users[MAX USERS]`
### Výběr jazyka
- Assembler
	- Optimalizace
	- Nízkoúrovňové úlohy
- C
	- Vývoj jádra, kvůli absenci syntactic sugaru
	- Minimální režie, ale vysoké riziko pádu
- C++
	- Lepší bezpečnost než C
	- Doporučovaný jazyk
- Ada
	- Navržen pro kritické aplikace
- Rust
	- Vysoká bezpečnost
- Java
	- Příliš mnoho syntactic sugaru a skryté režie
### Konečné využití paměti
- Jádro ani kritická aplikace nesmí selhat kvůli chybě při malloc
- Kritické struktury musí být alokovány jednou
	- Např.: PCB tabulka konečné velikosti
- Alokace paměti s pevnou délkou je předvídatelnější než dynamické pole
### Nepředvídatelné zpoždění přidělení
- `malloc`/`free` fragmentují paměť 
- Defragmentace paměti je časově náročná a netriviální
- **Řešení:** alokovat paměť na začátku programu
- **Memory Pool:**
	- Pro každou velikost existují dva seznamy:
		- První pro volné bloky, druhý pro zabrané
		- Správce paměti přiděluje první volný blok s nejmenší velikostí
### Absence runtime výjimek
- **Výjimy = vysoká režie a nepředvídatelnost**
- Vyhýbat se třeba `if`
### Správné ukončování
- Při inicializace uvažovat o alokaci paměti a případných výjimkách
	- Výsledek musí být jasný
		- Alokace úspěšná => jdeme dál
		- Alokace neúspěšná
- Pokud systém/proces selže musí se to provést přesně definovaným **způsobem**
## Virtualizace
- **Virtualizace vs. Emulace**
	- **Virtualizace** = technologie, která vytváří softwarovou abstrakci reálného hardwaru a umožňuje spouštět více izolovaných operačních systémů současně, přičemž jejich instrukce se provádějí přímo na fyzickém procesoru (dnes prakticky výhradně s využitím hardwarové akcelerace CPU)
	- **Emulace** = softwarový proces, který kompletně napodobuje chování cizí hardwarové architektury a za běhu překládá instrukce určené pro jeden typ procesoru do instrukčního jazyka procesoru jiného, což umožňuje spouštět nekompatibilní software za cenu obrovské ztráty výkonu
### Hypervizor
- Virtual Machine Monitor
- Hostitel, který spouští VM
- Druhy:
	- **Typ 1** – běží přímo na HW (Xen, Hyper-V)
	- **Typ 2** – hostuje ho OS (Virtual Box)
	- ![[Pasted image 20260526175735.png]]
### Popek-Goldbergovo pravidlo
- 3 typy instrukcí:
	- **Privilegované**
		- Instrukce, které jde vykonat jen v CPL0
		- Pokud se zavolají jinde CPU vyvolá výjimku
		- Např.: `CLI`, `STI`
	- **Senzitivní**
		- Mění konfiguraci HW
		- Výsledek závisí na aktuální konfiguraci HW
		- Např.: `POPF`
	- **Klasické instrukce**
		- Většina instrukcí
		- Např.: `ADD`, `MOV`, ...
- **Pravidlo:**
	- Je možné efektivně a bezpečně virtualizovat pouze pokud jsou senzitivní instrukce podmnožinou privilegovaných
### Binární překlad
- Než pustíme hostovaný program ho zanalyzujeme
	- Hledáme a nahradíme unsafe instrukce bezpečnější alternativou
	- Nahrazení instrukcí není triviální
### Paravirtualizace
- Hostovaný OS ví, že neběží přímo na HW
- Volá se API hypervizoru
- Hypervizor přebírá kritické úkoly a bezpečně je vykoná za hostovaný OS
### VT-x (Intel Virtualization Technology)
1. Problém bez VT-x (Paradox jednoho CPL0)
	- V klasickém procesoru existuje pouze **jedna sada** privilegovaných úrovní (Ring 0 až Ring 3).
	- Pokud hostovaná aplikace (ve virtuálu) zavolá `Syscall`, procesor natvrdo přepne do **skutečného CPL0**.
	- **Průšvih:** Na tomto skutečném CPL0 ale sedí kód hypervisoru (Typ 1) nebo hostitelského OS (Typ 2), nikoliv jádro virtuálu.
	- Požadavek tak zachytí nesprávný operační systém, který mu nerozumí, což vede k okamžitému pádu (Crash). Virtuální jádro je kompletně obsenuto.
2. Řešení pomocí Intel VT-x (Dvě paralelní reality)
	- VT-x situaci řeší hardwarovým rozdělením procesoru na dva nezávislé světy: **VMX Root** (pro hypervisor) a **VMX Non-Root** (pro virtuály).
	- V **obou** těchto světech existuje kompletní škála Ring 0 až Ring 3.
3. Jak probíhá komunikace dnes
	- **Uvnitř virtuálu (`Syscall`):** Když aplikace ve virtuálu zavolá `Syscall`, hardware přepne procesor z _Non-Root Ring 3_ do **Non-Root CPL0**. Požadavek tak bezpečně převezme virtuální jádro (Linux), kterému je určen.
	- **Směrem k hardwaru (`VM Exit`):** Teprve když toto virtuální jádro (v Non-Root CPL0) provede _senzitivní instrukci_ (např. zápis do CR3 nebo sahání na reálný hardware), zasáhne křemík procesoru.
	- Procesor vykoná **VM Exit**, který virtuál zmrazí, kompletně přepne realitu do **Root CPL0** a předá řízení hypervisoru, aby požadavek bezpečně odbavil.
- VM Entry – vstup do VM módu
- VM Exit – opuštění VM módu
### Virtualizace a paměť
- **TLB**
	- Pokud by se měl TLB vyprazdňovat při každém VMX transition, bylo by to bezpečné ale pomalé
	- Řešení: **VPID (Virtual Processor ID)**
		- TLB se nemusí vyprazňovat
		- Jádro zakáže přístupu k záznamům v TLB s jiným VPID
- **Stránkování**
	- **Shadow Page Table** = tabulka stránek pro hostitele
		- Hypervizor si drží pro každý OS jeho tabulku stránek a sám provádí mapování
	- **Extended Page Tables:**
		- Představ si **EPT** jako situaci, kdy ti pošťák doručuje dopis do podnájmu v cizím městě. Musí proběhnout dva nezávislé překlady, aby dopis dorazil na správný stůl.
		1. První krok: Virtuální realita (Uvnitř Linuxu)
			- Aplikace (např. Apache Webserver) si zažádá o data z paměti.
			- Jádro virtuálního Linuxu se podívá do své klasické tabulky stránek (přes svůj virtuální registr CR3).
			- Přeloží adresu programu (Virtual Address) na to, co sám považuje za fyzickou paměť – na **GPA (Guest Physical Address)**.
			- _Příklad z reálného života:_ Linux řekne: „Data jsou v mé budově na pokoji číslo 104.“ (Linux si myslí, že mu patří celá budova).
		2. Druhý krok: Srážka s realitou (Zásah EPT)
			- Procesor ví, že ten Linux žije ve virtuální kleci a jeho „pokoj 104“ ve skutečnosti na základní desce vůbec neexistuje.
			- V ten moment procesor (jeho hardwarová jednotka MMU) vezme tu adresu GPA a prožene ji skrz **druhou, hardwarovou tabulku = EPT**.
			- V EPT tabulce má hypervisor předem zapsáno, kam ve skutečných čipech RAM paměť tohoto konkrétního virtuálu reálně usadil.
			- _Příklad z reálného života:_ EPT tabulka zafunguje jako vrátnice na recepci, která ví, že celý tenhle Linux byl přestěhován do hotelu Hilton. Vezme požadavek na „pokoj 104“ a bleskově ho přepočítá na skutečnou adresu: „Hotel Hilton, 4. patro, pokoj 412“ – což je **HPA (Host Physical Address)**.
### Virtualizace a I/O
- VT-D
	1. Co je VT-d (Intel Virtualization Technology for Directed I/O)
		- Hardwarová technologie zabudovaná **na základní desce a v čipsetu** (obecný název je **IOMMU**, u AMD jako _AMD-Vi_)
		- Slouží k virtualizaci vstupů a výstupů (I/O) – umožňuje vzít reálný hardware (grafiku, disk, síťovku) a poslat ho přímo do virtuálního stroje (tzv. **PCI Passthrough**)
	2. Problém bez VT-d (Riziko přímého přístupu)
		- Periferie používají **DMA (Direct Memory Access)** = zapisují data rovnou do RAM bez účasti procesoru
		- Periferie ale netuší, že v PC běží virtualizace, a znají jen reálné adresy
		- Kdyby virtuální OS (Debian) řekl síťovce: _„Zapiš data na mou adresu 100,“_ síťovka by bezhlavě přepsala adresu 100 ve skutečné RAM, kde může mít data hypervisor nebo jiný virtuál
		- **Následek bez VT-d:** Přímý přístup k hardwaru je zakázán. Všechna data musí složitě a pomalu emulovat/přepisovat softwarový kód hypervisoru (ztráta výkonu)
	3. Princip fungování s VT-d (Hardwarový policajt)
		- Čip VT-d (IOMMU) na základní desce se postaví jako filtr mezi PCIe sloty a paměť RAM
		1. **Povel:** Virtuální stroj zaúkoluje hardware (např. grafickou kartu): _„Zapiš data na adresu X.“_
		2. **Odchycení:** Hardware posílá data po základní desce do RAM. Čip VT-d tento požadavek hardwarově zachytí
		3. **Překlad:** VT-d se podívá do své interní tabulky (kterou mu připravil hypervisor) a adresu z virtuálu bleskově **přepíše na skutečnou, bezpečnou adresu v RAM**
		4. **Zápis:** Data propadnou do RAM plnou rychlostí, aniž by ohrozila zbytek systému
	4. Hlavní výhody a příklady pro komisi
		- **100% nativní výkon:** Periferie komunikuje s virtuálem napřímo, kód hypervisoru u toho spí a nebrzdí provoz
		- **GPU Passthrough:** Celá fyzická grafická karta (Nvidia/AMD) se daruje virtuálním Windows – ideální na plynulé hraní her nebo trénování umělé inteligence ve virtuálu
		- **Storage Passthrough:** Přímé mapování diskových řadičů (SATA/NVMe) do virtuálních fileserverů pro maximální rychlost čtení a zápisu
# 8. Překladače vyšších programovacích jazyků, struktura a činnost překladače. Lexikální, syntaktická a semantická analýza, její varianty (tj. rekurzivní sestup, shora dolů a zdola nahoru).
- **Základní typy překladačů:**
	- **Assembler**
		- Zpracovává jazyk symbolických adres a generuje skutečný strojový kód
	- **Compiler**
		- Zpracovává vysokoúrovňový jazyk
		- Generuje strojový kód, symbolický kód, nebo jiný jazyk (bytecode nebo něco podobného)
		- Rychlé vykonání programu
	- **Interpret**
		- Zpracovává vysokoúrovňový jazyk 
		- Místo generování rovnou vykonává pokyny
			- Vykonávání interpretovaného programu je řízeno jiným programem a běží v jeho prostoru
		- Často v interaktivním režimu
		- Snažší ladění, zvládá složitější instrukce
- **Celé zpracování programu**
	- ![[Pasted image 20260526200134.png]]
## Struktura a činnost překladače
- ![[Pasted image 20260526200005.png]]
#### Vícevrstvý překladač
- ![[Pasted image 20260526200228.png]]
### Vnitřní jazyky překladače
- Rychle zpracovatelné, jednoznačné, univerzální
- **Čtveřice**
	- Podobné jako instrukce CPU
	- Informace o operaci:
		- Operátor
		- Operand 1, operand 2
		- Výsledek
		- `+, a, b, pom1`
	- Snadné zpracování optimalizátorem (vždy vím kde jsou data)
	- Potřebuju paměť pro mezivýsledky
- **Trojice**
	- Místo dočasné proměnné reference na další trojici => vytváří stromovou strukturu
	- Informace o operaci:
		- Operátor
		- Operand 1, operand 2
		- `+, a, b`
	- Obtížnější optimalizace
## Lexikální analýza
- **Cíle:**
	- Převod proudu znaků (ACII, Unicode) na proud tokenů, se kterým pak může pracovat syntaktický analyzátor
- **Pojmy:**
	- **Lexém** = část vstupu, která je chápána jako samostatná jednotka a představuje terminální symbol jazyka (konkrétní řetězec znaků ve zdrojovém textu)
	- **Token** = nejmenší logická jednotka programu
		- Může mít další atributy (jméno identifikátoru, hodnota čísla)
	- Token vs Lexém příklad:
		- Token = KLÍČOVÉ_SLOVO
		- Lexém = int
- Využívá DKA (Deterministický Konečný Automat)
- **Princip:**
	- Všechny tokeny jsou popsány regulárními výrazy (DKA)
	- Pořadí těchto regulární výrazu určuje prioritu
	- DKA jsou spojeny do jednoho DKA
	- Jako token je vyhodnocen vždy ten nejdéle běžící automat
- Klasické DKA maj potíže s vnořováním (neumí počítat)
	- Můžeme vyřešit přidáním pomocných proměnných pro počítání
- **Překladová gramatika:**
	- $\text{PG} = \{ N,T \cup D, P, S\}$, kde:
		- $N$ – neterminální symboly
		- $T$ – vstupní terminální symboly
		- $D$ – výstupní terminální symboly
		- $P$ – přepisovací pravidle ve tvaru:
			- $A \rightarrow awB$
			- $A \rightarrow aw$
			- kde $a \in T$, $w \in D^*$
## Syntaktická analýza
- = proces, který kontroluje gramatickou správnost kódu a převádí proud tokenů do buď rovnou na kód nebo do AST
	- Jednoprůchodový překladač – generuje rovnou výstupní kód
	- Víceprůchodový překladač – nejdříve generuje AST se kterým dál pracuje
- **Formální definice gramatiky:**
	- $G = \{ N, T, P, S \}$
		- $N$ – konečná množina neterminálních symbolů
		- $T$ – konečná, neprázdná množina, kde $T \cap N = \emptyset$
		- $P$ – konečná množina produkčních pravidel
			- $(T \cup N)^* N (T \cup N)^* \rightarrow (T \cup N^*)$
		- $S$ – startovací symbol $S \in N$
	- $L(G)$ – jazyk generovaný gramatikou G
		- $L(G) = \{w \in T^* \vert S \Rightarrow^* w \}$
- **Základní pojmy:**
	- **Levá derivace** = expanduje neterminál nejvíce vlevo
	- **Pravá derivace** = expanduje neterminál nejvíce vpravo
	- **Větná forma** = řetězec $\alpha$ se označuje jako větná forma pokud $S \Rightarrow^* \alpha, \alpha \in (N \cup T^*)$
	- **Věta/slovo** = řetězec $\alpha$ se označuje jako věta, pokud $S \Rightarrow^* \alpha, \alpha \in T^*$
	- **Fráze** = řetězec $\lambda = \alpha \beta \gamma$ je větnou formou, pak je podřetězec $\beta$ frází větné formy pokud $S \Rightarrow^* \alpha A \gamma$ a $A \Rightarrow^* \beta$
		- **Jednoduchá fráze** = fráze kde $A \rightarrow \beta$
	- **L-fráze** = nejlevější jednoduchá fráze
- **Víceznačnost gramatiky**
	- Slovo $s$ je víceznačné, pokud v gramatice $G$ existují alespoň 2 různé derivační stromy k jeho odvození
	- **Nutná podmínka:**
		- Pro žádný neterminální symbol neexistuje jak pravo- tak levorekurzivní pravidlo (podmínka nutná ne postačující)
	- Může (a nemusí) existovat ekvivalentní jednoznačná gramatika
		- Pokud ji dokážu najít vím, že existuje, ale je obtížné dokázat, že neexistuje
	- **Způsoby eliminace:**
		- Seskupování operátorů podle priorit
		- Nastavení směru rekurze podle asociativity operátorů
		- Odstranění obousměrné rekurze doplněním dalších symbolů
### Bezkontextová gramatika
- $\text{BKG} = \{ N,T, P, S\}$, kde:
	- $N$ – neterminální symboly
	- $T$ – vstupní terminální symboly
	- $S$ – startovací symbol $S \in N$
	- $P$ – přepisovací pravidle ve tvaru:
		- $A \rightarrow \alpha$, kde $A \in N, \alpha \in (N \cup T)^*$
### Zásobníkový automat
- Abstraktní model výpočetního stroje
	- Jednocestný (= nevrací se při čtení vstupu)
	- Nedeterministický (= může potřebovat backtracking)
	- S nekonečně velkým zásobníkem
- ![[Pasted image 20260527110003.png]]
- Definice $\text{PDA} = \{ Q, \Sigma, \Gamma, \delta, q_0, z_0, F \}$
	- $Q$ – konečná mn. stavů
	- $\Sigma$ – konečná vstupní abeceda (T příslušné BKG)
	- $\Gamma$ – konečná abeceda zásobníkových symbolů (může být $T \cup N$ a větší)
	- $\delta$ – zobrazení definující chování, $\delta: Q \times (\Sigma \cup \{\epsilon \}) \times \Gamma \rightarrow Q \times \Gamma^*$
	- $q_0 \in Q$ – počáteční stav
	- $z_0 \in \Gamma$ – dno zásobníku
	- $F \subset Q$ – mn. koncových stavů
	- **Konfigurace automatu:**
		- $(q,w,\alpha) \in Q \times \Sigma^* \times \Gamma^*$
	- **Přechod $\vdash$:**
		- $(q,aw, \alpha \beta ) \vdash (p,q, \gamma \beta )$
	- Akceptační automat
- Pro každou BKG lze sestrojit nedeterministický zásobníkový automat
### Analýza shora dolů
- Pro gramatiku $G = \{ N,T,S,P \}$ je možné sestrojit zásobníkový automat $\text{PDA} = \{ \{ q \}, T, N \cup T \cup \{ \# \}, \delta, S, \emptyset \}$
	- **2 operace:**
		- **Expanze**
			- $\delta(q, \text{cokoliv}, A) = \{ (q,A): A \rightarrow \alpha \in P \}, \forall A \in N$
		- **Redukce**
			- $\delta(q, a, a) = \{ (q, \epsilon) \}, \forall a \in T$
- **LL(k) analyzátor**
	- Podmnožina BKG umožňující deterministickou analýzu (konstrukci deterministického zásobníkového automatu)
	- **L**eft to right
	- **L**eftmost derivation
	- Analýza v O(n)
	- Pokud pro gramatiku dokážu sestavit LL(k) analyzátor, generuje LL(k) jazyk
#### Greinbachové normální forma
- Gramatika s pravidly ve formě:
	- $X \rightarrow aY_1 \dots Y_n, n > 0, Y_1 \dots Y_n \in (N - \{ S \}) \cup \{ \epsilon \}$
	- $S \rightarrow \epsilon$
	- A každá pravá strana pro $X$ začíná jiným symbolem $a$
- Každý bezkontextový jazyk má takovou gramatiku
- Lze pro ní vždy sestavit LL analyzátor
#### Příklad
- ![[Pasted image 20260527154309.png]]
- ![[Pasted image 20260527154321.png]]
- ![[Pasted image 20260603085224.png]]
#### Funkce FIRST()
- Detekce čím vším může začínat daná větná forma
- **Vstup:** libovolný řetězec, pro který se analýza provádí + gramatika
- **Výstup:** množina $N$, které mohou být na začátku větné formy
- **Algoritmus:**
	1. Konstruujeme mn. $F$
		- $F = \{ .X_1 X_2 \dots X_n \}$
		1. Pokud je prvek za tečkou $X_i \in N$, přidáme do $F$ všechny pravidla, kde $X_i$ je na levé straně a tečku dáme před pravou stranu
		2. Pokud je v $F$ prvek s tečkou na konci pravidla ($B \rightarrow \gamma .$), pak do $F$ vložíme nové položky tak, že posuneme všechny tečky za B
	2. Mn. FIRST($\beta$) získáme jako všechny terminální symbole z $F$ bezprostředně za tečkou, pokud je tečka na konci řetězce, přidáme i prázdný symbol
#### Funkce FOLLOW()
- Detekuje co všechno se může objevit za daným symbolem
- **Vstup:** jeden symbol pro který se analýza provádí + gramatika
- **Výstup:** množina terminálních symbolů, které za ním mohou následovat v libovolné větné formě
- **Algoritmus:**
	1. Vytvoříme mn. všech $N$, které se mohou přepsat na $\epsilon$ $N_e = \{ B: B \rightarrow^* \epsilon, B \in N \}$
	2. Konstruujeme mn. $F$
		1. Startovací pravidlo $F = \{ A \rightarrow A. \}$
		2. Pokud je v mn. $F$ položka s tečkou na konci pravidla ($B \rightarrow \gamma.$) předáme do $F$ všechny pravidla z P, kde je $B$ na pravé straně a tečku umístíme za $B$
		3. Pokud je v $F$ prvek, kde je za tečkou symbol z $N_e$ přidáme do $F$ další položku, kterou vytvoříme z této položky posunem tečky o jedno doprava
		4. Pokud je v $F$ prvek, kde je za tečkou $B \in N$, přidáme do $F$ všechna pravidla z $P$, kde je $B$ na levé straně a tečku dáme před jejich pravé strany
	3. Množinu FOLLOW(A) získáme z $F$ tak, že do ní vložíme terminální symboly z $F$ bezprostředně za tečkou, pokued je v $F$ tečka na konci pravidla kde je na levé straně symbol $S$ přidáme do FOLLOW(A) i $\epsilon$
#### Obecná LL(1) gramatika
- BKG, nemá levou rekurzi
- A navíc platí:
	- $\text{FIRST}(\alpha) \cap \text{FIRST}(\beta) = \emptyset, \forall X \rightarrow \alpha, X \rightarrow \beta$
	- pokud:
		- $\alpha \rightarrow^* \epsilon$, pak $\text{FOLLOW}(A) \cap \text{FIRST}(\beta) = \emptyset$
		- $\beta \rightarrow^* \epsilon$, pak $\text{FIRST}(\alpha) \cap \text{FOLLOW}(\beta) = \emptyset$
	- Tzn.:
		- Neexistuje first-first kolize ani first-follow kolize
- Nebo:
	- $\text{FIRST}(\alpha \text{FOLLOW}(A)) \cap \text{FIRST}(\beta \text{FOLLOW}(A)) = \emptyset$ pro $A \rightarrow \alpha$ a $A \rightarrow \beta$ a $\alpha \neq \beta$
#### First-First kolize
- First dvou pravých stran jednoho pravidla nemá prázdný průnik
- **Odstranění:** levá faktorizace
	- Kolizní pravidlo ve tvaru: $A \rightarrow \alpha \alpha_1 | \alpha \alpha_2 | \dots | \alpha \alpha_n$
	- Přepíšeme:
		- $A \rightarrow \alpha A'$
		- $A' \rightarrow \alpha_1 | \dots | \alpha_n$
#### First-Follow kolize
- First pravidla, které začíná terminálem, který se může přepsat na $\epsilon$ je stejné jako Follow
- **Odstranění:** pohlcení terminálu
	- Kolizní pravidla ve tvaru:
		- $A \rightarrow \alpha B a \beta$
		- $B \rightarrow \gamma_1 | \dots | \gamma_n$, $\gamma_1 \rightarrow^* \epsilon$, $a \in \text{FIRST}(\gamma_2), a \in \text{FOLLOW}(B)$
	- Přepíšeme:
		- $A \rightarrow \alpha [Ba] \beta$
		- $[Ba] \rightarrow \gamma_1 a | \dots | \gamma_n a$
- **Nebo odstranění:** odstranění $\epsilon$ pravidel
#### Silná vs. Obecná LL(k) analýza
- **Silná** – pro rozhodování jí stačí pouze zásobník a vstup
- **Obecná** – pro rozhodnutí potřebuje všechny načtené symboly + vrchol zásobníku + symbol ze vstupu
### Analýza zdola nahoru
- Strom je konstruován od listů
- **Povolené operaca automatu:**
	- **Přesun (shift)**
		- Neterminál ze vstupu je přesunut do zásobníku a přeložen do abecedy $\Gamma$
	- **Redukce (reduce)**
		- Symboly na zásobníku tvořící pravou stranu jsou nahrazeny levou stranou
- **L**eft to right
- **R**ight most derivation
#### Tvorba LR(0) položek
- ![[Pasted image 20260527184500.png]]
- Položky $M_i$ lze chápat jak uzly grafu
- ![[Pasted image 20260527184741.png]]
- **Tabulka akcí:**
	- Vyplnění:
		1. Pokud je v množině M (v rámečku v grafu) položka ve tvaru $A \rightarrow \alpha.$ pak bud akcí redukce
		2. Pokud je v množině položek $S' \rightarrow S.$ pak bude akcí akceptace slova
		3. V ostatních případech je akcí přesun
	- ![[Pasted image 20260527184835.png]]
- **Tabulka přechodů:**
	- ![[Pasted image 20260527184859.png]]
- Pokud tabulku jde vyplnit jedná se o LR(0) gramatiku
#### SLR(k) gramatiky
- Simple LR(k)
- Tabulku z LR(0) položek nejde vyplnit
	- **Důvody:**
		- Reduce-reduce kolize = chci redukovat podle dvou různých pravidel
		- Shift-reduce kolize = nevím jestli mám redukovat ne přesouvat
- Stejná konstrukce grafu LR položek
- **Tabulka přechodů:**
	- ![[Pasted image 20260527194245.png]]
	- Vyplnění:
		1. Pokud je v položce $M_i$ pravidlo, kde je tečka před terminálem tak pro znak se tečkou se dělá shift
		2. Pokud je v položce $M_i$ tečka na konci pravidla tak počítám FOLLOW pro levou stranu pravidla a pro výslednou množinu FOLLOW v tabulce aplikuju reduce
		3. Pokud je v množině položek $S' \rightarrow S.$ pak bude akcí akceptace slova
#### LALR(k) gramatiky
- Look Ahead LR(k)
- Např.: yacc, bison
- Řeší případy kdy u položky v LR grafu nastane, že FOLLOW pravidla je stejný jako terminál před, kterým je tečka a tudíž pořád nevíme kdy použít shift nebo reduce
- **Výpočet Look Ahead:**
	- ![[Pasted image 20260527202236.png]]
	- ![[Pasted image 20260527213301.png]]
## Sémantická analýza
- Ověřuje, že program má jasný smysl
- Ověřuje dodržení vlastností, které není možné nebo praktické kontrolovat v lexikální a syntaktické analýze
- **Základní vlastnosti:**
	- Odmítnout co nejvíce nesprávných programů
	- Přijmout co nejvíce platných programů
	- Shromáždění užitečných informací o programu
- **Způsoby implementace:**
	- **Atributované gramatiky**
		- Rozšíření gramatiky o sémantické vlastnosti spojené s každým pravidel (yacc/bison)
	- **Rekurzivní procházení AST**
		- Sestavím AST
		- Sémantická analýza prováděna při jeho procházení
		- Např.: ANTLR
### Atributovaná gramatika
- Gramatika doplněná o atributy
- $G = (N, \Sigma, P, S)$, kde
	- $N$ – konečná mn. neterminálů
	- $\Sigma$ – neprázdná konečná mn. terminálů
	- $P$ – konečná mn. produkčních pravidel
	- $S$ – $S \in N$ startovací symbol
- $A. a$ je syntetizovaný atribut pokud platí:
	- $A \rightarrow \alpha \in P$ (= existuje takové pravidlo)
	- $\alpha = \alpha_1 \dots \alpha_n, \forall, 1 \leq i \leq n: \alpha_i \in (N \cup \Sigma)$ (na pravé straně jsou jen terminály a neterminály)
	- $A. a = f(\alpha_{j1}.a_1, \dots, \alpha_{jm}.a_m)$ (hodnota atributu je určena funkcí $f$ požitou na některé hodnoty symbolů z těla pravidla)
- Např.:
	- ![[Pasted image 20260527220626.png]]
### Derivační strom a AST
- **Derivační strom** = reprezentace vstupu získaná parserem (řada nepodstatných uzlů)
- **AST** = reprezentace programu (jen důležité věci pro vykonání programu)
### Vyhodnocení atributů
- Lze provádět během lexikální a syntaktické analýzy (jednoprůchodový překladač)
- Lze provést dodatečně pomocí AST
- Obecně:
	- Při cestě dolů od kořene k listům => **výpočet dědičných atributů**
	- Při cestě nahoru od listů ke kořeni => **výpočet syntetizovaných atributů**
### Syntetizované atributy
- ![[Pasted image 20260527221000.png]]
### Dědičné atributy
- ![[Pasted image 20260527221526.png]]
### Statický vs. Dynamický rozsah
- **Statický rozsah** = viditelnost při překladu
- **Dynamický rozsah** = viditelnost při běhu
- Př.:
```
promenna x = 10;

funkce B() {
    tiskni(x);
}

funkce A() {
    promenna x = 20;
    B();
}

A();
```
- Ve statickém rozsahu vytiskne funkce B() 10
- V dynamickém 20
### Tabulka symbolů
- Tabulka symbolů mapuje jména na deskriptor
- Vytváří a udržuje se během sémantické analýzy
- V deskriptoru typ (proměnná, metoda, třída, struktura)
- **Operace:**
	- Vlož rozsah
	- Odstraň rozsah
	- Vlož symbol
	- Najdi symbol
	- Najdi rozsah
- **Možné implementace:**
	- Zásobník/strom
		- Hash tabulka v každém bloku
- **Využítí:**
	- Zpracování identifikátorů
	- Debugging
	- U interpretovaných jazyků je k dispozici za běhu
### Typová kontrola
- Typ – nemá obecnou definici
- **Typové systémy:**
	- **Silné** = nikdy nedovolí typovou chybu – kontrola při překladu (Java, Python)
	- **Slabé** = za běhu může dojít k typové chybě (C, C++)
- **Druhy typové kontroly:**
	- **Statická** = analýza v době překladu
		- Vývoj stabilnějších a robustnějších programů
		- U většiny překládaných jazyků
	- **Dynamická** = analýza za běhu
		- Přesnější než statická kontrola
		- Většina interpretovaných jazyků
	- **Žádná**
- **Odvozování typů**
	- Explicitní deklarace
	- Implicitní (odvozeno z výrazu)
		- Odvození probíhá nad AST
		- Formálně se používají inferenční pravidla
- **Omezení statického typového systému:**
	- Vždy bude neúplný
		- Odmítne program, který by mohl fungovat bez problému
	- **Znělý (sound) typový systém**
		- = záruka, že žádný program schválený typovou kontrolou nezpůsobí chybu za běhu
# 9. Formální prostředky pro popis vyšších programovacích jazyků – gramatiky a jejich členění, vlastnosti gramatik, způsoby zápisu gramatik a nástroje pro jejich zpracování, využití gramatiky k tvorbě překladače.
## Definice gramatiky
- $G = (N, T, S, P)$
	- $N$ – konečná mn. neterminálů
	- $T$ – neprázdná konečná mn. terminálů
	- $S$ – $S \in N$ – startovací symbol
	- $P$ – produkční pravidla
		- $(T \cup N)^*N(T \cup N)^* \rightarrow (T \cup N)^*$
## Definice jazyka
- $L(G) = \{ w \in T^* | S \overset{*}{\implies} w \}$
## Členění gramatik
- Dělí se podle typů produkčních pravidel
- $a$, $b$ – terminály
- $A$, $B$ – neterminály
- $\alpha$, $\beta$ – řetězec terminálů a neterminálů ($\in (N \cup T \cup \epsilon)^*$)
- $\gamma$ – neprázdný řetězec terminlů a neterminálů ($\in (N \cup T )^*$)
- **Typ 0 – rekurzivně spočetné**
	- $\gamma \rightarrow \alpha$
- **Typ 1 – kontextové**
	- $\alpha A \beta \rightarrow \alpha \gamma \beta$
- **Typ 2 – bezkontextové**
	- $A \rightarrow \alpha$
- **Typ 3 – regulární**
	- $A \rightarrow a$
	- $A \rightarrow aB$
## Způsoby zápisu gramatik
### Backus-Naurova forma
- Metoda zápisu pro BKG
- Původní podoba:
	- <neterminál> ::= <neterminál> | <neterminál> "A" | "terminál"
- Yacc, ANTLR
	- neterminál : neterminál | 'terminál' neterminál
- Rozšířená BNF
	- neterminál: {neterminál $0 \dots \infty$} | \[neterminál jednou nebo vůbec]
### Regulární výrazy
- Metoda zápisu regulárních gramatik
## Regulární gramatiky
- **Pravidla ve formě:**
	- Levá:
		- $A \rightarrow a$
		- $A \rightarrow Ba$
		- $A \rightarrow \epsilon$
	- Pravá:
		- $A \rightarrow a$
		- $A \rightarrow aB$
		- $A \rightarrow \epsilon$
- Lze přímočaře chápat jako popis NKA
- Každý NKA lze převést na DKA
### Deterministický Konečný Automat
- $\text{DKA} = \{ Q, T, \delta, q_0, F \}$
	- $Q$ – mn. všech stavů
	- $T$ – mn. terminálů (vstupních symbolů)
	- $\delta$ – přechodová funkce
	- $q_0$ – počáteční stav ($q_0 \in Q$)
	- $F$ – konečné stavy $F \subset Q$
## Bezkontextové gramatiky
- $\text{BKG} = \{ N,T, P, S\}$, kde:
	- $N$ – neterminální symboly
	- $T$ – vstupní terminální symboly
	- $S$ – startovací symbol $S \in N$
	- $P$ – přepisovací pravidle ve tvaru:
		- $A \rightarrow \alpha$, kde $A \in N, \alpha \in (N \cup T)^*$
### Zásobníkový automat
- Abstraktní model výpočetního stroje
	- Jednocestný (= nevrací se při čtení vstupu)
	- Nedeterministický (= může potřebovat backtracking)
	- S nekonečně velkým zásobníkem
- ![[Pasted image 20260527110003.png]]
- Definice $\text{PDA} = \{ Q, \Sigma, \Gamma, \delta, q_0, z_0, F \}$
	- $Q$ – konečná mn. stavů
	- $\Sigma$ – konečná vstupní abeceda (T příslušné BKG)
	- $\Gamma$ – konečná abeceda zásobníkových symbolů (může být $T \cup N$ a větší)
	- $\delta$ – zobrazení definující chování, $\delta: Q \times (\Sigma \cup \{\epsilon \}) \times \Gamma \rightarrow Q \times \Gamma^*$
	- $q_0 \in Q$ – počáteční stav
	- $z_0 \in \Gamma$ – dno zásobníku
	- $F \subset Q$ – mn. koncových stavů
	- **Konfigurace automatu:**
		- $(q,w,\alpha) \in Q \times \Sigma^* \times \Gamma^*$
	- **Přechod $\vdash$:**
		- $(q,aw, \alpha \beta ) \vdash (p,q, \gamma \beta )$
	- Akceptační automat
- Pro každou BKG lze sestrojit nedeterministický zásobníkový automat
### Analýza shora dolů
- Pro gramatiku $G = \{ N,T,S,P \}$ je možné sestrojit zásobníkový automat $\text{PDA} = \{ \{ q \}, T, N \cup T \cup \{ \# \}, \delta, S, \emptyset \}$
	- **2 operace:**
		- **Expanze**
			- $\delta(q, \text{cokoliv}, A) = \{ (q,A): A \rightarrow \alpha \in P \}, \forall A \in N$
		- **Redukce**
			- $\delta(q, a, a) = \{ (q, \epsilon) \}, \forall a \in T$
- **LL(k) analyzátor**
	- Podmnožina BKG umožňující deterministickou analýzu (konstrukci deterministického zásobníkového automatu)
	- **L**eft to right
	- **L**eftmost derivation
	- Analýza v O(n)
	- Pokud pro gramatiku dokážu sestavit LL(k) analyzátor, generuje LL(k) jazyk
#### Greinbachové normální forma
- Gramatika s pravidly ve formě:
	- $X \rightarrow aY_1 \dots Y_n, n > 0, Y_1 \dots Y_n \in (N - \{ S \}) \cup \{ \epsilon \}$
	- $S \rightarrow \epsilon$
	- A každá pravá strana pro $X$ začíná jiným symbolem $a$
- Každý bezkontextový jazyk má takovou gramatiku
- Lze pro ní vždy sestavit LL analyzátor
#### Příklad
- ![[Pasted image 20260527154309.png]]
- ![[Pasted image 20260527154321.png]]
#### Funkce FIRST()
- Detekce čím vším může začínat daná větná forma
- **Vstup:** libovolný řetězec, pro který se analýza provádí + gramatika
- **Výstup:** množina $T$, které mohou být na začátku větné formy
- **Algoritmus:**
	1. Konstruujeme mn. $F$
		- $F = \{ .X_1 X_2 \dots X_n \}$
		1. Pokud je prvek za tečkou $X_i \in N$, přidáme do $F$ všechny pravidla, kde $X_i$ je na levé straně a tečku dáme před pravou stranu
		2. Pokud je v $F$ prvek s tečkou na konci pravidla ($B \rightarrow \gamma .$), pak do $F$ vložíme nové položky tak, že posuneme všechny tečky za B
	2. Mn. FIRST($\beta$) získáme jako všechny terminální symbole z $F$ bezprostředně za tečkou, pokud je tečka na konci řetězce, přidáme i prázdný symbol
#### Funkce FOLLOW()
- Detekuje co všechno se může objevit za daným symbolem
- **Vstup:** jeden symbol pro který se analýza provádí + gramatika
- **Výstup:** množina terminálních symbolů, které za ním mohou následovat v libovolné větné formě
- **Algoritmus:**
	1. Vytvoříme mn. všech $N$, které se mohou přepsat na $\epsilon$ $N_e = \{ B: B \rightarrow^* \epsilon, B \in N \}$
	2. Konstruujeme mn. $F$
		1. Startovací pravidlo $F = \{ A \rightarrow A. \}$
		2. Pokud je v mn. $F$ položka s tečkou na konci pravidla ($B \rightarrow \gamma.$) předáme do $F$ všechny pravidla z P, kde je $B$ na pravé straně a tečku umístíme za $B$
		3. Pokud je v $F$ prvek, kde je za tečkou symbol z $N_e$ přidáme do $F$ další položku, kterou vytvoříme z této položky posunem tečky o jedno doprava
		4. Pokud je v $F$ prvek, kde je za tečkou $B \in N$, přidáme do $F$ všechna pravidla z $P$, kde je $B$ na levé straně a tečku dáme před jejich pravé strany
	3. Množinu FOLLOW(A) získáme z $F$ tak, že do ní vložíme terminální symboly z $F$ bezprostředně za tečkou, pokued je v $F$ tečka na konci pravidla kde je na levé straně symbol $S$ přidáme do FOLLOW(A) i $\epsilon$
#### Obecná LL(1) gramatika
- BKG, nemá levou rekurzi
- A navíc platí:
	- $\text{FIRST}(\alpha) \cap \text{FIRST}(\beta) = \emptyset, \forall X \rightarrow \alpha, X \rightarrow \beta$
	- pokud:
		- $\alpha \rightarrow^* \epsilon$, pak $\text{FOLLOW}(A) \cap \text{FIRST}(\beta) = \emptyset$
		- $\beta \rightarrow^* \epsilon$, pak $\text{FIRST}(\alpha) \cap \text{FOLLOW}(\beta) = \emptyset$
	- Tzn.:
		- Neexistuje first-first kolize ani first-follow kolize
- Nebo:
	- $\text{FIRST}(\alpha \text{FOLLOW}(A)) \cap \text{FIRST}(\beta \text{FOLLOW}(A)) = \emptyset$ pro $A \rightarrow \alpha$ a $A \rightarrow \beta$ a $\alpha \neq \beta$
#### First-First kolize
- First dvou pravých stran jednoho pravidla nemá prázdný průnik
- **Odstranění:** levá faktorizace
	- Kolizní pravidlo ve tvaru: $A \rightarrow \alpha \alpha_1 | \alpha \alpha_2 | \dots | \alpha \alpha_n$
	- Přepíšeme:
		- $A \rightarrow \alpha A'$
		- $A' \rightarrow \alpha_1 | \dots | \alpha_n$
#### First-Follow kolize
- First pravidla, které začíná terminálem, který se může přepsat na $\epsilon$ je stejné jako Follow
- **Odstranění:** pohlcení terminálu
	- Kolizní pravidla ve tvaru:
		- $A \rightarrow \alpha B a \beta$
		- $B \rightarrow \gamma_1 | \dots | \gamma_n$, $\gamma_1 \rightarrow^* \epsilon$, $a \in \text{FIRST}(\gamma_2), a \in \text{FOLLOW}(B)$
	- Přepíšeme:
		- $A \rightarrow \alpha [Ba] \beta$
		- $[Ba] \rightarrow \gamma_1 a | \dots | \gamma_n a$
- **Nebo odstranění:** odstranění $\epsilon$ pravidel
#### Silná vs. Obecná LL(k) analýza
- **Silná** – pro rozhodování jí stačí pouze zásobník a vstup
- **Obecná** – pro rozhodnutí potřebuje všechny načtené symboly + vrchol zásobníku + symbol ze vstupu
### Analýza zdola nahoru
- Strom je konstruován od listů
- **Povolené operaca automatu:**
	- **Přesun (shift)**
		- Neterminál ze vstupu je přesunut do zásobníku a přeložen do abecedy $\Gamma$
	- **Redukce (reduce)**
		- Symboly na zásobníku tvořící pravou stranu jsou nahrazeny levou stranou
- **L**eft to right
- **R**ight most derivation
#### Tvorba LR(0) položek
- ![[Pasted image 20260527184500.png]]
- Položky $M_i$ lze chápat jak uzly grafu
- ![[Pasted image 20260527184741.png]]
- **Tabulka akcí:**
	- Vyplnění:
		1. Pokud je v množině M (v rámečku v grafu) položka ve tvaru $A \rightarrow \alpha.$ pak bud akcí redukce
		2. Pokud je v množině položek $S' \rightarrow S.$ pak bude akcí akceptace slova
		3. V ostatních případech je akcí přesun
	- ![[Pasted image 20260527184835.png]]
- **Tabulka přechodů:**
	- ![[Pasted image 20260527184859.png]]
- Pokud tabulku jde vyplnit jedná se o LR(0) gramatiku
- **Příklad:**
	- ![[Pasted image 20260603143828.png]]
	- ![[Pasted image 20260603143834.png]]
#### SLR(k) gramatiky
- Simple LR(k)
- Tabulku z LR(0) položek nejde vyplnit
	- **Důvody:**
		- Reduce-reduce kolize = chci redukovat podle dvou různých pravidel
		- Shift-reduce kolize = nevím jestli mám redukovat ne přesouvat
- Stejná konstrukce grafu LR položek
- **Tabulka přechodů:**
	- ![[Pasted image 20260527194245.png]]
	- Vyplnění:
		1. Pokud je v položce $M_i$ pravidlo, kde je tečka před terminálem tak pro znak se tečkou se dělá shift
		2. Pokud je v položce $M_i$ tečka na konci pravidla tak počítám FOLLOW pro levou stranu pravidla a pro výslednou množinu FOLLOW v tabulce aplikuju reduce
		3. Pokud je v množině položek $S' \rightarrow S.$ pak bude akcí akceptace slova
#### LALR(k) gramatiky
- Look Ahead LR(k)
- Např.: yacc, bison
- Řeší případy kdy u položky v LR grafu nastane, že FOLLOW pravidla je stejný jako terminál před, kterým je tečka a tudíž pořád nevíme kdy použít shift nebo reduce
- **Výpočet Look Ahead:**
	- ![[Pasted image 20260527202236.png]]
	- ![[Pasted image 20260527213301.png]]
- ![[Pasted image 20260609184115.png]]
## Využití gramatiky při tvorbě překladače
- Regulární gramatiku využíváme při lexikální analýze
- BKG využíváme při syntaktické analýze
# 10. Způsob překladu různých programových konstrukcí vyšších jazyků, překlad příkazů, zpracování deklarací, práce s objekty, volání podprogramů. Přidělování paměti. Interpretační zpracování.
## Způsob překladu různých programových konstrukcí vyšších jazyků, překlad příkazů, zpracování deklarací, práce s objekty, volání podprogramů.
### Způsob překladu různých programových konstrukcí vyšších jazyků
- Vstupem je AST
- Z AST je typicky vytvářen **mezijazyk** (trojice, čtveřice)
- Generování mezijazyka, je obvykle jednodušší než generování instrukcí CPU
- **Generování instrukcí:**
	- Na většině platforem lze přímočaře simulovat zásobníkový automat
		- 1 registr (nebo paměť) jako akumulátor
		- 1 registr (nebo paměť) jako ukazatel na vrchol zásobníku (SP)
		- 1 registr (nebo paměť) jako báze zásobníku
		- Zásobník udržovaný v paměti
	- Potřebuji mít přehled o cílové platformě
		- Jaké instrukce jsou k dispozici
		- Jaké zdroje jsou k dispozici
		- Jaké knihovny jsou k dispozici
		- Jaké datové typy jsou k dispozici
- **Generování kódu obecně:**
	- Podobná strategie jako rekurzivní sestup
		- Pro každý fragment generuji kód, který:
			- Má výsledek uložený na definovaném místě
			- Uklidí po sobě všechny nežádoucí vedlejší efekty
			- Zanechá po sobě potřebná data
		- Snadné pro aritmetiku
		- Složitější pro řídící konstrukce
### Překlad příkazů
- **Zpracování konstant** (konstanty v kódu, ne neměnitelné proměnné)
	- Vložení konstanty do pracovního prostředí (registr, vrchol zásobníku)
- **Zpracování aritmetiky**
	- Pro jeden uzel AST => jednu aritmetickou/logickou operaci
	- Postup:
		- Získat data pro práci
		- Provedení operace
		- Výsledek v pracovním prostředí
- **Zpracování podmínek**
	- Instrukce pro řízení toku programu
		- Podmíněný skok
		- Nepodmíněný skok
		- Návěstí/adresa
### Zpracování deklarací
- Nepotřebuje explicitní kód
- Př.: `int cislo;`
- Potřebuje přidělení paměti
	- Záznam v tabulce symbolů
	- Nejsnazší strategie:
		- Seřadit (podle pořadí ve zdrojovém kódu)
		- Naskládat za sebe z AZ
	- Alokace inkrementací ukazatele
### Práce s objekty
- Mají navíc polymorfní chování
	- V době překladu nejsou známy adresy skoku na volané metody
		- "obyčejné" metody – adresa skoku je určena za překladu
		- virtuální metody – adresa skoku je určena za běhu
- **Class Instance Record (CIR)**
	- ![[Pasted image 20260529114030.png]]
	- Atributy mají pevnou pozici vůči bázi záznamu
		- Potomci jen přidávají atributy na konec
	- Označení třídy jako číslo
	- Odkaz na tabulku skoků
	- Uloženo v dynamické paměti
- **Tabulka skoků:**
	- V době překladu obtížné rozhodnout jaké volání se provede
		- Ne vždy je možné zjistit na co ukazuje zadaná reference
			- => překladač nemůže skoky vyhodnotit přímo
			- => je nutné generovat instrukce pro hledání metody v tabulce skoků
	- Jedna pro každou třídu
	- ![[Pasted image 20260603143906.png]]
### Volání podprogramů
- Volání podprogramu je skok
	- Musíme najít polohu podprogramu v kódu – lze staticky
- Návrat z podprogramu je skok
	- Musíme se pamatovat kam se vrátit – nelze staticky (záleží na místě volání) => uloženo v zásobníku (dynamický ukazatel)
- Návratová hodnota
	- Po skončení funkce je výsledek v pracovním prostředí (vrchol zásobníku/akumulátor)
- Spravování zásobníku
	- Uložení řídících dat
	- Uložení parametrů
- **Aktivační záznam:**
	- Ukazatel na vrchol zásobníku (SP)
	- Ukazatel na bázi zásobníku
		- Umožňuje práci s relativními lokálními adresami
	- Ukazatel na bázi nadřazeného zásobníku – **statický ukazatel**
	- Ukazatel na bázi volajícího zásobníků – **dynamický ukazatel**
- ![[Pasted image 20260529105300.png]]
## Přidělování paměti 
- Práce s pamětí závisí na tom kde je program vykonáván
	- Typ architektury
	- Dostupné paměti
	- Jak mohu paměť alokovat
- Typicky mohu mít:
	- Oblast pro program
	- Oblast statických dat
	- Zásobník
	- Halda
- **Struktura paměti v C**
	- ![[Pasted image 20260529120738.png]]
- **Druhy přidělování paměti:**
	- **Statické**
		- Místo v paměti určeno při překladu
		- Statická oblast paměti
		- Zásobník
	- **Dynamické**
		- Místo v paměti určeno za běhu
		- Může být v zásobníku (jednodušší) nebo na haldě (složitější)
		- Potřebuji instrukce pro čtení z paměti
- **Správa zásobníku**
	- Ukazatel na vrchol (SP)
	- Ukazatel na bázi
	- Statický ukazatel
	- Dynamické ukazatel
- **Předávání parametrů**
	- **Hodnotou**
		- C, C++, Java pro primitivní typy
		- Vytvoření lokální proměnné se zadanou hodnotou
	- **Odkazem**
		- C++ pro pointery, Java pro objektové typy
		- Předá se adresa skutečného parametru
		- Všechny operace přímo nad předanou pamětí
	- **Výsledkem**
		- Vytvoření lokální proměnné se zadanou hodnotou
		- Před ukončením podprogramu hodnota zkopírována do zdrojové proměnné
- **Předávání podprogramů**
	- Parametr je další program
	- Nutno předat:
		- Adresa odkud se bude předaný program vykonávat
		- Platné prostředí
	- **Vazby:**
		- ![[Pasted image 20260529122648.png]]
- **Překlad netriviálních datových typů**
	- Deskriptor obsahuje:
		- **Statické struktury** – vytvořeno při překladu, nepotřebuji za běhu
		- **Dynamické struktury** – lze vytvořit až za běhu
	- ![[Pasted image 20260529125150.png]]
- **Ukládání pole:**
	- **Po řádcích**
		- ![[Pasted image 20260529125244.png]]
	- **Po sloupcích:**
		- ![[Pasted image 20260529125443.png]]
	- **Kontrola mezí:**
		- **Pascal** – velikost pole daná při překladu konstantou (při každém přístupu kontroluju zda nepřekračuju meze)
			- Musíme říct od jakého do jakého indexu pole je
		- **Java** – velikost uloženo spolu s polem (při každém přístupu dělám kontrolu proti mezím načtených z paměti)
		- **C** – bez kontroly
- **Ukládání struktur**
	- Několik položek různých typů seskupených dohromady
	- ![[Pasted image 20260529130024.png]]
- **Zásobník a paralelismus**
	- Každé vlákno potřebuje vlastní zásobník
	- **Základní modely:**
		- "Spaghetti stack" – zobecněný stromově se větvící zásobník
		- Zcela oddělené větvící se zásobníky (Java)
- **Ukládání objektových struktur**
	- Jako struktury ale navíc:
		- Dědičnost
		- Volání metod
	- 2 deskriptory:
		- Deskriptor třídy v tabulce symbolů, vzniká při překladu
			- Ukazatel na deskriptor rodiče
			- Seznam datových položek
			- Seznam metod
		- Deskriptor instance
			- Odkaz na deskriptor třídy
	- **Překrývání atributů:**
		- Volba atributu může záviset na type reference (statický pohled) nebo na typu CIR
#### Alokace dynamické paměti
- Z pohledu překladače knihovna nebo volání OS
	- V C `malloc()`, `calloc()`, `realloc()`, `free()`
	- V C++ `new`, `delete`
	- V Javě `new`
- **Typy podle správy paměti:**
	- Explicitní
	- Implicitní
- **Sledování přidělená paměti:**
	- ![[Pasted image 20260529153810.png]]
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
- **Hledání volného bloku:**
	- First-Fit
	- Next-Fit
	- Best-Fit
- **Fragmentace**
	- **Interní**
		- Bloky jsou alokované v určitých velikostech/násobcích (podle architektury CPU – na 64 bitové arch. je přirozený blok 64 bitů)
		- Skutečný obsah ale může být menší než alokovaný prostor
		- ![[Pasted image 20260529162457.png]]
	- **Externí**
		- Děje se kvůli průběžné alokaci a uvolňování bloků
		- ![[Pasted image 20260529162535.png]]
	- **Odstranění pomocí – slučování volných bloků**
		- **Jednoduché:**
			- Slučuji jenom s následujícím blokem
			- ![[Pasted image 20260529162721.png]]
		- **Donald Knuth (obousměrné):**
			- Záhlaví je na obouch koncích bloku => obousměrně zřetězený seznam
			- ![[Pasted image 20260529163050.png]]
#### Garbage Kolekce
- Hledáme nepotřebné objekty a automaticky uvolňujeme jimi drženou paměť
	- Doopravdy rozpoznat nepotřebné objekty nejde (zkouším pouze ty na které program vidí – reference)
- **Objekt je dostupný pokud:**
	- Ukazatel na objekt je v registru CPU
	- Ukazatel na objekt je v jiném dostupném objektu (typicky v zásobníku)
- **Obecný přístup:**
	- Správa paměti s GC musí:
		- Alokovat místo pro nové objekty
		- Pokud místo dochází => uvolňovat místo
- **Mark and Sweep**
	- Základní algoritmus
	- **Princip:**
		1. Fáze Mark
			- Vezmeme kořenové objekty a nastaví `mark = true`
			- Vezme všechny odkazované objekty a nastaví `mark = true`
			- Pokračuje dokud je co brát
		2. Fáze Sweep
			- Hledá v heapu všechny objekty s `mark = false`
			- Zařadí je do seznamu volných
			- Nastaví `mark = false` pro všechny přeživší
	- **Potíže:**
		- Potřebuje seznam dostupných objektů (zabírá další místo v paměti)
			- Řešení: udržovat seznam přímo v objektech
- **Stop and Copy**
	- Vychází z pozorování, že většinou objektů je v paměti krátkou dobu
	- **Princip:**
		- Paměť je rozdělena na 2 části:
			- Old space – místo kde se alokují objekty
			- New space – vyhrazení pro GC
		- Při GC najdu dostupné objekty v Old Space a přesunu je do New Space
			- Všechno ostatní je odpad => uvolním celý bývalý Old Space
			- Po skončení prohodím Old a New Space
		- ![[Pasted image 20260529172332.png]]
	- **Vlastnosti:**
		- Heap pointer ukazuje na začátek volného místa
		- Hledání dostupných objektů stejné jako v Mark and Sweep
		- Po kopírování je nutné aktualizovat všechny ukazatele
		- Defragmentuje paměť
		- Považován za nejrychlejší GC
	- **Javovská implementace:**
		- ![[Pasted image 20260529172545.png]]
## Interpretační zpracování
- Celý proces je stejný jako u překladače
- Rozdíl je pouze v závěrečné fázi
	- Překladač generuje kód – vytváří soubor s intrukcemi pro CPU
	- Interpret vykonává program rovnou