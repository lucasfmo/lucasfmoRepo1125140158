---
title: "Felhasználók társítása célszámítógéphez |} Microsoft Docs"
description: "Felhasználók társítása célhelyként megadott számítógépeken, operációs rendszerek központi telepítésekor a System Center Configuration Manager konfigurálása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 07c3c6d9-f056-4c4d-bc70-ede5ca933807
caps.latest.revision: 9
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: c0331567b94a99b29cc73c16de17a9f3bc6b9e43
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="associate-users-with-a-destination-computer-in-system-center-configuration-manager"></a>Felhasználók társítása célszámítógéphez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Operációs rendszer központi telepítéséhez a System Center Configuration Manager használatakor társíthatja a felhasználókat a célszámítógéphez, amelyikre az operációs rendszer telepítve lesz. A jelen konfiguráció tartalmazza a következőket is:  

-   Azt, hogy az egyetlen felhasználó a célként megadott számítógép elsődleges használója.  

-   Azt, hogy több felhasználó is a célként megadott számítógép elsődleges használója.  

 A felhasználó-eszközkapcsolat az alkalmazások központi telepítésekor támogatja a felhasználó központú kezelést. Ha a felhasználót társítja ahhoz a célként megadott számítógéphez, amelyre az operációs rendszert telepíti, később központilag terjesztheti az alkalmazásokat a felhasználó részére, azok pedig automatikusan települnek a célként megadott számítógépre. Bár az operációs rendszerek központi telepítésekor konfigurálhatja a felhasználó-eszköz kapcsolatot, de a felhasználó-eszköz kapcsolat nem használható az operációs rendszer központi telepítésére.  

 Felhasználó-eszköz kapcsolatra vonatkozó további információkért lásd: [felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

## <a name="how-to-specify-a-user-when-you-deploy-operating-systems"></a>Felhasználó megadása az operációs rendszerek központi telepítésekor  
 A következő táblázat felsorolja azokat a műveleteket, amelyeket a felhasználó-eszköz kapcsolatnak az operációs rendszerek központi telepítésébe integráláshoz kell elvégezni. A felhasználó-eszköz kapcsolat integrálható a PXE telepítésekbe, rendszerindító adathordozós telepítésekbe és előkészített adathordozós telepítésekbe.  

|Művelet|További információ|  
|------------|----------------------|  
|Hozzon létre olyan feladatütemezést, amely tartalmazza az **SMSTSAssignUsersMode** változót.|Adja hozzá az **SMSTSAssignUsersMode** változót a feladatütemezés elejéhez a [Feladatütemezési változó beállítása](../../osd/understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable) feladatütemezési lépés segítségével. Ez a változó határozza meg, hogy a feladatütemezés hogyan kezelje a felhasználói adatokat.<br /><br /> A változót a következő értékek egyikére lehet beállítani:<br /><br /> <br /><br /> **Automatikus**: A feladatütemezés automatikusan létrehozza a kapcsolatot a felhasználó és a cél közötti számítógép és az operációs rendszer központi telepítését.<br /><br /> **Függőben lévő**: A feladatütemezés létrehozza a kapcsolatot a felhasználó és a célszámítógép között, de megvárja a rendszergazdai jóváhagyást, az operációs rendszer telepítése előtt.<br /><br /> **Letiltott**: A feladatütemezés nem rendel hozzá felhasználót a célszámítógéphez, és továbbra is fennáll, az operációs rendszer központi telepítését.<br /><br /> <br /><br /> Ez a változó beállítható egy számítógépre vagy egy gyűjteményre. A beépített változóival kapcsolatos további információkért lásd: [beépített feladatütemezési változókat](../../osd/understand/task-sequence-built-in-variables.md).|  
|Hozzon létre egy olyan előindítási parancsot, amelyik összegyűjti a felhasználó adatait|Az előindítási parancs lehet olyan Visual Basic (VB) parancsfájl, amelyik tartalmaz beviteli mezőt, vagy lehet olyan HTML alkalmazás (HTA), amelyik érvényesíti a beírt felhasználói adatokat.<br /><br /> Az indítás előtti parancsnak azt az **SMSTSUdaUsers** változót kell beállítania, amelyet a feladatütemezés futásakor is. Ez a változó beállítható egy számítógépre, gyűjteményre vagy a feladatütemezés változójaként. Több felhasználó hozzáadásakor használja a következő formátumot: *tartomány\felhasználó1, tartomány\felhasználó2, tartomány\felhasználó3*.|  
|Konfigurálja azt, hogy a terjesztési pontok és az adathordozó hogyan társítsa a felhasználót a célszámítógéphez|Amikor a [terjesztési pontot a PXE rendszerindítási kérelmek fogadására konfigurálja](https://technet.microsoft.com/library/mt627944\(TechNet.10\).aspx#BKMK_PXEDistributionPoint), és a Feladatütemezési média létrehozása varázsló használatával [rendszerindító adathordozót](http://technet.microsoft.com/library/mt627921\(TechNet.10\).aspx) vagy [előkészített adathordozót](https://technet.microsoft.com/library/mt627922\(TechNet.10\).aspx) hoz létre, megadhatja azt, hogy a terjesztési pont és az adathordozó hogyan támogassa a felhasználó társítását ahhoz a célszámítógéphez, amelyikre az operációs rendszer telepítve lesz.<br /><br /> A felhasználó-eszköz kapcsolat támogatása nem rendelkezik beépített módszerrel a felhasználó azonosságának érvényesítéséhez. Ez olyankor lehet fontos, amikor a felhasználó nevében a számítógépet előkészítő technikus írja be az adatokat. Azon a beállításon kívül, hogy a feladatütemezés hogyan kezelje a felhasználói adatokat, ezen beállításoknak a terjesztési pontra és adathordozóra való konfigurálása azt a lehetőséget is biztosítja, hogy egy PXE rendszerindításból vagy adott adathordozótípusról indított központi telepítéseket korlátozza.|  

