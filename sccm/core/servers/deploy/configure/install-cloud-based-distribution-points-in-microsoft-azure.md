---
title: "Felhőalapú terjesztési pontok telepítése |} Microsoft Docs"
description: "Ismerje meg, mit kell tennie, indítsa el a felhő alapú terjesztési pontok használatával a Microsoft Azure-ban."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f96905f50f879b843f98cb57c8a755aa856fb381
ms.openlocfilehash: 39b35cccf78bba4e69a7de0ca3a5a8dc516201e3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="install-cloud-based-distribution-points-in-microsoft-azure-for-system-center-configuration-manager"></a>A Microsoft Azure felhő alapú terjesztési pontok telepítése a System Center Configuration Manager

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager felhő alapú terjesztési pontok is telepítheti a Microsoft Azure-ban. Ha nem ismeri, és a felhő alapú terjesztési pontok, lásd: [felhőalapú terjesztési pontot használ](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) folytatása előtt.

 A telepítés megkezdése előtt győződjön meg arról, hogy rendelkezik-e a szükséges tanúsítványfájlokkal:  

-   A Microsoft Azure felügyeleti tanúsítvánnyal, amely egy .cer kiterjesztésű fájlba, és egy .pfx fájlba van exportálva.  

-   A Configuration Manager felhő alapú terjesztési pont szolgáltatási tanúsítványához, amely egy .pfx fájlba van exportálva.  

    > [!TIP]
    >   Ezekről a tanúsítványokról további információkért lásd: a szakasz a felhőalapú terjesztési pontjának a [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) témakör. A felhőalapú terjesztési pont szolgáltatási tanúsítványához telepítését bemutató példát, az "A szolgáltatás-tanúsítvány a felhőalapú terjesztési pontok telepítése" szakaszában talál [részletes példa a nyilvános kulcsokra épülő infrastruktúra központi telepítése a System Center Configuration Manager tanúsítványok: Windows Server 2008 hitelesítésszolgáltató](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  


 Miután telepítette a felhőalapú terjesztési pont, Azure automatikusan előállít egy GUID Azonosítót a szolgáltatáshoz, és hozzáfűzi ezt a DNS-utótagját **cloudapp.net**. A GUID Azonosítónak a használatával kell konfigurálnia a DNS rendszert egy DNS-alias (CNAME rekord). Ez lehetővé teszi, hogy a Configuration Manager felhő alapú terjesztési pont szolgáltatási tanúsítványa az automatikusan előállított GUID azonosítóhoz megadott szolgáltatásnevet leképezik.  

 Ha proxywebkiszolgálót használ, lehetséges, hogy a proxybeállítások megadására a a terjesztési pontot üzemeltető felhőszolgáltatással való kommunikációhoz.  

##  <a name="BKMK_ConfigWindowsAzureandInstallDP"></a>Állítson be Azure és a felhő alapú terjesztési pontok telepítése  
 Az alábbi eljárásokkal állíthatja be Azure terjesztési pontok támogatásához, és a Configuration Managerben a felhő alapú terjesztési pontról telepítse.  

### <a name="to-set-up-a-cloud-service-in-azure-for-a-distribution-point"></a>Egy felhőalapú szolgáltatás, az Azure-ban a terjesztési pontok beállítása  

1.  Nyisson meg egy webböngészőt, https://manage.windowsazure.com, az Azure portálra, és elérni a fiókját.  

2.  Kattintson a **Hosted Services, Storage Accounts & CDN**, majd válassza ki **felügyeleti tanúsítványok**.  

3.  Kattintson a jobb gombbal az előfizetéshez, majd válassza ki **tanúsítvány hozzáadása**.  

4.  A **tanúsítványfájl**, azt a .cer fájlt, amely a felhőalapú szolgáltatás, és kattintson az Azure exportált felügyeleti tanúsítványát tartalmazza **OK**.  

A felügyeleti tanúsítvány betöltődik az Azure-ban, és most már telepítheti a felhőalapú terjesztési pont.  

### <a name="to-install-a-cloud-based-distribution-point-for-configuration-manager"></a>A felhőalapú terjesztési pont a Configuration Manager telepítése  

1.  Hajtsa végre az előző eljárás állíthat be egy felhőszolgáltatás felügyeleti tanúsítvánnyal az Azure-ban.  

2.  Az a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki a **Felhőszolgáltatások**, és válassza ki **felhőalapú terjesztési pontok**. Az a **Home** lapra, majd **felhőalapú terjesztési pont létrehozása**.  

3.  Az a **általános** a felhőalapú terjesztési pont létrehozása varázsló, állítsa be a következő oldalán:  

    -   Adja meg a **előfizetés-azonosító** Azure-fiókját.  

        > [!TIP]  
        >  Azure-előfizetése Azonosítóját az Azure portálon található.  

    -   Adja meg a **felügyeleti tanúsítvány**. Kattintson a **Tallózás** adja meg a .pfx fájlt, amely az Azure exportált felügyeleti tanúsítványát tartalmazza, és írja be a jelszót a tanúsítványhoz. Másik lehetőségként megadhat egy Azure SDK 1.7 verziójú 1 .publishsettings fájlt.  

4.  Kattintson a **Tovább** gombra. A Configuration Manager kapcsolódik az Azure-ba, a felügyeleti tanúsítvány érvényesítéséhez.  

5.  Az a **beállítások** lapon, fejezze be a következőt, majd **következő**:  

    -   A **régió**, válassza ki az Azure-régió, ahol szeretné létrehozni ezt a terjesztési pontot üzemeltető felhőszolgáltatást.  

    -   A **tanúsítványfájl**, adja meg az exportált tanúsítványt a Configuration Manager felhő alapú terjesztési pont szolgáltatás tartalmazó .pfx fájlt. Adja meg a jelszót.  

        > [!NOTE]  
        >  A **szolgáltatás FQDN** a tanúsítvány tulajdonos neve mező automatikusan feltöltődik értékkel. A legtöbb esetben nem rendelkezik a szerkesztéshez. A kivétel: Ha egy tesztelési környezetben helyettesítő tanúsítványt használ. Például ebben az esetben előfordulhat, hogy nem adhat az állomásnevet, hogy az azonos DNS-utótaggal rendelkező több számítógép használhatja a tanúsítványt. Ebben a forgatókönyvben a tanúsítvány tulajdonosának hasonló értéket tartalmaz **CN =\*. contoso.com**, és a Configuration Manager megjelenít egy üzenetet, hogy meg kell adnia a megfelelő FQDN-nel. Kattintson a **OK** zárja be az üzenetet, és írjon be egy egyedi nevet a teljes FQDN megadásához a DNS-utótag elé. Például előfordulhat, hogy hozzá **clouddp1** adhatja meg a teljes szolgáltatási FQDN **clouddp1.contoso.com**. A szolgáltatás FQDN abban a tartományban, egyedi legyen, és nem felel meg a tartományhoz csatlakoztatott eszközön.  
        >   
        >  Helyettesítő tanúsítványok csak tesztelési környezetben használhatók.  

6.  Az a **riasztások** beállítása tárolási kvótákat, az átviteli kvótákat, és ezek mely százalékértékénél kéri, azt szeretné, hogy hány százaléka létrehozása a Configuration Manager riasztást küld a lapon. Ezután kattintson a **Tovább** gombra.  

7.  Fejezze be a varázslót.  

A varázsló létrehoz egy új kezelt szolgáltatást a felhőalapú terjesztési pont. A varázsló bezárása után a telepítési folyamatot a felhőalapú terjesztési pont a Configuration Manager konzolon figyelheti meg. Ugyanígy figyelheti a **CloudMgr.log** fájlt az elsődleges helykiszolgálón. Megfigyelheti, hogy az Azure-portálon a felhőszolgáltatás kiépítését.  

> [!NOTE]  
>  Az Azure-ban új terjesztési pont kiépítése akár 30 percet is igénybe vehet. A következő üzenet ismételten megjelenhet a **CloudMgr.log** a tárolási fiók kiépítéséig fájlt: **Várakozás, ellenőrizze a tároló létezésének. Ellenőrzés 10 másodperc múlva**. Ezt követően a szolgáltatás létrehozása és konfigurálva.  

 Azonosíthatja, hogy a felhő alapú terjesztési pont telepítése befejeződött-e az alábbi módszerekkel:  

-   Az Azure portálon a **telepítési** a felhőalapú terjesztési pont állapotát jeleníti meg az egy **készen**.  

-   A Configuration Manager konzolon a a **felügyeleti** munkaterületen **Hierarchiakonfiguráció**, **felhő** csomópont, a felhőalapú terjesztési pont mezőjében a **készen**.  

-   A Configuration Manager Azonosítójú állapotüzenetet jeleníti meg **9409** az SMS_CLOUD_SERVICES_MANAGER összetevőhöz.  

##  <a name="BKMK_ConfigDNSforCloudDPs"></a>Állítsa be a felhő alapú terjesztési pontok névfeloldás  
 Mielőtt az ügyfelek hozzáférhessenek a felhőalapú terjesztési pont, fel kell tudnia oldani a felhőalapú terjesztési pont nevét egy Azure által kezelt IP-címre. Ügyfelek ehhez két fázisból áll:  

1.  A Configuration Manager felhő alapú terjesztési pont szolgáltatásának tanúsítványát a Azure szolgáltatásbeli teljes Tartománynévre megadott szolgáltatásnevet leképezik. Ez a teljes tartománynév tartalmaz egy GUID Azonosítót és a DNS-utótagja **cloudapp.net**. A felhőalapú terjesztési pont telepítése után a rendszer automatikusan előállítja a GUID. Megjelenik a teljes Tartománynevet az Azure-portálon a Vezérlőpultjának a **webhely URL-címe** a felhőszolgáltatás irányítópultján. Hely URL-cím **http://d1594d4527614a09b934d470.cloudapp.net**.  

2.  Az Azure által lefoglalt IP-címre oldja fel az Azure szolgáltatásbeli teljes Tartománynevet. Az IP-cím az Azure-portálon a felhőszolgáltatás irányítópultján is meghatározható, és nevű **PUBLIC VIRTUAL IP ADDRESS (VIP)**.  

A Configuration Manager felhő alapú terjesztési pont szolgáltatási tanúsítványához megadott szolgáltatásnevet leképezik a (például **clouddp1.contoso.com**) Azure szolgáltatásbeli teljes Tartománynevet (például **d1594d4527614a09b934d470.cloudapp.net**), az interneten lévő DNS-kiszolgálók rendelkeznie kell egy DNS-alias (CNAME rekord). Az ügyfelek fel tudják oldani a Azure szolgáltatásbeli teljes Tartománynevet az IP-címre az interneten lévő DNS-kiszolgálók használatával.  

##  <a name="BKMK_ConfigProxyforCloud"></a>Proxybeállítások felhőszolgáltatásokat kezelő elsődleges helyekhez beállítása  
 Ha felhőszolgáltatásokat használ a Configuration Managerrel, a felhőalapú terjesztési pontot felügyelő elsődleges helykiszolgálónak kapcsolódnia kell az Azure-portálon kell lennie. A helyhez csatlakozik, használja a **rendszer** fiók az elsődleges hely számítógépének. Ez a kapcsolat az elsődleges hely kiszolgálóján az alapértelmezett webböngésző használatával.  

 Az elsődleges helykiszolgálón a felhőalapú terjesztési pontot kezelő lehetséges, hogy ahhoz, hogy az elsődleges hely elérje az internetet és Azure proxybeállítások beállítása.  

 A következő eljárással állíthatja be a Configuration Manager konzol az elsődleges helykiszolgáló proxybeállításait.  

> [!TIP]  
>  Is állíthatja be a proxykiszolgáló telepítésekor új helyrendszerszerepkört az elsődleges hely kiszolgálóján használatával a **helyrendszer-szerepkörök hozzáadása varázslóval**.  

#### <a name="to-set-up-proxy-settings-for-the-primary-site-server"></a>Az elsődleges helykiszolgáló proxybeállításait beállítása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Kiszolgálók és helyrendszerszerepkörök**elemre. Ezután válassza ki a felhőalapú terjesztési pontot kezelő elsődleges helykiszolgálón.  

3.  A részleteket tartalmazó ablaktáblán kattintson a jobb gombbal **Helyrendszert**, és kattintson a **tulajdonságok**.  

4.  A **helyrendszer tulajdonságainál**, jelölje be a **Proxy** lapon, majd állítsa be az elsődleges helykiszolgáló proxybeállításait.  

5.  Kattintson a **OK** menti a beállításokat.  

