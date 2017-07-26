---
title: Transfer Manager csomag |} Microsoft Docs
description: "Ismerje meg, hogyan Package Transfer Manager a System Center Configuration Managerben továbbítja a tartalmat a helykiszolgálóról a távoli terjesztési pontokra."
ms.custom: na
ms.date: 2/8/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3359f254-dd48-42b7-9eab-c92a3417e3fb
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 099345d59891841a336cbada896ec349751fecd3
ms.openlocfilehash: 54e54409a1792c7e28620a5e3cea3e8d8695c7d4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="package-transfer-manager-in-system-center-configuration-manager"></a>Package Transfer Manager a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager-hely a Package Transfer Manager az SMS_Executive szolgáltatást, amely a tartalomátvitelt kezeli a helykiszolgáló számítógépet és távoli terjesztési pontok egy helyen összetevője. (A távoli terjesztési pontok egyike a helykiszolgáló számítógépen nem található.) A Package Transfer Manager nem támogatja a konfigurációkat a rendszergazda által, de működését segítségével ismertetése a tartalomkezelési infrastruktúra megtervezése. Azt is segíthetnek tartalomterjesztés kapcsolatos problémák megoldásához.


Amikor egy hely egy vagy több távoli terjesztési pontjára történő tartalomterjesztéshez a **a Distribution Manager** létrehoz egy tartalomátviteli feladatot. Ezután értesíti a Package Transfer Manager, az elsődleges és másodlagos helykiszolgálókon a tartalom távoli terjesztési pontokra való átvitelének.

 A Package Transfer Manager naplózza a tevékenységeit a **pkgxfermgr.log** fájlt a helykiszolgálón. A naplófájl az egyetlen hely, ahol megtekintheti a Package Transfer Manager tevékenységeit.  

> [!NOTE]  
>  A Configuration Manager korábbi verzióiban a Distribution Manager kezeli a tartalom átvitelét a távoli terjesztési pontra. A Distribution Manager a helyek közötti tartalomátvitel is kezeli. A System Center Configuration Manager, a Distribution Manager továbbra is a két hely közötti tartalomátvitel kezelésére. A Package Transfer Manager azonban most nagy mennyiségű terjesztési pontra történő tartalomátvitel kezeli. Ez segít a tartalom központi telepítéséhez, mind a helyek között, és a terjesztési pontok egy helyen belül a összteljesítmény növelése.  

A szabványos terjesztési pontra történő tartalomátvitel esetében a Package Transfer Manager ugyanúgy működik, mint a Distribution Manager a korábbi verziókban a Configuration Manager. Vagyis aktívan kezeli a fájlok átvitelét az egyes távoli terjesztési pontokra. A lekéréses terjesztési pont tartalmat terjeszteni, azonban a Package Transfer Manager értesíti a tartalom lekéréses terjesztési pont érhető el. A lekéréses terjesztési pontot, majd a Configuration Manager átveszi az átviteli folyamat.  

A következő információkat ismerteti, hogyan Package Transfer Manager a tartalomátvitelt kezeli a normál terjesztési pontokra, és a lekéréses terjesztési pontként konfigurált terjesztési pontokra:
1.  **Rendszergazda központilag telepíti a tartalmat egy vagy több terjesztési pontok egy helyen.**  

    -   **Normál terjesztési pont:** A Distribution Manager létrehoz egy tartalomátviteli feladatot az adott tartalomhoz.  

    -   **Lekéréses terjesztési pont:** A Distribution Manager létrehoz egy tartalomátviteli feladatot az adott tartalomhoz.  

2.  **A Distribution Manager lefuttatja az előzetes ellenőrzéseket.**  

    -   **Normál terjesztési pont:** A Distribution Manager Alapszintű ellenőrzés futtatásával ellenőrizze, hogy mindegyik terjesztési pont készen áll a tartalom fogadására fut. Az ellenőrzés után a Distribution Manager értesíti a Package Transfer Managert, hogy indítsa el a tartalom átvitelét a terjesztési pontra.  

    -   **Lekéréses terjesztési pont:** A Distribution Manager elindítja Package Transfer Managert, amely ezután értesíti a lekéréses terjesztési pontot, hogy új tartalomátviteli feladat. A Distribution Manager nem ellenőrzi a távoli terjesztési pontok, a lekéréses terjesztési pontok, amelyek az állapotát, mivel mindegyik lekéréses terjesztési pont kezeli a saját tartalomátviteleit.  

3.  **A Package Transfer Manager felkészül a tartalmat.**  

    -   **Normál terjesztési pont:** A Package Transfer Manager megvizsgálja az Egypéldányos tartalomtárhoz konvertál, az összes megadott távoli terjesztési pontra. Ennek célja azonosítsa azokat a fájlokat, amelyek már megtalálhatók az adott terjesztési pontokon. Ezt követően az átviteli szolgáltatáshoz a Package Transfer Manager várólisták csak azokat a fájlokat, amelyek még nem jelent-e.  

        > [!NOTE]  
        >  Fájlok másolása a terjesztési pontra akkor is, ha a fájlok már szerepel a terjesztési pont egypéldányos tárolójában, használja a **újraterjeszteni** műveletet használja a tartalomhoz.  

    -   **Lekéréses terjesztési pont:** Az egyes lekéréses terjesztési pontok elosztása a Package Transfer Manager ellenőrzi a lekéréses terjesztési pontot forrás terjesztési pontokat, győződjön meg róla, ha a tartalom áll rendelkezésre.  

        -   Ha a tartalom elérhető legalább egy forrás terjesztési ponton, a Package Transfer Manager értesítést küld a lekéréses terjesztési pont. Az értesítés irányítja az adott terjesztési pont kezdje el a tartalomátvitel folyamatát. Az értesítés a fájl nevét és méretét, attribútumokat és kivonatértékeket tartalmazza.  

        -   A tartalom még nem érhető el, amikor a Package Transfer Manager nem küld értesítést a terjesztési pontra. Ehelyett ismétlődik, az ellenőrzés 20 percenként addig, amíg a tartalom nem érhető el. Majd ha a tartalom érhető el, a Package Transfer Manager elküldi az értesítést az adott lekéréses terjesztési pontra.  

        > [!NOTE]  
        >  A fájlok másolása a terjesztési pontra, akkor is, ha a fájlok már szerepel az Egypéldányos tárolóba, a lekéréses terjesztési pont lekéréses terjesztési pont, használjon a **újraterjeszteni** műveletet használja a tartalomhoz.  

4.  **Elkezdődik a tartalom átvitele.**  

    -   **Normál terjesztési pont:** A Package Transfer Manager átmásolja a fájlokat mindegyik távoli terjesztési pontra. Egy normál terjesztési pont átvitelkor:  

        -   Alapértelmezés szerint a Package Transfer Manager is egyszerre három egyedi csomagot feldolgozni, és ossza ki őket a párhuzamos öt terjesztési pontra. Együttesen, ezeket nevezik **egyidejű terjesztési beállításokhoz**. Az egyidejű terjesztés beállítása a **szoftverterjesztési összetevő tulajdonságai** helyekhez, látogasson el a **általános** fülre.  

        -   A Package Transfer Manager használt egyes terjesztési pontok ütemezésére és hálózati sávszélesség beállításait, amikor a tartalom a terjesztési pontra történő továbbítása. Ezek a beállítások konfigurálása a a **tulajdonságok** mindegyik távoli terjesztési pontok, navigáljon a **ütemezés** és **sebességhatárok** lapokon. További információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    -   **Lekéréses terjesztési pont:** Amikor egy lekéréses terjesztési pont megkapja az értesítésfájlt, elkezdi a tartalom átvitelének folyamatát. Az átviteli folyamat függetlenül fut az egyes lekéréses terjesztési pont:  

        1.   A lekéréses terjesztési azonosítja a tartalom terjesztése, amely már nincs az Egypéldányos tárolójában, és előkészíti a tartalmat tölthet le egy forrásként használt terjesztési pontját a fájlokat.  

        2.   Ezután a lekéréses terjesztési pont ellenőrzi az összes forrásként használt terjesztési pontját, sorrendben, amíg talál egy forrás terjesztési pontról, amely rendelkezik a tartalom érhető el. A lekéréses terjesztési pont forrásként szolgáló terjesztési pont azonosítja a tartalommal, amikor megkezdi az adott tartalom letöltését.  

        > [!NOTE]  
        >  A tartalom letöltésére, a lekéréses terjesztési pont által a folyamat megegyezik a Configuration Manager-ügyfelek által használt. A tartalom átvitelét a lekéréses terjesztési pont, az egyidejű átvitel beállításai nem használt. Ütemezési és sávszélesség-szabályozás a normál terjesztési pontok nem konfigurált beállítások használhatók.  

5.  **Befejeződik a tartalom átvitele.**  

    -   **Normál terjesztési pont:** Miután a Package Transfer Manager elkészült átadó fájlok minden egyes megadott távoli terjesztési pontra, ellenőrzi a terjesztési ponton a tartalom kivonatát. Majd azt értesíti a Distribution Manager, hogy a terjesztés befejeződéséről.  

    -   **Lekéréses terjesztési pont:** Miután a lekéréses terjesztési pont befejezte a tartalom letöltését, a terjesztési pont ellenőrzi a tartalom kivonatát. Ezután az állapotüzenetet küld a helyfelügyeleti ponthoz a sikeres műveletet jelző. Ha ez az állapot 60 perc elteltével nem érkezik, a Package Transfer Manager felébred újra. Győződjön meg arról, hogy a lekéréses terjesztési pont letöltötte-e a tartalom a lekéréses terjesztési pont ellenőrzi. Ha a tartalom letöltése éppen folyamatban van, a Package Transfer Manager alszik, mielőtt ismét ellenőrzi a lekéréses terjesztési pont egy másik 60 percig. A ciklus addig folytatódik, amíg a lekéréses terjesztési pont be nem fejezi a tartalomátvitelt.  

