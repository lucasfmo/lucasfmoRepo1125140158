---
title: "Frissítés a System Center Configuration Manager |} Microsoft Docs"
description: "Ismerje meg, hogy egy sikeres frissítés futtatja a hely és a hierarchia, System Center 2012 Configuration Manager futtató lépéseit."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 9e58ab8dd892adf25429564adfd6f86849ddcbdf
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-to-system-center-configuration-manager"></a>Frissítés a System Center Configuration Managerre

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Futtatása helyben történő frissítést a System Center Configuration Manager hely és a System Center 2012 Configuration Manager futtató hierarchiát.  

 A System Center 2012 Configuration Manager alkalmazásra történő verziófrissítés előtt elő kell készítenie a helyeket, amelyek megkövetelik, hogy távolítsa el a meghatározott konfigurációk, amelyek megakadályozhatják a sikeres frissítést, és hajtsa végre a megfelelő frissítési sorrendet, ha több mint egy hely van szó.  

 > [!TIP]
 > Kezelése a System Center Configuration Manager-hely és hierarchia-infrastruktúra, a feltételek *frissítése*, *frissítése*, és *telepítése* három különböző fogalmi kört alkotnak használt... Minden kifejezéshez használatáról információkért lásd: [frissítés, frissítés és telepítés](/sccm/core/understand/upgrade-update-install).

##  <a name="bkmk_path"></a> Helyben végzett verzióváltási lépések  

**Frissítés 1702 verzióról**   
Ha verzió 1702 alapszintű verziót tartalmazó adathordozóról, a System Center Configuration Manager verziója 1702 teljes mértékben licencelt verzióra frissítheti a következő:   
-      A System Center Configuration Manager verziója 1702 próbaverziója
-      A System Center 2012 Configuration Manager Service Pack 1
-      A System Center 2012 Configuration Manager Service Pack 2
-      System Center 2012 R2 Configuration Manager
-      System Center 2012 R2 Configuration Manager Service Pack 1

**Frissítés 1606 verzióról**  
2016. December 15. az alapszintű verziót tartalmazó adathordozó verziójához 1606 újra lett kiadásra további frissítési forgatókönyvek támogatásához. Ebben a kiadásban támogatja a frissítést a System Center Configuration Manager verziója 1606 teljes mértékben licencelt verzióra a következő:  
-   A System Center Configuration Manager verziója 1606 próbaverziója
-   A kiadásra jelölt a System Center Configuration Managerben  
-   A System Center 2012 Configuration Manager Service Pack 1  
-   A System Center 2012 Configuration Manager Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager Service Pack 1  

2016. December 15-én előtt letöltött verziót 1606 alapszintű verziót tartalmazó adathordozó használatakor a teljes mértékben licencelt verzióra a System Center Configuration Manager verziója 1606 frissíthet csak a következő:
-   A System Center Configuration Manager verziója 1606 próbaverziója
-   A System Center 2012 Configuration Manager Service Pack 2
-   System Center 2012 R2 Configuration Manager Service Pack 1

<!-- Version 1511 has now dropped out of support
**Upgrade to version 1511**  
When you have version 1511 baseline media, you can upgrade the following to a fully licensed  version of System Center Configuration Manager version 1511:  
-   An evaluation install of System Center Configuration Manager version 1511
-   A release candidate install of System Center Configuration Manager  
-   System Center 2012 Configuration Manager with Service Pack 1  
-   System Center 2012 Configuration Manager with Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager with Service Pack 1  
-->


> [!TIP]  
>  Amikor frissít egy System Center 2012 Configuration Manager verziójából származó aktuális ág, valószínűleg létre tudja a frissítési folyamat egyszerűsítésére. További információkért tekintse át a következőket:  
>   
>  -   [A System Center Configuration Manager frissítései](../../../../core/servers/manage/updates.md)[Alapkonfiguráció és frissítési verziók](../../../../core/servers/manage/updates.md#bkmk_Baselines) szakasz  
>  -   [A CD-n. A System Center Configuration Manager legújabb mappa](../../../../core/servers/manage/the-cd.latest-folder.md)  

 **A következők nem támogatottak:**  
-   A System Center Configuration Manager Technical Preview verzióinak frissítése teljes mértékben licencelt verzióra nem támogatott.  A Technical Preview verzió csak a Technical Preview későbbi verziójára frissíthető.  

-   A Technical Preview áttelepítés teljes mértékben licencelt verzióra nem támogatott.  

##  <a name="bkmk_checklist"></a> Frissítési ellenőrzőlisták  
 A következő ellenőrzési listák alapján megtervezheti a sikeres frissítést a System Center Configuration Manager segítségével.  

### <a name="before-you-upgrade"></a>Frissítés előtti teendők  

**Tekintse át a System Center 2012 Configuration Manager környezetben** és a KB4018655 a problémák megoldásához: [Configuration Manager-ügyfelek újra öt óránként miatt újrapróbálkozási ismétlődő feladat, és szükségessé teheti az egy véletlen ügyfélfrissítést](https://support.microsoft.com/help/4018655).

**Győződjön meg arról, hogy az informatikai környezete megfelel-e a támogatott konfigurációk** , amelyek a System Center Configuration Manager verzióra frissítéshez szükséges:  

Tekintse át a helyrendszerszerepkörök működtetéséhez használt kiszolgálói operációs rendszereket:  

-   Egyes System Center 2012 Configuration Manager által támogatott régebbi operációs rendszerek nem támogatottak a System Center Configuration Manager által, és helyrendszer-szerepkörök a fenti operációs rendszerre kell helyezni vagy eltávolítja a frissítés előtt. Tekintse át a [támogatott operációs rendszerek a helyrendszer-kiszolgálókhoz](../../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md) dokumentációját.   
-   Az előfeltétel-ellenőrző a Configuration Manager nem ellenőrzi a helykiszolgálón vagy a távoli helyrendszeren helyrendszerszerepkörök előfeltételei  

Tekintse át az előfeltételeket minden olyan számítógépen, amelyen helyrendszerszerepkör működik.  

-   Például az operációs rendszerek központi telepítéséhez, a System Center Configuration Manager használ a Windows 10 Assessment and Deployment Kit (Windows ADK). A telepítő futtatása előtt le kell töltenie a Windows 10 ADK-t, és telepítenie kell azt a helykiszolgálón és minden olyan számítógépen, amelyen fut az SMS-szolgáltató példánya.  

Általános információ a támogatott platformokról és az előfeltétel-konfigurációkról: [Supported Configurations for System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md) (System Center Configuration Manager – támogatott konfigurációk).  

A Windows ADK használatával a Configuration Managerrel kapcsolatos információkért lásd: [infrastruktúrával kapcsolatos követelmények az operációs rendszer központi telepítéséhez a System Center Configuration Managerben](../../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

**Ellenőrizze a hely és a hierarchia állapotát, és ellenőrizze, hogy nincsenek-e megoldatlan problémák:**  
Mielőtt frissít egy helyet, oldja meg a működéssel kapcsolatos összes problémát a helykiszolgálón, a helyadatbázis kiszolgálóján és a távoli számítógépekre telepített helyrendszerszerepkörökben. A megoldatlan problémák megakadályozhatják a helyek frissítését.  

**Az operációs rendszer összes fontos frissítését telepíti a számítógépekre, a webhely üzemeltetésére, a Helyadatbázis-kiszolgáló és a távoli helyrendszerszerepköröket tartalmazzák:**  
Mielőtt frissít egy helyet, telepítse az összes kapcsolódó helyrendszer fontos frissítéseit. Ha valamelyik telepített frissítés újraindítást igényel, indítsa újra a megfelelő számítógépeket, mielőtt elkezdi a szervizcsomag-frissítés telepítését.  

További információkért lásd: [Windows Update](http://go.microsoft.com/fwlink/p/?LinkId=105851).  

**Távolítsa el a helyrendszerszerepköröket, a System Center Configuration Manager által nem támogatott:**  
A következő helyrendszerszerepkörök már nem használják a System Center Configuration Managerben, és a System Center 2012 Configuration Manager frissítése előtt el kell távolítani:  

-   Sávon kívüli felügyeleti pont  
-   Szolgáltatásállapot-érvényesítő pont  

**Tiltsa le az adatbázis-replikák beállítása felügyeleti pontokhoz az elsődleges helyeken:**  
A Configuration Manager nem tudja sikeresen frissíteni egy elsődleges helyet, amely egy adatbázis-replikát a felügyeleti pont is engedélyezve van. Tiltsa le az adatbázis-replikálást, mielőtt:  

-   Biztonsági másolatot készít a helyadatbázisról az adatbázis-frissítés teszteléséhez  
-   Frissíti a munkakörnyezeti helyet a System Center Configuration Managerben  

További információkért tekintse át a következőket:  
-   A System Center 2012 Configuration Manager:  [Adatbázis-replikák beállítása felügyeleti pontokhoz](https://technet.microsoft.com/library/hh846234.aspx)  
-   A System Center Configuration Manager: [A System Center Configuration Manager a felügyeleti pontok adatbázis-replikák](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md)  

**Konfigurálja újra a hálózati terheléselosztást használó szoftverfrissítési pontokhoz:**  
A Configuration Manager nem tudja frissíteni a helyet, amely a szoftverfrissítési pontok futtatásához hálózati terheléselosztási (NLB) fürtöt használnak.  

Ha NLB-fürtöket használ a szoftverfrissítési pontokhoz, a PowerShell használatával távolítsa el az NLB-fürtöt. (A System Center 2012 Configuration Manager SP1 kezdve volt a Configuration Manager konzolon nincs lehetőség NLB-fürt konfigurálása)  

**Tiltsa le az összes helykarbantartási feladatot az egyes helyeken az adott hely frissítésének időtartamára:**  
A System Center Configuration Manager rendszerre frissítés előtt tiltsa le a helykarbantartási feladatokat arra az időre, amíg a frissítés folyamatban. Ilyen letiltandó feladatok lehetnek például a következők:  

-   Helykiszolgáló biztonsági mentése  
-   Elavult ügyfélműveletek törlése  
-   Elavult felderítési adatok törlése  

Ha a frissítési folyamat közben fut egy helyadatbázis-karbantartási feladat, az a hely frissítésének sikertelenségét okozhatja.  

Mielőtt letilt egy feladatot, jegyezze fel az ütemezését, hogy a helyfrissítés befejezése után helyreállíthassa a feladat konfigurációját.  

További információ a helykarbantartási feladatokról:  

-   A System Center 2012 Configuration Manager:  [A Configuration Manager karbantartási feladatainak tervezése](https://technet.microsoft.com/library/gg712686.aspx)  
-   A System Center Configuration Manager:  [Útmutató a System Center Configuration Manager karbantartási feladatok](../../../../core/servers/manage/reference-for-maintenance-tasks.md)  

**Futtassa a telepítő előfeltétel-ellenőrzőjét**:  
Mielőtt frissít egy helyet, az **előfeltétel-ellenőrzőt** a telepítőtől függetlenül futtatva ellenőrizheti, hogy a hely megfelel-e az előfeltételeknek. Később amikor frissíti a helyet, az előfeltétel-ellenőrző ismét elindul.  

Az alapszintű verziót tartalmazó adathordozó a 2016. októberi kiadás 1606 verziót használja, ha a független előfeltétel-ellenőrzés kiértékeli a hely a frissítés az aktuális ág és a hosszú távú karbantartási ág (LTSB) a System Center Configuration kezelésére is. Néhány funkció nem támogatja a LTSB, mert a bejegyzéseket láthatja a *ConfigMgrPrereq.log* , amelyek a következőhöz hasonló:
 - INFORMÁCIÓ: A hely egy LTSB edition.
 - Nem támogatott helyrendszerszerepkör "Eszközintelligencia szinkronizálási pont" LTSB kiadásához;    Hiba történt;    A Configuration Manager azt észlelte, hogy telepítve van-e a "Eszközintelligencia szinkronizálási pont". Az eszközintelligencia szolgáltatás nem támogatott a LTSB-verziót. Folytatás előtt el kell távolítania az Eszközintelligencia szinkronizálási pont helyrendszer-szerepkör.

Ha azt tervezi, az aktuális ág frissítéséhez, a LTSB-kiadás hibák biztonságosan figyelmen kívül hagyható. Csak vonatkoznak, ha azt tervezi, hogy a LTSB frissítsen.

Később amikor futtatja a Configuration Manager telepítőjét hajtsa végre a frissítést, az Előfeltételek ellenőrzése futtatja újra és értékelje ki a helyet, a fiókiroda a System Center Configuration Manager úgy dönt, hogy telepíteni (aktuális ág vagy LTSB) alapján. Ha az aktuális ág frissítéséhez választja, a jelölőnégyzet nem támogatja a LTSB szolgáltatások futnak.

További információkért lásd: a [előfeltétel-ellenőrző](/sccm/core/servers/deploy/install/prerequisite-checker) és [lista az előfeltételként szükséges ellenőrzi a System Center Configuration Manager](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

**Előfeltételfájljait és újraterjeszthető fájljait a System Center Configuration Manager letöltése:**    
Használjon **a telepítő letöltési segédprogramja** letölteni a legújabb frissítéseket, előfeltételként szükséges újraterjeszthető fájlokat és nyelvi csomagokat a System Center Configuration Manager.  

További információ: [a telepítő letöltési segédprogramja](/sccm/core/servers/deploy/install/setup-downloader).  

**Tervezze meg a kiszolgáló és az ügyfelek nyelveinek felügyeletét**:  
Amikor frissít egy helyet, a helyfrissítés csak a frissítés során választott nyelvi csomagokat telepíti.  

-   A telepítő ellenőrzi a hely aktuális nyelvi beállításait, majd megkeresi az elérhető nyelvi csomagokat a korábban letöltött előfeltételfájlokat tároló mappában.  
-   Ezután elfogadhatja a kiszolgálóhoz és az ügyfelekhez kiválasztott nyelvi csomagokat, vagy a beállítások megváltoztatásával módosíthatja a támogatott nyelveket.  
-   Csak a telepítő futtatásakor elérhető (az előfeltételként szükséges fájlok letöltésével beszerzett) nyelvi csomagok választhatók ki.  

> [!NOTE]  
>  A System Center Configuration Manager-hely nyelvek engedélyezéséhez a System Center 2012 Configuration Manager nyelvi csomagjait nem használható.  

További információ a nyelvi csomagok: [nyelvi csomagokat a System Center Configuration Managerben](../../../../core/servers/deploy/install/language-packs.md).  

**Tekintse át a helyfrissítésekre vonatkozó szempontokat**:  
Amikor frissít egy helyet, néhány funkció és konfigurációs beállítás visszaáll az alapértelmezett értékére. Ezek és a kapcsolódó változások megértéséhez tekintse át a következő témakörben található információkat:  [A frissítéskor megfontolandó szempontok](#bkmk_considerations).  

**Hozzon létre egy biztonsági másolatot a helyadatbázisról a központi adminisztrációs helyen és elsődleges helyek:**  
Mielőtt frissít egy helyet, készítsen biztonsági mentést a helyadatbázisról, hogy legyen egy hibátlan biztonsági másolata, amelyet hiba esetén felhasználhat a helyreállításhoz.  

Lásd: [biztonsági mentés és helyreállítás a System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md).  

**Biztonsági mentés testreszabott Configuration.mof-fájlba**:  
Ha testreszabott Configuration.mof fájlt használ a hardverleltárral használt adatok definiálására, a hely frissítése előtt készítsen a fájlról biztonsági másolatot, majd a frissítés után állítsa vissza a fájlt a helyen. A fájl használatáról további információk: [a System Center Configuration Managerben a Hardverleltár bővítése](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

**Tesztelje a frissítési folyamatát a Helyadatbázis legfrissebb biztonsági másolatán:**  
Mielőtt frissíti a Configuration Manager egy központi adminisztrációs helyét vagy elsődleges helyét, próbálja ki a helyadatbázis frissítési folyamatát a helyadatbázis másolatán.  

-   Tesztelje a helyadatbázis frissítési folyamatát, mert amikor frissít egy helyet, előfordulhat, hogy módosítja a helyadatbázist  
-   Bár a tesztadatbázison végzett frissítés nem kötelező, segítségével felderíthetők a frissítés esetleges hibái az éles adatbázis frissítése előtt.  
-   A sikertelen adatbázis-frissítés működésképtelenné teheti a helyadatbázist, és előfordulhat, hogy csak a hely helyreállításával lehet működőképes állapotba hozni.  
-   Bár a helyadatbázis meg van osztva a helyek között a hierarchiában, tesztelje az adatbázist minden érintett helyen, mielőtt frissíti azokat.  
-   Ha adatbázis-replikákat használ a felügyeleti pontokhoz az elsődleges helyeken, tiltsa le a replikációt, mielőtt végrehajtja a helyadatbázis biztonsági mentését.  

A Configuration Manager nem támogatja a másodlagos helyek biztonsági mentését, sem a másodlagos Helyadatbázis tesztelési célú frissítését.  

A munkakörnyezeti helyadatbázis tesztelési célú frissítése nem támogatott. Ez frissíti a helyadatbázist, és működésképtelenné teheti a helyet.  

További információ: [A helyadatbázis frissítése teszteléshez](#bkmk_test).  

**Indítsa újra a helykiszolgálón és minden olyan számítógépen, amelyen helyrendszerszerepkör működik**:  
Erre azért van szükség, győződjön meg arról, hogy legyen függőben semmilyen művelet vagy az Előfeltételek korábban elindított telepítései közül frissítések, és egy a vállalatra jellemző belső folyamat.  

**Helyek frissítése**:  
Kezdve a hierarchia legfelső szintű helyen, futtassa a Setup.exe a System Center Configuration Manager forrás-adathordozóján.  

Miután a legfelső szintű helyeken befejeződött a frissítés, elkezdheti a gyermekhelyek frissítését. A helyek frissítését egyenként hajtsa végre, a következő hely frissítésének elkezdése előtt várja meg, amíg befejeződik az aktuális hely frissítése  

Amíg a hierarchiában lévő összes hely frissítése a System Center Configuration Manager, a hierarchia vegyes szervizcsomag-verziójú üzemmódban működik.  

A frissítéssel kapcsolatos információkért lásd: [helyek frissítésére](#bkmk_upgrade).  

### <a name="after-you-upgrade"></a>Frissítés utáni teendők  
**Frissítse a különálló Configuration Manager-konzol**:  
Alapértelmezés szerint amikor frissít egy központi adminisztrációs hely vagy elsődleges helyen, a telepítés is frissíti a Configuration Manager konzolt, hogy a helyrendszer-kiszolgálóra van telepítve. A többi számítógépen azonban kézzel kell frissítenie a konzolokat.  

> [!TIP]  
>  A frissítés megkezdése zárja be az egyes megnyitott konzolokat.  

További információ: [System Center Configuration Manager konzolok telepítése](../../../../core/servers/deploy/install/install-consoles.md).  

**Konfigurálja újra az adatbázis-replikák beállítása felügyeleti pontokhoz az elsődleges helyeken:**  
Ha adatbázis-replikákat használ a felügyeleti pontokhoz az elsődleges helyeken, el kell távolítani az adatbázis-replikákat a hely frissítése előtt. Elsődleges hely frissítése előtt konfigurálja újra a felügyeleti pontok adatbázis-replikáit.   
További információk: [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Konfigurálja újra a frissítés előtt letiltott adatbázis-karbantartási feladatokat:**  
Ha a frissítés előtt letiltotta [ System Center Configuration Manager karbantartási feladataihoz tartozó referenciákat](../../../../core/servers/manage/reference-for-maintenance-tasks.md) a helyen, konfigurálja újra ezeket a feladatokat ugyanazokkal a beállításokkal, mint amelyek a frissítés előtt voltak érvényben.  

**Frissítse az ügyfeleket**:  
A helyek a System Center Configuration Manager frissítés után szeretne frissítse az ügyfeleket.  

Az ügyfelek frissítésekor a rendszer eltávolítja a meglévő ügyfélszoftvert és telepíti az új ügyfélszoftver-verziót. Az ügyfelek frissítéséhez a Configuration Manager által támogatott bármelyik módszert használhatja.  

> [!TIP]  
>  Amikor frissíti egy hierarchia legfelső szintű helyét, az ügyfél-telepítési csomag is frissül a hierarchia minden terjesztési pontján. Amikor frissít egy elsődleges helyet, frissül az elsődleges helyről elérhető ügyfélfrissítési csomag is.  

A meglévő ügyfelek frissítésével, illetve az új ügyfelek telepítésével kapcsolatos információkért lásd: [A Windows rendszerű számítógépekhez készült ügyfelek frissítése a System Center Configuration Managerben](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

##  <a name="bkmk_considerations"></a> A frissítéskor megfontolandó szempontok  
**Automatikus műveletek**:  
A System Center Configuration Manager frissítéskor a következő műveletek automatikusan megtörténnek:  

-   A hely alaphelyzetbe áll, ami az összes helyrendszerszerepkör újratelepítését is jelenti.  
-   Ha a hely egy hierarchia legfelső szintű helye, akkor a hierarchia minden terjesztési pontján frissíti az ügyfél-telepítési csomagot. A hely az alapértelmezett rendszerindító lemezképeket is frissíti a Windows Assessment and Deployment Kit 10-ben szereplő Windows PE új verziója használatára. A frissítés azonban nem frissíti a meglévő adathordozót lemezképek központi telepítésére való használatra.  
-   Ha a hely elsődleges hely, akkor az adott hely ügyfélfrissítési csomagját frissíti.  

**Manuális műveletek a rendszergazda felhasználóknak frissítés után**   
Miután frissít egy helyet, érdekében, hogy a következő műveleteket:  

-   Győződjön meg arról, hogy az egyes elsődleges helyekhez rendelt ügyfelek frissülnek, és telepítse az új verzióhoz tartozó ügyfélszoftvert.  
-   Minden egyes Configuration Manager konzol, amely kapcsolódik a helyhez, és a helykiszolgálótól távoli számítógépen futó frissítéséhez.  
-   Azokon az elsődleges helyeken, ahol adatbázis-replikákat használ a felügyeleti pontokhoz, konfigurálja újra az adatbázis-replikákat.  
-   A helyfrissítések után frissítenie kell manuálisan a fizikai adathordozókat, például a CD-khez, DVD-khez és USB flash meghajtókhoz való ISO-fájlokat, valamint a Windows To Go központi telepítéséhez manuálisan előkészített vagy a hardvergyártók rendelkezésére bocsátott adathordozókat. Bár a webhely frissítése frissíti az alapértelmezett rendszerindító lemezképeket, nem tudja frissíteni a médiafájlokat vagy eszközön használt Configuration Manager alkalmazáson kívüli  
-   Tervezze be a nem alapértelmezett rendszerindító lemezképek frissítését, ha nincs szüksége a Windows PE eredeti (régebbi) verziójára.  

**Konfigurációkat és beállításokat befolyásoló műveletek**   
Amikor egy hely System Center Configuration Manager rendszerre frissül, bizonyos konfigurációk és beállítások a frissítés után nem maradnak meg vagy új alapértelmezett konfigurációra. A következő táblázat azokat a beállításokat tartalmazza, amelyek nem maradnak meg vagy amelyek módosulnak, és részleteket közöl a tervezés elősegítésére helyfrissítés esetén:  

-   **Szoftverközpont:**  
    A következő szoftverközpontbeli elemek alapértékre állnak vissza:  
    -   A**Munkainformációk** értéke visszaáll az **5:00** -tól **22:00** Monday -tól Friday.  
    -   A **Számítógép-karbantartás** értéke **Szoftverközpont műveleteinek felfüggesztése, ha a számítógép bemutató üzemmódban van**lesz.  
    -   A **Távvezérlés** a számítógéphez rendelt ügyfélbeállításokban lévő értékre áll.  
-   **Szoftverfrissítés összefoglalásának ütemezése:**  
     A szoftverfrissítések vagy szoftverfrissítés-csoportok egyéni összefoglalási ütemezései az alapértelmezett 1 órás értékre állnak vissza. Miután a frissítés befejeződött, állítsa vissza az egyéni összefoglalási értékeket a szükséges gyakoriságra.  

##  <a name="bkmk_test"></a> A helyadatbázis frissítése teszteléshez  
A következő információk csak akkor, amikor frissít egy korábbi versoin, például a System Center 2012 Configuration Manager a System Center Configuration Manager vonatkoznak. Ha a webhely már fut a System Center Configuration Manager, és új frissítést telepít, meg [2. lépés: A frissítés telepítése előtt az adatbázis-frissítés teszteléséhez](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) a **konzolon belüli frissítés telepítése előtt**.

Mielőtt frissít egy helyet, tesztelheti, hogy a hely adatbázisát a frissítéshez.  

Az adatbázis frissítés szempontjából való teszteléséhez első lépésként kell visszaállítania a Helyadatbázis egy példányát a Configuration Manager-hely nem üzemeltető SQL Server-példányra. Az adatbázis másolatához használt SQL Server verzióját az SQL Server-, hogy a Configuration Manager verziója, amely támogatja-e az adatbázis-másolat forrását verziónak kell lennie.  

A következő visszaállítását követően a Helyadatbázis az SQL Server-számítógépen futtassa a Configuration Manager telepítő adathordozó forrásmappából a System Center Configuration Managerbe integrált a **/testdbupgrade** parancssori kapcsolót.  

-   Tudnivalók a helyadatbázisok biztonsági másolatának elkészítéséről és visszaállításáról: [A telepítéshez használható parancssori kapcsolók](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  
-   A **/TESTDBUPGRADE** parancssori kapcsolóról [A telepítéshez használható parancssori kapcsolók](../../../../core/servers/deploy/install/command-line-options-for-setup.md) témakörben talál tájékoztatást.  
-   További információ az SQL Server támogatott verzióiról: [A System Center Configuration Manager által támogatott SQL Server-verziók](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

> [!TIP]  
>  Ha integrálja az Intune-hoz és a Configuration Managerben:  
>   
>  Tesztadatbázis-frissítés futtatásakor a helyadatbázis 5 napos vagy régebbi példányán, az alábbi üzenetek egyike jelenhet meg:  
>   
>  -   FIGYELMEZTETÉS: Frissítés arra kényszeríti a teljes szinkronizálás a felhővel.  
>  -   HIBA: Adatbázis-frissítés arra kényszeríti a teljes szinkronizálás a felhővel.  
>   
> Mindkét biztonságosan figyelmen kívül hagyható során az adatbázis-frissítés tesztelésre, mivel az nem jelzi a hiba vagy probléma a tesztelési célú frissítését. Ehelyett azt jelzik, hogy, hogy a tényleges frissítés során, az adatok a **felhő** adatbázis-replikációs csoport előfordulhat, hogy szinkronizálja a Microsoft Intune-nal.  

A következő eljárás használható a frissíteni tervezet egyes központi adminisztrációs helyeken és elsődleges helyeken.  

#### <a name="to-test-a-site-database-for-upgrade"></a>Helyadatbázis tesztelése frissítéshez  

1.  Készítsen másolatot a helyadatbázisról, és a példányt állítsa vissza, amely a helyadatbázissal azonos kiadást használ, és amelyen nem működik a Configuration Manager-hely SQL Server példánya. Például ha a helyadatbázis az SQL Server Enterprise kiadású példányán fut, ügyeljen arra, hogy olyan SQL Server-példányon állítsa vissza, amely szintén az SQL Server Enterprise kiadását futtatja.  

2.  Az adatbázis-példány visszaállítását követően futtassa a telepítőt a forrás-adathordozóján a System Center Configuration Manager. A telepítő futtatásakor használja a **/TESTDBUPGRADE** parancssori kapcsolót. Ha az adatbázispéldányt tartalmazó SQL Server-példány nem az alapértelmezett példány, meg kell adni az adatbázis másolatát tartalmazó példányt azonosító parancssori argumentumokat.  

     Tegyük fel például, hogy egy SMS_ABC nevű helyadatbázis frissítését tervezi. A helyadatbázis másolatát egy DBTest nevű, támogatott SQL Server-példányon állítja vissza. A Helyadatbázis példányának frissítési teszteléséhez a következő parancsot használja: **Setup.exe/testdbupgrade DBtest\CM_ABC**  

     A következő helyen forrás-adathordozóján a System Center Configuration Manager található Setup.exe: **SMSSETUP\BIN\X64**.  

3.  Az adatbázis frissítési tesztjének futtatásához használt SQL Server-példányon ellenőrizze a rendszermeghajtó gyökérmappájában található ConfigMgrSetup.log fájlban a folyamat előrehaladását és sikerességét:  

    -   Ha a tesztfrissítés sikertelen, oldja meg a helyadatbázis frissítésének sikertelenségét okozó problémákat, hozzon létre új biztonsági másolatot a helyadatbázisról, és tesztelje a frissítést a helyadatbázis új másolati példányán.  
    -   Ha a folyamat sikerült, törölheti az adatbázis másolati példányát.  

        > [!NOTE]  
        >  A tesztfrissítéshez használt helyadatbázis-példány visszaállítása más helyen helyadatbázisként történő használatra nem támogatott.  

Miután sikeresen frissítette a Helyadatbázis egy példányát, a frissítés a Configuration Manager-hely és a hozzá tartozó Helyadatbázis folytatásához.  

##  <a name="bkmk_upgrade"></a> Helyek frissítése  
Miután elvégezte a helyre vonatkozóan a frissítés előtti konfigurálási feladatokat, tesztelje a Helyadatbázis frissítését az az adatbázis egy másolatán, és töltse le az előfeltételként szükséges fájlokat és nyelvi csomagokat a telepíteni tervezett szervizcsomag-verzióhoz, készen áll a Configuration Manager hely frissítése.  

Amikor hierarchiában frissít helyeket, elsőként a hierarchia legfelső szintű helyét frissíti. A legfelső szintű hely lehet központi adminisztrációs hely vagy önálló elsődleges hely. A központi adminisztrációs hely frissítése után tetszés szerinti sorrendben frissítheti az elsődleges gyermekhelyeket. Elsődleges hely frissítése után, hogy a hely alárendelt másodlagos helyek frissítésére, vagy frissítsen további elsődleges helyeket, mielőtt bármelyik másodlagos helyet frissítené.  

A központi adminisztrációs hely vagy elsődleges hely frissítéséhez futtatnia a System Center Configuration Manager forrás-adathordozóján. A másodlagos helyek frissítéséhez azonban nem a telepítőt kell futtatni, Ehelyett használja a Configuration Manager konzol a másodlagos hely frissítését követően az elsődleges szülőhely frissítése befejeződik.  

Mielőtt frissít egy helyet, zárja be a Configuration Manager konzolon, a helyfrissítés befejezése után a helykiszolgálón, amíg nem telepített. Is zárja be a helykiszolgálón kívüli számítógépeken futó Configuration Manager konzolokat. A hely frissítésének befejeződése után újra csatlakozhat a konzollal. Azonban a Configuration Manager konzol a Configuration Manager új verzióra frissít, amíg ez a konzol nem jeleníthető meg egyes objektumokat és információkat, amelyek a Configuration Manager új verziójában elérhető.  

Az alábbi eljárások segítségével a Configuration Manager-helyek frissítésére:  

#### <a name="to-upgrade-a-central-administration-site-or-primary-site"></a>Központi adminisztrációs hely vagy elsődleges hely frissítése  

1.  Ellenőrizze, hogy a telepítőt futtató felhasználó rendelkezik-e az alábbi biztonsági jogosultságokkal:  

    -   Helyi rendszergazdai jogosultságok a helykiszolgálóként működő számítógéphez.  
    -   Távoli elsődleges hely esetén a helyre vonatkozó helyi rendszergazdai jogosultságok a távoli helyadatbázis-kiszolgálón.    </br></br>

2.  A helykiszolgáló számítógépen, nyissa meg a Windows Intézőt, és keresse meg a  **&lt;ConfigMgSourceMedia\>\SMSSETUP\BIN\X64**.  

3.  Kattintson duplán a **Setup.exe**fájlra. Megnyílik a Configuration Manager telepítő varázsló.  

4.  Az **Alapismeretek** lapon kattintson a **Tovább**gombra.  

5.  Az **Első lépések** lapon válassza a **Configuration Manager-hely frissítése**lehetőséget, majd kattintson a **Tovább**gombra.  

6.  A **Termékkulcs** lapon kattintson a **Tovább**gombra.  

     Ha korábban telepítette a Configuration Manager kiértékelése, akkor választhat **a termék licencelt verziójának telepítése**, és írja be a termékkulcsot a teljes Configuration Manager telepítésének megadásával teljes verziójúra alakíthatja át a helyet.  

     2016. októberi kiadása a verzió 1606 alapszintű verziót tartalmazó adathordozó a System Center Configuration Manager-kezdve is megadhat a frissítési garancia szerződés lejárati dátuma. Akkor is a beállítással adhatja meg a **Software Assurance lejárati dátum** a dátumnak kényelmes ne feledje, hogy a licencelési feltételeit. Ha nem adja meg a telepítés során, adja meg azt később a Configuration Manager konzolon.

     >  [!NOTE]   
     >  A Microsoft nem ellenőrzi a lejárati dátum megadott, és ne használja ezt a dátumot licencérvényesítés.  Ehelyett használhatja a lejárati dátum emlékeztetőként. Ez akkor hasznos, mert a Configuration Manager rendszeresen ellenőrzi az új szoftverfrissítések kínált online, és a megbízhatósági szoftverlicencek állapotának aktuális a további frissítések használatára jogosult.    

     További információkért lásd: [licencelés és a System Center Configuration Manager az](/sccm/core/understand/learn-more-editions).

7.  A **Microsoft szoftverlicenc-szerződés** oldalon olvassa el és fogadja el a licencfeltételeket, majd kattintson a **Tovább**gombra.  

8.  Az **Előfeltételként szükséges licencek** lapon olvassa el és fogadja el az előfeltételként szükséges szoftverek licencfeltételeit, majd kattintson a **Tovább**gombra. A telepítő letölti és automatikusan telepíti a szoftvert a helyrendszereken vagy ügyfeleken, ha szükséges. A továbblépés előtt be kell jelölnie az összes négyzetet.  

9. Az **Előfeltételként szükséges letöltések** lapon adja meg, hogy a telepítő letöltse-e a legújabb, előfeltételként szükséges újraterjeszthető fájlokat és nyelvi csomagokat, valamint a legújabb termékfrissítéseket az internetről, vagy a korábban letöltött fájlokat használja. Ez után kattintson a **Tovább**gombra. Ha a telepítő letöltési segédprogramjával már letöltötte a fájlokat, jelölje be a **Korábban letöltött fájlok használata** elemet, majd adja meg a letöltési mappát. További információkért lásd: [a telepítő letöltési segédprogramja](/sccm/core/servers/deploy/install/setup-downloader).

    > [!NOTE]  
    >  Korábban letöltött fájlok használata esetén győződjön meg arról, hogy a letöltési mappa útvonalán a fájlok legújabb verziója található.  

10. A **Kiszolgáló nyelvének kiválasztása** lapon tekintse meg a helyen aktuálisan telepített nyelvek listáját. Ezen a helyen a Configuration Manager konzolon és jelentések érhetők el további nyelveket adhat, vagy törölje a nyelveket, amelyeket már nem támogatja az ezen a helyen, majd **következő**. Az angol nyelv alapértelmezés szerint ki van választva, és nem távolítható el.  

    > [!IMPORTANT]  
    >  Minden egyes Configuration Manager verziója a Configuration Manager korábbi verziója nyelvi csomagjait nem használhatja. Ahhoz, hogy a Configuration Manager-hely frissítése egy nyelv támogatását, a nyelvi csomagnak a verziója, az új verzióhoz tartozó kell használnia. Példa, verzióra történő frissítés a System Center 2012 Configuration Manager a System Center Configuration Manager, a nyelvi csomag a System Center Configuration Manager verziója nem érhető el az előfeltételként szükséges fájlok letöltése, ha támogatja az adott nyelvhez nem telepíthető.  

11. Az **Ügyfélnyelv kiválasztása** lapon tekintse meg a helyen aktuálisan telepített nyelvek listáját. Válassza ki a helyen az ügyfélszámítógépek számára használható további nyelveket, illetve törölje az ezen a helyen támogatni már nem kívánt nyelveket. Adhat meg, hogy a mobileszközök ügyfelei számára engedélyezi-e az összes ügyfélnyelvet, majd kattintson a **Tovább**gombra. Az angol nyelv alapértelmezés szerint ki van választva, és nem távolítható el.  

    > [!IMPORTANT]  
    >  Minden egyes Configuration Manager verziója a Configuration Manager korábbi verziója nyelvi csomagjait nem használhatja. Ahhoz, hogy a Configuration Manager-hely frissítése egy nyelv támogatását, a nyelvi csomagnak a verziója, az új verzióhoz tartozó kell használnia. Példa, verzióra történő frissítés a System Center 2012 Configuration Manager a System Center Configuration Manager, a nyelvi csomag a System Center Configuration Manager verziója nem érhető el az előfeltételként szükséges fájlok letöltése, ha támogatja az adott nyelvhez nem telepíthető.  

12. A **Beállítások összegzése** lapon kattintson a **Tovább** gombra a kiszolgálónak a hely frissítésére való alkalmasságát vizsgáló előfeltétel-ellenőrző indításához.  

13. Ha az **Előfeltételek telepítésének ellenőrzése** lap nem jelez problémákat, kattintson a **Tovább** gombra a hely és a helyrendszerszerepkörök frissítéséhez. Ha az Előfeltételek ellenőrzése eszköz problémát talál, kattintson a megfelelő elemre a listában a probléma megoldásával kapcsolatos részletekért. A telepítés folytatása előtt javítsa ki a listában **Hiba** állapottal jelzett összes problémát. Ha elhárította a problémát, kattintson az **Ellenőrzés futtatása** gombra az újbóli előfeltétel-ellenőrzéshez. Az előfeltétel-ellenőrző eredményeit a rendszermeghajtó gyökérmappájában található ConfigMgrPrereq.log fájlban is áttekintheti. A naplófájl további információkat is tartalmazhat, amelyek a kezelőfelületen nem jelennek meg. Telepítés előfeltételeinek szabályait és leírásukat listájáért lásd: [előfeltétel-ellenőrző](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

A **Frissítés** lapon a telepítés általános folyamatállapota látható. Ha a telepítő befejezte a központi helykiszolgáló és -rendszer telepítését, bezárhatja a varázslót. A hely konfigurálása a háttérben folytatódik.  

#### <a name="to-upgrade-a-secondary-site"></a>Másodlagos hely frissítése  

1.  Ellenőrizze, hogy a telepítőt futtató rendszergazda felhasználó rendelkezik-e az alábbi biztonsági jogosultságokkal:  

    -   Helyi rendszergazdai jogosultságok a másodlagos hely számítógépén.  
    -   Infrastruktúra-rendszergazda vagy Teljes körű rendszergazda biztonsági szerepkör az elsődleges szülőhelyen.  
    -   Rendszergazdai jogosultságok a másodlagos hely helyadatbázisán.  
    </br>
2.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

3.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Helyek**lehetőségre.  

4.  Jelölje ki a frissíteni kívánt másodlagos helyet, majd a **Kezdőlap** **Hely** csoportjában kattintson a **Frissítés**elemre.  

5.  Az **Igen** gombra kattintva erősítse meg a döntést, és kezdje meg a másodlagos hely frissítését.  

A másodlagos hely frissítése a háttérben történik. A frissítés befejezése után ellenőrizheti a állapotát a Configuration Manager konzolon. Az állapot megerősítéséhez jelölje ki a másodlagos helykiszolgálót, majd a **Kezdőlap** lapon lévő **Hely** csoportban kattintson a **Telepítési állapot megjelenítése**elemre.  

##  <a name="BKMK_PostUpgrade"></a> A frissítés utáni feladatok végrehajtása  
Miután elvégezte egy hely új szervizcsomagra történő frissítését, előfordulhat, hogy a frissítés lezárásához vagy a hely újrakonfigurálásához további feladatokat kell elvégeznie. A feladatok közé tartozhat a frissítés a Configuration Manager-ügyfelek vagy a Configuration Manager konzolok, a felügyeleti pontok adatbázis-replikák újraengedélyezése, vagy amely használ, amelyek nem maradnak a szervizcsomaggal való frissítés után a Configuration Manager funkcióihoz tartozó olyan beállítások visszaállítása.  

**A másodlagos helyek kapcsolatos ismert problémák:**  
- **Amikor frissít 1511-es verzióra:** Ellenőrizze a másodlagos helyeken lévő ügyfelek is a felügyeleti pontot a másodlagos helyről (proxy felügyeleti pont), manuálisan adja hozzá a felügyeleti pont a terjesztési pontokat, a másodlagos helyen is tartalmazó határcsoporthoz.  

- **Amikor frissít 1606 vagy újabb verzióra:** Proxy felügyeleti pontokat a rendszer automatikusan hozzáadja a másodlagos hely terjesztési pontjára tartalmazó határcsoportokat.

