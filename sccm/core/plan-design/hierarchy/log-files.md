---
title: "Naplófájlok a Configuration Manager |} Microsoft Docs"
description: "Problémák a System Center Configuration Manager hierarchia naplófájlokat használ."
ms.custom: na
ms.date: 3/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1ff371e-b0ad-4048-aeda-02a9ff08889e
caps.latest.revision: 9
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b991b4ea27e66c233b04f8e65a412404521d89a6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="log-files-in-system-center-configuration-manager"></a>Naplófájlok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben, ügyfél és a helykiszolgáló összetevő a folyamatadatokat külön naplófájlba. Használhatja az információkat a naplófájlokban segítséget nyújthatnak a Configuration Manager hierarchiájában előforduló problémák megoldásában. Alapértelmezés szerint az ügyfél és a helykiszolgáló összetevő naplózása engedélyezve van a Configuration Manager alkalmazásban.   

 A következő szakaszok részletesen bemutatják a különböző naplófájlokat elérhetővé Önnek. Az ismertetés alapján megtekintheti és figyelése a Configuration Manager-ügyfél és a kiszolgáló naplóiban használhatja a működési részleteket, és hiba azonosításához, amelyek segíthetnek információk elhárításában.  

-   [A Configuration Manager naplófájljainak áttekintése](#BKMK_AboutLogs)  

    -   [Naplózási beállítások konfigurálása a Configuration Manager Service Manager használatával](#BKMK_LogOptions)  

    -   [A Configuration Manager naplóinak helye](#BKMK_LogLocation)  

-   [A Configuration Manager ügyfeleinek naplói](#BKMK_ClientLogs)  

    -   [Ügyfélműveletek](#BKMK_ClientOpLogs)  

    -   [Ügyfél-telepítési naplófájlok](#BKMK_ClientInstallLog)  

    -   [A Linux és UNIX-ügyfél](#BKMK_LogFilesforLnU)  

    -   [Mac számítógépeken futó ügyfele](#BKMK_LogfilesforMac)  

-   [A Configuration Manager helykiszolgáló naplófájljai](#BKMK_ServerLogs)  

    -   [Helyrendszer-kiszolgáló és a helyrendszer-kiszolgáló naplói](#BKMK_SiteSiteServerLog)  

    -   [Helykiszolgáló telepítési naplófájljai](#BKMK_SiteInstallLog)  

    -   [Tartalék állapotkezelő pont naplófájlok](#BKMK_FSPLog)  

    -   [Felügyeleti pont naplófájlok](#BKMK_MPLog)  

    -   [Szoftverfrissítési pont napló fájlokat](#BKMK_SUPLog)  

-   [A Configuration Manager funkcióihoz tartozó naplófájlok](#BKMK_FunctionLogs)  

    -   [Alkalmazáskezelés](#BKMK_AppManageLog)  

    -   [Eszközintelligencia](#BKMK_AILog)  

    -   [Biztonsági mentés és helyreállítás](#BKMK_BnRLog)  

    -   [Tanúsítványigénylés](#BKMK_CertificateEnrollment)

    -   [Ügyfélértesítés](#BKMK_BGB)

    -   [Felügyeleti átjáró](#cloud-management-gateway)

    -   [A megfelelőségi beállítások és hozzáférés a vállalati erőforrásokhoz](#BKMK_CompSettingsLog)  

    -   [A Configuration Manager konzol](#BKMK_ConsoleLog)  

    -   [Tartalomkezelés](#BKMK_ContentLog)  

    -   [Felderítés](#BKMK_DiscoveryLog)  

    -   [Az Endpoint Protection](#BKMK_EPLog)  

    -   [Bővítmények](#BKMK_Extensions)  

    -   [Szoftverleltár](#BKMK_InventoryLog)  

    -   [Szoftverhasználat-mérő](#BKMK_MeteringLog)  

    -   [Áttelepítés](#BKMK_MigrationLog)  

    -   [Mobileszközök](#BKMK_MDMLog)  

    -   [Operációs rendszer központi telepítése](#BKMK_OSDLog)  

    -   [Energiagazdálkodás](#BKMK_PowerMgmtLog)  

    -   [Távvezérlés](#BKMK_RCLog)  

    -   [Jelentéskészítés](#BKMK_ReportLog)  

    -   [Szerepkör alapú felügyelet](#BKMK_RBALog)  

    -   [Szolgáltatáskapcsolódási pont](#BKMK_WITLog)  

    -   [Szoftverfrissítések](#BKMK_SU_NAPLog)  

    -   [Hálózati ébresztés](#BKMK_WOLLog)  

    -   [Windows 10 karbantartása](#BKMK_WindowsServicingLog)

    -   [A Windows Update Agent](#BKMK_WULog)  

    -   [WSUS-kiszolgáló](#BKMK_WSUSLog)  

##  <a name="BKMK_AboutLogs"></a>A Configuration Manager naplófájljainak áttekintése  
 A legtöbb folyamatokat a Configuration Manager működéssel kapcsolatos adatokat ír az adott folyamathoz tartozó naplófájlba. A naplófájlok azonosítva **.log** vagy **.lo_** fájlkiterjesztések. A Configuration Manager egy .log fájlba ír, amíg nem éri a maximális méretét. Amikor a napló megtelik, a rendszer átmásolja a .log fájlt az ugyanolyan nevű, de .lo_ kiterjesztésű fájlba, és a folyamat vagy az összetevő folytatja az írást a .log fájlba. Amikor a .log fájl ismét eléri maximális méretét, a .lo_ fájlt felülírja a rendszer, és a folyamat ismétlődik. Egyes összetevők kiépítik a naplófájlok előzményeit úgy, hogy a naplófájl nevéhez egy dátum- és időbélyeget fűznek, és megtartják a .log kiterjesztést. Kivételt képez a maximális méret és a .lo_ fájlt az ügyfél Linux és UNIX rendszerű. Hogyan a Linux és UNIX rendszerű ügyfélnél a naplófájlok kapcsolatos információkért lásd: [kezelése naplófájlok az ügyfél Linux és UNIX rendszerű](#BKMK_ManageLinuxLogs) ebben a témakörben.  

 A naplók megtekintéséhez használja a Configuration Manager naplómegtekintő eszköze a CMTrace, található, a \\SMSSetup\\eszközök mappából a Configuration Manager forrás-adathordozóján. A CMTrace eszköz bekerül minden rendszerindító lemezképbe is a szoftver könyvtárába kerülnek.  

###  <a name="BKMK_LogOptions"></a>Naplózási beállítások konfigurálása a Configuration Manager Service Manager használatával  
 A Configuration Managerben módosíthatja, ahol az naplófájlok tárolásához és módosíthatja a naplófájl méretét.  

 Módosíthatja a naplófájlok méretét, a nevének és a naplófájl helyének módosításához, vagy több összetevő írjon egyetlen naplófájlba kényszerítése, hajtsa végre az alábbi lépéseket.  

#### <a name="to-modify-logging-for-a-component"></a>Egy összetevő naplózás módosítása  

1.  A Configuration Manager konzolon válassza **figyelés**, jelölje be **rendszerállapot**, és válassza **Helyállapot** vagy **összetevő-állapot**.  
2.  A a **Home** lap a **összetevő** csoportban válassza **Start**, majd válassza ki **Configuration Manager Service Manager**.  
3.  Amikor a Configuration Manager Service Manager megnyílik, csatlakozzon a kezelni kívánt helyhez. Ha nem látható, jelölje be a webhely, kezelni kívánt **hely**, jelölje be **Connect**, és írja be a megfelelő hely helykiszolgálójának nevét.  
4.  Bontsa ki a helyet, és navigáljon **összetevők** vagy **kiszolgálók**, attól függően, hol találhatók a kezelni kívánt összetevők.  
5.  A jobb oldali ablaktáblában jelöljön ki egy vagy több összetevőt.  
6.  Az a **összetevő** menü **naplózás**.  
7.  A **Configuration Manager összetevő-naplózás** párbeszédpanelen adja meg a választásához rendelkezésre álló konfigurációs beállításokat.  
8.  Válassza ki **OK** a konfiguráció mentéséhez.  

###  <a name="BKMK_LogLocation"></a>A Configuration Manager napló keresése  
Configuration Manager naplófájljainak hozza létre a naplófájlt folyamat és a helyrendszerek konfigurálása függő különböző helyeken vannak tárolva. A számítógépen a napló helye változhat, mert a keresési funkció segítségével található a megfelelő naplófájlok helyét a Configuration Manager számítógépeken, ha az adott helyzetben a hibaelhárítás van szüksége.  

##  <a name="BKMK_ClientLogs"></a>A Configuration Manager ügyfeleinek naplói  
Az alábbi szakaszok az ügyfélműveletekkel és az ügyféltelepítéssel kapcsolatos naplófájlokat tartalmazzák.  

###  <a name="BKMK_ClientOpLogs"></a>Ügyfélműveletek  
A következő táblázat a Configuration Manager-ügyfél található naplófájlokat.  

|Napló neve|Leírás|  
|--------------|-----------------|  
|CAS.log|A tartalomhoz való hozzáférést szolgáltatás. A helyi csomag gyorsítótárát kezeli az ügyfélen.|  
|Ccm32BitLauncher.log|Olyan alkalmazások az ügyfél műveleteit rögzíti a "Futtatás mint 32 bites" jelölésű.|  
|CcmEval.log|Rögzíti a Configuration Manager ügyfél állapotának kiértékelési tevékenységeit és a Configuration Manager-ügyfél által igényelt összetevők részletes adatait.|  
|CcmEvalTask.log|A Configuration Manager ügyfél állapotának kiértékelési tevékenységeit, amelyeket a kiértékelés ütemezett feladata kezdeményezett rögzíti.|  
|CcmExec.log|Az ügyfél és az SMS ügynökállomás szolgáltatás tevékenységeit rögzíti. A naplófájl az ébresztési proxy engedélyezésével és letiltásával kapcsolatos adatokat is tartalmaz.|  
|CcmMessaging.log|Az ügyfél és a felügyeleti közötti kommunikáció pontok kapcsolatos tevékenységeket rögzíti.|  
|CCMNotificationAgent.log|Az ügyfél értesítési műveleteivel kapcsolatos tevékenységeket rögzíti.|  
|Ccmperf.log|Az ügyfél teljesítményszámlálóival kapcsolatos adatok karbantartására és gyűjtésére vonatkozó tevékenységeket rögzíti.|  
|CcmRestart.log|Az ügyfélszolgáltatás újraindítási tevékenységét rögzíti.|  
|CCMSDKProvider.log|Az ügyfél SDK felületeihez tartozó tevékenységeket rögzíti.|  
|CertificateMaintenance.log|Az Active Directory tartományi szolgáltatások és a felügyeleti pontok tanúsítványait kezeli.|  
|CIDownloader.log|Konfigurációelem definíciójának letöltéseire vonatkozó részletes adatokat rögzíti.|  
|CITaskMgr.log|Azon feladatokat rögzíti, amelyeket az alkalmazás és központi telepítési típus, például tartalom egyes kezdeményeztek töltse le és telepítse, vagy az eltávolítási műveleteket.|  
|ClientAuth.log|Aláírási rekordok, és az ügyfél hitelesítési tevékenységet.|  
|ClientIDManagerStartup.log|Az ügyfél GUID azonosítóját hozza létre és kezeli, valamint azonosítja az ügyfélregisztrálás és -hozzárendelés során végrehajtott feladatokat.|  
|ClientLocation.log|Az ügyfél helyhozzárendelésével kapcsolatos feladatokat rögzíti.|  
|CMHttpsReadiness.log|A Configuration Manager HTTPS Készültségfelmérő eszköz futtatásának eredményeire rögzíti. Az eszköz ellenőrzi, hogy a számítógépek rendelkeznek-e a nyilvános kulcsokra épülő infrastruktúra (PKI) ügyfél-hitelesítési tanúsítványt, amely a Configuration Managerrel használható.|  
|CmRcService.log|A távvezérlési szolgáltatáshoz tartozó adatokat rögzíti.|  
|ContentTransferManager.log|A háttérben futó intelligens átviteli szolgáltatás (BITS) vagy Server Message Block (SMB) töltse le, vagy a hozzáférési csomagok ütemezi.|  
|DataTransferService.log|A BITS összes, házirend- és csomag-hozzáférési kommunikációját rögzíti.|  
|EndpointProtectionAgent|A System Center Endpoint Protection-ügyfél és a kártevőirtó-házirend alkalmazását, hogy az ügyfél telepítésével kapcsolatos adatokat rögzíti.|  
|execmgr.log|Az ügyfélen futó csomag- és feladatütemezésekre vonatkozó részletes adatokat rögzíti.|  
|ExpressionSolver.log|A részletes használt, vagy a hibakeresési naplózás speciális észlelési módszerekre vonatkozó részletes adatokat rögzíti be van kapcsolva.|  
|ExternalEventAgent.log|Az Endpoint Protection kártevőészlelésének és az ügyfél állapotával kapcsolatos események előzményadatait rögzíti.|  
|FileBITS.log|Az SMB összes csomag-hozzáférési feladatát rögzíti.|  
|FileSystemFile.log|A Windows Management Instrumentation (WMI) szolgáltató szoftverleltárral és fájlgyűjtéssel kapcsolatos tevékenységét rögzíti.|  
|FSPStateMessage.log|Az ügyfél által a tartalék állapotkezelő pontra küldött állapotüzenetekkel kapcsolatos tevékenységet rögzíti.|  
|InternetProxy.log|A hálózati proxykonfigurálási és használata tevékenységet rögzíti az ügyfélnél.|  
|InventoryAgent.log|Az ügyfélen végrehajtott hardver- és szoftver-nyilvántartási, valamint szívveréses felderítési műveletek tevékenységeit rögzíti.|  
|LocationCache.log|Az ügyfél karbantartási és a hely gyorsítótár-használata tevékenységet rögzíti.|  
|LocationServices.log|A felügyeleti pontok, szoftverfrissítési pontok és terjesztési pontok keresésével kapcsolatos ügyféltevékenységet rögzíti.|  
|MaintenanceCoordinator.log|Általános karbantartási feladatok kapcsolatos tevékenységet rögzíti az ügyfélnél.|  
|Mifprovider.log|A WMI szolgáltató Management Information Format (MIF) fájlokkal kapcsolatos tevékenységét rögzíti.|  
|mtrmgr.log|Az összes szoftverhasználat-mérési folyamatot figyeli.|  
|PolicyAgent.log|Házirendigényléseket rögzíti az adatátviteli szolgáltatás használatával végrehajtott.|  
|PolicyAgentProvider.log|A házirendváltozásokat rögzíti.|  
|PolicyEvaluator.log|Az ügyfélszámítógépeken a házirendek (beleértve a szoftverfrissítésekből származó házirendeket is) kiértékelésére vonatkozó részletes adatokat rögzíti.|  
|PolicyPlatformClient.log|Szervizelési és megfelelőségi összes szolgáltatónál a fájlszolgáltató kivételével Policy Platform \Program Files\Microsoft található folyamatát rögzíti.|  
|PolicySdk.log|A házirendrendszer SDK felületeihez tartozó tevékenységeket rögzíti.|  
|Pwrmgmt.log|Az ébresztési proxyügyfél engedélyezésére vagy letiltására és beállításainak konfigurálására vonatkozó adatokat rögzíti.|  
|PwrProvider.log|A WMI szolgáltatásban üzemeltetett energiagazdálkodási szolgáltató (PWRInvProvider) tevékenységeit rögzíti. A Windows összes támogatott verzióján a szolgáltató a hardverleltározás során számba veszi a számítógépeken az aktuális beállításokat, és energiaséma beállításait alkalmazza.|  
|SCClient_&lt;*domain*\>@&lt;*username*\>_1.log|A Szoftverközpontban végzett tevékenységet rögzíti a megadott felhasználónál az ügyfélszámítógépen.|  
|SCClient_&lt;*domain*\>@&lt;*username*\>_2.log|A Szoftverközpontban végzett tevékenység előzményeit rögzíti a megadott felhasználónál az ügyfélszámítógépen.|  
|Scheduler.log|Az ütemezett feladatok tevékenységeit rögzíti az összes ügyfélműveletnél.|  
|SCNotify_&lt;*domain*\>@&lt;*username*\>_1.log|A szoftverrel kapcsolatos értesítési tevékenységet rögzíti a megadott felhasználónál.|  
|SCNotify_&lt;*domain*\>@&lt;*username*\>_1-&lt;*date_time*>.log|A szoftverrel kapcsolatos értesítési tevékenység előzményadatait rögzíti a megadott felhasználónál.|  
|setuppolicyevaluator.log|A konfigurálási és leltárházirend WMI szolgáltatásban való létrehozását rögzíti.|  
|SleepAgent_&lt;*tartomány*\>@SYSTEM_0.log|Az ébresztési proxyhoz tartozó fő naplófájl.|  
|smscliui.log|A Configuration Manager-ügyfél a Vezérlőpulton használatát rögzíti.|  
|SrcUpdateMgr.log|A telepített és az aktuális terjesztési pont forráshelyeiről frissített Windows Installer-alkalmazások tevékenységét rögzíti.|  
|StatusAgent.log|Az ügyfél összetevők által létrehozott állapotüzeneteket rögzíti.|  
|SWMTRReportGen.log|Egy használja a mérési ügynök által gyűjtött adatok jelentését állítja. Ezeknek az adatoknak a naplózása a Mtrmgr.log fájlban történik.|  
|UserAffinity.log|A felhasználó-eszköz kapcsolatra vonatkozó részletes adatokat rögzíti.|  
|VirtualApp.log|Az Application Virtualization (App-V) központi telepítési típusok kiértékelésére rekordok adatokat.|  
|Wedmtrace.log|Az írási szűrőkkel kapcsolatos, Windows Embedded ügyfeleken végrehajtott műveleteket rögzíti.|  
|wakeprxy-install.log|Telepítési adatokat rögzít amikor az ügyfelek megkapják az ébresztési proxy bekapcsolása vonatkozó ügyfélbeállítást.|  
|wakeprxy-uninstall.log|Az ébresztési proxy eltávolítására, amikor az ügyfelek megkapják az ügyfélbeállítást kikapcsolása ébresztési proxyt, ha az ébresztési proxy előzőleg engedélyezve kapcsolatos adatokat rögzíti.|  

###  <a name="BKMK_ClientInstallLog"></a>Ügyfél-telepítési naplófájlok  
 A következő táblázat a Configuration Manager-ügyfél telepítésével kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|  
|--------------|-----------------|  
|ccmsetup.log|Az ügyfelek telepítéséhez, frissítéséhez és eltávolításához ccmsetup.exe feladatokat rögzíti. Az ügyfél-telepítési problémák megoldásához használható.|  
|ccmsetup-ccmeval.log|Az ügyfél állapotával és szervizelésével kapcsolatos ccmsetup.exe feladatokat rögzíti.|  
|CcmRepair.log|Az ügyfélügynök javítási tevékenységeit rögzíti.|  
|client.msi.log|A client.msi által végrehajtott beállítási feladatokat rögzíti. Az ügyfél-telepítési és -eltávolítási problémák megoldásához használható.|  

###  <a name="BKMK_LogFilesforLnU"></a>A Linux és UNIX-ügyfél  
 A Configuration Manager-ügyfél Linux és UNIX rendszeren a következő naplófájlokba ír adatokat.  

> [!TIP]  
>  Verziótól kezdődően az ügyfelek Linux és UNIX rendszerekhez készült 1. összesítő frissítést a segítségével CMTrace naplófájljainak megtekintéséhez az ügyfél Linux és UNIX rendszerekhez készült.  

> [!NOTE]  
>  Ha a Linux és UNIX rendszerű ügyfél eredeti kiadását használja, a dokumentáció ezen szakaszában cserélje le a következő hivatkozásokat az egyes fájloknál vagy folyamatoknál:  
>   
>  -   Cserélje le az **omiserver.bin**-t **nwserver.bin**-re  
> -   Cserélje le az **omi**-t **nanowbem**-re  

|Napló neve|Részletek|  
|--------------|-------------|  
|Scxcm.log|A Linux és UNIX rendszerű (ccmexec.bin) a Configuration Manager-ügyfél alapvető szolgáltatásához naplófájl. Ez a naplófájl a ccmexec.bin telepítésére és ezt követő műveleteire vonatkozó adatokat tartalmaz.<br /><br /> Alapértelmezés szerint ez a naplófájl itt található: **/var/opt/microsoft/scxcm.log**<br /><br /> A naplófájl helye módosításához nyissa meg szerkesztésre az **/opt/microsoft/configmgr/etc/scxcm.conf** fájlt, és módosítsa a **PATH** mező értékét. A változtatás érvénybe léptetéséhez nem kell újraindítania az ügyfélszámítógépet vagy a szolgáltatást.<br /><br /> A naplózási szintet állíthat be egy négy beállítást.|  
|Scxcmprovider.log|A Linux és UNIX rendszerű (omiserver.bin) a Configuration Manager-ügyfél CIM szolgáltatásához naplófájl. Ez a naplófájl az nwserver.bin folyamatban lévő műveleteire vonatkozó adatokat tartalmaz.<br /><br /> Ez a napló itt található:**/var/opt/microsoft/configmgr/scxcmprovider.log**<br /><br /> A naplófájl helyének módosításához nyissa meg szerkesztésre az **/opt/microsoft/omi/etc/scxcmprovider.conf** fájlt, és módosítsa a **PATH** mező értékét. A változtatás érvénybe léptetéséhez nem kell újraindítania az ügyfélszámítógépet vagy a szolgáltatást.<br /><br /> A naplózási szintet állíthat be három beállítás egyikét.|  

 Mindkét naplófájl több naplózási szintet támogat:  

-   **scxcm.log**. A naplózási szint módosításához szerkessze **/opt/microsoft/configmgr/etc/scxcm.conf** , és minden példánya módosítsa a **modul** címkén belül, hogy a kívánt naplózási szintet:  

    -   HIBA: Figyelmet igénylő problémák jelzése  

    -   FIGYELMEZTETÉS: Az ügyfél műveleteivel lehetséges problémák jelzése  

    -   INFORMÁCIÓ: Részletesebb naplózás, amely jelzi az ügyfélen történt különféle események állapotát  

    -   NYOMKÖVETÉS: Részletes naplózás, amely jellemzően problémák diagnosztizálásához szolgál  

-   **scxcmprovider.log**. A naplózási szint módosításához szerkessze **/opt/microsoft/omi/etc/scxcmprovider.conf** , és minden példánya módosítsa a **modul** címkén belül, hogy a kívánt naplózási szintet:  

    -   HIBA: Figyelmet igénylő problémák jelzése  

    -   FIGYELMEZTETÉS: Az ügyfél műveleteivel lehetséges problémák jelzése

    -   INFORMÁCIÓ: Részletesebb naplózás, amely jelzi az ügyfélen történt különféle események állapotát  

Szokásos üzemi körülmények az ERROR naplózási szintet használja. A naplózási szint hozza létre a legkisebb naplófájlt. A naplózási szint megnövelik a hiba, figyelmeztetés, információ, majd NYOMKÖVETÉSI, mert nagyobb naplófájlt jön létre, mivel több adatot ír a fájlt.  

####  <a name="BKMK_ManageLinuxLogs"></a>A Linux és UNIX rendszerű ügyfélnél a naplófájlok kezelése  
A Linux és UNIX rendszerű ügyfél nem korlátozza az ügyfél-naplófájlok maximális méretét, és nem az ügyfél automatikusan másolja a .log fájl másik fájlba, például a .lo_ fájlt. Ha szeretné a naplófájlok maximális méretét, alkalmazzon a egy folyamatot, amely független a naplófájlok kezelése a Configuration Manager-ügyfél Linux és UNIX rendszerekhez készült.  

Például használhatja a Linux és UNIX rendszerű parancs **logrotate** méretének és váltogatásának, így az ügyfél kezeléséhez. A Configuration Manager-ügyfél Linux és UNIX rendszerű rendelkezik, amely lehetővé teszi illesztőfelület **logrotate** hogy jelezze az ügyfélnek a naplóváltás befejezését, így az ügyfél folytathatja a naplófájlba írást.  

A **logrotate** parancsról az Ön által használt Linux- vagy UNIX-disztribúció dokumentációjában olvashat.  

###  <a name="BKMK_LogfilesforMac"></a>Mac számítógépeken futó ügyfele  
A Configuration Manager-ügyfél Mac számítógépeken a következő naplófájlokba ír adatokat.  

|Napló neve|Részletek|  
|--------------|-------------|  
|CCMClient -&lt;*dátum_időpont*> .log|A Mac ügyfél műveleteket, beleértve az alkalmazások kezelése, a leltározás és a hibanaplózás kapcsolatos tevékenységeket rögzíti.<br /><br /> Ez a naplófájl a Mac számítógépen Library/Application Support/Microsoft/CCM/Logs mappában található.|  
|CCMAgent -&lt;*dátum_időpont*> .log|Az ügyfél műveleteivel, beleértve a felhasználói bejelentkezés és kijelentkezés műveletek és a Mac számítógép tevékenysége kapcsolatos adatokat rögzíti.<br /><br /> Ez a naplófájl a Mac számítógépen ~/Library/Logs mappában van.|  
|CCMNotifications -&lt;*dátum_időpont*> .log|A Mac számítógépen megjelenített, a Configuration Manager értesítések kapcsolatos tevékenységeket rögzíti.<br /><br /> Ez a naplófájl a Mac számítógépen ~/Library/Logs mappában található.|  
|CCMPrefPane -&lt;*dátum_időpont*> .log|A Mac számítógépen, amely tartalmazza az általános állapot és a hibanaplózás Configuration Manager párbeszédpaneljével kapcsolatos tevékenységeket rögzíti.<br /><br /> Ez a naplófájl a Mac számítógépen ~/Library/Logs mappában található.|  

A M a helyrendszer-kiszolgálón lévő SMS_DM.log naplófájl a Mac számítógépek és a felügyeleti pont be van állítva a mobileszközök és Mac számítógépek közötti kommunikáció is rögzíti.  

##  <a name="BKMK_ServerLogs"></a>A Configuration Manager helykiszolgáló naplófájljai  
 Az alábbi szakaszok a helykiszolgálón vagy adott helyrendszerszerepkörökkel, amelyek kapcsolódnak naplófájlokat sorolják fel.  

###  <a name="BKMK_SiteSiteServerLog"></a>Helyrendszer-kiszolgáló és a helyrendszer-kiszolgáló naplói  
 A következő táblázat a naplófájlokat, amelyek a Configuration Manager-helykiszolgáló és helyrendszer-kiszolgálók.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|adctrl.log|A beléptetés feldolgozási tevékenységét rögzíti.|Helykiszolgáló|  
|ADForestDisc.log|Az Active Directory erdőfelderítési műveleteit rögzíti.|Helykiszolgáló|  
|ADService.log|Az Active Directory címtárban a fióklétrehozás és a biztonsági csoport részletes adatait rögzíti.|Helykiszolgáló|  
|adsgdis.log|Az Active Directory csoportfelderítési műveleteit rögzíti.|Helykiszolgáló|  
|adsysdis.log|Az Active Directory rendszer-felderítési műveleteit rögzíti.|Helykiszolgáló|  
|adusrdis.log|Az Active Directory felhasználófelderítési műveleteit rögzíti.|Helykiszolgáló|  
|ccm.log|Az ügyfélleküldéses telepítés tevékenységeit rögzíti.|Helykiszolgáló|  
|CertMgr.log|Rögzíti helyen belüli kommunikáció tevékenységek tanúsítvány.|Helyrendszer kiszolgálója|  
|chmgr.log|Az ügyfélállapot-kezelő tevékenységeit rögzíti.|Helykiszolgáló|  
|Cidm.log|A Client Install Data Manager (CIDM) által az ügyfélbeállításokon végrehajtott változtatásokat rögzíti.|Helykiszolgáló|  
|colleval.log|A gyűjteménykiértékelő által létrehozott, módosított és törölt gyűjteményekről szóló információkat rögzíti.|Helykiszolgáló|  
|compmon.log|A helykiszolgáló számára figyelt összetevőszálak állapotát rögzíti.|Helyrendszer kiszolgálója|  
|compsumm.log|Az összetevőállapot-összegző feladatait rögzíti.|Helykiszolgáló|  
|ComRegSetup.log|A COM regisztrálási eredményeinek kezdeti telepítését rögzíti adott helykiszolgálónál.|Helyrendszer kiszolgálója|  
|dataldr.log|A MIF-fájlok és a Hardverleltár a Configuration Manager adatbázisban feldolgozásával kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|ddm.log|A felderítésiadat-kezelő tevékenységeit rögzíti.|Helykiszolgáló|  
|despool.log|A helyek közötti bejövő kommunikációs adatátviteleket rögzíti.|Helykiszolgáló|  
|distmgr.log|Csomag létrehozására, tömörítésére, változásreplikálására és adatmódosításaira vonatkozó részleteket rögzít.|Helykiszolgáló|  
|EPCtrlMgr.log|A kártevő-fenyegetés adatainak az Endpoint Protection helyrendszerszerepkör-kiszolgáló és a Configuration Manager adatbázisának szinkronizálással kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|EPMgr.log|Az Endpoint Protection helyrendszerszerepkör állapotát rögzíti.|Helyrendszer kiszolgálója|  
|EPSetup.log|Az Endpoint Protection helyrendszerszerepkör telepítésével kapcsolatos adatokat tartalmazza.|Helyrendszer kiszolgálója|  
|EnrollSrv.log|A beléptetési szolgáltatás folyamatának tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|EnrollWeb.log|A beléptetési webhely folyamatának tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|fspmgr.log|A tartalék állapotkezelő pont helyrendszerszerepkör tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|hman.log|Rekordok információ a hely konfigurálási változtatásaira, és a helyadatok közzétételére az Active Directory tartományi szolgáltatásokban.|Helykiszolgáló|  
|Inboxast.log|A felügyeleti pontról a helykiszolgáló megfelelő INBOXES mappájába áthelyezett fájlokat rögzíti.|Helykiszolgáló|  
|inboxmgr.log|A beérkezett üzenetek mappái közötti fájlátviteli tevékenységeket rögzíti.|Helykiszolgáló|  
|inboxmon.log|A beérkező fájlok és a teljesítményszámlálók módosításainak feldolgozását rögzíti.|Helykiszolgáló|  
|invproc.log|A MIF-fájlok másodlagos helyről annak fölérendelt helyére való továbbítását rögzíti.|Helykiszolgáló|  
|migmctrl.log|Az áttelepítési műveletek, például áttelepítési feladatok, megosztott terjesztési pontok és terjesztési pontok frissítéseinek adatait rögzíti.|A Configuration Manager-hierarchia felső szintű helye végzi, és az összes alárendelt elsődleges hely.<br /><br /> A több elsődleges helyet tartalmazó hierarchiában használja a központi adminisztrációs helyen létrehozott naplófájlt.|  
|mpcontrol.log|A regisztráció, a felügyeleti pont Windows Internet Name Service (WINS) rögzíti. 10 percenként rögzíti a felügyeleti pont rendelkezésre állását.|Helyrendszer kiszolgálója|  
|mpfdm.log|A felügyeleti pont azon összetevőjének műveleteit rögzíti, amely az ügyfélfájlokat a helykiszolgáló megfelelő INBOXES mappájába helyezi át.|Helyrendszer kiszolgálója|  
|mpMSI.log|A pont telepítési felügyeleti kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|MPSetup.log|A felügyeleti pont telepítési burkolófolyamatát rögzíti.|Helykiszolgáló|  
|netdisc.log|A hálózatfelderítési műveleteket rögzíti.|Helykiszolgáló|  
|ntsvrdis.log|A helyrendszer-kiszolgálók felderítési tevékenységét rögzíti.|Helykiszolgáló|  
|Objreplmgr|Replikálásnál az objektummódosítási értesítések feldolgozását rögzíti.|Helykiszolgáló|  
|offermgr.log|A hirdetésfrissítéseket rögzíti.|Helykiszolgáló|  
|offersum.log|A központi telepítési állapotüzenetek összefoglalását rögzíti.|Helykiszolgáló|  
|OfflineServicingMgr.log|Az operációs rendszer lemezképfájljain a frissítések alkalmazásával kapcsolatos tevékenységeket rögzíti.|Helykiszolgáló|  
|outboxmon.log|A kimenő fájlok és a teljesítményszámlálók módosításainak feldolgozását rögzíti.|Helykiszolgáló|  
|PerfSetup.log|A teljesítményszámlálók telepítésének eredményeit rögzíti.|Helyrendszer kiszolgálója|  
|PkgXferMgr.log|Tartalom küldése egy elsődleges helyről távoli terjesztési pontra felelős SMS_Executive összetevő műveleteit rögzíti.|Helykiszolgáló|  
|policypv.log|Az ügyfél beállításai vagy központi telepítései változtatásai miatt az ügyfélházirendeken szükséges frissítéseket rögzíti.|Elsődleges hely kiszolgálója|  
|rcmctrl.log|A hierarchia helyei közötti adatbázis-replikálás tevékenységeit rögzíti.|Helykiszolgáló|  
|replmgr.log|Fájloknak a helyrendszer összetevői és az ütemező összetevő közötti replikálását rögzíti.|Helykiszolgáló|  
|ResourceExplorer.log|A hibák, figyelmeztetések és erőforrás-kezelő futtatásával kapcsolatos információkat.|A Configuration Manager konzolt futtató számítógép|  
|ruleengine.log|Az azonosításhoz, tartalomletöltéshez, valamint szoftverfrissítési csoport és központi telepítés létrehozásához tartozó automatikus központi telepítési szabályokra vonatkozó adatokat rögzíti.|Helykiszolgáló|  
|schedule.log|A helyek közötti feladat- és fáljlreplikálásra vonatkozó részleteket rögzíti.|Helykiszolgáló|  
|sender.log|A helyek közötti fájl alapú replikálás által átvitelre kerülő fájlokat rögzíti.|Helykiszolgáló|  
|sinvproc.log|A szoftverleltáradatok helyadatbázisba történő feldolgozásának adatait rögzíti.|Helykiszolgáló|  
|sitecomp.log|A hely összes helyrendszer-kiszolgálóján a telepített helyösszetevők karbantartására vonatkozó részletes adatokat rögzíti.|Helykiszolgáló|  
|sitectrl.log|Az adatbázisban a hely vezérlőobjektumain végrehajtott helybeállítási változtatásokat rögzíti.|Helykiszolgáló|  
|sitestat.log|Az összes helyrendszer rendelkezésre állását és lemezterületet figyelő folyamatát rögzíti.|Helykiszolgáló|  
|SmsAdminUI.log|A Configuration Manager konzol tevékenységét rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|SMSAWEBSVCSetup.log|Az alkalmazáskatalógus webszolgáltatás telepítési tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|smsbkup.log|A hely biztonsági mentési folyamatának eredményét rögzíti.|Helykiszolgáló|  
|smsdbmon.log|Az adatbázis változásait rögzíti.|Helykiszolgáló|  
|SMSENROLLSRVSetup.log|A beléptetés webszolgáltatás telepítési tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|SMSENROLLWEBSetup.log|A beléptetési webhely telepítési tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|smsexec.log|A helykiszolgáló összes összetevőszálának feldolgozását rögzíti.|Helykiszolgáló vagy a helyrendszer kiszolgálója|  
|SMSFSPSetup.log|Az adott tartalék állapotkezelő pont telepítése által előállított üzeneteket rögzíti.|Helyrendszer kiszolgálója|  
|SMSPORTALWEBSetup.log|Az alkalmazáskatalógus webhely telepítési tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|SMSProv.log|A WMI-szolgáltató helyadatbázishoz való hozzáférését rögzíti.|Az SMS Provider eszközt futtató számítógép|  
|srsrpMSI.log|A jelentéskészítési pont telepítési folyamatának részletes eredményeit rögzíti az MSI kimenetéről.|Helyrendszer kiszolgálója|  
|srsrpsetup.log|A jelentéskészítési pont telepítési folyamatának eredményeit rögzíti.|Helyrendszer kiszolgálója|  
|statesys.log|Az állapotrendszer üzeneteinek feldolgozását rögzíti.|Helykiszolgáló|  
|statmgr.log|Az összes állapotüzenet adatbázisba írását rögzíti.|Helykiszolgáló|  
|swmproc.log|A mérési fájlok és beállítások feldolgozását rögzíti.|Helykiszolgáló|  

###  <a name="BKMK_SiteInstallLog"></a>Helykiszolgáló telepítési naplófájljai  
 A következő táblázat a hely telepítésével kapcsolatos adatokat tartalmazó naplófájlokat ismerteti.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|ConfigMgrPrereq.log|Előfeltételként szükséges összetevők kiértékelési és telepítési tevékenységeit rögzíti.|Helykiszolgáló|  
|ConfigMgrSetup.log|Rögzíti a helykiszolgáló telepítésének részletes kimenet.|Helykiszolgáló|  
|ConfigMgrSetupWizard.log|A telepítővarázsló tevékenységével kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|SMS_BOOTSTRAP.log|A másodlagos hely telepítési folyamatának indítási állapotára vonatkozó adatokat rögzíti. A tényleges telepítési folyamat részletes adatait a ConfigMgrSetup.log naplófájl tartalmazza.|Helykiszolgáló|  
|smstsvc.log|A telepítés, a használata és a kiszolgálók, a kapcsolatot kezdeményező kiszolgáló számítógépfiókjának használatával közötti hálózati kapcsolat és engedélyek tesztelésére használt Windows-szolgáltatás eltávolításával kapcsolatos adatokat rögzíti.|Helykiszolgáló és helyrendszer-kiszolgáló|  

###  <a name="BKMK_FSPLog"></a>Tartalék állapotkezelő pont naplófájlok  
 A következő táblázat a tartalék állapotkezelő ponttal kapcsolatos adatokat tartalmazó naplófájlokat ismerteti.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|FspIsapi|A hagyományos mobileszközök és az ügyfélszámítógépek, valamint a tartalék állapotkezelő pont kommunikációjának adatait rögzíti.|Helyrendszer kiszolgálója|  
|fspMSI.log|Az adott tartalék állapotkezelő pont telepítése által előállított üzeneteket rögzíti.|Helyrendszer kiszolgálója|  
|fspmgr.log|A tartalék állapotkezelő pont helyrendszerszerepkör tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  

###  <a name="BKMK_MPLog"></a>Felügyeleti pont naplófájlok  
 A következő táblázat a felügyeleti ponttal kapcsolatos adatokat tartalmazó naplófájlokat ismerteti.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|CcmIsapi.log|Az ügyfél végponti üzenetkezelési tevékenységét rögzíti.|Helyrendszer kiszolgálója|  
|MP_CliReg.log|Az ügyfél felügyeleti pont által feldolgozott regisztrálási tevékenységét rögzíti.|Helyrendszer kiszolgálója|  
|MP_Ddr.log|Rekordok XML.DDR rekordok konvertálását az ügyfelektől, és majd a hely kiszolgálójára másolja őket.|Helyrendszer kiszolgálója|  
|MP_Framework.log|Az alapvető felügyeleti pont és az ügyfél keretrendszeri összetevőinek tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|MP_GetAuth.log|Az ügyfél engedélyezési tevékenységét rögzíti.|Helyrendszer kiszolgálója|  
|MP_GetPolicy.log|Az ügyfélszámítógépekről érkező házirendkérelmi tevékenységet rögzíti.|Helyrendszer kiszolgálója|  
|MP_Hinv.log|Az ügyfelektől érkező XML hardverleltárrekordok konvertálására és ezek helykiszolgálóra másolására vonatkozó részletes adatokat rögzíti.|Helyrendszer kiszolgálója|  
|MP_Location.log|Az ügyfelektől érkező helykérelemmel és válasszal kapcsolatos tevékenységet rögzíti.|Helyrendszer kiszolgálója|  
|MP_OOBMgr.log|A felügyeleti pont ügyféltől egy OTP fogadásával kapcsolatos tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|MP_Policy.log|A házirenddel kapcsolatos kommunikációt rögzíti.|Helyrendszer kiszolgálója|  
|MP_Relay.log|Az ügyfélről gyűjtött fájlok átvitelét rögzíti.|Helyrendszer kiszolgálója|  
|MP_Retry.log|Rekordok Hardverleltár ismétlési folyamatait.|Helyrendszer kiszolgálója|  
|MP_Sinv.log|Az ügyfelektől érkező XML szoftverleltárrekordok konvertálására és ezek helykiszolgálóra másolására vonatkozó részletes adatokat rögzíti.|Helyrendszer kiszolgálója|  
|MP_SinvCollFile.log|A fájlgyűjtéssel kapcsolatos részletes adatokat rögzíti.|Helyrendszer kiszolgálója|  
|MP_Status.log|Az ügyfelektől érkező XML.svf állapotüzenet-fájlok konvertálására és ezek helykiszolgálóra másolására vonatkozó részletes adatokat rögzíti.|Helyrendszer kiszolgálója|  
|mpcontrol.log|A felügyeleti pont WINS kiszolgálón való regisztrálását rögzíti. 10 percenként rögzíti a felügyeleti pont rendelkezésre állását.|Helykiszolgáló|  
|mpfdm.log|A felügyeleti pont azon összetevőjének műveleteit rögzíti, amely az ügyfélfájlokat a helykiszolgáló megfelelő INBOXES mappájába helyezi át.|Helyrendszer kiszolgálója|  
|mpMSI.log|A pont telepítési felügyeleti kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|MPSetup.log|A felügyeleti pont telepítési burkolófolyamatát rögzíti.|Helykiszolgáló|  

###  <a name="BKMK_SUPLog"></a>Szoftverfrissítési pont napló fájlokat  
 A következő táblázat a szoftverfrissítési pont kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|objreplmgr.log|A szoftver-replikációval kapcsolatos adatokat rögzíti értesítési fájlok fölérendelt helyről alárendelt helyekre való frissíti.|Helykiszolgáló|  
|PatchDownloader.log|A szoftverfrissítéseknek a frissítési forrásból a helykiszolgálón lévő frissítési forrásból történő letöltési folyamatának adatait rögzíti.|A Configuration Manager konzolt, amely a letölthető elemet üzemeltető számítógépen|  
|ruleengine.log|Az azonosításhoz, tartalomletöltéshez, valamint szoftverfrissítési csoport és központi telepítés létrehozásához tartozó automatikus központi telepítési szabályokra vonatkozó adatokat rögzíti.|Helykiszolgáló|  
|SUPSetup.log|A szoftverfrissítési pont telepítésével kapcsolatos adatokat rögzíti. A szoftverfrissítési pont telepítésének befejezése után a rendszer a következő bejegyzést írja a naplófájlba: **Installation was successful** (A telepítés sikeres volt).|Helyrendszer kiszolgálója|  
|WCM.log|A pont konfiguráció és a WSUS-kiszolgálóhoz az előfizetett frissítési kategóriákat, besorolásokat és nyelveket a szoftverfrissítési kapcsolatos adatokat rögzíti.|A WSUS-kiszolgálóhoz csatlakozó helykiszolgáló|  
|WSUSCtrl.log|A hely WSUS-kiszolgálójának konfigurációjával, adatbázis-kapcsolatával és állapotával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|wsyncmgr.log|A frissítések szinkronizálási folyamat adatait rögzíti.|Helyrendszer kiszolgálója|  
|WUSSyncXML.log|A Microsoft Updates leltározási eszközének adatait rögzíti. a szinkronizálási folyamat.|A Microsoft Updates leltározási eszközének szinkronizálási állomásaként konfigurált ügyfélszámítógép|  

##  <a name="BKMK_FunctionLogs"></a>A Configuration Manager funkcióihoz tartozó naplófájlok  
 A Configuration Manager funkcióihoz kapcsolódó naplófájlok a következő szakaszok listája.  

###  <a name="BKMK_AppManageLog"></a>Alkalmazáskezelés  
 A következő táblázat az Alkalmazáskezelés kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|AppIntentEval.log|Az alkalmazások aktuális és várt állapotának, alkalmazhatóságának, a követelményeknek való megfelelés, a telepítési típusok és a függőségek adatait rögzíti.|Ügyfél|  
|AppDiscovery.log|Az ügyfélszámítógépeken lévő alkalmazások felderítésének vagy észlelésének adatait rögzíti.|Ügyfél|  
|AppEnforce.log|Az ügyfélen lévő alkalmazásokkal kapcsolatban kényszerítetten végrehajtott műveletek (telepítés és eltávolítás) adatait rögzíti.|Ügyfél|  
|awebsctl.log|Rögzíti a figyelési tevékenységek az Alkalmazáskatalógus webszolgáltatási pontja helyrendszerszerepkör.|Helyrendszer kiszolgálója|  
|awebsvcMSI.log|Az alkalmazáskatalógus webszolgáltatási pontja helyrendszerszerepkör részletes telepítési adatait rögzíti.|Helyrendszer kiszolgálója|  
|Ccmsdkprovider.log|Az alkalmazáskezelési SDK tevékenységeit rögzíti.|Ügyfél|  
|colleval.log|A gyűjteménykiértékelő által létrehozott, módosított és törölt gyűjteményekről szóló információkat rögzíti.|Helyrendszer kiszolgálója|  
|ConfigMgrSoftwareCatalog.log|Az alkalmazáskatalógus tevékenységét rögzíti, beleértve a Silverlight használatát.|Ügyfél|  
|portlctl.log|Az alkalmazáskatalógus weboldal-elérési pontja helyrendszerszerepkör figyelési tevékenységeit rögzíti.|Helyrendszer kiszolgálója|  
|portlwebMSI.log|Az alkalmazáskatalógus weboldal-elérési pontja szerepkör MSI-telepítési tevékenységét rögzíti.|Helyrendszer kiszolgálója|  
|PrestageContent.log|Az ExtractContent.exe eszköz távoli, manuálisan előkészített terjesztési pontok használatának adatait rögzíti. Ez az eszköz a fájlba exportált tartalmat bontja ki.|Helyrendszer kiszolgálója|  
|ServicePortalWebService.log|Az alkalmazáskatalógus webszolgáltatás tevékenységét rögzíti.|Helyrendszer kiszolgálója|  
|ServicePortalWebSite.log|Az alkalmazáskatalógus webhely tevékenységét rögzíti.|Helyrendszer kiszolgálója|  
|SMSdpmon.log|A terjesztési pontokon beállított állapotfigyelési ütemezett feladat adatait rögzíti.|Helykiszolgáló|  
|SoftwareCatalogUpdateEndpoint.log|A Szoftverközpontban megjelenített Alkalmazáskatalógus URL-CÍMÉT kezelésével kapcsolatos tevékenységeket rögzíti.|Ügyfél|  
|SoftwareCenterSystemTasks.log|A Szoftverközponthoz előfeltételként szükséges összetevők ellenőrzésének kapcsolatos tevékenységeket rögzíti.|Ügyfél|  

 A következő táblázatban található a csomagok és a programok központi telepítésével kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|colleval.log|A gyűjteménykiértékelő által létrehozott, módosított és törölt gyűjteményekről szóló információkat rögzíti.|Helykiszolgáló|  
|execmgr.log|A futó csomag- és feladatütemezésekre vonatkozó adatokat rögzíti.|Ügyfél|  

###  <a name="BKMK_AILog"></a>Eszközintelligencia  
 A következő táblázatban található az eszközintelligenciával kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|AssetAdvisor.log|Az eszközintelligencia leltározási műveleteinek tevékenységeit rögzíti.|Ügyfél|  
|aikbmgr.log|A beérkező fájlok mappájában található, az eszközintelligencia-katalógus frissítéséhez használt XML-fájlok feldolgozásának adatait rögzíti.|Helykiszolgáló|  
|AIUpdateSvc.log|A pontja közötti műveleteket rögzíti az Eszközintelligencia-katalógus szinkronizálása a System Center Online (SCO), az online webszolgáltatás.|Helyrendszer kiszolgálója|  
|AIUSMSI.log|A pont helyrendszer-szerepkör az Eszközintelligencia-katalógus szinkronizálása telepítésével kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|AIUSSetup.log|A pont helyrendszer-szerepkör az Eszközintelligencia-katalógus szinkronizálása telepítésével kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|ManagedProvider.log|A szoftverekhez társított szoftverazonosító címke használatával végzett szoftverfelderítés adatait rögzíti. Hardverleltárral kapcsolatos tevékenységeket rögzíti.|Helyrendszer kiszolgálója|  
|MVLSImport.log|Az importált licencfájlok feldolgozásának adatait rögzíti.|Helyrendszer kiszolgálója|  

###  <a name="BKMK_BnRLog"></a>Biztonsági mentés és helyreállítás  
 A következő táblázat felsorolja a biztonsági mentési és helyreállítási műveletek, beleértve a helyek alaphelyzetbe állítását kapcsolatos adatokat tartalmazó naplófájlokat és az SMS-szolgáltató módosításait.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|ConfigMgrSetup.log|A Configuration Manager helyreállít egy helyet a biztonsági mentés telepítési és helyreállítási feladatokkal kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|Smsbkup.log|A helyek biztonsági mentési tevékenységének adatait rögzíti.|Helykiszolgáló|  
|smssqlbkup.log|Ha olyan kiszolgálót, amely nem a helykiszolgáló SQL Server telepítve van a Helyadatbázis biztonsági mentési folyamatának eredményét rögzíti.|Helyadatbázis-kiszolgáló|  
|Smswriter.log|A biztonsági mentési folyamathoz használt Configuration Manager VSS-író állapotára vonatkozó adatokat rögzíti.|Helykiszolgáló|  

###  <a name="BKMK_CertificateEnrollment"></a>Tanúsítványigénylés  
 A következő táblázat a Configuration Manager naplófájljainak tanúsítványigényléssel kapcsolatos adatokat tartalmazó. Tanúsítványigénylés használja a tanúsítványregisztrációs pont és a Configuration Manager házirend modulját a hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgálón.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|Crp.log|Igénylési tevékenységeket rögzíti.|Tanúsítványregisztrációs pont|  
|Crpctrl.log|A tanúsítványregisztrációs pont működési állapotát rögzíti.|Tanúsítványregisztrációs pont|  
|Crpsetup.log|A tanúsítványregisztrációs pont telepítésével és konfigurálásával kapcsolatos adatokat rögzíti.|Tanúsítványregisztrációs pont|  
|Crpmsi.log|A tanúsítványregisztrációs pont telepítésével és konfigurálásával kapcsolatos adatokat rögzíti.|Tanúsítványregisztrációs pont|  
|NDESPlugin.log|Rekordok ellenőrző kérdés ellenőrzése és a tanúsítvány beléptetési aktivitást.|Configuration Manager házirend modulját és a hálózati eszközök tanúsítványigénylési szolgáltatása|  

 A Configuration Manager naplófájljainak kívül tekintse át a Windows-alkalmazás az eseménynaplóban a hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgáló és a tanúsítványregisztrációs pontot tartalmazó kiszolgáló. Keresse meg például a **NetworkDeviceEnrollmentService** forrás üzeneteit. A következő naplófájlokat is használhatja:  

-   Az IIS-naplófájljai hálózati eszközök tanúsítványigénylési szolgáltatása:  **&lt;elérési\>\inetpub\logs\LogFiles\W3SVC1**  

-   IIS-naplófájljai a tanúsítványregisztrációs pont:  **&lt;elérési\>\inetpub\logs\LogFiles\W3SVC1**  

-   A Hálózati eszközök tanúsítványigénylési szolgáltatásának naplófájlja: **mscep.log**  

    > [!NOTE]  
    >  Ez a fájl a Hálózati eszközök tanúsítványigénylési szolgáltatás fiókprofiljának mappájában található, például: C:\Users\SCEPSvc. További információkért a Hálózati eszközök tanúsítványigénylési szolgáltatás naplózásának engedélyezéséről l. [A naplózás engedélyezése](http://go.microsoft.com/fwlink/?LinkId=320576) című rész a Technet wiki Hálózati eszközök tanúsítványigénylési szolgáltatással (NDES) és Active Directory tanúsítványszolgáltatással (AD CS) foglalkozó cikkében.  

###  <a name="BKMK_BGB"></a>Ügyfélértesítés  
 A következő táblázatban található az ügyfélértesítéssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|bgbmgr.log|Ügyfél-értesítési feladataival és feldolgozási online és feladatállapotot tartalmazó fájlok vonatkozó hely kiszolgálói tevékenység kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|BGBServer.log|Például az ügyfél – kiszolgáló kommunikáció és a feladatok küldését az ügyfelek számára az értesítési kiszolgáló tevékenységeit rögzíti. Generációja online és feladatállapotot tartalmazó fájlok a helykiszolgálónak küldendő kapcsolatos adatokat rögzíti.|Felügyeleti pont|  
|BgbSetup.log|Az értesítési kiszolgáló telepítési burkolófolyamatát tevékenységeit rögzíti telepítése vagy eltávolítása során.|Felügyeleti pont|  
|bgbisapiMSI.log|Az értesítési kiszolgáló telepítésével és eltávolításával kapcsolatos adatokat rögzíti.|Felügyeleti pont|  
|BgbHttpProxy.log|Az értesítési HTTP-proxy tevékenységeit rögzíti, amikor az a HTTP használatával továbbítja az üzeneteket az ügyfelek és az értesítési kiszolgáló között.|Ügyfél|  
|CcmNotificationAgent.log|Rögzíti, például az ügyfél – kiszolgáló kommunikáció és a feladatokkal kapcsolatos információt az értesítési ügynök tevékenységeit kapott, és más ügyfélügynököknek továbbított.|Ügyfél|  

### <a name="cloud-management-gateway"></a>Felügyeleti átjáró

A következő táblázat a felhő adatkezelési átjáró kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.

||||
|-|-|-|
|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|
|CloudMgr.log|A felhő management gateway szolgáltatás, a folyamatos szolgáltatás állapotának és a használati adatokat a szolgáltatáshoz társított központi telepítésével kapcsolatos adatokat rögzíti.<br>Konfigurálhatja a naplózási szint a beállításjegyzék szerkesztése **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_CLOUD_SERVICES_MANAGER\Logging szint**|A **SMS/Logs** mappa a helyrendszer-kiszolgálón|
|CMGSetup.log vagy CMG -*RoleInstanceID*-CMGSetup.log<sup>1</sup>|A felhő felügyeleti átjáró telepítési (helyi telepítése az Azure-ban) 2. fázis adatait rögzíti.<br>Konfigurálhatja a naplózási szint a beállítással **nyomkövetési szint** (**információk** (alapértelmezett), **részletes**, **hiba**) a a **Azure portal\Cloud konfigurálása** fülre.|A **%approot%\logs** az Azure-kiszolgálóval, vagy az SMS/Logs mappában, a helyrendszer-kiszolgálón|
|CMGHttpHandler.log vagy CMG -*RoleInstanceID*-CMGHttpHandler.log<sup>1</sup>|A felhő felügyeleti átjáró http kezelő kötés Internet Information Services az Azure-ban adatait rögzíti.<br>Konfigurálhatja a naplózási szint a beállítással **nyomkövetési szint** (**információk** (alapértelmezett), **részletes**, **hiba**) a a **Azure portal\Cloud konfigurálása** fülre.|A **%approot%\logs** az Azure-kiszolgálóval, vagy az SMS/Logs mappában, a helyrendszer-kiszolgálón|
|CMGService.log vagy CMG -*RoleInstanceID*-CMGService.log<sup>1</sup>|A felhő felügyeleti átjáró szolgáltatás alapszolgáltatása az Azure-ban adatait rögzíti.<br>Konfigurálhatja a naplózási szint a beállítással **nyomkövetési szint** (**információk** (alapértelmezett), **részletes**, **hiba**) a a **Azure portal\Cloud konfigurálása** fülre.|A **%approot%\logs** az Azure-kiszolgálóval, vagy az SMS/Logs mappában, a helyrendszer-kiszolgálón|
|SMS_Cloud_ProxyConnector.log|Pont a felhő management gateway szolgáltatás és a felhő management gateway-kapcsolatot közötti kapcsolatok beállításával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|

<sup>1</sup> ezek a helyi Configuration Manager naplófájljainak, hogy a service manager szinkronizálás az Azure storage 5 percenként. A felhő adatkezelési átjáró fogja leküldeni a naplók az Azure storage 5 percenként. így a maximális késleltetési 10 perc. Részletes kapcsolók hatással lesz a helyi és távoli naplókat.

- Központi telepítések a hibaelhárításhoz használható **CloudMgr.log** és **CMGSetup.log**
- Hibaelhárítás a szolgáltatás állapotát, használja a **CMGService.log** és **SMS_Cloud_ProxyConnector.log**.
- Hibaelhárítási ügyfélforgalmat, használjon **CMGHttpHandler.log**, **CMGService.log**, és **SMS_Cloud_ProxyConnector.log**.

###  <a name="BKMK_CompSettingsLog"></a>A megfelelőségi beállítások és hozzáférés a vállalati erőforrásokhoz  
 A következő táblázatban található a megfelelőségi beállításokkal és a vállalati erőforrásokhoz való hozzáféréssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|CIAgent.log|A megfelelőségi beállítások, a szoftverfrissítések és az alkalmazáskezelés szervizelési és megfelelőségi folyamatával kapcsolatos adatokat rögzíti.|Ügyfél|  
|CITaskManager.log|A konfigurációelemek feladatütemezésével kapcsolatos adatokat rögzíti.|Ügyfél|  
|DCMAgent.log|A konfigurációelemek és az alkalmazások kiértékelésével, ütközésjelentésével és szervizelésével kapcsolatos áttekintő szintű adatokat rögzíti.|Ügyfél|  
|DCMReporting.log|A házirendplatform eredményeinek a konfigurációelemek állapotüzeneteiben történő jelentésének adatait rögzíti.|Ügyfél|  
|DcmWmiProvider.log|A konfigurációelemek kiolvasásával a WMI kapcsolatos adatokat rögzíti.|Ügyfél|  

###  <a name="BKMK_ConsoleLog"></a>A Configuration Manager konzol  
 A következő táblázat a Configuration Manager konzol kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|ConfigMgrAdminUISetup.log|A Configuration Manager konzol telepítését rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|SmsAdminUI.log|A Configuration Manager konzol működésével kapcsolatos adatokat rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|Smsprov.log|Az SMS-szolgáltató tevékenységét rögzíti. A Configuration Manager konzoljában végrehajtott tevékenységek az SMS-szolgáltatót használják.|Helykiszolgáló vagy a helyrendszer kiszolgálója|  

###  <a name="BKMK_ContentLog"></a>Tartalomkezelés  
 A következő táblázatban található a tartalomkezeléssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|CloudDP -&lt;guid\>.log|A meghatározott felhőalapú terjesztési ponttal kapcsolatos adatokat rögzíti, beleértve a tároló és a tartalom hozzáférését.|Helyrendszer kiszolgálója|  
|CloudMgr.log|Tartalom kiépítése kapcsolatos adatokat rögzíti, tárolási és a sávszélesség statisztikájával, valamint a rendszergazda által kezdeményezett műveletek leállításához vagy elindításához egy felhőalapú terjesztési pontot futtató felhőszolgáltatás gyűjtése.|Helyrendszer kiszolgálója|  
|DataTransferService.log|A BITS összes, házirend- és csomag-hozzáférési kommunikációját rögzíti. Ez a napló is használják a Tartalomkezelés a lekéréses terjesztési pontok.|A lekéréses terjesztési pontként konfigurált számítógép|  
|PullDP.log|A lekéréses terjesztési pont által a forrásként szolgáló terjesztési pontoktól lekért tartalommal kapcsolatos adatokat rögzíti.|A lekéréses terjesztési pontként konfigurált számítógép|  
|PrestageContent.log|Az ExtractContent.exe használatának adatait rögzíti eszköz távoli, manuálisan előkészített terjesztési ponton. Ez az eszköz a fájlba exportált tartalmat bontja ki.|Helyrendszerszerepkör|  
|SMSdpmon.log|Ütemezett feladatok a terjesztési pontokon beállított állapotfigyelési pont telepítési adatait rögzíti.|Helyrendszerszerepkör|  
|smsdpprov.log|Az elsődleges helyekről érkezett tömörített fájlok kibontásával kapcsolatos adatokat rögzíti. Ezt a naplót a távoli terjesztési pont WMI-szolgáltatója állítja elő.|Terjesztési pont számítógépén, amely nem a helykiszolgálóval közös elhelyezésű|  


###  <a name="BKMK_DiscoveryLog"></a>Felderítés  
A következő táblázat a felderítéssel kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|adsgdis.log|Az Active Directory biztonságicsoport-felderítési műveleteit rögzíti.|Helykiszolgáló|  
|adsysdis.log|Az Active Directory rendszer-felderítési műveleteit rögzíti.|Helykiszolgáló|  
|adusrdis.log|Az Active Directory felhasználófelderítési műveleteit rögzíti.|Helykiszolgáló|  
|ADForestDisc.Log|Az Active Directory erdőfelderítési műveleteit rögzíti.|Helykiszolgáló|  
|ddm.log|A felderítésiadat-kezelő tevékenységeit rögzíti.|Helykiszolgáló|  
|InventoryAgent.log|Az ügyfélen végrehajtott hardver- és szoftver-nyilvántartási, valamint szívveréses felderítési műveletek tevékenységeit rögzíti.|Ügyfél|  
|netdisc.log|A hálózatfelderítési műveleteket rögzíti.|Helykiszolgáló|  

###  <a name="BKMK_EPLog"></a>Az Endpoint Protection  
 A következő táblázatban található az Endpoint Protection-kezeléssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|EndpointProtectionAgent.log|Az Endpoint Protection-ügyfél telepítésére és adott ügyfél kártevőirtó-házirendjének alkalmazására vonatkozó adatokat rögzíti.|Ügyfél|  
|EPCtrlMgr.log|A kártevő-fenyegetés adatainak az Endpoint Protection szerepkör kiszolgálóról, a Configuration Manager-adatbázis szinkronizálása kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|EPMgr.log|Az Endpoint Protection helyrendszerszerepkör állapotát figyeli.|Helyrendszer kiszolgálója|  
|EPSetup.log|Az Endpoint Protection helyrendszerszerepkör telepítésével kapcsolatos adatokat tartalmazza.|Helyrendszer kiszolgálója|  

###  <a name="BKMK_Extensions"></a>Bővítmények  
 A következő táblázat a bővítményekkel kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|AdminUI.ExtensionInstaller.log|A Microsofttól letöltött bővítményekkel és az összes bővítmény telepítésével és eltávolításával kapcsolatos adatokat rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|FeatureExtensionInstaller.log|A telepítési és az egyes bővítmények történő engedélyezésekor vagy letiltásakor a Configuration Manager konzol eltávolítására vonatkozó adatokat rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|SmsAdminUI.log|A Configuration Manager konzol tevékenységét rögzíti.|A Configuration Manager konzolt futtató számítógép|  

###  <a name="BKMK_InventoryLog"></a>Szoftverleltár  
 A következő táblázatban található a leltáradatok feldolgozásával kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|dataldr.log|A MIF-fájlok és a Hardverleltár a Configuration Manager adatbázisban feldolgozásával kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|invproc.log|A MIF-fájlok másodlagos helyről annak fölérendelt helyére való továbbítását rögzíti.|Másodlagos hely kiszolgálója|  
|sinvproc.log|A szoftverleltáradatok helyadatbázisba történő feldolgozásának adatait rögzíti.|Helykiszolgáló|  

###  <a name="BKMK_MeteringLog"></a>Szoftverhasználat-mérő  
 A következő táblázatban található a méréssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|mtrmgr.log|Az összes szoftverhasználat-mérési folyamatot figyeli.|Helykiszolgáló|  

###  <a name="BKMK_MigrationLog"></a>Áttelepítés  
 A következő táblázatban található az áttelepítéssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|migmctrl.log|Az áttelepítési műveletek, például az áttelepítési munkák, a megosztott terjesztési pontok és a terjesztési pontok frissítéseinek adatait rögzíti.|A Configuration Manager-hierarchia felső szintű helye végzi, és az összes alárendelt elsődleges hely.<br /><br /> A több elsődleges helyet tartalmazó hierarchiában használja a központi felügyeleti helyen létrehozott naplófájlt.|  

###  <a name="BKMK_MDMLog"></a>Mobileszközök  
 Az alábbi szakaszok a mobileszközök felügyeletével kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

####  <a name="BKMK_EnrollmentLog"></a>Regisztráció  
 A következő táblázatban található a mobileszközök beléptetésével kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|DMPRP.log|A mobileszközökhöz és a felügyeleti ponti végpontokhoz engedélyezett felügyeleti pontok közötti kommunikációt rögzíti.|Helyrendszer kiszolgálója|  
|dmpmsi.log|A mobileszközökhöz engedélyezett felügyeleti pont konfigurációjának Windows Installer-adatait rögzíti.|Helyrendszer kiszolgálója|  
|DMPSetup.log|A felügyeleti pont konfigurációját rögzíti, amikor az engedélyezve van a mobileszközökhöz.|Helyrendszer kiszolgálója|  
|enrollsrvMSI.log|A beléptetési pontok konfigurációjának Windows Installer-adatait rögzíti.|Helyrendszer kiszolgálója|  
|enrollmentweb.log|A mobileszközök és a beléptetési proxypont közötti kommunikációt rögzíti.|Helyrendszer kiszolgálója|  
|enrollwebMSI.log|A beléptetési proxypontok konfigurációjának Windows Installer-adatait rögzíti.|Helyrendszer kiszolgálója|  
|enrollmentservice.log|A beléptetési proxypontok és a beléptetési pontok közötti kommunikációt rögzíti.|Helyrendszer kiszolgálója|  
|SMS_DM.log|Mobileszközök, Mac számítógépek és a mobileszközök és Mac számítógépekhez engedélyezett felügyeleti pont közötti kommunikációt rögzíti.|Helyrendszer kiszolgálója|  

####  <a name="BKMK_ExchSrvLog"></a>Exchange Server-összekötő  
 A következő naplók kapcsolódnak az Exchange Server-összekötővel kapcsolatos adatokat tartalmazza.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|easdisc.log|Az Exchange Server-összekötő tevékenységeit és állapotát rögzíti.|Helykiszolgáló|  

####  <a name="BKMK_MDLegLog"></a>Hagyományos mobileszköz  
 A következő táblázatban található a hagyományos mobileszközökkel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|DmCertEnroll.log|A hagyományos mobileszközök tanúsítványbeléptetési adataival kapcsolatos információt rögzíti.|Ügyfél|  
|DMCertResp.htm|A tanúsítványkiszolgáló HTML-válaszát rögzíti, amikor a hagyományos mobileszközök beléptetési programja PKI-tanúsítványt kér.|Ügyfél|  
|DmClientHealth.log|A mobileszközökhöz engedélyezett felügyeleti ponttal kommunikáló összes mobileszközön lévő korábbi ügyfelek azonosítóját rögzíti.|Helyrendszer kiszolgálója|  
|DmClientRegistration.log|A hagyományos mobileszközök regisztrálási kérelmeit és válaszait rögzíti.|Helyrendszer kiszolgálója|  
|DmClientSetup.log|A hagyományos mobileszközök ügyfél-telepítési adatait rögzíti.|Ügyfél|  
|DmClientXfer.log|A hagyományos mobileszközök és az ActiveSync-telepítések ügyfélátviteli adatait rögzíti.|Ügyfél|  
|DmCommonInstaller.log|Az ügyfelek átviteli fájljának a hagyományos mobileszközök átviteli fájljainak konfigurálásához végrehajtott telepítését rögzíti.|Ügyfél|  
|DmInstaller.log|Azt rögzíti, hogy a DMInstaller helyesen hívja-e meg a DmClientSetup eljárást, és hogy a DmClientSetup a művelet sikeres végrehajtásával vagy hibajelzéssel lép-e ki a hagyományos mobileszközök esetében.|Ügyfél|  
|DmpDatastore.log|A mobileszközökhöz engedélyezett felügyeleti pont által végrehajtott összes helyadatbázis-kapcsolatot és lekérdezést rögzíti.|Helyrendszer kiszolgálója|  
|DmpDiscovery.log|A mobileszközökhöz engedélyezett felügyeleti ponton lévő hagyományos mobileszközök felderítési adatait rögzíti.|Helyrendszer kiszolgálója|  
|DmpHardware.log|A mobileszközökhöz engedélyezett felügyeleti ponton lévő hagyományos mobileszközök hardverleltáradatait rögzíti.|Helyrendszer kiszolgálója|  
|DmpIsapi.log|A hagyományos mobileszközök és a mobileszközökhöz engedélyezett felügyeleti pont kommunikációját rögzíti.|Helyrendszer kiszolgálója|  
|dmpmsi.log|A mobileszközökhöz engedélyezett felügyeleti pont konfigurációjának Windows Installer-adatait rögzíti.|Helyrendszer kiszolgálója|  
|DMPSetup.log|A felügyeleti pont konfigurációját rögzíti, amikor az engedélyezve van a mobileszközökhöz.|Helyrendszer kiszolgálója|  
|DmpSoftware.log|A mobileszközökhöz engedélyezett felügyeleti ponton lévő hagyományos mobileszközök szoftverterjesztési adatait rögzíti.|Helyrendszer kiszolgálója|  
|DmpStatus.log|A mobileszközökhöz engedélyezett felügyeleti ponton lévő mobileszközök állapotüzenet-adatait rögzíti.|Helyrendszer kiszolgálója|  
|DmSvc.log|A hagyományos mobileszközök és a mobileszközökhöz engedélyezett felügyeleti pont ügyfél-kommunikációját rögzíti.|Ügyfél|  
|FspIsapi.log|A hagyományos mobileszközök és az ügyfélszámítógépek, valamint a tartalék állapotkezelő pont kommunikációjának adatait rögzíti.|Helyrendszer kiszolgálója|  

###  <a name="BKMK_OSDLog"></a>Operációs rendszer központi telepítése  
 A következő táblázatban található az operációs rendszer telepítésével kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|CAS.log|A hivatkozott tartalomhoz talált terjesztési pontok adatait rögzíti.|Ügyfél|  
|ccmsetup.log|Az ügyfelek telepítéséhez, frissítéséhez és eltávolításához ccmsetup feladatokat rögzíti. Az ügyfél-telepítési problémák megoldásához használható.|Ügyfél|  
|CreateTSMedia.log|A feladatütemezési adathordozó létrehozási adatait rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|DeployToVhd.log|A virtuális merevlemez (VHD) létrehozási és -módosítási folyamat adatait rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|Dism.log|Illesztőprogram telepítési vagy frissítési kérelem műveletekről offline karbantartáshoz rögzíti.|Helyrendszer kiszolgálója|  
|Distmgr.log|A terjesztési pont a Preboot Execution Environment (PXE) engedélyezéséhez szükséges konfiguráció adatait rögzíti.|Helyrendszer kiszolgálója|  
|DriverCatalog.log|Az illesztőprogram-katalógusba importált illesztőprogramokkal kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|mcsisapi.log|A csoportos küldésű csomagok átvitelével és az ügyfélkérelmek válaszaival kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|mcsexec.log|Rögzíti az állapot-ellenőrzéssel, a névtér, a munkamenet-létrehozással és a tanúsítvány ellenőrizze a műveletek.|Helyrendszer kiszolgálója|  
|mcsmgr.log|Konfiguráció, a biztonsági üzemmód és a rendelkezésre állás módosításait rögzíti.|Helyrendszer kiszolgálója|  
|mcsprv.log|A csoportos küldési szolgáltató és a WDS (Windows Deployment Services) interakcióját rögzíti.|Helyrendszer kiszolgálója|  
|MCSSetup.log|A csoportos küldési kiszolgáló szerepkör telepítésével kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|MCSMSI.log|A csoportos küldési kiszolgáló szerepkör telepítésével kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|Mcsperf.log|A csoportos küldési teljesítményszámláló frissítéseivel kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|MP_ClientIDManager.log|A felügyeleti pont által a PXE vagy a rendszerindító adathordozó által küldött ügyfél-azonosítási feladatütemezés-kérelmekre adott válaszokat rögzíti.|Helyrendszer kiszolgálója|  
|MP_DriverManager.log|A felügyeleti pont által az illesztőprogramok automatikus alkalmazását végrehajtó feladatütemezés műveleti kérelmeire adott válaszokat rögzíti.|Helyrendszer kiszolgálója|  
|OfflineServicingMgr.log|Kapcsolat nélküli karbantartási ütemezését és a frissítés kapcsolatos adatokat rögzíti az operációs rendszer Windows Imaging Format (WIM) fájl műveletek alkalmazása.|Helyrendszer kiszolgálója|  
|Setupact.log|A Windows Sysprep és a telepítési naplók részleteit rögzíti.|Ügyfél|  
|Setupapi.log|A Windows Sysprep és a telepítési naplók részleteit rögzíti.|Ügyfél|  
|Setuperr.log|A Windows Sysprep és a telepítési naplók részleteit rögzíti.|Ügyfél|  
|smpisapi.log|Az ügyfélállapot rögzítési és helyreállítási műveleteivel, valamint a küszöbértékkel kapcsolatos adatokat rögzíti.|Ügyfél|  
|Smpmgr.log|Az állapotáttelepítési pont állapot-ellenőrzési eredményeire és a konfigurációmódosításokra vonatkozó adatokat rögzíti.|Helyrendszer kiszolgálója|  
|smpmsi.log|Az állapotáttelepítési pont telepítésével és konfigurálásával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|smpperf.log|Az állapotáttelepítési pont teljesítményszámlálójának frissítéseivel kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|smspxe.log|PXE-rendszerindításhoz és a rendszerindító lemezképek és rendszerindító fájlok kibővítésével kapcsolatos adatokat használó ügyfelek által küldött válaszokkal kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|smssmpsetup.log|Az állapotáttelepítési pont telepítésével és konfigurálásával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|Smsts.log|A feladatütemezés tevékenységeit rögzíti.|Ügyfél|  
|TSAgent.log|A feladatütemezések indítás előtti függőségeinek eredményeit rögzíti.|Ügyfél|  
|TaskSequenceProvider.log|A feladatok importálásával, exportálásával vagy szerkesztésével kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|loadstate.log|A Felhasználóiállapot-áttelepítő eszközzel (USMT) és a felhasználói állapotadatok helyreállításával kapcsolatos adatokat rögzíti.|Ügyfél|  
|scanstate.log|A Felhasználóiállapot-áttelepítő eszközzel (USMT) és a felhasználói állapotadatok rögzítésével kapcsolatos adatokat rögzíti.|Ügyfél|  

###  <a name="BKMK_PowerMgmtLog"></a>Energiagazdálkodás  
 A következő táblázatban található az energiagazdálkodással kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|pwrmgmt.log|Energiagazdálkodási tevékenységek az ügyfélszámítógépen, beleértve a felügyeletéhez és a beállítások az energiagazdálkodási Ügyfélügynök használatával kapcsolatos adatokat rögzíti.|Ügyfél|  

###  <a name="BKMK_RCLog"></a>Távvezérlés  
 A következő táblázatban található a távvezérléssel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|CMRcViewer.log|A távvezérlés megjelenítőjének tevékenységével kapcsolatos adatokat rögzíti.|A távvezérlés megjelenítőjét futtató számítógép % temp % mappában|  

###  <a name="BKMK_ReportLog"></a>Jelentéskészítés  
 Az alábbi táblázat a jelentéskészítéssel kapcsolatos adatokat tartalmazó Configuration Manager naplófájlokat.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|srsrp.log|A jelentéskészítési szolgáltatási pont tevékenységével és állapotával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|srsrpMSI.log|A jelentéskészítési szolgáltatási pont telepítési folyamatának részletes eredményeit rögzíti az MSI-kimenetből.|Helyrendszer kiszolgálója|  
|srsrpsetup.log|A jelentéskészítési szolgáltatási pont telepítési folyamatának eredményeit rögzíti.|Helyrendszer kiszolgálója|  

###  <a name="BKMK_RBALog"></a>Szerepkör alapú felügyelet  
 A következő táblázatban található a szerepköralapú rendszergazdai felügyelettel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|hman.log|A hely konfigurálási változtatásaira és a helyadatok közzétételére az Active Directory tartományi szolgáltatásokban kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|SMSProv.log|A WMI-szolgáltató helyadatbázishoz való hozzáférését rögzíti.|Az SMS Provider eszközt futtató számítógép|  

###  <a name="BKMK_WITLog"></a>Szolgáltatáskapcsolódási pont  
 A következő táblázat a szolgáltatáskapcsolódási pont telepítésével kapcsolatos adatokat tartalmazó naplófájlokat ismerteti.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|CertMgr.log|A tanúsítvány és a proxyfiók adatait rögzíti.|Helykiszolgáló|  
|CollEval.log|A gyűjteménykiértékelő által létrehozott, módosított és törölt gyűjteményekről szóló információkat rögzíti.|Elsődleges hely és központi felügyeleti hely|  
|Cloudusersync.log|A felhasználóknak engedélyezett licencekkel kapcsolatos adatokat rögzíti.|A szolgáltatáskapcsolódási ponttal rendelkező számítógép|  
|Dataldr.log|A MIF-fájlok feldolgozásával kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|ddm.log|A felderítésiadat-kezelő tevékenységeit rögzíti.|Helykiszolgáló|  
|Distmgr.log|A tartalomterjesztési kérelmekkel kapcsolatos adatokat rögzíti.|Legfelső szintű helykiszolgáló|  
|Dmpdownloader.log|A Microsoft Intune-ból letöltött fájl adatait rögzíti.|A szolgáltatáskapcsolódási ponttal rendelkező számítógép|  
|Dmpuploader.log|Adatbázis-változást visszaállított feltöltése a Microsoft Intune kapcsolatos adatokat rögzíti.|A szolgáltatáskapcsolódási ponttal rendelkező számítógép|  
|hman.log|Az üzenettovábbítással kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|objreplmgr.log|Az irányelv és a hozzárendelés feldolgozását rögzíti.|Elsődleges hely kiszolgálója|  
|PolicyPV.log|Az összes irányelv előállítását rögzíti.|Helykiszolgáló|  
|outgoingcontentmanager.log|A Microsoft Intune alkalmazásba feltöltött tartalmat rögzíti.|A szolgáltatáskapcsolódási ponttal rendelkező számítógép|  
|Sitecomp.log|A szolgáltatáskapcsolódási pont telepítésével kapcsolatos adatokat rögzíti.|Helykiszolgáló|  
|SmsAdminUI.log|A Configuration Manager konzol tevékenységét rögzíti.|A Configuration Manager konzolt futtató számítógép|  
|Smsprov.log|Az SMS-szolgáltató tevékenységét rögzíti. A Configuration Manager konzoljában végrehajtott tevékenységek az SMS-szolgáltatót használják.|Az SMS Provider eszközt futtató számítógép|  
|SrvBoot.log|A szolgáltatáskapcsolódási pont telepítési szolgáltatásával kapcsolatos adatokat rögzíti.|A szolgáltatáskapcsolódási ponttal rendelkező számítógép|  
|Statesys.log|A mobileszközök felügyeleti üzeneteinek feldolgozását rögzíti.|Elsődleges hely és központi felügyeleti hely|  

###  <a name="BKMK_SU_NAPLog"></a>Szoftverfrissítések  
 A következő táblázat a szoftverfrissítésekkel kapcsolatos adatokat tartalmazó naplófájlokat ismerteti.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|ccmperf.log|Az ügyfél teljesítményszámlálóival kapcsolatos adatok karbantartására és gyűjtésére vonatkozó tevékenységeket rögzíti.|Ügyfél|  
|PatchDownloader.log|A szoftverfrissítéseknek a frissítési forrásból a helykiszolgálón lévő frissítési forrásból történő letöltési folyamatának adatait rögzíti.|A Configuration Manager konzolt, amely a letölthető elemet üzemeltető számítógépen|  
|PolicyEvaluator.log|Az ügyfélszámítógépeken a házirendek (beleértve a szoftverfrissítésekből származó házirendeket is) kiértékelésére vonatkozó részletes adatokat rögzíti.|Ügyfél|  
|RebootCoordinator.log|Az ügyfélgépeken a szoftverfrissítések telepítése után végrehajtott rendszer-újraindítások koordinálásának adatait rögzíti.|Ügyfél|  
|ScanAgent.log|A szoftverfrissítések vizsgálati kérelmeire, a WSUS-helyekre és a kapcsolódó műveletekre vonatkozó adatokat rögzíti.|Ügyfél|  
|SdmAgent.log|A követési szervizelési és megfelelőségi adatait rögzíti. Azonban a szoftver frissítések naplófájl, Updateshandler.log, ismerteti még informatívabbá a megfelelőségi a szükséges szoftverfrissítések telepítése.<br /><br /> Ezt a naplófájlt a rendszer a megfelelőségi beállításokhoz is használja.|Ügyfél|  
|ServiceWindowManager.log|A karbantartási időszakok kiértékelésével kapcsolatos adatokat rögzíti.|Ügyfél|  
|SmsWusHandler.log|A Microsoft-frissítések leltározási eszközének vizsgálati folyamatával kapcsolatos adatokat rögzíti.|Ügyfél|  
|StateMessage.log|A szoftverrel kapcsolatos adatokat rögzíti frissítése létrehozott és a felügyeleti pontra küldött állapotüzenetek.|Ügyfél|  
|SUPSetup.log|A szoftverfrissítési pont telepítésével kapcsolatos adatokat rögzíti. A szoftverfrissítési pont telepítésének befejezése után a rendszer a következő bejegyzést írja a naplófájlba: **Installation was successful** (A telepítés sikeres volt).|Helyrendszer kiszolgálója|  
|UpdatesDeployment.log|Az ügyfélen végrehajtott központi telepítések adatait rögzíti, beleértve a szoftverfrissítés aktiválását, kiértékelését és kényszerített érvényesítését. A részletes naplózás további információval is szolgál az ügyfél felhasználói felületén végzett műveletekről.|Ügyfél|  
|UpdatesHandler.log|A szoftverfrissítés megfelelőségi vizsgálatának adatait, valamint a szoftverfrissítések letöltésével és az ügyfélen végrehajtott telepítésével kapcsolatos adatokat tartalmazza.|Ügyfél|  
|UpdatesStore.log|A megfelelőségi vizsgálat során ellenőrzött szoftverfrissítések megfelelőségi állapotával kapcsolatos adatokat rögzíti.|Ügyfél|  
|WCM.log|Szoftverfrissítésekkel kapcsolatos adatokat rögzíti az előfizetett frissítési kategóriákat, besorolásokat és nyelveket a WSUS-kiszolgáló frissítése pontok konfigurációi és a kapcsolatok.|Helykiszolgáló|  
|WSUSCtrl.log|A hely WSUS-kiszolgálójának konfigurációjával, adatbázis-kapcsolatával és állapotával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|wsyncmgr.log|A szoftverfrissítésekkel kapcsolatos adatokat rögzíti a szinkronizálási folyamat frissíteni.|Helykiszolgáló|  
|WUAHandler.log|A Windows Update Agent ügyfélen végzett tevékenységével kapcsolatos adatokat rögzíti, amikor az ügynök szoftverfrissítéseket keres.|Ügyfél|  

###  <a name="BKMK_WOLLog"></a>Hálózati ébresztés  
 A következő táblázat a hálózati ébresztés használatával kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

> [!NOTE]  
>  Ha a hálózati ébresztést kiegészíti az ébresztési proxy használatával, ez a tevékenység naplózza az ügyfélen. Például lásd a CcmExec.log és a SleepAgent_ <*tartomány* \> @SYSTEM_0.log a a [Ügyfélműveletek](#BKMK_ClientOpLogs) című szakaszát.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|wolcmgr.log|Azokkal az ügyfelekkel kapcsolatos adatokat rögzíti, amelyeknek ébresztési csomagot kell küldeni, valamint az elküldött ébresztési csomagok számát és az újraküldött ébresztési csomagok számát is rögzíti.|Helykiszolgáló|  
|wolmgr.log|Az ébresztési eljárásokkal kapcsolatos adatokat rögzíti, például a hálózati ébresztésre konfigurált központi telepítések ébresztésének időpontját.|Helykiszolgáló|  

###  <a name="BKMK_WindowsServicingLog"></a>Windows 10 karbantartása  
 A következő táblázat a Windows 10 karbantartásával kapcsolatos adatokat tartalmazó naplófájlokat sorolja fel.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|ccmperf.log|Az ügyfél teljesítményszámlálóival kapcsolatos adatok karbantartására és gyűjtésére vonatkozó tevékenységeket rögzíti.|Ügyfél|  
|CcmRepair.log|Az ügyfélügynök javítási tevékenységeit rögzíti.|Ügyfél|
|PatchDownloader.log|A szoftverfrissítéseknek a frissítési forrásból a helykiszolgálón lévő frissítési forrásból történő letöltési folyamatának adatait rögzíti.|A Configuration Manager konzolt, amely a letölthető elemet üzemeltető számítógépen|  
|PolicyEvaluator.log|Az ügyfélszámítógépeken a házirendek (beleértve a szoftverfrissítésekből származó házirendeket is) kiértékelésére vonatkozó részletes adatokat rögzíti.|Ügyfél|  
|RebootCoordinator.log|Az ügyfélgépeken a szoftverfrissítések telepítése után végrehajtott rendszer-újraindítások koordinálásának adatait rögzíti.|Ügyfél|  
|ScanAgent.log|A szoftverfrissítések vizsgálati kérelmeire, a WSUS-helyekre és a kapcsolódó műveletekre vonatkozó adatokat rögzíti.|Ügyfél|  
|SdmAgent.log|A követési szervizelési és megfelelőségi adatait rögzíti. Azonban a szoftver frissítések naplófájl, UpdatesHandler.log, ismerteti még informatívabbá a megfelelőségi a szükséges szoftverfrissítések telepítése.<br /><br /> Ezt a naplófájlt a rendszer a megfelelőségi beállításokhoz is használja.|Ügyfél|  
|ServiceWindowManager.log|A karbantartási időszakok kiértékelésével kapcsolatos adatokat rögzíti.|Ügyfél|  
|Setupact.log|A Windows-telepítési folyamat során felmerülő leggyakoribb hibák tartozó elsődleges naplófájl. A naplófájl a % windir % található\$Windows.~BT\sources\panther mappa.|Ügyfél|
|SmsWusHandler.log|A Microsoft-frissítések leltározási eszközének vizsgálati folyamatával kapcsolatos adatokat rögzíti.|Ügyfél|  
|StateMessage.log|A szoftverfrissítések létrehozott és a felügyeleti pontnak elküldött állapotüzeneteivel kapcsolatos adatokat rögzíti.|Ügyfél|  
|SUPSetup.log|A szoftverfrissítési pont telepítésével kapcsolatos adatokat rögzíti. A szoftverfrissítési pont telepítésének befejezése után a rendszer a következő bejegyzést írja a naplófájlba: **Installation was successful** (A telepítés sikeres volt).|Helyrendszer kiszolgálója|  
|UpdatesDeployment.log|Az ügyfélen végrehajtott központi telepítések adatait rögzíti, beleértve a szoftverfrissítés aktiválását, kiértékelését és kényszerített érvényesítését. A részletes naplózás további információval is szolgál az ügyfél felhasználói felületén végzett műveletekről.|Ügyfél|  
|Updateshandler.log|A szoftverfrissítés megfelelőségi vizsgálatának adatait, valamint a szoftverfrissítések letöltésével és az ügyfélen végrehajtott telepítésével kapcsolatos adatokat tartalmazza.|Ügyfél|  
|UpdatesStore.log|A megfelelőségi vizsgálat során ellenőrzött szoftverfrissítések megfelelőségi állapotával kapcsolatos adatokat rögzíti.|Ügyfél|  
|WCM.log|Szoftverfrissítésekkel kapcsolatos adatokat rögzíti az előfizetett frissítési kategóriákat, besorolásokat és nyelveket a WSUS-kiszolgáló frissítése pontok konfigurációi és a kapcsolatok.|Helykiszolgáló|  
|WSUSCtrl.log|A hely WSUS-kiszolgálójának konfigurációjával, adatbázis-kapcsolatával és állapotával kapcsolatos adatokat rögzíti.|Helyrendszer kiszolgálója|  
|wsyncmgr.log|A szoftverfrissítésekkel kapcsolatos adatokat rögzíti a szinkronizálási folyamat frissíteni.|Helykiszolgáló|  
|WUAHandler.log|A Windows Update Agent ügyfélen végzett tevékenységével kapcsolatos adatokat rögzíti, amikor az ügynök szoftverfrissítéseket keres.|Ügyfél|  

###  <a name="BKMK_WULog"></a>A Windows Update Agent  
 A következő táblázatban található a Windows Update Agenttel kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|WindowsUpdate.log|Amikor a Windows Update Agent a WSUS-kiszolgálóhoz csatlakozik, és lekéri a szoftverfrissítéseket a megfelelőség ellenőrzéséhez kapcsolatos adatokat rögzíti, és hogy van-e frissítések az ügynökösszetevőkhöz.|Ügyfél|  

###  <a name="BKMK_WSUSLog"></a>WSUS-kiszolgáló  
 A következő táblázatban található a WSUS-kiszolgálóval kapcsolatos adatokat tartalmazó naplófájlok felsorolása.  

|Napló neve|Leírás|Naplófájlt tartalmazó számítógép|  
|--------------|-----------------|----------------------------|  
|Change.log|A adatbázisában módosított információval WSUS-kiszolgálóval kapcsolatos adatokat rögzíti.|WSUS-kiszolgáló|  
|SoftwareDistribution.log|A WSUS-kiszolgáló adatbázisába szinkronizált a konfigurált frissítési forrásból a szoftverfrissítésekkel kapcsolatos adatokat rögzíti.|WSUS-kiszolgáló|  

