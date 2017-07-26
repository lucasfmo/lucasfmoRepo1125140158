---
title: "Gyűjtemények kezelése |} Microsoft Docs"
description: "A System Center Configuration Manager felügyeleti feladatokat hajthatnak végre, közös gyűjtemények."
ms.custom: na
ms.date: 4/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e102fd1a-76df-4d8e-b1b0-10ee18318f67
caps.latest.revision: 8
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 4d44f98eb0755619cdd2101203a13725186b835b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-manage-collections-in-system-center-configuration-manager"></a>A System Center Configuration Manager gyűjtemények kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a témakörben az áttekintő információkat használatával alakítsa ki a System Center Configuration Manager gyűjtemények felügyeleti feladatokat hajthat végre.  

> [!NOTE]  
>  A Configuration Manager gyűjteményeinek létrehozásával kapcsolatos további információkért lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md).  

## <a name="how-to-manage-device-collections"></a>Eszközgyűjtemények kezelése  
 Az **Eszközök és megfelelőség** munkaterületen válassza az **Eszközgyűjtemények**lehetőséget, majd válassza ki a kezelni kívánt gyűjteményt és a kezelési feladatot.  

 A következő táblázat használatával további információt kaphat azokról a kezelési feladatokról, amelyek kiválasztása előtt még tájékozódni szeretne.  

|Kezelési feladat|Részletek|További információ|  
|---------------------|-------------|----------------------|  
|**Tagok megjelenítése**|Megjeleníti az összes olyan erőforrást, amely tagja a kijelölt gyűjteménynek egy, az **Eszközök** csomópont alatti, ideiglenes csomópontban.|Nem áll rendelkezésre további információ.|  
|**Kiválasztott elemek hozzáadása**|A következő műveletek végrehajtását teszi lehetővé:<br /><br /> - <br />                    **Kijelölt elemek hozzáadása létező Eszközgyűjteményhez** – megnyitja a **gyűjtemény választása** párbeszédpanelt, ahol kiválaszthatja a gyűjteményt, amelyhez a kijelölt gyűjtemény tagjainak hozzáadása kívánja. A kijelölt gyűjteményt a rendszer a **Gyűjtemények belefoglalása** tagsági szabály használatával ebbe gyűjteménybe foglalja bele.<br /><br /> - **Kijelölt elemek hozzáadása új Eszközgyűjteményhez** – megnyitja a **eszközgyűjtemény létrehozása varázsló** amellyel új gyűjtemény hozható létre. A kijelölt gyűjteményt a rendszer a **Gyűjtemények belefoglalása** tagsági szabály használatával ebbe gyűjteménybe foglalja bele.|[Gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md)|  
|**Ügyfél telepítése**|Megnyitja a **ügyfél telepítése varázsló** használó ügyfélleküldéses telepítés Configuration Manager-ügyfél telepítéséhez a kiválasztott gyűjteményben lévő összes számítógépen.|[Ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md)|  
|**Affinitási kérések kezelése**|Megnyitja a **Felhasználó-eszköz kapcsolatokra vonatkozó kérések kezelése** párbeszédpanelt, amely lehetővé teszi az eszközök függőben lévő, felhasználó-eszköz kapcsolatainak létrehozására vonatkozó kérések jóváhagyását és elutasítását a kiválasztott gyűjteményben.|[Felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat a System Center Configuration Managerben](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**Szükséges PXE-központitelepítések törlése**|Töröl minden szükséges, PXE-rendszerindítással végzett központi telepítést a kijelölt gyűjteményt összes tagjáról.|[Operációs rendszer központi telepítése – bevezetés](../../../../osd/understand/introduction-to-operating-system-deployment.md)|  
|**Tagság frissítése**|Kiértékeli a kiválasztott gyűjtemény tagságát. A sok tagot tartalmazó gyűjtemények esetében a frissítés hosszabb időt is igénybe vehet. Miután a frissítés befejeződött, a **Frissítés** művelettel megjelenítheti a képernyőn az új gyűjtemények tagjait.|Nem áll rendelkezésre további információ.|  
|**Erőforrások hozzáadása**|Megnyitja az **Erőforrások hozzáadása a gyűjteményhez** párbeszédpanelt, amelyen a kijelölt gyűjteményhez hozzáadható új erőforrások kereshetők.<br /><br /> A kijelölt gyűjtemény ikonja homokóra szimbólumra jelenik meg, amíg a frissítés van folyamatban.|Nem áll rendelkezésre további információ.|  
|**Ügyfélértesítés**|A kijelölt eszközgyűjteményhez tartozó összes ügyfelet számítógép-szabályzat vagy felhasználói szabályzat letöltésére utasítja.|Nem áll rendelkezésre további információ.|  
|**Endpoint Protection**|A kijelölt gyűjteményhez tartozó összes számítógépen teljes vagy gyors kártevőkeresést végez, vagy letölti a legújabb kártevőirtó-definíciókat a számítógépekre.|[Az Endpoint Protection a System Center Configuration Managerben](../../../../protect/deploy-use/endpoint-protection.md)|  
|**Exportálásálás**|Megnyitja a **gyűjtemény exportálása varázslót** exportálja a gyűjteményhez való egy Managed Object Format (MOF) fájlt, majd archiválható vagy egy másik Configuration Manager-helyen használt.<br /><br /> Gyűjtemény exportálásakor a rendszer nem exportál olyan gyűjteményeket, amelyekre a kijelölt gyűjtemény **Belefoglalás** vagy **Kizárás** szabállyal hivatkozik.|Nem áll rendelkezésre további információ.|  
|**Másolás**|Másolatot készít a kijelölt gyűjteményről. Az új gyűjtemény a kijelölt gyűjteményt korlátozó gyűjteményként használja.|Nem áll rendelkezésre további információ.|  
|**Törlés**|Törli a kijelölt gyűjteményt. Lehetőség van továbbá a gyűjteményhez tartozó összes erőforrást is törölni a helyadatbázisból.<br /><br /> A Configuration Manager beépített gyűjteményei nem törölhetők.|A beépített gyűjtemények listáját lásd: [a System Center Configuration Manager gyűjteményeinek bemutatása](../../../../core/clients/manage/collections/introduction-to-collections.md).|  
|**Központi telepítés szimulálása**|Megjeleníti az **Alkalmazás-központitelepítés szimulálása varázslót** , amellyel az alkalmazások telepítése és eltávolítása nélkül tesztelhető az alkalmazások központi telepítése.|[Alkalmazás központi telepítésének a System Center Configuration Managerrel szimulálása](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**Telepítés**|A következő lehetőségeket jeleníti meg:<br /><br /> - <br />                    **Alkalmazás** – megnyitja a **szoftver központi telepítése varázsló** ahol kiválasztása és konfigurálása az alkalmazás központi telepítése a kijelölt gyűjteményhez.<br /><br /> - <br />                    **Program** – Megnyitja a **Szoftver központi telepítése varázslót** , amellyel a kijelölt gyűjteményhez csomagot vagy programot telepíthet, illetve konfigurálhatja a telepítést.<br /><br /> - **Alapkonfiguráció** – megnyitja a **Alapkonfigurációk központi telepítése** párbeszédpanelt, ahol konfigurálhatja a kijelölt gyűjteményhez referenciakonfigurációk központi telepítése.<br /><br /> - <br />                    **Feladatütemezés** – Megnyitja a **Szoftver központi telepítése varázslót** , amellyel a kijelölt gyűjteményhez feladatütemezést adhat meg és konfigurálhat.<br /><br /> - <br />                    **Szoftverfrissítések** – megnyitja a **szoftverfrissítések központi telepítése varázsló** ahol konfigurálhatja a kijelölt gyűjtemény erőforrásaihoz a szoftverfrissítések központi telepítését.|[A System Center Configuration Managerrel alkalmazások központi telepítése](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [Csomagok és programok a System Center Configuration Managerben](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [A System Center Configuration Managerben referenciakonfigurációk központi telepítése](../../../../compliance/deploy-use/deploy-configuration-baselines.md)<br /><br /> [A System Center Configuration Managerben feladatok automatizálásához feladatütemezések kezelése](../../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md)<br /><br /> [A System Center Configuration Manager-szoftverfrissítések kezelése](/sccm/sum/understand/software-updates-introduction)|  

## <a name="how-to-manage-user-collections"></a>Felhasználógyűjtemények kezelése  
 Az **Eszközök és megfelelőség** munkaterületen válassza a **Felhasználógyűjtemények**lehetőséget, majd válassza ki a kezelni kívánt gyűjteményt és a kezelési feladatot.  

 A következő táblázat használatával további információt kaphat azokról a kezelési feladatokról, amelyek kiválasztása előtt még tájékozódni szeretne.  

|Kezelési feladat|Részletek|További információ|  
|---------------------|-------------|----------------------|  
|**Tagok megjelenítése**|Megjeleníti az összes olyan erőforrást, amely tagja a kijelölt gyűjteménynek egy, a **Felhasználók** csomópont alatti, ideiglenes csomópontban.|Nem áll rendelkezésre további információ.|  
|**Kiválasztott elemek hozzáadása**|Ezzel a paranccsal az alábbi műveletek hajthatók végre:<br /><br /> - <br />                    **Kijelölt elemek hozzáadása létező Felhasználógyűjteményhez** – megnyitja a **gyűjtemény választása** párbeszédpanelt, ahol kiválaszthatja a gyűjteményt, amelyhez a kijelölt gyűjtemény tagjainak hozzáadása kívánja. A kijelölt gyűjteményt a rendszer a **Gyűjtemények belefoglalása** tagsági szabály használatával ebbe gyűjteménybe foglalja bele.<br /><br /> - **Kijelölt elemek hozzáadása új Felhasználógyűjteményhez** – megnyitja a **Felhasználógyűjtemény létrehozása varázsló** amellyel új gyűjtemény hozható létre. A kijelölt gyűjteményt a rendszer a **Gyűjtemények belefoglalása** tagsági szabály használatával ebbe gyűjteménybe foglalja bele.|[Gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md)|  
|**Affinitási kérések kezelése**|Megnyitja a **Felhasználó-eszköz kapcsolatokra vonatkozó kérések kezelése** párbeszédpanelt, amely lehetővé teszi a felhasználók függőben lévő, felhasználó-eszköz kapcsolatainak létrehozására vonatkozó kérések jóváhagyását és elutasítását a kiválasztott gyűjteményben.|[Felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat a System Center Configuration Managerben](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**Tagság frissítése**|Kiértékeli a kiválasztott gyűjtemény tagságát. A sok tagot tartalmazó gyűjtemények esetében a frissítés hosszabb időt is igénybe vehet. Miután a frissítés befejeződött, a **Frissítés** művelettel megjelenítheti a képernyőn az új gyűjtemények tagjait.<br /><br /> A kijelölt gyűjtemény ikonja homokóra szimbólumra jelenik meg, amíg a frissítés van folyamatban.|Nem áll rendelkezésre további információ.|  
|**Erőforrások hozzáadása**|Megnyitja az **Erőforrások hozzáadása a gyűjteményhez** párbeszédpanelt, amelyen a kijelölt gyűjteményhez hozzáadható új erőforrások kereshetők.|Nem áll rendelkezésre további információ.|  
|**Exportálásálás**|Megnyitja a **gyűjtemény exportálása varázslót** , amely segítséget nyújt a gyűjteményt exportálhat egy Managed Object Format (MOF) fájlt, majd archiválható vagy egy másik Configuration Manager-helyen használt.<br /><br /> Gyűjtemény exportálásakor a rendszer nem exportál olyan gyűjteményeket, amelyekre a kijelölt gyűjtemény **Belefoglalás** vagy **Kizárás** szabállyal hivatkozik.|Nem áll rendelkezésre további információ.|  
|**Másolás**|Másolatot készít a kijelölt gyűjteményről. Az új gyűjtemény a kijelölt gyűjteményt korlátozó gyűjteményként használja.|Nem áll rendelkezésre további információ.|  
|**Törlés**|Törli a kijelölt gyűjteményt. Lehetőség van továbbá a gyűjteményhez tartozó összes erőforrást is törölni a helyadatbázisból.<br /><br /> A Configuration Manager beépített gyűjteményei nem törölhetők.|A beépített gyűjtemények listáját lásd: [a System Center Configuration Manager gyűjteményeinek bemutatása](../../../../core/clients/manage/collections/introduction-to-collections.md).|  
|**Központi telepítés szimulálása**|Megjeleníti az **Alkalmazás-központitelepítés szimulálása varázslót** , amellyel az alkalmazások telepítése és eltávolítása nélkül tesztelhető az alkalmazások központi telepítése.|[Alkalmazás központi telepítésének a System Center Configuration Managerrel szimulálása](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**Telepítés**|A következő lehetőségeket jeleníti meg:<br /><br /> - **Alkalmazás** – megnyitja a **szoftver központi telepítése varázsló** ahol kiválasztása és konfigurálása az alkalmazás központi telepítése a kijelölt gyűjteményhez.<br /><br /> - <br />                    **Program** – Megnyitja a **Szoftver központi telepítése varázslót** , amellyel a kijelölt gyűjteményhez csomagot vagy programot telepíthet, illetve konfigurálhatja a telepítést.<br /><br /> - **Alapkonfiguráció** – megnyitja a **Alapkonfigurációk központi telepítése** párbeszédpanelt, ahol konfigurálhatja a kijelölt gyűjteményhez referenciakonfigurációk központi telepítése.|[A System Center Configuration Managerrel alkalmazások központi telepítése](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [Csomagok és programok a System Center Configuration Managerben](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [A System Center Configuration Managerben referenciakonfigurációk központi telepítése](../../../../compliance/deploy-use/deploy-configuration-baselines.md)|  

##  <a name="BKMK_CollProp"></a> Gyűjtemény tulajdonságai  
 A gyűjtemények **Tulajdonságok** párbeszédpanelének megnyitásakor az alábbi tulajdonságokat tekintheti meg és konfigurálhatja.  

|Lap neve|További információ|  
|--------------|----------------------|  
|**Általános**|Lehetővé teszi a kijelölt gyűjtemény általános adatainak (többek között a gyűjtemény nevének és a korlátozó gyűjteménynek) a megtekintését és konfigurálását.|  
|**Tagsági szabályok**|Lehetővé teszi a gyűjteményben való tagságot meghatározó tagsági szabályok konfigurálását. További információkért lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md).|  
|**Energiagazdálkodás**|Lehetővé teszi a kiválasztott gyűjteményhez tartozó számítógépekhez rendelt energiagazdálkodási sémák konfigurálását. További információkért lásd: [energiagazdálkodás bemutatása](../../../../core/clients/manage/power/introduction-to-power-management.md).|  
|**Központi telepítés**|Megjeleníti a kiválasztott gyűjtemény tagjain központilag telepített szoftvereket.|  
|**Karbantartási időszakok**|Lehetővé teszi a kijelölt gyűjtemény tagjaira vonatkozó karbantartási időszakok megtekintését és konfigurálását. További információkért lásd: [a System Center Configuration Manager karbantartási időszakok használata](../../../../core/clients/manage/collections/use-maintenance-windows.md).|  
|**Gyűjteményváltozók**|Olyan, a feladatütemezések által használható változók konfigurálását teszi lehetővé, amelyek erre a gyűjteményre érvényesek. További információkért lásd: [beépített feladatütemezési változókat](../../../../osd/understand/task-sequence-built-in-variables.md).|  
|**Terjesztésipont-csoportok**|Lehetővé teszi egy vagy több terjesztésipont-csoport hozzárendelését a kiválasztott gyűjtemény tagjaihoz. További információkért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|**Biztonság**|Megjeleníti azokat a rendszergazdákat, akikhez a kiválasztott gyűjteményhez engedélyeket biztosító szerepkörök és biztonsági hatókörök vannak társítva.|  
|**Figyelő**|Lehetővé teszi annak beállítását, hogy mikor jöjjenek létre az ügyfélállapottal és az Endpoint Protection szolgáltatással kapcsolatos riasztások. További információkért lásd: [ügyfélállapot konfigurálása a System Center Configuration Managerben](../../../../core/clients/deploy/configure-client-status.md) és [figyelése a System Center Configuration Managerben az Endpoint Protection](../../../../protect/deploy-use/monitor-endpoint-protection.md).|  

