---
title: "Alkalmazáshasználat figyelése a szoftverhasználat-mérés |} Microsoft Docs"
description: 
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1fdaee2-2816-4447-94cd-609f6948f215
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a85a5cece803e5c16da71f897d5780049fbb82cd
ms.openlocfilehash: eddf20bebd80028336503957dfc4c3d1dbbb23f2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="software-metering-in-system-center-configuration-manager"></a>A szoftverhasználat-mérés a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a System Center Configuration Manager szoftverhasználat-mérés használata esetén előfordulhat, hogy elvégezhető műveleteket a hivatkozást tartalmaz.

> [!IMPORTANT]
>  A szoftverhasználat-mérés a Windows rendszerű számítógépek **.exe**fájlkiterjesztésű asztali alkalmazásainak figyelésére használható. A szoftverhasználat-mérés a modern (például a Windows 8 által használt) Windows-alkalmazásokat nem figyeli.

##  <a name="prerequisites-for-software-metering"></a>A szoftverhasználat-mérés előfeltételei
A szoftverhasználat-mérésnek nincsenek külső függőségei, csak a terméken belüli függőségei.

|Függőség|További információ|
|----------------|----------------------|
|A szoftverhasználat-méréshez tartozó ügyfélbeállítások|A szoftverhasználat-mérés használatához engedélyezni és telepíteni kell a számítógépeken a **Szoftverhasználat mérésének engedélyezése az ügyfeleken** ügyfélbeállítást. A szoftverhasználat-mérési beállításokat telepítheti a hierarchiában lévő összes számítógépre, vagy telepíthet egyéni beállításokat számítógépek csoportjaira. Lásd: **szoftverhasználat-mérés konfigurálása** ebben a témakörben.|
|A jelentéskészítési szolgáltatási pont|A szoftverhasználat-mérési jelentésék megtekintéséhez konfigurálnia kell egy jelentéskészítési szolgáltatási pontot. További információ: [Jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md).|

##  <a name="configure-software-metering"></a>Szoftverhasználat-mérés konfigurálása
 Ezzel az eljárással konfigurálhatja a szoftverhasználat-mérés alapértelmezett ügyfélbeállításait, és alkalmazhatja azokat a hierarchia minden számítógépére. Ha ezeket a beállításokat csak néhány számítógépen szeretné alkalmazni, hozzon létre egyéni ügyfél-eszközbeállítást és rendelje hozzá egy gyűjteményhez, amely tartalmazza a számítógépeket, melyeken szoftverhasználat-mérést szeretne használni. Egyéni Eszközbeállítás létrehozásáról további információk: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.

2.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.

3.  Az **Alapértelmezett beállítások** párbeszédpanelen kattintson a **Szoftverhasználat-mérés**elemre.

4.  Az **Eszközbeállítások** listában állítsa be a következőket:

    -   **Szoftverhasználat mérésének engedélyezése az ügyfelek**: Válassza ki **igaz** szoftverhasználat-mérés engedélyezéséhez.

    -   **Adatgyűjtés ütemezése**: Milyen gyakran konfigurálása az ügyfélszámítógépekről gyűjtött szoftverhasználat-mérési adatokat. Használja az alapértelmezett **7 nap** értéket, vagy az **Ütemezés** lehetőségre kattintva adjon meg egyéni ütemezést.

5.  Kattintson az **OK** gombra az **Alapértelmezett beállítások** párbeszédpanel bezárásához.

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egy ügyfél házirend lekérésének kezdeményezéséhez, lásd: [ügyfelek kezelése](../../core/clients/manage/manage-clients.md).

##  <a name="create-software-metering-rules"></a>Szoftverhasználat-mérési szabályok létrehozása
 A szoftver mérési szabály létrehozása varázsló segítségével hozzon létre egy új szoftverhasználat-mérési szabály a Configuration Manager-helyhez.

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **szoftverhasználat-mérés**.

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Szoftverhasználat-mérési szabály létrehozása**lehetőségre.

4.  Az a **általános** lap a szoftverhasználat-mérés szabály létrehozása varázslóban adja meg a következő adatokat:

    -   **Név** : a szoftverhasználat-mérési szabály neve. Ennek egyedinek és leírónak kell lennie.

        > [!NOTE]
        >  A szoftverhasználat-mérési szabályok rendelkezhetnek egyforma névvel, amennyiben a szabályokban megadott fájlnevek eltérőek.

    -   **Fájlnév** : A mérni kívánt programfájl neve. A **Tallózás** lehetőségre kattintva megjelenítheti a **Megnyitás** párbeszédpanelt, melyben kiválaszthatja a használni kívánt programfájlt.

        > [!NOTE]
        >  Ha a végrehajtható fájl nevét beírja a **Fájlnév** mezőbe, a rendszer semmilyen ellenőrzést nem végez annak meghatározására, hogy a fájl létezik-e és tartalmazza-e a szükséges fejlécadatokat. Ha lehetséges, kattintson a **Tallózás** lehetőségre, és válassza ki a mérni kívánt végrehajtható fájlt.
        >
        >  A helyettesítő karakterek használata nem engedélyezett a fájlnévben.
        >
        >  Ez a mező nem kötelező, ha az **Eredeti fájlnév** mező értéke meg van adva.

    -   **Eredeti fájlnév** : A mérni kívánt végrehajtható fájl neve. Ez a név a fájl fejlécében megadott adatoknak felel meg, nem pedig magával a fájlnévvel egyezik meg, így olyan esetekben lehet hasznos, melyekben a végrehajtható fájl át lett nevezve, de az eredeti néven szeretné mérni azt.

        > [!NOTE]
        >  A helyettesítő karakterek használata nem engedélyezett az eredeti fájlnévben.
        >
        >  Ez a mező nem kötelező, ha a **Fájlnév** mező értéke meg van adva.

    -   **Verzió** : a mérni kívánt végrehajtható fájl verziója. A (*) helyettesítő karakterrel bármilyen tetszőleges karakterláncot, a (?) helyettesítő karakterrel pedig egyetlen tetszőleges karaktert jelölhet. Ha szeretné egy végrehajtható fájl összes verzióját mérni, használja az alapértelmezett értéket (\*).

    -   **Nyelv** : a mérni kívánt végrehajtható fájl nyelve. Az alapértelmezett értéke a használt operációs rendszer aktuális területi beállítása. Ha a **Tallózás** gombra kattintva választ ki egy mérni kívánt végrehajtható fájlt, a rendszer automatikusan kitölti ezt a mezőt a fájl fejlécében található nyelvi adatokkal. Ha egy fájl összes nyelvi verzióját mérni szeretné, válassza ki a **Bármely** lehetőséget a legördülő listában.

    -   **Leírás** : a szoftverhasználat-mérési szabály opcionális leírása.

    -   **A szoftverhasználat-mérési szabály alkalmazása a következő ügyfelekre** : adja meg, hogy a szoftverhasználat-mérési szabályt a hierarchiában lévő összes ügyfélre, vagy a megadott helyhez a **Hely** listában hozzárendelt ügyfelekre szeretné alkalmazni.

5.  A folytatáshoz kattintson a **Tovább**gombra.

6.  Tekintse át és hagyja jóvá a beállításokat, majd fejezze be a varázslót a szoftverhasználat-mérési szabály létrehozásához. Az új szoftverhasználat-mérési szabály megjelenik a **Szoftverhasználat-mérés** csomópontban az **Eszközök és megfelelőség** munkaterületen.

##  <a name="configure-automatic-software-metering-rules"></a>Automatikus szoftverhasználat-mérési szabályok konfigurálása
 Konfigurálhatja a szoftverhasználat-mérés a Configuration Manager automatikusan létre letiltott szoftverhasználat-mérési szabályokat a helyadatbázisban tárolt legutóbbi használati leltár adataiból. Ezeket a leltári adatokat konfigurálhatja úgy, hogy csak a számítógépek egy adott százalékán használt alkalmazásokhoz jöjjenek létre mérési szabályok. Emellett megadhatja a helyen automatikusan létrehozott szoftverhasználat-mérési szabályok megengedett maximális számát is.

> [!NOTE]
>  Alapértelmezés szerint az automatikusan létrehozott szoftverhasználat-mérési szabályok le vannak tiltva. Ahhoz, hogy megkezdhesse a szabályok használati adatainak gyűjtését, engedélyeznie kell azokat.

1.  A Configuration Manager konzolon kattintson **eszközök és megfelelőség** > **szoftverhasználat-mérés**, majd a a **Home** lap a **beállítások** csoportjában kattintson a **szoftverhasználat-mérés tulajdonságai**.

3.  A **Szoftverhasználat-mérés tulajdonságai** párbeszédpanelen állítsa be a következőket:

    -   **Adatok megőrzése (napokban)** : a szoftverhasználat-mérés által létrehozott adatok a helyadatbázisban való megőrzésének időtartamát határozza meg. Az alapértelmezett érték **90** nap.

    -   Engedélyezze **A letiltott mérési szabályok automatikus létrehozása a legutóbbi használati leltár adataiból**beállítást.

    -   **Adja meg a hierarchia számítógépeinek százalékarányát, amelyeknek használniuk kell egy adott programot ahhoz, hogy a rendszer automatikusan létrehozzon egy szoftverhasználat-mérési szabályt** : az alapértelmezett érték **10** százalék.

    -   **Adja meg a szoftverhasználat-mérési szabályok számát a hierarchiában, amelyet meghaladva a rendszer letiltja a szabályok automatikus létrehozását** : az alapértelmezett érték **100** szabály.

4.  A **Szoftverhasználat-mérés tulajdonságai** párbeszédpanel bezárásához kattintson az **OK** gombra.

##  <a name="manage-software-metering-rules"></a>Szoftverhasználat-mérési szabályok kezelése
 Az **Eszközök és megfelelőség** munkaterületen válassza a **Szoftverhasználat-mérés**lehetőséget, és válassza ki a kezelni kívánt szoftverhasználat-mérési szabályt, majd egy kezelési feladatot.

 A következő táblázat használatával további információt kaphat azokról a kezelési feladatokról, amelyek kiválasztása előtt még tájékozódni szeretne.

|Kezelési feladat|Részletek|
|---------------------|-------------|
|**Engedélyezés**<br /><br /> **Letiltás**|Egy szoftverhasználat-mérési szabály engedélyezése vagy letiltása. Ez a beállítás az ügyfélbeállítások **Ügyfélházirend** szakaszában megadott **Ügyfélházirend lekérdezési időköze** beállításnak megfelelően (alapértelmezés szerint 60 percenként) töltődik le az ügyfélszámítógépekre.<br /><br /> Lásd: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md) .|

##  <a name="monitor-software-metering"></a>Szoftverhasználat-mérés figyelése
 A szoftverhasználat-mérés a Configuration Manager számos olyan beépített jelentéseket, amelyek lehetővé teszik a szoftver mérési műveleteire vonatkozó információk figyelését. Ezek a jelentések a **Szoftverhasználat-mérés**jelentéskategóriába tartoznak.

 Jelentéskészítés a Configuration Managerben konfigurálásával kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).

 Ezenkívül létrehozhat lekérdezéseket és gyűjteményeket a szoftverhasználat-mérés által a Configuration Manager-adatbázisban tárolt adatok alapján.

 További információ a Configuration Manager-gyűjtemények: [gyűjteményeinek bemutatása](/sccm/core/clients/manage/collections/introduction-to-collections).

 A Configuration Manager-lekérdezésekkel kapcsolatos további információkért lásd: [Bevezetés a lekérdezésekbe](/sccm/core/servers/manage/introduction-to-queries).

##  <a name="security-and-privacy-for-software-metering"></a>Biztonság és adatvédelem a szoftverhasználat-mérés

### <a name="security-issues-for-software-metering"></a>A szoftverhasználat-mérés biztonsági problémái
 A támadó érvénytelen szoftverhasználat-mérési adatokat a Configuration Manager, amelyek elfogadják a felügyeleti pont akkor is, ha a szoftverhasználat-mérési ügyfélbeállítás le van tiltva. A hierarchiában, szolgáltatásmegtagadást okozó, és a Configuration Manager helyrendszer-kiszolgálókon replikált mérési szabályok nagy számú eredményezhet.

 Mivel egy támadó érvénytelen szoftverhasználat-mérési adatokat hozhat létre, a szoftverhasználat-mérési adatokat ne tekintse mérvadónak.

 A szoftverhasználat-mérés alapértelmezés szerint engedélyezve van ügyfélbeállításként.

###  <a name="privacy-information-for-software-metering"></a>Adatvédelmi információ a szoftverhasználat-mérés
 A szoftverhasználat-mérés alkalmazások az ügyfélszámítógépeken való használatát figyeli. A szoftverhasználat-mérés alapértelmezés szerint engedélyezve van. Konfigurálnia kell, hogy mely alkalmazásokat kívánja mérni. Mérési adatokat a Configuration Manager-adatbázis tárolja. Az információ titkosított, egy felügyeleti pontra való átvitel során, de nem a Configuration Manager adatbázisban titkosított formában tárolja.

 Az adatbázis addig őrzi meg ezeket az adatokat, amíg nem törli azokat (öt naponta) az **Elavult szoftverhasználat-mérési adatok törlése** és (270 naponta) az **Elavult szoftverhasználat-mérési összefoglaló adatok törlése** helykarbantartási feladat. Beállíthatja a törlési időközt. A rendszer nem küld mérési adatokat a Microsoftnak.

 A szoftverhasználat-mérés konfigurálása előtt gondolja át az adatvédelmi követelményeket.

## <a name="example-scenario-for-using-software-metering"></a>Példaforgatókönyv a szoftverhasználat-mérés használatára
 A jelen szakasz bemutatja egy olyan szoftverhasználat-mérési szabály létrehozását, amely segítségével teljesítheti a következő üzleti igényeket:

-   Annak megállapítása, hogy egy adott alkalmazás hány példánya van a vállalatnál

-   Egy alkalmazás nem használt példányainak felderítése

-   Annak megállapítása, hogy mely felhasználók használnak rendszeresen egy adott alkalmazást

 A Woodgrove Bank a Microsoft Office 2010-et üzemelteti, mint szabványos hatékonyságnövelő programcsomagot. Azonban egy örökölt alkalmazás támogatásához egyes számítógépeken továbbra is futnia kell a Microsoft Office Word 2003 programnak. Az informatikai részleg csökkenteni szeretné a támogatási és licencelési költségeket a Word 2003 példányainak eltávolításával azon számítógépekről, amelyeken már nem használják az örökölt alkalmazást. A támogatási szolgálat emellett szeretné azonosítani azon felhasználókat, akik használják az örökölt alkalmazást.

 John a Woodgrove Bank funkcióját használja ezen üzleti célok eléréséhez a szoftverhasználat-mérés a Configuration Manager. Ezután az alábbi műveleteket hajtja végre:

- Ellenőrzi a szoftverhasználat-mérés előfeltételeit, és megerősíti, hogy a jelentéskészítési szolgáltatási pont telepítve van és működik.
- Konfigurálja az alapértelmezett ügyfélbeállításokat a szoftverhasználat-méréshez:<br>Ezután engedélyezi a szoftverhasználat-mérést, és az alapértelmezett adatgyűjtési ütemezést (hét naponta) használja.<br>A szoftverleltár **Leltározandó fájltípusok**ügyfélbeállításával úgy konfigurálja a szoftverleltárat, hogy az  .exe kiterjesztésű fájlokat leltározza.<br>Hozzáad egy új szoftverhasználat-mérési szabályt **woodgrove.exe**néven az örökölt alkalmazás figyelésére.
- Megvárja, amíg eltelik a hét nap, mely után az ügyfélszámítógépek elkezdik jelenteni a **woodgrove.exe** végrehajtható fájlra vonatkozó használati adatokat.
- János a Configuration Manager-jelentés **telepítési bázisa összes mért használatú szoftver** mely számítógépek vannak-e az alkalmazás **woodgrove.exe** betöltve.
- Hat hónap után futtatja az **Azok a számítógépek amelyekre telepítve van egy mért használatú program amelyet azonban nem futtattak a megadott dátum óta**jelentést, megadva a szoftverhasználat-mérési szabályt és egy hat hónappal korábbi dátumot. Ez a jelentés 120 olyan számítógépet azonosít, amelyen nem futtatták a programot az elmúlt hat hónapban.
- John elvégez néhány további ellenőrzést, hogy meggyőződjön arról, hogy az azonosított számítógépeken nincs szükség az örökölt alkalmazásra. Ezután eltávolítja az örökölt alkalmazást és a Word 2003 példányát ezekről a számítógépekről.<br>John ezután futtatja a **Meghatározott mért használatú szoftvert futtató felhasználók** jelentést, azon felhasználók listájának megadásához a segélyszolgálat számára, akik továbbra is használják az örökölt alkalmazást.
- John továbbra is hetente ellenőrzi a szoftverhasználat-mérési jelentéseket, és végrehajtja a javító műveleteket, ha szükséges.

 Az intézkedés következtében az informatikai támogatási és a licencelési költségek csökkennek a szükségtelenné vált alkalmazások eltávolításával. Továbbá a támogatási szolgálat most már rendelkezik az örökölt alkalmazást futtató felhasználók listájával.

