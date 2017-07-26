---
title: "Felügyeleti pont adatbázis-replikák |} Microsoft Docs"
description: "Adatbázis-replikák használatára a CPU-terhelésének a Helyadatbázis-kiszolgáló által a felügyeleti pontok csökkentése érdekében."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b06f781b-ab25-4d9a-b128-02cbd7cbcffe
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 130c053c9f2a1817dd85b1f3c01285aab19d59cb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="database-replicas-for-management-points-for-system-center-configuration-manager"></a>A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager elsődleges helyek adatbázis-replika használatával is csökkenthető a CPU-terhelésének a Helyadatbázis-kiszolgáló által a felügyeleti pontok, az ügyfelektől érkező kérelmek kiszolgálása során.  

-   Amikor egy felügyeleti pont adatbázis-replikát használ, az adott felügyeleti pont a helyadatbázis-kiszolgáló helyett azon SQL Server rendszert futtató számítógépről kér adatokat, amely az adatbázis-replikát tartalmazza.  

-   Ez csökkentheti a helyadatbázis-kiszolgáló processzorának feldolgozási terhelését azáltal, hogy mentesíti az ügyfelekkel kapcsolatos gyakori feldolgozási feladatok alól.  Az ügyfelek gyakori feldolgozási feladatainak egy példája az olyan helyek, ahol nagy mennyiségű ügyfél gyakori ügyfélházirend- kérést végez.  


##  <a name="bkmk_Prepare"></a> Adatbázis-replikák használatának előkészítése  
**Tudnivalók a felügyeleti pontok  adatbázis-replikáiról**  

-   A replika a helyadatbázis részleges másolata, amelyet a rendszer replikál egy különálló SQL Server-példányra:  

    -   Elsődleges helyek támogatják a dedikált adatbázis-replikát a hely valamennyi felügyeleti pontnál (a másodlagos helyek nem támogatják az adatbázis-replikákat)  

    -   Egy adatbázis-replikát több felügyeleti pont is használhat ugyanazon helyről  

    -   Egy SQL Server-kiszolgáló több, különböző felügyeleti pontok által használt adatbázis-replikát is tud kezelni, feltéve, hogy mindegyiket külön SQL Server-példány futtatja  

-   A replikák meghatározott ütemezés szerint szinkronizálják a helyadatbázis egy példányát a helyadatbázis-kiszolgáló által erre a célra közzétett adatokból.  

-   A felügyeleti pontok beállíthatók replikák használatára a felügyeleti pontok telepítésekor, vagy egy későbbi időpontban a korábban telepített felügyeleti pont újrakonfigurálásával az adatbázis-replika használatára.  

-   Rendszeresen figyelje a helyadatbázis-kiszolgálót és mindegyik adatbázisreplika-kiszolgálót, és ellenőrizze, hogy megtörténik-e közöttük a replikáció, valamint azt, hogy az adatbázisreplika-kiszolgáló teljesítménye elegendő-e a hely és a kiszolgálandó ügyfelek számára.  

**Adatbázis-replikákra vonatkozó előfeltételek:**  

-   **SQL Server-követelmények:**  

    -   Az adatbázis-replikát kezelő SQL Server-kiszolgálóra ugyanazok a követelmények vonatkoznak, mint a helyadatbázis-kiszolgálóra. A replikakiszolgálónak azonban nem kell az SQL Server ugyanazon verzióját vagy kiadását futtatnia, mint a helyadatbázis-kiszolgálónak, feltéve, hogy az SQL Server egy támogatott verziójáról és kiadásáról van szó. További információk: [A System Center Configuration Manager által támogatott SQL Server-verziók](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

    -   Az adatbázis-replikát tartalmazó számítógépen futó SQL Server szolgáltatásnak a **Rendszer** fiókot kell használnia.  

    -   A helyadatbázist kezelő és az adatbázisreplikát kezelő SQL Server-kiszolgálón egyaránt telepítve kell lennie az **SQL Server-replikáció** funkciónak.  

    -   A helyadatbázisnak **közzé kell tennie** az adatbázis-replikát, és mindegyik távoli adatbázisreplika-kiszolgálónak **elő kell fizetnie** a közzétett adatokra.  

    -   Mind a helyadatbázist kezelő, mind az adatbázis-replikát kezelő SQL Server-kiszolgálót a **Max Text Repl Size** beállítás 2 GB értékének támogatására kell konfigurálni. Az SQL Server 2012 rendszerben például a következő témakörben leírtak szerint konfigurálhatja ezt a beállítást: [A „max text repl size” kiszolgálói konfigurációs beállítás megadása](http://go.microsoft.com/fwlink/p/?LinkId=273960).  

-   **Önaláírt tanúsítvány:** Adatbázis-replika konfigurálásához hozzon létre egy önaláírt tanúsítványt az adatbázisreplika-kiszolgálón, és elérhetővé tenni ezt a tanúsítványt mindegyik adatbázisreplika-kiszolgálót használó felügyeleti ponthoz.  

    -   A tanúsítvány automatikusan elérhető az adatbázisreplika-kiszolgálón telepített felügyeleti pontok számára.  

    -   Azonban ahhoz, hogy a tanúsítvány a távoli felügyeleti pontok számára is elérhető legyen, exportálnia kell a tanúsítványt, és fel kell vennie azt a **megbízható személyek** tanúsítványtárolójába a távoli felügyeleti ponton.  

-   **Ügyfélértesítés:** Támogatja a ügyfélértesítést adatbázis-replikát használó felügyeleti ponttal, konfigurálnia kell a Helyadatbázis-kiszolgáló és az adatbázisreplika-kiszolgáló közötti kommunikáció a **SQL Server Service Broker**. Ehhez szükséges, hogy:  

    -   Mindkét adatbázisban konfigurálja a másik adatbázisra vonatkozó adatokat  

    -   Tanúsítványcserét végezzen a két adatbázis között a biztonságos kommunikáció érdekében  

**Az adatbázis-replikák használatára vonatkozó korlátozások:**  

-   Ha a hely adatbázis-replikák közzétételére van konfigurálva, a szokásos helyett az alábbi eljárásokat kell használni:  

    -   [Az adatbázis-replikát közzétevő helykiszolgáló eltávolítása](#BKMK_DBReplicaOps_Uninstall)  

    -   [Az adatbázis-replikát közzétevő helykiszolgáló-adatbázis áthelyezése](#BKMK_DBReplicaOps_Move)  

-   **Frissítés a System Center Configuration Manager**: Mielőtt frissít egy helyet a System Center 2012 Configuration Manager a System Center Configuration Manager, le kell tiltania az adatbázis-replikák beállítása felügyeleti pontokhoz.  A hely frissítése után konfigurálja újra a felügyeleti pontok adatbázis-replikáit.  

-   **Több replika egyetlen SQL-kiszolgálón:**  Ha egy adatbázisreplika-kiszolgálót több adatbázis-replika, a felügyeleti pontokhoz (minden egyes replikának egy másik példányon kell lennie) adja meg a kiszolgálón korábban konfigurált adatbázis-replikák által használt önaláírt tanúsítvány felülírásának elkerülése érdekében (a következő szakasz 4. lépését) módosított konfigurációs parancsfájlt kell használnia.  

##  <a name="BKMK_DBReplica_Config"></a> Adatbázis-replikák konfigurálása  
Adatbázis-replika konfigurálásához a következő lépések szükségesek:  

-   [1. lépés - A helyadatbázis-kiszolgáló konfigurálása az adatbázis-replika közzétételére](#BKMK_DBReplica_ConfigSiteDB)  

-   [2. lépés - Az adatbázisreplika-kiszolgáló beállítása](#BKMK_DBReplica_ConfigSrv)  

-   [3. lépés - A felügyeleti pontok beállítása az adatbázis-replika használatára](#BKMK_DBReplica_ConfigMP)  

-   [4. lépés - Önaláírt tanúsítvány konfigurálása az adatbázisreplika-kiszolgáló számára](#BKMK_DBReplica_Cert)  

-   [5. lépés - Az SQL Server Service Broker beállítása az adatbázisreplika-kiszolgálóhoz](#BKMK_DBreplica_SSB)  

###  <a name="BKMK_DBReplica_ConfigSiteDB"></a> 1. lépés - A helyadatbázis-kiszolgáló konfigurálása az adatbázis-replika közzétételére  
 A következő példa bemutatja, hogyan konfigurálható a Windows Server 2008 R2 rendszerű számítógépen működő helyadatbázis-kiszolgáló az adatbázis-replika közzétételére. Ha más verziójú operációs rendszert használ, tekintse át az adott operációs rendszer dokumentációját, és ha szükséges, helyesbítse megfelelően az alábbi művelet lépéseit.  

##### <a name="to-configure-the-site-database-server"></a>A helyadatbázis-kiszolgáló konfigurálása  

1.  A helyadatbázis-kiszolgálón állítsa be az SQL Server Agent automatikus indítását.  

2.  A Helyadatbázis-kiszolgálón hozzon létre egy helyi felhasználói csoportot nevű **ConfigMgr_MPReplicaAccess**. Az adott helyen használt összes adatbázisreplika-kiszolgáló számítógépfiókját fel kell vennie ebbe a csoportba annak engedélyezéséhez, hogy ezek az adatbázisreplika-kiszolgálók végrehajtsák a szinkronizálást a közzétett adatbázis-replikával.  

3.  A Helyadatbázis-kiszolgáló, adja meg a fájlmegosztás nevű **ConfigMgr_MPReplica**.  

4.  Adja meg a következő engedélyeket a **ConfigMgr_MPReplica** megosztása:  

    > [!NOTE]  
    >  Ha az SQL Server Agent nem a helyi rendszerfiókot használja, a következő lista RENDSZER fióknevét cserélje le az adott fióknévre.  

    -   **Megosztási engedélyek**:  

        -   RENDSZER: **Írási**  

        -   ConfigMgr_MPReplicaAccess: **Olvasás**  

    -   **NTFS-engedélyek**:  

        -   RENDSZER: **Teljes hozzáférés**  

        -   ConfigMgr_MPReplicaAccess: **Olvasási**, **olvasási & hajtható végre**, **mappa tartalmának listázása**  

5.  Az **SQL Server Management Studio** eszközzel csatlakozzon a helyadatbázishoz, és futtassa a következő tárolt eljárást lekérdezésként: **spCreateMPReplicaPublication**  

A tárolt eljárás befejeződésekor a helyadatbázis-kiszolgáló konfigurálva van az adatbázis-replika közzétételére.  

###  <a name="BKMK_DBReplica_ConfigSrv"></a> 2. lépés - Az adatbázisreplika-kiszolgáló beállítása  
Az adatbázisreplika-kiszolgáló egy olyan számítógép, amelyen az SQL Server rendszer fut, és amely tartalmaz egy adatbázis-replikát a felügyeleti pontok általi használatra. Az adatbázisreplika-kiszolgáló meghatározott ütemezés szerint szinkronizálja az adatbázispéldányát a helyadatbázis-kiszolgáló által közzétett adatbázis-replikával.  

Az adatbázisreplika-kiszolgálóra ugyanazok a követelmények vonatkoznak, mint a helyadatbázis-kiszolgálóra. Az adatbázisreplika-kiszolgálón azonban más kiadású vagy verziójú SQL Server is futtatható, mint a helyadatbázis-kiszolgálón. További információ az SQL Server támogatott verzióiról: [A System Center Configuration Manager által támogatott SQL Server-verziók](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

> [!IMPORTANT]  
>  Az adatbázis-replikát tartalmazó számítógépen futó SQL Server szolgáltatásnak a Rendszer fiókot kell használnia.  

A következő példa bemutatja, hogyan konfigurálható a Windows Server 2008 R2 rendszerű számítógépen működő adatbázisreplika-kiszolgáló. Ha más verziójú operációs rendszert használ, tekintse át az adott operációs rendszer dokumentációját, és ha szükséges, helyesbítse megfelelően az alábbi művelet lépéseit.  

##### <a name="to-configure-the-database-replica-server"></a>Az adatbázisreplika-kiszolgáló konfigurálása  

1.  Az adatbázisreplika-kiszolgálón állítsa be az SQL Server Agent automatikus indítását.  

2.  Az adatbázisreplika-kiszolgálón az **SQL Server Management Studio** használatával csatlakozzon a helyi kiszolgálóhoz, és az **Új előfizetés varázsló** elindításához lépjen a **Replikáció** mappába, kattintson a Helyi előfizetések elemre, majd válassza az **Új előfizetések**lehetőséget:  

    1.  A **Kiadvány** lap **Közzétevő** listáján jelölje ki az **SQL Server-közzétevő keresése**elemet, írja be a helyadatbázis-kiszolgáló nevét, és kattintson a **Csatlakozás**gombra.  

    2.  Válassza ki **ConfigMgr_MPReplica**, és kattintson a **következő**.  

    3.  Az a **terjesztési ügynök helye** lapon jelölje be **minden ügynök futtatása az Előfizetőjénél (lehívásos előfizetések)**, és kattintson a **következő**.  

    4.  Az **Előfizetők** lapon hajtsa végre az alábbi műveletek egyikét:  

        -   Az adatbázisreplika-kiszolgálón válasszon egy meglévő adatbázist, amelyet adatbázis-replikaként kíván használni, és kattintson az **OK**gombra.  

        -   Válassza az **Új adatbázis** lehetőséget, ha új adatbázist kíván létrehozni az adatbázis-replika számára. Az **Új adatbázis** lapon adja meg az adatbázis nevét, majd kattintson az **OK**gombra.  

    5.  A folytatáshoz kattintson a **Tovább** gombra.  

    6.  Az a **terjesztési ügynök biztonsága** lapján kattintson a Tulajdonságok gombra **(...)**  a párbeszédpanel előfizetői kapcsolat sorában mezőben, és adja meg a kapcsolat biztonsági beállításait.  

        > [!TIP]  
        >  A Tulajdonságok gombra **(...)** , a negyedik oszlopban található megjelenítő.  

        **Biztonsági beállítások:**  

        -   Adja meg a terjesztési ügynök folyamata (a folyamat fiókja) futtató fiókhoz:  

            -   Ha az SQL Server Agent helyi rendszerként fut, válassza ki a **fusson az SQL Server Agent szolgáltatásfiók használatával (ez nem ajánlott biztonsági szempontból ajánlott.)**  

            -   Ha az SQL Server Agent más fiók használatával fut, válassza a **Futtatás a következő Windows-fiók használatával**lehetőséget, majd adja meg a fiók beállításait. Megadhat Windows-fiókot vagy SQL Server-fiókot.  

            > [!IMPORTANT]  
            >  A terjesztési ügynököt futtató fióknak a lehívásos előfizetésre vonatkozó engedélyeket kell megadnia a közzétevőhöz. További információ a szükséges engedélyek beállításáról: [A terjesztési ügynök biztonsága](http://go.microsoft.com/fwlink/p/?LinkId=238463) témakör az SQL Server TechNet Library webhelyén.  

        -   A **Csatlakozás a terjesztőhöz**beállításnál válassza **A folyamatfiók megszemélyesítésével**lehetőséget.  

        -   A **Csatlakozás az előfizetőhöz**beállításnál válassza **A folyamatfiók megszemélyesítésével**lehetőséget.  

         A kapcsolat biztonsági beállításainak megadása után a beállítások mentéséhez kattintson az **OK** gombra, majd kattintson a **Tovább**gombra.  

    7.  A **Szinkronizálás ütemezése** lap **Ügynök ütemezése** listáján jelölje ki az **Ütemezés definiálása**elemet, majd válassza az **Új feladatütemezés**lehetőséget. A gyakoriságát, hogy mi történjen, **napi**, megismétlődik minden **5 perc**, az időtartamhoz pedig **nincs befejezési dátum**. Az ütemezés mentéséhez kattintson a **Tovább** gombra, majd kattintson ismét a **Tovább** gombra.  

    8.  Az a **Varázslóműveletek** lapon, jelölje be a jelölőnégyzetet **(s)-előfizetések létrehozása**, és kattintson a **következő**.  

    9. **A varázsló befejezése** lapon kattintson a **Befejezés**gombra, majd kattintson a **Bezárás** gombra a varázsló bezárásához.  

3.  Az Új előfizetés varázsló végrehajtása után az **SQL Server Management Studio** használatával rögtön csatlakozzon az adatbázisreplika-kiszolgáló adatbázisához, és a következő lekérdezés futtatásával engedélyezze a TRUSTWORTHY adatbázis-tulajdonságot:  `ALTER DATABASE <MP Replica Database Name> SET TRUSTWORTHY ON;`  

4.  Tekintse meg a szinkronizálási állapotot az előfizetés sikerességének ellenőrzéséhez:  

    -   Az előfizető számítógépen:  

        -   Az **SQL Server Management Studio**eszközben csatlakozzon az adatbázisreplika-kiszolgálóhoz, és bontsa ki a **Replikáció**elemet.  

        -   Bontsa ki a **helyi előfizetések**, kattintson a jobb gombbal a helyrendszer adatbázis kiadványra szóló előfizetés, és válassza **szinkronizálási állapot megtekintése**.  

    -   A közzétevő számítógépen:  

        -   A **SQL Server Management Studio**, a Helyadatbázis számítógépe csatlakozni, kattintson a jobb gombbal a **replikációs** mappára, és válassza **Replikációfigyelő**.  

5.  Engedélyezze a közös nyelvi futtatókörnyezet (CLR) integrációját az adatbázis-replika az **SQL Server Management Studio** használatával csatlakozzon az adatbázisreplika-kiszolgálón az adatbázis-replikát, és futtassa a következő tárolt eljárást lekérdezésként: **exec sp_configure 'clr enabled', 1. KONFIGURÁLJA ÚJRA FELÜLBÍRÁLÁSA**  

6.  Az adatbázisreplika-kiszolgálót használó valamennyi felügyeleti pontnál vegye fel az adott felügyeleti pont számítógépét a helyi **Rendszergazdák** csoportba az adott adatbázisreplika-kiszolgálón.  

    > [!TIP]  
    >  Ezt a lépést nem kell végrehajtani annál a felügyeleti pontnál, amely az adatbázisreplika-kiszolgálón fut.  

 Az adatbázis-replika ezzel készen áll a felügyeleti pont általi használatra.  

###  <a name="BKMK_DBReplica_ConfigMP"></a> 3. lépés - A felügyeleti pontok beállítása az adatbázis-replika használatára  
 Az elsődleges helyeken lévő felügyeleti pontokat beállíthatja az adatbázis-replikák használatára a felügyeleti pont szerepkör telepítésekor, vagy meglévő felügyeleti pontot is beállíthat az adatbázis-replikák használatára.  

 A felügyeleti pontokat a következő műveletek végrehajtásával állíthatja be az adatbázis-replikák használatára:  

-   **Egy új felügyeleti pont konfigurálása:** Az a **Felügyeletipont-adatbázis** , amellyel a felügyeleti pont telepítéséhez, válassza ki a varázsló **adatbázis-replikák használatára**, és adja meg az adatbázis-replikát üzemeltető számítógép teljes Tartománynevét. Ezután a **ConfigMgr-helyadatbázis neve**mezőben adja meg az adott számítógépen található adatbázis-replika nevét.  

-   **A korábban telepített felügyeleti pont konfigurálása**: A felügyeleti pont, válassza a Tulajdonságok lapjának megnyitásához a **Felügyeletipont-adatbázis** lapon jelölje be **adatbázis-replikák használatára**, és adja meg az adatbázis-replikát tartalmazó számítógép teljes Tartománynevét. Ezután a **ConfigMgr-helyadatbázis neve**mezőben adja meg az adott számítógépen található adatbázis-replika nevét.  

-   **Minden adatbázis-replikát használó felügyeleti pont esetében**, manuálisan kell hozzáadni a a felügyeletipont-kiszolgáló számítógépfiókjának a **db_datareader** az adatbázis-replika szerepkör.  

Azonkívül, hogy a felügyeleti pontot beállítja az adatbázisreplika-kiszolgáló használatára, a felügyeleti ponton az **IIS** funkciói között engedélyeznie kell a **Windows-hitelesítés** beállítást is:  

1.  Nyissa meg **az Internet Information Services (IIS) kezelője**.  

2.  Válassza ki a felügyeleti pont által használt webhelyet, és nyissa meg a **Hitelesítés**párbeszédpanelt.  

3.  Állítsa be **Windows-hitelesítés** való **engedélyezve**, majd zárja be **Internet Information Services (IIS) Manager**.  

###  <a name="BKMK_DBReplica_Cert"></a> 4. lépés - Önaláírt tanúsítvány konfigurálása az adatbázisreplika-kiszolgáló számára  
 Hozzon létre egy önaláírt tanúsítványt az adatbázisreplika-kiszolgálón kell, és elérhetővé tenni ezt a tanúsítványt mindegyik adatbázisreplika-kiszolgálót használó felügyeleti ponthoz.  

 A tanúsítvány automatikusan elérhető az adatbázisreplika-kiszolgálón telepített felügyeleti pontok számára. Ahhoz, hogy a tanúsítvány a távoli felügyeleti pontok számára is elérhető legyen, exportálnia kell a tanúsítványt, és fel kell vennie azt a megbízható személyek tanúsítványtárolójába a távoli felügyeleti ponton.  

 Az alábbi eljárásokkal egy példa az önaláírt tanúsítvány konfigurálása a Windows Server 2008 R2 rendszerű számítógépen az adatbázisreplika-kiszolgálón. Ha más verziójú operációs rendszert használ, tekintse át az adott operációs rendszer dokumentációját, és ha szükséges, helyesbítse megfelelően az alábbi műveletek lépéseit.  

##### <a name="to-configure-a-self-signed-certificate-for-the-database-replica-server"></a>Az adatbázisreplika-kiszolgáló önaláírt tanúsítvány konfigurálása  

1.  Az adatbázisreplika-kiszolgálón, nyisson meg egy PowerShell-parancssort rendszergazdai jogosultságokkal, és futtassa a következő parancsot: **set-executionpolicy UnRestricted**  

2.  Készítsen másolatot a következő PowerShell-parancsfájlról, és mentse fájlba a **CreateMPReplicaCert.ps1**név megadásával. A fájl másolatát helyezze el az adatbázisreplika-kiszolgáló rendszerpartíciójának gyökérmappájában.  

    > [!IMPORTANT]  
    >  Ha egynél több adatbázis-replikát konfigurál egy SQL Server-kiszolgálón, minden egyes későbbiekben konfigurált replikához a parancsfájl módosított változatát kell használnia ezen eljáráshoz. Lásd:  [Kiegészítő parancsfájl további adatbázis-replikákhoz egy SQL Server-kiszolgálón](#bkmk_supscript)  

    ```  
    # Script for creating a self-signed certificate for the local machine and configuring SQL Server to use it.  

    Param($SQLInstance)  

    $ConfigMgrCertFriendlyName = "ConfigMgr SQL Server Identification Certificate"  

    # Get local computer name  
    $computerName = "$env:computername"  

    # Get the sql server name  
    #$key="HKLM:\SOFTWARE\Microsoft\SMS\MP"  
    #$value="SQL Server Name"  
    #$sqlServerName= (Get-ItemProperty $key).$value  
    #$dbValue="Database Name"  
    #$sqlInstance_DB_Name= (Get-ItemProperty $key).$dbValue  

    $sqlServerName = [System.Net.Dns]::GetHostByName("localhost").HostName   
    $sqlInstanceName = "MSSQLSERVER"  
    $SQLServiceName = "MSSQLSERVER"  

    if ($SQLInstance -ne $Null)  
    {  
        $sqlInstanceName = $SQLInstance  
        $SQLServiceName = "MSSQL$" + $SQLInstance  
    }  

    # Delete existing cert if one exists  
    function Get-Certificate($storename, $storelocation)  
    {   
        $store=new-object System.Security.Cryptography.X509Certificates.X509Store($storename,$storelocation)   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Certificates   
    }   

    $cert = Get-Certificate "My" "LocalMachine" | ?{$_.FriendlyName -eq $ConfigMgrCertFriendlyName}   
    if($cert -is [Object])  
    {  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("My","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()  

        # Remove this cert from Trusted People too...  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("TrustedPeople","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()      
    }  

    # Create the new cert  
    $name = new-object -com "X509Enrollment.CX500DistinguishedName.1"  
    $name.Encode("CN=" + $sqlServerName, 0)  

    $key = new-object -com "X509Enrollment.CX509PrivateKey.1"  
    $key.ProviderName = "Microsoft RSA SChannel Cryptographic Provider"  
    $key.KeySpec = 1  
    $key.Length = 1024  
    $key.SecurityDescriptor = "D:PAI(A;;0xd01f01ff;;;SY)(A;;0xd01f01ff;;;BA)(A;;0x80120089;;;NS)"  
    $key.MachineContext = 1  
    $key.Create()  

    $serverauthoid = new-object -com "X509Enrollment.CObjectId.1"  
    $serverauthoid.InitializeFromValue("1.3.6.1.5.5.7.3.1")  
    $ekuoids = new-object -com "X509Enrollment.CObjectIds.1"  
    $ekuoids.add($serverauthoid)  
    $ekuext = new-object -com "X509Enrollment.CX509ExtensionEnhancedKeyUsage.1"  
    $ekuext.InitializeEncode($ekuoids)  

    $cert = new-object -com "X509Enrollment.CX509CertificateRequestCertificate.1"  
    $cert.InitializeFromPrivateKey(2, $key, "")  
    $cert.Subject = $name  
    $cert.Issuer = $cert.Subject  
    $cert.NotBefore = get-date  
    $cert.NotAfter = $cert.NotBefore.AddDays(3650)  
    $cert.X509Extensions.Add($ekuext)  
    $cert.Encode()  

    $enrollment = new-object -com "X509Enrollment.CX509Enrollment.1"  
    $enrollment.InitializeFromRequest($cert)  
    $enrollment.CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"  
    $certdata = $enrollment.CreateRequest(0x1)  
    $enrollment.InstallResponse(0x2, $certdata, 0x1, "")  

    # Add this cert to the trusted peoples store  
    [Byte[]]$bytes = [System.Convert]::FromBase64String($certdata)  

    $trustedPeople = new-object System.Security.Cryptography.X509certificates.X509Store "TrustedPeople", "LocalMachine"  
    $trustedPeople.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)  
    $trustedPeople.Add([Security.Cryptography.X509Certificates.X509Certificate2]$bytes)  
    $trustedPeople.Close()  

    # Get thumbprint from cert  
    $sha = new-object System.Security.Cryptography.SHA1CryptoServiceProvider  
    $certHash = $sha.ComputeHash($bytes)  
    $certHashCharArray = "";  
    $certThumbprint = "";  

    # Format the bytes into a hexadecimal string  
    foreach($byte in $certHash)  
    {  
        $temp = ($byte | % {"{0:x}" -f $_}) -join ""  
        $temp = ($temp | % {"{0,2}" -f $_})  
        $certHashCharArray = $certHashCharArray+ $temp;  
    }  
    $certHashCharArray = $certHashCharArray.Replace(' ', '0');  

    # SQL needs the thumbprint in lower case  
    foreach($char in $certHashCharArray)  
    {  
        [System.String]$myString = $char;  
        $certThumbprint = $certThumbprint + $myString.ToLower();  
    }  

    # Configure SQL to use this cert  
    $path = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\Instance Names\SQL"  
    $subKey = (Get-ItemProperty $path).$sqlInstanceName  
    $realPath = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\" + $subKey + "\MSSQLServer\SuperSocketNetLib"  
    $certKeyName = "Certificate"  
    Set-ItemProperty -path $realPath -name $certKeyName -Type string -Value $certThumbprint  

    # restart sql service  
    Restart-Service $SQLServiceName -Force  
    ```  

3.  Az adatbázisreplika-kiszolgálón futtassa az SQL Server konfigurációjára vonatkozó következő parancsot:  

    -   Az SQL Server alapértelmezett példánya: Kattintson jobb gombbal a fájlra **CreateMPReplicaCert.ps1** válassza **Futtatás a PowerShell szolgáltatással**. A parancsfájl futtatása, ha az önaláírt tanúsítványt hoz létre, és beállítja az SQL Server, a tanúsítvány használatára.  

    -   Az SQL Server megnevezett példánya: Futtassa a parancsot a PowerShell segítségével **%path%\CreateMPReplicaCert.ps1 xxxxxx** ahol **xxxxxx** az SQL Server-példány neve.  

    -   Miután a parancsfájl lefutott, ellenőrizze, hogy fut-e az SQL Server Agent. Ha az SQL Server Agent nem fut, indítsa újra.  

##### <a name="to-configure-remote-management-points-to-use-the-self-signed-certificate-of-the-database-replica-server"></a>Távoli felügyeleti pontok általi használatra az önaláírt tanúsítványt az adatbázisreplika-kiszolgáló konfigurálása  

1.  Hajtsa végre a következő lépéseket az adatbázisreplika-kiszolgálón a kiszolgáló önaláírt tanúsítványának exportálásához:  

    1.  Kattintson a **Start**gombra, a **Futtatás**pontra, majd írja be az **mmc.exe**parancsot. Az üres konzolban kattintson a **Fájl**pontra, majd a **Beépülő modul hozzáadása/eltávolítása**elemre.  

    2.  A **Beépülő modul hozzáadása/eltávolítása** párbeszédpanelen válassza ki a **Tanúsítványok** lehetőséget az **Elérhető beépülő modulok**listájából, majd kattintson a **Hozzáadás**gombra.  

    3.  A **Tanúsítványkezelő beépülő modul** párbeszédpanelen válassza ki a **Számítógépfiók**lehetőséget, majd kattintson a **Tovább**gombra.  

    4.  A **Számítógép kiválasztása** párbeszédpanelen győződjön meg arról, hogy a **Helyi számítógép (az a számítógép, amelyen ez a konzol fut)** be van jelölve, majd kattintson a **Befejezés**elemre.  

    5.  Kattintson a **Beépülő modul hozzáadása/eltávolítása** párbeszédpanelen az **OK**gombra.  

    6.  A konzolon bontsa ki **tanúsítványok (helyi számítógép)**, bontsa ki a **személyes**, és válassza ki **tanúsítványok**.  

    7.  Kattintson a jobb gombbal a rövid nevű tanúsítványra **ConfigMgr SQL Server Identification Certificate**, kattintson a **feladataival**, majd válassza ki **exportálása**.  

    8.  Az alapértelmezett beállításokat használva fejezze be a **Tanúsítványexportáló varázslót** , és mentse el a tanúsítványt a **.cer** fájlnévkiterjesztéssel.  

2.  Hajtsa végre az alábbi lépéseket a felügyeleti pont számítógépén az önaláírt tanúsítványt az adatbázisreplika-kiszolgáló hozzáadása a felügyeleti pont a megbízható személyek tanúsítványtárolójához:  

    1.  A fenti 1.a–1.e lépéseket megismételve konfigurálhatja a **tanúsítvány** MMC beépülő a felügyeleti pont számítógépén.  

    2.  A konzolban bontsa ki a **Tanúsítványok (Helyi számítógép)**, **Megbízható személyek**csomópontot, az egér jobb gombjával kattintson a **Tanúsítványok**elemre, és válassza **Az összes feladat**, majd az **Importálás** lehetőséget a **Tanúsítványimportáló varázsló**elindításához.  

    3.  Az **Importálandó fájl** lapon jelölje ki az 1.h lépésben mentett tanúsítványt, és kattintson a **Tovább**gombra.  

    4.  A **Tanúsítványtároló** lapon jelölje be a **Minden tanúsítvány tárolása ebben a tárolóban**választógombot, a **Tanúsítványtároló** beállításban adja meg a **Megbízható személyek**lehetőséget, és kattintson a **Tovább**gombra.  

    5.  Kattintson a **Befejezés** gombra a varázsló bezárásához és a tanúsítvány felügyeleti ponton történő konfigurálásának befejezéséhez.  

###  <a name="BKMK_DBreplica_SSB"></a> 5. lépés - Az SQL Server Service Broker beállítása az adatbázisreplika-kiszolgálóhoz  
Ha ügyfélértesítést szeretne biztosítani egy adatbázis-replikát használó felügyeleti ponttal, konfigurálnia kell a helyadatbázis-kiszolgáló és az adatbázisreplika-kiszolgáló közötti kommunikációt az SQL Server Service Broker számára. Ehhez mindkét adatbázishoz be kell állítania a másik adatbázis adatait, illetve tanúsítványt kell cserélnie a két adatbázis között a biztonságos kommunikáció érdekében.  

> [!NOTE]  
>  Az alábbi eljárás elvégzése előtt az adatbázisreplika-kiszolgálónak sikeresen be kell fejeznie a kezdeti szinkronizálást a helyadatbázis-kiszolgálóval.  

 Az eljárással nem módosítja a Service Broker azon portját, amely konfigurálva van az SQL Serverben az adatbázisreplika-kiszolgálóhoz és a helyadatbázis-kiszolgálóhoz. Csak azt konfigurálja mindkét adatbázishoz, hogy a megfelelő Service Broker-porton át kommunikáljon a másik adatbázissal.  

 Az alábbi eljárással konfigurálhatja a Service Brokert a helyadatbázis-kiszolgálóhoz és az adatbázisreplika-kiszolgálóhoz.  

##### <a name="to-configure-the-service-broker-for-a-database-replica"></a>A Service Broker konfigurálása egy adatbázis-replikához  

1.  Használjon **SQL Server Management Studio** használatával csatlakozzon az adatbázisreplika-kiszolgáló adatbázisához, és a következő lekérdezés futtatásával engedélyezze a Service Brokert az adatbázisreplika-kiszolgálón: **ALTER DATABASE &lt;replika-adatbázis neve\> SET ENABLE_BROKER, HONOR_BROKER_PRIORITY a WITH ROLLBACK IMMEDIATE**  

2.  Ezután az adatbázisreplika-kiszolgálón konfigurálja a Service Brokert az ügyfélértesítésre, és exportálja a Service Broker-tanúsítványt. Ehhez futtasson egy olyan SQL Server tárolt eljárást, amely egyetlen lépésben konfigurálja a Service Brokert és exportálja a tanúsítványt. A tárolt eljárás futtatásakor meg kell adnia az adatbázisreplika-kiszolgáló teljes tartománynevét, az adatbázis-replika nevét, illetve a tanúsítványfájl exportálási helyét.  

     Futtassa a következő lekérdezés futtatásával konfigurálhatja a szükséges adatokat az adatbázisreplika-kiszolgálón, és az adatbázisreplika-kiszolgáló tanúsítványának exportálásához: **EXEC sp_BgbConfigSSBForReplicaDB '&lt;replika SQL Server teljes Tartományneve\>','&lt;replika-adatbázis neve\>','&lt;tanúsítványmásolat fájlelérési útja\>"**  

    > [!NOTE]  
    >  Ha az adatbázisreplika-kiszolgáló nem az SQL Server alapértelmezett példányán van, akkor ebben a lépésben meg kell adnia a példány nevét is a replika-adatbázis nevén kívül. Ehhez cserélje le a **&lt;Replika-adatbázis neve\>** elemet a **&lt;Példánynév\\Replika-adatbázis neve\>** elemre.  

     Miután exportálta a tanúsítványt az adatbázisreplika-kiszolgálóról, helyezze el a tanúsítvány másolatát az elsődleges hely adatbázis-kiszolgálóján.  

3.  Az **SQL Server Management Studio** segítségével csatlakozzon az elsődleges helyadatbázishoz. Miután csatlakozott az elsődleges helyadatbázishoz, egy lekérdezés futtatásával importálja a tanúsítványt, illetve adja meg az adatbázisreplika-kiszolgálón használt Service Broker-portot, az adatbázisreplika-kiszolgáló teljes tartománynevét és az adatbázis-replika nevét. Ezzel az elsődleges hely adatbázisát arra konfigurálja, hogy a Service Broker használatával kommunikáljon az adatbázisreplika-kiszolgáló adatbázisával.  

     Futtassa a következő lekérdezés futtatásával importálja a tanúsítványt az adatbázisreplika-kiszolgálóról és adhatja meg a szükséges adatokat: **EXEC sp_BgbConfigSSBForRemoteService 'REPLICA', '&lt;SQL Service Broker-Port\>','&lt;tanúsítvány fájlelérési útja\>','&lt;replika SQL Server teljes Tartományneve\>','&lt;replika-adatbázis neve\>"**  

    > [!NOTE]  
    >  Ha az adatbázisreplika-kiszolgáló nem az SQL Server alapértelmezett példányán van, akkor ebben a lépésben meg kell adnia a példány nevét is a replika-adatbázis nevén kívül. Ehhez cserélje le a  **&lt;replika-adatbázis neve\>**  rendelkező **\Instance neve\\replika-adatbázis neve\>**.  

4.  Ezután a Helyadatbázis-kiszolgálón, futtassa a következő parancsot a Helyadatbázis-kiszolgáló tanúsítványának exportálásához: **EXEC sp_BgbCreateAndBackupSQLCert '&lt;tanúsítványmásolat fájlelérési útja\>"**  

     Miután exportálta a tanúsítványt a helyadatbázis-kiszolgálóról, helyezze el a tanúsítvány másolatát az adatbázisreplika-kiszolgálón.  

5.  Az **SQL Server Management Studio** segítségével csatlakozzon az adatbázisreplika-kiszolgáló adatbázisához. Miután csatlakozott az adatbázisreplika-kiszolgáló adatbázisához, egy lekérdezés futtatásával importálja a tanúsítványt, illetve adja meg az elsődleges hely helykódját és a helyadatbázis-kiszolgálón használt Service Broker-portot. Ezzel az adatbázisreplika-kiszolgálót arra konfigurálja, hogy a Service Broker használatával kommunikáljon az elsődleges hely adatbázisával.  

     Futtassa a következő lekérdezés futtatásával importálja a tanúsítványt a Helyadatbázis-kiszolgálóról: **EXEC sp_BgbConfigSSBForRemoteService '&lt;Helykód\>','&lt;SQL Service Broker-Port\>','&lt;tanúsítvány fájlelérési útja\>"**  

 Néhány perccel a helyadatbázis és az adatbázis-replika konfigurálásának befejezését követően az elsődleges helyen működő értesítéskezelő beállítja az ügyfélértesítésekhez szükséges Service Broker-beszélgetést az elsődleges hely adatbázisa és az adatbázis-replika között.  

###  <a name="bkmk_supscript"></a> Kiegészítő parancsfájl további adatbázis-replikákhoz egy SQL Server-kiszolgálón  
 4. lépésben szereplő parancsfájlt konfigurálása az adatbázisreplika-kiszolgáló egy önaláírt tanúsítványt, amely már a továbbiakban is használni szeretné az adatbázis-replikát SQL-kiszolgálón való használatakor, az eredeti parancsfájl módosított változatát kell használnia. A következő módosítások megakadályozzák, hogy a parancsfájl töröljön egy létező tanúsítványt a kiszolgálón, és a további tanúsítványokat egyedi rövid névvel hozza létre.  Az alábbiak szerint módosítsa az eredeti parancsfájlt:  

-   Megjegyzéssé (tiltsa le a futását) között a parancsfájlban soronként **# meglévő tanúsítvány törlése, ha van ilyen** és **# létrehozása az új tanúsítvány**. Ehhez minden szóban forgó sor elejére írjon egy  **#**  karaktert.  

-   Minden további adatbázis-replika esetében, amelyet ezen parancsfájl segítségével konfigurál, frissítse a tanúsítvány rövid nevét.  Ehhez szerkessze a **$enrollment. CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"** , és cserélje le **ConfigMgr SQL Server Identification Certificate** új néven, például a **ConfigMgr SQL Server-azonosítási Certificate1**.  

##  <a name="BKMK_DBReplicaOps"></a> Adatbázisreplika-konfigurációk kezelése  
 Ha egy helyen adatbázis-replikát használ, az alábbi részekben olvasható információk segítséget nyújtanak az adatbázis-replikák eltávolításához, az adatbázis-replikát használó helyek eltávolításához vagy a helyadatbázis áthelyezéséhez az SQL Server egy újonnan telepített példányába. Ha az alábbi információk felhasználásával közzétételeket töröl, a tranzakciós replikáció törlését leíró azon útmutatást kövesse, amelyik megfelel az adatbázis-replikához használt SQL Server verziójának. Például ha az SQL Server 2008 R2 használata esetén tekintse meg [hogyan: Delete a Publication (replikálás Transact-SQL Programming)](http://go.microsoft.com/fwlink/p/?LinkId=273934).  

> [!NOTE]  
>  Miután visszaállított egy adatbázis-replikákhoz létrehozott helyadatbázist, ahhoz, hogy használhatók legyenek az adatbázis-replikák, újra kell konfigurálni mindegyiket, újból létrehozva a közzétételeket és az előfizetéseket.  

###  <a name="BKMK_UninstallDbReplica"></a> Adatbázis-replika eltávolítása  
 Ha adatbázis-replikát használ egy felügyeleti ponthoz, előfordulhat, hogy egy időre el kell távolítania az adatbázis-replikát, majd újból konfigurálnia kell a használathoz. Adatbázis-replikák például el kell távolítania a Configuration Manager-hely új szervizcsomagra való frissítés előtt. A hely frissítését követően visszaállíthatja használatra az adatbázis-replikát.  

 Az adatbázis-replikákat az alábbi eljárással távolíthatja el.  

1.  Az a **felügyeleti** a Configuration Manager konzol munkaterületén bontsa ki a **Helykonfiguráció**, majd jelölje be **kiszolgálók és Helyrendszerszerepkörök**, majd a részleteket tartalmazó ablaktáblán válassza ki a távolítsa el az adatbázis-replikát használó felügyeleti pontot üzemeltető helyrendszer-kiszolgáló.  

2.  A **Helyrendszerszerepkörök** ablaktáblán kattintson a jobb gombbal a **Felügyeleti pont** lehetőséget, és válassza a **Tulajdonságok**parancsot.  

3.  A **Felügyeletipont-adatbázis** lapon jelölje be **A helyadatbázis használata** választógombot ahhoz, hogy a felügyeleti pontot a helyadatbázis használatára konfigurálja az adatbázis-replika használata helyett. Ezután kattintson az **OK** gombra a konfiguráció mentéséhez.  

4.  A következő lépésként az **SQL Server Management Studio** segítségével hajtsa végre az alábbi műveleteket:  

    -   Törölje az adatbázis-replikához tartozó közzétételt a helyrendszer adatbázisából.  

    -   Törölje az adatbázis-replikához tartozó előfizetést az adatbázisreplika-kiszolgálóról.  

    -   Törölje a replika-adatbázist az adatbázisreplika-kiszolgálóról.  

    -   Tiltsa le a közzétételt és a terjesztést a helyadatbázis-kiszolgálón. Közzététel és a terjesztés letiltásához kattintson a jobb gombbal a replikáció mappára, és kattintson a **közzététel és terjesztés letiltása**.  

5.  A közzététel, az előfizetés és a replika-adatbázis törlésével, valamint a helyadatbázison való közzététel letiltásával elvégezte az adatbázis-replika eltávolítását.  

###  <a name="BKMK_DBReplicaOps_Uninstall"></a> Az adatbázis-replikát közzétevő helykiszolgáló eltávolítása  
 Mielőtt eltávolít egy adatbázis-replikát közzétevő helyet, az alábbi lépésekkel szüntesse meg a közzétételt és minden előfizetést.  

1.  Az **SQL Server Management Studio** segítségével törölje az adatbázis-replika közzétételét a helykiszolgáló adatbázisából.  

2.  Az **SQL Server Management Studio** eszközben törölje az adatbázis-replikára való előfizetést mindegyik távoli SQL Server-kiszolgálóról, amely a hely adatbázis-replikáját tárolja.  

3.  Távolítsa el a helyet.  

###  <a name="BKMK_DBReplicaOps_Move"></a> Az adatbázis-replikát közzétevő helykiszolgáló-adatbázis áthelyezése  
 A helyadatbázist a következő lépésekkel helyezheti át egy új számítógépre:  

1.  Az **SQL Server Management Studio** segítségével törölje az adatbázis-replika közzétételét a helykiszolgáló adatbázisából.  

2.  Az **SQL Server Management Studio** eszközben törölje az adatbázis-replikára való előfizetést a hely mindegyik adatbázisreplika-kiszolgálójáról.  

3.  Helyezze át az adatbázist az SQL Servert futtató új számítógépre. További információt [A System Center Configuration Manager infrastruktúrájának módosítása](../../../../core/servers/manage/modify-your-infrastructure.md) című témakör [A helyadatbázis konfigurációjának módosítása](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_dbconfig) című szakaszában talál.  

4.  Hozza létre újra az adatbázis-replika közzétételét a helyadatbázis-kiszolgálón. További információkért lásd jelen témakör [1. lépés - A helyadatbázis-kiszolgáló konfigurálása az adatbázis-replika közzétételére](#BKMK_DBReplica_ConfigSiteDB) című szakaszát.  

5.  Hozza létre újra az adatbázis-replikára vonatkozó előfizetéseket mindegyik adatbázisreplika-kiszolgálón. További információkért lásd jelen témakör [2. lépés - Az adatbázisreplika-kiszolgáló beállítása](#BKMK_DBReplica_ConfigSrv) című szakaszát.  

