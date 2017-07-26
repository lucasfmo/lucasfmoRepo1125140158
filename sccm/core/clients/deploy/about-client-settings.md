---
title: "Ügyfél-beállítások |} Microsoft Docs"
description: "Válassza az ügyfél-beállításokat a felügyeleti konzol a System Center Configuration Manager használatával."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 3d90f16eac59b7069ff2f33170eba85d2cde65ef
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>A System Center Configuration Manager ügyfél beállításairól

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Minden ügyfél beállításai a System Center Configuration Manager felügyelete a Configuration Manager konzolt a **ügyfélbeállítások** csomópontja a **felügyeleti** munkaterületen. A Configuration Manager különböző alapértelmezett beállításokkal rendelkezik. Ha megváltoztatja az alapértelmezett ügyfélbeállításokat, ezek a beállítások a hierarchia összes ügyfelére érvényesek. Emellett egyéni ügyfélbeállításokat is konfigurálhat, amelyek felülírják az alapértelmezett ügyfélbeállításokat, ha gyűjteményekhez rendeli őket. További információ az ügyfélbeállítások konfigurálásáról: [Az ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-settings.md).  

Az ügyfélbeállítások jelentős része magától értetődő. Másokkal a dokumentum ismerteti.  

## <a name="background-intelligent-transfer-service"></a>A háttérben futó intelligens átviteli szolgáltatás  

-   **Korlátozza a maximális hálózati sávszélességet a háttérben futó BITS-adatátvitelek számára**  

   Ha ez a beállítás akkor **igaz** vagy **Igen**, az ügyfelek által használt BITS sávszélesség-szabályozás.  

-   **Szabályozó ablak indítási időpontja**  

   Adja meg a helyi kezdési ideje a BITS szabályozási időszakban.  

-   **Szabályozó ablak végidőpontja**  

   Adja meg a helyi befejezésének a BITS szabályozási időszakban. Ha egyenlő **szabályozó ablak indítási időpontja**, BITS sávszélesség-szabályozása mindig engedélyezve van.  

-   **Maximális átviteli sebesség a szabályozó ablakon belül (kb/s)**  

   Adja meg a maximális átviteli sebesség, amellyel az ügyfelek a időszak alatt történjen.  

-   **BITS-letöltések engedélyezése a szabályozó ablakon kívül**  

   Válassza ezt a beállítást, a Configuration Manager ügyfelek külön BITS-beállításokat használhatnak a megadott időszakon kívül.  

-   **Maximális átviteli sebesség a szabályozó ablakon kívül (kbps)**  

   Adja meg az ügyfelek által használt, a BITS-sávszélesség szabályozási időszakának, hogy a BITS sávszélesség-szabályozást a időszakon kívül kiválasztása kívülről maximális adatátviteli sebességet.  

## <a name="client-cache-settings"></a>Ügyfél-gyorsítótár beállításai

- **A BranchCache konfigurálása**

  1606 verziójától kezdve az a beállítás segítségével állítsa be az ügyfélszámítógépen [BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). A BranchCache gyorsítótárazás érdekében az ügyfélen, állítsa be **engedélyezze a BranchCache** való **Igen**.

- **Ügyfélgyorsítótár méretének beállítása**

  A Windows rendszerű számítógépeken az ügyfél gyorsítótárában telepíthetők alkalmazások és programok ideiglenes fájlok tárolására. Válasszon **Igen** meg **a gyorsítótár maximális mérete** (megabájtban vagy lemez százalékos hányada). Ha ez a beállítás **nem**, alapértelmezett mérete 5,120 MB.

## <a name="client-policy"></a>Ügyfélházirend  

-   **Ügyfélházirend lekérdezési időköze (perc)**  

   Adja meg, hogy milyen gyakran a következő Configuration Manager-ügyfelek ügyfélházirendet töltenek le:  

  -   Windows-számítógépek (például asztali gépek, kiszolgálók, laptopok)  

  -   A Configuration Manager által beléptetett mobileszközök  

  -   Mac számítógépek  

  -   Linux vagy UNIX rendszert futtató számítógépek  

-   **Felhasználói házirend engedélyezése az ügyfeleken**  

   Ha a beállítás **igaz** vagy **Igen**, és a Configuration Manager rendelkezzen [felderített a felhasználó](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), számítógépeken lévő ügyfelek fogadják alkalmazásokat és a programok, amelyek a bejelentkezett felhasználónak szánt.  

   Mivel az Alkalmazáskatalógus a felhasználók számára elérhető szoftverek listáját a helykiszolgálótól kap, ezt a beállítást nem kell lennie **igaz** vagy **Igen** a felhasználók megtekinthessék és lekérhessék alkalmazásokat az alkalmazáskatalógusból. De ha ez a beállítás **hamis** vagy **nem**, a következők nem fognak működni, amikor a felhasználók az Alkalmazáskatalógust használják:  

  -   A felhasználók nem telepíthetik az alkalmazáskatalógusban látható alkalmazásokat.  

  -   A felhasználónál nem jelenik meg értesítés alkalmazás-jóváhagyási kérelmeiről, ehelyett a jóváhagyási állapot ellenőrzéséhez frissítenie kell az alkalmazáskatalógust.  

  -   A felhasználók nem kapják meg a katalógusban közzétett alkalmazások revízióit és frissítéseit. De az alkalmazáskatalógusban változásai megjelennek.  

  -   Ha eltávolít egy alkalmazáspéldányt, miután az ügyfél már telepítette az alkalmazást a katalógusból, az ügyfél legfeljebb két napig továbbra is ellenőrzi, hogy az alkalmazás telepítve van-e.  

   Emellett, ha a beállítás értéke **hamis** vagy **nem**, felhasználók nem kapják meg a felhasználók vagy bármely más felügyeleti feladatokat a felhasználói házirendeket központilag telepített kötelező alkalmazásokat.  

   A felhasználók számára alkalmazza a beállítást, ha számítógépük csatlakozik az intranethez és az interneten. Lehet **igaz** vagy **Igen** Ha is engedélyezni szeretné az internetes felhasználói házirendeket.  

-   **Felhasználói házirend lekérésének engedélyezése internetes ügyfelektől**  

   Ha az ügyfél és a webhely Internet alapú ügyfélfelügyeletre vannak konfigurálva, és ez a beállítás, **igaz** vagy **Igen** és mindkét alábbi feltétel teljesül, a felhasználók fogadják a felhasználói házirendeket, ha a számítógép csatlakozik az interneten:  

  -   A **felhasználói házirend engedélyezése az ügyfeleken** ügyfélbeállítás van **igaz**, vagy **felhasználói házirend engedélyezése az ügyfeleken** van **Igen**.  

  -   Az internetes felügyeleti pont sikeresen hitelesíti a felhasználót Windows-hitelesítés (Kerberos vagy NTLM) használatával.  

   Ha a beállítást **Hamis** vagy **Nem**értéken hagyja, vagy valamelyik feltétel nem teljesül, az internethez kapcsolódó számítógép csak számítógép-házirendeket fogad. A felhasználók ennek ellenére továbbra is megtekinthetik, lekérhetik és telepíthetik az alkalmazásokat az internetes alkalmazáskatalógusból. Ha ez a beállítás **hamis** vagy **nem** , de **felhasználói házirend engedélyezése az ügyfeleken** van **igaz** vagy **felhasználói házirend engedélyezése az ügyfeleken** van **Igen**, felhasználók nem kapják meg a felhasználói házirendek mindaddig, amíg a számítógép csatlakozik az intranethez.  

   Az interneten lévő ügyfelek kezelésével kapcsolatos további információkért lásd: [ügyfél-kommunikáció az internetről vagy nem megbízható erdőben szempontjai](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) a [a System Center Configuration Managerben végpontok közötti kommunikáció](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

  > [!NOTE]  
  >  A felhasználók alkalmazás-jóváhagyási kérelmeihez nincs szükség felhasználói házirendekre vagy hitelesítésre.  

##  <a name="compliance-settings"></a>Megfelelőségi beállítások  

-   **A megfelelés kiértékelésének ütemezése**  

     Válasszon **ütemezés** referenciakonfiguráció telepítésekor a felhasználók számára megjelenített alapértelmezett ütemezés létrehozásához. Ez az érték minden egyes referenciakonfigurációnál beállítható a **Referenciakonfiguráció központi telepítése** párbeszédpanelen.  

-   **Felhasználói adatok és profilok engedélyezése**  

     Válasszon **Igen** Ha telepíteni szeretné [felhasználói adatok és profilok](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) konfigurálási elemeket, hogy a hierarchiában található Windows 8 rendszerű számítógép.  

## <a name="computer-agent"></a>Számítógépügynök  

-   **Alapértelmezett alkalmazáskatalógus webhely pont**  

     Configuration Manager használ a ezzel a beállítással csatlakoztatja a felhasználókat az alkalmazáskatalógushoz a Szoftverközpontból. Megadhatja az alkalmazáskatalógus weboldal-elérési pontját üzemeltető kiszolgálót NetBIOS-névvel vagy teljes tartománynévvel (FQDN), automatikus észlelést is beállíthat, vagy URL-t is megadhat testreszabott központi telepítésekhez. A legtöbb esetben az automatikus észlelés a legmegfelelőbb választás, ez ugyanis az alábbi előnyöket biztosítja:  

    -   Az ügyfelek automatikusan kap egy Alkalmazáskatalógus weboldal-elérési pontot rendel, ha a helyrendszer az Alkalmazáskatalógus weboldal-elérési pontja.  

    -   Alkalmazás Alkalmazáskatalógus weboldal-elérési pontjával az intraneten, amely a HTTPS használatára konfigurált rendszer előnyben részesíti a HTTPS-hez nincs konfigurálva. Ez segít, hogy egy Engedélyezetlen kiszolgáló elleni védelem érdekében.

    -   Ha az ügyfelek intranetes és Internet alapú ügyfélfelügyeletre vannak beállítva, által megadott az internetalapú Alkalmazáskatalógus weboldal-elérési pontja, ha vannak az interneten és az intranet-alapú Alkalmazáskatalógus webszolgáltatási pontja, ha az intraneten vannak.  

     Automatikus észlelés esetén nem garantált, hogy a rendszer a legközelebbi alkalmazáskatalógus weboldal-elérési pontot rendeli az ügyfelekhez. Az **Automatikus felismerés** használata nem minden esetben célszerű – ilyenek például a következő esetek:  

     -   Ha szeretné manuálisan beállítani a legközelebbi kiszolgálót az ügyfelek számára, hogy ne kelljen lassú hálózati kapcsolaton keresztül csatlakozniuk.  

     -   Ha szeretné beállítani, hogy melyik ügyfél melyik kiszolgálóhoz csatlakozzon – tesztelési, teljesítményhez kapcsolódó vagy üzleti okokból.  

     -   Ha nem szeretne akár 25 órát várni, vagy hálózatváltásra várakozni ahhoz, hogy az ügyfelek számára másik alkalmazáskatalógus weboldal-elérési pontot lehessen konfigurálni.  

     Ha adja meg az Alkalmazáskatalógus weboldal-elérési pontja helyett automatikus felismerés, adja meg az intranetes teljes Tartománynevet, hanem a NetBIOS-nevét. Ezzel csökkenthető a valószínűsége, hogy felhasználók bekéri a hitelesítő adatokat az intraneten az Alkalmazáskatalógushoz történő csatlakozáskor. A NetBIOS-név használatához teljesülnie kell az alábbi feltételeknek:  

     -   A NetBIOS-nevet az alkalmazáskatalógus weboldal-elérési pontjának tulajdonságai között kell megadni.  

     -   A WINS, vagy minden ügyfélnek az Alkalmazáskatalógus weboldal-elérési pontja ugyanabban a tartományban.  

     -   Az Alkalmazáskatalógus weboldal-elérési pontját használja a HTTP-ügyfélkapcsolatokat, vagy HTTPS-ügyfélkapcsolatokhoz van konfigurálva, és a webkiszolgáló-tanúsítvány van a NetBIOS-nevét.  

     Általában rendszer kéri a felhasználóktól a hitelesítő adatokat, ha az URL-címnek FQDN-t azonban nem az URL-címet az a NetBIOS-név. Ha a felhasználó az internetről csatlakozik, a rendszer várhatóan minden esetben kéri a hitelesítő adatokat, ez a kapcsolat ugyanis kötelezően az internetes teljes tartománynevet (FQDN) használja. Ha a rendszer hitelesítő adatokat kér a felhasználótól interneten keresztüli csatlakozás esetén, győződjön meg arról, hogy az alkalmazáskatalógus weboldal-elérési pontját futtató kiszolgáló képes a felhasználó fiókjának tartományvezérlőjéhez kapcsolódni, így a felhasználó a Kerberos protokollal hitelesíthető.  

    > [!NOTE]  
    >  Az automatikus felismerés működése:  
    >   
    >  Az ügyfél a szolgáltatás helyére vonatkozó kérelmet küld egy felügyeleti pontra. Ha az ügyféllel azonos helyen található alkalmazáskatalógus weboldal-elérési pont, a rendszer az ügyfélhez rendeli a kiszolgálót alkalmazáskatalógus-kiszolgálóként. Egynél több Alkalmazáskatalógus weboldal-elérési pontját a helyen érhető el, egy HTTPS-kompatibilis kiszolgáló elsőbbséget élvez a kiszolgáló a HTTPS nem engedélyezett. A szűrés után rendszer minden ügyfélnek kioszt egyik kiszolgálóra kívánja használni, mint az Alkalmazáskatalógus; A Configuration Manager e terheléskiegyenlítést több kiszolgáló között. Az ügyfél helye nincs az Alkalmazáskatalógus weboldal-elérési pontja, a felügyeleti pont nem determinisztikus módon visszaad egy Alkalmazáskatalógus weboldal-elérési pontját a hierarchiában.  
    >   
    >  Ha az ügyfél az intraneten, ha a választott Alkalmazáskatalógus weboldal-elérési pontja egy NetBIOS-nevet a katalógus URL-címe van konfigurálva, az ügyfelek kapnak a NetBIOS-név helyett az intranetes teljes Tartománynevet. Ha a rendszer az interneten észleli az ügyfelet, csak az internetes teljes tartománynevet (FQDN) osztja ki számára.  
    >   
    >  Az ügyfél 25 óránként küldi el a szolgáltatás helyére vonatkozó kérelmet, illetve minden alkalommal, amikor hálózatváltást észlel. Ha például az ügyfél az intranetről az internetre vált, és az ügyfél képes internetes felügyeleti pontot találni, az internetes felügyeleti pont alkalmazáskatalógus weboldal-elérési pontként internetes kiszolgálót biztosít az ügyfeleknek.  

-   **Az alapértelmezett alkalmazáskatalógus webhely hozzáadása az Internet Explorer megbízható helyek zónához**  

     Ha ez a beállítás **igaz** vagy **Igen**, a jelenlegi alapértelmezett Alkalmazáskatalógus webhely URL-cím automatikusan hozzáadódik az ügyfeleken az Internet Explorer Megbízható helyek zónájába.  

     Ez a beállítás biztosítja, hogy az Internet Explorer védett módja ne legyen engedélyezve. Ha a védett mód engedélyezve van, a Configuration Manager-ügyfél nem feltétlenül képes alkalmazásokat telepíteni az alkalmazáskatalógusból. Alapértelmezés szerint a megbízható helyek zónája a felhasználói bejelentkezést is támogatja az alkalmazáskatalógushoz, amihez Windows-hitelesítés szükséges.  

     Ha nem adja meg a beállítás értéke **hamis**, előfordulhat, hogy a Configuration Manager ügyfelek nem lesznek képesek alkalmazásokat telepíteni az alkalmazáskatalógusból, ha az Internet Explorer ezen beállításait egy másik zónában konfigurálja a katalógus URL-címe, amellyel az ügyfelek számára.  

    > [!NOTE]  
    >  Amikor a Configuration Manager egy alapértelmezett Alkalmazáskatalógust vesz fel a megbízható helyek zónájába, a Configuration Manager eltávolítja az előző alapértelmezett katalógus URL-címe a Configuration Manager hozzáadott új bejegyzés hozzáadása előtt.  
    >   
    >  A Configuration Manager nem adható hozzá az URL-címet, ha már szerepel az egyik biztonsági zónában. Ebben a forgatókönyvben állítsa az URL-cím eltávolítása a zónából, vagy manuálisan konfigurálja a szükséges Internet Explorer-beállításokat.  

-   **Az emelt szintű megbízhatóság módban való futás engedélyezése a Silverlight alkalmazások részére**  

     Ezzel a beállítással lehet **Igen** Ha a felhasználó a Configuration Manager-ügyfél és az Alkalmazáskatalógust használják.  

     A módosított beállítás akkor lép érvénybe, amikor a felhasználó legközelebb betölti a böngészőjét, vagy frissíti a jelenleg megnyitott böngészőablakot.  

     Ezzel a beállítással kapcsolatos további információkért lásd: [tanúsítványokat a Microsoft Silverlight 5 és az alkalmazáskatalógushoz szükséges emelt szintű megbízhatósági módban](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5) a [biztonsága és adatvédelme a System Center Configuration Manager felügyelet](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   **A Szoftverközpontban megjelenített név**  

     Írja be a felhasználók számára a Szoftverközpontban megjelenített nevet. A márkajelzés alapján a felhasználók azonosíthatják, hogy az alkalmazás megbízható forrásból származik.  

-   **Az új Szoftverközpont használata**  

     Ha engedélyezve van, ezek az ügyfélbeállítások által megcélzott minden ügyfélszámítógép az új Szoftverközpontot fogja használni. A Szoftverközpont jeleníti meg a felhasználók számára elérhető alkalmazások, melyeket korábban csak a Silverlight-függő Alkalmazáskatalógusban érhető el.  

     Az Alkalmazáskatalógus weboldal-elérési pontja és az Alkalmazáskatalógus webszolgáltatási pontja helyrendszerszerepkör továbbra is szükséges, a felhasználók számára elérhető alkalmazások megjelenjenek a Szoftverközpontban.  

     További információk: [Az alkalmazáskezelés tervezése és konfigurálása a System Center Configuration Managerben](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   **Telepítési engedélyek**  

    > [!WARNING]  
    >  Ez a beállítás az alkalmazáskatalógusra és a Szoftverközpontra vonatkozik. A beállítás a vállalati portál használatára nincs hatással.  

     Adja meg, hogy mely felhasználók kezdeményezhetik szoftverek, szoftverfrissítések és feladatütemezések telepítését:  

    -   **Minden felhasználó**: Bármilyen engedéllyel, kivéve az ügyfélszámítógépre bejelentkezett felhasználók kezdeményezheti szoftverek, szoftverfrissítések és feladatütemezések telepítését.  

    -   **Csak a rendszergazdák**: Az ügyfélszámítógépre bejelentkezett felhasználók kezdeményezhetik szoftverek, szoftverfrissítések és feladatütemezések telepítését a helyi Rendszergazdák csoport tagjának kell lennie.  

    -   **Csak rendszergazdák és elsődleges felhasználók**: Az ügyfélszámítógépre bejelentkezett felhasználók kezdeményezhetik szoftverek, szoftverfrissítések és feladatütemezések a helyi Rendszergazdák csoport tagjaként vagy a számítógép elsődleges felhasználójának kell lennie.  

    -   **Egy felhasználó sem**: Az ügyfélszámítógépre bejelentkezett felhasználók nem kezdeményezheti szoftverek, szoftverfrissítések és feladatütemezések telepítését. A számítógéphez szükséges központi telepítések mindig települnek a határidő lejártakor. A felhasználók nem indíthatnak a szoftvertelepítést, az Alkalmazáskatalógus vagy a Szoftverközpontból.  

-   **BitLocker PIN-kód bevitelének felfüggesztése újrainduláskor**  

     Ha a BitLocker PIN-kód bevitele konfigurálva van a számítógépeken, ez a beállítás mentesíthet a PIN-kód bevitele alól, amikor a számítógép újraindul egy szoftvertelepítés után.  

    -   **Mindig**: A Configuration Manager átmenetileg felfüggeszti a BitLocker, az olyan szoftvert telepített, újra kell indítani, és kezdeményezte a számítógép újraindítását követően. Ez a beállítás csak a számítógép újraindítását, hogy a Configuration Manager által kezdeményezett, és nem függeszti fel a BitLocker PIN-kód megadását, amikor a felhasználó indítja újra a számítógépet a követelmény vonatkozik. A BitLocker PIN-kód bevitelének követelménye visszaáll a Windows elindítása után.

    -   **Soha ne**: A Configuration Manager nem függeszti fel a BitLocker a következő számítógép következő indításakor, miután újraindítást igénylő szoftver telepítve van. Ilyen esetben a szoftvertelepítés nem tud befejeződni, amíg a felhasználó be nem írja a PIN-kódot a szokásos rendszerindításhoz és a Windows betöltéséhez.

-   **Egy másik szoftver kezeli az alkalmazások és szoftverfrissítések központi telepítését**  

     Ezt a beállítást csak akkor engedélyezze, ha a következő körülmények egyike fennáll:  

    -   Olyan gyártói megoldást használ, amelyhez engedélyezni kell ezt a beállítást.  

    -   Használhatja a Configuration Manager szoftverfejlesztői készlet (SDK) kezelheti az ügyfeleken futó ügynökök értesítéseit, és az alkalmazások és szoftverfrissítések telepítése.  

    > [!WARNING]  
    >  Akkor válassza ezt a beállítást, ha ezek a feltételek egyike sem érvényes, ha szoftverfrissítések és alkalmazások nem települnek az ügyfeleken. Ez a beállítás nem tiltása felhasználók alkalmazásokat telepítsenek az Alkalmazáskatalógusból vagy akadályozható meg az csomagok, programok és feladatütemezések telepítését az ügyfélszámítógépeken.  

-   **PowerShell végrehajtási házirend**  

     Állítsa be, hogyan a Configuration Manager-ügyfelek Windows PowerShell-parancsfájlok futtathatók. Ezek a parancsfájlok gyakran használják konfigurációs elemek a megfelelőségi beállításokhoz észlelést. Ezek is elküldhetők központi telepítésben is szabványos parancsfájlként.  

    -   **Áthidaló**: A Configuration Manager-ügyfél nincs hatással a Windows PowerShell-konfiguráció az ügyfélszámítógépen, hogy futtathatók az aláíratlan parancsfájlok.  

    -   **Korlátozott**: A Configuration Manager-ügyfél az ügyfélszámítógépen Windows PowerShell-konfigurációt használja. Ez a konfiguráció határozza meg, hogy futtatható-e az aláíratlan parancsfájlok.  

    -   **Minden aláírt**: A Configuration Manager-ügyfél futtatja a parancsfájlokat, csak akkor, ha megbízható közzétevő aláírta őket. Ez a korlátozás az ügyfélszámítógép aktuális Windows PowerShell-konfigurációjától függetlenül érvényes.  

     Ez a beállítás akkor legalább a Windows PowerShell 2.0-s verziójában. Az alapértelmezett érték **minden aláírt**.  

    > [!TIP]  
    >  Ha az aláíratlan parancsfájlok nem tudnak futni ezen ügyfélbeállítás miatt, a Configuration Manager az alábbi módokon jelenti ezt a hibát:  
    >   
    > -   Hibaazonosító **0X87D00327** és **parancsfájl nincs aláírva** a központi telepítési állapothibaként a **figyelés** a Configuration Manager konzol munkaterületén.  
    > -   Hibakódok és leírások az **0X87D00327** és **parancsfájl nincs aláírva** vagy **0X87D00320** és **a parancsfájlfuttató még nem lett telepítve** hiba típusú **hibája az inicializálási** a jelentésekben. Példa: **az eszközhöz tartozó alapkonfiguráció konfigurációs elemek hibái**.  
    > -   Az üzenet **parancsfájl nincs aláírva (hiba: 87D 00327; Forrás: CCM)** a a **DcmWmiProvider.log** fájlt.  

-   **Határidő véletlenszerűsítésének letiltása**  

     Ez a beállítás meghatározza, hogy az ügyfél használ-e legfeljebb kétórás aktiválási késleltetést számára a határidő elérésekor telepítse a szükséges szoftverfrissítéseket. Alapértelmezésben az aktivációs késleltetés le van tiltva.  

     A virtuális asztali infrastruktúra (VDI) használata esetén ez a késés segítheti a Processzor feldolgozási elosztását, és az adatátviteli, amelyen több virtuális gép a Configuration Manager-ügyfelet futtató számítógép. Akkor is, ha a VDI-t, nem hajtja végre, ha sok ügyfél telepíti egyidejűleg ugyanazokat a frissítéseket, ez kedvezőtlen hatással növelheti a helykiszolgáló Processzorának terhelése. Azt is lelassíthatják a terjesztési pontokat, és jelentősen csökkentheti a rendelkezésre álló hálózati sávszélességet.  

     Ha szükséges szoftverfrissítéseket késleltetés nélkül kell telepítve a konfigurált határidő elérésekor, válassza ki a **Igen** ehhez a beállításhoz.  

-   **Türelmi idő a kényszerítésre a telepítési határidő (óra) után**

     Bizonyos esetekben előfordulhat, hogy szeretné telepíteni a szükséges alkalmazások központi telepítéseit vagy szoftverfrissítéseket minden konfigurált határidők túl további időt hagy a felhasználók. Ez lehet, hogy általában szükség lehet, amikor a számítógép ki van kapcsolva hosszabb ideig, és számos alkalmazás vagy frissítés központi telepítéséhez szükséges. Például ha a felhasználó csak adott vissza a szabadsága, előfordulhat, hogy rendelkeznek long vár, amíg a lejárt alkalmazásként telepíti a központi telepítések. Ez a probléma megoldásához meghatározásához egy kényszerítési türelmi ügyfélbeállítások a Configuration Manager telepítése egy gyűjteménybe.

     Megadhat egy 1 és 120 óra türelmi időszak. Ezzel a beállítással a rendszerbe állítási tulajdonság együtt **felhasználói beállítások szerint a telepítés kényszerítésének késleltetés**. További részletekért lásd: [telepíthet központilag alkalmazásokat](/sccm/apps/deploy-use/deploy-applications).

##  <a name="computer-restart"></a>A számítógép újraindítása  
 Amikor megadja ezeket a számítógép-újraindítási beállításokat, győződjön meg arról, hogy az újraindítás átmeneti értesítésének időtartama és az utolsó visszaszámlálás időtartama rövidebb, mint a legrövidebb karbantartási időszak, amely érvényben van a számítógépen.  

 További információ a karbantartási időszakokról: [Karbantartási időszakok használata a System Center Configuration Managerben](../../../core/clients/manage/collections/use-maintenance-windows.md).  

##  <a name="endpoint-protection"></a>Endpoint Protection  

-   **Az Endpoint Protection ügyfél kezelése az ügyfélszámítógépeken**  

     Válasszon **igaz** vagy **Igen** Ha be szeretné állítani a meglévő Endpoint Protection-ügyfeleket a hierarchiájában lévő számítógépeken.  

     Válassza ezt a beállítást, ha már telepítette az Endpoint Protection-ügyfelet, és szeretne felügyelni, akkor a Configuration Managerrel.  

     Emellett válassza ezt a beállítást, ha szeretne létrehozni egy parancsfájl egy meglévő kártevőirtó megoldás eltávolítása az Endpoint Protection ügyfél telepítése, és ezt a parancsfájlt telepítése a Configuration Manager-alkalmazás vagy csomag és program használatával.  

-   **Endpoint Protection ügyfél telepítése az ügyfélszámítógépeken**  

     Válasszon **igaz** vagy **Igen** telepítésével és engedélyezésével az Endpoint Protection-ügyfél az ügyfélszámítógépeken, ha még nincs telepítve.  

    > [!NOTE]  
    >  Ha az Endpoint Protection-ügyfél már telepítve van, kiválasztása **hamis** vagy **nem** művelet nem távolítja el az Endpoint Protection-ügyfelet. Az Endpoint Protection-ügyfél eltávolításához állítsa be a **Endpoint Protection ügyfél kezelése az ügyfélszámítógépeken** ügyfélbeállítást **hamis** vagy **nem**. Ezt követően telepítheti egy csomagot és programot az Endpoint Protection-ügyfél eltávolításához.  

-   **Az írási szűrőket tartalmazó Windows Embedded-eszközök esetén hajtsa végre az Endpoint Protection ügyféltelepítést (többszöri újraindítás szükséges)**  

     Válasszon **Igen** letilthatja az írási szűrőt a Windows Embedded-eszközön, majd indítsa újra az eszközt. Ezzel végrehajtja a telepítést az eszközön.  

     Ha a **Nem** értéket adja meg, az ügyfél egy átmeneti területre kerül, amelynek tartalma törlődik az eszköz újraindításakor. Ilyenkor az Endpoint Protection-ügyfél telepítése nem történik meg, amíg egy másik telepítés el nem végzi a módosításokat az eszközön. Ez az alapértelmezett beállítás.  

-   **Szükséges Újraindítás mellőzése az Endpoint Protection ügyfél telepítése után**  

     Válasszon **igaz** vagy **Igen** arra, hogy letiltsa a számítógép újraindítását, ha szükséges az Endpoint Protection ügyfél telepítése után.  

    > [!IMPORTANT]  
    >  Ha az Endpoint Protection-ügyfél a számítógép újraindítását igényli, és ez a beállítás **hamis**, az újraindítás megtörténik függetlenül a beállított karbantartási időszakokon.  

-   **Megengedett időtartam, amikor a felhasználók elhalaszthassák az Endpoint Protection telepítéséhez szükséges újraindítást (óra)**  

     Adja meg az órát, hogy a felhasználók elhalaszthassák a számítógép újraindítását, ha ez szükséges az Endpoint Protection ügyfél telepítése után. Ez a beállítás konfigurálható, ha csak a **szükséges Újraindítás mellőzése az Endpoint Protection ügyfél telepítése után** lehetőség **hamis**.  

-   **Az alternatív források (például a Windows Update, Microsoft Windows Server Update Services vagy UNC-megosztásnevek) letiltása az ügyfélszámítógépek kezdeti definíciófrissítéséhez**  

     Válasszon **igaz** vagy **Igen** Ha azt szeretné, hogy a Configuration Manager csak a kezdő definíciófrissítést telepítse az ügyfélszámítógépeken. Ez a beállítás hasznos lehet a szükségtelen hálózati kapcsolódások és a hálózati sávszélesség csökkenésének elkerüléséhez a definíciófrissítés első telepítésekor.  

##  <a name="hardware-inventory"></a>Hardverleltár  

-   **Egyedi MIF-fájl maximális mérete (kB)**  

     Adja meg a maximális méretét kilobájtban, minden egyéni Management Information Format (MIF) fájl, hogy egy ügyfél egy hardverleltározási ciklus során engedélyezett. Ha bármely MIF-fájl túllépi ezt a méretet, a Configuration Manager-Hardverleltár nem dolgozza fel azokat. Megadhat egy 1 és 5000 KB-os méret. Az alapértelmezett beállítás 250 KB. Ez a beállítás nincs hatással a normál hardverleltár-adatfájlra.  

    > [!NOTE]  
    >  Ez a beállítás csak az alapértelmezett ügyfélbeállításban érhető el.  

-   **Hardverleltárosztályok**  

     A Configuration Managerben az sms_def.mof fájl manuális szerkesztése nélkül ügyfelektől begyűjtött hardverinformációk bővítheti. Válasszon **osztályok beállítása** Ha a Configuration Manager hardverleltárának bővítéséhez. További információkért lásd: [Hardverleltár konfigurálása a System Center Configuration Managerben](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

-   **MIF-fájlok gyűjtése**  

     A beállítás segítségével megadhatja, hogy a MIF-fájlok gyűjtése a Configuration Manager-ügyfelek a Hardverleltár során.  

     A Hardverleltár begyűjthesse a MIF-fájl akkor kell a megfelelő helyen, az ügyfélszámítógépen. Alapértelmezés szerint a fájlok találhatók az alábbiak szerint:  

    -   IDMIF-fájlok a Windows\System32\CCM\Inventory\Idmif mappában kell lennie.  

    -   NOIDMIF-fájlok a Windows\System32\CCM\Inventory\Noidmif mappában kell lennie.  

    > [!NOTE]  
    >  Ez a beállítás csak az alapértelmezett ügyfélbeállításban érhető el.

-   **Maximális véletlenszerű késleltetés**

    A hardver információk begyűjtése véletlenszerű legfeljebb négy óránként, hogy a művelet egyidejűleg az összes ügyfél a hely nem veszi. Ahhoz, hogy korlátozni az az idő, amely során a művelet akkor történik meg a késleltetési állíthatja be.      

##  <a name="metered-internet-connections"></a>Mért internetkapcsolatok használata esetén  
 Kezelheti a Windows 8 rendszerű ügyfélszámítógépek közötti kommunikáció módját a Configuration Manager-helyek Ha mért internetkapcsolatot használnak. Ha forgalmi díjas internetkapcsolatot használ, az internetszolgáltatók néha díjat számítanak fel a küldött és fogadott adatok mennyisége után.  

> [!NOTE]  
>  A konfigurált ügyfélbeállítás a következő esetekben nem érvényes a Windows 8 rendszerű ügyfélszámítógépekre:  
>   
> -   A számítógép be van kapcsolva barangoló adatkapcsolatot használ: A Configuration Manager-ügyfél nem végez a Configuration Manager-helyek adatátvitel igénylő feladatok.  
> -   A Windows hálózati kapcsolatának tulajdonságai nem forgalmi díjas vannak konfigurálva: A Configuration Manager-ügyfél úgy viselkedik, mintha nem forgalmi díjas internetkapcsolatot használna, és átviszi az adatokat a Configuration Manager-helyek számára.  

-   **Ügyfél-kommunikáció mért internetkapcsolatok használata esetén**  

     A legördülő listából válassza az alábbiak egyikét a Windows 8 rendszerű ügyfélszámítógépekhez:  

    -   **Engedélyezése**: Minden ügyfél-kommunikáció engedélyezett a forgalmi díjas internetkapcsolaton keresztül, kivéve, ha az ügyféleszköz barangoló adatkapcsolatot használ.  

    -   **Korlát**: Csak a következő ügyfél-kommunikáció engedélyezett a forgalmi díjas internetkapcsolaton keresztül:  

        -   Ügyfélházirend lekérése  

        -   A helynek küldendő ügyfélállapot-üzenetek  

        -   Az alkalmazáskatalógust használó szoftvertelepítési kérések  

        -   Szükséges központi telepítések (ha elérkezett a telepítési határidő)  

        > [!IMPORTANT]  
        >  Ha egy felhasználó szoftvertelepítést kezdeményez a szoftverközpontból vagy az alkalmazáskatalógusból, ezek mindig engedélyezettek, függetlenül a forgalmi díjas internetkapcsolat beállításaitól.  

         Ha a mért internetkapcsolat eléri az adatátviteli korlátot, az ügyfél már nem Configuration Manager-helyek kommunikálni próbál.  

    -   **Blokk**: A Configuration Manager-ügyfél nem próbál kommunikálni Configuration Manager-helyek, ha mért internetkapcsolatot használjanak. Ez az alapértelmezett beállítás.  

##  <a name="power-management"></a>Energiagazdálkodás  

-   **A felhasználók kizárhassák az eszközeiket az energiagazdálkodásból**  

     A legördülő listából válassza ki a **igaz** vagy **Igen** ahhoz, hogy a Szoftverközpont felhasználóinak számítógépük kizárását minden konfigurált energiatakarékossági beállításból.  

-   **Ébresztési proxy engedélyezése**  

     Válassza az **Igen** lehetőséget a hálózati ébresztés beállítás kiegészítéséhez, ha az egyedi küldésű csomagokra van konfigurálva.  

     Az ébresztési proxyval kapcsolatos további információkért lásd: [tervezése a System Center Configuration Manager ügyfelek felébresztése](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

    > [!WARNING]  
    >  Ne engedélyezze az ébresztési proxyt éles hálózati környezetben anélkül, hogy először megértené annak működését és kiértékelné tesztkörnyezetben.  

-   **Ébresztési proxy portszáma (UDP)**  

     Tartsa meg a portszámot, amelyeket a felügyelt számítógépek használja az ébresztési csomagok küldését az alvó számítógépek esetén az alapértelmezett értéket. Vagy az Ön által választott értékre számának megváltoztatására.  

     Az itt megadott portszám használatakor a Windows tűzfalat futtató ügyfelek esetében automatikusan konfigurálja a **Windows tűzfal-kivétel az ébresztési proxy** lehetőséget. Ha az ügyfelek más tűzfalat futtatnak, akkor manuálisan kell konfigurálnia az ehhez a beállításhoz megadott UDP-portszám engedélyezését.  

-   **Helyi hálózati ébresztés portszáma (UDP)**  

     Tartsa meg a 9-es, alapértelmezett értéket, ha nem változtatta meg a hálózati ébresztés (UDP) portszám a a **portok** lapot a hely **tulajdonságok**.  

    > [!IMPORTANT]  
    >  Ennek a számnak meg kell egyeznie a hely **Tulajdonságok**beállításában megadottal. Ha megváltoztatja ezt a számot, egy helyen, akkor nem automatikusan frissül a többi beállítási helyet.  

##  <a name="remote-tools"></a>Táveszközök  

-   **Ügyfelek távvezérlésének engedélyezése** hibakód és **Tűzfalkivételi profilok**  

     Válassza ki, hogy engedélyezve van-e a Configuration Manager Távvezérlés az összes olyan ügyfélszámítógépen, amely megkapja ezeket az ügyfélbeállításokat. Válasszon **konfigurálása** távvezérlés engedélyezése. Szükség esetén konfigurálja a tűzfal beállításait, amivel lehetővé teszi a távvezérlés működését az ügyfélszámítógépeken.  

     A távvezérlés alapértelmezés szerint le van tiltva.  

    > [!IMPORTANT]  
    >  Ha nincsenek megadva a tűzfal beállításai, akkor lehetséges, hogy nem fog megfelelően működni a távvezérlés.  

-   **A felhasználók megváltoztathatják a házirend vagy az értesítés beállításait a szoftverközpontban**  

     Válassza ki, hogy a felhasználók módosíthatják-e a távvezérlési lehetőségeket a szoftverközpontban.  

-   **Távvezérlés engedélyezése egy felügyelet nélküli számítógéphez**  

     Válassza ki, hogy a rendszergazda használhatja-e a távvezérlést egy kijelentkezett vagy zárolt ügyfélszámítógép elérésére. Csak a bejelentkezett vagy nem zárolt számítógépet távolról vezérelhető, ha ez a beállítás le van tiltva.  

-   **Adatkérés a felhasználónak a távvezérlés engedélyezéséhez**  

     Válassza ki az ügyfélszámítógép megjelenjen-e egy üzenetet, amely bekéri azt a felhasználói engedélyek, mielőtt engedélyezi a távvezérlési munkamenet.  

-   **Távvezérlési jogosultság megadása a helyi rendszergazdák csoportjának**  

     Válassza ki, hogy a helyi rendszergazda azon a kiszolgálón, a távvezérlési kapcsolatot kezdeményez létesíthet-e a távvezérlési munkamenetet az ügyfélszámítógépekhez.  

-   **Engedélyezett hozzáférési szint**  

     Adja meg a távvezérlési elérés engedélyezett szintjét. A következő lehetőségek közül választhat:  

    -   Teljes hozzáférés  

    -   Csak megtekintés  

    -   Nincsenek  

-   **Feljogosított megtekintők**  

     Válasszon **jogosultak** megnyitásához a **ügyfélbeállítás konfigurálása** párbeszédpanel és a Windows-felhasználókat, akik az ügyfélszámítógépek számára a távvezérlési munkamenetet hozhatnak létre a nevét adja meg.  

-   **Munkamenet-értesítési ikon megjelenítése a tálcán**  

     Ezzel a beállítással ikon megjelenítése a tálcán ügyfél számítógépek azt jelzi, hogy a távvezérlési munkamenet aktív.  

-   **Munkamenet kapcsolatjelző sávjának megjelenítése**  

     Ezzel a beállítással egy jól látható munkamenet kapcsolatjelző sávjának megjelenítése ügyfélen számítógépek azt jelzi, hogy a távvezérlési munkamenet aktív.  

-   **Hang lejátszása az ügyfélen**  

     Válassza ezt a beállítást jelzik, ha egy távvezérlési munkamenet aktív az ügyfélszámítógépen a hang segítségével. Lejátszhat egy hangot a munkamenet csatlakozásakor vagy lekapcsolódásakor, de azt is beállíthatja, hogy a munkamenet során ismétlődően lehessen hallani a hangot.  

-   **A nem kért távsegítség beállításainak kezelése**  

     Válassza ezt a beállítást, hogy a Configuration Manager nem kért távsegítségi munkameneteket kezelhessen.  

     Nem kért távsegítségi munkamenetekben az ügyfélszámítógép felhasználója nem kért segítséget a munkamenet indítása.  

-   **A kért távsegítség beállításainak kezelése**  

     Válassza ezt a beállítást, hogy a Configuration Manager kért távsegítségi munkameneteket kezelhessen.  

     A kért Távsegítség-munkamenet az ügyfélszámítógépen a felhasználói kérelmet küldött a rendszergazda Távsegítség.  

-   **Távsegítség hozzáférési szintje**  

     Válassza ki a Configuration Manager-konzolon kezdeményezett Távsegítség munkameneteihez hozzárendelése hozzáférési szintet.  

    > [!NOTE]  
    >  Az ügyfélszámítógép felhasználójának mindig engedélyeznie kell a távsegítség munkamenetének létrejöttét.  

-   **Távoli asztal beállításainak kezelése**  

     Válassza ezt a beállítást, hogy a Configuration Manager távoli asztali munkameneteket kezelhessen a számítógépekkel.  

-   **A feljogosított megjelenítők csatlakozásának engedélyezése a távoli asztal kapcsolat használatával**  

     Ezzel a beállítással a feljogosított megjelenítők listájában megadott felhasználókat vehető fel a távoli asztal helyi felhasználói csoportba az ügyfélszámítógépeken.  

-   **Hálózati szintű hitelesítés szükséges a Windows Vista operációs rendszert vagy későbbi verziókat futtató számítógépeken**  

     Válassza ezt a biztonságosabb beállítást, ha azt szeretné, hogy a Windows Vista rendszerű ügyfélszámítógépek távoli asztali kapcsolatot létrehozni a hálózati szintű hitelesítés használandó vagy újabb. Hálózati szintű hitelesítés kezdetben szükséges kevesebb távoli számítógép-erőforrásokra, mivel a felhasználói hitelesítés befejezné a távoli asztali kapcsolat létesítése előtt. Ez a módszer sokkal biztonságosabb, mert segít megvédeni a számítógépet a rosszindulatú felhasználóktól és szoftverektől, valamint a szolgáltatásmegtagadásos támadás veszélyét is csökkenti.  

## <a name="software-deployment"></a>Szoftver központi telepítése  

-   **A központi telepítés újraértékelésének ütemezése**  

     Konfiguráljon egy ütemezést az, amikor a Configuration Manager értékelje újra a követelményszabályait. Az alapértelmezett érték 7 naponta.  

    > [!IMPORTANT]  
    >  Azt javasoljuk, hogy ne változtassa ezt az értéket az alapértelmezettnél alacsonyabb érték. Ennek során, amely hátrányosan befolyásolhatja a hálózat és az ügyfélszámítógépek a számítógépek teljesítményére.  

     Ez a művelet egy Configuration Manager ügyfélszámítógépről is kezdeményezheti válassza a **központi alkalmazástelepítés kiértékelési ciklusa** a a **műveletek** lapján **Configuration Manager** a Vezérlőpulton.  

##  <a name="software-inventory"></a>Szoftverleltár  

-   **Részletes jelentést küldő leltár**  

     Adja meg a fájlok adatainak szintjét a leltárban. Leltárt készíthet a fájl adatait a fájl vagy a fájl összes adatát tartozó termék részletes adatait.  

-   **Leltározandó fájltípusok**  

     Ha meg szeretné határozni a leltárban szereplő fájlok típusait, válassza ki a **típusok beállítása** , majd konfigurálja a következőket a **ügyfélbeállítás konfigurálása** párbeszédpanel:  

    > [!NOTE]  
    >  Ha több egyéni ügyfélbeállítás is vonatkozik egy számítógépre, a készlet egyes beállítások visszaadó összevonva fogja tartalmazni.  

    -   Válassza ki a **új** ikonra egy új fájltípus leltárhoz adásához. Ezt követően adja meg a következő információkat a **leltározott fájlok tulajdonságai** párbeszédpanel:  

        -   **Név**: Adja meg a leltározni kívánt fájl nevét. Használhatja a * *\**  karaktert bármilyen szöveglánc helyettesítéséhez, és a **?** karaktert bármely egy karakter helyettesítéséhez. Például, ha szeretné leltározni az összes .doc kiterjesztésű fájlt, adja meg a fájlnevet  **\*.doc**.  

        -   **Hely**: Válasszon **beállítása** megnyitásához a **elérési útvonal tulajdonságai** párbeszédpanel megnyitásához. Konfigurálhatja a szoftverleltár a megadott fájl összes merevlemezén keresse, egy adott elérési úton keressen (például **C:\Folder**), vagy egy adott változóban keressen (például *% windir %*). A megadott elérési utak almappáiban is kereshet.  

        -   **Titkosított és tömörített fájlok kizárása**: Ha ezt a lehetőséget választja, semmilyen tömörített vagy titkosított fájl nem lesz Leltározva.  

        -   **A Windows mappában található fájlok kizárása**: Ha ezt a lehetőséget választja, a Windows mappából és almappáiból semmilyen fájl nem lesz Leltározva.  

    -   Válasszon **OK** bezárásához a **leltározott fájlok tulajdonságai** párbeszédpanel megnyitásához.  

    -   Adja hozzá a leltárt, és válassza a kívánt fájlokat **OK** bezárásához a **ügyfélbeállítás konfigurálása** párbeszédpanel megnyitásához.  

-   **Fájlok gyűjtése**  

     Ha azt szeretné, fájlokat gyűjthet az ügyfélszámítógépekről, **fájlok** , majd konfigurálja a következőket:  

    > [!NOTE]  
    >  Ha több egyéni ügyfélbeállítás is vonatkozik egy számítógépre, a készlet egyes beállítások visszaadó összevonva fogja tartalmazni.  

    -   Az a **ügyfélbeállítás konfigurálása** párbeszédpanelen válassza ki a **új** ikonra a gyűjtendő fájl hozzáadásához.  

    -   A **Gyűjtött fájlok tulajdonságai** párbeszédpanelen adja meg a következő információkat:  

        -   **Név**: Adja meg a gyűjteni kívánt fájl nevét. Használhatja a * *\**  karaktert bármilyen szöveglánc helyettesítéséhez, és a **?** karaktert bármely egy karakter helyettesítéséhez.  

        -   **Hely**: Válasszon **beállítása** megnyitásához a **elérési útvonal tulajdonságai** párbeszédpanel megnyitásához. Konfigurálhatja a szoftverleltár keresése az ügyfél összes merevlemezén a fájl, amelyet szeretne gyűjteni, egy adott elérési úton keressen (például **C:\Folder**), vagy egy adott változóban keressen (például *% windir %*). A megadott elérési utak almappáiban is kereshet.  

        -   **Titkosított és tömörített fájlok kizárása**: Ha ezt a lehetőséget választja, akkor semmilyen tömörített vagy titkosított fájl nem lesznek összegyűjtve.  

        -   **Fájlgyűjtés leállítása, ha a fájlok összesített mérete meghaladja (KB)**: Adja meg a fájl méretét (kilobájtban) után melyik nem több, a megadott fájlok **neve** lesz begyűjtve.  

          > [!NOTE]  
          >  A helykiszolgáló összegyűjti a gyűjtött fájlok öt legutóbb módosított verzióit, és tárolja őket a  *&lt;ConfigMgr telepítési könyvtára\>*\Inboxes\Sinv.box\Filecol könyvtár. Ha a fájl nem változott az utoljára begyűjtött szoftverleltár óta, akkor a fájlt nem gyűjti be újra.  
          >   
          >  A szoftverleltár nem gyűjt 20 MB-nál nagyobb méretű fájlokhoz.  
          >   
          >  Az érték **maximális mérete (KB) gyűjtött fájlok** a a **ügyfélbeállítás konfigurálása** párbeszédpanel megjeleníti az összes gyűjtött fájl maximális méretét. Ennek a méretnek az elérésekor a gyűjtés abbamarad. A már addig gyűjtött fájlok megmaradnak, és a helykiszolgálóra lesznek küldve.  

          > [!IMPORTANT]
          >  Ha a szoftverleltárt úgy állítja be, hogy az sok nagy fájlt gyűjtsön, az ronthatja a hálózat és a helykiszolgáló teljesítményét.  

        Összegyűjtött fájlok kapcsolatos információkért lásd: [a System Center Configuration Manager szoftverleltár megjelenítése az erőforrás-kezelő használatával](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    -   Válasszon **OK** bezárásához a **gyűjtött fájlok tulajdonságai** párbeszédpanel megnyitásához.  

    -   Adja hozzá az gyűjt, és válassza a kívánt fájlokat **OK** bezárásához a **ügyfélbeállítás konfigurálása** párbeszédpanel megnyitásához.  

-   **Nevek...**  

     A szoftverleltár során a gyártók neveit és a termékek neveit a hely ügyfeleire telepített fájlok fejlécéből lehet kiolvasni. Mivel ezek a fájlok fejléceiben lévő nevek nem mindig szabványosak, amikor az erőforrás-kezelőben megtekinti a szoftverleltárt vagy lekérdezéseket futtat, akkor ugyanannak a gyártónak vagy terméknek különböző nevei jelenhetnek meg. Ha egységessé szeretné megjelenített neveket, válassza a **nevek...** , majd konfigurálja a következőket a **ügyfélbeállítás konfigurálása** párbeszédpanel:  

    -   **Név típusa**: A szoftverleltár mind a gyártókról, mind a termékek adatokat gyűjt. A legördülő listából válassza ki, hogy szeretné-e megjelenítési nevének konfigurálása egy **gyártó** vagy egy **termék**.  

    -   **Megjelenített név**: Adja meg a megjelenített név, amelyet a található nevek helyett a **leltározott nevek** listája. Kiválaszthatja a **új** ikonra kattintva adjon meg egy új megjelenítendő nevet.  

    -   **Leltározott nevek**: Válassza ki a **új** ikonra, melyet a rendszer egy új leltározott név hozzáadásához a szoftverleltár által megadott nevét a **megjelenített név** listája. Több kicserélendő nevet is megadhat.  

##  <a name="software-updates"></a>Szoftverfrissítések  

-   **Szoftverfrissítések engedélyezése az ügyfeleken**  

     Ez a beállítás használatával engedélyezze a Configuration Manager-ügyfelek a szoftverfrissítések. Ha letiltja ezt a beállítást, a Configuration Manager ügyfél meglévő központi telepítési házirendek eltávolítja. Ha újra engedélyezi ezt a beállítást, akkor az ügyfél letölti az aktuális központi telepítésre vonatkozó házirendet.  

    > [!IMPORTANT]  
    >  Ha letiltja ezt a beállítást, a szoftverfrissítések eszközbeállítást támaszkodó NAP- és megfelelőségi beállításokra vonatkozó házirendek nem fog működni.  

-   **Szoftverfrissítések vizsgálatának ütemezése**  

     Ezzel a beállítással adhatja meg, hogy milyen gyakran kezdeményezze az ügyfél a szoftverfrissítések megfelelőségvizsgálatát. A szoftverfrissítések megfelelőségvizsgálata határozza meg a szoftverfrissítések állapotát az ügyfélen (például szükséges vagy telepített). További információ a megfelelőségi vizsgálata: [szoftverfrissítés megfelelőségi vizsgálata](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

     Alapértelmezés szerint használható olyan egyszerű ütemezés, és a megfelelőségi vizsgálat kezdeményezett gyakoriság 7 nap. Egyéni ütemezést is készíthet pontos kezdési dátum és időpont megadásával, kiválaszthatja, hogy az egyezményes világidőt (UTC) vagy a helyi időt használja-e, és egy ismétlődő időtartamot is megadhat a hét egy adott napjára.  

    > [!NOTE]  
    >  Ha 1 napnál rövidebb időközt ad meg, a Configuration Manager rendszer automatikusan az alapértelmezett 1 nap.  

    > [!WARNING]  
    >  A tényleges kezdési időpont az ügyfélszámítógépeken a megadott kezdési időpont egy véletlen, legfeljebb 2 óra értékkel későbbi lesz. Ez megakadályozza, hogy az ügyfélszámítógépek keressék és egyidejűleg csatlakozzanak az aktív szoftverfrissítési pont kiszolgálóján a Windows Server Update Services (WSUS) szolgáltatáshoz.  

-   **Központi telepítés újraértékelésének ütemezése**  

     Ez a beállítás segítségével konfigurálhatja, milyen gyakran a szoftverfrissítések Ügyfélügynöke értékelje szoftverfrissítések telepítési állapotát a Configuration Manager ügyfélszámítógépein. Ha korábban telepített szoftverfrissítések már nem találhatók az ügyfélszámítógépeken, és továbbra is szükséges, hogy újratelepíti.

     A központi telepítés újraértékelésének ütemezését kell igazítani, a vállalati házirend, a szoftverfrissítés megfelelőségének, hogy a felhasználók eltávolíthatnak-távolítsa el a szoftverfrissítések, és így tovább. Ne feledje, hogy minden központi telepítés újraértékelésének gyakorisága egyes hálózati és az ügyfél CPU számítógépes tevékenység eredményez-e. Alapértelmezés szerint használható olyan egyszerű ütemezés, és a központi telepítés újraértékelésének vizsgálati gyakoriság 7 nap lehet kezdeményezni.  

    > [!NOTE]  
    >  Ha 1 napnál rövidebb időközt ad meg, a Configuration Manager rendszer automatikusan az alapértelmezett 1 nap.  

-   **Bármely szoftverfrissítés határidejének elérésekor telepítse központilag az összes olyan szoftverfrissítést, amelynek a határideje egy meghatározott időtartamon belül esik.**  

     Ez a beállítás használható arra, hogy a határidős kötelező központi telepítések telepítsenek minden olyan szoftverfrissítést is, amelyik telepítése egy adott időn belül esedékes. A határidő elérésekor a szükséges szoftverek az üzemelő példány frissítése, az ügyfelek a központi telepítésben lévő szoftverfrissítések telepítési indítható. Ez a beállítás határozza meg, hogy a többi kötelező központi telepítésben lévő szoftverfrissítések telepítése is elkezdődjék, amikor azok telepítési határideje a megadott időn belül esedékes.  

     Ezzel a beállítással gyorsabban elintézhető a kötelező szoftverfrissítések telepítése, esetleg a biztonságot is növeli, csökkentheti az értesítések megjelenítését, és esetleg csökkenti az ügyfélszámítógépek újraindításainak számát is. Alapértelmezés szerint ez a beállítás nem engedélyezett.  

-   **Az az időszak, amelyben az összes olyan központi telepítés is megtörténik, amelynek a határideje ebbe az időszakba esik**  

     Ez a beállítás használható az előző beállítás időkeretének megadására. Időkeretként megadható 1–23 óra, illetve 1–365 nap. Alapértelmezés szerint ez a beállítás 7 nap.  

-   **Engedélyezhető az expressz telepítési fájlok az ügyfelek telepítése**

-   **Az expressz telepítési fájlok tartalom letöltéséhez használt port**

-   **Az Office 365 ügyfél újra a felügyeletének lehetővé tételéhez** használja ezt a beállítást, az Office 365 ügyfélügynök felügyeletének lehetővé tételéhez. Ha beállította a érték **Igen**, lehetővé teszi az Office 365-telepítési beállítások konfigurálása, fájlokat tartalom kézbesítési hálózatokon (tartalomtovábbító) töltse le és telepíti a fájlokat a Configuration Manager alkalmazásként.

##  <a name="user-and-device-affinity"></a>Felhasználó-eszköz kapcsolat  

-   **A felhasználó-eszköz kapcsolat küszöbértéke (perc)**  

     Adja meg percben, mielőtt a Configuration Manager létrehozza a felhasználó-eszköz kapcsolatot.  

-   **A felhasználó-eszköz kapcsolat küszöbértéke (nap)**  

     Adja meg, amelyben a használat alapján létrehozott kapcsolat küszöbértékének mérése napok száma.  

    > [!NOTE]  
    >  Például ha **felhasználó-eszköz kapcsolat küszöbértéke (perc)** megadott **60** perc és **felhasználó-eszköz kapcsolat küszöbértéke (nap)** megadott **5** nap, a felhasználónak kell használnia az eszközt egy 5 napos időszakon át 60 percig felhasználó-eszköz kapcsolat automatikus létrehozásához.  

-   **A felhasználó-eszköz kapcsolat automatikus konfigurálása a felhasználás adataiból**  

     Válasszon **igaz** vagy **Igen** ahhoz, hogy a Configuration Manager automatikusan létrehozza a felhasználó – eszköz kapcsolatokat az összegyűjtött használati információk alapján.  

##  <a name="mobile-devices"></a>Mobileszközök  

-   **Mobileszköz-beléptetési profil**  

     E beállítás konfigurálása előtt a **Mobileszközök beléptetésének engedélyezése** felhasználói beállítást az **Igaz**értékre kell állítani. Ezután kiválaszthatja **profil beállítása** megadása egy regisztrációs profilt, amelyen a tanúsítványsablont a regisztrációs folyamatot, a helyet, amelynek a beléptetési pontról és a beléptetési proxypont és a helyet, amely a regisztráció után kezelni fogja az eszközt során használandó információkat.  

    > [!IMPORTANT]  
    >  Legyen biztos benne, hogy ennek a beállításnak a konfigurálása előtt már konfigurálta a mobileszköz beléptetéséhez való tanúsítványsablont.  

##  <a name="enrollment"></a>Beléptetés  

-   **Mobileszköz-beléptetési profil**  

     E beállítás konfigurálása előtt a **Mobileszközök és Mac számítógépek beléptetésének engedélyezése a felhasználóknak** felhasználóbeléptető beállítást az **Igen**értékre kell állítani. Ezután kiválaszthatja **profil beállítása** megadása egy regisztrációs profilt, amelyen a tanúsítványsablont a regisztrációs folyamatot, a helyet, amelynek a beléptetési pontról és a beléptetési proxypont és a helyet, amely a regisztráció után kezelni fogja az eszközt során használandó információkat.  

    > [!IMPORTANT]  
    >  Legyen biztos benne, hogy ennek a beállításnak a konfigurálása előtt már konfigurálta a mobileszköz beléptetéséhez való tanúsítványsablont, illetve a Mac ügyféltanúsítványát.  

## <a name="user-and-device-affinity"></a>Felhasználó-eszköz kapcsolat  

-   **A felhasználók definiálhassák elsődleges eszközeiket**  

     Adja meg, hogy a felhasználók jogosultak-e a saját elsődleges eszközüket lévő azonosításához a **Eszközeim** az alkalmazáskatalógus fülre.  

