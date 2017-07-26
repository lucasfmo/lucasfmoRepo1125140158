---
title: "Szolgáltatáskapcsolódási pont |} Microsoft Docs"
description: "További tudnivalók a Configuration Manager helyrendszer-szerepkör, és ismerje meg, és használati helyzetek körét tervezése."
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: ad6df047beff670411d203220576b87f7d56d50c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="about-the-service-connection-point-in-system-center-configuration-manager"></a>A System Center Configuration Manager szolgáltatáskapcsolódási pontjának ismertetése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager szolgáltatáskapcsolódási pont olyan helyrendszerszerepkör, amely számos fontos funkciót tölt szolgál a hierarchiában. A szolgáltatáskapcsolódási pont beállítása előtt megértéséhez, és megtervezheti, hogy használ, amelyek hatással lehetnek, hogyan állíthatja be a helyrendszer-szerepkör helyzetek körét:  

-   **Mobileszközök kezelése a Microsoft Intune** -e a szerepkör váltja fel a Windows Intune-összekötő, amely a Configuration Manager korábbi verzióját használja, és konfigurálhatók az Intune-előfizetés részleteit. Lásd: [hibrid mobileszköz-kezelés (MDM) a System Center Configuration Manager és a Microsoft Intune](../../../../mdm/understand/hybrid-mobile-device-management.md).  

-   **Mobileszközök kezelése a helyszíni MDM** – Ez a szerepkör támogatást nyújt az Ön által kezelt és, amelyek nem kapcsolódnak az internethez a helyszíni eszközök. Lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

-   **Töltse fel a Configuration Manager-infrastruktúra használati adatait** -szabályozhatja a szint vagy a feltöltött részletességét. A feltöltött adatok lehetővé teszik számunkra az alábbiakat:  

    -   A problémák proaktív azonosítása és elhárítását  

    -   A termékek és szolgáltatások javításában  

    -   A Configuration Manager számára a Configuration Manager használt verziójára vonatkozó frissítések azonosításában  

  Minden szinten gyűjti az adatokat és módosítása a gyűjtemény szintjén, a szerepkör telepítése után kapcsolatos információkért lásd: [diagnosztikai és használati adatok](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data), és hajtsa végre a Configuration Manager használt verziójára vonatkozó hivatkozás.  

  További információkért lásd: [használati adatszintek és beállítások](../../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

-   **A Configuration Manager infrastruktúrára vonatkozó frissítések letöltése** – csak az infrastruktúrára vonatkozó frissítések elérhetővé válnak a feltöltött használati adatok alapján.  

- **Mindegyik hierarchia ezen szerepkör egyetlen példányát támogatja:**  

 -   A helyrendszerszerepkör csak a legfelső szintű helyen a hierarchia, amely egy központi adminisztrációs hely vagy önálló elsődleges helyen telepíthető.  

  -   Ha egy önálló elsődleges helyet kibővít nagyobb hierarchiává történő, akkor el kell távolítania ezt a szerepkört az elsődleges helyről, és ezután telepítheti azt a központi adminisztrációs helyen.  


##  <a name="bkmk_modes"></a>Működési módja  
 A szolgáltatáskapcsolódási pont a következő két működési módot támogatja:  

-   A **online módban**, a szolgáltatáskapcsolódási pont frissítéseket 24 óránként automatikusan ellenőrzi, és aztán töltse le az új frissítések érhetők el az aktuális infrastruktúrához és termékverzióhoz verzió elérhetővé a Configuration Manager konzolon.  

-   A **kapcsolat nélküli módban**, a szolgáltatáskapcsolódási pont nem csatlakozik a Microsoft felhőszolgáltatásához, és manuálisan kell [a szolgáltatáskapcsolódási eszköz használata a System Center Configuration Manager](../../../../core/servers/manage/use-the-service-connection-tool.md) rendelkezésre álló frissítések importálásához.  

A szolgáltatáskapcsolódási pont telepítését követően online és offline módok között módosításakor kell majd indítani a Configuration Manager SMS_Executive szolgáltatás SMS_DMP_DOWNLOADER szálát a módosítás életbe lép. Ehhez használja a Configuration Manager Service Manager csak az SMS_Executive szolgáltatás SMS_DMP_DOWNLOADER szálát. Az SMS_Executive szolgáltatást a Configuration Manager, amely a legtöbb helyösszetevőt újraindítja is újraindíthatja, vagy megvárhatja a hely biztonsági mentése, leállítja, majd később újraindítja az SMS_Executive szolgáltatást, például egy ütemezett feladatot.  

A Configuration Manager Service Manager használatához a nyissa meg a konzol **figyelés** > **rendszerállapot** > **összetevő-állapot**, válassza a **Start**, és válassza a **Configuration Manager Service Manager**. A Service Managerben:  

-   A navigációs ablaktáblán bontsa ki a webhely, **összetevők**, majd kattintson az újraindítani kívánt összetevőt.  

-   A részleteket tartalmazó ablaktáblán kattintson a jobb gombbal az összetevőt, és válassza **lekérdezés**.  

-   Az összetevő állapotának ellenőrzése után kattintson ismét a jobb gombbal az összetevőt, és válassza a **leállítása**.  

-   **Lekérdezés** az összetevőt újra győződjön meg arról, hogy le van állítva, kattintson a jobb gombbal az összetevő még egyszer, és válassza **Start**.  

> [!IMPORTANT]  
>  A folyamat, amely a Microsoft Intune-előfizetés automatikusan hozzáadja a szolgáltatáskapcsolódási pont beállítása a helyrendszer-szerepkör online állapotba. A szolgáltatáskapcsolódási pont nem támogatja a kapcsolat nélküli módban, ha ez be van állítva az Intune-előfizetést.  

**Ha a szerepkör, amely a helykiszolgálótól távoli számítógépen telepíti:**  

-   A helykiszolgáló számítógépfiókjának a számítógépen, amelyen a távoli szolgáltatáskapcsolódási helyi rendszergazdának kell lennie.

-   Be kell állítania a helyrendszer-kiszolgáló, amelyen a szerepkört egy helyrendszer-telepítési fiók.  

-   A distribution manager a helykiszolgálón a frissítések átvitelére a szolgáltatáskapcsolódási pont az a helyrendszer-telepítési fiókot használja.

##  <a name="bkmk_urls"></a>Internetelérési követelményei  
Ahhoz, hogy a művelet, a számítógép, amelyen a szolgáltatáskapcsolódási pont és a tűzfalak, hogy a számítógép és az Internet között meg kell felelnie a kommunikáció **TCP 443-as porton** és **TCP 443-as porton** a következő internetes helyekhez. A szolgáltatáskapcsolódási pont is támogatja a webproxy (vagy anélkül hitelesítési) használni ezeket a helyeket.  Ha szeretne beállítani egy webalkalmazás-proxy fiókot lásd: [Proxykiszolgáló-támogatás a System Center Configuration Managerben](/sccm/core/plan-design/network/proxy-server-support).

**Frissítések és karbantartás**  

-   *.akamaiedge.net  

-   *.manage.microsoft.com

-   go.microsoft.com

-   blob.core.windows.net  

-   download.microsoft.com  

-   download.windowsupdate.com

-   sccmconnected-a01.cloudapp.net  

**A Microsoft Intune**  

-   *manage.microsoft.com  
-   https://bspmts.mp.microsoft.com/V
-   https://Login.microsoftonline.com/{a TenantID}


**Windows 10 karbantartása**  

-   download.microsoft.com  

-   https://go.microsoft.com/fwlink/?LinkID=619849  

## <a name="install-the-service-connection-point"></a>A szolgáltatáskapcsolódási pont telepítése
Amikor futtatja **telepítő** szeretné telepíteni a hierarchia legfelső szintű helyének, lehetősége van a szolgáltatáskapcsolódási pont telepítéséhez.

Telepítés után, vagy ha a helyrendszerszerepkör újratelepítését végzi, használja a **helyrendszer-szerepkörök hozzáadása** varázsló vagy a **helyrendszer-kiszolgáló létrehozása** varázsló segítségével telepítheti a helyrendszer-kiszolgálóra a hierarchia legfelső szintű helyen, amely, a központi adminisztrációs hely vagy önálló elsődleges hely. Mindkét varázsló szerepelnek a **Home** a konzolhoz lapján **felügyeleti** > **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**.

## <a name="log-files-used-by-the-service-connection-point"></a>A szolgáltatáskapcsolódási pont által használt naplófájlok
Tekintse meg a Microsoft feltöltések, tekintse meg a **Dmpuploader.log** a szolgáltatáskapcsolódási pontot futtató számítógépen.  Letöltések, beleértve a frissítéseket, letöltés előrehaladását megtekintése **Dmpdownloader.log**. A naplók a szolgáltatáskapcsolódási pont teljes listájáért lásd: [szolgáltatáskapcsolódási pont](/sccm/core/plan-design/hierarchy/log-files#BKMK_WITLog) a Configuration Manager napló fájlok témakörben.

A következő folyamatábrák segítségével is folyamata és a frissítés letöltése és a frissítések más helyekre replikálás kulcs naplóbejegyzések:
 - [Folyamatábra – frissítések letöltése](/sccm/core/servers/manage/download-updates-flowchart)
 - [Folyamatábra – frissítés replikáció](/sccm/core/servers/manage/update-replication-flowchart)

