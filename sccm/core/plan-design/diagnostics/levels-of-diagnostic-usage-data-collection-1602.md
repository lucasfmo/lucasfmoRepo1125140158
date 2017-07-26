---
title: Diagnosztikai adatok az 1602-es |} Microsoft Docs
description: "További információk a diagnosztikai és használati adatok alapján gyűjti a System Center Configuration Manager 1602-es szintek."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1210a1ca-78c7-4d17-81cf-ac1bc5c5cf3e
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
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
ms.openlocfilehash: 3e50327678d29fa2c1fed4ac0fd63738e65776cb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1602-of-system-center-configuration-manager"></a>Diagnosztikai és használati adatok gyűjtésének 1602-es verzióra a System Center Configuration Manager szintjei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager 1602-es verziójában a következő három szinten képes diagnosztikai és használati adatok: **Alapszintű**, **fokozott**, és **teljes**. Alapértelmezés szerint ez a funkció a Bővített szintre van beállítva. Az alábbi szakaszokban további részleteit, amely minden szinten gyűjt adatokat.

Egy korábbi módosítások leírásban ki vannak emelve az ***[Új]*** vagy ***[frissítése]***.

> [!IMPORTANT]
>  A Configuration Manager nem gyűjt helykódok, helyneveket, IP címek, felhasználóneveket, számítógépneveket, fizikai címeket vagy e-mail címek az alapszintű és a bővített szinten. Az adatok a teljes szinten gyűjtemény nincs szándékos, ez azt jelenti, hogy melyek esetlegesen szerepelhetnek a speciális diagnosztikai információkat, például naplófájlokban vagy memória-pillanatképeket. A Microsoft nem használja ezt az információt azonosítására, Önnel a kapcsolatot, és hirdetési fejlesztéséhez.

##  <a name="bkmk_change"></a> A szint módosítása
 Rendszergazdákat, akik a szerepköralapú felügyeleti hatókörrel, amely tartalmazza az **módosítás** engedélyeit a **hely** módosíthatják az adatgyűjtés a diagnosztikai és használati adatok beállításai a Configuration Manager konzolon szintjét.


  Ehhez a konzolon nyissa meg a backstage lapját (felső bal oldali lapon a lefelé mutató nyíl), válasszon **használati adatok**, majd válassza ki a használni kívánt adatok szintet.  

##  <a name="bkmk_level1"></a> 1. szint – Alapszintű
 Az alapszint a hierarchiában, amely szükséges a telepítés javítása, vagy frissítse a felhasználói élmény, és az adatok segítenek meghatározni, a Configuration Manager-frissítések a hierarchia megfelelő adatok vonatkozó adatokat tartalmazza.

 A System Center Configuration Manager 1602-es verziójától kezdve ez a szint a következőket tartalmazza:


 -   Telepítési információk:
     - Build, telepítés típusa, nyelvi csomagokat, szolgáltatásokat, hogy engedélyezve van  

     - ***[Frissítése] *** Csomagok központi telepítési állapota és a hibák, a letöltési folyamat és az előfeltételeknél észlelt hibákat frissítése     

     - ***[Új] *** Frissítés utáni parancsfájl verziója

     - ***[Új] *** Frissítés gyors gyűrű használata

-   Adatbázisteljesítmény-metrikák (replikációs feldolgozási adatok, a processzor és lemezhasználati felső tárolt SQL Server-eljárások)

-   Alapvető adatbázis-konfiguráció (processzor, fürtkonfiguráció és az elosztott nézetek konfigurálása)

-   A Configuration Manager adatbázis-séma (az összes Objektumdefiníció kivonata)

-   Ügyfél-verziónkénti száma a Configuration Manager és az operációsrendszer-verziók

-   Operációs rendszerek felügyelt eszközök és az Exchange Connector által beállított házirendek száma

-   Ügyfélnyelvek és területi beállítások száma

-   Windows 10-eszközök száma ág és build szerint

-   Alapszintű Configuration Manager hierarchia helyadatok (helyek listája, típus, verzió, állapot, ügyfelek száma és időzóna)

-   Alapszintű helyrendszer-kiszolgáló információk (használt helyrendszerszerepkörök, internetes és SSL-állapot, operációs rendszer, processzorok, és a fizikai vagy virtuális gép)

-   Alapszintű felhasználófelderítési statisztika (felhasználói felderítési száma és minimális, maximális és átlagos csoport mérete)

-   Alapszintű Endpoint protection-információk (a kártevőirtó ügyfélprogram verziói)

-   Alapszintű alkalmazás és központi telepítési típus száma (összesen, teljes alkalmazások több központi telepítési típust, felülírt teljes függőségekkel rendelkező alkalmazások alkalmazások és központi telepítési technológiák száma)

-   Alap operációs rendszer központi telepítési (OSD) számok (lemezképek)

-   Terjesztési pontok és felügyeleti pontok típusai és alapvető konfigurációs adatai (védett, manuálisan előkészített, PXE, csoportos küldés, SSL-állapot, lekéréses és társ terjesztési pontok, MDM-kompatibilitás, SSL-kompatibilitás, stb.)

-   Telemetriai statisztikák (futása közben futásidejű és a hibák)

- ***[Új] *** Telemetriai adatok szintjét, módját (online vagy kapcsolat nélküli) és konfigurációjának gyors frissítése

- ***[Új] *** Használja a hálózati felderítés (engedélyezve vagy letiltva)
- ***[Új] *** Felügyeleti konzol:

    -  Konzol kapcsolataihoz (opeating rendszer verziója, nyelvi, SKU és architektúra, rendszermemória, logikai processzorok száma a Helyazonosító, a telepített .NET-verziót és a konzol nyelvi csomagok) statisztikája

##  <a name="bkmk_level2"></a> 2. szint - Bővített
A bővített szint az alapértelmezett beállítás, a telepítés befejezése után. Ez a szint az alapszintű a gyűjtött adatok, a funkciószintű adatokat (gyakorisága és időtartama), a Configuration Manager ügyfél beállításait (az összetevő neve, állapota és bizonyos beállításai, például lekérdezési időközök) és a szoftverfrissítésekkel kapcsolatos alapvető információkat tartalmaz.

Ez a szint használata ajánlott, mivel a Microsoft nyújtja a szükséges termékek és szolgáltatások jövőbeli verzióinak hasznos fejlesztéseihez minimálisan szükséges adat. Ez a szint nem nem gyűjt kijelölendő objektumok nevét (helyek, felhasználók, számítógép vagy objektumok), biztonsággal kapcsolatos objektumok és a biztonsági réseket adatait, például szoftverfrissítéseket igénylő rendszerek számát.

A System Center Configuration Manager 1602-es verziójától kezdve ez a szint a következőket tartalmazza:

-   **Alkalmazáskezelés:**

  -   ***[Frissítése] *** a szervezetben használt központi telepítési típusok alapvető használati és célcsoport-kezelési információkat (felhasználó és eszköz vonatkozik, és elérhető, és az univerzális alkalmazások szükséges)  

  -  ***[Frissítése] *** Alkalmazás központi telepítési információjának (telepítés vagy eltávolítás, jóváhagyást, engedélyezett vagy letiltott felhasználói beavatkozás, függőségi és helyettesítési igényel)  

  -   Alkalmazáskérelmek rendelkezésre álló statisztikái  

  -   Csomagok száma típusonként  

  -   Alkalmazható alkalmazások száma operációs rendszerenként  

  -   Csomag- és program-központitelepítések száma  

  -   App-V környezetek és központi telepítési tulajdonságok száma  

  -   A Windows 10-ben licencelt alkalmazáslicencek száma  

  -   ***[Frissítése] *** Alkalmazástelepítések felhasználó/eszköz időszak minimális, maximális és átlagos száma

  -   Karbantartási időszak típusa és időtartama  

  -  ***[Új] *** Alkalmazás házirend méretét és összetettségét statisztikái

-   **Ügyfél:**

    -   Engedélyezett ügyfélügynökök listája és száma

    -   Az egyes forráshelytípusokból származó ügyféltelepítések száma

    -   Ügyféltelepítési hibák száma

-   **Megfelelőségi beállítások:**

    -   Konfigurációelemek száma típusonként

    -   Alapkonfigurációkra vonatkozó alapvető információk (darabszám, központi telepítések száma és hivatkozások száma)

    -   (A beállítás értékét nem rögzíti) beépített beállítások hivatkozó központi telepítések száma

    -   Szabályok és az egyéni beállításokhoz létrehozott telepítések száma

    -   ***[Frissítése] *** Telepített egyszerű tanúsítványigénylési protokollt, VPN, Wi-Fi, tanúsítvány (.pfx) és a megfelelőségi szabályzat sablonok száma   

    -  ***[Új] *** Száma az egyszerű tanúsítványigénylési protokoll (SCEP) tanúsítvány, VPN, Wi-Fi, tanúsítvány (.pfx) és a megfelelőségi szabályzat központi telepítések platform

-   **Tartalom:**

    -   Határok száma típusonként

    -   Határcsoportra vonatkozó információkat (határokat és az egyes határcsoportokhoz rendelt helyrendszerek száma)

    -   Terjesztési pont csoport információk (csomagok és terjesztési pontok egyes terjesztésipont-csoportokhoz rendelt száma)

    -   Terjesztési pontok konfigurációs adatai (fiókiroda-gyorsítótár és a terjesztési pont figyelési használata)

    -   Distribution Manager konfigurációs adatai (szálak, újrapróbálkozási késleltetés, újrapróbálkozások száma, és lekéréses terjesztési pontok beállításai)

-   **Endpoint Protection:**

    -   Endpoint Protection kártevőirtó- és Windows tűzfalházirendek (csoporthoz rendelt egyedi házirendek száma)<br /><br />Ez nem vonatkozik semmilyen, a házirendben szereplő beállítások vonatkozó információt.

    -   Az Endpoint Protection központi telepítési hibái (az Endpoint Protection házirend-telepítési hibakódok száma)

    -   Endpoint protection-irányítópulton megjelenő kijelölt gyűjtemények száma

    -   Az Endpoint Protection szolgáltatáshoz konfigurált riasztások száma

-   **Mobilalkalmazás-kezelés (MAM):**

    -   A MAM-kompatibilis Office alkalmazások, az üzletági alkalmazások és operációs rendszerenként házirendek száma

    -   Mobilalkalmazás-kezelési alkalmazás- és házirend-központitelepítések száma

    -   Mobilalkalmazás-kezelési beállításonként létrehozott szabályok száma

-   **Mobileszköz-felügyelet (MDM):**

    -   Kiadott mobileszköz-műveletek száma: zárolás, PIN-kód rest-, Adattörlés és kivonás parancsok

    -   A Configuration Manager és a Microsoft Intune és a hogyan azok regisztrált (tömeges vagy felhasználó alapú) által felügyelt mobileszközök száma

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

    -   ***[Új] *** Szoftverfrissítési pont által szinkronizált besorolások

-   **SQL- és teljesítményadatok:**

    -   A legnagyobb adatbázistáblák száma

    -   SQL Always-On replika adatai

    -   Gyűjtemények száma típusonként

    -   ***[Frissítése] *** Gyűjtemény értékelési statisztika (lekérdezés idő, és a hozzá nem rendelt számát, hozzárendelt típus azonosító helyettesítő és szabály használati száma)

    - ***[Új] *** SQL változáskövetési megőrzési időnél

-   ***[Új] Hely frissítéseket:***

    - ***[Új] *** Konfigurációs Manager telepített gyorsjavítások verziói

##  <a name="bkmk_level3"></a> 3. szint – Teljes
A teljes szint az alapszintű és a bővített szinten az összes adatait tartalmazza. Ezenfelül további adatokat továbbít az Endpoint Protectionnel, a frissítések megfelelőségi százalékértékeivel és a szoftverfrissítésekkel kapcsolatban. Ez a szint speciális diagnosztikai információkat, például rendszerfájlokat és a memóriáról készült pillanatképeket, beleértve például rögzítési időpontjában már létezett a memóriában vagy naplófájlokban található személyes adatokat is tartalmazhatnak.

A System Center Configuration Manager 1602-es verziójától kezdve ez a szint a következőket tartalmazza:

-   Gyűjtemények kiértékelési és frissítési statisztikái

-   Az Endpoint Protection állapotösszegzése (beleértve a védett, a kockázatnak kitett, az ismeretlen és a nem támogatott ügyfelek számát)

-   Az Endpoint Protection házirend-konfigurációja

-   Szoftverfrissítési központi telepítések adatai (célzott ügyféllel UTC idő, és a szükséges központi telepítések és a csendes, és újraindítás tiltási nem kötelező)

-   A szoftverfrissítési központi telepítések összesített megfelelősége

-   Az automatikus központi telepítési szabályok értékelésének ütemezési adatai

-   Hálózati hozzáférés adatvédelmi szabályzatok rendelkező ügyfelek száma

-   Szoftverfrissítési központi telepítések hibakódjai és azok számai

-   A szoftverfrissítés-telepítési gyűjtemények inaktív ügyfeleinek minimális, maximális és átlagos száma

-   A lejárt szoftverfrissítések csoportok száma

-   Szoftverfrissítések minimális, maximális és átlagos száma csomagonként

-   A szoftverfrissítések vizsgálatainak százalékos sikerességi aránya

-   A szoftverfrissítések legutóbbi vizsgálata óta eltelt órák minimális, maximális és átlagos száma

-   ***[Új] *** Szoftverfrissítési pont által szinkronizált frissítési szoftvertermékek
-   ***[Új] *** Megfelelőségi beállítások: SCEP, VPN, Wi-Fi és a megfelelőségi szabályzat sablon konfiguráció részletei

-   ***[Új] *** Típus az EAS feltételes hozzáférési szabályzatok (letiltás vagy karantén értékű) az Intune által kezelt eszközök

