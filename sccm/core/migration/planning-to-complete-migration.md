---
title: "Áttelepítés befejezésének |} Microsoft Docs"
description: "Útmutató a System Center Configuration Manager célhierarchiába áttelepítése befejezése után a forráshierarchia már nem tartalmaz adatokat."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0f4a10ba7bbe397f05d724141b562b6cd8b78ea8
ms.openlocfilehash: eb1d2e320df02b26423ed4341d5bd1568b9444ad
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-to-complete-migration-in-system-center-configuration-manager"></a>Tervezi áttelepítése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerrel, befejezheti az áttelepítés folyamatát, ha a forráshierarchia már nem rendelkezik a célhierarchiára áttelepíteni kívánt adatokat. Az áttelepítés befejezése a következő általános lépéseket tartalmazza:  

-   Győződjön meg arról, hogy a szükséges adatokat át lett telepítve. A forráshierarchiából történő áttelepítés befejezése előtt győződjön meg arról, hogy sikeresen áttelepítette összes olyan erőforrást a forráshierarchiából, amelyre szüksége van a célhierarchiában. Ez tartalmazhatja az adatok és ügyfelek.  

-   Állítsa le az adatgyűjtést a forráshierarchiában. A forráshierarchiából történő áttelepítés befejezéséhez először le kell adatokat gyűjt a forráshelyekről.  

-   Áttelepítési adatok törlése. Miután leállította az adatgyűjtést a forráshierarchiában található forráshelyekről, eltávolíthatja az áttelepítési folyamat és a forrás hierarchia adatait a célhierarchia adatbázisából.  

-   A forráshierarchia leszerelése. Miután befejezte az áttelepítést egy forráshierarchiából és, hogy a hierarchia már nem tartalmaz felügyelt erőforrásokat, leszerelheti a forráshierarchiában lévő helyeket, és eltávolíthatja a kapcsolódó infrastruktúrát a környezetből. Információ a helyek és a forráshierarchiák leszereléséről a dokumentációt a Configuration Manager adott verziójához.  

A következő részekben az adatgyűjtést, és az áttelepítési adatok törlése leállításával forráshierarchiából áttelepítéshez tervezéséhez nyújtanak segítséget:  

-   [Adatgyűjtés leállításának megtervezése](#Plan_to_Stop_Data_Gath)  

-   [Az áttelepítési adatok törlésének megtervezése](#Plan_to_clean_up)  

##  <a name="Plan_to_Stop_Data_Gath"></a>Adatgyűjtés leállításának megtervezése  
 Mielőtt befejezi az áttelepítést, és törölje az áttelepítési adatokat, le kell állítania, adatgyűjtést a forráshierarchiában lévő összes forráshelyről. Ha azt szeretné, állítsa le az adatgyűjtést a forráshelyekről, végezze el a **adatgyűjtés leállítása** az alacsonyabb szintű forráshelyeken parancsot, és ismételje meg a műveletet minden szülőhelyen. A forráshierarchia legfelső szintű helyén kell utoljára leállítania az adatgyűjtést. Le kell állítania az adatgyűjtést, az összes gyermekhely a szülőhelyen elvégzi a parancs végrehajtása előtt. Általában csak leállítja az adatgyűjtést, amikor készen áll az áttelepítési folyamat befejezéséhez.  

 Miután leállította az adatgyűjtést a forráshelyen, erről a helyről a megosztott terjesztési pontok nem lesznek elérhetők tartalomhelyként a célhierarchiában lévő ügyfelek számára. Ezért győződjön meg arról, hogy minden olyan áttelepített tartalom igénylő a célhierarchiában lévő ügyfelek elérését elérhető marad a következő lehetőségek egyikének használatával:  

-   A célhierarchiában terjessze a tartalmat legalább egy terjesztési pontra.  

-   Mielőtt leállítaná az adatgyűjtést a forráshelyen, frissítés, vagy a szükséges tartalom rendelkező megosztott terjesztési pontok átrendelése. További hamarosan frissítéséről vagy újbóli megosztott terjesztési pontok, a megfelelő szakaszaiban talál [a System Center Configuration Managerben tartalom központi telepítési stratégiájának tervezése](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

Miután leállította az adatgyűjtést a forráshierarchiában lévő összes forráshelyről, törölheti is az áttelepítési adatok. Áttelepítési adatok törléséig minden egyes áttelepítési feladat futtatott vagy futtatásra beütemezett a Configuration Manager-konzolon elérhető marad.  

Adatok forráshelyekről és kapcsolatban bővebben lásd: [a System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md).  

##  <a name="Plan_to_clean_up"></a>Az áttelepítési adatok törlésének megtervezése  
 Az áttelepítés befejezéséhez szükséges utolsó lépése, hogy törölje az áttelepítési adatokat. Használhatja a **áttelepítési adatok törlése** parancsot, amikor már leállította az adatgyűjtést a forráshierarchia összes forráshelyén. Ez a választható művelet eltávolítja az aktuális forráshierarchia adatait a célhierarchia adatbázisából.  

 Áttelepítési adatok törlése, ha a rendszer eltávolítja az áttelepítés legtöbb adatait a célhierarchia adatbázisából. Áttelepített objektumok adatai azonban megőrződnek. Ezen adatok segítségével a **áttelepítési** munkaterületen újból konfigurálhatja azt a forráshierarchiát, amely adatokat tartalmazó át lett telepítve az adott forráshierarchiából, az áttelepítés folytatásához, vagy tekintse át az objektumokat és az azokhoz az előzőleg áttelepített objektumok helyeket.  

