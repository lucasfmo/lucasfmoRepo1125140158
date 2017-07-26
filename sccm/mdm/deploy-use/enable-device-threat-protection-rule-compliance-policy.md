---
title: "Megfelelőségi szabályzat eszköz védelmi szabály engedélyezése |} Microsoft Docs"
description: "Engedélyezze a mobil threat protection szabály az eszköz megfelelőségi házirendben is szerepel."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: faa92e150686e615164ce3f5435b77a65305aab3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Az eszköz threat protection-szabályt a megfelelőségi szabályzat engedélyezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Intune és a Lookout mobil veszélyforrások elleni védelem lehetővé teszi a mobil fenyegetések észlelése és a kockázatbecslés az eszközön. Létrehozhat egy megfelelőségi szabályzatot szabály a Configuration Managerben annak megállapításához, hogy az eszköz megfelel a kockázatbecslés tartalmazza. Használhatja a feltételes hozzáférési házirend engedélyezi vagy letiltja az Exchange, SharePoint és egyéb eszközök megfelelőségének alapuló szolgáltatások eléréséhez.

A Lookout eszköz fenyegetésészlelés befolyásolják a megfelelőségi szabályzat, az eszköz rendelkezik:

* A **veszélyforrások elleni Eszközvédelem** szabály engedélyezni kell a megfelelőségi szabályzat.

* A **Lookout állapot** lapját a **Intune felügyeleti konzolján** kell megjeleníteni **aktív**. Tekintse meg a [engedélyezése a Lookout MTP-alapú kapcsolat az Intune-ban](enable-lookout-connection-in-intune.md) témakör további részleteket és a Lookout integráció aktiválására vonatkozó útmutatást.


Mielőtt az eszköz threat protection szabályt hoz létre, a előírásainak házirend, akkor javasoljuk, hogy Ön [Lookout veszélyforrások elleni eszközvédelem előfizetés beállítása](set-up-your-subscription-with-lookout.md), [engedélyezése az Intune-ban a Lookout kapcsolat](enable-lookout-connection-in-intune.md), és [keressen olyan munkahelyi alkalmazás konfigurálása](configure-and-deploy-lookout-for-work-apps.md). A megfelelőségi szabály csak a telepítés befejezése után lépnek érvénybe.

Ahhoz, hogy az eszköz threat protection szabály, egy meglévő házirend-megfelelőségi vagy hozzon létre egy újat.

A Lookout eszköz threat protection telepítésének részeként a a [Lookout konzol](https://aad.lookout.com), létrehozott egy házirendet, amely magas, közepes és alacsony szintű az egyes fenyegetésekre osztályozza. Az Intune megfelelőségi házirendben is szerepel a fenyegettségi szint használandó maximális engedélyezett fenyegettségi szint beállítása.

Az a **szabályok** lap a megfelelőségi házirend varázsló, adja meg egy új szabályt, a következő információkat:
  * Feltétel: Eszköz threat protection maximális kockázati szintjét.
  * Érték: Az érték a következők egyike lehet:
    * **Nincs (védett)**: Ez az a legbiztonságosabb. Ez azt jelenti, hogy az eszköz nem rendelkezik a fenyegetéseket. Ha minden változáskérésnél a fenyegetések találhatók, az eszköz nem megfelelő kiértékelése.
    * **Low**: Az eszköz megfelelőnek történik, ha csak az alacsony szintű fenyegetést találhatók. Minden újabb állapotba állítja az eszközt egy nem megfelelő.
    * **Közepes**: Az eszköz megfelelőnek, ha az eszközön található fenyegetések közepes vagy alacsony szintje kiértékelése. Ha magas szintű fenyegetést észlel, az eszköz nem megfelelő határozza meg.
    * **Magas**: Ez a legkevésbé biztonságos. Alapvetően, ez lehetővé teszi, hogy az összes fenyegetés szint, és lehet, hogy csak akkor hasznos, ha ez a megoldás csak számára a jelentéskészítéshez használ.

Feltételes hozzáférési szabályzatokat hoz létre az Office 365 és más szolgáltatások védelmét, ha a fenti megfelelőségértékelés figyelembe veszi, és nem megfelelő eszközöknek nincs hozzáférése a vállalati erőforrások eléréséhez a fenyegetés kijavításáig.

Az eszköz threat protection állapota megjelenik a **biztonsági** csomópontja a **figyelés** munkaterületen.
A szál különböző szintű állapotának összegzését visual diagram jelenik meg. Az egyes szakaszok további részletek a diagram meg, például, eszközöket, amelyek nem megfelelő platform és minden jelentett hibák számát.
Megtekintheti az egyes eszköz állapotát a **eszközök és megfelelőség** munkaterületen, a **eszközök**.  Hozzáadhat a **fenyegetés eszközmegfelelőség** és a **eszköz veszélyforrás adott szintjéhez** oszlopok állapotát tekintheti meg.  Ezekben az oszlopokban alapértelmezés szerint nem jelenik meg.

