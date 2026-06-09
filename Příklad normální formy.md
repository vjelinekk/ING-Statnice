Pojďme postavit jeden parádní, komplexní příklad z reálného života, na kterém si projdeme celou očistnou cestu **od totálního databázového pekla až po čistý ráj ve 3. normální formě**.

Představ si, že navrhuješ systém pro firmu, která sleduje, **kteří zaměstnanci pracují na jakých projektech a v jakých odděleních**.

### Výchozí stav: Úplná katastrofa (Nenormalizovaná forma - UNF)

Nezkušený programátor vyplivl do databáze jednu obří, línou tabulku, kam nasypal úplně všechno:

|**EmpID**|**EmpName**|**Phones (Seznam)**|**ProjID**|**ProjName**|**Hours**|**DeptID**|**DeptName**|
|---|---|---|---|---|---|---|---|
|**101**|Pepa|777111, 777222|P1|Web e-shopu|20|D5|Vývoj|
|**101**|Pepa|777111, 777222|P2|Mobilní App|10|D5|Vývoj|
|**102**|Jana|606333|P1|Web e-shopu|30|D6|Marketing|

Tato tabulka trpí všemi představitelnými nemocemi: data se opakují (Pepa a Vývoj jsou tu dvakrát), telefony jsou v seznamu a celé se to nedá rozumně spravovat.

### Krok 1: Cesta k 1. normální formě (1NF)

**Pravidlo 1NF:** Žádné seznamy v buňkách (atomická data) a žádné opakující se sloupce.

- **Co musíme udělat:** Rozbít to nešťastné pole telefonů u Pepy. Každé telefonní číslo musí dostat svůj vlastní řádek
    
- **Určení primárního klíče:** Abychom v této nové tabulce jednoznačně identifikovali řádek, potřebujeme složený primární klíč: **(EmpID, ProjID, Phone)**
    

**Výsledná tabulka v 1NF:**

| **EmpID (PK)** | **ProjID (PK)** | **Phone (PK)** | **EmpName** | **ProjName** | **Hours** | **DeptID** | **DeptName** |
| -------------- | --------------- | -------------- | ----------- | ------------ | --------- | ---------- | ------------ |
| 101            | P1              | 777111         | Pepa        | Web e-shopu  | 20        | D5         | Vývoj        |
| 101            | P1              | 777222         | Pepa        | Web e-shopu  | 20        | D5         | Vývoj        |
| 101            | P2              | 777111         | Pepa        | Mobilní App  | 10        | D5         | Vývoj        |
| 101            | P2              | 777222         | Pepa        | Mobilní App  | 10        | D5         | Vývoj        |
| 102            | P1              | 606333         | Jana        | Web e-shopu  | 30        | D6         | Marketing    |
|                |                 |                |             |              |           |            |              |

_Gratulace, jsme v 1NF. Ale všimni si, jak ta redundance (opakování) po rozbití telefonů strašně narostla. Pepa je tu najednou čtyřikrát._

### Krok 2: Cesta ke 2. normální formě (2NF)

**Pravidlo 2NF:** Musíme být v 1NF a **všechny neklíčové sloupce musí záviset na CELÉM primárním klíči**, nikoliv jen na jeho části (odstranění částečných závislostí).

Náš klíč je trojice: `(EmpID, ProjID, Phone)`. Pojďme se podívat na neklíčové sloupce:

- `Hours` (Odpracované hodiny) – Závisí na celém klíči? Ano, hodiny vyjadřují, kolik daný člověk odpracoval na daném projektu
    
- `EmpName`, `DeptID`, `DeptName` – Závisí na celém klíči? **Ne.** Závisí pouze na `EmpID`. Telefon ani projekt jejich jméno nezajímá
    
- `ProjName` – Závisí na celém klíči? **Ne.** Závisí čistě na `ProjID`
    
- `Phone` – Zjistili jsme, že telefonní čísla si žijí vlastním životem a dělají nám v klíči neplechu, vyčleníme je zvlášť
    
- **Co musíme udělat:** Rozsekat tabulku na více logických celků tak, aby v každé tabulce záviselo všechno na svém vlastním primárním klíči
    

**Výsledné tabulky ve 2NF:**

**Tabulka A: Zaměstnanci (Dočasná)** (Klíč: `EmpID`)

|**EmpID (PK)**|**EmpName**|**DeptID**|**DeptName**|
|---|---|---|---|
|101|Pepa|D5|Vývoj|
|102|Jana|D6|Marketing|

**Tabulka B: Telefony zaměstnanců** (Klíč: `EmpID, Phone`)

|**EmpID (FK)**|**Phone**|
|---|---|
|101|777111|
|101|777222|
|102|606333|

**Tabulka C: Projekty** (Klíč: `ProjID`)

|**ProjID (PK)**|**ProjName**|
|---|---|
|P1|Web e-shopu|
|P2|Mobilní App|

**Tabulka D: Výkazy práce** (Klíč: `EmpID, ProjID`)

|**EmpID (FK)**|**ProjID (FK)**|**Hours**|
|---|---|---|
|101|P1|20|
|101|P2|10|
|102|P1|30|

_Skvělé, jsme ve 2NF. Duplicity zmizely, data jsou rozdělená._

### Krok 3: Cesta ke 3. normální formě (3NF)

**Pravidlo 3NF:** Musíme být ve 2NF a **žádný neklíčový sloupec nesmí záviset na jiném neklíčovém sloupci** (odstranění tranzitivních závislostí).

Pojďme zkontrolovat naše čtyři tabulky ze 2NF. Tabulky B, C a D jsou naprosto čisté. Ale podívejme se pozorně na **Tabulku A (Zaměstnanci)**:

- Primární klíč je `EmpID`
    
- `EmpName` závisí na `EmpID` (To je v pořádku)
    
- `DeptID` (ID oddělení) závisí na `EmpID` (To je v pořádku, Pepa pracuje v D5)
    
- `DeptName` (Název oddělení) – Závisí na `EmpID`? Ano, ale nepřímo! Název "Vývoj" závisí na tom, že ID je D5. Máme tu tranzitivní závislost:
    
    $$\text{EmpID} \rightarrow \text{DeptID} \rightarrow \text{DeptName}$$
    
- **Problém v praxi:** Kdybychom zítra přejmenovali oddělení D5 z „Vývoj“ na „Výzkum“, museli bychom to přepisovat u všech zaměstnanců, kteří tam pracují. To porušuje 3NF.
    
- **Co musíme udělat:** Vytrhnout informace o oddělení z tabulky zaměstnanců ven do samostatné tabulky.
    

### Finální ráj: Kompletní schéma ve 3. normální formě (3NF)

Z původní jedné tabulky máme nyní **5 dokonale čistých, specializovaných tabulek**:

**1. Tabulka: Employees (Zaměstnanci)**

|**EmpID (PK)**|**EmpName**|**DeptID (FK)**|
|---|---|---|
|101|Pepa|D5|
|102|Jana|D6|

**2. Tabulka: Departments (Oddělení)**

|**DeptID (PK)**|**DeptName**|
|---|---|
|D5|Vývoj|
|D6|Marketing|

**3. Tabulka: Employee_Phones (Telefony)**

|**EmpID (FK)**|**Phone (PK)**|
|---|---|
|101|777111|
|101|777222|
|102|606333|

**4. Tabulky: Projects (Projekty)**

|**ProjID (PK)**|**ProjName**|
|---|---|
|P1|Web e-shopu|
|P2|Mobilní App|

**5. Tabulka: Project_Assignments (Práce na projektech)**

|**EmpID (FK)**|**ProjID (FK)**|**Hours**|
|---|---|---|
|101|P1|20|
|101|P2|10|
|102|P1|30|

### Proč je tohle finální řešení dokonalé?

1. **Žádná redundance:** Každá informace (jméno, název projektu, název oddělení) je v celé databázi zapsaná **přesně jednou**.
    
2. **Žádné anomálie:** Když Pepa změní telefon, upravíš to v jedné buňce tabulky 3. Když se zruší projekt P2, prostě ho smažeš z tabulky 4 a databáze zůstane konzistentní. Když vytvoříš nové oddělení, kde ještě nikdo nepracuje, jednoduše ho přidáš do tabulky 2, aniž bys musel vymýšlet umělého zaměstnance.
    

Dává ti tenhle postup od A do Z smysl, nebo se ti tam nějaký ten krok zdá neintuitivní?