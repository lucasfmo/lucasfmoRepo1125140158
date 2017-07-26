---
title: "Replikálás |} Microsoft Docs"
description: "Megtudhatja, hogyan infrastruktúrájának és műveleteinek a Configuration Manager figyelése a konzolon a figyelés munkaterület használatával."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fab4d67-8d2a-45ce-8b06-471280102cf6
caps.latest.revision: 11
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 132803a1aa9aad5c5462686bd656688418e47d07
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="monitor-hierarchy-and-replication-infrastructure-in-system-center-configuration-manager"></a>Hierarchia és replikációs infrastruktúra figyelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Infrastruktúrájának és műveleteinek a System Center Configuration Manager figyelése a **figyelés** munkaterület a Configuration Manager konzolon.  

> [!NOTE]  
>  Ez alól kivétel az áttelepítés, amely közvetlenül figyelhető a **Felügyelet** munkaterület **Áttelepítés** csomópontjában. További információk: [A System Center Configuration Managerbe való áttelepítés műveletei](../../../core/migration/operations-for-migration.md).  

 Mellett a Configuration Manager konzol segítségével a figyeléshez, használja a Configuration Manager jelentéseit, vagy Configuration Manager-összetevők a Configuration Manager naplófájljainak megtekintéséhez. További információ a jelentésekről: [Jelentéskészítés a System Center Configuration Managerben](../../../core/servers/manage/reporting.md). További információ a naplófájlokról: [Naplófájlok a System Center Configuration Managerben](../../../core/plan-design/hierarchy/log-files.md).  

 A helyek figyelése közben keressen olyan problémákra utaló jeleket, amelyek felhasználói beavatkozást igényelnek. Példa:  

-   Hátralékos fájlok a helykiszolgálókon és a helyrendszerekben.  

-   Hibát vagy problémát jelző állapotüzenetek.  

-   Sikertelen kommunikáció a helyen belül.  

-   Hibaüzenetek és figyelmeztető üzenetek a kiszolgálók rendszeresemény-naplóiban.  

-   Hibaüzenetek és figyelmeztető üzenetek a Microsoft SQL Server hibanaplójában.  

-   Olyan helyek vagy ügyfelek, amelyek hosszú ideje nem küldtek jelentést.  

-   Lassú válasz az SQL Server-adatbázistól.  

-   Hardverhiba jelei.  

A hely meghibásodási kockázatának csökkentéséhez a figyelési feladat során észlelt problémák esetében a lehető leghamarabb határozza meg a probléma forrását, és javítsa ki a hibát.  



##  <a name="BKMK_MonintorMgmtTasks"></a> A Configuration Manager általános felügyeleti feladatainak figyelése  
 A Configuration Manager beépített figyelést biztosít a Configuration Manager konzolon. Számos feladatot figyelhet, így többek között a szoftverfrissítésekkel, az energiagazdálkodással és a hierarchiában tartalom központi telepítésével kapcsolatos feladatokat.  

 Az alábbi információk használatával alakítsa ki a Configuration Manager-feladatok figyelése:  

 **Riasztások**  
   Lásd [A riasztások és az állapotrendszer használata a System Center Configuration Managerben](../../../core/servers/manage/use-alerts-and-the-status-system.md) című témakör [Riasztások figyelése](../../../core/servers/manage/use-alerts-and-the-status-system.md#BKMK_MonitorAlerts) című szakaszát.  

 **Megfelelőségi beállítások**  
   Lásd: [A megfelelőségi beállítások figyelése a System Center Configuration Managerben](../../../compliance/deploy-use/monitor-compliance-settings.md).  

 **Tartalom központi telepítése**  
   Általános információk a tartalomfigyelésről: [A System Center Configuration Managerhez kapcsolódó tartalom és tartalomkezelési infrastruktúra felügyelete](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

Adott típusú tartalom központi telepítésének figyelése:
-   Az alkalmazások figyelése: [Alkalmazások figyelése a System Center Configuration Managerrel](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

-   A Csomagok és programok figyeléséhez tekintse meg a [Csomagok és programok a System Center Configuration Managerben](../../../apps/deploy-use/packages-and-programs.md) című témakör Csomagok és programok kezelése című szakaszát.  

**Endpoint Protection**  
   Lásd: [Az Endpoint Protection figyelése a System Center Configuration Managerben](../../../protect/deploy-use/monitor-endpoint-protection.md).  

**Energiagazdálkodás figyelése**  
 Lásd: [Energiagazdálkodási figyelés és tervezés a System Center Configuration Managerben](../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

**Szoftverhasználat-mérés figyelése**  
Lásd: [Alkalmazáshasználat figyelése a szoftverhasználat-méréssel a System Center Configuration Managerben](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

**Szoftverfrissítések figyelése**  
 Lásd: [figyelése a System Center Configuration Manager szoftverfrissítések](../../../sum/deploy-use/monitor-software-updates.md).  


##  <a name="BKMK_MonitorInfrastructure"></a> A Configuration Manager hierarchiájának figyelése  
A Configuration Manager figyelése állapotának és műveleteinek a hierarchia több módszert kínál. Ellenőrizheti a hierarchiában található helyek állapotát, figyelheti a helyek közötti replikációt helyhierarchiában vagy földrajzi nézetben, figyelheti az adatbázis-replikációhoz használt helyek közötti replikációs hivatkozásokat, és a Replication Link Analyzer eszköz segítségével megoldhatja a replikációval kapcsolatos problémákat.  

###  <a name="BKMK_SH_Node"></a> A Helyhierarchia csomópont áttekintése  
A **Helyhierarchia** csomópontjának a **figyelés** csomópontja nyújt áttekintést a Configuration Manager hierarchia és a helyek közötti hivatkozásokról. Két nézetet használhat:  

-   **Hierarchiadiagram**: Ez a nézet, amelyek egyszerűsített, csak a fontos adatokat megjelenítése topológia-térképként ábrázolja a hierarchiát.  

-   **Földrajzi nézet**: Ez a nézet a konfigurált helyeket megjelenítő földrajzi térképként ábrázolja a helyeket.  

A **Helyhierarchia** csomópontot használhatja az egyes helyek állapotának figyeléséhez, valamint a helyek közötti replikációs hivatkozások és azok külső tényezőkkel, például a földrajzi helyekkel való kapcsolatának figyeléséhez.  

Hely állapota és a helyek közötti hivatkozásra állapot replikálja a helyadatok és az nem globális adatként, mint amikor a Configuration Manager konzol csatlakozik a gyermek elsődleges helyek, mert nem tudja megtekinteni a hely- vagy hivatkozásállapotot a többi elsődleges helyhez vagy azok másodlagos gyermekhelyeihez. Például a több elsődleges helyet tartalmazó hierarchiában, ha a Configuration Manager konzol egy elsődleges helyhez csatlakozik, megtekintheti a másodlagos gyermekhelyek, az elsődleges hely és a központi adminisztrációs hely állapotát, de más a központi adminisztrációs hely alá a hierarchia-csomópont állapotát nem látható.  

 A **Beállítások konfigurálása** parancs használatával adhatja meg, hogyan jelenjen meg a helyhierarchia. Konfigurálható, hogy a **Helyhierarchia** más helyekre replikált csomópont, amikor a Configuration Manager konzol csatlakoztatva van egy helyhez.  

#### <a name="hierarchy-diagram"></a>Hierarchiadiagram:  
 A hierarchiadiagram topológiatérképen jeleníti meg a helyeket. Ebben a nézetben kijelölhet egy helyet, és megtekintheti az adott hely állapotüzeneteinek összefoglalását, a részletesebb szinteken megtekintheti az egyes állapotüzeneteket, és elérheti a helyekhez tartozó **Tulajdonságok** párbeszédpanelt.  

 Emellett akkor is az egérmutatót az adott objektum általános állapotának megtekintéséhez a helyek közötti hely vagy replikációs hivatkozásra. Mivel a replikációs hivatkozás állapota nem replikálja globálisan, a több elsődleges helyet tartalmazó hierarchiákban csatlakoznia kell a Configuration Manager konzolt a központi adminisztrációs hely a replikációs hivatkozások részletes adatait tekintheti meg helyek közötti.  

 A hierarchiadiagram a következő beállításokkal módosítható:  

-   **Csoportok**: Beállíthatja, hogy az elsődleges és másodlagos helyeken, amelyek hatására úgy változik meg a hierarchia diagram megjelenítése, hogy a helyek egy objektumként száma. Helyek egy objektumként van együtt, a helyek számát és egy magas szintű összegző állapotüzeneteit és a hely állapota megjelenik. A csoportok beállításai nincsenek hatással a földrajzi nézetre.  

-   **Kedvenc helyek**: Megadhatja az egyes helyeket kedvenc helyként. A kedvenc helyeket csillag ikon jelöli a hierarchiadiagramon. A kedvenc helyek mindig megjelennek, nincsenek csoportba foglalva, amikor csoportokat használ.  

#### <a name="geographical-view"></a>Földrajzi nézet:  
 A földrajzi nézet földrajzi térképen jeleníti meg, hogy hol találhatók az egyes helyek. Csak azok a helyek jelennek meg, amelyeknél megadta az elhelyezkedésüket. Amikor kijelöl egy helyet ebben a nézetben, megjelennek a szülő- vagy a gyermekhelyekre mutató replikációs hivatkozásai. A hierarchiadiagram nézettel ellentétben ebben a nézetben nem jelenítheti meg a helyek állapotüzeneteit és a replikációs hivatkozások adatait.  

> [!NOTE]  
>  A földrajzi nézet használatához a számítógép, amelyhez a Configuration Manager konzol csatlakozik a rendelkeznie kell az Internet Explorer telepítve, és érhetik el a Bing térképekhez a HTTP protokoll használatával.  

A földrajzi nézet a következő beállításokkal módosítható.  

-   **Hely elhelyezkedése**: Megadhatja az egyes helyek földrajzi elhelyezkedését. Ehhez olyan adatokat adhat meg, mint a cím vagy a város, valamint a szélességi és a hosszúsági koordinátákkal is meghatározhatja a földrajzi helyet. Ha például a Washington állambeli Redmond földrajzi helyét szeretné szélességi és hosszúsági koordinátákkal meghatározni, az elhelyezkedést az **N 47 40 26,3572 W 122 7 17,4432** értékkel adhatja meg. Nem kell megadnia a hosszúság vagy a szélesség fok, perc vagy másodperc szimbólumait. A Configuration Manager a Bing Maps használatával jeleníti meg az elhelyezkedést a földrajzi nézetben. Ezzel lehetősége van arra, hogy a hierarchiát a földrajzi elhelyezkedése alapján tekintse meg, így könnyebben észreveheti az olyan regionális szintű problémákat, amelyek hatással lehetnek egyes helyekre vagy a helyek közötti replikációra.  

     A földrajzi hely megadásakor a **Hely** mező használatával keresheti meg a hierarchia meghatározott helyét. Jelölje ki a helyet, és írja be az elhelyezkedést a városnév vagy utcacím megadásával a **Hely** oszlopban. A Configuration Manager a Bing Maps használatával oldja fel a helyet.  

###  <a name="BKMK_MonitorRepLinksAndStatuss"></a> Az adatbázis-replikációs hivatkozások és a replikáció állapotának figyelése  
 A **Figyelés** munkaterület **Helyhierarchia** csomópontjából elérhető magas szintű adatok mellett. Az adatbázis-replikáció adatait is figyelheti a **Figyelés** munkaterület **Adatbázis replikálása** csomópontjának használatakor. Az a **adatbázis-replikáció** figyelheti a helyek, és a inicializálási és replikálási adatainak a helyen, amelyhez a Configuration Manager konzol csatlakoztatva van a replikációs csoportok közötti replikációs hivatkozások állapota.  

> [!TIP]  
>  Az **Adatbázis replikálása** csomópont az **Adminisztráció** munkaterület **Hierarchiakonfiguráció** csomópontjában is megjelenik, de itt nem tekintheti meg az adatbázis-replikációs hivatkozások replikációs állapotát.  

####  <a name="BKMK_MonitorReplicationLinks"></a> Replikációs hivatkozás állapota  
A helyek közötti adatbázis-replikáció több, replikációs csoportnak nevezett adatkészlet replikációját jelenti. Mindegyik replikációs csoporthoz különböző replikációs prioritások tartoznak. Alapértelmezés szerint a replikációs csoportok által tartalmazott adatok és a replikáció gyakorisága nem változtatható meg.  

 Amikor a replikációs hivatkozás aktív, és nem sikertelen vagy csökkentett teljesítményű az állapota, minden replikációs csoport replikálása időben végrehajtható. Ha egy vagy több replikációs csoport esetében nem sikerül befejezni a replikálást a várt időtartamon belül, a hivatkozás állapota csökkentett teljesítményűre vált. A csökkentett teljesítményű hivatkozások továbbra is működőképesek, de célszerű figyelnie ezeket a hivatkozásokat, hogy ellenőrizze, visszaállnak-e az aktív állapotra, vagy meg kell vizsgálnia, hogy nem történt-e további teljesítménycsökkenés, illetve replikációs hiba.  

 Minden replikációs hivatkozáshoz megadhatja, hogy sikertelen replikáció esetén a replikációs csoportok hány alkalommal próbálkozhatnak újra, mielőtt a hivatkozás állapota csökkentett teljesítményűre vagy sikertelenre vált. Ha az összes csoport közül csak egy replikációs csoport esetében sikertelen a replikáció, a hivatkozás állapota akkor is csökkentett teljesítményűre vagy sikertelenre vált emiatt az egy csoport miatt, amelynél a megadott számú kísérlet végrehajtásával sem sikerült végrehajtani a replikációt. A replikációs küszöbértékekkel kapcsolatban lásd az [Adatátvitel a System Center Configuration Manager helyei között témakör](../../../core/servers/manage/data-transfers-between-sites.md) című témakör [Az adatbázis-replikáció küszöbértékei](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) című szakaszát.  

 A következő táblázatban található információ segítségével tekintheti át a replikációs hivatkozások olyan állapotát, amely további vizsgálatot igényel.  

|Hivatkozás leírása|További információ|  
|----------------------|----------------------|  
|**Aktív hivatkozás**|Nem észlelhető probléma, és működik a kommunikáció a hivatkozáson keresztül.|  
|**Csökkentett teljesítményű hivatkozás**|A replikáció működik, de legalább egy replikációs objektumnál vagy csoportnál késés van. Figyelje az ilyen állapotú hivatkozásokat, és ellenőrizze, hogy a hivatkozáshoz tartozó helyek adataiban nem láthatók-e problémára utaló jelek.<br /><br /> A hivatkozások akkor is csökkentett állapotúként jelenhetnek meg, amikor a replikált adatokat megkapó hely nem tudja gyorsan véglegesíteni az adatokat az adatbázisban. Ez nagy mennyiségű adat replikálásakor fordulhat elő. Ha például nagy mennyiségű számítógépre telepít egy szoftverfrissítést, eltarthat egy ideig, amíg a hivatkozás szülőhelye fel tudja dolgozni a replikált adatokat. A szülőhelyen keletkezett feldolgozási késedelem a hivatkozás csökkentett teljesítményű állapotra váltását eredményezheti, amíg a szülőhely fel nem tudja dolgozni a hátralékos adatokat.|  
|**Sikertelen hivatkozás**|A replikáció nem működik. Lehetséges, hogy a replikációs hivatkozás beavatkozás nélkül helyreáll. A Replication Link Analyzer eszköz használatával vizsgálhatja meg a hivatkozáson keresztül végrehajtott replikációt, és megoldhatja az esetleges problémákat.<br /><br /> Ez az állapot a fizikai hálózat hibájára is utalhat a replikációs hivatkozáshoz tartozó szülőhely és gyermekhely között.|  

 Amikor a szülőhelyen folyamatban van egy új szervizcsomagra történő frissítés, és a gyermekhelyről ellenőrzi a hivatkozás állapotát, az állapot aktívként jelenik meg. A frissítés befejeződése után – ha gyermekhely és a szülőhely szervizcsomagja azonos – a hivatkozás állapota aktívként jelenik meg a szülőhelyről megtekintve, és konfigurálás alatt állónak a gyermekhelyről megtekintve.  

####  <a name="BKMK_MonitorReplicationStatus"></a> Replikáció állapota  
 A **Figyelés** munkaterület **Adatbázis replikálása** csomópontját használva tekintheti meg a replikációs hivatkozások állapotát, valamint a replikációs hivatkozáshoz tartozó helyeken lévő helyadatbázis adatait. A replikációs csoportok adatait is megtekintheti. Az adatok megtekintéséhez jelölje ki a kívánt replikációs hivatkozást, majd válassza a megtekinteni kívánt replikációs állapotnak megfelelő lapot. A következő rész tartalmazza a replikációs állapot egyes lapjainak ismertetését.  

 **Összefoglalás**  
 Itt tekintheti meg a hivatkozáshoz tartozó két hely közötti helyadat- és globálisadat-replikációval kapcsolatos általános adatokat.  

 A **Korábbi forgalmi adatok jelentéseinek megtekintése** elemre kattintva megjelenítheti a replikációs hivatkozáson keresztül végrehajtott replikáció által használt hálózati sávszélesség adatait tartalmazó jelentést.  

 **Szülőhely**  
 A replikációs hivatkozáshoz tartozó szülőhely esetében az adatbázis következő adatait tekintheti meg:  

-   Az SQL Server tűzfalportjai  

-   Szabad lemezterület  

-   Az adatbázisfájlok helye  

-   Tanúsítványok  

**Gyermekhely**  
 A replikációs hivatkozáshoz tartozó gyermekhely esetében az adatbázis következő adatait tekintheti meg:  

-   Az SQL Server tűzfalportjai  

-   Szabad lemezterület  

-   Az adatbázisfájlok helye  

-   Tanúsítványok  

**Inicializálás részletei**    
 Itt tekintheti meg a replikációs kapcsolaton keresztül replikált replikációs csoportok inicializálási adatait. Ezen információ alapján állapíthatja meg, hogy a replikált adatok inicializálása folyamatban van-e vagy sikertelen-e.  

 Ezenkívül azt is megállapíthatja, hogy a helyek együttműködési módban vannak-e. Használja az együttműködési módot lép fel, amikor az alárendelt hely számára nem Configuration Manager azonos verzióját a szülőhely.  

**Replikálás részletei**    
 Az ezen a kapcsolaton keresztül replikálásra kerülő egyes replikációs csoportoknál nézze meg a replikálás állapotát. Ez segítséget nyújt a problémák vagy adott adatok replikálási késésének azonosításához, valamint az adott kapcsolatnál az adatbázis-replikálás megfelelő küszöbértékeinek meghatározásához. Az adatbázis-replikálás küszöbértékeivel kapcsolatban lásd az [Adatátvitel a System Center Configuration Manager helyei között](../../../core/servers/manage/data-transfers-between-sites.md) című témakör [Az adatbázis-replikáció küszöbértékei](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) című szakaszát.  

> [!TIP]  
>  A helyadatokhoz tartozó replikációs csoportokat csak az alárendelt helyről küldi a rendszer a fölérendelt helyre. Globális adatok replikációs csoportjait mindkét irányban replikálja a rendszer.  

###  <a name="BKMK_RLA"></a> A Replication Link Analyzer áttekintése  
 A Configuration Manager tartalmaz **Replication Link Analyzer** amelyet replikálási problémák elemzéséhez és megoldásához használhat. A Replication Link Analyzer segítségével javíthatja a replikálási kapcsolat hibáit, ha sikertelen a replikálás, illetve ha leáll a replikálás működése, de a művelet ezt még nem jelentette. A Replication Link Analyzer a (a hibánál a replikálás iránya lényegtelen) Configuration Manager hierarchiájában szereplő következő számítógépek közötti replikálási problémák megoldásához használható:  

-   A helykiszolgáló és a helyadatbázis-kiszolgáló között.  

-   Egy hely Helyadatbázis-kiszolgáló és egy másik hely Helyadatbázis-számítógépe (helyek közötti replikálás).  

A Replication Link Analyzer vagy a Configuration Manager konzolon vagy a parancssorból futtatható:  

-   A Configuration Manager konzol futtatása: A a **figyelés** munkaterületet, kattintson a **adatbázis-replikáció** csomópont, jelölje ki a replikálási kapcsolatot, hogy meg szeretné tudni, majd a a **adatbázis-replikáció** csoportba az a **Home** lapon jelölje be **Replication Link Analyzer**.  

-   Futtassa a parancssorból, írja be a következő parancsot: **%path%\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManager.ReplicationLinkAnalyzer.Wizard.exe &lt;forrás helykiszolgáló teljes Tartományneve\> &lt;cél helykiszolgáló teljes Tartományneve\>**  

A Replication Link Analyzer a futtatáskor diagnosztikai szabályok és ellenőrzések sorozatának használatával észleli a problémákat. Az eszköz futása közben megtekintheti az azonosított problémákat. Ha egy problémánál ismertek a megoldására szolgáló utasítások, ezek megjelennek. Ha a Replication Link Analyzer automatikusan javítani tudja a hibát, ezt a lehetőséget is látja a felhasználó. A Replication Link Analyzer befejezése után a következő XML formátumú jelentésbe és egy naplófájlt az eszközt futtató felhasználó asztalán menti az eredményeket:  

-   ReplicationAnalysis.xml  

-   ReplicationLinkAnalysis.log  

A Replication Link Analyzer a futás közben bizonyos problémák megoldásakor leállítja a következő szolgáltatásokat, majd a javítás befejezése után újraindítja ezeket:  

-   SMS_SITE_COMPONENT_MANAGER  

-   SMS_EXECUTIVE  

Ha a Replication Link Analyzer nem tudja végrehajtani a javítást, ellenőrizze a helykiszolgálót, és indítsa újra ezeket a szolgáltatásokat, ha le vannak állítva.  

A sikeres és a sikertelen vizsgálati és javítási műveletek a naplóba kerülnek, így olyan további részletek ismerhetők meg, amelyek nem jelennek meg az eszköz felületén.  

**A Replication Link Analyzer használatának előfeltételei:**  

-   A Replication Link Analyzer futtatásához használt fióknak helyi rendszergazdai jogosultságokkal kell rendelkezni a replikálási kapcsolatban szereplő minden számítógépen. A fióknak nincs szüksége egy adott szerepkör alapú felügyelet biztonsági szerepkört. Ezért hozzáféréssel rendelkező rendszergazda felhasználó a **adatbázis-replikáció** csomópont futtathatja az eszközt a Configuration Manager konzolon, vagy a minden számítógéphez megfelelő jogosultsággal rendelkező rendszergazda futtathatja az eszközt a parancssorba.  

-   A Replication Link Analyzer futtatásához használt fióknak rendszergazdai (sysadmin) jogosultságokkal kell rendelkezni a replikálási kapcsolatban szereplő minden SQL Server adatbázishoz.  

**A Replication Link Analyzer ismert problémái:**  

-   A System Center Configuration Manager 1511-es verzió kiadástól kezdve a replication link analyzer állít elő, frissített a System Center 2012 Configuration Manager elsődleges helyek SQL Server Service Broker tanúsítvány által jelzett hibákat. A tanúsítványok verziójában bevezetett változások miatt, amelynek még nem frissített a Replication Link Analyzer 1511-es. Ezek a hibák nyugodtan figyelmen kívül hagyhatók.  

###  <a name="BKMK_ProcsforMonitoringReplication"></a> Az adatbázis-replikáció figyelésének eljárásai  

##### <a name="to-monitor-high-level-site-to-site-database-replication-status"></a>Magas szintű hely-hely adatbázis-replikáció állapotának figyelése    
1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen kattintson a **Helyhierarchia** elemre a **Hierarchiadiagram** nézet megjelenítéséhez.  

3.  Tartsa rövid ideig az egérmutatót a két helyet elválasztó vonalon: ekkor megtekintheti a globális és a helyadatok replikálásának állapotát ezeknél a helyeknél.  

##### <a name="to-monitor-the-replication-status-for-a-replication-link"></a>Replikálási kapcsolat replikálási állapotának figyelése    
1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen kattintson az **Adatbázis-replikáció**csomópontra, majd jelölje ki a figyelni kívánt kapcsolathoz tartozó replikálási kapcsolatot. Ezután a munkaterületen a megfelelő lapon megtekintheti az adott kapcsolatnál a replikálási állapot különféle részletes adatait.  

