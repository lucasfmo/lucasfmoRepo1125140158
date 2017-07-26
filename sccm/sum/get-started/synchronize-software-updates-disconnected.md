---

title: "A frissítések szinkronizálása az internetkapcsolat - Configuration Manager |} Microsoft Docs"
description: "Futtassa a szoftverfrissítések szinkronizálását a legfelső szintű szoftverfrissítési ponton, amely nem kapcsolódik az internethez."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 1a997c30-8e71-4be5-89ee-41efb2c8d199
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: fd9c1e9418ff1956c6ef98753e23a293440179be
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---

# <a name="synchronize-software-updates-from-a-disconnected-software-update-point"></a>Szoftverfrissítések szinkronizálása leválasztott szoftverfrissítési pontról  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Ha a legfelső szintű szoftverfrissítési pont nincs csatlakoztatva az internethez, a WSUSUtil eszköz exportálás és importálás funkcióit kell használnia a szoftverfrissítések metaadainak szinkronizálásához. Választhat olyan meglévő WSUS-kiszolgálót nem a Configuration Manager-hierarchiában a szinkronizálás forrásaként. Ez a témakör az exportálás és importálás funkcióit, a WSUSUtil eszköz információ.  

 A szoftverfrissítések metaadatainak exportálásához és importálásához exportálnia kell a szoftverfrissítések metaadatait egy megadott exportálási kiszolgáló WSUS-adatbázisából, átmásolnia a helyileg tárolt licencfeltételi fájlokat a leválasztott szoftverfrissítési pontra, majd ezt követően importálnia a szoftverfrissítések metaadatait a leválasztott szoftverfrissítési pont WSUS-adatbázisába.  

 Az alábbi táblázatban kikeresheti, hogy melyik exportálási kiszolgálóra exportálja a szoftverfrissítés metaadatait.  

|Szoftverfrissítési pont|Felsőbb rétegbeli frissítési forrás csatlakoztatott szoftverfrissítési pontokhoz|Exportálási kiszolgáló leválasztott szoftverfrissítési ponthoz|  
|---------------------------|-----------------------------------------------------------------|------------------------------------------------------------|  
|Központi adminisztrációs hely|Microsoft Update (internet)<br /><br /> Meglévő WSUS-kiszolgáló|Válasszon egy WSUS-kiszolgálót, amely szinkronizálva van a Microsoft Update használatával, a szoftverfrissítési kategóriák, termékek és nyelvek, amelyekre szüksége van a Configuration Manager környezetben.|  
|Önálló elsődleges hely|Microsoft Update (internet)<br /><br /> Meglévő WSUS-kiszolgáló|Válasszon egy WSUS-kiszolgálót, amely szinkronizálva van a Microsoft Update használatával, a szoftverfrissítési kategóriák, termékek és nyelvek, amelyekre szüksége van a Configuration Manager környezetben.|  

 Az exportálás elindítása előtt ellenőrizze, hogy a szoftverfrissítések szinkronizálása befejeződött-e a kiválasztott exportálási kiszolgálón, és hogy az a legújabb szoftverfrissítési metaadatokat tartalmazza. A következő eljárás során meggyőződhet arról, hogy a szoftverfrissítések szinkronizálása sikeresen befejeződött.  

#### <a name="to-verify-that-software-updates-synchronization-has-completed-successfully-on-the-export-server"></a>Annak ellenőrzése, hogy a szoftverfrissítések szinkronizálása sikeresen befejeződött az exportálási kiszolgálón  

1.  Nyissa meg a WSUS adminisztrációs konzolt, és csatlakozzon az exportálási kiszolgáló WSUS-adatbázisához.  

2.  A WSUS adminisztrációs konzolon kattintson a **Szinkronizálások**elemre. A szoftverfrissítések szinkronizálási kísérletei az eredmények ablaktábláján jelennek meg.  

3.  Keresse meg a legutolsó szoftverfrissítés-szinkronizálási kísérletet, és ellenőrizze, hogy sikeresen befejeződött-e.  

> [!IMPORTANT]  
>  Az WSUSUtil eszköznek futnia kell az exportálási kiszolgálón a szoftverfrissítés metaadatainak exportálásához, és a leválasztott szoftverfrissítésipont-kiszolgálón is futnia kell a szoftverfrissítés metaadatainak importálásához. A WSUSUtil eszközt futtató felhasználónak ezenkívül minden egyes kiszolgálón a helyi felhasználói csoport tagjának kell lennie.  

## <a name="export-process-for-software-updates"></a>A szoftverfrissítések exportálása  
 A szoftverfrissítések exportálási folyamata két fő lépésből áll: a helyben tárolt licencfeltételi fájlok másolása a leválasztott szoftverfrissítési pontra, majd a szoftverfrissítések metaadatainak exportálása a WSUS-adatbázisból az exportálási kiszolgálóra.  

 A helyileg tárolt licencfeltételi metaadatok leválasztott szoftverfrissítési pontra történő másolásához a következő eljárás használható.  

#### <a name="to-copy-local-files-from-the-export-server-to-the-disconnected-software-update-point-server"></a>Helyi fájlok másolása exportálási kiszolgálóról a leválasztott szoftverfrissítésipont-kiszolgálóra  

1.  Az exportálási kiszolgálón navigáljon a szoftverfrissítéseket és azok licencfeltételeit tartalmazó mappához. Alapértelmezés szerint a WSUS-kiszolgáló a <*WSUSTelepítésiMeghajtó*>\WSUS\WSUSContent\\ mappában tárolja a fájlokat, ahol a *WSUSTelepítésiMeghajtó* az a meghajtó, amelyre a WSUS telepítve van.  

2.  Másoljon innen minden fájlt és mappát a leválasztott szoftverfrissítésipont-kiszolgáló WSUSContent mappájába.  

 Szoftverfrissítések metaadatainak az exportálási kiszolgáló WSUS-adatbázisából történő exportálásához a következő eljárás használható.  

#### <a name="to-export-software-updates-metadata-from-the-wsus-database-on-the-export-server"></a>Szoftverfrissítések metaadatainak az exportálási kiszolgáló WSUS-adatbázisából történő exportálása  

1.  Az exportálási kiszolgálón a parancssorban keresse meg a WSUSutil.exe fájlt tartalmazó mappát. Alapértelmezés szerint az eszköz a %*ProgramFiles*%\Update Services\Tools mappában található. Például ha az eszköz az alapértelmezett helyen található, a **cd %ProgramFiles%\Update Services\Tools**mappát adja meg.  

2.  Írja be a következőket a szoftverfrissítés metaadatainak csomagfájlba történő exportálásához:  

     **wsusutil.exe export**  *packagename*  *logfile*  

     Példa:  

     **wsusutil.exe export export.cab export.log**  

     A formátum a következőképpen összegezhető: A WSUSutil.exe az exportálási beállítás, az exportálás során létrehozott .cab exportfájl neve és a naplófájl neve követi. A WSUSutil.exe exportálja a metaadatokat az exportálási kiszolgálóról, és naplófájlt hoz létre a műveletről.  

    > [!NOTE]  
    >  A csomagnak (.cab fájl) és a naplófájlnak egyedi névvel kell rendelkeznie a mappában.  

3.  Helyezze át az exportálási csomagot abba a mappába, amely tartalmazza a WSUSutil.exe fájlt az importálási WSUS-kiszolgálón.  

    > [!NOTE]  
    >  Ha áthelyezi ezt a csomagot a szóban forgó mappába, az megkönnyíti az importálást. A csomagot bárhová áthelyezheti, ahol az importálási kiszolgáló hozzáfér; ezt követően adja meg a helyet a WSUSutil.exe futtatásakor.  

## <a name="import-software-updates-metadata"></a>A szoftverfrissítések metaadatainak importálása  
 A szoftverfrissítés metaadatainak az exportálási kiszolgálóról a leválasztott szoftverfrissítési pontra történő importálásához a következő eljárás használható.  

> [!IMPORTANT]  
>  Soha ne importáljon nem megbízható helyről exportált adatot. Ha olyan helyről importál tartalmat, amely nem megbízható, azzal veszélyeztetheti a WSUS-kiszolgáló biztonságát.  

#### <a name="to-import-metadata-to-the-database-of-the-import-server"></a>Metaadatok importálása az importálási kiszolgáló adatbázisába  

1.  A WSUS-kiszolgálón a parancssorban navigáljon a WSUSutil.exe fájlt tartalmazó mappához. Alapértelmezés szerint az eszköz a %*ProgramFiles*%\Update Services\Tools mappában található.  

2.  Írja be a következőket:  

     **wsusutil.exe import**  *packagename*  *logfile*  

     Példa:  

     **wsusutil.exe import export.cab import.log**  

     A formátum a következőképpen összegezhető: A WSUSutil.exe az importálási parancs, a csomag fájl nevét (.cab) jön létre az exportálás során, ha egy másik mappában van a csomag fájl elérési útját, és a naplófájl neve követi. A WSUSutil.exe importálja a metaadatokat az exportálási kiszolgálóról, és naplófájlt hoz létre a műveletről.  

## <a name="next-steps"></a>További lépések
Szoftverfrissítések első szinkronizálása, vagy nincsenek új besorolások vagy termékek érhető el, miután be kell után [az új besorolások és termékek konfigurálása](configure-classifications-and-products.md) szoftverfrissítéseket szinkronizálja az új feltételeket.

Szoftverfrissítések exportálhatja a feltételeket, amelyek van szüksége, miután [szoftverfrissítések beállításainak kezelése](manage-settings-for-software-updates.md).  

