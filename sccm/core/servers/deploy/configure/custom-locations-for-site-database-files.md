---
title: "Egyéni adatbázisfájl-helyek |} Microsoft Docs"
description: "Megtudhatja, hogyan adhatja meg az egyéni tárolóhelyeket az SQL Server adatbázisfájljaihoz."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e5155aa8c03b7e0c200d083024c8fa386f97aa7
ms.openlocfilehash: cfac2c03c1b71b40c68d8acd5fbd96c5e98caaa9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>Egyéni helyek a System Center Configuration Manager helyadatbázisának fájljait

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 A System Center Configuration Manager támogatja az egyéni tárolóhelyeket az SQL Server adatbázisfájljaihoz.  

> [!NOTE]  
>  Ha egy SQL Server-fürtöt használ, a lehetőség nem alapértelmezett fájlhelyek választására nem érhető el.  

 **A telepítés során** új elsődleges hely vagy központi adminisztrációs hely, a következőket teheti:  

-   **A Helyadatbázis nem alapértelmezett fájlhelyek választására**: A Configuration Manager telepítő létrehozza a Helyadatbázis ezeket a helyeket.  

-   **Adja meg az egyéni fájlhelyeket használó előre létrehozott SQL Server-adatbázis használatát**:  A Configuration Manager telepítő majd a, hogy az előre létrehozott adatbázis és az előre konfigurált fájlhelyeit használja.  

**A telepítés után**, módosíthatja a hely adatbázis-fájlok helyét. Ehhez szükséges, hogy a hely leállítása és az SQL Server a fájlhely szerkesztése:  

-   A Configuration Manager-hely kiszolgálóján állítsa le a **SMS_Executive** szolgáltatás.  

-   SQL Server adott verziójának dokumentációjában használatával a felhasználói adatbázis áthelyezése leírtakat. Például ha az SQL Server 2014 használata esetén tekintse meg [felhasználói adatbázisok áthelyezése](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) a TechNet webhelyen.  

-   Miután elkészült az adatbázisfájl áthelyezésével, indítsa újra a **SMS_Executive** szolgáltatás a Configuration Manager helykiszolgálón.  

