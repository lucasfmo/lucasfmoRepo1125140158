---
title: "Áttelepítés figyelése |} Microsoft Docs"
description: "Útmutató a Configuration Manager konzolon a figyelheti a folyamat és annak sikeressége az áttelepítési feladatokat."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: 4
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e3d3f4194b06442e34c10988a20fe9ca40ac5d7
ms.openlocfilehash: 896807ec2c4be2835094a27add59d4cc09e93add
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-to-monitor-migration-activity-in-system-center-configuration-manager"></a>A System Center Configuration Managerben az áttelepítési tevékenység figyelésének tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerrel, a Configuration Manager konzolon láthatja, hogy a célhierarchiához kapcsolódó áttelepítési figyelheti meg. A Configuration Manager konzol a **felügyeleti** munkaterület, használhatja a **áttelepítési** csomópont folyamatának és sikerességének az áttelepítési feladatok figyelése. Minden áttelepítési feladat, amely azonosítja az áttelepített objektumokat, még nem áttelepített objektumokat, és az objektumok, amelyek ki lettek zárva ebből az áttelepítési feladat összefoglaló információkat tekintheti meg. Az esetleges áttelepítési problémák részleteit is megjelenik.  

## <a name="view-migration-progress"></a>Áttelepítési folyamat megtekintése  
 Áttelepítési feladat állapotának megtekintéséhez használja a következő műveletek:  

-   Az a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki a **áttelepítési feladatok** csomópontra, jelölje ki az áttelepítési feladatot, és válassza a **objektumok a feladatban** fülre.  

-   A Configuration Manager naplófájljainak használja, az áttelepítés lefolyásának áttekintéséhez, és az esetleges problémák felismeréséhez. Áttelepítéskezelő a Configuration Manager folyamata, amelyik nyomon követi az áttelepítési műveleteket, és a migmctrl.log fájlba rögzíti a  **\&lt; Telepítésiútvonal\>\\naplók** mappájában a helykiszolgálón.  

    > [!NOTE]  
    >  Ha egy áttelepítési feladat sikertelen lesz, amint lehetséges tekintse át a részleteket a migmctrl.log fájl. Az áttelepítési napló bejegyzései folyamatosan kerülnek be a fájlt, és a régi részletek felülíródnak. Ha a bejegyzések felülíródtak, nem feltétlenül lehet azonosítani, hogy az áttelepített objektumok esetleg felmerülő problémákat áttelepítéshez kapcsolódnak. Az áttelepítési tevékenység naplózása a felső\-függetlenül a hely a Configuration Manager konzol csatlakozik, az áttelepítés konfigurálásakor a hierarchia szintű helyén.  

-   Használja a Configuration Manager jelentéskészítési. A Configuration Manager kínál számos beépített\-áttelepítési, vagy a jelentésekben ezeket szerkeszteni is lehet az igényeinek. A Configuration Manager-jelentésekkel kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

