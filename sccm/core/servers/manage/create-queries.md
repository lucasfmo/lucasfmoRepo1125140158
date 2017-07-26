---
title: "Lekérdezések létrehozása |} Microsoft Docs"
description: "Hogyan hozhat létre, és importálja a System Center Configuration Managerben lekérdezések felderítése. Mintalekérdezéseket és tippek tartalmaz."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 868049d3-3209-47ec-b34a-9cc26941893a
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 89bd798339489071fdb69325c957fefda32621e9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-queries-in-system-center-configuration-manager"></a>Lekérdezések létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör következő részeiben használatával alakítsa ki létrehozása vagy importálása a System Center Configuration Managerben lekérdezések.  

-   [How to Create Queries](#BKMK_Create)  

-   [How to Import Queries](#BKMK_Import)  

-   [Example WQL Queries](#BKMK_Example)  

##  <a name="BKMK_Create"></a> Lekérdezések létrehozása  
 Ezzel az eljárással hozhat létre lekérdezéseket a Configuration Manager alkalmazásban.  

#### <a name="to-create-a-query"></a>Lekérdezés létrehozása  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen kattintson a **Lekérdezések** lehetőségre, majd a **Lekérdezés létrehozása** lehetőségre a **Kezdőlap** lap **Létrehozás**csoportjában.  

3.  A **Lekérdezés létrehozása varázsló** **Általános**lapján adjon meg egy egyedi nevet, és nem kötelezően egy megjegyzést is megadhat a lekérdezéshez.  

4.  Ha egy meglévő lekérdezést szeretne importálni, hogy az új lekérdezés alapjaként használja, kattintson a **Lekérdezési utasítás importálása** lehetőségre, majd a **Lekérdezés tallózása** párbeszédpanelen válassza ki az importálni kívánt meglévő lekérdezést, és kattintson az **OK**gombra.  

5.  Az **Objektumtípus** listából válassza ki az objektumtípust, melyet szeretne, ha a lekérdezés visszaadna. A következő táblázat ismertet néhány példát a kereshető objektumtípusokra:  

    |Objektumtípus|Leírás|  
    |-----------------|-----------------|  
    |**Rendszererőforrás**|Segítségével jellemző rendszerattribútumokra, például az eszközök NetBIOS-nevére, az ügyfélverzióra, a ügyfél IP-címére és az Active Directory tartományi szolgáltatások adataira kereshet rá.|  
    |**Felhasználói erőforrás**|Segítségével jellemző felhasználói adatokra, például felhasználónevekre, felhasználói csoportok nevére és biztonsági csoportok nevére kereshet rá.|  
    |**Környezet**|Segítségével központi telepítések jellemző attribútumaira, például a központi telepítés nevére, ütemezésére és a gyűjteményre kereshet rá, amelyben telepítve lett.|  

6.  Kattintson a **lekérdezési utasítás szerkesztése** megnyitásához a  *&lt;lekérdezésnév\>***utasítás tulajdonságai** párbeszédpanel megnyitásához.  

7.  A a **általános** lapra a  *&lt;lekérdezésnév\>***utasítás tulajdonságai** párbeszédpanelen adja meg a lekérdezés által visszaadott attribútumokat, és hogyan vannak jeleníthető meg. Egy új attribútum hozzáadásához kattintson az **Új** ikonra. A **Lekérdezés nyelvének megjelenítése** lehetőségre is kattinthat, hogy közvetlenül WMI Query Language (WQL) nyelven adja meg vagy szerkessze a lekérdezést. Példa WMI-lekérdezéseket a témakör [Example WQL queries](#BKMK_Example) című szakaszában találhat.  

    > [!TIP]  
    >  A következő MSDN referenciadokumentumok segítségével hozhatja létre saját WQL-lekérdezéseit:  
    >   
    >  -   [WQL (SQL for WMI)](http://go.microsoft.com/fwlink/p/?LinkId=256653)  
    > -   [WHERE záradék](http://go.microsoft.com/fwlink/p/?LinkId=256654)  
    > -   [WQL-operátorok](http://go.microsoft.com/fwlink/p/?LinkId=256655)  

8.  Az a **feltételek** lapján a  *&lt;lekérdezésnév\>***utasítás tulajdonságai** párbeszédpanelen adja meg a lekérdezési eredmények szűkítéséhez használt feltételeket. A lekérdezési eredményekben visszaadhatja például csak az **XYZ** helykódú erőforrásokat. Egy lekérdezéshez több feltételt is beállíthat.  

    > [!IMPORTANT]  
    >  Ha feltételt nem tartalmazó lekérdezést hoz létre, az a **Minden rendszer** gyűjtemény minden eszközét visszaadja.  

9. A a **csatlakozik** lapra a  *&lt;lekérdezésnév\>***utasítás tulajdonságai** párbeszédpanelen két különböző attribútumból származó adatok egyesítése a lekérdezés eredménye. A Configuration Manager automatikusan létrehozza a lekérdezési összekapcsolásokat, amikor különböző attribútumokat jelöl ki a lekérdezési eredményhez, bár a **illesztések** lapon összetettebb beállításokat biztosítja. A System Center 2012 Configuration Manager által támogatott Attribútumosztályok az alábbi táblázatban láthatók:  

    |Összekapcsolás típusa|Leírás|  
    |---------------|-----------------|  
    |Belső|Jelenik meg, csak a megfelelő eredményeket - automatikusan létrehozott összekapcsolások mindig ezt használják.|  
    |Bal oldali|Az alapattribútum összes eredményét, a hozzákapcsolandó attribútumnak pedig csak a megfelelő eredményeit jeleníti meg.|  
    |Jobb oldali|Az hozzákapcsolandó attribútum összes eredményét, az alapattribútumnak pedig csak a megfelelő eredményeit jeleníti meg.|  
    |Teljes|Mind az alapattribútum, mind pedig a hozzákapcsolandó attribútum összes eredményét megjeleníti.|  

     Az összekapcsolási műveletek használatáról további információt az SQL Server dokumentációjában talál.  

10. Kattintson a **OK** bezárásához a  *&lt;lekérdezésnév\>***utasítás tulajdonságai** párbeszédpanel megnyitásához.  

11. A **Lekérdezés létrehozása varázsló** **Általános**lapján adja meg, hogy a lekérdezés eredményei nincsenek egy gyűjtemény tagjaira korlátozva, egy megadott gyűjtemény tagjaira vannak korlátozva, vagy a rendszer a lekérdezés minden futtatásakor kérjen be egy gyűjteményt.  

12. A lekérdezés létrehozásához fejezze be a varázslót. Az új lekérdezés megjelenik a **Figyelés** munkaterület **Lekérdezések** csomópontjában.  

##  <a name="BKMK_Import"></a> Lekérdezések importálása  
 Ezzel az eljárással importálhat egy lekérdezést a Configuration Managerbe. További információ a lekérdezések exportálásáról: [kezelése a System Center Configuration Managerben lekérdezések](../../../core/servers/manage/manage-queries.md).  

#### <a name="to-import-a-query"></a>Lekérdezés importálása  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen kattintson a **Lekérdezések** lehetőségre, majd az **Objektumok importálása** lehetőségre a **Kezdőlap** lap **Létrehozás**csoportjában.  

3.  Az **Objektumok importálása varázsló** **MOF-fájl neve**lapján kattintson a **Tallózás** lehetőségre az importálni kívánt, a lekérdezést tartalmazó Managed Object Format (MOF) formátumú fájl kijelöléséhez.  

4.  Tekintse át az importálni kívánt lekérdezés adatait, és fejezze be a varázslót. Az új lekérdezés megjelenik a **Figyelés** munkaterület **Lekérdezések** csomópontjában.  

##  <a name="BKMK_Example"></a> Example WQL queries  
 Ez a szakasz példa WMI-lekérdezéseket tartalmaz, melyeket használhat a hierarchiában, vagy módosíthat más célból. Ezen lekérdezések használatához kattintson a **Lekérdezés nyelvének megjelenítése** lehetőségre a **Lekérdezési utasítás tulajdonságai** párbeszédpanelen, majd másolja és illessze be a lekérdezést a **Lekérdezési utasítás** mezőbe.  

> [!TIP]  
>  Tetszőleges karakterlánc jelölésére a **%** helyettesítő karaktert használhatja. Például a **%Visio%** karakterlánc a Microsoft Office Visio 2010-et adja vissza.  

### <a name="computers-that-run-windows-7"></a>Windows 7 rendszerű számítógépek  
 A következő lekérdezéssel adhatja vissza az összes Windows 7 rendszerű számítógép NetBIOS-nevét és operációsrendszer-verzióját.  

> [!TIP]  
>  A Windows Server 2008 R2 rendszerű számítógépek visszaadásához módosítsa a **%Workstation 6.1%** kifejezést a **%Server 6.1%**kifejezésre.  

```  
select SMS_R_System.NetbiosName,  
SMS_R_System.OperatingSystemNameandVersion from    
SMS_R_System where   
SMS_R_System.OperatingSystemNameandVersion like "%Workstation 6.1%"  
```  

### <a name="computers-with-a-specific-software-package-installed"></a>Meghatározott szoftvercsomaggal rendelkező számítógépek  
 A következő lekérdezéssel adhatja vissza az összes olyan számítógép NetBIOS-nevét  és szoftvercsomagnevét, amelyen telepítve van egy adott szoftvercsomag. A példa megjeleníti az összes számítógépet, melyen telepítve van a Microsoft Visio egy verziója. Cserélje le a **%Visio%** kifejezést a lekérdezni kívánt szoftvercsomagra.  

> [!TIP]  
>  Ez a lekérdezés a Windows Vezérlőpult programlistájában megjelenített nevek alapján keresi meg a szoftvercsomagot.  

```  
select SMS_R_System.NetbiosName,   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName from    
SMS_R_System inner join SMS_G_System_ADD_REMOVE_PROGRAMS on   
SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceId =   
SMS_R_System.ResourceId where   
SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "%Visio%"  
```  

### <a name="computers-that-are-in-a-specific-active-directory-domain-services-organizational-unit-ou"></a>Az Active Directory tartományi szolgáltatások egy adott szervezeti egységében (OU) található számítógépek  
 A következő lekérdezéssel adhatja vissza az összes, a megadott szervezeti egységben található számítógép NetBIOS-nevét és szervezeti egységének nevét. Cseréje le az **OU Name** szöveget a lekérdezni kívánt szervezeti egység nevére.  

```  
select SMS_R_System.NetbiosName,   
SMS_R_System.SystemOUName from    
SMS_R_System where   
SMS_R_System.SystemOUName = "OU Name"  
```  

### <a name="computers-with-a-specific-netbios-name"></a>Megadott NetBIOS-névvel rendelkező számítógépek  
 A következő lekérdezéssel adhatja vissza az összes számítógép NetBIOS-nevét, mely egy meghatározott karakterlánccal kezdődik. Ebben a példában a lekérdezés visszaadja az összes számítógépet, melynek NetBIOS-neve az **ABC**karakterlánccal kezdődik.  

```  
select SMS_R_System.NetbiosName from    
SMS_R_System where SMS_R_System.NetbiosName like "ABC%"  
```  

###  <a name="BKMK_DeviceType"></a> Adott típusú eszközök  
 Eszköztípusok tárolódnak a Configuration Manager adatbázishoz az azzal erőforrásosztály **sms_r_system** és az attribútum neve **AgentEdition**. A következő lekérdezéssel kérheti le kizárólag azokat az eszközöket, amelyek megfelelnek a megadott eszköztípus ügynökverziójának:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = <Device ID>  
```  

 Használja a következő értékei  *&lt;Eszközazonosító\>*:  

|Eszköz típusa|AgentEdition mező értéke|  
|-----------------|---------------------------|  
|Windows rendszerű asztali vagy hordozható számítógép|0|  
|Windows ARM-alapú eszköz (Windows RT rendszerű)|1|  
|Windows Mobile 6.5|2|  
|Nokia Symbian|3|  
|Windows Phone|4|  
|Mac számítógép|5|  
|Windows CE|6|  
|Windows Embedded|7|  
|iOS|8|  
|iPad|9|  
|iPod Touch|10|  
|Android|11|  
|Intel egylapkás rendszer|12|  
|UNIX- és Linux-kiszolgálók|13|  

 Ha például azt szeretné, hogy a lekérdezés csak a Mac számítógépeket adja vissza, használja az alábbi lekérdezést:  

```  
Select SMS_R_System.ClientEdition from SMS_R_System where SMS_R_System.ClientEdition = 5  
```  

## <a name="see-also"></a>Lásd még:  
 [A System Center Configuration Managerben lekérdezések kapcsolatos tevékenységek és karbantartás](../../../core/servers/manage/operations-and-maintenance-for-queries.md)

