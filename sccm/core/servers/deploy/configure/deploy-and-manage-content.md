---
title: "Telepítse központilag a tartalmakat |} Microsoft Docs"
description: "Terjesztési pontok telepítése a System Center Configuration Manager, után ez hogyan elkezdheti a tartalom telepítéséért."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d50dcca0-4419-449d-a487-73abcadf328f
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 36b08285ef78d0acb9ba9c44abe2d57e311d44b3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="deploy-and-manage-content-for-system-center-configuration-manager"></a>Központi telepítése és a tartalomkezelésről a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Terjesztési pontok telepítése a System Center Configuration Manager, után elkezdheti a tartalom telepítéséért. Általában tartalmat a terjesztési pontokra továbbítani a hálózaton, de létezik-e más beállítások megszerezni a tartalmat a terjesztési pontokra. Miután tartalmat egy terjesztési pontra, frissítése, újraterjeszteni, távolítsa el, és ellenőrizze, hogy a tartalmat a terjesztési pontokon.  

##  <a name="bkmk_distribute"></a>Tartalom terjesztése  
 Általában terjeszt tartalmat a terjesztési pontokra, hogy az ügyfélszámítógépek számára elérhető. (A kivételt a használata esetén az igény szerinti tartalomterjesztést az egy adott központi telepítéshez.)  Tartalom terjesztésekor a Configuration Manager csomagban másolja a tartalomfájlokat, és majd a csomagot a terjesztési pontra terjeszti. Tartalomtípus terjeszthető, típusok a következők:  

-   Alkalmazás központi telepítési típusok  

-   Csomagok  

-   Központi telepítési csomagok  

-   Illesztőprogram-csomagok  

-   Operációsrendszer-lemezképek  

-   Operációs rendszerek telepítőcsomagjai  

-   Rendszerindító lemezképek  

-   Feladatütemezések  

Amikor egy alkalmazás központi telepítési típusát vagy központi telepítési csomagot, például a forrásfájlokat tartalmazó csomagot hoz létre a helyet, amelyen a csomag létrehozásakor a csomag tartalomforrásának tulajdonosává válik. A Configuration Manager másolja a forrásfájlokat a tartalomtár a helykiszolgálón, amely a csomag tartalomforrásának tulajdonosa az objektumhoz megadott forrásfájl útvonaláról.  A Configuration Manager, majd replikálja az információt a további helyeket. (Lásd: [a tartalomtár](../../../../core/plan-design/hierarchy/the-content-library.md) további információkat arról.)  

A következő eljárás használatával terjesztheti a tartalmat a terjesztési pontokra.  

#### <a name="to-distribute-content-on-distribution-points"></a>A terjesztési pontokon a tartalom terjesztése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületen jelölje ki az alábbi lépések egyikét a terjeszteni kívánt tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés** > **alkalmazások**, majd válassza ki a terjeszteni kívánt alkalmazásokat.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés** >  **csomagok**, majd válassza ki a terjeszteni kívánt csomagokat.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések** >  **központi telepítési csomagok**, majd válassza ki a terjeszteni kívánt központi telepítési csomagokat.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek** >  **illesztőprogram-csomagok**, majd válassza ki a terjeszteni kívánt illesztőprogram-csomagokat.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek** >  **operációsrendszer-lemezképek**, majd válassza ki a terjeszteni kívánt operációsrendszer-lemezképek.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek** > **operációs rendszerek telepítőcsomagjai**, majd válassza ki a terjeszteni kívánt operációsrendszer-telepítőcsomagokat.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek** >  **rendszerindító lemezképek**, majd válassza ki a terjeszteni kívánt rendszerindító lemezképeket.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek** >  **feladatütemezések**, és válassza ki a terjeszteni kívánt feladatütemezést. Habár a feladatütemezések nem rendelkeznek tartalommal, kapcsolódó tartalom függőségeinek, terjesztett.  

        > [!NOTE]  
        >  Ha módosítja a feladatütemezést, újra kell terjesztenie a tartalmat.  

3.  A **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Tartalom terjesztése**elemre. A tartalom terjesztése varázsló megnyitása.  

4.  Az a **általános** lapon, győződjön meg arról, hogy a felsorolt tartalom megfelel-e a használni kívánt terjesztése, válassza ki, hogy a Configuration Manager észleléséhez tartalomfüggőségeket, ezt a kiválasztott tartalomhoz kapcsolódó, és adja a függőségeket a terjesztéshez, majd **következő**.  

    > [!NOTE]  
    >  Lehetősége van a konfigurálása a **társított tartalom függőségeinek észlelése és hozzáadása ehhez a terjesztéshez** beállítás csak az alkalmazás tartalomtípusa. A Configuration Manager automatikusan konfigurálja ezt a beállítást a feladatütemezésekhez, és nem módosítható.  

5.  Az a **tartalom** lapon, ha megjelenik, győződjön meg arról, hogy a felsorolt tartalom megfelel-e a terjeszteni, és kattintson a kívánt **következő**.  

    > [!NOTE]  
    >  A **tartalom** lap jelenik meg, csak ha a **társított tartalom függőségeinek észlelése és hozzáadása ehhez a terjesztéshez** beállítás ki van választva a **általános** a varázsló.  

6.  Az a **tartalom célhelye** kattintson **Hozzáadás**, az alábbi lehetőségek közül választhat, és hajtsa végre a megfelelő lépést:  

    -   **Gyűjtemények**: Válassza ki **Felhasználógyűjtemények** vagy **Eszközgyűjtemények**, kattintson az egy vagy több terjesztésipont-csoporthoz hozzárendelt gyűjteményre, majd **OK**.  

        > [!NOTE]  
        >  Csak a terjesztésipont-csoporthoz társított gyűjteményeket. További információ a gyűjtemények társítása a terjesztésipont-csoportok: [terjesztésipont-csoportok kezelése](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) a a [telepítése és a terjesztési pontok konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) témakör.  

    -   **Terjesztési pont**: Válasszon egy meglévő terjesztési pontot, és kattintson **OK**. Nem jelennek meg, amelyek korábban megkapták a tartalmat terjesztési pontokra.  

    -   **Terjesztésipont-csoport**: Válasszon egy meglévő terjesztésipont-csoportot, és kattintson **OK**. Terjesztésipont-csoportokat, amelyek korábban megkapták a tartalmat nem jelennek meg.  

    Amikor befejezte a tartalom célhelyeinek, kattintson a **következő**.  

7.  Az a **összegzés** lapon, a folytatás előtt, tekintse át a terjesztés beállításait. Terjessze a tartalmat a kiválasztott célhelyekre, kattintson a **következő**.  

8.  A **folyamatban** lapon látható a terjesztés előrehaladásának állapota.  

9. A **megerősítő** lapon megjelenik, hogy a tartalmat sikerült-e hozzárendelni a pontokhoz. A tartalomterjesztés megfigyeléséről lásd: [figyelése a System Center Configuration Managerrel terjesztett tartalom](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

##  <a name="bkmk_prestage"></a>Előkészített tartalom használata  
 Akkor is készíthet elő tartalomfájlokat az alkalmazások és a csomagok:  

-   A Configuration Manager konzolon válassza a tartalom kell, és ezután a **manuálisan előkészített tartalomfájl létrehozása varázsló** egy tömörített, manuálisan előkészített tartalomfájl létrehozásához, amely tartalmazza a fájlok és a kiválasztott tartalomhoz kapcsolódó metaadatokkal.  

-   Ezután kézzel importálhatja helykiszolgálón, másodlagos hely, a tartalmat, vagy terjesztési ponton.  

-   Amikor a manuálisan előkészített tartalomfájlt helykiszolgálón importálja, a tartalomfájlok a helykiszolgálón lévő tartalomtárba hozzá, és regisztrálja a helykiszolgáló adatbázisából.  

-   Amikor a manuálisan előkészített tartalomfájlt terjesztési ponton importálja, a tartalomfájlokat a terjesztési ponton lévő tartalomtárba kerülnek, és egy állapotüzenetet küld a helykiszolgálónak, amelyben arról tájékoztatja a helyet, hogy a tartalom elérhető a terjesztési ponton.  

**Korlátozások és megfontolások az előzetesen beállított tartalomhoz:**  

-   **Ha a terjesztési pont a helykiszolgálón található**, ne engedélyezze a terjesztési pontot manuálisan előkészített tartalomhoz. Használja ezt az eljárást a [a terjesztési pont a helykiszolgálón a tartalom manuális előkészítése](#bkmk_dpsiteserver).  

-   **Ha a terjesztési pont lekéréses terjesztési pontként van konfigurálva**, ne engedélyezze a terjesztési pontot manuálisan előkészített tartalomhoz. A terjesztési pont manuális előkészítési konfiguráció felülírja a lekéréses terjesztési pont konfigurációját. A manuálisan előkészített tartalomhoz konfigurált lekéréses terjesztési pontok kéri le a tartalmat a forrásként szolgáló terjesztési pontról, és nem fogad tartalmat a helykiszolgálón.  

-   **A tartalomtárat kell létrehozni a terjesztési ponton, mielőtt előkészíthet tartalmat a terjesztési pontra**. Tartalom terjesztése a hálózaton legalább egy alkalommal, mielőtt a manuálisan előkészített tartalmat a terjesztési pontra.  

-   **Ha manuálisan előkészített tartalmat egy hosszú elérési úttal rendelkező csomag** (például több mint 140 karakter), a tartalom kibontása parancssori eszközt lehetséges, hogy nem sikerült kibontani a kérdéses csomag tartalmát a tartalomtárba.  

További információt a tartalomfájlok előkészítésének idejéről,: *előzetesen beállított tartalom* a a [hálózati sávszélesség szabályozása a Tartalomkezelés](/sccm/core/plan-design/hierarchy/manage-network-bandwidth) témakör.  

Az alábbi szakaszok segítségével előkészítheti a tartalmakat.  

###  <a name="BKMK_CreatePrestagedContentFile"></a>1. lépés: A manuálisan előkészített tartalomfájl létrehozása  
 Létrehozhat egy tömörített, manuálisan előkészített tartalomfájlt, amely tartalmazza a fájlok és a a Configuration Manager konzolt a kiválasztott tartalomhoz kapcsolódó metaadatokkal. A következő eljárás segítségével létrehozhat egy manuálisan előkészített tartalomfájlt.  

##### <a name="to-create-a-prestaged-content-file"></a>A manuálisan előkészített tartalomfájl létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületen jelölje ki az alábbi lépések egyikét a manuálisan előkészíteni kívánt tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés**, kattintson a **alkalmazások**, majd válassza ki a manuálisan előkészíteni kívánt alkalmazásokat.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés**, kattintson a **csomagok**, majd válassza ki a manuálisan előkészíteni kívánt csomagokat.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek**, kattintson a **illesztőprogram-csomagok**, majd válassza ki a manuálisan előkészíteni kívánt illesztőprogram-csomagokat.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek**, kattintson a **operációsrendszer-lemezképek**, majd válassza ki a manuálisan előkészíteni kívánt operációsrendszer-lemezképek.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek**, kattintson a **operációs rendszerek telepítőcsomagjai**, majd válassza ki a manuálisan előkészíteni kívánt operációsrendszer-telepítőcsomagokat.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek**, kattintson a **rendszerindító lemezképek**, majd válassza ki a manuálisan előkészíteni kívánt rendszerindító lemezképeket.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek**, kattintson a **feladatütemezések**, és válassza ki a manuálisan előkészíteni kívánt feladatütemezést.  

3.  Az a **Home** lap a **telepítési** csoportjában kattintson a **manuálisan előkészített tartalomfájl létrehozása**. A manuálisan előkészített tartalom fájl megnyílik létrehozása varázsló.  

    > [!NOTE]  
    >  **Alkalmazások esetében:** Az a **Home** lap a **alkalmazás** csoportjában kattintson a **manuálisan előkészített tartalomfájl létrehozása**.  
    >   
    >  **Csomagok esetében:** Az a **Home** lap a &lt; *csomagnév*> csoportjában kattintson a **manuálisan előkészített tartalomfájl létrehozása**.  

4.  Az a **általános** kattintson **Tallózás**, válassza ki a manuálisan előkészített tartalomfájl helyét, adja meg a fájl nevét, és kattintson **mentése**. Elsődleges hely kiszolgálóin, a másodlagos Helykiszolgálók vagy a terjesztési pontokat a manuálisan előkészített tartalomfájlt a tartalom és metaadatok importálásához használhatja.  

5.  Alkalmazások esetében válassza ki **minden függőség exportálása** szeretné, hogy a Configuration Manager észlelése és hozzáadása a manuálisan előkészített tartalomfájlt az alkalmazáshoz kapcsolódó függőségeket. Alapértelmezés szerint ez a beállítás be van jelölve.  

6.  A **rendszergazdai megjegyzések**, és észrevételeket fűzhet a manuálisan előkészített tartalomfájl, majd kattintson **következő**.  

7.  Az a **tartalom** lapon, győződjön meg arról, hogy a felsorolt tartalom megfelel-e a manuálisan előkészített tartalomfájlhoz hozzáadni, és kattintson a kívánt **következő**.  

8.  Az a **tartalom helye** adja meg azokat a terjesztési pontokon, ahonnan beolvasni a tartalomfájlokat a manuálisan előkészített tartalomfájlhoz. Kiválaszthatja, hogy a tartalom lekéréséhez egynél több terjesztési pontot. A terjesztési pontokon a tartalom helye szakaszban találhatók. A **tartalom** oszlop jeleníti meg, hogy hány a kiválasztott csomagok vagy alkalmazás érhető el minden egyes terjesztési ponton. A Configuration Manager kezdődik-e az első terjesztési pontot a listában, és a kiválasztott tartalom lekérése céljából, és majd lefelé halad a listában a manuálisan előkészített tartalomfájlhoz szükséges többi tartalom lekéréséhez. Kattintson a **fel** vagy **le** módosíthatja a terjesztési pontok fontossági sorrendjét. Ha a listában a terjesztési pontok nem tartalmazzák az összes kiválasztott tartalmat, hozzá kell adnia a listát, amely a tartalmat vagy a varázslóból való kilépéshez, terjessze a tartalmat legalább egy terjesztési pontra, és indítsa újra a varázslót terjesztési pontok.  

9. Az a **összegzés** lapon, erősítse meg az adatokat. Lépjen vissza az előző lapokra, és a módosításokat. Kattintson a **tovább** a manuálisan előkészített tartalomfájl létrehozásához.  

10. A **folyamatban** lap megjeleníti a manuálisan előkészített tartalomfájlhoz hozzáadott tartalmat.  

11. Az a **befejezési** lapon ellenőrizze, hogy a manuálisan előkészített tartalomfájl létrehozása sikeres volt, és kattintson a **Bezárás**.  

###  <a name="BKMK_AssignContentToDistributionPoint"></a>2. lépés: A tartalom hozzárendelése terjesztési pontokhoz  
 A tartalomfájl előkészítését követően rendelje hozzá a tartalmat a terjesztési pontokra.  

> [!NOTE]  
>  Amikor egy manuálisan előkészített tartalomfájlt a tartalomtár helykiszolgálón való helyreállításához használja, és nem kell előkészítenie a tartalomfájlokat egy terjesztési ponton, kihagyhatja ezt az eljárást.  

 A következő eljárással a manuálisan előkészített tartalomfájlból a tartalom hozzárendelése terjesztési pontokhoz.  

> [!IMPORTANT]  
>  Győződjön meg arról, hogy a manuálisan előkészíteni kívánt terjesztési pontok előkészített terjesztési pontként vannak-e konfigurálva, vagy az, hogy a tartalom van terjesztve a terjesztési pontokat a hálózaton keresztül.  

##### <a name="to-assign-the-content-to-distribution-points"></a>A tartalom hozzárendelése terjesztési pontok  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületet, jelölje ki az alábbi lépések, amely a manuálisan előkészített tartalomfájl létrehozásakor kiválasztott tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés**, kattintson a **alkalmazások**, majd válassza ki az előkészített alkalmazásokat.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés**, kattintson a **csomagok**, majd válassza ki az előkészített csomagokat.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések**, kattintson a **központi telepítési csomagok**, majd válassza ki az előkészített központi telepítési csomagokat.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek**, kattintson a **illesztőprogram-csomagok**, majd válassza ki az előkészített illesztőprogram-csomagokat.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek**, kattintson a **operációsrendszer-lemezképek**, majd válassza ki az előkészített operációsrendszer-lemezképeket.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek**, kattintson a **operációs rendszerek telepítőcsomagjai**, majd válassza ki az előkészített operációsrendszer-telepítőcsomagokat.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek**, kattintson a **rendszerindító lemezképek**, majd válassza ki az előkészített rendszerindító lemezképeket.  

3.  A **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Tartalom terjesztése**elemre. A tartalom terjesztése varázsló megnyitása.  

4.  Az a **általános** lapon, győződjön meg arról, hogy a felsorolt tartalom megfelel-e a manuálisan előkészített tartalommal, válassza ki, hogy a Configuration Manager észleléséhez tartalomfüggőségeket, ezt a kiválasztott tartalomhoz kapcsolódó, és adja a függőségeket a terjesztéshez, majd **következő**.  

    > [!NOTE]  
    >  Lehetősége van a konfigurálása a **társított tartalom függőségeinek észlelése és hozzáadása ehhez a terjesztéshez** beállítás csak az alkalmazás tartalomtípusa. A Configuration Manager automatikusan konfigurálja ezt a beállítást a feladatütemezésekhez, és nem módosítható.  

5.  Az a **tartalom** lapon, ha jelenik meg, győződjön meg arról, hogy a felsorolt tartalom megfelel-e a terjeszteni, és kattintson a kívánt **következő**.  

    > [!NOTE]  
    >  A **tartalom** lap jelenik meg, csak ha a **társított tartalom függőségeinek észlelése és hozzáadása ehhez a terjesztéshez** beállítás ki van választva a **általános** a varázsló.  

6.  Az a **tartalom célhelye** kattintson **Hozzáadás**, válasszon egyet az alábbi, amelyek tartalmazzák az előkészítendő terjesztési pontokat, és hajtsa végre a megfelelő lépést:  

    -   **Gyűjtemények**: Válassza ki **Felhasználógyűjtemények** vagy **Eszközgyűjtemények**, kattintson az egy vagy több terjesztésipont-csoporthoz hozzárendelt gyűjteményre, majd **OK**.  

        > [!NOTE]  
        >  Csak a terjesztésipont-csoporthoz társított gyűjteményeket.  További információkért lásd: [terjesztésipont-csoportok kezelése](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) a a [telepíteni és konfigurálni a terjesztési pontokat a System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) témakör.  

    -   **Terjesztési pont**: Válasszon egy meglévő terjesztési pontot, és kattintson **OK**. Nem jelennek meg, amelyek korábban megkapták a tartalmat terjesztési pontokra.  

    -   **Terjesztésipont-csoport**: Válasszon egy meglévő terjesztésipont-csoportot, és kattintson **OK**. Terjesztésipont-csoportokat, amelyek korábban megkapták a tartalmat nem jelennek meg.  

    Amikor befejezte a tartalom célhelyeinek, kattintson a **következő**.  

7.  Az a **összegzés** lapon, a folytatás előtt, tekintse át a terjesztés beállításait. Terjessze a tartalmat a kiválasztott célhelyekre, kattintson a **következő**.  

8.  A **folyamatban** lapon látható a terjesztés előrehaladásának állapota.  

9. A **megerősítő** lap megjeleníti-e a tartalmat sikerült-e hozzárendelni a terjesztési pontokra. A tartalomterjesztés megfigyeléséről lásd: [figyelése a System Center Configuration Managerrel terjesztett tartalom](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

###  <a name="BKMK_ExportContentFromPrestagedContentFile"></a>3. lépés: A tartalom kibontása a manuálisan előkészített tartalomfájlból  
 Miután a manuálisan előkészített tartalomfájl létrehozása, és rendelje hozzá a tartalmat a terjesztési pontokra, nyerhet a helykiszolgálón vagy terjesztési ponton lévő tartalomtárba tartalomfájlokat. Általában akkor tesznek a manuálisan előkészített tartalomfájlt hordozható meghajtóra, például USB-meghajtóra vagy lemezre szokás írni tartalom adathordozóra, például DVD-ről, és annak érhető el a tartalmat igénylő helykiszolgáló vagy terjesztési pont helyén.  

 A következő eljárással manuálisan exportálhatók a tartalomfájlok a manuálisan előkészített tartalomfájlból a tartalom kibontása parancssori eszköz használatával.  

> [!IMPORTANT]  
>  Ha a tartalom kibontása parancssori eszközt futtatja, az eszköz létrehoz egy ideiglenes fájlt, mivel az hozza létre a manuálisan előkészített tartalomfájl. Ezután másolja a fájlt a célmappa, és törli az ideiglenes fájlt. A sikertelen vagy elég szabad hely az ideiglenes fájlt kell lennie. Az ideiglenes fájl létrehozása a következő helyen:  
>   
>  -   Az ideiglenes fájl ugyanabba a mappába, a célmappa a manuálisan előkészített tartalomfájlhoz megadott jön létre.  

> [!IMPORTANT]  
>  A tartalom kibontása parancssori eszközt futtató felhasználónak rendelkezni kell **rendszergazda** jogosultságokkal azon a számítógépen, amelyről az előre meghatározott tartalom kibontásakor.  

##### <a name="to-extract-the-content-files-from-the-prestaged-content-file"></a>A tartalomfájlok kibontása a manuálisan előkészített tartalomfájlból  

1.  Másolja a manuálisan előkészített tartalomfájlt arra a számítógépre, bontsa ki a tartalmat kívánja.  

2.  Másolja a tartalom kibontása parancssori eszközt a &lt; *Configmgrtelepítésiútvonal*> \bin\\&lt;*platform*> arra a számítógépre, amelyről kibontása a manuálisan előkészített tartalomfájl.  

3.  Nyissa meg a parancssort, és keresse meg a manuálisan előkészített tartalomfájlt és a tartalom kibontása eszközt tartalmazó mappát.  

    > [!NOTE]  
    >  Is kibonthat egy vagy több manuálisan előkészített tartalomfájlok a helykiszolgálón, másodlagos helykiszolgálón vagy terjesztési ponttal.  

4.  Típus **extractcontent/p:**&lt;*Előkészítettfájlhelye*>**\\**&lt;*Előkészítettfájlneve*> **/S** egyetlen fájl importálásához.  

     Típus **extractcontent/p:**&lt;*Előkészítettfájlhelye*> **/S** összes importálása a manuálisan előkészített a megadott mappában található fájlokat.  

     Írja be például, **extractcontent /P:D:\PrestagedFiles\MyPrestagedFile.pkgx /S** ahol `D:\PrestagedFiles\` van az Előkészítettfájlhelye, `MyPrestagedFile.pkgx` a manuálisan előkészített fájl neve és `/S` arról tájékoztatja a Configuration Manager jelenleg a terjesztési ponton található fájloknál csak tartalomfájlok kibontása.  

     A manuálisan előkészített tartalomfájlt helykiszolgálón bontja ki, amikor a tartalomfájlok a helykiszolgálón lévő tartalomtárba kerülnek, és a tartalom hozzáférhetőségét regisztrálja a helykiszolgáló adatbázisában. A manuálisan előkészített tartalomfájlból a terjesztési pont exportálásakor a tartalomfájlokat a terjesztési ponton lévő tartalomtárba kerülnek, a terjesztési pont állapotüzenetet küld a szülő elsődleges helykiszolgálóról, majd a tartalom hozzáférhetőségét regisztrálja a hely adatbázisába.  

    > [!IMPORTANT]  
    >  Abban az esetben frissítenie kell a tartalom új verzióra való frissítésekor az egy manuálisan előkészített tartalomfájlból kibontott tartalmat:  
    >   
    >  1.  A csomag 1 verziójának manuálisan előkészített tartalomfájl létrehozása.  
    >  2.  A csomag forrásfájljainak 2 verziójával frissíti.  
    >  3.  Kibontja a manuálisan előkészített tartalomfájlt (1 a csomag verziója) a terjesztési ponton.  
    >   
    > A Configuration Manager automatikusan ossza el a Csomagverzió 2 a terjesztési pontra. Kell egy új manuálisan előkészített tartalom fájljának létrehozása, amely tartalmazza a fájl új verziója és majd bontsa ki a tartalmat, a megváltozott fájlok terjesztése a terjesztési pont frissítését, vagy a csomagban lévő összes fájl újraterjeszteni.  

###  <a name="bkmk_dpsiteserver"></a>A terjesztési pont a helykiszolgálón a tartalom manuális előkészítése  
 A terjesztési pont telepítésekor a helykiszolgálón a következő eljárás a tartalom sikeres előkészítéséhez kell használnia. Ennek az az oka a tartalomfájlok már eleve a tartalomtárban vannak.  

 Amennyiben a terjesztési ponton nincs engedélyezve, a tartalom előkészítése, illetve ha a terjesztési pont nem található a helykiszolgálón, tekintse meg a [használja a manuálisan előkészített tartalom](#bkmk_prestage) szakaszában talál.  

##### <a name="to-prestage-content-on-distribution-points-located-on-a-site-server"></a>A helykiszolgálón található terjesztési pontokon a tartalom manuális előkészítéséről  

1.  Az alábbi lépések segítségével győződjön meg arról, hogy a terjesztési ponton nincs engedélyezve az előzetesen beállított tartalomhoz.  

    1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

    2.  Az a **felügyeleti** munkaterületet, kattintson a **terjesztési pontok**, majd válassza ki a helykiszolgálón található terjesztési pontot.  

    3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

    4.  Az a **általános** lapon ellenőrizze, hogy a **engedélyezése e terjesztési pont használatát előzetesen beállított tartalomhoz** jelölőnégyzet nincs bejelölve.  

2.  A manuálisan előkészített tartalomfájl létrehozása a [1. lépés: A manuálisan előkészített tartalomfájl létrehozása](#BKMK_CreatePrestagedContentFile) szakaszában talál.  

3.  Rendelje hozzá a tartalmat a terjesztési pont használatával a [2. lépés: A tartalom hozzárendelése terjesztési pontokhoz](#BKMK_AssignContentToDistributionPoint) szakaszában talál.  

4.  A helykiszolgálón a tartalom kibontása a manuálisan előkészített tartalomfájl használatával a [3. lépés: A tartalom kibontása a manuálisan előkészített tartalomfájl](#BKMK_ExportContentFromPrestagedContentFile) szakaszában talál.  

    > [!NOTE]  
    >  Amikor a terjesztési pont egy másodlagos helyen, várjon legalább 10 percet, és ezután a fölérendelt elsődleges helyhez csatlakozó Configuration Manager konzol használatával rendelje hozzá a tartalmat a terjesztési pontot a másodlagos helyen.  

##  <a name="bkmk_manage"></a>A terjesztett tartalom kezelése  
 Lehetősége van a következő tartalom kezelését:  
 - [Tartalom frissítése](#update-content)
 - [Tartalom újraterjesztése](#redistribute-content)
 - [Tartalom eltávolítása](#remove-content)
 - [a tartalom ellenőrzésének](#validate-content)

### <a name="update-content"></a>Tartalom frissítése
Amikor új fájlokat vagy újabb verziójával cserélje le a létező fájlokat hozzáadva a központi telepítés forrásfájljainak helyét frissíti, a terjesztési pontokon található tartalomfájlokat használatával frissítheti a **terjesztési pontok frissítése** vagy **tartalom frissítése** művelet:  
-   A tartalomfájlok a forrásfájl-útvonalról másolandó a tartalomtár a helyen, amely a csomag tartalomforrásának tulajdonosa  
-   A csomag verziószáma növekszik  
-   Minden példánya a tartalomtár helykiszolgálókon és terjesztési pontok frissítések csak a módosított fájlok  

> [!WARNING]  
>  A csomag az alkalmazások verziószáma mindig 1. Egy alkalmazás központi telepítési típus tartalmának frissítésekor a Configuration Manager létrehoz egy új Tartalomazonosítót a központi telepítési típus, és a csomag hivatkozásokat az új tartalom.  

#### <a name="to-update-content-on-distribution-points"></a>A tartalom frissítése terjesztési ponton  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületen jelölje ki az alábbi lépések egyikét a terjeszteni kívánt tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés** > **alkalmazások**, majd válassza ki a terjeszteni kívánt alkalmazásokat. Kattintson a **központi telepítési típusok** fülre, és válassza ki a frissíteni kívánt központi telepítési típust.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés** > **csomagok**, majd válassza ki a frissíteni kívánt csomagokat.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések** > **központi telepítési csomagok**, majd válassza ki a frissíteni kívánt központi telepítési csomagokat.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek** > **illesztőprogram-csomagok**, majd válassza ki a frissíteni kívánt illesztőprogram-csomagokat.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek** > **operációsrendszer-lemezképek**, majd válassza ki a frissíteni kívánt operációsrendszer-lemezképeket.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek** > **operációs rendszerek telepítőcsomagjai**, majd válassza ki a frissíteni kívánt operációsrendszer-telepítőcsomagokat.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek** >  **rendszerindító lemezképek**, majd válassza ki a frissíteni kívánt rendszerindító lemezképeket.  

3.  A a **Home** lap a **telepítési** csoportjában kattintson a **terjesztési pontok frissítése**, és kattintson a **OK** , hogy szeretné-e a tartalom frissítésének megerősítéséhez.  

    > [!NOTE]  
    >  Az alkalmazások tartalmat frissítéséhez kattintson a **központi telepítési típusok** lapra, kattintson a jobb gombbal a központi telepítési típus, a **tartalom frissítése**, és kattintson a **OK** annak ellenőrzéséhez, hogy szeretné-e a tartalom frissítéséhez.  

    > [!NOTE]  
    >  Ha a rendszerindító lemezképek tartalmát frissíti, megnyílik a terjesztési pontok kezelése varázslót. Ellenőrizze az adatokat a **összegzés** lapon, és fejezze be a varázslót a tartalom frissítéséhez.  

### <a name="redistribute-content"></a>Tartalom újraterjesztése
A csomagban lévő összes tartalomfájlt terjesztési pontokra való másolásában csomag újraterjeszthető vagy terjesztési csoportokra, felülírva a meglévő fájlokat.  

 Használja ezt a műveletet a csomag tartalomfájljainak javítására, illetve a tartalom újraküldésére szolgál, ha a kezdeti terjesztés meghiúsul. A csomag újraterjeszthető:  

-   Csomag tulajdonságai  
-   Terjesztési pont tulajdonságai  
-   Terjesztésipontcsoport-tulajdonságok.  


#### <a name="to-redistribute-content-from-package-properties"></a>Csomagtulajdonságok tartalom újraterjesztése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületen jelölje ki az alábbi lépések egyikét a terjeszteni kívánt tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés** >  **alkalmazások**, majd válassza ki az újraterjeszteni kívánt alkalmazást.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés** > **csomagok**, majd válassza ki a terjeszteni kívánt csomagot.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések** >  **központi telepítési csomagok**, majd válassza ki az újraterjeszteni kívánt központi telepítési csomagot.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek** > **illesztőprogram-csomagok**, majd válassza ki az újraterjeszteni kívánt illesztőprogram-csomagot.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek** > **operációsrendszer-lemezképek**, majd válassza ki az újraterjeszteni kívánt operációs rendszer lemezképét.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek** > **operációs rendszerek telepítőcsomagjai**, majd válassza ki az újraterjeszteni kívánt operációs rendszer telepítőcsomagjának.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek** >  **rendszerindító lemezképek**, majd válassza ki az újraterjeszteni kívánt rendszerindító lemezképet.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Kattintson a **tartalom helye** lapra, válassza ki a terjesztési pontot vagy terjesztésipont-csoportján kívánja terjeszteni a tartalmat, kattintson a **újraterjeszteni**, és kattintson a **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-properties"></a>Terjesztési pont tulajdonságainak tartalom újraterjesztése  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  A a **felügyeleti** munkaterületet, kattintson a **terjesztési pontok**, majd válassza ki a terjesztési pontot, amelyben tartalmat terjeszteni szeretné.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Kattintson a **tartalom** lapra, válassza ki az újraterjeszteni, kattintson a tartalom **újraterjeszteni**, és kattintson a **OK**.  

#### <a name="to-redistribute-content-from-distribution-point-group-properties"></a>Terjesztésipontcsoport-tulajdonságok tartalom újraterjesztése  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az a **felügyeleti** munkaterületet, kattintson a **terjesztésipont-csoportok**, majd válassza ki a terjesztésipont-csoportján kívánja terjeszteni a tartalmat.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Kattintson a **tartalom** lapra, válassza ki az újraterjeszteni, kattintson a tartalom **újraterjeszteni**, és kattintson a **OK**.  

    > [!IMPORTANT]  
    >  A csomag tartalmát a rendszer a terjesztési pontokat a terjesztésipont-csoportokban lévő összes újra elosztja.  


#### <a name="use-the-sdk-to-force-replication-of-content"></a>Az SDK használatával kényszerítheti a replikációs tartalom
Használhatja a **RetryContentReplication** osztály adott metódusát Windows Management Instrumentation (WMI) a Configuration Manager SDK kényszerítheti a Distribution Manager a tartalomforrás-helyről másolhatják a tartalmat a tartalomtárba.  

Csak ehhez a módszerhez replikáció, amikor kell terjesztenie a tartalmat, miután problémák merültek fel a normál replikációs tartalom (általában megerősíti a figyelés csomópontot, a konzol használata).   

A SDK beállítással kapcsolatos további információkért lásd: [RetryContentReplication metódus a osztály SMS_CM_UpdatePackages](https://msdn.microsoft.com/library/mt762092(CMSDK.16).aspx) az MSDN Webhelyén. Microsoft.com.

### <a name="remove-content"></a>Tartalom eltávolítása
Ha Ön már nincs szükség a terjesztési pontokon, eltávolíthatja a tartalomfájlokat a terjesztési ponton.  

-   Csomag tulajdonságai  
-   Terjesztési pont tulajdonságai  
-   Terjesztésipontcsoport-tulajdonságok.  

Azonban ha a tartalom egy másik csomaghoz kötődik, amely ugyanarra a terjesztési pontra való terjesztése megtörtént, nem távolítható el a tartalmat.  

#### <a name="to-remove-package-content-files-from-distribution-points"></a>A csomag tartalomfájljainak eltávolítása terjesztési pontokról  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületen jelölje ki az alábbi lépések egyikét a törölni kívánt tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés** > **alkalmazások**, majd válassza ki az eltávolítani kívánt alkalmazást.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés** > **csomagok**, majd válassza ki a csomagot, hogy el szeretné távolítani.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések** > **központi telepítési csomagok**, majd válassza ki az eltávolítani kívánt központi telepítési csomagot.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek** > **illesztőprogram-csomagok**, majd válassza ki az eltávolítani kívánt illesztőprogram-csomagot.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek** > **operációsrendszer-lemezképek**, majd válassza ki az eltávolítani kívánt operációs rendszer lemezképét.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek** > **operációs rendszerek telepítőcsomagjai**, majd válassza ki az eltávolítani kívánt operációs rendszer telepítőcsomagjának.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek** > **rendszerindító lemezképek**, majd válassza ki az eltávolítani kívánt rendszerindító lemezképet.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Kattintson a **tartalom helye** lapra, válassza ki a terjesztési pontot vagy terjesztésipont-csoportot, amelyből el szeretné távolítani a tartalmat, kattintson a **eltávolítása**, és kattintson a **OK**.  

#### <a name="to-remove-package-content-from-distribution-point-properties"></a>Csomagtartalom eltávolítása terjesztésipont-tulajdonságokból  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  A a **felügyeleti** munkaterületet, kattintson a **terjesztési pontok**, majd válassza ki a terjesztési pontot, amelyben tartalmát törölni szeretné.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Kattintson a **tartalom** lapra, válassza ki a az eltávolítandó tartalmat, kattintson a **eltávolítása**, és kattintson a **OK**.  

#### <a name="to-remove-content-from-distribution-point-group-properties"></a>Tartalom eltávolítása terjesztésipontcsoport-tulajdonságokból  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  A a **felügyeleti** munkaterületet, kattintson a **terjesztésipont-csoportok**, majd válassza ki a terjesztésipont-csoportján, amelyben el szeretné távolítani a tartalmat.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Kattintson a **tartalom** lapra, válassza ki a az eltávolítandó tartalmat, kattintson a **eltávolítása**, és kattintson a **OK**.  


### <a name="validate-content"></a>A tartalom ellenőrzésének
A tartalomérvényesítés folyamata ellenőrzi a tartalomfájlokat a terjesztési pontokon integritását. Engedélyezi a tartalomérvényesítési ütemezés szerint, vagy a terjesztési pontok és csomagok tulajdonságai a tartalomérvényesítés manuális módszerrel is kezdeményezhető.  

 Amikor a tartalomérvényesítés folyamata elindul, a Configuration Manager ellenőrzi a tartalomfájlokat a terjesztési pontokon, és ha a fájlkivonat váratlan adatokat tartalmaz a terjesztési pontokon található fájlokkal, a Configuration Manager állapotüzenetet hoz létre, amely megtekinthető a **figyelés** munkaterületen.  

 A tartalomérvényesítési ütemezés konfigurálásáról további információkért lásd: [a terjesztési pontok konfigurációi](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs) a a [telepítése és a terjesztési pontok konfigurálása a System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md) témakör.  


#### <a name="to-initiate-content-validation-for-all-content-on-a-distribution-point"></a>Tartalomérvényesítés a terjesztési pont összes tartalma  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az a **felügyeleti** munkaterületet, kattintson a **terjesztési pontok**, és válassza ki a terjesztési pontot, amelyben a tartalmát érvényesíteni szeretné.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Az a **tartalom** lapra, válassza ki a csomag, amelyben szeretné érvényesíteni a tartalmat, kattintson **ellenőrzése**, kattintson a **OK**, és kattintson a **OK**. A tartalomérvényesítési folyamata elindul, a csomag a terjesztési ponton.  

5.  A tartalomérvényesítési folyamat eredményeinek megtekintéséhez a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **tartalom állapota** csomópont. A tartalom az egyes csomagtípusok (például alkalmazás, szoftverfrissítési csomag és rendszerindító lemezkép) jelenik meg. További információ a tartalomállapot: [figyelése a System Center Configuration Managerrel terjesztett tartalom](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

#### <a name="to-initiate-content-validation-for-a-package"></a>Tartalomérvényesítés csomag  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  Az a **szoftverkönyvtár** munkaterületen jelölje ki az alábbi lépések egyikét az érvényesíteni kívánt tartalomtípushoz:  

    -   **Alkalmazások**: Bontsa ki a **Alkalmazáskezelés** > **alkalmazások**, majd válassza ki az érvényesíteni kívánt alkalmazást.  

    -   **Csomagok**: Bontsa ki a **Alkalmazáskezelés** > **csomagok**, majd válassza ki az érvényesíteni kívánt csomagot.  

    -   **Központi telepítési csomagok**: Bontsa ki a **szoftverfrissítések** > **központi telepítési csomagok**, majd válassza ki az érvényesíteni kívánt központi telepítési csomagot.  

    -   **Illesztőprogram-csomagok**: Bontsa ki a **operációs rendszerek** > **illesztőprogram-csomagok**, majd válassza ki az érvényesíteni kívánt illesztőprogram-csomagot.  

    -   **Operációsrendszer-lemezképek**: Bontsa ki a **operációs rendszerek** > **operációsrendszer-lemezképek**, majd válassza ki az érvényesíteni kívánt operációs rendszer lemezképét.  

    -   **Operációs rendszerek telepítőcsomagjai**: Bontsa ki a **operációs rendszerek** >  **operációs rendszerek telepítőcsomagjai**, majd válassza ki az érvényesíteni kívánt operációs rendszer telepítőcsomagjának.  

    -   **Rendszerindító lemezképek**: Bontsa ki a **operációs rendszerek** > **rendszerindító lemezképek**, majd válassza ki a manuálisan előkészíteni kívánt rendszerindító lemezképet.  

3.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  

4.  Az a **tartalom helye** lapra, válassza ki a terjesztési pontot vagy terjesztésipont-csoportot, amelyben tartalmat, kattintson a érvényesítéséhez **ellenőrzése**, kattintson a **OK**, és kattintson a **OK**. A tartalomérvényesítés folyamata elindul, a tartalom a kiválasztott terjesztési pontra vagy terjesztésipont-csoportot.  

5.  A tartalomérvényesítési folyamat eredményeinek megtekintéséhez a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **tartalom állapota** csomópont. A tartalom az egyes csomagtípusok (például alkalmazás, szoftverfrissítési csomag és rendszerindító lemezkép) jelenik meg. További információ a tartalomállapot megfigyeléséről lásd: [figyelése a System Center Configuration Managerrel terjesztett tartalom](../../../../core/servers/deploy/configure/monitor-content-you-have-distributed.md).  

