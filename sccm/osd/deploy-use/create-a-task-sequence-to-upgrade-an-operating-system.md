---
title: "Hozzon létre egy feladatütemezést az operációs rendszer verziófrissítéséhez |} Microsoft Docs"
description: "Feladatütemezések a System Center Configuration Manager automatikusan frissítheti az operációs rendszer Windows 10-es Windows 7 vagy újabb."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: 12
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7b13f3dea5a3ae413ca6b8150ec24e1632a4d4d
ms.openlocfilehash: e63b639836bc38a030a051e80db4b057ab75a0b0
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Hozzon létre egy feladatütemezést az operációs rendszerek a System Center Configuration Manager frissítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Feladatütemezések használatával a System Center Configuration Managerben az operációs rendszer automatikus frissítése a Windows 10 a célszámítógépet a Windows 7 vagy újabb. Létrehozhat egy feladatütemezést, amely az operációs rendszer lemezképének telepítése a célként megadott számítógéphez, és az esetleges egyéb tartalmakra, például alkalmazások vagy szoftverfrissítések telepítéséhez használni kívánt kívánt hivatkozik. A feladatütemezés egy operációs rendszer verziófrissítéséhez része a [Windows frissítése a legújabb verzióra](upgrade-windows-to-the-latest-version.md) forgatókönyv.  

##  <a name="BKMK_UpgradeOS"></a>Hozzon létre egy feladatütemezést az operációs rendszer verziófrissítéséhez  
 A számítógépeken az operációs rendszer frissítéséhez a Windows 10, hozzon létre egy feladatütemezést és kiválasztása **az operációs rendszer frissítése frissítési csomagból** a a feladatütemezés létrehozása varázsló. A varázsló hozzáadja az operációs rendszer frissítéséhez, szoftverfrissítések és alkalmazások telepítése a lépéseket. A feladatütemezés létrehozása előtt a következőket kell teljesülniük:  

-   **Kötelező**  

     - A Windows 10 [operációs rendszer verziófrissítő csomagjának](../get-started/manage-operating-system-upgrade-packages.md) a Configuration Manager konzol elérhetőnek kell lennie.  

-   **Kötelező (használat esetén)**  

    -   [Szoftverfrissítések](../../sum/get-started/synchronize-software-updates.md) szinkronizálni kell a Configuration Manager konzolon.  

    -   [Alkalmazások](../../apps/deploy-use/create-applications.md) hozzá kell adni a Configuration Manager konzolon.  

#### <a name="to-create-a-task-sequence-that-upgrades-an-operating-system"></a>Hozzon létre egy feladatütemezést, amely frissíti az operációs rendszer  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  A a **hozzon létre egy új feladatütemezést** kattintson **frissíteni az operációs rendszer verziófrissítő csomagjának**, és kattintson a **következő**.  

5.  A **Feladatütemezés adatai** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Feladatütemezés neve**: Adjon meg egy nevet, amely azonosítja a feladatütemezést.  

    -   **Leírás**: Adja meg a feladatütemezés által végrehajtandó feladat leírását.  

6.  Az a **a Windows verziófrissítésének elvégzése** lapon adja meg a következő beállításokat, és kattintson a **következő**.  

    -   **Frissítési csomag**: Adja meg az operációs rendszer frissítési forrásfájlokat tartalmazó frissítési csomagot. Ellenőrizheti, hogy megadta az információk alapján a megfelelő frissítési csomagot a **tulajdonságok** ablaktáblán. További információkért lásd: [operációs rendszer verziófrissítő csomagjainak kezelése](../get-started/manage-operating-system-upgrade-packages.md).  

    -   **Kiadásindexének**: Ha operációs rendszer több kiadásszáma elérhető a csomagban, válassza ki a kívánt kiadásszámot. Alapértelmezés szerint az első elem van kijelölve.  

    -   **Termékkulcs**: Adja meg a telepítendő Windows operációs rendszer termékkulcsát. Kódolt mennyiségi licenckulcsot és normál termékkulcsot egyaránt megadhat. Nem kódolt termékkulcs használata esetén mindegyik 5 karakterből álló csoportot kötőjellel (-) kell egymástól elválasztani. Példa: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. Ha a mennyiségi licences kiadásra frissít, a termékkulcs nincs szükség. Csak akkor kell termékkulcsot egy kereskedelmi Windows-kiadás frissítése esetén.  

7.  A **Frissítésekkel együtt** lapon adja meg, hogy milyen szoftverfrissítéseket szeretne telepíteni: a szükséges szoftverfrissítéseket, minden szoftverfrissítést, vagy egyet sem; azután kattintson a **Tovább**gombra. Ha a szoftverfrissítések telepítését választja, a Configuration Manager csak azokat a frissítéseket, amelyek telepíti a gyűjteményeket, amelyek a célszámítógép a tagja legyen.  

8.  Az **Alkalmazások telepítése** oldalon adja meg a célszámítógépen telepítendő alkalmazásokat, majd kattintson a **Tovább**gombra. Ha több alkalmazást ad meg, lehetősége van a folytatáshoz a feladatsorrendet is megadni, amennyiben egy adott alkalmazást nem sikerült telepíteni.  

9. Fejezze be a varázslót.  



## <a name="configure-pre-cache-content"></a>Előzetes konfigurálása
A feladatütemezés elérhető központi telepítéséhez 1702, verziójától kezdve, dönthet úgy, hogy az ügyfelek csak a kapcsolódó tartalom letöltése előtt a felhasználó telepíti a tartalmat az előzetes szolgáltatás használata.
> [!TIP]  
> Bevezetett 1702 verziójával, a előtti gyorsítótár egy előzetes verziójú funkció. Az engedélyezéshez, lásd: [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/pre-release-features).

Például tételezzük fel feladatütemezés központi telepítése Windows 10 helyi frissítési, csak egyetlen feladatütemezés szeretné, hogy az összes felhasználó számára, és több architektúrák és/vagy nyelveket. 1702, ha az elérhető központi telepítés létrehozásához, majd a felhasználó rákattint-es vagy korábbi **telepítése** a Szoftverközpontban, a tartalom adott időpontban tölti le. Ez biztosítja, hogy a további időt megkezdheti a telepítés előtt. Emellett minden, a feladatütemezésben hivatkozott tartalom letöltve. Ez magában foglalja az operációs rendszer verziófrissítő csomagjának összes nyelvekhez és architektúráinak megfelelően. Egy körülbelül 3 GB-nál, ha a letöltőcsomag Igen tekintélyes lehet.

Előzetes lehetővé teszi a beállítás lehetővé teszi az ügyfél csak a megfelelő tartalom letöltésére, amint azt a központi telepítés kap. Ezért, amikor a felhasználó kattint **telepítése** a Szoftverközpontban, készen áll a tartalmat, és a telepítés megkezdése gyorsan, mert a tartalom a helyi merevlemez-meghajtón.

### <a name="to-configure-the-pre-cache-feature"></a>Az előzetes szolgáltatás konfigurálása

1. Operációs rendszer adott architektúrák és nyelvek frissítési csomagokat hozzon létre. Az architektúra és nyelvi meg a **adatforrás** a csomag lapján. A nyelv, használja a decimális átalakítás (például 1033 az angol nyelvű tájékoztatáshoz decimális és 0x0409 megfelel a hexadecimális). További információkért lásd: [hozzon létre egy feladatütemezést az operációs rendszer verziófrissítéséhez](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    Az architektúra és nyelvi értékek segítségével felel meg a feladat feladatütemezési lépés feltételeket, amelyek annak meghatározásához, hogy az operációs rendszer verziófrissítő csomagjának előre gyorsítótárazza a következő lépésben létrehoz.
2. Hozzon létre egy feladatütemezést, a különböző nyelvekhez és architektúrák feltételes lépéseit. Például angol nyelvű létrehozhat egy lépést, a következőhöz hasonló:

    ![előtti gyorsítótár tulajdonságai](../media/precacheproperties2.png)

    ![előtti gyorsítótár beállításai](../media/precacheoptions2.png)  

3. A feladatütemezés központi telepítése. Az előzetes szolgáltatás számára konfigurálja a következőket:
    - Az a **általános** lapon jelölje be **előre letölteni a tartalmat a Feladatütemező**.
    - A a **központi telepítési beállítások** lapra, konfigurálja a feladatütemezést a **elérhető** a **célú**. Ha létrehoz egy **szükséges** központi telepítését, az előzetes funkciók nem működnek.
    - Az a **ütemezés** lapon, az a **ütemezni, amikor a központi telepítés rendelkezésre áll** beállításnál válassza ki a jövőben egy időpontot, amely az ügyfelek elegendő idő előre a tartalom gyorsítótárazása, mielőtt a központi telepítést szeretné elérhetővé tenni a felhasználók számára. Például beállíthatja az elérhetőséget 3 órát a jövőben hagyjon elegendő időt a tartalmat előre összeállított kell lennie.  
    - Az a **terjesztési pontok** lapon a **központi telepítési beállítások** beállításait. Ha a tartalom a felhasználó a telepítés megkezdése előtt nincsenek gyorsítótárazva az ügyfélen előre, ezeket a beállításokat használja.


### <a name="user-experience"></a>A felhasználói felületet
- Ha az ügyfél megkapja a központi telepítés házirendet, elindul, a tartalmat előre gyorsítótárazásához. Ez magában foglalja az összes hivatkozott tartalom (a többi csomag típus), és csak az operációs rendszer verziófrissítő csomagjának, amely megfelel az ügyfél a feltételek alapján, hogy megadta-e a feladatütemezés.
- Ha a központi telepítést szeretné elérhetővé tenni a felhasználóknak (beállítása a **ütemezés** lapon a központi telepítés), egy értesítés jeleníti meg tájékoztatják a felhasználókat az új központi telepítés kapcsolatos, és a központi telepítés látható lesz a Szoftverközpontban. A felhasználó megnyithatja a szoftverközpont, és kattintson a **telepítése** a telepítés elindításához.
- Ha a tartalom nem teljesen előre összeállított, akkor a megadott beállításokat fogja használni a **rendszerbe állítási beállításának** lapon. Azt javasoljuk, hogy nincs-e elegendő idő között a központi telepítés létrehozásakor és az idő, amelyben a központi telepítés felhasználók számára engedélyezése az ügyfelek elegendő idő előzetes gyorsítótárazása a tartalom elérhetővé válnak.



## <a name="download-package-content-task-sequence-step"></a>Töltse le a csomag tartalmának a feladatütemezési lépés  
 A [csomagtartalom letöltése](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) lépés előtt használható a **operációs rendszer verziófrissítésének elvégzése** . lépés: a következő esetekben:  

-   Egy frissítési feladatütemezést, amely használható x86 és a x64 platformot használ. Ezt úgy teheti meg, hogy a **Verziófrissítés előkészítése** csoportban két **Csomag tartalmának letöltése** lépést ad meg olyan feltételekkel, amelyek észlelik az ügyfél architektúráját, és csak az operációs rendszer megfelelő verziófrissítési csomagját töltik le. Az egyes **Csomag tartalmának letöltése** lépéseket konfigurálja ugyanazon változó használatára, és használja az **Operációs rendszer verziófrissítésének elvégzése** lépés adathordozó-útvonalának változóját.  

-   A megfelelő illesztőprogam-csomag dinamikus letöltéséhez használjon két **Csomag tartalmának letöltése** lépést olyan feltételekkel, amelyek észlelik az egyes illesztőprogram-csomagokhoz tartozó megfelelő hardvertípust. Az egyes **Csomag tartalmának letöltése** lépéseket konfigurálja ugyanazon változó használatára, és használja a változót az **Előkészített tartalom** értékként az **Operációs rendszer verziófrissítésének elvégzése** lépés illesztőprogramokra vonatkozó szakaszában.  

   > [!NOTE]
   > Több csomag esetén a Configuration Manager egy numerikus utótagot ad a változó nevét. Például ha tartalom % változót adja meg egyéni változóként, ez az összes hivatkozott tartalom tároló gyökérszintű (amely több csomag is lehet). A változóra egy későbbi lépésben, például az Operációs rendszer verziófrissítésének elvégzése lépésben való hivatkozáskor az egy numerikus utótaggal használható. A példa, tartalom01 % vagy % tartalom02 %, ahol a szám a sorrendben, amelyben a csomag szerepel ebben a lépésben felel meg.

## <a name="optional-post-processing-task-sequence-steps"></a>Választható utófeldolgozási feladatütemezési lépések  
 A feladatütemezés létrehozása után adja hozzá az ismert kompatibilitási problémákkal rendelkező alkalmazások eltávolítására szolgáló további lépéseket, vagy végezze el a számítógép újraindítása, a Windows 10-re frissítés sikeres utófeldolgozási műveletekhez. A feladatütemezés utófeldolgozás csoportjához adja hozzá ezeket a további lépéseket.  

> [!NOTE]  
>  Mivel ez a feladatütemezés nem lineáris, feltételek a lépéseket, amelyek hatással lehetnek a feladatütemezés, attól függően, hogy sikeresen frissítette-e az ügyfélszámítógép eredményeit, vagy ha szeretné visszaállítani az ügyfélszámítógép operációs rendszerre van az lépései.  

## <a name="optional-rollback-task-sequence-steps"></a>Választható visszaállítási feladatütemezési lépések  
 Ha probléma merül fel a frissítési folyamat, a számítógép újraindítása után, telepítő visszaállítja a verziófrissítést a korábbi operációs rendszerre, és a feladatütemezés során esetlegesen a visszavonás csoportban szereplő lépésekkel folytatódik. Miután létrehozta a feladatütemezést, a választható lépéseket a visszavonás csoportba is hozzáadhat.  

## <a name="folder-and-files-removed-after-computer-restart"></a>Mappa és a fájlok eltávolítása után a számítógép újraindítása  
 Ha a feladatütemezés egy operációs rendszer frissítéséhez a Windows 10 és a feladatütemezés további lépéseinek be nem fejeződik, a utófeldolgozás és visszaállítási parancsfájlok nem lesznek eltávolítva, a számítógép újraindításáig.  Ezek a parancsfájlok nem tartalmaznak bizalmas adatokat.  

