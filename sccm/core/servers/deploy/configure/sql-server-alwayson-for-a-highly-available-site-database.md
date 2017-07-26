---
title: Az SQL Server AlwaysOn |} Microsoft Docs
ms.custom: na
ms.date: 1/4/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: aaaab003ddd22f18160d4be63cfeab3a7e7f6b03
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="sql-server-alwayson-for-a-highly-available-site-database-for-system-center-configuration-manager"></a>Magas rendelkezésre állású helyadatbázis biztosítása a System Center Configuration Manager számára az SQL Server AlwaysOn megoldással

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 A System Center Configuration Manager 1602-es verziójától kezdve használhatja az SQL Server [AlwaysOn rendelkezésre állási csoportok](https://msdn.microsoft.com/library/hh510230\(v=sql.120\).aspx) elsődleges helyeken és a magas rendelkezésre állású és vész-helyreállítási megoldásként a központi adminisztrációs helyen a Helyadatbázis futtatására. A rendelkezésre állási csoport üzemeltethető a helyszínen vagy a Microsoft Azure-ban.  

 Ha a Microsoft Azure-t használja a rendelkezésre állási csoport üzemeltetéséhez, tovább növelheti a helyadatbázis rendelkezésre állását az SQL Server AlwaysOn rendelkezésre állási csoportok és az Azure rendelkezésre állási készletek használatával. További információ az Azure rendelkezésre állási készletekről: [Manage the availability of virtual machines](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)(Virtuális gépek rendelkezésre állásának kezelése).  

 A Configuration Manager támogatja egy SQL rendelkezésre állási csoport, amely egy belső vagy külső terheléselosztó mögött a Helyadatbázis üzemeltetéséhez. Tűzfalkivételek minden replikán, másrészt szüksége lesz a terheléselosztási szabályok a következő portokat:
  - SQL TCP protokollon keresztül: TCP 1433
  - SQL Server Service Broker: 4022-ES TCP
  - Kiszolgálói üzenetblokk (SMB): TCP 445
  - RPC végpontleképező: TCP 135


A rendelkezésre állási csoportok a következő forgatókönyveket támogatják:  

-   Helyadatbázis áthelyezése a rendelkezésre állási csoport alapértelmezett példányába  

-   Replikatagok hozzáadása vagy eltávolítása helyadatbázist üzemeltető rendelkezésre állási csoportokból  

-   Helyadatbázis áthelyezése rendelkezésre állási csoportból az önálló SQL Server alapértelmezett vagy megnevezett példányába  

> [!Important]  
> Használatakor a Microsoft Intune és a Configuration Managerben hibrid konfigurációban, vagy egy rendelkezésre állási csoport eseményindítók a Helyadatbázis az áthelyezés az adatok a felhőben újraszinkronizálását. Ez nem lehetséges. 



> [!NOTE]  
>  A rendelkezésre állási csoportok sikeres beállításához és használatához az SQL Servernek és az SQL Server rendelkezési állási csoportjainak alapos ismerete szükséges. A témakörben szereplő eljárások a System Center Configuration Manager további dokumentáción és eljárásokon az SQL Server dokumentációs könyvtárában található támaszkodnak.  

 **Ismert problémák az AlwaysOn rendelkezésre állási csoportok és a Configuration Manager együttes használata esetén:**  

-   **A replikakiszolgálókon azonos fájlelérési útvonalnak kell érvényben lennie, amikor beállítja a Configuration Managert a rendelkezésre állási csoport használatára:**  

    -   Átirányítani a helyet az adatbázis egy rendelkezésre állási csoportban a Configuration Manager telepítő futtatása során a csoport minden másodlagos replikakiszolgálón rendelkeznie kell egy fájl elérési útját, amely azonos az aktuális elsődleges replikán a hely adatbázis-fájlok tárolására használt fájlelérési út. Ha a másodlagos replikákon nem ez az útvonal van beállítva, a telepítő nem tudja hozzáadni a rendelkezésre állási csoportok példányait új helyként a helyadatbázishoz.  

         Ezenfelül a helyi SQL Server szolgáltatásfiókjának minden másodlagos replikakiszolgálón **teljes hozzáférés** engedéllyel kell rendelkeznie ehhez a mappához.  

         A másodlagos replikakiszolgálóknál erre a fájlelérési útra csak akkor van szükség, amikor a telepítő használatával megadja az adatbázispéldányt a rendelkezésre állási csoportban.  Miután a telepítő befejezte a rendelkezésre állási csoportban lévő helyadatbázis használatára való áttérést, törölheti a nem használt elérési utat a másodlagos replikakiszolgálókból.  

         Vegyük példaként a következő esetet:  

        -   A felhasználó létrehoz egy három SQL Servert használ rendelkezésre állási csoportot.  

        -   Az elsődleges replikakiszolgálón az SQL Server 2014 újonnan telepített változata fut.  Az adatbázis .mdf- és .ldf-fájljainak helye: C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA  

        -   Mind a másodlagos replika kiszolgálók az SQL Server 2014 korábbi verzióról frissített, és tartsa meg a fájl eredeti elérési útjának adatbázis fájlok tárolásának képessége: C:\Program Files\Microsoft SQL Server\MSSQL10. MSSQLSERVER\MSSQL\DATA  

        -   Mielőtt megkísérli a hely adatbázisának áthelyezése a rendelkezésre állási csoporthoz, minden másodlagos replikakiszolgálón kell létrehoznia a következő fájl elérési útja még akkor is, ha a másodlagos replikákon nem fogja használni a fájl helye:  C:\Program Files\Microsoft SQL Server\MSSQL12. (Ez az az elérési út, az elsődleges replikán a használatban lévő duplikált) MSSQLSERVER\MSSQL\DATA  

        -   Ezt követően teljes hozzáférési engedélyt kell adnia a másodlagos replikákon futó SQL Server szolgáltatásfióknak a kiszolgálókon újonnan létrehozott mappához.  

        -   Most sikeresen futtathatja a Configuration Manager telepítő állítsa be a rendelkezésre állási csoportban található Helyadatbázis használatára  

-   **Ha a telepítő lefut, és beállítja, hogy a helyadatbázis a rendelkezésre állási csoportot használja, a ConfigMgrSetup.log fájlban az alábbihoz hasonló hibák jelenhetnek meg:**  

    -   HIBA: SQL Server-hiba: [25000] [3906] [Microsoft] [SQL Server natív ügyfél 11.0] [SQL Server] nem sikerült frissíteni a "CM_AAA" adatbázisban, mert az adatbázis csak olvasható.   Configuration Manager telepítő, 2016.01.21 16:54:59  7344 (0x1CB0)  

     Ezek a hibák akkor kerülnek be a naplóba, amikor a telepítő megpróbálja feldolgozni az adatbázis-szerepköröket a rendelkezésre állási csoport másodlagos replikáin. Ezek a hibák nyugodtan figyelmen kívül hagyhatók.
- **További rendelkezésre állási csoportok üzemeltető SQL-kiszolgáló:**

  1610, használja a rendelkezésre állási csoport és majd futtatásakor a Configuration Manager telepítő vagy egy adott frissítés telepítéséhez a Configuration Manager, verzió telepítése előtt minden egyes replikához, minden további rendelkezésre állási csoportban, amelyen a Configuration Manager rendelkezésre állási csoport SQL-kiszolgálón az alábbi beállításokkal kell rendelkeznie:
    - **kézi feladatátvételt**
    - **az összes csak olvasható kapcsolat engedélyezését**


##  <a name="bkmk_BnR"></a> A biztonsági mentés és a helyreállítás eltérései az SQL Server AlwaysOn rendelkezésre állási csoport használata esetén  
 **Biztonsági mentés:**  

 Ha egy Helyadatbázis egy rendelkezésre állási csoportban fut, akkor továbbra is futtassa a beépített **biztonsági tartalék telephelyről** karbantartási feladat közös Configuration Manager-beállítások és fájlok biztonsági mentését, de tervezi, hogy nem a. MDF vagy. A biztonsági mentéssel létrehozott LDF-fájlokat. Ehelyett tervezze meg a helyadatbázis közvetlen biztonsági másolatainak készítését az SQL Server használatával.  

 Ezenkívül meg kell terveznie a helyadatbázis tranzakciónaplójának figyelését és méretének karbantartását is, mivel az adatbázis helyreállítási modellje a „Teljes” értékre van állítva.  A teljes helyreállítási modell esetében a tranzakciók nincsenek megerősítve, amíg meg nem történik az adatbázis vagy a tranzakciónapló teljes biztonsági mentése. A teljes helyreállítási modell követelménynek számít a Helyadatbázis egy rendelkezésre állási csoport és a Configuration Managerrel való használatra csoport konfigurálásakor. Az SQL Server biztonsági mentésével és visszaállításával kapcsolatos további információkat a [Back Up and Restore of SQL Server Databases](https://msdn.microsoft.com/library/ms187048\(v=sql.120\).aspx) (SQL Server-adatbázisok biztonsági mentése és visszaállítása) című cikkben, az SQL Server dokumentációjában talál.  

 **Helyreállítás:**  

 A helyek helyreállítása során használhatja **Az adatbázis helyreállításának kihagyása (akkor válassza ezt a lehetőséget, ha a helyadatbázis nem sérült meg)**funkciót mindaddig, amíg van működőképes csomópont a rendelkezésre állási csoportban.  

 Azonban ha egy rendelkezésre állási csoport összes csomópontja elveszett, mielőtt a hely helyreállítása, újra létre kell hoznia a rendelkezésre állási csoport (System Center Configuration Manager nem tudja építse újra vagy állítsa vissza a rendelkezésre állási csomópontot.)  Miután a csoport újból létrejött a biztonsági másolat visszaállításával és újbóli konfigurálásával, már használhatja **Az adatbázis helyreállításának kihagyása (akkor válassza ezt a lehetőséget, ha a helyadatbázis nem sérült meg)** funkciót.  

 A biztonsági mentéssel és helyreállítással kapcsolatos további információkért lásd: [Biztonsági mentés és helyreállítás a System Center Configuration Managerben](../../../../protect/understand/backup-and-recovery.md).  

##  <a name="bkmk_create"></a> Rendelkezésre állási csoport konfigurálása a Configuration Managerrel való használatra  
 Az alábbi eljárás megkezdése előtt ismerkedjen meg az SQL Server azon eljárásaival Ez a konfiguráció befejezéséhez szükséges, és a rendelkezésre állási csoportokra vonatkozó következő adatok konfigurálása a Configuration Managerrel történő használathoz.  

 **A System Center Configuration Managerrel használt AlwaysOn rendelkezésre állási csoportokra vonatkozó követelmények**  

-  *Verzió*: A rendelkezésre állási csoport minden egyes csomópont (vagy replika) System Center Configuration Manager által támogatott SQL Server-verziónak kell futnia. Ha az SQL Server által támogatott különböző csomópontjait a rendelkezésre állási csoport futtathatja az SQL Server különböző verzióit.   

- *Edition*: Az SQL Server rendszer Enterprise verzióján kell használnia.  SQL Server 2016 Standard edition vezet be az alapvető rendelkezésre állási csoportok, a Configuration Manager által nem támogatott.


-   A rendelkezésre állási csoportnak rendelkeznie kell egy elsődleges másodpéldány, és legfeljebb két szinkron másodlagos replikája lehet.  

-  Miután hozzáadta az adatbázist a rendelkezésre állási csoporthoz, át kell adnia az elsődleges replika feladatait az egyik másodlagos replikának (így az válik az új elsődleges replikává), majd be kell állítania az adatbázison a következőket:
    - A Trustworthy tulajdonság engedélyezése: értéke legyen True
    - A Service Broker engedélyezése: értéke legyen True
    - dbowner beállítása: értéke legyen SA

    A beállítások konfigurálásához a következő parancsprogramot is futtathatja. A cm_ABC helyére írja be a helyadatbázis nevét:  

    >     HASZNÁLJON főkiszolgáló  
    >     Az ALTER DATABASE cm_ABC SET NEW_BROKER   
    >     Az ALTER DATABASE cm_ABC SET ENABLE_BROKER  
    >     Az ALTER DATABASE cm_ABC megbízható beállítása ON;  
    >     Cm_ABC használata  
    >     EXEC sp_changedbowner "sa"  
    >     Exec sp_configure ' max text repl size (B)", 2147483647 újrakonfigurálása



-   A rendelkezésre állási csoportban szerepelnie kell legalább egynek a következőből: **rendelkezésre állási csoport kérésfigyelője**.  Ez a figyelő virtuális neve szolgál a rendelkezésre állási csoportban található Helyadatbázis használatára a Configuration Manager konfigurálásakor. Bár a rendelkezésre állási csoport több figyelői is tartalmazza, a Configuration Manager csak tehet egyet használhat.  

-   Minden elsődleges és másodlagos replika esetében:  
    - Állítsa be **az összes csak olvasható kapcsolat engedélyezését**.
    - Használja az **alapértelmezett példányt**.
    - Állítson be **kézi feladatátvételt**.  

        > [!TIP]  
        >  A System Center Configuration Manager támogatja a rendelkezésre állási csoport replikái, ha az Automatikus feladatátvétel beállítása használatát. Azonban kézi feladatátvételt is be kell állítani elindítaná a telepítőt a Helyadatbázis használatának megadásához a rendelkezésre állási csoportban, és időben frissítéseinek telepítése a Configuration Manager (ne csak frissítést a Helyadatbázis).  

  **Rendelkezésre állási csoportokra vonatkozó korlátozások**
   - Alapvető rendelkezésre állási csoportok (SQL Server 2016 Standard edition rendszerben bevezetett) nem támogatottak. Ennek az az oka alapvető rendelkezésre állási csoportok nem támogatja az olvasási hozzáférést a másodlagos replikák előfeltétele annak, hogy a Configuration Managerrel használja. Kapcsolatban bővebben lásd: [alapvető rendelkezésre állási csoportok (az Always On rendelkezésre állási csoportok)](https://msdn.microsoft.com/en-us/library/mt614935.aspx).

   - Rendelkezésre állási csoportok csak a hely adatbázisának támogatottak, és nem a a szoftverfrissítési adatbázis vagy a jelentéskészítési adatbázist.   
   - Ha rendelkezésre állási csoportot használ, manuálisan be kell állítania, hogy a jelentési pont az aktuálisan elsődleges replikát használja, és ne a rendelkezésre állási csoport kérésfigyelőjét. Ha az elsődleges replika feladatátadást hajt végre egy másik replikára, ismét be kell állítania a jelentési ponton, hogy az az új elsődleges replikát használja.  
   - A frissítések (például az 1606-os verzió) telepítése előtt ellenőrizze, hogy a rendelkezésre állási csoportban beállította-e a manuális feladatátvételt. A hely frissítését követően visszaállíthatja az automatikus feladatátvételt.



 **A rendelkezésre állási csoportok konfigurálásához és használatához szükséges engedélyek:**  

-   A helykiszolgáló számítógépfiókjának a **Helyi rendszergazdák** csoport tagjának kell lennie minden olyan számítógépen, amely a rendelkezésre állási csoport tagja.  

#### <a name="to-configure-an-availability-group-to-host-a-site-database"></a>Rendelkezésre állási csoport konfigurálása helyadatbázis futtatására  

1.  A következő paranccsal állítsa le a Configuration Manager-hely:  
     **Preinst.exe /stopsite**  

     A Preinst.exe használatával kapcsolatos részletesebb információkért lásd: [A System Center Configuration Managerhez készült hierarchia-karbantartási eszköz (Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

2.  Módosítsa a helyadatbázis biztonsági mentési modelljét **egyszerűről** **teljesre**.  

     Lásd a [View or Change the Recovery Model of a Database](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) (Adatbázisok helyreállítási modelljének megtekintése vagy megváltoztatása) című témakört az SQL Server dokumentációjában. (A rendelkezésre állási csoportok csak a teljes mentési modellt támogatják.)  

3.  A csoport elsődleges replikáját futtató kiszolgálón az **Új rendelkezésre állási csoport varázsló** használatával hozza létre a rendelkezésre állási csoportot. A varázslóban:  

    -   Az a **adatbázis kijelölése** lapon, válassza ki az adatbázist, a Configuration Manager-hely  

    -   A **Replikák megadása** lapon adja meg a következő beállításokat:  

        -   **Replikák**: Adja meg a másodlagos replikákat tároló kiszolgálókat  

        -   **Figyelő**: Adja meg a **figyelő DNS-név** teljes DNS-névként, például a  **&lt;Listener_Server >. fabrikam.com**. Ez használatos, amikor a Configuration Manager az adatbázis használatára a rendelkezésre állási csoport konfigurálása.

    -   A **Kezdeti adatszinkronizálás kiválasztása** lapon válassza a **Teljes**lehetőséget. Miután a varázsló létrehozta a rendelkezésre állási csoportot, végrehajtja az elsődleges adatbázis és a tranzakciónapló biztonsági mentését, és visszaállítja ezeket minden olyan kiszolgálóra, amelyen másodlagos replika található. Ha nem hajtja végre ezt a lépést, a helyadatbázis példányát vissza kell állítania az összes olyan kiszolgálóra, amelyen másodlagos replika található, és kézzel kell csatlakoztatnia az adatbázist a csoporthoz.  

    További információt az SQL Server dokumentációjának [Use the Availability Group Wizard](https://msdn.microsoft.com/library/hh403415\(v=sql.120\).aspx) (A rendelkezésre állási csoport varázslójának használata) című témakörében talál.  

4.  A rendelkezésre állási csoport konfigurálása után konfigurálja az elsődleges replikán található a helyadatbázist a **TRUSTWORTHY** tulajdonság megadásával, majd **engedélyezze a CLR-integrációt**. A konfigurálásukkal kapcsolatos tudnivalókat lásd az SQL Server dokumentációjának [TRUSTWORTHY Database Property](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) (A TRUSTWORTHY adatbázis-tulajdonság) és  [Enabling CLR Integration](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx) (CLR-integráció engedélyezése) című témakörében.  

5.  A következő műveletek végrehajtásával konfigurálja az összes másodlagos replikát a rendelkezésre állási csoportban:  

    1.  Végezze el a manuális feladatátvételt az aktuális replikáról egy másodlagos replikára. Lásd az SQL Server dokumentációjának [Perform a Planned Manual Failover of an Availability Group](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) (Rendelkezésre állási csoport tervezett kézi feladatvételének végrehajtása) című témakörét.  

    2.  Konfigurálja az adatbázist az új elsődleges replikán a **TRUSTWORTHY** tulajdonság megadásával, és **engedélyezze a CLR-integrációt**.  

6.  Miután az összes replika elsődleges replikára változott, és a konfigurált adatbázisok van előléptetve, a rendelkezésre állási csoport készen áll a használható a Configuration Managerrel.  





##  <a name="bkmk_direct"></a> Helyadatbázis áthelyezése egy rendelkezésre állási csoportba  
 A korábban telepített helyek helyadatbázisát áthelyezheti rendelkezésre állási csoportokba. Először létre kell hoznia a rendelkezésre állási csoportot, majd be kell állítania az adatbázist a rendelkezésre állási csoportban való működésre.  

 Ez az eljárás végrehajtásához a Configuration Manager telepítőjét futtató felhasználói fióknak tagjának kell lennie a **helyi rendszergazdák** csoporthoz minden számítógépen, amely a rendelkezésre állási csoport tagja.  

#### <a name="to-move-a-site-database-to-an-availability-group"></a>Helyadatbázis áthelyezése egy rendelkezésre állási csoportba  

1.  Futtatás **a Configuration Manager telepítő** a  **&lt;Configuration Manager hely telepítési mappája\>\BIN\X64\setup.exe**.  

2.  A **Kezdeti lépések** oldalon válassza a **Helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása**lehetőséget, és kattintson a **Tovább**gombra.  

3.  Ezután válassza az **SQL Server konfigurációjának módosítása** beállítást, és kattintson a **Tovább**gombra.  

4.  Adja meg újból a helyadatbázis következő beállításait:  

    -   **SQL-kiszolgáló neve:** Adja meg a rendelkezésre állási csoport figyelőjének a rendelkezésre állási csoport létrehozásakor konfigurált virtuális nevét. A virtuális nevét kell teljes DNS-nevét, például  **&lt;Végpontkiszolgáló\>. fabrikam.com**  

    -   **Példány:** Ez az érték az alapértelmezett példány megadása a rendelkezésre állási csoport figyelőjének rendelkezésre állási csoport üresnek kell lennie.  Ha az aktuális helyadatbázis egy elnevezett példányon van telepítve, az elnevezett példány listázva lesz, és törölni kell.  

    -   **Adatbázis:** Hagyja neve, ahogyan megjelenik. Ez az aktuális helyadatbázis neve.  

5.  Miután megadta az új adatbázis helyének adatait, a telepítést a szokásos folyamattal és konfigurációkkal hajthatja végre.  

##  <a name="bkmk_change"></a> Aktív rendelkezésre állási csoport tagjainak hozzáadása vagy eltávolítása  
 Miután a Configuration Manager által használt egy rendelkezésre állási csoportban található helyadatbázist eltávolítására vagy is replikatagok (nem meghaladva az egy elsődleges és két másodlagos csomópontot).  

#### <a name="to-add-a-new-replica-member"></a>Új replikatag hozzáadása  

1.  Adja hozzá az új kiszolgálót másodlagos replikaként a rendelkezésre állási csoporthoz. Lásd az SQL Server dokumentációtárának  [Add a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/hh213247\(v=sql.120\).aspx)(Másodlagos replikák rendelkezésre állási csoporthoz (SQL Server) való hozzáadása) című témakörét.  

2.  Állítsa le a Configuration Manager-hely futtassa **Preinst.exe stopsite** lásd [hierarchia karbantartási eszköz (Preinst.exe) a System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

3.  Konfigurálja az összes másodlagos replikát. Hajtsa végre az alábbi műveleteket a rendelkezésre állási csoportban található minden másodlagos replikára vonatkozóan:  

    1.  Végezze el a manuális feladatátvételt az elsődleges replikáról az új másodlagos replikára. Lásd az SQL Server dokumentációjának [Perform a Planned Manual Failover of an Availability Group](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) (Rendelkezésre állási csoport tervezett kézi feladatvételének végrehajtása) című témakörét.  

    2.  Konfigurálja megbízhatónak az új kiszolgálón található adatbázist, és engedélyezze a CLR-integrációt. Lásd az SQL Server dokumentációjának [TRUSTWORTHY Database Property](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) (A TRUSTWORTHY adatbázis-tulajdonság) és  [Enabling CLR Integration](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx)(CLR-integráció engedélyezése) című témakörében.  

4.  Indítsa újra a helyet a Hely összetevő-kezelője (**sitecomp**) és az **SMS_Executive** szolgáltatás elindításával.  

#### <a name="to-remove-a-replica-member-from-the-availability-group"></a>Replikatag eltávolítása a rendelkezésre állási csoportból  

-   Olvassa el a [Remove a Secondary Replica from an Availability Group](https://msdn.microsoft.com/library/hh213149\(v=sql.120\).aspx) (Másodlagos replikák rendelkezésre állási csoportból való eltávolítása) című témakört az SQL Server dokumentációjában.  

##  <a name="bkmk_remove"></a> A helyadatbázis visszahelyezése rendelkezésre állási csoportból egypéldányos SQL-kiszolgálóra  
 Ha már nem szeretné rendelkezésre állási csoportban futtatni a helyadatbázist, hajtsa végre a következő műveletet.  

#### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>A helyadatbázis visszahelyezése rendelkezésre állási csoportból egypéldányos SQL-kiszolgálóra  

1.  Állítsa le a Configuration Manager-hely a következő paranccsal:  
     **Preinst.exe /stopsite**.  Részletesebb információkért lásd: [A System Center Configuration Managerhez készült hierarchia-karbantartási eszköz (Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

2.  Az SQL Server használatával hozzon létre egy teljes biztonsági mentést a helyadatbázisról az elsődleges replikából. Ennek végrehajtásáról az SQL Server dokumentációjában, a [Create a Full Database Backup](https://msdn.microsoft.com/library/ms187510\(v=sql.120\).aspx) (Teljes adatbázis biztonsági mentése) című témakörben olvashat bővebben.  

3.  Ha a rendelkezésre állási csoport elsődleges replikáját tároló kiszolgáló most a helyadatbázis egyetlen példányát fogja tárolni, akkor kihagyhatja ezt a lépést:  

    -   Az SQL Server használatával állítsa vissza a helyadatbázis biztonsági másolatát arra a kiszolgálóra, amely a helyadatbázist fogja tárolni.  Erről az SQL Server dokumentációjában, a [Restore a Database Backup (SQL Server Management Studio](https://msdn.microsoft.com/library/ms177429\(v=sql.120\).aspx) (Adatbázis biztonsági másolatának visszaállítása (SQL Server Management Studio)) című témakörben olvashat bővebben.  

4.  A visszaállított helyadatbázisban módosítsa a helyadatbázis biztonsági mentési modelljét **teljesről** **egyszerűre**.  Lásd a [View or Change the Recovery Model of a Database](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) (Adatbázisok helyreállítási modelljének megtekintése vagy megváltoztatása) című témakört az SQL Server dokumentációjában.  

5.  Futtatás **a Configuration Manager telepítő** a  **&lt;Configuration Manager hely telepítési mappája\>\BIN\X64\setup.exe**.  

6.  A **Kezdeti lépések** oldalon válassza a **Helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása**lehetőséget, és kattintson a **Tovább**gombra.  

7.  Ezután válassza az **SQL Server konfigurációjának módosítása** beállítást, és kattintson a **Tovább**gombra.  

8.  Adja meg újból a helyadatbázis következő beállításait:  

    -   **SQL-kiszolgáló neve:** Adja meg a helyadatbázist most tároló kiszolgáló neve.  

    -   **Példány:** Adja meg a helyadatbázist tároló elnevezett példányt, vagy hagyja üresen, ha az adatbázis az alapértelmezett példányon.  

    -   **Adatbázis:** Hagyja neve, ahogyan megjelenik. Ez az aktuális helyadatbázis neve.  

9. Miután megadta az új adatbázis helyének adatait, a telepítést a szokásos folyamattal és konfigurációkkal hajthatja végre. A telepítő befejeződése után a hely újraindul, és elkezdi használni az új adatbázishelyet.  

10. Ha törölni szeretné azokat a kiszolgálókat, amelyek a rendelkezésre állási csoport tagjai voltak, kövesse az SQL Server dokumentációjának [Remove an Availability Group](https://msdn.microsoft.com/library/ff878113\(v=sql.120\).aspx) (Rendelkezésre állási csoportok törlése) című témakörében foglalt útmutatást.

