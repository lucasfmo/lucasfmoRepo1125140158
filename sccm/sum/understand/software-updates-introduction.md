---

title: "Szoftverfrissítések bemutatása |} Microsoft Docs"
description: "A System Center Configuration Manager szoftverfrissítések alapismeretei."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: e9778b13-c8a3-40eb-8655-34ac8ce9cdaa
ms.translationtype: Machine Translation
ms.sourcegitcommit: d8cace9edd58e8fa438dbb43e54e57cd0dc55d2b
ms.openlocfilehash: 2904b904bbaf155f016f55fbd36af80308a42d76
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---
# <a name="introduction-to-software-updates-in-system-center-configuration-manager"></a>A System Center Configuration Manager szoftverfrissítéseinek bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager szoftverfrissítések biztosít eszközöket, és erőforrásokat kezelése követésének és az ügyfélszámítógépek számára a vállalati szoftverfrissítések alkalmazásának összetett feladatánál. A szoftverfrissítések célirányos felügyeleti folyamata szükséges a működési hatékonyság fenntartásához, a biztonsági problémák megelőzéséhez és a hálózati infrastruktúra stabilitásának fenntartásához. A technológia változó jellege és a folyamatosan felmerülő új biztonsági fenyegetések miatt azonban a szoftverfrissítések hatékony felügyelete következetes és folytonos figyelmet igényel.  

Egy példán keresztül bemutatja, hogyan helyezhetők üzembe szoftverfrissítéseket a környezetben, lásd: [biztonsági szoftverfrissítések központi telepítését. példa](../deploy-use/example-scenario-deploy-monitor-monthly-security-updates.md).  

##  <a name="BKMK_Synchronization"></a> Szoftverfrissítések szinkronizálása  
 A szoftverfrissítések szinkronizálását a Configuration Manager a Microsoft Update szoftverfrissítési metaadatok lekérése céljából kapcsolódik. A legfelső szintű hely (központi adminisztrációs hely vagy önálló elsődleges hely) szinkronizálása a Microsoft Update ütemezés szerint, vagy ha a szinkronizálás manuálisan is elindítható a Configuration Manager konzoljáról. A Configuration Manager befejezése után a szoftverfrissítések szinkronizálását a legfelső szintű helyen, elindul a szoftverfrissítések szinkronizálása alárendelt helyeken, ha vannak ilyenek. Amikor a szinkronizálás befejeződött minden elsődleges és másodlagos helyen, a rendszer a teljes helyre érvényes házirendet hoz létre, amely az ügyfélszámítógépek számára megadja a szoftverfrissítési pontok helyét.  

> [!NOTE]  
>  A szoftverfrissítések alapértelmezés szerint engedélyezve vannak az ügyfélbeállításokban. Ha viszont a **Szoftverfrissítések engedélyezése az ügyfeleken** ügyfélbeállításnál a szoftverfrissítések letiltásához a **Nem** értéket adja meg egy gyűjteményen vagy az alapértelmezett beállításoknál, a szoftverfrissítési pontok helyét nem küldi el a rendszer a kapcsolódó ügyfélgépeknek. További információkért lásd: [szoftverfrissítések ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md#software-updates).  

 Miután az ügyfél megkapta a házirendet, az ügyfél elindítja a szoftverfrissítések megfelelőségi vizsgálatát, és az adatokat a Windows Management Instrumentation (WMI) szolgáltatásba írja. Ezután a megfelelőségi adatokat a rendszer a felügyeleti pontba küldi, majd ezek elkerülnek a helykiszolgálóra. További információt a megfelelőségvizsgálatról a témakör [Software updates compliance assessment](#BKMK_SUMCompliance) című szakaszában talál.  

 Az elsődleges helyeken több szoftverfrissítési pontot telepíthet. Az elsőként telepített szoftverfrissítési pont a szinkronizálás forrásaként lesz konfigurálva. Ez szinkronizálja a Microsoft Update vagy a WSUS-kiszolgáló nem a Configuration Manager-hierarchiában. A helyen telepített további szoftverfrissítési pontok az első szoftverfrissítési pontot használják a szinkronizálás forrásaként.  

> [!NOTE]  
>  Amikor a szoftverfrissítések szinkronizálása befejeződött a legfelső szintű helyen, a szoftverfrissítések metaadatait – adatbázis-replikálás használatával – az alárendelt helyekre replikálja a rendszer. A Configuration Manager-konzolon való csatlakozáskor az alárendelt helyre, a Configuration Manager megjelenít a szoftverfrissítések metaadatait. Azonban amíg nem telepíti, és konfigurál szoftverfrissítési pontot ezen a helyen, az ügyfelek nem ellenőrzik a szoftverfrissítések megfelelőségét, nem jelentik a megfelelőségi adatokat a Configuration Manager és sikeresen nem szoftverfrissítések központi telepítését.  

### <a name="synchronization-on-the-top-level-site"></a>Szinkronizálás a legfelső szintű helyen  
 A legfelső szintű helyen a szoftverfrissítések szinkronizálási művelete lekéri a Microsoft Update webhelyről azoknak a szoftverfrissítéseknek a metaadatait, amelyek megfelelnek a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen megadott feltételeknek. Ezeket a feltételeket csak a legfelső szintű helyen konfigurálja.  

> [!NOTE]  
>  Megadhat egy létező WSUS-kiszolgálót, amely nem a Configuration Manager-hierarchiában, a szinkronizálás forrásaként a Microsoft Updates helyett.  

 A következő lista a legfelső szintű helyen végrehajtott szinkronizálási folyamat alapvető lépéseit ismerteti.  

1.  Elindul a szoftverfrissítések szinkronizálása.  

2.  A WSUS szinkronizáláskezelője kérelmet küld a szoftverfrissítési ponton futó WSUS szolgáltatásnak a Microsoft Update webhellyel való szinkronizálás elindításához.  

3.  Megtörténik a szoftverfrissítések metaadatainak szinkronizálása a Microsoft Update webhellyel, és a változások bekerülnek a WSUS adatbázisába.  

4.  Ha a WSUS befejezte a szinkronizálást, a WSUS szinkronizáláskezelője szinkronizálja a szoftverfrissítési metaadatokat a WSUS adatbázisból származó a Configuration Manager adatbázishoz, és a módosításokat az utolsó szinkronizálás után bekerülnek a hely adatbázisába. A szoftverfrissítések metaadatai konfigurációs elemként tárolódnak a helyadatbázisban.  

5.  A szoftverfrissítések konfigurációs elemeit – adatbázis-replikálás használatával – elküldi a rendszer az alárendelt helyekre.  

6.  Ha a szinkronizáció sikeresen befejeződött, a WSUS-szinkronizációkezelő a 6702-es számú állapotüzenetet adja vissza.  

7.  A WSUS szinkronizáláskezelője szinkronizálási kérelmet küld az összes alárendelt helynek.  

8.  A WSUS szinkronizáláskezelője egyenként kérelmet küld a hely más szoftverfrissítési pontjain futó WSUS szolgáltatásnak. A további szoftverfrissítési pontokon lévő WSUS-kiszolgálók a hely alapértelmezett szoftverfrissítési pontján futó WSUS replikájaként vannak konfigurálva.  

### <a name="synchronization-on-child-primary-and-secondary-sites"></a>Szinkronizálás alárendelt elsődleges és másodlagos helyen  
 A legfelső szintű helyen a szoftverfrissítések szinkronizálási folyamata során a szoftverfrissítések konfigurációs elemeit – adatbázis-replikálás használatával – az alárendelt helyekre replikálja a rendszer. A folyamat végén a legfelső szintű hely szinkronizálási kérelmet küld az alárendelt helynek, és az alárendelt hely elindítja a WSUS-szinkronizálást. A következő lista az alárendelt elsődleges helyen vagy másodlagos helyen végrehajtott szinkronizálási folyamat alapvető lépéseit ismerteti.  

1.  A WSUS szinkronizáláskezelője szinkronizálási kérelmet kap a legfelső szintű helyről.  

2.  Elindul a szoftverfrissítések szinkronizálása.  

3.  A WSUS szinkronizáláskezelője kérelmet küld a szoftverfrissítési ponton futó WSUS szolgáltatásnak a szinkronizálás elindításához.  

4.  Az alárendelt hely szoftverfrissítési pontján futó WSUS szinkronizálja a fölérendelt hely szoftverfrissítési pontján futó WSUS szolgáltatásból származó szoftverfrissítési metaadatokat.  

5.  Ha a szinkronizáció sikeresen befejeződött, a WSUS-szinkronizációkezelő a 6702-es számú állapotüzenetet adja vissza.  

6.  Egy elsődleges helyről a WSUS szinkronizáláskezelője szinkronizálási kérelmet küld az alárendelt másodlagos helyeknek. A másodlagos hely elindítja a szoftverfrissítések szinkronizálását a fölérendelt elsődleges hellyel. A másodlagos hely a fölérendelt helyen futó WSUS replikájaként van konfigurálva.  

7.  A WSUS szinkronizáláskezelője egyenként kérelmet küld a hely más szoftverfrissítési pontjain futó WSUS szolgáltatásnak. A további szoftverfrissítési pontokon lévő WSUS-kiszolgálók a hely alapértelmezett szoftverfrissítési pontján futó WSUS replikájaként vannak konfigurálva.  

##  <a name="BKMK_SUMCompliance"></a> Software updates compliance assessment  
 Mielőtt telepíti a frissítéseket az ügyfélszámítógépek számára a Configuration Manager alkalmazásban, indítsa el a szoftverfrissítések megfelelőségi vizsgálatát az ügyfélgépeken. Minden szoftverfrissítéshez állapotüzenetet hoz létre a rendszer, amely a frissítés megfelelőségi állapotát tartalmazza. Az állapotüzeneteket csoportosan a felügyeleti pontba, majd a helykiszolgálóra küldi a rendszer, ahol bekerülnek a helyadatbázisba. A szoftverfrissítések megfelelőségi állapota megjelenik a Configuration Manager konzolon. Szoftverfrissítések központi telepítését vagy telepítését frissítést igénylő számítógépeken hajthatja végre. A következő szakaszok a megfelelőségi állapotokat és a szoftverfrissítések megfelelőségi vizsgálatának folyamatát ismertetik.  

### <a name="software-updates-compliance-states"></a>Szoftverfrissítések megfelelőségi állapotai  
 A következő sorolja fel, és a Configuration Manager konzolján a szoftverfrissítéseknél megjelenő megfelelőségi állapotokat ismerteti.  

-   **Kötelező**  

     Azt jelenti, hogy a szoftverfrissítés alkalmazható és szükséges az ügyfélszámítógépen. A szoftverfrissítés állapota **Kötelező**lesz a következő feltételek bármelyikének teljesülésekor:  

    -   A szoftverfrissítés nem lett központilag telepítve az ügyfélszámítógépre.  

    -   A szoftverfrissítés telepítve lett az ügyfélszámítógépen. A legfrissebb állapotüzenet azonban még nem került be a helyrendszer adatbázisába. A telepítés befejezése után az ügyfélszámítógép újból keresi a frissítést. Akár két perc is eltelhet addig, amíg az ügyfélszámítógép elküldi a frissítve állapotot a felügyeleti pontra, amely ezután továbbítja ezt a helykiszolgálóra.  

    -   A szoftverfrissítés telepítve lett az ügyfélszámítógépen. A szoftverfrissítés telepítése azonban a számítógép újraindítását igényli a művelet befejezéséhez.  

    -   A szoftverfrissítés központilag telepítve lett az ügyfélszámítógépre, azonban az még nincs telepítve.  

-   **Nem szükséges**  

     Azt jelenti, hogy a szoftverfrissítés nem alkalmazható az ügyfélszámítógépen. Ezért a szoftverfrissítés nem szükséges.  

-   **Telepítve**  

     Azt jelenti, hogy a szoftverfrissítés alkalmazható az ügyfélszámítógépen, és az már telepítve van az ügyfélszámítógépen.  

-   **Ismeretlen**  

     Azt jelenti, hogy a helykiszolgáló még nem kapott állapotüzenetet az ügyfélszámítógépről, jellemzően a következő okok valamelyike miatt:  

    -   Az ügyfélszámítógépen sikertelen volt a szoftverfrissítések megfelelőségi vizsgálata.  

    -   A vizsgálat sikeresen befejeződött az ügyfélszámítógépen. Az állapotüzenet azonban még nem lett feldolgozva a helykiszolgálón, valószínűleg az állapotüzenet várakoztatása miatt.  

    -   A vizsgálat sikeresen befejeződött az ügyfélszámítógépen, de az állapotüzenet még nem érkezett meg az alárendelt helyről.  

    -   A vizsgálat sikeresen befejeződött az ügyfélszámítógépen, de az állapotüzenetet tartalmazó fájl sérült, és nem dolgozható fel.  

### <a name="scan-for-software-updates-compliance-process"></a>Szoftverfrissítések megfelelőségi vizsgálatának folyamata  
 Ha a szoftverfrissítési pont telepítve és szinkronizálva, a teljes helyre érvényes számítógép-házirendet, amely arról értesíti az ügyfélszámítógépeket, hogy a Configuration Manager szoftverfrissítések lettek-e engedélyezve a hely számára jön létre. Amikor egy ügyfélgép megkapja a számítógép-házirendet, a következő két órában véletlenszerű indítású megfelelőségi vizsgálat ütemezésére kerül sor. Amikor a vizsgálat elindult, a szoftverfrissítések ügyfélügynökének folyamata törli a vizsgálati előzményeket, és kérelmet küld a vizsgálatnál használandó WSUS-kiszolgáló kereséséhez, és a WSUS-kiszolgáló helyével frissíti a helyi csoportházirendet.  

> [!NOTE]  
>  Az internet alapú ügyfeleknek az SSL használatával kell kapcsolódniuk a WSUS-kiszolgálóhoz.  

 A rendszer vizsgálati kérést ad át a Windows Update Agent (WUA) ügynöknek. A WUA ezután csatlakozik a WSUS-kiszolgáló helyi házirendben feltüntetett helyéhez, lekéri a WSUS-kiszolgálón szinkronizált szoftverfrissítési metaadatokat, és megvizsgálja, hogy az ügyfélszámítógépen megtalálhatók-e a frissítések. A Szoftverfrissítések ügyfélügynökének egyik folyamat észleli, hogy a megfelelőségi vizsgálat befejeződött, és állapotüzeneteket hoz létre minden olyan szoftverfrissítéshez, amelynek a megfelelőségi állapota a legutóbbi vizsgálat óta megváltozott. Ezeket az állapotüzeneteket a rendszer 15 percenként összesítve elküldi a felügyeleti pontnak. A felügyeleti pont ezután a helykiszolgálónak továbbítja az állapotüzeneteket, ahol azok a helykiszolgáló adatbázisába kerülnek.  

 A szoftverfrissítések megfelelőségének első vizsgálatát követően a további vizsgálatok a beállított vizsgálati ütemezésnek megfelelően zajlanak. Ha azonban az ügyfél az élettartam (TTL) értéke által jelzett időszakban már megvizsgálta a szoftverfrissítések megfelelőségét, abban az esetben a helyben tárolt szoftverfrissítési metaadatokat fogja használni. Ha a legutóbbi vizsgálat kívül esik az élettartamon, az ügyfélnek csatlakoznia kell a szoftverfrissítési ponton futó WSUS szolgáltatáshoz, és frissítenie kell az ügyfélen tárolt szoftverfrissítési metaadatokat.  

 A szoftverfrissítések megfelelőségi vizsgálata az alábbi módokon indulhat el (az ütemezett vizsgálatokat is beleértve):  

-   **Ütemezett szoftverfrissítési vizsgálat**: A szoftverek keresése Software Updates Client Agent beállításaiban konfigurált beállított vizsgálati ütemezés szerint kezdődik megfelelőségi frissíti. A szoftverfrissítések ügyfélbeállításainak konfigurálásával kapcsolatos további információkért lásd: [szoftverfrissítések ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md#software-updates).  

-   **A Configuration Manager – tulajdonságok párbeszédpanel műveleteivel**: Elindíthat a **szoftverfrissítések keresésének ciklusa** vagy **szoftver központi telepítésének kiértékelési ciklusa** műveletet alkalmazza a **művelet** lapra a **Configuration Manager – tulajdonságok** párbeszédpanel az ügyfélszámítógépen.  

-   **Központi telepítés újraértékelésének ütemezése**: A központi telepítés értékelése és a szoftverek keresését frissítések megfelelőségi kezdődik, és a beállított újraértékelési ütemezés szerint, amely a szoftverfrissítések Ügyfélügynöke beállításainál konfigurálható. A szoftverfrissítések ügyfélbeállításainak kapcsolatos további információkért lásd: [szoftverfrissítések ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md#software-updates).  

-   **Frissítési fájlok letöltése előtt**: Egy ügyfélszámítógépre egy új kötelező központi telepítés kapcsán hozzárendelési házirendet kap, amikor a szoftverfrissítések Ügyfélügynöke letölti a szoftverfrissítési fájlokat az ügyfél helyi gyorsítótárába. A szoftverfrissítési fájlok letöltése előtt az ügyfélügynök megvizsgálja, hogy a szoftverfrissítés továbbra is szükséges-e.  

-   **Szoftver előtt frissítse a telepítési**: A telepítés előtt a szoftverfrissítések Ügyfélügynöke egy vizsgálattal meggyőződik arról, hogy továbbra is szükség-e a szoftverfrissítések elindul.  

-   **Szoftver követően frissítse a telepítési**: Csak egy szoftverfrissítés telepítésének befejezése után a szoftverfrissítések Ügyfélügynöke egy vizsgálattal meggyőződik arról, hogy a szoftverfrissítések már nem szükségesek, és létrehoz egy új állapotüzenetet arról, hogy telepítve van-e a szoftverfrissítés indítja el. Ha a telepítés befejeződött, viszont még újraindítás szükséges, az állapotüzenet azt jelzi, hogy az ügyfélszámítógép újraindításra vár.  

-   **Rendszer újraindítása után**: Amikor egy ügyfélszámítógép a rendszer újraindítására vár a szoftver a frissítés telepítésének véglegesítéséhez, a szoftverfrissítések ügyfélügynöke egy vizsgálatot az újraindítás győződjön meg arról, hogy a szoftverfrissítés már nincs szükség, és létrehoz egy állapotüzenetet arról, hogy a szoftverfrissítés telepítése után.  

#### <a name="time-to-live-value"></a>Élettartam  
 A szoftverfrissítési megfelelőség vizsgálatához szükséges szoftverfrissítési metaadatok a helyi ügyfélszámítógépen tárolódnak, és alapértelmezés szerint 24 óráig érvényesek. Ez az érték az ún. élettartam (Time to Live, TTL).  

#### <a name="scan-for-software-updates-compliance-types"></a>A szoftverfrissítések megfelelőségi vizsgálatának típusai  
 Az ügyfél a vizsgálat indítási módjától függően online vagy offline, illetve kényszerített vagy nem kényszerített módszerrel ellenőrzi a szoftverfrissítési megfelelőséget. Az alábbiak azt ismertetik, és a-e a vizsgálat a kényszerített vagy nem kényszerített vizsgálat indul módok esetén online vagy offline.  

-   **Ütemezett szoftverfrissítési vizsgálat** (nem kényszerített online vizsgálat)  

     Az ügyfél a beállított vizsgálati ütemezés szerint csak akkor kapcsolódik a szoftverfrissítési ponton futó WSUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése céljából, ha a legutóbbi vizsgálat az élettartamon kívül esik.  

-   **Szoftverfrissítések keresésének ciklusa** vagy **szoftver központi telepítésének kiértékelési ciklusa** (kényszerített online vizsgálat)  

     Az ügyfélszámítógép minden esetben kapcsolódik a szoftverfrissítési ponton futó WSUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése céljából, mielőtt ellenőrizné a szoftverfrissítések megfelelőségét. A vizsgálat befejezését követően a rendszer visszaállítja az élettartam számlálóját. Ha például az élettartam 24 óra, a szoftverfrissítési megfelelőség vizsgálatának felhasználói indítását követően az élettartam visszaáll 24 órára.  

-   **Központi telepítés újraértékelésének ütemezése** (nem kényszerített online vizsgálat)  

     Az ügyfél a központi telepítés újraértékelésének beállított ütemezése szerint csak akkor kapcsolódik a szoftverfrissítési ponton futó WSUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése céljából, ha a legutóbbi vizsgálat az élettartamon kívül esik.  

-   **Frissítési fájlok letöltése előtt** (nem kényszerített online vizsgálat)  

     A kötelező központi telepítések frissítési fájljainak letöltése előtt az ügyfél csak akkor kapcsolódik a szoftverfrissítési ponton futó WSUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése céljából, ha a legutóbbi vizsgálat az élettartamon kívül esik.  

-   **Szoftver előtt frissítse a telepítési** (nem kényszerített online vizsgálat)  

     A kötelező központi telepítések szoftverfrissítéseinek telepítése előtt az ügyfél csak akkor kapcsolódik a szoftverfrissítési ponton futó WUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése céljából, ha a legutóbbi vizsgálat az élettartamon kívül esik.  

-   **Szoftver követően frissítse a telepítési** (kényszerített offline vizsgálat)  

     A szoftverfrissítések telepítését követően a Szoftverfrissítések ügyfélügynöke vizsgálatot indít a helyi metaadatok alapján. Az ügyfél ebben az esetben nem kapcsolódik a szoftverfrissítési ponton futó WSUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése érdekében.  

-   **Rendszer újraindítása után** (kényszerített offline vizsgálat)  

     A szoftverfrissítések telepítését és a számítógép újraindítását követően a Szoftverfrissítések ügyfélügynöke vizsgálatot indít a helyi metaadatok alapján. Az ügyfél ebben az esetben nem kapcsolódik a szoftverfrissítési ponton futó WSUS szolgáltatáshoz a szoftverfrissítési metaadatok lekérése érdekében.  

##  <a name="BKMK_DeploymentPackages"></a> Szoftverfrissítések központi telepítési csomagjai  
 A rendszer szoftverfrissítési központi telepítési csomagok formájában tölti le a szoftverfrissítéseket egy megosztott hálózati mappába, majd ilyen formában másolja a szoftverfrissítések forrásfájljait a központi telepítésben definiált helykiszolgálókon és terjesztési pontokon lévő tartalomtárakba. A Frissítések letöltése varázsló segítségével szoftverfrissítéseket tölthet le, és központi telepítési csomagokhoz adhatja őket a telepítésük előtt. A varázslóval szoftverfrissítéseket helyezhet el a terjesztési pontokon, és ellenőrizheti a központi telepítési folyamat ezen részének sikerességét, mielőtt a szoftverfrissítéseket az ügyfelekre telepítené.  

 Amikor a Szoftverfrissítések központi telepítése varázslóval telepíti a letöltött szoftverfrissítéseket, a központi telepítéshez a rendszer automatikusan a szoftverfrissítéseket tartalmazó központi telepítési csomagot fogja használni. Ha olyan szoftverfrissítéseket telepít, amelyek korábban nem lettek letöltve, a Szoftverfrissítések központi telepítése varázslóban meg kell adnia egy új vagy egy meglévő központi telepítési csomagot. A rendszer a varázsló bezárásakor letölti a szoftverfrissítéseket.  

> [!IMPORTANT]  
>  Mielőtt a varázslóban megadná a csomagot, manuálisan kell létrehoznia a megosztott hálózati mappát a központi telepítőcsomag forrásfájljai számára. Minden központi telepítőcsomagnak külön megosztott hálózati mappát kell használnia.  

> [!IMPORTANT]  
>  Az SMS-szolgáltató számítógépfiókjának és a szoftverfrissítést ténylegesen letöltő rendszergazdának egyaránt **írási** engedéllyel kell rendelkezniük a csomag forrásához. Célszerű korlátozni a hozzáférést a csomag forrásához – ezzel csökkenthető a kockázata, hogy támadók illetéktelenül módosítsák a szoftverfrissítések forrásfájljait a csomag forráshelyén.  

 Új központi telepítőcsomag létrehozásakor a rendszer 1-esre állítja a tartalomverziót, még a szoftverfrissítések letöltése előtt. Amikor a csomagba szoftverfrissítési fájlokat tölt le, a tartalomverzió 2-es értékre növekszik. Ennek megfelelően minden új központi telepítőcsomag 2-es tartalomverzióval fog rendelkezni. Minden alkalommal, amikor a központi telepítőcsomag tartalma változik, a rendszer eggyel növeli a tartalomverziót. További információkért lásd: [a Tartalomkezelés alapvető fogalmai](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

 Az ügyfelek a központi telepítésekben lévő szoftverfrissítések telepítéséhez bármely olyan terjesztési pontot használhatják, amelyen elérhetők a szükséges szoftverfrissítések, a telepítőcsomagtól függetlenül. Az ügyfelek tehát akkor is telepíthetik a szoftverfrissítéseket, ha az aktív központi telepítés csomagját törölték, feltéve, hogy az egyes frissítések legalább egy másik központi telepítőcsomagba le vannak töltve, és rendelkezésre állnak az ügyfél által elérhető terjesztési pontok valamelyikén. Ha egy szoftverfrissítés legutóbbi központi telepítőcsomagját törölték, az ügyfélszámítógépek csak akkor tudják lekérni a szoftverfrissítést, ha a frissítést a rendszergazda újra letölti egy központi telepítőcsomagba. A Configuration Manager konzolon piros nyíl szoftverfrissítések jelennek meg, ha a frissítési fájlok nem központi telepítőcsomagban sem. Az ilyen frissítéseket tartalmazó központi telepítéseket dupla piros nyíl jelöli.  

##  <a name="BKMK_DeploymentWorkflows"></a> Szoftverfrissítések központi telepítési munkafolyamatai  
 A szoftverfrissítések központi telepítése alapvetően kétféle módon történhet a környezetben: manuális, illetve automatikus telepítéssel. Az ügyfélszámítógépek alapkonfigurációjának kialakításához jellemzően manuális központi szoftverfrissítést használnak, ezt követően viszont automatikus módon kezelik a szoftverfrissítéseket az ügyfeleken. Az alábbi szakaszok összefoglalást nyújtanak a szoftverfrissítések manuális és automatikus központi telepítésének munkafolyamatáról.  

###  <a name="BKMK_ManualDeployment"></a> Szoftverfrissítések manuális központi telepítése  
 A szoftverfrissítések manuális központi telepítésének szoftverfrissítések kiválasztása a Configuration Manager konzolon, és manuálisan kell elindítania a központi telepítési folyamat során a rendszer. Ez a telepítési módszer jellemzően az ügyfélszámítógépek kötelező szoftverfrissítésekkel való ellátására szolgál a naprakész működés érdekében, mielőtt automatikus központi telepítési szabályokat hozna létre a rendszeres havi szoftverfrissítések telepítéséhez, illetve a „sávon kívüli” szoftverfrissítési követelmények teljesítéséhez. Az alábbi lista ismerteti a szoftverfrissítések manuális központi telepítésének általános folyamatát:  

1.  Konkrét követelmények szerint szűrje a szoftverfrissítéseket. A megfelelő feltételek megadásával lekérheti például az összes olyan biztonsági és kritikus szoftverfrissítést, amelyre több mint 50 ügyfélszámítógépen szükség van.  

2.  Hozzon létre egy szoftverfrissítési csoportot, amely a kívánt szoftverfrissítéseket tartalmazza.  

3.  Töltse le a szoftverfrissítésekhez kapcsolódó tartalmat a szoftverfrissítési csoportba.  

4.  Manuális módszerrel végezze el a szoftverfrissítési csoport központi telepítését.  

###  <a name="BKMK_AutomaticDeployment"></a> Szoftverfrissítések automatikus központi telepítése  
 A szoftverfrissítések automatikus központi telepítése automatikus központi telepítési szabályokkal konfigurálható. Ez a központi telepítési módszer jellemzően a havi szoftverfrissítések telepítésére („Frissítő kedd”) és a definíciófrissítések kezelésére szolgál. A szabály futtatásakor a megadott feltételeknek megfelelő szoftverfrissítéseket (például az előző héten megjelent biztonsági szoftverfrissítéseket) a rendszer felveszi egy szoftverfrissítési csoportba, a szoftverfrissítésekhez tartozó tartalomfájlokat letölti és a terjesztési pontokra másolja, majd központilag telepíti a szoftverfrissítéseket a célgyűjtemény ügyfélszámítógépein. Az alábbi lista a szoftverfrissítések automatikus központi telepítésének általános folyamatát ismerteti:  

1.  Egy automatikus központi telepítési szabály létrehozásával adja meg a központi telepítés alábbi beállításait:  

    -   A célgyűjteményt  

    -   Azt, hogy engedélyezni szeretné-e a központi telepítést, vagy jelentést kér-e a célgyűjteményhez tartozó ügyfélszámítógépek szoftverfrissítési megfelelőségéről  

    -   A szoftverfrissítési feltételeket  

    -   Az értékelési és központi telepítési ütemezéseket  

    -   A felhasználói felületet  

    -   A letöltési tulajdonságokat  

2.  A rendszer felveszi a szoftverfrissítéseket egy szoftverfrissítési csoportba.  

3.  A rendszer a célgyűjtemény ügyfélszámítógépein telepíti a szoftverfrissítési csoportot, ha a célgyűjtemény meg van adva.  

 Meg kell határoznia, hogy milyen központi telepítési stratégiát kíván használni a környezetében. Az automatikus központi telepítési szabály létrehozását követően például tesztelési célú gyűjteményt is kijelölhet ügyfélszámítógépekből. Miután meggyőződött arról, hogy a szoftverfrissítéseket sikerült telepíteni a tesztcsoport tagjain, új központi telepítést adhat a szabályhoz, vagy bővebb ügyfélkört határozhat meg célgyűjteményként az a meglévő központi telepítésben. Az automatikus központi telepítési szabályok interaktív szoftverfrissítési objektumokat hoznak létre.  

-   Az automatikus központi telepítési szabállyal telepített szoftverfrissítéseket a rendszer automatikusan telepíti a célgyűjteménybe felvett új ügyfelekre is.  

-   A szoftverfrissítési csoportba felvett új szoftverfrissítéseket a rendszer automatikusan telepíti a célgyűjtemény ügyfélszámítógépein.  

-   Az automatikus központi telepítési szabályhoz kapcsolódó központi telepítések bármikor engedélyezhetők és letilthatók.  

 Az automatikus központi telepítési szabály létrehozása után további központi telepítéseket is hozzáadhat a szabályhoz. Ennek segítségével egyszerűbben felügyelheti a különböző frissítések különböző gyűjteményekbe történő központi telepítését. Minden egyes új központi telepítés rendelkezik az összes funkcióval, és a központi telepítés figyelésének lehetőségével. A hozzáadott új központi telepítések:  

-   Ugyanazt a frissítési csoportot és csomagot használják, amelyet a rendszer az ADR első futásakor létrehoz.  

-   Különböző gyűjteményeket adhatnak meg.  

-   Egyedi központi telepítési tulajdonságokat támogatnak, beleértve:  

    -   aktiválás ideje,  

    -   határidő,  

    -   végfelhasználói felület megjelenítése vagy elrejtése,  

    -   a központi telepítéshez tartozó külön riasztások.  

##  <a name="BKMK_DeploymentProcess"></a> Szoftverfrissítések központi telepítési folyamata  
 Miután manuális módszerrel vagy egy automatikus központi telepítési szabály futtatásával szoftverfrissítéseket telepít, a rendszer egy központitelepítés-hozzárendelési szabályt vesz fel a helyhez tartozó számítógép-házirendbe. Letölti a szoftverfrissítéseket a letöltési helyről – az internetről vagy egy megosztott hálózati mappából – a csomag forrásába, onnan pedig a helykiszolgáló tartalomtárába, majd a terjesztési ponton lévő tartalomtárba másolja a szoftverfrissítéseket.  

 Ha a központi telepítés célgyűjteményének egyik ügyfélszámítógépe megkapja a számítógép-házirendet, a szoftverfrissítési ügyfélügynök megkezdi az értékelést. Az ügyfélügynök letölti a szükséges szoftverfrissítésekhez a tartalmat egy terjesztési pontból a helyi ügyfélgyorsítótárba, amint megkapta a központi telepítési feladatot, de a **Szoftver rendelkezésre állási ideje** beállításban megadott ideig vár a szoftverfrissítések elérhetővé tételével. A választható telepítések szoftverfrissítéseit (azok a telepítések, amelyekhez nincs telepítési határidő hozzárendelve) addig nem tölti le a rendszer, amíg a felhasználó manuálisan el nem kezdi a telepítést.  

 A konfigurált határidő elérése után a szoftverfrissítési ügyfélügynök ellenőrzi, hogy a szoftverfrissítések még mindig szükségesek-e. Ezt követően ellenőrzi az ügyfélszámítógép helyi gyorsítótárában, hogy a szoftverfrissítési forrásfájlok még mindig elérhetők-e. Az ügynök utolsó lépésként telepíti a szoftverfrissítéseket. Ha az ügyfélgyorsítótár tartalmát törölték, hogy másik központi telepítésnek biztosítsanak helyet, az ügyfél ismételten letölti a szoftverfrissítéseket a terjesztési pontból az ügyfélgyorsítótárba. A szoftverfrissítéseket mindig az ügyfélgyorsítótárba tölti le a rendszer függetlenül annak maximális konfigurált méretétől. Ha a telepítés befejeződött, az ügyfeleken futó ügynök megerősíti, hogy a szoftverfrissítésekre már nincs szükség, majd állapotjelző üzenetet küld a felügyeleti pontnak, amely jelzi, hogy a szoftverfrissítések telepítve vannak az ügyfélre.  

### <a name="required-system-restart"></a>Szükséges rendszer-újraindítás  
 Alapértelmezés szerint ha szükséges központi telepítés szoftverfrissítéseit telepítik egy ügyfélszámítógépre, és a telepítés befejezéséhez rendszer-újraindítás szükséges, a rendszer újraindul. A határidő előtt telepített szoftverfrissítések esetében az automatikus rendszer-újraindításra a határidő lejártakor kerül sor, kivéve, ha bármilyen más okból azt megelőzően újra kell indítani a számítógépet. A rendszer-újraindítástól el lehet tekinteni kiszolgálók és munkaállomások esetében. Ezek a beállítások a Szoftverfrissítések központi telepítése varázsló vagy az Automatikus frissítési szabályok létrehozása varázsló **Felhasználói élmény** oldalán konfigurálhatók.  

### <a name="deployment-reevaluation-cycle"></a>A központi telepítés újrakiértékelési ciklusa  
 Az ügyfélszámítógépek alapértelmezés szerint 7 naponta indítják el a központi telepítés újrakiértékelési ciklusát. Ezalatt az ügyfélszámítógép korábban telepített szoftverfrissítéseket keres. A hiányzó szoftverfrissítéseket újratelepíti a helyi gyorsítótárból. Ha egy adott frissítés már nincs a helyi gyorsítótárban, a számítógép letölti egy terjesztési pontról, majd telepíti. A hely újrakiértékelési ütemezése az ügyfélbeállítások között, a **Szoftverfrissítések** oldalon konfigurálható.  

##  <a name="BKMK_EmbeddedDevices"></a> Írási szűrőket használó Windows Embedded-eszközök támogatása  
 Írási szűrőket használó Windows Embedded-eszközök szoftverfrissítéseinek központi telepítése esetén megadható, hogy az írási szűrő le legyen-e tiltva az eszközön a telepítés során, majd a telepítést követően újraindítható az eszköz. Ha az írási szűrő nincs letiltva, a szoftver központi telepítése átmeneti területre történik, és telepítésére nem kerül sor, ha az eszköz újraindul, hacsak egy másik központi telepítési művelet a változtatások megőrzésére nem kényszeríti a rendszert.  

> [!NOTE]  
>  Amikor szoftverfrissítést telepít egy Windows Embedded eszközön, győződjön meg arról, hogy az eszköz olyan gyűjtemény tagja, amely rendelkezik beállított karbantartási időszakkal. Ilyen módon felügyelheti, hogy az írási szűrő mikor van letiltva és engedélyezve, és az eszköz mikor indul újra.  

 Az írási szűrő viselkedésének vezérlésére **A változtatások véglegesítése a határidő lejártakor vagy karbantartási időszakban (újraindítást igényel)**jelölőnégyzettel jelölt felhasználóiélmény-beállítás szolgál.  

 További információ a Configuration Manager hogyan kezeli az írási szűrőket használó beágyazott eszközöket: [ügyfelek Windows Embedded-eszközökre való központi telepítésének tervezése](../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

##  <a name="BKMK_ExtendSoftwareUpdates"></a> A szoftverfrissítések kibővítése a Configuration Managerben  
 System Center Updates Publisher használatával, amelyek nem érhetők el a Microsoft Update-szoftverfrissítések kezelése. Miután közzétenni a szoftverfrissítések a frissítési kiszolgáló és a szoftverfrissítések szinkronizálása a Configuration Manager, a szoftverfrissítések telepítene Configuration Manager-ügyfelek. Az Updates Publisherrel kapcsolatos további információkért lásd: [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=252947).  

## <a name="next-steps"></a>További lépések
[Szoftverfrissítések tervezése](../plan-design/plan-for-software-updates.md)

