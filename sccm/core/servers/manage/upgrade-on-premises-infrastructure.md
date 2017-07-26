---
title: "A helyszíni infrastruktúra frissítése |} Microsoft Docs"
description: "Útmutató: az infrastruktúra, például az SQL Server és a helyrendszerek helyszíni operációs rendszerének frissítése."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ca970dd-e71c-404f-9435-d36e773a0db2
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2e711cce2435957f3e85dad08f17260e1a224fc2
ms.openlocfilehash: c6448932e91a02984ca57cef0b75c10ea3f43fa1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-on-premises-infrastructure-that-supports-system-center-configuration-manager"></a>A System Center Configuration Manager alkalmazást támogató helyszíni infrastruktúra frissítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a témakörben az információk használatával alakítsa ki a kiszolgáló System Center Configuration Manager futtató infrastruktúra frissítésében.  

 - Ha azt szeretné, a System Center Configuration Manager egy korábbi verziójáról a Configuration Manager frissítése, lásd: [frissítése a System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).

- Ha azt szeretné, a System Center Configuration Manager-infrastruktúra frissítése újabb verzióra, lásd: [frissíti a System Center Configuration Manager](/sccm/core/servers/manage/updates).

##  <a name="BKMK_SupConfigUpgradeSiteSrv"></a>Beléptetésihely-rendszerek operációs rendszerének frissítése  
 A Configuration Manager támogatja a helybeni frissítést, az operációs rendszer kiszolgálók, amelyek a helykiszolgálóra és távoli kiszolgálót, amelyhez bármely helyrendszerszerepkörét futtatja, a következő esetekben:  

-   Helyszíni frissítés Windows Server későbbi szervizcsomagra, ha az adott szervizcsomagot a Windows marad a Configuration Manager által támogatott.  
-   Helyben történő frissítés:
    - Windows Server 2012 R2, Windows Server 2016 ([további részletek megtekintéséhez](#upgrade-windows-server-2012-r2-to-2016)).
    - Windows Server 2012, Windows Server 2012 R2 ([további részletek megtekintéséhez](#upgrade-windows-server-2012-to-windows-server-2012-r2)).
    - Ha a Configuration Manager 1602-es verziót használja, vagy később is támogatott, a Windows Server 2008 R2 frissítése a Windows Server 2012 R2 ([további részletek megtekintéséhez](#upgrade-windows-server-2008-r2-to-windows-server-2012-r2)).

    > [!WARNING]  
    >  A Windows Server 2012 R2 rendszerre való frissítés előtt *el kell távolítania a WSUS 3.2 szolgáltatást* a kiszolgálóról.  
    >   
    >  Ez a lépés kritikus információ, az "Új és módosított funkciók" szakaszában talál [Windows Server Update Services áttekintése](https://technet.microsoft.com/library/hh852345.aspx) a Windows Server dokumentációjában.  

A kiszolgálók frissítéséhez a az operációs rendszer frissíti a frissítési eljárásait használhatja.  Tekintse át a következőket:
  -  [Frissítse a Windows Server 2012 R2 lehetőségeket](https://technet.microsoft.com/library/dn303416.aspx) a Windows Server dokumentációjában.  
  - [Windows Server 2016 frissítése és -konvertálási funkcióinak](https://technet.microsoft.com/windows-server-docs/get-started/supported-upgrade-paths) a Windows Server dokumentációjában.

### <a name="upgrade-windows-server-2012-r2-to-2016"></a>Windows Server 2012 R2-ben való 2016 frissítése  
Az operációs rendszer frissítési forgatókönyv rendelkezik a következő feltételeknek:

**A frissítés előtt:**  
-     Távolítsa el a System Center Endpoint Protection (SCEP) ügyfelet. Windows Server 2016 rendelkezik beépített, a Windows Defender, amely az SCEP-ügyfél. Az SCEP-ügyfél jelenléte előfordulhat, hogy a Windows Server 2016-os frissítést.

**: A frissítés után**
-     Győződjön meg arról, a Windows Defender engedélyezve van, állítsa be automatikus indítás és fut-e.
-     Győződjön meg arról, a következő Configuration Manager-szolgáltatások futnak:
  -     SMS_EXECUTIVE
  -     SMS_SITE_COMPONENT_MANAGER


-     Győződjön meg arról a **Windows folyamataktivációs** és **WWW/W3svc** szolgáltatások engedélyezve, állítsa be az automatikus indítás és a következő helyrendszer-szerepkörök (ezek a szolgáltatások le vannak tiltva a frissítés során) szolgáltatásnak futnia:
  -     Helykiszolgáló
  -     Felügyeleti pont
  -     Alkalmazáskatalógus webszolgáltatási pontja
  -     Alkalmazáskatalógus weboldal-elérési pontja


-     Győződjön meg arról, minden helyrendszerszerepkört futtató kiszolgáló továbbra is megfelel az összes a [helyrendszerszerepkörök prequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) , amelyek az adott kiszolgálón futnak. Szükség lehet például, telepítse újra a BITS, WSUS, vagy az IIS adott beállításainak a konfigurálásához.

  Visszaállítása után a hiányzó előfeltételeket, és győződjön meg arról szolgáltatás elindult, és működési még egyszer indítsa újra a kiszolgálót.

**Ismert probléma a távoli Configuration Manager-konzol:**  
Miután frissítette a helykiszolgáló vagy a Windows Server 2016-os az SMS-szolgáltató egy példányát üzemeltető kiszolgáló, a rendszergazda felhasználók nem feltétlenül tudni a Configuration Manager-konzol kapcsolódik a helyhez. A probléma megoldásához manuálisan vissza kell állítania a WMI-ben az SMS rendszergazdák csoport engedélyeit. A helykiszolgálón kell beállítani az engedélyeket, és az SMS-szolgáltató egy példányát üzemeltető minden egyes távoli kiszolgálón:

1. A Microsoft Management Console (MMC) nyissa meg a megfelelő kiszolgálók, és adja hozzá a beépülő modul a **WMI-vezérlő**, majd válassza ki **helyi számítógép**.
2. Az MMC-konzolon nyissa meg a **tulajdonságok** a **WMI-vezérlő (helyi)** válassza ki a **biztonsági** fülre.
3. Bontsa ki a fa legfelső szintű, válassza alább az **SMS** csomópont, és válassza a **biztonsági**.  Győződjön meg arról a **SMS rendszergazdák** csoport a következő engedélyekkel rendelkezik:
  -     Fiók engedélyezése
  -     Távelérés engedélyezése
4. Az a **Biztonság lap** alatt a **SMS** csomópontban jelölje ki a **site_**&lt;*Helykód*> csomópont, és válassza a **biztonsági**. Győződjön meg arról a **SMS rendszergazdák** csoport a következő engedélyekkel rendelkezik:
  -   Metódusok végrehajtása
  -   Szolgáltató írása
  -   Fiók engedélyezése
  -   Távelérés engedélyezése
5. Mentse az engedélyeket, hogy állítsa vissza a hozzáférést a Configuration Manager konzol.

### <a name="windows-server-2012-to-windows-server-2012-r2"></a>A Windows Server 2012, Windows Server 2012 R2 rendszerre

**A frissítés előtt:**
-  A más támogatott forgatókönyveket, ellentétben ebben a forgatókönyvben nem szükséges további szempontok a frissítés előtt.

**: A frissítés után**
  -    Győződjön meg arról a Windows-telepítési szolgáltatás elindult, és fut a következő helyrendszerszerepkörök, (a frissítés során ez a szolgáltatás leáll):
    - Helykiszolgáló
    - Felügyeleti pont
    - Alkalmazáskatalógus webszolgáltatási pontja
    - Alkalmazáskatalógus weboldal-elérési pontja


  -     Győződjön meg arról a **Windows folyamataktivációs** és **WWW/W3svc** szolgáltatások engedélyezve, állítsa be az automatikus indítás és a következő helyrendszer-szerepkörök (ezek a szolgáltatások le vannak tiltva a frissítés során) szolgáltatásnak futnia:
    -     Helykiszolgáló
    -     Felügyeleti pont
    -     Alkalmazáskatalógus webszolgáltatási pontja
    -     Alkalmazáskatalógus weboldal-elérési pontja


  -     Győződjön meg arról, minden helyrendszerszerepkört futtató kiszolgáló továbbra is megfelel az összes a [helyrendszerszerepkörök prequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) , amelyek az adott kiszolgálón futnak. Szükség lehet például, telepítse újra a BITS, WSUS, vagy az IIS adott beállításainak a konfigurálásához.

  Visszaállítása után a hiányzó előfeltételeket, és győződjön meg arról szolgáltatás elindult, és működési még egyszer indítsa újra a kiszolgálót.

### <a name="upgrade-windows-server-2008-r2-to-windows-server-2012-r2"></a>Windows Server 2008 R2 frissítése a Windows Server 2012 R2 rendszerre
Az operációs rendszer frissítési forgatókönyv rendelkezik a következő feltételeknek:  

**A frissítés előtt:**
-     Távolítsa el a WSUS 3.2-es verzióját.  
    Kiszolgálói operációs rendszert Windows Server 2012 R2 rendszerre való frissítés előtt el kell távolítania a WSUS 3.2-es verzióját a kiszolgálóról. Ez a lépés kritikus kapcsolatos információkért tekintse meg az új és módosított funkciók című Windows Server Update Services áttekintése a Windows Server dokumentációjában.

**: A frissítés után**
  -    Győződjön meg arról a Windows-telepítési szolgáltatás elindult, és fut a következő helyrendszerszerepkörök, (a frissítés során ez a szolgáltatás leáll):
    - Helykiszolgáló
    - Felügyeleti pont
    - Alkalmazáskatalógus webszolgáltatási pontja
    - Alkalmazáskatalógus weboldal-elérési pontja


  -     Győződjön meg arról a **Windows folyamataktivációs** és **WWW/W3svc** szolgáltatások engedélyezve, állítsa be az automatikus indítás és a következő helyrendszer-szerepkörök (ezek a szolgáltatások le vannak tiltva a frissítés során) szolgáltatásnak futnia:
    -     Helykiszolgáló
    -     Felügyeleti pont
    -     Alkalmazáskatalógus webszolgáltatási pontja
    -     Alkalmazáskatalógus weboldal-elérési pontja


  -     Győződjön meg arról, minden helyrendszerszerepkört futtató kiszolgáló továbbra is megfelel az összes [helyrendszerszerepkörök perquisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) , amelyek az adott kiszolgálón futnak. Szükség lehet például, telepítse újra a BITS, WSUS, vagy az IIS adott beállításainak a konfigurálásához.

  Visszaállítása után a hiányzó előfeltételeket, és győződjön meg arról szolgáltatás elindult, és működési még egyszer indítsa újra a kiszolgálót.


### <a name="unsupported-upgrade-scenarios"></a>Nem támogatott forgatókönyvek
A következő Windows Server frissítési forgatókönyveket kapcsolatban gyakran feltett, de nem támogatja a Configuration Manager:  

-   Windows Server 2008, Windows Server 2012 vagy újabb  
-   Windows Server 2008 R2, Windows Server 2012-re



##  <a name="BKMK_SupConfigUpgradeClient"></a>Configuration Manager-ügyfelek operációs rendszerének frissítése  
 A Configuration Manager támogatja az operációs rendszer helyben frissítés a Configuration Manager-ügyfelek a következő esetekben:  

-   Helyszíni frissítés a Windows későbbi szervizcsomagra, ha az adott szervizcsomagot marad a Configuration Manager által támogatott.  

-   Frissítés a Windows támogatott verziójából származó Windows 10-re. További információk: [A Windows frissítése a legújabb verzióra a System Center Configuration Managerrel](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md).  

-   A Windows 10-buildek karbantartási frissítései.  További információ: [A Windows mint szolgáltatás kezelése System Center Configuration Managerrel](../../../osd/deploy-use/manage-windows-as-a-service.md).  

##  <a name="BKMK_SupConfigUpgradeDBSrv"></a>A Helyadatbázis-kiszolgálón futó SQL Server frissítése  
  A Configuration Manager támogatja az SQL támogatott verziójáról az SQL Server helyszíni frissítés a Helyadatbázis-kiszolgálón. Az SQL Server frissítési forgatókönyveket, ebben a szakaszban a Configuration Manager által támogatott, és minden egyes forgatókönyv követelményei közé tartozik.

 Az SQL Server Configuration Manager által támogatott verzióival kapcsolatos információkért lásd: [SQL Server-verziók támogatása a System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

 **Frissítse az SQL Server szervizcsomag-verzióhoz:**    
 A Configuration Manager támogatja a frissítés az SQL Server egy későbbi szervizcsomagra, ha az adott SQL Server szervizcsomagot marad a Configuration Manager által támogatott.

 Ha a hierarchiában több Configuration Manager-helyek, minden helyen futtatható különböző szervizcsomag-verzió az SQL Server, és nincs korlátozás a helyek milyen sorrendben, amelyben frissítsék a helyadatbázishoz használt SQL Server szervizcsomag-verzióhoz.

 **Frissítsen az SQL Server új verziójára:**   
 A Configuration Manager támogatja a frissítés az SQL Server a következő verzióra:

 - SQL Server 2012  
 - SQL Server 2014  
 - SQL Server 2016  

A helyadatbázist futtató SQL Server verziójának frissítése esetén frissítenie kell a következő sorrendben helyeken használt SQL Server-verziótól:

 1. Először a központi adminisztrációs helyen frissítse az SQL Servert.
 2. Mielőtt frissít egy másodlagos hely elsődleges szülőhelyéről másodlagos helyek frissítésére.
 3. Az elsődleges szülőhelyeket utolsóként frissítse. Ez magában foglalja a mindkét alárendelt elsődleges helyet, amely egy központi adminisztrációs hely és az önálló elsődleges helyeken, amelyek a hierarchia legfelső szintű helyén.

**SQL Server számossága becslés szint és a helyadatbázishoz:**   
Frissítésekor a Helyadatbázis az SQL Server egy korábbi verziójáról, az adatbázis megőrzi a meglévő SQL számossága becslése (CE) szintje, ha az adott SQL Server-példánynál engedélyezett minimum. Az adatbázis egy adatbázis kompatibilitási szintje alacsonyabb, mint az engedélyezett szintje, automatikusan az SQL Server frissítése beállítja az SQL Server által megengedett legalacsonyabb kompatibilitási szintjét.

A következő táblázatból azonosíthatja a Configuration Manager adatbázis ajánlott kompatibilitási szintjének:

|SQL Server verziója | Támogatott kompatibilitási szint |Ajánlott szintje|
|----------------|--------------------|--------|
| SQL Server 2016| 130, 120, 110, 100 | 130|
| SQL Server 2014| 120, 110, 100      | 110|

Azonosítsa a helyadatbázishoz használt SQL Server CE kompatibilitási szintje, futtassa a következő SQL-lekérdezés a Helyadatbázis-kiszolgálón:  **Jelölje ki a nevét, compatibility_level FROM sys.databases**

 SQL CE kompatibilitási szintnek és azok beállításáról további információkért lásd: [ALTER adatbázis kompatibilitási szintje (Transact-SQL)](https://msdn.microsoft.com/library/bb510680.aspx).


További információ az SQL Server az SQL Server dokumentációjában a TechNet webhelyén:
-   [Frissítés az SQL Server 2012](http://technet.microsoft.com/library/ms143393\(v=sql.110))
-   [Frissítés az SQL Server 2014](http://technet.microsoft.com/library/ms143393\(v=sql.120))  
-   [Frissítés az SQL Server 2016](https://technet.microsoft.com/library/bb677622(v=sql.130))



### <a name="to-upgrade-sql-server-on-the-site-database-server"></a>A helyadatbázis-kiszolgálón futó SQL Server frissítése  

1.  A hely összes Configuration Manager szolgáltatások leállítása.  
2.  Frissítse az SQL Servert az SQL Server valamelyik támogatott verziójára.  
3.  Indítsa újra a Configuration Manager-szolgáltatásokat.  

> [!NOTE]  
>  Amikor a központi adminisztrációs helyen használt SQL Server-kiadást Standard kiadásról Datacenter vagy Enterprise kiadásra módosítja, a hierarchia által támogatott ügyfelek számát korlátozó adatbázis-partíció nem változik.

