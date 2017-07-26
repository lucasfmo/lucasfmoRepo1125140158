---
title: "Gyorsjavítás-telepítő |} Microsoft Docs"
description: "Tudni, mikor és hogyan keresztül a gyorsjavítás-telepítő a Configuration Manager frissítéseinek telepítéséhez."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f3058277-c597-4dac-86d1-41b6f7e62b36
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 8ffc7383e895909e6e6c4b8a7875fd5f0df2220e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-hotfix-installer-to-install-updates-for-system-center-configuration-manager"></a>A gyorsjavítás-telepítő használata a System Center Configuration Manager frissítéseinek telepítéséhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Néhány frissítés a System Center Configuration Manager nem érhetők el a Microsoft felhőszolgáltatásához, és csak akkor kapja meg a sávon kívüli. Ilyenek például a konkrét problémák megoldására szolgáló, korlátozott kiadású gyorsjavítások.   
Ha telepítenie kell a frissítés (vagy gyorsjavítást), amelyet a Microsofttól kapott, és a frissítési a fájl nevét, amely kiterjesztése **.exe** (nem **update.exe**), a frissítés a közvetlenül a Configuration Manager helykiszolgáló letöltött mellékelt gyorsjavítás-telepítő használata.  

 Ha a gyorsjavítás fájlnevének a **. update.exe** kiterjesztése című [a Frissítésregisztráló eszköz segítségével importálja a gyorsjavítást a System Center Configuration Manager](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md).  

> [!NOTE]  
>  Ez a témakör általános útmutatást ad a System Center Configuration Managert frissítő gyorsjavítások telepítéséről. Az egyes frissítések részletes ismertetését a megfelelő tudásbáziscikk tartalmazza a Microsoft támogatási szolgálatának webhelyén.  

##  <a name="bkmk_Overview"></a>A Configuration Manager gyorsjavítások áttekintése  
 A Configuration Manager gyorsjavítások hasonlóak a más Microsoft-termékek, például az SQL Server, vagy egy különálló javítást, vagy egy csomagot (összesített javításokat) tartalmaznak, és ismerteti a Microsoft Tudásbázis megfelelő cikkében.  

 Egyedi frissítések egyetlen célirányos frissítést egy adott verziójához a Configuration Manager tartalmaznak.  
Frissítési csomagok több frissítést egy adott verziójához a Configuration Manager tartalmaznak.  
Összesített frissítés esetén az adott csomagban található frissítések külön-külön nem telepíthetők.  

 Ha a frissítéseket központi telepítéssel tervezi további számítógépeken telepíteni, a frissítési csomagot központi adminisztrációs helykiszolgálón vagy elsődleges helykiszolgálón kell telepítenie.  

 A frissítési csomag futtatásakor a következő történik:  

-   A frissítési csomag kibontja a frissítési fájlokat minden egyes megfelelő összetevőhöz.  

-   Elindít egy varázslót, amely végigvezeti a frissítések és a kapcsolódó telepítési lehetőségek konfigurálási folyamatán.  

-   A beállítások megadása után a varázsló telepíti a helykiszolgálóra a csomagban lévő olyan frissítéseket, amelyek a helykiszolgálóra vonatkoznak.  

A varázsló emellett központi telepítéseket is létrehoz, amelyeket felhasználhat a frissítések további számítógépekre történő telepítéséhez. A frissítéseket egy támogatott központi telepítési módszer, például szoftvertelepítési csomag vagy a Microsoft System Center Updates Publisher 2011 segítségével telepítheti további számítógépekre.  

 A varázsló a futtatása közben létrehoz egy **.cab-fájlt** a helykiszolgálón az Updates Publisher 2011 számára. A varázslót konfigurálhatja úgy is, hogy létrehozzon egy vagy több csomagot a szoftverek központi telepítéshez. A központi telepítéseket segítségével telepítheti a frissítéseket az összetevőkön, például az ügyfelek vagy a Configuration Manager konzolon. Frissítéseket kézzel is telepítheti a számítógépeken, amelyeken nem fut a Configuration Manager-ügyfél.  

 A Configuration Manager a következő három csoport frissíthető:  

-   A Configuration Manager kiszolgálói szerepkörök, többek között:  

    -   Központi adminisztrációs hely  

    -   Elsődleges hely  

    -   Másodlagos hely  

    -   Távoli SMS-szolgáltató  

-   Configuration Manager-konzol  

-   Configuration Manager-ügyfél  

> [!NOTE]  
>  **A helyrendszerszerepkörök frissítések** (többek között a következőket frissítései a Helyadatbázis és a felhő alapú terjesztési pontok) vannak telepítve a frissítést a Helykiszolgálók és a szolgáltatások részeként a helyösszetevő-kezelő által.  
>   
>  Azonban a frissítések a lekéréses terjesztési pontok terjesztéskezelő végzi a helyösszetevő-kezelő helyett.  

 Mindegyik frissítési csomagja a Configuration Manager egy önkibontó .exe fájl (SFX), amely a frissítés a Configuration Manager megfelelő összetevőinek telepítéséhez szükséges fájlokat tartalmazza. Az SFX-fájl rendszerint a következő fájlokat tartalmazza:  

|Fájl|Részletek|  
|----------|-------------|  
|&lt;Termékverzió\>- QFE-KB&lt;KB cikk azonosítója\>-&lt;platform\>-&lt;nyelvi\>.exe|Ez a frissítésfájl. A fájl parancssorát az Updatesetup.exe felügyeli.<br /><br /> Példa:<br />CM1511RTM-QFE-KB123456-X 64-ENU.exe|  
|Updatesetup.exe|Ez az .msi-burkoló felügyeli a frissítési csomag telepítését.<br /><br /> A frissítés futtatásakor az Updatesetup.exe felismeri azon számítógép megjelenítési nyelvét, amelyen futtatva van. A frissítés felhasználói felületének nyelve alapértelmezés szerint angol. Ha azonban a megjelenítési nyelv támogatott, a felhasználói felület a számítógép helyi nyelvének megfelelően jelenik meg.|  
|Licenc_&lt;nyelv\>.rtf|Ha alkalmazható, mindegyik frissítés tartalmaz egy vagy több licencfájlt a támogatott nyelvekhez.|  
|&lt;Termék és frissítés típusa >-&lt;termékverzió\>-&lt;KB cikk azonosítója\>-&lt;platform\>.msp|Ha a frissítés a Configuration Manager konzolra vagy az ügyfelekre vonatkozik, a frissítési csomag különálló Windows Installer-javítófájlok (.msp) fájlok magában foglalja.<br /><br /> Példa:<br /><br /> **A Configuration Manager-konzol frissítése:** ConfigMgr1511-AdminUI-KB1234567-i386.msp<br /><br /> **Ügyfél frissítése:** ConfigMgr1511-client-KB1234567-i386.msp<br />ConfigMgr1511-client-KB1234567-x64.msp|  

 A frissítési csomag alapértelmezés szerint .log-fájlban naplózza a tevékenységeit a helykiszolgálón. A naplófájl neve megegyezik a frissítési csomag nevével, és a **%SystemRoot%/Temp** mappában található.  

 A frissítési csomag a futtatáskor a csomag kibont egy önmagával megegyező nevű fájlt a számítógép egy ideiglenes mappájába, majd futtatja az Updatesetup.exe fájlt. Updatesetup.exe elindítja a szoftverfrissítést a Configuration Manager &lt;termékverzió\> &lt;tudásbáziscikk\> varázsló.  

 Alkalmazhatók a frissítés hatókörének, a varázsló létrehoz több mappát a System Center Configuration Manager telepítési mappájában a helykiszolgálón. A mappastruktúra a következőhöz hasonló:   
 **\\\\&lt;Server Name\>\SMS_&lt;Site Code\>\Hotfix\\&lt;KB Number\>\\&lt;Update Type\>\\&lt;Platform\>**.  

 A következő táblázat tartalmazza a mappastruktúrában található mappák adatait:  

|Mappanév|További információ|  
|-----------------|----------------------|  
|&lt;Kiszolgáló neve\>|Annak a helykiszolgálónak a neve, amelyen a frissítési csomagot futtatja.|  
|SMS_&lt;Helykód\>|Ez az a Configuration Manager telepítési mappájának megosztásneve.|  
|&lt;Tudásbáziscikk száma\>|A frissítési csomaghoz tartozó tudásbáziscikk azonosítószáma.|  
|&lt;Frissítés típusa\>|Ezek a frissítések a Configuration Manager típusú. A varázsló külön mappát hoz létre a frissítési csomagban található mindegyik frissítéstípushoz. A mappanevek megfelelnek a frissítések típusának. Ezek a következők:<br /><br /> **Kiszolgáló**: Helykiszolgálók, a Helyadatbázis-kiszolgálók és az SMS-szolgáltatót futtató számítógépek frissítéseit tartalmazza.<br /><br /> **Ügyfél**: A Configuration Manager-ügyfél frissítéseit tartalmazza.<br /><br /> **AdminConsole**: A Configuration Manager konzol frissítéseit tartalmazza<br /><br /> A fenti frissítéstípusok mellett a varázsló létrehoz egy nevű mappát **SCUP**. Ez a mappa nem frissítési típust jelöl, hanem az Updates Publisher .cab-fájlját tartalmazza.|  
|&lt;Platform\>|Ez egy platformspecifikus mappa. A processzortípusnak megfelelő frissítésfájlokat tartalmaz.  Ezek a mappák a következők:<br /><br />-x64<br /><br /> -I386|  

##  <a name="bkmk_Install"></a> A frissítések telepítésének módja  
 A frissítések telepítéséhez előbb a frissítési csomagot kell telepíteni egy helykiszolgálóra. Amikor telepít egy frissítési csomagot, elindul az adott frissítéshez tartozó telepítési varázsló. A varázsló a következőket teszi:  

-   Kibontja a frissítési fájlokat  

-   Segít a központi telepítés konfigurálásában  

-   Telepíti a megfelelő frissítéseket a helyi számítógép kiszolgáló-összetevőire  

Telepítése után a frissítési csomagot egy helykiszolgálóra, frissítheti a további összetevők a Configuration Manager számára. A következő táblázat írja le az összetevők frissítési műveleteit:  

|Összetevő|Utasítások|  
|---------------|------------------|  
|Helykiszolgáló|Központilag telepítse a frissítéseket egy távoli helykiszolgálóra, amikor a frissítési csomagot nem telepíti közvetlenül az adott távoli helykiszolgálóra.|  
|Helyadatbázis|A távoli helykiszolgálók esetében központilag telepítse a helyadatbázis frissítését tartalmazó kiszolgálófrissítéseket, ha a frissítési csomagot nem telepíti közvetlenül az adott távoli helykiszolgálóra.|  
|Configuration Manager-konzol|A Configuration Manager konzol első telepítése után telepítheti a Configuration Manager konzol frissítéseit minden olyan számítógépen, amelyen fut a konzol. A frissítések alkalmazásához a konzol első telepítése közben a Configuration Manager konzol telepítőfájljait nem módosíthatja.|  
|Távoli SMS-szolgáltató|Telepítse a frissítéseket az SMS Provider minden példányára, amely a frissítési csomag telepítéséhez választott helykiszolgálótól eltérő számítógépen fut.|  
|Configuration Manager-ügyfelek|A Configuration Manager-ügyfél első telepítése után a Configuration Manager-ügyfél minden számítógépen, amelyen fut az ügyfél telepítése a frissítések.|  

> [!NOTE]  
>  A frissítéseket a Configuration Manager-ügyfelet futtató számítógépekre.  

 Ha egy ügyfél, a Configuration Manager-konzol vagy az SMS-szolgáltató újratelepítése, ezen összetevők frissítéseit is újra kell telepítenie.  

 Az alábbi szakaszokban található információk segítségével telepítheti a frissítéseket az egyes összetevők a Configuration Manager.  

###  <a name="bkmk_servers"></a> Kiszolgálók frissítései  
 A kiszolgálók frissítései tartalmazhatják a **helyek**, a **site database**és az **SMS Provider**példányait futtató számítógépek frissítéseit:  

####  <a name="bkmk_site"></a>Hely frissítése  
 A Configuration Manager-hely frissítéséhez a frissítési csomagot telepítheti közvetlenül a helykiszolgálón, vagy a frissítéseket telepítheti egy helykiszolgálóra, miután telepítette a frissítési csomagot egy másik helyre.  

 Amikor frissítést telepít egy helykiszolgálóra, a frissítés telepítési folyamata felügyeli a frissítés telepítéséhez szükséges további műveleteket, például a helyrendszerszerepkörök frissítését. Ez alól kivétel a helyadatbázis. A következő rész ismerteti a helyadatbázis frissítését.  

####  <a name="bkmk_database"></a>Helyadatbázis frissítése  
 A Helyadatbázis frissítéséhez a telepítési folyamat egy nevű fájlt futtat **update.sql** a helyadatbázisban. A frissítési folyamatot beállíthatja a helyadatbázis automatikus frissítésére, vagy kézzel is frissítheti később a helyadatbázist.  

 **A Helyadatbázis automatikus frissítése**  

 Amikor telepíti a frissítési csomagot egy helykiszolgálóra, dönthet úgy, hogy a Helyadatbázis automatikus frissítését, ha a kiszolgáló frissítés telepítve van. Ez a döntés csak azokra a helykiszolgálón, amelyen a frissítési csomagot telepíti, és nem vonatkozik a frissítések távoli helykiszolgálókon telepítéséhez létrehozott központi telepítések.  

> [!NOTE]  
>  Ha úgy dönt, hogy a Helyadatbázis automatikus frissítését, a folyamat frissíti az adatbázist, függetlenül attól, hogy az adatbázis nem található a helykiszolgálón vagy egy távoli számítógépen.  

> [!IMPORTANT]  
>  Mielőtt frissíti a helyadatbázist, a Helyadatbázis biztonsági másolatot készíteni. A helyadatbázis frissítését nem távolíthatja el. Biztonsági másolat a Configuration Manager létrehozásával kapcsolatos további információkért lásd: [biztonsági mentés és helyreállítás a System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **A Helyadatbázis kézi frissítése**  

 Ha nem kíván a Helyadatbázis automatikus frissítését, amikor a frissítési csomag telepítését a helykiszolgálón, a kiszolgáló frissítése nem módosítja az adatbázist, a frissítési csomagot futtató helyrendszer-kiszolgálón. A szoftvertelepítéshez létrehozott vagy, amely mindig telepíti a csomagot használó központi telepítések azonban a Helyadatbázis frissítését.  

> [!WARNING]  
>  A frissítés tartalmazza a frissítéseket a helykiszolgáló és a Helyadatbázis, a frissítés esetén nem működési mindaddig, amíg a frissítés befejeződött, a helykiszolgáló és a hely adatbázisába. A frissítés telepítéséig a Helyadatbázis, a hely nem támogatott állapotban van.  

 **Helyadatbázis manuális frissítése:**  

1.  A hely kiszolgálóján állítsa le az sms_site_component_manager, és állítsa le az SMS_EXECUTIVE szolgáltatást.  

2.  A Configuration Manager konzol bezárásához.  

3.  Futtassa a nevű frissítési parancsfájlt **update.sql** a hely adatbázisához. SQL Server-adatbázis frissítése egy parancsfájl futtatásával kapcsolatos információkért lásd: a Helyadatbázis-kiszolgáló használt SQL Server verziójának a dokumentációjában.  

4.  Újraindítás az előző lépésekben leállított szolgáltatásokat.  

5.  Ha a frissítési csomag kibontja **update.sql** a helykiszolgálón a következő helyre:  **\\\\&lt;Kiszolgálónév\>\SMS_&lt;Helykód\>\Hotfix\\&lt;tudásbáziscikk\>\update.sql**  

####  <a name="bkmk_provider"></a>Az SMS Providert futtató számítógép frissítése  
 Miután telepítette a frissítési csomag, amely az SMS Provider frissítését is tartalmazza, a frissítést kell telepítenie minden olyan számítógépen, az SMS-szolgáltatót futtató. Ez alól csak az SMS Provider azon példánya kivétel, amelyik előzőleg lett telepítve arra a helykiszolgálóra, amelyikre a frissítési csomagot telepítette. A helykiszolgálón az SMS Provider helyi példánya akkor frissül, amikor a frissítési csomagot telepíti.  

 Ha eltávolítja, majd telepítse újra az SMS-szolgáltató egy számítógépen meg kell telepíteni a SMS Provider frissítését a számítógépen.  

###  <a name="BKMK_clients"></a>Ügyfelek frissítése  
 Ha olyan frissítést telepít, amely a Configuration Manager-ügyfél frissítését is tartalmazza, lehetősége lesz a telepítés ügyfelek automatikus frissítése, vagy manuálisan frissítse az ügyfeleket egy későbbi időpontban. További információ az ügyfél automatikus frissítéséről: [A Windows rendszerű számítógépekhez készült ügyfelek frissítése](https://technet.microsoft.com/library/mt627885.aspx)gyorsjavításainak telepítéséhez.  

 A frissítések központilag telepíthetők az Updates Publisher használatával vagy a szoftver központi telepítési csomagjával, illetve manuálisan is telepítheti a frissítést az egyes ügyfelekre. Ha további információkat szeretne arról, hogy hogyan használhatja a központi telepítést a frissítések telepítésére, olvassa el az aktuális témakör [A Configuration Manager frissítéseinek központi telepítése](#BKMK_Deploy) , ebben a témakörben.  

> [!IMPORTANT]  
>  Ha az ügyfelek frissítéseinek telepítésekor, és a frissítési csomag kiszolgálók frissítését is tartalmazza, ügyeljen arra, hogy a kiszolgálói frissítések települnek arra az elsődleges hely, amelyhez az ügyfelek hozzá vannak rendelve is.  

Az ügyfél frissítése manuálisan telepíthető egyes Configuration Manager-ügyfél, futtatnia kell **Msiexec.exe** , és hivatkozik a platform-specifikus ügyfélfrissítés .msp fájljára.  

 Az ügyfélfrissítéshez például használhatja a következő parancsot. Ez a parancssor futtatja az MSIEXEC az ügyfélszámítógépen, és hivatkozik arra az .msp fájlra, amely a frissítési csomag kibontott a helykiszolgálón: **msiexec.exe /p \\ \\ &lt;kiszolgálónév\>\SMS_&lt;Helykód\>\Hotfix\\&lt;tudásbáziscikk\>\Client\\&lt;Platform\>\\&lt;msp\> /l\*v &lt;logfile\>REINSTALLMODE = mous REINSTALL = ALL**  

###  <a name="BKMK_console"></a>A Configuration Manager konzolok frissítése  
 A Configuration Manager konzol frissítését, telepítenie kell a frissítés a konzol telepítésének befejezése után a konzolt futtató számítógép.  

> [!IMPORTANT]  
>  Ha a Configuration Manager-konzol frissítéseinek telepítésekor, és a frissítési csomag kiszolgálók frissítését is tartalmazza, ügyeljen arra, hogy a kiszolgálói frissítések települnek arra a webhely, amelyet a Configuration Manager konzolon is.  

Ha a frissítendő számítógépen fut, a Configuration Manager-ügyfél:  

-   A frissítés telepítéséhez központi telepítést is használhat. Ha további információkat szeretne arról, hogy hogyan használhatja a központi telepítést a frissítések telepítésére, olvassa el az aktuális témakör [A Configuration Manager frissítéseinek központi telepítése](#BKMK_Deploy) , ebben a témakörben.  

-   Ha közvetlenül be van jelentkezve az ügyfélszámítógépre, interaktívan is elvégezheti a telepítést.  

-   A frissítést manuálisan is telepítheti az egyes számítógépekre. Manuális telepítéséhez a Configuration Manager konzol frissítés a Configuration Manager konzolt futtató mindegyik számítógépen futtassa az Msiexec.exe, és hivatkozzon a Configuration Manager konzol frissítésének .msp fájljára.  

A következő parancsot használhatja például a Configuration Manager konzol frissítését. Ez a parancssor futtatja az MSIEXEC a számítógépen, és hivatkozik arra az .msp fájlra, amely a frissítési csomag kibontott a helykiszolgálón: **msiexec.exe /p \\ \\ &lt;kiszolgálónév\>\SMS_&lt;Helykód\>\Hotfix\\&lt;tudásbáziscikk\>\AdminConsole\\&lt;Platform\>\\&lt;msp\> /l\*v &lt;logfile\>REINSTALLMODE = mous REINSTALL = ALL**  

##  <a name="BKMK_Deploy"></a> A Configuration Manager frissítéseinek központi telepítése  
 Telepítése után a frissítési csomagot egy helykiszolgálóra, használhatja a következő három módszerrel telepítheti a frissítéseket további számítógépekre.  

###  <a name="BKMK_DeploySCUP"></a>Updates Publisher 2011 használata a frissítések telepítése  
 Amikor telepíti a frissítési csomagot egy helykiszolgálóra, a telepítési varázsló létrehoz egy katalógusfájlt az Updates Publisher, amelyek segítségével telepítheti a frissítéseket a megfelelő számítógépekre. Ezt a katalógust a varázsló mindig létrehozza, még akkor is, ha a **Csomag és program használata a frissítés központi telepítéséhez**gyorsjavításainak telepítéséhez.  

 Az Updates Publisher katalógusának a neve **SCUPCatalog.cab** és a következő helyen a a frissítési csomagot futtató számítógépen található: **\\\\&lt;Kiszolgálónév\>\SMS_&lt;Helykód\>\Hotfix\\&lt;tudásbáziscikk\>\SCUP\SCUPCatalog.cab**  

> [!IMPORTANT]  
>  Az SCUPCatalog.cab fájl használata a helyrendszer-kiszolgálóra útneve a frissítési csomagot futtató hozta létre, mert azt más helykiszolgálókon nem használható.  

 A varázsló befejezése után a katalógust importálhatja az Updates Publisherbe, és a Configuration Manager szoftverfrissítések segítségével telepítheti a frissítéseket. Az Updates Publisherrel kapcsolatos további információkért lásd: [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkID=83449) a System Center 2012 TechNet könyvtárában.  

 Az SCUPCatalog.cab fájl importálhatja az Updates Publisherbe, és a frissítések közzétételéhez a következő eljárás segítségével.  

##### <a name="to-import-the-updates-to-updates-publisher-2011"></a>Importálása az updates Publisher 2011 részére  

1.  Indítsa el az Updates Publisher konzolját, és kattintson a **importálási**.  

2.  Az a **importálás típusa** a frissítések katalógusát importáló varázsló, válassza a lap **adja meg az importálandó katalógus elérési útjának**, és adja meg SCUPCatalog.cab fájlt.  

3.  Kattintson a **következő**, és kattintson a **következő** újra.  

4.  Az a **biztonsági figyelmeztetés - katalógus érvényesítése** párbeszédpanel, kattintson a **elfogadás**. Miután elkészült, zárja be a varázslót.  

5.  Az Updates Publisher konzolját, válassza ki a frissítés telepítése, és kattintson a kívánt **közzététel**.  

6.  Az a **közzétételi beállítások** a szoftverfrissítéseket közzé tévő varázsló, válassza a lap **teljes tartalom**, és kattintson a **következő**.  

7.  Fejezze be a varázslót, hogy közzétegye a frissítéseket.  

###  <a name="BKMK_DeploySWDist"></a>Használhatnak központi szoftvertelepítést, frissítések telepítése  
 Amikor telepíti a frissítési csomagot egy elsődleges hely vagy központi adminisztrációs hely helykiszolgálójára, konfigurálhatja a telepítővarázslót a szoftverek központi telepítéséhez a frissítési csomagokat hozhat létre. Majd egyes csomagokat telepítheti a frissíteni kívánt számítógépek gyűjteménye.  

 A szoftver központi telepítési csomag létrehozásához a **szoftver központi telepítésének konfigurálása** a varázsló, jelölje be a jelölőnégyzetet minden egyes frissítés típus, amely frissíti a csomagot. A használható típusok között lehetnek kiszolgálók, a Configuration Manager konzolok és ügyfelek. Kiválasztott frissítés egyes típusaihoz külön csomag jön létre.  

> [!NOTE]  
>  A kiszolgálók a csomag tartalmazza a következő összetevők frissítéseit:  
>   
>  -   Helykiszolgáló  
>  -   SMS Provider  
>  -   Helyadatbázis  

 Ezt követően a varázslóban, a **Szoftverfrissítés központi telepítésének konfigurálási módszere** oldalon válassza a **Szoftverterjesztést használok**lehetőséget. Ez a választás a varázslót a szoftverfrissítési központi telepítési csomagok létrehozásához irányítja.  

 A varázsló befejezése után megtekintheti a csomagokat, amelyek a Configuration Manager konzol hozna létre a **csomagok** csomópontja a **szoftverkönyvtár** munkaterületen. Használhatja a szokásos folyamat szoftvercsomagok telepítése a Configuration Manager-ügyfelek számára. Amikor a csomag fut az ügyfélen, az ügyfélszámítógépen vonatkozó összetevőinek a Configuration Manager telepíti a frissítéseket.  

 További információ a csomagok központi telepítése a Configuration Manager-ügyfelek: [csomagokat és programokat a System Center Configuration Managerben](../../../apps/deploy-use/packages-and-programs.md).  

###  <a name="BKMK_DeployCollections"></a>Hozzon létre gyűjteményeket a Configuration Manager frissítéseinek telepítéséhez  
 Speciális frissítéseket telepítheti a vonatkozó ügyfelekre. A következő információk segítségére lehetnek eszközgyűjtemények létrehozásakor különböző összetevői a Configuration Manager számára.  

|A Configuration Manager összetevő|Utasítások|  
|----------------------------------------|------------------|  
|Központi felügyeleti hely kiszolgálója|Hozzon létre közvetlen tagsági lekérdezést, és adja hozzá a központi felügyeleti hely kiszolgáló-számítógépét.|  
|Minden elsődleges hely kiszolgálója|Hozzon létre közvetlen tagsági lekérdezést, és adja hozzá az egyes elsődleges helyek kiszolgáló-számítógépét.|  
|Minden másodlagos hely kiszolgálója|Hozzon létre közvetlen tagsági lekérdezést, és adja hozzá az egyes másodlagos helyek kiszolgáló-számítógépét.|  
|Minden x86 alapú ügyfél|Hozzon létre egy gyűjteményt a következő feltételek:<br /><br /> **Válassza ki \* SMS_R_System belső való csatlakoztatás SMS_G_System_SYSTEM SMS_G_System_SYSTEM. Erőforrás azonosítója = SMS_R_System.ResourceId ahol SMS_G_System_SYSTEM. SystemType = "X86-alapú PC"**|  
|Minden x64 alapú ügyfél|Hozzon létre egy gyűjteményt a következő feltételek:<br /><br /> **Válassza ki \* SMS_R_System belső való csatlakoztatás SMS_G_System_SYSTEM SMS_G_System_SYSTEM. Erőforrás azonosítója = SMS_R_System.ResourceId ahol SMS_G_System_SYSTEM. SystemType = "X64-alapú PC"**|  
|A Configuration Manager konzolt futtató minden számítógép|Hozzon létre közvetlen tagsági lekérdezést, és adja hozzá mindegyik számítógépet.|  
|Az SMS Provider példányát futtató távoli számítógépek|Hozzon létre közvetlen tagsági lekérdezést, és adja hozzá mindegyik számítógépet.|  

> [!NOTE]  
>  A helyadatbázis frissítéséhez végezze el a frissítés központi telepítését az adott helykiszolgálón.  

 További információk a gyűjtemények létrehozásának módjáról: [Gyűjtemények létrehozása a System Center Configuration Managerben](../../../core/clients/manage/collections/create-collections.md).  

