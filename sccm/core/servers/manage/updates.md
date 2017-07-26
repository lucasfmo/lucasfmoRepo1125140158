---
title: "Frissítések |} Microsoft Docs"
description: "További információk egy nevű konzolon belüli karbantartási módszert **frissítés és karbantartás** megkeresheti és telepítheti az ajánlott frissítéseket is, amely megkönnyíti."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
caps.latest.revision: 51
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: a33960fb89b71c0f8128e21a5054f5b63cfc6b17
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="updates-for-system-center-configuration-manager"></a>A System Center Configuration Manager frissítései

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager egy nevű konzolon belüli szolgáltatási metódust használ **frissítés és karbantartás** , amely megkönnyíti a keresése és telepítése az ajánlott frissítések a Configuration Manager-infrastruktúrában. A konzolon belüli karbantartási módszert sávon kívüli frissítések például gyorsjavítások, az ügyfelek számára, akiknek adott környezetre lehet problémák megoldására készült egészítik ki.  

> [!TIP]
> Kezelése a System Center Configuration Manager-hely és hierarchia-infrastruktúra, a feltételek *frissítése*, *frissítése*, és *telepítése* három különböző fogalmi kört alkotnak használt... Minden kifejezéshez használatáról információkért lásd: [frissítés, frissítés és telepítés](/sccm/core/understand/upgrade-update-install).


 **A következő témakörök segítségével megismerheti, hogyan megkeresését és telepítését a különböző frissítési típusainak, a System Center Configuration Manager:**  

-   [A konzolon belüli frissítések telepítése a System Center Configuration Managerhez](../../../core/servers/manage/install-in-console-updates.md)  

-   [A szolgáltatáskapcsolódási eszköz használata a System Center Configuration Managerhez](../../../core/servers/manage/use-the-service-connection-tool.md)  

-   [A Frissítésregisztráló eszköz használatával gyorsjavítások importálása a System Center Configuration Managerben](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)  

-   [A gyorsjavítás telepítőjének használata a frissítések telepítéséhez a System Center Configuration Managerhez](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  


Ha a Technical Preview fiókirodai, [a System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview) a fiókirodában vonatkozó további információt.


##  <a name="bkmk_Baselines"></a> Alapkonfiguráció és frissítési verziók  
 System Center Configuration Manager aktuális ág első kiadására lett 1511-es verziójával, amelyet a rendszer egy alapszintű verzióra. Újabb alapverziók 1606 és 1702 verzióját tartalmazzák:

-   Ha egy új helyet telepít egy új hierarchiában, használja legújabb alapkonfigurációt.  

-   A System Center 2012 Configuration Manager rendszerről való frissítéshez egy alapkonfigurációt kell használnia.  

-   Rendszeres időközönként további alapverziók kiadjuk. Ha a legújabb alapkonfigurációt használatával elkerülheti a Configuration Manager elavult verziójának telepítése új hierarchia telepítése, annak érdekében, hogy naprakész infrastruktúra frissítése követi.  

Miután telepít egy alapkonfigurációt, a Configuration Manager további verziói konzolon belüli frissítésként érhetők el. A konzolon belüli frissítések a Configuration Manager legújabb verziójára frissítik infrastruktúráját.  

-   A konzolon belüli frissítések telepítésével a legfelső szintű hely verzióját frissíti.  

-   A központi adminisztrációs helyen telepített frissítések automatikusan települnek az alárendelt elsődleges helyeken, kivéve, ha az elsődleges helyen konfigurált karbantartási időszak blokkolja a frissítést.  

-   A másodlagos helyeket manuálisan kell frissítenie egy új frissítési verzióra a konzolról.  

Amikor frissítést telepít, az adott verziónak megfelelő telepítőfájlokat a helykiszolgáló egy CD.Latest nevű mappájában tárolja a frissítés. Lásd: [a CD-n. A System Center Configuration Manager legújabb mappa](../../../core/servers/manage/the-cd.latest-folder.md) további információ ezen fájlokkal kapcsolatban.  

-   A CD.Latest mappában található fájlokat használhatja helyek helyreállítása során, illetve további helyek telepítésekor olyan hierarchiában, amely már nem az alapkonfigurációt futtatja.  

-   A CD.Latest mappában lévő telepítőfájlok nem használhatók egy új hierarchia első helyének telepítésére, illetve a System Center 2012 Configuration Manager-hely frissítése esetén sem.  

A Configuration Manager egyes frissítései meglévő infrastruktúra konzolon belüli frissítési verziójaként és új verziójú alapkonfigurációként is elérhetők.  

A Configuration Manager következő verziói alapkonfigurációként, frissítésként vagy mindkét formában egyaránt elérhetők:  

|Verzió |Rendelkezésre állás dátuma|[Támogatás záró dátuma](/sccm/core/servers/manage/current-branch-versions-supported) |Alapkonfiguráció|Konzolon belüli frissítés|  
|-------------|-----------|------------|--------------|------------------------|  
|[1702](/sccm/core/plan-design/changes/whats-new-in-version-1702)<br /><br /> 5.00.8498.1000|3/27/2017| 3/27/2018|Igen|Igen|
|[1610](/sccm/core/plan-design/changes/whats-new-in-version-1610)<br /><br /> 5.00.8458.1000|11/18/2016| 11/18/2017|Nem|Igen|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)<br /><br /> 5.00.8412.1000|7/22/2016| 7/22/2017|Nem|Igen|
|[1606](/sccm/core/plan-design/changes/whats-new-in-version-1606) a 1606 gyorsjavítás összesítő (KB3186654) </br></br>5.00.8412.1307 *(Megjegyzés: 1)* |10/12/2016| 7/22/2017|Igen|Nem|
| 1602<br /><br /> 5.00.8355.1000|3/11/2016| 3/11/2017|Nem|Igen|
| 1511 <br /><br /> 5.00.8325.1000|12/8/2015| 12/8/2016|Igen|Nem|  


*(1. megjegyzés)*  A 1606 alapszintű verziót tartalmazó adathordozóról vagy a System Center Configuration Manager (aktuális ág és hosszú távú karbantartási ág 1606) kiadása a Microsoft System Center 2016 részeként érhető el.

A Configuration Manager-hely verziójának ellenőrzéséhez kattintson **A System Center Configuration Manager alkalmazásáról** elemre a konzol bal felső sarkában, ahol megjelenik az új hely és konzol verziója.  

##  <a name="bkmk_inconsole"></a> Konzolon belüli frissítések és karbantartás  
 Üzemkész telepítésének a System Center Configuration Manager, más néven az aktuális ág használatakor a legtöbb telepítése frissítései érhető el a frissítések és karbantartás csatorna. Ez a módszer azonosítja, letölti és elérhetővé teszi a jelenlegi infrastruktúrára és konfigurációra vonatkozó frissítéseket, és csak a Microsoft által az összes ügyfél számára javasolt frissítéseket tartalmazza.   
 Ezek a következők:  

-   Új verziók, például 1610 verziója  

-   Az aktuális verzióra vonatkozó új funkciókat tartalmazó frissítések  

-   A Configuration Manager adott verziójához készült azon gyorsjavítások, amelyeket az összes ügyfélnek célszerű telepíteni  

A konzolon belüli frissítések megnövekedett stabilitást nyújtanak, és megoldják a gyakori problémákat. Lecserélik a korábbi termékverziók frissítési típusait a szervizcsomagok, az összesítő frissítőcsomagok, az összes ügyfélre vonatkozó gyorsjavítások és a Microsoft Intune-bővítmény esetében. Ezek a frissítések a következők legalább egyikére alkalmazhatók:  

-   Elsődleges hely és központi felügyeleti hely kiszolgálói  

-   Helyrendszer-kiszolgálók és helyrendszerszerepkörök kiszolgálói  

-   Az SMS Provider példányai  

-   A Configuration Manager konzolok  

-   Configuration Manager-ügyfelek  

A Configuration Manager felderíti az új frissítéseket, ha a szolgáltatás kapcsolódási pont helyrendszer-szerepkör szinkronizálása a Microsoft felhőszolgáltatásához, és a letöltőközpontból:  

-   Ha a szolgáltatáskapcsolódási pont online módban van, a hely naponta szinkronizálja azt a Microsofttal azon új frissítések automatikus észleléséhez, amelyek érvényesek az adott infrastruktúrához.  Frissítések és a frissítések redist fájlok letöltéséhez a szolgáltatáskapcsolódási pont helyrendszerszerepkört futtató számítógépen használja a **rendszer** környezetben a következő internetes helyek elérésére: go.microsoft.com és a jövőben a Microsoft. A szolgáltatáskapcsolódási pont csatlakozik a további helyekre vonatkozó információkért lásd: [internetelérési követelményei](../../../core/servers/deploy/configure/about-the-service-connection-point.md#bkmk_urls) a [kapcsolatos a szolgáltatáskapcsolódási pont a System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   Ha a szolgáltatáskapcsolódási pont offline üzemmódban van, a szolgáltatáskapcsolati eszköz segítségével manuálisan szinkronizálhat a Microsoft-felhővel. További információk: [A System Center Configuration Manager szolgáltatáskapcsolódási eszközének használata](../../../core/servers/manage/use-the-service-connection-tool.md).  

-   A konzolon belüli frissítések feleslegessé teszik a frissítések, szervizcsomagok és új funkciók egyenkénti megkeresését és telepítését.  

-   Csak az Ön által kiválasztott konzolon belüli frissítések települnek, és néhány frissítés telepítése során kiválaszthatja az egyes engedélyezni és használni kívánt szolgáltatásokat. További információkért lásd: [a frissítések választható funkcióinak engedélyezése](../../../core/servers/manage/install-in-console-updates.md#bkmk_options).  

A konzolon belüli frissítés telepítésekor:  

-   Automatikusan futtatja az előfeltételek ellenőrzését. Az ellenőrzést a telepítés megkezdése előtt is futtathatja.  

-   Automatikusan települ a központi adminisztrációs helyen (ha van), és az elsődleges helyeken. Szabályozhatja, ha minden elsődleges hely kiszolgálója számára engedélyezett az infrastruktúra frissítése a [szolgáltatási időkeretek Helykiszolgálók számára](../../../core/servers/manage/service-windows.md).  

-   Egy helykiszolgáló frissítése után az összes érintett helyrendszer-szerepkört (beleértve az SMS Provider példányait) automatikusan frissíti. A Configuration Manager-konzolok emellett felszólítják a konzol felhasználóját a konzol frissítését, a hely a frissítés telepítése után.  

-   Ha egy frissítés tartalmazza a Configuration Manager-ügyfél, felkínálja a lehetőséget a frissítés tesztelése az üzem előtti, vagy a frissítés alkalmazásához minden ügyfélnek azonnal.  

-   Miután egy elsődleges hely frissült, a másodlagos helyek nem frissülnek automatikusan. Ehelyett a felhasználónak kezdeményeznie kell a másodlagos hely frissítését.  

> [!NOTE]  
>  Az éles kiadása System Center Configuration Manager (aktuális ág), a hosszú távú karbantartási ág és a Technical Preview a System Center Configuration Manager különböző kiadások. Egy fiókiroda tartozó frissítést, ezért a többi fiók közben a konzolon belüli frissítésként nem érhetők el. Az ágakkal rendelkező elérhető kapcsolatos további információkért lásd: [melyik Configuration Manager fiókirodai érdemes használni?](/sccm/core/understand/which-branch-should-i-use)

##  <a name="bkmk_outofband"></a> Sávon kívüli gyorsjavítások  
Egyes gyorsjavítások konkrét problémák megoldására szolgálnak korlátozott elérhetőséggel, vagy minden ügyfélre vonatkoznak, de nem telepíthetők a konzolon belüli módszerrel. Ezek a javítások sávon kívüli terjesztésűek, és a Microsoft felhőalapú szolgáltatásából nem észlelhetők.  

Általában, megismerkedhet a Microsoft terméktámogatási szolgálatán, a tudásbázison vagy a sávon kívüli gyorsjavítások a [System Center Configuration Manager Team blog](https://blogs.technet.microsoft.com/configmgrteam) amikor törekszik, és javítsa ki vagy oldja meg a problémát, a Configuration Manager telepítés.  

Ezeket a javításokat manuálisan telepítheti, kétféle módszerrel:  

-   **Regisztráció frissítése eszköz:** Ez az eszköz a Configuration Manager konzolt, ahol telepítheti a frissítést, akkor volna a konzolon belüli frissítések automatikusan felderített manuálisan importálja a gyorsjavítást. Ez a módszer a következő fájlnévstruktúrát használó frissítésekhez használatos: **.update.exe**.  Az ilyen típusú gyorsjavítások a teljes fájlnév a következőhöz hasonló: **&lt;A termék\>-&lt;termékverzió\>-&lt;Tudásbáziscikk azonosítója\>-ConfigMgr.Update.exe**.  

     További információkért lásd: [a Frissítésregisztráló eszköz segítségével importálja a gyorsjavítást a System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

-   **Gyorsjavítás-telepítő:** Ez az eszköz segítségével manuálisan telepítheti azon gyorsjavításokat, amelyek nem telepíthetők a konzolon belüli módszerrel. Ez a módszer a következő fájlnévstruktúrát használó javításokhoz szolgál: **&lt;Product\>-&lt;product version\>-&lt;KB article ID\>-&lt;platform\>-&lt;language\>.exe**.

     További információkért lásd: [a gyorsjavítás telepítőjének használata a frissítések telepítéséhez a System Center Configuration Manager](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md).

