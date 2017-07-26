---
title: "Ügyfelek áttelepítésének megtervezése |} Microsoft Docs"
description: "További tudnivalók a feladatokat, ügyfelek áttelepítését a forráshierarchiából a System Center Configuration Manager célhierarchiába."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e27b0b7-7bd3-45cd-bc99-9c991606c637
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ac4576035fda943e38d960dd425d44b7a6ef6a01
ms.openlocfilehash: b52ca4059dfeed08cabf1f75319da40d6499622f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-client-migration-strategy-in-system-center-configuration-manager"></a>A System Center Configuration Managerben ügyfélszoftverek áttelepítési stratégiájának tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ügyfelek áttelepítését a forráshierarchiából a System Center Configuration Manager célhierarchiába, két feladatot kell elvégeznie. Át kell telepítenie az ügyfélhez rendelt objektumokat, majd újra kell telepítenie az ügyfelet, vagy ismételten hozzá kell rendelnie az ügyfelet a forráshierarchiából a célhierarchiához. Először az objektumokat kell áttelepítenie, hogy elérhetők legyenek az ügyfelek áttelepítésekor. Az ügyfélhez rendelt objektumok áttelepítési feladatok használatával telepíthetők át. Az ügyfél társított az objektumok áttelepítésével kapcsolatos információkért lásd: [egy feladat stratégiájának tervezése a System Center Configuration Managerben](../../core/migration/planning-a-migration-job-strategy.md).  

 A következő részekben leírtak alapján tervezheti meg az ügyfelek áttelepítését a célhierarchiába.  

-   [Az ügyfelek célhierarchiába való áttelepítésének tervezése](#Planning_for_Client_Agent_Migration)  

-   [Az ügyfeleken tárolt adatok áttelepítés közbeni kezelésének megtervezése](#Planning_for_Client_Data_Migration)  

-   [Tervezze meg a leltári és megfelelőségi adatokat az áttelepítés során](#Planning_for_Inventory_data_migration)  

##  <a name="Planning_for_Client_Agent_Migration"></a> Az ügyfelek célhierarchiába való áttelepítésének tervezése  
 Amikor ügyfeleket telepít át egy forráshierarchiából, a számítógép az ügyfélfrissítéseket megfeleljen a célhierarchia rajtuk az ügyfélszoftvert.  

-   **A Configuration Manager 2007 verziójú Forráshierarchia:** Amikor ügyfeleket telepít át, amelyek a Configuration Manager, a szoftver az ügyfélfrissítéseket a célhierarchia ügyfélverzióra támogatott verzióját futtatja.  

-   **A System Center 2012 Configuration Manager vagy újabb Forráshierarchia:** Amikor azonos termékverziójú hierarchiák között ügyfeleket telepít át, az ügyfélszoftver nem módosítható, vagy frissítse. Ehelyett az alkalmazás a forráshierarchiáról a célhierarchia egyik helyére változtatja az ügyfél hozzárendelését.  

    > [!NOTE]  
    >  Ha egy forráshierarchia termékverziója nem támogatott a célhierarchiába történő áttelepítéshez, frissítse kompatibilis verzióra a forráshierarchiában lévő összes helyet és ügyfelet. Miután frissítette a forráshierarchiát egy támogatott termékverzióra, végrehajthatja az áttelepítést a hierarchiák között. További információkért lásd: [verziója a Configuration Manager áttelepítéshez támogatott](../../core/migration/prerequisites-for-migration.md#BKMK_SupportedMigrationVersions) a [előfeltételei a System Center Configuration Manager áttelepítési](../../core/migration/prerequisites-for-migration.md).  

Az ügyfelek áttelepítésének megtervezésekor vegye figyelembe a következőket:  

-   Az ügyfelek frissítéséhez vagy a hozzárendelésüknek a forráshelyről a célhelyre történő módosításához használhatja bármelyik olyan ügyfél-telepítési módszert, amelyet a célhierarchia támogat. A szokásos ügyfél-telepítési módszerek közé tartozik az ügyfelek leküldéses telepítése, a csoportházirend és a szoftverfrissítéses ügyféltelepítés. További információkért lásd: [ügyféltelepítési módszerek a System Center Configuration Managerben](../../core/clients/deploy/plan/client-installation-methods.md).  

-   Győződjön meg arról, hogy az ügyfélszoftvert a forráshierarchiában futtató eszköz megfelel a minimális hardverkövetelményeknek, és a rendeltetési hierarchiában a Configuration Manager verziója által támogatott operációs rendszerrel.  

-   Mielőtt áttelepít egy ügyfelet, futtassa az áttelepítési feladat, hogy az ügyfél használni fog a célhierarchiában lévő adatok áttelepítése.  

-   Frissített ügyfelek megőrzik a központi telepítés futtatási előzményei. Ez megakadályozza, hogy a telepítések szükségtelen újbóli futtatását a célhierarchiában.  

    -   A Configuration Manager 2007-ügyfelek esetében a hirdetés futtatási előzményei őrződnek meg.  

    -   A System Center 2012 Configuration Manager vagy a System Center Configuration Manager ügyfelek, a központi telepítés futtatási előzményei őrződnek meg.  

-   Az ügyfeleket tetszőleges sorrendben telepítheti át a forráshierarchiában lévő helyekről. Azonban célszerű inkább korlátozott mennyiségű ügyfél áttelepítése fázisban történik egyszerre nagy mennyiségű ügyfél áttelepítése helyett. A fázisos áttelepítés csökkenti a hálózat sávszélességigényét és a kiszolgáló által végrehajtott feldolgozást, amikor az egyes újonnan frissített ügyfelek elküldik a teljes kezdeti leltárukra vonatkozó adataikat és a megfelelési adataikat a hozzájuk rendelt helyre.  

-   A Configuration Manager 2007-ügyfelek áttelepítésekor a rendszer eltávolítja a meglévő ügyfélszoftvert az ügyfélszámítógépről, és az új ügyfélszoftver telepítése.  

-   A Configuration Manager nem telepíthető át egy Configuration Manager 2007-ügyfél, amely rendelkezik az App-V-ügyfél telepítve, kivéve, ha az App-V-ügyfél verziója nem 4.6 SP1 vagy újabb.  

Az ügyfél áttelepítési folyamatát a figyelheti a **áttelepítési** csomópontjának a **felügyeleti** munkaterület a Configuration Manager konzolon.  

Miután áttelepítette az ügyfelet a célhierarchiába, már nem kezelheti az adott eszközt a forráshierarchia használatával, és érdemes eltávolítania az ügyfelet a forráshierarchiából. Bár ez nem követelmény a hierarchiák áttelepítésekor, ezzel megakadályozhatja az áttelepített ügyfelek újbóli felismerését a forráshierarchiában, illetve helytelen számú erőforrás létrejöttét a két hierarchiában az áttelepítés során. Például amikor egy áttelepített ügyfél a forráshely adatbázisában marad, és futtat egy szoftverfrissítési jelentést, előfordulhat, hogy a számítógép a jelentésben tévesen nem felügyelt erőforrásként fog szerepelni, holott már a célhierarchiában van felügyelve.  

##  <a name="Planning_for_Client_Data_Migration"></a> Az ügyfeleken tárolt adatok áttelepítés közbeni kezelésének megtervezése  
Amikor egy ügyfelet áttelepít a forráshierarchiájából a célhierarchiába, néhány adat megőrződik az eszközön, más adatok pedig nem lesznek elérhetők az eszközön az áttelepítést követően.  

A következő adatok őrződnek meg az ügyféleszközön:  

-   Az egyedi azonosító (GUID), amely összerendeli az ügyfelet és annak adatait a Configuration Manager adatbázisába.  

-   A hirdetmények vagy a telepítések előzményadatai, amelyek megakadályozzák, hogy az ügyfelek szükségtelenül újból futtassák a hirdetményeket vagy a telepítéseket a célhierarchiában.  

A következő adatok nem őrződnek meg az ügyféleszközön:  

-   Az ügyfél gyorsítótárában lévő fájlok. Ha az ügyfélnek szüksége van ezekre a fájlokra a szoftver telepítéséhez, újból letölti azokat a célhierarchiából.  

-   A forráshierarchiából származó információ a még nem futtatott hirdetményekről vagy telepítésekről. Ha azt szeretné, hogy az ügyfél futtassa a hirdetményeket vagy telepítéseket az áttelepítése után, újból telepíteni kell azokat az ügyfélre a célhierarchiában.  

-   A leltárra vonatkozó információ. Az ügyfél újraküldi ezt az információt a hozzárendelt helyre a célhierarchiában, miután az ügyfél és az új ügyféladatok hozott létre.  

-   Megfelelési adatok. Az ügyfél újraküldi ezt az információt a hozzárendelt helyre a célhierarchiában, miután az ügyfél és az új ügyféladatok hozott létre.  

Ügyfél áttelepítésekor a Configuration Manager-ügyfél beállításjegyzék és a fájlelérési út a tárolt adatok nem őrződnek meg. Az áttelepítés után adja meg újból ezeket a beállításokat. A szokásos beállítások a következők:  

-   Energiagazdálkodási sémák  

-   Naplózási beállítások  

-   Helyi házirend beállításai  

Ezenkívül előfordulhat, hogy újra kell telepítenie néhány alkalmazást.  

##  <a name="Planning_for_Inventory_data_migration"></a> A leltáradatok és a megfelelési adatok áttelepítés közbeni kezelésének megtervezése  
A rendszer nem menti az ügyfél leltáradatait és megfelelési adatait, amikor a célhelyre telepíti át az ügyfelet. Ezek az adatok akkor jönnek létre a célhierarchiában, amikor az ügyfél elküldi az adatait a hozzárendelt helyre. Csökkentheti a hálózat sávszélességigényét és a kiszolgáló által végrehajtott feldolgozást, ha az ügyfeleket több fázisban telepíti át, egy-egy alkalommal kis mennyiségű ügyfelet kiválasztva, és nem nagy mennyiségű ügyfelet telepít át egyszerre.  

 Ezenkívül nem telepítheti át a hardverleltár testreszabásait sem a forráshierarchiából. Ezeket az áttelepítéstől függetlenül kell megadnia a célhierarchiában. Hardverleltár bővítése kapcsolatos információkért lásd: [Hardverleltár konfigurálása a System Center Configuration Managerben](../../core/clients/manage/inventory/configure-hardware-inventory.md).  

