---
title: "Ellenőrzőlista a 1610 |} System Center Configuration Managerben"
description: "További tudnivalók a System Center Configuration Manager 1610 verzióra frissítés előtt elvégzendő műveleteket."
ms.custom: na
ms.date: 2/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b411cb0-4fd1-41f2-a2f6-33738a5bde96
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 30af3326578d39c6d995672071705bcaeb877e4d
ms.openlocfilehash: 640fc5ddb4e0a6828901b7f406ca72fc210b2970
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1610-for-system-center-configuration-manager"></a>Ellenőrzőlista a frissítés 1610 a System Center Configuration Manager telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az aktuális ág a System Center Configuration Manager használata esetén a konzolon belüli frissítés verziójának frissítése a hierarchiában 1606 verziójáról 1610 is telepítheti. Ha a hierarchiában 1511-es, a 1602-es vagy 1606 verzióját futtatja, frissítheti, 1610 verzióra.

Ahhoz, hogy a frissítés 1610 verzióhoz, egy szolgáltatás szolgáltatáskapcsolódási pont helyrendszer-szerepkörrel kell használnia, a hierarchia legfelső szintű helyén. Ez lehet online vagy offline módban. Miután a hierarchia letölti a frissítési csomag a Microsoft, megtalálja a konzolon a **felügyeleti &gt; áttekintése &gt; Felhőszolgáltatások &gt; frissítés és karbantartás**.

-   Ha a frissítés jelenik meg, **elérhető**, a frissítés készen áll telepítésére. Verzió 1610 a telepítés előtt tekintse át a következőket [1610 frissítés telepítéséről](#about-installing-update-1610) és a [ellenőrzőlista](#checklist) konfigurációk a frissítés elkezdése előtt.

-   Ha a frissítés jelenik meg **letöltése** és nem módosítható, tekintse át a **hman.log** és **dmpdownloader.log** a hibákat.

    -   Általában is újraindíthatja a **SMS_Executive** szolgáltatás a helykiszolgálón indítsa újra a frissítés terjesztését fájlok letöltését.

    -   Egy másik közös letöltési probléma akkor fordul elő, ha a proxykiszolgáló beállításai megakadályozzák letölthető <http://silverlight.dlservice.microsoft.com> és <http://download.microsoft.com>.

Frissítések telepítésével kapcsolatos további információkért lásd: [konzolon belüli frissítések és karbantartás](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Az aktuális ág verzióival kapcsolatos információkért lásd: [alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#bkmk_Baselines) a [frissíti a System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1610"></a>Frissítés 1610 telepítéséről

**Webhelyek:**  
Frissítés 1610 csak a hierarchia legfelső szintű helyén telepíthető. Ez azt jelenti, hogy elindította a telepítés a központi adminisztrációs helyről, ha nincs fiókja, vagy az önálló elsődleges helyről. A frissítés a legfelső szintű helyen telepíti, gyermekhelyei után a következő frissítések működését:

-   A gyermek elsődleges helyek automatikusan telepítik a frissítést, a központi adminisztrációs hely befejezi a frissítés telepítése után. Szolgáltatás időszakokkal szabályozhatja, hogy is használhatja, amikor egy helyet telepíti a frissítéseket. Szolgáltatás windows verzió 1606, mielőtt karbantartási időszakok nevezik. További információkért lásd: [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows).

-   A szülőhely befejezi a frissítés telepítése után a Configuration Manager konzolon belül a másodlagos helyeket manuálisan kell frissíteni. A másodlagos helykiszolgálók automatikus frissítése nem támogatott.

**Helyrendszer-szerepkörök:**  
Ha a helykiszolgáló telepíti a frissítést, a helyrendszerszerepkörök a helykiszolgálón, valamint azokat, amelyeket a távoli számítógépekre automatikusan telepített telepített frissül. Ezért a frissítés telepítése előtt győződjön meg arról, hogy mindegyik helyrendszer-kiszolgáló megfelel-e az új, frissített verzióval való működés esetleges új előfeltételeinek.

**A Configuration Manager konzolok:**   
Az első használatakor a Configuration Manager konzol frissítés befejeződését követően kérni fogja, hogy a konzol frissítését. Ehhez futtassa a Configuration Manager telepítőt azon a számítógépen, amelyre a konzol, és kattintson a konzol frissítésére. Azt javasoljuk, hogy ne halogassa a frissítésnek a konzolra való telepítését.



## <a name="checklist"></a>Feladatlista

**Győződjön meg arról, hogy fut-e a System Center Configuration Manager támogatott verziója az összes helyen:** Frissítés 1610 telepítésének megkezdése előtt a hierarchia minden helyére a ugyanazt a verziót kell futtatnia a System Center Configuration Manager: 1511-es, a 1602-es vagy a 1606 bármelyik verziója.

**Tekintse át a frissítési garancia vagy egyenértékű előfizetés jogok állapotát:**   
Frissítés 1610 aktív Software Assurance (SA) szerződést kell rendelkeznie. Ha 1610 verzióját telepíti, a beállítás lesz a a **licencelés** lapon ellenőrizze a **Software Assurance lejárati dátum**.

Ez az egy választható értéket, a licenc lejárati dátumát, amely akkor látható, ha a jövőbeli frissítések telepítése kényelmes emlékeztetőként megadható. Ha telepítette a Configuration Manager a verzió 1606 alapszintű verziót tartalmazó adathordozóról, előfordulhat, hogy korábban megadott ezt az értéket a telepítés során, vagy pedig a **licencelés** lapján a **Hierarchiabeállítások** hely telepítése után.

További információkért lásd: [licencelés és a System Center Configuration Manager az](/sccm/core/understand/learn-more-editions).

**Tekintse át a Microsoft .NET-verziót a helyrendszer-kiszolgálókon telepítve:** Frissítés 1610 a hely telepítésekor a Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját minden számítógépen, amelyen a következő helyrendszerszerepkörök közül, ha a .NET-keretrendszer 4.5-ös vagy újabb verziója nincs telepítve:

-   Beléptetési proxypont
-   Beléptetési pont
-   Felügyeleti pont
-   Szolgáltatáskapcsolódási pont

A telepítést a helyrendszer-kiszolgáló helyezhetik újraindítás függőben állapot és a jelentés a Configuration Manager összetevőállapot-megjelenítője hibákat. Ezenkívül a kiszolgálón futó .NET-alkalmazások is szembesülhet véletlen hibákat, a kiszolgáló újraindításáig.

További információk: [Hely és helyrendszer előfeltételei](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

**Ellenőrizze a hely és a hierarchia állapotát, és ellenőrizze, hogy nincsenek-e megoldatlan problémák:** Mielőtt frissít egy helyet, oldja meg a működéssel kapcsolatos összes problémát a helykiszolgálón, a Helyadatbázis-kiszolgáló és a helyrendszerszerepkörök, amelyek a távoli számítógépekre telepített helyrendszerszerepkörökben. A megoldatlan működési problémák megakadályozhatják a helyek frissítését.

További információkért lásd: [A riasztások és az állapotrendszer használata a System Center Configuration Managerben](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Tekintse át a fájlt és az adatok helyek közötti replikáció:**   
Győződjön meg arról, hogy a fájl és a helyek közötti adatbázis-replikáció működési és aktuális. Késések vagy elmaradások vagy előfordulhat, hogy egy smooth, sikeres frissítést.
Az adatbázis-replikáció esetében a Replication Link Analyzer segítségével is megoldhatja a problémákat a frissítés elkezdése előtt.

További információkért lásd: [kapcsolatos a Replication Link Analyzer](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) a a [figyelő hierarchia és replikációs infrastruktúra a System Center Configuration Managerben](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) témakör.

**Az operációs rendszer összes fontos frissítését telepíti a számítógépekre, a webhely üzemeltetésére, a Helyadatbázis-kiszolgáló és a távoli helyrendszerszerepköröket tartalmazzák:** Mielőtt telepít egy frissítést a Configuration Manager számára, telepítse minden érintett helyrendszerre a fontos frissítéseket. Ha egy frissítés telepítése újraindítást igényel, a Configuration Manager-frissítés elindítása előtt indítsa újra a megfelelő számítógépekre.

**Tiltsa le az adatbázis-replikák beállítása felügyeleti pontokhoz az elsődleges helyeken:**   
A Configuration Manager nem tud sikeresen frissíteni egy elsődleges helyet, amely egy adatbázis-replikát a felügyeleti pont is engedélyezve van. Tiltsa le az adatbázis-replikálást, mielőtt:

-   A biztonsági mentést készít a helyadatbázisról az adatbázis-frissítés teszteléséhez.
-   Egy frissítés telepítése a Configuration Manager számára.

További információk: [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Manuális feladatátvételhez beállítva SQL Server AlwaysOn rendelkezésre állási csoportok:**   
Mielőtt telepíti a frissítéseket, például a verzió 1610, győződjön meg arról, hogy a rendelkezésre állási csoport kézi feladatátvételre értékre van állítva. A hely frissítését követően visszaállíthatja kell automatikus feladatátvételt. További információ: [Helyadatbázis az SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Konfigurálja újra a hálózati terheléselosztást használó szoftverfrissítési pontokhoz:**   
A Configuration Manager nem tudja frissíteni olyan helyet, amely egy hálózati terheléselosztási (NLB) fürt a szoftverfrissítési pontok futtatásához.

Ha a szoftverfrissítési pontok NLB-fürtöt használ, a Windows PowerShell használatával távolítsa el az NLB-fürt.
További információk: [Szoftverfrissítések tervezése a System Center Configuration Managerben](/sccm/sum/plan-design/plan-for-software-updates).

**Tiltsa le az összes helykarbantartási feladatot az egyes helyeken a hely a frissítés telepítésének időtartama:**   
A frissítés telepítése előtt tiltsa le a helykarbantartási feladatokat arra az időre, amíg a frissítés folyamatban. Ilyen letiltandó feladatok lehetnek például a következők:

-   Helykiszolgáló biztonsági mentése
-   Elavult ügyfélműveletek törlése
-   Elavult felderítési adatok törlése

Ha egy helyadatbázis-karbantartási feladat fut a frissítés telepítése során, a frissítés telepítése sikertelen lehet. Mielőtt letilt egy feladatot, jegyezze fel az ütemezését, a frissítés telepítése után visszaállíthatja a konfigurációja a feladat.

További információkért lásd: [karbantartási feladatok a System Center Configuration Manager](/sccm/core/servers/manage/maintenance-tasks) és [hivatkozás tartozó karbantartási feladatokat a System Center Configuration Manager](/sccm/core/servers/manage/reference-for-maintenance-tasks).

**Hozzon létre egy biztonsági másolatot a helyadatbázisról a központi adminisztrációs helyen és elsődleges helyek:** Mielőtt frissít egy helyet, készítsen biztonsági másolatot a helyadatbázisról, hogy rendelkezik-e egy sikeres mentés vész-helyreállítási.

További információkért lásd: [biztonsági mentés és helyreállítás a System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

**A legutóbbi Helyadatbázis biztonsági másolatán az adatbázis-frissítés teszteléséhez:** A System Center Configuration Manager központi adminisztrációs hely vagy elsődleges hely frissítése előtt tesztelje a Helyadatbázis frissítési folyamatát a Helyadatbázis másolatán.

-   Azt javasoljuk, hogy tesztelje a Helyadatbázis frissítési folyamatát, mert amikor frissít egy helyet, a Helyadatbázis módosítható.

-   Bár a tesztadatbázison végzett frissítés nem szükséges, felderíthetők a frissítés előtt az éles adatbázist frissítené.

-   A sikertelen adatbázis-frissítés működésképtelenné teheti a helyadatbázist, és előfordulhat, egy hely helyreállításával lehet működőképes állapotba hozni.

-   Bár a Helyadatbázis meg van osztva a hierarchiában lévő helyek között, tervezze meg tesztelje az adatbázist minden érintett helyen, mielőtt frissíti azokat.

-   Ha az adatbázis-replikákat használ a felügyeleti pontokhoz az elsődleges helyeken, tiltsa le a replikációt, mielőtt létrehozná a biztonsági mentést a helyadatbázisról.

A Configuration Manager nem támogatja a másodlagos helyek biztonsági mentését és nem támogatja a másodlagos Helyadatbázis tesztelési célú frissítését.

Az élesben használt helyadatbázison nem futnak a tesztadatbázison végzett frissítés. Ez frissíti a helyadatbázist, és működésképtelenné teheti a helyet. További információkért lásd: [2. lépés: A frissítés telepítése előtt az adatbázis-frissítés teszteléséhez](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) a **konzolon belüli frissítés telepítése előtt**.

**Ügyféltesztelés megtervezése:**   
Ha olyan frissítést telepít, amely frissíti az ügyfelet, tesztelheti, hogy új ügyfélfrissítés üzem előtti előtt telepíti, és az aktív ügyfelek frissítése.

Kihasználja ezt a beállítást, konfigurálnia kell a helyet az automatikus frissítésének támogatására a frissítés telepítésének megkezdése előtt éles üzem előtti használathoz.

További információkért lásd: [frissítse az ügyfeleket a System Center Configuration Managerben](/sccm/core/clients/manage/upgrade/upgrade-clients) és [ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Tervezi, hogy szolgáltatás időszakokkal szabályozhatja, hogy Helykiszolgálók telepítésekor frissítések:**   
A szolgáltatási segítségével meghatározhat egy olyan időszakot, amely során egy helykiszolgálóra frissítések telepítése.

Ezzel kontrollálhatja, hogy mikor telepítsék a frissítést a hierarchiába tartozó helyek. Szolgáltatás windows verzió 1606, mielőtt karbantartási időszakok nevezik. További információkért lásd: [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows).

**A telepítő előfeltétel-ellenőrzés futtatása:**   
Ha a frissítés szerepel-e a konzol **elérhető,** egymástól függetlenül futtathatja az előfeltétel-ellenőrző a frissítés telepítése előtt. (Ha a frissítés telepítése a helyen, az előfeltétel-ellenőrző ismét elindul.)

Előfeltétel-ellenőrzés futtatása a konzolt, keresse fel **felügyeleti > Áttekintés > Felhőszolgáltatások > frissítések és karbantartás.** Kattintson a jobb gombbal **frissítőcsomag Configuration Manager 1610**, és válassza a **előfeltételek ellenőrzésének futtatása**.

Kezdő- és az Előfeltételek ellenőrzése majd figyelési kapcsolatos további információkért lásd: **3. lépés: Az előfeltétel-ellenőrzés futtatása frissítés telepítése előtt** témakör [konzolon belüli frissítések telepítése a System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Ha az előfeltétel-ellenőrző önállóan vagy egy frissítés telepítésének részeként fut, a folyamat frissíti néhány termék forrásfájlok helykarbantartási feladatokhoz használt. Ezért az előfeltétel-ellenőrző futtatása előtt azonban után a frissítés 1610, ha egy Helyadatbázis-karbantartási feladat végrehajtásához futtassa **Setupwpf.exe** (Configuration Manager telepítő) a CD-ről. Legújabb mappában található a helykiszolgálón.

**Helyek frissítése:**   
Most már készen áll a hierarchiában a frissítés telepítésének elindítása. A frissítés telepítésével kapcsolatos további információkért lásd: [konzolon belüli frissítések telepítéséhez.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Azt javasoljuk, hogy szeretné-e minden helyen munkaidőn kívülre a frissítés telepítése, amikor a frissítés és a műveletek újra kell telepítenie a hely összetevőinek és a helyrendszerszerepkörök telepítési folyamata hatással lesz a legalább az üzleti tevékenységre.

További információ: [A System Center Configuration Manager frissítései](/sccm/core/servers/manage/updates).

