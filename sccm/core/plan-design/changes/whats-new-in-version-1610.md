---
title: "Új verzió 1610 |} Microsoft Docs"
description: "Ezzel adatokat kapjon módosítások és a System Center Configuration Manager 1610 verziójában bevezetett új képességekkel rendelkezik."
ms.custom: na
ms.date: 11/23/2016
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7eb0803-3f8f-4ab6-825a-99ac11f5ba7d
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 831d8a66c827d246069c7415cdce7a7c4bb95b33
ms.openlocfilehash: 19e3099773f887129374413482702de3f4b0a36f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1610-of-system-center-configuration-manager"></a>Mi &#39; verzió 1610 a System Center Configuration Manager újdonságai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1610 frissítése a System Center Configuration Manager aktuális ága 1511-es, a 1602-es vagy 1606 verzióját futtató már telepített helyeken a konzolon belüli frissítésként érhető el.


> [!TIP]  
> Új hely telepítése egy alapkonfigurációt a Configuration Manager kell használnia.  
>  További információ:    
>  -   [Új helyek telepítése](https://technet.microsoft.com/library/mt590197.aspx)  
>  -   [Helyfrissítések telepítése](https://technet.microsoft.com/library/mt607046.aspx)  
>  -   [Alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

A következő szakaszok részletesen bemutatják a módosításokat, és a Configuration Manager 1610 verziójában bevezetett új képességekkel rendelkezik.  


## <a name="in-console-monitoring-of-update-installation-status"></a>A konzolon belüli frissítés telepítési állapotának figyelése  
Verziójától 1610, ha egy frissítési csomagot telepíti, és figyelje a telepítés, a konzolon, egy új fázisa van: **A telepítés után**. Ebben a fázisban a feladatokat, például, hogy fontos szolgáltatások és a replikáció figyelése inicializálását újraindítása állapotát. (Ebben a fázisban nem érhető el a konzol verzióra 1610 a hely frissítése után.) További információ a frissítés telepítési állapotát: [konzolon belüli frissítések telepítése](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).


## <a name="exclude-clients-from-automatic-upgrade"></a>Ügyfelek kizárása az automatikus frissítés
Windows-ügyfelek kizárása első frissítik az ügyfélszoftver új verzióját. Ehhez az szükséges, az ügyfélszámítógépek ki lesznek zárva a frissítés megadott gyűjtemény tartalmazza. A kizárt gyűjtemény ügyfelei figyelmen kívül hagyja a kérelmek az ügyfélszoftver frissítéséhez.  További információkért lásd: [frissítések kizárása Windows ügyfelek](../../clients/manage/upgrade/exclude-clients-windows.md).


## <a name="improvements-for-boundary-groups"></a>A határcsoportok fejlesztései
1610 tartalmazza az fontos változások a határcsoportokat és a leírás és a terjesztési pontokról. Ezek a változások jobban vezérelheti, hogyan és mikor mutat-e további terjesztési kereséséhez ügyfelek tartalék tartalomforrás helyként miközben egyszerűbbé teheti a tartalmi infrastruktúra tervezési. Ez magában foglalja, mind a helyszíni és felhőalapú terjesztési pontok.
Ezek a fejlesztések cserélje le a fogalmakat és viselkedéshez, előfordulhat, hogy ismeri a (például a gyors vagy lassú terjesztési pontok konfigurálása). Az új modell beállításához és karbantartásához könnyebben lehet. Ezek a változások szintén meghatározza a jövőbeli változásokról, melyek más helyrendszerszerepköröket, határcsoporthoz hozzárendel javítja az áttelepítés.

Ha 1610 verzióra frissíti, a frissítés az aktuális határcsoportok konfigurációiról megfelelően az új modell, így ezek a változások ne zavarja meg a meglévő tartalom terjesztése konfigurációk alakítja át.

További információkért lásd: [határcsoportok](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-groups).


## <a name="peer-cache-for-content-distribution-to-clients"></a>A tartalmak terjesztéséhez, az ügyfelek számára társ-gyorsítótárazás
Kezdő 1610 verziójával, az ügyfél **társ-gyorsítótárazás** segítségével felügyelheti a tartalom távoli ügyfelek központi telepítését. Társ-gyorsítótárazás egy olyan beépített Configuration Manager megoldás az ügyfelek számára a más ügyfelek számára, közvetlenül a helyi gyorsítótárból.

Miután ügyfélbeállítások, amelyek lehetővé teszik a társ-gyorsítótárazás egy gyűjteményhez, tagjai működhet társ tartalomforrásként más ügyfelek számára az ugyanahhoz a határcsoporthoz.

Is használhatja az új **Ügyféladatforrások** irányítópult társ-gyorsítótárazás tartalomforrások környezetében használatának megértése.

> [!TIP]  
> Verziójával 1610 a társ-gyorsítótárazás és a Ügyféladatforrások irányítópult előzetes kiadású szolgáltatások. Engedélyezheti a őket [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

További információkért lásd: [Configuration Manager-ügyfelek számára társ-gyorsítótárazás](/sccm/core/plan-design/hierarchy/client-peer-cache), és [Ügyféladatforrások irányítópult](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).


## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Egyszerre több megosztott terjesztési pont áttelepítése
Ezután már használhatja is **terjesztési pont ismételt hozzárendelése** kell rendelkeznie a Configuration Manager-folyamat az újbóli hozzárendelésre, legfeljebb 50 párhuzamosan megosztott terjesztési pontok egy időben. Ez a kiadás előtt a máshoz hozzárendelt terjesztési pontok álltak feldolgozott egyszerre csak egy. További információ: [egyszerre több megosztott terjesztési pont áttelepítése](/sccm/core/migration/planning-a-content-deployment-migration-strategy#migrate-multiple-shared-distribution-points-at-the-same-time).

## <a name="cloud-management-gateway-for-managing-internet-based-clients"></a>Felügyeleti átjáró az internetes ügyfelek kezelése

Felügyeleti átjáró kezelése a Configuration Manager-ügyfelek az interneten lévő egyszerű módszert kínál. A felhő felügyeleti átjáró szolgáltatást, amely a Microsoft Azure telepít, és az Azure-előfizetés szükséges, a helyi Configuration Manager-infrastruktúrát, a felhő felügyeleti átjáró csatlakozási pont nevű új szerepkör alapján csatlakozik. Miután a teljes mértékben telepítve és konfigurálva, ügyfelek kommunikálhatnak a helyi Configuration Manager helyrendszer-szerepkörök és a felhő alapú terjesztési pontok, függetlenül attól, hogy van csatlakoztatva a belső magánhálózaton vagy az interneten. További információt, és hogyan Internet alapú ügyfélfelügyelethez felhőalapú adatkezelési átjáró összehasonlítja megtekintéséhez lásd: [az interneten lévő ügyfelek kezelése](/sccm/core/clients/manage/manage-clients-internet).

## <a name="improvements-to-the-windows-10-edition-upgrade-policy"></a>A Windows 10-kiadás frissítési szabályzatának változásai
Ebben a kiadásban a következő fejlesztéseken ment az ezt a házirendtípus:

- A Kiadásfrissítési házirend most futtassa a Configuration Manager-ügyfél mellett a Windows 10 rendszerű regisztrált a Microsoft Intune-nal, a Windows 10 rendszerű számítógépeken használható.
- A varázsló a platformokat, amelyek kompatibilisek-e a hardver egyik a Windows 10 Professional frissíthető.

## <a name="manage-hardware-identifiers"></a>Hardverazonosítók kezelése
Mostantól megadhatja a hardverek azonosítókat, a Configuration Manager céljából PXE rendszerindítás és az ügyfélregisztráció során figyelmen kívül hagyja. Van két olyan gyakori problémákat, amelyek a cím segítségével:

1. Számos eszközön, például a Surface Pro 3, nem tartalmaznak olyan beépített Ethernet port. Egy USB-Ethernet adapter szolgál az operációs rendszer telepítése céljából vezetékes kapcsolatot létesíteni. Azonban költségek és általános használhatóság miatt ezek a gyakran megosztott adapterek. Ez az adapter MAC-címét az eszköz azonosítására szolgál, mert további felügyeleti műveletek közötti minden egyes központi telepítés nélkül problematikus újból felhasználja az adapter lesz. Most már a Configuration Manager verziója 1610, kizárhatja Ez az adapter MAC-címét, hogy könnyen felhasználhatók ebben a forgatókönyvben.
2. Az SMBIOS azonosító egy egyedi hardverazonosító várt, de néhány speciális hardvereszközök ismétlődő azonosítójú épülnek. A probléma nem lehet a közös, mint az imént leírt USB-Ethernet adapter eset, de kizárt hardverazonosítóinak lista használatával lehet oldani.

További információkért lásd: [kezelése ismétlődő hardverazonosítók](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Fejlesztések a Windows Áruházra mutató integráció a vállalati és a Configuration Managerben
Ebben a kiadásban változásai:
- Csak telepíthet korábban, a vállalati Windows áruházból származó ingyenes alkalmazások. A Configuration Manager most emellett támogatja a telepítését online fizetett licenccel rendelkező alkalmazásokat (csak Intune-ban regisztrált eszközök esetén).
- Most kezdeményezheti az azonnali szinkronizálás a vállalati Windows áruház és a Configuration Manager között.
- Mostantól módosíthatja az Azure Active Directory beszerzett titkos ügyfélkulcsot.
- Törölheti a tároló-előfizetéssel.

További információkért lásd: [alkalmazások kezelése a System Center Configuration Managerrel a vállalati Windows áruházból](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


## <a name="policy-sync-for-intune-enrolled-devices"></a>Házirend-szinkronizálás Intune-ban regisztrált eszközök
A házirend-szinkronizálást az Intune-ban regisztrált eszközök a most már a Configuration Manager konzol helyett kellene szinkronizálási kérhet a eszközökön a vállalati portál alkalmazást is kérhet. Szinkronizálási kérelem állapotadatokat érhető el az eszköz nézetek nevű új oszlopként **távoli szinkronizálási állapotának**. Az információ is rendelkezésre áll a felderítési adatok szakaszában a **tulajdonságok** az egyes eszközök párbeszédpanel.
További információkért lásd: [távolról szinkronizálása az Intune-ban regisztrált eszközökön a Configuration Manager konzoljáról házirend](/sccm/mdm/deploy-use/sync-intune-device).


## <a name="use-compliance-settings-to-configure-windows-defender-settings"></a>Megfelelőségi beállítások segítségével a Windows Defender beállításainak konfigurálása
A Windows Defender-ügyfél beállításai az Intune-ban regisztrált Windows 10 számítógépek konfigurációs elemek a Configuration Manager konzol segítségével mostantól beállíthatja.
További információkért lásd: a **Windows Defender** szakasz [a System Center Configuration Manager-ügyfél nélkül felügyelt Windows 8.1 és Windows 10-eszközökhöz hozzon létre konfigurációelemek](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).



## <a name="general-improvements-to-software-center"></a>Általános fejlesztések a szoftverközpont
- Felhasználók mostantól kérhetnek az alkalmazások Szoftverközpontban, valamint az Alkalmazáskatalógust.
- Hogy megértse, mely szoftverek új és fontos felhasználók fejlesztései.

## <a name="new-columns-in-device-collection-views"></a>Új oszlopok eszköz gyűjteménynézetek társítása
Most jelenítheti meg az oszlopok **IMEI** és **sorozatszám** (csak iOS-eszközökön) az eszköz gyűjteménynézetek társítása.
További részletekért lásd: [előzetes deklarálása IMEI- vagy iOS-sorozatszámokat eszközök](https://docs.microsoft.com/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id).

## <a name="customizable-branding-for-software-center-dialogs"></a>Testre szabható branding Szoftverközpont párbeszédpanelek
A Szoftverközpont egyéni branding jelent meg a Configuration Manager 1602-es verzióját. Verzióban 1610 adott márkajelzési kiterjesztettük a Szoftverközpont számára egységesebb nyújtása összes társított párbeszédpanelt.

A Szoftverközpont egyéni branding a következő szabályok szerint alkalmazza:

- Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre nincs telepítve, akkor a Szoftverközpont a szervezet nevét jeleníti meg a **Számítógépügynök** ügyfélbeállítás **a Szoftverközpontban megjelenített név**. Útmutatásért lásd: [ügyfélbeállítások konfigurálása](../../clients/deploy/configure-client-settings.md).

- Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre telepítve van, akkor a Szoftverközpont jeleníti meg a szervezet nevét és az Alkalmazáskatalógus weboldal-elérési pont helykiszolgáló-szerepkörének tulajdonságaiban megadott színt. További információkért lásd: [Alkalmazáskatalógus weboldal-elérési pontjának konfigurációs beállításait](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#Application-Catalog-website-point).

- Ha a Microsoft Intune-előfizetés konfigurálva, és a Configuration Manager környezethez csatlakozik, majd a Szoftverközpont jeleníti meg a szervezet neve, a színt és a vállalati embléma, az Intune-előfizetés tulajdonságai megadott. További információ: [A Windows Intune-előfizetés konfigurálása](/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription).


## <a name="enforcement-grace-period-for-required-application-and-software-update-deployments"></a>Végrehajtási türelmi időszak a szükséges alkalmazások és szoftverfrissítések központi telepítésére
Bizonyos esetekben előfordulhat, hogy szeretné telepíteni a szükséges alkalmazások központi telepítéseit vagy szoftverfrissítések bármely beállítása határidők túl további időt hagy a felhasználók. Például ez lehet szükség, ha ki van kapcsolva a számítógép hosszabb ideig, és számos alkalmazás vagy frissítés központi telepítéséhez szükséges. Például ha a felhasználó csak adott vissza a szabadsága, előfordulhat, hogy rendelkeznek long vár, amíg a lejárt alkalmazásként telepíti a központi telepítések. Ez a probléma megoldásához most definiálhat egy kényszerítési türelmi időszak gyűjteményhez a Configuration Manager ügyfél beállítások telepítésével. 

A türelmi időszak konfigurálásához hajtsa végre a következő műveleteket:
1.      Az a **Számítógépügynök** lap, az ügyfélbeállítások konfigurálása az új tulajdonság **türelmi idő a kényszerítésre a telepítés utáni határidő (óra)** közötti értékű **1** és **120** óra.
2.      Szükséges alkalmazás új központi telepítést, vagy egy létező központi telepítés tulajdonságait a a **ütemezés** lapján jelölje be a jelölőnégyzetet **felhasználói beállítások szerint, legfeljebb az ügyfélbeállításokban megadott türelmi idő a telepítés kényszerítésének késleltetés**. Minden telepítés esetén, amelyek a jelölőnégyzet be van jelölve, és az eszközök számára is telepítve az ügyfél-eszközbeállítást, célozzák meg fogja használni a kényszerítési türelmi időszak.

Konfigurálja a kényszerítési türelmi időszak, és jelölje be a jelölőnégyzetet, az alkalmazás telepítési határidő elérésekor, ha telepítve az első nem üzleti ablak, amely a felhasználó és a türelmi időszak konfigurált történik. A felhasználó azonban továbbra is nyissa meg a Szoftverközpont és telepítheti az alkalmazást szeretnék bármikor. A türelmi időszak lejárta után a kényszerítési visszatér a lejárt központi telepítések elvégzéséhez ezek normál viselkedése. Hasonló beállítások érhetőek el a szoftverfrissítések központi telepítési varázsló, az automatikus központi telepítési szabályok varázslóban és a Tulajdonságok lap.



## <a name="improved-functionality-in-dialog-boxes-about-required-software"></a>A párbeszédpanelek szükséges szoftverekkel kapcsolatos továbbfejlesztett funkciók
A felhasználó WWhen kap kötelező szoftverek, a **emlékeztet és Emlékeztessen:** beállítást, és kiválaszthatja, melyik értékeket az alábbi legördülő listából: 
- **Később**. Meghatározza, hogy értesítések ütemezett az Ügyfélügynök az értesítési beállítások alapján.
- **Rögzített ideje**. Meghatározza, hogy az értesítés megjelenítése a kijelölt időszak (például a 30 perc) után ütemezi.

![Az Ügyfélügynök számítógép lap](media/client-notification-settings.png)

A maximális időtartamot a ügyfélügynökében beállított értesítési értékek alapul. Például ha a **központi telepítés határideje 24 óránál közelebbi, emlékeztesse a felhasználók (óránként)** a Számítógépügynök beállítása lap 10 óra van konfigurálva és a határidő előtt 24 óránál hosszabb, a felhasználó emlékeztető lehetőségekkel, de soha nem több mint 10 óra jelenik meg. Megközelíti a határidő lejártakor, kevesebb beállítás rendszer is elérhető, a megfelelő az egyes összetevők a központi telepítés ütemterv ügyfélügynökében konzisztens.

Magas kockázatú telepítés például az operációs rendszert központilag telepítő feladatütemezés a felhasználói értesítés élmény pedig most a leginkább zavaró beavatkozás. Helyett egy átmeneti értesítési, minden alkalommal, amikor a felhasználó értesítést kap, hogy a kritikus szoftverkarbantartást kell megadni egy párbeszédpanel a következő jelennek meg a felhasználó például:

![Szükséges szoftverek párbeszédpanel](media/client-toast-notification.png)


További információ:
- [Magas kockázatú központi telepítések felügyeletéhez szükséges beállítások](../../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Ügyfélbeállítások konfigurálása](../../clients/deploy/configure-client-settings.md)

## <a name="software-updates-dashboard"></a>Szoftver frissítések irányítópult
Az új szoftverfrissítési frissítések Irányítópult segítségével megtekintheti az eszközök aktuális megfelelőségi állapotát a szervezetben, és gyorsan elemezheti az adatokat, mely eszközök vannak kitéve. Az irányítópult megtekintéséhez lépjen **figyelés** > **áttekintése** > **biztonsági** > **szoftver frissítések irányítópult**.

További információkért lásd: [szoftverfrissítések figyelése](/sccm/sum/deploy-use/monitor-software-updates).


## <a name="improvements-to-the-application-request-process"></a>Az alkalmazás folyamat fejlesztései
Telepítési iránti kérelem jóváhagyását követően dönthet úgy, ezt követően visszautasítja a kérelmet kattintva **Megtagadás** a Configuration Manager konzolon. Korábban erre a gombra kattintva lett szürkén jelenik meg jóváhagyást követően.

Ez a művelet nem okoz azokat az eszközöket, a rendszer eltávolítja az alkalmazást. Azonban akkor állítsa le a felhasználókat az alkalmazás új példánya a Szoftverközpontból.

## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>A szűrőt az automatikus központi telepítési szabályokat a tartalom mérete alapján
Most már a szoftverfrissítések automatikus központi telepítési szabályokat a tartalom mérete alapján szűrhet. Például csak a 2 MB-nál kisebb méretű szoftverfrissítéseket töltheti le, beállíthatja a **tartalom mérete (KB)** kiszűrik **< 2048**. Szűrővel megakadályozza, hogy nagy szoftverfrissítések automatikus letöltés, amely jobb támogatja egyszerűsített karbantartását, ha hálózati sávszélessége korlátozott régebbi verziójú Windows. További információkért lásd:
- [Configuration Manager és az egyszerűsített a Windows karbantartási a lefelé szintű operációs rendszerek](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)
- [Szoftverfrissítések automatikus központi telepítése](/sccm/sum/deploy-use/automatically-deploy-software-updates)

Konfigurálhatja a **tartalom mérete (KB)** mezőben, tegye a következők egyikét:
- Lépjen az automatikus központi telepítési szabály létrehozása varázslóban egy automatikus központi telepítési szabály létrehozásakor a **szoftverfrissítések** lap.
- Egy meglévő automatikus központi telepítési szabály tulajdonságaiban, navigáljon a **szoftverfrissítések** fülre.

## <a name="office-365-client-management-dashboard"></a>Az Office 365-ügyfél kezelési irányítópult
Az Office 365-ügyfél kezelési irányítópult már elérhető a Configuration Manager konzolon. Az irányítópult megtekintéséhez lépjen **szoftverkönyvtár** > **áttekintése** > **Office 365-ügyfél kezelése**.

Az irányítópult a következő diagramot jelenít meg:

- Office 365-ügyfelek száma
- Az Office 365-ügyfél verziója
- Az Office 365 ügyfélnyelveket
- Az Office 365-ügyfél csatornák     

További információkért lásd: [Office 365 ProPlus kezelése frissíti](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Feladatütemezési lépések UEFI alakításához BIOS kezelése
Most testre egy operációs rendszer központi telepítésének feladatütemezése új változó TSUEFIDrive, így a **számítógép újraindítása** lépés való áttérés UEFI a merevlemez-meghajtón FAT32 partíció készítse elő. A következő eljárás azt mutatja, hogyan hozhat létre feladatütemezési lépések a merevlemez-meghajtó előkészítése a BIOS UEFI alakításához. További információkért lásd: [feladatütemezési lépéseket BIOS kezeléséhez UEFI alakításához](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion).

##  <a name="improvements-to-the-task-sequence-step-prepare-configmgr-client-for-capture"></a>A feladatütemezési lépés fejlesztései: Prepare ConfigMgr Client for Capture  
A ConfigMgr-ügyfél előkészítése a lépést most is teljesen eltávolítja a Configuration Manager-ügyfél csak a fontos információk eltávolítása helyett. Amikor a feladatütemezés a rögzített operációsrendszer-lemezképet telepíti, akkor telepíti egy új Configuration Manager-ügyfél minden alkalommal, amikor. További információkért lásd: [feladatütemezési lépéseket](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture).



## <a name="intune-compliance-policy-charts"></a>Intune megfelelőségi házirend diagramok
Most már az eszközök összesített megfelelőségének áttekintő képet kaphat, és a felső okai a meg nem felelés, az új diagramok használatával a **figyelés** munkaterület a Configuration Manager konzolon. Kattintson a diagram kategória eszközöket lebontva szakaszt. További információkért lásd: [a megfelelőségi házirend megfigyelése](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="lookout-integration-for-hybrid-implementations-to-protect-ios-and-android-devices"></a>A lookout integrációs hibrid megvalósítások iOS és Android-eszközök védelme
Microsoft van integrálása a Lookout tartozó mobil fenyegetés adatvédelmi megoldást iOS és Android rendszerű mobileszközök védi meg kártevő szoftverek, kockázatos alkalmazásokat, és több, az eszközökön. A lookout megoldással konfigurálható fenyegettségi szint határozza meg. A megfelelőségi házirend szabályai a System Center Configuration Manager meghatározásához az eszköznek meg kell felelnie a Lookout a kockázatbecslés alapján hozhat létre. Feltételes hozzáférési házirendekkel engedélyezi vagy letiltja az eszköz megfelelőségi állapota alapján a vállalati erőforrásokhoz való hozzáférést. Az integráció és annak működéséről, lásd: [kezelése eszköz, hálózati és alkalmazás kockázat alapján](/sccm/protect/deploy-use/manage-access-based-on-device-network-app-risk).

Nem megfelelő iOS-eszközök felhasználói regisztrálását kéri. Keressen olyan munkahelyi alkalmazás telepítése az eszközökön, aktiválja az alkalmazást, és szervizelheti azokat a fenyegetéseket, keressen olyan munkahelyi alkalmazás ahhoz, hogy hozzáférjenek a vállalati adatok jelentett szükség lesz. Megtudhatja, hogyan [konfigurálása és telepítése a Lookout munkahelyi alkalmazásokat](/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps).



## <a name="new-compliance-settings-for-configuration-items"></a>Új megfelelőségi beállítások a konfigurációs elemek
A konfigurációelemek használható különböző eszközplatformok számos új beállításokat a rendszer. Ezek a beállítások, amelyek korábban már létezett a Microsoft Intune önálló konfigurációban, és most már elérhető a Configuration Manager Intune használatakor.
További információkért lásd: [a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt eszközök konfigurációelemei](/sccm/compliance/deploy-use/configuration-items-for-devices-managed-without-the-client).

### <a name="new-settings-for-android-devices"></a>Új beállítások az Android-eszközök
#### <a name="password-settings"></a>Jelszóbeállítások
- **Korábbi jelszavak megjegyzése**
- **Ujjlenyomat használatának engedélyezése zárolásának feloldásához**

#### <a name="security-settings"></a>Biztonsági beállítások
- **Tárolókártyák titkosításának kötelezővé tétele**
- **Képernyőfelvétel-készítés engedélyezése**
- **Diagnosztikai adatok küldésének engedélyezése**

#### <a name="browser-settings"></a>Webböngésző beállításai
- **Webböngésző engedélyezése**
- **Automatikus kitöltés engedélyezése**
- **Előugróablak-blokkoló engedélyezése**
- **Cookie-k engedélyezése**
- **Active scripting engedélyezése**

#### <a name="app-settings"></a>Alkalmazásbeállítások
- **Google Play áruház engedélyezése**

#### <a name="device-capability-settings"></a>Eszközképességek beállításai
- **Cserélhető tároló engedélyezése**
- **Wi-Fi alapú internetmegosztás használatának engedélyezése**
- **Földrajzi hely meghatározásának engedélyezése**
- **NFC használatának engedélyezése**
- **Bluetooth használatának engedélyezése**
- **Hangroaming engedélyezése**
- **Adatroaming használatának engedélyezése**
- **SMS-és MMS engedélyezése**
- **Beszédfelismerés használatának engedélyezése**
- **Hangtárcsázás engedélyezése**
- **Másolás és Beillesztés engedélyezése**

### <a name="new-settings-for-ios-devices"></a>Új beállítások az iOS-eszközök
#### <a name="password-settings"></a>Jelszóbeállítások
- **A jelszóban megkövetelt speciális karaktereinek számát**
- **Egyszerű jelszavak engedélyezése**
- **Ennyi perc inaktivitás után kell jelszót beírni**
- **Korábbi jelszavak megjegyzése**

### <a name="new-settings-for-mac-os-x-devices"></a>Új beállítások Mac OS X rendszerű eszközökhöz
#### <a name="password-settings"></a>Jelszóbeállítások
- **A jelszóban megkövetelt speciális karaktereinek számát**
- **Egyszerű jelszavak engedélyezése**
- **Korábbi jelszavak megjegyzése**
- **Tétlenség után képernyőkímélő bekapcsolása ennyi perc**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Windows 10 asztali és mobil eszközök új beállításai
#### <a name="password-settings"></a>Jelszóbeállítások
- **Karakterkészletek minimális száma**
- **Korábbi jelszavak megjegyzése**
- **Jelszó kérése, amikor az eszköz visszatér inaktív állapotból**

#### <a name="security-settings"></a>Biztonsági beállítások
- **Mobileszköz titkosításának kötelezővé tétele**
- **Regisztráció manuális törlésének engedélyezése**

#### <a name="device-capability-settings"></a>Eszközképességek beállításai
- **VPN engedélyezése mobilhálózaton**
- **Engedélyezése mobilhálózati roaming VPN**
- **Telefon alaphelyzetbe állításának engedélyezése**
- **USB-kapcsolat engedélyezése**
- **A Cortana engedélyezése**
- **Műveletközponti értesítések engedélyezése**

### <a name="new-settings-for-windows-10-team-devices"></a>Új beállítások a Windows 10 Team rendszerű eszközökhöz
#### <a name="device-settings"></a>Eszközbeállítások
- **Azure Operational Insights engedélyezése**
- **Miracast vezeték nélküli vetítés**
- **Az üdvözlőképernyőn megjelenő értekezletadatok kiválasztása**
- **Zárolási képernyő háttérképének URL-címe**

### <a name="new-settings-for-windows-81-devices"></a>Windows 8.1-eszközök új beállításai
#### <a name="applicability-settings"></a>Alkalmazhatósági beállítások
- **Az összes konfiguráció alkalmazása a Windows 10**

#### <a name="password-settings"></a>Jelszóbeállítások
- **Jelszó kötelező típusa**
- **Karakterkészletek minimális száma**
- **Jelszó minimális hossza**
- **Ismétlődő sikertelen bejelentkezés az eszközön tárolt adatok törléséig való száma**
- **Ennyi perc tétlenség képernyő kikapcsolása**
- **Jelszó lejárata (nap)**
- **Korábbi jelszavak megjegyzése**
- **Korábbi jelszavak újbóli használatának tiltása**
- **Képjelszó és PIN-kód engedélyezése**

#### <a name="browser-settings"></a>Webböngésző beállításai
- **Intranetes hálózatok automatikus felderítésének engedélyezése**

### <a name="new-settings-for-windows-phone-81-devices"></a>Új beállítások a Windows Phone 8.1 rendszerű eszközökhöz
#### <a name="applicability-settings"></a>Alkalmazhatósági beállítások
- **Az összes konfiguráció alkalmazása a Windows 10**

#### <a name="password-settings"></a>Jelszóbeállítások
- **Karakterkészletek minimális száma**
- **Egyszerű jelszavak engedélyezése**
- **Korábbi jelszavak megjegyzése**

#### <a name="device-capability-settings"></a>Eszközképességek beállításai
- **Wi-Fi elérési pontokhoz való automatikus csatlakozás engedélyezése**

