---
title: "Funkciók és képességek |} Microsoft Docs"
description: "További információk a System Center Configuration Manager elsődleges felügyeleti funkcióit."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 53b27dcb5c8bb670556fe4cee9e990619a9a63e9
ms.openlocfilehash: 4691f43dccdf73936107f4635321897b9779bead
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="features-and-capabilities-of-system-center-configuration-manager"></a>A System Center Configuration Manager funkciói és képességei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az alábbiakban a System Center Configuration Manager elsődleges felügyeleti funkcióit. Mindegyik funkcióra saját Előfeltételek rendelkezik, és használni kívánt elérhető lehetőségek befolyásolhatja a megtervezését és megvalósítását a Configuration Manager-hierarchiában. Például ha azt szeretné, a szoftver telepítése ebben a hierarchiában található eszközöknél, telepítenie kell a terjesztési pont helyrendszer-szerepkör.  

 Megtervezése és telepítése a Configuration Manager ezeknek a felügyeleti funkcióknak a környezetben támogatja kapcsolatos további információkért lásd: [Felkészülés a System Center Configuration Manager](../../../core/plan-design/get-ready.md).  

 **Alkalmazáskezelés**  

 Eszközöket és erőforrásokat biztosít alkalmazások számos különböző kezelt eszközön való létrehozásához, felügyeletéhez, központi telepítéséhez és figyeléséhez. A Configuration Manager Emellett hozzá, és eszközök megkönnyítik a felhasználó alkalmazásokban lévő vállalati adatok védelme. Lásd: [Alkalmazáskezelés bemutatása](/sccm/apps/understand/introduction-to-application-management).

 **Vállalati erőforrások elérése**  

 Eszközöket és erőforrásokat biztosít annak lehetővé tételéhez, hogy a szervezetnél dolgozó felhasználók távolról is elérjék az adatokat és az alkalmazásokat. Ezek az eszközök közé tartozik a Wi-Fi profilok, VPN-profilok, a tanúsítványprofilok és feltételes hozzáférés az Exchange és SharePoint online. Lásd: [védelme adatok és a helyinfrastruktúra a System Center Configuration Managerrel](../../../protect/understand/protect-data-and-site-infrastructure.md) és [kezelése a System Center Configuration Manager-szolgáltatásokhoz való hozzáférés](../../../protect/deploy-use/manage-access-to-services.md).  

 **Megfelelőségi beállítások**  

 Eszközöket és erőforrásokat, amelyek segítségével felmérheti, nyomon követheti és szervizelheti azokat a vállalati ügyféleszközök konfigurációs megfelelőségének biztosít. Megfelelőségi beállítások segítségével ezenkívül egy számos szolgáltatást és a biztonsági beállítások konfigurálása a felügyelt eszközökön. Lásd: [a System Center Configuration Managerrel eszközök megfelelőségének biztosítása](../../../compliance/understand/ensure-device-compliance.md).  

 **Endpoint Protection**  

 Lehetővé teszi a biztonság, a kártevőirtó funkció és a Windows tűzfal vállalati számítógépeken való felügyeletét. Lásd: [a System Center Configuration Managerben az Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md).  

 **Szoftverleltár**  

 Számos eszközt eszközök azonosítására és figyelésére:  

-   **Hardverleltár**: A részletes információkat a hardvert a vállalati eszközök gyűjt. Lásd: [a System Center Configuration Manager hardverleltárának bemutatása](../../../core/clients/manage/inventory/introduction-to-hardware-inventory.md).  

-   **A szoftverleltár**: Gyűjt és jelent adatokat az ügyfélszámítógépeken a szervezet tárolt fájlok. Lásd: [Bevezetés a System Center Configuration Manager szoftverleltárába](../../../core/clients/manage/inventory/introduction-to-software-inventory.md).  

-   **Az Eszközintelligencia**: Különféle módszereket biztosít a leltáradatok gyűjtésére és a vállalati szoftverlicencek felhasználásának figyelésére. Lásd: [a System Center Configuration Manager Eszközintelligencia szolgáltatásának bemutatása](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

**A Microsoft Intune mobileszköz-kezelés**  

 A Configuration Manager segítségével az iOS, Android (beleértve a Samsung KNOX Standard), Windows Phone és Windows-eszközök kezelése a Microsoft Intune szolgáltatással az interneten keresztül.

 Noha az Intune-ba, felügyeleti feladatok a szolgáltatás kapcsolódási pont helyrendszerszerepkör a Configuration Manager konzolon keresztül elérhető használatával hajthatók végre. Lásd: [hibrid mobileszköz-kezelés (MDM) a System Center Configuration Manager és a Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

 **A helyszíni mobileszköz-kezelés**  

 Regisztrálja és kezeli a számítógépeket és mobileszközöket a helyi Configuration Manager infrastruktúra és a felügyeleti funkcióinak használatával (ahelyett, hogy egy külön telepített Configuration Manager ügyfél) eszközplatformok beépített. Jelenleg a Windows 10 Enterprise és a Windows 10 Mobile rendszerű eszközök kezelését támogatja. Lásd: [mobileszközök kezelése a helyszíni infrastruktúrával a System Center Configuration Managerben](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Operációs rendszer központi telepítése**  

 Eszközt biztosít az operációs rendszereket tartalmazó lemezképek létrehozásához. Majd segítségével ezeket a lemezképeket az operációs rendszerek központi telepítése a számítógépekre, PXE rendszerindítással vagy rendszerindításra alkalmas adathordózóról, például CD set, DVD vagy USB flash meghajtóról. Vegye figyelembe, hogy ez vonatkozik a Configuration Manager által felügyelt számítógépeken, valamint a nem felügyelt számítógépekre. Lásd: [operációs rendszer központi telepítése a System Center Configuration Managerben – bevezetés](../../../osd/understand/introduction-to-operating-system-deployment.md).  

 **Energiagazdálkodás**  

 Eszközöket és erőforrásokat biztosít a vállalati ügyfélszámítógépek energiafogyasztásának felügyeletéhez és figyeléséhez. Lásd: [az energiagazdálkodás a System Center Configuration Manager bemutatása](../../../core/clients/manage/power/introduction-to-power-management.md).  

 **Lekérdezések**  

 Eszközt biztosít a hierarchiába tartozó erőforrásokkal, valamint a leltáradatokkal és az állapotüzenetekkel kapcsolatos információk beolvasására. A jelentési, vagy az eszközöknek vagy felhasználóknak a szoftver központi telepítési és konfigurációs beállítások definiálására majd használja az információt. Lásd: [a System Center Configuration Manager lekérdezéseinek bemutatása](../../../core/servers/manage/introduction-to-queries.md).  

 **A távoli kapcsolati profilok**  

 Számos különböző eszközöket és erőforrásokat létrehozni, telepíteni és figyelemmel kísérni a távoli kapcsolati beállításokat a szervezetben lévő eszközök alapján. Ezen beállítások telepítésével lecsökkentheti a felhasználók a vállalati hálózaton működő számítógépeikhez való kapcsolódáshoz szükséges munkát. Lásd: [a System Center Configuration Manager távoli kapcsolati profilok használata](/sccm/compliance/deploy-use/create-remote-connection-profiles).  

 **Felhasználói adatokat és profilokat tartalmazó konfigurációs elemek**  

 Felhasználói adatokat és profilokat tartalmazó konfigurációs elemek a Configuration Manager olyan beállításokat tartalmaznak, kezelhető a mappaátirányítás, offline fájlokhoz és barangoló profilok a Windows 8 rendszerű számítógépeken, és később a hierarchiában lévő felhasználók számára. Lásd: [felhasználói adatokat és profilokat tartalmazó konfigurációelemek a System Center Configuration Manager használata](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items).  

 **Távvezérlés**  

 A Configuration Manager konzoljáról ügyfélszámítógépek távoli felügyeletéhez eszközöket biztosít. Lásd: [a System Center Configuration Manager Távvezérlés – bevezetés](../../../core/clients/manage/remote-control/introduction-to-remote-control.md).  

 **Jelentéskészítés**  

 Biztosítja az eszközöket és erőforrásokat, amelyek segítenek fejlett jelentéskészítési funkcióinak használatát az SQL Server Reporting Services a Configuration Manager konzoljáról. Lásd: [a System Center Configuration Manager jelentéskészítésének bemutatása](../../../core/servers/manage/introduction-to-reporting.md).  

 **A szoftverhasználat-mérés**  

 Figyelheti és gyűjtheti a szoftverhasználati adatokat a Configuration Manager-ügyfelek eszközöket biztosít. Lásd: [Alkalmazáshasználat figyelése a szoftverhasználat-méréssel a System Center Configuration Managerben](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

 **Szoftverfrissítések**  

 Eszközöket és erőforrásokat biztosít a vállalati szoftverfrissítések felügyeletéhez, központi telepítéséhez és figyeléséhez. Lásd: [szoftver bemutatása frissíti a System Center Configuration Managerben](/sccm/sum/understand/software-updates-introduction).  

