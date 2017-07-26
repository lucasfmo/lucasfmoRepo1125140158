---
title: "A Technical Preview-ban 1612 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1612 verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bceab2e8-2f05-4a17-9ac8-a7a558670fb7
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcb14a2be312d4d8a4a9c235652c7bf971a7a976
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1612-for-system-center-configuration-manager"></a>A rendszer 1612 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*



Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1612 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="the-data-warehouse-service-point"></a>A Data Warehouse szolgáltatási pont
A Technical Preview verzió 1612 kezdve a Data Warehouse szolgáltatási pont lehetővé teszi tárolja, és a Configuration Manager telepítéshez hosszú távú múltbeli adatok jelentése. Ez úgy érhető el, a Configuration Manager adatbázisából az adatraktár-adatbázis automatikus szinkronizálás. Ez az információ a jelentéskészítési szolgáltatási pont az majd érhető el.

Alapértelmezés szerint az új helyrendszerszerepkör telepítésekor a Configuration Manager létrehozza az adatraktár-adatbázis, a megadott SQL Server-példányt. Az adatraktár legfeljebb 2 TB adat, a változások követése Timestamp támogatja.  Alapértelmezés szerint az adatokat a helyadatbázisból szinkronizált a csoport tartalmazza a globális adatok, helyadatok, Global_Proxy, Felhőbeli adatát és adatbázis-nézetek. Módosíthatja azt is, milyen további táblákon, vagy adott táblák kizárja az alapértelmezett replikációs származó szinkronizálva.
A szinkronizált alapértelmezett adatokat az alábbiakról tájékozódhat:
- Infrastruktúra-állapot
- Biztonság
- Megfelelőségi
- Kártevő szoftver   
- Szoftverek központi telepítése
- Leltár részleteit (azonban nem szinkronizált leltárelőzmények törlése)

Telepítése és konfigurálása az adatraktár-adatbázis kívül számos új jelentések települnek, így könnyen kereshet és jelentést ezeken az adatokon.

### <a name="data-warehouse-dataflow"></a>Data Warehouse adatfolyam   
![Datawarehouse_flow](./media/datawarehouse.png)

| Lépés         | Részletek  |
|:------:|-----------|  
| **1**  |     A helykiszolgáló továbbítja, és a hely adatbázisában tárolja az adatokat.  |  
| **2** |      Ütemezési és konfigurációs alapján, a Data Warehouse pont adatok lekérése a hely adatbázisába.  |  
| **3** |  A Data Warehouse szolgáltatási pont továbbítja, és a szinkronizált adatok másolatát tárolja az adatraktár adatbázisából. |  
| **A** |  A beépített jelentések használatával, a adatok kérelem a Reporting Services átkerül pont az SQL Server Reporting Services segítségével. |  
| **B** |      A legtöbb jelentések aktuális információkat, és ezeket a kérelmeket van futtatni a helyadatbázist. |  
| **C** | Amikor jelentést kér jelentéseket egyikének használatával előzményadatait, egy *kategória* a **adatraktár**, a kérelem futtatása ellen az adatraktár adatbázisából.   |  

### <a name="prerequisites-for-the-data-warehouse-service-point-and-database"></a>A Data Warehouse szolgáltatási pont és az adatbázis előfeltételei
- A hierarchiának rendelkeznie kell egy jelentéskészítési szolgáltatási pont helyrendszerszerepkör van telepítve.
- A helyrendszer-szerepkör telepítéséhez használt számítógépnek szükséges a .NET-keretrendszer 4.5.2-es vagy újabb.
- A helyrendszer-szerepkör telepítéséhez használt számítógépnek számítógépfiókjának, amely az adatraktár-adatbázist tárolni fogja a számítógép helyi rendszergazdai engedélyekkel kell rendelkeznie.
- A helyrendszer-szerepkör telepítéséhez használt rendszergazdai fiókot az adatraktár-adatbázist futtató SQL Server-példányon DBO kell lennie.  
-  A-adatbázist támogatja:
  - SQL Server 2012 vagy újabb, Enterprise vagy Datacenter kiadásával.
  - Az alapértelmezett vagy megnevezett példány
  - Az egy *SQL Server-fürt*. Bár ebben a konfigurációban kell működnie, nem tesztelt, és a rendszer támogatja a lehető legkedvezőbb módon.
  - Ha a közösen elhelyezett vagy a hely adatbázisában, vagy a Reporting services pont adatbázisának. Azt javasoljuk azonban egy másik kiszolgálóra telepíthető.  
- A fiók, amely a *jelentéskészítési szolgáltatási pont fiókja* kell rendelkeznie a **db_datareader** az adatraktár-adatbázis engedéllyel.  
- Az adatbázis nem támogatja a *SQL Server AlwaysOn rendelkezésre állási csoport*.

### <a name="install-the-data-warehouse"></a>Az adatraktár telepítése
Telepíthető a Data Warehouse helyrendszerszerepkör a központi adminisztrációs hely vagy elsődleges hely használatával a **helyrendszer-szerepkörök hozzáadása varázslóval** vagy a **helyrendszer-kiszolgáló létrehozása varázsló**. Lásd: [helyrendszerszerepkörök telepítése](/sccm/core/servers/deploy/configure/install-site-system-roles) további információt. A hierarchiában a szerepkör több példányát támogatja, de csak egy példány támogatott az egyes helyeken.  

A szerepkör telepítésekor a Configuration Manager létrehozza az adatraktár-adatbázis, az SQL Server megadott példányán. Ha megad egy létező adatbázis nevét (, mint ha Ön [az adatraktár-adatbázis áthelyezése egy új SQL Server](#move-the-data-warehouse-database)), a Configuration Manager nem hoz létre egy új adatbázist, de Ehelyett használja a megadott.

#### <a name="configurations-used-during-installation"></a>Telepítés során használt konfigurációk
A helyrendszerszerepkör telepítéséhez használja a következő információkat:

**Rendszerszerepkör kiválasztása** lap:  
Mielőtt a varázsló megjeleníti azt a beállítást válassza ki, és a Data Warehouse szolgáltatási pont telepítéséhez, telepítenie kell egy jelentéskészítési szolgáltatási pontot.

**Általános** lap: A következő általános információkra szükség:
- **A Configuration Manager-adatbázis beállításait:**   
  - **Kiszolgálónév** -adja meg a helyadatbázist futtató kiszolgáló teljes Tartománynevét. Ha nem használja az SQL Server alapértelmezett példányán, meg kell adnia a példány után a teljes tartománynév, a következő formátumban: ***&lt;Sqlserver_FQDN >\&lt; példány_neve >***
  - **Az adatbázisnév** -adja meg a Helyadatbázis nevét.
  -    **Győződjön meg arról** -kattintson **ellenőrizze** győződjön meg arról, hogy a kapcsolat a Helyadatbázis nem sikeres.
</br></br>
- **Adatraktár adatbázis beállítások:**
  -    **Kiszolgálónév** – adja meg a Data Warehouse szolgáltatás pontot futtató kiszolgáló teljes Tartománynevét és az adatbázis. Ha nem használja az SQL Server alapértelmezett példányán, meg kell adnia a példány után a teljes tartománynév, a következő formátumban: ***&lt;Sqlserver_FQDN >\&lt; példány_neve >***
  -    **Az adatbázisnév** -az adatraktár-adatbázis teljes Tartománynevét adja meg.  A Configuration Manager létrehoz az adatbázis ezen a néven. Ha egy már létező adatbázisnevet ad meg az SQL server-példányt, a Configuration Manager fog használni, hogy az adatbázis.
  -    **Győződjön meg arról** -kattintson **ellenőrizze** győződjön meg arról, hogy a kapcsolat a Helyadatbázis nem sikeres.

**A szinkronizálási beállítások** lap:   
- **Beállítások:**
  - **Replikációs csoportok szinkronizálásához** – válassza ki a szinkronizálni kívánt adatcsoport. A különféle adatcsoportok kapcsolatos információkért lásd: [adatbázis-replikáció](/sccm/core/servers/manage/data-transfers-between-sites#a-namebkmkdbrepa-database-replication) és **elosztott nézetek** a [helyek közötti adatátvitel](/sccm/core/servers/manage/data-transfers-between-sites).
  - **Szinkronizálandó táblákhoz** – adja meg a szinkronizálni kívánt további táblák nevét. Több tábla külön által vesszővel válassza el. Ezek a táblázatok szinkronizálja a replikációs csoportokban mellett a helyadatbázisból.
  - **Szinkronizálandó kizárt táblák** -adja meg a replikációs csoport szinkronizált egyes táblák nevét. A megadott táblák nem történik. Több tábla külön által vesszővel válassza el.
- **Szinkronizálási beállítások:**
  - **Szinkronizálási időköz (perc)** -értéket adja meg percben. Az időköz elérése után egy új megkezdődik. Ez a funkció támogatja a 60 és 1440 perc (24 óra) közé.
  - **Ütemezés** -adja meg a kívánt szinkronizálását.

**Jelentési pont elérésére**:   
A data warehouse szerepkör telepítése után ellenőrizze a fiók, amely a *jelentéskészítési szolgáltatási pont fiókja* rendelkezik a **db_datareader** az adatraktár-adatbázis engedéllyel.

#### <a name="troubleshoot-installation-and-data-synchronization"></a>Telepítés és az adatok-szinkronizálás hibaelhárítása
A Data Warehouse szolgáltatási pont telepítése vagy az adatok szinkronizálását az kapcsolatos problémák kivizsgálásához használja a következő naplók kapcsolódnak:
- **DWSSMSI.log** és **DWSSSetup.log** -hibák vizsgálata a Data warehouse szolgáltatási pont telepítése során ezek a naplók segítségével.
-     **Microsoft.ConfigMgrDataWarehouse.log** – Ez a napló használatával vizsgálja meg a helyadatbázist az adatraktár-adatbázis adatainak szinkronizálása.

### <a name="reporting"></a>Jelentéskészítés
Adatraktár helyrendszerszerepkör telepítése után az alábbi jelentések érhetők el a jelentéskészítési szolgáltatási ponton a egy *kategória* a **Data warehouse-bA:**

|Jelentés                   | Részletek                                  |
|-------------------------|------------------------------------------|
| **Alkalmazás központi telepítési jelentés** | Az alkalmazás központi telepítését egy adott alkalmazás és a gép részleteinek megtekintése.|
| **Az Endpoint Protection és a frissítés megfelelőségi Szoftverjelentés**   | Hiányzó szoftverfrissítések számítógépek megtekintése.|
| **Általános hardver-Leltárjelentések**  | Egy adott számítógép összes Hardverleltár megjelenítése.|
| **Általános szoftverleltár-jelentés**  | Egy adott számítógép összes szoftverleltár megjelenítése.|
| **Infrastruktúra állapotának áttekintése**  |Megjeleníti a Configuration Manager-infrastruktúra állapotának áttekintése.|
| **Észlelt kártevők listája**  |Nézet kártevők, amelyek a szervezet észlelhető.|
|** A szoftverek terjesztési összegző jelentés ** | Az egy adott hirdetmény és a gép szoftverterjesztés összefoglalása.|

### <a name="move-the-data-warehouse-database"></a>Az adatraktár-adatbázis áthelyezése
Az adatraktár-adatbázis áthelyezése egy új SQL Server tegye a következőket:

  1. Tekintse át az aktuális adatbázis konfigurációját, és jegyezze fel a konfigurációs adatait, többek között:  
   - A szinkronizált adatok csoportok
   - Bevonhat vagy kizárhat a szinkronizálási táblák       

   Ezek adatcsoport és táblák újra fogja konfigurálni után állítsa vissza az adatbázist egy új kiszolgálóra, és telepítse újra a helyrendszer-szerepkör.  

  2. SQL Server Management Studio segítségével biztonsági mentés az adatraktár-adatbázist, majd ismét az új számítógépen, amely üzemelteti az adatraktár SQL server, hogy az adatbázis visszaállítása.

  Után állítsa vissza az adatbázist az új kiszolgálón, győződjön meg arról, hogy az adatbázis-hozzáférési engedélyek megegyeznek az új adatraktár-adatbázis a azzal, mintha az eredeti adatraktár-adatbázis.

  3. A Configuration Manager konzol használatával a Data Warehouse szolgáltatás pont helyrendszer-szerepkör eltávolítása az aktuális kiszolgáló.

  4. Telepítsen egy új Data Warehouse szolgáltatás pontot, és adja meg az új SQL-kiszolgáló és a visszaállított Data Warehouse-adatbázis-példány nevét.

  5. A helyrendszer-szerepkör telepítése után az áthelyezés befejeződött.

Tekintse át a következő Configuration Manager-naplók annak ellenőrzéséhez, hogy a helyrendszer-szerepkör sikeresen újratelepítette rendelkezik:  
- **DWSSMSI.log** és **DWSSSetup.log** -hibák vizsgálata a Data warehouse szolgáltatási pont telepítése során ezek a naplók segítségével.
-     **Microsoft.ConfigMgrDataWarehouse.log** – Ez a napló használatával vizsgálja meg a helyadatbázist az adatraktár-adatbázis adatainak szinkronizálása.


## <a name="content-library-cleanup-tool"></a>Tartalomtár Lemezkarbantartó eszköz
Technikai előzetes verziójában 1612 kezdve használhatja új parancssori eszköze (**ContentLibraryCleanup.exe**), amely már nem a csomag vagy egy terjesztési pontról alkalmazás társított tartalom eltávolítása (elárvult tartalom). Ez az eszköz a tartalomtár Lemezkarbantartó eszköz neve.

Ez az eszköz csak a tartalmat a terjesztési ponton, ha az eszköz futtatásához, és a tartalom nem távolítható el a tartalomtár a helykiszolgálón van hatással.

Miután telepítette a Technical Preview 1612, megtalálhatja **ContentLibraryCleanup.exe** a *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup a\* mappa a Technical Preview-hely kiszolgálóján.

Az eszköz, amely a jelen technikai előzetes kiadással készült lecseréli a korábbi Configuration Manager-termékek, amely a hasonló eszközök régebbi verzióit. Bár ez eszköz, verziószám: után 2017. március 1-jétől. működése leáll új verziókat a későbbi technikai Előzetesekben kiadja, mindaddig, amíg az eszköz megjelenik az aktuális ág vagy a termelési készen áll a sávon kívüli kiadást részeként.

### <a name="requirements"></a>Követelmények  
 - Az eszköz közvetlenül a számítógépen, amelyen a terjesztési pontot, vagy futtatható távolról egy másik kiszolgálóról. Az eszköz csak futtatható egyetlen terjesztési pont ellen egyszerre.
 - Az eszköz futtató felhasználói fióknak közvetlenül a Configuration Manager-hierarchia egy teljes körű rendszergazda egyenlő szerepkör alapú felügyelet engedélyekkel kell rendelkeznie.  Az eszköz nem működik, ha a felhasználói fiók engedéllyel rendelkezik teljes rendszergazdai jogosultsággal rendelkező Windows biztonsági csoport tagjaként.

### <a name="modes-of-operation"></a>Működési módok
Az eszköz két módban futtatható:
  1.    **Mi Ha mód**:   
      Ha nincs megadva a **/törlése** kapcsoló, az eszköz Lehetőségelemzések módban fut. és azonosítja a tartalmat a terjesztési pontról törlendő, de nem ténylegesen delete adatokat.

      - Amikor az eszköz ebben a módban fut, a törlésre kerülő szolgáltatásfájlok tartalommal kapcsolatos információk automatikusan írni az eszközök naplófájl. Nem kéri a felhasználót, hogy minden lehetséges törlés jóváhagyásához.
      - Alapértelmezés szerint a naplófájl írása a felhasználók ideiglenes mappába a számítógépen, amelyen futtatja az eszközt, azonban a/log kapcsoló használatával a naplófájl átirányíthatók más helyre.  
      </br>

    Javasoljuk, hogy ebben a módban futtassa az eszközt, és keresse meg az eredményül kapott naplófájljában az eszközt a/delete kapcsolóval futtatása előtt.  

  2. **Mód törlése**: Az eszköz futtatásakor a **/törlése** delete módban fut. az eszköz kapcsoló.

     - Amikor az eszköz ebben a módban fut, elárvult, amely a megadott terjesztési ponton található tartalom található tartalomtárból a terjesztési pont törölhetők.
     -     Minden egyes fájl törlése előtt a rendszer felajánlja a felhasználónak győződjön meg arról, hogy a fájlt törölni kell.  Kiválaszthatja, **Y** Igen, **N** nem, vagy **Igen az összes** kihagyja a további utasításokat, és törölje az összes elárvult tartalmat.  
     </br>

     Azt javasoljuk, Lehetőségelemzések módban futtassa az eszközt, és keresse meg az eredményül kapott naplófájljában az eszközt a/delete kapcsolóval futtatása előtt.  

Ha a tartalomtárat Lemezkarbantartó eszköz vagy módban fut, az automatikusan létrehoz egy naplófájlt a neve tartalmazza a módban fusson a eszköz, terjesztési pont nevét, dátum és idő művelet. A naplófájl automatikusan megnyílik, az eszköz befejezése után. Alapértelmezés szerint ez a napló írása a felhasználók **temp** mappába a számítógépen, amelyen futtatja az eszközt. azonban használhatja olyan parancssori kapcsolóval a naplófájl átirányíthatók más helyre, például egy hálózati megosztásra.   


### <a name="run-the-tool"></a>Futtassa az eszközt
Az eszköz futtatásához:
1. Nyisson meg egy rendszergazdai parancssort egy mappába, amelyben **ContentLibraryCleanup.exe**.  
2. Ezután adja meg egy parancssort, amely tartalmazza a kötelező parancssori kapcsolók és a nem kötelező kapcsolók szeretne használni.

**Ismert problémák** az eszköz futtatásakor a következő hiba előfordulhat, hogy adható vissza, ha a csomag vagy központi telepítés sikertelen volt, vagy folyamatban van:
-  *System.InvalidOperationException: E tartalomtárhoz nem törlődnek azonnal mert csomag <packageID> nincs megfelelően telepítve.*

**Megkerülő megoldás:** Nincs. Az eszköz nem megbízható árva fájlok azonosítása, amikor a tartalom központi telepítése sikertelen volt, vagy folyamatban van. Ezért az eszköz nem lehetővé teszi a karbantartás tartalomhoz, hogy a probléma megoldásáig.



### <a name="command-line-switches"></a>Parancssori kapcsolók  
A következő parancssori kapcsolókat is használható bármilyen sorrendben.   

|Kapcsoló|Részletek|
|---------|-------|
|**/ delete**  |**Nem kötelező** </br> A kapcsoló használata, ha törli a tartalmat a terjesztési pontról. Mielőtt tartalom törlését kéri. </br></br> A kapcsoló nem használható, ha az eszköz naplózza az eredményeket arról, hogy mely tartalmak törlése akkor történik meg, de nem törli a tartalmat a terjesztési pontról. </br></br> Például: ***ContentLibraryCleanup.exe /dp server1.contoso.com/DELETE*** |
| **/q**       |**Nem kötelező** </br> Futtassa az eszközt, amely minden használata (például kér tartalmat törlésekor) csendes módban, és nem automatikusan nyissa meg a naplófájlt. </br></br> Például: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;terjesztési pont teljes Tartományneve >**  | **Kötelező** </br> Adja meg a törölni kívánt terjesztési pont teljes tartománynevét (FQDN). </br></br> Például:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/PS &lt;elsődleges hely teljesen minősített Tartományneve >**       | **Nem kötelező** karbantartásakor tartalmat a terjesztési pontról egy elsődleges helyen.</br>**Szükséges** karbantartásakor tartalmat a terjesztési pontról egy másodlagos helyen. </br></br> Adja meg az elsődleges hely a terjesztési pont teljes Tartományneve tartozik, vagy a szülő elsődleges szülő, ha a terjesztési pont másodlagos helyen. </br></br> Például: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;elsődleges hely kódja >**  | **Nem kötelező** karbantartásakor tartalmat a terjesztési pontról egy elsődleges helyen.</br>**Szükséges** karbantartásakor tartalmat a terjesztési pontról egy másodlagos helyen. </br></br> Adja meg a helykódot az elsődleges hely, amely a terjesztési pont tartozik, vagy a szülő elsődleges hely, amikor a terjesztési pont másodlagos helyen.</br></br> Például: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Nem kötelező** </br> Adjon meg egy könyvtárat, ahová a rendszernapló fájljaiban. Ez akkor lehet egy helyi meghajtó, vagy egy hálózati megosztás.</br></br> Ha nem használja ezt a kapcsolót, naplófájlok automatikusan a felhasználók ideiglenes mappába kerülnek.</br></br> Helyi meghajtó példát: ***ContentLibraryCleanup.exe /dp server1.contoso.com log C:\Users\Administrator\Desktop*** </br></br>Példa a hálózati megosztáshoz: ***ContentLibraryCleanup.exe /dp server1.contoso.com/log \\ &lt;megosztás >\&lt; mappa >***|


## <a name="improvements-for-in-console-search"></a>A konzolon belüli keresési fejlesztései
User Voice visszajelzések alapján jelentek meg a következő fejlesztéseket kínálja a konzolon belüli keresés:
 - **Objektum elérési útja:**  
  Sok objektum mostantól egy olyan új oszlop neve **objektumelérési út**.  Ha keresni, és a megjelenített eredmények tartalmazza ezt az oszlopot, láthat minden objektum elérési útja. Például, ha futtatja a alkalmazások keresése az alkalmazások csomópontban, és alárendelt csomópontok is keres a *objektumelérési út* oszlop az eredmények panelen láthatja, minden visszaadott objektum elérési útjának.   

- **Keresett szöveg megőrzése:**  
  Adja meg a szöveget a keresési mezőbe, és utána váltsanak keresése egy alárendelt csomópont és az aktuális csomópont között, ha a beírt szöveg most továbbra is fennáll, és anélkül, hogy írja be újra az új keresés elérhetők maradnak.

- **Kereshet az alárendelt csomópont a döntési megőrzése:**  
 A beállítást csak akkor vagy kereső a *aktuális csomópont* vagy *összes alárendelt csomópont* most továbbra is fennáll a csomópont dolgozik módosításakor.   Ez a viselkedés azt jelenti, hogy nem kell folyamatosan alaphelyzetbe állítja a döntést, akkor a konzol Navigálás.  Alapértelmezés szerint a konzol megnyitásakor a lehetőség egy keresés csak az aktuális csomópont.

## <a name="prevent-installation-of-an-application-if-a-specified-program-is-running"></a>Ha egy adott program fut, hogy egy alkalmazás telepítése.
Most már konfigurálhatja végrehajtható fájlok (.exe kiterjesztésű) listáját a központi telepítési típus tulajdonságaihoz, amellyel fut, ha egy alkalmazás telepítését letiltja. Telepítési kísérlet történik, miután a felhasználók látni fogják egy párbeszédpanelen kéri a felhasználót a folyamatok, amelyek blokkolják a telepítés gombra.

### <a name="try-it-out"></a>Próbálja ki
Végrehajtható fájlok listájának konfigurálása
1.    Minden központi telepítési típus a Tulajdonságok lapon válassza ki a **Installer kezelése** fülre.
2.    Kattintson a **Hozzáadás**, egy további végrehajtható fájlok hozzáadása a listához (például **Edge.exe**)
3.    Kattintson a **OK** a központi telepítési típus tulajdonságai párbeszédpanel bezárásához.

Most egy felhasználó vagy egy eszközt, és egy végrehajtható fájlok hozzáadta, hogy fut-e az alkalmazás központi telepítésekor a végfelhasználó jelenik meg a Szoftverközpont párbeszédpanel közölve, hogy a telepítés sikertelen, mert az alkalmazás fut-e.

## <a name="new-windows-hello-for-business-notification-for-end-users"></a>Új Windows Hello-üzleti értesítés a végfelhasználók számára

Egy új Windows 10-értesítés tájékoztatja a végfelhasználók számára, hogy további műveletek végrehajtásához Windows Hello for Business telepítő (például a PIN-kód beállítása) szükséges.

## <a name="windows-store-for-business-support-in-configuration-manager"></a>Windows áruház vállalati verziójának ügyfélszolgálatával a Configuration Managerben

Most már telepítheti a központi telepítési céllal online licencelt alkalmazások **elérhető** a Windows áruházból a vállalati számítógépeken futó Configuration Manager-ügyfél.
További részletekért lásd: [alkalmazások kezelése a System Center Configuration Managerrel a vállalati Windows áruházból](https://docs.microsoft.com/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

Ez a szolgáltatás támogatása jelenleg csak a Windows 10 RS2 preview build futtató számítógépekre érhető el.

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>A feladatütemezés sikertelen lesz, ha az előző laphoz való visszatéréshez
Most visszatérhet az előző oldalra a feladatütemezés futtatása, és hiba történik. Ez a kiadás előtt indítsa újra a feladatütemezés, ha hiba történt a kellett. Használhatja például a **előző** gombra a következő esetekben:

- A számítógép indításakor a Windows PE környezetben, a feladat feladatütemezési rendszerindítási párbeszédpanelen előfordulhat, hogy megjeleníti, mielőtt a feladatütemezés érhető el. Ha a Tovább lehetőségre kattintás ebben a forgatókönyvben, a feladatütemezés utolsó lapján, hogy nincsenek nem feladatütemezések üzenetet jeleníti meg. Most, rákattinthat **előző** keresni az elérhető feladatütemezéseket. Ez az eljárás megismétlésével addig, amíg a feladatütemezés nem érhető el.
- Ha a feladatütemezés futtatása, de függő tartalomcsomagokkal még nem állnak rendelkezésre a terjesztési pontokon, a feladatütemezés sikertelen lesz. Most tartalmának terjesztése az hiányzó (Ha ez nem volt terjesztve van még), vagy várjon, amíg a tartalom a terjesztési pontokon elérhetővé válik, és kattintson **előző** szeretné, hogy a feladat feladatütemezési keres újra a tartalmat.

## <a name="express-installation-files-support-for-windows-10-updates"></a>Az expressz telepítési fájlok Windows 10-frissítés támogatása
Az expressz telepítési fájlok támogatása Windows 10-es frissítések a Configuration Manager jelentek meg. Ha a Windows 10 támogatott verzióját használja, használhatja a Configuration Manager-beállítások letöltése csak az aktuális hónap Windows 10 összegző frissítése és az előző hónap frissítés között a különbözeti. Jelenleg a Configuration Manager aktuális ágában, a teljes Windows 10-es összesítő frissítéssel (beleértve az előző hónap összes frissítését) lesznek letöltve, minden hónapban. Az expressz telepítési fájlok használatával biztosít a kisebb tölt le és gyorsabb telepítési idejét, az ügyfeleken.

> [!IMPORTANT]
> Támogatja a beállítások során az expressz telepítési fájlok használata érhető el a Configuration Manager alkalmazást, ez a funkció csak akkor támogatott a Windows 10 1607 a Windows Update Agent frissítése a mellékelt verzió 2017. január 10 (frissítő kedd) a kiadott frissítéseket. Ezekről a frissítésekről további információkért lásd: [támogatja a cikk 3213986](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693). Kihasználhatja az expressz telepítési fájlok a következő set frissítések a 2017. február 14 kiadásakor. Windows 10 1607 frissítés nélkül verziója és a korábbi verziók nem támogatják az expressz telepítési fájlok.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>A kiszolgálón a Windows 10-frissítés esetén expressz telepítési fájlokat a letöltésének engedélyezése
A Windows 10 expressz telepítési fájlok metaadatait szinkronizálás megkezdéséhez engedélyeznie kell azt a szoftverfrissítési pont tulajdonságai.
1.    A Configuration Manager-konzolon lépjen a **felügyeleti** > **Helykonfiguráció** > **helyek**.
2.    Válassza ki a központi adminisztrációs hely vagy önálló elsődleges helyen.
3.    A **Kezdőlap** **Beállítások** csoportjában nyissa meg a **Helyösszetevők konfigurálása**elemet, majd kattintson a **Szoftverfrissítési pont**elemre. Az a **Frissítésfájlok** lapon jelölje be **töltse le az összes jóváhagyott frissítések teljes fájlokat és expressz telepítési fájlok a Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Az Expressz telepítés fájljainak letöltése és telepítése az ügyfelek támogatásának engedélyezése
Ahhoz, hogy az expressz telepítési fájlok támogatása az ügyfeleken, engedélyeznie kell az expressz telepítési fájlok az ügyfél beállításai szakaszában szoftverfrissítések ügyfeleken. Ezzel létrehoz egy új HTTP-figyelő, amely figyeli a kéréseket a megadott porton expressz telepítési fájlok letöltéséhez. Amennyiben az ügyfél beállításait ennek a funkciónak az ügyfélen a telepít, akkor megkísérli a különbözeti között az aktuális hónap a Windows 10 összegző frissítése és az előző hónap frissítés letöltése (ügyfelek verziónak kell futnia. a Windows 10, hogy támogatja az expressz telepítési fájlok).
1.    Az Expressz telepítés fájljai a szoftverfrissítési pont összetevő tulajdonságai (az előző eljárásban) támogatásának engedélyezéséhez.
2.    A Configuration Manager-konzolon lépjen a **felügyeleti** > **ügyfélbeállítások**.
3.    Jelölje ki a megfelelő ügyfélbeállítások, ezt a a **Home** lapra, majd **tulajdonságok**.
4.    Válassza ki a **szoftverfrissítések** lapján konfigurálhatja **Igen** a a **engedélyezése az ügyfeleken Express frissítések telepítésének** beállítása és konfigurálása az ügyfélen a HTTP-figyelő által használt port a **Express frissítések tartalom letöltéséhez használt Port** beállítást.


## <a name="odata-endpoint-data-access"></a>Az OData-végpont adatelérési

 A Configuration Manager most kínál egy RESTful OData-végpont a Configuration Manager adatainak eléréséhez. A végpont található kompatibilis Odata 4-es verzióját, amely lehetővé teszi az eszközök, például az Excel és a Power bi-ban egyszerűen egy végpontot keresztül férnek hozzá a Configuration Manager-adatokat. Technical Preview 1612 csak támogatja objektumok olvasási hozzáférés a Configuration Manager alkalmazásban.  

A jelenleg rendelkezésre álló adatok a [Configuration Manager WMI-szolgáltató](/sccm/develop/reference/configuration-manager-reference) jelenleg is elérhető, az új OData RESTful-végponthoz. Az OData-végpont által elérhetővé tett entitáskészletekben lehetővé teszik a számbavétel ugyanazokat az adatokat a WMI-szolgáltatóval kérdezhetők le.

### <a name="try-it-out"></a>Próbálja ki

Az OData-végpont használata előtt engedélyeznie kell azt a helyhez.

1.  Ugrás a **felügyeleti** > **hely konfigurációs** > **helyek**.
2.  Válassza ki az elsődleges helyet, és kattintson a **tulajdonságok**.
3.  Az általános az elsődleges hely tulajdonságai lapon kattintson a **engedélyezése REST-végpont a webhely összes szolgáltató**, és kattintson a **OK**.

A kedvenc OData-lekérdezés megjelenítőben próbálja meg az alábbi példák a különböző objektumokat adjanak vissza a Configuration Manager hasonló lekérdezéseket:

| Cél | Az OData-lekérdezés |
|---|---|
| Minden gyűjtemény beolvasása | `http://localhost/CMRestProvider/Collection` |
| Egy gyűjtemény beolvasása | `http://localhost/CMRestProvider/Collection('SMS00001')`
| A top 100 eszközök beszerzése a gyűjteményben | `http://localhost/CMRestProvider/Collection('SMS00001')/Device?$top=100` |
| Egy eszköz egy erőforrás-azonosító beszerzése a gyűjteményben | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)` |
| Az eszköz operációs rendszerétől beolvasása a gyűjteményben | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)/OPERATING_SYSTEM` |
| A gyűjteményben lévő felhasználók beolvasása | `http://localhost/CMRestProvider/Collection('SMS00001')/User` |

> [!NOTE]
> A tábla használatban látható mintalekérdezéseket *localhost* az URL-cím neve legyen a gazdagép és az SMS-szolgáltatót futtató számítógépen használható. Ha a lekérdezések egy másik számítógépen fut, cserélje le localhost telepítve SMS-szolgáltatóval a kiszolgáló teljes Tartománynevét.

## <a name="azure-active-directory-onboarding"></a>Az Azure Active Directory bevezetésének

Az Azure Active Directory (AD) bevezetésének kapcsolatot hoz létre a Configuration Manager és az Azure Active Directory egyéb felhőalapú szolgáltatás által használandó között. Ez jelenleg alkalmas a felhőalapú adatkezelési átjáró szükséges kapcsolat létrehozása.

Hajtsa végre ezt a feladatot az Azure felügyeleti, mivel az Azure rendszergazdai hitelesítő adatokat kell.

#### <a name="to-create-the-connection"></a>A VPN-kapcsolat létrehozásához:

2. A a **felügyeleti** munkaterületen, válassza a **Felhőszolgáltatások** > **Azure Active Directory** > **Azure Active Directory hozzáadása**.
2. Válasszon **bejelentkezés** az Azure AD a VPN-kapcsolat létrehozásához.

#### <a name="configuration-manager-client-requirements"></a>A Configuration Manager ügyfél-követelmények

Nincsenek több követelmények a kezelési átjáró a felhasználói házirend létrehozásának engedélyezéséhez.

- Az Azure AD-bevezetési folyamat be kell fejeződnie, és az ügyfél rendelkezik kezdetben kell csatlakoztatni a vállalati hálózathoz, a kapcsolat adatainak megszerzése.
- Ügyfelek mindkét tartományhoz csatlakoztatott (regisztrálva az Active Directory), és a felhő-tartományhoz (regisztrálva az Azure AD) kell lennie.
- Futtatnia kell a [Active Directory-Felhasználófelderítés](/sccm/core/servers/deploy/configure/about-discovery-methods#active-directory-user-discovery#active-directory-user-discovery).
- Módosítsa a Configuration Manager-ügyfél, így a felhasználói házirend kérelmek az interneten keresztül, és az ügyfélnek a változtatás központi telepítésének. Mivel ez a változás az ügyfél akkor történik meg *az ügyféleszközön*, központilag telepíthető a felhő felügyeleti átjárón keresztül bár még nem fejeződött be a felhasználói házirend szükséges konfigurációs módosításokat.
- A felügyeleti pontot kell állítani a HTTPS PROTOKOLLT használják a hálózaton lévő a jogkivonat biztonságos, és rendelkeznie kell a .net 4.5 telepítve.

A konfigurációs módosítások után egy felhasználói házirend létrehozása, és helyezze át az ügyfelek az interneten, a házirend tesztelése. Felhasználói házirend kéréseket a felhő adatkezelési átjáró hitelesítése az Azure AD-jogkivonat-alapú hitelesítéssel.

## <a name="change-to-configuring-multi-factor-authentication-for-device-enrollment"></a>Módosítsa az eszközök regisztrálásához konfigurálása a multi-factor authentication

Most, hogy a többtényezős hitelesítés (MFA) az eszközök regisztrálása az Azure portálon állíthat be, a többtényezős hitelesítési beállítást el lett távolítva, a Configuration Manager konzolon. További információt a többtényezős hitelesítés beállítása a beléptetési [a Microsoft Intune témakör](https://docs.microsoft.com/en-us/intune/deploy-use/multi-factor-authentication-azure-active-directory).

