---
title: "Jelentéskészítésének bemutatása |} Microsoft Docs"
description: "További tudnivalók az eszközök és erőforrások elérhetők a kezelése a Configuration Manager jelentéskészítési készletét."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 230be984-d2cd-4d53-bd7a-bc24dd93fc22
caps.latest.revision: 7
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 5846ca3c91626491b03b36dd17b454bb9382a8dc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-reporting-in-system-center-configuration-manager"></a>A System Center Configuration Manager jelentéskészítésének bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Jelentéskészítés a System Center Configuration Managerben biztosít eszközöket és erőforrásokat, amelyek segítséget nyújtanak az SQL Server Reporting Services (SSRS) és a gazdag jelentéskészítő környezetét, hogy a Reporting Services jelentéskészítő biztosít a fejlett jelentéskészítési funkcióinak használata. Jelentéskészítési funkciókkal gyűjtsön, rendezése és felhasználók, hardver és szoftver-nyilvántartási, szoftverfrissítések, alkalmazások, a hely állapotának és más Configuration Manager operations információkat jelenít meg a szervezetében. A jelentéskészítési szolgáltatások keretében számos előre definiált jelentés vehető igénybe, amelyek akár változatlanul is használhatók vagy az igényeknek megfelelően módosíthatók, emellett pedig egyéni jelentések is készíthetők. A következő részekben a Configuration Manager jelentéskészítésének kezelésében nyújt segítséget.  

##  <a name="BKMK_SQLServerReportingServices"></a> SQL Server Reporting Services  
 Az SQL Server Reporting Services számos azonnal használható eszközt és szolgáltatást kínál jelentések létrehozásához, elkészítéséhez és kezeléséhez a szervezet számára, továbbá programozási funkciókat is biztosít a jelentéskészítési funkciókészlet bővítéséhez és testreszabásához. A Reporting Services kiszolgálói platform átfogó jelentéskészítési funkcionalitást kínál számos különböző adatforrás alapján.  

 A Configuration Manager SQL Server Reporting Services használja jelentéskészítési megoldásként. A Reporting Services-integráció az alábbi előnyöket nyújtja:  

-   Az iparági szabványos jelentéskészítő rendszer használatával a Configuration Manager adatbázisából.  

-   Jelentések megtekintése a Configuration Manager jelentésmegjelenítő vagy a jelentéshez webes kapcsolatot Jelentéskezelő használatával.  

-   Kiváló teljesítmény, rendelkezésre állás és méretezhetőség  

-   A felhasználók előfizethetnek a jelentésekre; például a vezetők napi automatikus e-mail jelentést kérhetnek a szoftverfrissítések telepítésének állapotáról  

-   Jelentések exportálása számos elterjedt formátumban  

 A Reporting Services platformról további információt az [SQL Server Reporting Services](http://go.microsoft.com/fwlink/p/?LinkID=212032) oldalon olvashat az SQL Server 2008 online dokumentációjában.  

##  <a name="BKMK_ReportingServicesPoint"></a> Jelentéskészítési szolgáltatási pont  
 A jelentéskészítési szolgáltatási pont egy Microsoft SQL Server Reporting Services környezetet futtató kiszolgálóra telepített helyrendszerszerepkör. A jelentéskészítési szolgáltatási pont másolja a Configuration Manager jelentést a Reporting Services definíciók hoz létre a jelentéskategóriák alapján jelentésmappák, és biztonsági házirendeket alkalmaz a jelentésmappákra és a jelentéseket a Configuration Manager rendszergazda felhasználók szerepköralapú engedélyeinek alapján. A jelentéskészítési szolgáltatási pont 10 percenként kapcsolódik a Reporting Serviceshez, és újraalkalmazza a biztonsági házirendet, amennyiben azt például a Jelentéskezelővel módosították. A jelentéskészítési szolgáltatási pont megtervezéséről és telepítéséről az alábbi dokumentációk nyújtanak további tájékoztatást:  

-   [A System Center Configuration Managerben a jelentéskészítés tervezése](planning-for-reporting.md)  

-   [A System Center Configuration Managerben a jelentéskészítés konfigurálása](configuring-reporting.md)  

##  <a name="BKMK_ConfigurationManagerReports"></a> A Configuration Manager jelentései  
 A Configuration Manager jelentéshez biztosít jelentésdefiníciókat több mint 400 jelentések több mint 50 jelentésmappában, amelyeket kerülnek a jelentés-gyökérmappájába az SQL Server Reporting Services a jelentéskészítési szolgáltatási pont telepítési folyamata során. A jelentések jelennek meg a Configuration Manager konzolon, és almappák jelentéskategória alapján vannak rendezve. Jelentéseket a rendszer nem propagálja felfelé vagy lefelé a Configuration Manager-hierarchiában; Futtatás csak a hely, amelyben létre adatbázison. Mert a Configuration Manager replikálja a globális adatokat a hierarchiában, lehetősége van azonban hierarchiára kiterjedő információkat nyújtanak. Ha egy jelentés adatokat kér le a helyadatbázisból, akkor az aktuális hely és a gyermekhelyek mellett a hierarchia összes helyének globális adataihoz is hozzáférést nyer. Más Configuration Manager-objektumok, például egy rendszergazda felhasználó a jelentések futtatásához vagy módosításához megfelelő engedélyekkel kell rendelkeznie. Jelentés futtatásához a rendszergazdának **Jelentés futtatása** engedéllyel kell rendelkeznie az adott objektumhoz. Jelentés módosításához a rendszergazdának **Jelentés módosítása** engedéllyel kell rendelkeznie az adott objektumhoz.  

###  <a name="BKMK_CreatingReports"></a> Jelentések készítése és módosítása  
 Configuration Manager használ a Microsoft SQL Server jelentéskészítőt használja az egyedüli jelentéskészítő és -szerkesztő eszközként mind a modellalapú és SQL-alapú jelentésekhez. Hozzon létre vagy a Configuration Manager konzolon jelentés módosítása, a jelentéskészítő nyílik meg. További információk jelentések kezeléséről: [Jelentésekkel kapcsolatos tevékenységek és karbantartás a System Center Configuration Managerben](operations-and-maintenance-for-reporting.md).  

###  <a name="BKMK_RunningReports"></a> Jelentések futtatása  
 A Configuration Manager konzol futtatásakor a jelentés a Report Viewer megnyílik, és csatlakozik a Reporting Services. A szükséges jelentésparaméterek megadása után a Reporting Services lekéri a szükséges adatokat, és az eredmények megtekinthetők a megjelenítőben. Emellett közvetlenül is csatlakozhat az SQL Server Reporting Serviceshez, majd a hely adatforrásához kapcsolódva futtathatja a kívánt jelentéseket.  

###  <a name="BKMK_ReportPrompts"></a> Jelentésparaméterek  
 A jelentés vagy a Configuration Manager egy jelentés tulajdonságot, amelynek konfigurálhatja, ha egy jelentés létrehozásakor vagy módosításakor. A jelentésparaméterekkel korlátozható vagy célzottan meghatározható a jelentés által lekért adatok köre. Egy jelentés több paramétert is tartalmazhat, a paraméterneveknek azonban egyedinek kell lenniük, és csak alfanumerikus karaktereket tartalmazhatnak, amelyek megfelelnek az SQL Server azonosítókra vonatkozó szabályainak.  

 Amikor futtat egy jelentést, a jelentéskérdés lekér egy értéket a kötelező paraméterhez, és az érték alapján lekéri a jelentés adatait. Az **Egyedi számítógép információi** jelentés például egy meghatározott számítógép adatainak lekérésére használható, és kéri a rendszergazdától a számítógép nevének megadását. A Reporting Services a megadott értéket átadja a jelentés SQL-utasításában definiált változónak.  

###  <a name="BKMK_ReportLinks"></a> Jelentéshivatkozások  
 Jelentési hivatkozásait. a Configuration Managerben a forrásjelentés egyszerűen hozzáférhetnek további adatokhoz, például részletesebb információkhoz a forrásjelentés egyes elemeiről a forrás rendszergazda felhasználóinak arra használnak. Ha a céljelentés futtatásához egy vagy több paraméter szükséges, a forrásjelentésnek tartalmaznia kell egy oszlopot az egyes paraméterek megfelelő értékeivel. Meg kell adnia annak az oszlopnak a számát, amely ellátja a paramétert a megfelelő értékkel. Például a közelmúltban felderített számítógépek listáját tartalmazó jelentés összekapcsolható egy olyan jelentéssel, amely az egyik számítógéphez érkezett legutóbbi üzeneteket tartalmazza. Ha a kapcsolat létrejött, meghatározhatja, hogy a forrásjelentés 2. oszlopa tartalmazza a számítógépneveket, amely a céljelentés kötelező paramétere. A forrásjelentés futtatásakor az egyes adatsorok bal oldalán hivatkozási ikonok jelennek meg. Ha valamelyik sor ikonjára kattint, a Jelentésmegjelenítő a sorhoz meghatározott oszlopban szereplő értéket átadja a céljelentés megjelenítéséhez szükséges paraméterértékként. A jelentések egyetlen hivatkozással is konfigurálhatók, amely akár mindössze egy célforráshoz is csatlakozhat.  

> [!WARNING]  
>  Ha egy céljelentést másik jelentésmappába helyez át, a céljelentés helye megváltozik. A rendszer nem frissíti automatikusan az új hellyel a forrásjelentésben lévő jelentéshivatkozást, ezért ez a hivatkozás nem fog működni.  

##  <a name="BKMK_ReportFolders"></a> Jelentésmappák  
 A System Center Configuration Managerben jelentésmappák jelentésmappái a Reporting Servicesben tárolt jelentések rendezésére és szűrésére. A jelentésmappák különösen hasznosak akkor, ha sok jelentés kezelésére van szükség. Amikor jelentéskészítési szolgáltatási pontot telepít, a rendszer a Reporting Servicesbe másolja és több mint 50 mappába rendezi a jelentéseket. A jelentésmappák csak olvashatók, Nem módosíthatók a Configuration Manager konzolon.  

##  <a name="BKMK_ReportSubscriptions"></a> Jelentés-előfizetések  
 A Reporting Services jelentés-előfizetései rendszeresen ismétlődő kérelmek egy adott jelentés kézbesítésére meghatározott időben vagy adott esemény bekövetkezésekor, az előfizetésben megadott alkalmazás-fájlformátumban. Az előfizetések a jelentések igény szerinti futtatása helyett használhatók. Az igény szerinti jelentéskészítéshez ténylegesen ki kell jelölnie a jelentést minden egyes alkalommal, amikor szeretné azt megjeleníteni. Ezzel szemben az előfizetésekkel ütemezhető és automatizálható a jelentések kézbesítése.  

 Jelentés-előfizetések a Configuration Manager konzolon kezelheti. Feldolgozásuk a jelentéskészítő kiszolgálón történik. A rendszer a kiszolgálón telepített kézbesítési kiterjesztésekkel terjeszti az előfizetéseket. Alapértelmezés szerint olyan előfizetéseket készíthet, amelyek megosztott mappába vagy e-mail címre küldenek jelentéseket. További információk jelentés-előfizetések kezeléséről: [Jelentésekkel kapcsolatos tevékenységek és karbantartás a System Center Configuration Managerben](operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_ReportBuilder"></a> Jelentéskészítő  
 Configuration Manager használ a Microsoft SQL Server Reporting Services jelentéskészítőt használja az egyedüli jelentéskészítő és -szerkesztő eszközként mind a modellalapú, mind az SQL-alapú jelentésekhez. Amikor lehet létrehozni vagy módosítani a jelentés a Configuration Manager konzol kezdeményezi, a jelentéskészítő nyílik meg. A Jelentéskészítő automatikusan települ, amikor először készít vagy módosít egy jelentést. A jelentések futtatásakor vagy szerkesztésekor a telepített SQL Server-verzióhoz kapcsolódó Jelentéskészítő indul el.  

 A Jelentéskészítő több mint 20 nyelvet támogat. A Jelentéskészítő futtatásakor az eszköz a helyi számítógépen futó operációs rendszer nyelvén jeleníti meg az adatokat. Ha a Jelentéskészítő nem támogatja az operációs rendszer nyelvét, az adatok angolul jelennek meg. A Jelentéskészítő az SQL Server 2008 Reporting Services teljes funkcionalitásának támogatása révén az alábbi előnyöket kínálja:  

-   A Microsoft Office felületéhez hasonló, intuitív jelentéskészítési környezetet.  

-   Az SQL Server 2008 jelentésdefiníciós nyelv (RDL) rugalmas jelentéselrendezését.  

-   Különböző adatmegjelenítési módszereket, például diagramokat és kijelzőket.  

-   Igényes formázású szövegmezőket.  

-   Exportálási lehetőséget Microsoft Word-formátumba.  

 A Jelentéskészítő az SQL Server Reporting Servicesből is megnyitható.  

##  <a name="BKMK_ReportModels"></a> Jelentésmodellek az SQL Server Reporting Services szolgáltatásban  
 Az SQL Reporting Services Configuration Manager jelentésmodellek használatával jelentésmodelljeivel a rendszergazdák válassza ki az elemeket szeretnék szerepeltetni a modellalapú jelentésekben az adatbázisból. A jelentést készítő rendszergazda csak meghatározott nézeteket és elemeket választhat a jelentésmodellekből. Modellalapú jelentések készítéséhez legalább egy jelentésmodellnek elérhetőnek kell lennie. A jelentésmodellek az alábbi funkciókkal rendelkeznek:  

-   A könnyebb jelentéskészítés érdekében az üzleti felhasználásnak megfelelő neveket adhat az adatbázismezőknek és -nézeteknek. A jelentések előállításához nem szükséges az adatbázis-szerkezet ismerete.  

-   Az elemek logikai csoportokba rendezhetők.  

-   Az elemek között kapcsolatok definiálhatók.  

-   A modell elemeire biztonsági korlátozást alkalmazhat, így a rendszergazdák csak azokat az adatokat láthatják, amelyekhez engedélyük van.  

 Bár a Configuration Manager jelentésmodell-mintákat, megadhatja a saját üzleti követelményeinek megfelelően jelentésmodellek. További információk jelentésmodellek létrehozásáról: [Jelentésmodellek létrehozása a System Center Configuration Managerhez az SQL Server Reporting Services szolgáltatásban](creating-custom-report-models-in-sql-server-reporting-services.md).  

## <a name="next-steps"></a>További lépések
[A jelentéskészítés tervezése](planning-for-reporting.md)

