---
title: "Biztonsági mentési és helyreállítási |} Microsoft Docs"
description: "További biztonsági mentéséhez és helyreállításához hiba vagy adatvesztés a System Center Configuration Managerben a helyeket."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ea6668ee7ee6b209b659426a0dc2c0be605ceaf1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="backup-and-recovery"></a>Biztonsági másolat és helyreállítás

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Készítse elő az adatvesztés elkerülése érdekében a biztonsági mentési és helyreállítási módszer. A Configuration Manager-helyek biztonsági mentési és helyreállítási módszer segítségével gyorsabban, és a legkisebb mértékű adatvesztéssel helyreállítása a helyek és hierarchiák. A jelen témakör részei segíti a helyek biztonsági mentését, és a hiba vagy adatvesztés helyreállításához.  



- [Configuration Manager-hely biztonsági mentése](#BKMK_SiteBackup)   

  - [A biztonsági mentési karbantartási feladat](#BKMK_BackupMaintenanceTask)   

  - [A helyadatbázis biztonsági mentése a Data Protection Manager használatával](#BKMK_DPMBackup)   

  -  [A biztonsági mentés pillanatképének archiválása](#BKMK_ArchivingBackupSnapshot)   

  -  [Az AfterBackup.bat fájl használata](#BKMK_UsingAfterBackup)   

  -  [Kiegészítő karbantartási feladatok](#BKMK_SupplementalBackup)   

-  [Configuration Manager-hely helyreállítása](#BKMK_RecoverSite)   

  -   [A helyreállítási lehetőségek meghatározása](#BKMK_DetermineRecoveryOptions)   

         -   [A helykiszolgáló helyreállítási lehetőségei](#BKMK_SiteServerRecoveryOptions)   

         -   [A helyadatbázis helyreállítási lehetőségei](#BKMK_SiteDatabaseRecoveryOption)   

         -   [Az SQL Server változáskövetési megőrzési ideje](#bkmk_SQLretention)   

         -   [Helyadatok vagy globális adatok újrainicializálásának folyamata](#bkmk_reinit)   

         -   [A helyadatbázis helyreállításának esetei](#BKMK_SiteDBRecoveryScenarios)  

  -   [A helyek felügyelet nélküli helyreállításához használható parancsfájl kulcsai](#BKMK_UnattendedSiteRecoveryKeys)  

  -   [Helyreállítás utáni feladatok](#BKMK_PostRecovery)  

  -   [Másodlagos hely helyreállítása](#BKMK_RecoverSecondarySite)  

-   [SMS-író szolgáltatás](#BKMK_SMSWriterService)  

> [!NOTE]  
>  Ha egy SQL Server AlwaysOn rendelkezésre állási csoport használja a Helyadatbázis futtatásához, módosítsa a biztonsági mentési és helyreállítási tervek leírtak a [változásokat a biztonsági mentés és helyreállítás egy SQL Server AlwaysOn rendelkezésre állási csoport](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md#bkmk_BnR) szakasza a [SQL Server AlwaysOn magas rendelkezésre állású Helyadatbázis a System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md) témakör.  

##  <a name="BKMK_SiteBackup"></a> Configuration Manager-hely biztonsági mentése  
 A Configuration Manager egy biztonsági mentési karbantartási feladat, amely rendelkezik:  

-   ütemezés szerint fut,  

-   biztonsági másolatot készít a helyadatbázisról,  

-   biztonsági másolatot készít a meghatározott beállításkulcsokról,  

-   biztonsági másolatot készít a meghatározott mappákról és fájlokról,  

-   Biztonsági mentést készít a System Center Configuration Manager **CD.Latest** mappájáról (l. [A System Center Configuration Manager CD.Latest mappája](../../core/servers/manage/the-cd.latest-folder.md))  

 tervbe veszi az alapértelmezett helymentési feladat legalább 5 naponta történő futtatását. Ennek oka, hogy a Configuration Manager használ a [SQL Server változáskövetési megőrzési időnél](#bkmk_SQLretention) 5 nap.  

 A biztonsági mentési folyamat egyszerűsítése érdekben létrehozhatja egy **AfterBackup.bat** fájlt, amellyel automatikusan végrehajthatja a biztonsági mentés utáni műveleteket, miután a biztonsági mentési karbantartási feladat sikeresen lefutott. Az AfterBackup.bat fájlt egy biztonságos helyre a biztonsági mentés pillanatképének archiválása általában szolgál. Az AfterBackup.bat fájl használatával a biztonsági mentés mappájába másolja a fájlokat, és más, kiegészítő biztonsági mentési feladatokat indíthat el.

A következő részekben a Configuration Manager biztonsági mentési stratégia létrehozásához.  

> [!NOTE]  
>  A Configuration Manager helyre tudja állítani a helyadatbázist, a Configuration Manager biztonsági mentési karbantartási feladatából, illetve egy Helyadatbázis biztonsági, amelyet egy másik folyamat során hozott létre. Például a Helyadatbázis visszaállíthatja egy biztonsági másolatból, amely a Microsoft SQL Server karbantartási tervének részeként jön létre. A helyadatbázist helyreállíthatja egy System Center 2012 Data Protection Manager (DPM) használatával létrehozott biztonsági másolatból. További információ: [A helyadatbázis biztonsági mentése a Data Protection Manager használatával](#BKMK_DPMBackup).  

###  <a name="BKMK_BackupMaintenanceTask"></a> A biztonsági mentési karbantartási feladat  
 A Configuration Manager-helyek biztonsági mentését az előre megadott helykiszolgáló biztonsági mentése karbantartási feladat ütemezésével teheti automatikussá. Biztonsági mentést készíthet a központi felügyeleti helyről és az elsődleges helyről, a másodlagos helyek és a helyrendszer-kiszolgálók esetében azonban nincs erre lehetőség. Amikor a Configuration Manager biztonsági mentési szolgáltatás fut, a biztonsági mentést vezérlő fájlban meghatározott utasításokat következik (**&lt;Configmgrtelepítésimappa\>\Inboxes\Smsbkup.box\Smsbkup.ctl**). A biztonsági mentés vezérlőfájljának módosításával megváltoztathatja a biztonsági mentési szolgáltatás működését. A biztonsági mentés állapotinformációit a rendszer az **Smsbkup.log** fájlba írja. A fájl a Helykiszolgáló biztonsági mentése karbantartási feladat tulajdonságaiban megadott célmappában jön létre.  


##### <a name="to-enable-the-site-backup-maintenance-task"></a>A biztonsági mentési karbantartási feladat engedélyezése  

1.  A Configuration Manager-konzolon nyissa meg **felügyeleti** > **Helykonfiguráció**  

     \> **Helyek**részt.  

2.  Válassza ki azt a helyet, amelynél engedélyezni szeretné a biztonsági mentési karbantartási feladatot.  

3.  Az a **Home** lap a **beállítások** csoportjában válassza **Helykarbantartási feladatok**.  

4.  Válasszon **helykiszolgáló biztonsági mentése**  >  **szerkesztése**.  

5.  Válasszon **feladat engedélyezése** > **elérési útvonalak beállítása** a biztonsági mentés célhelyének megadásához. A következő lehetőségek közül választhat:  

    > [!IMPORTANT]  
    >  A biztonsági mentés fájljainak illetéktelen módosításának megakadályozásához tárolja biztonságos helyen a fájlokat. A legbiztonságosabb hely a biztonsági mentés fájljainak tárolásához egy helyi meghajtó, amelyen beállíthatja az NTFS fájlrendszer engedélyeit az adott mappához. A Configuration Manager titkosítja a biztonsági másolat elérési tárolt biztonsági mentési adatokat.  

    -   **Helyi meghajtó a helykiszolgálón a helyadatok és az adatbázis**: Meghatározza, hogy a hely és a Helyadatbázis biztonsági másolatának fájljait a helykiszolgáló helyi lemezmeghajtóján a megadott elérési úton kell tárolni. A biztonsági mentési feladat futtatása előtt létre kell hoznia a helyi mappát. A helykiszolgáló helyi rendszer fiókjának az **Írás** NTFS fájlrendszerbeli engedéllyel kell rendelkeznie a helykiszolgáló biztonsági mentését tároló helyi mappához. Az SQL Server kiszolgálóval működő számítógépen a helyi rendszerfióknak **Írás** NTFS-engedéllyel kell rendelkeznie a helyadatbázis biztonsági mentését tároló mappához.  

    -   **Hálózati elérési út (UNC-név) a helyadatok és az adatbázis**: Megadja, hogy a hely és a Helyadatbázis biztonsági másolatának fájljait a megadott UNC elérési úton kell tárolni. A biztonsági mentési feladat futtatása előtt létre kell hoznia a megosztást. A helykiszolgáló számítógépfiókjának és az SQL Server számítógépfiókjának (ha az SQL Server másik számítógépre van telepítve) **Írás** NTFS-engedéllyel és megosztási engedéllyel kell rendelkeznie a megosztott hálózati mappára vonatkozóan.  

    -   **Helyi meghajtók a helykiszolgálón és az SQL Server**: Meghatározza, hogy a hely biztonsági másolatának fájljait a helykiszolgáló helyi meghajtójának megadott elérési tárolódnak, és a Helyadatbázis biztonsági másolatának fájljait a Helyadatbázis-kiszolgáló helyi meghajtójának megadott elérési útján tárolják. A biztonsági mentési feladat futtatása előtt létre kell hoznia a helyi mappákat. A helykiszolgáló számítógépfiókjának **Írás** NTFS-engedéllyel kell rendelkeznie a helykiszolgálón létrehozott mappához. Az SQL Server számítógépfiókjának **Írás** NTFS-engedéllyel kell rendelkeznie a helyadatbázis-kiszolgálón létrehozott mappához. Ez a beállítás csak akkor érhető el, ha a helyadatbázis nem a helykiszolgálóra van telepítve.  

    > [!NOTE]  
    >    - A biztonsági mentés célhelyének megkeresésének lehetősége csak akkor érhető el, ha megadja a biztonsági mentési célhely UNC elérési útját.

    > - A biztonsági mentési célhelyhez használt mappanév vagy megosztásnév nem támogatja a Unicode-karaktereket.  


6.  Konfiguráljon egy ütemezést az a hely biztonsági mentése. Legjobb megoldásként a biztonsági mentési ütemezést a munkaidőn kívüli órákra célszerű beállítani. Ha hierarchiát használ, olyan ütemezést állítson össze, amely hetente legalább két alkalommal futtatja a biztonsági mentést. Ezzel biztosíthatja az adatok legnagyobb mértékű megőrzését a hely meghibásodása esetén.  

    Amikor futtatja a Configuration Manager konzolt azon a helykiszolgálón, amelyet a biztonsági mentéshez konfigurált, a helykiszolgáló biztonsági mentése karbantartási feladat helyi időt használja az ütemezéshez. A Configuration Manager konzolon a webhely, amelyet a biztonsági mentéshez konfigurált távoli számítógépen fut, amikor a helykiszolgáló biztonsági mentése karbantartási feladat UTC IDŐT használja az ütemezéshez.  

7.  Válassza ki, hogy a riasztás létrehozása, ha meghiúsul a hely biztonsági mentése, kattintson a **OK**, és kattintson a **OK**. Kiválasztásakor a Configuration Manager létrehoz egy kritikus riasztás sikertelen biztonsági mentéshez megtekinthető a **riasztások** csomópontja a **figyelés** munkaterületen.  

 Ezt követően győződjön meg arról, hogy a helykiszolgáló biztonsági mentése karbantartási feladat fut-e, annak érdekében, hogy a biztonsági mentés létrehozása.  

##### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>Ellenőrizze, hogy a helykiszolgáló biztonsági mentése karbantartási feladat fut-e  

-   Győződjön meg arról, hogy a hely biztonsági mentése karbantartási feladat fut-e az alábbiak áttekintésével:  

    -   Ellenőrizze a biztonsági mentés célmappájában a feladat által létrehozott fájlok időbélyegzőjét. Győződjön meg arról, hogy az időbélyegző frissült, amely megfelel az idő, amikor a feladat utolsó ütemezett futtatásához időpontja.  

    -   A **Figyelés** munkaterület **Összetevő állapota** csomópontjában ellenőrizze az SMS_SITE_BACKUP állapotüzeneteit. Amikor a hely biztonsági mentése sikeres volt, az 5035-ös azonosítójú üzenet látható itt, ami azt jelzi, hogy a hely biztonsági mentése hiba nélkül befejeződött.  

    -   Amikor a Helykiszolgáló biztonsági mentése karbantartási feladat úgy van beállítva, hogy riasztást hozzon létre a biztonsági mentés hibája esetén, a **Figyelés** munkaterület **Riasztások** csomópontjában ellenőrizheti a biztonsági mentés során felmerült problémákat.  

    -   A &lt; *Configmgrtelepítésimappa*> \Logs, tekintse át az Smsbkup.log e figyelmeztetéseket és hibákat. A hely biztonsági mentésének sikeres végrehajtását az időbélyegzővel ellátott `Backup completed` üzenet jelzi, amelyhez a `STATMSG: ID=5035`üzenetazonosító tartozik.  

    > [!TIP]  
    >  A biztonsági mentési karbantartási feladat sikertelensége esetén az SMS_SITE_BACKUP szolgáltatás leállításával és újraindításával indíthatja el újból a biztonsági mentési feladatot.  

###  <a name="BKMK_DPMBackup"></a> A helyadatbázis biztonsági mentése a Data Protection Manager használatával  
 A helyadatbázis biztonsági mentésére használhatja a System Center 2012 Data Protection Manager (DPM) szoftvert. A DPM alkalmazásban létre kell hoznia egy új védelmi csoportot a helyadatbázis számítógépe számára. Új Az Új védelmi csoport létrehozása varázsló **Csoporttagok kiválasztása** lapján válassza ki az SMS-író szolgáltatást az adatforrások listájából, majd a csoport tagjaként válassza ki a helyadatbázist. További információért a helyadatbázis biztonsági mentéséről a DPM használatával l. [A Data Protection Manager dokumentációs könyvtárát](http://go.microsoft.com/fwlink/?LinkId=272772) a TechNet webhelyén.  

> [!IMPORTANT]  
>  A Configuration Manager nem támogatja a DPM biztonsági mentése SQL Server-fürtöt, amely megnevezett példányt használ, de támogatja a DPM biztonsági mentést az SQL Server alapértelmezett példányát használó SQL Server fürtön.  

 Miután helyreállította a helyadatbázist, a telepítő lépéseit követve állítsa helyre a helyet. Válassza ki a **manuálisan helyreállított Helyadatbázis használata** helyreállítási lehetőséget a Data Protection Manager helyreállított Helyadatbázis használatához.  

###  <a name="BKMK_ArchivingBackupSnapshot"></a> A biztonsági mentés pillanatképének archiválása  
 A Helykiszolgáló biztonsági mentése karbantartási feladat első futásakor létrehoz egy biztonsági mentési pillanatképet, amelyet hiba esetén felhasználhat a helykiszolgáló helyreállításához. A következő biztonsági mentési ciklus futásakor a feladat új biztonsági mentési pillanatképet hoz létre, amely felülírja az előző pillanatképet. Ennek következtében a helyhez csak egy biztonsági mentési pillanatkép tartozik, és nincs lehetőség egy korábbi pillanatkép helyreállítására.  

 A bevált gyakorlat szerint tartson meg több archív példányt a biztonsági mentési pillanatképből a következők miatt:  

-   Sikertelen, elveszik vagy csak részleges biztonsági másolat tartalmazza a biztonsági mentési adathordozó is. Egy meghibásodott önálló elsődleges helyet jobb helyreállítani egy régi biztonsági másolatból, mint biztonsági másolat nélkül. Egy hierarchiában lévő helykiszolgáló esetén a biztonsági másolatnak a változáskövetési megőrzési időn belül kell lennie, különben a biztonsági másolatra nincs szükség.  

-   A hely sérülése akár több biztonsági mentési cikluson át is észrevétlen maradhat. Lehetséges, hogy egy biztonsági mentési pillanatképet az a hely sérülése előtti használatára. Ez vonatkozik az önálló elsődleges hely és az a hierarchiában lévő helyek, ahol a biztonsági mentés van az SQL Server változáskövetési megőrzési idején belül.  

-   Lehet, hogy a helyről egyáltalán nincs biztonsági mentési pillanatkép, ha például a Helykiszolgáló biztonsági mentése karbantartási feladat sikertelen. Mivel a biztonsági mentési feladat eltávolítja az előző biztonsági mentési pillanatképet az aktuális adatok biztonsági mentésének megkezdése előtt, nem lesz érvényes biztonsági mentési pillanatkép.  

###  <a name="BKMK_UsingAfterBackup"></a> Az AfterBackup.bat fájl használata  
 A hely sikeres biztonsági mentését követően a Helykiszolgáló biztonsági mentése feladat automatikusan megkísérli futtatni az AfterBackup.bat nevű fájlt. Manuálisan kell létrehoznia az AfterBackup.bat fájlt a &lt; *Configmgrtelepítésimappa*> \Inboxes\Smsbkup. Ha AfterBackup.bat fájl létezik-e, és a megfelelő mappában található, akkor azt a automatikusan futtatja a biztonsági mentési feladat befejeződése után. Az AfterBackup.bat fájllal archiválhatja a biztonsági mentési pillanatképet minden biztonsági mentési művelet végén, és automatikusan elvégezhet a biztonsági mentés utáni más feladatokat is, amelyek nem részei a Helykiszolgáló biztonsági mentése feladatnak. Az AfterBackup.bat fájl integrálja az archiválási és a biztonsági mentési műveleteket, ezzel biztosítva, hogy minden új biztonsági mentési pillanatkép archiválva legyen. Ha nincs AfterBackup.bat fájl, a biztonsági mentési feladat kihagyja azt, és ez nincs hatással a biztonsági mentési műveletre. Annak ellenőrzéséhez, hogy a hely biztonsági mentési feladata sikeresen futtatta-e az AfterBackup.bat fájlt, tekintse meg az **Összetevő állapota** csomópontot a **Figyelés** munkaterületen, és nézze meg az SMS_SITE_BACKUP állapotüzeneteit. Ha a feladat sikeresen elindította az AfterBackup.bat parancsfájlt, megjelenik az 5040-es azonosítójú üzenet.  

> [!TIP]  
>  Hozni az AfterBackup.bat fájlt, hogy archiválja a helykiszolgáló biztonsági mentési fájljait, a Másolás parancsot eszköz, például a Robocopy, kell használnia a parancsfájlba. Például létrehozhatja az AfterBackup.bat fájlt, és az első sorba beírhat az alábbihoz hasonlót: `Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR`. A Robocopy eszközzel kapcsolatban további tudnivalókat a [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408) parancssor útmutatójának weblapján talál.  

 Bár az AfterBackup.bat rendeltetése a biztonsági mentési pillanatképek archiválása, létrehozhat egy AfterBackup.bat fájlt a biztonsági mentési művelet végén elvégzendő egyéb feladatokhoz.  

###  <a name="BKMK_SupplementalBackup"></a> Kiegészítő karbantartási feladatok  
 A Helykiszolgáló biztonsági mentése karbantartási feladat létrehoz egy biztonsági mentési pillanatképet a helykiszolgáló fájljairól és a helyadatbázisról, de vannak olyan elemek, amelyekről nem készül biztonsági mentés, és amelyeket érdemes figyelembe venni a biztonsági mentési stratégia létrehozásakor. A következő szakaszok segítségével végezze el a Configuration Manager biztonsági mentési stratégiának.  

#### <a name="back-up-custom-reporting-services-reports"></a>Reporting Services szolgáltatásbeli egyéni jelentések biztonsági mentése  
 Ha módosította az előre megadott Reporting Services-jelentéseket, vagy létrehozott egyénieket, a jelentési kiszolgáló adatbázisfájljainak biztonsági mentése fontos része a biztonsági mentési stratégiának. A jelentési kiszolgáló biztonsági mentésének tartalmaznia kell a jelentések és modellek forrásfájljainak, a titkosítási kulcsoknak, az egyéni szerelvényeknek vagy bővítményeknek, a konfigurációs fájloknak, az egyéni jelentésekben használt egyéni SQL Server-nézeteknek, az egyéni tárolt eljárásoknak stb. biztonsági másolatát.  

> [!IMPORTANT]  
>  Amikor a Configuration Manager egy újabb verzióra frissíti, az előre megadott jelentések felülíródhatnak az új jelentésekkel. Ha módosít egy előre megadott jelentést, készítsen biztonsági másolatot a jelentésről, és majd visszaállítani a Reporting Services szolgáltatásokban.  

 Ha többet szeretne tudni a Reporting Services szolgáltatásbeli egyéni jelentések biztonsági mentéséről, olvassa el a [Biztonsági mentésik és helyreállítási műveletek Reporting Services-példányhoz](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) című részt az SQL Server 2014 Books Online webhelyen.  

#### <a name="backup-content-files"></a>Tartalomfájlok biztonsági mentése  
 A tartalomtár a Configuration Managerben az a hely összes tartalomfájlt tároló a szoftverfrissítések, alkalmazások, operációs rendszerek központi telepítéséhez, és így tovább. A tartalomtár a helykiszolgálón és minden terjesztési pontján helyezkedik el. A Helykiszolgáló biztonsági mentése feladat nem tartalmazza a tartalomtár és a csomagforrásfájlok biztonsági mentését. Egy helykiszolgáló meghibásodása esetén a tartalomtárfájlokkal kapcsolatos információ visszaáll a helyadatbázisban, de a tartalomtárat és a csomagforrásfájlokat manuálisan kell visszaállítani a helykiszolgálón.  

-   **Tartalomtár**: A tartalomtár visszaállítása után terjeszthet újra tartalmat a terjesztési pontokra. Amikor hozzákezd a tartalom újraterjesztéséhez, a Configuration Manager másolja át a fájlokat a tartalomtár a helykiszolgálón a terjesztési pontokra. A helykiszolgáló tartalomtára az SCCMContentLib mappában, amely általában a ideje a hely telepítésekor legtöbb szabad területtel rendelkező meghajtón található van.  

-   **Csomagforrásfájlok**: A csomagforrásfájlokat vissza kell állítani, a terjesztési pontokon a tartalom frissítése előtt. Amikor elkezd egy tartalomfrissítést, Configuration Manager másolja át új vagy módosított fájlokat a csomagforrásból a tartalomtárba, amely kapcsolja másolja a fájlokat a társított terjesztési pontok. Az SQL Serverben a következő lekérdezéssel keresheti meg a csomagforrás helyét az összes csomaghoz és alkalmazáshoz: `SELECT * FROM v_Package`. A csomag forráshelyét a csomagazonosító első három karaktere alapján azonosíthatja. Ha például a csomagazonosító CEN00001, a forráshely helykódja CEN. A csomagforrásfájlok visszaállítása, akkor le kell állítani ugyanarra a helyre, ahol a meghibásodás előtt voltak.  

 Ellenőrizze, hogy a fájlrendszer biztonsági mentése tartalmazza-e a helykiszolgálóhoz a tartalomtárat és a csomagforráshelyeket is.  

#### <a name="back-up-custom-software-updates"></a>Egyéni szoftverfrissítések biztonsági mentése  
 A System Center Updates Publisher 2011 olyan önálló eszköz, amely lehetővé teszi az egyéni szoftverfrissítések közzé a Windows Server Update Services (WSUS), a Configuration Manager szoftverfrissítések szinkronizálását, szoftverfrissítések megfelelőségének az értékelését és az egyéni szoftverfrissítések központi telepítése az ügyfelekre. Frissítés-közzétevő egy helyi adatbázist használ a szoftverfrissítési tárházához. Ha Updates Publisher használatával kezeli az egyéni szoftverfrissítéseket, határozza meg, hogy fel kell vennie az Updates Publisher adatbázisában a biztonsági mentési terv. Az Updates Publisherrel kapcsolatos további tudnivalókért lásd a [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) dokumentumot a System Center TechCenter tárban.  

 A következő eljárás használatával készítsen biztonsági másolatot az Updates Publisher adatbázisában.  

###### <a name="to-back-up-the-updates-publisher-2011-database"></a>Az Updates Publisher 2011 adatbázisának biztonsági mentése  

1.  Az Updates Publishert futtató számítógépen keresse meg a frissítés-közzétevő adatbázisfájljához (Scupdb.sdf) a %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\. Az Updates Publishert futtató minden felhasználóhoz külön adatbázisfájl van.  

2.  Másolja az adatbázisfájlt a biztonsági mentési célhelyre. Például ha a biztonsági mentés célhelye E:\ConfigMgr_Backup, akkor nem átmásolni az Updates Publisher adatbázisfájlt E:\ConfigMgr_Backup\SCUP2011.  

    > [!TIP]  
    >  Amikor egy számítógépen több adatbázisfájl van, fontolja meg a fájlt egy almappában tárolni, amely jelöli az adatbázis-fájlhoz tartozó felhasználói profilt. Például lehet egy adatbázisfájlja az E:\ConfigMgr_Backup\SCUP2011\User1, és egy másik az E:\ConfigMgr_Backup\SCUP2011\User2 mappában.  

### <a name="user-state-migration-data"></a>Felhasználóáttelepítési adatok  
 Használhatja a Configuration Manager feladatütemezések rögzítheti és visszaállíthatja a felhasználói állapotadatokat olyan operációsrendszer-telepítési helyzetekben hol szeretné megőrizni az aktuális operációs rendszer felhasználói állapotát. A felhasználói adatokat tároló mappák a felhasználóáttelepítési pont tulajdonságaiban vannak megadva. Ezekről a felhasználóáttelepítési adatokról nem készül biztonsági mentés a Helykiszolgáló biztonsági mentése karbantartási feladat részeként. A biztonsági mentési terv részeként manuálisan készítsen biztonsági mentést azokról a mappákról, amelyeket megad a felhasználóáttelepítési adatok tárolására.   

#### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>A felhasználóáttelepítési adatok tárolására használt mappák megállapítása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, és válassza a **kiszolgálók és Helyrendszerszerepkörök**.  

3.  Válassza ki a felhasználóáttelepítési szerepkört tároló helyrendszert, és válassza a **állapotáttelepítési pont** a **Helyrendszerszerepkörök**.  


4.  A **Helyszerepkör** lap **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  
5.  A felhasználóáttelepítési adatokat tároló mappák az **Általános** lap **Mappa adata** szakaszában vannak megadva.  

## <a name="recover-a-configuration-manager-site"></a>Configuration Manager-hely helyreállítása
 A Configuration Manager-hely helyreállítása szükség a Configuration Manager-hely meghibásodik, vagy adatvesztés történik a helyadatbázisban. A helyhelyreállítás alapfeladata az adatok javítása és újraszinkronizálása a működés megszakadásának megelőzése érdekében.  

> [!IMPORTANT]  
>  Hely adatbázisának helyreállítása esetén:  

>  -   Az SQL Server azonos verzióját és kiadását kell használnia. SQL Server 2014-et az SQL Server 2012 verzióján futott adatbázis visszaállítása például nem támogatott. Az SQL Server 2014 Enterprise kiadására az SQL Server 2014 Standard kiadásán futott Helyadatbázis visszaállítása hasonlóképpen nem támogatott.  
> -   Az SQL Server nem lehet **egyfelhasználós üzemmódra**beállítva.  
> -   Ügyelnie kell arra, hogy az .MDF- és .LDF-fájlok érvényesek legyenek. Amikor helyreállít egy helyet, a rendszer nem ellenőrzi a visszaállított fájlok állapotát.  


 A Site recovery indítja el a CD-ről a Configuration Manager telepítése varázsló futtatását. Legfrissebb mappát.  A felügyelet nélküli telepítési parancsfájlt is konfigurálhatja, és kövesse a Setup parancs **/script** lehetőséget a azonos CD-ről futtassa a telepítőt. Legfrissebb mappát. A helyreállítási beállítások változhatnak attól függően, hogy van-e a Configuration Manager Helyadatbázis biztonsági másolatból. További információért lásd: [A System Center Configuration Manager CD.Latest mappája](../../core/servers/manage/the-cd.latest-folder.md).  

> [!IMPORTANT]  
>  Ha futtatja a Configuration Manager a **Start** menü a helykiszolgálón, a **hely helyreállítása** , nincs lehetőség.  

>  Ha telepítette a Configuration Manager konzolon belül a frissítéseket a biztonsági mentés előtt, akkor nem sikeresen a hely újratelepítését a telepítőprogram használatával a telepítési adathordozóról vagy a Configuration Manager telepítési mappája.  

> [!NOTE]  
>  Miután visszaállított egy adatbázis-replikákhoz létrehozott helyadatbázist, ahhoz, hogy használhatók legyenek az adatbázis-replikák, újra kell konfigurálni mindegyiket, újból létrehozva a közzétételeket és az előfizetéseket.  

###  <a name="BKMK_DetermineRecoveryOptions"></a> A helyreállítási lehetőségek meghatározása  
 Nincsenek a két fő területet kell figyelembe venni a Configuration Manager elsődleges helykiszolgáló és a központi adminisztrációs hely helyreállítása; a helykiszolgáló és a hely adatbázisába. A következő szakaszok segítségével meghatározhatja, hogy milyen beállításokat kell kiválasztania az adott helyreállítási körülményekhez.  

> [!NOTE]  

####  <a name="BKMK_SiteServerRecoveryOptions"></a> A helykiszolgáló helyreállítási lehetőségei  
 A CD-jének példányából kell elindítania a telepítőt. A Configuration Manager telepítési mappa kívül létrehozott legújabb mappához. Ezután válassza a **Hely helyreállítása** lehetőséget. A telepítő futtatásakor a következő helyreállítási beállítások érhetők el a hibás helykiszolgálóhoz:  

-   **Meglévő biztonsági mentésből helykiszolgáló helyreállítása**: Használja ezt a beállítást, ha van olyan biztonsági részeként készült a helykiszolgálón a Configuration Manager-kiszolgáló a **helykiszolgáló biztonsági mentése** karbantartási feladat a hely meghibásodása előtt. A hely újratelepül, és a helybeállítások konfigurálva lesznek azon hely alapján, amelyről biztonsági mentés készült.  

-   **A helykiszolgáló újratelepítése**: Használja ezt a beállítást, ha nem rendelkezik egy biztonsági másolata a helykiszolgálóról. A helykiszolgáló újratelepül, és meg kell adni a helybeállításokat, mint az első telepítéskor. A hely sikeres helyreállításához ugyanazt a helykódot és helyadatbázisnevet kell használni, mint a meghibásodott hely első telepítésekor.  

> [!NOTE]  
>  Amikor a telepítő észleli, egy meglévő Configuration Manager-hely a kiszolgálón, elindíthatja a hely helyreállítását, de a helykiszolgáló helyreállítási lehetőségei korlátozottak. Ha például egy meglévő helykiszolgálón futtatja a telepítőt, a helyreállítás kiválasztásakor helyreállíthatja az adatbázis-kiszolgálót, azonban a helykiszolgáló helyreállítási lehetősége le van tiltva.  

####  <a name="BKMK_SiteDatabaseRecoveryOption"></a> A helyadatbázis helyreállítási lehetőségei  
 A telepítő futtatásakor a következő helyreállítási beállítások érhetők el a helyadatbázishoz:  

-   **A Helyadatbázis biztonságimásolat-készletből helyreállítása**: Használja ezt a beállítást, ha a Configuration Manager Helyadatbázis részeként létrehozott biztonsági másolatot a **helykiszolgáló biztonsági mentése** karbantartási feladat a Helyadatbázis meghibásodása előtt. Ha rendelkezik hierarchiával, a helyadatbázison a helyadatbázis utolsó biztonsági mentése után végzett módosításokat a rendszer beolvassa az elsődleges hely központi felügyeleti helyéről vagy egy központi felügyeleti hely elsődleges referenciahelyéről. Amikor helyreállít egy helyadatbázist egy önálló elsődleges helyhez, elvesznek a hely utolsó biztonsági mentés óta végzett módosításai.  

     Amikor helyreállít egy helyadatbázist egy hierarchiabeli helyhez, a helyreállítás másképp működik egy központi felügyeleti helyhez és elsődleges helyhez, valamint ha az utolsó biztonsági mentés az SQL Server változáskövetési megőrzési idején belül vagy kívül van. További információért lásd a jelen témakör [A helyadatbázis helyreállításának esetei](#BKMK_SiteDBRecoveryScenarios) című részét.  

    > [!NOTE]  
    >  A helyreállítás sikertelen, ha a helyadatbázis biztonságimásolat-készletből történő helyreállítását választja, de a helyadatbázis már létezik.  

-   **Hozzon létre egy új adatbázist ehhez a helyhez**: Használja ezt a beállítást, ha nem áll a Configuration Manager Helyadatbázis biztonsági másolatból. Ha rendelkezik hierarchiával, új helyadatbázis jön létre, és az adatok helyreállnak egy elsődleges hely központi felügyeleti helyéről származó replikált adatokból, illetve egy központi felügyeleti hely elsődleges referenciahelyéről. Ez a beállítás nem érhető el, ha önálló elsődleges helyet vagy elsődleges helyekkel nem rendelkező központi felügyeleti helyet állít vissza.  

-   **Manuálisan helyreállított Helyadatbázis használata**: Használja ezt a beállítást, ha már helyreállította a Configuration Manager helyadatbázisát, de be kell fejeznie a helyreállítási folyamat. A Configuration Manager helyre tudja állítani a helyadatbázist, a Configuration Manager biztonsági mentési karbantartási feladatából, illetve egy Helyadatbázis biztonsági DPM vagy egy másik folyamat használatával elvégezhető. Miután helyreállította a Helyadatbázis egy metódussal a Configuration Manager alkalmazáson kívül, futtassa a telepítőt, és ezt a beállítást a Helyadatbázis helyreállításának befejezéséhez. Ha rendelkezik hierarchiával, a helyadatbázison a helyadatbázis utolsó biztonsági mentése után végzett módosításokat a rendszer beolvassa az elsődleges hely központi felügyeleti helyéről vagy egy központi felügyeleti hely elsődleges referenciahelyéről. Amikor helyreállít egy helyadatbázist egy önálló elsődleges helyhez, elvesznek a hely utolsó biztonsági mentés óta végzett módosításai.  

    > [!NOTE]  
    >  Ha DPM használatával készít biztonsági mentést a helyadatbázisról, használja a DPM eljárásait történő visszaállításához a Helyadatbázis adott helyre, mielőtt folytatja a helyreállítási folyamatot a Configuration Manager alkalmazásban. További információkért a DPM-ről l. [A Data Protection Manager dokumentációs könyvtárát](http://go.microsoft.com/fwlink/?LinkId=272772) a TechNet webhelyén.  

-   **Az adatbázis helyreállításának kihagyása**: Akkor válassza ezt a beállítást, ha adatvesztés nélküli történt a Configuration Manager Helyadatbázis-kiszolgálón. Ez a beállítás csak akkor érvényes, ha a helyadatbázis nem azon a számítógépen van, amelyiken a helyreállítandó helykiszolgáló.  

####  <a name="bkmk_SQLretention"></a> Az SQL Server változáskövetési megőrzési ideje  
 A változáskövetés engedélyezett az SQL Server rendszeren lévő helyadatbázishoz. Változáskövetés lehetővé teszi, hogy a Configuration Manager a módosításokat végzett adatbázistáblák után egy korábbi időpontra idő lekérdezést. A megőrzési idő megadja, hogy mennyi ideig maradnak meg a követési adatok. Alapértelmezésben a helyadatbázis 5 napos megőrzési idővel van konfigurálva. Helyadatbázis helyreállításakor a helyreállítási folyamat eltérő lehet attól függően, hogy a biztonsági mentés a megőrzési időn belül vagy kívül történik. Ha például az adatbázis-kiszolgáló meghibásodik, és az utolsó biztonsági mentés 7 napos, akkor kívül van a megőrzési időn.

 SQL Server változáskövetési internals kapcsolatos további információkért tekintse meg az SQL Server csapat következő angol nyelvű blogokban: [Változások követése tisztítás - 1. rész](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1) és [módosítása követési karbantartása – 2. rész](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2).



####  <a name="bkmk_reinit"></a> Helyadatok vagy globális adatok újrainicializálásának folyamata  
 A helyadatok vagy a globális adatok újrainicializálásának folyamata lecseréli a helyadatbázis meglévő adatait egy másik helyadatbázis adataira. Például amikor az ABC hely újrainicializálja az adatokat az XYZ helyről, a következő lépések történnek:  

-   A rendszer átmásolja az adatokat az XYZ helyről az ABC helyre.  

-   Az XYZ hely meglévő adatai törlődnek a helyadatbázisból az ABC helyen.  

-   Az XYZ helyről másolt adatok bekerülnek az ABC hely helyadatbázisába.  

##### <a name="example-scenario-1"></a>1. példa  
 **Az elsődleges hely újrainicializálja a globális adatokat a központi adminisztrációs hely**: A helyreállítási folyamat eltávolítja az elsődleges hely meglévő globális adatait az elsődleges hely adatbázisából, és lecseréli azokat a központi felügyeleti helyről másolt globális adatokra.  

##### <a name="example-scenario-2"></a>2. példa  
 **A központi felügyeleti hely újrainicializálja a helyadatokat egy elsődleges helyről**: A helyreállítási folyamat eltávolítja az elsődleges hely meglévő helyadatait a központi felügyeleti hely adatbázisából, és lecseréli azokat az elsődleges helyről másolt globális adatokra. A többi elsődleges hely helyadatait ez nem befolyásolja.  

####  <a name="BKMK_SiteDBRecoveryScenarios"></a> A helyadatbázis helyreállításának esetei  
 A Helyadatbázis egy biztonsági másolatból történt visszaállítása, miután a Configuration Manager megkísérli az adatbázis utolsó biztonsági mentése után állítsa vissza a hely és a globális adatokban történt módosításokat. A következő láthatók azok a műveletek adott Configuration Manager elkezdi a Helyadatbázis biztonsági másolatból történt visszaállítása után.  

 **A helyreállított hely egy központi adminisztrációs hely:**  

-   **Az adatbázis biztonsági mentése a változáskövetési megőrzési időn belül van**  

    -   **Globális adatok:** A globális adatok biztonsági mentés utáni változásai replikálódnak az összes elsődleges helyről.  

    -   **Helyadatok:** A helyadatok biztonsági mentés utáni változásai replikálódnak az összes elsődleges helyről.  

-   **Az adatbázis biztonsági mentése a változáskövetési megőrzési időnél régebbi**  

    -   **Globális adatok:** A központi adminisztrációs hely újrainicializálja a globális adatokat az elsődleges referenciahelyről, ha megadja azt. Ezután az összes többi elsődleges hely újrainicializálja a globális adatokat a központi felügyeleti helyről. Ha nincs megadva referenciahely, minden elsődleges hely újrainicializálja a globális adatokat a központi felügyeleti helyről (a biztonsági másolatból visszaállított adatokat).  

    -   **Helyadatok:** A központi felügyeleti hely újrainicializálja a helyadatokat valamennyi elsődleges helyről.  

 **A helyreállított hely egy elsődleges hely:**  

-   **Az adatbázis biztonsági mentése a változáskövetési megőrzési időn belül van**  

    -   **Globális adatok:** A globális adatok biztonsági mentés utáni változásai replikálódnak a központi adminisztrációs helyről.  

    -   **Helyadatok:** A központi felügyeleti hely újrainicializálja a helyadatokat az elsődleges helyről. A biztonsági mentés utáni módosítások elvesznek, de a legtöbb adatot újra létrehozzák azok az ügyfelek, amelyek információkat küldenek az elsődleges helyre.  

-   **Az adatbázis biztonsági mentése a változáskövetési megőrzési időnél régebbi**  

    -   **Globális adatok:** Az elsődleges hely újrainicializálja a globális adatokat a központi adminisztrációs helyről.  

    -   **Helyadatok:** A központi felügyeleti hely újrainicializálja a helyadatokat az elsődleges helyről. A biztonsági mentés utáni módosítások elvesznek, de a legtöbb adatot újra létrehozzák azok az ügyfelek, amelyek információkat küldenek az elsődleges helyre.  

### <a name="site-recovery-procedures"></a>Hely helyreállításának folyamata  
 Az alábbi eljárásokkal helyreállíthatja a helykiszolgálót és a helyadatbázist.  

##### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>Hely helyreállításának megkezdése a telepítővarázslóval  

1.  Másolja a CD-n. A Configuration Manager telepítési mappa kívülre legfrissebb mappát. (L. [A System Center Configuration Manager CD.Latest mappája](../../core/servers/manage/the-cd.latest-folder.md))  

     A CD-n másolatát. Legfrissebb mappát, a Configuration Manager telepítővarázsló futtatásához.  

2.  Az **Első lépések** lapon válassza a **Hely helyreállítása**lehetőséget, majd kattintson a **Tovább**gombra.  

3.  A varázslót az adott helyhelyreállításhoz megfelelő beállításokkal fejezze be.  

    > [!IMPORTANT]  
    >  Helyreállítás közben a telepítő megállapítja, hogy az SQL Server melyik SSB-portot (SQL Server Service Broker) használja. Ne módosítsa ezt a portbeállítást a helyreállítás közben, mert az adatreplikálás nem fog megfelelően működni a helyreállítás után.  

    > [!NOTE]  
    >  Megadhatja az eredeti, vagy egy új útvonalat a Configuration Manager telepítéséhez a telepítővarázslóban.  

##### <a name="to-start-an-unattended-site-recovery"></a>Hely felügyelet nélküli helyreállításának indítása  

1.  Készítse elő a felügyelet nélküli helyreállítási parancsfájlt a hely helyreállításához szükséges beállításokkal.  

2.  A parancs segítségével futtassa a Configuration Manager telepítő **/script** lehetőséget. Például ha a telepítési inicializációs fájlnak a configmgrunattend.ini nevet és a, amelyen a telepítőt futtató számítógép C:\Temp könyvtárában található, a parancs lenne az alábbiak szerint: **A telepítő/Script C:\temp\ConfigMgrUnattend.ini**.  

> [!NOTE]  
>  A központi adminisztrációs helyek helyreállítása után a gyermekhelyekről egyes helyadatok replikálása sikertelen lehet. Ilyen lehet például a hardverleltár, a szoftverleltár és az állapotüzenetek.  
>   
>  Ilyen esetben a **ConfigMgrDRSSiteQueue** újrainicializálása szükséges az adatbázis-replikáláshoz.  Ehhez használja **SQL Server Manager** a következő lekérdezés futtatása a Configuration Manager helyadatbázist a központi adminisztrációs hely:  
>   
>  **IF EXISTS (SELECT \* FROM sys.service_queues WHERE name = 'ConfigMgrDRSSiteQueue' AND is_receive_enabled = 0)**  
>   
>  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**  

###  <a name="BKMK_UnattendedSiteRecoveryKeys"></a> A helyek felügyelet nélküli helyreállításához használható parancsfájl kulcsai  
 Felügyelet nélküli helyreállításához a Configuration Manager központi adminisztrációs hely vagy elsődleges hely, létrehozhat egy felügyelet nélküli telepítési parancsfájlt, és amelyben a setup parancs/Script kapcsolóval használja. A parancsfájl ugyanolyan információkat tartalmaz, amilyeneket a telepítővarázsló kér, azzal a különbséggel, hogy nincsenek alapértelmezett beállítások. A telepítési kulcsokhoz minden értéket meg kell adni, ami az adott helyreállítás-típusra vonatkozik.  

 A Configuration Manager telepítő felügyelet nélküli is futtathatja egy inicializációs fájlt a setup parancs/Script telepítési parancssori kapcsoló használatával. A Configuration Manager központi adminisztrációs hely és elsődleges hely felügyelet nélküli telepítés esetén támogatott. A /script telepítési parancssori kapcsoló használatához létre kell hozni egy inicializációs fájlt, és a nevét meg kell adni a /script telepítési parancssori kapcsoló után. A fájl neve nem lényeges, csak az .ini fájlnévkiterjesztés számít. Amikor a parancssorból hivatkozik a telepítési inicializációs fájlra, meg kell adni a fájl teljes elérési útját. Ha például a telepítési inicializációs fájl neve setup.ini, és a C:\setup mappában található, a parancssor a következő lesz:  

 **setup /script c:\setup\setup.ini**.  

> [!IMPORTANT]  
>  A telepítő futtatásához rendszergazdai jogosultsággal kell rendelkeznie. Ha a felügyelet nélküli parancsfájllal futtatja a telepítőt, a parancssort rendszergazdai környezetben kell elindítania a **Futtatás rendszergazdaként**beállítás használatával.  

 A parancsfájl tartalmazza a szakaszneveket, a kulcsneveket és az értékeket. A szükséges szakaszkulcsnevek attól függenek, hogy milyen helyreállítás-típushoz készít parancsfájlt. A kulcsok szakaszokon belüli sorrendje, illetve a szakaszok fájlon belül sorrendje nem lényeges. A kulcsokban nincs különbség a kis- és a nagybetűk között. Ha értékeket ad meg a kulcsokhoz, a kulcsnevet egyenlőségjelnek (=) és a kulcs értékének kell követnie.  

 A következő részekben leírtak alapján létrehozhatja a felügyelet nélküli helyhelyreállítás parancsfájlját. A táblázatokban láthatók a telepítési parancsfájl elérhető kulcsai, a hozzájuk tartozó értékek, kötelezőségük, hogy mely telepítéstípusokhoz használhatók, valamint a kulcsok rövid leírása.  

#### <a name="recover-a-central-administration-site-unattended"></a>Központi adminisztrációs hely felügyelet nélküli helyreállítása  
 A következő információk segítségével konfigurálhat egy felügyelet nélküli telepítési parancsfájlt a központi adminisztrációs hely helyreállítása.  

 **Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** RecoverCCAR  

    -   **Részletek:** Központi adminisztrációs hely helyreállítása  

-   **Kulcsnév:** CDLatest  

    -   **Szükséges:** Igen – csak akkor, ha a CD-ről adathordozó használatával. Legfrissebb mappát.    

    -   **Értékek:** 1 értéke nem 1 tekintendő nem használja CD-ről. Legújabb.

    -   **Részletek:** A parancsfájl tartalmaznia a kulcs-érték telepítő CD-ről az adathordozóról való futtatásakor. Legújabb mappa céljából egy elsődleges vagy központi adminisztrációs hely telepítése, vagy egy elsődleges vagy központi adminisztrációs helyet állít helyre. Ez az érték tájékoztatja a beállítása, hogy a média CD alkotnak. Legutóbbi használatban van.  

**RecoveryOptions**  

-   **Kulcsnév:** ServerRecoveryOptions  

    -   **Szükséges:** Igen  

    -   **Értékek:** 1, 2 vagy 4  

         1 = helykiszolgáló és SQL Server helyreállítása.  

         2 = csak a helykiszolgáló helyreállítása.  

         4 = csak az SQL Server helyreállítása.  

    -   **Részletek:** Megadja, hogy a telepítő állítja helyre a helykiszolgálót, az SQL Server, vagy mindkettőt. A kapcsolódó kulcsok akkor szükségesek, amikor a ServerRecoveryOptions beállításhoz megadja a következő értéket:  

        -   **Érték = 1** A **SiteServerBackupLocation** kulcshoz értéket megadva a helyről készített biztonsági másolat használatával állíthatja helyre az adott helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

             A **BackupLocation** kulcsot kötelező megadni, ha a **DatabaseRecoveryOptions** kulcsnál a megadott érték **10** , ami a hely adatbázisának biztonsági másolatból történő visszaállítását jelenti.  

        -   **Érték = 2** A **SiteServerBackupLocation** kulcshoz értéket megadva a helyről készített biztonsági másolat használatával állíthatja helyre az adott helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

        -   **Érték = 4** : A **BackupLocation** kulcs értékét meg kell adni, ha a **DatabaseRecoveryOptions** kulcsnál a megadott érték **10** , ami a hely adatbázisának biztonsági másolatból történő visszaállítását jelenti.  

-   **Kulcsnév:** DatabaseRecoveryOptions  

    -   **Szükséges:** Talán  

    -   **Értékek:** 10, 20, 40, 80  

         10 = a hely adatbázisának visszaállítása biztonsági másolatból.  

         20 = más módszer alkalmazásával manuálisan helyreállított helyadatbázis használata.  

         40 = új adatbázis létrehozása a helyhez. Ezt a lehetőséget akkor kell használni, ha nem áll rendelkezésre biztonsági másolat a helyhez. A globális és a helyadatokat más helyekről történő replikációval állítja helyre a rendszer.  

         80 = az adatbázis helyreállításának kihagyása.  

    -   **Részletek:** Meghatározza, hogy a telepítő hogyan állítja helyre a helyadatbázist az SQL Server. Ezt a kulcsot meg kell adni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **4**.  

-   **Kulcsnév:** ReferenceSite  

    -   **Szükséges:** Talán  

    -   **Értékek:** &lt;Referenciahely teljes tartományneve\>  

    -   **Részletek:** Megadja a referencia elsődleges helyet, amellyel a központi adminisztrációs hely helyreállítja a globális adatokat, ha az adatbázis biztonsági másolata régebbi a változáskövetési megőrzési időnél, vagy ha a hely biztonsági másolat nélküli helyreállítása.  

         Ha nem ad meg referenciahelyet, és a biztonsági másolat régebbi a változáskövetési megőrzési időnél, akkor minden elsődleges hely újra lesz inicializálva a központi adminisztrációs helyről visszaállított adatokkal.  

         Ha nem ad meg referenciahelyet, és a biztonsági másolat a változáskövetési megőrzési időn belül van, akkor csak a biztonsági mentés óta történt változások lesznek replikálva az elsődleges helyekről. Ha a különböző elsődleges helyekről származó módosítások ütköznek, a központi adminisztrációs hely az első fogadott módosítást használja.  

         Ezt a kulcsot kötelező megadni, ha a **DatabaseRecoveryOptions** beállítás értéke **40**.  

-   **Kulcsnév:** SiteServerBackupLocation  

    -   **Szükséges:** Nem  

    -   **Értékek:** &lt;PathToSiteServerBackupSet\>  

    -   **Részletek:** Meghatározza a helykiszolgáló biztonságimásolat-készletének elérési útvonalát. Ezt a kulcsot nem kötelező megadni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **2**. A helynek a róla készített biztonsági másolat használatával történő helyreállításához adjon meg értéket a **SiteServerBackupLocation** kulcshoz. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

-   **Kulcsnév:** BackupLocation  

    -   **Szükséges:** Talán  

    -   **Értékek:** &lt;PathToSiteDatabaseBackupSet\>  

    -   **Részletek:** Meghatározza a Helyadatbázis biztonságimásolat-készletének elérési útvonalát. A **BackupLocation** kulcsot meg kell adni, ha a **ServerRecoveryOptions** kulcshoz megadott érték **1** vagy **4** , és a **DatabaseRecoveryOptions** kulcs értékének **10** -et kell megadni.  

**Paraméterek**  

-   **Kulcsnév:** Termékazonosító  

    -   **Szükséges:** Igen  

    -   **Értékek:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         Eval  

    -   **Részletek:** A Configuration Manager telepítési termékkulcsa kötőjelekkel. Adja meg **Eval** telepítheti a Configuration Manager próbaverziója.  

-   **Kulcsnév:** Helykód  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;Helykód\>  

    -   **Részletek:** Három alfanumerikus karakter, amely egyedileg azonosítja a helyet a hierarchiában. Azt a helykódot kell megadni, amelyet a hely a hiba előtt használt.  

-   **Kulcsnév:** SiteName  

    -   **Szükséges:** Igen  

    -   **Értékek:** SiteName  

    -   **Részletek:** A hely ismertetése.  

-   **Kulcsnév:** SMSInstallDir  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;*ConfigMgr telepítési útvonala*>  

    -   **Részletek:** A Configuration Manager programfájljainak telepítési mappáját adja meg.  

        > [!NOTE]  
        >  Megadhatja az eredeti elérési utat vagy egy új útvonalat a Configuration Manager telepítéséhez.  

-   **Kulcsnév:** SDKServer  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;*SMS-szolgáltató teljes Tartományneve*>  

    -   **Részletek:** Megadja az SMS-szolgáltatót futtató kiszolgáló teljes Tartománynevét. Az SMS-szolgáltatót a hiba előtt futtató kiszolgáló nevét kell megadni.  

         A kezdeti telepítés után a helyre vonatkozóan további SMS-szolgáltatókat is meg lehet adni.  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltés  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha például a megadott érték 0, a telepítőprorgram letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;*Telepítő előfeltételfájljainak elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

-   **Kulcsnév:** AdminConsole  

    -   **Szükséges:** Talán  

    -   **Értékek:** 0 vagy 1  

         0 = nincs telepítés  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a Configuration Manager konzol telepítéséhez. Ezt a kulcsot meg kell adni, kivéve, ha a **ServerRecoveryOptions** beállítás értéke **4**.  

-   **Kulcsnév:** JoinCEIP  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs csatlakozás  

         1 = csatlakozás  

    -   **Részletek:** Megadja, hogy a felhasználói élmény fokozása Program csatlakozni.  

**SQLConfigOptions**  

-   **Kulcsnév:** SQLServerName  

    -   **Szükséges:** Igen  

    -   **Értékek:** *&lt;SQLServerName\>*  

    -   **Részletek:** A kiszolgáló nevét, vagy fürtözött példány neve, az SQL Server rendszert futtató a Helyadatbázis tárolására. A helyadatbázist a hiba előtt futtató kiszolgáló nevét kell megadni.  

-   **Kulcsnév:** DatabaseName  

    -   **Szükséges:** Igen  

    -   **Értékek:**  

         *&lt;Helyadatbázisneve\>*  

         vagy  

         *&lt;Példánynév\>*\\*&lt;Helyadatbázisneve\>*  

    -   **Részletek:** Az SQL Server-adatbázis létrehozása vagy a központi adminisztrációs hely adatbázisának telepítése neve. A hiba előtt használttal azonos adatbázisnevet kell megadni.  

        > [!IMPORTANT]  
        >  Ha nem az alapértelmezett példányt használja, meg kell adnia a példány és a helyadatbázis nevét.  

-   **Kulcsnév:** SQLSSBPort  

    -   **Szükséges:** Nem  

    -   **Értékek:** &lt;*SSB-port száma*>  

    -   **Részletek:** Adja meg az SQL Server által használt SQL Server Service Broker (SSB) porton. Az SSB általában a 4022-es TCP-port használatára van beállítva, de más portok használata is támogatott. A hiba előtt használttal azonos SSB-portot kell megadni.  

#### <a name="recover-a-primary-site-unattended"></a>Elsődleges hely felügyelet nélküli helyreállítása  
 A következő információk segítségével konfigurálhat egy felügyelet nélküli telepítési parancsfájlt a központi adminisztrációs hely helyreállítása.  

 **Azonosító**  

-   **Kulcsnév:** Művelet  

    -   **Szükséges:** Igen  

    -   **Értékek:** RecoverPrimarySite  

    -   **Részletek:** Elsődleges hely helyreállítására szolgál  

-   **Kulcsnév:** CDLatest  

    -   **Szükséges:** Igen – csak akkor, ha a CD-ről adathordozó használatával. Legfrissebb mappát.    

    -   **Értékek:** 1 értéke nem 1 tekintendő nem használja CD-ről. Legújabb.

    -   **Részletek:** A parancsfájl tartalmaznia a kulcs-érték telepítő CD-ről az adathordozóról való futtatásakor. Legújabb mappa céljából egy elsődleges vagy központi adminisztrációs hely telepítése, vagy egy elsődleges vagy központi adminisztrációs helyet állít helyre. Ez az érték tájékoztatja a beállítása, hogy a média CD alkotnak. Legutóbbi használatban van.

**RecoveryOptions**  

-   **Kulcsnév:** ServerRecoveryOptions  

    -   **Szükséges:** Igen  

    -   **Értékek:** 1, 2 vagy 4  

         1 = helykiszolgáló és SQL Server helyreállítása.  

         2 = csak a helykiszolgáló helyreállítása.  

         4 = csak az SQL Server helyreállítása.  

    -   **Részletek:** Megadja, hogy a telepítő állítja helyre a helykiszolgálót, az SQL Server, vagy mindkettőt. A kapcsolódó kulcsok akkor szükségesek, amikor a ServerRecoveryOptions beállításhoz megadja a következő értéket:  

        -   **Érték = 1** A **SiteServerBackupLocation** kulcshoz értéket megadva a helyről készített biztonsági másolat használatával állíthatja helyre az adott helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

             A **BackupLocation** kulcsot kötelező megadni, ha a **DatabaseRecoveryOptions** kulcsnál a megadott érték **10** , ami a hely adatbázisának biztonsági másolatból történő visszaállítását jelenti.  

        -   **Érték = 2** A **SiteServerBackupLocation** kulcshoz értéket megadva a helyről készített biztonsági másolat használatával állíthatja helyre az adott helyet. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

        -   **Érték = 4** : A **BackupLocation** kulcs értékét meg kell adni, ha a **DatabaseRecoveryOptions** kulcsnál a megadott érték **10** , ami a hely adatbázisának biztonsági másolatból történő visszaállítását jelenti.  

-   **Kulcsnév:** DatabaseRecoveryOptions  

    -   **Szükséges:** Talán  

    -   **Értékek:** 10, 20, 40, 80  

         10 = a hely adatbázisának visszaállítása biztonsági másolatból.  

         20 = más módszer alkalmazásával manuálisan helyreállított helyadatbázis használata.  

         40 = új adatbázis létrehozása a helyhez. Ezt a lehetőséget akkor kell használni, ha nem áll rendelkezésre biztonsági másolat a helyhez. A globális és a helyadatokat más helyekről történő replikációval állítja helyre a rendszer.  

         80 = az adatbázis helyreállításának kihagyása.  

    -   **Részletek:** Meghatározza, hogy a telepítő hogyan állítja helyre a helyadatbázist az SQL Server. Ezt a kulcsot meg kell adni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **4**.  

-   **Kulcsnév:** SiteServerBackupLocation  

    -   **Szükséges:** Nem  

    -   **Értékek:** &lt;PathToSiteServerBackupSet\>  

    -   **Részletek:** Meghatározza a helykiszolgáló biztonságimásolat-készletének elérési útvonalát. Ezt a kulcsot nem kötelező megadni, ha a **ServerRecoveryOptions** beállítás értéke **1** vagy **2**. A helynek a róla készített biztonsági másolat használatával történő helyreállításához adjon meg értéket a **SiteServerBackupLocation** kulcshoz. Ha nem ad meg értéket, a hely újratelepítése biztonságimásolat-készlet nélkül történik.  

-   **Kulcsnév:** BackupLocation  

    -   **Szükséges:** Talán  

    -   **Értékek:** &lt;PathToSiteDatabaseBackupSet\>  

    -   **Részletek:** Meghatározza a Helyadatbázis biztonságimásolat-készletének elérési útvonalát. A **BackupLocation** kulcsot meg kell adni, ha a **ServerRecoveryOptions** kulcshoz megadott érték **1** vagy **4** , és a **DatabaseRecoveryOptions** kulcs értékének **10** -et kell megadni.  

**Paraméterek**  

-   **Kulcsnév:** Termékazonosító  

    -   **Szükséges:** Igen  

    -   **Értékek:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         Eval  

    -   **Részletek:** A Configuration Manager telepítési termékkulcsa kötőjelekkel. Adja meg **Eval** telepítheti a Configuration Manager próbaverziója.  

-   **Kulcsnév:** Helykód  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;Helykód\>  

    -   **Részletek:** Három alfanumerikus karakter, amely egyedileg azonosítja a helyet a hierarchiában. Azt a helykódot kell megadni, amelyet a hely a hiba előtt használt.  

-   **Kulcsnév:** SiteName  

    -   **Szükséges:** Igen  

    -   **Értékek:** SiteName  

    -   **Részletek:** A hely ismertetése.  

-   **Kulcsnév:** SMSInstallDir  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;*ConfigMgr telepítési útvonala*>  

    -   **Részletek:** A Configuration Manager programfájljainak telepítési mappáját adja meg.  

        > [!NOTE]  
        >  Megadhatja az eredeti elérési utat vagy egy új útvonalat a Configuration Manager telepítéséhez.  

-   **Kulcsnév:** SDKServer  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;*SMS-szolgáltató teljes Tartományneve*>  

    -   **Részletek:** Megadja az SMS-szolgáltatót futtató kiszolgáló teljes Tartománynevét. Az SMS-szolgáltatót a hiba előtt futtató kiszolgáló nevét kell megadni.  

         A kezdeti telepítés után a helyre vonatkozóan további SMS-szolgáltatókat is meg lehet adni.  

-   **Kulcsnév:** PrerequisiteComp  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = letöltés  

         1 = már letöltve  

    -   **Részletek:** Meghatározza, hogy telepítéshez szükséges fájlok már töltve. Ha például a megadott érték 0, a telepítőprorgram letölti a fájlokat.  

-   **Kulcsnév:** PrerequisitePath  

    -   **Szükséges:** Igen  

    -   **Értékek:** &lt;*Telepítő előfeltételfájljainak elérési útja*>  

    -   **Részletek:** Meghatározza a telepítéshez szükséges fájlok elérési útvonalát. A telepítőprogram a **PrerequisiteComp** érték függvényében ennek az elérési útnak a használatával a letöltött fájlokat tárolja vagy megkeresi a korábban letöltött fájlokat.  

-   **Kulcsnév:** AdminConsole  

    -   **Szükséges:** Talán  

    -   **Értékek:** 0 vagy 1  

         0 = nincs telepítés  

         1 = telepítés  

    -   **Részletek:** Megadja, hogy a Configuration Manager konzol telepítéséhez. Ezt a kulcsot meg kell adni, kivéve, ha a **ServerRecoveryOptions** beállítás értéke **4**.  

-   **Kulcsnév:** JoinCEIP  

    -   **Szükséges:** Igen  

    -   **Értékek:** 0 vagy 1  

         0 = nincs csatlakozás  

         1 = csatlakozás  

    -   **Részletek:** Megadja, hogy a felhasználói élmény fokozása Program csatlakozni.  

**SQLConfigOptions**  

-   **Kulcsnév:** SQLServerName  

    -   **Szükséges:** Igen  

    -   **Értékek:** *&lt;SQLServerName\>*  

    -   **Részletek:** A kiszolgáló nevét, vagy fürtözött példány neve, az SQL Server rendszert futtató a Helyadatbázis tárolására. A helyadatbázist a hiba előtt futtató kiszolgáló nevét kell megadni.  

-   **Kulcsnév:** DatabaseName  

    -   **Szükséges:** Igen  

    -   **Értékek:**  

         *&lt;Helyadatbázisneve\>*  

         vagy  

         *&lt;Példánynév\>*\\*&lt;Helyadatbázisneve\>*  

    -   **Részletek:** Az SQL Server-adatbázis létrehozása vagy a központi adminisztrációs hely adatbázisának telepítése neve. A hiba előtt használttal azonos adatbázisnevet kell megadni.  

        > [!IMPORTANT]  
        >  Ha nem az alapértelmezett példányt használja, meg kell adnia a példány és a helyadatbázis nevét.  

-   **Kulcsnév:** SQLSSBPort  

    -   **Szükséges:** Nem  

    -   **Értékek:** &lt;*SSB-port száma*>  

    -   **Részletek:** Adja meg az SQL Server által használt SQL Server Service Broker (SSB) porton. Az SSB általában a 4022-es TCP-port használatára van beállítva, de más portok használata is támogatott. A hiba előtt használttal azonos SSB-portot kell megadni.  

**Hierarchiabővítési lehetőség**  

-   **Kulcsnév:** CCARSiteServer  

    -   **Szükséges:** Talán  

    -   **Értékek:** &lt;*Központi adminisztrációs hely helykódja*>  

    -   **Részletek:** Adja meg a központi adminisztrációs hely, amely egy elsődleges hely kapcsolódni fog, amikor bekerül a Configuration Manager-hierarchiában. Ez a beállítás kötelező, ha az elsődleges hely központi adminisztrációs helyhez volt csatlakoztatva a hiba előtt. Azt a helykódot kell megadni, amely a hiba előtt volt beállítva a központi adminisztrációs helyhez.  

-   **Kulcsnév:** CASRetryInterval  

    -   **Szükséges:** Nem  

    -   **Értékek:** &lt;*Időköz*>  

    -   **Részletek:** Megadja az újrapróbálkozási időköz (percben) a központi adminisztrációs helyhez való után a kapcsolat hibája esetén. Ha például nem sikerül kapcsolódni a központi adminisztrációs helyhez, az elsődleges hely annyi percig várakozik, amennyit megadott a CASRetryInterval beállításban, majd újrapróbálkozik a kapcsolódással.  

-   **Kulcsnév:** WaitForCASTimeout  

    -   **Szükséges:** Nem  

    -   **Értékek:** &lt;*Időtúllépés*>  

    -   **Részletek:** Meghatározza a maximális időkorlátot (percben) az elsődleges hely a központi adminisztrációs helyhez való kapcsolódáshoz. Ha például egy elsődleges hely nem tud kapcsolódni egy központi felügyeleti helyhez, az elsődleges hely újrapróbálja a kapcsolódást a központi felügyeleti helyhez a CASRetryInterval alapján, amíg el nem éri a WaitForCASTimeout időtartamot. 0 és 100 közötti értéket lehet megadni.  

###  <a name="BKMK_PostRecovery"></a> Helyreállítás utáni feladatok  
 Miután helyreállította a helyet, van néhány helyreállítás utáni feladat, amelyeket érdemes elvégezni a helyhelyreállítás befejezéséhez. A következő részekben leírtak segítségével befejezheti a hely helyreállításának folyamatát.  

#### <a name="re-enter-user-account-passwords"></a>Felhasználóifiók-jelszavak újbóli megadása  
 Egy helykiszolgáló helyreállítása után a helyhez megadott felhasználóifiók-jelszavakat újra be kell írni, mert a hely helyreállításakor alapértékre állnak. A fiókok a telepítési varázsló **Kész** lapján láthatók, miután a hely helyreállítása befejeződött és mentésre került a C:\ConfigMgrPostRecoveryActions.html fájlba a helyreállított helykiszolgálón.  

###### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>Felhasználói fiókok jelszavainak újbóli megadása helyhelyreállítás után  

1.  Nyissa meg a Configuration Manager konzolt, és csatlakozzon a helyreállított helyhez.  

2.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

3.  A **Felügyelet** munkaterületen bontsa ki a **Biztonság**csomópontot, majd kattintson a **Fiókok**lehetőségre.  

4.  Minden olyan fiókhoz, amelyhez újra meg kell adni a jelszót, tegye a következőt:  

    1.  Válassza ki a fiókot a helyhelyreállítás után azonosított fiókok listájában. A lista a C:\ConfigMgrPostRecoveryActions.html fájlban található a helyreállított helykiszolgálón.  

    2.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok** elemre a fióktulajdonságok megnyitásához.  

    3.  Az **Általános** lapon kattintson a **Beállítás**lehetőségre, majd írja be újra a fiók jelszavait.  

    4.  Kattintson az **Ellenőrzés**lehetőségre, válassza ki a megfelelő adatforrást a kijelölt felhasználói fiókhoz, majd kattintson a **Kapcsolat tesztelése** elemre annak ellenőrzéséhez, hogy a felhasználói fiók kapcsolódni tud az adatforráshoz.  

    5.  Kattintson az **OK** gombra a jelszómódosítások mentéséhez, majd kattintson ismét az **OK**gombra.  

#### <a name="re-enter-sideloading-keys"></a>Közvetlen telepítési kulcsok újbóli megadása  
 Egy helykiszolgáló helyreállítása után a helyhez megadott közvetlen Windows-telepítési kulcsokat újra be kell írni, mert a hely helyreállításakor alapértékre állnak. A közvetlen telepítési kulcsokat, a száma, az ismételt megadását követően a **felhasznált aktiválások** oszlop Windows-telepítési kulcsok alaphelyzetbe áll a Configuration Manager konzolon. Például tegyük fel, a hely meghibásodását megelőzően egy **összes aktiválás** számlálóérték **100** és **felhasznált aktiválások** jelenleg **90** az eszközök által használt kulcsok számát. A hely helyreállítása után az **Összes aktiválás** oszlopban továbbra is a **100**érték látható, de a **Felhasznált aktiválások** oszlopban a helytelen **0**érték jelenik meg. Miután azonban 10 új eszköz felhasznál egy-egy közvetlen telepítési kulcsot, nem marad több közvetlen telepítési kulcs, és a következő eszközre nem lehet kulcsot alkalmazni.  

#### <a name="recreate-the-microsoft-intune-subscription"></a>A Microsoft Intune-előfizetés ismételt létrehozása  
 Ha a Configuration Manager helykiszolgáló módosítása után állít helyre a helykiszolgáló számítógép rendszer újra telepíti, a Microsoft Intune-előfizetést nem állítja vissza. A hely helyreállítását követően csatlakoztatnia kell az előfizetéshez.  Ne hozzon létre egy új APN-kérelmet, de ehelyett a jelenlegi érvényes .pem-fájl feltöltéséhez az iOS kezelésének lett konfigurálva, vagy megújítani legutóbbi feltöltött. További információ: [A Windows Intune-előfizetés konfigurálása](/sccm/mdm/deploy-use/configure-intune-subscription).  

#### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>Az SSL konfigurálása az IIS-t használó helyrendszerszerepkörökhöz  
 Ha az IIS-t futtató, a meghibásodást megelőzően HTTPS használatára konfigurált helyrendszert állít helyre, akkor újra kell konfigurálnia az IIS-t a webkiszolgáló-tanúsítvány használatára.  

#### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>Gyorsjavítások újratelepítése a helyreállított helykiszolgálón  
 Egy hely helyreállítását követően újra kell telepítenie minden gyorsjavítást, amelyet a helykiszolgálóra korábban telepítettek. A korábban telepített gyorsjavítások listája a hely helyreállítása után megjelenik a telepítési varázsló **Kész** lapján, illetve a rendszer menti a **C:\ConfigMgrPostRecoveryActions.html** fájlba a helyreállított helykiszolgálón.  

#### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Egyéni jelentések helyreállítása a Reporting Servicest futtató számítógépen  
 Ha egyéni Reporting Services-jelentéseket készített, és a Reporting Services meghibásodik, akkor a jelentéskészítési kiszolgáló biztonsági másolatából helyreállíthatja a jelentéseket. Ha többet szeretne tudni a Reporting Services szolgáltatásbeli egyéni jelentések visszaállításáról, olvassa el a [Biztonsági mentési és helyreállítási műveletek Reporting Services-telepítéshez](http://go.microsoft.com/fwlink/p/?LinkId=228724) című részt az SQL Server 2008 Books Online webhelyen.  

#### <a name="recover-content-files"></a>Tartalomfájlok helyreállítása  
 A helyadatbázis információt tárol arról, hogy hol találhatók a tartalomfájlok a helykiszolgálón, de a tartalomfájlok biztonsági mentése és visszaállítása nem történik meg a biztonsági mentési és helyreállítási folyamat részeként. A tartalomfájlok teljes helyreállításához vissza kell állítania a tartalomtárat és a csomagforrásfájlokat az eredeti helyükre. A tartalomfájlok többféleképpen is helyreállíthatók, de a legegyszerűbb módszer a helyrendszer fájlrendszeréről készült biztonsági másolatból való visszaállítás.  

 Ha nem áll rendelkezésre a fájlrendszerről a csomagforrásfájlokat tartalmazó biztonsági másolat, akkor saját kezűleg bemásolhatja vagy letöltheti a fájlokat ugyanúgy, ahogy eredetileg tette a csomag létrehozásakor. Az SQL Serverben a következő lekérdezéssel keresheti meg a csomagforrás helyét az összes csomaghoz és alkalmazáshoz: `SELECT * FROM v_Package`. A csomag forráshelyét a csomagazonosító első három karaktere alapján azonosíthatja. Ha például a csomagazonosító CEN00001, a forráshely helykódja CEN. A csomagforrásfájlokat ugyanarra a helyre kell visszaállítani, ahol a meghibásodás előtt voltak.  

 Ha nem áll rendelkezésre a tartalomtárat magában foglaló biztonsági másolat a helyrendszerről, akkor a következő visszaállítási eljárások alkalmazhatók:  

-   **A manuálisan előkészített tartalomfájl importálása**: Ha a Configuration Manager-hierarchiában, az összes csomaggal és alkalmazással egy másik helyről manuálisan előkészített tartalomfájl létrehozása, és importálhatja a manuálisan előkészített tartalomfájlt a tartalomtár a helykiszolgálón való helyreállításához.  

-   **Tartalom frissítése**: Amikor elindítja a tartalomfrissítési műveletet egy csomag vagy alkalmazás típusú központi telepítéshez, a tartalomtárba másolja a csomagforrásból a tartalomtárba. A csomag forrásfájljainak elérhetőnek kell lenniük az eredeti helyen ahhoz, hogy ez a művelet sikeresen záruljon. A műveletet minden egyes csomagon és alkalmazáson el kell végezni.  

#### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Egyéni szoftverfrissítések helyreállítása az Updates Publishert futtató számítógépen  
 Ha a frissítés-közzétevő adatbázisfájlok a biztonsági mentési terv is kiterjed, akkor helyreállíthatja az adatbázisokat az Updates Publishert futtató számítógép meghibásodása esetén. Az Updates Publisherrel kapcsolatos további tudnivalókért lásd a [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) dokumentumot a System Center TechCenter tárban.  

 A következő eljárás használatával állítsa vissza az Updates Publisher adatbázisában.  

###### <a name="to-restore-the-updates-publisher-2011-database"></a>Az Updates Publisher 2011 adatbázisának biztonsági visszaállítása  

1.  Telepítse újra a frissítés-közzétevő a helyreállított számítógépen.  

2.  Másolja az adatbázisfájlt (Scupdb.sdf) a biztonsági mentési célhelyről %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\ mappájába az Updates Publishert futtató számítógépen.  

3.  Ha egynél több felhasználó Updates Publisher a számítógépen fut, a minden adatbázisfájlt a megfelelő felhasználói profil mappájába át kell másolnia.  

#### <a name="user-state-migration-data"></a>Felhasználóáttelepítési adatok  
 Az állapotáttelepítési pont helyrendszerbeli tulajdonságainak beállításakor megadja a felhasználói állapot áttelepítési adatait tartalmazó mappákat. Miután helyreállít egy felhasználóáttelepítési adatokat tároló mappát tartalmazó kiszolgálót, manuálisan vissza kell állítania a felhasználóáttelepítési adatokat a kiszolgáló ugyanazon mappáiba, amelyek a meghibásodás előtt tárolták az adatokat.  

#### <a name="regenerate-the-certificates-for-distribution-points"></a>A terjesztési pontok tanúsítványainak újbóli létrehozása  
 A hely visszaállítása után a distmgr.log naplófájlban egy vagy több terjesztési pontot a következő bejegyzés szerepelhet: **Nem sikerült a tanúsítvány PFX-adatainak visszafejtése**. Ez a bejegyzés azt jelzi, hogy a hely nem tudja visszafejteni a terjesztési pont tanúsítványának adatait. A probléma megoldásához újból létre kell hoznia vagy újból importálnia kell az érintett terjesztési pontok tanúsítványát. Ezt a [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx) PowerShell-parancsmag használatával teheti meg.  

#### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>A felhőalapú terjesztési pontokhoz használt tanúsítványok frissítése  
 A Configuration Manager megköveteli egy felügyeleti tanúsítványra, amelyet a helykiszolgáló és a felhő alapú terjesztési pontok közötti kommunikációhoz használ. Egy hely helyreállítását követően frissítenie kell a felhőalapú terjesztési pontok tanúsítványait.  

####  <a name="BKMK_RecoverSecondarySite"></a> Másodlagos hely helyreállítása  
 A Configuration Manager nem támogatja az adatbázis biztonsági másolatát a másodlagos helyen, de támogatja a másodlagos hely újratelepítésével történő helyreállítást. Másodlagos hely helyreállítására szükség a Configuration Manager másodlagos helye meghibásodik. A másodlagos helyek használatával helyreállíthatja a **másodlagos hely visszaállítása** művelet a **helyek** csomópont a Configuration Manager konzolon. A központi adminisztrációs hely vagy az elsődleges hely helyreállításával szemben a másodlagos helyek helyreállítása nem biztonsági másolatból történik; ehelyett a Configuration Manager telepíti a másodlagos hely fájljait a másodlagos hely számítógépén, majd annak adatait újrainicializálja a szülő elsődleges hely adataival. A helyreállítási folyamat során a Configuration Manager ellenőrzi, hogy a tartalomtár létezik-e a másodlagos hely számítógépén, és hogy elérhető legyen-e a megfelelő tartalom. A másodlagos hely a meglévő tartalomtárat használja, ha az a megfelelő tartalmat tartalmazza. Ellenkező esetben a helyreállított másodlagos hely tartalomtárát újra kell terjeszteni, vagy manuálisan elő kell készíteni a tartalmat a helyreállított helyen. Ha olyan terjesztési ponttal rendelkezik, amely nem a másodlagos helyen található, akkor nem szükséges újratelepíteni a terjesztési pontot a másodlagos hely helyreállítása során. A másodlagos hely helyreállítását követően a hely automatikusan szinkronizálást végez a terjesztési ponttal.  

 Másodlagos hely visszaállításának állapotát segítségével ellenőrizheti a **telepítési állapot megjelenítése** művelet a **helyek** csomópont a Configuration Manager konzolon.  

> [!IMPORTANT]  
>  A meghibásodott számítógéppel azonos konfigurációjú (például azonos teljes tartománynevű) számítógépet kell használnia a másodlagos hely sikeres helyreállításához. A számítógépnek ezenkívül meg kell felelnie a másodlagos helyek előfeltételeinek is, illetve megfelelő biztonsági engedélyekkel kell rendelkeznie. Használja továbbá ugyanazt a telepítési útvonalat, amelyet a meghibásodott helyhez használt.  

> [!IMPORTANT]  
>  A másodlagos hely helyreállítása során a Configuration Manager nem telepíthető SQL Server Express Ha nincs telepítve a számítógépen. Ezért a másodlagos hely helyreállítása előtt saját kezűleg kell telepítenie az SQL Server Expresst vagy az SQL Servert. Az SQL Server ugyanazon verzióját és példányát kell használnia, amelyet a meghibásodás előtt használt a másodlagos hely adatbázisához.  

##  <a name="BKMK_SMSWriterService"></a> SMS-író szolgáltatás  
 Az SMS-író egy olyan szolgáltatás, amely együttműködik a Kötet árnyékmásolata szolgáltatással (VSS) a biztonsági mentési folyamat során. Az SMS-író szolgáltatásnak futnia kell a Configuration Manager-hely biztonsági akár sikeresen befejeződik.  

### <a name="purpose"></a>Cél  
 Az SMS-író regisztrálja magát a VSS szolgáltatásban, és kötést hoz létre annak felületeihez és eseményeihez. Amikor a VSS közzéteszi az eseményeket, vagy ha meghatározott értesítéseket küld az SMS-írónak, akkor az SMS-író válaszol az értesítésre, és végrehajtja a megfelelő műveletet. Az SMS-író beolvassa a található a biztonsági mentés vezérlőfájljának (smsbkup.ctl) a &lt; *ConfigMgr telepítési útvonala*> \inboxes\smsbkup.box, és meghatározza azokat a fájlokat és adatokat, amelyek biztonsági mentése. Az SMS-író metaadatokat hoz létre, amelyek ezeken az adatokon alapuló különböző összetevőkből, valamint az SMS beállításkulcsában és alkulcsaiban lévő meghatározott adatokból állnak. Az SMS-író kérés esetén elküldi a metaadatokat a VSS szolgáltatásnak. VSS ezután elküldi a metaadatokat az azokat kérő alkalmazásnak; A Configuration Manager biztonságimásolat-kezelőjének. A biztonságimásolat-kezelő kiválasztja a mentendő adatokat, és a VSS szolgáltatáson keresztül elküldi azokat az SMS-írónak. Az SMS-író végrehajtja a biztonsági mentés előkészítéséhez szükséges műveleteket. Később amikor VSS készen áll a pillanatkép elkészítésére, küld egy eseményt, az SMS-író leállítja az összes Configuration Manager szolgáltatást, és biztosítja, hogy a Configuration Manager tevékenységei szüneteltetve legyenek-e, a pillanatkép elkészítése közben. Miután elkészült a pillanatkép, az SMS-író újraindítja a szolgáltatásokat és a tevékenységeket.  

 A rendszer automatikusan telepíti az SMS-író szolgáltatást. A szolgáltatásnak futnia kell, amikor a VSS alkalmazás biztonsági mentést vagy helyreállítást kér.  

### <a name="writer-id"></a>Író azonosítója  
 Az SMS-író azonosítója a következő: 03ba67dd-dc6d-4729-a038-251f7018463b.  

### <a name="permissions"></a>Engedélyek  
 Az SMS-író szolgáltatást a helyi rendszerfiókból kell futtatni.  

### <a name="volume-shadow-copy-service"></a>Kötet árnyékmásolata szolgáltatás  
 A Kötet árnyékmásolata szolgáltatás (VSS) a COM API-k olyan készlete, amelyek egy keretrendszert valósítanak meg, amellyel biztonsági mentések készíthetők a kötetekről úgy, hogy közben a rendszerben lévő alkalmazások továbbra is írhatnak a kötetekre. A VSS egységes illesztőfelületet biztosít, amely lehetővé teszi a lemezen lévő adatokat frissítő felhasználói alkalmazások (az SMS-író szolgáltatás) és biztonsági mentést készítő alkalmazások (biztonságimásolat-kezelő szolgáltatás) működésének összehangolását. A VSS részletes ismertetését lásd: [Kötet árnyékmásolata szolgáltatás](http://go.microsoft.com/fwlink/p/?LinkId=241968) témakör, Windows Server TechCenter.  

