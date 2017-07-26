---
title: What&quot;s new in hibrid MDM a Configuration Manager |} Microsoft Docs
description: "További tudnivalók a mobileszközök felügyeleti elérhető új szolgáltatások hibrid telepítések esetén a Configuration Manager és az Intune-ban."
ms.custom: na
ms.date: 04/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
caps.latest.revision: 40
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: 0af5ae68353fcf1db846e2e27f3391fe87dcfc42
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="whats-new-in-hybrid-mobile-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hibrid mobileszköz-kezelés a System Center Configuration Manager és a Microsoft Intune újdonságai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a cikk részletesen a új mobileszköz-felügyelet (MDM) szolgáltatásához hibrid telepítések esetén a System Center Configuration Manager és a Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>A Configuration Manager verzióival való kompatibilitás érdekében  

 Ez a cikk minden szakasz hibrid funkciókról a 3 különböző kategóriák. Az alábbi útmutató segítségével meghatározhatja az egyes kategóriák funkciók kompatibilisek-e a Configuration Manager különböző verziói:  

|A szolgáltatás kategóriák|Leírás|
|-|-|
|**Új Microsoft Intune-ban** | A kategóriához tartozó összes funkcióját, többek között a System Center 2012 R2 Configuration Manager kiadások, mivel ezek a szolgáltatások csak megkövetelése az Intune-ba, és nincs szükség további funkciókat a Configuration Manager az összes Configuration Manager kiadásokban együtt kell működnie.|
|**A Configuration Manager Technical Preview újdonságai**| A kategóriához tartozó összes funkcióját csak a megadott technikai előzetes kiadásaiban dolgozhat. Próbálja ki ezeket a funkciókat, telepítenie kell a Technical Preview verzió van megadva a a szolgáltatás leírása. További információkért lásd: [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md).|
|**Új Configuration Manager (aktuális ág)**| A kategóriához tartozó összes funkcióját csak működik a megadott verziójú Configuration Manager (aktuális ág), például az 1511-es vagy az 1602-es verzióját. A hibrid telepítéshez használata a Configuration Manager egy régebbi verziója, frissítenie kell a Configuration Manager (aktuális ág) verzió van megadva a szolgáltatás leírása. További információkért lásd: [frissítése a System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|

## <a name="april-2017"></a>2017. április

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

- **Managed Browser elérhető MyApps**

  Microsoft MyApps most már rendelkezik jobb támogatása érdekében a Managed Browser belül. Felügyelt böngésző felhasználók, akikre nem érvényes a felügyeleti kerül közvetlenül a MyApps szolgáltatást, ha a rendszergazda által létesített SaaS-alkalmazások eléréséhez. Az Intune felügyeleti megcélzott felhasználók továbbra is fér hozzá a MyApps a beépített Managed Browser könyvjelzőt.

- **A Managed Browser és a vállalati portál új ikonok**

  A Managed Browser fogadja az alkalmazást az Android és iOS verzióinak frissített ikonjai. Az új ikonra a frissített Intune jelvény abba, hogy egységesebb más alkalmazásokkal az Enterprise Mobility + Security (EM + S) fogja tartalmazni. Megtekintheti az új ikonra a Managed Browser a [what's new in Intune alkalmazás felhasználói felületén lap](/intune/whats-new/whats-new-in-intune-app-ui.md).

  A vállalati portál frissített ikonjai a Android, iOS és Windows-verziók az alkalmazás javítására konzisztencia EM + s más alkalmazásokkal is fogadja. Ezekkel az ikonokkal fokozatosan kiadjuk késői előfordulhat, hogy a április a platformok közötti.

- **Bejelentkezési folyamatjelző az Androidos vállalati portál**

  Az Androidos vállalati portál alkalmazás frissítése bejelentkezési állapotjelző jeleníti meg, a felhasználó elindítja vagy az alkalmazás. A kijelző halad új állapotokat, kezdve a "Kapcsolódás...", "Aláírása ban", majd a "Ellenőrzése biztonsági követelmények..." előtt a felhasználók az alkalmazás eléréséhez. Megtekintheti az új képernyők, amelyekhez a vállalati portál alkalmazás Android a [what's new in Intune alkalmazás felhasználói felületén lap](/intune/whats-new/whats-new-in-intune-app-ui.md).

- **A SharePoint Online elérésének magakadályozása az alkalmazásoknak**

  Mostantól létrehozhat egy alkalmazás-alapú feltételes hozzáférési szabályzatot az alkalmazásoknak, amelyekre vonatkozóan nincs engedélyezve az alkalmazás adatvédelmi szabályzatok alkalmazása tőlük, hozzáférését [SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online). Az alkalmazások-alapú feltételes hozzáférés a forgatókönyvben az alkalmazások hozzáférjenek a SharePoint Online az Azure portál használatával kívánt is megadhat.

### <a name="new-in-configuration-manager-technical-preview-1704"></a>Új Configuration Manager Technical Preview 1704

- **Android-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek**

  Segítségével a System Center Configuration Manager (a Configuration Manager) alkalmazás-konfigurációs szabályzatok előre konfigurált beállítások terjesztése, amikor egy felhasználó egy alkalmazást futtat az Android munkahelyi eszközök. Android alkalmazás-konfigurációs szabályzatok csak munkahelyi az Android rendszerű eszközök elérhetők, és jóváhagyott alkalmazásokra vonatkozik a munkahelyi store a Play áruházból. Ez a szolgáltatás kipróbálásához kapcsolatos információkért lásd: [konfigurálása Android-alkalmazások az alkalmazás-konfigurációs házirendek](/sccm/core/get-started/capabilities-in-technical-preview-1704#configure-android-apps-with-app-configuration-policies).

## <a name="march-2017"></a>2017. március

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

- **Új felhasználói élmény a vállalati portál alkalmazás beállítása Androidhoz**

  A vállalati portál alkalmazás Android ki a felhasználói felület egy több modern Megjelenés és működés. A fontos frissítések a következők:

  - Színek: Vállalati portál lapon fejlécek az IT által definiált branding színe.
  - Alkalmazások: Az a **alkalmazások** lapon, a **kiemelt alkalmazások** és **minden alkalmazás** gombok frissülnek.
  - Keresés: Az a **alkalmazások** lapon, a **keresési** gomb egy lebegőpontos művelet gombra.
  - A Navigálás alkalmazások: **Minden alkalmazás** a nézetben látható lapokra nézetét **kiemelt**, **összes**, és **kategóriák** a könnyebb Navigálás érdekében.
  - A következőket támogatják: **Eszközök** és **IT-csoport elérhetősége** lapok frissítése olvashatóságának javítása érdekében.

  Változásokkal kapcsolatos további részletekért lásd: [Intune végfelhasználói alkalmazások felhasználói felületi frissítései](/intune/whats-new/whats-new-in-intune-app-ui).

- **Parancsfájl aláírása a Windows 10-es vállalati portál**

  A letöltés, és közvetlenül a Windows 10-es vállalati portál alkalmazást kell, ha használhatja egy parancsfájl egyszerűsítése és felgyorsítják az alkalmazás-aláíró a szervezet számára.  A parancsfájl és használatához kapcsolódó utasításokat letöltéséhez lásd: [Microsoft Intune aláíró parancsfájl a Windows 10-es vállalati portál](https://aka.ms/win10cpscript) a TechNet gyűjteményben. Ezt a hirdetményt kapcsolatos további tudnivalókért lásd: [a Windows 10-es vállalati portál alkalmazás frissítése](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) meg az Intune támogatási munkacsoportjának blogjából.

- **Android-alapú Kínában felhasználói továbbfejlesztett támogatása**

  Mivel a Google Play áruház kínai Android-eszközök alkalmazások kell beszereznie kínai piacterek. A vállalati portál Android-töltheti le a vállalati portál és az Outlook alkalmazásban helyi alkalmazás-áruházak Kínában felhasználói irányítják át fogja támogatni a munkafolyamat. Ez javítja a felhasználói élmény feltételes hozzáférési házirendeket, ha engedélyezve vannak a mobileszköz-kezelés és a mobilalkalmazás-kezelés. A vállalati portál és az Outlook Android-alkalmazások a következő kínai alkalmazás-áruházak érhetők el:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

- **Győződjön meg arról, hogy a vállalati portál alkalmazásainak naprakészek**

  2016. December azt adott frissítést, a többtényezős hitelesítés (MFA) kényszerítési engedélyezve van a felhasználók egy csoportjánál amikor regisztrálják az iOS, Android, Windows 8.1 + vagy Windows Phone 8.1 + eszköz. Ez a funkció nem megvalósítható, ha a vállalati portál alkalmazás bizonyos alapverziói Android (v5.0.3419.0 +) és az iOS rendszerhez (v2.1.17 +).

  Vannak folyamatosan javítja az Intune felügyeleti szolgáltatásait, és számos fejlesztést rendelkezik összehangolt frissítések a vállalati portál alkalmazásainak az összes támogatott platformon. Ennek eredményeképpen ajánlott, hogy őrizze meg a vállalati portál alkalmazás legújabb verzióját telepített eszközökön az Intune-ban és a legjobb felhasználói élmény előnyeit fejlesztései.

  >[!Tip]
  > A felhasználóknak az eszközeiket a megfelelő app Store áruházból származó alkalmazások automatikusan frissíteni kell. Ha az Androidos vállalati portál alkalmazás elérhetővé tett egy hálózati megosztáson, letöltheti a legújabb verziót [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

- **Microsoft Teams engedélyezve van a MAM-iOS és Android rendszeren**

  Az iOS és Android rendszerhez készült Microsoft Teams alkalmazások már támogatják az Intune mobilalkalmazás-felügyeleti képességei, úgy is, amelyekkel a munkahelyi szabadon eszközön, biztosítva, hogy a beszélgetés és a vállalati adatok van védve legyenek minden kapcsolja az adapterekhez. További részletekért lásd: [Microsoft Teams bejelentés](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) a nagyvállalati mobilitási és biztonsági blogon.

### <a name="new-in-configuration-manager-technical-preview-1703"></a>Új Configuration Manager Technical Preview 1703

- **További támogatási Apple Volume Purchase Program-forgatókönyvek**

   Technical Preview 1703 verziótól kezdve most már rendelkezik a következő Volume Purchase Program (VPP) forgatókönyvek támogatása:

   - Licencelési eszköz - alkalmazásokat, amelyek támogatják a licencelési eszköz, és az eszközök gyűjteményekbe csak eszközönként egy-egy licencet.  Korábban kellett használni licencet minden felhasználói eszközön. További információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások telepítése eszközgyűjtemények](/sccm/core/get-started/capabilities-in-technical-preview-1703#deploy-volume-purchased-ios-apps-to-device-collections).
   - Mindkét VPP-alkalmazásokat kezeléséhez használt jogkivonatokkal több VPP-tokenek egyetlen hibrid-bérlő használatát.
   - VPP oktatási jogkivonatok, amelyek képesek megkülönböztetni üzleti és education jogkivonatok használatát.

### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)

Az alábbi, korábban a Configuration Manager Technical Preview kiadásokban számára elérhető szolgáltatása hibrid telepítések esetén az Intune és a Configuration Manager (aktuális ág) 1702 verziója.

- [Android munkahelyi támogatásához](/sccm/core/plan-design/changes/whats-new-in-version-1702##android-for-work-support)
- [Nem megfelelő alkalmazások a megfelelőségi beállítások](/sccm/core/plan-design/changes/whats-new-in-version-1702#conditional-access-device-compliance-policy-improvements)
- [PFX-tanúsítvány létrehozása és a terjesztési és az S/MIME-támogatás](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-to-certificate-profiles)
- [Android és iOS verziója már nem nem targetable a létrehozási varázslók a hibrid MDM](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm)

A következő további hibrid funkciókat is tartalmaz 1702 a Configuration Manager verziója (aktuális ág):

- **Az Apple Volume Purchase Program (VPP) továbbfejlesztett támogatása**

  - Eszközök, valamint a felhasználók most már telepítheti az licencelt alkalmazások. Attól függően, hogy az alkalmazások képesek támogatni eszközlicencelési megfelelő licencre lesz engedte telepítésekor, az alábbiak szerint:

    | Configuration Manager verziója | Alkalmazás licencelésre eszköz? | Központi telepítési gyűjtemény típusa | Az igényelt licenc |
    |-|-|-|-|
    |Korábbi, mint 1702|Igen|Felhasználó|Felhasználói licenc|
    |Korábbi, mint 1702|Nem|Felhasználó|Felhasználói licenc|
    |Korábbi, mint 1702|Igen|Eszköz|Felhasználói licenc|
    |Korábbi, mint 1702|Nem|Eszköz|Felhasználói licenc|
    |1702 és újabb verziók|Igen|Felhasználó|Felhasználói licenc|
    |1702 és újabb verziók|Nem|Felhasználó|Felhasználói licenc|
    |1702 és újabb verziók|Igen|Eszköz|Eszköz-licenc|
    |1702 és újabb verziók|Nem|Eszköz|Felhasználói licenc|

  - Most is telepítheti és nyomon követheti a vásárolt alkalmazásokat az IOS Volume Purchase Program oktatási célokra.

  - Több Apple volume purchase program-tokenek a Configuration Manager mostantól társíthat.

  Mennyiségi programban vásárolt iOS-alkalmazásokkal kapcsolatos további információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások felügyelete](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

- **Az üzletági alkalmazások vállalati Windows áruházban támogatása**

  Most szinkronizálhatja az egyéni üzletági alkalmazások a vállalati Windows áruházban.

- **Új Mobile fenyegetés védelmi figyelési eszközök**

    Most már rendelkezik új módjai a figyelheti a Mobile fenyegetés védelmi szolgáltató megfelelőségi állapotát.

    További információkért lásd: [Mobile fenyegetés védelmi megfelelőségi figyelése](/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="february-2017"></a>2017. február

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

- **A vállalati portál webhelye korszerűsítésénél**

  A vállalati portál webhelye, akik nem rendelkeznek felügyelt eszközök szánt alkalmazások támogatja. A webhely igazodik más Microsoft-termékek és szolgáltatások kontrasztos színséma, dinamikus cikkben szereplő ábrákat és egy Hamburg "menü" segélyszolgálat kapcsolattartási adatai és a meglévő felügyelt eszközökön információkat tartalmazó használatával. A kezdőlapja nem rendezhetők át, hogy hangsúlyozzák, a kiemelt és nemrég frissített alkalmazások forgódobok rendelkező felhasználók számára elérhető alkalmazások. Megtalálja előtt és után érhető el a [felhasználói felület frissítések](/intune/whats-new/whats-new-in-intune-app-ui) lap.

- **Új MDM-kiszolgáló címe Windows-eszközök**

  A Windows és Windows Phone-eszközök regisztrációjával kapcsolatos MDM-kiszolgáló címe enrollment.manage.microsoft.com a manage.microsoft.com megváltozott. MDM-kiszolgáló címeként enrollment.manage.microsoft.com használatára, ha egy Windows regisztrálása során bekéri a felhasználó értesítése, vagy és a Windows Phone-eszközön. A frissítés is telepíthető a CNAME DNS, amely EnterpriseEnrollment.contoso.com átirányítja a manage.microsoft.com egy olyan CNAME REKORDOT a DNS-ben, amely az EnterpriseEnrollment.contoso.com webhelyről átirányítja a felhasználókat az EnterpriseEnrollment-s.Manage.microsoft.com címre kell cserélni. Ez a változás kapcsolatos további információkért látogasson el http://aka.ms/intuneenrollsvrchange.

### <a name="new-in-configuration-manager-technical-preview-1702"></a>Új Configuration Manager Technical Preview 1702

- **Android munkahelyi támogatásához**

  Kezelheti az Android-alapú eszközök Android for Work használata a Configuration Manager Technical Preview 1702 hibrid MDM-környezetekben. Támogatott Android-eszközök mostantól regisztrálása, Android munkahelyi eszközök, amely létrehoz egy munkahelyi profil jóvá a Play áruházban a munkahelyi alkalmazásokat telepítheti az eszközön. Akkor is konfigurálhatja, és a konfigurációs elemek, a megfelelőségi szabályzatok és az erőforrás-hozzáférési profilokkal ezen eszközök központi telepítése. További információkért lásd: [Android munkahelyi támogatásához](/sccm/core/get-started/capabilities-in-technical-preview-1702#android-for-work-support).

- **Nem megfelelő alkalmazások a megfelelőségi beállítások**

  A megfelelőségi szabályzatok most nem megfelelő alkalmazások Android és iOS alkalmazások szabályait hozhat létre. Ha az eszközön a meghatározott alkalmazások telepítve van, lesz megjelölve "nem megfelelő", és megszűnik a hozzáférése a feltételes hozzáférési házirendekkel megfelelően a vállalati erőforrásokhoz. További információ [feltételes hozzáférést biztosító eszköz megfelelőségi házirend fejlesztései](/sccm/core/get-started/capabilities-in-technical-preview-1702#conditional-access-device-compliance-policy-improvements).

- **PFX-tanúsítvány létrehozása és a terjesztési és az S/MIME-támogatás**

  Mostantól létrehozhat és PFX-tanúsítványok telepítése a felhasználók hibrid környezetben. Ezek a tanúsítványok majd használható S/MIME-e-mailek titkosításához és visszafejtéséhez, hogy a felhasználók által regisztrált eszközök által. További információkért lásd: [létrehozása PFX-tanúsítványokat használ S MIME támogatja](/sccm/core/get-started/capabilities-in-technical-preview-1702#create-pfx-certificates-with-s-mime-support).

- **További iOS konfigurációs beállítások támogatása**
   
    Most már rendelkezik egy konfigurációelem részeként konfigurálható 42 további iOS-beállítások. A beállítások (összes 35) a legtöbb felügyelt iOS-eszközök bővültek. További információkért lásd: [új megfelelőségi beállítások az iOS-eszközök](/sccm/core/get-started/capabilities-in-technical-preview-1702#new-compliance-settings-for-ios-devices).

## <a name="january-2017"></a>2017. január

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

- **Android 7.1.1 támogatja**

  Intune most már teljes mértékben támogatja és kezeli Android 7.1.1.

- **Hárítsa el a problémát, ahol az iOS-eszközök nem aktív, vagy a felügyeleti konzol nem tud kommunikálni őket**

  Amikor a felhasználók eszközeire elveszthetik a kapcsolatot az Intune-nal, átadhatja nekik új hibaelhárítási lépéseket segítséget nyújthatnak a vállalati erőforrásokhoz való hozzáféréshez. Lásd: [eszközök inaktívak, vagy a felügyeleti konzol nem tud kommunikálni őket](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="new-in-configuration-manager-technical-preview-1701"></a>Új Configuration Manager Technical Preview 1701

- **Android és iOS verziója már nem nem targetable a létrehozási varázslók a hibrid MDM**

  Hibrid mobileszköz-kezelés (MDM) a Technical Preview 1701 kezdve, már nem kell átadnia Android és iOS adott verzió új házirendek és profilok az Intune által felügyelt eszközök létrehozásakor. Ez a változás a hibrid telepítések is támogatást nyújt a gyorsabban új Android és iOS verziója egy új Configuration Manager-kiadás vagy a bővítmény anélkül. További tudnivalókért lásd: [Android és iOS verziója már nem nem a létrehozási varázslók targetable](/sccm/core/get-started/capabilities-in-technical-preview-1701#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm).


## <a name="december-2016"></a>2016. december

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

- **Többtényezős hitelesítés (MFA) a regisztrációs áll át az Azure-portálon**

  Korábban kerülne az Intune-konzolon, vagy a Configuration Manager konzol többtényezős hitelesítés beállítása az Intune-ban történő regisztrációt. A frissített szolgáltatással, először most jelentkezik be az [a Microsoft Azure-portálon] (https://manage.windowsazure.com) használata az Intune-felhasználó hitelesítő adatait, és az Azure AD MFA-beállítás konfigurálásához. További tudnivalókért tekintse meg az [a Microsoft Intune a többtényezős hitelesítést] (https://aka.ms/mfa_ad).

- **A vállalati portál alkalmazás Android Kínában most már hozzáférhető**

  A vállalati portál alkalmazás Android Kínában most érhető el. Google Play áruház Kínában hiánya miatt Android-eszközök alkalmazásokat kell beszereznie kínai app piacterek. A vállalati portál alkalmazás Android letölthető a következő tárolókat érhető el:

  -    [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  -    [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  -    [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  -    [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
  -    [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

  A vállalati portál alkalmazás Android Google Play-szolgáltatások a Microsoft Intune szolgáltatással való kommunikációra használja. Google Play-szolgáltatások még nem érhető el a kínai, mert a következő feladatokat végezheti órát is igénybe vehet legfeljebb 8 befejezéséhez.

  | A Configuration Manager felügyeleti konzol | Intune vállalati portál alkalmazás Android-verziójában | Intune vállalati portál webhely |
  |----|----|----|        
  | Kivonás/összes adat törlése (töröl minden adatot)    | Távolítsa el a távoli eszköz | Távolítsa el az eszköz (helyi és távoli) |
  | Kivonás/összes adat törlése (a vállalati adatok eltávolítása)    | Eszköz alaphelyzetbe állítása | Eszköz alaphelyzetbe állítása|
  | Új vagy frissített az alkalmazások telepítésének | Elérhető az üzletági alkalmazások telepítése | Eszköz PIN-kód alaphelyzetbe állítása|
  | Távoli zárolás    | | |
  | Jelszó alaphelyzetbe állítása | | |        


## <a name="november-2016"></a>2016. november

### <a name="new-in-microsoft-intune"></a>Új Microsoft Intune-ban

- **Új Microsoft Intune vállalati portál Windows 10 eszközökön érhető el**

  A Microsoft közzétette az új [Windows 10-eszközök a vállalati portál alkalmazás](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Ezt az alkalmazást, amely az új univerzális Windows 10-formátum, minden Windows 10-es eszközön, a számítógép és mobil egyaránt, továbbra is engedélyezze ugyanazokat előző vállalati portál alkalmazás által biztosított funkciókat azonos frissített felhasználói élményt biztosít.

  Az új alkalmazás kihasználja a platform jellegzetességeket, például egyszeri bejelentkezés (SSO) és a tanúsítvány alapú hitelesítést, a Windows 10 rendszerű eszközökön. Az alkalmazás érhető el a meglévő Windows 8.1 vállalati portál frissítése, és Windows Phone 8.1 vállalati portál telepíti a Windows áruházból. További részletekért látogasson el a [Intune támogatási munkacsoportjának blogjából](http://aka.ms/intunecp_universalapp).

  Az új vállalati portál alkalmazás megjeleníti bármely megjelölt üzleti alkalmazások Windows áruház **elérhető** a Configuration Manager konzolon.


### <a name="new-in-configuration-manager-current-branch"></a>Új Configuration Manager (aktuális ág)

Az alábbi, korábban a Configuration Manager Technical Preview kiadásokban számára elérhető szolgáltatása hibrid telepítések esetén az Intune és a Configuration Manager (aktuális ág) 1610 verziója.

* [További beállításokat és fejlett élményt a konfigurációs elemek](/sccm/core/plan-design/changes/whats-new-in-version-1610#new-compliance-settings-for-configuration-items)
* [További beállítások megadása a DEP-profilok](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [A vállalati Windows áruházban található alkalmazásokra fizetős](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Natív kapcsolattípusokat Windows 10 VPN-profilokhoz](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Intune megfelelőségi diagramok](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)
* [A konzol házirend szinkronizálni kívánt kérése](/sccm/mdm/deploy-use/sync-intune-device)
* [A Windows Defender konfigurációs beállításai](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#windows-defender)

A következő további hibrid funkciókat is tartalmaz 1610 a Configuration Manager verziója (aktuális ág):

- **A regisztrált eszközök megnövekedett számát**

  Most már lehetővé teheti a felhasználók legfeljebb 15-eszközök regisztrálásához. Az előző korlátját felhasználónként 5 eszköz volt.


- **További biztonsági támogatás**

  Teljes körű rendszergazda mellett a következő beépített biztonsági szerepkörök teljes hozzáféréssel rendelkezik elemekre a minden céges eszköz csomópontban, többek között a Predeclared eszközök, az iOS beléptetési profilok és a Windows regisztrációs csomagok:

    - Eszközkezelő
    - Company Resource Access Manager

  Ezek a területek a Configuration Manager konzol csak olvasható hozzáférést továbbra is kap az írásvédett elemző szerepkörhöz.

- **Automatikus indítást VPN-hozzáférését a Windows információvédelem alkalmazásokból**

  Hatására az összes társított alkalmazások automatikusan elindítani a VPN-kapcsolatot, az eszköz futtatásakor a Windows 10 VPN-profilokat is hozzáadhat egy Windows információvédelem elsődleges tartományt. Ez a beállítás egy natív kapcsolattípus kiválasztásakor csak érhető el.

- **Feltételes hozzáférés a Windows 10 VPN-profilok**

    Most előírhatja a Windows 10-es eszközöket regisztrálni kell a megfelelő Windows 10 VPN-profilok létrehozása a Configuration Manager konzolon keresztül VPN-hozzáférést Azure Active Directoryban. Ez az új révén lehetséges **engedélyezze a feltételes hozzáférést a VPN-kapcsolat** jelölőnégyzetet a hitelesítési módszer a VPN-profil varázsló és a Windows 10 VPN-profilok esetében a VPN-profil tulajdonságai lapján. Ez a beállítás egy natív kapcsolattípus kiválasztásakor csak érhető el.

    Ha engedélyezi a feltételes hozzáférés a profil egy külön egyszeri bejelentkezés hitelesítési tanúsítvány is megadható.


## <a name="notices"></a>Megjegyzések

### <a name="system-center-2012-configuration-sp1-and-system-center-2012-r2-configuration-manager-rtm-support-for-hybrid-mobile-device-management-ending-on-april-10-2017"></a>System Center 2012 Configuration SP1 és System Center 2012 R2 Configuration Manager (RTM): Hibrid mobileszköz-kezelés 2017. április 10 végződő támogatása

*2017. január 11.*

A System Center 2012 Configuration Manager SP1 és System Center 2012 R2 Configuration Manager RTM támogatása véget ért, 2016. július 12. Ezt követően támogatása ezektől a kiadásoktól csatlakozik a Microsoft Intune szolgáltatás a hibrid MDM 2017. április 10 ér véget. E dátumot követően a hibrid MDM leáll, az ezektől a kiadásoktól működik. Felügyelt eszközök lényegében válik nem felügyelt, mivel az Intune-összekötő nem csatlakoznak az Intune-bA. A Configuration Manager-adatok (például a szabályzatok és alkalmazások) nem halad legfeljebb Intune-ban, és felügyelt eszközön tárolt adatok nem erdőtől áramolnak a Configuration Manager le, amíg nem történik frissítés.

Ha hibrid telepítés Configuration Manager 2012 SP1 vagy R2 RTM használ, azt javasoljuk 2017. április 10. előtt frissíteni a Configuration Manager (aktuális ág) vagy a Configuration Manager 2012 (R2 SP1 vagy SP2) a legújabb támogatott szervizcsomagjának a szolgáltatás megszűnésének megelőzése érdekében.

További források:
-    [Frissítés a System Center Configuration Manager (aktuális ág)](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
-    [A System Center 2012 R2 Configuration Manager SP1 tartozó frissítések megtervezése](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningR2SP1Upgrade)
-    [A System Center 2012 Configuration Manager SP2 tartozó frissítések megtervezése](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningSP2Upgrade)

### <a name="windows-phone-8-company-portal-upload-deprecated"></a>Windows Phone 8 vállalati portál feltöltés elavult
*2016. október 25.*

Töltse fel az aláírt vállalati portál alkalmazás képes Intune támogatása is elavult a Windows 8, Windows Phone 8, és a Windows RT és a Windows Phone 8 vállalati portál támogatása befejezi novemberben eltávolították a Configuration Manager konzol.  Már regisztrált Windows 8, Windows Phone 8 és Windows RT rendszerű eszközök továbbra is támogatott, de az ezekhez a platformokhoz további eszközök regisztrálása nem támogatott.


### <a name="see-also"></a>Lásd még:

- [Hibrid MDM-funkciókat részhez](whats-new-hybrid-archive.md)
- [Új mobileszköz-kezelési funkciók a System Center 2012 Configuration Managerben](https://technet.microsoft.com/library/mt445560.aspx)

