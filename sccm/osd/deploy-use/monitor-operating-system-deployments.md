---
title: "Operációs rendszer központi telepítésének figyelése |} Microsoft Docs"
description: "Segítségével operációs rendszer központi telepítési objektumainak figyelését, a Configuration Manager konzolon a riasztásokat, jelentéseket és különböző Állapotjelzők biztosít."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08085d94-295c-432f-b5e3-9736bce0193b
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 154c0a286e6b9ccedc7545eb010967ac00d35407
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="monitor-operating-system-deployments-in-system-center-configuration-manager"></a>Operációs rendszerek központi telepítése a System Center Configuration Manager figyelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager konzol operációs rendszer központi telepítési objektumainak figyelését segítő a következő módszereket biztosítja.  


##  <a name="BKMK_OSDAlerts"></a> Operációs rendszer központi telepítésére vonatkozó riasztások  
 A feladatütemezés központi telepítési beállításaiban riasztásokat lehet beállítani, amelyek értesítik a rendszergazda felhasználókat, ha a központi telepítésre vonatkozó megfelelőségi szintek a beállított százalékos arány alatt vannak.  

 Miután konfigurálta a riasztási beállításokat, ha a megadott feltételek teljesülnek, a Configuration Manager riasztást küld. A feladatütemezés központi telepítési riasztásai a következő helyeken tekinthetők át:  

1.  A legújabb riasztások az **Operációs rendszerek** csomópontban, a **Szoftverkönyvtár** munkaterületen.  

2.  A beállított riasztásokat a **Figyelés** munkaterület **Riasztások** csomópontján kezelheti.  

##  <a name="BKMK_TSDeployStatus"></a> Feladatütemezés központi telepítési állapota  
 A feladatütemezés üzembe helyezését követően figyelheti a központi telepítés állapotát. A feladatütemezés központi telepítési állapotának figyelésére alkalmazza a következő eljárást.  

#### <a name="to-monitor-deployment-status"></a>Központi telepítési állapot figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A Figyelés munkaterületen kattintson a **Központi telepítések**elemre.  

3.  Kattintson arra a feladatütemezésre, amelynél figyelni szeretné a központi telepítés állapotát.  

4.  A **Kezdőlap** lapon lévő **Központi telepítés** csoportban kattintson az **Állapot megtekintése**elemre.  

##  <a name="BKMK_TSReports"></a> Operációsrendszer-telepítési jelentések  
 Számos előre definiált operációsrendszer-telepítési jelentés áll rendelkezésre. Ezek különböző kategóriákba vannak rendezve, és állapotáttelepítések és feladatütemezések üzembe helyezésével kapcsolatos különféle információkról készíthet velük jelentést. Az előre konfigurált jelentések használata mellett egyéni szoftverfrissítési jelentések is létrehozhatók a vállalat igényeinek megfelelően. További információkért lásd: [reporting kapcsolatos tevékenységek és karbantartás](../../core/servers/manage/operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_MonitorContent"></a> Tartalom figyelése  
 Az összes csomagtípus található a társított terjesztési pontokhoz képest állapotának ellenőrzését, a Configuration Manager konzol tartalmak figyelését is. Idetartozik például a csomag tartalomérvényesítési állapota, az adott terjesztésipont-csoporthoz rendelt tartalom állapota, az adott terjesztési ponthoz rendelt tartalom állapota, valamint az egyes terjesztési pontok opcionális szolgáltatásainak állapota (tartalomérvényesítés, PXE és csoportos küldés).  

###  <a name="BKMK_ContentStatus"></a> Tartalomállapot figyelése  
 A tartalomcsomagokkal kapcsolatos tudnivalók a **Figyelés** munkaterület **Tartalomállapot** csomópontján találhatók. Áttekintheti a csomaggal és a csomag terjesztési állapotával kapcsolatos általános információkat, továbbá megjelenítheti a csomag részletes állapotadatait is. A tartalomállapot megtekintéséhez a következő eljárást használhatja.  

#### <a name="to-monitor-content-status"></a>Tartalomállapot figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A Figyelés munkaterületen bontsa ki a **Terjesztés állapota**csomópontot, majd kattintson a **Tartalom állapota**lehetőségre. A program megjeleníti a csomagokat.  

3.  Válassza ki azt a csomagot, amelynek részletes állapotadatait meg szeretné jeleníteni.  

4.  A **Kezdőlapon** kattintson az **Állapot megtekintése elemre**. Ekkor megjelennek a csomag részletes állapotadatai.  

###  <a name="BKMK_DPGroupStatus"></a> Terjesztésipont-csoport állapota  
 A **Figyelés** munkaterületen a **Terjesztésipont-csoport állapota** csomópont a terjesztésipont-csoportokról szolgáltat adatokat. Megtekintheti a terjesztésipont-csoporttal kapcsolatos általános információkat, például a terjesztésipont-csoport állapotát és megfelelőségi arányát, továbbá a terjesztésipont-csoport részletes állapotadatait is. Terjesztésipont-csoport állapotának megtekintéséhez a következő eljárást használhatja.  

#### <a name="to-monitor-distribution-point-group-status"></a>Terjesztésipont-csoport állapotának figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A Figyelés munkaterületen bontsa ki a **Terjesztés állapota**csomópontot, majd kattintson a **Terjesztésipont-csoport állapota**elemre. Megjelennek a terjesztésipont-csoportok.  

3.  Jelölje ki azt a terjesztésipont-csoportot, amelyről részletes állapotadatokat szeretne megtekinteni.  

4.  A **Kezdőlapon** kattintson az **Állapot megtekintése elemre**. Ekkor megjelennek a terjesztésipont-csoport részletes állapotadatai.  

###  <a name="BKMK_DPConfigStatus"></a> Terjesztési pont konfigurációs állapota  
 A **Figyelés** munkaterületen a **Terjesztési pont konfigurációs állapota** csomópont a terjesztési pontról szolgáltat adatokat. Megtekintheti, hogy mely attribútumok (például PXE, csoportos küldés és tartalomérvényesítés) vannak engedélyezve a terjesztési ponthoz. Megtekintheti továbbá a terjesztési pont részletes állapotadatait. Terjesztési pont konfigurációs állapotának megtekintéséhez a következő eljárást használhatja.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>Terjesztési pont konfigurációs állapotának figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A Figyelés munkaterületen bontsa ki a **Terjesztés állapota**csomópontot, majd kattintson a **Terjesztési pont konfigurációs állapota**elemre. Megjelennek a terjesztési pontok.  

3.  Jelölje ki azt a terjesztési pontot, amelynek az állapotinformációit szeretné megtekinteni.  

4.  Az eredmények ablaktáblájában jelenítse meg a **Részletek** lapot. Ekkor megjelennek a terjesztési pont állapotadatai.  

