---
title: "Adatok áttelepítése |} Microsoft Docs"
description: "Útmutató a forráshierarchia adatok átvitele a System Center Configuration Manager célhierarchiába."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf014eb0-f8c2-4d37-b8d7-368d63a10b89
caps.latest.revision: 11
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a8959c72608a1531fb323176c33a848a4a669b1c
ms.openlocfilehash: dface33392c2a2a662522656eabf0936b52b28fc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="migrate-data-between-hierarchies-in-system-center-configuration-manager"></a>Adatok áttelepítése a System Center Configuration Manager hierarchiái között

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Áttelepítési vihet át adatokat a támogatott forráshierarchiából, a System Center Configuration Manager célhierarchiába.  Amikor telepít át adatokat a forráshierarchia:  

-   Adatelérés azokból a helyadatbázisokból a forrási infrastruktúrában azonosítható, és majd átviszi ezeket az adatokat az aktuális környezetébe.  

-   Áttelepítés nem módosítja az adatokat a forráshierarchiában, de ehelyett felderíti az adatokat és tárolja a másolatukat a célhierarchia adatbázisában.  

Az áttelepítési stratégia tervezésekor vegye figyelembe a következőket:  

-   A System Center Configuration Manager telepíthet át egy meglévő Configuration Manager 2007 SP2-infrastruktúra.  

-   A forráshelyről áttelepítheti a támogatott adatok egy részét vagy az összes adatot is.  

-   Az adatokat egyetlen forráshelyről a célhierarchia több különböző helyére is áttelepítheti.  

-   Az adatokat több forráshelyről a célhierarchia egyetlen helyére is áttelepítheti.  

##  <a name="BKMK_MigrationConcepts"></a> Áttelepítési fogalmak  
 A következő fogalmakat és szakkifejezéseket tartalmazza, ha áttelepítést használ léphetnek fel.  

|Fogalom vagy kifejezés|További információ|  
|---------------------|----------------------|  
|Forráshierarchia|A hierarchia, amely a Configuration Manager támogatott verzióját futtatja, és az áttelepíteni kívánt adatokat tartalmaz. Áttelepítési beállításakor a forráshierarchia azonosította a forráshierarchia legfelső szintű hely megadásakor. A forráshierarchia megadása után a célhierarchia legfelsőbb szintű helye gyűjti az adatokat a kijelölt forráshely adatbázisából, hogy beazonosítsa az áttelepíthető adatokat.<br /><br /> További információkért lásd: [Forráshierarchiák](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Hierarchies) a [a System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Forráshelyek|Azok a helyek a forráshierarchiában, amelyekben vannak a célhierarchiába áttelepíthető adatok.<br /><br /> További információkért lásd: [Forráshelyekről](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Sites) a [a System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Célhierarchia|A System Center Configuration Manager hierarchia, ahová a migrálás importálja a forráshierarchia adatait.|  
|Adatgyűjtés|A forráshierarchiában lévő azon információk azonosításának folyamata, amelyek áttelepíthetők a célhierarchiába. A Configuration Manager ellenőrzi a forráshierarchiát, hogy felismerje a forráshierarchiában, korábban már áttelepített, és érdemes frissíteni fogja a célhierarchiában lévő adatok megváltozását ütemezés szerint.<br /><br /> További információkért lásd: [adatgyűjtési](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering) a [a System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Áttelepítési feladatok|Adott objektumok konfigurálása az áttelepítéshez, majd ezen objektumok célhierarchiába történő áttelepítésének kezelése.<br /><br /> További információkért lásd: [egy feladat stratégiájának tervezése a System Center Configuration Managerben](../../core/migration/planning-a-migration-job-strategy.md)|  
|Ügyfélszoftveri áttelepítés|Az ügyfélszoftverek által használt információk átvitele a forráshelyi adatbázisból a célhierarchia adatbázisába. Ezt az áttelepítést aztán az eszközökön az ügyfélszoftvernek a célhierarchia ügyfélszoftverének verziójára frissítése követi.<br /><br /> További információk: [Ügyfélszoftverek áttelepítési stratégiájának tervezése a System Center Configuration Managerben](../../core/migration/planning-a-client-migration-strategy.md).|  
|Megosztott terjesztési pontok|A forráshierarchia azon terjesztési pontjai, amelyek az áttelepítés idején a célhierarchiával vannak megosztva.<br /><br /> Az áttelepítés idején a célhierarchiában a helyekhez hozzárendelt ügyfelek beszerezheti a tartalmat a megosztott terjesztési pontokról.<br /><br /> További információkért lásd: [megosztja a terjesztési pontokat a forrás- és Célhierarchiák között](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) a [a System Center Configuration Managerben tartalom központi telepítési stratégiájának tervezése](../../core/migration/planning-a-content-deployment-migration-strategy.md).|  
|Áttelepítés figyelése|Az áttelepítési tevékenységek figyelési folyamata. Áttelepítési folyamat és annak sikeressége az figyelheti a **áttelepítési** csomópontja a **felügyeleti** munkaterületen.<br /><br /> További információkért lásd: [a System Center Configuration Managerben az áttelepítési tevékenység figyelésének tervezése](../../core/migration/planning-to-monitor-migration-activity.md).|  
|Adatgyűjtés leállítása|A forrás helyeiről történő adatok gyűjtési folyamatának leállítása. Többé már nem kell áttelepíteni a forráshierarchiából adatokat, vagy ha fel szeretné függeszteni áttelepítési tevékenységeket, beállíthatja a célhierarchiában az leállította az adatgyűjtést a forráshierarchiában.<br /><br /> További információkért lásd: [adatgyűjtési](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering) a [a System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Áttelepítési adatok törlése|A forráshierarchiából történő áttelepítés befejezése úgy, hogy eltávolítja az áttelepítésre vonatkozó információkat a célhierarchia adatbázisából.<br /><br /> További információ: [Áttelepítés befejezésének megtervezése a System Center Configuration Managerben](../../core/migration/planning-to-complete-migration.md).|  

## <a name="typical-workflow-for-migration"></a>Áttelepítés általános munkafolyamata  
Az áttelepítési munkafolyamat beállítása:

1.  Adja meg a támogatott forráshierarchiát.  

2.  Állítsa be az adatgyűjtést. Az adatgyűjtés lehetővé teszi, hogy a Configuration Manager információt azokról az adatokról, amelyek áttelepíthetők a forráshierarchiából gyűjtendő.  

     A Configuration Manager automatikusan gyűjti az adatokat egy egyszerű ütemezés szerint meg addig, amíg az adatgyűjtési folyamat ismétlődik. Alapértelmezés szerint az adatgyűjtési folyamat négy óránként ismétlődik, hogy a Configuration Manager azonosíthassa az adatok megváltozását abban a forráshierarchiában, amelyiket áttelepíteni kívánt. Adatgyűjtésre szükség van a terjesztési pontoknak a forráshierarchiából a célhierarchia részére történő megosztáshoz is.  

3.  Hozzon létre áttelepítési feladatokat az adatoknak a forráshierarchiából a célhierarchiába áttelepítéséhez.  

4.  Az adatgyűjtési folyamat bármikor leállítható az **Adatgyűjtés leállítása** paranccsal. Amikor leállítja az adatgyűjtést, a Configuration Manager nem figyeli a forráshierarchiában lévő adatok, és többé nem osztja meg terjesztési pontokat a forrás- és Célhierarchiák között. Ezt a műveletet rendszerint olyankor használja, ha többé nem tervezi az adatok áttelepítését vagy a forráshierarchia megosztását.  

5.  Miután az adatgyűjtés a forráshierarchia összes helyén leállt, az áttelepítési adatokat törölheti is az **Áttelepítési adatok törlése** paranccsal. Ez a parancs törli a célhierarchia adatbázisából a forráshierarchiából történő áttelepítésre vonatkozó előzményi adatokat.  

Miután telepít át adatokat a Configuration Manager forráshierarchiájában, hogy Ön többé nem fog használni a környezete kezeléséhez, leszerelheti a forrás- és infrastruktúra.  

##  <a name="BKMK_MigrationScenarios"></a> Áttelepítési forgatókönyvek  
 A Configuration Manager az alábbi áttelepítési forgatókönyveket támogatja.  

> [!NOTE]  
>  A kibővítése olyan hierarchiává, amely rendelkezik egy önálló helyet központi adminisztrációs hellyel rendelkező hierarchiává nem kategorizálható áttelepítésként. További információ a hierarchia kibővítéséről: [kibővít egy önálló elsődleges helyet](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) a [helyek telepítése a telepítővarázsló segítségével](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  

### <a name="migration-from-configuration-manager-2007-hierarchies"></a>Áttelepítés a Configuration Manager 2007 hierarchiáiból  
 Ha áttelepítés használatával adatok áttelepítése a Configuration Manager 2007, a létező hely infrastruktúrájára befektetéseit karbantartása, és a következő előnyöket:  

|Előny|További információ|  
|-------------|----------------------|  
|Helyadatbázisi továbbfejlesztések|A System Center Configuration Manager adatbázisa teljes Unicode támogatással rendelkezik.|  
|Adatbázisok replikálása a helyek között|A System Center Configuration Manager replikációs Microsoft SQL Server alapul. Ez javítja a helyek közötti adatátvitelt.|  
|Felhasználó központú felügyelet|A System Center Configuration Manager felügyeleti feladatok fókuszában a felhasználók. Egy szoftver terjeszthető egy felhasználó részére akkor is, ha az adott felhasználó eszközének neve nem ismert. Emellett a System Center Configuration Manager lehetőséget ad a felhasználók milyen szoftver telepítve van az eszközeiket, és ha a szoftver telepítve van-e több ellenőrzést.|  
|A hierarchia egyszerűsítése|A System Center Configuration Managerben, a központi felügyeleti hely típusa és az elsődleges és másodlagos helyek viselkedésének változásai lehetővé teszik olyan egyszerűbb Helystruktúra felépítését, amelyek kevesebb sávszélességet használnak, és kevesebb kiszolgálót igényelnek.|  
|Szerepköralapú adminisztráció|A System Center Configuration Manager központi biztonsági modellje kínál hierarchiára kiterjedő olyan biztonságot és felügyeletet, amely megfelel az irányítási és üzletviteli követelményeiknek.|  

> [!NOTE]  
>  A System Center 2012 Configuration Manager először bevezetett tervezési módosítások, miatt a Configuration Manager 2007-infrastruktúrát a System Center Configuration Manager nem tudja frissíteni. Helyszíni frissítés a System Center 2012 Configuration Manager a System Center Configuration Manager támogatott.  

### <a name="migration-from-configuration-manager-2012-or-another-system-center-configuration-manager-hierarchy"></a>Áttelepítés Configuration Manager 2012- vagy más System Center Configuration Manager-hierarchiából  
 Folyamata az áttelepítéshez a System Center 2012 Configuration Manager vagy a System Center Configuration Manager hierarchiából adatok megegyezik. Ez magában foglalja az áttelepítés adatok több forráshierarchiából egyetlen célhierarchiába, amikor a vállalat lekérdezi a Configuration Manager által kezelt már további erőforrások, például. Ezen felül áttelepítheti az adatokat egy tesztkörnyezetből a Configuration Manager az üzemi környezetben. Ez lehetővé teszi a Configuration Manager tesztkörnyezetben befektetéseit karbantartása.  

## <a name="additional-topics-for-migration"></a>Kiegészítő témakörök az áttelepítéshez:  

-   [System Center Configuration Manager az áttelepítés tervezése](../../core/migration/planning-for-migration.md)  

-   [Forráshierarchiák és Forráshelyek System Center Configuration Manager áttelepítéshez](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

-   [System Center Configuration Managerben történő áttelepítés műveletei](../../core/migration/operations-for-migration.md)  

-   [Biztonság és adatvédelem a System Center Configuration Manager áttelepítési](../../core/migration/security-and-privacy-for-migration.md)  

## <a name="see-also"></a>Lásd még:  
 [Ismerkedés a System Center Configuration Managerben](../../core/servers/deploy/start-using.md)

