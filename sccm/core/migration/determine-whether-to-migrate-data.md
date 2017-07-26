---
title: "Válassza ki, mit kell áttelepíteni |} Microsoft Docs"
description: "Ismerje meg, mely adatokat telepíthet át, és mely adatokat nem lehet áttelepíteni a System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99222dc8-0e1e-4513-8302-7a1acf671e9b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d37261c03fddc3d576fcef73fabd7189e4c46d38
ms.openlocfilehash: 9dc5f6c9f58e1fc33b2dc9dd76737ae23af81993
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="determine-whether-to-migrate-data-to-system-center-configuration-manager"></a>Annak meghatározása, hogy szükséges-e az adatoknak a System Center Configuration Manager rendszerbe történő áttelepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben, áttelepítés egy folyamatot biztosít a átvitelére adatok és konfigurációk létrehozott támogatott verzióiról a Configuration Manager az új hierarchiába.  Ezzel a funkcióval a következőket végezheti el:  

-   A több hierarchiás egy egységgé kombinálják.  

-   Adatok és konfigurációk áthelyezése egy laboratóriumi telepítésből az éles telepítési környezetbe.

-   Helyezze át a adatot és konfigurációs egy korábbi verziójáról a Configuration Manager, például a Configuration Manager 2007, amely rendelkezik a System Center Configuration Manager frissítési útvonal, vagy a System Center 2012 Configuration Manager (amely támogatja a frissítési lépések a System Center Configuration Manager).  

A terjesztési pont helyrendszerszerepköre és a terjesztési pontokat üzemeltető számítógépek kivételével nincs szükség (helyeket, helyrendszerszerepköröket, illetve a helyrendszerszerepköreit üzemeltető számítógépeket magába foglaló) infrastruktúrára, áttelepítésekre, illetve hierarchiák közti megosztásra.  

 Bár kiszolgálói infrastruktúra nem telepíthető át, a Configuration Manager ügyfelek hierarchiák közötti áttelepítheti. Az ügyfél áttelepítése magába foglalja az ügyfélszoftver által használt adatoknak a forráshierarchiából a célhierarchiába való áttelepítését, majd az ügyfélszoftver telepítését vagy a hozzárendelésének megváltoztatást úgy, hogy már az új hierarchiához tartozzon.

Miután az ügyfélt az új hierarchiához telepítette, és az ügyfél elküldte az adatait, a Configuration Manager egyedi azonosítója segít a Configuration Manager az adatokat, amelyeket előzőleg áttelepített társíthat az egyes ügyfélszámítógépekről.  

 Az áttelepítés által biztosított funkciókat segít beruházások értékét, és közben, és így a teljes körű kihasználása változtatások a termékben első központi, (amelyek először a System Center 2012 Configuration Manager verzióban jelent, és majd továbbra is a System Center Configuration Managerben) végzett karbantartása. Ezen változtatások közé tartozik egy egyszerűsített Configuration Manager-hierarchia által használt kevesebb helyet és az erőforrások és a feldolgozási teljesítmény javítása elérhető lesz a natív 64 bites kód a 64 bites hardveren futó használatával.  

 A Configuration Manager verziói által támogatott áttelepítési kapcsolatos információkért lásd: [előfeltételei a System Center Configuration Manager áttelepítési](../../core/migration/prerequisites-for-migration.md).  

 A következő szakaszok segítségével tervezheti meg az adatok, vagy nem telepíthető át:  

-   [A System Center Configuration Manager áttelepíthető adatok](#Can_Migrate)  

-   [Nem lehet áttelepíteni a System Center Configuration Manager adatok](#Cannot_migrate)  

##  <a name="Can_Migrate"></a>A System Center Configuration Manager áttelepíthető adatok  
 Áttelepítés támogatott Configuration Manager-hierarchia közötti legtöbb objektum áttelepíthető. A Configuration Manager 2007 támogatott verziójából néhány objektum áttelepített példányát módosítani kell, hogy a System Center 2012 Configuration Manager sémájának és objektumformátumának formátumban.

Ezek a módosítások nem érintik a forráshely adatbázisában az adatokat. A System Center 2012 Configuration Manager vagy a System Center Configuration Manager támogatott verziójából áttelepített objektumok nem igényelnek módosítást.  

 A Configuration Manager a forráshierarchiában lévő verziója alapján áttelepíthető objektumok a következők: Bizonyos objektumok, például a lekérdezések nem telepíthetők át. Ha ezeket a nem áttelepíthető objektumokat továbbra is használni kívánja, akkor ezeket újra létre kell hozni az új hierarchiában. Más objektumok, beleértve az egyes ügyfél-adatok automatikusan létrejönnek az új hierarchiában, ha abban a hierarchiában ügyfeleket kezel.  

### <a name="objects-that-you-can-migrate-from-system-center-2012-configuration-manager-or-system-center-configuration-manager-current-branch"></a>A System Center 2012 Configuration Manager vagy a System Center Configuration Manager aktuális ágának áttelepíthető objektumok

-   Hirdetések  

-   Alkalmazások, a System Center 2012 Configuration Manager és újabb verziók  

-   A System Center 2012 Configuration Manager és újabb verziók App-V virtuális környezet  

-   Eszközintelligencia testreszabása  

-   Határok  

-   Gyűjtemények: Gyűjtemények áttelepítése a System Center 2012 Configuration Manager vagy a System Center Configuration Manager támogatott verziójából származó, egy objektum-áttelepítési feladat használja.  

-   Megfelelőségi beállítások:  

    -   Referenciakonfigurációk  

    -   Konfigurációelemek  

-   Operációs rendszer központi telepítése:  

    -   Rendszerindító lemezképek  

    -   Illesztőprogram-csomagok  

    -   Illesztőprogramok  

    -   Képek  

    -   Csomagok  

    -   Feladatütemezések  

-   Keresési eredmények: Mentett keresési feltételek  

-   Szoftverfrissítések:  

    -   Központi telepítés  

    -   Központi telepítési csomagok  

    -   Sablonok  

    -   Szoftverfrissítési listák  

-   Szoftverterjesztési csomagok  

-   Szoftverhasználat-mérési szabályok  

-   Virtuális alkalmazáscsomagok  

### <a name="objects-that-you-can-migrate-from-configuration-manager-2007-sp2"></a>A Configuration Manager 2007 SP2 áttelepíthető objektumok

-   Hirdetések  

-   Alkalmazások, a System Center 2012 Configuration Manager és újabb verziók  

-   A System Center 2012 Configuration Manager és újabb verziók App-V virtuális környezet  

-   Eszközintelligencia testreszabása  

-   Határok  

-   Gyűjtemények: Gyűjteményt telepít át, a Configuration Manager 2007 támogatott verziójából a gyűjtemény áttelepítési feladatának használatával.  

-   Megfelelőségi beállítások (a Configuration Manager 2007-ben szükséges konfigurációkezelésként említve)  

    -   Referenciakonfigurációk  

    -   Konfigurációelemek  

-   Operációs rendszer központi telepítése:  

    -   Rendszerindító lemezképek  

    -   Illesztőprogram-csomagok  

    -   Illesztőprogramok  

    -   Képek  

    -   Csomagok  

    -   Feladatütemezések  

-   Keresési eredmények: A keresési mappák  

-   Szoftverfrissítések:  

    -   Központi telepítés  

    -   Központi telepítési csomagok  

    -   Sablonok  

    -   Szoftverfrissítési listák  

-   Szoftverterjesztési csomagok  

-   Szoftverhasználat-mérési szabályok  

-   Virtuális alkalmazáscsomagok  

##  <a name="Cannot_migrate"></a>Nem lehet áttelepíteni a System Center Configuration Manager adatok  
 A következő típusú objektumok nem telepíthetők át:  

-   AMT ügyfél kiépítési információi  

-   Az ügyfeleken, beleértve fájlok:  

    -   Ügyfélleltári és előzményi adatok  

    -   Az ügyfél gyorsítótárában lévő fájlok  

-   Lekérdezések  

-   A Configuration Manager 2007 biztonsági jogosultságai és példányai a hely és az objektumok  

-   Az SQL Server Reporting Services Configuration Manager 2007-jelentések  

-   A Configuration Manager 2007 webes jelentések  

-   A System Center 2012 Configuration Manager és a System Center Configuration Manager-jelentések  

-   A System Center 2012 Configuration Manager és a System Center Configuration Manager szerepköralapú felügyelet:  

    -   Biztonsági szerepkörök  

    -   Biztonsági hatókörök  

