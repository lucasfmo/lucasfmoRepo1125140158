---

title: "Szoftverfrissítések figyelése |} Microsoft Docs"
description: "A System Center Configuration Manager konzolt biztosít a riasztások és a figyelheti a frissítések és a megfelelőségi állapotok."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 956ef263a1c178b5ab5926705859f4b2d0ae5bc7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="monitor-software-updates-in-system-center-configuration-manager"></a>Szoftverfrissítések figyelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager használatával figyelheti a szoftverfrissítési objektumok, folyamatok és megfelelőségi információk számos lehetőséget biztosít. Szoftverfrissítések figyelése a következő szakaszok egyikét használhatja.

## <a name="software-updates-dashboard"></a>Szoftver frissítések irányítópult
-Től kezdődően a Configuration Manager verziója 1610 használhatja a szoftver frissítések irányítópult megtekintéséhez az eszközök aktuális megfelelőségi állapotát a szervezetben, és gyors adatelemzés mely eszközök vannak kitéve. Az irányítópult megtekintéséhez lépjen **figyelés** > **áttekintése** > **biztonsági** > **szoftver frissítések irányítópult**.   

##  <a name="BKMK_SUAlerts"></a> Riasztások szoftverfrissítésekhez  
 A szoftverfrissítésekhez riasztásokat lehet beállítani, amelyek értesítik a rendszergazda felhasználókat, ha a szoftverfrissítések központi telepítésére vonatkozó megfelelőségi szintek a beállított százalékos arány alatt vannak. A szoftverfrissítések központi telepítésére vonatkozó riasztásokat a következő helyeken lehet konfigurálni:  

-   Automatikus központi telepítési szabály beállításai: Beállíthatja a riasztások beállításai az automatikus központi telepítési szabály létrehozása varázslóban és a tulajdonságok az automatikus központi telepítési szabály.  

-   Központi telepítés beállításai: A riasztások beállításai a szoftverfrissítések központi telepítése varázslóban és a központi telepítés tulajdonságaiban konfigurálható.  

Miután konfigurálta a riasztási beállításokat, ha a megadott feltételek teljesülnek, a Configuration Manager riasztást küld. A szoftverfrissítésekre vonatkozó riasztások a következő helyeken tekinthetők át:  

1.  A legújabb riasztások a **Szoftverkönyvtár** munkaterület **Szoftverfrissítések** csomópontján tekinthetők meg.  

2.  A beállított riasztásokat a **Figyelés** munkaterület **Riasztások** csomópontján kezelheti.  

##  <a name="BKMK_SUSyncStatus"></a> Szoftverfrissítések szinkronizálási állapota  
 Miután elindította a szinkronizálást, a szinkronizálási folyamatot a Configuration Manager konzol összes szoftverfrissítési pontján figyelheti a hierarchiában. Kövesse az alábbi eljárást a szoftverfrissítések szinkronizálásának figyeléséhez.  

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>A szoftverfrissítések szinkronizálási folyamatának figyelése  

- A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **szoftverfrissítési pont szinkronizálási állapota**.  

    A Configuration Manager-hierarchia szoftverfrissítési pontjai az eredmények ablaktábláján jelennek meg. Ebben a nézetben figyelheti az összes szoftverfrissítési pont szinkronizálási állapotát. A szinkronizálási folyamat kapcsolatos részletesebb információkért megtekintéséhez tekintse át a wsyncmgr.log fájlt, amely <*Configmgrtelepítésiútvonal*> \Logs minden egyes helykiszolgálóján.  

##  <a name="BKMK_SUDeployStatus"></a> Szoftverfrissítések központi telepítésének állapota  
 Miután elindította egy szoftverfrissítési csoport frissítéseinek vagy egy önálló szoftverfrissítésnek a központi telepítését, lehetősége van a központi telepítési állapot figyelésére. A szoftverfrissítési csoportok vagy az önálló szoftverfrissítések figyeléséhez használja a következő eljárást.  

#### <a name="to-monitor-deployment-status"></a>Központi telepítési állapot figyelése  

1.  A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **központi telepítések**.  

2.  Kattintson arra a szoftverfrissítési csoportra vagy önálló szoftverfrissítésre, amelynek központi telepítési állapotát figyelni szeretné.  

3.  A **Kezdőlap** lapon lévő **Központi telepítés** csoportban kattintson az **Állapot megtekintése**elemre.  

##  <a name="BKMK_SUReports"></a> Szoftverfrissítési jelentések  
 A szoftverfrissítések állapotüzenetei információkkal szolgálnak a szoftverfrissítések megfelelőségéről, valamint a szoftverfrissítések központi telepítéseinek értékelési és kényszerítési állapotáról. Az állapotüzeneteket a szoftverfrissítési jelentések futtatásával jelenítheti meg. Több mint 30 előre definiált szoftverfrissítési jelentés áll rendelkezésre. A jelentések számos kategóriába vannak rendezve, és a szoftverfrissítésekkel, valamint a központi telepítésekkel kapcsolatos különféle információk jelentéséhez használhatók. Az előre konfigurált jelentések használata mellett egyéni szoftverfrissítési jelentések is létrehozhatók a vállalat igényeinek megfelelően. További információkért lásd: [reporting kapcsolatos tevékenységek és karbantartás](../../core/servers/manage/operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_MonitorContent"></a> Tartalom figyelése  
 Az összes csomagtípus található a társított terjesztési pontokhoz képest állapotának ellenőrzését, a Configuration Manager konzol tartalmak figyelését is. Idetartozik például a csomag tartalomérvényesítési állapota, az adott terjesztésipont-csoporthoz rendelt tartalom állapota, az adott terjesztési ponthoz rendelt tartalom állapota, valamint az egyes terjesztési pontok opcionális szolgáltatásainak állapota (tartalomérvényesítés, PXE és csoportos küldés).  

###  <a name="BKMK_ContentStatus"></a> Tartalomállapot figyelése  
 A tartalomcsomagokkal kapcsolatos tudnivalók a **Figyelés** munkaterület **Tartalomállapot** csomópontján találhatók. Áttekintheti a csomaggal és a csomag terjesztési állapotával kapcsolatos általános információkat, továbbá megjelenítheti a csomag részletes állapotadatait is. A tartalomállapot megtekintéséhez a következő eljárást használhatja.  

#### <a name="to-monitor-content-status"></a>Tartalomállapot figyelése  

1.  A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **terjesztés állapota** > **Tartalomállapot**. A program megjeleníti a csomagokat.  

2.  Válassza ki azt a csomagot, amelynek részletes állapotadatait meg szeretné jeleníteni.  

3.  A **Kezdőlapon** kattintson az **Állapot megtekintése elemre**. Ekkor megjelennek a csomag részletes állapotadatai.  

###  <a name="BKMK_DPGroupStatus"></a> Terjesztésipont-csoport állapota  
 A **Figyelés** munkaterületen a **Terjesztésipont-csoport állapota** csomópont a terjesztésipont-csoportokról szolgáltat adatokat. Megtekintheti a terjesztésipont-csoporttal kapcsolatos általános információkat, például a terjesztésipont-csoport állapotát és megfelelőségi arányát, továbbá a terjesztésipont-csoport részletes állapotadatait is. Terjesztésipont-csoport állapotának megtekintéséhez a következő eljárást használhatja.  

#### <a name="to-monitor-distribution-point-group-status"></a>Terjesztésipont-csoport állapotának figyelése  

1.  A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **terjesztés állapota** > **terjesztésipont-csoport állapota**. Megjelennek a terjesztésipont-csoportok.  

2.  Jelölje ki azt a terjesztésipont-csoportot, amelyről részletes állapotadatokat szeretne megtekinteni.  

3.  A **Kezdőlapon** kattintson az **Állapot megtekintése elemre**. Ekkor megjelennek a terjesztésipont-csoport részletes állapotadatai.  

###  <a name="BKMK_DPConfigStatus"></a> Terjesztési pont konfigurációs állapota  
 A **Figyelés** munkaterületen a **Terjesztési pont konfigurációs állapota** csomópont a terjesztési pontról szolgáltat adatokat. Megtekintheti, hogy mely attribútumok (például PXE, csoportos küldés és tartalomérvényesítés) vannak engedélyezve a terjesztési ponthoz. Megtekintheti továbbá a terjesztési pont részletes állapotadatait. Terjesztési pont konfigurációs állapotának megtekintéséhez a következő eljárást használhatja.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>Terjesztési pont konfigurációs állapotának figyelése  

1.  A Configuration Manager-konzolon lépjen a **figyelés** > **áttekintése** > **terjesztés állapota** > **terjesztési pont konfigurációs állapota**. Megjelennek a terjesztési pontok.  

2.  Jelölje ki azt a terjesztési pontot, amelynek az állapotinformációit szeretné megtekinteni.  

3.  Az eredmények ablaktáblájában jelenítse meg a **Részletek** lapot. Ekkor megjelennek a terjesztési pont állapotadatai.  

