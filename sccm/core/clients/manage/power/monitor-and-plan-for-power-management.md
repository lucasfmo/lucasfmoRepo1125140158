---
title: "Figyelés és tervezés energiagazdálkodási |} Microsoft Docs"
description: "Megtudhatja, hogyan figyelheti és tervezése a System Center Configuration Managerben az energiagazdálkodás."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 507bf676-2679-4e4d-8831-3ffc9cf8557e
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: b308329635400438cebc4935efe79b46e607fd58
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-and-plan-for-power-management-in-system-center-configuration-manager"></a>Figyelés és a terv az energiagazdálkodáshoz a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbi információk használatával alakítsa ki, figyelés és tervezés a System Center Configuration Manager energiagazdálkodási.  

##  <a name="BKMK_How_to_use_reports"></a> Energiagazdálkodási jelentések használata  
 Az energiagazdálkodás a Configuration Manager segítségével elemezheti energiafogyasztását és a számítógép energiaellátási beállításait a szervezetben számos jelentést tartalmaz. A jelentések segíthetnek a problémák elhárításában is.  

 Az energiagazdálkodási jelentések használata előtt konfigurálnia kell a jelentéskészítést a hierarchiájához. További információ a jelentéskészítés a Configuration Managerben: [a System Center Configuration Manager jelentéskészítési](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Napi jelentésekben használt energiagazdálkodási adatokat 31 napig megmarad a Configuration Manager-hely adatbázisába.  
>           Havi jelentésekben használt energiagazdálkodási adatokat 13 hónapig megmarad a Configuration Manager-hely adatbázisába.  
>   
>  Amikor az energiagazdálkodás figyelési és tervezési, valamint megfelelőségi fázisában jelentéseket futtat, mentse vagy exportálja eredményét, amelynek meg szeretné őrizni jelentéseket későbbi összehasonlítás céljából adatai abban az esetben, ha később eltávolítja a Configuration Manager által.  

## <a name="list-of-power-management-reports"></a>Energiagazdálkodási jelentések listája  
 A következő listákban részletezi az energiagazdálkodási jelentések, amelyek a Configuration Manager alkalmazásban érhető el.  

> [!NOTE]  
>  Az energiagazdálkodási jelentések megjelenítik egy kijelölt gyűjtemény fizikai és virtuális számítógépeinek a számát. Az energiagazdálkodási jelentésekben azonban csak a fizikai számítógépek energiagazdálkodási adatai láthatók.  

###  <a name="BKMK_Activity"></a> Számítógépes tevékenység jelentés  
 A **Számítógépes tevékenység** jelentés egy grafikont jelenít meg, amely adott gyűjtemény alábbi tevékenységét mutatja megadott időszakon át:  

-   **Számítógép bekapcsolva** – A számítógép be van kapcsolva.  

-   **Monitor bekapcsolva** – A monitor be van kapcsolva.  

-   **Aktív felhasználó** – A számítógépes egérről, a billentyűzetről vagy a számítógép távoli asztali kapcsolatáról származó tevékenység észlelhető.  

 Ez a jelentés használható a figyelési és tervezési, valamint alkalmazási fázis során a számítógépes, figyelési és felhasználói tevékenység közötti összehangolás megértésére egy 24 órás időszakon át. Ha bizonyos számú napon át futtatja a jelentést, a rendszer ezen időszakon át összesíti az adatokat. A jelentés segítségével meghatározhatja egy kijelölt gyűjtemény tipikus munkaidejét (csúcsidőt) és munkaidőn kívüli idejét (nem csúcsidőt), hogy eldönthesse, mikor kell konfigurált energiagazdálkodási sémákat alkalmazni.  

 A grafikonon látszanak azok az időszakok, amikor egy számítógép lehet, hogy be van kapcsolva, de nem észlelhető rajta felhasználói tevékenység. Érdemes ezen időszakokban korlátozóbb energiaellátási beállításokat alkalmazni a bekapcsolt, de nem használt számítógépek energiaköltségének csökkentéséhez. A számítógép akkor számít aktívnak, ha a grafikonon megjelenített egy óra alatt legalább egy percig számítógépes, felhasználói vagy figyelési tevékenység volt észlelhető. Ha egy számítógép nem jelent energiagazdálkodási adatokat, nem fog szerepelni a **Számítógépes tevékenység** jelentésben.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Kezdő dátum**|A legördülő listában jelölje ki a jelentés kezdő dátumát.|  
|**Befejező dátum (nem kötelező)**|A legördülő listában jelölje ki a jelentés nem kötelező befejező dátumát.|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Eszköz típusa**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek).|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ha nincs megadva a **Befejező dátum (nem kötelező)** értéke, ez a jelentés hivatkozást tartalmaz az alábbi jelentésre, amelyben további információk találhatók.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Számítógépes tevékenység részletei**|A **Részletes információkért kattintson ide** hivatkozásra kattintva megjelenítheti az aktív, inaktív és jelentéseket nem készítő számítógépek listáját a megadott dátum esetén.<br /><br /> További információ a jelen témakör [Computer Activity Details Report](#BKMK_Activity_Details) című szakaszában található.|  

###  <a name="BKMK_Comp_Activity_by_computer"></a> Számítógépes tevékenység számítógépenként jelentés  
 A **Számítógépes tevékenység számítógépenként** jelentés egy grafikont jelenít meg, amely adott számítógép alábbi tevékenységét mutatja egy bizonyos dátumon:  

-   **Számítógép bekapcsolva** – A számítógép be van kapcsolva.  

-   **Monitor bekapcsolva** – A monitor be van kapcsolva.  

-   **Aktív felhasználó** – Tevékenység észlelhető a számítógépes egérről, a billentyűzetről vagy a számítógép távoli asztali kapcsolatáról.  

 A jelentés futtatható önállóan, illetve meghívhatja a **Számítógépes tevékenység részletei** jelentés.  

> [!NOTE]  
>  A számítógépes tevékenységre vonatkozó információk a hardverleltározás során gyűjthetők az ügyfélszámítógépekről. A hardverleltározás futtatásának idejétől függően, egy csúcsidőre vagy nem csúcsidőre alkalmazott energiaséma során gyűjthetők a tevékenységadatok.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Jelentés dátuma**|A legördülő listában jelölje ki a jelentés dátumát.|  
|**Számítógép neve**|Adja meg a számítógép nevét, amelyhez jelentést szeretne futtatni.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Számítógép részletei**|A **Részletes információkért kattintson ide** hivatkozásra kattintva megjelenítheti a kijelölt számítógép energiaellátási lehetőségeit, energiaellátási beállításait és alkalmazott energiasémáit.|  

###  <a name="BKMK_Activity_Details"></a> Computer Activity Details report  
 A **Számítógépes tevékenység részletei** jelentés egy listát jelenít meg az aktív és az inaktív számítógépekről az alvási és ébredési képességeikkel. Ezt a jelentést a [Computer Activity Report](#BKMK_Activity) jelentés hívja meg, és nem a webhelygazda általi közvetlen futtatásra készült.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Jelentés dátuma**|A legördülő listában jelölje ki a jelentéshez használandó dátumot.|  
|**Jelentés órája**|A legördülő listában a megadott dátumon jelöljön ki egy órát, amikor futtatni szeretné ezt a jelentést. Az érvényes értékek **12** és **23**óra közé esnek.|  
|**Számítógép állapota**|A legördülő listában jelölje ki a számítógép állapotát, amelynél futtatni szeretné ezt a jelentést. Érvényes értékek a következők **összes** (számítógépek, amelyek volt kapcsolva), **a** (számítógépek bekapcsolt), és **ki** (volt kapcsolva Alvás, kikapcsolva, vagy a hibernált állapot). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  
|**Eszköz típusa**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  
|**Alvó üzemmódra képes**|A legördülő listában adja meg, hogy meg szeretné-e jeleníteni az alvó üzemmódra képes számítógépeket a jelentésben. Érvényes értékek a következők **összes** (mindkét számítógépen képes és képtelen alvó) **nem** (számítógépek, amelyek képtelen alvó), és **Igen** (az alvó üzemmódra képes számítógépek).|  
|**Alvó üzemmódból felébredni képes**|A legördülő listában adja meg, hogy meg szeretné-e jeleníteni az alvó üzemmódból felébredni képes számítógépeket a jelentésben. Érvényes értékek a következők **összes** (mindkét számítógépen kompatibilis és nem alkalmas az alvó üzemmódból felébredni) **nem** (számítógépek, amelyek az alvó üzemmódból felébredni képes), és **Igen** (az alvó üzemmódból felébredni képes számítógépek).|  
|**Energiaséma**|A legördülő listában jelölje ki azokat az energiaséma-típusokat, amelyeket meg szeretne jeleníteni a jelentésben. Érvényes értékek a következők **összes** (a számítógép, amely nem rendelkezik ilyennel energiagazdálkodási sémákat alkalmazni; egy energiagazdálkodási séma alkalmazva rendelkező számítógépek; az energiagazdálkodásból kizárt számítógépek), **nincs megadva** (számítógépek, amelyek nem rendelkeznek egy energiagazdálkodási séma alkalmazva), **definiált** (számítógépek, amelyek rendelkeznek egy energiagazdálkodási séma alkalmazva), és **kizárt** (az energiagazdálkodásból kizárt számítógépek).|  
|**Operációs rendszer**|A legördülő listában jelölje ki azokat az operációs rendszereket, amelyeket meg szeretne jeleníteni a jelentésben, illetve válassza az **Összes** lehetőséget az összes operációs rendszer megjelenítéséhez.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Számítógépes tevékenység számítógépenként**|Kattintson egy számítógépnévre kattintva tekintse meg az adott számítógépre vonatkozó adott tevékenységek egy kiválasztott jelentési időszak alatt. Ezek a tevékenységek **számítógép** (a számítógép engedélyezve lett?), **figyelheti** (a figyelő be lett kapcsolva?), és **felhasználó Active** (tevékenység észlelhető a számítógépes egérről, billentyűzet vagy a távoli asztali kapcsolat).<br /><br /> További információ a jelen témakör [Computer Activity by Computer Report](#BKMK_Comp_Activity_by_computer) című szakaszában található.|  

###  <a name="BKMK_Computer_Details"></a> Számítógép részletei jelentés  
 A **Számítógép részletei** jelentés megjeleníti egy megadott számítógép részletes energiaellátási lehetőségeit, energiaellátási beállításait, valamint energiasémáit. Ezt a jelentést a **Számítógépes tevékenység számítógépenként** jelentés, a **Több energiasémával rendelkező számítógépek** jelentés, az **Energiaellátási lehetőségek** jelentés és az **Energiaellátási beállítások részletei** jelentés hívja meg. Ez a jelentés nem a webhelygazda általi közvetlen futtatásra készült.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Számítógép neve**|Adja meg a számítógép nevét, amelyhez jelentést szeretne futtatni.|  
|**Energiamódban**|A legördülő listában jelölje ki a jelentés eredményeiben megjeleníteni kívánt energiaellátási beállítások típusát. A **Hálózat** elemet választva a számítógép hálózathoz csatlakozásához konfigurált energiaellátási beállításokat tekintheti meg, az **Akkumulátor** elemet választva pedig a számítógép akkumulátorról történő működéséhez konfigurált energiaellátási beállításokat nézheti meg.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nincsenek olyan rejtett paraméterek, amelyeket megadhat.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Not_Reporting"></a> A számítógép nem küld részleteket jelentés  
 **A számítógép nem küld részleteket** jelentés megjeleníti egy megadott gyűjtemény azon számítógépeinek listáját, amelyek adott dátum meghatározott időpontjakor nem jelentettek energiaellátással kapcsolatos tevékenységet. Ezt a jelentést a **Computer Activity Report** jelentés hívja meg, és nem a webhelygazda általi közvetlen futtatásra készült.  

> [!NOTE]  
>  A számítógépek a hardverleltár-ütemezések részeként készítenek jelentést az energiagazdálkodási információkról. Mielőtt egy számítógépet jelentést nem készítőnek tekintene, ellenőrizze, hogy jelentette-e a hardverleltárt.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Jelentés dátuma**|A legördülő listában jelölje ki a jelentés dátumát.|  
|**Jelentés órája**|A legördülő listában a megadott dátumon jelöljön ki egy órát, amikor futtatni szeretné ezt a jelentést. Az érvényes értékek **12** és **23**óra közé esnek.|  
|**Eszköz típusa**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Excluded"></a> Kizárt számítógépek  
 A **kizárt számítógépek** jelentés egy adott gyűjtemény Configuration Manager energiagazdálkodásból kizárt számítógépek listáját jeleníti meg.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  
|**Ok**|A legördülő listában válassza ki az okot, ami miatt a számítógépek ki lettek zárva az energiagazdálkodásból. Megjelenítheti **összes** (összes kizárt számítógépek), **rendszergazda által kizárt** (csak számítógépek egy rendszergazda felhasználó által kizárt), és **felhasználó által kizárt** (csak számítógépekre a Szoftverközpont egy felhasználója által kizárt).|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Energiagazdálkodás – számítógép részletei**|Egy számítógépnévre kattintva megjelenítheti a kijelölt számítógép energiaellátási lehetőségeit, energiaellátási beállításait és alkalmazott energiasémáit.<br /><br /> További információ a jelen témakör [Computer Details Report](#BKMK_Computer_Details) című szakaszában található.|  

###  <a name="BKMK_Multiple"></a> Több energiasémával rendelkező számítógépek  
 A **Több energiasémával rendelkező számítógépek** jelentés megjeleníti azon számítógépek listáját, amelyek több, különböző energiasémákat alkalmazó gyűjtemény tagjai. A jelentés a vélhetően ütköző energiaellátási beállításokkal rendelkező minden számítógép esetén megjeleníti a számítógépnevet és az azokhoz a gyűjteményekhez alkalmazott energiasémákat, amelyeknek tagja a számítógép.  

> [!IMPORTANT]  
>  Ha egy számítógép több gyűjtemény tagja, ahol az egyes gyűjtemények rendelkezik különböző energiasémákat, majd a legkevésbé korlátozó energiasémát alkalmazza a rendszer.  
>   
>  Ha egy számítógép több gyűjtemény tagja, ahol az egyes gyűjtemények rendelkezik különböző Felébresztési idő, majd az éjfélhez legközelebbi idő lesz.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Energiagazdálkodás – számítógép részletei**|Egy számítógépnévre kattintva megjelenítheti a kijelölt számítógép energiaellátási lehetőségeit, energiaellátási beállításait és alkalmazott energiasémáit.<br /><br /> További információ a jelen témakör [Computer Details Report](#BKMK_Computer_Details) című szakaszában található.|  

###  <a name="BKMK_Consumption"></a> Energiafogyasztás jelentés  
 Az **Energiafogyasztás** jelentés az alábbi információkat jeleníti meg:  

-   Adott gyűjtemény számítógépeinek a megadott időszakra vonatkozó teljes havi energiafogyasztását kilowattórában (kWh) megjelenítő grafikon.  

-   Adott gyűjtemény egyes számítógépeinek a megadott időszakra vonatkozó átlagos energiafogyasztását kilowattórában (kWh) megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek a megadott időszakra vonatkozó teljes havi energiafogyasztását kilowattórában (kWh) és átlagos energiafogyasztását megjelenítő táblázat.  

 Ezek az információk segíthetik környezete fogyasztási trendjeinek a megértését. Miután energiasémát alkalmazott a kijelölt gyűjteményben lévő számítógépekre, a számítógépek energiafogyasztásának csökkennie kell.  

> [!NOTE]  
>  Ha egy energiaséma alkalmazását követően tagokat vesz fel a gyűjteménybe, illetve távolít el abból, ez hatással lesz az **Energiafogyasztás** jelentés által megjelenített eredményekre, és megnehezítheti a figyelési és tervezési, valamint alkalmazási fázisból származó eredmények összehasonlítását.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Kezdő dátum**|A legördülő listában jelölje ki a jelentés kezdő dátumát.|  
|**Befejező dátum**|A legördülő listában jelölje ki a jelentés befejező dátumát.|  
|**Gyűjtemény neve**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  
|**Eszköz típusa**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Asztali számítógép bekapcsolva**|Bekapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,07** kWh.|  
|**Hordozható számítógép bekapcsolva**|Bekapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,02** kWh.|  
|**Asztali számítógép alvó állapota**|Alvó állapotba lépett asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,003** kWh.|  
|**Hordozható számítógép alvó üzemmódban**|Alvó állapotba lépett hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,001** kWh.|  
|**Asztali számítógép kikapcsolva**|Kikapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Hordozható számítógép kikapcsolva**|Kikapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Asztali monitor bekapcsolva**|Bekapcsolt állapotú asztali számítógép-monitor energiafogyasztásának megadása. Az alapértelmezett érték **0,028** kWh.|  
|**Hordozható számítógép kijelzője bekapcsolva**|Bekapcsolt állapotú hordozható számítógép kijelzője energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Consumption_by_Day"></a> Napi energiafogyasztás jelentés  
 A **Napi energiafogyasztás** jelentés az alábbi információkat jeleníti meg:  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó teljes napi energiafogyasztását kilowattórában (kWh) megjelenítő grafikon.  

-   Adott gyűjtemény egyes számítógépeinek az elmúlt 31 napra vonatkozó átlagos napi energiafogyasztását kilowattórában (kWh) megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó teljes napi energiafogyasztását kilowattórában (kWh) és átlagos napi energiafogyasztását megjelenítő táblázat.  

 Ezek az információk segíthetik környezete fogyasztási trendjeinek a megértését. Miután energiasémát alkalmazott a kijelölt gyűjteményben lévő számítógépekre, a számítógépek energiafogyasztásának csökkennie kell.  

> [!NOTE]  
>  Ha egy energiaséma alkalmazását követően tagokat vesz fel a gyűjteménybe, illetve távolít el abból, ez hatással lesz az **Energiafogyasztás** jelentés által megjelenített eredményekre, és megnehezítheti a figyelési és tervezési, valamint alkalmazási fázisból származó eredmények összehasonlítását.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  
|**Device Type**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Asztali számítógép bekapcsolva**|Bekapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,07** kWh.|  
|**Hordozható számítógép bekapcsolva**|Bekapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,02** kWh.|  
|**Asztali számítógép alvó állapota**|Alvó állapotba lépett asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,003** kWh.|  
|**Hordozható számítógép alvó üzemmódban**|Alvó állapotba lépett hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,001** kWh.|  
|**Asztali számítógép kikapcsolva**|Kikapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Hordozható számítógép kikapcsolva**|Kikapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Asztali monitor bekapcsolva**|Bekapcsolt állapotú asztali számítógép-monitor energiafogyasztásának megadása. Az alapértelmezett érték **0,028** kWh.|  
|**Hordozható számítógép kijelzője bekapcsolva**|Bekapcsolt állapotú hordozható számítógép kijelzője energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Cost"></a> Energiaköltség jelentés  
 Az **Energiaköltség** jelentés az alábbi információkat jeleníti meg:  

-   Adott gyűjtemény számítógépeinek a megadott időszakra vonatkozó teljes havi energiaköltségét megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek a megadott időszakra vonatkozó átlagos havi energiaköltségét megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó teljes havi energiaköltségét és átlagos havi energiaköltségét megjelenítő táblázat.  

 Ezek az információk segíthetik környezete energiaköltségi trendjeinek a megértését. Miután energiasémát alkalmazott a kijelölt gyűjteményben lévő számítógépekre, a számítógépek energiaköltségének csökkennie kell.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Kezdő dátum**|A legördülő listában jelölje ki a jelentés kezdő dátumát.|  
|**Befejező dátum**|A legördülő listában jelölje ki a jelentés befejező dátumát.|  
|**kWh költsége**|Az elektromos áram kilowattóránkénti költségének megadása Az alapértelmezett érték **0,09**.<br /><br /> A rejtett paraméterek szakaszban módosíthatja a jelentésben használt pénznemegységet.|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Eszköz típusa**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Asztali számítógép bekapcsolva**|Bekapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,07** kWh.|  
|**Hordozható számítógép bekapcsolva**|Bekapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,02** kWh.|  
|**Asztali számítógép alvó állapota**|Alvó állapotba lépett asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,003** kWh.|  
|**Hordozható számítógép alvó üzemmódban**|Alvó állapotba lépett hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,001** kWh.|  
|**Asztali számítógép kikapcsolva**|Kikapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Hordozható számítógép kikapcsolva**|Kikapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Asztali monitor bekapcsolva**|Bekapcsolt állapotú asztali számítógép-monitor energiafogyasztásának megadása. Az alapértelmezett érték **0,028** kWh.|  
|**Hordozható számítógép kijelzője bekapcsolva**|Bekapcsolt állapotú hordozható számítógép kijelzője energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Pénznem**|A jelentéshez használandó pénznemcímke megadása. Az alapértelmezett érték **USD ($)**.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Cost_by_Day"></a> Napi energiaköltség jelentés  
 A **Napi energiaköltség** jelentés az alábbi információkat jeleníti meg:  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó teljes napi energiaköltségét megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó átlagos napi energiaköltségét megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó teljes napi energiaköltségét és átlagos napi energiaköltségét megjelenítő táblázat.  

 Ezek az információk segíthetik környezete energiaköltségi trendjeinek a megértését. Miután energiasémát alkalmazott a kijelölt gyűjteményben lévő számítógépekre, a számítógépek energiaköltségének csökkennie kell.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Eszköz típusa**|A legördülő listában jelölje ki a számítógép típusát, amelyről jelentést szeretne készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  
|**kWh költsége**|Az elektromos áram kilowattóránkénti költségének megadása Az alapértelmezett érték **0,09**.<br /><br /> A rejtett paraméterek szakaszban módosíthatja a jelentésben használt pénznemegységet.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Asztali számítógép bekapcsolva**|Bekapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,07** kWh.|  
|**Hordozható számítógép bekapcsolva**|Bekapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,02** kWh.|  
|**Asztali számítógép alvó állapota**|Alvó állapotba lépett asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,003** kWh.|  
|**Hordozható számítógép alvó üzemmódban**|Alvó állapotba lépett hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,001** kWh.|  
|**Asztali számítógép kikapcsolva**|Kikapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Hordozható számítógép kikapcsolva**|Kikapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Asztali monitor bekapcsolva**|Bekapcsolt állapotú asztali számítógép-monitor energiafogyasztásának megadása. Az alapértelmezett érték **0,028** kWh.|  
|**Hordozható számítógép kijelzője bekapcsolva**|Bekapcsolt állapotú hordozható számítógép kijelzője energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Pénznem**|A jelentéshez használandó pénznemcímke megadása. Az alapértelmezett érték **USD ($)**.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Environmental_Impact"></a> Környezeti hatás jelentés  
 A **Környezeti hatás** jelentés az alábbi információkat jeleníti meg:  

-   Adott gyűjtemény számítógépeinek a megadott időn belüli számítógépek a teljes havi CO2 kibocsátását (tonnában) megjelenítő grafikon.  

-   A megadott gyűjtemény számítógépeinek a megadott időszakra vonatkozó számítógépenként a átlagos havi CO2 kibocsátását (tonnában) megjelenítő grafikon.  

-   A teljes havi CO2 jön létre, és a számítógépen lévő adott gyűjtemény számítógépeinek a megadott időszakra vonatkozó létre átlagos havi CO2 megjelenítő táblázat.  

 A **környezeti hatás** jelentés kiszámítja a kibocsátott CO2 kibocsátását (tonnában) a idő alapján, amelyet egy számítógép vagy monitor bekapcsolva töltött egy 24 órás időszakban.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Jelentés kezdő dátuma**|A legördülő listában jelölje ki a jelentés kezdő dátumát.|  
|**Jelentés befejező dátuma**|A legördülő listában jelölje ki a jelentés befejező dátumát.|  
|**Gyűjtemény neve**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  
|**Eszköz típusa**|A legördülő listában jelölje ki, hogy milyen számítógéptípus esetén szeretne jelentést készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Asztali számítógép bekapcsolva**|Bekapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,07** kWh.|  
|**Hordozható számítógép bekapcsolva**|Bekapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,02** kWh.|  
|**Asztali számítógép alvó állapota**|Alvó állapotba lépett asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,003** kWh.|  
|**Hordozható számítógép alvó üzemmódban**|Alvó állapotba lépett hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,001** kWh.|  
|**Asztali számítógép kikapcsolva**|Kikapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Hordozható számítógép kikapcsolva**|Kikapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Asztali monitor bekapcsolva**|Bekapcsolt állapotú asztali számítógép-monitor energiafogyasztásának megadása. Az alapértelmezett érték **0,028** kWh.|  
|**Hordozható számítógép kijelzője bekapcsolva**|Bekapcsolt állapotú hordozható számítógép kijelzője energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Széndioxid kibocsátási tényező (tonna/kWh)** (CO2Mix)|A széndioxid kibocsátási tényező (tonna/kWh) értékének megadása, amelyet általában az energiaszolgáltatótól tudhat meg. Az alapértelmezett érték **0,0015** tonna/kWh.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Environmental_Impact_by_Day"></a> Napi környezeti hatás jelentés  
 A **Napi környezeti hatás** jelentés az alábbi információkat jeleníti meg:  

-   A megadott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó a teljes napi CO2 kibocsátását (tonnában) megjelenítő grafikon.  

-   Adott gyűjtemény számítógépeinek az elmúlt 31 napra vonatkozó a átlagos napi CO2 kibocsátását (tonnában) megjelenítő grafikon.  

-   A teljes napi CO2 generált megjelenítő táblázat és az átlagos napi CO2 kibocsátását számítógépek a megadott gyűjtemény számítógépeinek az elmúlt 31 napra.  

 A **napi környezeti hatás** jelentés kiszámítja a kibocsátott CO2 kibocsátását (tonnában) a idő alapján, amelyet egy számítógép vagy monitor bekapcsolva töltött egy 24 órás időszakban.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  
|**Eszköz típusa**|A legördülő listában jelölje ki a számítógép típusát, amelyről jelentést szeretne készíteni. Érvényes értékek a következők **összes** (asztali és a hordozható számítógépek), **asztali** (csak asztali számítógépekkel), és **hordozható** (csak a hordozható számítógépek). Ezek az értékek csak a kiválasztott jelentési időszak adja vissza.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Asztali számítógép bekapcsolva**|Bekapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,07** kWh.|  
|**Hordozható számítógép bekapcsolva**|Bekapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,02** kWh.|  
|**Asztali számítógép kikapcsolva**|Kikapcsolt állapotú asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Hordozható számítógép kikapcsolva**|Kikapcsolt állapotú hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Asztali számítógép alvó állapota**|Alvó állapotba lépett asztali számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,003** kWh.|  
|**Hordozható számítógép alvó üzemmódban**|Alvó állapotba lépett hordozható számítógép energiafogyasztásának megadása. Az alapértelmezett érték **0,001** kWh.|  
|**Asztali monitor bekapcsolva**|Bekapcsolt állapotú asztali számítógép-monitor energiafogyasztásának megadása. Az alapértelmezett érték **0,028** kWh.|  
|**Hordozható számítógép kijelzője bekapcsolva**|Bekapcsolt állapotú hordozható számítógép kijelzője energiafogyasztásának megadása. Az alapértelmezett érték **0** kWh.|  
|**Széndioxid kibocsátási tényező (tonna/kWh)** (CO2Mix)|A széndioxid kibocsátási tényező (tonna/kWh) értékének megadása, amelyet általában az energiaszolgáltatótól tudhat meg. Az alapértelmezett érték **0,0015** tonna/kWh.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés nem kapcsolódik semmilyen más energiagazdálkodási jelentéshez.  

###  <a name="BKMK_Insomnia_Computer_Details"></a> Az alvó üzemmódra képtelen számítógépek részletei jelentés  
 **Az alvó üzemmódra képtelen számítógépek részletei** jelentés megjeleníti azoknak a számítógépeknek a listáját, amelyek adott időszakban bizonyos okból kifolyólag nem tudtak alvó vagy hibernált állapotba lépni. Ezt a jelentést **Az alvó üzemmódra képtelen számítógépek jelentése** hívja meg, és nem a webhelygazda általi közvetlen futtatásra készült.  

 **Az alvó üzemmódra képtelen számítógépek jelentése** **alvó üzemmódra nem alkalmasként** jeleníti meg a számítógépeket, amikor nem képesek alvó állapotba lépni, és a jelentés teljes megadott intervallumában be voltak kapcsolva. A jelentés **hibernálásra nem alkalmasként** jeleníti meg a számítógépeket, amikor nem képesek hibernált állapotba lépni, és a jelentés megadott teljes intervallumában be voltak kapcsolva.  

> [!NOTE]  
>  Az energiagazdálkodás csak Windows 7 vagy Windows Server 2008 R2 rendszerű számítógépek alvó vagy hibernált állapotba lépését megakadályozó okokat tud összegyűjteni.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Jelentési időköz (nap)**|A jelentés napjainak számát adja meg. Az alapértelmezett érték **7** nap.|  
|**A sikertelen alvó állapotba lépés oka**|A legördülő listában jelölje ki az egyik okot, amely megakadályozza, hogy a számítógépek alvó vagy hibernált állapotba lépjenek.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Számítógép részletei**|A **Részletes információkért kattintson ide** hivatkozásra kattintva megjelenítheti a kijelölt számítógép energiaellátási lehetőségeit, energiaellátási beállításait és alkalmazott energiasémáit.<br /><br /> További információ a jelen témakör [Computer Details Report](#BKMK_Computer_Details) című szakaszában található.|  

###  <a name="BKMK_Insomnia"></a> Insomnia report  
 **Az alvó üzemmódra képtelen számítógépek jelentése** megjeleníti a számítógépek alvó vagy hibernált állapotba lépését megakadályozó általános okok listáját, valamint az adott időszakban az egyes okok által érintett számítógépek számát. A számítógépek alvó vagy hibernált állapotba lépésének számos akadálya lehet. Ilyen például a számítógépen futó egyik folyamat, egy megnyitott távoli asztali munkamenet, illetve ha a számítógép képtelen alvó vagy hibernált állapotba lépni. Ebből a jelentésből megnyithatja **Az alvó üzemmódra képtelen számítógépek részletei** jelentést, amelyben az alvó vagy hibernált állapotba lépést akadályozó egyes okok által érintett számítógépek listája látható.  

 Az Energiaellátás alvó módba kapcsolhatatlanságának okai jelentés **alvó üzemmódra nem alkalmasként** jeleníti meg a számítógépeket, amikor nem képesek alvó állapotba lépni, és a jelentés teljes megadott intervallumában be voltak kapcsolva. A jelentés **hibernálásra nem alkalmasként** jeleníti meg a számítógépeket, amikor nem képesek hibernált állapotba lépni, és a jelentés megadott teljes intervallumában be voltak kapcsolva.  

> [!NOTE]  
>  Az energiagazdálkodás csak Windows 7 vagy Windows Server 2008 R2 rendszerű számítógépek alvó vagy hibernált állapotba lépését megakadályozó okokat tud összegyűjteni.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Jelentési időköz (nap)**|A jelentés napjainak számát adja meg. Az alapértelmezett érték **7** nap. A maximális érték **365** nap. Ha ma szeretné futtatni a jelentést, adja meg a **0** értéket.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Az alvó üzemmódra képtelen számítógépek részletei**|Az **Érintett számítógépek** oszlopban egy számra kattintva megjelenítheti azon számítógépek listáját, amelyek a kijelölt ok miatt nem tudtak alvó vagy hibernált állapotba lépni.<br /><br /> További információ a jelen témakör [Insomnia Computer Details Report](#BKMK_Insomnia_Computer_Details) című szakaszában található.|  

###  <a name="BKMK_Capabilites"></a> Energiaellátási lehetőségek jelentés  
 Az **Energiaellátási lehetőségek** jelentés megjeleníti a megadott gyűjtemény számítógépeinek energiagazdálkodási hardveres képességeit. Ez a jelentés általában az energiagazdálkodás figyelési fázisában használható szervezete számítógépeinek energiagazdálkodási képességeinek meghatározásához. A jelentésben látható információk segítségével létrehozhatók olyan számítógép-gyűjtemények, amelyekhez energiasémákat kell alkalmazni, illetve amelyek kizárandók az energiagazdálkodásból. A jelentés által megjelenített energiagazdálkodási képességek az alábbiak:  

-   **Alvó üzemmódra képes** – Annak jelzése, hogy a számítógép képes-e alvó állapotba lépni, ha erre van konfigurálva.  

-   **Hibernálásra alkalmas** – Annak jelzése, hogy a számítógép hibernált állapotba léphet-e, ha erre van konfigurálva.  

-   **Felébresztés alvó állapotból** – Annak jelzése, hogy a számítógép felébredhet-e alvó állapotból, ha erre van konfigurálva.  

-   **Felébresztés hibernált állapotból** – Annak jelzése, hogy a számítógép felébredhet-e hibernált állapotból, ha erre van konfigurálva.  

 Az **Energiaellátási lehetőségek** jelentésben szereplő értékek jelzik a számítógépek alvó és hibernált állapottal kapcsolatos, a Windows által jelentett képességeit. A jelentett értékek azonban nem tükrözik azokat az eseteket, ahol a Windows vagy a BIOS beállításai megakadályozzák e funkciók működését.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  
|**Szűrő megjelenítése**|Válassza ki a legördülő listáról, **nem támogatott** csak a számítógépek megjelennek a megadott gyűjteményben, amelyek képtelen alvó, hibernált állapotba lépni, alvó üzemmódból felébredni vagy felébressze a hibernált állapotból. Válassza ki **összes megjelenítése** összes számítógép megjelenítése a megadott gyűjteményben.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Ehhez a jelentéshez nem tartoznak megadható rejtett paraméterek.  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Számítógép részletei**|Egy számítógépnévre kattintva megjelenítheti a kijelölt számítógép energiaellátási lehetőségeit, energiaellátási beállításait és alkalmazott energiasémáit.<br /><br /> További információ a jelen témakör [Computer Details Report](#BKMK_Computer_Details) című szakaszában található.|  

###  <a name="BKMK_Settings"></a> Energiaellátási beállítások jelentés  
 Az **Energiaellátási beállítások** jelentés a megadott gyűjteményben a számítógépek által használt energiaellátási beállítások összesített listáját jeleníti meg. Az egyes energiaellátási beállítások esetén a lehetséges energiamódok, értékek és egységek láthatók, az értékeket használó számítógépek számával együtt. Az energiagazdálkodás figyelési fázisában a rendszergazda e jelentés segítségével áttekintheti a számítógépek által a webhelyen használt meglévő energiaellátási beállításokat, és egy energiagazdálkodási séma használatával megtervezheti az alkalmazni kívánt optimális beállításokat. Ez a jelentés hasznos annak ellenőrzésében is, hogy az energiaellátási beállítások alkalmazása megfelelő volt-e.  

> [!NOTE]  
>  A megjelenített beállítások összegyűjtése az ügyfélszámítógépekről történt a hardverleltározás során. A hardverleltár futásának időpontjától függően a csúcsidőre vagy nem csúcsidőre alkalmazott energiasémákból gyűjthetők a beállítások.  

 A jelentés konfigurálásához az alábbi paraméterek használhatók.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény neve**|A legördülő listában jelöljön ki egy gyűjteményt a jelentéshez.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**numberOfLocalizations**|Azon nyelvek számának megadása, amelyeken meg szeretné jeleníteni az ügyfélszámítógépek által jelentett energiaellátási beállításneveket. Ha csak a legnépszerűbb nyelvet szeretné megjeleníteni, hagyja a beállítást az alapértelmezett **1**értéken. Ha az összes nyelvet meg szeretné jeleníteni, állítsa **0**értékre a beállítást.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Energiaellátási beállítások részletei**|A **Számítógépek** oszlopban a számítógépek számára kattintva megjelenítheti az összes, az abban a sorban az energiaellátási beállításokat használó számítógép listáját.<br /><br /> További információ a jelen témakör [Power Settings Details Report](#BKMK_Settings_Details) című szakaszában található.|  

###  <a name="BKMK_Settings_Details"></a> Power Settings Details report  
 Az **Energiaellátási beállítások részletei** jelentésben további információk láthatók az **Energiaellátási beállítások** jelentésben kijelölt számítógépekről. Ezt a jelentést az **Energiaellátási beállítások** hívja meg, és nem a webhelygazda általi közvetlen futtatásra készült.  

#### <a name="required-report-parameters"></a>Szükséges jelentésparaméterek  
 Az alábbi paramétereket meg kell adni a jelentés futtatásához.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**Gyűjtemény**|A legördülő listában jelölje ki a jelentéshez használandó gyűjteményt.|  
|**Energiaellátási beállítás GUID azonosítója**|A legördülő listában jelölje ki az energiaellátási beállítás GUID azonosítóját, amelyről jelentést szeretne készíteni. Az összes energiaellátási beállításait, valamint a használatukat listájáért lásd: [terv elérhető energiagazdálkodási beállításokat](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) témakör [hogyan hozhat létre és alkalmazhat energiasémákat a System Center Configuration Managerben](../../../../core/clients/manage/power/create-and-apply-power-plans.md).|  
|**Power Mode**|A legördülő listában jelölje ki a jelentés eredményeiben megjeleníteni kívánt energiaellátási beállítások típusát. A **Hálózat** elemet választva a számítógép hálózathoz csatlakozásához konfigurált energiaellátási beállításokat tekintheti meg, az **Akkumulátor** elemet választva pedig a számítógép akkumulátorról történő működéséhez konfigurált energiaellátási beállításokat nézheti meg.|  
|**Beállítás indexe**|A legördülő listában válassza ki a kijelölt energiaellátási beállítás nevének értékét, amelyről jelentést szeretne készíteni. Ha például meg szeretné jeleníteni az összes számítógépet, amelynél a **Merevlemez kikapcsolása** beállítás **10** percre van állítva, válassza a **Merevlemez kikapcsolása** lehetőséget az **Energiaellátási beállítás neve** esetén és a **10** értéket a **Beállítás indexe**esetén.|  

#### <a name="hidden-report-parameters"></a>Rejtett jelentésparaméterek  
 Az alábbi rejtett jelentésparaméterek megadásával módosítható a jelentés viselkedése.  

|Paraméternév|Leírás|  
|--------------------|-----------------|  
|**numberOfLocalizations**|Azon nyelvek számának megadása, amelyeken meg szeretné jeleníteni az ügyfélszámítógépek által jelentett energiaellátási beállításneveket. Ha csak a legnépszerűbb nyelvet szeretné megjeleníteni, hagyja a beállítást az alapértelmezett **1**értéken. Ha az összes nyelvet meg szeretné jeleníteni, állítsa **0**értékre a beállítást.|  

#### <a name="report-links"></a>Jelentéshivatkozások  
 Ez a jelentés hivatkozásokat tartalmaz az alábbi jelentésre, amelyben további információk találhatók a kijelölt elemről.  

|Jelentés neve|Részletek|  
|-----------------|-------------|  
|**Számítógép részletei**|Egy számítógépnévre kattintva megjelenítheti a kijelölt számítógép energiaellátási lehetőségeit, energiaellátási beállításait és alkalmazott energiasémáit.<br /><br /> További információ a jelen témakör [Computer Details Report](#BKMK_Computer_Details) című szakaszában található.|  

