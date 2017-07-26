---
title: "Regisztráció frissítése eszköz |} Microsoft Docs"
description: "Ismerje meg a frissítésregisztráló eszköz segítségével manuálisan importálja a Configuration Manager konzol frissítés és mikor."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cc13635-85d6-4b07-a3ec-c42188bc5c74
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 35a4c201f73469fdfaa5bb8629e91886f7ae8751
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-update-registration-tool-to-import-hotfixes-to-system-center-configuration-manager"></a>A frissítésregisztráló eszköz használatával importálhatja a System Center Configuration Manager gyorsjavításait.

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager egyes frissítései nem érhetők el a Microsoft felhőszolgáltatásához, és csak akkor kapja meg a sávon kívüli. Ilyenek például a konkrét problémák megoldására szolgáló, korlátozott kiadású gyorsjavítások.   
Ha telepítenie kell egy sávon kívüli kiadást, és a frissítés vagy gyorsjavítás fájlnevének kiterjesztése **update.exe**, használja a **frissítésregisztráló eszköz** manuálisan importálhatja a frissítés a Configuration Manager konzolon. Az eszköz segítségével kibonthatja és továbbíthatja a frissítési csomagot a helykiszolgálóra, és regisztrálhatja a frissítést a Configuration Manager-konzolon.  

 Ha a gyorsjavítás fájlnevének a **.exe** kiterjesztése (nem **update.exe**), lásd: [a gyorsjavítás telepítőjének használata a frissítések telepítéséhez a System Center Configuration Managerhez](../../../core/servers/manage/use-the-hotfix-installer-to-install-updates.md)  

> [!NOTE]  
>  Ez a témakör általános útmutatást ad a System Center Configuration Managert frissítő gyorsjavítások telepítéséről. Az egyes gyorsjavítások vagy frissítés adatait tekintse meg a megfelelő Tudásbázis (KB) cikk, Microsoft Support.  

 **A frissítésregisztráló eszköz használatának előfeltételei:**  

-   Csak a sávon kívüli frissítések a **. update.exe** bővítmény ezzel az eszközzel telepíthető  

-   Az eszköz az egyes közvetlenül a Microsofttól kapott frissítések beépítve tartalmazzák  

-   Az eszköz nem függ a szolgáltatáskapcsolati pont üzemmódjától.  

-   Az eszközt a szolgáltatáskapcsolati pontot üzemeltető számítógépen kell futtatni.  

-   A számítógép, amelyen az eszköz fut (a szolgáltatáskapcsolódási pont számítógépén) rendelkeznie kell a .NET keretrendszer 4.52-es verziójának telepítése  

-   Az eszköz futtatásához használt fióknak rendelkeznie kell **helyi rendszergazda** engedélyekkel a számítógépen, amelyen a szolgáltatáskapcsolati pontot (ha az eszköz fut)  

-   Az eszköz futtatásához használt fióknak rendelkeznie kell **írási** engedélyeket a szolgáltatáskapcsolódási pontot üzemeltető számítógépen a következő mappához:  **&lt;ConfigMgr telepítési könyvtára\>\EasySetupPayload\offline**  

### <a name="to-use-the-update-registration-tool"></a>A Regisztráció frissítése eszköz használata  

1.  A szolgáltatáskapcsolódási pontot üzemeltető számítógépen:  

    -   Nyisson meg egy parancssort rendszergazdai jogosultságokkal, majd lépjen arra a helyre, amely tartalmazza  **&lt;termék\>-&lt;termékverzió\>-&lt;KB cikk azonosítója\>-ConfigMgr.Update.exe**  

2.  Futtassa a következő parancsot a frissítésregisztráló eszköz elindításához:  

    -   **&lt;A termék\>-&lt;termékverzió\>-&lt;KB cikk azonosítója\>-ConfigMgr.Update.exe**  

    Regisztrálása után a gyorsjavítás 24 órán belül új frissítésként jelenítik meg a konzolon.  A folyamat felgyorsítható:

    - Nyissa meg a Configuration Manager konzolt, és navigáljon a **felügyeleti** > **frissítés és karbantartás**, és kattintson a **frissítések keresése**. (Előtt verzió 1702, frissítés és karbantartás alatt állt **felügyeleti** > **Felhőszolgáltatások**.) 

    A frissítésregisztráló eszköz .log-fájlban naplózza a tevékenységeit a helyi számítógépen. A naplófájl neve megegyezik a gyorsjavítás .exe fájl, és van-e írni a **%SystemRoot%/Temp** mappa.  

     A frissítés regisztrálása után bezárhatja a frissítésregisztráló eszközt.  

3.  Nyissa meg a Configuration Manager konzolt, és navigáljon a **felügyeleti** > **frissítés és karbantartás**. A korábban importált gyorsjavítások már elérhetők a telepítéshez. (Előtt verzió 1702, frissítés és karbantartás alatt állt **felügyeleti** > **Felhőszolgáltatások**.)

 További információ a frissítések telepítése: [konzolon belüli frissítések telepítése a System Center Configuration Managerhez](../../../core/servers/manage/install-in-console-updates.md)  

