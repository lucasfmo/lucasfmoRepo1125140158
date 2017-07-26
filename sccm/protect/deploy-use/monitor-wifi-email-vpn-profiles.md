---
title: "E-mailek, Wi-Fi és VPN-profilok figyelése |} Microsoft Docs"
description: "Megtudhatja, hogyan figyelheti az e-mailek, Wi-Fi és VPN-profilok a System Center Configuration Manager megfelelőségi állapotát."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2315b8b-98bc-40e1-8ef9-bfb5e69ab109
caps.latest.revision: 4
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 73d941633d270cf9628f8be14e1e56f3c78624b6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="monitor-email-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>E-mailek, Wi-Fi és VPN-profilok a System Center Configuration Manager figyelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután telepítette a System Center Configuration Manager e-mailek, Wi-Fi vagy VPN-profilok a felhasználók számára a hierarchiában, az alábbi eljárásokkal figyelheti a profil megfelelőségi állapotát:  

-   [Megfelelési eredmények megtekintése a Configuration Manager konzolon](#BKMK_console)  

-   [Megfelelési eredmények megtekintése jelentések segítségével](#BKMK_Reports)  

##  <a name="BKMK_console"></a> Megfelelési eredmények megtekintése a Configuration Manager konzolon  
 Ezzel az eljárással telepített profilok megfelelőségére vonatkozó részletek megtekintéséhez a System Center Configuration Manager konzolon.  

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Az alábbi módon tekintheti meg a megfelelési eredményeket a Configuration Manager konzolon:  

1.  A System Center Configuration Manager konzolon kattintson **figyelés**.  

2.  A **Figyelés** munkaterületen kattintson a **Központi telepítések**elemre.  

3.  Az a **központi telepítések** listára, válassza ki a profilok központi telepítését, amelyre vonatkozóan szeretné ellenőrizni a megfelelőségi információkat.  

4.  A profilok központi telepítésének megfelelőségére vonatkozó összefoglaló információkat a főoldalon tekintheti meg. Részletesebb adatok megtekintéséhez válassza ki a profilok azon központi telepítését, majd a a **Home** lap a **telepítési** csoportjában kattintson **állapotának megtekintése** megnyitásához a **központi telepítési állapot** lap.  

     A **Telepítés állapota** lapon a következő fülek találhatók:  

    -   **Megfelelő:** Az a profil megfelelőségét az érintett eszközök száma alapján mutatja. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt, ahol megjelenik a profilnak megfelelő összes felhasználó. A **eszköz adatai** ablaktáblán megjelennek azok a felhasználók, akik megfelelnek a profilnak. További információk megjelenítéséhez a listában kattintson duplán a kívánt felhasználónévre.  

        > [!IMPORTANT]  
        >  A profil nem kerül kiértékelésre, ha nem alkalmazható az ügyféleszközre; azonban az megfelelőként adja vissza.  

    -   **Hiba:** Megjeleníti az összes a kiválasztott profil központi telepítésére vonatkozó hibákat az érintett eszközök száma alapján. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt, ahol megjelenik a profillal kapcsolatban hibát okozó összes felhasználó. Amikor kijelöl egy felhasználót, az **Eszköz adatai** ablaktáblán megjelennek azok a felhasználók, akiket a kijelölt probléma érint. A problémáról további információk megjelenítéséhez kattintson duplán a kívánt felhasználónévre a listában.  

    -   **Nem megfelelő:** Az érintett eszközök száma alapján profilon belüli összes nem megfelelő szabályok listáját jeleníti meg. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt, ahol megjelenik a profilnak nem megfelelő összes felhasználó. Amikor kijelöl egy felhasználót, az **Eszköz adatai** ablaktáblán megjelennek azok a felhasználók, akiket a kijelölt probléma érint. A problémáról további információk megjelenítéséhez kattintson duplán a kívánt felhasználónévre a listában.  

    -   **Ismeretlen:** Megjeleníti az összes olyan felhasználó, nem jelentett megfelelőséget, a kijelölt központi telepítésére vonatkozóan az aktuális ügyfélállapotával együtt az eszközökön.  

5.  Az a **központi telepítési állapot** lapon áttekintheti a központilag telepített profil megfelelőségével kapcsolatos részletes információk. A **Központi telepítések** csomópont alatt létrejön egy ideiglenes csomópont, amellyel később gyorsan előkeresheti ezt az információt.  

##  <a name="BKMK_Reports"></a> Megfelelési eredmények megtekintése jelentések segítségével  
 Megfelelőségi beállítások, például a profilok a System Center Configuration Managerben, is számos olyan beépített jelentéseket, amelyek segítségével figyelemmel profilokkal kapcsolatos információk. Ezek a jelentések a **Megfelelőség és beállítások kezelése**jelentési kategóriába tartoznak.  

> [!IMPORTANT]  
>  Ha a megfelelőségi beállítások jelentéseiben az **Eszközszűrő** és a **Felhasználószűrő** paraméterek szerepelnek, helyettesítő (%) karaktert kell használnia.  

 A System Center Configuration Manager jelentéskészítési konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

