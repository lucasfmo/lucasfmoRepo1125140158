---
title: "Támogatott SQL Server-verziók |} Microsoft Docs"
description: "SQL Server verziója és konfigurációs követelményei a System Center Configuration Manager helyadatbázisát befogadó beolvasása."
ms.custom: na
ms.date: 05/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 4166560602edf6eb299511c8b59dc3903e3bfffc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>Támogatott SQL Server-verziók a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Minden System Center Configuration Manager hely támogatott SQL Server verziója és a konfigurációját, és a Helyadatbázis tárolásához szükséges.  

##  <a name="bkmk_Instances"></a> Az SQL Server példányai és helyük  
 **Központi adminisztrációs helyen és elsődleges helyek:**  
A Helyadatbázis az SQL Server teljes telepítését kell használnia.  

 SQL Server is található:  

-   A helykiszolgáló számítógépén.  
-   A helykiszolgálóhoz képest távoli számítógépről.  

A rendszer a következő példányokat támogatja:  

-   Az alapértelmezett vagy az SQL Server nevesített példánya.  
-   Többpéldányos konfigurációk.  
-   SQL Server-fürtöt. Lásd: [SQL Server-fürtöt használ a Helyadatbázis futtatására](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md).
-   Egy SQL Server AlwaysOn rendelkezésre állási csoport. Ezt a lehetőséget a Configuration Manager 1602-es vagy újabb verziója szükséges. További információkért lásd: [SQL Server AlwaysOn magas rendelkezésre állású Helyadatbázis a System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).


 **A másodlagos helyek:**  
 A Helyadatbázis az SQL Server vagy SQL Server Express teljes telepítése az alapértelmezett példányát használhatja.  

 SQL Server a helykiszolgáló számítógépen kell lennie.  

 **Korlátozások támogatásához**   
 A következő konfigurációk nem támogatottak:
 -   A hálózati terheléselosztási (NLB) fürt konfigurációjába SQL Server-fürt
 -   SQL Server-fürtöt egy fürt megosztott fürtkötet (CSV)
 -   SQL Server datbase tükrözési technológiája és a társ-társ replikáció

SQL Server tranzakciós replikáció csak támogatott objektumok replikálása használatára konfigurált felügyeleti pontok [az adatbázis-replikák](https://technet.microsoft.com/library/mt608546.aspx).  

##  <a name="bkmk_SQLVersions"></a> Az SQL Server támogatott verziói  
 Több hellyel rendelkező hierarchia esetén a különböző helyek használhatják az SQL Server különböző verzióit a Helyadatbázis futtatására, feltéve, hogy a következők teljesülnek:
 -  A Configuration Manager támogatja a használt SQL Server-verziók.
 -  Az SQL Server-verziók használata a Microsoft támogatási maradnak.
 -  SQL Server két SQL Server-verziók közötti replikáció támogatja.  Például [SQL Server nem támogatja az SQL Server 2008 R2 és az SQL Server 2016 közötti replikáció](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 Hiányában az SQL Server következő verziói támogatottak a System Center Configuration Manager az összes aktív verziójával. Ha egy új SQL Server-verzió támogatja vagy szervizcsomag kerül, a Configuration Manager verzióra, amely biztosítja, hogy támogatást tájékoztat. Hasonlóképpen ha támogatása elavult, keresse meg az érintett verziók a Configuration Manager adatait.   

Egy adott SQL Server szervizcsomag támogatása adott szervizcsomagra összegző frissítését is tartalmazza, kivéve, ha az összegző frissítés megszakítja az előző verziókkal való, az adott alapszintű service pack verzióra. Nincs szervizcsomag-verzió van feltüntetve, ha a funkció szervizcsomag nélküli SQL Server adott verziójának. A jövőben a service pack verzióra vonatkozó megjelenik, ha külön támogatási nyilatkozattal fog deklarálni ahhoz, hogy új szervizcsomag verziója támogatott.


> [!IMPORTANT]  
>  Ha használ SQL Server Standard a központi adminisztrációs hely adatbázisához, akkor korlátozza a hierarchia által támogatott ügyfelek teljes száma. Lásd: [Méret és méretezési számok](../../../core/plan-design/configs/size-and-scale-numbers.md).

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 SP1: Standard, Enterprise  
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A központi adminisztrációs hely  
-   Az elsődleges hely  
-   A másodlagos hely  

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Standard, Enterprise  
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A központi adminisztrációs hely  
-   Az elsődleges hely  
-   A másodlagos hely  


### <a name="sql-server-2014-sp2-standard-enterprise"></a>Az SQL Server 2014 SP2: Standard, Enterprise  
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A központi adminisztrációs hely  
-   Az elsődleges hely  
-   A másodlagos hely



### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Standard, Enterprise  
 Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A központi adminisztrációs hely  
-   Az elsődleges hely  
-   A másodlagos hely


### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 SP3: Standard, Enterprise  
 Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A központi adminisztrációs hely  
-   Az elsődleges hely  
-   A másodlagos hely  

<!-- Support for this service pack version has been dropped by Microsoft    
### SQL Server 2012 SP2: Standard, Enterprise   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A central administration site  
-   A primary site  
-   A secondary site  
-->

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter     
  Az SQL Server jelen verziójában nem támogatott [verziójától 1702](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database).  
 Az SQL Server jelen verziójában továbbra is támogatja, a Configuration Manager verziója előtt 1702 használatakor.

Ha a Configuration Manager verziója támogatja, akkor az SQL Server jelen verziójában nincs minimális összegző frissítés verziója esetében használható a következő:  

-   A központi adminisztrációs hely  
-   Az elsődleges hely
-   A másodlagos hely



### <a name="sql-server-2016-express-sp1"></a>SQL Server 2016 expressz SP1  
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:
-   A másodlagos hely

### <a name="sql-server-2016-express"></a>Az SQL Server 2016 Express
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:
-   A másodlagos hely


### <a name="sql-server-2014-express-sp2"></a>Az SQL Server 2014 expressz SP2   
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A másodlagos hely  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A másodlagos hely  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
Az SQL Server e verziója a következők esetében az összesítő frissítőcsomagra vonatkozó minimális követelmények nélkül használható:  

-   A másodlagos hely  

<!-- Support for this service pack version has been dropped by Microsoft   
### SQL Server 2012 Express SP2   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A secondary site  
-->


##  <a name="bkmk_SQLConfig"></a> Az SQL Server kötelező konfigurációi  
 A következő igényel minden olyan (beleértve az SQL Server Express) Helyadatbázis használt SQL Server telepítését. A Configuration Manager telepíti az SQL Server Expresst a másodlagos hely telepítésének részeként, ha ezeket a konfigurációkat automatikusan létrejönnek.  

 **SQL Server architektúrájának verziója:**  
 A Configuration Manager egy SQL Server a Helyadatbázis futtatásához 64 bites verziója szükséges.  

 **Adatbázis rendezése:**  
 Az egyes helyeken a helykiszolgáló és a helyadatbázishoz használt SQL Server példánynak egyaránt a következő rendezést kell használnia: **SQL_Latin1_General_CP1_CI_AS**.  

 A Configuration Manager támogatja a rendezést a kínai használatra definiált GB18030 szabványainak való megfelelés érdekében két kivétel. További információ: [Nemzetközi támogatás a System Center Configuration Managerben](../../../core/plan-design/hierarchy/international-support.md).  

 **Az SQL Server funkciói:**  
 Csak az **Adatbázismotor-szolgáltatások** funkció kötelező minden helykiszolgáló esetében.  

 A Configuration Manager adatbázis-replikáció nincs szükség a **SQL Server-replikáció** szolgáltatás. Azonban az SQL Server-konfigurációs szükség, ha használ [a System Center Configuration Manager adatbázis-replikák beállítása felügyeleti pontokhoz](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Windows-hitelesítés:**  
 A Configuration Manager megköveteli **Windows-hitelesítés** való az adatbázishoz való csatlakozás érvényesítéséhez.  

 **SQL Server-példány:**  
 Minden hely esetében dedikált SQL Server-példányt kell használnia. Ez lehet egy **megnevezett példány** vagy az **alapértelmezett példány**.  

 **Az SQL Server memóriája:**  
 Foglaljon le memóriát az SQL Server által az SQL Server Management Studio használatával és a **minimális kiszolgálómemória** beállítás alatt **Kiszolgálómemória beállításai**. A rögzített méretű memória beállításával kapcsolatos további információkért lásd: [hogyan: A rögzített méretű memória (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).  

-   **A helyrendszer-kiszolgáló ugyanazon a számítógépen telepített adatbázis-kiszolgáló:** Korlátozza az SQL Server memóriáját 50 – a rendelkezésre álló rendszermemória 80 százalékát.  

-   **A dedikált adatbázis-kiszolgáló (a helykiszolgálótól távol):** Korlátozza az SQL Server memóriáját 80 – 90 %-át a rendelkezésre álló rendszermemória.  

-   **A memória tartalék az egyes SQL Server-példányok puffer készlete:**  

    -   A központi adminisztrációs hely: Állítsa be a legalább 8 gigabájt (GB).  
    -   Az elsődleges hely: Állítsa be a legalább 8 gigabájt (GB).  
    -   A másodlagos helyek: Állítsa be a legalább 4 gigabájt (GB).  

**Az SQL beágyazott eseményindítói:**  
 [Az SQL beágyazott eseményindítói](http://go.microsoft.com/fwlink/?LinkId=528802) szolgáltatásnak engedélyezve kell lennie.  

 **SQL Server CLR-integráció**  
  A helyadatbázishoz be kell kapcsolnia a közös nyelvi futtatókörnyezetet (CLR) az SQL Serverhez. Ez automatikusan engedélyezve lesz a Configuration Manager telepítésekor. CLR kapcsolatos további információkért lásd: [Bevezetés az SQL Server CLR-integrációt](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx).  

##  <a name="bkmk_optional"></a> Az SQL Server választható konfigurációi  
 A következő konfigurációk beállíthatók minden egyes olyan adatbázis esetében, amely az SQL Server teljes telepítését használja.  

 **SQL Server szolgáltatás:**  
 Az SQL Server szolgáltatás beállítható úgy, hogy a következő használatával fusson:  

-   A **tartományi helyi felhasználói** fiók:  

    -   Ez az ajánlott eljárás, és előfordulhat, hogy manuálisan kell regisztrálni az egyszerű szolgáltatásnév (SPN) a fiókhoz.  

-   A **helyi rendszer** SQL Server rendszert futtató számítógép:  

    -   A helyi rendszerfiók használatával egyszerűbbé tehető a konfigurációs folyamat.  
    -   Ha a helyi rendszerfiókot használja, a Configuration Manager automatikusan regisztrálja az SQL Server szolgáltatás egyszerű Szolgáltatásnevét.  
    -   Vegye figyelembe, hogy a helyi rendszerfiók használata az SQL Server szolgáltatáshoz nem tartozik az SQL Server ajánlott eljárásai közé.  

Ha az SQL Servert futtató számítógép a helyi rendszer fiók használatával nem futtathatja az SQL Server szolgáltatást, konfigurálnia kell az egyszerű Szolgáltatásnevet az Active Directory tartományi szolgáltatásokban az SQL Server szolgáltatást futtató fiók. (A rendszer a fiókot használja, az egyszerű Szolgáltatásnevet automatikusan regisztrálja az Ön.)

A Helyadatbázis egyszerű szolgáltatásneveivel információkért lásd: [a Helyadatbázis-kiszolgáló kezelhető](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN) a a [a System Center Configuration Manager infrastruktúra](../../../core/servers/manage/modify-your-infrastructure.md) témakör.  

Az SQL Server szolgáltatás által használt fiók módosításával kapcsolatos információkért lásd: [hogyan: Az SQL Server (SQL Server Konfigurációkezelő) szolgáltatás Indítófiókjának módosítása](http://go.microsoft.com/fwlink/p/?LinkId=237661).  

**SQL Server Reporting Services:**  
SQL Server Reporting Services telepítése a jelentéskészítési szolgáltatási pont, amely lehetővé teszi a jelentések futtatásához szükség.  

> [!IMPORTANT]  
> A frissítés befejezése után az SQL Server egy korábbi verziójáról láthatja a következő hibával:  *A jelentés jelentéskészítő nem létezik*.    
> Ez a hiba megoldása érdekében újra kell telepítenie a jelentéskészítési szolgáltatási pont helyrendszerszerepkört.

**Az SQL Server portjai:**  
Kommunikáció az SQL Server adatbázismotor és a helyek közötti replikációhoz használja az alapértelmezett SQL Server portkonfigurációját, vagy megadhat egyéni portokat:  

-   **Helyek közötti kommunikáció** használja az SQL Server Service Broker, használó 4022-es TCP port alapértelmezés szerint.  
-   **Helyen belüli kommunikáció** között az SQL Server adatbázismotor és a különböző Configuration Manager helyrendszer-szerepkörök alapértelmezés szerint a TCP 1433-as port használata. A következő helyrendszerszerepkörök közvetlenül kommunikálnak az SQL Server adatbázissal:  

    -   Felügyeleti pont  
    -   Az SMS-szolgáltató számítógép  
    -   Jelentéskészítési szolgáltatási pont  
    -   Helykiszolgáló  

Ha az SQL Servert futtató számítógép üzemelteti az adatbázis egynél több helyről, minden adatbázisnak az SQL Server külön példányának kell használnia. Is minden példányt kell konfigurálni a portokat egyedi készletének használata.  

> [!WARNING]  
>  A Configuration Manager nem támogatja a dinamikus portokat. Az SQL Server megnevezett példányai alapértelmezés szerint dinamikus portokat használnak az adatbázismotorhoz való csatlakozáshoz, ezért amikor megnevezett példányt használ, kézzel kell konfigurálnia azt a statikus portot, amelyet a helyen belüli kommunikációhoz kíván használni.  

Ha az SQL Servert futtató számítógépen engedélyezve van a tűzfal, ellenőrizze, hogy az engedélyezi-e a telepítés során használt portokon keresztüli kommunikációt a hálózaton található bármely olyan számítógépek között, amelyek az SQL Serverrel kommunikálnak.  

Példa bemutatja, hogyan konfigurálhatja az SQL Server egy adott port használatára, lásd: [hogyan: A Server to Listen on a Specific TCP Port (SQL Server Configuration Manager) konfigurálása](http://go.microsoft.com/fwlink/p/?LinkID=226349) az SQL Server TechNet könyvtárban.  

## <a name="upgrade-options-for-sql-server"></a>SQL Server frissítési lehetőségei
Ha frissítenie kell az SQL Server verziója, az alábbi módszerek, az összetett könnyen ajánlott.
1. [Frissítse az SQL Server helyi](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (ajánlott).
2. SQL Server új verziójának telepítése egy új számítógépre, majd [használja a datbase move beállítást](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) a Configuration Manager telepítőjét a helykiszolgáló mutasson az új SQL Server.
3. Használjon [biztonsági mentési és helyreállítási](/sccm/protect/understand/backup-and-recovery).

