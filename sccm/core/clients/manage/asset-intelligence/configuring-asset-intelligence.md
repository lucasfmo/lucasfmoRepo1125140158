---
title: "Az Eszközintelligencia konfigurálásának |} Microsoft Docs"
description: "A System Center Configuration Manager Eszközintelligencia beállítása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08e0382d-de05-4a76-ba5c-7223173f7066
caps.latest.revision: 7
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: d2704e0f93ad9748f7eb06d714b3754463cb3bdb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="configure-asset-intelligence-in-system-center-configuration-manager"></a>Az Eszközintelligencia szolgáltatás konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az Eszközintelligencia leltárba veszi, és kezeli a szoftverlicencek használatát.   

## <a name="steps-to-configure-asset-intelligence"></a>Az Eszközintelligencia konfigurálásának lépései  
   

- **1. lépés**: az Eszközintelligencia-jelentésekhez szükséges leltáradatok gyűjtéséhez, be kell a hardverleltározási ügyfélügynök engedélyezése a [a System Center Configuration Managerben a Hardverleltár bővítése](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).
- **2. lépés**: [Eszközintelligencia Hardverleltár-jelentési osztályainak engedélyezése](#BKMK_EnableAssetIntelligence).  
- **3. lépés**: [Eszközintelligencia szinkronizációs pontjának telepítése](#BKMK_InstallAssetIntelligenceSynchronizationPoint)
- **4. lépés**: [Sikeres bejelentkezési események naplózásának engedélyezése](#BKMK_EnableSuccessLogonEvents)  
- **5. lépés**: [Szoftverlicenc-adatok importálása](#BKMK_ImportSoftwareLicenseInformation)  
- **6. lépés**: [Az Eszközintelligencia karbantartási feladatainak konfigurálása](#BKMK_ConfigureMaintenanceTasks) 


###  <a name="BKMK_EnableAssetIntelligence"></a> Enable Asset Intelligence hardware inventory reporting classes  
 A Configuration Manager-helyek Eszközintelligencia engedélyezéséhez engedélyeznie kell egy vagy több Eszközintelligencia Hardverleltár-jelentési osztályok. Az osztályokat engedélyezheti a **Eszközintelligencia** kezdőlapján, vagy az **Adminisztráció** munkaterületen, a **Ügyfél beállításai** csomópontban az ügyfél beállításainak tulajdonságai között. A következő eljárások egyikét használhatja.  

##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-the-asset-intelligence-home-page"></a>Eszközintelligencia hardverleltár-jelentési osztályainak engedélyezése az Eszközintelligencia kezdőlapjáról  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **Eszközintelligencia**.  

3.  Az a **Home** lap a **Eszközintelligencia** csoportjában válassza **Leltárosztályok szerkesztése**.   

4.  Eszközintelligencia-jelentések engedélyezéséhez jelölje be **összes Eszközintelligencia-jelentési osztályainak engedélyezése** vagy **csak a kiválasztott Eszközintelligencia-jelentési osztály engedélyezése**, és legalább egy jelentési osztályt a megjelenített osztályok kiválasztása.  

    > [!NOTE]  
    >  Az ezen eljárással engedélyezett hardverleltárosztályoktól függő eszközintelligencia-jelentések nem jelenítenek meg adatokat mindaddig, amíg meg nem történik a hardverleltár keresése az ügyfeleken, és azok vissza nem adják azt.  


##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-client-settings-properties"></a>Az Eszközintelligencia hardverleltár-jelentési osztályainak engedélyezése az ügyfél beállításainak tulajdonságaiban  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >  **ügyfélbeállítások** > **Ügyfélügynök alapértelmezett beállításai**. Ha beállításokat hozott létre egyéni ügyfélbeállításokat, kiválaszthatja azokat, helyette.  

3.  Az a **Home** lapon > **tulajdonságok** csoportjában válassza **tulajdonságok**.   

4.  Válasszon **Hardverleltár** > **osztályok beállítása**. .  

5.  Válasszon **szűrés kategória szerint** > **Eszközintelligencia-jelentési osztályok**. Az osztályok listáját a rendszer csak az Eszközintelligencia hardverleltár-jelentési osztályaival frissíti.  

6.  Válasszon legalább egy jelentési osztályt a listából.  

    > [!NOTE]  
    >  Az ezen eljárással engedélyezett hardverleltárosztályoktól függő eszközintelligencia-jelentések nem jelenítenek meg adatokat mindaddig, amíg meg nem történik a hardverleltár keresése az ügyfeleken, és azok vissza nem adják azt.  
  

###  <a name="BKMK_InstallAssetIntelligenceSynchronizationPoint"></a> Install an Asset Intelligence Synchronization Point  

Az Eszközintelligencia szinkronizálási pont helyrendszer-szerepkör használatával csatlakozzon a Configuration Manager-helyek a System Center Online Eszközintelligencia-katalógus adatainak szinkronizálásához. Az Eszközintelligencia szinkronizációs pontja csak a Configuration Manager-hierarchia legfelső szintű helyén található helyrendszerre telepíthető, és 443-as TCP-port használatával a System Center Online szinkronizálása Internet-hozzáférést igényel.

Új eszközintelligencia-katalógusbeli adatok letöltése mellett az Eszközintelligencia szinkronizációs pontja feltölthet egyéni szoftvercím-adatokat is a System Center Online szolgáltatásba kategorizálás céljából. Microsoft feltöltött szoftvercímeket nyilvános információként kezeli. Győződjön meg arról, hogy saját egyéni szoftvercímei nem tartalmaznak bizalmas vagy szellemi tulajdont képező adatokat. Szoftvercím-kategorizálás kérésével kapcsolatos további információkért lásd: [Kategorizálatlan szoftvercímek katalógusfrissítés igénylése](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_RequestCatalogUpdate).  

##### <a name="to-install-an-asset-intelligence-synchronization-point-site-system-role"></a>Az Eszközintelligencia szinkronizációs pontja helyrendszerszerepkör telepítése  

1.  Kattintson a Configuration Manager konzol **felügyeleti**> **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**.  

3.  Az Eszközintelligencia szinkronizálási pont helyrendszer-szerepkör hozzáadása egy új vagy meglévő helyrendszer-kiszolgálóra:  

    -  Az egy **új helyrendszer-kiszolgáló**: Az a **Home** lap a **létrehozása** csoportjában válassza **helyrendszer-kiszolgáló létrehozása** varázsló elindításához.   

        > [!NOTE]  
        >  Alapértelmezés szerint a Configuration Manager telepíti a helyrendszerszerepkört, ha a telepítési fájlok települnek az első elérhető NTFS fájlrendszerű merevlemezen, amely a legtöbb szabad lemezterülettel rendelkezik. A Configuration Manager adott lemezegységeken elkerülése érdekében hozzon létre egy No_sms_on_drive.sms nevű üres fájlt, és a helyrendszer-kiszolgáló telepítése előtt másolja azt a lemezegység gyökérmappájába.  

    -  Az egy **meglévő helyrendszer-kiszolgáló**: Válassza ki a kiszolgálón, amelyen az Eszközintelligencia szinkronizálási pont helyrendszer-szerepkör telepítése. Ha úgy dönt, hogy a kiszolgáló, a kiszolgálóra már telepített helyrendszerszerepkörök listája a részletek ablaktáblán jelennek meg.  

         Az a **Home** lap a **Server** csoportjában válassza **Helyrendszerszerepkörök hozzáadása** varázsló elindításához.  

4.  Fejezze be a **általános** lap. Ha egy meglévő helyrendszer-kiszolgálóra veszi fel az Eszközintelligencia szinkronizációs pontját, ellenőrizze a korábban beállított értékeket.  

5.  Az a **Rendszerszerepkör kiválasztása** lapon jelölje be **Eszközintelligencia szinkronizációs pontja** az elérhető szerepkörök listájából.  

6.  Az a **eszköz az Eszközintelligencia szinkronizációs pontjának kapcsolatbeállításai** lapon, válassza ki **következő**.  

     Alapértelmezés szerint a **Használja ezt az eszközintelligencia-szinkronizációs pontot** beállítás van kiválasztva, és ezen a lapon nem konfigurálható. A System Center Online csak a 443-as TCP-porton keresztül fogad hálózati forgalmat, ezért az **SSL portszám** beállítás a varázsló ezen lapján nem konfigurálható.  

7.  Ha szükséges a System Center Online hitelesítési tanúsítvány (.pfx) fájl elérési útját is megadhat. Általában nincs szükség a tanúsítvány elérési útjának megadására, mert a kapcsolattanúsítványt automatikusan létrehozza a rendszer a helyrendszer-szerepkör telepítése során.  

8.  Az a **proxykiszolgáló beállításai** csoportjában adja meg, hogy az Eszközintelligencia szinkronizációs pontja kapcsolódáskor fog használni proxykiszolgálót a System Center Online a katalógus szinkronizálása, valamint hogy a hitelesítő adatok használata a proxykiszolgálóhoz való csatlakozáshoz-e.  

    > [!WARNING]  
    >  Ha proxykiszolgáló szükséges a System Center Online-hoz való csatlakozáskor, előfordulhat, hogy a kapcsolattanúsítvány is törlődik, ha a proxykiszolgálói hitelesítéshez konfigurált felhasználói fiók jelszava lejár.  

9. A **Szinkronizálás ütemezése** lapon adja meg, hogy az ütemezés szerint történjen-e az eszközintelligencia-katalógus szinkronizálása. Ha engedélyezi a szinkronizálási ütemezést, meg kell adnia egy egyszerű vagy egyéni szinkronizálási ütemezést. Ütemezett szinkronizálás során az Eszközintelligencia szinkronizációs pontja csatlakozik a System Center Online-hoz, hogy lekérje a legújabb eszközintelligencia-katalógust. Manuálisan is szinkronizálhatja az Eszközintelligencia-katalógusban a Configuration Manager konzolon az Eszközintelligencia csomópontból. Az Eszközintelligencia-katalógus szinkronizálási lépéseit, lásd: a [manuálisan szinkronizálhatja az Eszközintelligencia-katalógus](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ManuallySynchronizeCatalog) szakasz a [az Eszközintelligencia a System Center Configuration Managerben műveletei](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).  

10. Fejezze be a varázslót 

###  <a name="BKMK_EnableSuccessLogonEvents"></a> Enable auditing of success logon events  
 Négy eszközintelligencia-jelentés az ügyfélszámítógépek Windows biztonsági eseménynaplójából gyűjtött információkat jelenít meg. Megtudhatja, hogyan számítógép biztonsági házirend beállításainak bejelentkezés sikeres bejelentkezési események naplózásának engedélyezése.  

##### <a name="to-enable-success-logon-event-logging-by-using-a-local-security-policy"></a>Sikeres bejelentkezési esemény naplózásának engedélyezése egy helyi biztonsági házirend segítségével  

1.  A Configuration Manager-ügyfél számítógépen, válassza ki a **Start** > **felügyeleti eszközök** > **helyi biztonsági házirend**.  

2.  Az a **helyi biztonsági házirend** párbeszédpanel **biztonsági beállítások**, bontsa ki a **helyi házirendek**, és válassza a **naplórend**.  

3.  Az eredménypanelen kattintson duplán a **bejelentkezési események naplózása**, ügyeljen arra, hogy a **siker** jelölőnégyzet be van jelölve, és válassza a **OK**.  

##### <a name="to-enable-success-logon-event-logging-by-using-an-active-directory-domain-security-policy"></a>Sikeres bejelentkezési események naplózásának engedélyezése az Active Directory tartományi biztonsági házirend használatával  

1.  Válassza ki a tartományvezérlő számítógép **Start**, mutasson a **felügyeleti eszközök**, és válassza a **tartomány biztonsági házirendje**.  

2.  Az a **helyi biztonsági házirend** párbeszédpanel **biztonsági beállítások**, bontsa ki a **helyi házirendek**, és válassza a **naplórend**.  

3.  Az eredménypanelen kattintson duplán a **bejelentkezési események naplózása**, ügyeljen arra, hogy a **siker** jelölőnégyzet be van jelölve, és válassza a **OK**.  

###  <a name="BKMK_ImportSoftwareLicenseInformation"></a> Import software license information  
 A következő szakaszok ismertetik a szoftverlicenc importálása varázsló használatával a Configuration Manager-hely adatbázisában a Microsoft és az általános szoftverlicencelési információknak importálása szükséges eljárásokat. A szoftverlicenc-információk licenckimutatás-fájlokból a helyadatbázisba való importálásakor a helykiszolgáló számítógépfiókja számára **Teljes vezérlés** engedélyek szükségesek az NTFS fájlrendszerben azon fájlmegosztásra vonatkozóan, amely a szoftverlicenc-információk importálására szolgál.  

> [!IMPORTANT]  
>  Szoftverlicenc-információk a helyadatbázisba történő importálásakor meglévő szoftverlicenc-információk felülíródnak. Győződjön meg arról, hogy a Szoftverlicenc importálása varázslóval használt szoftverlicencfájl tartalmazza a szükséges szoftverlicenc-információk teljes listáját.  

##### <a name="to-import-software-license-information-into-the-asset-intelligence-catalog"></a>A szoftverlicenc-információk importálása az eszközintelligencia-katalógusba  

1.  Az a **eszközök és megfelelőség** munkaterületen, válassza a **Eszközintelligencia**.  

2.  Az a **Home** lap a **Eszközintelligencia** csoportjában válassza **szoftverlicencek importálása**.   

4.  Az **Importálás** lapon adja meg, hogy egy Microsoft mennyiségi licencelési (MVLS-) fájl (.xml vagy .csv) vagy egy általános licenckimutatás-fájlt (.csv) importál-e. Általános licenckimutatás-fájl létrehozásával kapcsolatos további információkért lásd a témakör későbbi, [Create a general license statement information file for import](#BKMK_CreateGeneralLicenseStatement) című szakaszát.  

    > [!WARNING]  
    >  Egy MVLS .csv formátumú fájl letöltéséhez, amelyet importálhat az eszközintelligencia-katalógusba, lásd [a Microsoft mennyiségi licencszolgáltatási központját](http://go.microsoft.com/fwlink/p/?LinkId=226547). Ezen információ eléréséhez regisztrált fiókkal kell rendelkeznie a webhelyen. Azzal kapcsolatban, hogy miként kérhet .xml formátumú MVLS-fájl, keresse meg a Microsoft képviselőjét.  

5.  Írja be a UNC elérési útját a licenckimutatás-fájl, vagy válasszon **Tallózás** válasszon egy hálózatot a megosztott mappához és fájlhoz.  

    > [!NOTE]  
    >  A közös mappát megfelelően titkosítani kell a licencinformációs fájlhoz való jogosulatlan hozzáférés elkerülése érdekében, és a varázslót futtató számítógép számítógépfiókjának Teljes vezérlés hozzáférési engedéllyel kell rendelkeznie a licencimportálási fájlt tartalmazó megosztásra vonatkozóan.  

6. Fejezze be a varázslót.  

###  <a name="BKMK_CreateGeneralLicenseStatement"></a> Create a general license statement information file for import  
 Általános licenckimutatást vesszővel tagolt (.csv) formátumban manuálisan létrehozott licencimportálási fájl használatával is importálhat az eszközintelligencia-katalógusba.  

> [!NOTE]  
>  Míg csak a **Név**, a **Kiadó**, a **Verzió**, és a **Hatályos mennyiség** mező kitöltése kötelező, a licencimportálási fájl első sorában az összes mezőt meg kell adni. Minden dátummező üzenetnek kell megjelennie a következő formátumban: Hónap/nap/év, például 08/04/2008.  

Az Eszközintelligencia az általános licenckimutatásban  megadott termékek egyeztetésekor használja a termék nevét és verzióját, a kiadó nevét viszont nem. Az általános licenckimutatásban használt terméknévnek pontosan egyeznie kell a helyadatbázisban tárolt terméknévvel. Eszközintelligencia a **hatályos mennyiség** az általános licenckimutatásban és hasonlítja össze a telepített termékek száma a szám, a Configuration Manager-készletben található a megadott szám.  

> [!TIP]  
>  Ahhoz, hogy a Configuration Manager-hely adatbázisában tárolt terméknevek teljes listáját, futtathatja a helyadatbázist a következő lekérdezést: SELECT ProductName0 FROM v_GS_INSTALLED_SOFTWARE.  

 Megadhatja a termék pontos verzióit, vagy a verziószám egy részét, például csak a főverziót. Az alábbi példák megadják az eredményül kapott verzióegyezéseket az általános licenckimutatás egy adott termékre vonatkozó verzióbejegyzéséhez.  

|Általános licenckimutatás-bejegyzés|Egyező helyadatbázis-bejegyzések|  
|-------------------------------------|------------------------------------|  
|Név: "MySoftware", ProductVersion0: "2"|ProductName0: "Mysoftware", ProductVersion0: "2.01.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.02.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.10.1234"|  
|Név: "MySoftware", verzió: "2.05"|ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"|  
|Név: "Mysoftware", "2" verziójú<br /><br /> Név: "Mysoftware", verzió: "2.05"|Hiba történt az importálás során. Az importálás sikertelen lesz, amikor egynél több bejegyzés azonos termékverzióval egyezik.|  
  

##### <a name="to-create-a-general-license-statement-import-file-by-using-microsoft-excel"></a>Általános licenckimutatási importfájl létrehozása a Microsoft Excel használatával  

1.  Nyissa meg a Microsoft Excelt, és hozzon létre egy új táblázatot.  

2.  Adja meg az összes szoftverlicenc-adat mezőnevét az új táblázat első sorában.  

3.  Adja meg az új táblázat második és az azt követő soraiban a szoftverlicencek adatait szükség szerint. Győződjön meg arról, hogy legalább az összes kötelező szoftverlicenc-adatmező értéke meg lett adva a következő sorokban minden egyes szükséges szoftverlicenchez. A táblázatban megadott szoftvercím nevének azonosnak kell lennie az ügyfélszámítógépen a hardverleltár futtatása után az Erőforrás-kezelőben megjelenített szoftvercímmel.  

4.  Mentse a fájlt .csv formátumban.  

5.  A .csv fájl másolja arra a fájlmegosztásra, amely a szoftverlicenc-információknak az eszközintelligencia-katalógusba való importálására szolgál.  

6.  A Configuration Manager konzolon a szoftverlicenc importálása varázsló segítségével importálja az újonnan létrehozott .csv fájlt.  

7.  Futtassa az Eszközintelligencia **licenc 15A – külső gyártótól származó szoftverek Licencegyeztetési jelentése** ellenőrzése, hogy a licencinformáció sikeresen importálva lett a az Eszközintelligencia-katalógusba.  

> [!NOTE]  
>  Egy tesztelési célokra használható általános szoftverlicencfájl példáért lásd: [példa Eszközintelligencia általános licenckimutatási importfájl a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md).  

#### <a name="sample-table-to-describe-software-licenses"></a>Mintatáblázat szoftverlicencek leírásához  
 Általános licenckimutatás-importfájl létrehozásakor az alábbi táblázatban szereplő adatok használhatók a szoftverlicencek leírására az eszközintelligencia-katalógusba való importáláshoz.  

|Oszlopnév|Adattípus|Kötelező|Példa|  
|-----------------|---------------|--------------|-------------|  
|Név|Legfeljebb 255 karakter hosszú lehet|Igen|Szoftvercím|  
|Kiadó|Legfeljebb 255 karakter hosszú lehet|Igen|Szoftverkiadó|  
|Verzió|Legfeljebb 255 karakter hosszú lehet|Igen|Szoftvercím verziója|  
|Nyelv|Legfeljebb 255 karakter hosszú lehet|Igen|Szoftvercím nyelve|  
|Hatályos mennyiség|Egész szám|Igen|Megvásárolt licencek száma|  
|Rendelésszám|Legfeljebb 255 karakter hosszú lehet|Nem|Megrendelés adatai|  
|Viszonteladó neve|Legfeljebb 255 karakter hosszú lehet|Nem|Viszonteladói információk|  
|Vásárlás dátuma|Dátum értéke a következő formátumban: HH/NN/ÉÉÉÉ|Nem|Licencvásárlás dátuma|  
|Megvásárolt támogatás|Bit értéke|Nem|0 vagy 1: Adja meg a 0 Igen vagy nem 1.|  
|Támogatás lejárati dátuma|Dátum értéke a következő formátumban: HH/NN/ÉÉÉÉ|Nem|Megvásárolt támogatás záró dátuma|  
|Megjegyzések|Legfeljebb 255 karakter hosszú lehet|Nem|Nem kötelező megjegyzések|  

###  <a name="BKMK_ConfigureMaintenanceTasks"></a> Configure Asset Intelligence maintenance tasks  
 Eszközintelligenciával kapcsolatosan a következő karbantartási feladatok érhetők el:  

-   **Ellenőrizze az alkalmazás címének és a Leltáradatokat**: Ellenőrzi, hogy az Eszközintelligencia-katalógusban a szoftvercím egyeztetve-e a szoftverleltár bejelentett szoftvercím. Alapértelmezés szerint ez a feladat engedélyezve van, és ütemezett szombaton déli 12:00-kor után és reggel 5:00 előtt A karbantartási feladat csak érhető el a legfelső szintű helyen a Configuration Manager-hierarchiában.  

-   **Telepített szoftverek adatainak összefoglalója**: A megjelenített információkat nyújt a **eszközök és megfelelőség** munkaterület, a a **leltározott szoftverek** csomópont alatt a **Eszközintelligencia** csomópont. A feladat futtatásakor a Configuration Manager az elsődleges helyen az összes leltározott szoftvercímek számát gyűjti. Alapértelmezés szerint ez a feladat engedélyezve van, és minden nap 0:00 óra után ütemezve és reggel 5:00 előtt A karbantartási feladat csak az elsődleges helyeken érhető el.  

##### <a name="to-configure-asset-intelligence-maintenance-tasks"></a>Eszközintelligencia-karbantartási feladatok konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **Helykonfiguráció** > **helyek**.  

3.  Válassza ki a helyet, amelyen az eszközintelligencia-karbantartási feladatot konfigurálja.  

4.  Az a **Home** lap a **beállítások** csoportjában válassza **Helykarbantartás**. Válasszon egy feladatot, és válassza a **szerkesztése** a következő beállításokat módosíthatja. 

      Azt javasoljuk, hogy a hely csúcsidején állítsa be az adott időszakban. Az időszak az az időköz, amelyben a feladat futhat. Az értéket a **Feladat tulajdonságai** párbeszédpanelen a **Kezdés ezután** és a **Legkésőbbi indítási idő** mezőkben megadott értékek határozzák meg.  

    A feladat azonnal is kezdeményezhető az aktuális nap kiválasztásával és a **Kezdés ezután** időt a jelenlegi időpont után néhány percre beállítva.  

7.  Válasszon **OK** a beállítások mentéséhez. A feladat most az ütemezése szerint fut.  

    > [!NOTE]  
    >  Ha egy feladatot az első kísérlet futtatása sikertelen, a Configuration Manager megkísérli futtassa újra a feladatot, amíg a feladat sikeresen lefutott, vagy az időszakot, amelyben a feladat futtatásához a rendszer megfelelt.  

