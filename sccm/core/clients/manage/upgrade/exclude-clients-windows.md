---
title: "Ügyfélfrissítések kizárása |} Windows |} System Center Configuration Managerben"
description: "Útmutató Windows-ügyfelek kizárása első frissítése a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: de5602179f3ac55b51133b8280a0143f1b0ff30e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-exclude-upgrading-clients-for-windows-computers-in-system-center-configuration-manager"></a>Kihagyása a Windows rendszerű számítógépekre a System Center Configuration Manager-ügyfelek frissítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1610 verziójától kezdve, kizárhatja ügyfelek gyűjteményét az automatikus telepítése a frissített ügyfél-verziónkénti. Automatikus frissítés, valamint az egyéb módszerek, például a szoftverfrissítés-alapú, a parancsfájlok és a csoportházirend vonatkozik. Ezzel az ügyfél frissítésekor nagyobb figyelmet igénylő számítógépek gyűjteményét. Egy ügyfél, amely egy kizárt gyűjtemény figyelmen kívül hagyja a kérelmek frissített ügyfélszoftver telepítéséhez.

## <a name="configure-exclusion-for-automatic-upgrades"></a>Kizárási az automatikus frissítések konfigurálása

1. Nyissa meg a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**, és kattintson a **Hierarchiabeállítások**.

2. Kattintson a **ügyfélfrissítési** fülre.

3. Kattintson a jelölőnégyzetbe **kizárási megadott frissítésből ügyfelek**, és kizárási gyűjtemény, válassza ki a kizárni kívánt gyűjteményt. Egyetlen gyűjtemény kizárásra jelölhet ki.

4.  Kattintson a **OK** bezárásához és a konfiguráció mentéséhez. Ezt követően ügyfelek frissítési házirendet, miután a kizárt gyűjteményben lévő ügyfelek már nem automatikusan telepíti a frissítéseket a kliens szoftver. További információkért lásd: [Windows rendszerű számítógépekhez készült ügyfelek frissítése](upgrade-clients-for-windows-computers.md).

![Az automatikus frissítési kizárási beállításai](media/automatic_upgrade_exclusion.png)



>[!NOTE]
>Bár a felhasználói felület, hogy az ügyfelek nem frissülnek a a módszerrel, kétféleképpen felülírja ezeket a beállításokat is használhatja. Az ügyfélleküldéses telepítés és a kézi ügyféltelepítés segítségével bírálja felül ezt a konfigurációt. További részletekért tekintse meg a következő szakaszban.

## <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>Egy ügyfél, amely egy kizárt gyűjtemény frissítése

Mindaddig, amíg egy gyűjteményt ki lesznek zárva van konfigurálva, a gyűjtemény tagjai csak az ügyfélszoftvert frissíteni a két módszer, amelyek felülírják a kizárási veheti fel:
 - **Az Ügyfélleküldéses telepítés** – ügyfélleküldéses telepítés segítségével olyan ügyfél, amely egy kizárt gyűjtemény frissítése. Ez akkor tekinthető kell a rendszergazda szándéka szerint engedélyezett, és lehetővé teszi, hogy frissítse az ügyfeleket a teljes gyűjteményt a kizárási eltávolítása nélkül.       

 - **Kézi ügyféltelepítés** – manuálisan frissítheti a lévő ügyfelek egy kizárt gyűjtemény a ccmsetup a következő parancssori kapcsoló használata esetén: ***/ignoreskipupgrade***

  Ha egy ügyfél, amely tagja a kizárt gyűjtemény manuális frissítésére tett kísérlet, és ne használja ezt a kapcsolót, az ügyfél nem telepíti az új ügyfélszoftvert. További információ: [telepítése a Configuration Manager ügyfelek manuális](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).

Az ügyfél-telepítési módszerekről további információkért lásd: [ügyfélszoftverek központi telepítése Windows rendszerű számítógépekre a System Center Configuration Managerben](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

