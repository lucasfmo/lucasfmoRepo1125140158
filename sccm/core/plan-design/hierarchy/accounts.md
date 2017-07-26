---
title: "A Configuration Manager által használt fiókok |} Microsoft Docs"
description: "Határozza meg és kezelheti a Windows-csoportok és a fiókok a System Center Configuration Managerben."
ms.custom: na
ms.date: 2/9/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 72d7b174-f015-498f-a0a7-2161b9929198
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 72263ec5e7104924a1ca46dc2000be9f8568599f
ms.openlocfilehash: a776667cc9f24bd4a468afea76e466c34ce66864
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="accounts-used-in-system-center-configuration-manager"></a>A System Center Configuration Managerben használt fiókok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A következő információk segítségével azonosíthatja a Windows-csoportokat és a fiókjait, amelyek a System Center Configuration Manager, a azok használata és a kapcsolódó követelményekkel.  

## <a name="windows-groups-that-configuration-manager-creates-and-uses"></a>A Configuration Manager által létrehozott és használt Windows-csoportok  
 A Configuration Manager automatikusan hoz létre, és számos esetben automatikusan is kezeli, az alábbi Windows-csoportokat.  

> [!NOTE]  
>  A Configuration Manager létrehoz egy csoportot a számítógépen, amely tagja egy tartománynak, a csoport esetén a helyi biztonsági csoport. Ha a számítógép tartományvezérlő, a csoport a tartomány összes tartományvezérlője körében megosztott tartományi helyi csoport lesz.  


### <a name="configmgrcollectedfilesaccess"></a>ConfigMgr_CollectedFilesAccess  
Configuration Manager használja ezt a csoportot a szoftverleltár által összegyűjtött fájlok megtekintésére ad engedélyt.  

A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez az elsődleges hely kiszolgálóján létrehozott helyi biztonsági csoport.<br /><br /> Ha eltávolít egy helyet, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni.|  
|Tagság|A Configuration Manager automatikusan kezeli a csoporttagságot. A csoport tagjai közé azok a rendszergazdák tartoznak, akik egy hozzárendelt biztonsági szerepkör alapján **Összegyűjtött fájlok megtekintése** engedéllyel rendelkeznek a **Gyűjtemény** biztonságos objektumhoz.|  
|Engedélyek|Alapértelmezés szerint ez a csoport rendelkezik **olvasási** engedéllyel a következő mappához a helykiszolgálón: **%path%\Microsoft Configuration Manager\sinv.box\FileCol**.|  

### <a name="configmgrdviewaccess"></a>ConfigMgr_DViewAccess  
 Ez a csoport, amely a Configuration Manager létrehozza a Helyadatbázis-kiszolgáló vagy az adatbázisreplika-kiszolgáló helyi biztonsági csoport. Jelenleg nincs használatban, de későbbi használatra fenntartva.  

### <a name="configmgr-remote-control-users"></a>A ConfigMgr távvezérlést végző felhasználói  
 A Configuration Manager távoli eszközök fiókokat és csoportokat, amelyek az egyes ügyfelekhez rendelt feljogosított megjelenítők listájával beállítása tárolására használhatja ezt a csoportot.  

 A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez a csoport, amikor az ügyfél megkapja a házirendet, amely a távvezérlési eszközöket engedélyező a Configuration Manager-ügyfélen létrehozott helyi biztonsági csoport.<br /><br /> Miután az ügyfél letiltja a távvezérlési eszközöket, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni minden ügyfélszámítógépről.|  
|Tagság|Ennek a csoportnak nincsenek alapértelmezett tagjai. A rendszer a feljogosított megjelenítők listájára felvett felhasználókat adja hozzá automatikusan ehhez a csoporthoz.<br /><br /> Közvetlenül ne vegyen fel ide felhasználókat és csoportokat, hanem a feljogosított megjelenítők listájával kezelje a csoport tagságát.<br /><br /> Nem csak feljogosított megjelenítőnek, a rendszergazdának rendelkeznie kell a **távvezérlési** engedéllyel a **gyűjtemény** objektum. Ez az engedély a Távolieszköz-kezelő biztonsági szerepkörrel osztható ki.|  
|Engedélyek|Alapértelmezés szerint ez a csoport nincs engedélye a számítógép helyekhez. Csak a feljogosított megjelenítők listájának tárolására szolgál.|  

### <a name="sms-admins"></a>SMS rendszergazdák  
 A Configuration Manager ezt a csoportot a hozzáférést az SMS-szolgáltatóhoz, a Windows Management Instrumentation (WMI) keresztül. Az SMS-szolgáltatóhoz való hozzáférésre megtekintése és módosítása a Configuration Manager konzolon objektumok szükséges.  

> [!NOTE]  
>  Egy rendszergazda felhasználó a szerepköralapú Adminisztráció szerinti konfigurációja határozza meg, milyen objektumokat tekinthet meg és kezelheti a Configuration Manager konzol használata esetén.  

 A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez a csoport minden számítógépen, amelyen az SMS-szolgáltatók létrehozott helyi biztonsági csoport.<br /><br /> Ha eltávolít egy helyet, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni.|  
|Tagság|A Configuration Manager automatikusan kezeli a csoporttagságot. Alapértelmezés szerint az SMS rendszergazdák csoportjának a hely minden egyes SMS Provider eszközt futtató számítógépén tagja a hierarchia valamennyi rendszergazdája, valamint a helykiszolgáló számítógépéhez tartozó fiók.|  
|Engedélyek|Az SMS rendszergazdák csoport jogosultságai és engedélyei a WMI-vezérlő MMC beépülő modulban állíthatók. Alapértelmezés szerint az SMS rendszergazdák csoport rendelkezik **fiók engedélyezése** és **távoli engedélyezés** a Root\SMS névtéren. Hitelesített felhasználók **metódusok végrehajtása**, **szolgáltató írása**, és **fiók engedélyezése**.<br /><br /> Rendszergazda felhasználók, akik használni fogják a távoli Configuration Manager konzol a helykiszolgáló számítógépén, mind az SMS Provider számítógép Távoli aktiválás DCOM-engedély szükséges. Az egyszerűbb felügyelet érdekében ezeket a jogokat ajánlott az SMS rendszergazdáknak adni, közvetlenül a felhasználók vagy csoportok helyett. További információt [A System Center Configuration Manager infrastruktúrájának módosítása](../../../core/servers/manage/modify-your-infrastructure.md) témakör [DCOM-engedélyek konfigurálása a távoli Configuration Manager konzolhoz](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ConfigDCOMforRemoteConsole) című szakaszában talál.|  

### <a name="smssitesystemtositeserverconnectionmpltsitecode"></a>SMS_SiteSystemToSiteServerConnection_MP_&lt;Helykód\>  
 A helykiszolgálóhoz képest távoli felügyeleti pontok a Configuration Manager a csoport segítségével csatlakozzon a helyadatbázishoz. A csoport hozzáférést biztosít a felügyeleti pont számára a helykiszolgálón és a helyadatbázison található Beérkezett üzenetek mappákhoz.  

 A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez a csoport minden számítógépen, amelyen az SMS-szolgáltatók létrehozott helyi biztonsági csoport.<br /><br /> Ha eltávolít egy helyet, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni.|  
|Tagság|A Configuration Manager automatikusan kezeli a csoporttagságot. A csoportba alapértelmezés szerint az olyan számítógépek fiókjai tartoznak, amelyek felügyeleti ponttal rendelkeznek az adott helyhez.|  
|Engedélyek|Alapértelmezés szerint ez a csoport rendelkezik **olvasási**, **olvasási & hajtható végre**, és **mappa tartalmának listázása** engedéllyel a **%path%\Microsoft Configuration Manager\inboxes** mappájában a helykiszolgálón. Ez a csoport rendelkezik engedéllyel **írási** almappákhoz a **inboxes** való, amelyek a felügyeleti pont az ügyféladatokat.|  

### <a name="smssitesystemtositeserverconnectionsmsprovltsitecode"></a>SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;Helykód\>  
 A Configuration Manager SMS Provider-számítógépei, amelyek a helykiszolgálótól távol használhatja ezt a csoportot a helyrendszer-kiszolgálóhoz való csatlakozáshoz.  

 A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez a csoport a helykiszolgálón létrehozott helyi biztonsági csoport.<br /><br /> Ha eltávolít egy helyet, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni.|  
|Tagság|A Configuration Manager automatikusan kezeli a csoporttagságot. Alapértelmezés szerint a csoportba tartozik, a számítógép fiókja vagy a tartományi felhasználói fiók, amely minden egyes távoli számítógépről, amely a helyhez tartozó SMS-szolgáltató telepítve van a helykiszolgálóhoz való kapcsolódásra szolgál.|  
|Engedélyek|Alapértelmezés szerint ez a csoport rendelkezik **olvasási**, **olvasási & hajtható végre**, és **mappa tartalmának listázása** engedéllyel a **%path%\Microsoft Configuration Manager\inboxes** mappájában a helykiszolgálón. Ez a csoport rendelkezik engedéllyel **írási** engedéllyel vagy **írási** és **módosítás** almappákhoz a **beérkezettfájl-tárolók** , amelyre az SMS Provider hozzáférést igényel.<br /><br /> Ez a csoport is rendelkezik **olvasási**, **olvasási & hajtható végre**, **mappa tartalmának listázása**, **írási**, és **módosítás** alatti mappákhoz engedélyek **%path%\Microsoft Configuration Manager\OSD\boot** és **olvasási** alatti mappákhoz engedély **%path%\Microsoft Configuration Manager\OSD\Bin** a helykiszolgálón.|  

### <a name="smssitesystemtositeserverconnectionstatltsitecode"></a>SMS_SiteSystemToSiteServerConnection_Stat_&lt;Helykód\>  
 A Configuration Manager távoli helyrendszeri számítógépeken Fájlküldéskezelő ezt a csoportot használja a helykiszolgálóhoz való kapcsolódásra.  

 A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez a csoport a helykiszolgálón létrehozott helyi biztonsági csoport.<br /><br /> Ha eltávolít egy helyet, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni.|  
|Tagság|A Configuration Manager automatikusan kezeli a csoporttagságot. A csoportba alapértelmezés szerint a helykiszolgálóhoz való kapcsolódásra szolgáló számítógépfiók vagy tartományi felhasználói fiók tartozik a helyrendszer minden olyan távoli számítógépéről, amely a fájlküldéskezelőt futtatja.|  
|Engedélyek|Alapértelmezés szerint ez a csoport rendelkezik **olvasási**, **olvasási & hajtható végre**, és **mappa tartalmának listázása** engedéllyel a **%path%\Microsoft Configuration Manager\inboxes** mappában és annak almappáiban alatt erre a helyre, a helykiszolgálón. Ez a csoport rendelkezik engedéllyel **írási** és **módosítás** számára a **%path%\Microsoft Configuration Manager\inboxes\statmgr.box** mappájában a helykiszolgálón.|  

### <a name="smssitetositeconnectionltsitecode"></a>SMS_SiteToSiteConnection_&lt;Helykód\>  
 A Configuration Manager ezt a csoportot használja a hierarchiában lévő helyek közötti fájlalapú replikáció engedélyezéséhez. Minden egyes távoli hely, amely közvetlenül küld fájlokat erre a webhelyre, ez a csoport-kiszolgálóként beállított fiók rendelkezik egy **fájlreplikációs fiókként**.  

 A következő táblázat a csoport további adatait tartalmazza:  

|Adat|További információ|  
|------------|----------------------|  
|Típus és hely|Ez a csoport a helykiszolgálón létrehozott helyi biztonsági csoport.|  
|Tagság|Ha egy új helyet telepít egy másik hely gyermekeként, a Configuration Manager automatikusan hozzáadja az új hely számítógépfiókját a szülő helykiszolgáló csoportjához. A Configuration Manager is hozzáad a szülő hely számítógépfiókját az új helykiszolgáló csoportjához. Ha egy másik fiókot ad meg a fájl alapú átvitelt, adja hozzá a fiókot a célhely kiszolgálóján a csoport.<br /><br /> Ha eltávolít egy helyet, ez a csoport nem törlődik automatikusan. Azt manuálisan kell törölni.|  
|Engedélyek|Alapértelmezés szerint ez a csoport rendelkezik **teljes hozzáférés** számára a **%path%\Microsoft Configuration Manager\inboxes\despoolr.box\receive** mappa.|  

## <a name="accounts-that-configuration-manager-uses"></a>A Configuration Manager által használt fiókok  
 Állíthat be a következő fiókok a Configuration Manager számára.  

### <a name="active-directory-group-discovery-account"></a>Active Directory csoportfelderítési fiók  
 A **Active Directory Csoportfelderítési fiók** helyi, globális és univerzális biztonsági csoportok, ezek a csoportok tagjainak és az Active Directory tartományi szolgáltatások meghatározott helyeiről származó terjesztési csoportok tagjainak felderítésére szolgál. A terjesztési csoportokat a rendszer nem csoporterőforrásként deríti fel.  

 Ez a fiók lehet egy számítógép-fiók a felderítést futtató helykiszolgálón vagy egy Windows felhasználói fiók. **Olvasás** hozzáférési engedéllyel kell rendelkeznie a felderítéshez megadott Active Directory-helyeken.  

### <a name="active-directory-system-discovery-account"></a>Active Directory rendszerfelderítési fiók  
 Az **Active Directory rendszerfelderítési fiók** az Active Directory tartományi szolgáltatások meghatározott helyein található számítógépek felderítésére szolgál.  

 Ez a fiók lehet egy számítógép-fiók a felderítést futtató helykiszolgálón vagy egy Windows felhasználói fiók. **Olvasás** hozzáférési engedéllyel kell rendelkeznie a felderítéshez megadott Active Directory-helyeken.  

### <a name="active-directory-user-discovery-account"></a>Active Directory felhasználófelderítési fiók  
 Az **Active Directory felhasználófelderítési fiók** az Active Directory tartományi szolgáltatások meghatározott helyein található felhasználói fiókok felderítésére szolgál.  

 Ez a fiók lehet egy számítógép-fiók a felderítést futtató helykiszolgálón vagy egy Windows felhasználói fiók. **Olvasás** hozzáférési engedéllyel kell rendelkeznie a felderítéshez megadott Active Directory-helyeken.  

### <a name="active-directory-forest-account"></a>Active Directory-erdőfiók  
 A **Active Directory-erdő fiókjának** Active Directory-erdők hálózati infrastruktúrájának felderítésére szolgál. A központi adminisztrációs helyek és elsődleges helyek is használhatja a helyadatok közzétételéhez erdő Active Directory tartományi szolgáltatásokban.  

> [!NOTE]  
>  A másodlagos helyek mindig a másodlagos hely kiszolgálójának számítógépfiókját használják az Active Directoryban való közzétételhez.  

> [!NOTE]  
>  Az Active Directory-erdő fiókjának felderítéséhez és közzétételéhez a nem megbízható erdőkben globális fióknak kell lennie. Ha a nem a helykiszolgáló számítógépfiókját használja, csak globális fiókot is választhat.  

 A fióknak **Olvasás** engedéllyel kell rendelkeznie minden olyan Active Directory-erdőhöz, amelyben szeretné felderíteni a hálózati infrastruktúrát.  

 A fióknak **Teljes hozzáféréssel** kell rendelkeznie a rendszerkezelési tárolóhoz és valamennyi gyermekobjektumához minden olyan Active Directory-erdőben, ahol helyadatokat kíván közzétenni.  

### <a name="asset-intelligence-synchronization-point-proxy-server-account"></a>Eszközintelligencia-szinkronizálási pont proxykiszolgáló-fiókja  
 Az Eszközintelligencia szinkronizációs pontja használja az **eszköz az Eszközintelligencia szinkronizálási pont proxykiszolgáló-fiókját** egy proxyn keresztül az Internet eléréséhez, vagy a tűzfal igénylő hitelesített hozzáférést.  

> [!IMPORTANT]  
>  Adjon meg olyan fiókot, amely a legkisebb lehetséges engedélyekkel rendelkezik a szükséges proxykiszolgálóhoz vagy tűzfalhoz.  

### <a name="certificate-registration-point-account"></a>Tanúsítványregisztrációs pont fiók  
 A **Tanúsítványregisztrációs pont fiók** a tanúsítványregisztrációs pont csatlakozik a Configuration Manager adatbázisába. A tanúsítvány regisztrációs kiszolgálójának számítógépfiókját használják alapértelmezett, de beállíthat egy felhasználói fiók helyett. Ha a tanúsítványregisztrációs pont a helykiszolgáló számára nem megbízható tartományban van, meg kell adnia egy felhasználói fiókot. Ez a fiók csak igényel **olvasási** hozzáférni a helyadatbázishoz, mert az állapotüzenet-rendszer kezeli az írási feladatok.  

### <a name="capture-operating-system-image-account"></a>Operációs rendszer lemezképének rögzítése fiók  
 A Configuration Manager használ a **operációs rendszer lemezképének rögzítése fiókot** rögzített lemezképeket tároló operációs rendszerek központi telepítéséhez a mappa elérésére. Erre a fiókra akkor van szükség, ha a **Operációs rendszer lemezképének rögzítése** lépést hozzáadja egy feladatütemezéshez.  

 A fióknak **Olvasás** és **Írás** engedéllyel kell rendelkeznie a rögzített lemezkép tárolására szolgáló hálózati megosztáshoz.  

 Ha a fiók jelszavát módosítják a Windows, az új jelszóval frissítenie kell a feladatütemezést. A Configuration Manager-ügyfél az új jelszót fog kapni, amikor legközelebb letölti az ügyfélházirendet.  

 Ezzel a fiókkal létrehozhat egy minimális jogosultságokkal rendelkező tartományi felhasználói fiókot, amely hozzáfér a szükséges hálózati erőforrásokhoz, és minden feladatütemezési fiókhoz használható.  

> [!IMPORTANT]  
>  Ezt a fiókot ne rendeljen interaktív bejelentkezési engedéllyel.  
>   
>  Ilyen fiókként ne használja a Hálózati hozzáférés fiókot.  

### <a name="client-push-installation-account"></a>Ügyfélleküldéses telepítési fiók  
 A **Ügyfélleküldéses telepítési fiók** kapcsolódhatnak a számítógépekhez, és a Configuration Manager ügyfélszoftver telepítéséhez, ha használatával kíván üzembe helyezni az ügyfelek ügyfélleküldéses telepítés. Ha nincs megadva ez a fiók, akkor a helykiszolgáló-fiók telepíti az ügyfélszoftvert.  

 Ehhez a fiókhoz kell tartoznia a helyi **rendszergazdák** csoportban azokon a számítógépeken, ahol a Configuration Manager-ügyfélszoftvert telepíti. Ez a fiók nem igényel **tartománygazdai** jogok.  

 Megadhat egy vagy több ügyfél Ügyfélleküldéses telepítési fiókot, amely a Configuration Manager sorra próbálja őket, amíg valamelyik nem jár sikerrel.  

> [!TIP]  
>  Nagy Active Directory központi telepítések esetén hatékonyabban koordinálhatja, hozzon létre egy új fiókot valamilyen más névvel, és adja hozzá az új fiókot az Ügyfélleküldéses telepítési fiókot a Configuration Manager listájához. Adjon elég időt az új fiók replikálja az Active Directory tartományi szolgáltatásokban, és azután távolítsa el a régi fiókot a Configuration Manager és az Active Directory tartományi szolgáltatásokban.  

> [!IMPORTANT]  
>  Nem adja meg ezt a fiókot a jogot helyileg jelentkezzen be.  

### <a name="enrollment-point-connection-account"></a>Beléptetési pont kapcsolatfiókja  
 A **beléptetési pont Kapcsolatfiókja** a beléptetési pont csatlakozik a Configuration Manager-hely adatbázisába. A beléptetési pont számítógépfiókját használja alapértelmezés szerint, de beállíthat egy felhasználói fiók helyett. Ha a beléptetési pont olyan tartományban van, amely a helykiszolgáló számára nem megbízható, akkor muszáj megadni egy felhasználói fiókot. Ez a fiók igényel **olvasási** és **írási** a Helyadatbázis eléréséhez.  

### <a name="exchange-server-connection-account"></a>Exchange Server-kapcsolatfiók  
 Az **Exchange Server-kapcsolatfiók** összekapcsolja a helykiszolgálót a megadott Exchange Server-számítógéppel, hogy megkeresse és felügyelje az Exchange Server kiszolgálóhoz csatlakozó mobileszközöket. A fióknak Exchange PowerShell parancsmagokra van szüksége, amelyek megfelelő jogosultságokat biztosítanak az Exchange Server-számítógéphez. További információ a parancsmagokról: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

### <a name="exchange-server-connector-proxy-server-account"></a>Exchange Server-összekötő proxykiszolgáló-fiókja  
 Az Exchange Server-összekötőt használja a **Exchange Server Connector proxykiszolgáló-fiók** egy proxyn keresztül az Internet eléréséhez, vagy a tűzfal igénylő hitelesített hozzáférést.  

> [!IMPORTANT]  
>  Adjon meg olyan fiókot, amely a legkisebb lehetséges engedélyekkel rendelkezik a szükséges proxykiszolgálóhoz vagy tűzfalhoz.  

### <a name="management-point-connection-account"></a>Felügyeleti pont csatlakozási fiókja  
 A **felügyeleti pont csatlakozási fiókja** segítségével összekapcsolja a felügyeleti pontot a Configuration Manager-hely adatbázisába, így küldhet és -ügyfelekre vonatkozó információ beolvasása. A felügyeleti pont számítógépfiókját használja alapértelmezés szerint, de beállíthat egy felhasználói fiók helyett. Ha a felügyeleti pont olyan tartományban van, amely a helykiszolgáló számára nem megbízható, akkor muszáj megadni egy felhasználói fiókot.  

 A fiók egy alacsony jogosultságú, helyi fiók létrehozása a Microsoft SQL Server rendszert futtató számítógépen.  

> [!IMPORTANT]  
>  Ne adjon interaktív bejelentkezési jogokat ehhez a fiókhoz.  

### <a name="multicast-connection-account"></a>Csoportos kapcsolat fiókja  
 Csoportos küldési használatra beállított terjesztési pontokat a **csoportos kapcsolat fiókja** adatolvasás a helyadatbázisból. A terjesztési pont számítógépfiókját használja alapértelmezés szerint, de beállíthat egy felhasználói fiók helyett. Ha a helyadatbázis egy nem megbízható erdőben van, akkor muszáj megadni egy felhasználói fiókot. Ha például az adatközpontnak szegélyhálózata van egy másik erdőben, mint ahol a helykiszolgáló és a helyadatbázis található, akkor ezzel a fiókkal lehet kiolvasni a csoportos küldés adatait a helyadatbázisból.  

 Ha létrehozza ezt a fiókot, hozzon létre egy alacsony jogosultságú, helyi fiók a Microsoft SQL Server rendszert futtató számítógépen.  

> [!IMPORTANT]  
>  Ne adjon interaktív bejelentkezési jogokat ehhez a fiókhoz.  

### <a name="network-access-account"></a>Hálózatelérési fiók  
 Ügyfélszámítógépek használnak a **hálózatelérési fiók** nem használatakor a helyi számítógépes fiókot a terjesztési pontokon a tartalom eléréséhez. Ez vonatkozik a munkacsoport-ügyfelekre és a nem megbízható tartományokban levő számítógépekre is. Ez a fiók is lehet, hogy használni operációs rendszer központi telepítése során, amikor a számítógépen, amely az operációs rendszer telepítése van még nincs számítógépfiók a tartományon.  

> [!NOTE]  
>  A hálózatelérési fiókot soha nem használatos biztonsági környezetként programok futtatására, szoftverfrissítés telepítése vagy feladatütemezésre. A csak a hálózati erőforrások eléréséhez használatos.  

 Csak annyi jogosultságot adjon a fióknak, amennyi feltétlenül szükséges ahhoz, hogy az ügyfél elérje a szoftvert. A fióknak rendelkeznie kell **A számítógép elérése a hálózatról** jogosultsággal a terjesztési ponton vagy a csomagtartalmat tároló más kiszolgálón. Egy helyen legfeljebb 10 hálózatelérési fiókot konfigurálhat.  

> [!WARNING]  
>  Ha a Configuration Manager nem tudja letölteni a tartalmat a computername$ fiók segítségével, akkor automatikusan újrapróbálkozik a hálózatelérési fiókkal, akkor is, ha korábban már próbálta használni, és nem sikerült.  

 A fiók bármelyik tartományban létrehozható, amelyik megfelelő hozzáférést biztosít az erőforrásokhoz. A hálózatelérési fióknak tartalmaznia kell a tartomány nevét. Átmenő hitelesítés nem támogatott ehhez a fiókhoz. Ha több tartományban is vannak terjesztési pontok, akkor egy megbízható tartományban hozza létre a fiókot.  

> [!TIP]  
>  A fiók zárolásának elkerülése érdekében ne módosítsa a meglévő hálózatelérési fiók jelszavát. Ehelyett hozzon létre egy új fiókot, és állítsa be az új fiókot a Configuration Manager alkalmazásban. Ha már minden ügyfél megkapta az új fiók adatait, akkor távolítsa el a korábbi fiókot a megosztott hálózati mappákból, és törölje a fiókot.  

> [!IMPORTANT]  
>  Ne adjon interaktív bejelentkezési jogokat ehhez a fiókhoz.
>   
>  Ne engedélyezze a fióknak, hogy számítógépeket csatlakoztasson a tartományhoz. Ha egy feladatütemezés végrehajtása közben tartományhoz kell csatlakoztatnia a számítógépeket, használja a Feladatütemezés-szerkesztő tartományhoz való csatlakozásra szolgáló fiókját.  

### <a name="package-access-account"></a>Csomag-hozzáférési fiók  
 A **csomag-hozzáférési fiók** lehetővé teszi, hogy a felhasználók és felhasználói csoportokat, amelyeknek férhetnek hozzá a terjesztési pontok csomagmappáihoz megadásához NTFS-engedélyek beállítására. Alapértelmezés szerint a Configuration Manager hozzáférést csak az általános hozzáférési fiókok **felhasználók** és **rendszergazdák**. További Windows-fiókokat vagy csoportokat szabályozhatja az ügyfélszámítógépek számára a hozzáférést. Mobileszközök mindig csomag tartalmának lekéréséhez névtelenül, hogy nem a csomag-hozzáférési fiókokat.  

 Alapértelmezés szerint amikor a Configuration Manager létrehozza a csomagmegosztást egy terjesztési ponton, alapértelmezésben **olvasási** hozzáférést ad a helyi **felhasználók** csoport és **teljes hozzáférés** a helyi **rendszergazdák** csoport. A csomagtól függ, hogy valójában milyen engedélyekre van szükség. Ha munkacsoportokban vagy nem megbízható erdőkben levő ügyfelekkel rendelkezik, ezek az ügyfelek hálózatelérési fiókon keresztül férnek hozzá a csomagtartalomhoz. Ügyeljen arra, hogy a hálózatelérési fiók hozzáférhessen a csomaghoz a megadott csomagelérési fiókok segítségével.  

 Olyan tartomány fiókjait használja, amely hozzáfér a terjesztési pontokhoz. Ha hoz létre vagy módosítja a fiókot, a csomagot a létrehozása után, újra kell terjesztenie a csomagot. A csomag frissítése esetén a csomag NTFS-engedélyeit változatlanok maradnak.  

 Nem kell felvennie a hálózatelérési fiókot csomagelérési fiókként, mert a Felhasználók csoport tagsága automatikusan felveszi. Az ügyfelek attól még hozzáférhetnek a csomaghoz, hogy a csomag-hozzáférési fiók csak a hálózatelérési fiókra van korlátozva.  

### <a name="reporting-services-point-account"></a>Jelentéskészítési szolgáltatási pont fiókja  
 SQL Server Reporting Services használja a **jelentéskészítési szolgáltatási pont fiókja** Configuration Manager jelentések adatok lekéréséhez a helyadatbázisból. A megadott Windows-felhasználói fiókot és jelszót az SQL Server Reporting Services-adatbázis tárolja titkosítva.  

### <a name="remote-tools-permitted-viewer-accounts"></a>Távoli eszközök engedélyezett megjelenítő fiókjai  
 A távvezérléshez **engedélyezett megjelenítőként** megadott fiókok azok a felhasználók, akik használhatják az ügyfeleken a távoli eszközök funkciót.  

### <a name="site-system-installation-account"></a>Helyrendszer-telepítési fiók  
 A helykiszolgáló használja a **helyrendszer-telepítési fiók** telepítéséhez újra kell telepítenie, távolítsa el, és állítsa be a helyrendszerek. Ha a helyrendszer a megkövetelése a helykiszolgálótól ehhez a helyrendszerhez kapcsolatok kezdeményezésének úgy konfigurálja a Configuration Manager is ezt a fiókot használja segítségével szerez adatokat a helyrendszer számítógépéről a helyrendszer és a helyrendszerszerepkörök telepítése után. Minden helyrendszer egy másik helyrendszer-telepítési fiókot lehet, de minden helyrendszer-szerepkört az adott helyrendszer kezeléséhez csak egy helyrendszer-telepítési fiók állíthat be.  

 Ennek a fióknak helyi rendszergazdai jogosultságokkal kell azon a helyrendszeren, amelyet a rendszergazda telepíti és állítsa be. Emellett ennek a fióknak rendelkeznie kell **a számítógép elérése a hálózatról** azon a helyrendszeren, amelyet a rendszergazda telepíti és állítsa be a biztonsági házirendben.  

> [!TIP]  
>  Ha több tartományvezérlővel rendelkezik, és ezek a fiókok tartományokban lesz alkalmazva, ellenőrizze, hogy a fiókok replikálása a helyrendszer beállítása előtt.  
>   
>  Ha helyi fiókot ad meg mindegyik felügyelendő helyrendszeren, az biztonságosabb a tartományi fiókok használatánál, mert a fiók esetleges feltörése esetén a támadók kisebb kárt okozhatnak. Azonban a tartományi fiókokat is könnyebben kezelhető. Vegye figyelembe a kompromisszum biztonsági és hatékony felügyeleti között.  

### <a name="smtp-server-connection-account"></a>SMTP-kiszolgáló csatlakozási fiókja  
 A helykiszolgáló használja a **SMTP-kiszolgáló csatlakozási fiókja** küld e-mail riasztást, hogy mikor van szükség az SMTP-kiszolgáló hitelesített hozzáférést.  

> [!IMPORTANT]  
>  Adjon meg egy olyan, e-mail küldésre alkalmas fiókot, amely a lehető legkevesebb jogosultsággal rendelkezik.  

### <a name="software-update-point-connection-account"></a>Szoftverfrissítési pont csatlakozási fiókja  
 A helykiszolgáló használja a **szoftverfrissítési pont csatlakozási fiókja** az alábbi két software update Services:  

-   Windows Server Update Services (WSUS) Configuration Manager alkalmazást, amely beállítja a beállítások, például a TERMÉKMEGHATÁROZÁSOK, besorolások és felsőbb rétegbeli beállítások.  

-   A WSUS szinkronizációkezelőhöz, amely szinkronizálást kér a felsőbb rétegbeli WSUS-kiszolgálóval vagy a Microsoft Update szolgáltatással.  

A helyrendszer-telepítési fiók telepítheti a szoftverfrissítések összetevőit, de azt nem hajtható végre update-specifikus funkcióit a szoftverfrissítési ponton. Ha a helykiszolgáló számítógépfiókja nem használható erre a funkcióra, mert a szoftverfrissítési pont egy nem megbízható erdőben van, akkor ezt a fiókot is meg kell adni a helyrendszer-telepítési fiók mellett.  

Ez a fiók a számítógépen, amelyre a WSUS telepítve van-e helyi rendszergazdának kell lennie. Emellett a helyi WSUS-rendszergazdák csoporthoz kell lennie.  

### <a name="software-update-point-proxy-server-account"></a>Szoftverfrissítési pont proxykiszolgáló-fiókja  
 A szoftverfrissítési pontot használ a **szoftverfrissítési pont Proxy-fiók** egy proxyn keresztül az Internet eléréséhez, vagy a tűzfal igénylő hitelesített hozzáférést.  

> [!IMPORTANT]  
>  Adjon meg olyan fiókot, amely a legkisebb lehetséges engedélyekkel rendelkezik a szükséges proxykiszolgálóhoz vagy tűzfalhoz.  

### <a name="source-site-account"></a>Forráshelyfiók  
 Az áttelepítési folyamat használja a **Forráshelyfiók** a forráshely SMS-szolgáltató elérésére. A fióknak **olvasási** jogosultsággal kell rendelkeznie a forráshely helyobjektumai felett, hogy adatokat gyűjthessen az áttelepítési feladatokhoz.  

 Ha a Configuration Manager 2007 terjesztési pontokat vagy olyan másodlagos helyeket, ahol társ elhelyezésű terjesztési pontok a System Center Configuration Manager terjesztési pontokra frissít, ennek a fióknak is rendelkeznie kell **törlése** engedélyeket a **hely** osztályra, hogy sikeresen eltávolíthassa a terjesztési pontot a Configuration Manager 2007 helyről a frissítés során.  

> [!NOTE]  
>  A Forráshelyfiók és a Forráshelyi adatbázisfiók is azonosítottak **Áttelepítéskezelő** a a **fiókok** csomópontjának a **felügyeleti** munkaterület a Configuration Manager konzolon.  

### <a name="source-site-database-account"></a>Forráshelyi adatbázisfiók  
 Az áttelepítési folyamat használja a **Forráshelyi adatbázisfiók** a forráshely SQL Server-adatbázisának eléréséhez. Az adatok gyűjtését a forráshely SQL Server-adatbázis, a Forráshelyi adatbázisfiók kell rendelkeznie a **olvasási** és **Execute** engedéllyel kell rendelkeznie a forráshely SQL Server adatbázishoz.  

> [!NOTE]  
>  Ha a System Center Configuration Manager számítógépfiókját használja, győződjön meg arról, hogy minden a következők teljesülnek-e ehhez a fiókhoz:  
>   
> -   A biztonsági csoport tagja **elosztott COM-felhasználók** a tartományban, amelyben a Configuration Manager 2007 helyen található.  
> -   Tagja az **SMS rendszergazdák** biztonsági csoportnak.  
> -   Rendelkezik a **olvasási** engedély az összes Configuration Manager 2007-objektumokhoz.  

> [!NOTE]  
>  A Forráshelyfiók és a Forráshelyi adatbázisfiók azonosítottak **Áttelepítéskezelő** a a **fiókok** csomópontjának a **felügyeleti** munkaterület a Configuration Manager konzolon.  

### <a name="task-sequence-editor-domain-joining-account"></a>Feladatütemezés-szerkesztő tartománycsatlakozási fiókja  
 A **feladatütemezés-szerkesztő tartománycsatlakozási fiókja** segítségével tartományhoz csatlakoztathatja az újonnan leképezett számítógépeket a feladatütemezés során. Ez a fiók akkor szükséges, ha a feladatütemezésbe felvette a **Csatlakozás tartományhoz vagy munkacsoporthoz** lépést, majd a **Csatlakozás tartományhoz** lehetőséget választotta. Ez a fiók is beállítható a lépés hozzáadásakor **hálózati beállítások alkalmazása** tevékenységhez feladatütemezési, de nincs szükség.  

 Ennek a fióknak **Tartományhoz való csatlakozás** jogosultságra van szüksége abban a tartományban, amelyikhez a számítógép csatlakozni fog.  

> [!TIP]  
>  Ha a feladatütemezéseihez szüksége van erre a fiókra, létrehozhat egy minimális engedéllyel rendelkező tartományi felhasználói fiókot, hogy elérje a hálózati erőforrásokat, és használja azt minden feladatütemezési fiókhoz.  

> [!IMPORTANT]  
>  Ezt a fiókot ne rendeljen interaktív bejelentkezési engedéllyel.  
>   
>  Ilyen fiókként ne használja a Hálózati hozzáférés fiókot.  

### <a name="task-sequence-editor-network-folder-connection-account"></a>Feladatütemezés-szerkesztő hálózati mappához csatlakoztató fiókja  
 A feladatütemezés használja a **feladat feladatütemezési szerkesztő hálózati mappához csatlakoztató fiókja** csatlakozni egy megosztott hálózati mappából. Erre a fiókra akkor van szükség, ha a **Csatlakozás hálózati mappához** lépést hozzáadja egy feladatütemezéshez.  

 Ez a fiók a megadott megosztott mappa elérésére szolgáló engedélyekkel kell rendelkeznie. Tartományi felhasználói fiókot kell lennie.  

> [!TIP]  
>  Ha a feladatütemezéseihez szüksége van erre a fiókra, létrehozhat egy minimális engedéllyel rendelkező tartományi felhasználói fiókot, hogy elérje a hálózati erőforrásokat, és használja azt minden feladatütemezési fiókhoz.  

> [!IMPORTANT]  
>  Ezt a fiókot ne rendeljen interaktív bejelentkezési engedéllyel.  
>   
>  Ilyen fiókként ne használja a Hálózati hozzáférés fiókot.  

### <a name="task-sequence-run-as-account"></a>Fiókként futó feladatütemezés  
 A **fiókként futó feladatütemezés** segítségével parancssorokat futtathat a feladatütemezés során. Olyan hitelesítőadatokat is használhat, amelyek nem a helyi rendszerfióktól származnak. Ez a fiók akkor szükséges, ha hozzáadja a lépést **parancssor futtatása** egy feladatütemezést, de nem akarja a feladatütemezés helyi rendszerfiók engedélyeivel fusson a felügyelt számítógépen.  

 A fiók beállítása a feladatütemezésben megadott parancssor futtatásához szükséges legkevesebb engedélye legyen. A fióknak interaktív bejelentkezési jogokat, és általában szüksége van arra, hogy szoftvert telepítsen és hálózati erőforrások eléréséhez.  

> [!IMPORTANT]  
>  Ilyen fiókként ne használja a Hálózati hozzáférés fiókot.  
>   
>  Tegye soha a fiókot egy tartományi rendszergazda segítségét.  
>   
>  Soha nem állít be központi profilokat ehhez a fiókhoz. Amikor a feladatütemezés fut, le fogja tölteni a fiók barangolási profilját. Így marad a profil hozzáférhetnek a helyi számítógépen.  
>   
>  Korlátozza a fiók hatókörét. Például különböző fiókként futó feladatütemezést hozzon létre az egyes feladatütemezésekhez, így ha az egyik fiók biztonsága sérül, csak az adott fiók által elérhető ügyfélszámítógépek kerülnek veszélybe.  
>   
>  Ha a parancssornak a számítógépen rendszergazdai hozzáférésre van szüksége, fontolja meg egy helyi rendszergazdai fiók létrehozását a feladat fiókként futó minden olyan számítógépre, amely futtatja a feladatütemezést. A fiók törlése, amint azt már nem szükséges.  

