---
title: "Hozzon létre egy feladatütemezést, a felhasználói állapot rögzítéséhez és visszaállításához |} Microsoft Docs"
description: "Használja a System Center Configuration Manager telepítő feladatütemezés rögzítéséhez és visszaállításához a felhasználóiállapot adatok operációsrendszer-telepítési helyzetekben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d566d85c-bf7a-40e7-8239-57640a1db5f4
caps.latest.revision: 7
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: fdfbdd1acb1190ca7de9cff2b4b7f916d8dc1272
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-to-capture-and-restore-user-state-in-system-center-configuration-manager"></a>Hozzon létre egy feladatütemezést, rögzítheti és visszaállíthatja a felhasználói állapotot a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használhatja a System Center Configuration Manager feladatütemezések rögzítheti és visszaállíthatja a felhasználói állapotadatokat olyan operációsrendszer-telepítési helyzetekben hol szeretné megőrizni az aktuális operációs rendszer felhasználói állapotát. A létrehozni kívánt feladatütemezés típusától függően előfordulhat, hogy egyes rögzítési és visszaállítási lépések hozzáadása automatikusan fog történni. Más esetekben előfordulhat, hogy manuálisan kell hozzáadnia a rögzítési és visszaállítási lépéseket a feladatütemezéshez. Ebben a témakörben megtalálhatja azokat a lépéseket, amelyeket a meglévő feladatütemezésekhez hozzá kell adnia a felhasználói állapotadatok rögzítéséhez és visszaállításához.  

##  <a name="BKMK_CaptureRestoreUserState"></a> Felhasználói állapotadatok rögzítése és helyreállítása  
 A felhasználói állapot rögzítéséhez és visszaállításához a következő lépéseket kell felvennie a feladatütemezésbe:  

-   **Állapot tárolásának igénylése**: Ez a lépés csak akkor, ha a felhasználói állapotot az állapotáttelepítési ponton tárolja van szükség.  

-   **Felhasználói állapot rögzítése**: Ez a lépés a felhasználói állapotadatokat rögzíti, és az állapotáttelepítési ponton vagy a helyi, hivatkozásokkal számítógépen tárolja azokat.  

-   **Felhasználói állapot visszaállítása**: Ebben a lépésben állítja vissza a felhasználói állapotadatokat a célszámítógépen. és képes lekérni a szükséges adatokat az állapotáttelepítési pontról vagy a célszámítógépről.  

-   **Állapot tárolásának felszabadítása**: Ez a lépés csak akkor, ha a felhasználói állapotot az állapotáttelepítési ponton tárolja van szükség. A lépés eltávolítja a felhasználói állapotadatokat az állapotáttelepítési pontról.  

 A felhasználói állapot rögzítéséhez és helyreállításához szükséges feladatütemezési lépések hozzáadásához kövesse az alábbi eljárásokat. Feladat feladatütemezések létrehozásával kapcsolatos további információkért lásd: [feladatok automatizálásához a feladatütemezések kezeléséhez](manage-task-sequences-to-automate-tasks.md).  

#### <a name="to-add-task-sequence-steps-to-capture-the-user-state"></a>Feladatütemezési lépések hozzáadása a felhasználói állapot rögzítéséhez  

1.  A **Feladatütemezés** listán jelöljön ki egy feladatütemezést, majd kattintson a **Szerkesztés**parancsra.  

2.  Ha állapotáttelepítési pontot használ a felhasználói állapot tárolására, vegye fel az **Állapot tárolásának igénylése** lépést a feladatütemezésbe. A **Feladatütemezés-szerkesztő** párbeszédpanelen kattintson a **Hozzáadás**gombra, mutasson a **Felhasználói állapot**elemre, majd kattintson az **Állapot tárolásának igénylése**lehetőségre. Adja meg az alábbi tulajdonságokat és beállításokat az **Állapot tárolásának igénylése** lépéshez, majd kattintson az **Alkalmaz**gombra.  

     A **Tulajdonságok** lapon adja meg az alábbi beállításokat:  

    -   Adja meg a lépés nevét és leírását.  

    -   Kattintson az **Állapot rögzítése a számítógépről**elemre.  

    -   Az **Ismételt kísérletek száma** mezőben adja meg, hogy a feladatütemezés hiba esetén hányszor tegyen kísérletet a felhasználói állapotadatok rögzítésére.  

    -   Az **Újrapróbálkozás késleltetése (másodperc)** mezőben adja meg, hogy a feladatütemezés hány másodpercet várjon, mielőtt újra megpróbálja rögzíteni az adatokat.  

    -   Válassza ki a **Ha a számítógépes fiók nem tud csatlakozni az állapottárolóhoz, használja a hálózati elérésre szolgáló fiókot** melletti jelölőnégyzetet, hogy adja meg, hogy a Configuration Manager által használt [hálózatelérési fiók](../../core/plan-design/hierarchy/manage-accounts-to-access-content.md#a-namebkmknaaa-network-access-account) az állapottárolóhoz való csatlakozás.  

     A **Beállítások** lapon adja meg az alábbi beállításokat:  

    -   Ha szeretné, hogy a feladatsor a következő lépéssel folytatódjon, ha ez a lépés sikertelen, jelölje be a **Folytatás hiba esetén** négyzetet.  

    -   Határozza meg azokat a feltételeket, amelyeknek teljesülniük kell ahhoz, hogy a feladatsor folytatódhasson hiba esetén.  

3.  A feladatütemezésbe vegye fel a **Felhasználói állapot rögzítése** lépést. A **Feladatütemezés-szerkesztő** párbeszédpanelen kattintson a **Hozzáadás**gombra, mutasson a **Felhasználói állapot**elemre, majd kattintson a **Felhasználói állapot rögzítése**lehetőségre. Adja meg az alábbi tulajdonságokat és beállításokat a **Felhasználói állapot rögzítése** lépéshez, majd kattintson az **OK**gombra.  

    > [!IMPORTANT]  
    >  Amikor hozzáadja ezt a lépést a feladatütemezéshez, állítsa be az **OSDStateStorePath** feladatütemezési változót is a felhasználói állapotadatok tárolási helyének meghatározásához. A felhasználói állapot helyi tárolása esetén ne adjon meg gyökérmappát, ez esetben ugyanis a feladatütemezés futtatása sikertelen lehet. A felhasználói adatok helyi tárolása esetén mindig mappát vagy almappát használjon. Ezen változóval kapcsolatos információkért lásd: [rögzítése felhasználói állapot feladatütemezési művelet változói](../understand/task-sequence-action-variables.md#BKMK_CaptureUserState).  

     A **Tulajdonságok** lapon adja meg az alábbi beállításokat:  

    -   Adja meg a lépés nevét és leírását.  

    -   Határozza meg azt a csomagot, amely a felhasználói állapotadatok rögzítésére szolgáló USMT-forrásfájlt tartalmazza.  

    -   Adja meg a rögzítendő felhasználói profilokat:  

        -   Az összes profil rögzítéséhez kattintson **Az összes felhasználói profil rögzítése a szokásos beállítások használatával** elemre.  

        -   A rögzítendő felhasználói profilok meghatározásához kattintson a **Felhasználói profilok rögzítésének testre szabása** elemre.  

    -   A **Részletes naplózás engedélyezése** elemmel meghatározhatja, hogy a rendszer mennyi információt írhat a naplófájlokba hiba esetén.  

    -   Jelölje be **A titkosított fájlrendszert (EFS) használó fájlok mellőzése**négyzetet.  

    -   Ha a **Másolás fájlrendszerelérés használatával** elemet választja, határozza meg az alábbi beállításokat:  

        -   **Továbbra is, ha egyes fájlok nem rögzíthetők**: Ezzel a beállítással a feladatütemezési lépéssel az áttelepítési folyamat folytatódik, még akkor is, ha egyes fájlok nem rögzíthetők. Ha letiltja ezt a beállítást, és valamelyik fájl nem rögzíthető, a feladatütemezési lépés sikertelen lesz. A beállítás alapértelmezés szerint engedélyezett.  

        -   **Helyi rögzítés fájlok másolása helyett hivatkozásokat használva**: Ez a beállítás lehetővé teszi, hogy az USMT 4.0 rögzített hivatkozásokat áttelepítési funkcióját használja. Ha USMT 4.0 előtti USMT-verziót használ, a rendszer figyelmen kívül hagyja ezt a beállítást.  

        -   **Üzemmódban végezze a rögzítést (csak Windows PE)**: Ez a beállítás lehetővé teszi a meglévő operációs rendszer elindítása nélkül rögzítheti a felhasználói állapotot a Windows PE környezetben. Ha USMT 4.0 előtti USMT-verziót használ, a rendszer figyelmen kívül hagyja ezt a beállítást.  

    -   Válassza a **Rögzítés a VSS-szolgáltatás (Volume Copy Shadow Service) használatával**lehetőséget. Ha USMT 4.0 előtti USMT-verziót használ, a rendszer figyelmen kívül hagyja ezt a beállítást.  

     A **Beállítások** lapon adja meg az alábbi beállításokat:  

    -   Ha szeretné, hogy a feladatsor a következő lépéssel folytatódjon, ha ez a lépés sikertelen, jelölje be a **Folytatás hiba esetén** négyzetet.  

    -   Határozza meg azokat a feltételeket, amelyeknek teljesülniük kell ahhoz, hogy a feladatsor folytatódhasson hiba esetén.  

4.  Ha a felhasználói állapot tárolásához állapotáttelepítési pontot használ, adja hozzá a [állapot tárolásának felszabadítása](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) lépést a feladatütemezéshez. A **Feladatütemezés szerkesztő** párbeszédpanelen kattintson a **Hozzáadás**elemre, mutasson a **Felhasználói állapot**elemre, majd kattintson az **Állapot tárolásának felszabadítása**gombra. Adja meg a következő tulajdonságokat és beállításokat az **Állapot tárolásának felszabadítása** lépéshez, majd kattintson az **OK**gombra.  

    > [!IMPORTANT]  
    >  A **Felhasználói állapot felszabadítása** lépés előtt futtatott feladatütemezési műveletnek sikeresnek kell lennie az **Állapot tárolásának felszabadítása** lépés megkezdése előtt.  

     A **Tulajdonságok** lapon adja meg lépés nevét és leírását.  

     A **Beállítások** lapon adja meg az alábbi beállításokat.  

    -   Ha szeretné, hogy a feladatsor a következő lépéssel folytatódjon, ha ez a lépés sikertelen, jelölje be a **Folytatás hiba esetén** négyzetet.  

    -   Határozza meg azokat a feltételeket, amelyeknek teljesülniük kell ahhoz, hogy a feladatütemezés folytatódhasson hiba esetén.  

 Telepítse ezt a feladatütemezést, ha szeretné rögzíteni a felhasználói állapotot egy célszámítógépen. További információ a feladatütemezések központi telepítéséről: [feladatütemezés központi telepítése](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

#### <a name="to-add-task-sequence-steps-to-restore-the-user-state"></a>Feladatütemezési lépések hozzáadása a felhasználói állapot visszaállításához  

1.  A **Feladatütemezés** listán jelöljön ki egy feladatütemezést, majd kattintson a **Szerkesztés**parancsra.  

2.  Adja hozzá a [felhasználói állapot visszaállítása](../understand/task-sequence-steps.md#BKMK_RestoreUserState) lépést a feladatütemezéshez. A **Feladatütemezés szerkesztő** párbeszédpanelen kattintson a **Hozzáadás**elemre, mutasson a **Felhasználói állapot**elemre, majd kattintson a **Felhasználói állapot visszaállítása**gombra. Ezzel a lépéssel kapcsolat jön létre az állapotáttelepítési ponttal. Adja meg a következő tulajdonságokat és beállításokat a **Felhasználói állapot visszaállítása** lépéshez, majd kattintson az **OK**gombra.  

     A **Tulajdonságok** lapon adja meg az alábbi tulajdonságokat:  

    -   Adja meg a lépés nevét és leírását.  

    -   Adja meg az USMT-t tartalmazó csomagot a felhasználói állapot adatainak visszaállításához.  

    -   Adja meg a visszaállítandó felhasználói profilokat:  

        -   Kattintson a **Az összes rögzített felhasználói profil visszaállítása a szokásos beállításokkal** elemre az összes felhasználói profil visszaállításához.  

        -   Kattintson a **Felhasználói profil rögzítésének testreszabása** elemre egyedi felhasználói profilok visszaállításához.  

    -   Válassza a **Helyi számítógép-felhasználói profilok visszaállítása** elemet ahhoz, hogy új jelszót adjon meg a visszaállított profilokhoz. Helyi profilokhoz tartozó jelszavakat nem telepíthet át.  

        > [!NOTE]  
        >  Ha rendelkezik helyi felhasználói fiókokkal, és használja a [felhasználói állapot rögzítése](../understand/task-sequence-steps.md#BKMK_CaptureUserState) lépést, valamint kiválasztja **összes felhasználói profil rögzítése a szokásos beállításokkal**, ki kell választania a **helyi számítógép-felhasználói profilok visszaállítása** beállítást azokban a [felhasználói állapot visszaállítása](../understand/task-sequence-steps.md#BKMK_RestoreUserState) lépés vagy a feladatütemezés sikertelen lesz.  

    -   Válassza a **Folytassa, ha egyes fájlok nem állíthatók vissza** lépést ahhoz, hogy a **Felhasználói állapot visszaállítása** lépés folytatassa a műveletet, ha egy fájl nem állítható vissza.  

         Ha a felhasználói állapotot helyi hivatkozások használatával tárolja, és a visszaállítás sikertelen, a rendszergazda felhasználó manuálisan törölheti az adatok tárolásához létrehozott rögzített hivatkozásokat, vagy a feladatütemezés futtatni tudja az USMTUtils eszközt. Ha törléséhez az usmtutils eszközt használja, vegye fel a [számítógép újraindítása](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer) lépést az USMTUtils futtatása után.  

    -   A **Részletes naplózás engedélyezése** elemmel meghatározhatja, hogy a rendszer mennyi információt írhat a naplófájlokba hiba esetén.  

     A **Beállítások** lapon adja meg az alábbi beállításokat:  

    -   Ha szeretné, hogy a feladatsor a következő lépéssel folytatódjon, ha ez a lépés sikertelen, jelölje be a **Folytatás hiba esetén** négyzetet.  

    -   Határozza meg azokat a feltételeket, amelyeknek teljesülniük kell ahhoz, hogy a feladatsor folytatódhasson hiba esetén.  

3.  Ha a felhasználói állapot tárolásához állapotáttelepítési pontot használ, adja hozzá a [állapot tárolásának felszabadítása](../understand/task-sequence-steps.md#BKMK_ReleaseStateStore) lépést a feladatütemezéshez. A **Feladatütemezés szerkesztő** párbeszédpanelen kattintson a **Hozzáadás**elemre, mutasson a **Felhasználói állapot**elemre, majd kattintson az **Állapot tárolásának felszabadítása**gombra. Adja meg a következő tulajdonságokat és beállításokat az **Állapot tárolásának felszabadítása** lépéshez, majd kattintson az **OK**gombra.  

    > [!IMPORTANT]  
    >  A **Felhasználói állapot felszabadítása** lépés előtt futtatott feladatütemezési műveletnek sikeresnek kell lennie az **Állapot tárolásának felszabadítása** lépés megkezdése előtt.  

     A **Tulajdonságok** lapon adja meg lépés nevét és leírását.  

     A **Beállítások** lapon adja meg az alábbi beállításokat.  

    -   Ha szeretné, hogy a feladatsor a következő lépéssel folytatódjon, ha ez a lépés sikertelen, jelölje be a **Folytatás hiba esetén** négyzetet.  

    -   Határozza meg azokat a feltételeket, amelyeknek teljesülniük kell ahhoz, hogy a feladatütemezés folytatódhasson hiba esetén.  

 Központilag telepítse ezt a feladatütemezést, a célszámítógépen lévő felhasználói adatok visszaállításához. További információ a feladatütemezések központi telepítéséről: [feladatütemezés központi telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

## <a name="next-steps"></a>További lépések
[A feladatütemezés központi telepítésének figyelése](monitor-operating-system-deployments.md#BKMK_TSDeployStatus)

