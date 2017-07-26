---
title: "Beállítások konfigurálása |} Microsoft Docs"
description: "System Center Updates Publisher használatával beállítások konfigurálása"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e620080-5400-45bb-87c2-fbdbc8aeacac
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: b66ed0a5e1c87d8c82853da86e3d55b0e2c043bb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="configure-options-for-updates-publisher"></a>Az Updates Publisher beállítások konfigurálása

*Vonatkozik: A System Center frissítés-közzétevő*

Tekintse át, és a beállítások és a frissítés-közzétevő működését befolyásoló kapcsolódó beállítások konfigurálása.

Az Updates Publisher lehetőséget, a konzol bal felső sarkában az eléréséhez kattintson a a **frissítés-közzétevő** **tulajdonságok** lapra, és válassza a **beállítások**.

![Paraméterek](media/properties1.png)   


Beállítások vannak osztva a következő:

-   A frissítési kiszolgáló
-   ConfigMgr-kiszolgálón
-   Proxybeállítások
-   Megbízható gyártók
-   Speciális
-   Frissítések
-   Naplózás

## <a name="update-server"></a>A frissítési kiszolgáló
Konfigurálnia kell a frissítési kiszolgáló például Windows Server Update Services (WSUS) használata előtt a frissítés-közzétevő [közzéteheti a frissítéseket](/sccm/sum/tools/manage-updates-with-updates-publisher#publish-updates-and-bundles). Ez magában foglalja a kiszolgáló megadásával, is csatlakozhassanak a kiszolgálóhoz, ha távoli a konzolról, és egy digitális aláírásához használt tanúsítványt a frissítéseket, metódusok közzététele.

-   **Állítson be egy frissítési kiszolgálót**. Egy frissítési kiszolgáló beállításakor válassza ki a legfelső szintű WSUS-kiszolgálóval (frissítési kiszolgáló) a Configuration Manager-hierarchiában, hogy az összes alárendelt hely frissítéseket, amelyek tesz közzé hozzáférése.

  Ha a frissítési kiszolgáló távoli az Updates Publisher kiszolgálóról, adja meg a kiszolgáló teljesen minősített tartománynevét (FQDN), és ha SSL kapcsolódni fog. Ha SSL kapcsolódik, az alapértelmezett port a 8530-as 8531 változik. Gondoskodjon arról, hogy a beállított port megegyezik a frissítési kiszolgálót használja.

    > [!TIP]  
    > Ha nem konfigurálja a frissítési kiszolgálón, a szoftverfrissítések történő továbbra is használhatja a frissítés-közzétevő.

-   **Az aláíró tanúsítvány konfigurálása**. Konfigurálni kell, és sikeresen csatlakozni a megadott frissítési kiszolgálón az aláíró tanúsítvány konfigurálása előtt.

    Frissítés-közzétevő a szoftverfrissítések a frissítési kiszolgáló közzétett aláírására használt aláíró tanúsítványt. Közzététel sikertelen lesz, ha a digitális tanúsítvány nem érhető el a frissítési kiszolgáló vagy az Updates Publisher futtató számítógép tanúsítványtárolójában.

    A tanúsítványt a tanúsítványtárolóból történő hozzáadásával kapcsolatos további információkért lásd: [tanúsítványokat és a frissítés-közzétevő biztonsági](/sccm/sum/tools/updates-publisher-security).

    Ha egy digitális tanúsítvány automatikusan nem észlelt a frissítési kiszolgáló, a következő közül választhat:

    -   **Tallózás**: Tallózás csak akkor használható, ha a frissítési kiszolgálót a konzolt futtató kiszolgálón telepítve van. Miután kiválasztotta a tanúsítványt ki kell választania **létrehozása** , hogy a tanúsítvány felvétele a WSUS a frissítési kiszolgáló tanúsítványtárolójában. Meg kell adnia a **.pfx** fájl ezzel a módszerrel kiválasztott tanúsítványhoz jelszót.

    -   **Hozza létre:** Ez a beállítás segítségével hozzon létre egy új tanúsítványt. Ez is hozzáadja a tanúsítványt a WSUS a frissítési kiszolgáló tanúsítványtárolójában.

    **Ha a saját aláíró tanúsítvány létrehozása**, állítsa be a következőket:

    -   Engedélyezze a **a titkos kulcs exportálható** lehetőséget.

    -   Állítsa be **kulcshasználat** digitális aláírás.

    -   Állítsa be **minimális kulcshossz** egyenlő vagy nagyobb, mint 2048 bites értékre.

    Használja a **eltávolítása** eltávolítani egy tanúsítványt a WSUS-tárolóba. Ez a beállítás érhető el a frissítési kiszolgáló helyi az Updates Publisher konzol használata esetén, illetve ha Ön **SSL** csatlakozni egy távoli frissítési kiszolgáló.

## <a name="configmgr-server"></a>ConfigMgr-kiszolgálón
A Configuration Manager használatakor egy frissítés-közzétevő használja az alábbi beállításokat.

-   **Adja meg a Configuration Manager-kiszolgáló:** Miután engedélyezte a Configuration Manager támogatási, adja meg a Configuration Manager-hierarchia legfelső szintű hely kiszolgálójának helyét. A frissítés-közzétevő telepítést a távoli kiszolgáló esetén adja meg a hely kiszolgálójának teljes Tartománynevét. Válasszon **kapcsolat tesztelése** annak érdekében, hogy a helykiszolgáló csatlakozhat.

-   **Küszöbértékek konfigurálása:** Ha közzéteszi a frissítések automatikus kiadvány típussal rendelkező küszöbértékek használt. A küszöbértékek meghatározásához, hogy a teljes tartalmát egy frissítés helyett csak a metaadatok közzétételekor. További típusok kapcsolatban [frissítések hozzárendelése egy kiadvány](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)

    A következő küszöbértékek valamelyikét teheti:

    -   **A kért ügyfél számának küszöbértéke:** Ez határozza meg, hány ügyfelet kell igényelnie a frissítés előtt az Updates Publisher automatikusan közzétehet, ez a frissítés tartalmának teljes készletét. Amíg az ügyfelek a megadott számú kérelem a frissítést, csak a metaadatok közzé van téve.

    -   **Csomag forrása adatbázisméret küszöbértéke (MB):** Ez megakadályozza, hogy a frissítések, amelyek mérete meghaladja a megadott méret automatikus közzétételét. A frissítések mérete meghaladja ezt az értéket, ha csak a metaadatok közzé van téve. A frissítések, amelyek kisebb, mint a megadott méret lehet a közzétett teljes tartalmát.

## <a name="proxy-settings"></a>Proxybeállítások
Frissítés-közzétevő használja a proxybeállítások helyességét, amikor szoftver katalógusok importálása az internetről, vagy közzétenni a frissítéseket az internethez.

-   Adja meg a proxykiszolgáló teljes Tartománynevét vagy IP-címe. IPv4 és IPv6 használata támogatott.

-   Ha a proxykiszolgáló hitelesíti a felhasználókat az internethez, a Windows nevet kell megadnia. Egy univerzális elv felhasználónév (UPN) nem támogatott.

## <a name="trusted-publishers"></a>Megbízható gyártók
Ha importál egy frissítési katalógus, a katalógus (a tanúsítvány alapján), a forrás meg van adva a megbízható közzétevők. Hasonlóképpen ha közzéteszi a frissítést, a frissítések tanúsítvány forrását meg van adva a megbízható közzétevők.

Minden közzétevő tanúsítvány részleteinek megtekintése, és távolítsa el a megbízható közzétevők listájából, a közzétevő.

Tartalmából áll, amelyek nem megbízható közzétevők esetleg kárt is tehetnek ügyfélszámítógépek számára, amikor az ügyfél ellenőrzi a frissítéseket. Csak a megbízható közzétevők tartalom kell fogadnia.

## <a name="advanced"></a>Speciális
Speciális beállítások a következők:

-   **Tárház helye:** Megtekintheti és módosíthatja az adatbázis-fájl helyét **scupdb.sdf**. A fájl a tárházban az Updates Publisher.

-   **Időbélyeg:** Ha engedélyezve van, időbélyeg kerül frissítések meg bejelentkezési azonosító, ha volt aláírva. Egy frissítés során a tanúsítvány érvényes az aláírt aláíró tanúsítvány lejárata után is használható. Alapértelmezés szerint a szoftverfrissítések nem állítható rendszerbe, az aláíró tanúsítvány lejárata után is.

-   **Előfizetett a katalógusok frissítéseinek keresése:** Minden alkalommal, amikor elindul a frissítés-közzétevő, az automatikusan megkeresi az előfizetett a katalógusok frissítéseit. Katalógusfrissítés megtalált részletek vannak megadva, a **legújabb riasztások** a a **áttekintése** ablakában a **frissítések munkaterület**.

-   **Tanúsítvány-visszavonás:** Válassza ezt a beállítást, tanúsítvány-visszavonási ellenőrzést engedélyezéséhez.

-   **Helyi forrás közzététel:** Frissítés-közzétevője használható egy frissítést, ez a frissítés letöltése az internetről előtt tesz közzé egy helyi példányát. A helyen kell lennie az Updates Publishert futtató számítógép egyik mappájába. Alapértelmezés szerint ez a hely van **saját Documents\LocalSourcePublishing.** Akkor használja, ha már korábban letöltötte egy vagy több frissítést, vagy telepíteni kívánt frissítés módosítások történtek.

-   **Szoftverfrissítések karbantartása varázsló:** A frissítések karbantartása varázsló elindításához. A varázsló a frissítések, amelyek a frissítési kiszolgálóhoz, de nem a frissítés-közzétevő tárházban lejár. Lásd: [nem hivatkozott frissítések lejár](#expire-unreferenced-software-updates) további részleteket.

## <a name="updates"></a>Frissítések
 Frissítés-közzétevő automatikusan megkeresi az új frissítéseket minden alkalommal, amikor nyílik meg. Úgy is dönthet, azokat a frissítés-közzétevő előzetes buildjeit fogadását.

Manuálisan a frissítéseket, az Updates Publisher konzolján kattintson a ![tulajdonságai](media/properties2.png)  
lehetőségre a **frissítés-közzétevő tulajdonságai**, és válassza a **update keressen**.

Után az Updates Publisher új frissítést talál, megjelenik a **elérhető frissítés** ablakot, és választhat, hogy telepítse. Ha telepítette a frissítést, ajánlott a konzol következő megnyitásakor.

## <a name="logging"></a>Naplózás
Frissítés-közzétevő naplózza az Updates Publisherrel kapcsolatos alapvető információk  **&lt;* elérési*&gt;\Windows\Temp\UpdatesPublisher.log**.

Használja a Jegyzettömb vagy **CMTrace** a napló megtekintéséhez. CMTrace eszköz, a Configuration Manager napló fájlt, és itt található: a **\SMSSetup\Tools** mappában található a Configuration Manager forrás-adathordozóján.

A napló mérete és a részletességi szintje módosítható.

Adatbázis-naplózás engedélyezésekor szemben az Updates Publisher adatbázisában futó lekérdezések információk érhetők el. Adatbázis-naplózás használata a frissítés-közzétevő számítógép szűk vezethet.

A naplófájlban, a konzolon kattintson a ![tulajdonságok](media/properties2.png) megnyitásához a **frissítés-közzétevő tulajdonságai**, és válassza a **naplófájl megtekintése**.

## <a name="expire-unreferenced-software-updates"></a>Nem hivatkozott szoftverfrissítéseket lejár
Futtathatja a **Software Update karbantartása varázsló** frissítések, amelyek a frissítési kiszolgálón, de nem a frissítés-közzétevő tárházban lejár. Ez közli, hogy a Configuration Manager alkalmazást, amelyet majd eltávolítja azokat a frissítéseket az összes későbbi központi telepítését.

A folyamat, lejár a frissítést nem lehet visszavonni. Ha meggyőződött arról, hogy a kiválasztott szoftverfrissítések már nem szükséges a szervezet csak a feladat végrehajtásához.

### <a name="to-remove-expired-software-updates"></a>A lejárt szoftverfrissítések eltávolítása
1.  Az Updates Publisher konzolját, kattintson a ![tulajdonságok](media/properties2.png) megnyitásához a **frissítés-közzétevő tulajdonságai**, és válassza a **beállítások**.

2.  Válasszon **speciális**, majd a **szoftverfrissítési tiszta varázsló,** válasszon **Start**.

3.  Válassza ki azokat a szoftverfrissítéseket, lejár, és válassza a kívánt **következő**.

4.  Miután megtekintette a beállításokat, választott **következő** fogadja el a beállításokat, és ezek a frissítések lejár.

5.  A varázsló befejezése után válassza ki a **Bezárás** a varázsló befejezéséhez.

