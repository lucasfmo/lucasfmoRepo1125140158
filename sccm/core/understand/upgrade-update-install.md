---
title: "Frissítés, frissítés és telepítés |} Microsoft Docs"
description: "Ismerje meg, hogy a telepítés, frissítés és kezelése a Configuration Manager-infrastruktúrát a frissítés a feltételek közötti különbség."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17fab17f-304d-4f6a-87c7-30ab4f5521ed
caps.latest.revision: 0
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d0735c170820259ac8bb6706aac7cc5569a1628
ms.openlocfilehash: 6bd6cd7ea3c41fa1d70e17a1290c9f1f74cc9e37
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="about-upgrade-update-and-install-for-site-and-hierarchy-infrastructure"></a>A frissítés frissítése, illetve a hely és hierarchia-infrastruktúra telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Kezelése a System Center Configuration Manager-hely és hierarchia-infrastruktúra, a feltételek *frissítése*, *frissítése*, és *telepítése* használt három különböző fogalmi kört alkotnak.

## <a name="upgrade"></a>Upgrade
*Frissítés* vagy *helybeni frissítést*, való átalakításakor a Configuration Manager 2012 hely vagy hierarchia, amely futtatja a System Center Configuration Manager szolgál.
A System Center Configuration Manager frissítése System Center 2012 Configuration Manager esetén továbbra is ugyanazokat a kiszolgálókat a helyek és helyrendszer-kiszolgálók üzemeltetésére használhatja, és hogy megőrizze a meglévő adatok és konfigurációk a Configuration Manager.  Ez nem azonos a [áttelepítési](/sccm/core/migration/migrate-data-between-hierarchies) amely módja a tartsa meg a konfigurációk és a felügyelt eszközökkel kapcsolatos adatokat új hardverre telepített új System Center Configuration Manager-helyek használata során.

További részletekért lásd: [frissítése a System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).



## <a name="update"></a>Frissítés
*Frissítés* szolgál a konzolon belüli frissítések telepítése a System Center Configuration Manager és a sávon kívüli frissítéseket, amelyek nem kézbesíthetők fel az a Configuration Manager konzolon belüli frissítések érhetők el. A konzolon belüli frissítések módosítható az a hely aktuális ág (vagy a Technical Preview-hely) verzióját, hogy egy újabb verziója fusson. Például, hogy a hely 1606 verzióját futtatja, ha egy frissítés 1610 telepítheti. Frissítések is telepíthető egy ismert probléma, javítja a helyek verziója módosítása nélkül.      

Általában frissítések hozzáadása biztonsági javítások, minőségének javítása és új funkciók a jelenlegi telepítés. A Technical Preview fiókirodai használja, ha egy frissítés telepítheti a Technical Preview újabb verziója.
-    Megadhatja a konzolon belüli frissítés telepítésének elindítása a hierarchia legfelső szintű helyen.
- Minden frissítés érhető el a konzol telepítése. Például ha a webhely az 1602-es verzió fut, és 1606 és a 1610 felajánlja, érdemes 1610 verziójának telepítése, mert minden egyes verzió magában foglalja a funkcióktól, amelyek először elérhetők a korábban kiadott verzióihoz.
- Új frissítést a legfelső szintű hely telepítésének befejezése után a gyermek elsődleges helyek automatikusan elindítja a folyamat frissíteni. Beállíthatja azonban [szolgáltatás Windows](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkservicewindowa-service-windows-for-site-servers) frissítések időzítése szabályozására.
- A másodlagos helyek nem telepíti automatikusan a frissítéseket. Ehelyett manuálisan is elindítható a frissítést a Configuration Manager konzolon.

Kapcsolatban bővebben lásd: [frissítések a System Center Configuration Manager](/sccm/core/servers/manage/updates), és [a System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview).



## <a name="install"></a>Telepítse
*Telepítés* használhatók, amikor egy új Configuration Manager-hierarchia létrehozása a teljesen, vagy további helyek hozzáadása egy meglévő hierarchiához.  

Amikor új elsődleges hely vagy központi adminisztrációs helyet telepít, a setup.exe és a kapcsolódó forrásfájlokat, amelyekkel a hely a telepítési forgatókönyv függ.

Kapcsolatban bővebben lásd: [helyek telepítését előkészítése](/sccm/core/servers/deploy/install/prepare-to-install-sites).

