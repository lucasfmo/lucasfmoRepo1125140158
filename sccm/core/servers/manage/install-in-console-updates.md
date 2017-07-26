---
title: "A konzolon belüli frissítések |} Microsoft Docs"
description: "A System Center Configuration Manager telepítése a konzolon belüli frissítések beszerzéséhez a Microsoft Felhő szinkronizálása."
ms.custom: na
ms.date: 4/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 29a55948a1897e1345ba14ec685b9288a844feaa
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="install-in-console-updates-for-system-center-configuration-manager"></a>A System Center Configuration Manager konzolon elérhető frissítések telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a Microsoft felhőszolgáltatással való frissítés szinkronizálja. Ezután telepítheti a frissítéseket a Configuration Manager konzolon.

## <a name="get-available-updates"></a>Az elérhető frissítések beszerzése
A rendszer csak azokat a frissítéseket tölti le és teszi elérhetővé a hierarchia számára, amelyek megfelelnek az adott infrastruktúrának és verziónak. A szinkronizálás lehet automatikus vagy kézi, attól függően, hogy hogyan konfigurálja a szolgáltatáskapcsolódási pont a hierarchiában:

-   **Online módban**a szolgáltatáskapcsolati pont automatikusan csatlakozik a Microsoft felhőszolgáltatásához, és letölti a megfelelő frissítéseket.  

     Alapértelmezés szerint a Configuration Manager ellenőrzi az új frissítések 24 óránként. Ellenőrizheti a frissítések azonnal kiválasztásával **frissítések keresése** a a **felügyeleti** > **frissítés és karbantartás** csomópont a Configuration Manager konzol. (Előtt 1702 verziója, ez a csomópont alatt állt **felügyeleti** > **Felhőszolgáltatások**.)

-   A **kapcsolat nélküli módban**, a szolgáltatáskapcsolódási pont nem csatlakozik a Microsoft felhőalapú szolgáltatásából. Manuálisan kell [a szolgáltatáskapcsolódási eszköz használata a System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md) letöltéséhez és majd a rendelkezésre álló frissítések importálásához.  

> [!NOTE]  
>  Mellett a frissítéseket, ha a Microsoft felhőszolgáltatással való szinkronizálás, sávon kívüli javítások, amelyek használatával telepítheti a [Frissítésregisztráló eszköz](http://technet.microsoft.com/library/mt691544.aspx) rendszer is importálja a parancsmagmodulokat a konzolon, ahol majd kiválaszthatja a telepítéséhez.  

Szinkronizálásuk után megtekintheti azokat a Configuration Manager konzolon nyissa meg a **felügyeleti** > **frissítés és karbantartás** csomópont:  

-   A még nem telepített frissítések állapota **Elérhető**.

-   A már telepített frissítések állapota **Telepített**.  Csak a legutóbb telepített frissítés jelenik meg. Kiválaszthatja a **előzmények** gombot a menüszalagon megtekintéséhez korábban telepített frissítések.



A szolgáltatáskapcsolódási pont konfigurálása előtt ismerje meg, és tervezze meg a további használja. A következő használatát befolyásolhatja, hogyan konfigurálja a helyrendszer-szerepkör:  

-   A szolgáltatáskapcsolódási pont a hellyel kapcsolatos használati információk feltöltésére szolgál. A Microsoft felhőszolgáltatása ezen információk alapján azonosítja az infrastruktúra adott verziójához rendelkezésre álló frissítéseket. További információkért lásd: [diagnosztikai és használati adatokat a System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

-   A szolgáltatáskapcsolódási pont a Microsoft Intune és a Configuration Manager helyszíni mobileszköz-kezelés használatával kezelésére szolgál. További információkért lásd: [hibrid mobileszköz-kezelés (MDM) a System Center Configuration Manager és a Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

Jobb megértése érdekében mi történik, ha a frissítések letöltése, lásd:  

-   [Folyamatábra – a System Center Configuration Manager frissítéseinek letöltése](../../../core/servers/manage/download-updates-flowchart.md)

-   [Folyamatábra – a System Center Configuration Manager frissítési replikáció](../../../core/servers/manage/update-replication-flowchart.md)  

## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>Frissítések és szolgáltatások megtekintéséhez és kezeléséhez engedélyek hozzárendelése
A konzol frissítések megtekintéséhez egy felhasználó kell hozzárendelni egy szerepkör alapú felügyelet biztonsági szerepkör, amely magában foglalja a biztonsági osztályt **csomagok**. Ez az osztály megtekintése és kezelése a Configuration Manager konzol frissítések hozzáférést biztosít.    

**A Frissítési csomagok osztály bemutatása:**  
Alapértelmezés szerint a **Frissítési csomagok** (SMS_CM_Updatepackages) a következő beépített biztonsági szerepkörök részét képezi, és az alább listázott engedélyeket biztosítja:
 -  **Teljes körű rendszergazda** a **Módosítás** és **Olvasás** engedélyekkel:
    -   A biztonsági szerepkör és a hozzáférés egy felhasználó a **összes** biztonsági hatókör megtekintheti frissítések, telepítse a frissítéseket és szolgáltatások engedélyezése a telepítés során, és a frissítés telepítését követően az egyes szolgáltatások engedélyezése.
    - A biztonsági szerepkör és a hozzáférés egy felhasználó a **alapértelmezett** biztonsági hatókör is frissítések, frissítések telepítése és a telepítés során a szolgáltatások engedélyezése és megtekintése szolgáltatások egy frissítés telepítése után. De a felhasználó nem engedélyezhető a szolgáltatások, a frissítés telepítése után.

- **Csak olvasási engedéllyel rendelkező elemző** az **Olvasás** engedéllyel:
  -  A biztonsági szerepkör és a hozzáférés egy felhasználó a **alapértelmezett** hatókörű megtekinthesse a frissítéseket, de nem telepíti azokat. A felhasználó is megtekintheti szolgáltatásait után a frissítés telepítve van, de nem engedélyezhető.

**A frissítések és karbantartás szükséges engedélyek:**   
  - Olyan fiókot használjon, amelynek biztonsági szerepköre tartalmazza a **Frissítési csomagok** osztályt, illetve a **Módosítás** és **Olvasás** engedélyt.
  - A fióknak rendelkeznie kell az **Alapértelmezett** hatókörrel is.

**Csak a frissítések megtekintéséhez Permissoins**:
  - Olyan fiókot használjon, amelynek biztonsági szerepköre tartalmazza a **Frissítési csomagok** osztályt és az **Olvasás** engedélyt.
  - A fióknak rendelkeznie kell az **Alapértelmezett** hatókörrel is.

**Frissítések telepítése után a szolgáltatások engedélyezéséhez szükséges engedélyek:**
  -  Olyan fiókot használjon, amelynek biztonsági szerepköre tartalmazza a **Frissítési csomagok** osztályt, illetve a **Módosítás** és **Olvasás** engedélyt.
  -  A fióknak rendelkeznie kell az **Összes** hatókörrel is.






##  <a name="bkmk_beforeinstall"></a> Mielőtt telepít egy a konzolon elérhető frissítést:  
 A Configuration Manager konzolon belül a frissítés telepítése előtt, tekintse át az alábbi lépéseket.  

###  <a name="bkmk_step1"></a>1. lépés: Olvassa el a frissítési ellenőrzőlistát  
Tekintse át a hozzá kapcsolódó ellenőrzőlistát a frissítés megkezdése előtt elvégzendő műveletekről:

- Frissítse 1606: Lásd: [ellenőrzőlista a telepítés frissítéséhez 1606](../../../core/servers/manage/checklist-for-installing-update-1606.md).  

- Frissítse a vagy 1606 1610: Lásd: [ellenőrzőlista a telepítés frissítéséhez 1610](../../../core/servers/manage/checklist-for-installing-update-1610.md).  

- Frissítse a 1606 vagy 1610 1702: Lásd: [ellenőrzőlista a telepítés frissítéséhez 1702](../../../core/servers/manage/checklist-for-installing-update-1702.md).

###  <a name="bkmk_step2"></a>2. lépés: A frissítés telepítése előtt az adatbázis-frissítés teszteléséhez  
Ebben a lépésben információk vonatkoznak, csak ha telepít egy *frissítése* a System Center Configuration Manager-hely. Ha Ön *frissítése* a System Center 2012 Configuration Manager-hely System Center Configuration Manager, lásd: [a hely adatbázis-frissítés teszteléséhez](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager#a-namebkmktesta-test-the-site-database-upgrade).

Mielőtt új frissítést telepít a hierarchiában, például 1610 frissítése, tesztelheti a frissítést a Helyadatbázis. A parancssori kapcsoló, amellyel tesztelheti a frissítést telepítését a Helyadatbázis biztonsági másolatának neve **testdbupgrade**.  

Ha a frissítés telepítése nem sikerül, akkor nem kell hajtson végre egy helyhelyreállítást. Ehelyett újra a frissítés telepítését. Igen Bár a tesztelési célú frissítését az adatbázis kevésbé létfontosságú, mint például a System Center 2012 Configuration Manager korábbi verziók, továbbra is ajánlott.


#### <a name="to-run-testdbupgrade-before-installing-an-update"></a>A testdbupgrade futtatása frissítés telepítése előtt  

1.  A forrás-fájlokat az beszerzése a **CD-ről. Legújabb** mappát a hely, amely a verzió fut, amely azt tervezi, hogy frissíteni. Ez egy, amikor egy helyet előbb telepítenie kell, vagy a System Center Configuration Manager verziója tesztkörnyezetben.  

     A **CD-ről. Legújabb** mappát a hely van adott verzió forrásfájljait. Ezeket a forrásfájlokat kell használnia a helyadatbázis tesztfrissítésének futtatásához. További információért lásd: [A System Center Configuration Manager CD.Latest mappája](../../../core/servers/manage/the-cd.latest-folder.md).  

     Például ha a webhely 1606 verzióját futtatja, és frissíti a 1610, ha előbb telepítik azokra CD-ről. Legújabb mappa verzióra 1610 már frissítve van helyről. Általában egy új és átmeneti helyet telepít egy tesztkörnyezetben, és frissítse a, verzióra 1610 CD létrehozásához. A szükséges fájlokat tartalmazó legfrissebb mappát.  

2.  Másolja a CD-n. Legfrissebb mappát egy helyre a tesztcélú adatbázis-frissítés futtatásához használandó SQL Server-példányon.

3.  Készítsen biztonsági másolatot a helyadatbázisról, amely a frissítés teszteléséhez, és ezt a Configuration Manager-hely nem üzemeltető SQL Server példányának állítsa vissza, hogy az adatbázis másolatát. Az SQL Server-példány az SQL Server ugyanazon kiadását kell használnia, a helyadatbázissal.  

4.  Az adatbázis-példány visszaállítását követően futtassa a **telepítő** CD-ről. Legújabb mappába másolt a labor- vagy tesztkörnyezetben környezetből. A telepítő futtatásakor használja a **/TESTDBUPGRADE** parancssori kapcsolót. Ha az adatbázispéldányt tartalmazó SQL Server-példány nem az alapértelmezett példány, meg kell adni az adatbázis másolatát tartalmazó példányt azonosító parancssori argumentumokat.  

     Tegyük fel például, hogy SMS_ABC nevű Helyadatbázis frissítését tervezi. A helyadatbázis másolatát egy DBTest nevű, támogatott SQL Server-példányon állítja vissza. A Helyadatbázis példányának frissítési teszteléséhez a következő parancsot használja: **Setup.exe/testdbupgrade DBtest\CM_ABC**  

     A következő helyen forrás-adathordozóján a System Center Configuration Manager található Setup.exe: **SMSSETUP\BIN\X64**.  

5.  Az adatbázis frissítési tesztjének futtatásához használt SQL Server-példányon figyelje a rendszermeghajtó gyökérmappájában található ConfigMgrSetup.log fájlban, hogyan halad, illetve sikeres-e a folyamat.  

     Ha a tesztfrissítés sikertelen, javítsa ki a Helyadatbázis frissítésének sikertelenségét okozó problémákat, hozzon létre egy új biztonsági másolatot készít a helyadatbázisról, és tesztelje a frissítést a Helyadatbázis új másolati.  

     Ha a folyamat sikerült, törölheti az adatbázis másolati példányát.  

    > [!NOTE]  
    >  A tesztfrissítéshez használt helyadatbázis-példány visszaállítása más helyen helyadatbázisként történő használatra nem támogatott.  

###  <a name="bkmk_step3"></a>3. lépés: Az előfeltétel-ellenőrzés futtatása frissítés telepítése előtt  
Mielőtt telepít egy frissítést, tanácsos futtatni a frissítés előfeltétel-ellenőrzését. Ha futtatja az előfeltétel-ellenőrzést a frissítés telepítése előtt:  

-   A frissítési fájlokat más helyekre, a frissítés telepítése előtt replikálódnak.  

-   Az előfeltétel-ellenőrzés automatikusan újra elindul. Ha úgy dönt, hogy a frissítés telepítéséhez.  

Később Ha telepíti a frissítést, lehetősége van a frissítés előfeltétel-ellenőrzés vonatkozó figyelmeztetések mellőzését konfigurálásához.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>Az előfeltétel-ellenőrzés futtatása a frissítés telepítése előtt  

1.  Nyissa meg a Configuration Manager konzol **felügyeleti** > **frissítés és karbantartás**.   

2.  Kattintson a jobb gombbal arra a frissítésre, amelynek ellenőrizni szeretné az előfeltételeit.  

3.  Válassza az **Előfeltételek ellenőrzésének futtatása**parancsot.  

     Az előfeltétel-ellenőrzés futtatásakor replikálódik a frissítés tartalma a gyermekhelyekre.  Megtekintheti a distmgr.log naplófájlban a helyen server annak ellenőrzéséhez, hogy a tartalom sikeres replikálódásból.  

4.  A Configuration Manager konzolon, az ellenőrzés eredményeit látogassa meg a **figyelés** > **frissítések és karbantartás állapot** , és tekintse meg az Előfeltételek állapotát. További részleteket talál a helykiszolgáló ConfigMgrPrereq.log nevű fájljában is.  



##  <a name="bkmk_install"></a> A konzolon elérhető frissítések telepítése  
 Ha készen áll a Configuration Manager konzolon belüli frissítések telepítésére, a hierarchia legfelső szintű hely és megkezdése. Ez lehet a központi adminisztrációs hely vagy önálló elsődleges hely.  

 Azt javasoljuk, hogy szeretné-e telepíteni a frissítést minden helyen munkaidőn kívül. A frissítés és a műveletek újra kell telepítenie a hely összetevőinek és a helyrendszer-szerepkörök telepítésének folyamatát, majd hatással lesz a legalább az üzleti tevékenységre.  

-   A gyermek elsődleges helyek automatikusan telepítik a frissítést azt követően, hogy a központi adminisztrációs hely befejezi frissítés telepítését. Ez az alapértelmezett és ajánlott eljárás. Használhat azonban [szolgáltatási időkeretek Helykiszolgálók számára](/sccm/core/servers/manage/service-windows) szabályozásához, hogy elsődleges hely mikor telepítse a frissítéseket.  

-   A szülőhely frissítése után a Configuration Manager konzolon belül a másodlagos helyeket manuálisan kell frissíteni. A másodlagos helykiszolgálók automatikus frissítése nem támogatott.  

-   Ha a hely frissítése után a Configuration Manager konzol használatával kéri a konzol frissítését.  

-  Miután a kiszolgálóra a frissítést a telepítés sikeresen befejeződött, minden vonatkozó helyrendszerszerepkörök automatikusan frissíti.  Ez csak szerint van a terjesztési pontok. Amikor frissítést telepít, minden terjesztési pontok nem újra kell telepítenie és offline állapotú, egy időben frissítése. Ehelyett a helykiszolgáló beállításai a hely terjessze a tartalmakat a terjesztési pontok egy részhalmazát frissítésének terjesztése egyszerre. Az eredménye, hogy csak néhány terjesztési pontról a frissítés offline állapotba kerülnek. Ez lehetővé teszi, hogy a terjesztési pontok, amelyek még nem kezdett frissíteni vagy, hogy befejeződött a frissítés online és kell tartalmat biztosítania ügyfelek maradniuk.


###  <a name="bkmk_overview"></a> A konzolon belüli frissítés telepítésének áttekintése  
**1. A frissítés telepítésének indításakor**  
Megnyílik a Frissítés varázsló, amely megjeleníti azoknak a termékterületeknek a listáját, amelyekre a frissítés vonatkozik.  

-   A varázsló **Általános** lapján elvégezheti az **Előfeltételekre vonatkozó figyelmeztetések**beállítását.  
      -   Az előfeltételekkel kapcsolatos hibák mindig leállítják a frissítés telepítését. Hibák sikeresen újra megkísérelhetné a frissítés telepítése előtt javítsa. További információk: [Újrapróbálkozás sikertelen frissítés esetén](#bkmk_retry) .  

    -   Az előfeltételekre vonatkozó frissítések is leállíthatják a telepítést. Figyelmeztetések kell kijavítani, mielőtt újra megpróbálja a frissítés telepítését. További információk: [Újrapróbálkozás sikertelen frissítés esetén](#bkmk_retry) .  
    -   A beállítás bejelölésével **bármely előfeltétel-ellenőrzés figyelmeztetéseinek mellőzése, és ez a frissítés attól függetlenül a hiányzó követelményekre**, olyan feltételt állít be a frissítés telepítése, amely figyelmen kívül hagyja az előfeltételekre vonatkozó figyelmeztetéseket. Ez lehetővé teszi, hogy a frissítés a telepítés folytatásához. Ha nem ezt a beállítást, a frissítés telepítése leáll figyelmeztetés jelentkezése esetén. Kivéve, ha korábban már futtattak az előfeltétel-ellenőrzés és a hely rögzített előfeltételekkel kapcsolatos figyelmeztetéseket, ez a beállítás használata nem ajánlott.  

      Mind a **felügyeleti** és **figyelés** munkaterületek, a frissítések és karbantartás csomópont tartalmazza az egy gombot a menüszalagon nevű **előfeltételekre vonatkozó figyelmeztetések mellőzését**. A gomb elérhetővé válik, amikor egy frissítési csomagot sikertelen előfeltétel-ellenőrzés figyelmeztetéseinek miatt a telepítés befejezéséhez. Például, ha a beállítás használatával előfeltételekre vonatkozó figyelmeztetések mellőzését nélkül telepít egy frissítést (a frissítések varázslóban), és, hogy frissítse az telepítési állomások állapotának előfeltételekkel kapcsolatos figyelmeztetés, de nincs hiba, később választhat **előfeltételekre vonatkozó figyelmeztetések mellőzését** egy automatikus folytatása, amely majd figyelmen kívül hagyja az előfeltételekkel kapcsolatos figyelmeztetéseket frissítés telepítés elindítása a szalagról. Ha ezt a beállítást használja, néhány perc múlva automatikusan folytatja a frissítés telepítését.



-   Ha egy frissítés a Configuration Manager-ügyfél vonatkozik, lehetősége lesz az ügyfélfrissítés korlátozott számú ügyféllel tesztelésére. További információkért lásd: [ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

**2. A frissítés telepítése során**  
A Configuration Manager frissítés telepítésének részeként:  

-   Újratelepíti az érintett összetevők, például a helyrendszer-szerepkörök vagy a Configuration Manager konzolon.  

-   A kiválasztott beállítások végzett ügyféltesztelésre vonatkozóan, és az ügyfelek frissítéseit kezeli [automatikus ügyfélfrissítések](https://technet.microsoft.com/library/mt627885.aspx).  

-   Nem kell indítsa újra a helyrendszer-kiszolgálók a frissítés részeként (kivéve, ha a helyrendszerszerepkörök előfeltételének részeként telepítve van a .NET).  

> [!TIP]  
>  Frissítések telepítése, a Configuration Manager is frissíti a CD-n. Legfrissebb mappát. Használja ezt a mappát a hely helyreállítása során.  

**3. A frissítések előrehaladásának figyeléséhez, telepítés közben**  
A következők segítségével figyelheti a haladást:  

-   A Configuration Manager konzolon: **Felügyeleti** > **frissítés és karbantartás** csomópont. Ez a csomópont minden frissítés telepítési állapotát megjeleníti.


-   A Configuration Manager konzolon: **Figyelési** > **áttekintése** > **frissítések és karbantartás állapot** csomópont. Ez a csomópont csak a jelenleg telepített frissítési csomag telepítési állapotát megjeleníti.  

  A frissítési csomag telepítése a következő fázisok megkönnyítése érdekében a figyelési van lebontva. Az egyes fázisokban további részleteket tartalmaz mely naplófájl további információk megtekintéséhez.:  
    -   **Töltse le** (ebben a fázisban vonatkozik csak a legfelső szintű helyet, ahol a szolgáltatás kapcsolódási pont helyrendszerszerepkör telepítve van.)
    -   **Replikáció**
    -   **Előfeltételek ellenőrzése**
    -   **Telepítés**
    -   **A telepítés után** (ebben a fázisban a 1610 verziójával szervizcsomagjától kezdve érhetők el.)

-   Megtekintheti a **CMUpdate.log** fájlt  **&lt;Configmgr_telepítési_könyvtára > \Logs**  

**4. A frissítés telepítésének befejeződésekor**  
Az első hely frissítésének befejeződése után:  

-   A gyermek elsődleges helyek automatikusan telepítik a frissítést. Nincs szükség további műveletre.  

-   Másodlagos helyeket manuálisan frissíteni kell a a Configuration Manager konzolon.
> [!TIP]
> Bár a másodlagos hely verziója nem jeleníti meg a konzolon, a Configuration Manager SDK segítségével ellenőrizze a hely verziója. Lásd: [SMS_Site kiszolgáló WMI-osztály](https://technet.microsoft.com/library/hh442832(CMSDK.16).aspx).


-   A hierarchia vegyes verziójú üzemmódban működik, amíg a hierarchia összes helyén be nem fejeződik az új verzióra történő frissítés. További információk: [Együttműködés a System Center Configuration Manager különböző verziói között](../../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

**5.   A Configuration Manager konzolok frissítése**  
A központi adminisztrációs hely vagy elsődleges hely frissítése után minden egyes Configuration Manager konzolt, amely ahhoz a helyhez csatlakozik frissíteni kell. A rendszer a következő esetekben kéri a konzol frissítését:  

-   A konzol megnyitásakor.  

-   Ha egy megnyitott konzol új csomópontjának Ugrás.  

Azt javasoljuk, hogy a frissítés azonnal.  

Miután a konzol frissítése befejeződött, ellenőrizze, hogy helyes-e a konzol és a hely verziója. Ugrás a **System Center Configuration Manager** a konzol bal felső sarkában.  

###  <a name="bkmk_toptier"></a> A frissítés telepítésének elindítása a legfelső szintű helyen  
A hierarchia legfelső szintű helyen a Configuration Manager konzolon lépjen **felügyeleti** > **frissítés és karbantartás**, jelölje be egy **elérhető** frissítése, és kattintson a **frissítési csomag telepítése**.  

###  <a name="bkmk_secondary"></a> A frissítés telepítésének elindítása másodlagos helyen  
Miután a másodlagos helyek szülő elsődleges hely frissült, frissítheti a másodlagos hely a Configuration Manager konzolon.  Ehhez használja a **Másodlagos hely frissítése varázslót**.  

1.  Nyissa meg a a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**, jelölje ki a frissíteni kívánt, majd a kezdőlap a lapon, a a **hely** csoportjában válassza **frissítése**.  

2.  Indítsa el a másodlagos hely frissítését: kattintson az **Igen** lehetőségre.  

Egy másodlagos hely a frissítés telepítésének figyelésére, válassza ki a másodlagos helykiszolgálón. Végül a a **Home** lap a **hely** csoportjában válassza **telepítési állapot megjelenítése**. Azt is megteheti, hogy felveszi a **Verzió** oszlopot a konzol képernyőjére, így az összes másodlagos hely verzióját megtekintheti.  

Miután egy másodlagos hely frissítése sikeres volt, ha az állapotot a konzol frissítése sikertelen, vagy felajánlja a frissítést nem sikerült, használja a **újrapróbálkozás** lehetőséget. Ezt a beállítást nem telepíti újra a frissítést, a másodlagos helyek frissítés sikeres telepítése, de arra kényszeríti a konzol állapotának frissítése.


##  <a name="bkmk_retry"></a> Újrapróbálkozás sikertelen frissítés esetén  
Ha egy frissítés nem telepíthető, tekintse át a konzolon belüli visszajelzés feloldását figyelmeztetések és hibák azonosítására. További részleteket talál a helykiszolgáló ConfigMgrPrereq.log nevű fájljában is. A telepít egy frissítést újra, mielőtt kell javítsa ki a hibákat, és figyelmeztetések meg kell határoznia.  

Ha készen áll a telepít újra egy frissítést, válassza ki a frissítés sikertelen, és válasszon vonatkozó beállítást. A frissítés telepítési újrapróbálási viselkedése attól függ, a csomópont az először az újra gombra, és az újrapróbálkozási beállítást használja.  

1.  **Újrapróbálkozás hierarchia egésze számára történő telepítéssel:**  
Ha a frissítés a következő állapotok valamelyikében van, megpróbálkozhat azzal, hogy a teljes hierarchia számára telepíti újra a frissítést:  

    -   Az előfeltétel-ellenőrzés figyelmeztetésekkel lefutott egy vagy több, és a frissítés varázslóban nincs beállítva az előfeltétel-ellenőrzés figyelmeztetések mellőzését előíró beállítást. (A frissítés a következő **számolt figyelmeztetés figyelmen kívül hagyása** a a **frissítések és karbantartás** csomópont **nem**.)   
    -   Nem felelt meg az előfeltételek ellenőrzésén    
    -   Sikertelen telepítés
    -   A tartalomnak a helyre történő replikálása sikertelen volt   

    Ugrás a **felügyeleti** > **frissítés és karbantartás**, válassza ki a frissítést, és válassza a következők egyikét:  

    -   **Próbálja meg újra** - futtatásakor **újra** ebből a csomópontból, a frissítés elindul telepítse újra, és automatikusan figyelmen kívül hagyja előfeltételekkel kapcsolatos figyelmeztetéseket. Emellett ha korábban sikertelen volt a replikálás, a rendszer ismét elvégzi a tartalmak replikálását.
    - **Előfeltételekre vonatkozó figyelmeztetések mellőzését** -verziótól kezdődően verzió 1606, ha a frissítés telepítése leáll figyelmeztetés miatt dönthet **előfeltételekre vonatkozó figyelmeztetések mellőzését**. Ezzel néhány perc elteltével újraindul a frissítések telepítése, ezúttal az előfeltételekre vonatkozó figyelmeztetések mellőzése mellett.   

2.  **Újrapróbálkozás a hely számára történő telepítéssel:**  
 Ha a frissítés a következő állapotok valamelyikében van, megpróbálkozhat azzal, hogy egy konkrét hely számára telepíti újra a frissítést:  

    -   Az előfeltétel-ellenőrzés figyelmeztetésekkel lefutott egy vagy több, és figyelmen kívül hagyja az előfeltétel-ellenőrzés figyelmeztetéseinek kapcsoló nem lett beállítva a frissítés varázslóban (érték, a frissítések **számolt figyelmeztetés figyelmen kívül hagyása** a frissítések és karbantartás csomópont **nem**.)  
    -   Nem felelt meg az előfeltételek ellenőrzésén    
    -   Sikertelen telepítés    

    Nyissa meg a **Figyelés** > **Áttekintés** > **Helykarbantartás állapota**csomópontot, válassza ki a frissítést, és tegye az alábbiak valamelyikét:

       - **Próbálja meg újra** - futtatásakor **újra** ebből a csomópontból, indítsa újra a telepítőt a frissítés csak adott helyen. Futó eltérően **újra** a a **frissítés és karbantartás** csomópont, ily módon tett újrapróbálkozás hagyja figyelmen kívül az előfeltételekre vonatkozó figyelmeztetéseket.
       -    **Előfeltételekre vonatkozó figyelmeztetések mellőzését** -verzió 1606, kezdve, ha a frissítés telepítése leáll figyelmeztetés miatt, majd kattintson **előfeltételekre vonatkozó figyelmeztetések mellőzését**. Ezzel néhány perc elteltével újraindul a frissítések telepítése, ezúttal az előfeltételekre vonatkozó figyelmeztetések mellőzése mellett.

##  <a name="bkmk_after"></a> Miután települ egy frissítés egy helyre  
A következő ellenőrzőlista segítségével elvégezheti az általános feladatok és konfigurációs műveleteket a hely frissítése után.   

**Ellenőrizze, hogy helyek közötti replikálás aktív:** A Configuration Manager konzolt keresse meg a következő helyeken, az állapot megtekintése, és győződjön meg arról, hogy a replikáció aktív:  

-   **Figyelés** > **Áttekintés** > **Helyhierarchia**  

-   **Figyelés** > **Áttekintés** > **Adatbázis replikálása**  

További információkért lásd: [figyelő hierarchia és replikációs infrastruktúra a System Center Configuration Managerben](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) és [kapcsolatos a Replication Link Analyzer](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA).  

 **Győződjön meg arról, hogy Helykiszolgálók és a távoli helyrendszer-kiszolgálók újraindítása (ha szükséges):** Ellenőrizze a hely infrastruktúráját, és győződjön meg arról, hogy érintett Helykiszolgálók és (a helykiszolgálóhoz képest távoli) helyrendszer-kiszolgálók újraindítása sikeresen megtörtént.  Ez általában egy várható üzenet, csak akkor, ha a Configuration Manager telepíti a .NET-egy helyrendszer-szerepkör előfeltételeként.  

 **Különálló Configuration Manager-konzolok frissítése:** Győződjön meg arról, hogy minden távoli Configuration Manager konzolt ugyanarra a verzióra frissítés. A rendszer a következő esetekben kéri a konzol frissítését:  

-   A konzol új csomópontjának Ugrás.  

-   A konzol megnyitásakor.

**Konfigurálja újra az adatbázis-replikák beállítása felügyeleti pontokhoz az elsődleges helyeken:** Ha az adatbázis-replikákat használ a felügyeleti pontokhoz az elsődleges helyeken, el kell távolítania az adatbázis-replikákat a hely frissítése előtt. Miután frissít egy elsődleges helyet, konfigurálja újra a felügyeleti pontok adatbázis-replikáit. További információk: [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Konfigurálja újra a frissítés előtt letiltott adatbázis-karbantartási feladatokat:** Ha letiltotta az adatbázis [karbantartási feladatok a System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) frissítés helyen, konfigurálja újra ezeket a feladatokat a helyen. A frissítés előtt a helyükön lévő azonos beállításokat használ.  

**Frissítse az ügyfeleket:** A meglévő ügyfelek frissítésével, illetve az új ügyfelek telepítésével kapcsolatos információkért lásd: [A Windows rendszerű számítógépekhez készült ügyfelek frissítése a System Center Configuration Managerben](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

**További beállításokat:** Tekintse át a módosításokat, hogy a frissítés megkezdése előtt, majd állítsa vissza a konfigurációk a helyek és hierarchia.  

##  <a name="bkmk_options"></a> A frissítések választható funkcióinak engedélyezése  
Ha olyan frissítést telepít, amely nem kötelező funkciót vagy funkciókat is tartalmaz, engedélyezheti ezeket a funkciókat a hierarchiában.  Után is ezt az időt a frissítés telepítve van, vagy később térjen vissza a konzol is a választható funkcióinak engedélyezése.

Rendelkezésre álló szolgáltatásokat és azok állapotának megtekintése, a konzolon navigáljon **felügyeleti** > **frissítés és karbantartás** > **szolgáltatások**.

Ha egy funkció nem választható, automatikusan települ, és nem jelenik meg a **szolgáltatások** csomópont.  


Egy új funkció vagy a kiadás előtti funkció engedélyezésével, a Configuration Manager-hierarchia kezelője (HMAN) kell feldolgozni a módosítást, mielőtt elérhetővé válik, hogy a szolgáltatás. A módosítás következményeivel feldolgozási gyakran azonnali, de HMAN feldolgozási ciklus függően akár 30 percet is igénybe vehet. A módosítás feldolgozása után újra kell indítania a konzolt, új felhasználói Felületet, az adott szolgáltatáshoz kapcsolódó megtekintése előtt.


##  <a name="bkmk_prerelease"></a> A frissítésekben biztosított előzetes funkciók használata
Előzetes kiadású szolgáltatások olyan funkciókat, amelyek szerepelnek az aktuális ág éles környezetben is tesztelhessék őket. Ezeket a funkciókat nem tekinthető éles kész, de az üzemi környezetben is használható. További tudnivalók előzetes kiadású szolgáltatások engedélyezése őket a környezetben, beleértve: [előzetes kiadású szolgáltatások](/sccm/core/servers/manage/pre-release-features).             


## <a name="known-issues"></a>Ismert problémák

###  <a name="bkmk_faq"></a>Miért nem látom az egyes frissítések a konzolon?  
 Ha nem találja egy adott frissítés (vagy bármilyen frissítést) a konzolon a Microsoft felhőszolgáltatással való sikeres szinkronizálás után, ennek oka lehet:  

-   A frissítés olyan konfigurációt igényel, amelyet az adott infrastruktúra nem használ, vagy a termék aktuális verziója nem teljesít egy olyan előfeltételt, amely szükséges ahhoz, hogy letöltődjön a frissítés.  

     Ha azt feltételezi, hogy, hogy a konfiguráció megfelel a hiányzó frissítés előfeltételei, ellenőrizze, hogy a szolgáltatáskapcsolódási pont online módban van-e. Ezt követően a **frissítések keresése** beállítást a **frissítés és karbantartás** csomópont ellenőrzése.  Ha offline üzemmódban van, a szolgáltatáskapcsolati eszköz segítségével manuálisan szinkronizálhat a felhőszolgáltatással.  

-   A fiókjának nincsenek meg a megfelelő szerepkör alapú felügyelet engedélyekkel megtekinthesse a frissítéseket a Configuration Manager konzol.

    Lásd az aktuális témakör [Frissítések kezelésére vonatkozó engedélyek](../../../core/servers/manage/install-in-console-updates.md#assign-permissions-to-view-and-manage-updates-and-features) fejezetét a frissítések megtekintéséhez, illetve a különböző funkciók konzolból való be- és kikapcsolásához szükséges engedélyek listájáért.

### <a name="why-do-i-see-two-updates-for-version-1610"></a>Miért látom verzió 1610 két frissítéseit
Amikor a webkonzolban megjeleníti frissítések, telepített verzió 1610 két frissítések jelenhet meg. Ezek a frissítések különböző időpontokban rendelkezik. Ez akkor fordul elő, ha az alábbiak egyike igaz:   
-    Egy korábbi (például 1606) telepítése után verzió 1610 váltak elérhetővé

-    Ön hierarchia 1511-es vagy az 1602-es verzió fut, és nem tudták 1606 verzió letöltése

Nincsenek két frissítési verziójához 1610 kiadások, mert a frissítés megjelent néhány apró eltéréstől néhány fájl bináris fájlok után történtek. Ezek a változások nem befolyásolják a funkciókat a Configuration Manager vagy a frissítést.

Ha mindkét frissítések érhetők el a konzolon, ajánlott a frissítés telepítése a korábbi dátumot. Azonban a mindkét ugyanezeket a funkciókat biztosítanak, ha már telepítette az egyik legyen nem kell további beavatkozásra.
-    Ha korábban telepítette a régebbi frissítést, nem kell telepíteni a frissítést az újabb dátummal. Azonban ha az újabb frissítés rendelkező első frissítés telepítése után telepíti, a bináris fájlok frissítéséhez, de semmilyen további változás következik be, és nem kell további műveleteket beavatkozást szükségesek.

-    Ha korábban már telepítette a legújabb frissítést, és telepítse a frissítést a korábbi dátumot, további műveletekre van szükség. Ennek az az oka az újabb bináris fájljait már telepítette nem felülírja az eredeti Update azonos bináris fájlokat.

