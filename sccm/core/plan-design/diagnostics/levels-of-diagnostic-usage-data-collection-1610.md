---
title: Diagnosztikai adatok 1610 |} System Center Configuration Managerben
description: "További információk a diagnosztikai és használati adatok alapján gyűjti a System Center Configuration Manager verziója 1610 szintek."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb20eb90-bcc0-41de-bfea-638ea470c0dd
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ba1e53fdc895690bb958c12d59f82a26067ecad3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1610-of-system-center-configuration-manager"></a>Diagnosztikai és használati adatok gyűjtésének 1610 verziójának a System Center Configuration Manager szintjei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager verziója 1610 a következő három szinten képes diagnosztikai és használati adatok: **Alapszintű**, **fokozott**, és **teljes**. Alapértelmezés szerint ez a funkció a Bővített szintre van beállítva. Az alábbi szakaszokban további részleteit, amely minden szinten gyűjt adatokat.

Egy korábbi módosítások leírásban ki vannak emelve az ***[Új]***, ***[frissítése]***, ***[eltávolítása]***, vagy ***[áthelyezése]***.


> [!IMPORTANT]
>  A Configuration Manager nem gyűjt helykódok, helyneveket, IP címek, felhasználóneveket, számítógépneveket, fizikai címeket vagy e-mail címek az alapszintű és a bővített szinten. Az adatok a teljes szinten gyűjtemény nincs szándékos, ez azt jelenti, hogy melyek esetlegesen szerepelhetnek a speciális diagnosztikai információkat, például naplófájlokban vagy memória-pillanatképeket. A Microsoft nem használja ezt az információt azonosítására, Önnel a kapcsolatot, és hirdetési fejlesztéséhez.

##  <a name="bkmk_change"></a> A szint módosítása
 Rendszergazdákat, akik a szerepköralapú felügyeleti hatókörrel, amely tartalmazza az **módosítás** engedélyeit a **hely** módosíthatják az adatgyűjtés a diagnosztikai és használati adatok beállításai a Configuration Manager konzolon szintjét.

1610 verziójával kezdve módosítja az adatgyűjtési szint a a konzolról való **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **helyek**. Nyissa meg **Hierarchiabeállítások**, majd válassza ki a használni kívánt adatok szintet.  

##  <a name="bkmk_level1"></a> 1. szint – Alapszintű
 Az alapszint a hierarchiában, amely szükséges a telepítés javítása, vagy frissítse a felhasználói élmény, és az adatok segítenek meghatározni, a Configuration Manager-frissítések a hierarchia megfelelő adatok vonatkozó adatokat tartalmazza.

 A System Center Configuration Manager 1610 verziója, ez a szint a következőket tartalmazza:


-   Telepítési információk:
       - Build, telepítés típusa, nyelvi csomagokat, szolgáltatásokat, hogy engedélyezve van  

       - Frissítési csomagok központi telepítési állapota és a hibák, végrehajtási és előfeltétel-ellenőrzési hibák     

       - A frissítés utáni parancsfájl verziója

       - Frissítés gyors gyűrű használata

    - ***[Új] *** Előzetes használja, a telepítő adathordozó-típus, a fiókiroda típusa

    - ***[Új] *** Software Assurance lejárati dátuma

- Adatbázisteljesítmény-metrikák (replikációs feldolgozási adatok, a legnagyobb processzor- és lemezhasználatú tárolt SQL Server-eljárások)

- Alapvető adatbázis-konfiguráció (processzor, fürtkonfiguráció és az elosztott nézetek konfigurálása)

- A Configuration Manager adatbázis-séma (az összes Objektumdefiníció kivonata)

- Ügyfél-verziónkénti száma a Configuration Manager és az operációsrendszer-verziók

- Operációs rendszerek felügyelt eszközök és az Exchange Connector által beállított házirendek száma

- Ügyfélnyelvek és területi beállítások száma

- Windows 10-eszközök száma ág és build szerint

- Alapszintű Configuration Manager hierarchia helyadatok (helyek listája, típus, verzió, állapot, ügyfelek száma és időzóna)

- Alapszintű helyrendszer-kiszolgáló információk (használt helyrendszerszerepkörök, internetes és SSL-állapot, operációs rendszer, processzorok, és a fizikai vagy virtuális gép)

- Alapszintű felhasználófelderítési statisztika (felhasználói felderítési száma és minimális, maximális és átlagos csoport mérete)

- Az Endpoint Protection alapinformációk (a kártevőirtó ügyfélprogram verziói)

- Alapszintű alkalmazás és központi telepítési típus száma (összesen, teljes alkalmazások több központi telepítési típust, felülírt teljes függőségekkel rendelkező alkalmazások alkalmazások és központi telepítési technológiák száma)

- Alap operációs rendszer központi telepítési (OSD) számok (lemezképek)

- Terjesztési pontok és felügyeleti pontok típusai és alapvető konfigurációs adatai (védett, manuálisan előkészített, PXE, csoportos küldés, SSL-állapot, lekéréses és társ terjesztési pontok, MDM-kompatibilitás, SSL-kompatibilitás, stb.)

- Telemetriai statisztikák (futtatás feltételei, futásidő, hibák)

- Konfigurált telemetriai adatok szintjét, módját (online vagy kapcsolat nélküli) és konfigurációjának gyors frissítése

- A hálózatfelderítés (engedélyezett vagy tiltott) használata
- Felügyeleti konzol:

     - Konzol kapcsolataihoz (operációs rendszer verziója, nyelvi, SKU és architektúra, rendszermemória, logikai processzorok száma a Helyazonosító, a telepített .NET-verziót és a konzol nyelvi csomagok) statisztikája    

- SQL-verzióra, szervizcsomagot, edition, Rendezésazonosító és karakterkészlet


##  <a name="bkmk_level2"></a> 2. szint - Bővített
A bővített szint az alapértelmezett beállítás, a telepítés befejezése után. Ez a szint az alapszintű a gyűjtött adatok és a funkciószintű adatokat (gyakorisága és időtartama), a Configuration Manager ügyfél beállításait (az összetevő neve, állapota és bizonyos beállításai, például lekérdezési időközök) és a szoftverfrissítésekkel kapcsolatos alapvető információkat tartalmaz.

Ez a szint használata ajánlott, mivel a Microsoft nyújtja a szükséges termékek és szolgáltatások jövőbeli verzióinak hasznos fejlesztéseihez minimálisan szükséges adat. Ez a szint nem nem gyűjt kijelölendő objektumok nevét (helyek, felhasználók, számítógép vagy objektumok), biztonsággal kapcsolatos objektumok és a biztonsági réseket részleteit, például szoftverfrissítéseket igénylő rendszerek számát.

A System Center Configuration Manager 1610 verziója, ez a szint a következőket tartalmazza:

-   **Alkalmazáskezelés:**  

    -    A szervezetben használt központi telepítési típusok alapvető használati és célcsoport-kezelési információkat (felhasználó és eszköz vonatkozik, szükséges és elérhető, és az univerzális alkalmazások)  

    -   Alkalmazás központi telepítési információjának (telepítés vagy eltávolítás, jóváhagyást, engedélyezett vagy letiltott felhasználói beavatkozás, függőségi és helyettesítési igényel)  

    -   Alkalmazáskérelmek rendelkezésre álló statisztikái  

    -   Csomagok száma típusonként  

    -   Alkalmazható alkalmazások száma operációs rendszerenként  

    -   Csomag- és program-központitelepítések száma  

    -   App-V környezetek és központi telepítési tulajdonságok száma  

    -   A Windows 10-ben licencelt alkalmazáslicencek száma  

    -   Alkalmazások központi telepítésének felhasználó/eszköz időszak minimális, maximális és átlagos száma

    -   Karbantartási időszak típusa és időtartama  

    -  Alkalmazás házirend méretét és összetettségét statisztikái

    - ***[Frissítése] *** Száma a Windows áruház az üzleti alkalmazások és a szinkronizálási statisztika (összesített típusú alkalmazásokat, beleértve a licencelt alkalmazások állapotát, és online és offline licencelt alkalmazások)  

    - Határ csoportonkénti statisztikák (hány gyors, hogy hány lassú, és száma csoportonként)

    - MSI-konfigurációs beállítások és száma

    - Alkalmazáskövetelmények (száma a beépített feltételekről hivatkozik központi telepítési technológia)

    - Alkalmazás-helyettesítés, lánc maximális mélysége

    - Univerzális Data Access (UDA) használati, hogyan létrehozott

    - ***[Új] *** Alkalmazások jóváhagyási statisztikák és a használat gyakorisága



-   **Ügyfél:**  

    -   Engedélyezett ügyfélügynökök listája és száma  

    -   Az egyes forráshelytípusokból származó ügyféltelepítések száma  

    -   Ügyféltelepítési hibák száma  

    -  ***[Frissítése] *** Ügyfél automatikus frissítési: telepítési konfigurációt, beleértve az ügyfél tesztelés és kizárási használati (kiterjesztett együttműködési ügyfél)

    -  Ügyfél állapotának statisztikák és felső probléma összefoglalása

    - BIOS-kor évben

    - Operációs rendszer kora hónapban

    - A Szoftverközpont száma műveletek

    - Active Management Technology (AMT) ügyfél verziója

    - Ügyfél központi telepítés letöltési hiba

    - Ügyfél értesítési művelet művelet állapota (hány alkalommal van célzott ügyfeleket, és átlagos sikerességi arányát futtatási, maximális száma)

    - Központi telepítési módszerekkel használt ügyfél és az ügyfelek az üzembe helyezési módszer másodpercenkénti száma

    - Ügyfél-gyorsítótár mérete konfigurációja

    - ***[Új] *** Hardverleltárosztályok, a szoftverhasználat-készlet szabályok és a fájl gyűjtési szabályok száma




- **Cloud Services csomag:**

  - Az Operations Management Suite szinkronizált gyűjtemények száma

  -  Hogy engedélyezve van-e az Operations Management Suite felhőcsatlakozót

  - ***[Új] *** Felhő felügyeleti átjáró konfigurációs és a használati statisztikák

  - ***[Új] *** Frissítési Analytics összekötők száma




- **Gyűjtemények:**

    -  Gyűjtemény értékelési statisztika (lekérdezés idejét, és ki nem osztott száma, típusa azonosító helyettesítő és szabály használati számok hozzárendelt)

    - Gyűjtemények, központi telepítés nélkül

    - Gyűjtemény azonosítója használati (azonosítók kívül nem fut)



-   **Megfelelőségi beállítások:**  

    -   Konfigurációelemek száma típusonként  

    -   Alapkonfigurációkra vonatkozó alapvető információk (darabszám, központi telepítések száma és hivatkozások száma)  

    -   A központi telepítések száma (most rögzítése szervizelése beállítással), hogy hivatkozás beépített beállításai  

    -   Szabályok és az egyéni beállításokhoz (most rögzítése szervizelése beállítással) létrehozott központi telepítések száma  
    -   Egyszerű tanúsítványigénylési protokoll (SCEP), VPN, Wi-Fi, tanúsítvány (.pfx) és a megfelelőségi házirendet telepített sablonok száma

    -  Száma az SCEP-tanúsítvány, VPN, Wi-Fi, tanúsítvány (.pfx) és a megfelelőségi szabályzat központi telepítések platform

    - A Passport for Work-házirend (létrehozni, központilag telepített)



-   **Tartalom:**  

    -   Határok száma típusonként  

    -   Határcsoportra vonatkozó információkat (határokat és az egyes határcsoportokhoz rendelt helyrendszerek száma)  

    - ***[Új] *** Határ csoportok közötti kapcsolatok és tartalék konfigurációja

    -   Terjesztési pont csoport információk (csomagok és terjesztési pontok egyes terjesztésipont-csoportokhoz rendelt száma)  

    -   Terjesztési pontok konfigurációs adatai (fiókiroda-gyorsítótár és a terjesztési pont figyelési használata)  

    -   Distribution Manager konfigurációs adatai (szálak, újrapróbálkozási késleltetés, újrapróbálkozások száma, és lekéréses terjesztési pontok beállításai)  

    - ***[Új] *** Társ-gyorsítótárazási ügyfelek és a használati statisztikák száma

    - ***[Új] *** Ügyfél a tartalom letöltése statisztikák


-   **Endpoint Protection:**  

    -   Endpoint Protection kártevőirtó- és Windows tűzfalházirendek (csoporthoz rendelt egyedi házirendek száma)<br /><br /> Ez nem vonatkozik semmilyen, a házirendben szereplő beállítások vonatkozó információt.  

    -   Az Endpoint Protection központi telepítési hibái (az Endpoint Protection házirend-telepítési hibakódok száma)  

    -   Endpoint Protection-irányítópulton megjelenő kijelölt gyűjtemények száma  

    -   Az Endpoint Protection szolgáltatáshoz konfigurált riasztások száma  

    -     Advanced Threat Protection (ATP) házirendek (házirendek, és hogy házirendet telepít száma)


- **Áttelepítés:**

  -   (A nyomtatóáttelepítő varázsló használata) áttelepített objektumok száma



-   **Mobileszköz-felügyelet (MDM):**  

    -   ***[Frissítése] *** Kiadott mobileszköz-műveletek száma: zárolás, PIN-kód rest, törlése, a kivonása és a szinkronizálás most parancsok  

    -   A Configuration Manager és a Microsoft Intune és a hogyan azok regisztrált (csoportos, felhasználóalapú) által felügyelt mobileszközök száma  

    -   Mobileszköz-lekérdezési ütemezés és a statisztika mobileszközök bejelentkezési időtartama  

    -   Mobileszköz-házirendek száma  

    -   Több regisztrált mobileszközzel rendelkező felhasználók száma  

-   **A Microsoft Intune hibáinak elhárítása:**

    -   Állapot, az állapot, a szoftverleltár, száma és mérete RDR-, DDR-, UDX, bérlői állapot, a Microsoft Intune-ból letöltött POL, napló, tanúsítvány, CRP, újraszinkronizálási, CFD, RDO, BEX, ISM és megfelelőségi üzenetek

    -   Eszközműveletek száma és mérete (törlése, kivonás, zárolás), telemetriai adatokat, és a Microsoft Intune szolgáltatásba replikált adatüzenetek

    -   Teljes és különbözeti felhasználószinkronizálásának statisztikái a Microsoft Intune


-   **Helyszíni mobileszköz-felügyelet (MDM):**  

    -   Az alkalmazások helyszíni mobileszköz-felügyelettel végzett sikeres és sikertelen központi telepítéseinek statisztikái.  

    -   Windows 10-es csoportos regisztrációs csomagok és profilok száma  



-   **Operációs rendszer központi telepítéséhez:**  

    -   Rendszerindító lemezképek, illesztőprogramok, illesztőprogram-csomagok, csoportos küldésre képes terjesztési pontok, PXE-t támogató terjesztési pontok és feladatütemezések száma  

    -   A feladat feladatütemezési lépés használati számát

    - ***[Új] *** Edition frissítési házirendek száma



-   **Hely frissítéseket:**

    - A Configuration Manager telepített gyorsjavítások verziói




-   **Szoftverfrissítések:**  

    -   Teljes és átlagos gyűjteményeket, amelyek a szoftverfrissítési központi telepítések száma és a telepített frissítések maximális és átlagos száma  

    -   A szinkronizáláshoz kötött automatikus központi telepítési szabályok száma  

    -   Azon automatikus központi telepítési szabályok száma, amelyek új csoportot hoznak létre, vagy meglévő csoporthoz adnak hozzá frissítéseket  

    -   Automatikus központi telepítési szabályokban használt elérhető és határidős eltérések  

    -   Hozzárendelések átlagos és maximális száma frissítésenként  

    -   A System Center frissítés-közzétevője létrehozott és telepített frissítések  

    -   Frissítési csoportok és hozzárendelések száma  

    -   A frissítési csomagok és a maximális, minimális és átlagos száma, amelyek a csomagok terjesztési pontok száma  

    -   A frissítési csoportok száma, illetve a frissítések minimális, maximális és átlagos száma csoportonként  

    -   A frissítések számát és százalékos aránya a frissítések, telepített, lejárt, felülírt, letöltött és EULA tartalmaz  

    -   Frissítési vizsgálatok hibakódjai és a számítógépek száma  

    -   Ügyfelek frissítéseinek értékelése és vizsgálatütemezései  

    -   Szoftverfrissítési pontok szinkronizálásának ütemezése  

    -   Több központi telepítéssel rendelkező automatikus központi telepítési szabályok száma  

    -   Aktív Windows 10-es karbantartási tervek használt konfigurációk  

    -   A Windows 10 irányítópultjának tartalomverziói  

    -   A Windows Update szolgáltatást használja a vállalati száma a Windows 10-ügyfelek  

    -   Fürtjavítási statisztikák  

    -   Az Office 365 telepített frissítéseinek száma  

    -   Szoftverfrissítési pont által szinkronizált besorolások

    -   Szoftverfrissítési pont terheléselosztási statisztikák

    -  ***[Új] *** Windows 10 konfigurációs express frissítések




-   **SQL- és teljesítményadatok:**  

    -   A legnagyobb adatbázistáblák száma  

    -   ***[Frissítése] *** SQL AlwaysOn replika információt, használati, és állapota

    -  SQL-változáskövetési megőrzési időnél

    - A felderítést, engedélyezett és ütemezése (teljes, növekményes)

    - Felderítési működési statisztika (található objektumok száma)

    - SQL-változáskövetési teljesítménnyel kapcsolatos problémák, a megőrzési időtartam és a auto-karbantartási állapota



- **Vegyes**

    - A helyek számát az ébresztési a Lan (WOL)

    - ***[Új] *** Reporting használati és teljesítményadatokat statisztikák  



##  <a name="bkmk_level3"></a> 3. szint – Teljes
A teljes szint az alapszintű és a bővített szinten az összes adatait tartalmazza. Ezenfelül további adatokat továbbít az Endpoint Protectionnel, a frissítések megfelelőségi százalékértékeivel és a szoftverfrissítésekkel kapcsolatban.  Ez a szint speciális diagnosztikai információkat, például rendszerfájlokat és a memóriáról készült pillanatképeket, beleértve például rögzítési időpontjában már létezett a memóriában vagy naplófájlokban található személyes adatokat is tartalmazhatnak.

A System Center Configuration Manager 1610 verziója, ez a szint a következőket tartalmazza:

-   Gyűjtemények kiértékelési és frissítési statisztikái

-   Az Endpoint Protection állapotösszegzése (beleértve a védett, a kockázatnak kitett, az ismeretlen és a nem támogatott ügyfelek számát)

-   Az Endpoint Protection házirend-konfigurációja

-   Szoftverfrissítési központi telepítések adatai (központi telepítések, amelyek az ügyfél UTC idő, és a szükséges és a csendes, és újraindítás tiltási nem kötelező)

-   A szoftverfrissítési központi telepítések összesített megfelelősége

-   Az automatikus központi telepítési szabályok értékelésének ütemezési adatai

-   Szoftverfrissítési központi telepítések hibakódjai és azok számai

-   A szoftverfrissítés-telepítési gyűjtemények inaktív ügyfeleinek minimális, maximális és átlagos száma

-   A lejárt szoftverfrissítések csoportok száma

-   Szoftverfrissítések minimális, maximális és átlagos száma csomagonként

-   A szoftverfrissítések vizsgálatainak százalékos sikerességi aránya

-   A szoftverfrissítések legutóbbi vizsgálata óta eltelt órák minimális, maximális és átlagos száma

-    Szoftverfrissítési pont által szinkronizált frissítési szoftvertermékek
-    Megfelelőségi beállítások: SCEP, VPN, Wi-Fi és a megfelelőségi szabályzat sablon konfiguráció részletei

-    EAS vonatkozó feltételes hozzáférési szabályzatok (letiltás vagy karantén értékű) eszközöket, amelyek az Intune kezeli típusa

-   A környezetben 50 legfontosabb processzorok

-   DCM konfigurációs csomag a System Center Configuration Manager használata

-   MSI-termékkód (általános alkalmazások, amelyeket az ügyfelek központi telepítése)

-   ATP állapotának összegzése

-   Részletes ügyfél-telepítési telepítési hibák

- ***[Új] *** Üzleti alkalmazás részletes adatainak (például AppID, online vagy offline állapotban és megvásárolt licencek teljes száma a szinkronizált alkalmazások listája nem összevont) a Windows áruházban

