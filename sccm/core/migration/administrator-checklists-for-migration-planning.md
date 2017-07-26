---
title: "Áttelepítési Ellenőrzőlisták |} Microsoft Docs"
description: "Rendszergazdai ellenőrzőlista használata a System Center Configuration Manager áttelepítési stratégiájának tervezéséhez nyújtanak segítséget."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 295fdf07-93cc-490c-acdd-ce3ee88cb36f
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e6e8a18a8fc705c993177b3c5b4113a351a45a4
ms.openlocfilehash: 36f7c37e4da3f2bce64a25d266dae57d9fe98c36
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="administrator-checklists-for-migration-planning-in-system-center-configuration-manager"></a>Rendszergazdai ellenőrzőlisták a System Center Configuration Managerben végzett migrálás megtervezéséhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A következő rendszergazdai ellenőrzőlista használata áttelepítési stratégiájának tervezését segítheti a System Center Configuration Manager segítségével.

##  <a name="Checklist_Migraiton_Planning"></a>Rendszergazdai ellenőrzőlista az áttelepítés megtervezése  
 A következő ellenőrzőlista használható az áttelepítés előtti lépések tervezéséhez.  

-   **Hozzáférés az aktuális környezethez:**  

     Azonosítsa azokat az üzleti igényeket, amelyeknek a forráshierarchia megfelel, és alakítson ki olyan tervet, ami garantálja, hogy ezeknek az igényeknek a célhierarchia is megfeleljen a továbbiakban.  

-   **Tekintse át a megjelenő funkciókat és változtatásokat, hogy a Configuration Manager verziója, amely használja, és ezen információk használatával alakítsa ki a célhierarchiát:**  

    További információk: [A System Center Configuration Manager – Alapok](../../core/understand/fundamentals.md) és [A System Center Configuration Manager újdonságai](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).  


-   **Határozza meg a szerepköralapú felügyelethez használandó felügyeleti biztonsági modellt:**  

    További információkért lásd: [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../core/understand/fundamentals-of-role-based-administration.md).  

-   **A hálózat és az Active Directory topológiájának felmérése:** Tekintse át a létező tartománystruktúrát és hálózati topológiát, majd vegye figyelembe, hogy ez hogyan befolyásolja a hierarchia kialakítását és az áttelepítési feladatokat.  

-   **Véglegesítse a célhierarchia kialakítását:**  

    Döntsön a központi felügyeleti hely, az elsődleges helyek, a másodlagos helyek elhelyezéséről és a tartalomterjesztési lehetőségekről.  

-   **Képezze le a hierarchiát azokra a számítógépekre, helyek és helyrendszer-kiszolgálók a célhierarchiában használni:**  

    A számítógépek, amely helyek és helyrendszer-kiszolgálók a célhierarchiában használni, majd ellenőrizze, hogy rendelkezik-e elegendő kapacitással a jelenlegi és jövőbeni működési követelményeinek azonosítása.  

-   **Tervezze meg az objektumok áttelepítési stratégiáját:**  

    Többek között a helyhatárok, gyűjtemények, hirdetmények és központi telepítések különböző objektumok áttelepítéséhez igénybe vehető olyan áttelepítési feladatok használni szeretne. További információkért lásd: [áttelepítési feladatok típusai](../../core/migration/planning-a-migration-job-strategy.md#Types_of_Migration) a [egy feladat stratégiájának tervezése a System Center Configuration Managerben](../../core/migration/planning-a-migration-job-strategy.md)  

    A Configuration Manager csak a kiválasztott objektumok áttelepítése. Lehet, hogy át nem és, amelyre szüksége van a célhierarchiában lévő objektumok a célhierarchiában hozza létre újra.  

    Az áttelepíthető objektumok az áttelepítési feladatok konfigurálásakor megjelennek.  

-   **Tervezze meg az ügyfélszoftverek áttelepítési stratégiáját:**  

    Ennél az áttelepítésnél olyan megközelítéssel végezze a tervezést, amely korlátozza a hálózati sávszélességet és a kiszolgálóval szemben támasztott feldolgozási igényeket az ügyfélszoftveri információ célhierarchiába telepítésekor. Ügyfélszoftverek áttelepítési stratégiájának tervezésével kapcsolatban bővebben lásd: [a System Center Configuration Manager ügyfelek áttelepítési stratégiájának tervezése](../../core/migration/planning-a-client-migration-strategy.md).  

-   **Tervezze meg a leltári és megfelelőségi adatokat:**  

    A Configuration Manager nem támogatja áttelepítése Hardverleltár, szoftverleltár vagy kívánt konfigurálás-felügyeleti megfelelőségi adatainak a szoftverfrissítések és az ügyfelek számára.  

    Ehelyett miután az ügyfél a célhierarchiában áttelepül az új helyére és ezen konfigurálásokhoz házirendet kap, ezeket az információkat az ügyfél küldi el a hozzárendelt helyére. Ezzel a művelettel a cél helyadatbázisa az aktuális leltári és megfelelőségi adatokkal töltődik fel.  

-   **A forráshierarchiából történő áttelepítés befejezésének megtervezése:**  

    Döntse el, mikor lesznek áttelepítve az objektumok és az ügyféli adatok. Az áttelepítés befejezése után tervbe veheti a forráshierarchiában a helykiszolgálók üzemen kívül helyezését.  

##  <a name="Checklist_Hierarchy_for_migration"></a>Rendszergazdai ellenőrzőlista a hierarchiák áttelepítéséhez  
A következő ellenőrzőlisták az áttelepítés előtt lehetnek hasznosak a célhierarchia megtervezéséhez.  

-   **Válassza ki a célhierarchiában használni kívánt számítógépeket:**  

    A Configuration Manager nem támogatja a Configuration Manager 2007-infrastruktúrát helybeni frissítése. Ehelyett használja a áttelepítési áthelyezni az adatokat a Configuration Manager 2007 System Center Configuration Manager. Ehhez szükséges, hogy egymás melletti központi telepítés használata, és telepítse a System Center Configuration Manager az új számítógépekre.  

    Hasonlóképpen ha át egy másik System Center Configuration Manager-hierarchiából, telepítenie kell a egy új célhierarchiát, amelyik a forráshierarchia egymás melletti központi telepítés is.  

-   **Hozza létre a célhierarchiát:**  

    Felkészülés az áttelepítésre, telepítéséhez és konfigurálásához a System Center Configuration Manager célhierarchiába, amely egy elsődleges helyet tartalmaz. Példa:  

    -   Központi adminisztrációs hely telepítése, és telepítse a legalább egy alárendelt elsődlegest.  

    -   Telepítsen önálló elsődleges, ha nem tervezi, hogy egy központi adminisztrációs hellyel.  

-   **Ha szeretne áttelepíteni a szoftverfrissítésekre vonatkozó információt, konfigurálja a szoftverfrissítési pontot a célhierarchiában, és szinkronizálja a szoftverfrissítéseket:**  

    A szoftverfrissítéseket a célhierarchiában még azelőtt kell konfigurálni és szinkronizálni, mielőtt áttelepítené a forráshierarchiából a szoftverfrissítési információkat.  


-   **Telepítse és konfigurálja a további helyrendszerszerepköröket a célhierarchiában:**  

    Konfigurálja a helyrendszerszerepköröket és helyrendszereket, amikre szüksége van.  

-   **Ellenőrizze a műveletek működőképességét a célhierarchiában:**  

    Ellenőrizze a következőt:  

    -   A célhierarchia tartalmaz-e több helyet is, győződjön meg, hogy a helyek között működik-e az adatbázis-replikálás. Adatbázis-replikáció esetén nem alkalmazható az önálló elsődleges helyekre.  

    -   Ellenőrizze, hogy az összes telepített helyrendszerszerepkör működik.  

    -   Ellenőrizze, hogy a Configuration Manager-ügyfelek telepítése a rendeltetési hierarchiába sikeresen kommunikálhatnak a hozzárendelt hely.  


##  <a name="Checklisit_Migration"></a>Rendszergazdai ellenőrzőlista az áttelepítéshez  
A következő ellenőrzőlista használható az adatoknak a forráshierarchiából a célhierarchiába történő áttelepítéséhez.  

-   **Engedélyezze az áttelepítést a célhierarchiában:**  

    Megadhatja a forráshierarchia a forráshierarchia legfelső szintű helyén. További információ a forráshely [a System Center Configuration Managerben forráshierarchia stratégiájának tervezése](../../core/migration/planning-a-source-hierarchy-strategy.md).  

-   **Ha a forráshierarchia a Configuration Manager 2007 SP2 fut, válassza ki és konfiguráljon a forráshierarchiában további helyeket:**  

    Minden olyan további helyénél a szeretne adatokat gyűjteni a Configuration Manager 2007 SP2-forráshierarchiában konfigurálnia kell az adatgyűjtés hitelesítő adatait. Forráshelyekről konfigurálásakor a-adatgyűjtési folyamat azonnal megkezdődik, és továbbra is fennáll, az áttelepítési időszakban, amíg le nem állítják az adatgyűjtést, hogy a hely. Adatgyűjtés garantálja, hogy objektum áttelepíthető a forráshierarchiából, frissíteni vagy egy előző-adatgyűjtési folyamat után hozzá.

    > [!NOTE]  
    >  Ha a forráshierarchia futtatja a System Center 2012 Configuration Manager, vagy később, nem kell további Forráshelyek konfigurálására.  

-   **Konfigurálja a terjesztési pont megosztását:**  

    A terjesztési pontokat meg lehet osztani két hierarchia között, hogy az áttelepített objektumok tartalmát elérhetővé tegye a célhierarchiában lévő ügyfeleknek. Ez biztosítja, hogy ugyanazt a tartalmat a mindkét hierarchia ügyfelei számára elérhető marad, és hogy is megtarthassa a tartalmat, amíg leállította az adatgyűjtést, és az áttelepítés befejezéséhez.  

    Megosztott terjesztési pontokkal kapcsolatos információért lásd: [megosztja a terjesztési pontokat a forrás- és Célhierarchiák között](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) a [a System Center Configuration Managerben tartalom központi telepítési stratégiájának tervezése](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

-   **Hozzon létre és futtasson áttelepítési feladatokat a forráshierarchiában az ügyfelekhez társított objektumok áttelepítéséhez:**  

    Hozzon létre áttelepítési feladatokat az objektumok hierarchiák közötti áttelepítéséhez. Az egyes áttelepítési feladatokhoz szükséges konfigurálások eltérhetnek attól függően, hogy a feladat milyen adatokat telepít át.  

    Ha például tartalmat telepít át, a használt áttelepítési feladattól függetlenül, annak a tartalomnak a saját kezeléséhez a célhierarchiában helyet kell hozzárendelni. A hozzárendelt hely fogja elérni a tartalom eredeti forrásfájljának helyét, és ez a hely lesz a felelős a tartalomnak a célhierarchia terjesztési pontjaira való terjesztéséért is.  

    További információkért lásd: [létrehozása és szerkesztése a system center configuration manager áttelepítési feladatok](../../core/migration/operations-for-migration.md#Create_Edit_migration_Jobs) a [System Center Configuration Managerben történő áttelepítés műveletei](../../core/migration/operations-for-migration.md).  

-   **Az ügyfelek a célhierarchiára áttelepíteni:**  

    Az ügyfelek áttelepítési folyamata az áttelepítéshez választott forgatókönyvtől függ:  

    -   Egy ügyfél verziója nem ugyanaz, mint a célhierarchia rendelkező ügyfelek áttelepítésekor frissítenie kell az ügyfélszoftvert. A frissítés csak a jelenlegi Configuration Manager-ügyfél, majd az új ügyfélverzióra, amely megfelel az adott hely telepítésére eltávolítása.  

    -   Ha olyan ügyfeleket telepít át, amelyek ügyfélszoftveri verziója ugyanaz, mint a célhierarchiáé, nincs szükség szoftverfrissítésre vagy újratelepítésre. Ehelyett az ügyfél a célhierarchia elsődleges helyére változtatja a hozzárendelését.  

    Az ügyfélszoftver célhierarchiába áttelepítésekor az ügyfélszoftver társítva lesz azokkal az adataival, amelyeket előzőleg áttelepített a célhierarchiába.  

    További információk: [Ügyfélszoftverek áttelepítési stratégiájának tervezése a System Center Configuration Managerben](../../core/migration/planning-a-client-migration-strategy.md).  

-   **Frissítés, vagy a megosztott terjesztési pontok átrendelése:**  

    Ha már nem rendelkezik a forráshierarchiában található ügyfelek támogatására, a Configuration Manager 2007-forráshelyről megosztott terjesztési pontok frissítését, vagy a System Center 2012 Configuration Manager vagy a System Center Configuration Manager-forráshelyről megosztott terjesztési pontok átrendelése. A terjesztési pont frissítésekor vagy hozzárendelésének megváltoztatásakor a helyrendszerszerepkör át lesz téve a célhierarchia elsődleges helyére, és el lesz távolítva a forráshierarchiában a forráshelyről. Frissítése vagy hozzárendelésének megváltoztatásakor a megosztott terjesztési pont, a tartalom a terjesztési pont számítógépén marad, és nem kell újratelepíteni a tartalmat a célhierarchiában lévő terjesztési pontokra.  

    A Configuration Manager 2007 másodlagos helykiszolgálón közös elhelyezésű terjesztési pontot is lehet frissíteni. Ez eltávolítja a másodlagos helyet, és ennek eredményeként csak terjesztési pont lesz a célhierarchiában.  

    Megosztott terjesztési pontokkal kapcsolatos információért lásd: [megosztja a terjesztési pontokat a forrás- és Célhierarchiák között](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) a [a System Center Configuration Managerben tartalom központi telepítési stratégiájának tervezése](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

-   **Áttelepítés befejezése:**  

    Miután a forráshierarchiában minden helyről áttelepítette adatok és az ügyfelek és a megfelelő terjesztési pontokra frissít, áttelepítés befejezéséhez. Áttelepítés befejezéséhez leállította az adatgyűjtést a forráshierarchiában lévő összes forráshelyről. Ezt követően eltávolíthatja a nem szükséges áttelepítési információkat, és megszüntetheti a forráshierarchia infrastruktúrájának ilyen célú működését. További információ: [Áttelepítés befejezésének megtervezése a System Center Configuration Managerben](../../core/migration/planning-to-complete-migration.md).  

