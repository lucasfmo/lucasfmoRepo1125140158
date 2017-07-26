---
title: "Az Endpoint Protection kártevő-definíciók hálózati megosztásról |} Microsoft Docs"
description: "Útmutató a Microsoft Updates a Configuration Manager az Endpoint Protection kártevő-definíciók letöltésének engedélyezése."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ab7626ae-d4bf-4ca6-ab25-c61f96800a02
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 58c468fc3d4427cc1f2a8f197ab784a767151203
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="enable-endpoint-protection-malware-definitions-to-download-from-microsoft-updates-for-configuration-manager"></a>Az Endpoint Protection kártevő-definíciók letöltése a Microsoft Updates a Configuration Manager engedélyezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 Ha a Microsoft Update szolgáltatásból tölti le a definíciókat, az ügyfelek a Kártevőirtó házirend párbeszédpanel **Definíciófrissítések** szakaszában meghatározott időközönként ellenőrzik a Microsoft Update webhelyet.

 Ez a módszer akkor lehet hasznos, amikor az ügyfél nem rendelkezik kapcsolattal a Configuration Manager-helyhez, vagy ha azt szeretné, hogy a felhasználók kezdeményezhessék a definíciók frissítését.

> [!IMPORTANT]
>  Az ügyfeleknek el kell érniük a Microsoft Update-et az interneten, hogy ezt a módszert használhassák a definíciófrissítések letöltésére.

## <a name="using-the-microsoft-malware-protection-center-to-download-definitions"></a>A definíciók frissítése a Microsoft kártevőkezelési központból
 Beállíthatja, hogy az ügyfelek a definíciófrissítéseket a Microsoft kártevőkezelési központból töltsék le. Ez a beállítás az Endpoint Protection-ügyfelek használják definíciófrissítések letöltésére, ha azok nem volt képes a más forrásból származó frissítések letöltésére. Ez a frissítési mód hasznos lehet, ha a Configuration Manager-infrastruktúrával, a frissítések megakadályozó probléma van.

> [!IMPORTANT]
>  Az ügyfeleknek el kell tudniuk érni a Microsoft Update szolgáltatást az interneten, hogy ezt a módszert használhassák a definíciófrissítések letöltésére.


> [!div class="button"]
[Következő lépés >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Vissza >](endpoint-configure-alerts.md)

