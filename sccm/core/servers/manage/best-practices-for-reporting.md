---
title: "Gyakorlati tanácsok Reporting |} Microsoft Docs"
description: "Olvassa el a System Center Configuration Manager jelentéskészítési funkció használatával kapcsolatos néhány hasznos tipp."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 759258999f3eaa810803a6a7f856f00fe7771a9e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-reporting-in-system-center-configuration-manager"></a>Ajánlott eljárások jelentéskészítéshez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a következő gyakorlati tanácsok a System Center Configuration Manager Jelentéskészítés:  

## <a name="for-best-performance-install-the-reporting-services-point-on-a-remote-site-system-server"></a>A legjobb teljesítmény érdekében telepítse távoli helyrendszer-kiszolgálóra a jelentéskészítési szolgáltatási pontot  
 Bár a jelentéskészítési szolgáltatási pont helykiszolgálóra és távoli helyrendszerre is telepíthető, növelhető a teljesítmény, ha a jelentéskészítési szolgáltatási pontot távoli helyrendszer-kiszolgálóra telepíti.  

## <a name="optimize-sql-server-reporting-services-queries"></a>Az SQL Server Reporting Services lekérdezéseinek optimalizálása  
 A jelentéskészítés esetleges késedelmét jellemzően a lekérdezések futtatására és az eredmények visszakeresésére fordított idő okozza. A Microsoft SQL Server használatakor a lekérdezések optimalizálását segíthetik az olyan eszközök, mint a Lekérdezéselemző és a Profiler.  

## <a name="schedule-report-subscription-processing-to-run-outside-standard-office-hours"></a>A jelentés-előfizetés feldolgozását ütemezze úgy, hogy az a szabályos munkaidőn kívül történjék.  
 Amikor csak lehetséges – jelentés előfizetés feldolgozását ütemezze úgy futtatásához a munkaidőn kívül standard órái minimalizálása érdekében a Processzor feldolgozási a Configuration Manager Helyadatbázis-kiszolgálón. Ezzel a gyakorlattal javítja az előre nem tervezett jelentéskérelmek igénybe vehetőségét is.  

## <a name="next-steps"></a>További lépések
[Jelentéskészítési beállítások konfigurálásához](configuring-reporting.md)

