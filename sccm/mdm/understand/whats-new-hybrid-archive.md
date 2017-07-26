---
title: "Mi az az új hibrid MDM az archív |} Microsoft Docs"
description: "Archív múltbeli mobileszköz funkciók hibrid telepítések esetén a System Center Configuration Manager és az Intune használatával érhető el."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c27b161-9eb7-4cdd-b469-d8eb27e71aea
author: Mtillman
ms.author: mtillman
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 623a30eddebcae196ff345ef5debc8183ecd6ae6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="past-hybrid-features-with-system-center-configuration-manager-and-microsoft-intune"></a>Elmúlt hibrid szolgáltatások a System Center Configuration Manager és a Microsoft Intune

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a cikk részletesen a múltbeli mobileszköz-felügyelet (MDM) szolgáltatásához hibrid telepítések esetén a System Center Configuration Manager és a Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>A Configuration Manager verzióival való kompatibilitás érdekében  

 Ez a cikk minden szakasz hibrid funkciókról a 3 különböző kategóriák. Az alábbi útmutató segítségével meghatározhatja az egyes kategóriák funkciók kompatibilisek-e a Configuration Manager különböző verziói:  

|A szolgáltatás kategóriák|
|-|  
|**Új Microsoft Intune-ban** – általában a kategóriához tartozó összes funkcióját kell működnie, beleértve a System Center 2012 R2 Configuration Manager kiadások, mivel ezek a szolgáltatások csak megkövetelése az Intune-ba, és nincs szükség további funkciókat a Configuration Manager az összes Configuration Manager kiadásainak.<br /><br /> **A Configuration Manager Technical Preview új** -a megadott a Technical Preview kiadással csak munkahelyi kategóriában felsorolt összes funkcióját. Próbálja ki ezeket a funkciókat, telepítenie kell a Technical Preview verzió van megadva a a szolgáltatás leírása. További információkért lásd: [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md).<br /><br /> **A Configuration Manager (aktuális ág) új** – például 1511-es vagy az 1602-es verziója a kategória csak együttműködnek a megadott Configuration Manager verziója (aktuális ág), a felsorolt összes funkcióját. A hibrid telepítéshez használata a Configuration Manager egy régebbi verziója, frissítenie kell a Configuration Manager (aktuális ág) verzió van megadva a szolgáltatás leírása. További információkért lásd: [frissítése a System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|  

## <a name="new-hybrid-features-in-october-2016"></a>Új hibrid funkciókról a 2016. október

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

A következő Intune-funkciók október 2016 rendszerben bevezetett hibrid telepítések működjön.

- **Feltételes hozzáférés a mobilalkalmazás-kezelés**

  Exchange online-hoz való hozzáférés korlátozhatja, hogy a hozzáférés csak az Intune mobilalkalmazás-kezelési házirendekkel például az Outlook támogató alkalmazások származik. [Ezen új szolgáltatás](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) párokat tökéletesen Intune mobilalkalmazás-kezelés (MAM) házirendek, akkor képes blokkolni a hozzáférést a beépített e-mail-ügyfélprogramokat vagy más alkalmazásokat, amelyek az Intune MAM-szabályzatokkal nincsenek konfigurálva. Ez biztosítja, hogy a felhasználók elérik-e a szervezet adatait a alkalmazásoknál, amelyeket az Intune MAM is védhetők. Ismerkedés az Intune mobilalkalmazás-kezelés az Azure-portálon. Keresse meg az új feltételes hozzáférés szakaszban a "Beállítások" paneljén.

-    **Androidhoz készült Intune Alkalmazásburkoló eszközzel**

  Az alkalmazások Intune mobilalkalmazás-kezelési (MAM) házirendek használata az Intune App Wrapping Tool használatával engedélyezheti.

- **Az Intune-nal az Android Samsung KNOX Standard kompatibilitási**

  Egyes modellek a Samsung Galaxy Ace telefon, Samsung KNOX Standard eszközökhöz az Intune által nem kezelhető. Ha ezek az eszközök Intune-nal regisztrálja, azokat helyette kezelik, Android-eszközök.

  A modell számok hatással a következők:

  - SM-G313HU
  -    SM-G313HY
  -    SM-G313M
  -    SM-G313MY
  -    SM-G313U

  Ön és a végfelhasználók semmilyen további műveletet kell tenni. További információkért látogasson el a Samsung KNOX-webhelyet.

### <a name="new-in-configuration-manager-technical-preview-1610"></a>Új Configuration Manager Technical Preview 1610

A következő új hibrid funkciókról a Configuration Manager Technical Preview 1610 október 2016 vezettek be.

- **Házirend szinkronizálást kér a felügyeleti konzol**

  A Configuration Manager-konzolon kell a vállalati portál alkalmazás maga az eszköz a szinkronizálási kérelem helyett egy regisztrált mobileszközön házirend szinkronizálási is kérhet. Egy új művelet hívása **szinkronizálási kérés küldése** a távoli eszközök műveletei menü, amely akkor jelenik meg a menüszalagon mobileszköz eszközök kiválasztásakor.

- **A Windows Defender konfigurációs beállításai**

  Most már konfigurálhatja a Windows Defender-ügyfél beállításainak a Intune-ban regisztrált Windows 10 számítógépeknél konfigurációs elemek a Configuration Manager konzolon. Egy új beállítás csoport nevű **Windows Defender** a konfigurációs elem varázslóban. Vegye figyelembe, hogy ez támogatott csak Windows 10-es verziója 1511-es és újabb verziók.


### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)

Nincs új hibrid funkciókról a Configuration Manager (aktuális ág) 2016 augusztusában jelentek meg.

## <a name="new-hybrid-features-in-september-2016"></a>2016 szeptemberétől új hibrid funkciókról

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

2016 szeptemberétől bevezetett következő Intune szolgáltatásai hibrid telepítések működnek.

- **Az Androidhoz a vállalati portál "értesítések" bevezetése**

  Egy új értesítések ikonjában bővült a vállalati portál Android-verziójában a kezdőlapon. Az értesítések lapon, amely bemutatja a végfelhasználók számára az összes, figyelmet igénylő elemet a vállalati portál alkalmazás, például az eszköz nem felel meg, a regisztráció frissítésének és aktiválásának erre az ikonra koppintva fér hozzá. Az IOS rendszerű vállalati portál alkalmazás már van ennek értesítések tapasztalhat. Az új értesítések oldal azt jelenti, hogy a felhasználó nem jelenik a vállalati hozzáférés beállítása lap minden alkalommal, amikor azok vagy folytatásakor a vállalati portálon, mindaddig, amíg az eszköz már regisztrálva van. Ha létrehozta a saját végfelhasználói útmutatókat, érdemes frissítse a dokumentációt a változásnak. Keresés a frissített képernyőképek [Itt](https://aka.ms/androidcpupdate).

- **Az iOS vállalati portál alkalmazás támogatására vonatkozó módosítások**

  Minden felhasználójának az alkalmazás a Microsoft Intune vállalati portál alkalmazás iOS-hez szükséges legújabb verzióját használja. Új felhasználók csak a legújabb verzió letöltéséhez, és a jelenlegi felhasználóknak frissíteniük kell erre van szükség. A legújabb iOS 8.0-s vagy újabb verzió, igényel, régebbi iOS-verziót futtató eszközökön nem a vállalati portál vagy regisztrálni, amíg nem frissítik az eszközt iOS 8.0-s vagy újabb verzió, és frissítse a vállalati portál alkalmazás legújabb verziójára. IOS 8.0-s verziójánál régebbi rendszerű regisztrált eszközök kezelésének és az Intune felügyeleti konzolján szereplő folytatja.

- **Windows Phone 8.1 vállalati portál alkalmazás hozzá visszajelzésküldő gombot**

  A Windows Phone 8.1 vállalati portál alkalmazás lehetővé teszi, hogy a végfelhasználók számára, hogy az alkalmazás visszajelzést küld egy új "visszajelzés küldése" gomb használatával. A gomb található, a felhasználók közvetlenül a vállalati portál alkalmazást képernyő aljára "három pont" menüben koppintson, és koppintson a **visszajelzés küldése**. A gyűjtött, anonimizált visszajelzéseket a Microsoft vállalati portál alkalmazás biztosítása a felhasználók.

### <a name="new-in-configuration-manager-technical-preview-1609"></a>Új Configuration Manager Technical Preview 1609

A következő új hibrid funkciókról a Configuration Manager Technical Preview 1609 2016 szeptemberétől vezettek be.

- **További beállításokat és a konfigurációs elem beállítások fejlett élményt**

  Új Android, iOS és Windows-beállítások váltak elérhetővé, és csak a támogatott platformok lapon platformra vonatkozó beállítások jelennek meg a varázslóban. További információ: [új megfelelőségi beállítások a konfigurációs elemek TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#new-compliance-settings-for-configuration-items).

- **További beállítások megadása a DEP-profilok**

  Touch ApplePay és nagyítás DEP profilokat az iOS-eszközök a konfigurálható beállítások lettek hozzáadva.

- **A vállalati Windows áruházban található alkalmazásokra fizetős**

  Ezután adja hozzá a vállalati Windows áruház alkalmazások mind a fizetős, mind a szabad és telepíteni a felhasználók számára a szervezetében. További információ: [TP 1609 a vállalati Windows áruház fejlesztései](/sccm/core/get-started/capabilities-in-technical-preview-1609#enhancements-to-windows-store-for-business-integration-with-configuration-manager).

- **Natív kapcsolattípusokat Windows 10 VPN-profilokhoz**

  Mostantól létrehozhat Windows 10 VPN-profilok mobileszköz-kezelési Microsoft Automatic, IKEv2 és PPTP kapcsolattípusok közül a Configuration Manager konzolon OMA-URI használata nélkül.

- **Intune megfelelőségi diagramok**

  Általános eszköz gyors áttekintést kaphat megfelelőség és a felső okokból meg nem felelés új diagramok használatával a figyelés munkaterületen. További információkért lásd: [Intune megfelelőségi diagramok TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#intune-compliance-charts).

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)

2016 szeptemberétől bevezetni a következő új szolgáltatás érhető el hibrid telepítések esetén a Microsoft Intune és a Configuration Manager verziója 1606 (aktuális ág).

- **iOS 10-támogatás**

  Ha a profilok vagy a konfigurációs elemek céloz meg minden iOS platform, ezek is leküldött IOS 10. Egy frissítést adunk ki, amely lehetővé teszi, hogy a cél-profilok a Configuration Manager verziója 1606 és egyéni iOS-platformokon, beleértve az iOS 10 konfigurációs elemeket is már megjelent. És a Configuration Manager felügyeleti konzolt is telepíti a frissítést **felügyeleti > Áttekintés > Felhőszolgáltatások > frissítések és karbantartás**. További információt a frissítés található [http://support.microsoft.com/kb/3192616](http://support.microsoft.com/kb/3192616).

## <a name="new-hybrid-features-in-august-2016"></a>2016 augusztusától az új hibrid funkciókról

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

A következő Intune-funkciók 2016 augusztusában bevezetett hibrid telepítések működjön.

- **A vállalati portál alkalmazás Android-7 támogatás**

  Az Androidhoz készült Intune vállalati portál alkalmazás "day 0" támogatást nyújt a azonnali Android 7.0 operációs rendszerhez mobileszközökön.

- **Google eltávolításának PIN-kód távoli alaphelyzetbe állításának Android 7.0 rendszerű eszközökön**

  A Google megszünteti a rendszergazdák és a végfelhasználók távolról alaphelyzetbe állítja a jelszót, az Android 7.0 rendszerű eszközök képességét. Korábban a rendszergazdák távolról új felhasználó PIN-kódot, és a végfelhasználók állíthattak a vállalati portál webhelyről.

- **Engedélyezett és letiltott alkalmazások házirendje Samsung KNOX Standard eszközökhöz**

  Konfigurálhat egy egyéni házirend Samsung KNOX Standard eszközökön használható, amely lehetővé teszi, hogy hozzon létre egyet a következő:

  - Az eszközön nem futtatható alkalmazások listája. Akkor is, ha telepítve, a tiltólistán szereplő alkalmazások nem lehet aktiválni, az eszközön.
  - Amelyeket a felhasználók az eszköz a Google Play áruházból telepíthető alkalmazások listáját. Más alkalmazás nem telepíthető az áruházból.

  Ezek a beállítások csak rendszert futtató Samsung KNOX Standard eszközökön használható. További információkért lásd: [egyéni házirendekkel engedélyezéséhez és letiltásához a Samsung KNOX Standard eszközökön használható alkalmazások](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).

- **Visszajelzési hivatkozás a vállalati portálról a Microsoftnak**

   A vállalati portál lehetővé teszi, hogy a visszajelzés küldése a Microsoftnak a webhelyen szerzett tapasztalataikról az oldal alján egy új "Visszajelzés" hivatkozásra koppintva. A gyűjtött, anonimizált visszajelzéseket a Microsoft felhasználók a vállalati portál nyújtotta felhasználói élmény javítása.

- **Minimális iOS Managed Browser-verziójához 8.0**

  Az iOS rendszerhez készült Microsoft Intune Managed Browser alkalmazás iOS 8.0-s vagy újabb rendszerű eszközök támogatásához frissítve lett. IOS 7.1-es eszközök továbbra is használhatja a meglévő Managed Browser alkalmazást, miközben ösztönözzék a felhasználókat, hogy az iOS 8.0-s vagy újabb hozzáférés frissítése és a Managed Browser új funkcióinak teljes körű kihasználása.

### <a name="new-in-configuration-manager-technical-preview"></a>A Configuration Manager Technical Preview újdonságai

Nincs új hibrid funkciókról a Configuration Manager Technical Preview 2016 augusztusában vezettek be.

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)

Nincs új hibrid funkciókról a Configuration Manager (aktuális ág) 2016 augusztusában jelentek meg.

## <a name="new-hybrid-features-in-july-2016"></a>Új hibrid funkciókról a 2016. július

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

A következő Intune-funkciók július 2016 rendszerben bevezetett hibrid telepítések működjön.

- **Intune-hoz készült Xamarin SDK érhető el**

  Az Intune App SDK Xamarin összetevőjével engedélyezése az Intune mobilalkalmazás-felügyeleti funkciókat a mobil iOS és Android-alkalmazások Xamarinnal készült teszi lehetővé. Megtalálhatja az összetevőt a [Xamarin áruházban](https://components.xamarin.com/view/Microsoft.Intune.MAM) vagy a [Microsoft Intune Github-oldalon](https://github.com/msintuneappsdk).

- **Továbbfejlesztett végfelhasználói élmény Windows-eszközök regisztrálásakor**

  Használatakor a feltételes hozzáférés, regisztráció lépései a Windows 8.1, Windows 10 asztali verzió és Windows 10 Mobile rendelkeznek a vállalati portál webhelyen találhatók. Felhasználók jelenik meg külön **eszközregisztráció** és **munkahelyi csatlakoztatás** lépéseket, így megkönnyíti számukra az eszköz állapotának megállapítását, és a folyamat befejezéséhez, ha a munkahelyi csatlakoztatás esetleges Meghiúsulása után az ügyfeleken. A különálló lépések várhatóan is a hibaelhárítási folyamat leegyszerűsítése érdekében a rendszergazdák számára. Korábban amikor a végfelhasználók próbált meg regisztrálni, és a regisztráció sikeres volt munkahelyi csatlakoztatás kivételével, a regisztrált eszköz nem jelent meg a listán szereplő eszközök, felhasználók által azonosítható, ami.

 - **Teljes törlést Windows 10-eszközök most már hozzáférhető**

    Windows 10 rendszerű számítógépeket és a hordozható számítógépek mobileszközként is törlendő visszaállítani az eszközt annak gyári állapotába. További információkért lásd: [hogyan védi meg a regisztrált eszközök távoli Törlés](/sccm/mdm/deploy-use/wipe-lock-reset).

- **Változások Készülékregisztráció-kezelői fiókokban az IOS rendszerű vállalati portál alkalmazás**

  Jobb teljesítmény és méretezés érdekében az Intune már nem jelenik meg az összes Készülékregisztráció-kezelő (DEM) eszközök az IOS rendszerhez készült vállalati portál alkalmazás saját eszközök panelén. Csak az alkalmazást futtató helyi eszköz fog megjelenni, és csak akkor, ha azt korábban már regisztrálták a vállalati portál alkalmazást.

  A DEM-felhasználó elvégezheti a kapcsolódó műveleteket a helyi eszközön, de a további regisztrált eszközök távoli felügyeleti csak az Intune felügyeleti konzolon hajtható végre. Emellett Intune-ból kivezettük való DEM-fiókoknak az Apple Device Enrollment programmal és az Apple Configurator eszközzel használatát. Ezek a regisztrálási módszerek már támogatják a megosztott iOS-eszközök felhasználó nélküli regisztrálását.

  DEM-fiókokat csak akkor használható, ha nem érhető el megosztott eszközök felhasználó nélküli regisztrálását. További információkért lásd: [vállalati-eszközök regisztrálása az Eszközregisztráció-kezelővel a Microsoft Intune-ban](../deploy-use/enroll-devices-with-device-enrollment-manager.md).

- **Az Androidos vállalati portál alkalmazás módosításai**

  Ha Android-végfelhasználók egy hibaüzenet, amely szerint az eszköz hiányzik egy szükséges tanúsítvány, lépéseket lekérése a hiányzó tanúsítvány telepítését egy "Útmutató a probléma megoldásához" gombra koppintva. Ha a felhasználók hajtsa végre a lépéseket, de lásd: egy "hiányzó tanúsítvány" hibaüzenetet jelenít meg, akkor a rendszer felkéri lépjen kapcsolatba a rendszergazdával, és adja meg a hivatkozást, amely tartalmazza a lépéseket, amelyek a rendszergazdák javítsa ki a tanúsítvánnyal kapcsolatos problémát.

- **Közvetlenül telepített alkalmazások telepítésére regisztrált Android-eszközökre korlátozhatja.**

  Android-eszközökhöz már nem lehet telepíteni a vállalati portál webhelyen keresztül alkalmazásokat, ha az eszközök nincsenek regisztrálva az Intune-ban az Intune vállalati portál alkalmazás használatával Android rendszeren.


### <a name="new-in-configuration-manager-technical-preview"></a>A Configuration Manager Technical Preview újdonságai

Nincs új hibrid funkciókról a Configuration Manager Technical Preview 2016. július vezettek be.

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)

Az alábbi, korábban a Configuration Manager Technical Preview kiadásokban számára elérhető szolgáltatása hibrid telepítések esetén az Intune és a Configuration Manager (aktuális ág) 1606 verziója.

* Keresése, kezelése és terjesztése a Windows áruház az üzletági alkalmazások Windows 10 rendszerű eszközökhöz, a Configuration Manager konzolról ([1604](#new-in-1604-technical-preview))
*     SmartLock-beállítás Android-eszközök ([1604](#new-in-1604-technical-preview))
*    Alkalmazás által indított VPN Windows 10-eszközök ([1605](#new-in-1605-technical-preview))
*    A távoli eszközök műveletei új élmény ([1605](#new-in-1605-technical-preview))
*    Windows áruház-alkalmazások ([1605](#new-in-1605-technical-preview))
*    Általános fejlesztések a mennyiségi programban vásárolt alkalmazások ([1605](#new-in-1605-technical-preview))
*    A Windows információvédelem (folyamatban) ([1605](#new-in-1605-technical-preview))
*    Vállalati tulajdonban lévő eszközök IMEI- vagy iOS sorozatszámmal előzetes bejelentése ([1605](#new-in-1605-technical-preview))
*    Automatikusan eszközök kategorizálása gyűjteményekbe ([1606](#new-in-1606-technical-preview))

Az új funkciókkal információkért lásd: a megadott technikai előzetes kiadásaiban dokumentációját.

## <a name="new-hybrid-features-in-june-2016"></a>Új hibrid funkciókról a 2016. június

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban
A következő Intune-funkciók a 2016. június bevezetett hibrid telepítések működjön.

- **Az Intune szolgáltatás állapota** vonatkozó szolgáltatásállapot-adatok az Intune-hoz egy központi helyen, más Microsoft-szolgáltatásokkal át lett helyezve. Ezek az információk az Office 365 felügyeleti portál szolgáltatás állapota a most találhat. További információkért tekintse meg a [blogbejegyzés](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Bővített Windows 10 vállalati adatkezelési házirend konfigurációs élmény**

  Intune most már a Windows 10-es információ protection-házirend konfigurálása fejlett élményt. Fejlesztései közé tartozik a hatékonyabb módszer alkalmazásszabályok létrehozása, a hálózathatár-definíciók és egyéb Windows Information Protection-beállítások megadása. További tudnivalókért lásd: [a Microsoft Intune Windows információk védelme (folyamatban) házirend létrehozása](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

- **Cisco ISE hálózati hozzáférés-vezérlési szabályzat az Intune-hoz**

  Az ügyfelek, akik a Cisco Identity Service Engine (ISE) 2.1-es verzióját használja, és is használhatja a Microsoft Intune hálózati hozzáférés-vezérlési házirend ISE állíthatja be. Használja ezt a házirendet, a Wi-Fi vagy VPN hálózathoz való kapcsolódáshoz igénylő eszközök az alábbi feltételeknek kell megfelelniük ahhoz, azok csatlakozhatnának a hozzáférés:

  - Intune által felügyeltnek kell lennie
  - Meg kell felelniük az Intune összes telepített megfelelőségi szabályzatának

  A végfelhasználók a nem megfelelő eszközök regisztrálásához kérni fogja, és bármely felelést okozó problémák ahhoz, hogy hozzáférjenek.

- **Feltételes hozzáférés böngészőhöz**

  Beállíthatja a feltételes hozzáférési házirend Exchange Online és SharePoint online-hoz, így azok csak a felügyelt és megfelelő iOS és Android-eszközök támogatott webböngészőiről elérhetők. Végfelhasználók számára, akik próbál bejelentkezni az Outlook Web Access (OWA) és a SharePoint webhelyekre iOS és Android-eszközök az Intune-nal, valamint a nem megfelelést okozó problémák hiányosságok a bejelentkezés végrehajtása előtt az eszköz regisztrálását kéri. További információk a következő helyen találhatók:

  * [Exchange online-hoz és az új dedikált Exchange Online-hoz az Intune-nal való e-mail hozzáférés korlátozása](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
  * [SharePoint online-hoz a Microsoft Intune-nal való hozzáférés korlátozása](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

- **Dynamics CRM Online támogatja a feltételes hozzáférés**

  Beállíthatja a feltételes hozzáférési házirend Dynamics CRM Online-hoz, így csak használható által felügyelt és megfelelő iOS és Android-eszközök. A Dynamics CRM mobilalkalmazás iOS és Android rendszeren bejelentkezni próbáló végfelhasználóktól bekéri a az Intune-ban, valamint a nem megfelelést okozó problémák ahhoz bejelentkezési végre lehessen hajtani. További információkért lásd: [korlátozza a hozzáférést a Dynamics CRM Online-hoz a Microsoft Intune-nal](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune).

- **Az Androidos vállalati portál alkalmazás frissítése**

  Intune most már a következő új házirendeket, amelyek hatással lesznek a felhasználók Android rendszerű vállalati portál:   

  Házirend  |Felhasználók hatása  
  ---------|---------
  Eszközök tiltsák le az ismeretlen forrásból (Android 4.0 +) alkalmazások telepítése     |  Android 4.0-val és későbbi verziókkal rendelkező végfelhasználók számára az üzenet jelenik meg, "Az ismeretlen forrásból történő telepítést le kell tiltani." Ugrás a felhasználóknak kell **beállítások > biztonsági** az eszközökön, és kapcsolja ki az **ismeretlen források**. A megfelelőségi üzenet tartalmaz egy hivatkozást engedélyezi a felhasználóknak az üzenetről és azok van folyamatban a beállítás kikapcsolásának kapcsolatban további információkat.
  Eszközök tiltsák le az ismeretlen forrásból (Android 4.0 +) alkalmazások telepítése  |    Android 4.0-val és későbbi verziókkal rendelkező végfelhasználók számára megjelenik az üzenet "Keresése az eszközön a biztonsági kockázatok." Ugrás a felhasználóknak kell **beállítások > Google > biztonsági** az eszközökön, és kapcsolja be a **biztonsági fenyegetések keresése az eszközön**. A megfelelőségi üzenet tartalmaz egy hivatkozást lehetővé teszi, hogy a felhasználóknak további információt az üzenet és miért ezek alatt szükséges, hogy a beállítás bekapcsolása.     
  USB-hibakeresés letiltásának megkövetelése (Android 4.2 +)  | Android 4.2-es és későbbi verziókkal rendelkező végfelhasználók számára az üzenet jelenik meg, "USB-hibakeresést le kell tiltani." Ugrás a felhasználóknak kell **beállítások > Fejlesztői beállítások** az eszközökön, és kapcsolja ki az **USB-hibakeresés**. A megfelelőségi üzenet tartalmaz egy hivatkozást engedélyezi a felhasználóknak az üzenetről és azok van folyamatban a beállítás kikapcsolásának kapcsolatban további információkat.
  Minimális Android biztonsági javítási szintje (Android 6.0 +)  | Csak Android 6.0 vagy későbbi verziókkal rendelkező végfelhasználók számára az üzenet jelenik meg, "az eszköz nem felel meg a minimális Android biztonsági javítási szintet." Felhasználók kell telepíteni a szükséges biztonsági javítási szintet. A megfelelőségi üzenet tartalmaz egy hivatkozást lehetővé teszi, hogy a felhasználóknak a szükséges biztonsági javítás, és hogy melyik biztonsági javítási jelenleg telepített olvashat.

- **Az IOS rendszerű vállalati portál alkalmazás frissítése**

  * A végfelhasználók-üzleti alkalmazások telepítésekor, jelenik meg egy továbbfejlesztett telepítési élmény. Ha az alkalmazás telepítése hosszú ideig tart, a felhasználók manuálisan szinkronizálhatják az eszközt a szinkronizálási folyamat kényszerített folytatásához. A végfelhasználói lépéseket lásd: manuális szinkronizálás iOS-eszköz.
  * A Microsoft Intune vállalati portál alkalmazást IOS rendszerre frissítve lett az iOS 8.0-s és újabb verzióit támogatja. A frissítés azt jelenti, hogy a végfelhasználók számára a vállalati portál alkalmazás telepítésekor, és regisztrálhatnak új eszközöket az Intune-ban, csak akkor, ha az eszköz fut az iOS 8.0-s vagy újabb. Az iOS nem támogatott verzióját futtató eszközöket korábban regisztrált felhasználók továbbra is a vállalati portál alkalmazással, amely az eszközükön.


### <a name="new-in-1606-technical-preview"></a>Új 1606 Technical Preview
A következő új funkciók, 2016. június bevezetett hibrid Intune és a Configuration Manager Technical Preview 1606 telepítések esetén érhetők el.

- **Automatikusan eszközök gyűjteményekbe kategorizálása**

  Eszközök automatikus elhelyezése a eszközgyűjtemények használatakor a Configuration Manager Intune-nal használható eszközkategóriákat hozhat létre. Felhasználók majd válasszon egy eszközkategóriát, amikor regisztrálják az eszköz Intune-beli van szükség. Emellett módosíthatja a kategóriája az eszköz a Configuration Manager konzoljáról. További információkért lásd: [automatikusan eszközök kategorizálása gyűjteményekbe](/sccm/core/get-started/capabilities-in-technical-preview-1606#dmp_category) a [a Technical Preview 1606 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1606).

  > [!IMPORTANT]
  > Ez a funkció a Microsoft Intune 2016. június kiadásának működik. Győződjön meg arról, hogy Ön frissültek az ebben a kiadásban ahhoz, hogy próbálja ki ezeket az eljárásokat.

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)
Nincs új hibrid funkciókról a Configuration Manager (aktuális ág) 2016. június jelentek meg.

##  <a name="new-hybrid-features-in-may-2016"></a>Új hibrid funkciókról a 2016. május  

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban  
 A következő Intune-funkciók a 2016. május bevezetett hibrid telepítések működjön.

- **MAM SDK HASZNÁLATÁVAL: Támogatási PIN-kód hosszának konfigurálása**

  Mostantól megadhatja a PIN-kód hasonló MAM-alkalmazások PIN-kód hossza. Ehhez a beállított új korlátozásoknak ahhoz, hogy a végfelhasználók számára. A PIN-kód képernyő kis mértékben módosított hosszabb bemeneti fiókjára. További információkért lásd: [MAM-szabályzat beállításai Android](https://docs.microsoft.com/intune/deploy-use/android-mam-policy-settings), és [MAM-szabályzat beállításai iOS](https://docs.microsoft.com/intune/deploy-use/ios-mam-policy-settings).  

- **Skype vállalati verzió IOS és Android**

  Skype vállalati verziót most célba [MAM regisztrálási házirendek nélkül](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). A felhasználók bejelentkezését követően a rendszer alkalmazza a MAM-szabályzatok.  

- **MAM-szabályzatokkal felügyeletre alkalmas új alkalmazások**

  Az Androidos Microsoft Word, Excel és PowerPoint alkalmazásokhoz mostantól társítható MAM-szabályzatok az Intune-ban nem regisztrált eszközökön. Támogatott alkalmazások teljes listájának megtekintéséhez keresse fel a Microsoft Intune mobilalkalmazás-galériát a a [Microsoft Intune alkalmazási partnerektől származó](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) lap.  

- **Androidos vállalati portál alkalmazást: Végfelhasználói bejelentési értesítések**

  Bejelentési értesítést kapnak az Androidos vállalati portál alkalmazás jelenik meg, amikor a végfelhasználók regisztrálásához, vagy távolítsa el az eszközeiket a vállalati portálról.  

- **Vállalati portál webhelyét: Eszközazonosító sáv több információt nyújt a végfelhasználók számára**

  A végfelhasználók mostantól könnyebben azonosíthassa az eszközt a vállalati portál webhelyen választott. Ha a megfelelő eszköz választotta, és kiválaszthatja, melyik a megfelelő eszközt koppintva a **koppintson ide** a kezdőlap hivatkozással.  


### <a name="new-in-1605-technical-preview"></a>Új 1605 Technical Preview  
 A következő új funkciók, 2016. május bevezetett hibrid Intune és a Configuration Manager Technical Preview 1605 telepítések esetén érhetők el. Ezen funkciók szükségesek, hogy a Configuration Manager konzol segítségével konfigurálhatja és kezelheti azokat.  

- **Alkalmazás által indított VPN Windows 10-eszközök**

  Windows 10-es eszközök felügyelete a Configuration Managerbe integrált Intune használata esetén adja hozzá azokat az alkalmazásokat, amelyek automatikusan meg, amelyet a Configuration Manager felügyeleti konzol segítségével konfigurált VPN-kapcsolat. További információkért lásd: [alkalmazás által indított VPN Windows 10-eszközök](/sccm/core/get-started/capabilities-in-technical-preview-1605) a [a Technical Preview 1605 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1605)  

- **Új élmény a távoli eszközök műveletei**

  Javult a felhasználói élmény a távoli eszközök műveletei végrehajtásához a Configuration Manager konzoljáról.

  Például közös műveletek **kivonás/összes adat törlése**, **új PIN-kód**, **távoli zárolás**, és **az aktiválási zár megkerülése** most már megtalálható a **távoli eszközök műveletei** menüjéből érhető el a **eszközök és megfelelőség** munkaterület

  További információkért lásd: [új élmény a távoli eszközök műveletei](/sccm/core/get-started/capabilities-in-technical-preview-1605#new-experience-for-remote-device-actions) a [a Technical Preview 1605 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Üzletági alkalmazások a Windows áruházban**

  A [vállalati Windows áruház](https://www.microsoft.com/en-us/business-store) hol található, és alkalmazásokat vásárolhat a szervezete számára egyenként vagy nagyobb mennyiségben. Ha összekapcsolja az áruházat a Configuration Manager, a Configuration Manager konzolról kezelheti a mennyiségi programban vásárolt alkalmazásokat. További információkért lásd: [üzletági alkalmazások a Windows áruházban](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#windows-store-for-business-apps) a [a Technical Preview 1605 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Általános fejlesztések a mennyiségi programban vásárolt alkalmazások**

  Mennyiségi programban vásárolt alkalmazásokat a vállalati Windows áruház és az iOS app store ugyanazt a nézetet, az engedélyezés **tárolására alkalmazások Licencadatai**. Javult az is, a mennyiségi programban vásárolt alkalmazásokat az IOS-es létrehozási módját. További információkért lásd:[általános fejlesztések a mennyiségi programban vásárolt alkalmazások](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#general-improvements-for-volume-purchased-apps) a [a Technical Preview 1605 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Vállalati tulajdonban lévő eszközök IMEI- vagy iOS sorozatszámmal előzetes bejelentése**

  Vállalat által birtokolt eszközök most azonosíthatja az állomás nemzetközi mobilkészülék-azonosító (IMEI) számokat importálásával. Feltöltheti az eszközök IMEI-számának tartalmazó vesszővel tagolt (.csv) fájlt, vagy meg manuálisan is beírhatja az eszközadatokat.  Az iOS-eszközök sorozatszámokat is importálhat.  További információkért lásd: [előzetes bejelentése vállalati tulajdonban lévő eszközök IMEI- vagy iOS sorozatszámmal](../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_IMEI) a [a Technical Preview 1605 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **A Windows információvédelem (folyamatban)**

  Konfigurációelemek, amelyek lehetővé teszik, hogy telepítheti a Windows információk védelme (folyamatban) házirendeket, többek között, és válassza ki a védett alkalmazások, a Befejezetlen-védelmi szintek és a vállalati adatokat a hálózaton található, így hozhat létre. Befejezetlen kapcsolatos további információkért lásd a következő témaköröket:  

  -   [Vállalati adatok védelme a Windows információk védelme (folyamatban)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)  

  -   [A System Center Configuration Manager használatával Windows információk védelme (folyamatban) szabályzat létrehozása és telepítése](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-sccm)  

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)  
 Nincs új hibrid funkciókról a 2016. május a Configuration Manager (aktuális ág) jelentek meg.  

##  <a name="new-hybrid-features-in-april-2016"></a>Új hibrid funkciókról a 2016. április  

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban  
 A következő Intune-funkciók a 2016. április bevezetett hibrid telepítések működjön.  

- **A MAM-felhasználók megfelelősége**

  Most már megtekintheti az alkalmazásfelügyeleti házirendek bármely felhasználó állapotát az Azure Active Directory (AAD) bérlőben.  További információ: [a Microsoft Intune mobilalkalmazás-felügyeleti szabályzatok figyelése](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) az Intune könyvtárában.  

- **A MAM felügyeletével elkerülhető az Outlook-névjegyek szinkronizálása (Android)**

  Új beállítás érhető el, ami lehetővé teszi az alkalmazás a névjegyeket a natív címjegyzékbe az Android-eszközök szinkronizálása érdekében. Ez az új beállítást kezdetben támogatja az Android-eszközökön elérhető Outlook alkalmazás. További információkért lásd: [létrehozása és telepítése Microsoft Intune mobilalkalmazás-felügyeleti szabályzatok](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) az Intune könyvtárában.  

- **A vállalati portál webhelye fejlesztései**

  Windows 10 Mobile és Windows Phone 8.1-felhasználók-üzleti alkalmazások telepítésekor, akkor a következő új állapotokat, amelyek több részlettel számukra a telepítés most fog látni:  

  -   **Várakozás az eszköz szinkronizálására** – a felhasználó "Telepítés" gombra kattintott, és az eszköz pedig most megpróbál szinkronizálni az Intune-infrastruktúrával. A szinkronizálás szükség, mielőtt a telepítés folytatásához. A "Várakozás az eszköz szinkronizálására" üzenet egyben hivatkozás is, amellyel a felhasználó kattintva olvashat útmutatást manuális szinkronizálása az eszközüket az Intune-ban, ha a szinkronizálási folyamat hosszú ideig tart vagy elakad.  

  -   **Letöltés** – a felhasználó letöltési kérelme feldolgozás alatt áll, és az eszköz letöltése és telepítése.  

- **Az Androidos vállalati portál alkalmazás fejlesztései**

  Felhasználók, akik nem regisztrálták az eszközeiket az Intune-ban, és akiknél nincs telepítve a megfelelő tanúsítvány nem tudnak bejelentkezni az Androidos vállalati portál alkalmazást, és az üzenet jelenik meg, a "Nem tud bejelentkezni, mert az eszközhöz hiányzik egy szükséges tanúsítvány." Az üzenettel együtt megjelenő "Útmutató a probléma megoldásához" hivatkozással, a felhasználó megtekintheti a tanúsítvány telepítési lépéseit. A következő lépések a végfelhasználók a probléma megoldásához, olvassa el [az eszközhöz hiányzik egy szükséges tanúsítvány](/intune/enduser/using-your-android-device-with-intune) az Intune könyvtárában.  

- **Az IOS rendszerű vállalati portál alkalmazás fejlesztései**

  Már támogatja a lekéréses frissítési művelet frissíti a tartalmat a kezdőképernyőn, amely tartalmazza a felsorolt alkalmazások, eszközök és az IT elérhetőségi információkat. A lekéréses frissítési művelet a megfelelőséggel és házirenddel adatokat, amelyeket az aktuális eszköz kiválasztásával, és koppintson végezhető nem ellenőrzi a **szinkronizálási** gombra.  

- **Fejlesztések a Windows 10 Mobile és Windows Phone 8.1 vállalati portál alkalmazásba**

  A végfelhasználók-üzleti alkalmazások telepítésekor, jelenik meg egy továbbfejlesztett telepítési élmény. Ha az alkalmazás telepítése hosszú ideig tart, a felhasználók manuálisan szinkronizálhatják az eszközt a szinkronizálási folyamat kényszerített folytatásához. A végfelhasználói lépéseket lásd: [az eszköz manuális szinkronizálása érdekében alkalmazástelepítések felgyorsítása](/intune/enduser/using-your-windows-device-with-intune) az Intune könyvtárában.  

###  <a name="new-in-1604-technical-preview"></a>A Technical Preview 1604 új
 A következő új funkciók, 2016. április bevezetett hibrid Intune és a Configuration Manager Technical Preview 1604 telepítések esetén érhetők el. Ezen funkciók szükségesek, hogy a Configuration Manager konzol segítségével konfigurálhatja és kezelheti azokat.  

- **Keresése, kezelése és terjesztése a Windows áruház az üzletági alkalmazások Windows 10 rendszerű eszközökhöz, a Configuration Manager konzolról**


  Konfigurációs Manager Technical Preview 1604 segítséget nyújtanak a keresése, kezelése és terjesztése a Windows 10-eszközöket felügyel az alkalmazásokat a vállalati Windows áruházhoz támogatás érhető el. További információkért lásd: [a vállalati Windows áruházból mennyiségi programban vásárolt alkalmazások kezelése](/sccm/core/get-started/capabilities-in-technical-preview-1604#manage-volume-purchased-apps-from-the-windows-store-for-business) a [a Technical Preview 1604 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1604).  

- **SmartLock-beállítás Android-eszközök**

  Új beállítás fel lett véve az Android és Samsung KNOX Standard konfigurációelem, amely lehetővé teszi, hogy a kompatibilis Android-eszközökön a Smart LOCK funkció szabályozza.  Ez a beállítás segítségével megakadályozhatja a végfelhasználók számára a Smart LOCK konfigurálását. Lásd: [SmartLock-beállítás Android-eszközök](/sccm/get-started/capabilities-in-technical-preview-1604#smartlock-setting-for-android-devices) a [a Technical Preview 1604 a System Center Configuration Manager képességei](/sccm/core/get-started/capabilities-in-technical-preview-1604.md).  

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)  
 Nincs új hibrid funkciókról a Configuration Manager (aktuális ág) 2016. április lett bevezetve.  

##  <a name="new-hybrid-features-in-march-2016"></a>Új hibrid funkciókról a 2016. március  

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban  
 A következő Intune-funkciók a 2016. március bevezetett hibrid telepítések működjön.  

- **A MAM felügyeletével elkerülhető az Outlook-névjegyek szinkronizálása (iOS)**

  Új beállítás érhető el, ami lehetővé teszi az alkalmazás a névjegyeket a natív címjegyzékbe az iOS-eszközök szinkronizálása érdekében. Az új beállítást az iOS-eszközökön elérhető Outlook alkalmazás támogatja. További és az egyéb beállításokkal kapcsolatos további információkért lásd: [létrehozása és telepítése mobilalkalmazás-felügyeleti szabályzatok](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) az Intune könyvtárában.  

- **Skype vállalati Online verzió feltételes hozzáférést biztosító támogatja.**

  Beállíthatja a feltételes hozzáférési házirend a Skype vállalati online, hogy csak használható által felügyelt és megfelelő iOS és Android-eszközök.  További információkért lásd: [kezelésére a Skype vállalati online](/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) az Intune könyvtárában.  

- **Támogatás az iOS 9.3 alatt**

  Március 21-én hétfőn jelentette be az iOS 9.3 megjelenését. Az összes meglévő Intune-ban jelenleg elérhető szolgáltatások az iOS-eszközök kezelésének továbbra is problémamentesen működjön, mint a felhasználók IOS 9.3-as verzióra frissítik az eszközeiket.  

- **Windows-alkalmazáscsomagok közvetlenül elérhetők a vállalati portál webhelye**

  Windows 8, Windows 8.1 és Windows RT rendszerű számítógépek felhasználói most már telepítheti a Windows-alkalmazáscsomagokat (.appx kiterjesztés) közvetlenül a vállalati portál webhelyről. Korábban Önnek kellett központilag telepítenie, vagy a felhasználók a vállalati portál alkalmazás telepítésekor az eszközökön alkalmazásokat telepíteni kellett.  

- **Távolról zárolhatják az eszközeiket a vállalati portál webhelye**

  Egy új távoli zárolási beállítás bővült a vállalati portál webhelyre a felhasználók távolról zárolható eszközüket a portálról, ha az eszköz elvesztésekor vagy ellopásakor.  

- **Kihasználhatja az iOS "Megnyitás a következőben" kezelési, a külső MDM-megoldásban regisztrált eszközökhöz**

  A harmadik fél mobileszköz-felügyelet (MDM) szállító segítségével kihasználhatja az iOS "Megnyitás a következőben" kezelési. A korlátozásokat állíthat be a konfigurációs profil beállításaiban, és telepítheti az alkalmazást a mobileszköz-kezelési szoftverrel. Amikor a felhasználó telepíti a felügyelt alkalmazást, a korlátozások érvényesek. A részletekért olvassa el: [A Microsoft Intune mobilalkalmazás-felügyeleti szabályzatok és az iOS megnyitási engedélyei](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune) az Intune könyvtárában.  

- **Mam-ot támogató Microsoft-alkalmazások**

  Intune mobilalkalmazás-kezelési házirendekkel használható Microsoft-alkalmazások listája frissítve lett a legújabb alkalmazásokat (csak az Intune-ban regisztrált eszközök) tartalmazza.  

- **Intune-hoz készült Adobe Reader telepítése az Intune által felügyelt iOS-eszközöket a vállalati**

  Az IOS rendszerhez készült Adobe Reader alkalmazás mostantól kezelhető a regisztrált eszközökön az Intune mobilalkalmazás-kezelési házirendjével.  

- A Rights Management megosztóalkalmazás Android esetén támogatott

  A rendszergazdák telepítheti a mobilalkalmazás-felügyeleti házirendekkel, így megtekintheti, hogy a végfelhasználók képek, AV és PDF-fájlok biztonsága érdekében-e informatikai szerint kezelhetők az eszközök Intune-t használja.  

- **Az Android és iOS vállalati portál alkalmazás fejlesztések**

  -   Amikor a felhasználók mobilalkalmazás-kezelés (MAM) által kezelt alkalmazás, egy üzenetet, amely értesíti őket, hogy az alkalmazás a vállalat felügyeli látnak. Felhasználók mostantól mit jelent a "felügyelt alkalmazás" kapcsolatban további információkat itt a "További információk" hivatkozásra koppintva. Is koppintva "Ne jelenjen meg ismét", hogy az üzenet már nem jelenik meg, ha az alkalmazás elindításakor.  

  -   Új képernyők vezetik végig a regisztrációs folyamatot a felhasználókat, és további információval szolgálnak a felhasználóknak miért érdemes regisztrálniuk, és mi a rendszergazdák és mit nem láthat a regisztrált eszközökön.  

  -   A regisztrációs hibaüzenetek jelennek meg a vállalati portál alkalmazás.  

### <a name="new-in-configuration-manager-technical-preview"></a>A Configuration Manager Technical Preview újdonságai  
 Nincs új hibrid funkciókról a Configuration Manager Technical Preview a 2016. március-ben jelentek meg.  

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)  
 2016. március bevezetett az alábbi új szolgáltatások érhetők el hibrid telepítések esetén az Intune és a Configuration Manager (aktuális ág) 1602-es verzióra. Ezen funkciók szükségesek, hogy a Configuration Manager konzol segítségével konfigurálhatja és kezelheti azokat.  

- **iOS-alkalmazáskonfigurációs szabályzatok**

  A Configuration Manager (aktuális ág) 1602-es verziójában a alkalmazás-konfigurációs házirendek segítségével megadhatja azokat a beállításokat, amelyekre szükség lehet, amikor a felhasználó egy iOS-alkalmazást futtat. További információkért lásd: [iOS-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek a System Center Configuration Managerben](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies).  

- **Mennyiségi programban vásárolt iOS-alkalmazások felügyelete**

  Az 1602-es verziójában a Configuration Manager (aktuális ág) telepítheti és vásárolt alkalmazások kezelése a mennyiségi programban az Apple Volume Purchase Program (VPP) importálja a licencadatokat az app store-ból, és nyomon követni, hogy hány licencet használt fel. További információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások a System Center Configuration Managerrel kezelése](/sccm/apps/deploy-use/manage-volume-purchased-ios-apps).  

- **Office-mobilalkalmazások automatikus létrehozása**

  A Configuration Manager (aktuális ág) 1602-es verziójától kezdve a következő Microsoft Office-mobilalkalmazások Android és iOS jönnek létre 1511-es verzióra való frissítéskor:  

  -   A Microsoft Word  
  -   A Microsoft Excel  
  -   Microsoft PowerPoint  
  -   Microsoft onedrive vállalati verzió  
  -   Microsoft OneNote (csak iOS)  
  -   A Microsoft Outlook  

  Ezeket az alkalmazásokat a Configuration Manager konzol alkalmazások csomópontjában találja. Alkalmazások központi telepítésével kapcsolatos további információkért lásd: [központi telepítése a System Center Configuration Managerrel alkalmazások](../../apps/deploy-use/deploy-applications.md).  

- **Teljes képernyős mód beállításai Android Samsung KNOX Standard eszközökhöz**

  A teljes képernyős mód lehetővé teszi az eszközök zárolását, hogy csak bizonyos szolgáltatások működjenek rajtuk.  A Configuration Manager (aktuális ág) 1602-es verziójától kezdve megadhat teljes képernyős mód beállításai Samsung KNOX Standard eszközökön használható. További információkért lásd: [Android és Samsung KNOX Standard eszközökhöz konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client).  

- **iOS aktiválási zára**

  A Configuration Manager (aktuális ág) 1602-es verziójától kezdve kezelheti iOS aktiválási zára, egyik funkciója a Find My iPhone alkalmazást az iOS 7.1 és újabb rendszerű eszközök. Ha a Find My iPhone alkalmazást használják egy eszközön, az aktiválási zár automatikusan engedélyezve lesz.  További információkért lásd: [kezelése iOS aktiválási zár megkerülésével a System Center Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock#bypass-activation-lock).  

