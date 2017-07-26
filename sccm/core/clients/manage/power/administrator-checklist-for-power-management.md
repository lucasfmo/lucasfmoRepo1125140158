---
title: "Rendszergazdai ellenőrzőlista az energiagazdálkodáshoz |} Microsoft Docs"
description: "A rendszergazdai ellenőrző lista használatával alakítsa ki tervezése és implementálása az energiagazdálkodás a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94e42cbe-9df8-4228-a04e-0ad7626180ca
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: e6a7a0b853be930b558cdd739b90285ebb8538e7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="administrator-checklist-for-power-management-in-system-center-configuration-manager"></a>Rendszergazdai ellenőrzőlista az energiagazdálkodáshoz a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a rendszergazdai ellenőrzőlista tartalmazza a javasolt lépéseket a System Center Configuration Manager energiagazdálkodási használatát mutatja be a szervezet.  

## <a name="configuring-power-management"></a>Energiagazdálkodás konfigurálása  
 A következő lépések ahhoz nyújtanak segítséget, hogy konfigurálja a hierarchiát az energiagazdálkodási adatok az ügyfélszámítógépekről való gyűjtésére.  

> [!IMPORTANT]  
>  Ne alkalmazzon energiasémákat a hierarchiában lévő számítógépeken, amíg meg nem történt az ügyfélszámítógépek energiagazdálkodási adatainak begyűjtése és elemzése. Ha a meglévő beállítások vizsgálata nélkül alkalmaz új energiagazdálkodási beállításokat a számítógépekre, az az energiafogyasztás növekedéséhez vezethet.  

|Feladat|Részletek|  
|----------|-------------|  
|Tekintse át az energiagazdálkodás fogalmait a Configuration Manager dokumentációs könyvtárában.|Lásd: [energiagazdálkodás bemutatása](introduction-to-power-management.md).|  
|Tekintse át az energiagazdálkodás előfeltételeit a Configuration Manager dokumentációs könyvtárában.|Lásd: [energiagazdálkodás előfeltételei](prerequisites-for-power-management.md).|  
|Tekintse át az energiagazdálkodásra vonatkozó gyakorlati tanácsokat.|Lásd: [ajánlott eljárások az energiagazdálkodáshoz](best-practices-for-power-management.md).|  
|A gyűjtemények konfigurálása kezeléséhez energiafogyasztását a környezetben lévő számítógépekről.|Használja a **gyűjtemény az alapadatokról jelentéskészítéshez**, **gyűjtemény az alapadatokról jelentéskészítéshez**, **energiagazdálkodás nem alkalmas számítógépek gyűjteménye**, **gyűjtemény számítógépeire, melyeken energiasémákat kíván alkalmazni**, **gyűjtemény számítógépeire, melyeken energiasémákat kíván alkalmazni**, és **Windows Server rendszerű számítógépek gyűjteményei** segítséget nyújtanak a hierarchiában lévő számítógépek energiaellátási beállításainak kezelését. Több gyűjteményt is létrehozhat, és minden gyűjteményben más energiasémát alkalmazhat.|  
|Engedélyezze az energiagazdálkodást.|Az energiagazdálkodás használatához engedélyeznie kell azt és konfigurálnia kell a szükséges ügyfélbeállításokat. További információkért lásd: [az energiagazdálkodás konfigurálása](configuring-power-management.md).|  
|Gyűjtse be az energiagazdálkodási adatokat az ügyfélszámítógépekről.|A hardverleltárral a Configuration Manager ügyfelek által jelentett energiagazdálkodási adatokat. A hardverleltár beállított ütemezésétől függően a leltáradatok az összes ügyfélszámítógépről való lekérése eltarthat egy ideig.|  

## <a name="monitoring-and-planning-phase"></a>Figyelési és tervezési fázis  

|Feladat|Részletek|  
|----------|-------------|  
|Futtassa a **Számítógépes tevékenység**jelentést.|A **Számítógépes tevékenység** jelentés egy adott gyűjtemény megfigyelési, számítógépes és felhasználói tevékenységeit mutató grafikont jelenít meg az adott időszakra vonatkozóan. Ez a jelentés a **Számítógépes tevékenység részletei** jelentésre hivatkozik, mely megjeleníti a megadott gyűjteményben lévő számítógépek alvási és ébresztési képességeit. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Energiafogyasztás** vagy a **Napi energiafogyasztás**jelentést.|Az **Energiafogyasztás** és a **Napi energiafogyasztás** jelentés a megadott gyűjtemény a megadott időszakra vonatkozó teljes havi energiafogyasztását jeleníti meg kilowattórában (kWh). További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Környezeti hatás** vagy a  **Napi környezeti hatás**jelentést.|A **Környezeti hatás** és a **Napi környezeti hatás** jelentés a megadott gyűjtemény által kibocsátott széndioxidot (CO2-t) mutató grafikont jelenít meg a megadott időszakra vonatkozóan. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Energiaköltség** vagy a **Napi energiaköltség**jelentést.|Az **Energiaköltség** és a **Napi energiaköltség** jelentés a teljes energiafogyasztási költséget jeleníti meg a megadott időszakra vonatkozóan. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Energiaellátási lehetőségek**jelentést.|Az **Energiaellátási lehetőségek** jelentés a megadott gyűjtemény számítógépeinek energiagazdálkodási képességeit jeleníti meg. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Energiaellátási beállítások**jelentést.|Az **Energiaellátási beállítások** jelentés a megadott gyűjteményben a számítógépek által aktuálisan használt energiaellátási beállítások összesített listáját jeleníti meg. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Zárja ki a szükséges számítógép-gyűjteményeket az energiagazdálkodásból.|Lásd: [az energiagazdálkodás konfigurálása](configuring-power-management.md).|  

> [!IMPORTANT]  
>  Mindenképpen mentse el a figyelési és tervezési fázisban létrehozott energiagazdálkodási jelentésekből származó adatokat. Ezen adatok az alkalmazási és a megfelelőségi fázisban létrejövő energiagazdálkodási adatokkal való összevetése elősegítheti a hierarchiában lévő számítógépekre energiaséma alkalmazásával az energiafogyasztás, az energiaköltség és a környezeti hatás terén elért megtakarítások értékelését.  

## <a name="enforcement-phase"></a>Alkalmazási fázis  

|Feladat|Részletek|  
|----------|-------------|  
|Válasszon ki meglévő energiasémákat, vagy hozzon létre új energiasémákat a szervezet számítógép-gyűjteményeihez.|Lásd: [hogyan hozhat létre és alkalmazhat energiasémákat](create-and-apply-power-plans.md).|  
|Alkalmazza ezeket az energiasémákat a számítógépeken.|Lásd: [hogyan hozhat létre és alkalmazhat energiasémákat](create-and-apply-power-plans.md).|  

## <a name="compliance-phase"></a>Megfelelőségi fázis  

|Feladat|Részletek|  
|----------|-------------|  
|Futtassa a **Számítógépes tevékenység**jelentést.|A **Számítógépes tevékenység** jelentés egy adott gyűjtemény megfigyelési, számítógépes és felhasználói tevékenységeit mutató grafikont jelenít meg az adott időszakra vonatkozóan. Ez a jelentés az **Energiagazdálkodás - számítógépes tevékenység részletei** jelentésre hivatkozik, mely megjeleníti a megadott gyűjteményben lévő számítógépek alvási és ébresztési képességeit. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Energiafogyasztás** vagy a **Napi energiafogyasztás**jelentést.|Az **Energiafogyasztás** és a **Napi energiafogyasztás** jelentés a megadott gyűjtemény a megadott időszakra vonatkozó teljes havi energiafogyasztását jeleníti meg kilowattórában (kWh). További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Környezeti hatás** vagy a **Napi környezeti hatás**jelentést.|A **Környezeti hatás** és a **Napi környezeti hatás** jelentés a megadott gyűjtemény által kibocsátott széndioxidot (CO2-t) mutató grafikont jelenít meg a megadott időszakra vonatkozóan. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Futtassa az **Energiaköltség** vagy a **Napi energiaköltség**jelentést.|Az **Energiaköltség** és a **Napi energiaköltség** jelentés a teljes energiafogyasztási költséget jeleníti meg a megadott időszakra vonatkozóan. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  

## <a name="troubleshooting"></a>Hibaelhárítás  

|Feladat|Részletek|  
|----------|-------------|  
|Ha a hierarchiában lévő számítógépek nem léptek alvó vagy hibernált állapotba, a lehetséges okok megjelenítéséhez futtassa **Az alvó üzemmódra képtelen számítógépek jelentését** .|**Az alvó üzemmódra képtelen számítógépek jelentése** azon általános okok listáját jeleníti meg, amelyek meggátolták a számítógépek alvó vagy hibernált állapotba lépését, valamint az adott időszakban az egyes okok által befolyásolt számítógépek számát. További információkért lásd: [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  
|Ha egy adott számítógépre több energiaséma is vonatkozik, a rendszer a legkevésbé korlátozó energiasémát alkalmazza. Futtassa a **Több energiasémával rendelkező számítógépek** jelentést azon számítógépek megtekintéséhez, melyekre több energiaséma vonatkozik.|Lásd: **több energiasémával rendelkező számítógépek** a [figyelés és tervezés az energiagazdálkodás hogyan](monitor-and-plan-for-power-management.md).|  

