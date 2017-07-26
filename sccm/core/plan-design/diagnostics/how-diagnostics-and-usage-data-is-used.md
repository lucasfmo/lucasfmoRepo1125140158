---
title: "Diagnosztikai adatok felhasználása |} Microsoft Docs"
description: "További tudnivalók a Microsoft hogyan használja a diagnosztikai és használati adatok alapján gyűjti a System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 24a233516058e645df2a43623855665b97b041b0
ms.openlocfilehash: 9864f6ba7b9a2211c99b1a5d9ebd582e01ccfeb6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>A diagnosztikai és használati adatok felhasználása a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Gyűjti a System Center Configuration Manager diagnosztikai és használati adatokat a Microsoft szinte azonnali visszajelzést biztosítanak arról, hogyan a termék működik-e, és a jövőbeli frissítések hangolására szolgálnak. Emellett az éles környezetben használt konfigurációk tervezését és tesztelését elősegítő konfigurációs adatok is láthatóvá válnak. Példa:  

-   A helykiszolgálók által használt Windows Server-verziók  

-   A telepített nyelvi csomagok  

-   Az SQL-séma eltérése a a termék alapértelmezéséhez képest  

Ezen adatok segítenek a mérnöki csapatnak megtervezni a jövőbeli teszteket a legjobb élmény biztosítása érdekében a leggyakoribb konfigurációk esetében. Frissítések a Configuration Manager kiadása gyorsabb ütemben történik (a gyorsan változó technológiák, például a Windows 10 és a Microsoft Intune jobb támogatása), mivel ezek az adatok kulcsfontosságúak a gyors módosításokhoz és alkalmazkodáshoz.  

Ugyanilyen fontos a módját a diagnosztikai és használati adatok nem használt. A Microsoft nem használja ezeket az adatokat a következőkre:  

-   Licencauditálási célokra, például az ügyfél használati adatainak összevetésére a licencszerződésekkel  

-   A nem támogatott termékek auditálására  

-   A rendelkezésre álló adatok, például a funkciók használata vagy a földrajzi hely (időzóna) alapján hirdetési  

##  <a name="bkmk_improve"></a>Példák hogyan diagnosztikai és használati adatok javítja a termék  
A Microsoft a rendelkezésre álló adatokat a termék fejlesztésére használja. Az alábbiakban néhány példa:  

-   **A régebbi kiszolgálói operációs rendszerek felülvizsgált támogatása:**  

     A System Center Configuration Manager aktuális ágához kínált kezdeti támogatás a Windows Server 2008 R2 támogatási ütemtervére korlátozott. Vizsgálata folyamatban volt a Configuration Manager aktuális ágának frissített ügyfelek használati adatait, után felismertük az igényt, felülvizsgálata és kiterjesztése a ütemterv az ügyfelek, akik továbbra is használhatják a kiszolgáló operációs rendszer fogadó helyrendszer-kiszolgálók és helyrendszerszerepkörök támogatásához.  

-   **Továbbfejlesztett előfeltétel-ellenőrzések:**  

     Használati adatok alapján továbbfejlesztettük eltávolítottuk az elavult szabályokat, újabb eseteket, és egyes esetekben bizonyos problémák automatikus javítása egy frissítés telepítésére vonatkozó előfeltételek ellenőrzését.  

