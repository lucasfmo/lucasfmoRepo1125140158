---
title: "Kiadványok kezelése |} Microsoft Docs"
description: "A System Center Updates Publisher kiadványban szoftverfrissítési csoportok kezelése"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c1df1d-7728-4980-9199-bc32cde5439e
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: ddea7af935d5be880b96e383401061f8aa11e6da
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-publications-in-updates-publisher"></a>Az Updates Publisher kiadványok kezelése

*Vonatkozik: A System Center frissítés-közzétevő*

Kiadványok segítségével kezelheti a frissítéseket és a csomagok egyetlen objektumként. Ez magában foglalja a frissítések közzétételéhez a felügyeleti kiszolgáló és a kiadvány exportálása csoportot egy másik telepítése frissítés-közzétevő való használatra.

## <a name="create-publications"></a>Kiadványok létrehozása
Kiadványok kétféleképpen hozhatja létre:

-   Amikor Ön felügyeli a frissítések és a csomagok a **frissítések munkaterület**, akkor [hozzárendelése](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication) ekkor jön létre új kiadvány őket.

-   Az a **kiadványok munkaterület** használhatja a **létrehozása** gombra a **kiadvány** a menüszalag lapján. Ez a módszer lehetővé teszi a jövőbeli használatra kiadvány létrehozása. Később Ha frissítések, erre a kiadványra használhatja.

## <a name="rename-a-publication"></a>Nevezze át a kiadvány
Nevezze át a kiadványt, válassza ki a kiadvány belül a **kiadványok munkaterület**, majd a a **kiadvány** lapon válassza ki a menüszalagon **szerkesztése**.

## <a name="change-the-publication-type-of-updates-in-a-publication"></a>A kiadvány típusa a kiadvány frissítések módosítása
Az a **kiadvány munkaterület**, módosíthatja a **kiadvány típusa** a frissítések és az olyan kiadványhoz rendelt csomagok.

1. Válassza ki a módosítani kívánt frissítéseket tartalmazó kiadványt, és válassza ki egy vagy több frissítés, vagy a csomagokat a **összes &lt;kiadvány neve > tagok frissítését** listája.

2. Ezt követően a **Home** adja meg a következő lehetőségek közül. A rendelkezésre álló lehetőségek attól függ, hogy a kijelölt frissítések kiadvány típusú.

  -   **Automatikus**
  -   **Teljes tartalom**
  -   **Csak metaadat.**

A módosítások elvégzése után szükség lehet a kiadvány nézet frissítése új értékeinek megtekintéséhez.

A különböző típusok kapcsolatos információkért lásd: [frissítések és a csomagok hozzárendelése egy kiadvány](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication).

> [!TIP]    
> Ha úgy állítja be a kiadvány típusa a csomag egyik gyermekszoftver, ezt a köteget lévő összes szoftverfrissítés közzétett ezt a köteget a kiadvány típusát.

## <a name="remove-updates-from-a-publication"></a>Távolítsa el a frissítéseket a kiadvány
A kiadványban, frissítések vagy csomagok eltávolítása a **kiadványok munkaterület** válassza ki a módosítani kívánt kiadvány, és jelölje ki a frissítések és az eltávolítani kívánt csomagokat. Ezt követően a **Home** lapon válassza ki a menüszalag **eltávolítása**.

Frissítések a kiadványból eltávolításuk után elérhetők maradjanak a frissítés-közzétevő tárházban.

## <a name="publish-publications"></a>Kiadványok közzététele
Ha közzéteszi a frissítések és a csomagok, frissítés-közzétevő információ a frissítések és a csomagok (metadata) és valószínűleg a frissítések (teljes tartalmát), a bináris fájlok hozzáadása számítógépekre történő központi frissítési kiszolgálón.

Mielőtt lehetősége van a közzététel, konfigurálnia kell a [frissítési kiszolgáló](/sccm/sum/tools/updates-publisher-options#update-server) az Updates Publisher lehetőséget. Nyissa meg a konfigurációs beállítás, keresse fel **frissítések munkaterület** &gt; **áttekintése** válassza **konfigurálása a WSUS és az aláíró tanúsítvány.** A frissítési kiszolgáló lapra az Updates Publisher beállításai is választhatja.

> [!NOTE]   
> Frissítés-közzétevő csak is közzéteheti a frissítéseket, amelyek 375 megabájt (MB) vagy mérete.

### <a name="to-publish-a-publication"></a>A kiadvány közzététele

1.  Lépjen a **kiadványok munkaterület**, majd válassza ki a csoport a frissítések és közzététele, vagy exportálni kívánt csomagokat tartalmazó kiadványt. Válassza a **közzététel** a **Home** a menüszalag lapján.

2.  Az a **kiválasztása** oldalán a **közzététel** varázsló, dönthet úgy, minden frissítés egy új közzétételi tanúsítvánnyal aláírásához, de a kiadvány típusa nem módosítható.

3.  Fejezze be a varázslót.

  Ha sikertelen a közzétételi, lehetősége lesz, amely további információt nyújt a UpdatesPublisher.log fájlra mutató hivatkozás.

## <a name="export-a-publication"></a>A kiadvány exportálása
A frissítés-közzétevő tárházból exportálhatja egy kiadvány. Ezzel a frissítések és a csomagok adott kiadványra házirendjét, és létrehoz egy frissítési katalógus exportálása. Követően [hozzáadása](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) , majd [importálása](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) frissítés-közzétevő másik példányára, hogy katalógus. Emellett [frissítések exportálása](/sccm/sum/tools/manage-updates-with-updates-publisher#export-updates) , amelyek nem részei egy kiadvány.

A kiadvány exportálásához nyissa meg a **kiadványok munkaterület** válassza ki az exportálni kívánt frissítéseket tartalmazó kiadványt. Egyszerre csak egy kiadvány jelölhet ki.

Válassza ki a kijelölt kiadvánnyal, **exportálása** a a **Home** a menüszalag lapján a katalógus exportálási adja meg egy elérési út és fájlnév.

Akkor is exportálására szolgáló beállítás (tartalmaz) függő szoftverfrissítéseket az Exportálás részeként.

## <a name="rename-a-publication"></a>Nevezze át a kiadvány
Nevezze át a kiadványt, jelölje be a kiadvány a **kiadványok munkaterület**, és válassza a **szerkesztése** a a **kiadvány** a menüszalag lapján.

## <a name="delete-a-publication"></a>Közzététel törlése
A kiadvány törléséhez válassza ki a kiadvány a **kiadványok munkaterület**, és válassza a **törlése** a a **kiadvány** a menüszalag lapján.

A kiadvány az Updates Publisher eltávolítása után volt a következő kiadványban: a frissítések elérhetők maradnak a frissítés-közzétevő tárházban.

## <a name="expire-or-reactivate-updates-and-bundles"></a>Lejár, és aktiválja újra a frissítések és csomagok
Használhatja a **frissítések munkaterület** válassza ki, majd lejáratát vagy aktiválja újra a frissítések és a csomagok. Lejár, és aktiválja újra a frissítések és a csomagok, ahányszor választja.

-   **Lejár a frissítések vagy csomagok**, és a frissítések munkaterületen válassza az egy vagy több frissítéseket vagy bundles, amely nem lejárt, és válassza a **lejárati** a a **Home** lapon. Az egy vagy több csomagot a Configuration Manager lejártként közzétételéig újraaktiválhatja.

    Eltávolítása előtt (Törlés) egy egyéni frissítés vagy a csomagot a Configuration Manager alkalmazásból, azt lejár, és tegye közzé az, hogy lejárt állapotát a Configuration Manager. Frissítések vagy kötegek lejárt a Configuration Manager alkalmazásban, miután már nem telepíthet vagy aktiválja újra a frissítést vagy a csomag.

-   **Frissítések vagy csomagok újraaktiválása**, a frissítések munkaterületen válassza ki, amely lejárt, és válasszon egy vagy több frissítést **újraaktiválása** a a **Home** a menüszalag lapján. Ha lejárt a frissítés a Configuration Manager lejártként korábban közzétett, nem lehet újraaktiválni.

