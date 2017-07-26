---
title: "Helyek előfeltételei |} Microsoft Docs"
description: "További információk a System Center Configuration Manager-helyek a különböző típusú telepítéséhez szükséges előfeltételeket."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ff89d4aea6be871e64e0a788f054ba4cadb3e51d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="prerequisites-for-installing-system-center-configuration-manager-sites"></a>A System Center Configuration Manager-helyek telepítésének előfeltételei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A hely telepítésének megkezdése előtt tanácsos további tudnivalók a System Center Configuration Manager-helyek a különböző típusú telepítéséhez szükséges előfeltételeket.

## <a name="primary-sites-and-the-central-administration-site"></a>Elsődleges helyek és a központi adminisztrációs hely
A következő előfeltételek vonatkoznak egy központi adminisztrációs hely egy hierarchia első helyének telepítése, önálló elsődleges hely telepítése vagy egy alárendelt elsődleges hely telepítése. Ha a központi adminisztrációs hely egy hierarchia bővítése részeként telepíti, lásd: [önálló elsődleges hely kibővítése](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand) ebben a témakörben.

###  <a name="bkmk_PrereqPri"></a>Az elsődleges hely vagy központi adminisztrációs hely telepítésének előfeltételei  

-   A felhasználói fiókhoz, a rendszer telepíti a helyet a következő jogosultságokkal kell rendelkeznie:  

    -   **Rendszergazda** a helykiszolgáló számítógépen  
    -   **Rendszergazda** minden számítógépen, amely üzemelteti a **Helyadatbázis** vagy egy példányát a **SMS-szolgáltató** a hely  
    -   **Sysadmin** a helyadatbázist futtató SQL Server-példányon  

        > [!IMPORTANT]  
        >  Telepítés befejezése után a telepítőt futtató felhasználói fióknak, mind a helykiszolgáló számítógép fióknak kell továbbra is rendszergazdai jogosultsággal az SQL-kiszolgálón. Ne távolítsa el a rendszergazdai jogosultságok ezeket a fiókokat.  

-   Ha egy elsődleges helyet telepít, a következő további jogosultságok szükségesek:  
    -  **Rendszergazda** további számítógépeken, amelyeken a kezdeti felügyeleti pontot és terjesztési pont telepíti, vagy a helyrendszer-kiszolgálón  

-   Ha telepít egy új gyermek elsődleges hely egy központi adminisztrációs hely alá, a következő további jogosultságok szükségesek:  

    -   **Rendszergazda** a központi adminisztrációs helyet üzemeltető számítógépen  

    -   Szerepköralapú felügyeleti jogosultságokkal a Configuration Manager a biztonsági szerepkörrel egyenértékű **infrastruktúra-rendszergazda** vagy **teljes körű rendszergazda**  

-   A megfelelő telepítési adathordozót (Forrásfájlok), és onnan futtassa a telepítőt. A megfelelő forrásfájlokat különböző helyek telepítése kapcsolatos információkért lásd: [különböző helyek telepítésének beállításait](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) a a [helyek telepítését előkészítése](../../../../core/servers/deploy/install/prepare-to-install-sites.md) témakör.

-   A helykiszolgáló számítógépnek hozzáféréssel kell rendelkeznie a frissített Microsoft, az alábbi módszerek valamelyikével:
    -  A telepítés megkezdése előtt töltse le, és ezeket a fájlokat, a helyi hálózaton egy példányának tárolása a [a telepítő letöltési segédprogramja](../../../../core/servers/deploy/install/setup-downloader.md).
    -  Ha egy helyi másolata nem érhető el a fájlt, a helykiszolgáló internetkapcsolattal kell rendelkeznie, ezért a telepítés során a Microsoft ezeket a fájlokat tölthet le.

- Mielőtt kibővíthetne egy önálló elsődleges helyet, amely rendelkezik egy szolgáltatási kapcsolódási pont helyrendszerszerepkör van telepítve, el kell távolítania a szolgáltatáskapcsolódási pont. Ezt a szerepkört csak egy példánya engedélyezett a hierarchiában, és csak a legfelső szintű helyen a hierarchia számára engedélyezett. A állomástelepítéshez újra kell telepítenie a szerepkört a központi adminisztrációs hely telepítése során.
- A helykiszolgáló és a Helyadatbázis-számítógépnek teljesítenie kell az összes előfeltételként szükséges konfigurációt. A telepítés megkezdése előtt is [előfeltétel-ellenőrző manuális futtatásával](../../../../core/servers/deploy/install/prerequisite-checker.md) a problémák azonosítása és megoldása.  


### <a name="bkmk_expand"></a>Egy önálló elsődleges hely bővítésének előfeltételei
Egy önálló elsődleges helyet meg kell felelnie a következő előfeltételek teljesülését, mielőtt egy központi adminisztrációs helyet tartalmazó hierarchiává bővítheti:

-   **Telepítenie kell az új központi adminisztrációs hely telepítése CD-ről adathordozó használatával. Legújabb mappában (amely a forrásfájlokat tartalmaz), amely megfelel az önálló elsődleges hely verziója**

 Található verzió egyezés érdekében lévő forrásfájlok használata a [CD-ről. Legújabb mappa](/sccm/core/servers/manage/the-cd.latest-folder) az önálló elsődleges helyen.

 A megfelelő forrásfájlokat különböző helyek telepítése kapcsolatos további információkért lásd: [különböző helyek telepítésének beállításait](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) a a [helyek telepítését előkészítése](../../../../core/servers/deploy/install/prepare-to-install-sites.md) témakör.


-   **Az önálló elsődleges helyen nem lehet beállítva, hogy adatokat telepítsen át egy másik Configuration Manager-hierarchia**  

     Az önálló elsődleges hely aktív áttelepítési leállítás, a többi Configuration Manager-hierarchia kell, és távolítsa el az áttelepítéshez szükséges összes konfigurációkat. Ez magában foglalja az áttelepítési feladatok, amelyek nem végzett, az adatgyűjtést, és az aktív forráshierarchia beállításait.  

     Erre akkor szükség, mert az áttelepítési műveleteket a hierarchia legfelső szintű helye végzi, és az áttelepítési beállításokat nem veszi át a központi adminisztrációs helyet egy önálló elsődleges hely kibővítésekor.  

     Az önálló elsődleges hely kibővítését újrakonfigurálja az áttelepítést az elsődleges helyen, a központi adminisztrációs hely áttelepítéssel kapcsolatos műveleteket hajtja végre. Áttelepítési konfigurálásával kapcsolatos további információkért lásd: [forráshierarchiák és Forráshelyek System Center Configuration Manager az áttelepítés konfigurálása](../../../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md).  

-   **Az új központi adminisztrációs helyet futtató számítógép számítógépfiókjának a standa egyetlen elsődleges helyen, a rendszergazda felhasználói csoport tagjának kell lennie.**  

     Az önálló elsődleges hely sikeres bővítéséhez az új központi felügyeleti hely számítógépfiókjának rendelkeznie **rendszergazda** jogok az önálló elsődleges helyen. Erre azért szükség csak a helybővítés során. A fiók helybővítés befejezése távolíthatók el a felhasználói csoportot az elsődleges helyen.  

-   **Az új központi adminisztrációs hely telepítéséhez a telepítőt futtató felhasználói fióknak szerepköralapú felügyeleti jogosultságokkal kell rendelkeznie az önálló elsődleges helyen**  

     A hely bővítése részeként a központi adminisztrációs hely telepítéséhez a központi adminisztrációs hely telepítéséhez a telepítőt futtató felhasználói fióknak definiálni kell a szerepkör alapú felügyelet, vagyis az önálló elsődleges helyen egy **teljes körű rendszergazda** vagy egy **infrastruktúra-rendszergazda**.  

-   **Mielőtt bővítené a helyet el kell távolítania az önálló elsődleges helyről a következő helyrendszer-szerepkörök:**  

    -   Eszközintelligencia-katalógus szinkronizálási pontja  
    -   Endpoint Protection-pont  
    -   Szolgáltatáskapcsolódási pont  

   Ezen helyrendszerszerepkörök csak a hierarchia legfelső szintű helyén támogatott. Ezen helyrendszerszerepkörök, ezért el kell távolítania az önálló elsődleges hely kibővítése előtt. Miután a hely kibővítése, telepítse újra a helyrendszerszerepkört a központi adminisztrációs helyen.  

    Minden más helyrendszer-szerepkört az elsődleges helyen telepített maradhat.  

-   **Az az SQL Server Service Broker (SSB) az önálló elsődleges hely és a központi adminisztrációs helyet telepítő számítógép között portnak nyitva kell lennie.**  

     A központi adminisztrációs hely és az elsődleges hely közötti sikeres replikálja az adatokat, a Configuration Manager megköveteli egy nyitott port használandó SSB a két hely között. Ha a központi adminisztrációs helyet telepít, és kibővít egy önálló elsődleges helyet, az Előfeltételek ellenőrzése nem ellenőrizze, hogy állít be az SSB porton nyissa meg az elsődleges helyen.  


## <a name="bkmk_secondary"></a>A másodlagos helyek
A másodlagos helyek telepítésének előfeltételei a következők:
-   A másodlagos hely telepítését a Configuration Manager konzolon a rendszergazda biztonsági szerepkörrel egyenértékű szerepköralapú felügyeleti jogosultságokkal kell rendelkeznie **infrastruktúra-rendszergazda** vagy **teljes körű rendszergazda**.  
-   A szülő elsődleges hely a számítógép fiókjának szerepelnie kell egy **rendszergazda** a másodlagos helykiszolgáló számítógépen.  
-   Amikor a másodlagos hely az SQL Server korábban telepített példányát használja a másodlagos Helyadatbázis futtatására:  

    -   A **számítógépfiók** a szülő elsődleges helynek kapcsolódnia kell **sysadmin** jogosultságok a másodlagos helykiszolgáló számítógépen az SQL Server példányon.  

    -   A **helyi rendszer** a másodlagos helykiszolgáló számítógép fióknak rendelkeznie kell **sysadmin** jogosultságok a másodlagos helykiszolgáló számítógépen az SQL Server példányon.  

        > [!IMPORTANT]  
        >  Telepítés befejezése után mindkét fióknak kell továbbra is rendszergazdai jogosultsággal az SQL-kiszolgálón. Ne távolítsa el a rendszergazdai jogosultságok ezeket a fiókokat.  

-   A másodlagos helykiszolgáló számítógépén meg kell felelnie az összes előfeltételként szükséges konfigurációt, mely tartalmazza az SQL Server és a felügyeleti és terjesztési pont az alapértelmezett helyrendszerszerepköröket.  

