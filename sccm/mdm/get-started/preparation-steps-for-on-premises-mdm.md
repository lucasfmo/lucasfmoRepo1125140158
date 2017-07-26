---
title: "Előkészítő lépések |} Microsoft Docs"
description: "Felkészülés a helyszíni mobileszköz-kezelés a System Center Configuration Managerben az eszközök kezelésére."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
caps.latest.revision: 4
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 85bdadaaaeed9a42cfa5165d2b9f0f3ef434dc03
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Előkészítő lépések helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Eszközök kezelése a System Center Configuration Manager a\-helyszíni mobileszköz-kezelés megköveteli, hogy a szükséges helyrendszerszerepkörök (beléptetési proxypont, beléptetési pont, eszközfelügyeleti pont és terjesztési pont) megbízható csatornán keresztül kommunikálhassanak a felügyelendő mobileszközök beállítása a Configuration Manager-infrastruktúrát.  

 A következő magas szintű feladatok szükségesek a Configuration Manager rendszer előkészítését a\-helyszíni mobileszköz-kezelés:  

-   [A Microsoft Intune-előfizetés beállítása helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     Ebben a feladatban hogy feliratkozzon a Microsoft Intune, és adja hozzá az előfizetés a Configuration Manager a Configuration Manager konzol segítségével. Ez a lépés csak licenckezelési célokból szükséges. Intune-t nem használja az eszközök felügyeletére vagy a felügyeleti információk tárolására. Koordinálása és az eszközök felügyelete vállalati környezetben a helyi Configuration Manager infrastruktúrájának használatával jelenti.  

-   [Helyrendszerszerepkörök telepítése a helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     Ebben a feladatban telepítése és konfigurálása a Configuration Manager-infrastruktúrát a helyszíni eszközök felügyeletéhez szükséges helyrendszerszerepköröket. A\-helyszíni mobileszköz-kezelés minimálisan szükséges a beléptetési proxypont, beléptetési pont, eszközfelügyeleti pont és terjesztési pont helyrendszerszerepkör esetében.  

-   [A helyszíni mobileszközök kezeléséhez a System Center Configuration Manager megbízható kommunikációhoz szükséges tanúsítványok beállítása](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     Ebben a feladatban konfigurálja a helyi Configuration Manager infrastruktúrájának engedélyezik a felügyelt eszközök és a szükséges helyrendszerszerepköröket üzemeltető kiszolgálók közötti megbízható kommunikációt (HTTPS).  

-   [A helyszíni mobileszköz-kezelés a System Center Configuration Managerben az eszközregisztráció beállítása](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     Ebben a feladatban engedélyezi a felhasználóknak a számítógépek és eszközök regisztrálását, és telepíti a megbízható legfelső szintű tanúsítványt az eszközökön (általában azokon, amelyek nincsenek tartományhoz csatlakoztatva) a HTTPS-kapcsolatok engedélyezéséhez a helyrendszer-kiszolgálókon.  

