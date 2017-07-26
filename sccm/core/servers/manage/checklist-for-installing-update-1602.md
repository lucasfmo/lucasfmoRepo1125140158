---
title: "Ellenőrzőlista a 1602-es |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager 1511-es verzió 1602-es verzióra frissítés előtt elvégzendő műveleteket."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: 13
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3e0de56b7a592b105e6a61b3d6654b1d0142584d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1602-for-system-center-configuration-manager"></a>Ellenőrzőlista a System Center Configuration Manager 1602. frissítésének telepítéséhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager 1511-es verzió frissítése a 1602-es verzióra, előtt tekintse át az alábbi információk és a frissítés megkezdése előtt elvégzendő műveleteket a feladatlista.  

 **Az 1602-es frissítés telepítéséről:**  

 Az 1602-es frissítést csak a hierarchia legfelső szintű helyére lehet telepíteni. Ez azt jelenti, hogy elindította a telepítés a központi adminisztrációs helyről, ha nincs fiókja, vagy az önálló elsődleges helyről.  

-   A gyermek elsődleges helyek automatikusan telepítik a frissítést, a központi adminisztrációs hely befejezi a frissítés telepítése után. Karbantartási időszakokkal szabályozhatja is használhatja, amikor egy helyet telepíti a frissítéseket. Az 1602-es frissítés kezdve karbantartási időszakot átnevezték *szolgáltatás windows*. További információkért lásd: [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows).  

-   Az elsődleges szülőhely befejezi a frissítés telepítése után a Configuration Manager konzolon a másodlagos helyeket manuálisan kell frissíteni. A másodlagos Helykiszolgálók automatikus frissítések nem támogatottak.  

Amikor a helykiszolgáló telepíti a frissítést, a helykiszolgálón, valamint azokat, amelyeket a távoli számítógépekre automatikusan telepített telepített helyrendszerszerepkörök módosul. A frissítés telepítése előtt győződjön meg arról, hogy mindegyik helyrendszer-kiszolgáló megfelel-e az új, frissített verzióval rendelkező műveleteket esetleges új előfeltételeinek.  

Az első használatakor a Configuration Manager konzol frissítés befejeződését követően kérni fogja, hogy a konzol frissítését. Ehhez futtassa a Configuration Manager telepítőt azon a számítógépen, amelyre a konzol, és a konzol frissítése lehetőséget. Azt javasoljuk, hogy ne halogassa a frissítésnek a konzolra való telepítését.  

 **Ellenőrzőlista:**  

 **Győződjön meg arról, hogy fut-e a System Center Configuration Manager támogatott verziója az összes helyen:**  A hierarchia mindegyik helykiszolgálóján futtatásához a System Center Configuration Manager 1602-es frissítés telepítésének megkezdése előtt 1511-es verzió.  

 **Tekintse át a Microsoft .NET-verziót a helyrendszer-kiszolgálókon telepítve:** Amikor egy helyre települ az 1602-es frissítést, Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját minden olyan számítógépen, amely futtatja a következő helyrendszer-szerepkörök közül (Ha a .NET-keretrendszer 4.5-ös vagy újabb verziója nincs telepítve):  

-   Beléptetési proxypont  

-   Beléptetési pont  

-   Felügyeleti pont  

-   Szolgáltatáskapcsolódási pont  

A telepítést a helyrendszer-kiszolgáló helyezhetik újraindítás függőben állapotba, és a Configuration Manager összetevőállapot-megjelenítője jelentés hibát. Emellett a kiszolgálón futó .NET-alkalmazások tapasztalhat véletlen hibákat, a kiszolgáló újraindításáig.  

 További információk: [Hely és helyrendszer előfeltételei](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Ellenőrizze a hely és a hierarchia állapotát, és ellenőrizze, hogy nincsenek-e megoldatlan problémák:** Mielőtt frissít egy helyet, oldja meg a működéssel kapcsolatos összes problémát a helykiszolgálón, a Helyadatbázis-kiszolgáló és a helyrendszerszerepkörök, amelyek a távoli számítógépekre telepített helyrendszerszerepkörökben. A megoldatlan működési problémák megakadályozhatják a helyek frissítését.  

További információkért lásd: [A riasztások és az állapotrendszer használata a System Center Configuration Managerben](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Tekintse át a fájlt és az adatok helyek közötti replikáció:**  Győződjön meg arról, hogy a fájl és a helyek közötti adatbázis-replikáció működési és aktuális. Késések vagy elmaradások vagy előfordulhat, hogy egy smooth, sikeres frissítést.    

Az adatbázis-replikáció esetében a Replication Link Analyzer segítségével is megoldhatja a problémákat a frissítés elkezdése előtt.    

 További információkért lásd: [kapcsolatos a Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) a a [figyelő hierarchia és replikációs infrastruktúra a System Center Configuration Managerben](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) témakör.  

 **Az operációs rendszer összes fontos frissítését telepíti a számítógépekre, a webhely üzemeltetésére, a Helyadatbázis-kiszolgáló és a távoli helyrendszerszerepköröket tartalmazzák:** Mielőtt telepít egy frissítést a Configuration Manager számára, telepítse minden érintett helyrendszerre a fontos frissítéseket. Ha valamelyik telepített frissítés újraindítást igényel, indítsa újra a megfelelő számítógépeket, mielőtt elkezdi a frissítés telepítését.  

 **Tiltsa le az adatbázis-replikák beállítása felügyeleti pontokhoz az elsődleges helyeken:** A Configuration Manager nem tud sikeresen frissíteni egy elsődleges helyet, amely egy adatbázis-replikát a felügyeleti pont is engedélyezve van. Tiltsa le az adatbázis-replikálást, mielőtt:  

-   A biztonsági mentést készít a helyadatbázisról az adatbázis-frissítés teszteléséhez.  

-   Egy frissítés telepítése a Configuration Manager számára.  

További információkért lásd: [a System Center Configuration Manager adatbázis-replikák beállítása felügyeleti pontokhoz](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Konfigurálja újra a hálózati terheléselosztást használó szoftverfrissítési pontokhoz:** A Configuration Manager nem tudja frissíteni a helyet, amely a szoftverfrissítési pontok futtatásához hálózati terheléselosztási (NLB) fürtöt használnak a.  Ha a szoftverfrissítési pontok NLB-fürtöt használ, a Windows PowerShell segítségével távolítsa el az NLB-fürt.    

 További információk: [Szoftverfrissítések tervezése a System Center Configuration Managerben](../../../sum/plan-design/plan-for-software-updates.md).  

 **Tiltsa le az összes helykarbantartási feladatot az egyes helyeken a hely a frissítés telepítésének időtartama:** Frissítések telepítése előtt tiltsa le a helykarbantartási feladatokat arra az időre, amíg a frissítés folyamatban. Ezeket a feladatokat tartalmazza (de nem kizárólag) a következők:  

-   Helykiszolgáló biztonsági mentése  

-   Elavult ügyfélműveletek törlése  

-   Elavult felderítési adatok törlése  

Ha egy helyadatbázis-karbantartási feladat fut a frissítés telepítése során, a frissítés telepítése sikertelen lehet. Mielőtt letilt egy feladatot, jegyezze fel az ütemezését, hogy a frissítés telepítése után visszaállíthassa a feladat konfigurációját.  

 További információkért lásd: [karbantartási feladatok a System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) és [hivatkozás tartozó karbantartási feladatokat a System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Hozzon létre egy biztonsági másolatot a helyadatbázisról a központi adminisztrációs helyen és elsődleges helyek:** Mielőtt frissít egy helyet, készítsen biztonsági másolatot a helyadatbázisról, hogy rendelkezik-e egy sikeres mentés vész-helyreállítási.   

További információkért lásd: [biztonsági mentés és helyreállítás a System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Biztonsági mentés testreszabott Configuration.mof-fájlba:** Ha testreszabott Configuration.mof-fájlba segítségével határozza meg, amely a hardverleltárral használt adatosztályokat, készítsen biztonsági másolatot a fájl a hely frissítése előtt. A frissítés után állítsa vissza a fájlt az 1602-es verzió webhelyekhez. Amikor frissít egy helyet, az aktuális fájl felülírja a fájlt eredeti (alapértelmezett) verzióját. A fájl használatáról további információk: [a System Center Configuration Managerben a Hardverleltár bővítése](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 **A legutóbbi Helyadatbázis biztonsági másolatán az adatbázis-frissítés teszteléséhez:** A System Center Configuration Manager központi adminisztrációs hely vagy elsődleges hely frissítése előtt tesztelje a Helyadatbázis frissítési folyamatát a Helyadatbázis másolatán.  

-   Mert amikor frissít egy helyet, a Helyadatbázis módosulhatnak, tesztelje a Helyadatbázis frissítési folyamatát.  

-   Bár a tesztadatbázison végzett frissítés nem szükséges, felderíthetők a frissítés előtt az éles adatbázist frissítené.  

-   A sikertelen adatbázis-frissítés működésképtelenné teheti a helyadatbázist, és előfordulhat, egy hely helyreállításával lehet működőképes állapotba hozni.  

-   Bár a Helyadatbázis meg van osztva a hierarchiában lévő helyek között, tervezze meg tesztelje az adatbázist minden érintett helyen, mielőtt frissíti azokat.  

-   Ha az adatbázis-replikákat használ a felügyeleti pontokhoz az elsődleges helyeken, tiltsa le a replikációt, mielőtt létrehozná a biztonsági mentést a helyadatbázisról.  

A Configuration Manager nem támogatja a másodlagos helyek biztonsági mentését és nem támogatja a másodlagos Helyadatbázis tesztelési célú frissítését.   
Az élesben használt helyadatbázison nem futnak a tesztadatbázison végzett frissítés. Ez frissíti a helyadatbázist, és működésképtelenné teheti a helyet. További információkért lásd: [2. lépés: A frissítés telepítése előtt az adatbázis-frissítés teszteléséhez](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) a **konzolon belüli frissítés telepítése előtt**.  

 **Ügyféltesztelés megtervezése:** Ha olyan frissítést telepít, amely frissíti az ügyfelet, tesztelheti, hogy új ügyfélfrissítés üzem előtti előtt telepíti, és az aktív ügyfelek frissítése.   

 Kihasználja ezt a beállítást, konfigurálnia kell a helyet az automatikus frissítésének támogatására a frissítés telepítésének megkezdése előtt éles üzem előtti használathoz. További információk: [Ügyfelek frissítése a System Center Configuration Managerben](../../../core/clients/manage/upgrade/upgrade-clients.md) és   
[Ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Tervezi, hogy karbantartási időszakokkal szabályozhatja Helykiszolgálók telepítésekor frissítések:** A karbantartási időszakok segítségével megadhatja egy adott időn belül, amely során a helykiszolgálóra frissítések telepítése. Ezzel kontrollálhatja, hogy mikor telepítsék a frissítést a hierarchiába tartozó helyek.   

Az 1602-es frissítés kezdve karbantartási időszakot átnevezték *szolgáltatás windows*. További információkért lásd: [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows).  

 **A telepítő előfeltétel-ellenőrzés futtatása:**  Az 1602-es frissítés telepítése előtt futtathatja az előfeltétel-ellenőrző egymástól függetlenül a frissítés telepítését. Ha a frissítés telepítése a helyen, az előfeltétel-ellenőrző ismét elindul.  

További információkért lásd: **3. lépés: Az előfeltétel-ellenőrzés futtatása frissítés telepítése előtt** a a [frissíti a System Center Configuration Manager](../../../core/servers/manage/updates.md) témakör.  

> [!IMPORTANT]  
>  Ha az előfeltétel-ellenőrző önállóan vagy egy frissítés telepítésének részeként fut, a folyamat frissíti néhány termék forrásfájlok helykarbantartási feladatokhoz használt. Ezért az előfeltétel-ellenőrző futtatásához, de előtte futtatása után az 1602-es frissítés telepítése, ha egy Helyadatbázis-karbantartási feladat végrehajtásához futtassa **Setupwfe.exe** (Configuration Manager telepítő) a CD-ről. Legújabb mappában található a helykiszolgálón.  

 **Helyek frissítése:** Most már készen áll a hierarchiában a frissítés telepítésének elindítása. Azt javasoljuk, hogy szeretné-e minden helyen munkaidőn kívülre a frissítés telepítése, amikor a frissítés és a műveletek újra kell telepítenie a hely összetevőinek és a helyrendszerszerepkörök telepítési folyamata hatással lesz a legalább az üzleti tevékenységre.

További információ: [A System Center Configuration Manager frissítései](../../../core/servers/manage/updates.md).  

## <a name="see-also"></a>További információ  
 [A System Center Configuration Manager frissítései](../../../core/servers/manage/updates.md)

