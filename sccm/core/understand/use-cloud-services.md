---
title: "Felhőszolgáltatások használata a Configuration Manager |} Microsoft Docs"
description: "Felhőalapú erőforrások kiépítése a System Center Configuration Manager a helyszíni infrastruktúra kiegészítésére."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d7ddd48cc4e75b12f893e686b847d66058441e1
ms.openlocfilehash: 52f7c63d155d5c34f0f12e13020767dec1867dab
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-cloud-services-with-system-center-configuration-manager"></a>Felhőszolgáltatások használata a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager felhő alapú beállításokat támogatja. Ezek a helyszíni infrastruktúra is használható, és például üzleti problémák megoldásához nyújtson segítséget:  

-   Hogyan kezelheti a BYOD (mobileszköz-kezelés az Intune használatával).  

-   Tartalom-erőforrások biztosítása elkülönített ügyfeleknek, illetve (a felhő alapú terjesztési pontok használatával) a vállalati tűzfalon kívüli intranetes erőforrások módjáról.  

-   Hogyan infrastruktúra kiterjesztése olyan esetekben fizikai hardver nem áll rendelkezésre, vagy nem logikailag elhelyezett támogatásához az igényeknek (Microsoft Azure virtuális gépek használatával).  

Felhőalapú erőforrások kiépítése, de nem a Configuration Manager telepítése előtt kell megtenni, érdemes lehet megismerheti ezeket a beállításokat, mielőtt elmélyedne a hierarchiatervezésben. A felhőalapú erőforrások előfordulhat, hogy menteni, pénzt és időt, üzleti problémák megoldása során, hogy a helyszíni infrastruktúrára nem.  

## <a name="cloud-based-resources-you-can-use-with-configuration-manager"></a>A Configuration Managerrel használható felhőalapú erőforrások  
 Mivel az egyes lehetőségekre különböző követelmények vonatkoznak, tanulmányozza részletesen mindegyiket, különösen azok egyedi előfeltételeit, korlátait, valamint a használatukkal járó esetleges többletköltségeket.  

-   Felhőalapú terjesztési pontokkal kapcsolatos információért lásd: [felhő alapú terjesztési pontok telepítése](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure).

-   Azure kapcsolatos további információkért lásd: [Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) az MSDN könyvtárában.  

### <a name="azure-virtual-machines-for-cloud-based-infrastructure"></a>Az Azure virtuális gépek (felhőalapú infrastruktúrához)  
 A Configuration Manager támogatja az Azure virtuális gépeken futó számítógépek ugyanúgy, mint amikor futtatja a helyi fizikai vállalati hálózaton belül. Azure-alapú virtuális gépek a következő esetekben használhatók:  

-   **1. forgatókönyv:** Futtassa a Configuration Manager-beli virtuális gépeken, és más virtuális gépeken telepített ügyfelek kezelésére használhatja.  

-   **2. forgatókönyv:** Futtassa a Configuration Manager-beli virtuális gépeken, és nem az Azure-ban futó ügyfelek kezelésére használhatja.  

-   **3. forgatókönyv:** Futtatása másik Configuration Manager helyrendszer-szerepkörök virtuális gépeken, miközben fizikai vállalati hálózatban más szerepköröket futtat (a kommunikációhoz megfelelő hálózati kapcsolattal).  

Ugyanazok a követelmények vonatkoznak, a hálózatok, operációs rendszerek és hardverekre vonatkozó követelmények a Configuration Manager telepítése a fizikai vállalati hálózatban történő a Configuration Manager telepítését az Azure-ban is vonatkozik.  

Az Azure virtuális gépek használatához Azure-előfizetés szükséges. Függő díj terheli a virtuális gépek, a konfiguráció és a felhőalapú erőforrások száma alapján.  

Emellett a Configuration Manager-helyek és az Azure virtuális gépeken futó ügyfelek lépnek ugyanazok a licenckövetelmények vonatkoznak, mint a helyszíni telepítésekre.  

### <a name="azure-services-for-cloud-based-distribution-points"></a>Az Azure-szolgáltatások (felhőalapú terjesztési pont)  
 Az Azure-szolgáltatások segítségével a Configuration Manager terjesztési pontok, nevezzük hívott felhőalapú terjesztési pont. Is [felhőalapú terjesztési pontot használ a System Center Configuration Managerrel](../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) mellett a helyszíni terjesztési pontok, és az Azure virtuális gépeken telepített terjesztési pontokkal.  

 Ez eltér attól az esettől, amikor Azure-alapú virtuális gépen telepít helyrendszerszerepkört. Felhőalapú terjesztési pontok:  

-   Szolgáltatásként az Azure virtuális gépen nem.  

-   Automatikus méretezése ügyfelek megnövekedett tartalom kérelmeinek teljesítéséhez.  

-   Az interneten és az intranetes ügyfelek támogatása.  

Azure-előfizetéssel kell használnia az Azure terjesztési pontok futtatásához. Függő díj terheli adatot kell továbbítani a szolgáltatás érkező vagy oda irányuló mennyisége alapján.  

### <a name="microsoft-intune-for-mobile-device-management"></a>A Microsoft Intune (a mobileszköz-kezelés)  
 A Microsoft Intune-előfizetését integrálhatja a Configuration Manager eszközök felügyeletének engedélyezése az Intune szolgáltatás segítségével. Tudnivalók az integrációról:  

-   A hibrid konfigurációnak nevezik, és az általa bővített Configuration Manager (vagy az Intune-ban, attól függően, hogy az Ön szempontjából) az eszközök széles választékát támogatja.  

-   A Microsoft Intune Connectort helyrendszerszerepkör szükséges.  

-   Szükséges hozzá egy különálló Intune-előfizetést, amely elegendő licencet biztosít az Intune-nal kezelni kívánt eszközöket.  

Bár az Intune-ban Azure használ, kell hozzá külön konfigurálni az Azure, és semmilyen többletköltséggel nem az Intune-előfizetés használata.  

### <a name="additional-configuration-manager-capabilities"></a>A Configuration Manager további képességei  
 Egyes Configuration Manager képességeivel csatlakozhat felhő alapú szolgáltatások, például:  

-   Windows Server Update Services (WSUS).  

-   A Configuration Manager szolgáltatás felhőalapú, a Configuration Manager frissítéseinek letöltéséhez.  

Ezekhez a kiegészítő lehetőségekhez nincs szükség Azure-előfizetésre. Állítsa be a megadott kapcsolatok, tanúsítványok, vagy a felhőben nincs. Ehelyett azok automatikusan kezeli a Configuration Manager által az Ön. Mindössze annyit kell tennie biztosítása érdekében a megfelelő helyrendszerek és eszközök érhessék el az internetes URL-címeket.  

##  <a name="BKMK_CloudSec"></a>Felhő alapú szolgáltatások biztonsága  
 A Configuration Manager-tanúsítványokat használ, tárolásához és hozzáféréséhez a tartalmat az Azure-ban, és a szolgáltatások kezeléséhez. A Configuration Manager titkosítja az Azure-ban tárolt adatokat, de nem használ ruházzák Azure által biztosított további biztonsági vagy adatellenőrzési eljárásokat.  

 További információkért tekintse meg a különböző felhőalapú erőforrás forgatókönyvek a részleteit. Az alábbi témakörök az Azure biztonsági is megtekintheti:  

-   [Azure: Az Azure-fiók biztonsági felügyeletének megértése](http://go.microsoft.com/fwlink/p/?LinkId=262968)  

-   [Azure biztonsági áttekintése](http://go.microsoft.com/fwlink/p/?LinkId=262970)  

-   [A biztonsági útkereszteződésekben a áttelepülés a felhőbe a múltbeli beolvasása](http://go.microsoft.com/fwlink/p/?LinkId=262971)  

-   [2 / 1. az Azure rész az adatok biztonsága](http://go.microsoft.com/fwlink/p/?LinkId=262974)  

