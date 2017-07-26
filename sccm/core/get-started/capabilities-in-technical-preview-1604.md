---
title: "A Technical Preview 1604 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1604 verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 684a5559-9e6e-469b-86ae-e768e9f0c9ac
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 26b0d8ea7b3e841c48945df55f8860394a98a29f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1604-for-system-center-configuration-manager"></a>A Technical Preview 1604 rendszer képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat a Technical Preview a System Center Configuration Manager, a verzió 1604 elérhető. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti.      A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.  

 Új funkciókat próbálhatja ki ebben a következők:  

##  <a name="BKMK_WindowsVPP"></a>A vállalati Windows áruházból mennyiségi programban vásárolt alkalmazások kezelése  
 A [vállalati Windows áruház](https://www.microsoft.com/en-us/business-store) hol található, és alkalmazásokat vásárolhat a szervezete számára egyenként vagy nagyobb mennyiségben. Ha összekapcsolja az áruházat a Configuration Manager, kezelheti mennyiségi programban vásárolt alkalmazásokat a Configuration Manager konzolról, például:  

-   Szinkronizálhatja a megvásárolt alkalmazások listáját a Configuration Managerrel  

-   A szinkronizált alkalmazások megjelennek-e a Configuration Manager konzolon, és telepítheti őket a többi alkalmazáshoz hasonlóan  

-   Követheti nyomon, hogy hány licencet, és hány van használatban a Configuration Manager konzol  

### <a name="try-it-out"></a>Próbálja ki!  

##### <a name="scenario-1-set-up-windows-store-for-business-synchronization"></a>1. forgatókönyv: Üzleti szinkronizálási Windows áruház beállítása  

1.  Az Azure Active Directoryban regisztrálja a Configuration Manager "Web Application and/or Web API" felügyeleti eszközként. Ekkor kap egy ügyfél-Azonosítót, amely később szüksége lesz.  

    1.  Az a **Active Directory** munkaterület [https://manage.windowsazure.com](https://manage.windowsazure.com), válassza ki az Azure Active Directoryban, majd kattintson a **alkalmazások** > **Hozzáadás**.  

    2.  Kattintson a **a szerveztem által fejlesztett alkalmazás hozzáadása**.  

    3.  Adjon meg egy nevet az alkalmazásnak, válassza a **webes alkalmazás** és/vagy **Web API**, majd kattintson a Tovább nyílra.  

    4.  Adja meg az URL-CÍMÉRE mind a **bejelentkezési URL-cím** és **App ID URI**.  Az URL bármi lehet, és nem kell valódi címre mutatnia. Megadhat például **https://&lt;tartomanynev\>/sccm**.  

    5.  Fejezze be a varázslót.  

2.  Az Azure Active Directoryban hozzon létre egy ügyfélkulcsot a regisztrált felügyeleti eszközhöz.  

    1.  Jelölje ki az imént létrehozott alkalmazást, majd kattintson **konfigurálása**.  

    2.  A **kulcsok**, válasszon egy időtartamot a listából, és kattintson a **mentése**.  Ezzel létrehoz egy új ügyfélkulcsot.  Ne lépjen ki erről az oldalról amíg sikeresen fel nem vállalati a Configuration Manager előkészítve a Windows áruházban.  

3.  A vállalati Windows áruházban konfigurálja a Configuration Manager áruházi kezelőeszközként.  

    1.  Nyissa meg [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools) és jelentkezzen be a kérésre.  

    2.  Ha szükséges, fogadja el a használati feltételeket.  

    3.  A **kezelőeszközök**, kattintson a **felügyeleti eszköz hozzáadása**.  

    4.  A **keressen rá név szerint az eszköz**, írja be a korábban létrehozott az aad-ben az alkalmazás nevét, majd kattintson a **Hozzáadás**.  

    5.  Kattintson a **aktiválás** imént importált alkalmazás neve mellett.  

    6.  Az a **offline licencelt alkalmazások** varázsló, kattintson a **Igen** Ha azt szeretné, hogy az offline licencelt alkalmazások vásárlását.  

4.  Vásároljon legalább egy alkalmazást a vállalati Windows áruházban.  

5.  A a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki **Felhőszolgáltatások**, majd kattintson a **vállalati Windows áruház**.  

6.  A a **Home** lap a **létrehozása** csoportjában kattintson a **hozzáadása a Windows áruház-fiók üzleti**.  

7.  A bérlő azonosítója, az ügyfél-azonosító és az ügyfél kulcs hozzáadása az Azure Active Directoryból, majd fejezze be a varázslót.  

8.  Ha elkészült, látni fogja a beállított fiók megjelenik a **Windows Áruházbeli fiókok üzleti** lista a Configuration Manager konzolon.  

##### <a name="scenario-2-create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-offline-licensed-app"></a>2. forgatókönyv: Létrehozhat és telepíthet a Configuration Manager-üzleti offline licencelt alkalmazások Windows áruházbeli alkalmazás  

1.  Az a **szoftverkönyvtár** a Configuration Manager konzol munkaterületén bontsa ki a **Alkalmazáskezelés**, majd kattintson a **Áruházbeli alkalmazások Licencadatai**.  

2.  A **Beszerezve Windows áruház-alkalmazások** lista mutatja azokat az áruházból szinkronizált alkalmazások listája. Válassza ki a kívánt alkalmazást, telepíti, ezt követően a a **Home** lap a **létrehozása** csoportjában kattintson a **alkalmazás létrehozása**.  

3.  Configuration Manager-alkalmazás jön létre, amely tartalmazza a Windows Áruházbeli alkalmazás. Ezután telepítheti és figyelheti az alkalmazás, mint bármely más Configuration Manager-alkalmazás.  

##  <a name="BKMK_PFW"></a>A Microsoft Passport for Work felügyeletének fejlesztései  
 A Passport for Work-házirendeket a tartományhoz csatlakoztatott Windows 10-eszközökre a Configuration Manager-ügyfél által felügyelt most már telepítheti.  

##  <a name="bkmk_switchsup"></a>Az ügyfelek új szoftverfrissítési pontot váltani beállítás  
 A Technical Preview 1604 engedélyezheti a Configuration Manager-ügyfelek új szoftverfrissítési pontot váltani, ha az aktív szoftverfrissítési ponttal probléma vonatkozó beállítást. Ezt a beállítást, az elsődleges helyen több szoftverfrissítési pont rendelkezésre kell rendelkeznie. Engedélyezze ezt a kapcsolót egy eszközgyűjteményt, és egyszer engedélyezve van, a gyűjteményben lévő ügyfelek fog keresni egy másik szoftverfrissítési pontot a következő vizsgálat alkalmával, amikor az ügyfél nem tud csatlakozni az aktív szoftverfrissítési pont. Attól függően, hogy a WSUS konfigurációs beállítások (frissítési besorolás, termékek, stb.) a kapcsolót, hogy egy új szoftverfrissítési pontot hoz létre további hálózati forgalmat. Ennek megfelelően csak szükséges esetben használja ezt a beállítást.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>A szoftverfrissítési pont váltására szolgáló beállítás engedélyezése  

1.  A Configuration Manager-konzolon kattintson az **Eszközök és megfelelőség > Áttekintés Eszközgyűjtemények** elemre.  

2.  A **Kezdőlap** **Gyűjtemény** csoportjában kattintson az **Ügyfélértesítés**elemre, majd a **Váltás a következő szoftverfrissítési pontra**lehetőségre.  

> [!NOTE]  
>  Ez a beállítás csak érhető el több szoftverfrissítési pontot rendelkező helyeken.  

##  <a name="bkmk_peercache"></a>Ügyfélbeállítások kezelése az Ügyfélgyorsítótár beállításait, valamint az ügyfél társ-gyorsítótárazás  
 Technical preview 1604 tartalmazza az két új eszközoldali ügyfélbeállítás, amely az ügyfél gyorsítótárának használatát érintik. Mindkét külön-külön is használható, de ügyfélbeállítások azonos tulajdonságlapjának vannak konfigurálva, és segítséget nyújtanak a tartalom a távoli ügyfelek központi telepítésének kezelése össze.  

-   Első az **társ-gyorsítótárazási ügyfél**, az ügyfelek által közvetlenül a helyi gyorsítótárból más ügyfelekkel tartalmat osszanak a beépített Configuration Manager megoldással. Társ-gyorsítótárazási ügyfelek számára tartalmak megosztása akkor az adott csoporthoz tagjának kell lennie. Társ-gyorsítótárazás nem helyettesíti az egyéb megoldások, például BracnchCache, de ehelyett működik mellé további lehetőségek bővítése hagyományos tartalomterjesztési megoldások, például a terjesztési pontok.  

     Miután ügyfélbeállítások, amelyek lehetővé teszik a társ-gyorsítótárazás egy gyűjteményhez, tagjai működhet társ tartalomforrásként más a határcsoportban lévő ügyfelek számára.  Gyorsítótárazott tartalom forrás nyújt az elérhető tartalmak listáját társ működik az ügyfél a felügyeleti pontjára. Majd amikor az adott határcsoport a következő ügyfél ezt a tartalmat, a társ-gyorsítótárazási forrástól tartományregisztráció együtt az összes olyan terjesztési pontok, amelyek úgy vannak konfigurálva, hogy gyors lehetséges tartalomforrásként. Az ügyfél véletlenszerűen tartalomforrás tartalomforrás a kombinált készletből választ. Az ügyfelek csak arra törekednek lassú, amikor a gyors terjesztési pontok konfigurált terjesztési pont tartalmát, vagy társközi gyorsítótár források szerepelnek a határcsoporthoz.  

-   A második beállítás lehetővé teszi **kezelheti a gyorsítótár méretének** az ügyfeleken. Beállíthatja a gyorsítótár maximális méretét megabájtban és a maximális méretét az ügyfél lemezterületének százalékában.  Az ügyfél érvénybe lépteti a beállításhoz tartozó éri el hamarabb.  

Megismerheti az ügyfél társ-gyorsítótárazás használatát, megtekintheti a **Ügyféladatforrások** irányítópult. Nyissa meg a a konzol **figyelés > ügyfélállapot > Ügyféladatforrások**. Itt adhatja meg azt a az irányítópultra alkalmazandó időszakot. Ezt követően a kijelzőn kiválaszthatja a határcsoportot vagy csomagot, amelynek meg szeretné tekinteni az adatokat. Ha az adatok megtekintésekor is az egérrel a felületen házirend adatforrásokat, illetve a különböző tartalom kapcsolatos további részletek megtekintéséhez.  

 Is használhatja, egy új jelentés, **Ügyféladatforrások – összefoglalás**, az egyes határcsoportokban ügyféladatforrások egy összegzése megtekintéséhez.   
**Társ-gyorsítótárazás használatára vonatkozó követelményeket:**  

-   Konfigurálnia kell a webhelyet a egy **hálózatelérési fiók** , amely rendelkezik **teljes hozzáférés** a gyorsítótár mappája az egyes ügyfelekre. Alapértelmezés szerint ez a **%windir%\ccmcache**  

-   Az ügyfelek csak akkor továbbíthatnak tartalmakat a társgyorsítótár használatával, ha ugyanahhoz a határcsoporthoz tagjai.  

#### <a name="to-configure-client-peer-cache-client-settings"></a>Ügyfél társgyorsítótár beállításainak konfigurálása  

1.  Mindkét beállítás konfigurálva van az ügyfélbeállítások ugyanazon az oldalon. Nyissa meg a Configuration Manager konzol **Adminisztráció > ügyfélbeállítások**, és ezután nyissa meg az eszköz ügyfélbeállításait objektum szeretne használni. Módosíthatja az alapértelmezett ügyfélbeállítások objektum is.  

2.  Válassza ki a listáról a rendelkezésre álló beállítások, **Ügyfélgyorsítótár beállításait**.  

3.  Kezelheti a gyorsítótár méretét, állítsa be **ügyfélgyorsítótár méretének beállítása** egyenlő **Igen**. Ezután beállíthatja a gyorsítótár maximális méretének mindkét mérete (MB) és az ügyfél lemezterületének százalékában.  

4.  Ahhoz, hogy az ügyfelek számára, hogy részt vesz a társ-gyorsítótárazási ügyfél, be **teljes körű operációsrendszer tartalommegosztás engedélyezése a Configuration Manager-ügyfél** egyenlő **Igen**. Ezután konfigurálhatja a portokat, amelyeket az ügyfelek használják, ha azok HTTP vagy HTTPS PROTOKOLLT fogja.  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja a következő feladatok végezhetők, majd ez a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel járt:  

1.  Adjon meg egy új ügyfél-gyorsítótár mérete-ügyfél beállításainak módosítására, és erősítse meg ezt a beállítást, az ügyfélen.  

2.  Ügyfél-beállítások segítségével konfigurálhatja a társ-gyorsítótárazás használatára több ügyfél  

3.  Telepítse központilag a tartalmakat az ügyfelek számára, hogy vagy a legtöbb ügyfelek kapják meg a tartalmat egy másik ügyfél társgyorsítótár révén.  A tartalom forrásához használt új irányítópult megtekintésével ellenőrizheti.  

    > [!NOTE]  
    >  A technical Preview kiadással és egyetlen terjesztési ponttal rendelkező a feladat végrehajtásához a terjesztési pont konfigurálása ahhoz lassú az összes ügyfél hálózati helye számára. Ezt követően terjessze a tartalmat egyetlen ügyfélre.  Követően, hogy az ügyfél megkapta a tartalmat, terjesztheti a tartalmat, amely kell helyi társakat kell találniuk tartalomforrásként előtt az ügyfél helyéről lassúnak minősülő terjesztési pontot használjon további ügyfelek.  

##  <a name="bkmk_passport"></a>A Passport for Work kulcstároló-Szolgáltatóra támogatása  
 A System Center Configuration Manager lehetővé teszi az integrációt a Microsoft Passport for Work nevű alternatív bejelentkezési módszerrel, amely Active Directoryt vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya van.  
A Passport lehetővé teszi jelszó helyett felhasználói kézmozdulatok használatát a bejelentkezéshez használatát. A felhasználói hitelesítési mód lehet egy egyszerű PIN-kód, biometrikus hitelesítés, mint például a Windows Hello vagy egy külső eszköz, például egy ujjlenyomat-olvasó.  

-   A Configuration Manager segítségével szabályozhatja, hogy mely hitelesítési módok a felhasználók és a bejelentkezés, és a PIN-kód bonyolult konfigurálása nem használható.  

-   Hitelesítési tanúsítványokat tárolhatja a Passport for Work kulcstároló-szolgáltatójában.  

Amikor egy felhasználó Passport PIN-kódot hoz létre, a Windows a Configuration Manager által figyelt a értesítést küld.  Ez lehetővé teszi a Configuration Manager gyorsan értesülhet arról hogy mely felhasználók hozott létre Passport PIN-kódot. A Configuration Manager tudja majd is új tanúsítványokat kiadni azoknak a felhasználóknak Passport használata, mint a kulcstároló-szolgáltató egy.  

##  <a name="bkmk_onpremdha"></a>Helyszíni Készülékállapot-igazolás  
 Az Eszközállapot-igazolás Windows 10-eszközök most már beállítható úgy, hogy a helyszíni infrastruktúrát használja kommunikációra.  A rendszergazdák adhat meg, hogy jelentéskészítés a felhő használatával történik vagy a helyszíni erőforrások.  Ha **helyszíni** az egészségügyi állapotigazolási jelentéshez, be van jelölve, akkor egy URI-t a szolgáltatás adható meg. Ez lehetővé teszi az ügyfélszámítógépeken az internet-hozzáférés nélküli használatát, engedélyezését és az Eszközállapot-igazolás eszközöket kezelheti.  

#### <a name="enable-health-attestation-for-on-premises-devices"></a>Az Eszközállapot-igazolás a helyszíni eszközök engedélyezése  

1.  A Configuration Manager-konzolon lépjen az **Adminisztráció** > **Áttekintés** > **Ügyfélbeállítások**területre, majd a **Helyszíni állapotigazolási szolgáltatás használata** beállításnál válassza az **Igen**értéket.  

2.  Adja meg a **Helyszíni állapotigazolási szolgáltatás URL-címét**, majd kattintson az **OK**gombra.  

A kipróbáláshoz konfigurálja a helyszíni Állapotigazolási szolgáltatás ügyfélügynök-beállításokkal.  

##  <a name="BKMK_Smart"></a>SmartLock-beállítás Android-eszközök  
 Egy új beállítás **engedélyezése a Smart LOCK és más megbízhatósági ügynökök** hozzá lett adva a **Android és Samsung KNOX** konfigurációelemet, amely lehetővé teszi, hogy a kompatibilis Android-eszközökön a Smart LOCK funkció szabályozza. Ez a „megbízhatósági ügynökök” néven is ismert telefonos funkció lehetővé teszi az eszköz zárolási képernyője jelszavának letiltását vagy megkerülését, ha az eszköz megbízható helyen van, például ha egy adott Bluetooth-eszközhöz van csatlakoztatva, vagy egy bizonyos NFC-címkéhez van közel. Ez a beállítás segítségével megakadályozhatja a végfelhasználók számára a Smart LOCK konfigurálását.  

