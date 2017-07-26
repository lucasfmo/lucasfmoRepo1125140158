---
title: "Készültségi frissítése |} System Center Configuration Managerben"
description: "Frissítési készültségének integrálhatja a Configuration Managerrel. Hozzáférés a frissítés kompatibilitásának adatokat a felügyeleti konzolon. A frissítéshez vagy javítási Céleszközök."
keywords: 
author: brenduns
ms.author: brenduns
manager: angerobe
ms.date: 3/1/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.translationtype: Machine Translation
ms.sourcegitcommit: dcbcd57b95f304f007e92ebe2b9aeefb4b579662
ms.openlocfilehash: 986d0446209f6e7eac1b681066d1b2e2305e1975
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Frissítési készültségének integrálása a System Center Configuration Managerrel
Frissítési készültségének (korábbi nevén frissítése Analytics) segítségével mérheti fel, és elemezze eszköz készültsége és a Windows 10-es kompatibilitási egyszerűbbé és gördülékenyebb frissítések engedélyezéséhez teszi lehetővé. Frissítési készültségének integrálhatja a Configuration Manager ügyfél a frissítés kompatibilitásának adatok a Configuration Manager felügyeleti konzol eléréséhez. Majd képes lesz a frissítéshez vagy javítási céleszközökre az eszköz listából.

Frissítési készültségének egy olyan megoldás a Microsoft Operations Management Suite (OMS). További információ a frissítési készültségének [Ismerkedés a frissítési készültségének](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

## <a name="configure-clients"></a>Ügyfelek konfigurálása

Van néhány konfigurálási lépés, hogy szükség van annak ellenőrzéséhez, hogy az ügyfelek számára adatokat képes biztosítani a frissítési készültségének:

-  Telemetria ügyfélbeállítások konfigurálása, lásd: [a szervezet Windows beállítása telemetriai](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization).
-  Telepítse a KB ismertetett a * telepítse a kompatibilitási frissítés és a kapcsolódó KB * szakasza [Ismerkedés a frissítési készültségének](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).

    > [!NOTE]
    > Letöltheti a parancsfájl az ügyfél-beállítási feladatok automatizálására. Tekintse meg a *a frissítési készültségének üzembe helyezési parancsfájl futtatása* szakasza [Ismerkedés a frissítési készültségének](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness) a parancsfájllal kapcsolatos információkat.

## <a name="create-a-connection-to-upgrade-readiness"></a>Kapcsolatot létesíthet készültségi frissítése

### <a name="prerequisites"></a>Előfeltételek

- Ahhoz, hogy vegye fel a kapcsolatot, a Configuration Manager-környezetben, először konfigurálnia kell egy [szolgáltatáskapcsolódási pont](/sccm/core/servers/deploy/configure/about-the-service-connection-point) a egy [online módban](https://azure.microsoft.com/en-us/documentation/articles/resource-group-create-service-principal-portal/). Ha a kapcsolat hozzá a környezethez, azt is telepíti a Microsoft Monitoring Agent azon a számítógépen, amelyen a helyrendszerszerepkör.
- A Configuration Manager "Web Application and/or Web API" felügyeleti eszközként regisztrálja, és lekérése a [ügyfél-azonosító az ehhez a regisztrációhoz](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
- Hozzon létre egy ügyfélkulcsot a regisztrált felügyeleti eszköz az Azure Active Directoryban.
- Az Azure felügyeleti portálon, adja meg a regisztrált web app az OMS-ben, hozzáféréssel a [adja meg a Configuration Manager az OMS Szolgáltatáshoz engedélyekkel](https://azure.microsoft.com/en-us/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

    > [!IMPORTANT]
    > OMS hozzáféréssel konfigurálásakor ügyeljen arra, hogy válassza ki a **közreműködő** szerepkört, és az engedélyek hozzárendelése a regisztrált alkalmazáshoz tartozó erőforráscsoport.

### <a name="create-the-connection"></a>A kapcsolat létrehozása

1.  A Configuration Manager konzolon kattintson **felügyeleti** > **Felhőszolgáltatások** > **frissítési készültségének összekötő** > **frissítése Analytics kapcsolat létrehozása** elindítani a **hozzáadása Analytics kapcsolat varázsló**.
3.  Az a **Azure Active Directory** adja meg a jobb **bérlői**, **ügyfél-azonosító**, és **titkos ügyfélkulcsot**, majd jelölje be **következő**.
4.  Az a **frissítési készültségének** képernyőn, adja meg a kapcsolati beállításokat kitöltésével a **Azure-előfizetés**, **Azure erőforráscsoport**, és **Operations Management Suite-munkaterülettel**.
5.  Ellenőrizze, hogy a kapcsolat beállításait a **összegzés** képernyőt, majd válassza ki **következő**.

    > [!NOTE]
    > Csatlakoztatni kell frissítési készültségének a legfelső szintű helyet a hierarchiában. Ha a frissítési készültségének csatlakozni egy önálló elsődleges helyhez, és adja hozzá a központi adminisztrációs hely a környezetben, akkor törölje, majd hozza létre újra az OMS-kapcsolatot az új hierarchiában.

### <a name="complete-upgrade-readiness-tasks"></a>Teljes készültségi frissítési feladatok  

Miután már létrehozta a kapcsolatot a Configuration Managerben, hajtsa végre ezeket a feladatokat a [Ismerkedés a frissítési készültségének](https://technet.microsoft.com/itpro/windows/deploy/manage-windows-upgrades-with-upgrade-readiness).  

1. A UpgradeReadiness szolgáltatás hozzáadása az OMS-munkaterület.  
2. Egy kereskedelmi. készítése  
3. Előfizetni a frissítési készültségének.   

## <a name="use-the-upgrade-readiness-deployment-script"></a>A frissítési készültségének telepítési parancsfájl használata  

A frissítési készültségének feladatok automatizálásához, és problémák megosztása a Microsofttal adatok hibaelhárítása **frissítési készültségének telepítési parancsfájl**.  
A frissítési készültségének telepítési parancsfájl a következőket teszi:  

- Beállítja a kereskedelmi azonosító kulcs + CommercialDataOptIn + RequestAllAppraiserVersions kulcsok.  
- Ellenőrzi, hogy felhasználói számítógépek képes adatokat küldeni a Microsoftnak.  
- Ellenőrzi, hogy a számítógép rendelkezik-e a függőben lévő újraindítás.   
- Ellenőrzi, hogy a KB legújabb verziójának 10.0.x csomag telepítve van (10.0.14913 vagy a következő kiadásokban szükséges).  
- Ha engedélyezve van, bekapcsolja a részletes módot hibaelhárítási.  
- Kezdeményezi a gyűjtemény a telemetriai adatok, amelyet a Microsoft a szervezet frissítési készültségének ellenőrzéséhez.  
- Ha engedélyezve van, megjelennek a parancsfájl egy parancssori ablakban, így a problémák (sikeres vagy sikertelen lesz minden lépés) láthatósága és/vagy ír a naplófájlba.  

### <a name="to-run-the-upgrade-readiness-deployment-script"></a>A frissítési készültségének üzembe helyezési parancsfájl futtatása:  

1. Töltse le a [frissítési készültségének telepítési parancsfájl](https://go.microsoft.com/fwlink/?LinkID=822966&clcid=0x409) és UpgradeReadiness.zip kibontásához. A fájlokat a **diagnosztika** mappa szükség, csak akkor, ha azt tervezi, a hibakeresési mód a parancsfájl futtatásához.  
2. Ezek a paraméterek a RunConfig.bat szerkesztése:  
- Naplózási adatok tárolási helyét. Példa: % SystemDrive%\URDiagnostics. Naplózási adatok tárolhatók távoli fájlmegosztás vagy a helyi könyvtárat. A parancsprogram le van tiltva a naplófájl a megadott elérési út létrehozása, ha a meghajtót, amelyen a Windows-könyvtár létre a rendszernapló fájljaiban.  
- Kereskedelmi azonosító kulcsa.  
- Alapértelmezés szerint a parancsfájl napló adatokat küld a konzol és a naplófájlt is. Az alapértelmezett viselkedés módosításához használja a következő lehetőségek közül:  
    - logMode = 0 napló csak konzolon  
    - logMode = 1 log fájl és a konzol  
    - logMode = 2, a következő fájl csak naplózása  
    - A hibaelhárításhoz, állítsa be **isVerboseLogging** való **$true** szereplő információkat, amelyek segíthetnek a problémák diagnosztizálásával létrehozásához. Alapértelmezés szerint **isVerboseLogging** értéke **$false**. Győződjön meg arról, a diagnosztika mappa telepítve van a parancsfájl ebben a módban használandó ugyanabban a könyvtárban.  
    - Értesítse a felhasználókat, ha azokat újra kell indítania a számítógépet. Alapértelmezés szerint értéke OFF.  

3. A paraméterek a RunConfig.bat szerkesztésének befejezése után futtassa a parancsfájlt rendszergazdaként.  


## <a name="view-microsoft-upgrade-readiness-properties-in-configuration-manager"></a>A Microsoft frissítési készültségének tulajdonságainak megtekintése a Configuration Managerben  

1.  A Configuration Manager-konzolon lépjen a **Felhőszolgáltatások**, majd válassza **OMS-összekötő** megnyitásához a **OMS kapcsolat tulajdonságai** lap.  

2.  Ezen a lapon belül van két lap található:
  * A **Azure Active Directory** lapra mutat be a **bérlői**, **ügyfél-azonosító**, **ügyfél titkos kulcs lejárati**, és lehetővé teszi **ellenőrizze** a **titkos ügyfélkulcsot** , ha már lejárt.
  * A **frissítési készültségének** lapra mutat be a **Azure-előfizetés**, **Azure erőforráscsoport**, és **Operations Management Suite-munkaterülettel**.

## <a name="view-and-use-the-upgrade-information"></a>Megtekintése és használata a frissítési információ

Miután a Configuration Manager frissítési készültségének már integrált, az ügyfelek frissítési készültségének elemzése megtekintheti és majd hajtsa végre a műveletet.

1. Kattintson a Configuration Manager konzol **figyelés** > **áttekintése** > **frissítési készültségének**.
2. Tekintse át az adatokat, köztük a verziófrissítés készültségi állapotával és a Windows-eszközök telemetriai jelentő százalékát.
3. Az irányítópult az eszközök adatainak megtekintéséhez adott gyűjteményekre jeleníthetők meg.
4. Tekintse meg az eszközök adott készenléti állapotot, és az eszközökhöz tartozó dinamikus gyűjtemény létrehozása, hogy frissítse az eszközöket, ha készen áll, vagy hajtsa végre a műveletet, hogy azok készenléti állapotot.

