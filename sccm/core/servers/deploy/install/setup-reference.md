---
title: "Hivatkozás beállítása |} Microsoft Docs"
description: "Tekintse át ezt a hivatkozást a Configuration Manager-hely vagy hierarchia telepítése előkészítéséhez."
ms.custom: na
ms.date: 4/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdb9fb0c-0912-41e4-b427-f40620971763
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: 739461a6cca0fd67431093524c1e8158afd80d0f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="reference-for-system-center-configuration-manager-setup"></a>Útmutató a System Center Configuration Manager telepítéséhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager telepítése, amely részletes leírást talál az alábbi szakaszok néhány témakörökre mutató hivatkozásokat biztosít. Az itt bemutatott információval segítségével készítse elő a Configuration Manager-hely vagy hierarchia telepítése, és néhány ellenőriznie kell, a telepítés során az alábbi döntéseket segítségével.  


##  <a name="bkmk_start"></a> Előkészületek  
Új Configuration Manager-helyek telepítése előtt győződjön meg arról, hogy tekintse át a következő adatokat, amelyek segíthetnek a környezet sikeres kialakításának előkészítésében:  

-   [A System Center Configuration Manager alapja](../../../../core/understand/fundamentals.md)  
-   [A System Center Configuration Manager infrastruktúrájának tervezése](../../../plan-design/network/configure-firewalls-ports-domains.md)  
-   [Felkészülés a System Center Configuration Manager-helyek telepítése](prepare-to-install-sites.md)  

##  <a name="bkmk_assess"></a> A kiszolgáló készen állásának felmérése  
Az új hely a telepítés megkezdése előtt győződjön meg arról, hogy a helykiszolgáló és a hely (például a kiszolgálón, amely a helyadatbázist tároló) használatát tervezi távoli helyrendszer-kiszolgálók megfelelnek-e az összes előfeltételként szükséges konfigurációkról. Ezek a témakörök a dokumentációs könyvtárban segítségével:  

-   [A System Center Configuration Manager támogatott konfigurációk](../../../../core/plan-design/configs/supported-configurations.md)  
-   [Az előfeltétel-ellenőrző](prerequisite-checker.md)  

##  <a name="bkmk_Addclients"></a> Ügyfelek egyéb operációs rendszerekhez  
Ügyfélszoftvert a Configuration Manager a következő operációs rendszerekhez a Microsoft Download Center webhelyről tölthető le:  

-   Mac (Apple)  
-   UNIX  
-   Linux  

A következő hivatkozások használata a Configuration Manager használt verziójára vonatkozó mobilügyfelek akkor tölthetők le:  

-   Lásd: [a Microsoft System Center Configuration Manager - ügyfelek egyéb operációs rendszerekhez](http://www.microsoft.com/download/details.aspx?id=47719)  

##  <a name="bkmk_usage"></a> Használati adatszintek és beállítások  
Az első System Center Configuration Manager-hely telepítésekor a Configuration Manager automatikusan telepíti és konfigurálja az új helyrendszerszerepkör, a **szolgáltatáskapcsolódási pont**, a helykiszolgálón. A szolgáltatáskapcsolódási pont az alapértelmezett beállításokat tartalmaz:  

-   **Online** mód (egy offline üzemmód is elérhető)  
-   **Továbbfejlesztett** adatgyűjtési szint (két másik adatgyűjtési szint, alapszintű és a teljes is érhetők el)  

Amikor a szolgáltatási kapcsolódási pont helyrendszerszerepkörének online állapotban, a Microsoft automatikusan adatokat gyűjthet a diagnosztikai és használati adatokat az interneten keresztül. Az összegyűjtött információk a következőkben segítenek nekünk:  

-   A problémák azonosításában és elhárításában  
-   A termékek és szolgáltatások javításában  
-   A Configuration Manager használt verziójára vonatkozó  frissítések azonosítását  

### <a name="levels-of-data-collection"></a>Adatgyűjtési szintek  
Adatgyűjtés a három szinteket tartalmazza:

-   **Alapszintű** beállításra és frissítésre, például a helyek és a Configuration Manager-szolgáltatásokat engedélyezett számát vonatkozó adatokat tartalmazza. Átkerülnek a személyes azonosításra alkalmas adatokat.  

-   **Továbbfejlesztett** tartalmazza az alapszintű beállítás, az adatok mellett adatokat továbbít a hierarchiával továbbítja, és használatának a módjával egyes szolgáltatásokhoz (gyakoriság és időtartam), valamint speciális diagnosztikai információkat, például a kiszolgáló memóriaállapotát a rendszer vagy alkalmazás összeomlása esetén. Átkerülnek a személyazonosításra alkalmas adatokat.  

-   **Teljes** adatokat tartalmazza. a Basic és a bővített szint beállításainak, valamint azt is küld speciális diagnosztikai információkat, például rendszerfájlokat és a memóriáról készült pillanatképeket. Ez a beállítás tartalmazhatnak személyes azonosításra alkalmas adatokat, de ezt az információt nem használjuk azonosítására vagy kapcsolatfelvételre, vagy a cél hirdetések küldésére.  

További információ, beleértve az egyes szinteken gyűjtött adatok kiadásáról: [diagnosztikai és használati adatokat a System Center Configuration Manager](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

A System Center Configuration Manager adatvédelmi nyilatkozata online megtekintéséhez nyissa meg a [http://go.microsoft.com/fwlink/?LinkID=626527](http://go.microsoft.com/fwlink/?LinkID=626527).

