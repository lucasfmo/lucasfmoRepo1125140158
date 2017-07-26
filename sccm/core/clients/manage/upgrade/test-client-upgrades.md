---
title: "Teszt ügyfél frissíti az üzem előtti gyűjteménnyel |} Microsoft Docs"
description: "Ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49ef2ed2-2e15-4637-8b63-1d5b7f9c17e1
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 572ef13883f7930e69ec1f1f53c9bfe029898c81
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-test-client-upgrades-in-a-pre-production-collection-in-system-center-configuration-manager"></a>Ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Új Configuration Manager ügyfélverzió tesztelheti egy üzem előtti gyűjteménnyel, mielőtt frissítené vele a webhely többi részétől.  Ha ezt teszi, csak a vizsgálat gyűjtemény részét képező eszközök frissülnek. Miután tesztelte az ügyfelet, előléptetheti az ügyfelet, ami a hely többi részének elérhetővé teszi az ügyfélszoftver új verzióját.

> [!NOTE]
> Előléptetése üzemi teszt ügyfél, be kell jelentkeznie biztonsági szerepkörrel rendelkező felhasználóként **teljes körű rendszergazda** és egy biztonsági hatókört a **összes**. További információkért lásd: [szerepköralapú adminisztrációjának alapjai](/sccm/core/understand/fundamentals-of-role-based-administration). A központi adminisztrációs hely vagy egy legfelső szintű önálló elsődleges helyhez csatlakoztatott kiszolgálót is kell bejelentkeznie.

 Az ügyfelek üzem előtti tesztelés 3 alapvető lépésből áll.  

1.  Éles üzem előtti gyűjtemény használatára automatikus ügyfélfrissítések konfigurálása.  

2.  A frissítés a Configuration Manager, az ügyfél új verzióját tartalmazza.  

3.  A termelési új ügyfél előléptetése.  

##  <a name="to-configure-automatic-client-upgrades-to-use-a-pre-production-collection"></a>Éles üzem előtti gyűjtemény használatára az automatikus ügyfélfrissítések konfigurálása  

1. [Állítson be egy gyűjtemény](..\collections\create-collections.md) , amely tartalmazza az éles üzem előtti ügyfelet telepíteni kívánt számítógépeket. Éles üzem előtti gyűjtemény munkacsoport-számítógépek ne vegye fel. A hitelesítés használatához a terjesztési pont nem használhatják az éles üzem előtti ügyfélcsomag eléréséhez.   

1.  Nyissa meg a Configuration Manager konzolon **felügyeleti** > **Helykonfiguráció** > **helyek**, és válassza a **Hierarchiabeállítások**.  

     A **Hierarchiabeállítások tulajdonságai** **Ügyfélfrissítés**lapján:  

    -   Válassza **Az összes ügyfél automatikus frissítése az üzemi előtti gyűjteményben az üzemi előtti ügyféllel**elemet.  

    -   Adja meg az üzemi előtti gyűjteményként használni kívánt gyűjtemény nevét.  

![Ügyfélfrissítések tesztelése](media/test-client-upgrades.png)

>[!NOTE]
>Ezek a beállítások módosításához a fiók tagjának kell lennie a **teljes körű rendszergazda** biztonsági szerepkör, és a **összes** biztonsági hatókör megadása.


##  <a name="to-install-a-configuration-manager-update-that-includes-a-new-version-of-the-client"></a>Az ügyfél új verzióját tartalmazó Configuration Manager-frissítés telepítése  

1.  A Configuration Manager-konzolon nyissa meg **felügyeleti** > **frissítés és karbantartás**, jelölje be egy **elérhető** frissítése, és válassza a **frissítési csomag telepítése**. (Előtt verzió 1702, frissítés és karbantartás alatt állt **felügyeleti** > **Felhőszolgáltatások**.)

     További információk frissítések telepítéséről: [A System Center Configuration Manager frissítései](../../../../core/servers/manage/updates.md).  

2.  A frissítés telepítése során a a **ügyfél beállításai** lapján jelöljön ki **tesztelése az üzem előtti gyűjteményben**.  

3.  Fejezze be a varázslót, és telepítse a frissítési csomagot.  

     A varázsló befejezése után az üzem előtti gyűjtemény ügyfelei megkezdik a frissített ügyfél telepítését. A frissített ügyfelek központi telepítésének figyeléséhez menjen ide: **Figyelés** > **Ügyfélállapot** > **Üzem előtti ügyféltelepítés**. További információk: [Ügyfél-központitelepítési állapot figyelése a System Center Configuration Managerben](../../../../core/clients/deploy/monitor-client-deployment-status.md).

    > [!NOTE]
    > Előfordulhat, hogy egy üzem előtti gyűjteménnyel helyrendszerszerepköröket üzemeltető számítógépeken a központi telepítési állapot jelentett **nem kompatibilis** még ha az ügyfél telepítése sikerült. Amikor előlépteti az ügyfelet üzemre, a telepítési állapota helyesen szerepel a jelentésekben.

##  <a name="to-promote-the-new-client-to-production"></a>Az új ügyfél előléptetése üzemi ügyféllé  

1.  A Configuration Manager-konzolon nyissa meg **felügyeleti** > **frissítés és karbantartás**, és válassza a **üzem előtti ügyfél előléptetése**. (Előtt verzió 1702, frissítés és karbantartás alatt állt **felügyeleti** > **Felhőszolgáltatások**.)

    > [!TIP]
    > Az **Üzem előtti ügyfél előléptetése** gomb az ügyféltelepítések nyomon követésekor is elérhető a konzol **Figyelés** > **Ügyfélállapot** > **Üzem előtti ügyféltelepítés**eleménél.

2.  Tekintse át az éles tárhely és az éles üzem előtti ügyfél-verziónkénti, győződjön meg arról, hogy a megfelelő üzem előtti gyűjtemény van megadva, és kattintson **előléptetés**, majd **Igen**.  

3.  A párbeszédpanel bezárása után a frissített ügyfélverzióra felülírja, az ügyfél verzióját használja a hierarchiában. Ezután frissítheti az ügyfeleket a teljes helyen. További információk: [A Windows rendszerű számítógépekhez készült ügyfelek frissítése a System Center Configuration Managerben](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

>[!NOTE]
>Ahhoz, hogy az éles üzem előtti ügyfelet, vagy egy üzem előtti ügyfél üzemi ügyféllé előléptetéséhez, a fiók, amely rendelkezik egy biztonsági szerepkör tagjának kell lennie **olvasási** és **módosítás** engedélyeit a **frissítési csomagokat** objektum.
>Ügyfélfrissítések fogadják el semmilyen Configuration Manager karbantartási időszakok konfigurálása.

