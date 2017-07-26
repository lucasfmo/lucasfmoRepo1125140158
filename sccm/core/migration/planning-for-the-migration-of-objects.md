---
title: "Objektumok áttelepítése |} Microsoft Docs"
description: "Útmutató: az objektumok a System Center Configuration Manager környezetben hierarchiák közötti áttelepítésének tervezésében."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45931f60273f3130cca36320770126a36dcc3d1e
ms.openlocfilehash: 9870ffa6ae5f80db823bfc74a7cc2e67fc8cf21d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-migration-of-configuration-manager-objects-to-system-center-configuration-manager"></a>A Configuration Manager-objektumok a System Center Configuration Manager az áttelepítés tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerrel, telepítheti át, amely egy forráshelyen található különféle szolgáltatásaihoz társított különböző objektumok közül. A következő szakaszok segítséget nyújtanak az objektumok hierarchiák közötti áttelepítésének tervezésében.  

-   [Szoftverfrissítések áttelepítésének tervezése](#Plan_migrate_Software_updates)  

-   [Tartalom áttelepítésének tervezése](#Plan_Migrate_content)  

-   [Gyűjtemények áttelepítésének tervezése](#BKMK_MigrateCollections)  

-   [Operációs rendszerek központi telepítései áttelepítésének tervezése](#Plan_migrate_OSD)  

-   [A szükséges konfiguráció kezelése áttelepítésének tervezése](#Plan_Migrate_Compliance_settings)  

-   [Határok áttelepítésének tervezése](#Plan_migrate_Boundaries)  

-   [Jelentések áttelepítésének tervezése](#Plan_Migrate_reports)  

-   [Szervezeti és keresési mappák áttelepítésének megtervezése](#Plan_Migrate_Org_Folders)  

-   [Tervezze meg az Eszközintelligencia egyéni beállításainak áttelepítése](#Plan_Migrate_AI)  

-   [Szoftverhasználat-mérési szabályok testreszabások áttelepítésének megtervezése](#Plan_Migrate_SWM_Rules)  

##  <a name="Plan_migrate_Software_updates"></a>Szoftverfrissítések áttelepítésének tervezése  
 A szoftverfrissítési objektumok, például a szoftverfrissítési csomagokat és a szoftver a frissítés központi telepítések áttelepíthetők.  

 A szoftverfrissítési objektumok sikeres áttelepítéséhez először be kell állítania a célhierarchiát a forráshierarchia környezetének megfelelő beállításokkal. Ehhez a következő műveletek végrehajtása szükséges:  

-   Egy aktív szoftverfrissítési pontot a célhierarchiában lévő telepítése  

-   A forráshierarchia beállításainak termékek és nyelvek katalógusának beállítása  

-   A szoftverfrissítési pontot a célhierarchiában a Windows Server Update Services (WSUS) szinkronizálása  

Szoftverfrissítések áttelepítésekor vegye figyelembe a következőket:  

-   A szoftverfrissítési objektumok áttelepítése sikertelen lehet, ha a forráshierarchia beállításainak a célhierarchiában nem szinkronizálta információkat.  

    > [!WARNING]  
    >  A Configuration Manager nem támogatja a forrás és cél hierarchia között szinkronizálja az adatokat a WSUSutil eszköz használatát.  

-   Nem telepíthet át olyan egyéni frissítéseket, amelyek a System Center frissítés-közzétevő használatával lettek közzétéve. Ebben az esetben az egyéni frissítéseket újból közzé kell tenni a célhierarchia számára.  

Áttelepítésekor a Configuration Manager 2007 forráshierarchia, az áttelepítési folyamat néhány szoftverfrissítési objektumokat a célhierarchia által használt formátumúra módosítja a. Használja az alábbi táblázat segítségével megtervezheti a Configuration Manager 2007 a szoftverfrissítési objektumok áttelepítése.  

|A Configuration Manager 2007 objektum|Objektum neve az áttelepítés után|  
|-----------------------------------|---------------------------------|  
|Szoftverfrissítési listák|A szoftverfrissítési listákat szoftverfrissítési csoportokká alakítja át a rendszer.|  
|Szoftverfrissítések telepítése|A szoftverfrissítési telepítéseket központi telepítésekké és frissítési csoportokká alakítja át a rendszer.<br /><br /> A központi telepítés a Configuration Manager 2007 az áttelepítés után engedélyeznie kell azt a célhierarchiában csak ezután telepítheti azt.|  
|Szoftverfrissítési csomagok|A szoftverfrissítési csomagok ugyanilyen csomagok maradnak.|  
|Szoftverfrissítési sablonok|A szoftverfrissítési sablonok ugyanilyen sablonok maradnak.<br /><br /> A **időtartam** érték a Configuration Manager 2007 központi telepítési sablonokból nem lesz áttelepítve.|  

Ha a System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiából telepít át objektumokat, a szoftverfrissítési objektumok nem módosulnak.  

##  <a name="Plan_Migrate_content"></a>Tartalom áttelepítésének tervezése  
 Támogatott forráshierarchiából tartalmat telepíthet át célhierarchiájába. A Configuration Manager 2007 verziójú forráshierarchia Ez a tartalom magában foglalja szoftverterjesztési csomagokat és programokat, valamint virtuális alkalmazásokat, például Microsoft Application Virtualization (App-V). System Center 2012 Configuration Manager és a System Center Configuration Manager forráshierarchiáknál Ez a tartalom alkalmazásokat és App-V virtuális alkalmazások magában foglalja. Hierarchiák között tartalmat telepít át, a tömörített forrásfájlok telepíti át a célhierarchiába.  

### <a name="packages-and-programs"></a>Csomagok és programok  
 Amikor csomagokat és programokat telepít át, ezek változatlanok maradnak a művelet során. Azonban az áttelepítés előtt azokat be kell állítania minden csomag egy univerzális elnevezési konvenció (UNC) szerinti elérési utat a forrásfájl helyén használandó. A csomagok és programok áttelepítése konfigurálásának részeként helyet kell hozzárendelnie a célhierarchiában az adott tartalom felügyeletéhez. A tartalom nem települ át a hozzárendelt helyről, de az áttelepítés után a hozzárendelt hely fér hozzá a forrásfájl eredeti helyéhez az UNC leképezés használatával.  

 Miután egy csomagot és programot telepít át a célhierarchiába, és amíg a forráshierarchiából történő áttelepítés aktív marad, akkor is használhatja a tartalom az ügyfelek számára, hogy a hierarchiában egy megosztott terjesztési pont használatával. Megosztott terjesztési pont használatához a tartalomnak hozzáférhetőnek kell maradnia a forráshely terjesztési pontján. Megosztott terjesztési pontokkal kapcsolatban bővebben lásd: [megosztja a terjesztési pontokat a forrás- és Célhierarchiák között](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) a [tervezze meg a tartalom központi telepítési stratégiájának a System Center Configuration Managerben](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

 A tartalom, amely át lett telepítve, ha a forráshierarchia vagy a célhierarchiába, az ügyfelek megváltozik a verzió már nem férhetnek hozzá a tartalomhoz a célhierarchiában lévő megosztott terjesztési pontról. Ebben az esetben újból át kell a csomag forrás- és a célhierarchia közötti megegyező verziójának visszaállítani a tartalmat. Ez az információ szinkronizálja, az adatgyűjtési ciklus során.  

> [!TIP]  
>  Minden áttelepített csomag esetében a csomagot a célhierarchiában frissítse. Ezzel elkerülheti a csomag célhierarchiában lévő terjesztési pontokra történő telepítésével kapcsolatos problémákat. Azonban a csomagot a célhierarchiában, az ügyfelek a terjesztési pont frissítésekor, az adott hierarchiában már nem fogja tudni, hogy a csomag beszerzése egy megosztott terjesztési pont. Frissíti a csomagot a rendeltetési hierarchiában, a Configuration Manager konzolon nyissa meg a szoftverkönyvtár, kattintson a jobb gombbal a csomagra, majd válassza ki **terjesztési pontok frissítése**. Minden áttelepített csomag a művelet végrehajtására.  

> [!TIP]  
>  Microsoft System Center Configuration Manager Csomagkonverzió-kezelője segítségével a csomagok és programok átalakítása System Center Configuration Manager alkalmazások. A csomagkonverzió-kezelőt a [Microsoft letöltőközpont](http://go.microsoft.com/fwlink/p/?LinkId=212950) webhelyről töltheti le. További információ: [A Configuration Manager csomagkonverzió-kezelője](http://go.microsoft.com/fwlink/p/?LinkId=247245).  

### <a name="virtual-applications"></a>Virtuális alkalmazások  
App-V csomagokat telepít át egy támogatott Configuration Manager 2007 helyre, ha az áttelepítési folyamat alkalmazásokká alakítja át ezeket a célhierarchiában. Emellett az App-V csomaghoz létező hirdetmények alapján, a következő központi telepítési típusok jönnek létre a célhierarchiában:  

-   Ha nincsenek hirdetmények, egy központi telepítési típust hoz létre, amely az alapértelmezett központi telepítési típus beállításait használja.  

-   Ha egy hirdetmény létezik, egy központi telepítési típust, amely ugyanazokat a beállításokat használja a Configuration Manager 2007 hirdetménye jön létre.  

-   Ha több hirdetmény létezik, a központi telepítési típus létrejön az egyes Configuration Manager 2007 hirdetmény által az adott hirdetmény beállításait használják.  

> [!IMPORTANT]  
>  Ha egy korábban már áttelepített Configuration Manager 2007 App-V csomagot telepít át, az áttelepítés sikertelen lesz, mivel a virtuális alkalmazási csomagok nem támogatják az áttelepítés felülírása funkciót. Ebben az esetben törölnie kell az áttelepített virtuális alkalmazási csomagot a célhierarchiából, majd új áttelepítési feladatot kell létrehoznia a virtuális alkalmazás áttelepítéséhez.  

> [!NOTE]  
>  Az App-V-csomag az áttelepítés után a tartalom frissítése varázsló segítségével módosíthatja a forrás elérési útja App-V központi telepítési típusok. További információ a központi telepítési típus tartalmát, tekintse meg a központi telepítési típusok kezelése [System Center Configuration Manager-alkalmazásokkal kapcsolatos felügyeleti feladatok](../../apps/deploy-use/management-tasks-applications.md).  

A System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchia áttelepítésekor áttelepítheti az App-V virtuális környezet App-V központi telepítési típusok és alkalmazások mellett objektumokat. App-V környezetekről bővebben lásd: [telepítése App-V virtuális alkalmazások a System Center Configuration Managerrel](../../apps/get-started/deploying-app-v-virtual-applications.md).  

### <a name="advertisements"></a>Hirdetések  
Hirdetményeket telepíthet át egy Configuration Manager 2007 támogatott forráshelyről a célhierarchiába gyűjtemény alapú áttelepítés használatával. Ha ügyfélgépet frissít, ez megőrzi a korábban futtatott hirdetmények előzményeit, így az ügyfélgép nem fogja újból futtatni az áttelepített hirdetményeket.  

> [!NOTE]  
>  Virtuális csomagokhoz tartozó hirdetményeket nem telepíthet át. Ez kivételt képez a hirdetmények áttelepítésénél.  

### <a name="applications"></a>Alkalmazások  
 Egy támogatott System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiájában alkalmazások áttelepíthetők a célhierarchiába. Ha a forráshierarchiából ügyfélgép újbóli hozzárendelését hajtja végre a célhierarchiába, az ügyfél megőrzi a korábban telepített alkalmazások előzményadatait, így nem fogja újból futtatni az áttelepített alkalmazásokat.  

##  <a name="BKMK_MigrateCollections"></a>Gyűjtemények áttelepítésének tervezése  
 A támogatott System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchiából gyűjteményekhez tartozó feltételeket telepíthet át. Ehhez használja az objektum alapú áttelepítési feladatot. Gyűjtemény áttelepítésekor a gyűjteményhez tartozó szabályokat telepíti át, és nem a gyűjtemény tagjaira vonatkozó adatokat vagy a gyűjtemény tagjaival kapcsolatos adatokat vagy objektumokat.  

 Gyűjtemény objektum áttelepítése nem támogatott, ha a Configuration Manager 2007-forráshierarchiából végez áttelepítést.  

##  <a name="Plan_migrate_OSD"></a>Operációs rendszerek központi telepítései áttelepítésének tervezése  
Támogatott forráshierarchiából az operációs rendszerek következő központi telepítési objektumait telepítheti át:  

-   Operációs rendszerek lemezképei és csomagjai. A forrás elérési útja a rendszerindító lemezképek a Windows felügyeleti telepítési csomag (Windows AIK) célhelyen lévő alapértelmezett lemezképhelyére frissül. Operációs rendszerek lemezképeinek és csomagjainak áttelepítésére a következő követelmények és korlátozások érvényesek:  

    -   A lemezképfájlok sikeres áttelepítéséhez, rendelkeznie kell a célhierarchia legfelső szintű helyen az SMS Provider kiszolgáló számítógépfiókjának **olvasási** és **írási** engedéllyel a forráshely a Windows AIK helyéhez tartozó lemezkép forrásfájljaihoz.  

    -   Operációs rendszer telepítési csomagjának áttelepítésekor győződjön meg arról, hogy a csomagot a a forráshelyen a WIM-fájl a mappában, és nem magára a WIM-fájl beállításait. Ha a telepítési csomag a WIM-fájlra mutat, a telepítési csomag áttelepítése sikertelen lesz.  

    -   A rendszerindító lemezkép csomagjának áttelepítésekor a Configuration Manager 2007-forráshelyről a csomag Csomagazonosítóját nem őrzi meg a célként megadott helyen. Ennek eredményeként a célhierarchiában lévő ügyfelek nem használhatják a megosztott terjesztési pontokon rendelkezésre álló rendszerindító lemezképek csomagjait.  

-   Feladatütemezések. Ügyfél-telepítési csomagra hivatkozik feladatütemezés áttelepítésekor a hivatkozás egy hivatkozást a célhierarchia ügyfél-telepítési csomag helyére.  

    > [!NOTE]  
    >  Feladatütemezés áttelepítésekor a Configuration Manager a célhierarchiában szükségtelen objektumokat is áttelepíthet. Ezek az objektumok rendszerindító lemezképeket és a Configuration Manager 2007 ügyfél-telepítési csomagokat tartalmaznak.  

-   Illesztőprogramok és illesztőprogram-csomagok.  

##  <a name="Plan_Migrate_Compliance_settings"></a>A szükséges konfiguráció kezelése áttelepítésének tervezése  
Áttelepíthet konfigurációs elemeket és referenciakonfigurációkat.  

> [!NOTE]  
>  A Configuration Manager 2007 forráshierarchiákból származó nem értelmezett konfigurációs elemekről nem támogatottak az áttelepítéshez. Ezeket a konfigurációs elemeket nem telepítheti át és nem importálhatja a célhierarchiába. Nem értelmezett konfigurációs elemekről kapcsolatban bővebben lásd: a nem értelmezett konfigurációs elemekről a [kapcsolatos Konfigurációelemek szükséges konfiguráció kezelésének](http://go.microsoft.com/fwlink/?LinkId=103846) témakört a Configuration Manager 2007 dokumentációs könyvtárában.  

A Configuration Manager 2007 konfigurációs csomagjait importálhatja. Az importálási folyamat automatikusan átalakítja a konfigurációs csomagok kompatibilis a System Center Configuration Managerrel.  

##  <a name="Plan_migrate_Boundaries"></a>Határok áttelepítésének tervezése  
 A határok a következő hierarchiák között telepíthetők át: Határok áttelepítésekor a Configuration Manager 2007 a forrás helyéről minden határ egyszerre áttelepíti, és a rendeltetési hierarchiában létrehozott új határcsoportba kerül. Ha a határokat a System Center 2012 Configuration Manager vagy a System Center Configuration Manager hierarchiából telepít át, mindegyik kiválasztott határ a célhierarchiában lévő új határcsoportba kerül.  

 Tartalom elhelyezése engedélyezett mindegyik automatikusan létrehozott határcsoportnál, de a helyhozzárendelés nem. Ezzel elkerülhető, hogy a helyek hozzárendelésekor a forrás és a rendeltetés hierarchiái között átfedések keletkezzenek. Amikor telepít át egy Configuration Manager 2007-forráshelyről, így megakadályozható, hogy új Configuration Manager 2007-ügyfelek, amelyek a rendeltetési hierarchiába helytelen hozzárendeléséből települnek. Alapértelmezés szerint a System Center Configuration Manager-ügyfelek automatikusan rendel hozzá a Configuration Manager 2007-helyek.  

 Áttelepítéskor ha terjesztési pontot rendeltetési hierarchiával oszt meg, a terjesztési ponthoz társított határok automatikusan áttelepülnek a rendeltetési hierarchiába. A célhierarchiában lévő áttelepítési létrehoz egy új írásvédett határcsoportot minden megosztott terjesztési pont. Ha a forrás hierarchiájában megváltoztatja a terjesztési pont határait, a rendeltetés hierarchiájában a határcsoport a legközelebbi adatgyűjtéskor frissül ezen változásokkal.  

##  <a name="Plan_Migrate_reports"></a>Jelentések áttelepítésének tervezése  
A Configuration Manager nem támogatja a jelentések áttelepítését. Helyette használható az SQL Server Reporting Services jelentéskészítője, hogy a jelentéseket exportálja a forrás hierarchiájából, majd importálja a rendeltetés hierarchiájába.  

> [!NOTE]  
>  Mivel változás történt a Configuration Manager 2007 és System Center Configuration Manager között jelentésekben, tesztelje az egyes jelentések, amelyek importál a Configuration Manager 2007 hierarchia, annak érdekében, hogy a várt módon működik.  

További tudnivalók a jelentésekről [a System Center Configuration Manager jelentéskészítési](../../core/servers/manage/reporting.md).  

##  <a name="Plan_Migrate_Org_Folders"></a>Szervezeti és keresési mappák áttelepítésének megtervezése  
 Támogatott forráshierarchiából szervezeti és keresési mappákat telepíthet át célhierarchiába. Emellett a System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchia áttelepítheti a mentett keresés feltételei a célhierarchiába.  

 Alapértelmezés szerint áttelepítéskor megmarad a keresési mappa és az objektumok és gyűjtemények felügyeleti mappájának a struktúrája. Azonban az áttelepítési feladat létrehozása varázslóban a a **beállítások** lapján állíthat be egy áttelepítési feladat hogy ne telepítse át az objektumok szervezeti struktúráját ehhez a beállításhoz tartozó jelölőnégyzet jelölésének törlése. A gyűjtemények szervezeti struktúrája mindig megőrződik.  

 Kivéve az olyan keresési mappáét, amelyik virtuális alkalmazásokat tartalmaz. App-V csomag áttelepítésekor az App-V csomag a System Center Configuration Manager alkalmazás alakul. A keresési mappa áttelepítése után csak a többi csomag található, és a keresési mappa nem keresse meg az App-V-csomag miatt az átalakításhoz egy alkalmazás az App-V csomag áttelepítésekor.  

 A System Center 2012 Configuration Manager vagy a System Center Configuration Manager forráshierarchia mentett keresést telepít át, a Keresés és a keresési eredmények nem a információ feltételeket telepíti át. A mentett keresés áttelepítése a esetén nem alkalmazható a Configuration Manager 2007-forráshelyről.  

##  <a name="Plan_Migrate_AI"></a>Tervezze meg az Eszközintelligencia egyéni beállításainak áttelepítése  
 Az Eszközintelligencia testreszabásai áttelepíthetők a támogatott forráshierarchiából a célhierarchiába. Nincsenek nem módosult jelentős mértékben a Configuration Manager 2007 és System Center Configuration Manager Eszközintelligencia testreszabásainak struktúrájába.  

> [!NOTE]  
>  A System Center Configuration Manager nem támogatja az Eszközintelligencia objektumainak áttelepítését a Configuration Manager 2007 helyen, amely Asset Intelligence Service 2.0 (AIS 2.0) használja.  

##  <a name="Plan_Migrate_SWM_Rules"></a>Szoftverhasználat-mérési szabályok testreszabások áttelepítésének megtervezése  
 Nincsenek nem módosult jelentős mértékben a szoftverhasználat-mérés a Configuration Manager 2007 és System Center Configuration Manager között. A szoftverhasználat-mérési szabályok áttelepíthetők a támogatott forráshierarchiából a célhierarchiába.  

 A célhierarchiába áttelepített szoftverhasználat-mérési szabályok nincsenek konkrét helyhez társítva a célhierarchiában, hanem a hierarchia összes ügyfelére vonatkoznak. Ha azt szeretné, hogy egy szoftverhasználat-mérési szabály csak adott helyre vonatkozzon, az áttelepítése után szerkeszteni kell azt a mérési szabályt.  

