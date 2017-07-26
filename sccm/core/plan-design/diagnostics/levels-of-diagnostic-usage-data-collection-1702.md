---
title: Diagnosztikai adatok 1702 |} System Center Configuration Managerben
description: "További információk a diagnosztikai és használati adatok alapján gyűjti a System Center Configuration Manager verziója 1702 szintek."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d43ab033-2902-4681-8716-b4b17a6df372
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
ms.openlocfilehash: 0e1d93712150fb3d6fabc3f057711eba1194c3ad
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1702-of-system-center-configuration-manager"></a>Diagnosztikai és használati adatok gyűjtésének 1702 verziójának a System Center Configuration Manager szintjei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager verziója 1702 a következő három szinten képes diagnosztikai és használati adatok: **Alapszintű**, **fokozott**, és **teljes**. Alapértelmezés szerint ez a funkció a Bővített szintre van beállítva. Az alábbi szakaszokban további részleteit, amely minden szinten gyűjt adatokat.

Egy korábbi módosítások leírásban ki vannak emelve az ***[Új]***, ***[frissítése]***, ***[eltávolítása]***, vagy ***[áthelyezett]***.


> [!IMPORTANT]
>  A Configuration Manager nem gyűjt helykódok, helyneveket, IP címek, felhasználóneveket, számítógépneveket, fizikai címeket vagy e-mail címek az alapszintű és a bővített szinten. Az adatok a teljes szinten gyűjtemény nincs szándékos, ez azt jelenti, hogy melyek esetlegesen szerepelhetnek a speciális diagnosztikai információkat, például naplófájlokban vagy memória-pillanatképeket. A Microsoft nem használja ezt az információt azonosítására, Önnel a kapcsolatot, és hirdetési fejlesztéséhez.



##  <a name="bkmk_change"></a> A szint módosítása
 Rendszergazdákat, akik a szerepköralapú felügyeleti hatókörrel, amely tartalmazza az **módosítás** engedélyeit a **hely** módosíthatják az adatgyűjtés a diagnosztikai és használati adatok beállításai a Configuration Manager konzolon szintjét.

Módosíthatja a adatgyűjtési szint a a konzolról való **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **helyek**. Nyissa meg **Hierarchiabeállítások**, majd válassza ki a használni kívánt adatok szintet.  



##  <a name="bkmk_level1"></a> 1. szint – Alapszintű
Az alapszint a hierarchiában, amely szükséges a telepítés javítása, vagy frissítse a felhasználói élmény, és az adatok segítenek meghatározni, a Configuration Manager-frissítések a hierarchia megfelelő adatok vonatkozó adatokat tartalmazza.

A System Center Configuration Manager verzió 1702, ez a szint a következőket tartalmazza:

- Felügyeleti konzol:
   - Konzol kapcsolataihoz (operációs rendszer verziója, nyelvi, SKU és architektúra, rendszermemória, logikai processzorok száma a Helyazonosító, a telepített .NET-verziót és a konzol nyelvi csomagok) statisztikája

- Alapszintű alkalmazás és központi telepítési típus száma (összesen, teljes alkalmazások több központi telepítési típust, felülírt teljes függőségekkel rendelkező alkalmazások alkalmazások és központi telepítési technológiák száma)

- Alapszintű Configuration Manager hierarchia helyadatok (webhely-lista, típus, verzió, állapot, ügyfelek száma és időzóna)

- Alapvető adatbázis-konfiguráció (processzor, fürtkonfiguráció és az elosztott nézetek konfigurálása)

- ***[Frissítése] *** Alapszintű felhasználófelderítési statisztika (felderítési száma és minimális, maximális és átlagos csoport mérete) is beleértve, amikor a hely teljes mértékben az Azure Active Directory szolgáltatáshoz fut-e.

- Az Endpoint Protection alapinformációk (a kártevőirtó ügyfélprogram verziói)

- Alap operációs rendszer központi telepítési (OSD) számok (lemezképek)

- Alapszintű helyrendszer-kiszolgáló információk (használt helyrendszerszerepkörök, internetes és SSL-állapot, operációs rendszer, processzorok, és a fizikai vagy virtuális gép)

- A Configuration Manager adatbázis-séma (az összes Objektumdefiníció kivonata)

- Konfigurált telemetriai adatok szintjét, módját (online vagy kapcsolat nélküli) és konfigurációjának gyors frissítése

- Ügyfélnyelvek és területi beállítások száma

- Ügyfél-verziónkénti száma a Configuration Manager és az operációsrendszer-verziók

- Operációs rendszerek a felügyelt eszközök és az Exchange Connector által beállított házirendek száma

- Windows 10-eszközök száma ág és build szerint

- Adatbázisteljesítmény-metrikák (replikációs feldolgozási adatok, a legnagyobb processzor- és lemezhasználatú tárolt SQL Server-eljárások)

- Terjesztési pontok és felügyeleti pontok típusai és alapvető konfigurációs adatai (védett, manuálisan előkészített, PXE, csoportos küldés, SSL-állapot, lekéréses és társ terjesztési pontok, MDM-kompatibilitás, SSL-kompatibilitás, stb.)

- Telepítési információk:
     - Build, telepítés típusa, nyelvi csomagokat, szolgáltatásokat, hogy engedélyezve van   

     - Kiadás előtti használat, a telepítő adathordozó-típus, a fiókiroda típusa

     - Software Assurance lejárati dátuma      

     - Frissítési csomagok központi telepítési állapota és a hibák, végrehajtási és előfeltétel-ellenőrzési hibák     

     - Frissítés gyors gyűrű használata

     - A frissítés utáni parancsfájl verziója

- SQL-verzióra, szervizcsomagot, edition, Rendezésazonosító és karakterkészlet     
- Telemetriai statisztikák (futtatás feltételei, futásidő, hibák)

- A hálózatfelderítés (engedélyezett vagy tiltott) használata




##  <a name="bkmk_level2"></a> 2. szint - Bővített
A bővített szint az alapértelmezett beállítás, a telepítés befejezése után. Ez a szint az alapszintű a gyűjtött adatok és a funkciószintű adatokat (gyakorisága és időtartama), a Configuration Manager ügyfél beállításait (az összetevő neve, állapota és bizonyos beállításai, például lekérdezési időközök) és a szoftverfrissítésekkel kapcsolatos alapvető információkat tartalmaz.

Ez a szint használata ajánlott, mivel a Microsoft nyújtja a szükséges termékek és szolgáltatások jövőbeli verzióinak hasznos fejlesztéseihez minimálisan szükséges adat. Ez a szint nem nem gyűjt kijelölendő objektumok nevét (helyek, felhasználók, számítógép vagy objektumok), biztonsággal kapcsolatos objektumok és a biztonsági réseket részleteit, például szoftverfrissítéseket igénylő rendszerek számát.

A System Center Configuration Manager verzió 1702, ez a szint a következőket tartalmazza:

- **Alkalmazáskezelés:**  

   - (A beépített feltételekről száma központi telepítési technológia hivatkoznak) alkalmazáskövetelmények

   - Alkalmazás-helyettesítés, lánc maximális mélysége

   - Alkalmazások jóváhagyási statisztikák és a használat gyakorisága

   - ***[Frissítése] *** Alkalmazás központi telepítési információjának (telepítés vagy eltávolítás használja, szükséges hozzá jóváhagyási, engedélyezett vagy letiltott felhasználói beavatkozás, függőség, helyettesítési, és telepítési viselkedés szolgáltatás használati száma)  

   - Alkalmazás házirend méretét és összetettségét statisztikái

   - Alkalmazáskérelmek rendelkezésre álló statisztikái

   - ***[Új] *** Alapszintű konfigurációs adatok csomagok és programok (a központi telepítési beállítások és a program jelzők)

   - A szervezetben használt központi telepítési típusok alapvető használati és célcsoport-kezelési információkat (felhasználó és eszköz vonatkozik, és elérhető, és az univerzális alkalmazások szükséges)

   - Határ csoportonkénti statisztikák (hány gyors, hogy hány lassú, és száma csoportonként)

   - App-V környezetek és központi telepítési tulajdonságok száma

   - Alkalmazható alkalmazások száma operációs rendszerenként  

   - ***[Új] *** Alkalmazásokat, amelyek a feladatütemezés által hivatkozott száma

   - Csomagok száma típusonként  

   - Csomag- és program-központitelepítések száma  

   - A Windows 10-ben licencelt alkalmazáslicencek száma  

   - Száma a Windows áruház az üzleti alkalmazások és a szinkronizálási statisztika (összesített típusú alkalmazásokat, beleértve a licencelt alkalmazások állapotát, és online és offline licencelt alkalmazások)  

   - Karbantartási időszak típusa és időtartama  

   - Alkalmazások központi telepítésének felhasználó/eszköz időszak minimális, maximális és átlagos száma

   - ***[Új] *** Leggyakrabban használt alkalmazás telepítési hibakódok által központi telepítési technológia

   - MSI-konfigurációs beállítások és száma

   - ***[Új] *** Statisztikák végfelhasználói beavatkozást értesítéssel a szükséges szoftverek központi telepítése   

   - Univerzális Data Access (UDA) használati, hogyan létrehozott




- **Ügyfél:**  

   - Active Management Technology (AMT) ügyfél verziója

   - BIOS-kor évben

   - Ügyfél automatikus frissítési: telepítési konfigurációt, beleértve az ügyfél tesztelés és kizárási használati (kiterjesztett együttműködési ügyfél)

   - Ügyfél-gyorsítótár mérete konfigurációja

   - Ügyfél központi telepítés letöltési hiba

   - Ügyfél állapotának statisztikák és felső probléma összefoglalása

   - Ügyfél értesítési művelet művelet állapota (hány alkalommal van célzott ügyfeleket, és átlagos sikerességi arányát futtatási, maximális száma)
   - Az egyes forráshelytípusokból származó ügyféltelepítések száma  

   - Ügyféltelepítési hibák száma  

   - ***[Új] *** Hyper-V vagy Azure virtuális eszközök száma  

   - A Szoftverközpont száma műveletek   

   - ***[Új] *** Száma az UEFI-kompatibilis eszközök

   - Központi telepítési módszerekkel használt ügyfél és az ügyfelek az üzembe helyezési módszer másodpercenkénti száma

   - Engedélyezett ügyfélügynökök listája és száma  

   - Operációs rendszer kora hónapban

   - Hardverleltárosztályok, a szoftverhasználat-készlet szabályok és a fájl gyűjtési szabályok száma

   - ***[Új] *** Többek között a leggyakoribb hiba az Eszközállapot-igazolás statisztikája kódok, a helyszíni kiszolgálók számát, és a különböző állapotok eszközök számát.



- **Cloud Services csomag:**

  - Felügyeleti átjáró konfigurációs és használati statisztikáinak

  - ***[Új] *** Azure Active Directory-szolgáltatások csatlakozott ügyfelek száma

  - Az Operations Management Suite szinkronizált gyűjtemények száma

  - A frissítési Analytics összekötők száma

  - Hogy engedélyezve van-e az Operations Management Suite felhőcsatlakozót




- **Gyűjtemények:**

    - Gyűjtemény azonosítója használati (azonosítók kívül nem fut)

    - Gyűjtemény értékelési statisztika (lekérdezés idejét, és ki nem osztott száma, típusa azonosító helyettesítő és szabály használati számok hozzárendelt)

    - Gyűjtemények, központi telepítés nélkül




- **Megfelelőségi beállítások:**  

    - Alapkonfigurációkra vonatkozó alapvető információk (darabszám, központi telepítések száma és hivatkozások száma)  

    - Konfigurációelemek száma típusonként  

    - A központi telepítések száma (most rögzítése szervizelése beállítással), hogy hivatkozás beépített beállításai  

    - Szabályok és az egyéni beállításokhoz (most rögzítése szervizelése beállítással) létrehozott központi telepítések száma  
    -  Egyszerű tanúsítványigénylési protokoll (SCEP), VPN, Wi-Fi, tanúsítvány (.pfx) és a megfelelőségi házirendet telepített sablonok száma

    - Száma az SCEP-tanúsítvány, VPN, Wi-Fi, tanúsítvány (.pfx) és a megfelelőségi szabályzat központi telepítések platform

    - A Passport for Work-házirend (létrehozni, központilag telepített)



- **Tartalom:**  

    - Határcsoportra vonatkozó információkat (határokat és az egyes határcsoportokhoz rendelt helyrendszerek száma)  

    - Határ csoportok közötti kapcsolatok és tartalék konfigurációja

    - Ügyfél a tartalom letöltése statisztikák

    - Határok száma típusonként  

    - Társ-gyorsítótárazási ügyfelek és a használati statisztikák száma

    - Distribution Manager konfigurációs adatai (szálak, újrapróbálkozási késleltetés, újrapróbálkozások száma, és lekéréses terjesztési pontok beállításai)  

    - Terjesztési pontok konfigurációs adatai (fiókiroda-gyorsítótár és a terjesztési pont figyelési használata)

    - Terjesztési pont csoport információk (csomagok és terjesztési pontok egyes terjesztésipont-csoportokhoz rendelt száma)  



- **Endpoint Protection:**  

   - Advanced Threat Protection (ATP) házirendek (házirendek, és hogy házirendet telepít száma)

   - Az Endpoint Protection szolgáltatáshoz konfigurált riasztások száma  

   - Endpoint Protection-irányítópulton megjelenő kijelölt gyűjtemények száma  

   - Az Endpoint Protection központi telepítési hibái (az Endpoint Protection házirend-telepítési hibakódok száma)  

   - Endpoint Protection kártevőirtó- és Windows tűzfalházirendek (csoporthoz rendelt egyedi házirendek száma)<br /><br /> Ez nem vonatkozik semmilyen, a házirendben szereplő beállítások vonatkozó információt.  



- **Áttelepítés:**

  - (A nyomtatóáttelepítő varázsló használata) áttelepített objektumok száma



- **Mobileszköz-felügyelet (MDM):**  

    - Kiadott mobileszköz-műveletek száma: zárolás, PIN-kód rest, törlése, a kivonása és a szinkronizálás most parancsok

    - Mobileszköz-házirendek száma  

    - A Configuration Manager és a Microsoft Intune és a hogyan azok regisztrált (csoportos, felhasználóalapú) által felügyelt mobileszközök száma  

    - Több regisztrált mobileszközzel rendelkező felhasználók száma  

    - Mobileszköz-lekérdezési ütemezés és a statisztika mobileszközök bejelentkezési időtartama  




- **A Microsoft Intune hibáinak elhárítása:**

    - Eszközműveletek száma és mérete (törlése, kivonás, zárolás), telemetriai adatokat, és a Microsoft Intune szolgáltatásba replikált adatüzenetek

    - Állapot, az állapot, a szoftverleltár, száma és mérete RDR-, DDR-, UDX, bérlői állapot, a Microsoft Intune-ból letöltött POL, napló, tanúsítvány, CRP, újraszinkronizálási, CFD, RDO, BEX, ISM és megfelelőségi üzenetek

    - Teljes és különbözeti felhasználószinkronizálásának statisztikái a Microsoft Intune



- **Helyszíni mobileszköz-felügyelet (MDM):**  

    - Windows 10-es csoportos regisztrációs csomagok és profilok száma  

    - Az alkalmazások helyszíni mobileszköz-felügyelettel végzett sikeres és sikertelen központi telepítéseinek statisztikái.  




- **Operációs rendszer központi telepítéséhez:**  

    - Rendszerindító lemezképek, illesztőprogramok, illesztőprogram-csomagok, csoportos küldésre képes terjesztési pontok, PXE-t támogató terjesztési pontok és feladatütemezések száma  

    - Kiadás frissítési házirendek száma

    - A feladat feladatütemezési lépés használati számát



- **Hely frissítéseket:**

    - A Configuration Manager telepített gyorsjavítások verziói



- **Szoftverfrissítések:**  

    - Automatikus központi telepítési szabályokban használt elérhető és határidős eltérések  

    - Hozzárendelések átlagos és maximális száma frissítésenként  

    - Ügyfelek frissítéseinek értékelése és vizsgálatütemezései  

    - Szoftverfrissítési pont által szinkronizált besorolások

    - Fürtjavítási statisztikák  

    - A Windows 10 express frissítések konfigurációja

    - Aktív Windows 10-es karbantartási tervek használt konfigurációk  

    - Az Office 365 telepített frissítéseinek száma  

    - Frissítési csoportok és hozzárendelések száma  

    - A frissítési csomagok és a maximális, minimális és átlagos száma, amelyek a csomagok terjesztési pontok száma  

    - A System Center frissítés-közzétevője létrehozott és telepített frissítések  

    - A Windows Update szolgáltatást használja a vállalati száma a Windows 10-ügyfelek  

    - A szinkronizáláshoz kötött automatikus központi telepítési szabályok száma  

    - Azon automatikus központi telepítési szabályok száma, amelyek új csoportot hoznak létre, vagy meglévő csoporthoz adnak hozzá frissítéseket  

    - Több központi telepítéssel rendelkező automatikus központi telepítési szabályok száma  
    - A frissítési csoportok száma, illetve a frissítések minimális, maximális és átlagos száma csoportonként  

    - A frissítések számát és százalékos aránya a frissítések, telepített, lejárt, felülírt, letöltött és EULA tartalmaz  

    - Szoftverfrissítési pont terheléselosztási statisztikák

    - Szoftverfrissítési pontok szinkronizálásának ütemezése  

    - Teljes és átlagos gyűjteményeket, amelyek a szoftverfrissítési központi telepítések száma és a telepített frissítések maximális és átlagos száma  

    - Frissítési vizsgálatok hibakódjai és a számítógépek száma  

    - A Windows 10 irányítópultjának tartalomverziói  



- **SQL- és teljesítményadatok:**  

    - ***[Új] *** Konfiguráció és a hely összegzési időtartama

    - A legnagyobb adatbázistáblák száma  

    - Felderítési működési statisztika (található objektumok száma)

    - A felderítést, engedélyezett és ütemezése (teljes, növekményes)

    - Az SQL AlwaysOn replika információt, használati, és állapota

    - SQL-változáskövetési teljesítménnyel kapcsolatos problémák, a megőrzési időtartam és a auto-karbantartási állapota

    - SQL-változáskövetési megőrzési időnél

    - ***[Új] *** Állapot üzenet többek között a leggyakoribb és legköltségesebb üzenettípusok teljesítménystatisztikáit.



- **Vegyes**

    - ***[Új] *** Konfigurációs az adatraktár Service adatpont többek között a szinkronizálási ütemezés és átlagos idő

    - A helyek számát az ébresztési a Lan (WOL)

    - Használati és teljesítményadatokat statisztikák jelentési  



##  <a name="bkmk_level3"></a> 3. szint – Teljes
A teljes szint az alapszintű és a bővített szinten az összes adatait tartalmazza. Ezenfelül további adatokat továbbít az Endpoint Protectionnel, a frissítések megfelelőségi százalékértékeivel és a szoftverfrissítésekkel kapcsolatban.  Ez a szint speciális diagnosztikai információkat, például rendszerfájlokat és a memóriáról készült pillanatképeket, beleértve például, hogy a rögzítési időpontjában már létezett a memóriában vagy naplófájlokban található személyes adatokat is tartalmazhatnak.

A System Center Configuration Manager verzió 1702, ez a szint a következőket tartalmazza:

- Az automatikus központi telepítési szabályok értékelésének ütemezési adatai

- ATP állapotának összegzése

- Gyűjtemények kiértékelési és frissítési statisztikái

- Megfelelőségi beállítások: SCEP, VPN, Wi-Fi és a megfelelőségi szabályzat sablon konfigurációs adatait a lejárt szoftverfrissítések csoportok száma

- DCM konfigurációs csomag a System Center Configuration Manager használata

- Részletes ügyfél-telepítési telepítési hibák
- Az Endpoint Protection állapotösszegzése (beleértve a védett, a kockázatnak kitett, az ismeretlen és a nem támogatott ügyfelek számát)

- Az Endpoint Protection házirend-konfigurációja

- ***[Új] *** Folyamatok konfigurált telepítési működés az alkalmazások listája

- A szoftverfrissítések legutóbbi vizsgálata óta eltelt órák minimális, maximális és átlagos száma

- A szoftverfrissítés-telepítési gyűjtemények inaktív ügyfeleinek minimális, maximális és átlagos száma

- Szoftverfrissítések minimális, maximális és átlagos száma csomagonként

- MSI-termékkód (általános alkalmazások, amelyeket az ügyfelek központi telepítése)

- A szoftverfrissítési központi telepítések összesített megfelelősége

- Szoftverfrissítési központi telepítések hibakódjai és azok számai

- Szoftverfrissítési központi telepítések adatai (központi telepítések, amelyek az ügyfél UTC idő, és a szükséges és a csendes, és újraindítás tiltási nem kötelező)

- Szoftverfrissítési pont által szinkronizált frissítési szoftvertermékek

- A szoftverfrissítések vizsgálatainak százalékos sikerességi aránya

- A környezetben 50 legfontosabb processzorok

- EAS vonatkozó feltételes hozzáférési szabályzatok (letiltás vagy karantén értékű) eszközöket, amelyek az Intune kezeli típusa

- Windows áruház üzleti alkalmazás részletes adatainak (például AppID, online vagy offline állapotban és megvásárolt licencek teljes száma a szinkronizált alkalmazások listája nem összesített)

