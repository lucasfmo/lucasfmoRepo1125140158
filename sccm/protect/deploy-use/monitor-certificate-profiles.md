---
title: "Tanúsítványprofilok figyelése |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager a tanúsítványprofilok megfelelőségi állapotát."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98feaa06-64b1-4e86-a122-93017c97cd4f
caps.latest.revision: 7
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 84e275fa5b17bc703da22fb686ef9050d17e557f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-certificate-profiles-in-system-center-configuration-manager"></a>A System Center Configuration Managerben tanúsítványprofilok figyelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Megfelelési eredmények megtekintése a Configuration Manager konzolon  

Figyelendő SCEP-tanúsítvány megfelelőségének nem használja a konzol ahelyett, hogy [jelentések](#view-compliance-results-by-using-reports). 

1.  Kattintson a Configuration Manager konzol **figyelés**>  **központi telepítések**.  

3.  Válassza ki a tanúsítványprofilok azon központi telepítését iránt.  

4.  Tekintse át az összefoglaló tanúsítvány megfelelőségi információkat a főoldalon. Részletes információkat, válassza ki a tanúsítványprofilt, majd a a **Home** lap a **telepítési** csoportjában válassza **állapotának megtekintése** megnyitásához a **központi telepítési állapot** lap.  

     A **Telepítés állapota** lapon a következő fülek találhatók:  

    -   **Megfelelő**: A tanúsítványprofil megfelelőségét az az érintett eszközök száma alapján mutatja. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt. Ez a csomópont minden olyan felhasználót tartalmaz, amelyik megfelel a tanúsítványprofilnak. Az **Eszköz adatai** ablaktáblán jelennek meg azok a felhasználók, amelyek megfelelnek ennek a profilnak. Kattintson duplán a felhasználó további információt a listában.  

        > [!IMPORTANT]  
        >  A tanúsítványprofil nem kerül kiértékelésre, ha nem alkalmazható az ügyféleszközre, hanem a rendszer megfelelőként jelzi azt.  

    -   **Hiba**: Megjeleníti az összes a kiválasztott tanúsítvány profil központi telepítésére vonatkozó hibákat az érintett eszközök száma alapján. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt. Ez a csomópont tartalmazza az összes olyan felhasználót, amelyik ezzel a profillal hibát jelzett. Amikor kijelöl egy felhasználót, az **Eszköz adatai** ablaktáblán megjelennek azok a felhasználók, akiket a kijelölt probléma érint. Kattintson duplán a felhasználó további információk megjelenítéséhez a listában.  

    -   **Nem megfelelő**: A tanúsítványprofil, az érintett eszközök száma alapján nem megfelelő szabályok teljes listáját jeleníti meg. A megfelelő szabályra duplán kattintva ideiglenes csomópontot hozhat létre az **Eszközök és megfelelőség** munkaterület **Felhasználók** csomópontja alatt. Ez a csomópont tartalmazza az összes olyan felhasználót, amelyik nem megfelelő ezzel a profillal. Amikor kijelöl egy felhasználót, az **Eszköz adatai** ablaktáblán megjelennek azok a felhasználók, akiket a kijelölt probléma érint. A problémáról további információk megjelenítéséhez kattintson duplán a kívánt felhasználónévre a listában.  

    -   **Ismeretlen**: Megjeleníti az összes olyan felhasználó, nem jelentett megfelelőséget, a tanúsítványprofilok kiválasztott központi telepítésére az aktuális ügyfélállapotával együtt az eszközök számára.  

5.  Az a **központi telepítési állapot** lapon, a központilag telepített tanúsítványprofil megfelelőségével kapcsolatos részletes információk. A **Központi telepítések** csomópont alatt létrejön egy ideiglenes csomópont, amellyel később gyorsan előkeresheti ezt az információt.  

     A tanúsítvány beléptetési állapota szám formájában jelenik meg. Az alábbi táblázat segítségével értelmezhető az egyes számok jelentése:  

    |Beléptetés állapota|Leírás|  
    |-----------------------|-----------------|  
    |0x00000001|A beléptetés sikeres volt, a tanúsítvány ki van állítva.|  
    |0x00000002|A kérés elküldése megtörtént, a beléptetés függőben van, vagy pedig a kérés kiadása sávon kívül történt.|  
    |0x00000004|A beléptetést el kell halasztani.|  
    |0x00000010|Hiba történt.|  
    |0x00000020|A beléptetés állapota ismeretlen.|  
    |0x00000040|Az állapotinformációt kihagyta a folyamat. Ez akkor fordulhat elő, ha a HYPERLINK "http://msdn.microsoft.com/en-us/windows/ms721572" \l "_security_certification_authority_gly" hitelesítésszolgáltató érvénytelen, vagy nincs beállítva a figyelésre.|  
    |0x00000100|A beléptetést elutasították.|  

##  <a name="view-compliance-results-by-using-reports"></a>Megfelelési eredmények megtekintése jelentések segítségével

 A System Center Configuration Manager megfelelőségi beállítások közé tartozik a beépített jelentéseket, amelyek a tanúsítványprofilokra vonatkozó információk megfigyelésére használhatja. Ezek a jelentések a **Megfelelőség és beállítások kezelése**jelentési kategóriába tartoznak.  

> [!IMPORTANT]  
>  Ha a megfelelőségi beállítások jelentéseiben az **Eszközszűrő** és a **Felhasználószűrő** paraméter szerepel, helyettesítő (%) karaktert kell használni.  

SCEP-tanúsítvány megfelelőségének használja a tanúsítvány jelentések jelentéscsomópont alatt figyelése **hozzáférés a vállalati erőforrásokhoz**:  

 -   Tanúsítványkiadási előzmények  
 -   A hamarosan lejáró tanúsítvánnyal rendelkező eszközök listája  
 -   Tanúsítványkiadási állapot szerint rendezett eszközlista  



 A System Center Configuration Manager jelentéskészítési konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

