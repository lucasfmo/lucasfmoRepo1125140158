---
title: "Frissíti a közzétevő |} Microsoft Docs"
description: "Egyéni frissítések kezelése a System Center Updates Publisher használatával"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: f4951c204b32da58174b94a539b380c278fa9756
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="system-center-updates-publisher"></a>A System Center frissítés-közzétevő

*Vonatkozik: A System Center frissítés-közzétevő*

A System Center frissítés-közzétevő (Publisher frissítések) olyan önálló eszköz, amely lehetővé teszi a független szoftvergyártók vagy a-üzleti alkalmazások fejlesztői az egyéni frissítések felügyeletére. Ez magában foglalja, amelyekhez függőségét, például az illesztőprogramok és a frissítési csomagok.

Frissítés-közzétevő használatával:

-   Frissítések importálása külső katalógusok (nem a Microsoft update katalógus).
-   Módosítsa a definíciófrissítések, beleértve a alkalmazhatósági és a központi telepítési metaadatok.
-   Külső katalógusok frissítések exportálja.
-   Frissítések közzétételéhez a frissítési kiszolgálón.

Frissítések miutá közzéteszi a frissítési kiszolgálóhoz, majd segítségével System Center Configuration Manager észlelése és a felügyelt eszközök számára telepítheti ezeket a frissítéseket.

> [!TIP]  
> Az előző verzió [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/?LinkId=848111), továbbra is támogatott. A frissített verzió megtartja ugyanazt a funkciót, de támogatja egyéb operációs rendszerekhez, egyszerűbbé teheti az egyes feladatokhoz, új funkciókat, és egy frissített felhasználói felület.

## <a name="workspaces"></a>A munkaterületek között
Frissítés-közzétevő megnyitásakor, alapértelmezés szerint az áttekintési csomópontban, az *frissítések munkaterületen.*

![Frissítések Publisher konzolját](media/console1.png)   


Frissítés-közzétevő rendelkezik négy munkaterületek azt rendszerezésének elősegítése érdekében.


**Frissítések munkaterület:** A munkaterületen a [létrehozása](/sccm/sum/tools/create-updates-with-updates-publisher) és [kezelése](/sccm/sum/tools/manage-updates-with-updates-publisher) szoftverfrissítéseket és a frissítési csomagok. Ez tartalmazza a frissítések hozzárendelése és kötegek kiadványra, közzététele, és egy másik frissítés-közzétevő tárházba exportálása.

**Kiadványok munkaterület:** Ez akkor, ha Ön [kiadványok kezelése](/sccm/sum/tools/updates-publisher-publications). A kiadvány pedig csoport frissítések hoz létre az exportálás és a frissítések közzétételi leegyszerűsítése érdekében.

A kiszolgáló közzétételi frissítéseit kiadványok kezelése tartalmazza, így az ügyfelek találhatja meg és telepítheti azokat, frissítéseket és a csomagok használatra telepített más frissítés-közzétevő által exportálásának és kiadvány részleteit vagy tartalmának módosítása.



**Szabályok munkaterület:** Itt akkor, ha Ön [alkalmazhatósági szabályok kezelése](/sccm/sum/tools/updates-publisher-applicability-rules) , mentett, és telepített frissítésektől majd használni. A szabályok két típusa van:

-   Telepíthető szabályok – ezek a szabályok meghatározásához, hogy ha egy ügyfél kell-e egy adott frissítés telepítéséhez.
-   Telepített szabályok – ezek a szabályok ellenőrizze, hogy ha egy frissítés már telepítve van.

**Katalógusok munkaterület:** A munkaterület használatával ad hozzá és [software update katalógusok kezelése](/sccm/sum/tools/updates-publisher-catalogs). Ez magában foglalja a szoftverfrissítéseket e katalógusok az Updates Publisher tárházba való importálásakor.
## <a name="first-steps"></a>Első lépések
A kezdéshez, először [telepítése](/sccm/sum/tools/install-updates-publisher), majd [beállításokat adhat meg](/sccm/sum/tools/updates-publisher-options) az Updates Publisher.

