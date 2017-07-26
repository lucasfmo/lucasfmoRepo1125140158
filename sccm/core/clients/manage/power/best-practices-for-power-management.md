---
title: "Ajánlott eljárások az energiagazdálkodáshoz |} Microsoft Docs"
description: "Első ajánlott eljárások az energiagazdálkodáshoz a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f7142e1-c972-4384-853b-2da1568cb3e3
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: d3cc24c7923141f039dcda26ac27489cb0143e89
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-power-management-in-system-center-configuration-manager"></a>Ajánlott eljárások az energiagazdálkodáshoz a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a következő ajánlott eljárások az energiagazdálkodáshoz a System Center Configuration Managerben.  

## <a name="perform-the-monitoring-phase-at-a-representative-time"></a>A figyelési fázis reprezentatív időszakban való elvégzése  
 Az energiagazdálkodás figyelési fázisa biztosít adatokat a szervezet számítógépeinek energiafogyasztásával, tevékenységével, energiagazdálkodási lehetőségeivel és környezeti hatásával kapcsolatban. Mindenképpen egy reprezentatív időszakot válasszon a megfigyelési fázis végrehajtásához. Ha például egy nemzeti ünnepen hajtja végre a megfigyelési fázist, az nem fog reális jelentést adni a számítógépek energiafogyasztásáról.  

## <a name="create-a-control-collection-of-computers-with-no-power-plans-applied"></a>Számítógépek kontrollgyűjteményének létrehozása olyan számítógépekből, melyeken nincs energiaséma alkalmazva  
 Hozzon létre két számítógép-gyűjteményt annak elősegítésére, hogy figyelhesse az energiasémák a számítógépeken való alkalmazásának hatásait. Az első gyűjtemény tartalmazza azon számítógépek többségét, melyeken energiagazdálkodási beállításokat kíván alkalmazni, a másik gyűjtemény (a kontrollgyűjtemény) pedig tartalmazza a fennmaradó számítógépeket. Alkalmazza a szükséges energiagazdálkodási sémát a számítógépek többségét tartalmazó gyűjteményre. Jelentések futtatásával összevetheti azon számítógépek energiaköltségét, energiafogyasztását és környezeti hatását, melyekre alkalmazott energiagazdálkodási beállításokat, a kontrollgyűjteményével, melyre nem alkalmazott energiagazdálkodási beállításokat.  

## <a name="run-the-power-settings-report-before-you-apply-a-power-management-plan"></a>Az Energiaellátási beállítások jelentés futtatása az energiagazdálkodási beállítások alkalmazása előtt  
 Mielőtt alkalmazna egy energiagazdálkodási sémát egy számítógép-gyűjteményre, a **Energiaellátási beállítások** jelentéssel megismerheti a gyűjteményben lévő számítógépeken már konfigurált energiagazdálkodási beállításokat. Ha a meglévő beállítások vizsgálata nélkül alkalmaz új energiagazdálkodási beállításokat a számítógépekre, az az energiafogyasztás növekedéséhez vezethet.  

## <a name="exclude-servers-from-power-management"></a>Kiszolgálók kizárása az energiagazdálkodásból  
 A Windows Server rendszerű számítógépeken nem támogatott az energiagazdálkodás (bár a rendszer gyűjti azok energiafogyasztási adatait). A kiszolgálókat mindenképpen adja hozzá egy gyűjteményhez, és zárja azt ki az energiagazdálkodásból.  

## <a name="exclude-computers-that-you-do-not-want-to-manage"></a>A kezelni nem kívánt számítógépek kizárása  
 Ha egyes számítógépeken nem kívánja kezelni az energiagazdálkodást, ezeket adja hozzá egy gyűjteményhez, és győződjön meg róla, hogy ez a gyűjtemény ki legyen zárva az energiagazdálkodásból.  

 Többek között például az alábbi számítógépeket lehet érdemes kizárni az energiagazdálkodásból:  

-   Számítógépek, amelyeknek bekapcsolva kell maradnia.  

-   Számítógépek, amelyekhez a felhasználóknak távoli asztali kapcsolattal kell csatlakoznia.  

-   Számítógépek, melyek nem képesek az energiagazdálkodás használatára.  

-   A terjesztési pont helyrendszer-szerepkörrel rendelkező számítógépek.  

-   Nyilvános számítógépek, például számítógép-állomások, információmegjelenítők vagy figyelési konzolok, melyeknél a számítógépnek és a monitornak is folyamatosan bekapcsolva kell lennie.  

 További információkért lásd: [az energiagazdálkodás konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/power/configuring-power-management.md).  

## <a name="first-apply-power-plans-to-a-test-collection-of-computers"></a>Az energiasémák alkalmazása először a számítógépek egy tesztgyűjteményére  
 Mindig tesztelje az energiagazdálkodási séma alkalmazásának hatásait számítógépek egy tesztgyűjteményén, mielőtt egy nagyobb számítógép-gyűjteményen alkalmazná az energiasémát.  

 A Windows XP vagy Windows Server 2003 rendszerű számítógépeken alkalmazott energiaellátási beállításokat akkor sem állítja vissza a rendszer az eredeti értékekre, ha kizárja a számítógépet az adott energiagazdálkodásból. Ha a Windows újabb verziói esetében zár ki egy számítógépet az energiagazdálkodásból, az összes energiaellátási beállítás visszaáll az eredeti értékére. Az egyes energiaellátási beállítások nem állíthatók vissza az eredeti értékükre.  

## <a name="apply-power-plan-settings-individually"></a>Az energiaséma beállításainak egyenkénti alkalmazása  
 Figyelje meg minden egyes energiagazdálkodási beállítás hatását a következő beállítás alkalmazása előtt, annak biztosítására, hogy minden beállítás a megfelelő hatást váltsa ki. Energiaséma beállításait kapcsolatos további információkért lásd: [terv elérhető energiagazdálkodási beállításokat](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) témakör [hogyan hozhat létre és alkalmazhat energiasémákat a System Center Configuration Managerben](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="regularly-monitor-computers-to-see-if-they-have-multiple-power-plans-applied"></a>A számítógépek rendszeres figyelése annak ellenőrzésére, hogy több energiaséma van-e alkalmazva rajtuk  
 Az energiagazdálkodás tartalmaz egy jelentést, amely az egynél több energiasémával rendelkező számítógépeket jeleníti meg.  

 Ha egy számítógép több gyűjtemény tagja, és mind különböző energiasémát alkalmaz, a rendszer a következő műveleteket hajtja végre:  

-   Energiaséma: Ha egy számítógépre alkalmazott energiaellátási beállítások több értéket, a legkevésbé korlátozó értéket használja.  

-   Felébresztés ideje: Ha több Felébresztési idő is vonatkozik egy asztali számítógépre, az éjfélhez legközelebbi idő lesz.  

     További információkért lásd: [több energiasémával rendelkező számítógépek](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Multiple) témakör [figyelés és tervezés a System Center Configuration Managerben az energiagazdálkodás hogyan](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md). További információ az energiagazdálkodás hogyan oldja fel ütközések: [hogyan hozhat létre és alkalmazhat energiasémákat a System Center Configuration Managerben](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="save-or-export-power-management-information-during-the-monitoring-and-planning-phase-of-power-management"></a>Az energiagazdálkodási adatok mentése vagy exportálása az energiagazdálkodás figyelési és tervezési fázisában  
 Napi jelentésekben használt energiagazdálkodási adatokat 31 napig megmarad a Configuration Manager-hely adatbázisába.  

 Havi jelentésekben használt energiagazdálkodási adatokat 13 hónapig megmarad a Configuration Manager-hely adatbázisába.  

 Amikor az energiagazdálkodás figyelési és tervezési, valamint megfelelőségi fázisában jelentéseket futtat, mentse vagy exportálja eredményét, amelynek meg szeretné őrizni jelentéseket későbbi összehasonlítás céljából adatai abban az esetben, ha később eltávolítja a Configuration Manager által.  

