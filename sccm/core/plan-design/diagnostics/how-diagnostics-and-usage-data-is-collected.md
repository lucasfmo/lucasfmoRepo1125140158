---
title: "Diagnosztikai adatok gyűjtésének |} Microsoft Docs"
description: "További információk a hogyan gyűjti a System Center Configuration Manager diagnosztikai és használati adatokat saját magáról."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 24a233516058e645df2a43623855665b97b041b0
ms.openlocfilehash: 9c0165212fe34f460be2ce870d0542b616f3bc4d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-diagnostics-and-usage-data-is-collected-by-system-center-configuration-manager"></a>Diagnosztikai és használati adatok gyűjtése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager diagnosztikai és használati adatok gyűjtéséhez lesz, minden elsődleges hely SQL Server-lekérdezéseket futtat heti bontásban. Többhelyes hierarchiában a rendszer a központi adminisztrációs helyre replikálja az adatokat.  

A hierarchia legfelső szintjén a szolgáltatáskapcsolódási pont helyrendszerszerepkör a frissítések keresésekor küldi el ezeket az adatokat. A szolgáltatás kapcsolódási pont detemines hogyan az adatátvitel módja:  

-   **Online módban:** Diagnosztikai és használati adatok a felhőszolgáltatásnak pont a szolgáltatáskapcsolódási hetente egyszer automatikusan elküldi.  

-   **Kapcsolat nélküli módban:** Diagnosztikai és használati adatok továbbítása manuálisan történik a szolgáltatáskapcsolati eszköz segítségével. További információk: [A System Center Configuration Manager szolgáltatáskapcsolódási eszközének használata](../../../core/servers/manage/use-the-service-connection-tool.md).  

További információk: [A System Center Configuration Manager szolgáltatáskapcsolódási pontjának ismertetése](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

