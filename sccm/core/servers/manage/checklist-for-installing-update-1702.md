---
title: "Ellenőrzőlista a 1702 |} System Center Configuration Managerben"
description: "További tudnivalók a System Center Configuration Manager 1702 verzióra frissítés előtt elvégzendő műveleteket."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b587779e-1bd3-4ee3-8146-8e31f53499bd
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: c4ace452d62d4fa08f4457cb1735718ca4bd016d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1702-for-system-center-configuration-manager"></a>Ellenőrzőlista a frissítés 1702 a System Center Configuration Manager telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az aktuális ág a System Center Configuration Manager használata esetén a konzolon belüli frissítés verziójának frissítése a hierarchiában egy korábbi verziójáról 1702 is telepítheti.

> [!TIP]  
1702 verziója is elérhető [alapszintű verziót tartalmazó adathordozó](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions) használható egy új hierarchia első helyének telepítéséhez.

Ahhoz, hogy a frissítés 1702 verzióhoz, egy szolgáltatás szolgáltatáskapcsolódási pont helyrendszer-szerepkörrel kell használnia, a hierarchia legfelső szintű helyén. Ez lehet online vagy offline módban. Miután a hierarchia letölti a frissítési csomag a Microsoft, megtalálja a konzolon a **felügyeleti &gt; áttekintése &gt; Felhőszolgáltatások &gt; frissítés és karbantartás**.

-   Ha a frissítés jelenik meg, **elérhető**, a frissítés készen áll telepítésére. Verzió 1702 a telepítés előtt tekintse át a következőket [frissítés telepítéséről 1702](#about-installing-update-1702) és a [ellenőrzőlista](#checklist) konfigurációk a frissítés elkezdése előtt.

-   Ha a frissítés jelenik meg **letöltése** és nem módosítható, tekintse át a **hman.log** és **dmpdownloader.log** a hibákat.

    -   Ha a dmpdownloader.log a dmpdownloader folyamat alvó állapotban van, és várakozik időközönkénti előtt a frissítések keresését, később is újraindíthatja a **SMS_Executive** szolgáltatás a helykiszolgálón indítsa újra a frissítés terjesztését fájlok letöltését.

    -   Egy másik közös letöltési probléma akkor fordul elő, ha a proxykiszolgáló beállításai megakadályozzák letölthető <http://silverlight.dlservice.microsoft.com> és <http://download.microsoft.com>.

Frissítések telepítésével kapcsolatos további információkért lásd: [konzolon belüli frissítések és karbantartás](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Az aktuális ág verzióival kapcsolatos információkért lásd: [alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#bkmk_Baselines) a [frissíti a System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1702"></a>Frissítés 1702 telepítéséről

**Webhelyek:**  
A hierarchia legfelső szintű helyén 1702 frissítést telepíti. Ez azt jelenti, hogy elindította a telepítés a központi adminisztrációs helyről, ha nincs fiókja, vagy az önálló elsődleges helyről. A legfelső szintű helyen a frissítés telepítése után a gyermekhelyek rendelkezik a következő frissítések működését:

-   A gyermek elsődleges helyek automatikusan telepítik a frissítést, a központi adminisztrációs hely a frissítés telepítésének befejeződése után. Szolgáltatás időszakokkal szabályozhatja, hogy is használhatja, amikor egy helyre települ a frissítés. További információkért lásd: [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows).

-   Az elsődleges szülőhely befejezi a frissítés telepítése után a Configuration Manager konzolon belül minden másodlagos hely manuálisan kell frissíteni. A másodlagos helykiszolgálók automatikus frissítése nem támogatott.

**Helyrendszer-szerepkörök:**  
A helykiszolgáló telepíti a frissítést, ha telepítve vannak a helykiszolgáló számítógépén, és a távoli számítógépekre telepített helyrendszerszerepkörök automatikusan frissülnek. A frissítés telepítése előtt győződjön meg arról, hogy mindegyik helyrendszer-kiszolgáló megfelel-e az új, frissített verzióval való működés előfeltételek.

**A Configuration Manager konzolok:**   
Az első használatakor a Configuration Manager konzol frissítés befejeződését követően kérni fogja, hogy a konzol frissítését. Ehhez futtassa a Configuration Manager telepítőt azon a számítógépen, amelyre a konzol, és kattintson a konzol frissítésére. Azt javasoljuk, hogy ne halogassa a frissítésnek a konzolra való telepítését.

> [!IMPORTANT]  
> Amikor telepít egy frissítést a központi adminisztrációs helyen, az alábbi korlátozások és várakozás, amely a léteznek, amíg az összes alárendelt elsődleges hely is a frissítés telepítésének befejezéséhez figyelembe venni:    
> - **Ügyfélfrissítések** nem indulnak el. Ez magában foglalja az ügyfelek és az éles üzem előtti ügyfelek automatikus frissítése. Emellett az éles üzem előtti ügyfelek nem lehetséges előléptetés, csak az utolsó helyen a frissítés telepítésének befejeződése után. Az utolsó helyen a frissítés telepítésének befejezése után ügyfélfrissítések megkezdődik a konfigurációs lehetőségek alapján.   
> - **Új szolgáltatások** engedélyezi a frissítés nem érhetők el. Ez az olyan helyhez, amely még nem telepítette az adott funkcióhoz tartozó támogatási elküldését az adott szolgáltatáshoz kapcsolódó adatainak a replikálását megelőzése érdekében. Ha minden elsődleges hely telepítette a frissítést, a szolgáltatás számára érhető el.   
> - **Replikációs hivatkozások** között a központi adminisztrációs hely és gyermek elsődleges helyek állapottal láthatók ugyanitt nem frissített. Ez jeleníti meg a frissítési csomag telepítési állapota a befejezett állapotú figyelmeztetés a figyelés replikáció inicializálásánál. A Figyelés csomópont, a konzol, ez jeleníti meg, *hivatkozás konfigurálás alatt*.



## <a name="checklist"></a>Feladatlista

**Győződjön meg arról, hogy az összes hely a System Center Configuration Manager, hogy a támogatja frissíteni 1702 változata fusson:**   
A hierarchia mindegyik helykiszolgálóján a System Center Configuration Manager azonos verzióját kell futtatnia, 1702 frissítés telepítésének megkezdése előtt. 1702 frissítéséhez az 1602-es, 1606 vagy 1610 verziót kell használnia.

**Tekintse át a frissítési garancia vagy egyenértékű előfizetés jogok állapotát:**   
Frissítés 1702 aktív Software Assurance (SA) szerződést kell rendelkeznie. Ha a frissítés telepítése a **licencelés** lapon megadja a lehetőség, hogy jóváhagyja a **Software Assurance lejárati dátum**.

Ez az egy kényelmes ne feledje, a licenc lejárati dátum megadása nem kötelező érték. Ez a dátum a jövőbeli frissítések telepítése esetén látható. Előfordulhat, hogy korábban már megadta ezt az értéket telepítés vagy frissítés, vagy a telepítés közben a **licencelés** lapján a **Hierarchiabeállítások**, az a Configuration Manager konzolon.

További információkért lásd: [licencelés és a System Center Configuration Manager az](/sccm/core/understand/learn-more-editions).

**Tekintse át a Microsoft .NET-verziót a helyrendszer-kiszolgálókon telepítve:** A frissítés a hely telepítésekor Configuration Manager automatikusan telepíti a .NET-keretrendszer 4.5.2-es verzióját minden számítógépen, amelyen a következő helyrendszerszerepkörök közül, ha a .NET-keretrendszer 4.5-ös vagy újabb verziója nincs telepítve:

-   Beléptetési proxypont
-   Beléptetési pont
-   Felügyeleti pont
-   Szolgáltatáskapcsolódási pont

A telepítést a helyrendszer-kiszolgáló helyezhetik újraindítás függőben állapot és a jelentés a Configuration Manager összetevőállapot-megjelenítője hibákat. Ezenkívül a kiszolgálón futó .NET-alkalmazások is szembesülhet véletlen hibákat, a kiszolgáló újraindításáig.

További információk: [Hely és helyrendszer előfeltételei](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

**Nézze át a Windows Assessment and Deployment Kit (ADK) verzióját a Windows 10** a Windows 10 ADK 1607 vagy újabb verzióját kell lennie. Ha frissítenie kell az ADK, tegye meg a Configuration Manager frissítés megkezdése előtt. Ez biztosítja, hogy az alapértelmezett rendszerindító lemezképek automatikusan frissülnek a Windows PE a legújabb verzióra. (Egyéni rendszerindító lemezképeket manuálisan frissítendő.)

Ha az ADK frissítése előtt frissíteni a helyet, tekintse meg a blog [Configuration Manager és a Windows ADK for Windows 10, verziója 1607](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/09/configuration-manager-and-the-windows-adk-for-windows-10-version-1607/) egy parancsfájlt, amelynek a segítségével generálja újra a rendszerindító lemezképeket.

**Ellenőrizze a hely és a hierarchia állapotát, és ellenőrizze, hogy nincsenek-e megoldatlan problémák:** Mielőtt frissít egy helyet, oldja meg a működéssel kapcsolatos összes problémát a helykiszolgálón, a Helyadatbázis-kiszolgáló és a helyrendszerszerepkörök, amelyek a távoli számítógépekre telepített helyrendszerszerepkörökben. A megoldatlan működési problémák megakadályozhatják a helyek frissítését.

További információkért lásd: [A riasztások és az állapotrendszer használata a System Center Configuration Managerben](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Tekintse át a fájlt és az adatok helyek közötti replikáció:**   
Győződjön meg arról, hogy a fájl és a helyek közötti adatbázis-replikáció működési és aktuális. Késések vagy elmaradások vagy előfordulhat, hogy egy smooth, sikeres frissítést.
Az adatbázis-replikáció esetében a Replication Link Analyzer segítségével is megoldhatja a problémákat a frissítés elkezdése előtt.

További információkért lásd: [kapcsolatos a Replication Link Analyzer](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) a a [figyelő hierarchia és replikációs infrastruktúra a System Center Configuration Managerben](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) témakör.

**Az operációs rendszer összes fontos frissítését telepíti a számítógépekre, a webhely üzemeltetésére, a Helyadatbázis-kiszolgáló és a távoli helyrendszerszerepköröket tartalmazzák:** Mielőtt telepít egy frissítést a Configuration Manager számára, telepítse minden érintett helyrendszerre a fontos frissítéseket. Ha valamelyik telepített frissítés újraindítást igényel, indítsa újra a megfelelő számítógépeket, mielőtt elkezdi a frissítés telepítését.

**Tiltsa le az adatbázis-replikák beállítása felügyeleti pontokhoz az elsődleges helyeken:**   
A Configuration Manager nem tud sikeresen frissíteni egy elsődleges helyet, amely egy adatbázis-replikát a felügyeleti pont is engedélyezve van. Tiltsa le az adatbázis-replikálást, mielőtt:

-   A biztonsági mentést készít a helyadatbázisról az adatbázis-frissítés teszteléséhez.
-   Egy frissítés telepítése a Configuration Manager számára.

További információk: [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Manuális feladatátvételhez beállítva SQL Server AlwaysOn rendelkezésre állási csoportok:**   
Ha azt egy rendelkezésre állási csoportban, győződjön meg arról, hogy a rendelkezésre állási csoport beállításai kézi feladatátvételre a frissítés telepítésének megkezdése előtt. Miután frissítette a helyet, kell lennie az automatikus feladatátvételt is helyreállíthatja. További információ: [Helyadatbázis az SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Konfigurálja újra a hálózati terheléselosztást használó szoftverfrissítési pontokhoz:**   
A Configuration Manager nem tudja frissíteni olyan helyet, amely egy hálózati terheléselosztási (NLB) fürt a szoftverfrissítési pontok futtatásához.

Ha a szoftverfrissítési pontok NLB-fürtöt használ, a Windows PowerShell segítségével távolítsa el az NLB-fürt.
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

**A legutóbbi Helyadatbázis biztonsági másolatán az adatbázis-frissítés teszteléséhez:** A System Center Configuration Manager központi adminisztrációs hely vagy elsődleges hely frissítése előtt tesztelheti a Helyadatbázis frissítési folyamatát a Helyadatbázis másolatán.

-   Azt javasoljuk, hogy tesztelje a Helyadatbázis frissítési folyamatát, mert amikor frissít egy helyet, a Helyadatbázis módosítható.

-   Bár a tesztadatbázison végzett frissítés nem szükséges, felderíthetők a frissítés előtt az éles adatbázist frissítené.

-   A sikertelen adatbázis-frissítés működésképtelenné teheti a helyadatbázist, és előfordulhat, a hely helyreállításával lehet működőképes állapotba hozni.

-   Bár a Helyadatbázis meg van osztva a hierarchiában lévő helyek között, tervezze meg tesztelje az adatbázist minden érintett helyen, mielőtt frissíti azokat.

-   Ha az adatbázis-replikákat használ a felügyeleti pontokhoz az elsődleges helyeken, tiltsa le a replikációt, mielőtt létrehozná a biztonsági mentést a helyadatbázisról.

A Configuration Manager nem támogatja a másodlagos helyek biztonsági mentését és nem támogatja a másodlagos Helyadatbázis tesztelési célú frissítését.

Az élesben használt helyadatbázison nem futnak a tesztadatbázison végzett frissítés. Ez frissíti a helyadatbázist, és működésképtelenné teheti a helyet. További információkért lásd: [2. lépés: A frissítés telepítése előtt az adatbázis-frissítés teszteléséhez](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) a **konzolon belüli frissítés telepítése előtt**.

**Ügyféltesztelés megtervezése:**   
Ha olyan frissítést telepít, amely frissíti az ügyfelet, tesztelheti, hogy új ügyfélfrissítés üzem előtti előtt telepíti, és az aktív ügyfelek frissítése.

Kihasználja ezt a beállítást, konfigurálnia kell a helyet az automatikus frissítésének támogatására a frissítés telepítésének megkezdése előtt éles üzem előtti használathoz.

További információkért lásd: [frissítse az ügyfeleket a System Center Configuration Managerben](/sccm/core/clients/manage/upgrade/upgrade-clients) és [ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Tervezi, hogy szolgáltatás időszakokkal szabályozhatja, hogy Helykiszolgálók telepítésekor frissítések:**   
A szolgáltatási segítségével meghatározhat egy olyan időszakot során melyik frissítéseket kell egy helyet a kiszolgáló telepíthető.

Ezzel kontrollálhatja, hogy mikor telepítsék a frissítést a hierarchiába tartozó helyek. További információkért lásd: [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows).

**A telepítő előfeltétel-ellenőrzés futtatása:**   
Ha a frissítés szerepel-e a konzol **elérhető,** egymástól függetlenül futtathatja az előfeltétel-ellenőrző a frissítés telepítése előtt. (Ha a frissítés telepítése a helyen, az előfeltétel-ellenőrző ismét elindul.)

Előfeltétel-ellenőrzés futtatása a konzolt, keresse fel **felügyeleti > Áttekintés > Felhőszolgáltatások > frissítések és karbantartás.** Kattintson a jobb gombbal **frissítőcsomag Configuration Manager 1702**, és válassza a **előfeltételek ellenőrzésének futtatása**.

Kezdő- és az Előfeltételek ellenőrzése majd figyelési kapcsolatos további információkért lásd: **3. lépés: Az előfeltétel-ellenőrzés futtatása frissítés telepítése előtt** témakör [konzolon belüli frissítések telepítése a System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Ha az előfeltétel-ellenőrző önállóan vagy egy frissítés telepítésének részeként fut, a folyamat frissíti néhány termék forrásfájlok helykarbantartási feladatokhoz használt. Ezért az előfeltétel-ellenőrző futtatása előtt azonban után a frissítés telepítésekor, ha egy Helyadatbázis-karbantartási feladat végrehajtásához futtassa **Setupwpf.exe** (Configuration Manager telepítő) a CD-ről. Legújabb mappában található a helykiszolgálón.

**Helyek frissítése:**   
Most már készen áll a hierarchiában a frissítés telepítésének elindítása. A frissítés telepítésével kapcsolatos további információkért lásd: [konzolon belüli frissítések telepítéséhez.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Azt javasoljuk, hogy szeretné-e minden helyen munkaidőn kívülre a frissítés telepítése, amikor a frissítés és a műveletek újra kell telepítenie a hely összetevőinek és a helyrendszerszerepkörök telepítési folyamata hatással lesz a legalább az üzleti tevékenységre.

További információ: [A System Center Configuration Manager frissítései](/sccm/core/servers/manage/updates).

## <a name="post-update-checklist"></a>POST frissítési ellenőrzőlistája
Tekintse át a következő műveleteket a frissítés telepítésének befejezése után.
1.    Győződjön meg arról, hogy a helyek közötti replikálás aktív. A konzolon megtekintheti **figyelés** > **Helyhierarchia**, és **figyelés** > **adatbázis-replikáció** a problémák vagy megerősítése, hogy a replikációs hivatkozások aktívak-e.
2.    Győződjön meg arról, hogy minden egyes helykiszolgálóján és helyrendszer-szerepkör frissített verzióját 1702. A konzolon adja hozzá a választható oszlop **verzió** beleértve az egyes csomópontok megjelenítéséhez **helyek** és **terjesztési pontok**.

 Ha szükséges, a helyrendszer-szerepkör újra fogja automatikusan az új verzióra frissíteni. Fontolja meg a távoli helyrendszerek arról, hogy nem sikerült frissíteni.
3.    Konfigurálja újra a felügyeleti pontokhoz az elsődleges helyeken, a frissítés előtt letiltott adatbázis-replikáit.
4.  Konfigurálja újra a frissítés előtt letiltott adatbázis-karbantartási feladatokat.
5.    Ha konfigurálni ügyféltesztelés a frissítés telepítése előtt, frissítse az ügyfelek száma a létrehozott csomagot.

