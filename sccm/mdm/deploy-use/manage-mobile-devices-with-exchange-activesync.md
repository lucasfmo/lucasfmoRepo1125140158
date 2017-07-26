---
title: "Mobileszközök kezelése |} Microsoft Docs"
description: "Mobileszközök kezelése a System Center Configuration Managerben az Exchange Server-összekötő használatával."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: aba688d9-fd5b-4c42-8cb4-f7e1b161ef50
caps.latest.revision: 8
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 44958bc35586f5e57ab3fb59681bfb018d2bd5da
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-mobile-devices-with-system-center-configuration-manager-and-exchange"></a>Mobileszközök kezelése a System Center Configuration Manager és az Exchange

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a System Center Configuration Manager Exchange Server-összekötő helyzet Exchange Serverhez csatlakozó mobileszközök felügyeletéhez (a helyszínen vagy online) használatával a Microsoft Exchange ActiveSync protokoll, és nem tudja beléptetni azokat a Configuration Manager használatával. Beállíthatja az Exchange mobileszköz-kezelési funkcióit, eszköztartalom távoli törlését és beállítások több Exchange-kiszolgáló, a Configuration Manager konzoljáról.  

 ![ConfigMgr &#45; &#45; exchange](../../mdm/deploy-use/media/configmgr-with-exchange.png "configmgr az exchange")  

 Ha az Exchange Server-összekötő segítségével kezelt mobileszközök, az nem telepíti a Configuration Manager-ügyfél a mobileszközökön. Ezért néhány felügyeleti funkció korlátozott. Nem telepíthet például szoftvereket ezekre az eszközökre, és nem használhat konfigurációs elemeket ezeknek az eszközöknek a konfigurálásához. A Configuration Manager a mobileszközök kezeléséhez használható különféle lehetőségekről kapcsolatos további információkért lásd: [eszköz megoldás választása a System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md).  

> [!IMPORTANT]  
>  Az Exchange Server-összekötő telepítése előtt győződjön meg arról, hogy a Configuration Manager támogatja-e a Microsoft Exchange Ön által használt verzióját. További információkért tekintse meg az "Exchange Server-összekötő" a [helyeket és -ügyfeleket a System Center Configuration Manager támogatott operációs rendszerekről](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  

 Az Exchange Server-összekötő használata esetén a mobileszközök kezelhető a konfigurált beállítások a Configuration Manager felügyelete alatt áll. az alapértelmezett Exchange ActiveSync postaláda-házirendek helyett. A következő csoportbeállításokban használni kívánt beállításainak megadása: **Általános**, **jelszó**, **E-mail kezelés**, **biztonsági**, és **alkalmazás**. A **Jelszó** csoportbeállításban például beállíthatja, hogy a mobileszközök kérjenek-e jelszót, megadhatja a jelszó minimális hosszát és a jelszó bonyolultságát, és engedélyezheti vagy letilthatja a jelszó-visszaállítást.  

 Ha a csoportban legalább egy beállítást, a Configuration Manager kezeli a mobileszközök kezeléséhez a csoport összes beállítását. Ha egy csoport egyetlen beállítását sem adja meg, az Exchange kezeli majd továbbra is az adott beállításokat mobileszközök esetén. Az Exchange Serveren konfigurált és felhasználókhoz rendelt Exchange ActiveSync postaláda-házirendek továbbra is érvényben lesznek.  

 Megfelelő beállítással az Exchange Server-összekötőt használhatja az Exchange hozzáférési szabályainak kezeléséhez, és a mobileszközök engedélyezéséhez, blokkolásához vagy karanténba helyezéséhez is. Mobileszközöket a Configuration Manager konzol segítségével távolról törölhetik, és a felhasználók távolról törölhetik a mobileszközeiket az Alkalmazáskatalógus használatával.  

 A felhasználó mobileszköze automatikusan megjelenik az alkalmazáskatalógusban Ha az Exchange Server-összekötővel kezeli, és az Exchange Server helyszíni. A Microsoft Exchange online-hoz az Exchange Server-összekötő konfigurálásakor a felhasználó mobil eszköz számára az alkalmazáskatalógusban jelennek meg a felhasználó-eszköz kapcsolatot manuálisan kell konfigurálni. Felhasználó-eszköz kapcsolat manuális konfigurálásával kapcsolatos további információkért lásd: [felhasználók és eszközök összekapcsolása felhasználó-eszköz kapcsolat a System Center Configuration Managerben](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

> [!TIP]  
>  Ha kezel egy mobileszközt az Exchange Server-összekötő használatával, és a mobileszközt átadják egy másik felhasználónak, törölje a mobileszközt a Configuration Manager konzolról, mielőtt a mobileszköz új tulajdonosa konfigurálja a, az Exchange-fiókját az átvett mobileszközön.  

## <a name="required-security-permissions"></a>A szükséges biztonsági engedélyek  
 Az Exchange Server-összekötő konfigurálásához a következő biztonsági engedélyekkel kell rendelkeznie:  

-   Hozzáadása, módosítása, és az Exchange Server-összekötő törlése: **Módosítsa** engedély a **hely** objektum.  

-   A mobileszköz-beállítások konfigurálása: **ModifyConnectorPolicy** engedély a **hely** objektum.  

 A **Teljes körű rendszergazda** biztonsági szerepkör tartalmazza az Exchange Server-összekötő konfigurálásához szükséges engedélyeket.  

 A mobileszközök kezeléséhez a következő biztonsági engedélyekkel kell rendelkeznie:  

-   Mobil eszköz tartalmának törlése: **Erőforrás törlése** a a **gyűjtemény** objektum.  

-   Az összes adat törlésére vonatkozó parancs visszavonása: **Erőforrás módosítása** a a **gyűjtemény** objektum.  

-   A mobil eszközök letiltása és engedélyezése: **Erőforrás módosítása** a a **gyűjtemény** objektum.  

 A **Műveleti rendszergazda** biztonsági szerepkör tartalmazza a mobileszközök Exchange Server-összekötő segítségével történő kezeléséhez szükséges engedélyeket.  

 Biztonsági engedélyek konfigurálásának módjáról további információkért lásd: [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md).  

## <a name="installing-and-configuring-an-exchange-server-connector"></a>Az Exchange Server-összekötő telepítése és konfigurálása  
 A következő eljárással telepíthet és konfigurálhat Exchange Server-összekötőt a mobileszközök kezeléséhez. A Configuration Manager csak egyetlen összekötőt támogat az Exchange-szervezetben. A lépések elvégzése után a mobileszközöket megjelenítő gyűjtemények megtekintésekor, és a mobileszközök jelentéseinek segítségével felügyelheti az összekötő által megtalált és kezelt mobileszközöket.  

> [!NOTE]  
>  A Configuration Manager riasztást nevek a mobil eszközök talált a következő formátumban *felhasználónév*_*DeviceType*. Ha egy felhasználónak egynél több mobileszköz, amelyen azonos típusú, a Configuration Manager a mobileszközök ugyanazt a nevet jeleníti meg a konzol és a jelentésekben.  

#### <a name="to-install-and-configure-an-exchange-server-connector"></a>Az Exchange Server-összekötő telepítése és konfigurálása  

1.  Döntse el, hogy a mobileszközök kezelése érdekében melyik fiók fog csatlakozni az Exchange ügyfélelérési kiszolgálóhoz. Ez a fiók lehet a helykiszolgáló számítógépfiókja vagy egy Windows felhasználói fiók. Ezután konfigurálja, hogy ez a fiók futtassa az alábbi Exchange Server-parancsmagokat:  

    -   **CLEAR-ActiveSyncDevice**  

    -   **Get-ActiveSyncDevice**  

    -   **Get-ActiveSyncDeviceAccessRule**  

    -   **Get-ActiveSyncDeviceStatistics**  

    -   **Get-ActiveSyncMailboxPolicy**  

    -   **Get-ActiveSyncOrganizationSettings**  

    -   **Get-ExchangeServer**  

    -   **Get-címzett**  

    -   **Set-ADServerSettings**  

    -   **Set-ActiveSyncDeviceAccessRule**  

    -   **Set-ActiveSyncMailboxPolicy**  

    -   **Set-CASMailbox**  

    -   **Új ActiveSyncDeviceAccessRule**  

    -   **Új ActiveSyncMailboxPolicy**  

    -   **Remove-ActiveSyncDevice**  

    > [!NOTE]  
    >  Az Exchange Server következő kezelői szerepkörei tartalmazzák ezeket a parancsmagokat: Címzettkezelés, csak megtekintésre Szervezetkezelés és Kiszolgálókezelés. A Microsoft Exchange Server 2010 kezelőiszerepkör-csoportjairól bővebben lásd: [Understanding Management Role Groups](http://go.microsoft.com/fwlink/p/?LinkId=212914).  

    > [!TIP]  
    >  Ha a szükséges parancsmagok nélkül kísérli meg telepíteni vagy használni az Exchange Server-összekötőt, a rendszer az `Invoking cmdlet <cmdlet> failed` (A(z)  parancsmag indítása nem sikerült) üzenettel naplózza a hibát az EasDisc.log naplófájlban a helykiszolgáló számítógépén.  

2.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

3.  Az **Adminisztráció** munkaterületen bontsa ki a **Hierarchiakonfiguráció**elemet, majd kattintson az **Exchange Server-összekötők**lehetőségre.  

4.  A **Kezdőlap** **Létrehozás** csoportjában kattintson az **Exchange Server hozzáadása**lehetőségre.  

5.  Fejezze be az Exchange Server hozzáadása varázslót:  

    -   Ha az Exchange Server helyszíni példányát használja, és megad egy ügyfélelérési kiszolgálót, akkor minden egyes Active Directory-helyhez egyetlen kiszolgálót vagy egy ügyfélelérésikiszolgáló-tömböt határozhat meg. Ha a kiszolgáló vagy a tömb offline állapotban, a Configuration Manager megpróbál felderíteni egy használható ügyfélelérési kiszolgálót használja. Ha nem sikerül, a Configuration Manager visszaáll egy postaláda-kiszolgáló használatával kapcsolatot teremtsen egy ügyfélelérési kiszolgálóval. Az újrapróbálkozásokat figyelmeztetésekként naplózza az EasDisc.log fájlban a helykiszolgáló számítógépén. Keressen például a `Failed to open runspace for site <site_name>`(Nem sikerült megnyitni a futási teret a(z)  hely esetén) üzenetre.  

    -   Az Exchange Server-összekötő fiókjaként adja meg az 1. lépésben beállított fiókot.  

    -   Configuration Manager használatával beléptetett mobileszközök is, ha engedélyezi a beállítást **külső mobileszköz-kezelés** annak érdekében, hogy a mobileszközök továbbra is megkapja leveleket az Exchange, miután a Configuration Manager belépteti azokat.  

    -   Az a **fiók** oldalon a varázsló be lehet állítani ügyfeleknél, amelyek a Configuration Manager feltételes hozzáférése által blokkolt e-mail értesítések küldéséhez használt fiókot. A megadott fióknak érvényes postafiókkal kell rendelkeznie az Exchange-kiszolgálón.  

         További információkért lásd: [kezelése a System Center Configuration Manager-szolgáltatásokhoz való hozzáférés](../../protect/deploy-use/manage-access-to-services.md).  

6.  Állapotüzenetek segítségével és a naplófájlok vizsgálatával ellenőrizheti az Exchange Server-összekötő telepítését:  

    -   Ha meg szeretne győződni róla, hogy a Helyösszetevő-kezelő sikeresen telepítette az Exchange Server-összekötőt, keresse meg az **SMS_EXCHANGE_CONNECTOR** összetevő **1015-ös** azonosítóval rendelkező állapotüzenetét. Ha a Configuration Manager nem telepíthető az összekötőt (mert például a megadott ügyfélelérési kiszolgáló számítógépe nem elérhető), a Configuration Manager újrapróbálkozik a telepítéssel mindaddig, amíg a telepítés sikeres, vagy el nem távolítja az Exchange Server-összekötő 60 percenként.  

    -   Keresse meg a SiteComp.log fájlt a helykiszolgáló számítógépén, majd a naplófájlban keresse meg a `Component SMS_EXCHANGE_CONNECTOR flagged for installation`(Az SMS_EXCHANGE_CONNECTOR telepítésre megjelölve) üzenetet. A sikeres telepítés a következő szöveggel kerül naplózásra: `STATMSG: ID=1015`  

