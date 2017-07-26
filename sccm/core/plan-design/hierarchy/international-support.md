---
title: "Nemzetközi támogatás |} Microsoft Docs"
description: "System Center Configuration Manager országonként eltérő igényeknek ahhoz, hogy konfigurálja."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 40e018084dd2703327ff653f962f488432b1ec98
ms.openlocfilehash: 3bab51be96445f766e8f5bbf54eee854e5d09cee
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="international-support-in-system-center-configuration-manager"></a>Nemzetközi támogatás a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A következő szakaszok olyan technikai részleteket annak érdekében, hogy a System Center Configuration Manager országonként eltérő igényeknek megfelelő.  

## <a name="gb18030-requirements"></a>A GB18030 követelményrendszer  
 A Configuration Manager eleget tesz a GB18030 határozzák meg, hogy a Configuration Manager Kínában használható. Configuration Manager telepítési rendelkeznie kell a következő beállításokat, hogy megfeleljen a GB18030 követelményeinek:  

-   Minden helykiszolgáló és SQL Server-számítógépen, és a Configuration Managerben használt kínai operációs rendszert kell használnia.  

-   Mindegyik helyadatbázisnak és az SQL Server minden példányának ugyanazt a sorbarendezési rendet kell használni, és az csak a következők egyike lehet:  

    -   Chinese_Simplified_Pinyin_100_CI_AI  

    -   Chinese_Simplified_Stroke_Order_100_CI_AI  

    > [!NOTE]  
    >  Ezek az adatbázisi sorrendek kivételt leírásban ki vannak emelve követelmények [SQL Server-verziók támogatása a System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   A hierarchiában mindegyik helykiszolgáló rendszerkötetének gyökérmappájában el kell helyezni a **GB18030.SMS** nevű fájlt. Ez a fájl nem tartalmaz semmilyen adatot, hogy eleget tegyen ennek a követelménynek lehet akár egy ilyen nevű üres szövegfájl is.  

