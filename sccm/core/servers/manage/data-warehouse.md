---
title: "Adatraktár |} Microsoft Docs"
description: "Data Warehouse szolgáltatási pont és az adatbázis a System Center Configuration Managerhez"
ms.custom: na
ms.date: 3/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf43e69-68b4-469a-ad58-9b66deb29057
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3c2a07f560e0aa3d2beb7cc50e71c98ac45c27e1
ms.openlocfilehash: 9239f6e749c368835e8594ca2d07378d8555b99e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
#  <a name="the-data-warehouse-service-point-for-system-center-configuration-manager"></a>Az adatraktár pontja a System Center Configuration Managerhez
*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Verzió 1702 a Data Warehouse pont segítségével tárolja, és hosszú távú múltbeli adatok jelentése a Configuration Manager telepítéshez kezdve.

> [!TIP]  
> Bevezetett 1702 verziójával, a Data Warehouse pont egy előzetes verziójú funkció. Az engedélyezéshez, lásd: [előzetes kiadású szolgáltatások használata](/sccm/core/servers/manage/pre-release-features).

Az adatraktár legfeljebb 2 TB adat, a változások követése Timestamp támogatja. Adatok tárolása az adatraktár-adatbázis a Configuration Manager helykiszolgáló helyadatbázisból automatizált szinkronizálások úgy érhető el. Ez az információ a jelentéskészítési szolgáltatási pont az majd érhető el.


Szinkronizált adatokat tartalmaz a következő, a globális adatok és a helyadatok csoportokból:
- Infrastruktúra-állapot
- Biztonság
- Megfelelőségi
- Kártevő szoftver   
- Szoftverek központi telepítése
- Leltár részleteit (azonban nem szinkronizált leltárelőzmények törlése)

Amikor telepíti a helyrendszerszerepkört, az telepíti, és konfigurálja az adatraktár-adatbázis. Azt is telepít néhány könnyen kereshet, jelentések és jelentés ezeket az adatokat.



## <a name="prerequisites-for-the-data-warehouse-service-point"></a>A Data Warehouse pont előfeltételei
- A helyrendszer-szerepkör telepítéséhez használt számítógépnek szükséges a .NET-keretrendszer 4.5.2-es vagy újabb.
- A helyrendszer-szerepkör telepítéséhez használt számítógépnek számítógépfiókjának szinkronizálja az adatokat az adatraktár-adatbázis a szolgál. Ezt a fiókot a következő engedélyekkel kell rendelkeznie:  
  - **Rendszergazda** a számítógépen, amely az adatraktár-adatbázist tárolni fogja.
  - **DB_owner** engedélyt az adatraktár-adatbázis.
-    Az adatraktár-adatbázis támogatott az alapértelmezett vagy megnevezett példány az SQL Server 2012 vagy újabb. A kiadás Enterprise vagy Datacenter kell lennie.
  - SQL Server AlwaysOn rendelkezésre állási csoportot: Ez a konfiguráció nem támogatott.
  - SQL Server-fürt: SQL Server feladatátvevő fürtök nem támogatottak. Ennek az az oka az adatraktár-adatbázis nem mélyen tesztelték SQL Server feladatátvevő fürtökön.
  - Ha az adatraktár-adatbázis távoli, a helykiszolgáló adatbázisából, az adatbázist futtató SQL Server külön licenccel kell rendelkeznie.

> [!IMPORTANT]  
> Az adatraktár nem támogatott, ha az adatraktár pontját vagy, amely futtatja az adatraktár-adatbázist futtató számítógépen, futtatja a következő nyelvek valamelyikével:
> - JPN-japán
> - KOR – koreai
> - CHS – egyszerű kínai
> - CHT – hagyományos kínai, a probléma egy későbbi kiadásban megszűnik.


## <a name="install-the-data-warehouse"></a>Az adatraktár telepítése
Az adatok adatraktár helyrendszerszerepkör csak a (egy központi adminisztrációs hely vagy önálló elsődleges helyen) a hierarchia legfelső szintű helyen is telepítheti.

Mindegyik hierarchia ezen szerepkör egyetlen példányát támogatja, és bármely helyrendszeren, a legfelső szintű hely is található. Az adatraktár adatbázisát futtató SQL Server lehet a helyrendszer-szerepkör a helyi vagy távoli. Bár az adatraktár együttműködve biztosítja a jelentéskészítési szolgáltatási pont ugyanazon a helyen telepített, a két helyrendszer-szerepkörök nem kell ugyanarra a kiszolgálóra telepíteni.   

A szerepkör telepítéséhez használja a **helyrendszer-szerepkörök hozzáadása varázslóval** vagy a **helyrendszer-kiszolgáló létrehozása varázsló**. Lásd: [helyrendszerszerepkörök telepítése](/sccm/core/servers/deploy/configure/install-site-system-roles) további információt.  

A szerepkör telepítésekor a Configuration Manager létrehozza az adatraktár-adatbázis, az SQL Server megadott példányán. Ha megad egy létező adatbázis nevét (, mint ha Ön [az adatraktár-adatbázis áthelyezése egy új SQL Server](#move-the-data-warehouse-database)), a Configuration Manager nem hoz létre egy új adatbázist, de Ehelyett használja a megadott.

### <a name="configurations-used-during-installation"></a>Telepítés során használt konfigurációk
**Rendszerszerepkör kiválasztása** lap:  

**Általános** lap:
-     **A Configuration Manager az adatraktár-adatbázis kapcsolati beállításait**:
 - **SQL Server teljes tartományneve**:  
 Adja meg a teljes tartománynév (FQDN) a kiszolgáló, amelyen az adatraktár szolgáltatási pont adatbázisának.
 - **SQL Server-példány neve, ha van ilyen**:   
 Ha nem használja az SQL Server alapértelmezett példányán, meg kell adnia a példány.
 - **Az adatbázisnév**:   
 Adja meg az adatraktár-adatbázis nevét.  A Configuration Manager ezen a néven létrehoz az adatraktár-adatbázis. Ha egy már létező adatbázisnevet ad meg az SQL server-példányt, a Configuration Manager fog használni, hogy az adatbázis.
 - **A kapcsolathoz használt SQL Server port**:   
 Adja meg a TCP/IP-portot a data warehouse datbase futtató SQL Server konfigurált. Ezt a portot használják az adatraktár-szinkronizálási szolgáltatás csatlakozni az adatraktár-adatbázis.  

**Szinkronizálás ütemezése** lap:   
- **Szinkronizálás ütemezése**:
 - **Kezdési idő**:  
 Adja meg az idő, amelyet az adatraktár-szinkronizálás elindításához.
 - **Ismétlődési**:
    - **Napi**: Adja meg, hogy szinkronizálás naponta fut-e.
    - **Heti**: Adjon meg egy nap, minden héten és heti ismétlődési szinkronizálás.

## <a name="reporting"></a>Jelentéskészítés
A Data Warehouse szolgáltatási pont telepítése után a több jelentést a jelentéskészítési szolgáltatási ponton ugyanazon a helyen telepített elérhetővé válnak. Ha a Data Warehouse szolgáltatási pont egy jelentéskészítési szolgáltatási pont telepítése előtt telepít, a jelentések megkapja automatikusan Ha később telepíti a jelentéskészítési szolgáltatási ponton.

A Data Warehouse helyrendszer-szerepkör magában foglalja az alábbi jelentések, amelyhez tartozik egy kategóriát a **adatraktár**:
 - **Alkalmazástelepítés - előzmény**:   
 Az alkalmazás központi telepítését egy adott alkalmazás és a gép részleteinek megtekintése.
 - **Az Endpoint Protection és a szoftverfrissítések frissítési megfelelőségét - előzmény**: Hiányzó szoftverfrissítések számítógépek megtekintése.  
 - **Általános Hardverleltár - előzmény**:      
 Egy adott számítógép összes Hardverleltár megjelenítése.
 - **Általános szoftverleltár - előzmény**:      
 Egy adott számítógép összes szoftverleltár megjelenítése.
 - **Infrastruktúra állapotának áttekintése - előzmény**:     
 A Configuration Manager-infrastruktúra állapotának áttekintése
 - **Észlelt kártevők listáját - előzmény**:     
 Nézet kártevők, amelyek a szervezet észlelhető.
 - **Szoftver telepítési összefoglaló - előzmény**:     
 Az egy adott hirdetmény és a gép szoftverterjesztés összefoglalása.


## <a name="expand-an-existing-stand-alone-primary-into-a-hierarchy"></a>Bontsa ki a meglévő önálló elsődleges hierarchiává
Bontsa ki egy meglévő önálló elsődleges hely központi adminisztrációs hely telepítése előtt el kell távolítania a Data Warehouse szolgáltatási pont szerepkör. A központi adminisztrációs hely telepítése után telepítse a helyrendszerszerepkör a központi adminisztrációs helyen.  

Egy az adatraktár-adatbázis áthelyezése, eltérően ennek eredményeként adatvesztést a végfelhasználókhoz korábban szinkronizálta az elsődleges helyen. Biztonsági másolatot az adatbázisról, az elsődleges helyről, és állítsa vissza azt a központi adminisztrációs helyen nem támogatott.




## <a name="move-the-data-warehouse-database"></a>Az adatraktár-adatbázis áthelyezése
Az adatraktár-adatbázis áthelyezése egy új SQL Server tegye a következőket:

1.    Használjon SQL Server Management Studio biztonsági másolatot az adatraktár-adatbázis, és majd állítsa vissza az adatbázist az új számítógépen, amely üzemelteti az adatraktár SQL Server.   
> [!NOTE]     
> Után állítsa vissza az adatbázist az új kiszolgálón, győződjön meg arról, hogy az adatbázis-hozzáférési engedélyek megegyeznek az új adatraktár-adatbázis a azzal, mintha az eredeti adatraktár-adatbázis.  

2.    A Configuration Manager konzol használatával a Data Warehouse szolgáltatási pont helyrendszerszerepkörének eltávolítása az aktuális kiszolgáló.
3.    Telepítse újra az adatraktár szolgáltatási pont, és adja meg az új SQL-kiszolgáló és a visszaállított Data Warehouse-adatbázis-példány nevét.
4.    A helyrendszer-szerepkör telepítése után az áthelyezés befejeződött.

## <a name="troubleshooting-data-warehouse-issues"></a>Data warehouse problémák elhárítása
**Naplófájlok**:  
A Data Warehouse szolgáltatási pont telepítése vagy az adatok szinkronizálását az kapcsolatos problémák kivizsgálásához használja a következő naplók kapcsolódnak:
 - *DWSSMSI.log* és *DWSSSetup.log* -ezek a naplók segítségével vizsgálja meg a hibákat, az adatraktár szolgáltatási pont telepítése során.
 - *Microsoft.ConfigMgrDataWarehouse.log* – Ez a napló használatával vizsgálja meg a helyadatbázist az adatraktár-adatbázis adatainak szinkronizálása.

**Hiba beállítása**  
 A Data Warehouse szolgáltatási pont telepítése nem sikerül egy távoli helyrendszer-kiszolgálón az adott számítógépre telepített első helyrendszer-szerepkör esetén az adatraktárba.  
  - **Megoldás**:   
    Győződjön meg arról, hogy a számítógépen, telepíti a Data Warehouse pont már fut-e legalább egy másik helyrendszerszerepkör.  


**Ismert problémák szinkronizálási**:   
Szinkronizálás a következő hibát jelez a *Microsoft.ConfigMgrDataWarehouse.log*: **"sémaobjektumok feltöltése sikertelen"**  
 - **Megoldás**:  
    Győződjön meg arról, hogy a helyrendszerszerepkört üzemeltető számítógép számítógépfiókjának egy **db_owner** meg az adatraktár-adatbázis.

Adatraktár-jelentések nem nyílik meg, ha az adatraktár-adatbázis és a jelentéskészítési szolgáltatási pont más helyrendszereket.  

 - **Megoldás**:  
    Engedélyezze a **jelentéskészítési szolgáltatási pont fiókja** a **db_datareader** engedélyt az adatraktár-adatbázis.

A data warehouse jelentés megnyitásakor a következő hibaüzenet:

*Hiba történt a jelentés feldolgozása során. (rsProcessingAborted) Az adatforrás "AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_" kapcsolat nem hozható létre. (rsErrorOpeningConnection) Sikeresen létrejött egy kapcsolat a kiszolgálóval, de hiba történt a bejelentkezés előtti kézfogás során. (szolgáltató: SSL-szolgáltató, hiba: 0 – a tanúsítványlánc ki, amely nem megbízható hatóság.)*

- **Megoldás**: Az alábbi lépések segítségével tanúsítványok konfigurálása:

  1. Az adatraktár adatbázisát üzemeltető számítógépen:

    1. Nyissa meg az IIS, kattintson **kiszolgálótanúsítványok**, kattintson a jobb gombbal a **önaláírt tanúsítvány létrehozása**, és adja meg a tanúsítvány neve megegyezik a "rövid neve" **adatok adatraktár SQL Server Identification Certificate**. A tanúsítvány választása szerint **személyes**.
    2. Nyissa meg **SQL Server Configuration Manager**a **SQL Server hálózati konfigurációja**, kattintson a jobb gombbal, válassza ki a **tulajdonságok** alatt **MSSQLSERVER protokolljai**. Ezt követően a **tanúsítvány** lapon jelölje be **adatok adatraktár SQL Server Identification Certificate** a tanúsítványt, majd mentse a módosításokat.  
    3. Nyissa meg **SQL Server Configuration Manager**a **SQL Server Services**, indítsa újra a **SQL Server szolgáltatás** és **hibajelentési szolgáltatás**.
    4.    Nyissa meg a Microsoft Management Console (MMC), és adja hozzá a beépülő modul a **tanúsítványok**, jelölje be a tanúsítvány kezelése **számítógépfiók** a helyi számítógép. Ezt követően az MMC-konzolon bontsa ki a **személyes** mappa > **tanúsítványok**, és exportálja a **adatok adatraktár SQL Server Identification Certificate** , egy **DER kódolású bináris X.509 (. CER)** fájlt.    
  2.    A számítógép, amelyen az SQL Server Reporting Services, nyissa meg az MMC-t, és adja hozzá a beépülő modul a **tanúsítványok**, majd válassza ki a tanúsítvány kezelése **számítógépfiók**. Az a **megbízható legfelső szintű hitelesítésszolgáltatók** mappa importálása a **adatok adatraktár SQL Server Identification Certificate**.


## <a name="data-warehouse-dataflow"></a>Data Warehouse adatfolyam   
![Datawarehouse_flow](./media/datawarehouse.png)

**Adattárolás és szinkronizálás**

| Lépés   | Részletek  |
|:------:|-----------|  
| **1**  |     A helykiszolgáló továbbítja, és a hely adatbázisában tárolja az adatokat.  |  
| **2**  |      Ütemezési és konfigurációs alapján, az adatraktár szolgáltatási pont adatok lekérése a hely adatbázisába.  |  
| **3**  |  A Data Warehouse pont továbbítja, és a szinkronizált adatok másolatát tárolja az adatraktár adatbázisából. |  
**Jelentéskészítés**

| Lépés   | Részletek  |
|:------:|-----------|  
| **A**  |  A beépített jelentések használatával, a felhasználó kér adatokat. A kérés átadódik a Reporting Services pont az SQL Server Reporting Services segítségével. |  
| **B**  |      A legtöbb jelentések aktuális információkat, és ezeket a kérelmeket van futtatni a helyadatbázist. |  
| **C**  | Amikor jelentést kér jelentéseket egyikének használatával előzményadatait, egy *kategória* a **adatraktár**, a kérelem futtatása ellen az adatraktár adatbázisából.   |  

