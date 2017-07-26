---
title: "Áttelepítés tervezése |} Microsoft Docs"
description: "Helyek és hierarchiák tudnivalók az adatok a System Center Configuration Manager célhierarchiába történő áttelepítése előtt."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a2405bc04889bd6ae46069fe447228149bbaf468
ms.openlocfilehash: fffef1e95e1dfa03971f140a6e5a7fff9bfe5e27
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-migration-to-system-center-configuration-manager"></a>System Center Configuration Manager az áttelepítés tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt adatokat telepít át a System Center Configuration Manager célhierarchiába, győződjön meg arról, hogy jártas a Configuration Manager helyeinek és hierarchiáinak. Helyek és hierarchiák kapcsolatban bővebben lásd: [a System Center Configuration Manager – alapok](../../core/understand/fundamentals.md).  

 Telepítenie kell a System Center Configuration Manager hierarchia a célhierarchia kell, mielőtt egy támogatott forráshierarchiából telepít át adatokat.  

 Miután telepítette a célhierarchiában, beállítása a felügyeleti funkciókat, használni kívánt a célhierarchiában lévő adatok áttelepítése előtt.  

 Továbbá lehetséges, hogy a forrás és a célhierarchia közötti átfedést tervezését. Például előfordulhat, hogy beállította a forráshierarchiában az azonos hálózati helyeket vagy határokat használja a célhierarchia, és ezután telepítse az új ügyfeleket a célhierarchiába és használjon automatikus helyhozzárendelést. Ebben a forgatókönyvben egy újonnan telepített Configuration Manager-ügyfél bármelyik hierachiából csatlakozási helyet is választani, az ügyfél esetleg helytelenül hozzárendelése a forráshierarchia. Ezért tervezze meg a célhierarchiában lévő minden új ügyfél hozzárendelése automatikus helyhozzárendelés használata helyett a hierarchia meghatározott helyét.  

 További információ a helyek hozzárendeléséről beállításáról lásd: [az ügyfelek helyhozzárendelésének szempontjai](../../core/plan-design/hierarchy/interoperability-between-different-versions.md#BKMK_SupConfigSiteAssignment) a [együttműködés a System Center Configuration Manager különböző verziói között](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

## <a name="plan-topics"></a>Terv kapcsolatos témakörök  
 Használja a következő témakörök segítségével megtervezheti a támogatott forráshierarchiából a System Center Configuration Manager célhierarchiába áttelepítéséhez:

-   [A System Center Configuration Managerben a migrálással kapcsolatos előfeltételek](../../core/migration/prerequisites-for-migration.md)  

-   [Rendszergazdai ellenőrzőlista az áttelepítés tervezése a System Center Configuration Managerben](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Szükség van-e az adatok áttelepítése a System Center Configuration Managerben](../../core/migration/determine-whether-to-migrate-data.md)  

-   [A System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md)  

-   [Rendszergazdai ellenőrzőlista az áttelepítés tervezése a System Center Configuration Managerben](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [A System Center Configuration Managerben ügyfélszoftverek áttelepítési stratégiájának tervezése](../../core/migration/planning-a-client-migration-strategy.md)  

-   [Tervezze meg a tartalom központi telepítési stratégiájának a System Center Configuration Managerben](../../core/migration/planning-a-content-deployment-migration-strategy.md)  

-   [A Configuration Manager-objektumok a System Center Configuration Manager az áttelepítés tervezése](../../core/migration/planning-for-the-migration-of-objects.md)  

-   [A System Center Configuration Manager áttelepítési tevékenység figyelésének tervezése](../../core/migration/planning-to-monitor-migration-activity.md)  

-   [Tervezi áttelepítése a System Center Configuration Managerben](../../core/migration/planning-to-complete-migration.md)  

