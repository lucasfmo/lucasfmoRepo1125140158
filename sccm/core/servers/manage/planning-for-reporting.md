---
title: "A jelentéskészítés tervezése |} Microsoft Docs"
description: "A telepítés részleteiből a biztonságra és a hálózati sávszélesség fontos a Configuration Manager jelentéskészítésének tervezéséhez nyújtanak."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ff920c84-d5c8-458c-b67f-bc7219b05690
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 119f501057bf44e483be31db20b88326b3d05ebb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-reporting-in-system-center-configuration-manager"></a>A jelentéskészítés tervezése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Jelentéskészítés a System Center Configuration Managerben biztosítja az eszközöket és erőforrásokat, amelyek segítséget nyújtanak az SQL Server Reporting Services fejlett jelentéskészítési funkcióinak használata. A következő részekben a Configuration Manager jelentéskészítésének tervezéséhez nyújtanak segítséget.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> A jelentéskészítési szolgáltatási pont telepítési helyének meghatározása  
 Ha egy helyen futtatja a Configuration Manager-jelentések, a jelentéseknek hozzáférésük van az információk a helyadatbázisban, amelyben csatlakozik. A következő szakaszok segítenek meghatározni, hogy hova telepítse a jelentéskészítési szolgáltatási pontot, és hogy az milyen adatforrást használjon.  

> [!NOTE]  
>  A Configuration Manager rendszert tervezésével kapcsolatos további információkért lásd: [helyrendszer-szerepkörök hozzáadásához](../deploy/configure/add-site-system-roles.md).  

###  <a name="BKMK_SupportedSiteServers"></a> Támogatott helyrendszer-kiszolgálók  
 A jelentéskészítési szolgáltatási pont telepíthető a központi felügyeleti helyre és az elsődleges helyekre, valamint a hierarchiában az adott hely vagy más hely több helyrendszerére. Másodlagos helyeken a jelentéskészítési szolgáltatási pont nem támogatott. Az adott helyen az első jelentéskészítési szolgáltatási pont lesz alapértelmezett jelentéskiszolgálóként konfigurálva. Egy helyen több jelentéskészítési szolgáltatási pontok adhat hozzá, de az egyes helyeken az alapértelmezett jelentéskiszolgáló használható aktívan Configuration Manager jelentések. A jelentéskészítési szolgáltatási pont telepíthető helykiszolgálóra vagy távoli helykiszolgálóra. Teljesítési szempontból viszont a bevált gyakorlat a jelentéskészítési szolgáltatások távoli helyrendszer-kiszolgálókon történő használata.  

###  <a name="BKMK_DataReplication"></a> Adatreplikálási megfontolások  
 A Configuration Manager osztályozza a globális adatok vagy a helyadatok replikált adatokat. A globális adatok azokat az objektumokat jelentik, amelyeket rendszergazda felhasználó hozott létre és replikálva lettek a hierarchia összes helyére, a másodlagos helyek viszont csak a globális adatok részhalmazát kapják. A globális adatok közé tartoznak például a szoftverek központi telepítései, a szoftverfrissítések, a gyűjtemények és a szerepkör alapú rendszergazdai biztonsági hatókörök. Helyadatok azok az operatív információk, hogy a Configuration Manager elsődleges hely és az ügyfelek, az elsődleges helyekhez jelentés létrehozása. A helyadatok replikálódnak a központi felügyeleti hely részére, de más elsődleges helyek részére nem. Az ilyen helyadatok közé tartoznak a hardverleltári adatok, az állapotüzenetek, a riasztások és a lekérdezésalapú gyűjtemények eredményei. A helyadatok csak a központi felügyeleti helyen és azon az elsődleges helyen láthatók, ahonnan származnak az adatok.  

 A jelentéskészítési szolgáltatási pontok telepítési helyének meghatározásához vegye figyelembe a következő tényezőket:  

-   A jelentéskészítési szolgáltatási pont a központi felügyeleti helyi adatbázissal rendelkező, a jelentéskészítési adatok forrásaként van a Configuration Manager-hierarchiában a hozzáférést minden globális és helyi adathoz. Ha a hierarchiában több helyre vonatkozó helyadatokat tartalmaznak jelentéseket van szüksége, javasoljuk, hogy telepítse a jelentéskészítési szolgáltatási pontot egy helyrendszerre, a központi adminisztrációs helyen, és a központi adminisztrációs hely adatbázisát használja a jelentéskészítési adatok forrásaként.  

-   Az alárendelt elsődleges helyadatbázissal rendelkező jelentéskészítési szolgáltatási pontnak, mint jelentéskészítési adatforrásnak hozzáférése van a globális adatokhoz és csak a helyi elsődleges hely és az annak esetleg alárendelt másodlagos helyek helyadataihoz. A Configuration Manager-hierarchiában lévő többi elsődleges hely helyadatait nem replikálódnak az elsődleges hely, és ezért a jelentéskészítési szolgáltatások nem tudja elérni. Ha egy adott elsődleges hely helyadatait és globális adatokat tartalmazó jelentések van szüksége, de nem szeretné, hogy a felhasználók elérhessék a helyadatokat más elsődleges helyekről, telepíteni egy jelentéskészítési szolgáltatási pontot egy helyrendszerre, az elsődleges helyen, és az elsődleges hely adatbázisát használja a jelentéskészítési adatok forrásaként.  

###  <a name="BKMK_NetworkBandwidth"></a> Hálózati sávszélességgel kapcsolatos megfontolások  
 Az azonos helyen belüli helyrendszer-kiszolgálók az egymás közötti kommunikációhoz a hely konfigurálásától függően SMB (Server Message Block), HTTP vagy HTTPS protokollt használnak. Mivel ez a kommunikáció felügyelet nélküli, és a hálózati sávszélesség szabályozása nélkül bármikor előfordulhat, a jelentéskészítési szolgáltatási pont szerepkörének a helyrendszerre telepítése előtt ellenőrizze a rendelkezésre álló hálózati sávszélességet.  

> [!NOTE]  
>  További információ a helyrendszerek tervezéséről: [helyrendszer-szerepkörök hozzáadásához](../deploy/configure/add-site-system-roles.md).  

##  <a name="BKMK_RoleBaseAdministration"></a> Szerepköralapú adminisztráció tervezése a jelentéskészítéshez  
 A jelentési biztonsági más objektumokat a Configuration Manager ahol biztonsági szerepköröket és engedélyeket rendelhet a rendszergazda felhasználók hasonlítanak. A rendszergazda felhasználók csak azokat a jelentéseket futtathatják és módosíthatják, amelyekre megfelelő biztonsági jogosultsággal rendelkeznek. Jelentések futtatása a Configuration Manager konzolon, rendelkeznie kell a **olvasási** jogosultság a **hely** engedélyeire és az egyes objektumokhoz konfigurált engedélyekre.  

 Azonban más objektumokat a Configuration Manager ellentétben azon rendszergazda felhasználók esetén a Configuration Manager konzolján beállított biztonsági jogosultságot kell is konfigurálható a Reporting Services szolgáltatásokban. Amikor biztonsági engedélyeket konfigurál a Configuration Manager konzolon, a jelentéskészítési szolgáltatási pont csatlakozik a Reporting Serviceshez, és beállítja a jelentésekhez a megfelelő engedélyeket. Például a **Szoftverfrissítés-kezelő** biztonsági szerepkörhöz a **Jelentés futtatása** és a **Jelentés módosítása** engedély van társítva. Azok a rendszergazda felhasználók akikhez csak a **Software Update Manager** szerepkör lett társítva, csak a szoftverfrissítések jelentéseit futtathatják és módosíthatják. Más objektumokra vonatkozó jelentések nem jelennek meg a Configuration Manager konzolon. A kivételt a rendszer, hogy egyes jelentések nem kapcsolódnak az adott Configuration Manager biztonságos objektumokra. Ezeknél a jelentéseknél a rendszergazda felhasználónak **Olvasás** joggal kell rendelkeznie a **Hely** engedélyére, hogy jelentéseket futtasson, és **Módosítás** joggal kell rendelkeznie a **Hely** engedélyére, hogy jelentéseket módosítson.  

 A jelentések teljes mértékben támogatják a szerepköralapú adminisztrációt. A Configuration Manager elérhető valamennyi jelentés adatai a jelentést futtató rendszergazda engedélyei alapján szűrt. Adott szerepkörrel rendelkező rendszergazdák csak a szerepkörükhöz definiált információkat tekinthetik meg.  

 További információ a jelentéskészítés biztonsági engedélyeiről: [konfigurálása reporting](configuring-reporting.md).  

 További információ a szerepköralapú felügyelet a Configuration Manager: [szerepköralapú Adminisztráció konfigurálása](../deploy/configure/configure-role-based-administration.md).  

## <a name="next-steps"></a>További lépések  
 A következő kiegészítő témakörök segítségével a Configuration Manager jelentéskészítésének tervezéséhez nyújtanak segítséget:  

-   [A System Center Configuration Managerben a jelentéskészítés előfeltételei](../../../core/servers/manage/prerequisites-for-reporting.md)  
-   [Ajánlott eljárások jelentéskészítéshez a System Center Configuration Managerben](../../../core/servers/manage/best-practices-for-reporting.md)  

