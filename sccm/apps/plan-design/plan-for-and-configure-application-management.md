---
title: "Tervezze meg, és az Alkalmazáskezelés konfigurálása |} Microsoft Docs"
description: "Alkalmazza, és konfigurálja a szükséges függőségek a System Center Configuration Managerben alkalmazások központi telepítéséhez."
ms.custom: na
ms.date: 02/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2be84a1d-ebb9-47ae-8982-c66d5b92a52a
caps.latest.revision: 13
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1c43c4968f93985515249ddb117269f8ed61302a
ms.openlocfilehash: 46cc3fcfd9516cf1c124e24b50d0aac0cb0025dc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-and-configure-application-management-in-system-center-configuration-manager"></a>A System Center Configuration Managerrel végzett alkalmazáskezelés tervezése és konfigurálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Olvassa el ebben a cikkben az alkalmazás a System Center Configuration Manager központi telepítéséhez szükséges függőségek megvalósításához nyújtanak segítséget.  

## <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  

|Függőség|További információ|  
|------------------|----------------------|  
|Az Internet Information Services (IIS) szükséges az olyan helyrendszer-kiszolgálóknál, amelyek az alkalmazáskatalógus weboldal-elérési pontját, az alkalmazáskatalógus webszolgáltatási pontját, a felügyeleti pontot és a terjesztési pontot futtatják.|Ez a követelmény kapcsolatban bővebben lásd: [által támogatott konfigurációk](../../core/plan-design/configs/supported-configurations.md).|  
|A Configuration Manager által beléptetett mobileszközök|Ha kódjának aláírása alkalmazásokat telepíthet a mobileszközökre, nem használja a tanúsítványt, amelyik a 3-as verziójú sablonnal jött létre (**Windows Server 2008, Enterprise Edition**). Ez a tanúsítványsablon tanúsítványt hoz létre, amely nem kompatibilis a Configuration Manager mobileszközi alkalmazásaival.<br /><br /> Ha alkalmazások kódjának aláírása Active Directory tanúsítványszolgáltatások használatával a mobileszközön lévő alkalmazások, ne használja egy 3-as verziójú tanúsítványsablont.|  
|Ügyfelek kell állítani a bejelentkezési események naplózása, ha azt szeretné, hogy automatikusan létrejöjjön a felhasználó-eszköz kapcsolatokat.|A Configuration Manager-ügyfél olvas típusú bejelentkezési esemény **sikeres** a számítógépek biztonsági eseménynaplójából automatikus felhasználó-eszköz kapcsolatok meghatározásához.  Ezek az események a következő két naplózási házirendek által engedélyezettek: "<br>**Fiókbejelentkezés naplózása**<br>**Bejelentkezés naplózása**<br>A felhasználók és az eszközök közötti kapcsolat automatikus létrehozásához ennek a két beállításnak engedélyezettnek kell lenni az ügyfélgépeken. Ezen beállítások konfigurálásához a Windows csoportházirendje használható.|  

## <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei   

|Függőség|További információ|  
|------------------|----------------------|  
|Felügyeleti pont|Az ügyfelek kapcsolatba egy felügyeleti ponthoz, hogy letöltsék az ügyfélházirendet, keresse meg a tartalmat, és az Alkalmazáskatalógushoz való kapcsolódáshoz.<br /><br /> Ha az ügyfelek nem érhetik el a felügyeleti pontot, nem használhatják az Alkalmazáskatalógust.|  
|Terjesztési pont|Az alkalmazások ügyféleszközökre telepítése előtt a hierarchiában legalább egy terjesztési ponttal kell rendelkeznie. Alapértelmezetten a helykiszolgálónak a szabályos telepítéskor terjesztési ponti engedélyezett helyszerepköre van. A terjesztési pontok száma és helye változó, igazodik az önök vállalatának konkrét követelményeihez.<br /><br /> További információ a terjesztési pontok telepítéséről és a tartalomkezelésről, lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|Ügyfélbeállítások|Sok ügyfél beállítások szabályozzák, hogyan az alkalmazások telepítése az ügyfél és a felhasználói élmény az ügyfélen. Ilyen beállítások lehetnek a következők:<br /><br /><ul><li>Számítógépügynök</li><li>Számítógép újraindítása</li><li>Szoftver központi telepítése</li><li>Felhasználó-eszköz kapcsolat</li></ul> Ezeket az ügyfélbeállításokat kapcsolatban bővebben lásd: [kapcsolatos](../../core/clients/deploy/about-client-settings.md).<br /><br /> Az ügyfél beállításainak konfigurálása című kapcsolatos [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).|  
|Az Alkalmazáskatalógus esetén:<br /><br /> Felderített felhasználói fiókok|A Configuration Manager először fel kell deríteni felhasználók ahhoz, hogy megtekintheti és alkalmazást kérnének az alkalmazáskatalógusból. További információkért lásd: [felderítés futtatása](/sccm/core/servers/deploy/configure/run-discovery).|  
|App-V 4.6 SP1 vagy újabb verziójú ügyfélszoftver a virtuális alkalmazások futtatásához|Tudjanak virtuális alkalmazásokat létrehozni a Configuration Manager alkalmazásban, ügyfélszámítógépeken rendelkeznie kell az App-V 4.6 SP1 vagy újabb ügyfél telepítve.<br /><br /> Frissíteni kell az App-V-ügyfél a a Tudásbázis ismertetett gyorsjavítással [2645225 sz. cikkében cikk](http://go.microsoft.com/fwlink/p/?LinkId=237322) virtuális alkalmazások telepítése előtt.|  
|Alkalmazáskatalógus webszolgáltatási pontja|Az alkalmazáskatalógus webszolgáltatási pontja olyan helyrendszerszerepkör, amelyik a Szoftverkönyvtárból információt szolgáltat az Alkalmazáskatalógus webhelye részére.<br /><br /> Ilyen helyrendszerszerepkör konfigurálásáról bővebben: [konfigurálása a Szoftverközpont és az Alkalmazáskatalógus (csak Windows rendszerű számítógépek)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only) ebben a cikkben.|  
|Alkalmazáskatalógus weboldal-elérési pontja|Az alkalmazáskatalógus weboldal-elérési pontja olyan helyrendszer-szerepkör, amelyik megadja a felhasználóknak az elérhető szoftverek listáját.<br /><br /> Ilyen helyrendszerszerepkör konfigurálásáról bővebben: [konfigurálása a Szoftverközpont és az Alkalmazáskatalógus (csak Windows rendszerű számítógépek)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only) ebben a cikkben.|  
|Jelentéskészítési szolgáltatási pont|Tudjanak az alkalmazáskezeléshez a Configuration Managerben a jelentéseket használhatja, hogy először telepítenie és konfigurálnia kell egy jelentéskészítési szolgáltatási pontot.<br /><br /> További információ: [Jelentéskészítés a System Center Configuration Managerben](../../core/servers/manage/reporting.md).|  
|Biztonsági engedélyek az alkalmazáskezeléshez|Az alkalmazások kezeléséhez a következő biztonsági engedélyekkel kell rendelkezni.<br /><br /> A **alkalmazás szerzője** biztonsági szerepkör tartalmazza azokat az előbb felsorolt engedélyeket, létrehozása, módosítása és a Configuration Manager telepítéséhez szükséges.<br /><br /> **Alkalmazások telepítéséhez:**<br /><br /> A **alkalmazás-KözpontiTelepítés kezelő** biztonsági szerepkör tartalmazza azokat az előbb felsorolt engedélyeket, amelyek szükségesek az alkalmazás a Configuration Manager központi telepítéséhez.<br /><br /> A **alkalmazás-rendszergazda** biztonsági szerepkör rendelkezik minden engedélyeit is a **alkalmazás szerzője** és a **alkalmazás-KözpontiTelepítés kezelő** biztonsági szerepköröket.<br /><br /> További információkért lásd: [szerepköralapú Adminisztráció konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md).|  

##  <a name="configure-software-center-and-the-application-catalog-windows-pcs-only"></a>A Szoftverközpont és az alkalmazáskatalógus konfigurálása (csak Windows-számítógépek esetében)  

 A System Center Configuration Managerben, most két lehetősége van a beállítások módosítása, az alkalmazások és alkalmazások telepítése a felhasználók:  

-   **Az új Szoftverközpont** -az új Szoftverközpont modern megjelenéssel rendelkezik. Alkalmazások jelent volna meg csak a Silverlight-függő Alkalmazáskatalógusban (a felhasználók számára elérhető alkalmazások) mostantól megjelennek a Szoftverközpont a **alkalmazások** fülre. Az Alkalmazáskatalógus továbbra is elérhetők, hivatkozással a **telepítési állapotát** szoftverközpont fülre.  

     A **Számítógépügynök** > **Az új Szoftverközpont használata**ügyfélbeállítás engedélyezésével beállíthatja, hogy az ügyfelek az új Szoftverközpontot használják.  

    > [!IMPORTANT]  
    >  Bár a már nem kell kapcsolódni az Alkalmazáskatalógushoz, továbbra is konfigurálnia kell az Alkalmazáskatalógus weboldal-elérési pontja és az Alkalmazáskatalógus webszolgáltatási pontját részletes, a következő szakaszban.  

-   **Az előző Szoftverközpont és az alkalmazáskatalógus** – alapértelmezés szerint felhasználók továbbra is az előző verziójú Szoftverközponthoz csatlakoznak, és kapcsolódnak az alkalmazáskatalógushoz (Silverlight-kompatibilis webböngésző szükséges) az elérhető alkalmazások tallózásához.  

 Bármely verzió szeretne használni, a Szoftverközpont automatikusan települ a Windows rendszerű számítógépeken a Configuration Manager-ügyfél telepítésekor.  

    > [!TIP]  
    >  A felhasználók számára a Szoftverközpont verziója a Configuration Manager-ügyfél beállításai alapul. Ez lehetővé teszi a rugalmasság vezérlőhöz használt verzióját a gyűjteménybe telepített egyéni ügyfélbeállítások alapján. 

    > [!IMPORTANT]
    > Néhány hónapon belül azt fogja eltávolítani az előző verziójú Szoftverközponthoz, és már nem lesz elérhető lesz szükség.
    > A **Számítógépügynök** > **Az új Szoftverközpont használata**ügyfélbeállítás engedélyezésével beállíthatja, hogy az ügyfelek az új Szoftverközpontot használják. 

## <a name="steps-to-install-and-configure-the-application-catalog-and-software-center"></a>Az alkalmazáskatalógus és a Szoftverközpont telepítésének és konfigurálásának lépései  

> [!IMPORTANT]  
>  Mielőtt ezeket a lépéseket, győződjön meg arról, hogy teljesül az összes korábban felsorolt előfeltételek.  

|Lépések|Részletek|További információ|  
|-----------|-------------|----------------------|  
|**1. lépés:** Ha a HTTPS-kapcsolatok használata esetén ellenőrizze, hogy helyrendszer-kiszolgálókon legyen telepítve webkiszolgáló-tanúsítvány.|Végezze el webkiszolgáló-tanúsítvány központi telepítését azokon a helyrendszer-kiszolgálókon, amelyeken az alkalmazáskatalógus weboldal-elérési pontja és az alkalmazáskatalógus webszolgáltatási pontja futni fog.<br /><br /> Továbbá ha azt szeretné, hogy az ügyfelek számára az Alkalmazáskatalógus az internetről, egy webkiszolgáló-tanúsítvány telepítése legalább egy felügyeleti pont helyrendszer-kiszolgálón, és konfigurálja az internetről érkező ügyfélkapcsolatok.|További információért tanúsítványokkal szemben támasztott követelmények, lásd: [PKI-tanúsítványkövetelmények](../../core/plan-design/network/pki-certificate-requirements.md).|  
|**2. lépés:** Ha PKI-ügyféltanúsítványt fogja használni a felügyeleti pontok kapcsolataihoz, központilag telepíti a ügyfél-hitelesítési tanúsítványt az ügyfélgépekre.|Bár az ügyfelek nem használnak PKI-ügyféltanúsítványt az Alkalmazáskatalógushoz való kapcsolódáshoz, hogy felügyeleti pontot kell csatlakozni, az Alkalmazáskatalógus használatához. A következő helyzetekben mindenképpen telepíteni kell az ügyfélszámítógépeken ügyfél-hitelesítési tanúsítványt:<br /><br /><ul><li>Az intraneten az összes felügyeleti pont csak HTTPS-kapcsolatok fogadására.</li><li>Ügyfelek az internetről fognak kapcsolódni az Alkalmazáskatalógushoz.</li></ul>|További információért tanúsítványokkal szemben támasztott követelmények, lásd: [PKI-tanúsítványkövetelmények](../../core/plan-design/network/pki-certificate-requirements.md).|  
|**3. lépés:** Telepítse és konfigurálja az Alkalmazáskatalógus webszolgáltatási pontját és az Alkalmazáskatalógus webhelyet.|Telepítenie kell mindkét helyrendszerszerepköröket ugyanazon a helyen. Nem szükséges azokat ugyanarra a helyrendszer-kiszolgálóra vagy ugyanazon Active Directory-erdőn belül telepíteni. Az Alkalmazáskatalógus webszolgáltatási pontját azonban a helyadatbázissal azonos erdőben kell lennie.|További információ a helyrendszerszerepkörök elhelyezéséről [helyrendszer-kiszolgálók és helyrendszerszerepkörök tervezése](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).<br /><br /> Az Alkalmazáskatalógus webszolgáltatási pontját és az Alkalmazáskatalógus weboldal-elérési pontjának konfigurálásával kapcsolatban lásd: **3. lépés: Telepítse és konfigurálja az Alkalmazáskatalógus helyrendszerszerepkörök**.|  
|**4. lépés:** Az Alkalmazáskatalógus és a Szoftverközpontra vonatkozó ügyfélbeállítások konfigurálása.|Ha a cél az, hogy minden felhasználónál ugyanaz legyen a beállítás, konfigurálja az ügyfél alapértelmezett beállításait. Ha nem ez a cél, konfigurálja az adott gyűjteményekre vonatkozó egyéni ügyfélbeállításokat.|Ügyfélbeállítások kapcsolatban bővebben lásd: [kapcsolatos](../../core/clients/deploy/about-client-settings.md).<br /><br /> Ezek az ügyfélbeállítások konfigurálásáról bővebben: **4. lépés: Az Alkalmazáskatalógus és a Szoftverközpontra vonatkozó ügyfélbeállítások konfigurálása**.|  
|**5. lépés:** Az Alkalmazáskatalógus működőképességének ellenőrzése.|Az Alkalmazáskatalógus közvetlenül böngészőből vagy a Szoftverközpontból is használhatja.|Lásd: **5. lépés: Az Alkalmazáskatalógus működőképességének ellenőrzése**.|  

## <a name="supplemental-procedures-to-install-and-configure-the-application-catalog-and-software-center"></a>Kiegészítő eljárások az alkalmazáskatalógus és a Szoftverközpont telepítéséhez és konfigurálásához  
 A következő információkra támaszkodhat, amennyiben az előbbi táblázat lépéseihez további eljárások szükségesek.  

###  <a name="step-3-install-and-configure-the-application-catalog-site-system-roles"></a>3. lépés: Telepítse és konfigurálja az Alkalmazáskatalógus helyrendszerszerepkörök  
 Ezek az eljárások konfigurálják a helyrendszerszerepköröket az alkalmazáskatalógusra vonatkozóan. Válassza ki, attól függően, hogy fog egy új helyrendszer-kiszolgálót telepít, vagy egy meglévő helyrendszer-kiszolgálót használ a két alábbi eljárások egyikét:  

> [!NOTE]  
>  Az alkalmazáskatalógus másodlagos helyen vagy központi felügyeleti helyen nem telepíthető.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-new-site-system-server"></a>Telepítse és konfigurálja az Alkalmazáskatalógus helyrendszereinek: Új helyrendszer-kiszolgáló  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **helyrendszer-kiszolgáló létrehozása**.  

4.  Az a **általános** lapon adja meg a helyrendszer általános beállításait, és válassza a **következő**.  

    > [!TIP]  
    >  Ha azt szeretné, hogy ügyfélszámítógépek számára, hogy az interneten keresztül használni az Alkalmazáskatalógust, adja meg az internetes teljesen minősített tartománynevét (FQDN).  

5.  Az a **Rendszerszerepkör kiválasztása** lapon jelölje be **Alkalmazáskatalógus webszolgáltatási pontja** és **Alkalmazáskatalógus weboldal-elérési pontja** az elérhető szerepkörök listájából, és válassza a **tovább**.  

6.  Fejezze be a varázsló futtatását.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-existing-site-system-server"></a>Telepítse és konfigurálja az Alkalmazáskatalógus helyrendszereinek: Meglévő helyrendszer-kiszolgáló  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**, majd válassza ki az alkalmazáskatalógushoz használni kívánt kiszolgálót.  

3.  Az a **Home** lap a **Server** csoportjában válassza **helyrendszer-szerepkörök hozzáadása**.  

4.  Az a **általános** lapon adja meg a helyrendszer általános beállításait, és válassza a **következő**.  

    > [!TIP]  
    >  Ha azt szeretné, hogy ügyfélszámítógépek számára, hogy az interneten keresztül használni az Alkalmazáskatalógust, adja meg az internetes teljesen minősített tartománynevét (FQDN).  

5.  Az a **Rendszerszerepkör kiválasztása** lapon jelölje be **Alkalmazáskatalógus webszolgáltatási pontja** és **Alkalmazáskatalógus weboldal-elérési pontja** az elérhető szerepkörök listájából, és válassza a **tovább**.  

6.  Fejezze be a varázsló futtatását.  

7. Állapotüzenetek és a naplófájlok vizsgálatával ellenőrizze a helyrendszerszerepkörök telepítését:  

    Állapotüzenetek: Az összetevőket használnak **SMS_PORTALWEB_CONTROL_MANAGER** és **SMS_AWEBSVC_CONTROL_MANAGER**.  

    Például Állapotazonosítója **1015** a **SMS_PORTALWEB_CONTROL_MANAGER** megerősíti, hogy a Helyösszetevő-kezelő sikeresen telepítette az Alkalmazáskatalógus weboldal-elérési pontját.  

    Naplófájlok: Keresse meg **SMSAWEBSVCSetup.log** és **SMSPORTALWEBSetup.log**.  

    További információért keresse meg a **awebsvcMSI.log** és **portlwebMSI.log** naplófájlok.  

###  <a name="step-4-configure-the-client-settings-for-the-application-catalog-and-software-center"></a>4. lépés: Az Alkalmazáskatalógus és a Szoftverközpontra vonatkozó ügyfélbeállítások konfigurálása  
 Ez az eljárás az alkalmazáskatalógus és a Szoftverközpont a hierarchiában található összes eszközre érvényes alapértelmezett ügyfélbeállításait konfigurálja. Ha azt szeretné, hogy ezek a beállítások csak bizonyos eszközökre vonatkoznak, hozzon létre egy egyéni ügyfélbeállítást, és központilag telepítenie kell egy gyűjteményt, amely a a konkrét beállításokkal majd rendelkező eszközöket. Egyéni Eszközbeállítás létrehozásáról bővebben lásd: a [létrehozása és egyéni ügyfélbeállítások központi telepítése](../../core/clients/deploy/configure-client-settings.md#create-and-deploy-custom-client-settings) szakasz a [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-settings.md) cikk.  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

3.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

4.  Ellenőrizze és konfigurálja a felhasználói értesítésekhez, az alkalmazáskatalógushoz és a Szoftverközponthoz kapcsolódó beállításokat. Példa:  

    1.  **Számítógépügynök** csoport:  

        -   **Alapértelmezett alkalmazáskatalógus webhely pont**  

        -   **Az alapértelmezett alkalmazáskatalógus webhely hozzáadása az Internet Explorer megbízható helyek zónához**  

        -   **A Szoftverközpontban megjelenített név**  

            > [!TIP]  
            >  Adja meg az alkalmazáskatalógusban megjelenített szervezetnév és a webhely témájának konfigurálásához használja a **testreszabási** az Alkalmazáskatalógus webhelytulajdonságainak fülre.  

        -   **Új Szoftverközpont használata** -beállítása **Igen** Ha szeretné-e az új szoftverközpont, így a felhasználók kereshetnek és kereshessék az alkalmazásokat (amelyhez szükséges egy Silverlight-kompatibilis webböngésző) az Alkalmazáskatalógus elérése nélkül.  

        -   **Telepítési engedélyek**  

        -   **Értesítések megjelenítése az új központi telepítéseknél**  

    2.  **Energiagazdálkodás** csoport:  

        -   **A felhasználók kizárhassák az eszközeiket az energiagazdálkodásból**  

    3.  **Táveszközök** csoport:  

        -   **A felhasználók megváltoztathatják a házirend vagy az értesítés beállításait a szoftverközpontban**  

    4.  **Felhasználó-eszköz kapcsolat** csoport:  

        -   **A felhasználók definiálhassák elsődleges eszközeiket**  

    > [!NOTE]  
    >  További információ az ügyfélbeállítások,: [információ a System Center Configuration Manager ügyfélbeállításainak](../../core/clients/deploy/about-client-settings.md).  

5.  Válasszon **OK** bezárásához a **alapértelmezett ügyfélbeállítások** párbeszédpanel megnyitásához.  

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egy ügyfél házirend lekérésének kezdeményezéséhez, lásd: [ügyfelek kezelése](../../core/clients/manage/manage-clients.md).

#### <a name="how-to-customize-software-center-branding"></a>A Szoftverközpont márkajelzési testreszabása

A Szoftverközpont egyéni branding a következő szabályok szerint alkalmazza:

1. Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre nincs telepítve, akkor a szoftverközpont a szervezet nevét a **Számítógépügynök** ügyfélbeállítás **szervezetnév** jelenik meg a Szoftverközpontban. Útmutatásért lásd: [ügyfélbeállítások konfigurálása](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/configure-client-settings).
2. Ha az Alkalmazáskatalógus weboldal-elérési pontjának helykiszolgáló-szerepköre telepítve van, akkor a Szoftverközpont jelenít meg a szervezet nevét és az Alkalmazáskatalógus weboldal-elérési pont helykiszolgáló-szerepkörének tulajdonságaiban megadott színt. További információkért lásd: [Alkalmazáskatalógus weboldal-elérési pontjának konfigurációs beállításait](https://docs.microsoft.com/en-us/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#BKMK_ApplicationCatalog_Website).
3. Ha a Microsoft Intune-előfizetés konfigurálva, és a Configuration Manager csatlakoztatva van, akkor a Szoftverközpont jelenít meg a szervezet neve, a színt és vállalati emblémát az Intune-előfizetés tulajdonságai. További információ: [A Windows Intune-előfizetés konfigurálása](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription).

> [!IMPORTANT]  
>  Az Intune szolgáltatással 14 naponta ezért valószínűleg késleltetés előtt az Intune-ban végzett módosítások jelennek meg a Configuration Manager Szoftverközpont márkajelzéséhez képest szinkronizálva.

###  <a name="step-5-verify-that-the-application-catalog-is-operational"></a>5. lépés: Az Alkalmazáskatalógus működőképességének ellenőrzése  
 Az alábbi eljárásokkal ellenőrizheti az alkalmazáskatalógus működőképességét. Az Alkalmazáskatalógus közvetlenül böngészőből vagy a Szoftverközpontból is használhatja.  

> [!NOTE]  
>  Az Alkalmazáskatalógus működéséhez szükséges a Microsoft Silverlight, a Configuration Manager-ügyfél előfeltételeként automatikusan megtörténik. Ha az Alkalmazáskatalógust közvetlenül a böngészőből olyan számítógép, amelyen nincs telepítve a Configuration Manager-ügyfél használatával használja, először győződjön meg arról, hogy Microsoft Silverlight telepítve van-e a számítógépen.  

> [!TIP]  
>  Az alkalmazáskatalógus helytelenül fog működni a telepítés után a legtipikusabb okok közé tartoznak, hiányzó előfeltételeket. Ellenőrizze a helyrendszerszerepkörök előfeltételeit az alkalmazáskatalógus helyrendszerszerepköreire vonatkozóan. Ehhez a a [által támogatott konfigurációk](../../core/plan-design/configs/supported-configurations.md) cikk.  

> [!NOTE]  
>  Ha egy tartományi rendszergazdai fiókkal jelentkezett a Configuration Manager-ügyfél (például arról, hogy rendelkezésre áll-e új szoftverfrissítési üzenetek) értesítési üzenetek nem lesznek megjelenítve.  

### <a name="to-use-the-application-catalog-directly-from-a-browser"></a>Az Alkalmazáskatalógus közvetlenül böngészőből használata  

-   A böngészőben adja meg az Alkalmazáskatalógus webhely címét, és győződjön meg arról, hogy a weblap bemutatja a három lappal: **Alkalmazáskatalógus**, **Alkalmazásigénylések**, és **eszközök**.  

     Válassza ki és használja a megfelelő címet az alábbi listában az Alkalmazáskatalógushoz, ahol &lt;server&gt; a számítógép neve, intranetes teljes Tartományneve vagy internetes teljes Tartományneve:  

    -   Beállítások a HTTPS-ügyfélkapcsolatok és alapértelmezett helyrendszerszerepkörökhöz: **https://&lt;server&gt;/CMApplicationCatalog**  

    -   Beállítások a HTTP-ügyfélkapcsolatok és alapértelmezett helyrendszerszerepkörökhöz: **http://&lt;server&gt;/CMApplicationCatalog**  

    -   HTTPS-ügyfélkapcsolatok és egyéni beállítások: **https://&lt;server&gt;:&lt;port&gt;/&lt;webes alkalmazás neve&gt;**  

    -   HTTP-ügyfélkapcsolatok és egyéni beállítások: **http://&lt;server&gt;:&lt;port&gt;/&lt;webes alkalmazás neve&gt;**  

### <a name="to-use-the-application-catalog-from-software-center-does-not-apply-to-the-new-version-of-software-center"></a>Az Alkalmazáskatalógus használatához a Szoftverközpontból (nem érvényes a Szoftverközpont új verziójára)  

1.  Egy ügyfélszámítógépen válassza **Start** > **minden program** > **Microsoft System Center 2012** > **Configuration Manager** > **Szoftverközpont**.  

2.  Ha korábban a Szoftverközponthoz ügyfélbeállításként megadott szervezetnevet, ellenőrizze, hogy a név a megadott formában jelenik-e meg.  

3.  Válasszon **található további alkalmazásokat az alkalmazáskatalógusból**, és győződjön meg arról, hogy a lap megjeleníti-e a három lappal: **Alkalmazáskatalógus**, **Alkalmazásigénylések**, és **eszközök**.  

> [!WARNING]  
>  Az Alkalmazáskatalógus helyrendszerszerepkörök telepítése után nem azonnal látni fogja az Alkalmazáskatalógus kiválasztásakor a **az alkalmazáskatalógusban további alkalmazások keresése** hivatkozás a Szoftverközpontból. Az alkalmazáskatalógus a Szoftverközpontból akkor válik elérhetővé, amikor az ügyfél legközelebb letölti az ügyfélházirendjét, illetve legfeljebb 25 órával azt követően, hogy megtörtént az alkalmazáskatalógus helyrendszerszerepköreinek telepítése.  

