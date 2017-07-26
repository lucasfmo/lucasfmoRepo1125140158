---
title: "A Technical Preview 1511-es Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1511-es verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69473706-21b3-498b-a67e-670fdc988f0d
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: d0bde2c085cc9b330bc772e68081d629ca9e2f11
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1511-for-system-center-configuration-manager"></a>A rendszer 1511-es Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk bemutatja a Technical Preview a System Center Configuration Manager, 1511-es verziójában elérhető funkciókat. Ebben a verzióban az alapkonfigurációt, melyekkel a technical preview telepítése egy új technical preview-hely telepítése vagy egy korábbi, a technical Preview frissíteni.   A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.  

Új funkciókat próbálhatja ki ebben a következők:  

##  <a name="BKMK_WUfB"></a>Integráció a Windows Update for Business a Windows 10  
 A Configuration Manager most már képes megkülönböztetni azokat a Windows 10 rendszerű számítógépeket, amely közvetlenül csatlakozik a Windows Update for Business (WUfB) és a WSUS a kapcsolódnak a Windows 10 frissítéseinek és új kapcsolat megfelelően.  A wufb szolgáltatáshoz kapcsolódó számítógépek a frissítések és verziófrissítések csoportházirendek vagy mobileszköz-kezelési házirendek egy rendszergazda felhasználó által beállított ütemben kezelhetők, és a frissítések verziófrissítések is telepíthető közvetlenül a wufb-t.    
A wufb szolgáltatáshoz kapcsolódó számítógépek a Configuration Manager csak akkor tudni jelentést készíteni a megfelelőségi állapotról (ideértve a Windows vagy a frissítéseket). Emellett a Configuration Manager csak akkor tudja telepíteni a Microsoft Updates vagy 3. felek frissítéseit ezekre a számítógépekre.  

 **A forgatókönyv előfeltételei:**  

-   Windows 10 Pro asztali verzió vagy Windows 10 Enterprise Edition 1511-es vagy újabb verzió  

-   Szolgáltatással kezelendő számítógépek [a Windows Update for Business](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx).  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja a következő feladat befejeződik, majd kövesse a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel járt:  

1.  Ha korábban engedélyezve lett, tiltsa le a Windows Update Agent szoftvert, hogy az ne keressen a WSUS szolgáltatásban.   
    A beállításkulcs **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** annak jelzésére, hogy a számítógép van keres a WSUS vagy a Windows Update állítható be.  Ha a 2 érték van megadva, a számítógép nem keres a WSUS szolgáltatásban.  

2.  Jegyezze fel az új attribútum **UseWUServer**alatt a **a Windows Update** Configuration Manager Resource Explorer csomópontja.  

3.  Hozzon létre egy gyűjteményt a **UseWUServer** attribútum alapján az összes számítógéphez, amely a WUfB szolgáltatáshoz csatlakozva szerzi be a frissítéseket és az új verziókat.  

4.  Hozzon létre egy ügyfélügynök-beállítást a szoftverfrissítési munkafolyamat letiltásához, és telepítése a beállítást a közvetlenül a WUfB szolgáltatáshoz csatlakozó számítógépek gyűjteményére.  

5.  A WUfB szolgáltatással felügyelt számítógépek megfelelőségi állapotánál az **Ismeretlen** érték fog megjelenni, és nem fognak beleszámítani az összesített megfelelőségi arányba.  

##  <a name="BKMK_Office365ProPlus"></a>Az Office 365 ProPlus ügyfél frissítésének a System Center Configuration Manager használatával kezelése  
 A Configuration Manager most már képes kezelni az Office 365 asztali ügyfél frissítéseinek használata a Configuration Manager szoftverfrissítések felügyelete munkafolyamatával.    
Amikor a Microsoft Office 365 asztali ügyfél új frissítést a Windows Server frissíti Services (WSUS), a Configuration Manager fog tudni szinkronizálni a frissítést a katalógusával, ha az Office 365 frissítése úgy van konfigurálva, a katalógus szinkronizálása részét.  A Configuration Manager helykiszolgáló letölti az Office 365-ügyfélfrissítések és terjeszteni a csomagot a Configuration Manager terjesztési pontokra.  A Configuration Manager-ügyfél ezután megadja az Office 365 asztali ügyfél frissítéseinek beszerzése a hol és mikor kell elkezdeni a telepítési folyamat.  

**A forgatókönyv előfeltételei:**  

### <a name="try-it-out"></a>Próbálja ki!  
 Próbálja a következő feladat befejeződik, majd kövesse a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel járt:  

1.  Office 365-frissítések a Configuration Manager-kiszolgálóra történő szinkronizálása, és megtekintheti azokat a Configuration Manager konzoljáról.  

2.  Hagyja jóvá, és sikeresen telepítheti az Office 365-frissítéseket.  

3.  Letöltheti és sikeresen Office 365 frissítéseit az ügyfelekre.  

4.  Office 365 frissítéseinek megfelelőségét a konzolon belüli figyelés vagy jelentések használatával ellenőrizheti.  

 Részletes útmutató: [kezelése Office 365 asztali ügyfél frissítéseit a System Center Configuration Manager Technical Preview](https://technet.microsoft.com/library/mt628083.aspx).  

##  <a name="BKMK_AlwasyOn"></a>Az SQL Server AlwaysOn magas rendelkezésre állású adatbázisok támogatása  
 A Configuration Manager mostantól támogatja a Helyadatbázis futtatására egy SQL Server AlwaysOn rendelkezésre állási csoportok használatával.  Amikor új helyet telepít, közvetlenül telepíthet a rendelkezésre állási csoport használata helyett az SQL Server normál példányát.  

> [!NOTE]  
>  Sikeres konfigurációs rendelkezésre állási csoportok használata kell ismernie az SQL Server rendelkezésre állási csoportok konfigurálása és található dokumentáció és eljárások nyújtanak az SQL Server dokumentációs könyvtárában.  

Konfigurálhatja és használhatja a rendelkezésre állási csoportokat magas szintű folyamata tartalmazza:  

1.  Az SQL Server rendelkezésre állási csoport konfigurálása.  

2.  Új Configuration Manager-hely telepítése, és a beállítás során utasítsa a helyet a rendelkezésre állási csoport használatára a csoport végpontjának megadásával.  

**A forgatókönyv előfeltételei:**  

-   A Configuration Manager Technical Preview által támogatott SQL Server verziója szükséges  

-   Létre kell hoznia és az SQL Server rendelkezésre állási csoport konfigurálása a Configuration Manager telepítése előtt  

-   A rendelkezésre állási csoportnak rendelkeznie kell egy elsődleges replikával, és legfeljebb két szinkron másodlagos replikája lehet.  

-   A rendelkezésre állási csoportban legalább egy végponttal rendelkeznie kell  

-   Rendelkeznie kell egy hálózati helyre, amely a rendelkezésre állási csoport minden egyes SQL Server hozzáfér. Ez a hely által használt, a rendelkezésre állási csoport konfigurálásakor és a telepítés befejezése után eltávolítható.  

**Jelen kiadással kapcsolatos ismert problémák:**  

-   Nem adhat sikeresen új replikatag egy rendelkezésre állási csoporthoz, amely már helyadatbázisként használatban van. Ehelyett után újra kell telepítenie a helyet az új replikatag hozzáadását.  

-   Ebben a forgatókönyvben szükség lehet telepíteni a **SQL Server 2012 natív ügyfél** ([az SQL Server 2012 funkciócsomag a](http://www.microsoft.com/download/details.aspx?id=29065)) a a felügyeletipont-kiszolgálóra. Ez megakadályozza, hogy SQL-csatlakozási hibákat (amelyek naplózása a **mp_getauth.log** a a felügyeletipont-kiszolgálóra).  

### <a name="try-it-out"></a>Próbálja ki!  
Próbálja a következő feladatok végezhetők, majd ez a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel:  

-   Képes vagyok telepíteni egy SQL AlwaysOn rendelkezésre állási csoportokkal konfigurált adatbázis-kiszolgálót használó elsődleges hely  

-   Sikerült feladatátvételt az SQL AlwaysOn rendelkezésre állási csoport számára, a csoport egy új replikájára, és az elsődleges hely továbbra is működik.  

### <a name="configuring-sql-server-alwayson-for-configuration-manager"></a>SQL Server AlwaysOn konfigurálása a Configuration Manager  
 Az alábbi eljárásokkal először létrehozhat és a rendelkezésre állási csoport konfigurálásához, és telepítse az új Configuration Manager-hely, amely a rendelkezésre állási csoportot használja.  

#### <a name="to-create-a-sql-server-alwayson-availability-group"></a>Egy SQL Server AlwaysOn rendelkezésre állási csoport létrehozása  
A folyamat [hozzon létre egy SQL Server rendelkezésre állási csoportot](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) dokumentációja az SQL Server dokumentációs könyvtárában.  Amikor a rendelkezésre állási csoportot hoz létre, győződjön meg arról, a Configuration Managerrel történő használathoz a következő feltételek teljesülnek:  

-   Egy legfeljebb három tag:  

    -   Egy elsődleges másodpéldány és legfeljebb két másodlagos replika  

    -   Másodlagos replikák szinkron replikáknak kell lenniük.  

        > [!TIP]  
        >  Azt javasoljuk, hogy a másodlagos replikákat írásvédettként legyen beállítva. Ez lehetővé teszi, hogy egy másodlagos másodpéldány függvényeket, mint a jelentéskészítés, míg az elsődleges másodpéldány-műveletek teljesítményének fenntartása használni.  

-   Legalább egy végpontot. Ez a végpont virtuális nevét a Configuration Manager-hely telepítésekor használható.  

    > [!TIP]  
    >  Bár a csoport több végpontot is tartalmazhat, a Configuration Manager tehet csak egyet használhat.  

#### <a name="to-install-a-configuration-manager-site-that-uses-the-availability-group"></a>A rendelkezésre állási csoportot használó Configuration Manager-hely telepítése  
Egy SQL Server rendelkezésre állási csoportot használó hely telepítése:  

1.  Helyettesítse be a következő Configuration Manager telepítő kérésére:  

    -   **SQL Server-név**: Adja meg a rendelkezésre állási csoport létrehozásakor konfigurált végpont virtuális nevét. A virtuális nevét kell teljes DNS-nevét, például  **&lt;Végpontkiszolgáló\>. fabrikam.com**.  

    -   **Példány**:  Ezt az értéket üresen kell maradnia. Egyetlen példánya van ebben a konfigurációban.  

    -   **Adatbázis**: Adja meg a rendelkezésre állási csoport elsődleges replikáján létrehozott adatbázis nevét.  

2.  Ezután meg kell adnia egy hálózati helyre, amely a csoport minden SQL-kiszolgálója elérhet:  

    -   A számítógép fiókjának és minden egyes SQL Server szolgáltatásfiók szükséges teljes körű hozzáférést ehhez a helyhez.  

    -   Ez a hely csak a telepítés során használt és megosztása visszavonható vagy törölte a telepítés befejeződése és a hely telepítése után.  

3.  Miután megadta ezeket az információkat, a szokásos folyamattal és konfigurációkkal beállításának befejezése.  

##  <a name="BKMK_ClusterServerUpdates"></a>Kiszolgálófürt karbantartása  
Most hozzon létre egy gyűjteményt, amely egy fürt kiszolgálóit tartalmazza, és konfigurálja a fürt beállításokat a frissítések központi telepítéséhez a fürthöz. Szabályozhatja, hogy a kiszolgálók százalékos arányát az adott időpontban, is konfigurálhat a központi telepítés előtti és utáni PowerShell-parancsfájlokat egyéni műveletek futtatása online állapotban vannak.  

**Jelen kiadással kapcsolatos ismert problémák:**  

-   Jelentéskészítési nem érhető el a fürtkiszolgálók szoftverfrissítések központi telepítési állapotának ellenőrzése.  

-   A Karbantartás ütemezése lehetőség a **fürtbeállítások** lap letiltva és nem érhető el ebben a kiadásban.  

### <a name="try-it-out"></a>Próbálja ki!  
Próbálja a következő feladat befejeződik, majd kövesse a témakör tetejénél található visszajelzési információk használva tudassa velünk, milyen eredménnyel járt:  

-   Képes vagyok kiszolgálófürtöt képviselő gyűjteményt létrehozni. A teszteléshez konfigurálhatja a gyűjteménytagsági szabályokat, hogy a gyűjtemény 2 számítógépet tartalmazzon.  

-   Képes vagyok meghatározni, hogy a fürtben lévő kiszolgálókat csak 50 %-át lehet-e offline állapotban a fürt karbantartásának tetszőleges pontján. Az eljárás mintaparancsfájljainak segítségével megadhatja a központi telepítés előtti és utáni parancsfájlokat.  

-   Egy frissítés telepítése a gyűjteményhez. Tekintse át a start.txt és az end.txt fájlt a C:\temp mappában, és ellenőrizze a fürtben lévő kiszolgálók a központi telepítés indításának és befejezésének idejét. Tekintse át az UpdatesDeployment.log fájlt további információt.  

#### <a name="to-create-a-collection-for-a-server-cluster"></a>A kiszolgálófürt gyűjtemény létrehozása  

1.  [Hozzon létre egy eszközgyűjteményt](https://technet.microsoft.com/library/gg712295.aspx) , amely a fürtbeli kiszolgálókat tartalmazza.  

2.  Az a **eszközök és megfelelőség** munkaterületet, kattintson a **Eszközgyűjtemények**, kattintson a jobb gombbal a fürtben lévő kiszolgálókat tartalmazó gyűjteményt, és kattintson a **tulajdonságok**.  

3.  Az a **általános** lapon jelölje be **minden eszköz ugyanahhoz a kiszolgálófürthöz részét képező**, és kattintson a **beállítások**.  

4.  Az a **fürtbeállítások** lapon, válassza ki a kiszolgálók százalékos arányát céljából lekapcsolódhatnak egyidejűleg a szoftverfrissítései legyenek telepítve. Egy fürtkiszolgálót lehet lekapcsolni, függetlenül a megadott százaléktól egyszerre. A Configuration Manager lefelé kerekíti a szolgáltatás egy időben szervizelhető kiszolgálók. Például ha úgy dönt, hogy 51 % és 4 kiszolgáló a fürtben, 2-kiszolgálókhoz megnyílik offline egyszerre.  

5.  Adja meg, hogy a központi telepítés előtti (a csomópont kiürítésekor) vagy (a Csomópont fürttevékenységének újraindításakor) telepítés utáni parancsfájl használatára.  

    > [!TIP]  
    >  Az alábbiakban példákat is használhatja a központi telepítés előtti tesztelése és a központi telepítés utáni parancsfájlok, amelyek szöveges fájlba írni az aktuális idő:  
    >   
    >  **Központi telepítés előtti**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Telepítés után**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-cluster"></a>A szoftverfrissítések központi telepítése a kiszolgálófürtre  

1.  [Szoftverfrissítések központi telepítése](https://technet.microsoft.com/library/gg712304.aspx) a kiszolgálófürt-gyűjteménybe.  

2.  [A szoftverfrissítések központi telepítésének](https://technet.microsoft.com/library/gg712304.aspx).  

