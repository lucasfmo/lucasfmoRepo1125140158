---
title: "Frissítés katalógusok kezelése |} Microsoft Docs"
description: "Szoftverek frissítési katalógusok kezelése a System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 887f8029-1a3a-423c-a9c1-31dc0d693386
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 7451d699e0e5e146b0538a57deca595188d113bf
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-software-update-catalogs-in-updates-publisher"></a>Az Updates Publisher software update katalógusok kezelése

*Vonatkozik: A System Center frissítés-közzétevő*

Használja a **katalógusok** **munkaterület** software update katalógusok kezeléséhez. Ez magában foglalja, hozzáadása új katalógusok, meglévő katalógus az előfizetések kezelése és a frissítésekkel kapcsolatos információk importálása a katalógusból a frissítés-közzétevő tárházba.

Szoftverek frissítési katalógus szervezetek nem a Microsoft által létrehozott kapcsolódó frissítésével kapcsolatos információkat tartalmaz. Más szervezetek közé tartoznak a saját szervezet és a Microsoft a katalógusok regisztrált külső szoftvergyártók. Regisztrált katalógusok szoftverszállítóktól származó nevezzük *katalógusok partneri*. Hoz létre, és nem regisztrált a Microsoft, katalógusok nevezzük *felhasználói* katalógusok.

## <a name="add-software-update-catalogs"></a>Szoftverek frissítési katalógus hozzáadása
Hozzá kell adnia egy frissítési katalógus az Updates Publisherbe, amely tartalmazza a frissítések kezeléséhez. A katalógus, a frissítés-közzétevő hozzáadásakor:
-   A katalógus egy előfizetést hoz létre, ezért azt is ellenőrzi, hogy a katalógus frissítések.
-   A katalógus listáját, amely hozzáadja a **saját Software Update katalógusok** ablakot, a **katalógusok munkaterület**.  

Minden előfizetett katalógus vonatkozó információk is elérhető a konzolon. Információk közé tartozik a letöltési URL-cím vagy helyét, a neve, a vállalat vagy szervezet ki hozta létre a katalógusban, és mikor volt utoljára importálhatja, vagy módosítani.

Frissítés-közzétevő automatikusan megkeresheti az előfizetések módosítások minden indításakor. Ez úgy van konfigurálva egy [speciális beállítás](/sccm/sum/tools/updates-publisher-options#advanced). Konfigurálásakor az Updates Publisher hivatkozik a letöltési URL-cím vagy a hely információ az előfizetés és a riasztások, ha a katalógus legutóbbi óta végzett módosítások vannak importálta, akkor a tárházba.

Manuálisan ellenőrizze az katalógusfrissítés, válassza a katalógus a **a szoftver frissítéséhez katalógusok** listában, és válassza a **frissítése** a szalagról.

Katalógusok hozzáadása, és előfizetett a katalógusok vonatkozó információk megtekintése, mellett a következő műveletek végezhetők el:
-  **Szerkesztés** információi *felhasználói* katalógusok.
-  **Törlés** (Eltávolítás) egy katalógust a frissítés-közzétevő.
-  **Importálás** frissítések az Updates Publisher tárház a katalógusból. Frissítések importálásakor importálja, hogy a katalógusban lévő összes frissítés. A frissítések munkaterületen, ahol válassza ki, majd közzéteheti a frissítési kiszolgáló a frissítések tekinthető meg.

> [!NOTE]   
> A katalógusban távolít el a tárházat a frissítést eredményez a katalógus törlése a frissítés-közzétevő. Ez nem befolyásolja a frissítési kiszolgáló közzétett frissítéseket. Távolítsa el a frissítési kiszolgálót, amely már nincs az adattárban lévő frissítések, lásd: [nem hivatkozott szoftverfrissítéseket lejár](/sccm/sum/tools/updates-publisher-options#expire-unreferenced-software-updates).

## <a name="manage-update-catalogs"></a>Frissítés katalógusok kezelése
Megtekintheti a importálta-e a lista katalógusok a **saját Software Update katalógusok** ablakot, a **katalógusok munkaterület**. A munkaterületen a következőket teheti:

-   **Egy partner katalógust hozzáadása:** Új partner katalógusok kereséséhez használja a következő egyikét:

    -   Nyissa meg a a konzol **frissítések munkaterület** > **áttekintése**. Az a **bevezetés** ablakban válassza a **hozzáadása Partner szoftver frissítések katalógusok**.

    -   Nyissa meg a a konzol **katalógusok munkaterület** > **saját katalógusok**. Ezután a menüszalagról válassza **hozzáadása katalógusok**.

-   **A felhasználó katalógus hozzáadása:** Nyissa meg a a konzol **katalógusok munkaterület** > **saját katalógusok**. Ezután a menüszalagról válassza **hozzáadása katalógusok**. A .cab-fájl helyét, valamint meg kell adnia egy Publisher, nevét és leírását a katalógus azonosításához.


-   **Ellenőrizze a katalógus frissítése:** Válasszon egy vagy több katalógusokat, és válassza a **frissítése** a szalagról.

-   **Egy felhasználó katalógus szerkesztése:** Válassza ki a *felhasználói* katalógusban, és válassza a **szerkesztése** a szalagról. A felhasználó által definiált tulajdonságok ezután módosíthatja.

-   **Katalógusok törlése:** Válasszon egy vagy több katalógusok, és válassza a **eltávolítása** a szalagról. Ezek az Updates Publisher tárházból katalógusok a katalógusban, az előfizetés és a frissítések ezzel eltávolítja.

-   **Adja hozzá a frissítések a katalógusból a tárházhoz**: Válasszon **importálási** elindítani a szalagról a **importálandó katalógus** varázsló. További infomration, lásd: [frissítéseknek](#import-updates)

## <a name="import-updates"></a>Frissítések importálása
A katalógus importálásakor frissítések Manager ad hozzá a frissítések adott katalógusból az Updates Publisher tárház. Után az importált frissítéseket, a frissítési kiszolgálót, a felügyelt eszközökön történő elérhetővé teszi azokat a közzéteheti őket.

### <a name="to-import-updates"></a>Frissítések importálása
1.  Elindítani a **importálandó katalógus** varázsló, válassza a **importálási** a menüszalagról, a következő munkaterületek egyikében:

    -   Katalógusok munkaterület

    -   Frissítések munkaterület

2.  Az a **Importálástípus** lapon jelölje be az Updates Publisherbe hozzáadott egy vagy több katalógusok, vagy még nem telepített egy előfizetés katalógus elérési útja. Kiválasztott **következő** az összegző képernyő megtekintése, és ha készen áll, válassza a **következő** az importálás elindításához.

3.  Az a **biztonsági figyelmeztetés-katalógus érvényesítése** ablak, tekintse át a katalógus tanúsítvány, és ha készen áll, kiválasztott **elfogadás** importálása az updates.

    > [!CAUTION]    
    > Fogadja el a frissítéseket csak a megbízható közzétevők. Szoftverfrissítések számára nem megbízható közzétevők a esetleg kárt is tehetnek ügyfélszámítógépek számára a frissítések keresése során.

    >  Ha már nem megbízható közzétevő, távolítsa el, hogy a kiadó megbízható közzétevők listájáról. További információ a katalógusok elfogadása megkereséséhez kattintson **közölje Me további** a a **biztonsági figyelmeztetés-katalógus érvényesítése** párbeszédpanel.

    Ha mindig elfogadja a katalógusokat közzétevőtől származó, adott publisher hozzáadódik a [megbízható közzétevők lista](/sccm/sum/tools/updates-publisher-options#trusted-publishers). Tekintse át, és szerkeszthetik a listát a frissítés-közzétevő lehetőség.

4.  Importálás kihagyja importálása egy frissítést, ha a frissítés már szerepel a tárházban, az alábbiak egyike igaz:

    -   A frissítés nem tér el a legutóbbi alkalommal importálta.

    -   A frissítés módosítva lett, és új digitális kivonattal rendelkezik. Frissítés szerkesztése megelőzhető, hogy egy új frissítési felülírja az eredeti, ezzel előfordulhat, hogy telepítette a módosításokat felülírja.

5.  Az a **megerősítő** lapon tekintse át az importálási eredmény.

6.  Kattintson a **Bezárás** a varázsló befejezéséhez. A frissítések a katalógus most már megtekintheti a frissítések munkaterületen.

## <a name="next-steps"></a>További lépések
Frissítések importálása után közös műveletek a következők lehetnek:
-   [Frissítések kezelése](/sccm/sum/tools/manage-updates-with-updates-publisher) csomagot, rendelje hozzá, és a frissítési kiszolgálót telepíthet.
-   [Az alkalmazhatósági szabályok létrehozása](/sccm/sum/tools/updates-publisher-applicability-rules) annak meghatározásához, amikor a frissítési kiszolgáló frissítések telepítése.

