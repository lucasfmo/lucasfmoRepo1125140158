---
title: "A karbantartási feladat referencia |} Microsoft Docs"
description: "Az egyes a System Center Configuration Manager helykarbantartási feladatok, és hogy ezek a feladatok alapértelmezés szerint engedélyezett adatainak beolvasása."
ms.custom: na
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
caps.latest.revision: 16
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: a2d4420c2274a9b1ceb47ffd267849fdb5a55a61
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>A System Center Configuration Manager karbantartási feladataihoz tartozó referenciák

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör részletek felsorolja az egyes System Center Configuration Manager helykarbantartási feladat, és adja meg a helytípusok, amennyiben rendelkezésre áll-e a feladatot. Leírásokban azt is megtalálja, ha a feladat engedélyezve van, vagy alapértelmezés szerint nincs engedélyezve. További információ a tervezéséről és konfigurálásáról a karbantartási feladatok futtatásához helyek: [karbantartási feladatok a System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md).  

**Helykiszolgáló biztonsági mentése**: Ez a feladat használható a fontos adatok helyreállítását készíti elő. A hely és a Configuration Manager-adatbázis visszaállítása a kritikus információinak biztonsági mentését is létrehozhat. További információkért lásd: [biztonsági mentés és helyreállítás a System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Nincs engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Ellenőrizze az alkalmazás címének és a Leltáradatokat**: Ez a feladat segítségével biztosítja az egységességet a szoftverleltár jelentett szoftvercímek és az Eszközintelligencia-katalógusban szereplő szoftvercímek között. További információkért lásd: [A System Center Configuration Manager Eszközintelligencia szolgáltatásának bemutatása](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Telepítési jelző törlése**: Ez a feladat használható a telepített állapot jelzője eltávolítja azon ügyfelek, amelyek nem küldenek Szívveréses felderítési adatrekordot során a **ügyfél Újrafelderítési** időszak. A telepített jelző megakadályozza az automatikus ügyfélleküldéses telepítést olyan számítógép, amelyen esetleg aktív Configuration Manager-ügyfél.  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Nincs engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Alkalmazásigénylési adatok törlése**: Ez a feladat segítségével törölheti az elavult alkalmazásigénylési az adatbázisból. Alkalmazás kérelmekkel kapcsolatos további információkért lásd: [hozzon létre és telepítsen egy alkalmazást a System Center Configuration Managerrel](/sccm/apps/get-started/create-and-deploy-an-application).  

-   Központi adminisztrációs hely: Nem érhető el
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult ügyfél letöltési előzmények törlése**: Ez a feladat segítségével törölheti a letöltési forrás ügyfelek által használt kapcsolatos előzményadatok. Töltse le való feltöltéséhez használt adatforrás adatait a [Ügyféladatforrások irányítópult](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).  
-  Központi adminisztrációs hely – nem érhető el
-     **Elsődleges hely** – Engedélyezve
-  Másodlagos hely – Nem érhető el

**Elavult Ügyfélműveletek törlése**: Ez a feladat segítségével Ügyfélműveletek összes azokat az elavult adatokat törli a helyadatbázisból. Ilyenek többek között az elavult vagy lejárt ügyfélértesítések (például gépi vagy felhasználói szabályzatok letöltésére vonatkozó kérések) vagy az Endpoint Protection adatai (például adminisztrátori kérések az ügyfelek felé, hogy futtassanak vizsgálatot vagy töltsék le a frissített definíciókat).

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Ügyféljelenlét-előzmények törlése**: Ez a feladat segítségével törölheti az előzmények állapotára vonatkozó információk az online ügyfelek (ügyfélértesítések által rögzített), amely a megadott időtartamnál régebbi. Az ügyfél-értesítésekkel kapcsolatos további információkért lásd: [Ügyfelek figyelése a System Center Configuration Managerben](../../../core/clients/manage/monitor-clients.md).  

-   **Központi adminisztrációs hely**: Engedélyezve   
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Törli az elavult felhő felügyeleti átjáró forgalmi adatok**: Ez a feladat használható a forgalom átmegy kapcsolatos összes elavult adatokat törli a [felhő adatkezelési átjáró](/sccm/core/clients/manage/plan-cloud-management-gateway) a helyadatbázisból. Például a kérelmek, a teljes kérelem bájt, a teljes válasz bájtok, a sikertelen kérések száma és a egyidejű kérelmek maximális számát számát vonatkozó adatokat tartalmazza.  
- **Központi adminisztrációs hely** – Engedélyezve
- **Elsődleges hely** – Engedélyezve
- Másodlagos hely – Nem érhető el


**Elavult gyűjteményfájlok törlése**: Ez a feladat segítségével törli az összegyűjtött fájlok kapcsolatos elavult adatokat az adatbázisból. A gyűjteményfájlokat is törli a helykiszolgáló-mappastruktúrából a kiválasztott helyen. Alapértelmezés szerint a gyűjteményfájlok öt legújabb példánya a helykiszolgálón tárolja a **Inboxes\sinv.box\FileCol** könyvtár. További információkért lásd: [Bevezetés a System Center Configuration Manager szoftverleltárába](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult számítógép-társítási adatok törlése**: Ez a feladat segítségével elavult operációs rendszer központi telepítésének számítógép-társítási adatok törlése az adatbázisból. Az információk a felhasználóiállapot-visszaállítás végrehajtásakor használatosak. A számítógép-társítással kapcsolatos további információkért lásd: [A felhasználói állapot kezelése a System Center Configuration Managerben](../../../osd/get-started/manage-user-state.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Eszközészlelési adatok törlése**: Ez a feladat használatával törli a kibontási nézetek által létrehozott adatbázisból az elavult adatokat. Alapértelmezés szerint a kibontási nézetek le vannak tiltva. Csak engedélyezi ezeket a Configuration Manager SDK használatával. Ha a kibontási nézetek le vannak tiltva, nincsenek törlendő adatok ehhez a feladathoz.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Az elavult Eszköztörlési rekordokat törlése**: Ez a feladat használatával törli a mobileszköz tartalomtörlési műveleteivel kapcsolatos elavult adatokat az adatbázisból. További információ a mobil eszközök tartalmának törlését: [távoli törléssel, zárolással vagy PIN-kód alaphelyzetbe állításával a System Center Configuration Manager használatával adatok védelméhez](/sccm/mdm/deploy-use/wipe-lock-reset-devices).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Az Exchange Server-összekötő által kezelt elavult eszközök törlése**: Ez a feladat segítségével törölheti az Exchange Server-összekötő által kezelt mobileszközökkel kapcsolatos elavult adatokat. Ezek az adatok a konfigurált időköz szerint törlődnek az **(nap) percnél hosszabb ideig inaktív mobileszközök figyelmen kívül hagyása** beállítást a **felderítési** az Exchange Server-összekötő tulajdonságainak lapján. További információkért lásd: [Mobileszközök kezelése a System Center Configuration Manager és az Exchange használatával](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

-   Központi adminisztrációs hely: Nem érhető el   
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult eszközfelderítési adatok törlése**: Ez a feladat segítségével törli az elavult felderítési adatokat az adatbázisból. Ezek az adatok tartalmazhatnak azt jelzi, hogy a Szívveréses felderítés, a hálózati felderítés és az Active Directory tartományi szolgáltatások felderítési módszerek (rendszer, felhasználó és csoport). Amikor egy adott helyen lefut a feladat, törli a helyhez tartozó adatokat, majd replikálja a módosításokat a többi helyen. A felderítéssel kapcsolatos további információkért lásd: [A felderítés futtatása a System Center Configuration Managerből](../../../core/servers/deploy/configure/run-discovery.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult terjesztésipont-használati adatok törlése**: Ez a feladat törli az adatbázisból az elavult, amely a megadott időtartamnál hosszabb tárolt adatokat a terjesztési pontok használatát.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Az Endpoint Protection előzmények állapotadatok elavult törlése**: Ez a feladat segítségével törli az Endpoint Protection elavult állapotadatait az adatbázisból. Az Endpoint Protection-állapotadatokról bővebben lásd: [Az Endpoint Protection figyelése a System Center Configuration Managerben](../../../protect/deploy-use/monitor-endpoint-protection.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult beléptetett eszközök törlése**: Az 1602-es frissítés kezdve ez a feladat alapértelmezés szerint nincs engedélyezve. Ez a feladat törli a helyadatbázisból a mobil eszközök, amelyek még nem jelentettek semmilyen adatról a helynek egy meghatározott ideig kapcsolatos elavult adatokat használhatja.

Ez a feladat a Microsoft Intune (hibrid) regisztrált eszközökre vonatkozik, vagy a Configuration Manager helyszíni mobileszköz-kezelés. A Configuration Manager vagy az Intune használatával regisztrált eszközökön az operációs rendszerekkel kapcsolatos információk: a [Microsoft Intune által beléptetett mobileszközök](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mobile-devices-enrolled-by-microsoft-intune) szakasz [operációs rendszerek támogatott ügyfelek és eszközök a System Center Configuration Manager](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Nincs engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Leltárelőzmények törlése**: Ez a feladat segítségével törölheti a leltáradatokat az adatbázisból a megadott időtartamnál hosszabb tárolt. További információkért a leltárelőzményekkel kapcsolatban lásd: [A hardverleltár megjelenítése az erőforrás-kezelővel a System Center Configuration Managerben](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult naplóadatok törlése**: Ez a feladat segítségével törölheti az adatbázisból a hibaelhárításhoz használt elavult naplóadatokat. Ezek az adatok nem kapcsolódik a Configuration Manager összetevőinek működéséhez.  

> [!IMPORTANT]  
> Alapértelmezés szerint ez a feladat mindennap lefut az egyes helyeken. A központi adminisztrációs helyen és az elsődleges helyeken a 30 napnál régebbi adatokat törli. Ha használja az SQL Server Express másodlagos helyen, győződjön meg arról, hogy ez a feladat naponta fut, és törli az adatokat, amely a hét napja inaktív volt.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   **Másodlagos hely**: Engedélyezve  

**Elavult értesítési feladatelőzmények törlése**: Ez a feladat segítségével törli az ügyfél-értesítési feladataival kapcsolatos adatokat a helyadatbázisból, ha az adott ideje nem frissült. Az ügyfélértesítés kapcsolatos további információkért lásd: [ügyfelek központi telepítésének feladatai a System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult replikációs összefoglalások adatainak törlése**: Ez a feladat segítségével törli az elavult replikációs összefoglalások adatait a helyadatbázisból, ha az adott ideje nem frissült. További információkért lásd: [Az adatbázis-replikációs hivatkozások és a replikáció állapotának figyelése](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) című szakasz a [Hierarchia és replikációs infrastruktúra figyelése a System Center Configuration Managerben](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) témakörben.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   **Másodlagos hely**: Engedélyezve  

**Elavult Jelszórekordok törlése**: A hierarchia legfelső szintű helyén ez a feladat segítségével törölheti az Android és Windows Phone-eszközök PIN-kód alaphelyzetbe állítása azokat az elavult adatokat. Jelszó alaphelyzetbe állítása adatok titkosítva van, de az eszközök a PIN-kódot tartalmaz. Ez a feladat alapértelmezés szerint engedélyezve van, és egy napnál régebbi adatokat törli.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Replikációkövetési adatok törlése**: Ez a feladat segítségével törölheti az adatbázisból a Configuration Manager-helyek közötti adatbázis-replikációval kapcsolatos elavult adatokat. A karbantartási feladat beállításainak módosítása esetén a rendszer a megváltoztatott konfigurációt alkalmazza a hierarchia mindegyik érintett helyén. További információkért lásd: [Az adatbázis-replikációs hivatkozások és a replikáció állapotának figyelése](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) című szakasz a [Hierarchia és replikációs infrastruktúra figyelése a System Center Configuration Managerben](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) témakörben.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   **Másodlagos hely**: Engedélyezve  

**Elavult szoftverhasználat-mérési adatok törlése**: Ez a feladat segítségével törölheti azokat az elavult adatokat a szoftverhasználat-mérés, amelyek ideje vannak az adatbázisban a megadott időtartamnál hosszabb. További információkért lásd: [Szoftverhasználat-mérés a System Center Configuration Managerben](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult szoftverhasználat-mérési összefoglaló adatok törlése**: Ez a feladat segítségével törölheti azokat az elavult összegző adatokat a szoftverhasználat-mérés, amelyek ideje vannak az adatbázisban a megadott időtartamnál hosszabb. További információkért lásd: [Szoftverhasználat-mérés a System Center Configuration Managerben](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult állapotüzenetek törlése**: Ez a feladat segítségével törölheti azokat az elavult állapotüzenet-adatokat, a Állapotszűrő szabályok az adatbázisból. Információkért lásd: a "Figyelése a Configuration Manager állapotrendszer" című rész, témakör [riasztások és az állapotrendszer használata a System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult kockázati adatok törlése**: Ez a feladat törli az elavult Endpoint Protection kockázati adatokat az adatbázisból a megadott időtartamnál hosszabb tárolt használata Bővebben az Endpoint Protectionnel kapcsolatban lásd: [Endpoint Protection a System Center Configuration Managerben](../../../protect/deploy-use/endpoint-protection.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Ismeretlen számítógépek törlése**: Ez a feladat törli az ismeretlen számítógépekkel kapcsolatos adatokat a helyadatbázisból, ha az adott ideje nem frissült használható. További információkért lásd: [Felkészülés az ismeretlen számítógépekre való központi telepítésre a System Center Configuration Managerben](../../../osd/get-started/prepare-for-unknown-computer-deployments.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Felhasználóeszköz-kapcsolati adatok törlése**: Ez a feladat segítségével törli az elavult Felhasználóeszköz-kapcsolati adatokat az adatbázisból. További információkért lásd: [Felhasználók és eszközök összekapcsolása felhasználó és eszköz közötti kapcsolattal a System Center Configuration Managerben](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Lejárt Csomagrekordjainak törlése csoportos regisztráció**: Ez a feladat segítségével törölje a régi tömeges beléptetési tanúsítványainak és a megfelelő profilok, a beléptetési tanúsítvány lejárta után. További információkért lásd: [tanúsítványprofilok létrehozása](/sccm/protect/deploy-use/create-certificate-profiles).
-   **Központi adminisztrációs helyet**: Engedélyezve
-   **Elsődleges hely**: Engedélyezve
-   Másodlagos hely: Nem érhető el

**Inaktív ügyfél-felderítési adatok törlése**: Ez a feladat segítségével-felderítési adatok törlése az adatbázisból inaktív ügyfelek számára. Ügyfelek vannak megjelölve inaktívként, ha az ügyfél elavultként van megjelölve, és -konfigurációja által létrehozott és az ügyfél állapotát.

Ez a feladat csak olyan erőforrásokon használható, amelyek a Configuration Manager-ügyfelek működik. Nem egyezik a **elavult eszközfelderítési adatok törlése** feladat, amely törli az összes elavult eszköz-felderítési adatrekordot. Ha egy helyen futtatja le ezt a feladatot, az a hierarchia összes helyének adatbázisából eltávolítja az adatokat. További információkért lásd: [Az ügyfélállapot konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-status.md).  

> [!IMPORTANT]  
> Ha engedélyezve van, úgy állítsa be a ennek a feladatnak a futtatását, hogy nagyobb, mint a **a Szívveréses felderítés** ütemezést. Ez lehetővé teszi az aktív ügyfelek küldjenek Szívveréses felderítési adatrekordot való megjelöléséhez ügyfélrekordjuk aktívnak, így ez a feladat nem törli őket.  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Nincs engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult riasztások törlése**: Ez a feladat segítségével törölheti a lejárt riasztásokat, amelyek az adatbázisból a megadott időtartamnál hosszabb tárolja. További információkért lásd: [A riasztások és az állapotrendszer használata a System Center Configuration Managerben](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult ügyfél-felderítési adatok törlése**: Ez a feladat segítségével törli az elavult ügyfélrekordokat az adatbázisból. Az elavultként megjelölt rekordot általában újabb váltja fel a szóban forgó ügyfél esetében. Az újabb rekord lesz az ügyfél aktuális rekordja. A felderítéssel kapcsolatos további információkért lásd: [A felderítés futtatása a System Center Configuration Managerből](../../../core/servers/deploy/configure/run-discovery.md).  

> [!IMPORTANT]  
> Ha engedélyezve van, ez a feladat futtatását, hogy nagyobb, mint a Szívveréses felderítés ütemezésének konfigurálása Az ügyfelek ezáltal olyan szívveréses felderítési rekordot küldhetnek, amelyik pontosan megadja az elavult állapotot.  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Nincs engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Elavult Erdőfelderítési helyek és alhálózatok törlése**: Ez a feladat segítségével törölheti az Active Directory helyek, alhálózatok és tartományok, amelyek még nem derített fel az Active Directory Erdőfelderítési mód az elmúlt 30 nap adatait. Ez eltávolítja a felderítési adatokat, de nincs hatással az ezen adatokból létrehozott határokat. További információkért lásd: [A felderítés futtatása a System Center Configuration Managerből](../../../core/servers/deploy/configure/run-discovery.md).  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Árva ügyfelek telepítési Állapotrekordjainak törlése**: Ez a feladat segítségével rendszeres kiürítése az ügyfél központi telepítési állapot információk tartalmazó tábla. Ez a feladat elavult vagy leszerelt eszközök társított rekordok fog törölni.  
-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el

**Nem használt Alkalmazásváltozatok törlése**: Ez a feladat segítségével törölheti a már nem hivatkozott alkalmazásváltozatokat. További információkért lásd: [Alkalmazások módosítása és felülírása a System Center Configuration Managerben](../../../apps/deploy-use/revise-and-supersede-applications.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Gyűjteménytagok**: A Gyűjteménytagság értékelését helyösszetevőként konfigurálnia. További információkért a helyösszetevőkkel kapcsolatban lásd: [A System Center Configuration Manager helyösszetevői](../../../core/servers/deploy/configure/site-components.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Kulcsok figyelése**: Ez a feladat használható a Configuration Manager-adatbázis elsődleges kulcsok sértetlenségének figyelésére. Egy elsődleges kulcs egy olyan oszlop (vagy akár kombinálhatja is oszlopok), amely egyedileg azonosít egy sort, és megkülönböztetik a Microsoft SQL Server adatbázisi táblájának többi sorától.  

-   **Központi adminisztrációs hely**: Engedélyezve    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Indexek újraépítése**: Ez a feladat használható a Configuration Manager-adatbázis indexeinek újraépítésére. Az index olyan adatbázisi struktúra, amelyik adatbázis táblán lett létrehozva, hogy meggyorsítsa az adatvisszakeresést. Például az indexelt oszlopban keresés gyakran sokkal gyorsabb, mint a nem indexelt oszlopban.

A teljesítmény javítása érdekében a Configuration Manager adatbázisa indexei gyakran frissülnek, hogy továbbra is szinkronizálja az adatbázisban tárolt adatok állandó változásaival. Ez a feladat azokat az oszlopokat indexeli, amelyek legalább 50 százalékban egyediek, elveti az indexelést azoknál az oszlopoknál, amelyek kevesebb, mint 50 százalékban egyediek, az egyediség feltételeinek eleget tévő meglévő indexeket pedig újraépíti.  

-   **Központi adminisztrációs hely**: Nincs engedélyezve    
-   **Elsődleges hely**: Nincs engedélyezve    
-   **Másodlagos hely**: Nincs engedélyezve  

**Telepített szoftverek adatainak összefoglalója**: Ez a feladat használható a telepített szoftverek adatainak több rekordból egy általános rekordban való összefoglalásához. Adatok összegzési tömörítheti a Configuration Manager adatbázisában tárolt adatok mennyisége. További információkért lásd: [Bevezetés a System Center Configuration Manager szoftverleltárába](../../clients/manage/inventory\introduction-to-software-inventory.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Szoftverhasználat-mérés fájlhasználati adatainak összefoglalója**: Ez a feladat használható a adatainak több rekordból egyetlen általános rekordba fájl mérési való összefoglalásához. Adatok összegzési tömörítheti a Configuration Manager adatbázisában tárolt adatok mennyisége.

Ezt a feladatot használhatja a **szoftverhasználat-mérés havi használati adatainak összefoglalója** feladat, hogy összesítse a szoftverhasználat-mérési adatokat, és a Configuration Manager adatbázisban lemezterületet takarítson meg. További információkért lásd: [Szoftverhasználat-mérés a System Center Configuration Managerben](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Szoftverhasználat-mérés havi használati adatainak összefoglalója**: Ez a feladat használható a adatainak több rekordból szoftverhasználat-mérés havi fájlhasználati egy általános rekordban való összefoglalásához. Adatok összegzési tömörítheti a Configuration Manager adatbázisában tárolt adatok mennyisége.

Ezt a feladatot használhatja a **összesítse a szoftverhasználat-mérés használati adatainak** feladat, hogy összesítse a szoftverhasználat-mérési adatokat, és a Configuration Manager-adatbázis lemezterületet takarítson meg. További információkért lásd: [Szoftverhasználat-mérés a System Center Configuration Managerben](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Alkalmazáshoz elérhető célzás frissítése**: Ez a feladat használható szeretné, hogy a Configuration Manager újraszámítsa a gyűjteményben, a házirend és az alkalmazástelepítések erőforrásokhoz. Ha házirendeket vagy alkalmazásokat gyűjteménybe telepíti, a Configuration Manager létrehoz egy kezdeti leképezést a központilag telepített objektumok és a gyűjtemény tagjai között.

Ezeket a leképezéseket a rendszer a gyors elérés céljából egy táblázatban tárolja. Ha egy gyűjtemény tagsága módosul, a rendszer frissíti a tárolt leképezéseket a változásokkal. Azonban úgy is a leképezések elavulttá válhatnak. Ha például a hely nem képes megfelelően feldolgozni az értesítési fájlt, előfordulhat, hogy a módosítást a rendszer nem vezeti be a leképezésekbe. Ez a feladat frissíti a leképezéseket gyűjtemény aktuális tagságától függenek.  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

**Alkalmazáskatalógus tábláinak frissítése**: Ez a feladat segítségével szinkronizálja az Alkalmazáskatalógus weboldal-adatbázisának gyorsítótárát a legfrissebb alkalmazásadatokkal. A karbantartási feladat beállításainak módosítása esetén a rendszer a megváltoztatott konfigurációt alkalmazza a hierarchia összes elsődleges helyén.  

-   Központi adminisztrációs hely: Nem érhető el    
-   **Elsődleges hely**: Engedélyezve    
-   Másodlagos hely: Nem érhető el  

