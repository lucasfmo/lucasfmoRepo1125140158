---
title: "Diagnosztikai és használati adatok |} Microsoft Docs"
description: "További tudnivalók a diagnosztikai és használati adatok, amelyek a System Center Configuration Manager gyűjt saját magáról."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: 9
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 4a4b7c9c0d40b6bd3ea2f318e37d744f1a0cc084
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Diagnosztikai és használati adatok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager diagnosztikai és használati adatokat saját magáról, a telepítési élmény, minőségét és a jövőbeli kiadások biztonságának javítása érdekében a Microsoft által használt gyűjti.  

 Diagnosztikai és használati adatok minden System Center Configuration Manager-hierarchiában engedélyezve van. SQL Server-lekérdezéseket, amelyek hetente futnak az egyes elsődleges helyeken és a központi adminisztrációs helyen áll. Amikor a hierarchia központi adminisztrációs helyet használ, a rendszer erre a helyre replikálja az elsődleges helyekről származó adatokat. A hierarchia legfelső szintű helyen a szolgáltatáskapcsolódási pont keresésekor küldi el ezeket az információkat a frissítéseket. Ha a szolgáltatáskapcsolódási pont kapcsolat nélküli módban van, a rendszer a szolgáltatáskapcsolódási eszközzel küldi át az adatokat.  

> [!NOTE]  
>  A Configuration Manager gyűjti az adatokat csak a hely SQL server adatbázisa, és közvetlenül az ügyfelektől vagy helykiszolgálóktól nem gyűjt adatokat.  

 További információkért lásd: a [a System Center Configuration Manager adatvédelmi nyilatkozata](http://go.microsoft.com/fwlink/?LinkID=626527).  

 További tudnivalók a diagnosztikai és használati adatok a System Center Configuration Manager a következő cikkekben:  

-   [Diagnosztikai és használati adatok használatáról a System Center Configuration Managerhez](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   Diagnosztikai és használati adatok gyűjtésének szintjei:
    - [Diagnosztikai adatok 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Diagnosztikai adatok 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Diagnosztikai adatok 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    

<!--
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [Diagnosztikai és használati adatok gyűjtése hogyan System Center Configuration Managerrel](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [Diagnosztikai és használati adatok megtekintése a System Center Configuration Managerhez](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [Felhasználói élmény fokozása Program (CEIP) a System Center Configuration Managerhez](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

-   [A System Center Configuration Manager diagnosztikai és használati adatok kapcsolatos gyakran ismételt kérdések](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>Lásd még:  
 [Tudnivalók a szolgáltatáskapcsolódási pont a System Center Configuration Managerben](../../../core/servers/deploy/configure/about-the-service-connection-point.md)

