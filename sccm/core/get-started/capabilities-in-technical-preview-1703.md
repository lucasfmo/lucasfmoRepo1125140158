---
title: "A Technical Preview-ban 1703 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1703 verziója."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e801f8c-d331-41ee-8f27-908448fc0951
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: bb1b96a56db68dcea22270855b899ba3a90afd0d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1703-for-system-center-configuration-manager"></a>A rendszer 1703 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1703 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan technical Preview funkciókkal kapcsolatos visszajelzés küldése közötti frissíteni.    


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Eszközgyűjtemények mennyiségi programban vásárolt iOS-alkalmazások telepítése

Eszközök, valamint a felhasználók most már telepítheti az licencelt alkalmazások. Attól függően, hogy az alkalmazások képesek támogatni eszközlicencelési megfelelő licencre lesz engedte telepítésekor, az alábbiak szerint:

|||||
|-|-|-|-|
|Configuration Manager verziója|Alkalmazás licencelésre eszköz?|Központi telepítés gyűjtemény típusa|Az igényelt licenc|
|Korábbi, mint 1702|Igen|Felhasználó|Felhasználói licenc|
|Korábbi, mint 1702|Nem|Felhasználó|Felhasználói licenc|
|Korábbi, mint 1702|Igen|Eszköz|Felhasználói licenc|
|Korábbi, mint 1702|Nem|Eszköz|Felhasználói licenc|
|1702 és újabb verziók|Igen|Felhasználó|Felhasználói licenc|
|1702 és újabb verziók|Nem|Felhasználó|Felhasználói licenc|
|1702 és újabb verziók|Igen|Eszköz|Eszköz-licenc|
|1702 és újabb verziók|Nem|Eszköz|Felhasználói licenc|

Mennyiségi programban vásárolt iOS-alkalmazásokkal kapcsolatos további információkért lásd: [mennyiségi programban vásárolt iOS-alkalmazások felügyelete](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

## <a name="direct-links-to-applications-in-software-center"></a>A Szoftverközpont elérhető alkalmazásokra mutató közvetlen hivatkozásokat

Mostantól megadhatja a végfelhasználók egy alkalmazást a Szoftverközpontban mutató közvetlen hivatkozást. Ez azt jelenti, hogy azok már nem kell nyissa meg a Szoftverközpontban, és keresse meg az alkalmazás azt telepítése előtt. Ez az csak a Configuration Manager alkalmazásokat, nem csomagok és programok és feladatütemezések érhető el.

### <a name="try-it-out"></a>Próbálja ki                 

A következő URL-formátum használatával nyissa meg a Szoftverközpont alkalmazások:

**Softwarecenter:SoftwareId =*alkalmazás azonosítója***

### <a name="how-to-get-the-application-identifier-of-an-application"></a>Hogyan kérhet egy alkalmazás azonosítója.

1.    A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.
2.    A szoftverkönyvtár munkaterületen bontsa ki a **Alkalmazáskezelés**, és kattintson a **alkalmazások**.
3.    Az a **alkalmazások** megtekintése, kattintson a jobb gombbal az oszlopfejlécre, és ezt követően, válassza ki a listáról **CI egyedi azonosító**. Látni fogja, hogy minden alkalmazáshoz egyedi azonosítója már megjelenik a listában.
4.    Megjegyzés: a **CI egyedi azonosító** adjon meg egy hivatkozást, például szeretné az alkalmazás: **ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f/2**
5.    Távolítsa el, az alkalmazás GUID, ebben az esetben a következő szöveg **/2**. Ez visszatérhet az alkalmazásazonosító.
6.    Végezetül hozhat létre, a hivatkozás befejezéséhez elé a **Softwarecenter:SoftwareID =**. A fenti példa használ, a végső kapcsolatot olvasását: **Softwarecenter:SoftwareId = ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f**.

Ez a hivatkozás segítségével a végfelhasználók is nyissa meg a Szoftverközpont közvetlenül a megadott alkalmazás.


## <a name="pfx-certificates-for-configuration-manager-windows-client-computers"></a>A Configuration Manager Windows-ügyfélszámítógépek számára a PFX-tanúsítványok

Most már telepítheti a Configuration Manager ügyfélszámítógépeken a Windows 10-es az importált PFX-tanúsítványprofilok.

### <a name="try-it-out"></a>Próbálja ki

Kövesse az utasításokat a [PFX-tanúsítványprofilok létrehozása](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) PFX-profil importálása, telepítse a profilt, és ellenőrizze, ha a tanúsítvány a célzott felhasználó részére lett-e telepítve.



## <a name="configure-azure-services-wizard"></a>Azure Services varázsló konfigurálása
Technical Preview-ban 1703 vezet be a **konfigurálása Azure-szolgáltatások** varázsló. A varázsló segítségével egy közös konfigurációs élményt nyújt a felváltja az egyes munkafolyamatok állíthatja be a felhőszolgáltatások használata a Configuration Managerrel. Ehhez használja az **Azure-webalkalmazásban** adja meg az előfizetés és a konfigurációs adatait, amely minden alkalommal, amikor egy új Configuration Manager összetevő vagy az Azure-bA állíthatja ellenkező esetben adja meg.

A technical preview 1703 vállalati (vállalati Windows Áruházbeli) csak a Windows áruház a varázsló segítségével konfigurálhatók.  Más felhőalapú szolgáltatásokat a külön munkafolyamatok használatával vannak konfigurálva.

-    A további információkat a jelen előzetes témakörben cserélje le a beállítási lépéseket használja a [üzleti szinkronizálási Windows áruház beállítása](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#set-up-windows-store-for-business-synchronization) az aktuális ág témakör [alkalmazások kezelése a System Center Configuration Managerrel a vállalati Windows áruházból](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

-    További információ a webalkalmazások: [hitelesítési és engedélyezési az Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-authentication-overview), és [webalkalmazások áttekintése](https://docs.microsoft.com/azure/app-service-web/app-service-web-overview).

### <a name="prerequisites-and-planning"></a>Előfeltételek és tervezése
Ha a Configuration Manager és a vállalati Windows áruházból közötti kapcsolat beállítása, meg kell adnia egy mappát, ahol a store-ból szinkronizált alkalmazástartalom tárolni fogja. Győződjön meg arról, hogy ez a mappa biztonságos, és, hogy a benne lévő tartalom eszközökre telepíthető, ellenőrizze az alábbi engedélyek legyenek érvényben:
-    A számítógépen, amelyre telepíti a szolgáltatás kapcsolódási pont helyrendszerszerepkör (a hierarchia legfelső szintű helye) rendelkeznie kell olvasási és írási engedéllyel a használatakor a megadott mappába a **számítógép$** fiók.  

-    Az alkalmazás szerzője olvasási engedélyekkel kell rendelkeznie a megadott mappába.  

-    A **számítógép$** minden SMS-szolgáltató példányát futtató számítógépen meg kell tudni használni a megadott mappát.

Az Azure Active Directoryban regisztrálja a Configuration Manager webalkalmazást vagy webes API-felügyeleti eszköz. Létrejön az ügyfél-azonosító, amely később szüksége lesz.

### <a name="use-the-wizard-to-configure-the-wsfb-cloud-service"></a>A varázsló segítségével a vállalati Windows Áruházbeli felhőszolgáltatás konfigurálása

1. Nyissa meg a a konzol **felügyeleti** > **áttekintése** > **felhőalapú szolgáltatások felügyeleti** > **Azure** > **Azure Services**, és válassza a **konfigurálása Azure-szolgáltatások** elindítani a **Azure Services varázsló**.

2. Az a **Azure Services** lapon, válassza ki a szolgáltatás konfigurálja, és kattintson a kívánt **következő**. Ebben az előzetes csak a vállalati Windows Áruházbeli konfigurálható.

3. A a **általános** lapján adjon meg egy rövid nevet a **Azure szolgáltatás neve** és egy leírást, és végül **következő**.

4. Az a **App** lapon adja meg az Azure környezetben, és kattintson a **Tallózás** a Server App-ablak megnyitásához.

5. Az a **Server alkalmazás** ablak, válassza ki a használni kívánt kiszolgáló alkalmazást, és végül **OK**.
Kiszolgálói alkalmazások az Azure-webalkalmazásokban, amelyek tartalmazzák az Azure-fiókjával, beleértve a bérlő azonosítója, az ügyfél-azonosító és a titkos kulcsot az ügyfelek konfigurációit is. Ha nincs elérhető kiszolgálói alkalmazások, használja az alábbiak egyikét:
  -    **Hozzon létre**: Új kiszolgálói alkalmazás létrehozásához kattintson a **létrehozása**. Adjon meg egy rövid nevet az alkalmazás és a bérlői. Ezt követően után bejelentkezés az Azure-ba, a Configuration Manager létrehozza a webalkalmazást az Azure-ban, beleértve az ügyfél-azonosító és a titkos kulcsot a webalkalmazásban való használatra. Később megtekintheti, ezek az Azure portálról.
  -    **Importálás**: A webes alkalmazás, amely már szerepel az Azure-előfizetéshez használatához kattintson **importálási**. Adjon meg egy rövid nevet az alkalmazás és a bérlői, és adja meg a bérlő azonosítója, ügyfél-azonosító és a titkos kulcsot, amelyet a Configuration Manager használatához Azure webalkalmazás számára. Miután **ellenőrizze** az adatokat, kattintson **OK** folytatja.  </br></br>

6. Tekintse át a **információk** lapon, és végezze el a további lépéseket és konfigurációk megfelelően. Ezek a konfigurációk szükségesek a szolgáltatás Configuration Managerrel együtt használni.
Ha például vállalati Windows Áruházbeli konfigurálása:

  1. Az Azure-ban kell regisztrálni a Configuration Manager webalkalmazást vagy webes API-t, és jegyezze fel az ügyfél-azonosítót. Is meg ügyfél kulcs a felügyeleti eszköz (amely a Configuration Manager).

  2.    A vállalati Windows Áruházbeli konzolon kell majd vásároljon legalább egy alkalmazást, az offline licencelt alkalmazások támogatásának engedélyezése és konfigurálása a Configuration Manager áruházi kezelőeszközként el.   </br>

  Kattintson a **következő** amikor készen áll a folytatáshoz.

7. Az a **App konfigurációk** lapon adja meg a app katalógus és a nyelvi beállításokat ezt a szolgáltatást, és kattintson a **következő**.
8. A varázsló befejezése után a Configuration Manager konzol jeleníti meg, hogy konfigurálta **vállalati Windows áruház** , egy **Cloud Service Type**.

Ezután már használhatja a hátralévő részét a [aktuális ág tartalom](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) szinkronizálása a vállalati Windows Áruházbeli alkalmazások kezelése, a hozzon létre és telepítheti és figyelheti a Windows Store üzleti alkalmazásokhoz.

### <a name="modify-a-cloud-service-configuration"></a>Egy felhőalapú szolgáltatás konfigurációjának módosítása
Megtekintheti, és konfigurációjának módosítása egy felhőalapú szolgáltatás tulajdonságainak szerkesztése.

Nyissa meg a a konzol **felügyeleti** > **áttekintése** > **felhőalapú szolgáltatások felügyeleti** > **Azure** > **Azure Services**, és válassza a **konfigurálása Azure-szolgáltatások**, jelöljön ki egy felhőalapú szolgáltatás, és válassza **tulajdonságok**.

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>A BIOS átalakítása UEFI helybeni frissítés során
Windows 10 Creators frissítés egy egyszerű átalakítás eszközt, amely automatizálja az UEFI-kompatibilis hardveres a merevlemez újraparticionálása folyamatát, és az átalakítás eszközzel integrálódik a Windows 7, Windows 10 helyi frissítési folyamat vezet be. Ha az eszköz együttesen az operációs rendszer frissítési feladatütemezés és az OEM-eszközt, amely a belső vezérlőprogram a BIOS UEFI alakítja, átválthat a számítógépek BIOS UEFI helyben frissítés a Windows 10 Creators frissítés során. További információkért lásd: [feladatütemezési lépéseket BIOS kezeléséhez UEFI alakításához](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

## <a name="collapsible-task-sequence-groups"></a>Az összecsukható feladatütemezési csoportok
Ebben a verzióban bontsa ki és csukja össze a feladatütemezési csoportok vezet be. Bontsa ki és csukja össze az egyes csoportok vagy kibontása vagy összecsukása egyszerre az összes csoport.


## <a name="client-settings-to-configure-windows-analytics-for-upgrade-readiness"></a>Ügyfélbeállítások konfigurálása Windows Analytics készültségi frissítése
Ebben a verzióban kezdve segítségével eszköz ügyfélbeállításait leegyszerűsítheti a konfigurációt a Windows használatához szükséges telemetriai adatot [Windows Analytics](https://www.microsoft.com/en-us/WindowsForBusiness/windows-analytics) megoldások, például [frissítési készültségének](/sccm/core/clients/manage/upgrade/upgrade-analytics) a Configuration Managerrel. A Configuration Manager adatainak lekérése is, amely a környezetben, az ügyfélszámítógépek által jelentett Windows telemetriai adatok alapján a jelenlegi állapotának értékes betekintést nyújt a Windows Analytics. A Windows telemetriai adatokat a Windows telemetriai szolgáltatás ügyfél számítógépek által jelentett, és majd a vonatkozó adatokat később továbbítják, amelyek a szervezet OMS-munkaterület egyik Windows elemzési megoldásokat. Frissítési készültségének egy Windows elemzési megoldások, amelyik segíthet a Windows-frissítések a kezelt eszközök döntéseket rangsorolására.

Windows telemetriai beállításaival kapcsolatos további információkért lásd: [a szervezet Windows beállítása telemetriai](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).

### <a name="prerequisites"></a>Előfeltételek
- Konfigurálnia kell a helyet használja a frissítési készültségének felhőalapú szolgáltatás. További információ: [készültségi frissítése](/sccm/core/clients/manage/upgrade/upgrade-analytics)

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics ügyfélbeállítások konfigurálása
Konfigurálja a Windows Analytics, a Configuration Manager konzolon lépjen **felügyeleti** > **ügyfélbeállítások**, kattintson duplán a **egyéni ügyfél-Eszközbeállítás létrehozása** , majd ellenőrizze **Windows Analytics**.  

Ezt követően konfigurálja a következő követően navigáljon a **Windows Analytics** beállítások lapján:
- **Kereskedelmi azonosítója**  
A kereskedelmi azonosító kulcs leképezi a szervezet Windows Analytics adatokat tároló OMS-munkaterület a kezelt eszközökről információk. Ha a frissítési készültségének kereskedelmi azonosító kulcs már beállította, használja a azzal az azonosítóval. Ha még nem rendelkezik egy kereskedelmi azonosító kulcs, lásd: [a kereskedelmi azonosító kulcs létrehozása]( https://technet.microsoft.com /itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key).

- Állítsa be a **Telemetriai szint a Windows 10-eszközök**   
További információ az egyes Windows 10 telemetriai szinteken gyűjtött adatok: [a szervezet Windows beállítása telemetriai]( https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels).

- Válassza ki a **részt kereskedelmi forgalomban beszerezhető adatok gyűjtése a Windows 7, 8, 8.1-eszközökön**   
Az adatokkal kapcsolatos információkat gyűjti a program ezen operációs rendszerekből Ön részt, lásd: Töltse le a [appraiser telemetriai események Windows 7, Windows 8 és Windows 8.1 és a mezők](https://go.microsoft.com/fwlink/?LinkID=822965) Microsoft PDF-fájl.

- **Internet Explorer adatgyűjtésének konfigurálását** vagy korábbi Windows 8.1 rendszerű eszközökön, az Internet Explorer adatgyűjtés lehetővé teheti a frissítés készültségi észleléséhez web app inkompatibilitási problémák, amelyek megakadályozzák a zökkenőmentes frissítés Windows 10-re. Az Internet Explorer adatgyűjtés engedélyezhető egy internet zóna szintjén száma. Internet zóna kapcsolatos további információkért lásd: [kapcsolatos URL-cím biztonsági zónák](https://msdn.microsoft.com/en-us/library/ms537183(v=vs.85).aspx).
