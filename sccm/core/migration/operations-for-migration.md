---
title: "Áttelepítési műveletek |} Microsoft Docs"
description: "Hozzon létre, és az adatok és ügyfelek áttelepítése a System Center Configuration Manager feladatok futtatása."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c28e3492-851a-40fc-ba13-67ebc2d8b41a
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5df6478362499d87038fa4ed2cb444aa8d5b4b7c
ms.openlocfilehash: fb8a292c4fecbe5744e2cd09bc1442fab11046bc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="operations-for-migrating-to-system-center-configuration-manager"></a>System Center Configuration Managerben történő áttelepítés műveletei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager az áttelepítés után áttelepítheti a adatok és az ügyfelek sikeres adatgyűjtést egy forráshelyről ebben a támogatott forráshierarchiát. Olvassa el a következő szakaszokban hozzon létre és futtasson áttelepítési feladatokat adatok és az ügyfelek áttelepítését, majd fejezze be az áttelepítési folyamat.  

-   [Áttelepítési feladatok létrehozása és szerkesztése](#Create_Edit_migration_Jobs)  

-   [Áttelepítési feladatok futtatása](#Run_Migration_Jobs)  

-   [Megosztott terjesztési pont frissítése vagy hozzárendelésének módosítása](#BKMK_ProcUpgrdSS)  

-   [Az áttelepítési tevékenység figyelése az Áttelepítés munkaterületen](#Monitor_MIgration)  

-   [Ügyfelek áttelepítése](#BKMK_MigrateClients)  

-   [Áttelepítés befejezése](#Complete_Migration)  

##  <a name="Create_Edit_migration_Jobs"></a> Áttelepítési feladatok létrehozása és szerkesztése  
 Az alábbi eljárások segítségével adatok áttelepítési feladatok létrehozására, a gyűjtemény alapú áttelepítési feladatok kizárási lista szerkesztése, állítson be megosztott terjesztési pontok és szerkesztheti az áttelepítési feladatok ütemezését.  

> [!NOTE]  
>  Áttelepítési feladat, amely áttelepíti a gyűjtemény létrehozásához az alábbi eljárás csak a Configuration Manager 2007 támogatott verzióját futtató forráshierarchia vonatkozik. A gyűjtemény alapú áttelepítési feladat típusa nem érhető el, ha a System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiából telepít át.  

#### <a name="create-a-migration-job-to-migrate-by-collections"></a>Gyűjtemények szerinti áttelepítéshez áttelepítési feladat létrehozása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **áttelepítési feladatok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **áttelepítési feladat létrehozása**.  

4.  Az a **általános** lap az áttelepítési feladat létrehozása varázsló, állítsa be a következőt, és válassza a **OK**:  

    -   Adjon meg nevet az áttelepítési feladathoz.  

    -   A **Feladat típusa** legördülő listában válassza a **Gyűjteményáttelepítés**elemet.  

5.  Az a **gyűjtemények kiválasztása** lapon állítsa be a következőt, és válassza a **következő**:  

    -   Jelölje ki az áttelepíteni kívánt gyűjteményeket.  

    -   Ha szeretné áttelepíteni csak gyűjtemények és az ezekhez a gyűjteményekhez társított objektumokat nem, törölje a jelet **a megadott gyűjteményekkel társított objektumok áttelepítése**. Törölje ezt a beállítást, ha a társított objektumokat nem települnek át a feladat, és 6 és 7 lépéseket kihagyhatja.  

6.  Az a **objektumok kijelölése** lapon, törölje a jelet, semmilyen objektumtípusokat, illetve konkrét elérhető objektumokat, amelyeknél nem szeretné áttelepíteni. Alapértelmezés szerint az összes társított objektumtípus és elérhető objektum ki van jelölve. Válasszon **következő**.  

7.  Az a **tartalom tulajdonosa** lapon rendelje hozzá a tartalmakat mindegyik felsorolt forráshelyről a célhierarchia valamelyik helyéhez, és válassza a **következő**.  

8.  Az a **biztonsági hatókör** lapon, válassza ki egy vagy több szerepköralapú adminisztrációs biztonsági hatókörök telepítse át az áttelepítési feladat, és válassza az objektumok hozzárendelése **következő**.  

9. Az a **Gyűjteménykorlátozás** lapon hoz létre egy gyűjteményt a céloldali hierarchiából a listán szereplő egyes gyűjtemények hatókörének korlátozása, és válassza a **következő**. Ha nincsenek gyűjtemények találhatók, válassza a **következő**.  

10. Az a **Helykódcsere** lapon adjon meg helykódot a célhierarchiából, cserélje le a Configuration Manager 2007 helykódot listán szereplő egyes gyűjtemények, és válassza ki, **következő**. Ha nincsenek gyűjtemények találhatók, válassza a **következő**.  

11. Az a **információk áttekintése** lapon, válassza ki **fájl mentése** a megjelenített információkat szeretné későbbi megtekintés mentéséhez. Amikor készen áll a folytatáshoz, **következő**.  

12. Az a **beállítások** oldalon, állítsa be, amikor fog futni az áttelepítési feladat, válassza ki az esetleges egyéb beállításokat, amelyekre szüksége van az áttelepítési feladat, és válassza a **következő**.  

13. Erősítse meg a beállításokat, majd fejezze be a varázslót.  

#### <a name="create-a-migration-job-to-migrate-by-objects"></a>Áttelepítési feladat áttelepítendő objektumok létrehozása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **áttelepítési feladatok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **áttelepítési feladat létrehozása**.  

4.  Az a **általános** lap az áttelepítési feladat létrehozása varázsló, állítsa be a következőt, és válassza **következő**:  

    -   Adjon meg nevet az áttelepítési feladathoz.  

    -   A **Feladat típusa** legördülő listában válassza az **Objektumáttelepítés**elemet.  

5.  Az **Objektumok kijelölése** lapon válassza ki az áttelepítendő objektumtípusokat. Alapértelmezés szerint a kiválasztott összes objektumtípusnál minden rendelkezésre álló objektum ki van jelölve.  

6.  Az a **tartalom tulajdonosa** lapon rendelje hozzá a tartalmakat mindegyik felsorolt forráshelyről a célhierarchia valamelyik helyéhez, és válassza a **következő**. Ha nincs Forráshelyek találhatók, válassza a **következő**.  

7.  Az a **biztonsági hatókör** lapon, válassza ki egy vagy több szerepköralapú felügyeleti biztonsági szerepet, amelyet hozzárendel az áttelepítési feladatban szereplő objektumokhoz, és válassza **következő**.  

8.  Az a **információk áttekintése** lapon, válassza ki **fájl mentése** a megjelenített információkat szeretné későbbi megtekintés mentéséhez. Amikor készen áll a folytatáshoz, **következő**.  

9. Az a **beállítások** lapon állítsa be, amikor az áttelepítési feladatot futtatja, és válassza ki az esetleges egyéb beállításokat, amelyekre szüksége van az áttelepítési feladathoz. Válassza a **következő**.  

10. Erősítse meg a beállításokat, majd fejezze be a varázslót.  

#### <a name="create-a-migration-job-to-migrate-changed-objects"></a>Módosított objektumok áttelepítése áttelepítési feladat létrehozása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **áttelepítési feladatok**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **áttelepítési feladat létrehozása**.  

4.  Az a **általános** lap az áttelepítési feladat létrehozása varázsló, állítsa be a következőt, és válassza a **következő**:  

    -   Adjon meg nevet az áttelepítési feladathoz.  

    -   Az a **típusú feladattal** legördülő listában válassza **áttelepítés után módosult objektumok**.  

5.  Az **Objektumok kijelölése** lapon válassza ki az áttelepítendő objektumtípusokat. Alapértelmezés szerint a kiválasztott összes objektumtípusnál minden rendelkezésre álló objektum ki van jelölve.  

6.  Az a **tartalom tulajdonosa** lapon rendelje hozzá a tartalmakat mindegyik felsorolt forráshelyről a célhierarchia valamelyik helyéhez, és válassza a **következő**. Ha nincs Forráshelyek találhatók, válassza a **következő**.  

7.  Az a **biztonsági hatókör** lapon, válassza ki egy vagy több szerepköralapú felügyeleti biztonsági szerepet, amelyet hozzárendel az áttelepítési feladatban szereplő objektumokhoz, és válassza **következő**.  

8.  Az a **információk áttekintése** lapon, válassza ki **fájl mentése** a megjelenített információkat szeretné későbbi megtekintés mentéséhez. Amikor készen áll a folytatáshoz, **következő**.  

9. Az a **beállítások** lapon állítsa be, amikor az áttelepítési feladatot futtatja, és válassza ki az esetleges egyéb beállításokat, az áttelepítési feladathoz szükséges. Az áttelepítési feladatok többi típusától eltérően ennek a feladatnak felül kell írnia a korábban áttelepített objektumokat a System Center Configuration Manager-adatbázisban. Válasszon **következő**.  

10. Hagyja jóvá a beállításokat, és majd a varázsló.  

###  <a name="BKMK_Modify_Exclusion_List"></a>Az áttelepítés kizárási listájának módosítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületen, válassza a **áttelepítési** a kizárási lista eléréséhez. A kizárási lista a **Forráshierarchia** vagy az **Áttelepítési feladatok** csomópontból is elérhető.  

3.  Az a **Home** lap a **áttelepítési** csoportjában válassza **kizárási lista szerkesztése**.  

4.  Az a **kizárási lista szerkesztése** párbeszédpanelen jelölje ki a kizárt objektumot, a kizárási listáról eltávolítandó, és válassza a kívánt **eltávolítása**.  

5.  Válasszon **OK** a módosítások mentéséhez és a szerkesztés befejezéséhez. Aktuális változtatások visszavonásához és az összes eltávolított objektum visszaállításához, válassza a **Mégse**, és válassza a **nem**. Ezzel a művelettel visszavonja az objektumok eltávolítását, és bezárja a **Kizárási lista szerkesztése** párbeszédpanelt.  

#### <a name="share-distribution-points-from-the-source-hierarchy"></a>Terjesztési pontok megosztása a forráshierarchiából  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  A a **felügyeleti** munkaterületen bontsa ki a **áttelepítés**, válassza a **forráshierarchia**, majd válassza ki a beállítani kívánt forráshelyet.  

3.  Az a **Home** lap a **forráshely** csoportjában válassza **konfigurálása**.  

4.  Az a **forráshely hitelesítő adatai** párbeszédpanelen jelölje ki **engedélyezése a terjesztési pont megosztását a forráshely kiszolgálója számára**, és válassza a **OK**.  

5.  Ha az adatgyűjtés befejezésekor dönt **Bezárás**.  

#### <a name="change-the-schedule-of-a-migration-job"></a>Áttelepítési feladat ütemezésének módosítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **áttelepítési feladatok**.  

3.  Válassza ki a módosítani kívánt áttelepítési feladat. Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Az áttelepítési feladat tulajdonságait, válassza ki a **beállítások** fülre, változtassa meg az áttelepítési feladat futtatásának időpontját, és válassza a **OK**.  

##  <a name="Run_Migration_Jobs"></a> Áttelepítési feladatok futtatása  
 A következő eljárás használatával futtathatók a még el nem indított áttelepítési feladatok.  


1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **áttelepítési feladatok**.  

3.  Válassza ki a futtatni kívánt áttelepítési feladat. Az a **Home** lap a **áttelepítési feladat** csoportjában válassza **Start**.  

4.  Válasszon **Igen** elindítja az áttelepítési feladatot.  

##  <a name="BKMK_ProcUpgrdSS"></a> Megosztott terjesztési pont frissítése vagy hozzárendelésének módosítása  
 Frissítse a Configuration Manager 2007-forráshelyről megosztott támogatott terjesztési pontot (vagy a System Center Configuration Manager-forráshelyről megosztott támogatott terjesztési pont ismételt hozzárendelése) kell lennie a célhierarchiában lévő terjesztési ponttá.  

> [!IMPORTANT]  
>  A Configuration Manager 2007 fiókirodai terjesztési pont frissítése előtt távolítsa el a Configuration Manager 2007-ügyfélszoftvert a fiókirodai terjesztési pont számítógépén. A Configuration Manager 2007 ügyfélszoftver telepítve van a terjesztési pont frissítésére tett kísérlet során, ha a frissítés sikertelen lesz, és korábban a fiókirodai terjesztési pontra központilag telepített tartalom eltávolítása a számítógépről.  

> [!CAUTION]  
>  Frissítése vagy hozzárendelésének megváltoztatásakor a megosztott terjesztési pont, a terjesztési pont helyrendszer szerepkör és a hely system számítógépén eltávolítva a forráshelyről, és terjesztési pontként hozzáadni a célhierarchiában kiválasztott helyen.  

#### <a name="upgrade-or-reassign-a-shared-distribution-point"></a>A megosztott terjesztési pont frissítése vagy átrendelése  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **forráshierarchia**.  

3.  Válassza ki a helyet, amelyikhez a terjesztési pontot szeretné frissíteni, válassza ki a **megosztott terjesztési pontok** fülre, és válassza ki a megfelelő terjesztési pontot, frissíteni vagy átrendelni kívánt.  

4.  Az a **terjesztési pont** lap a **terjesztési pont** csoportjában válassza **ismételt hozzárendelése**.  

5.  A megosztott terjesztési pont ismételt hozzárendelése varázsló beállításainak megadása, például telepíti egy új terjesztési pontot a célhierarchiában, de a következő kiegészítéssel:  

    -   Az a **tartalomátalakítás** lapon, olvassa el a meglévő tartalom átalakításához szükséges helyre vonatkozó útmutatást. Ezt követően a **Meghajtóbeállítások** oldalon a varázsló, ügyeljen arra, hogy a terjesztési ponthoz tartozó kijelölt meghajtó a szükséges méretű szabad lemezterület szükséges.  

6.  Hagyja jóvá a beállításokat, és majd a varázsló.  

##  <a name="Monitor_MIgration"></a> Az áttelepítési tevékenység figyelése az Áttelepítés munkaterületen  
 A Configuration Manager konzol segítségével kísérheti figyelemmel az áttelepítést.  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **áttelepítési feladatok**.  

3.  Válassza ki a figyelni kívánt áttelepítési feladat.  

4.  A kiválasztott áttelepítési feladatra vonatkozóan az adatokat és a feladat állapotát az **Összefoglalás** és az **Objektumok a feladatban**lapon tudja megtekinteni.  

##  <a name="BKMK_MigrateClients"></a> Ügyfelek áttelepítése  
 Miután telepít át adatokat, az ügyfelek hierarchiák közötti, de áttelepítésének befejezése előtt, tervezze meg az ügyfelek áttelepítését a célhierarchiába. Az ügyfelek hierarchiák közötti áttelepítése általában azt jelenti, a Configuration Manager ügyfélszoftver eltávolítása a számítógépről, hogy a forráshierarchiához hozzárendelt, és majd telepítése a Configuration Manager-ügyfélszoftvert a célhierarchiából. A célhierarchiából történő telepítéskor az ügyfelet az adott hierarchia egyik elsődleges helyéhez is hozzárendeli. További információk az áttelepítéssel ügyfelek esetében: [a System Center Configuration Manager ügyfelek áttelepítési stratégiájának tervezése](../../core/migration/planning-a-client-migration-strategy.md).  

##  <a name="Complete_Migration"></a>Áttelepítés befejezése  
 Ezzel az eljárással a forráshierarchiából történő áttelepítés befejezéséhez.  

1.  Kattintson a Configuration Manager konzol **felügyeleti**.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **áttelepítési**, és válassza a **forráshierarchia**.  

3.  A Configuration Manager 2007-forráshierarchia esetében jelöljön ki egy forráshelyet, a forráshierarchia alsó szintjén. A System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiájában válassza ki a rendelkezésre álló forráshelyet.  

4.  Az a **Home** lap a **karbantartás** csoportjában válassza **adatgyűjtés leállítása**.  

5.  Válasszon **Igen** gombbal erősítse meg a műveletet.  

6.  A Configuration Manager 2007 verziójú forráshierarchia mielőtt továbblép a következő lépéssel, ismételje meg a 3., 4, és 5. Nyissa meg a fenti lépéseket a hierarchia aljától a tetejéig alján, a hierarchia mindegyik helyén. A System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiát továbbra is a következő lépéssel.  

7.  Az a **Home** lap a **karbantartás** csoportjában válassza **áttelepítési adatok törlése**.  

8.  Az a **áttelepítési adatok törlése** párbeszédpanel, az a **forráshierarchia** legördülő listában válassza ki a helykódot és a forráshierarchia legfelső szintű hely helykiszolgálójára, és válassza **OK**.  

9. Válasszon **Igen** a forráshierarchia az áttelepítési folyamat befejezéséhez.  

