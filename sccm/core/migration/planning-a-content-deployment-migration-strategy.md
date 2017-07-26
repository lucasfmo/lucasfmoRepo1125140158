---
title: "Tartalom áttelepítésének |} Microsoft Docs"
description: "Terjesztési pontok használatával kezeli a tartalom, amíg a System Center Configuration Manager célhierarchiába telepít át adatokat."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66f7759c-6272-4116-aad7-0d05db1d46cd
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 468673581e0464fab21397c472b76708b8a5438b
ms.openlocfilehash: 25619d91522193178e0415f649ca4b34c94ecc89
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-content-deployment-migration-strategy-in-system-center-configuration-manager"></a>Tervezze meg a tartalom központi telepítési stratégiájának a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager célhierarchiába adatok aktív áttelepítését, amíg a forrás-és a Configuration Manager-ügyfelek hozzáférhetnek a forráshierarchiába központilag telepített a forráshierarchiában lévő tartalomhoz. Áttelepítés használatával frissítésekor vagy hozzárendelésének megváltoztatásakor a terjesztési pontokat a forráshierarchiából a célhierarchiában lévő terjesztési pontokra lesz. Terjesztési pontok megosztásakor, frissítésekor vagy átrendelésekor ennek a stratégiának a segítségével elkerülhető, hogy a tartalmat ismét központilag kelljen telepíteni az új, célhierarchiában lévő kiszolgálókra az áttelepített ügyfelek számára.  

Bár a célhierarchiában lévő tartalmat újból létrehozhatja és terjesztheti, azonban ezt a tartalmat az alábbi lehetőségeket kihasználva is kezelheti:  

-   A forráshierarchiában lévő terjesztési pontok megosztása a célhierarchiában lévő ügyfelekkel.  

-   Frissítse a különálló Configuration Manager 2007 terjesztési pontokat vagy a Configuration Manager 2007 másodlagos helyek a forráshierarchiában található legyen, a célhierarchiában lévő terjesztési pontokra.  

-   A System Center Configuration Manager forráshierarchia egy helyre a célhierarchiában lévő terjesztési pontok átrendelése.  

Az alábbi szakaszok segítséget nyújtanak az áttelepítés alatti központi tartalomtelepítés tervezéséhez:  

-   [Terjesztési pontok megosztása forrás- és célhierarchiák között](#About_Shared_DPs_in_Migration)  

-   [A Configuration Manager 2007 megosztott terjesztési pontok frissítését tervezi](#Planning_to_Upgrade_DPs)  

    -   [A terjesztési pont frissítési folyamata](#BKIMK_UpgradeProcess)  

    -   [A Configuration Manager 2007 másodlagos helyeihez tartozó frissítések megtervezése](#BKMK_UpgradeSS)  

-   [System Center Configuration Manager terjesztési pontok átrendelése megtervezése](#BKMK_ReassignDistPoint)  

    -   [Terjesztési pont újbóli hozzárendelésének folyamata](#BKMK_ReassignProcess)  

-   [Tartalom tulajdonjoga a tartalomáttelepítéskor](#About_Migrating_Content)  

##  <a name="About_Shared_DPs_in_Migration"></a> Terjesztési pontok megosztása forrás- és célhierarchiák között  
Áttelepítés közben megoszthatja a forráshierarchia terjesztési pontjait a célhierarchiával. A megosztott terjesztési pontokat arra használhatja, hogy egy forráshierarchiáról áttelepített tartalmat azonnal elérhetővé tegyen a célhierarchiában lévő ügyfelek számára anélkül, hogy újból létre kellene hoznia ezt a tartalmat, majd el kellene terjesztenie a célhierarchiában lévő terjesztési pontokra. Amikor a célhierarchiában lévő ügyfelek korábban megosztott terjesztési pontokra központilag telepített tartalmat kérnek, a megosztott terjesztési pontok az ügyfelek számára érvényes tartalomhelyként kínálhatók fel.  

 Nem érvényes tartalomhelyek a célhierarchiában lévő ügyfelek számára, amíg a forráshierarchiából történő áttelepítés aktív marad, akkor lehet frissítésekor vagy hozzárendelésének megváltoztatásakor a terjesztési pontot a célhierarchiában. A Configuration Manager 2007 megosztott terjesztési pontok frissítését, és a System Center 2012 Configuration Manager megosztott terjesztési pontok átrendelése. Megosztott terjesztési pont frissítésekor vagy átrendelésekor a rendszer eltávolítja a terjesztési pontot a forráshierarchiából, és az a célhierarchia terjesztési pontjává válik. Megosztott terjesztési pont frissítését vagy átrendelését követően a terjesztési pont tovább használható a célhierarchiában, miután a forráshierarchiáról történő áttelepítés befejeződött. Megosztott terjesztési pont frissítésével kapcsolatban bővebben lásd: [terv a frissítést a Configuration Manager 2007 megosztott terjesztési pontok](#Planning_to_Upgrade_DPs). További információ a megosztott terjesztési pont ismételt hozzárendelése, lásd: [ismételt hozzárendelése a System Center Configuration Manager terjesztési pontjai tervezi](#BKMK_ReassignDistPoint).  

 A forráshierarchiában lévő bármely forráshelyről megoszthat terjesztési pontokat. Egy forráshely terjesztési pontok megosztásakor alárendelt másodlagos helyének megosztottak, egyes megfelelő terjesztési pontok az elsődleges helyen és annak minden egyes elsődleges helyeken. Ahhoz, hogy a megosztott terjesztési pontként, a helyrendszer-kiszolgáló, a terjesztési pontot üzemeltető kell beállítása egy teljesen minősített tartománynév (FQDN). Egyetlen terjesztési ponton sem, amelyek be vannak állítva a NetBIOS-névvel figyelmen kívül hagyja.  

> [!TIP]  
>  A Configuration Manager 2007 nem szükséges a helyrendszer-kiszolgálók teljes tartománynév beállítása.  

A következő részek a megosztott terjesztési pontok tervezéséhez nyújtanak segítséget:  

-   A megosztani kívánt terjesztési pontoknak ki kell elégíteniük a megosztott terjesztési pontokra vonatkozó előfeltételeket. Ezekről az előfeltételekről bővebben lásd: [az áttelepítéshez szükséges konfigurációk](../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) a [előfeltételei a System Center Configuration Manager áttelepítési](../../core/migration/prerequisites-for-migration.md).  

-   A terjesztési pont megosztása művelet egy, az egész helyre kiterjedő beállítás, amely egy forráshelyen és annak közvetlen másodlagos gyermekhelyein lévő összes megfelelő terjesztési pontot megosztja. A terjesztési pontok megosztásának engedélyezésekor nem válaszhatók ki egyenként a megosztandó terjesztési pontok.  

-   A célhierarchiában lévő ügyfelek képesek a tartalomhely-információk fogadására olyan csomagok esetén, amelyeket a forráshierarchiából megosztott terjesztési pontokra küldtek. A terjesztési pontok a Configuration Manager 2007 forráshierarchiából Ez magában foglalja a fiókirodai terjesztési pontok, a kiszolgálómegosztásokon lévő terjesztési pontokat és normál terjesztési pontokat.  

    > [!WARNING]  
    >  Ha megváltoztatja a forráshierarchiát, az eredeti forráshierarchia megosztott terjesztési pontjai többé nem elérhetők, és nem kínálhatók fel tartalomhelyként a célhierarchiában lévő ügyfelek számára. Ha újrakonfigurálja az áttelepítést, hogy az eredeti forráshierarchiát használja, akkor a rendszer visszaállítja a korábban megosztott terjesztési pontokat mint érvényes tartalomhely-kiszolgálókat.  

-   Egy megosztott terjesztési ponton tárolt csomag áttelepítésekor a csomag verziójának azonosnak kell maradnia a forrás- és a célhierarchiában. Ha egy csomag verziója nem azonos a forrás- és a célhierarchiában, a célhierarchiában található ügyfelek nem tudják lekérni az adott tartalmat a megosztott terjesztési pontról. Amikor tehát frissít egy csomagot a forráshierarchiában, újból át kell telepítenie a csomagot, mielőtt a célhierarchiában lévő ügyfelek lekérhetnék a tartalmat egy megosztott terjesztési pontról.  

    > [!NOTE]  
    >  Amikor tárolt csomag adatait tekinti a megosztott terjesztési pont, a megjelenő csomagok száma **tárolt áttelepített csomagok** a forráshelyen **megosztott terjesztési pontok** lapon a következő adatgyűjtési ciklus addig nem frissül.  

-   Megtekintheti a megosztott terjesztési pontok és azok tulajdonságai a **forráshierarchia** csomópontjának a **felügyeleti** a Configuration Manager konzolt, amely a célhierarchiához kapcsolódó munkaterületén.  

-   Microsoft Application Virtualization (App-V) csomagok tárolására a Configuration Manager 2007-forráshierarchia megosztott terjesztési pont nem használható. Az App-V csomagokat a célhierarchiában lévő ügyfeleknek kell áttelepíteniük és felhasználásra átkonvertálniuk. App-V csomagok tárolására a System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchia megosztott terjesztési pont azonban használható a célhierarchiában lévő ügyfelek számára.  

-   Ha a Configuration Manager 2007-forráshierarchiából egy védett terjesztési pontot oszt meg, a célhierarchia létrehoz egy, az adott terjesztési pont védett hálózati helyeit tartalmazó határcsoportot. Ezt a határcsoportot a célhierarchiában nem módosítható. Azonban ha módosítja a Configuration Manager 2007 verziójú forráshierarchia a terjesztési ponthoz tartozó védett határ adatait, a változás megjelenik a célhierarchiában a következő adatgyűjtési ciklus befejezését követően.  

    > [!NOTE]  
    >  A System Center 2012 Configuration Manager és a System Center Configuration Manager helyek védett terjesztési pont helyett az előnyben részesített terjesztési pont fogalmat használják. Ez a feltétel csak a Configuration Manager 2007-Forráshelyek megosztott terjesztési pontokra vonatkozik.  

A megfelelő terjesztési pontok ne legyenek láthatók a Configuration Manager konzolon, mielőtt megosztja a terjesztési pontokat egy forráshelyről. A terjesztési pontok megosztását követően a listában csak a sikeresen megosztott terjesztési pontok jelennek meg.  

A terjesztési pontok megosztását követően bármely megosztott terjesztési pont konfigurációját módosíthatja a forráshierarchiában. Egy terjesztési pont konfigurációjában elvégzett módosítások a következő adatgyűjtési ciklust követően jelennek meg a célhierarchiában. A terjesztési pontok, amelyeket azért frissített, hogy megosztásra megfelelőek legyenek, automatikusan megosztásra kerülnek, míg a továbbiakban nem megfelelő terjesztési pontok megosztása megszűnik. Például lehetséges, hogy nem beállítása egy intranetes teljes Tartománynevet, és eredetileg nem osztott a célhierarchia terjesztési pontot. Miután beállította a terjesztési pont teljes Tartománynevét, a következő adatgyűjtési ciklus felismeri ezt a konfigurációt, és a terjesztési pont majd megosztott a célhierarchiával.  

##  <a name="Planning_to_Upgrade_DPs"></a>A Configuration Manager 2007 megosztott terjesztési pontok frissítését tervezi  
Ha telepít át egy Configuration Manager 2007 verziójú forráshierarchia, frissítheti egy megosztott terjesztési pont abba, hogy egy System Center Configuration Manager terjesztési pont. Frissítheti az elsődleges és másodlagos helyeken lévő terjesztési pontokra. A frissítési folyamat eltávolítja a terjesztési pontot a Configuration Manager 2007-hierarchiából, és a rendeltetési hierarchiában egy helyrendszer-kiszolgáló segítségével. Ez a folyamat átmásolja a terjesztési pont számítógépén lévő új helyre a terjesztési ponton meglévő tartalmat. A frissítési folyamat ezután módosítja a tartalom másolatát, és létrehozza a tartalom központi telepítéséhez használható, egypéldányos tárolót a célhierarchiában. Ezért amikor egy terjesztési pontot frissít, nincs a Configuration Manager 2007 terjesztési ponton tárolt áttelepített tartalmak újraterjesztésére.  

A Configuration Manager konvertálja a tartalmat az Egypéldányos tárolóba, a Configuration Manager törli az eredeti forrástartalmat a terjesztési pont számítógépén szabadítson fel megfelelő mennyiségű lemezterületet. A Configuration Manager nem használja az eredeti forrástartalom-helyet.  

Nem minden megoszthatja a Configuration Manager 2007 terjesztési pontok frissítése a System Center Configuration Manager jogosultak. Jogosult a frissítésre, a Configuration Manager 2007 terjesztési pont kell felelnie a frissítéshez. Ezek a feltételek közé tartozik a helyrendszer-kiszolgáló a terjesztési pont telepítését és milyen típusú Configuration Manager 2007 terjesztési pont, amely telepítve van. Egy elsődleges hely helykiszolgálójának számítógépére telepített terjesztési pontok közül például nem frissítheti bármelyik típusút, de például frissítheti egy másodlagos hely helykiszolgálójának számítógépére telepített normál terjesztési pontot.  

> [!NOTE]  
>  Frissítheti csak azokat a Configuration Manager 2007 megosztott terjesztési pontok, amelyek egy számítógépen, amely egy operációs rendszert futtat, amely a célhierarchiában lévő terjesztési pontok esetén támogatott. Például azonban a Configuration Manager 2007 terjesztési pont, amely a Windows Vista rendszerű számítógép, nem a megosztott terjesztési pont frissítése, mert az operációs rendszer nem támogatott a System Center Configuration Manager által a használatát terjesztési pontként.  

A következő táblázat a támogatott helyek frissítheti a Configuration Manager 2007 terjesztési pontok egyes típusai.  

|Terjesztési pont típusa|Terjesztési pont a helykiszolgálótól különböző helyrendszer-számítógépen|Terjesztési pont a helykiszolgálótól különböző, és más helyrendszerszerepköröket is kiszolgáló helyrendszer-számítógépen|Terjesztési pont másodlagos helykiszolgálón|  
|--------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------|  
|Szabványos terjesztési pont|Igen|Nem|Igen|  
|Terjesztési pont kiszolgálómegosztásokon<sup>1</sup>|Igen|Nem|Nem|  
|Fiókirodai terjesztési pont|Igen|Nem|Nem|  

 <sup>1</sup> system Center Configuration Manager nem támogatja a kiszolgálómegosztásokat helyrendszerek, de támogatja a kiszolgálómegosztáson lévő Configuration Manager 2007 terjesztési pont frissítését. A kiszolgálómegosztáson lévő Configuration Manager 2007 terjesztési pont frissítésekor a terjesztési pont típusát rendszer automatikusan kiszolgálóvá konvertálja át, és ki kell választania a meghajtó a terjesztési pont számítógépén, hogy fogja tárolni az Egypéldányos tartalomtárat.  

> [!WARNING]  
>  Fiókirodai terjesztési pont frissítése előtt távolítsa el a Configuration Manager 2007-ügyfélszoftvert. Amikor olyan fiókirodai terjesztési pontot, amelyen a Configuration Manager 2007 ügyfélszoftverrel frissít, a számítógép korábban központilag telepített tartalom eltávolítása a számítógépről, és a terjesztési pont frissítése pedig sikertelen lesz.  

A Configuration Manager konzolján a frissítésre jogosult terjesztési pontok azonosításához a **forráshierarchia** csomópont, válasszon ki egy forráshelyet, majd válassza ki a **megosztott terjesztési pontok** lapon. A jogosult terjesztési pontok esetén **Igen** jelenik meg a **Jogosult a frissítésre** oszlopban.  

A Configuration Manager 2007 másodlagos helykiszolgálón telepített terjesztési pont frissítése esetén a másodlagos hely eltávolítása a forráshierarchiából. Habár ezt a műveletet a másodlagos hely frissítésének hívják, csak a terjesztésipont-helyrendszerszerepkörre vonatkozik. Az eredménye az, hogy a másodlagos hely nem lesz frissítve, hanem el lesz távolítva. A terjesztési pont a célhierarchiából, azon a számítógépen, a másodlagos helykiszolgáló rendszer mindeddig. Ha egy másodlagos helyen lévő terjesztési pont frissítését tervezi, tekintse meg a [Configuration Manager 2007 másodlagos helyeihez tartozó frissítések megtervezése](#BKMK_UpgradeSS) ebben a témakörben.  

###  <a name="BKIMK_UpgradeProcess"></a> A terjesztési pont frissítési folyamata  
A Configuration Manager konzol segítségével frissítse a Configuration Manager 2007 terjesztési pontokat, amelyeket megosztott a célhierarchiával. Amikor megosztott terjesztési pontot frissít, a rendszer eltávolítja a terjesztési pontot a Configuration Manager 2007 helyről. Ezután telepíti a rendszer a célhierarchiában megadott elsődleges vagy másodlagos helyhez kapcsolt terjesztési pontként. A frissítési folyamat másolatot hoz létre a terjesztési ponton tárolt áttelepített tartalomról, majd ezt a másolatot konvertálja az egypéldányos tartalomtárhoz. Amikor a Configuration Manager csomag konvertálja az Egypéldányos tartalomtárhoz konvertál, törli a csomag a terjesztési pont számítógépén lévő SMSPKG-megosztásról kivéve ha a csomag egy vagy több olyan, amelyek **program futtatása a terjesztési pontról**.  

A terjesztési pont frissítéséhez, a Configuration Manager használ a **forráshely-elérési fiókok** , amely be van állítva az adatok gyűjtését a forráshely SMS-szolgáltató. Bár ez a fiók csak igényel **olvasási** helyobjektumok adatokat gyűjtsenek a forráshelyről történő engedéllyel, akkor is rendelkeznie kell **törlése** és **módosítás** engedéllyel a **hely** osztályra, hogy sikeresen eltávolíthassa a terjesztési pontot a Configuration Manager 2007 helyről a frissítés során.  

> [!NOTE]  
>  A Configuration Manager egyszerre alakíthatja az Egypéldányos tároló csak egy terjesztési ponton lévő tartalmat. Több terjesztésipont-frissítés beállításakor a terjesztési pontok frissítése várólistáján szereplő, és egyenként feldolgozása.  

Megosztott terjesztési pont frissítése előtt győződjön meg arról, hogy a terjesztési pontra központilag telepített minden tartalom áttelepítésére sor került. A terjesztési pont frissítése előtt nem áttelepített tartalmak nem lesznek elérhetők a célhierarchiában a frissítést követően. Terjesztési pont frissítésekor az áttelepített csomagokban lévő tartalom olyan formátumra lesz konvertálva, amely kompatibilis a célhierarchia egypéldányos tárolójával.  

A Configuration Manager konzolon a terjesztési pont frissítéséhez a Configuration Manager 2007 helyrendszer-kiszolgáló a következő feltételeknek kell megfelelniük:  

-   A terjesztési pont konfigurációjának és helyének frissítésre jogosultnak kell lenniük.  

-   A terjesztési pont számítógépén elegendő lemezterület van a tartalom konvertálásához a Configuration Manager 2007 tartalomtárolási formátumáról az Egypéldányos tároló formátumára kell rendelkeznie. A konvertáláshoz a terjesztési ponton tárolt legnagyobb csomag méretével megegyező szabad lemezterület szükséges.  

-   A terjesztési pont számítógépének olyan operációsrendszer-verziót kell futtatnia, amelynek terjesztési pontként való használatát a célhierarchia támogatja.  

    > [!NOTE]  
    >  Amikor a Configuration Manager ellenőrzi a terjesztési pont frissítésre való jogosultságát, a terjesztési pont számítógépen operációs rendszer verzióját nem ellenőrzi.  

A terjesztési pont frissítéséhez a a **felügyeleti** munkaterületet, bontsa ki a **áttelepítés**, bontsa ki a **forráshierarchia** csomópont, és válassza ki a helyet, amely a terjesztési pontot, hogy szeretné-e frissíteni. Ezután a részleteket megjelenítő ablaktábla **Megosztott terjesztési pontok** lapján válassza ki a frissíteni kívánt terjesztési pontot.  

Azt, hogy a terjesztési pont készen áll-e a frissítésre, a **Jogosult az ismételt hozzárendelésre** oszlopban lévő állapotból állapíthatja meg.  Ezt követően a Configuration Manager konzol menüszalagján a a **terjesztési pontok** lap a **terjesztési pont** csoportban válassza **ismételt hozzárendelése**. Ekkor megnyílik egy varázsló, amellyel a frissítés a terjesztési pont.  

Megosztott terjesztési pont frissítésekor a terjesztési pontot a célhierarchia egy kiválasztott elsődleges vagy másodlagos helyéhez kell rendelni. A terjesztési pont frissítését követően a terjesztési pont kezeléséhez jelenítik meg terjesztési pontot a célhierarchiában, mint bármely más terjesztési pontra.  

Figyelheti a terjesztési pont frissítésének előrehaladása a Configuration Manager konzol előrehaladását kiválasztásával a **terjesztési pont áttelepítése** csomópont alatt a **áttelepítési** csomópontjának a **felügyeleti** munkaterületen. Az információk a célhierarchia központi adminisztrációs helykiszolgálójának **Migmctrl.log** naplófájljában vagy a frissített terjesztési pontot kezelő célhierarchia helykiszolgálójának **distmgr.log** naplófájljában is megtekinthetők.  

> [!NOTE]  
>  A terjesztési pont célhierarchiába történő frissítésekor a rendszer eltávolítja a terjesztési pont helyrendszer-szerepkör a Configuration Manager 2007-forráshelyről. A terjesztési pontnak küldött csomagok azonban nem frissülnek a Configuration Manager 2007 hierarchia. A Configuration Manager 2007 konzolon, a terjesztési pontnak elküldött csomagok továbbra is a helyrendszer számítógépét jelenítik meg terjesztési pontok és a lista egy **típus** a **ismeretlen**. A csomagot a Configuration Manager 2007 vezethet a Distribution Manager a distmgr.log naplófájlban az adott hely hibákat jelez, amikor a hely próbálja az ismeretlen helyrendszeren lévő csomagot.  

Ha úgy dönt, hogy nem frissít megosztott terjesztési pontot, továbbra is telepíthet a terjesztési pontok egy korábbi Configuration Manager 2007 terjesztési pont a célhierarchiából. Az új terjesztési pont telepítése előtt el kell távolítania minden Configuration Manager 2007 helyrendszer-szerepkört a terjesztési pont számítógépéről. Ez magában foglalja a Configuration Manager 2007 helyen, ha a helykiszolgáló számítógépén. A Configuration Manager 2007 terjesztési pont eltávolításakor volt a terjesztési pontra központilag telepített tartalmat, nem törlődik a számítógépről.  

###  <a name="BKMK_UpgradeSS"></a>A Configuration Manager 2007 másodlagos helyeihez tartozó frissítések megtervezése  
 Ha áttelepítés használatával frissíti a Configuration Manager 2007 másodlagos helykiszolgálón tárolt megosztott terjesztési pont, a Configuration Manager frissíti a terjesztési pont helyrendszer-szerepkör a célhierarchiában lévő terjesztési pontként. Azt is eltávolítja a másodlagos helyet a forráshierarchiából. A System Center Configuration Manager terjesztési pont, de a másodlagos hely nem jön létre.  

 A terjesztési ponton, a helykiszolgáló számítógépen jogosult a frissítésre a Configuration Manager és az egyes a helyrendszer-szerepkörök adott számítógépen a másodlagos hely eltávolítása képesnek kell lennie. A Configuration Manager 2007 kiszolgálómegosztáson lévő megosztott terjesztési pont általában jogosultak a frissítésre. Ha azonban a másodlagos helykiszolgálón kiszolgálómegosztás található, a másodlagos hely és az adott számítógépen lévő megosztott terjesztési pontok nem jogosultak a frissítésre. Ennek oka az, a kiszolgálómegosztást egy olyan további helyénél Rendszerobjektum a folyamat megpróbálja eltávolítani a másodlagos helyet, és ezt nem képes eltávolítani ezt az objektumot a rendszer. Ilyen esetben engedélyezhet normál terjesztési pontot a másodlagos helykiszolgálón, majd a tartalmat újraterjesztheti erre a normál terjesztési pontra. Ez a folyamat nem használja a hálózati sávszélesség, és befejeződése után távolítsa el a kiszolgálómegosztáson lévő terjesztési pont, távolítsa el a kiszolgálómegosztást, és frissítse a terjesztési pont és a másodlagos hely.  

 Megosztott terjesztési pont frissítése előtt tekintse át a terjesztési pont konfigurációját a Configuration Manager 2007 egy másodlagos helyen, amelyek továbbra is használni kívánt Configuration Manager 2007 terjesztési pont frissítése elkerülése érdekében. Bevált gyakorlat, Ez azért, mert miután másodlagos helykiszolgálón lévő megosztott terjesztési pont frissítéséhez a helyrendszer-kiszolgáló törlődik a Configuration Manager 2007 hierarchia, és már nem érhető el, hogy a hierarchiában való használatra. A másodlagos hely eltávolításakor a rajta lévő összes terjesztési pont árván marad. Ez azt jelenti, hogy váljanak felügyelet nélküli ügyfelekké, a Configuration Manager 2007 és a rendszer már nem megosztott frissítésre sem jogosultak.  

> [!WARNING]  
>  Megosztott terjesztési pont megtekintése a Configuration Manager konzolon, nincs látható jele annak, hogy egy megosztott terjesztési pont egy távoli helyrendszer-kiszolgálón vagy a másodlagos helykiszolgálón.  

 Ha egy másodlagos helyen található elsősorban az adott távoli helyre tartalom központi telepítésére használt távoli hálózati helyre, másodlagos helyeket érdemes frissíteni a megosztott terjesztési ponttal. System Center Configuration Manager terjesztési pontra történő tartalomterjesztés állíthat be a sávszélesség-vezérlést, mert, gyakran egy másodlagos hely terjesztési ponttá frissítsen, beállíthatja a terjesztési pont a sávszélesség-vezérlést, elkerülheti a másodlagos helyet telepítsen az adott hálózati helyre a célhierarchiában.  

 A másodlagos helykiszolgálón lévő megosztott terjesztési pont frissítése ugyanúgy történik, mint bármely más megosztott terjesztési pont frissítése. Tartalom másolása és a célhierarchia által használt egypéldányos tárolóhoz konvertálni. Azonban, hogy a másodlagos helykiszolgálón lévő megosztott terjesztési pont frissítésekor a frissítési folyamat is eltávolítja az a felügyeleti pontot (ha van ilyen) és majd eltávolítja a másodlagos helyet a kiszolgálóról. Az eredménye, hogy a másodlagos helyet eltávolította-e a Configuration Manager 2007-hierarchiából. A másodlagos hely eltávolítására, a Configuration Manager használ a fiókot, amely be van állítva az adatok gyűjtését a forráshelyről.  

 A frissítés során késleltetés van között, amikor a Configuration Manager 2007 másodlagos hely eltávolítása során a és a célhierarchia a terjesztési pont telepítésének megkezdése előtt. A-adatgyűjtési ciklus határozza meg, hogy ez a késleltetés akár négy órát. A késleltetés arra szolgál, hogy a másodlagos hely eltávolításához, az új terjesztési pont telepítésének megkezdése előtt időt adjon.  

 Megosztott terjesztési pont frissítésével kapcsolatban bővebben lásd: [terv a frissítést a Configuration Manager 2007 megosztott terjesztési pontok](#Planning_to_Upgrade_DPs).  

##  <a name="BKMK_ReassignDistPoint"></a>System Center Configuration Manager terjesztési pontok átrendelése megtervezése  
 Amikor telepít át a System Center 2012 Configuration Manager támogatott verziójából, ugyanolyan verziójú hierarchiába, hozzárendelheti egy megosztott terjesztési pontokat a forráshierarchiából a célhierarchia egy helyéhez. Ez olyan, mintha a célhierarchiában lévő terjesztési ponttá válik a Configuration Manager 2007 terjesztési pont frissítéséhez, amelynek. Elsődleges és másodlagos helyek terjesztési pontokat újból hozzárendelheti. A terjesztési pont ismételt hozzárendelése a művelet eltávolítja a terjesztési pontot a forráshierarchiából, és lehetővé teszi a számítógép és a terjesztési pont helyrendszer-kiszolgáló az a célhierarchiában kiválasztott helyen.  

 Terjesztési pont újbóli hozzárendelésekor nincs szükség a forráshely terjesztési pontján tárolt áttelepített tartalmak újraterjesztésére. Emellett a Configuration Manager 2007 terjesztési pont frissítésével ellentétben a terjesztési pont újbóli hozzárendelése nem igényel további lemezterületet a terjesztési pont számítógépén. Ennek az az oka kezdve a System Center 2012 Configuration Manager, a terjesztési pontok az Egypéldányos tároló formátumát használják a tartalmakhoz. A terjesztési pont számítógépén lévő tartalmat nem kell konvertálni a terjesztési pont a hierarchiák közötti újbóli hozzárendelés során.  

 A System Center 2012 Configuration Manager terjesztési pont jogosult legyen az újbóli hozzárendelésre a következő feltételeknek kell megfelelnie:  

-   A megosztott terjesztési pont telepítési helye (számítógépe) nem lehet a helykiszolgáló.  

-   A megosztott terjesztési pont nem lehet közösen elhelyezve egyéb helyrendszerszerepkörökkel.  

A Configuration Manager konzol, az újbóli hozzárendelésre jogosult terjesztési pontok azonosításához a **forráshierarchia** csomópont, válasszon ki egy forráshelyet, majd válassza ki a **megosztott terjesztési pontok** fülre. Jogosult terjesztési pontoknál **Igen** a a **jogosult az ismételt hozzárendelésre** oszlop (az oszlop neve **jogosult a frissítésre** előtt a System Center 2012 R2 Configuration Manager).  

###  <a name="BKMK_ReassignProcess"></a> Terjesztési pont újbóli hozzárendelésének folyamata  
 A Configuration Manager konzol segítségével, amelyeket aktív forráshierarchiából megosztott terjesztési pontok átrendelése. Ha egy megosztott terjesztési pont ismételt hozzárendelése, a terjesztési pont el lesz távolítva a forráshelyről és települ a célhierarchiában megadott elsődleges vagy másodlagos helyhez kapcsolt terjesztési pontként.  

 A terjesztési pont ismételt hozzárendelése, a célhierarchia használja a forráshely-elérési fiókja az adatok gyűjtését a forráshely SMS-szolgáltató be van állítva. További információ a szükséges engedélyekkel, és a további előfeltételekről: [előfeltételei a System Center Configuration Manager áttelepítési](../../core/migration/prerequisites-for-migration.md).  

## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Egyszerre több megosztott terjesztési pont áttelepítése
1610 verziójával kezdve használhatja **ismételt hozzárendelése terjesztési pont** kell rendelkeznie a Configuration Manager-folyamat az újbóli hozzárendelésre, legfeljebb 50 párhuzamosan megosztott terjesztési pontok egy időben. Ez magában foglalja a támogatott forráshierarchiában futtató megosztott terjesztési pontok:  
- Configuration Manager 2007
- System Center 2012 Configuration Manager
- System Center 2012 R2 Configuration Manager
- A System Center Configuration Manager (aktuális ág)

Amikor a terjesztési pontok átrendelése egyes terjesztési pontokon kell frissítése vagy újbóli hozzárendelés kell jogosultak. A művelet és az érintett folyamatot nevét (a frissítése vagy ismételt hozzárendelése) attól függ, melyik verziója a Configuration Manager a forráshely fusson. Mindkét műveletet állnak ugyanaz: a terjesztési pont hozzá van rendelve, a benne lévő tartalom helyen aktuális ág helyek egyikére.

Verzió 1610, mielőtt a Configuration Manager sikerült feldolgozni a csak egy terjesztési pont egyszerre. Most már hozzárendelheti annyi terjesztési pontokat, ahányat csak szeretne, a következő kikötésekkel:  
- Bár nem kell társítani, ha rendelkezik egynél több sorba multiselect terjesztési pontok, a Configuration Manager fog dolgozza fel őket párhuzamos helyett egy, a következő elindítása előtt befejezésre vár.  
- Alapértelmezés szerint legfeljebb 50 terjesztési pontok feldolgozása párhuzamosan történik egyszerre. Miután a az első terjesztési pont újbóli hozzárendelése befejeződött, a Configuration Manager elkezdi a 51. feldolgozásához, és így tovább.  
- A Configuration Manager SDK használatakor módosíthatja **SharedDPImportThreadLimit** úgy, hogy a máshoz hozzárendelt terjesztési pontok, amely a Configuration Manager képes a párhuzamosan.


##  <a name="About_Migrating_Content"></a>Rendelje hozzá a tartalom tulajdonjoga a tartalomáttelepítéskor  
 Ha központi telepítésekhez telepít át tartalmakat, a tartalomobjektumot hozzá kell rendelnie a célhierarchia egy helyéhez. A hely ezután a tartalom tulajdonosa lesz a célhierarchiában. Bár a célhierarchia legfelső szintű helyen a helyet, amely a tartalom metaadatainak áttelepíti, akkor a tartalom eredeti forrásfájljaihoz a hálózaton keresztül használja a hozzárendelt hely.  

 A tartalmak áttelepítésekor használt sávszélesség minimálisra csökkentése érdekében érdemes a tartalom tulajdonjogát a célhierarchia olyan helyének átadni, amely a hálózaton közel van a tartalom helyéhez a forráshierarchiában. Mivel a célhierarchiában lévő tartalommal kapcsolatos információk megosztása globális jellegű, azok minden helyen elérhetők lesznek.  

 Habár a tartalommal kapcsolatos információk megosztása összes adatbázis-replikáció használatával, bármilyen tartalmat, amelyet egy elsődleges helyhez rendelt, és ezután telepíti a terjesztési pontok más elsődleges helyeken lévő átvitelek fájl alapú replikációként. Az átvitel során az adatok a központi adminisztrációs helyen keresztül jutnak el a további elsődleges helyhez. Alacsony sávszélességű hálózatokon keresztül adatátvitelek csökkentik központosítja azokat a csomagokat, amelyeket terjeszteni több elsődleges helyhez áttelepítés előtt vagy közben rendel egy helyet a tartalom tulajdonosaként.

