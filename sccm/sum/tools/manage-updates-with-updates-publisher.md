---
title: "Frissítések kezelése |} Microsoft Docs"
description: "A frissítések központi telepítése, és hozzon létre a System Center frissítés-közzétevő kezelése"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd64994c-b426-4465-96cd-54b0edc2778d
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 1d6c3b1db14867bdbc5cae8ded099d9024a79549
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-software-updates-in-updates-publisher"></a>A frissítés-közzétevő-szoftverfrissítések kezelése

*Vonatkozik: A System Center frissítés-közzétevő*     

A System Center frissítés-közzétevő, használja a **frissítések munkaterület** szoftverfrissítéseket és csomagokat, a tárházba importált kezelésére.  

Fájlkezelési feladatok közé tartozik a másolás, szerkesztésére és lejár vagy frissítések és csomagok, és hozzárendelése frissítések és csomagok olyan kiadványokra újraaktiválás. Exportálhatja a telepített más frissítés-közzétevője használható egyéni katalógusok is.

A frissítések, hogy kezelheti:
-  [Adja hozzá a frissítési katalógus](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) az Updates Publisher telepítése
-  [Importálás](/sccm/sum/tools/updates-publisher-catalogs#import-updates) a frissítések adott katalógusból a tárházhoz.

Emellett [hozzon létre egy saját frissítések](/sccm/sum/tools/create-updates-with-updates-publisher).



## <a name="create-a-duplicate-of-an-update"></a>Egy frissítés másolatának létrehozása
Ismétlődő vagy a tárházban lévő szoftverfrissítésekhez, másolatait is létrehozhat. Majd módosíthatja a példány módosítása a frissítés helyett. Frissítési csomagok példánya nem hozható létre.

Hozzon létre egy másolatot, jelölje be a frissítés a **frissítések munkaterület**, és válassza a **ismétlődő**. A Másolás a frissítés jelenik meg a frissítések munkaterületen az ugyanazon a helyen *másolata* hozzá annak nevét.

Létrehozhat új állapotba került **Unexpired**, de egyébként megőrzi az eredeti beállítások.

## <a name="edit-updates-and-bundles"></a>Frissítések és a csomagok szerkesztése
Kiválaszthatja a frissítések és a tárház azokat a csomagokat.

Az a **frissítések munkaterület** válasszon egy update vagy a csomagot, és válassza **szerkesztése** a a **Home** elemére kattintva nyissa meg a szerkesztése varázsló. Frissítések és a csomagok is, hogy a beállítások szerint különálló, de a szorosan kapcsolódó varázslók a [létrehozása frissítése](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-update-wizard) vagy [csomagot hozzon létre](/sccm/sum/tools/create-updates-with-updates-publisher#the-create-bundle-wizard) varázslók.

Szerkesztésekor, bármely elérhető részletes információkat a frissítés módosíthatja vagy, hogy a környezetben használt csomagot. Például a alkalmazhatósági vagy elsőbbséget szabályok szerkesztése, vagy módosítsa a nyelvet. A termék és forgalmazójával, hogy helyezze át a frissítés, vagy egy egyéni mappába csoport frissítések saját használatra csomagot is módosíthatja.

## <a name="assign-updates-and-bundles-to-a-publication"></a>Frissítések és a csomagok hozzárendelése egy kiadvány
Kiválaszthatja a frissítések és a csomagok a **frissítések munkaterületen** majd **hozzárendelése** a a **Home** kiadvány adja hozzá a menüszalagon látható lapján. Ekkor elindul a **szoftverfrissítések hozzárendelése** varázsló.
-  Lásd: [közzétenni a frissítéseket és a csomagok](#publish-updates-and-bundles-from-the-updates-workspace) válassza ki, és a frissítések és a csomagok közzététele az egyetlen feladatok olvashat.
-  Lásd: [kiadványok kezelése](/sccm/sum/tools/updates-publisher-publications) információ a frissítések és a csomagok kezelése egyetlen objektumként. Miután frissítések olyan kiadványban, kezelheti, hogy a kiadványt, aminek pedig tartalmazza az összes hozzárendelt frissítést.

Ha egy kiadvány társít frissítések:

-   Egyazon kiadványban lejárt és nem lejárt frissítések és a csomagok tartalmazhatnak.

-   Adja meg a kiadvány típusa:

    -   **Teljes tartalom** – Ez a frissítés a teljes tartalmat tesz közzé a WSUS-kiszolgáló. Ez magában foglalja a metaadatok és a frissítés bináris fájljait.

    -   **Csak metaadat** – Ez csak a metaadatok tesz közzé; a frissítés bináris fájljait a rendszer nem teszi közzé. Előfordulhat, hogy válassza ezt a beállítást, ha meg szeretné megfelelőségi adatokat gyűjt.

    -   **Automatikus** – ebben az üzemmódban csak érhető el, ha csatlakozott Updates Publisher a Configuration Manager (lásd a [ConfigMgr-kiszolgáló](/sccm/sum/tools/updates-publisher-options#configmgr-server) lehetőséget.)

    Az ilyen típusú frissítés-közzétevő lekérdezi a Configuration Manager határozza meg, ha a frissítések vagy a kötegek közzé kell tenni a teljes tartalmát, vagy csak metaadat. Egy frissítés közzé van téve, csak ha, amely megfelel-e a tartalom teljes a **kért ügyfél száma küszöbértékét** és **csomag forrás adatbázisméret küszöbértéke** amelyek nincsenek megadva a **ConfigMgr-kiszolgáló** Updates Publisher beállítások lapján.

-   Válassza ki a kiadvány:

    -   Használjon **szoftverfrissítés hozzárendelése a meglévő kiadványokat** Ha már létrehozott egy használni kívánt kiadvány. Ez a beállítás nem érhető el, amíg legalább egy kiadvány létezik.

    -   Használjon **szoftverfrissítés hozzárendelése egy új kiadvány** Ha nem rendelkezik a megfelelő kiadvány. Ezzel létrehoz egy új kiadvány a megadott névvel.

Miután frissítések rendel egy kiadvány, használhatja a **kiadvány munkaterület** való [közzététele](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) vagy [exportálása](/sccm/sum/tools/updates-publisher-publications#export-a-pubilcation) a kiadvány csoportként.

## <a name="publish-updates-and-bundles-from-the-updates-workspace"></a>Frissítések és a frissítések munkaterületen csomagok közzététele
Ha közzéteszi a frissítések és a csomagok, Updates Publisher hozzáadja azokat a frissítéseket és a csomagok (metadata) és esetleg a bináris fájlok a frissítések (teljes tartalmát), információ számítógépekre történő központi frissítési kiszolgálón.

Mielőtt lehetősége van a közzététel, konfigurálnia kell a [frissítési kiszolgáló](/sccm/sum/tools/updates-publisher-options#update-server) az Updates Publisher lehetőséget. Nyissa meg a konfigurációs beállítás, keresse fel **frissítések munkaterület** &gt; **áttekintése** válassza **konfigurálása a WSUS és az aláíró tanúsítvány.** A frissítési kiszolgáló lapra az Updates Publisher beállításai is választhatja.

Két módon lehet közzétenni a frissítéseket és a csomagok:
-   Közvetlenül a frissítések munkaterületen. (Lásd az alábbi eljárás *közzétenni a frissítéseket és a csomagok*.)
-   Mint egy [kiadvány](/sccm/sum/tools/updates-publisher-publications#publish-pubilcations) a kiadványok munkaterületről.  

> [!NOTE]   
> Frissítés-közzétevő csak is közzéteheti a frissítéseket, amelyek 375 megabájt (MB) vagy mérete.

### <a name="to-publish-updates-and-bundles"></a>Frissítések és a csomagok közzététele
1.  Ugrás a **frissítések munkaterület** és válassza ki egy vagy több frissítések és a közzétenni kívánt csomagokat. Válassza a **közzététel** a **Home** a menüszalag lapján.

2.  Az a **kiválasztása** oldalán a **közzététel** varázsló, válassza ki, hogyan szeretné közzétenni a frissítéseket. A beállítások ugyanazok, mint a [frissítések hozzárendelése](#assign-updates-and-bundles-to-a-publication): **Teljes tartalom**, **csak metaadat**, vagy **automatikus**.

    Választhatja azt is, minden frissítés egy új közzétételi tanúsítvánnyal aláírásához.

3.  Fejezze be a varázslót.

Ha sikertelen a közzétételi, lehetősége lesz, amely további információt nyújt a UpdatesPublisher.log fájlra mutató hivatkozás.

## <a name="export-updates"></a>Frissítések exportálása
Frissítések és a csomagok exportálhatja az Updates Publisher tárházból egyéni frissítési katalógus létrehozása. Ezután [hozzáadása](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) , majd [importálása](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) frissítés-közzétevő másik példányára, hogy katalógus. (Is [frissítések exportálni egy kiadvány](/sccm/sum/tools/updates-publisher-publications##export-a-publication).)

Közvetlenül exportálásához nyissa meg a **frissítések munkaterület** > **minden szoftverfrissítés** és válassza a frissítések és a csomagok egy vagy több. Nem lehet exportálni a gyártó vagy a termék mappa, de válasszon ki egy mappát, és válassza ki a frissítéseket az exportált abban a mappában.

Egy vagy több frissítés kiválasztva, majd kattintson **exportálása** a a **Home** a menüszalag lapján a katalógus exportálási adja meg egy elérési utat és fájlnevet.

Hogy exportálására szolgáló beállítás (tartalmaz) függő szoftverfrissítéseket.

## <a name="delete-updates-and-bundles"></a>Frissítések és kötegek törlése
Törölheti a frissítések és a frissítések az Updates Publisher tárház távolítsa el azokat a csomagokat.

Keresse fel **frissítések munkaterület** > **minden szoftverfrissítés** , és válasszon egy vagy több egyedi frissítések. Válassza a **törlése** a a **Home** a menüszalag lapján.

-   Ha a kijelölés csak a frissítések vagy a csomagokat, amelyek még nem lettek közzétéve vagy tartalmaz, amely lejárt, a rendszer felkéri előtt eltávolítja a törlés jóváhagyásához.

-   Ha a kiválasztott tartalmazza a frissítés vagy csomagot, amely közzé lett téve, és még nem járt le, lehetősége van a figyelmeztetést. Meg kell [lejár](/sccm/sum/tools/updates-publisher-pubilcations#expire-or-reactivate-updates-and-bundles) azokat a frissítéseket, majd tegye közzé Ez a változás, mielőtt törli őket a tárházból.  

Ha töröl egy frissítés vagy egy kereskedőtől egy szoftvermegoldás csomagot, és majd importálja újra a katalógus, a tárházhoz, ez a frissítés állítottak vissza.

## <a name="manage-vendor-and-product-folders"></a>Szállítói és a termék mappák kezelése
A szállítók és termékek listáját az egyes szállítók, amelynek Ön importált vagy létrehozott frissítések megtekintéséhez nyissa meg a **frissítések munkaterület** > **áttekintése** > **minden szoftverfrissítés**.

A szállítók és termékek mappák jönnek létre automatikusan frissítés-közzétevő egy varázsló segítségével importálja, vagy hozzon létre egy szoftverfrissítés vagy csomagot. Ezek a mappák manuálisan is létrehozhat.

-   Egy szállító mappa létrehozása a navigációs ablaktábláján található a **frissítések munkaterület**, kattintson a jobb gombbal a **minden szoftverfrissítés**, és válassza a **létrehozása szállító**.

-   Hozzon létre egy termék mappát egy szállító mappát, kattintson a jobb gombbal a szállító mappára, és válassza a **létrehozása termék**.

Mellett mappák létrehozása, átnevezése vagy a szállító és a tárházban termék mappa törlése. Ehhez, kattintson a jobb gombbal a mappára, és válassza ki a kívánt, **átnevezése** vagy **törlése**. A mappa törlése eltávolítja a frissítéseket és a csomagok mappa és a termék mappákhoz, a frissítés-közzétevő tárházból.

Frissítések áthelyezhet szállító és a termék mappák, beleértve a mappákat hoz létre. Helyezze át egy frissítést, vagy csomagot egy új mappába, ki kell választania, majd **szerkesztése** az egy vagy több csomagot. Ezt követően a **információk** lap a szállító és a termék hozzárendelheti a frissítési szerkesztése varázsló. Ha a **szerkesztése frissítése** varázsló befejeződött, a módosított, és a frissítés az új mappába helyezi át.

## <a name="view-the-xml-of-an-update-or-bundle"></a>Egy update vagy a csomag XML-megtekintése
Válasszon ki egy frissítést, vagy a csomagot a **frissítések munkaterület** majd **nézet** , ez a frissítés XML-szerkezettel megjelenítendő XML. Az XML-struktúra közvetlenül szerkesztése nincs lehetőség áll rendelkezésre.

