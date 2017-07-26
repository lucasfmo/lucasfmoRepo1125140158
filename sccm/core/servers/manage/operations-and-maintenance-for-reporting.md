---
title: "Jelentéskészítési kapcsolatos tevékenységek és karbantartás |} Microsoft Docs"
description: "Ismerje meg, a jelentések és a System Center Configuration Manager-jelentés-előfizetések kezelése részleteit."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b89bcfbf-f5b6-4fb1-bb5e-a5cc18ec0c78
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f5a58ba9ecd9b0998c2859b6d3f45e493d7ef3cb
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="operations-and-maintenance-for-reporting-in-system-center-configuration-manager"></a>A System Center Configuration Manager jelentéskészítési kapcsolatos tevékenységek és karbantartás

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután az infrastruktúra alkalmazásban végzett jelentéskészítéshez a System Center Configuration Managerben, számos műveleteket kell végrehajtania a jelentések és jelentés-előfizetések kezeléséhez.  

##  <a name="BKMK_ManageReports"></a>Configuration Manager jelentéseinek kezelése  
 A Configuration Manager több mint 400 előre megadott jelentéseket, amelyek segítenek gyűjtse rendszerezésére és felhasználók, hardver és szoftver-nyilvántartási, szoftverfrissítések, alkalmazások, a hely állapotának és más Configuration Manager operations információkat jelenít meg a szervezet kínál. Az előre megadott jelentéseket használhatja vannak, vagy módosíthatja az igényeinek megfelelő jelentést. Is létrehozhat egyéni modell\-alapuló és az SQL\--alapú jelentések az igényeknek. A következő részekben a Configuration Manager jelentéseinek kezeléséhez nyújt segítséget.  

###  <a name="BKMK_RunReport"></a>A Configuration Manager-jelentés futtatása  
 A Configuration Manager jelentések SQL Server Reporting Services kerülnek, és a jelentésben megjelenített adatok a Configuration Manager Helyadatbázis lekért. A Configuration Manager konzolon vagy a webböngészőben férhet Jelentéskezelő használatával jelentések érheti el. Megnyithatja a jelentéseket bármely olyan számítógépen, amely hozzáfér az SQL Server Reporting Services rendszert futtató számítógépre, és a jelentések megtekintéséhez szükséges jogosultságokkal kell rendelkeznie. A jelentés futtatásakor a jelentés címe, leírása és kategóriája a helyi operációs rendszer nyelvén jelennek meg.  

> [!NOTE]  
>  Egyes nem\-angol nyelvű, karakter lehet, hogy nem megfelelően jelennek meg a jelentéseket.  Ebben az esetben jelentések megtekinthetők a webes\-alapú Jelentéskezelő vagy a távoli felügyeleti konzol segítségével.  

> [!WARNING]  
>  Jelentések futtatásához rendelkeznie kell **olvasási** vonatkozó jogosultságokat a **hely** engedéllyel és az **jelentés futtatása** egyes objektumokhoz konfigurált engedéllyel.  

> [!NOTE]  
>  A Jelentéskezelő egy webes\--alapú jelentés hozzáférési és felügyeleti eszköz, amellyel HTTP-kapcsolaton keresztül egy távoli helyre egyetlen jelentéskészítő kiszolgálópéldány felügyeletére. Segítségével Jelentéskezelő olyan üzemeltetési feladatokat, például megtekinteni a jelentéseket, a jelentések tulajdonságainak módosítása és a kapcsolódó jelentés-előfizetések kezeléséhez. Ez a témakör megtekint egy jelentést, és a jelentéskezelőben Jelentéstulajdonságok módosításának lépéseit, kínált további lehetőségek, amely Jelentéskezelő ismertetését lásd: [Jelentéskezelő](http://go.microsoft.com/fwlink/p/?LinkId=224916) az SQL Server 2008 Books Online.  

 Az alábbi eljárások segítségével a Configuration Manager-jelentés futtatása.  

##### <a name="to-run-a-report-in-the-configuration-manager-console"></a>Jelentés futtatása a Configuration Manager konzolon  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **jelentéskészítési**, és kattintson a **jelentések** elemre az elérhető jelentések megjelenítéséhez.  

    > [!IMPORTANT]  
    >  Ebben a verzióban a Configuration Manager a **minden tartalom** jelentések csak csomagokat jelenítenek meg, alkalmazásokat nem.  

    > [!TIP]  
    >  Ha egyetlen jelentés sem jelenik meg, ellenőrizze, hogy a jelentéskészítési szolgáltatási pont telepítve és konfigurálva. További információkért lásd: [konfigurálása reporting](configuring-reporting.md).  

3.  Válassza ki a jelentést, amely szeretné futtatni, majd a a **Home** lap a **jelentéscsoport** területen kattintson **futtatása** a jelentés megnyitásához.  

4.  Ha a jelentéshez kötelező paraméterek tartoznak, adja meg a paramétereket, és kattintson **jelentés megtekintése**.  

#### <a name="to-run-a-report-in-a-web-browser"></a>Jelentés futtatása webböngészőben  

1.  A böngészőben, írja be a Jelentéskezelő URL-CÍMÉT, például **http:\/\/kiszolgáló1\/jelentések**. A Jelentéskezelő URL-CÍMÉT a segítségével meghatározhatja a **Jelentéskezelő URL-címe** lap a Reporting Services Configuration Manager.  

2.  A jelentéskezelőben kattintson a jelentés mappája. a Configuration Manager például **ConfigMgr\_CAS**.  

    > [!TIP]  
    >  Ha egyetlen jelentés sem jelenik meg, ellenőrizze, hogy a jelentéskészítési szolgáltatási pont telepítve és konfigurálva. További információkért lásd: [konfigurálása reporting](configuring-reporting.md).  

3.  Kattintson a jelentést, amely a futtatni kívánt jelentés kategóriájára, és kattintson a jelentés hivatkozására. A jelentés megnyílik a jelentéskezelőben.  

4.  Ha a jelentéshez kötelező paraméterek tartoznak, adja meg a paramétereket, és kattintson **jelentés megtekintése**.  

###  <a name="BKMK_ModifyReportProperties"></a>Configuration Manager-jelentés tulajdonságainak módosítása  
 A Configuration Manager konzolon, a jelentés nevét és leírását, például a jelentések tulajdonságainak megtekintése, de a tulajdonságok módosításához használja a Jelentéskezelő. Az alábbi eljárás segítségével a Configuration Manager-jelentés tulajdonságainak módosítása.  

#### <a name="to-modify-report-properties-in-report-manager"></a>A jelentéskezelőben jelentések tulajdonságainak módosítása  

1.  A böngészőben, írja be a Jelentéskezelő URL-CÍMÉT, például **http:\/\/kiszolgáló1\/jelentések**. A Jelentéskezelő URL-CÍMÉT a segítségével meghatározhatja a **Jelentéskezelő URL-címe** lap a Reporting Services Configuration Manager.  

2.  A jelentéskezelőben kattintson a jelentés mappája. a Configuration Manager például **ConfigMgr\_CAS**.  

    > [!TIP]  
    >  Ha egyetlen jelentés sem jelenik meg, győződjön meg arról, hogy a jelentéskészítési szolgáltatási pont telepítve és konfigurálva van. További információkért lásd: [Jelentéskészítés konfigurálása](configuring-reporting.md)  

3.  Kattintson a jelentés kategóriájára, amelynek a tulajdonságait módosítani szeretné, és kattintson a jelentés hivatkozására. A jelentés megnyílik a jelentéskezelőben.  

4.  Kattintson a **tulajdonságok** fülre. A jelentés nevét és leírását módosíthatja.  

5.  Ha elkészült, kattintson a **alkalmaz**. A jelentés tulajdonságait a jelentéskészítő kiszolgáló tárolja, és a Configuration Manager konzol lekéri a jelentés módosított tulajdonságait.  

###  <a name="BKMK_EditReport"></a>A Configuration Manager-jelentés szerkesztése  
 Ha egy meglévő Configuration Manager-jelentés nem kéri le a szükséges adatokat, hogy, vagy nem rendelkezik a szükséges elrendezést vagy kialakítást, szerkesztheti a jelentést a jelentéskészítőben.  

> [!NOTE]  
>  Azt is beállíthatja megnyit egy meglévő jelentést, szerkeszti azt, és kattintással nyissa **Mentés másként** az új jelentésként menti azt.  

> [!IMPORTANT]  
>  A felhasználói fióknak rendelkeznie kell **hely módosítása** engedéllyel és **jelentés módosítása** engedélyeket a módosítani kívánt jelentéshez tartozó objektumokhoz.  

> [!IMPORTANT]  
>  A Configuration Manager egy újabb verzióra történő frissítésekor az új jelentések felülírják az előre megadott jelentéseket. Ha módosít egy előre megadott jelentést, készítsen biztonsági másolatot a jelentésről előtt telepíti az új verziót, majd állítsa vissza a jelentést a Reporting Services szolgáltatásokban. Ha jelentős módosításokat végez egy előre megadott jelentésben, fontolja meg inkább egy új jelentés létrehozása. Új jelentéseket létrehozni előtt frissítési a hely nem íródnak felül.  

 A következő eljárás segítségével a Configuration Manager-jelentés tulajdonságainak szerkesztése.  

#### <a name="to-edit-report-properties"></a>A jelentés tulajdonságainak szerkesztése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **jelentéskészítési**, és kattintson a **jelentések** elemre az elérhető jelentések megjelenítéséhez.  

3.  Válassza ki a jelentést, amely a módosítandó, majd a a **Home** lap a **jelentéscsoport** területén kattintson **szerkesztése**. Adja meg a felhasználónevét és jelszavát, ha a rendszer kéri, és kattintson a **OK**. Ha a jelentéskészítő nincs telepítve a számítógépen, a telepítéshez kéri. Kattintson a **futtatása** a jelentések módosításához és készítéséhez szükséges jelentéskészítő telepítéséhez.  

4.  A jelentéskészítőben módosítsa megfelelően a jelentés beállításait, és kattintson a **mentése** elemre kattintva mentse a jelentést a jelentéskészítő kiszolgáló.  

###  <a name="BKMK_CreateModelBasedReport"></a>A modell létrehozása\--alapú jelentés  
 A modell\--alapú jelentés kiválaszthatja, interaktív módon a jelentésbe felvenni kívánt elemeket. Egyéni jelentéskészítési modellek létrehozásával kapcsolatos további információkért lásd: [egyéni jelentéskészítési modellek létrehozása a System Center Configuration Manager az SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md).  

> [!IMPORTANT]  
>  A felhasználói fióknak rendelkeznie kell **hely módosítása** hozhat létre egy új jelentés. A felhasználó csak létrehozhatja a jelentés mappákban, amelyhez a felhasználó rendelkezik-e **jelentés módosítása** engedélyek.  

 A következő eljárással hozhat létre egy modell\-Configuration Manager-jelentés alapján.  

#### <a name="to-create-a-model-based-report"></a>A modellek létrehozásához\--alapú jelentés  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **jelentéskészítési** kattintson **jelentések**.  

3.  A a **Home** lap a **létrehozása** kattintson **jelentés létrehozása** megnyitásához a **jelentés létrehozása varázsló**.  

4.  Az a **információk** lapon, a következő beállításokat:  

    -   **Típus**: Válassza ki **modell\--alapú jelentés** jelentés létrehozása a jelentéskészítőben a Reporting Services-modell használatával.  

    -   **Név**: Adja meg a jelentés nevét.  

    -   **Leírás**: Adja meg a jelentés leírását.  

    -   **Kiszolgáló**: A jelentéskészítő kiszolgálón, amelyen létrehozásakor ez a jelentés neve.  

    -   **Elérési út**: Kattintson a **Tallózás** megadhat egy mappát, ahol a jelentés tárolni szeretné.  

     Kattintson a **Tovább** gombra.  

5.  Az a **Modellválasztás** lapon, az elérhető modellek válassza ki a listában, ez a jelentés létrehozására használhatja. A jelentésmodell kiválasztásakor az **előzetes** szakasz jelenít meg az SQL Server-nézetek és entitások is elérhetővé válnak a választott jelentésmodellben.  

6.  Az **Összefoglalás** lapon tekintse át a beállításokat. Kattintson a **előző** módosíthatja a beállításokat, vagy kattintson a **következő** jelentés létrehozása a Configuration Manager alkalmazásban.  

7.  Az a **megerősítő** kattintson **Bezárás** gombra a varázslóból való kilépéshez, majd nyissa meg a jelentéskészítőt a jelentés beállításainak megadásához. Adja meg a felhasználónevét és jelszavát, ha a rendszer kéri, és kattintson a **OK**. Ha a jelentéskészítő nincs telepítve a számítógépen, a telepítéshez kéri. Kattintson a **futtatása** a jelentések módosításához és készítéséhez szükséges jelentéskészítő telepítéséhez.  

8.  A Microsoft Report Builderben létrehozhatja a jelentés elrendezését, jelölje ki az adatokat a rendelkezésre álló SQL Server-nézetekben, adja meg a jelentés paramétereit, és így tovább. Új jelentés létrehozása a Report Builder használatával kapcsolatos további információkért tekintse meg a Report Builder súgójában.  

9. Kattintson a **futtatása** gombra a jelentés futtatásához. Győződjön meg arról, hogy a jelentés a várt információkat tartalmazza. Kattintson a **tervezési** visszatérhet a tervezés nézetbe, és módosíthatja a jelentést, szükség esetén.  

10. Kattintson a **mentése** elemre kattintva mentse a jelentést a jelentéskészítő kiszolgáló. Akkor futtathatja és módosíthatja az új jelentést a **jelentések** csomópontja a **figyelés** munkaterületen.  

###  <a name="BKMK_CreateSQLBasedReport"></a>Hozzon létre egy SQL\--alapú jelentés  
 Egy SQL\--alapú jelentés segítségével visszaállíthatja az adatokat a jelentés SQL-utasítás alapján.  

> [!IMPORTANT]  
>  Amikor létrehoz egy egyéni jelentés SQL-utasítást, ne hivatkozzon közvetlenül az SQL Server-táblákra. Ehelyett hivatkozzon a jelentéskészítési SQL Server-nézetek \(megjelenítése v kezdődő neveket\_ \) a helyadatbázisból. Akkor nyilvános tárolt eljárásokra is hivatkozhat \(tárolt eljárás neve az sp\_ \) a helyadatbázisból.  

> [!IMPORTANT]  
>  A felhasználói fióknak rendelkeznie kell **hely módosítása** hozhat létre egy új jelentés. A felhasználó csak létrehozhatja a jelentés mappákban, amelyhez a felhasználó rendelkezik-e **jelentés módosítása** engedélyek.  

 A következő eljárással hozhat létre egy SQL\-Configuration Manager-jelentés alapján.  

#### <a name="to-create-a-sql-based-report"></a>Egy SQL létrehozásához\--alapú jelentés  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  A **Figyelés** munkaterületen bontsa ki a **Jelentéskészítés**csomópontot, majd kattintson a **Jelentések**elemre.  

3.  A a **Home** lap a **létrehozása** kattintson **jelentés létrehozása** megnyitásához a **jelentés létrehozása varázsló**.  

4.  Az a **információk** lapon, a következő beállításokat:  

    -   **Típus**: Válassza ki **SQL\--alapú jelentés** jelentés létrehozása a jelentéskészítő SQL-utasítás használatával.  

    -   **Név**: Adja meg a jelentés nevét.  

    -   **Leírás**: Adja meg a jelentés leírását.  

    -   **Kiszolgáló**: A jelentéskészítő kiszolgálón, amelyen létrehozásakor ez a jelentés neve.  

    -   **Elérési út**: Kattintson a **Tallózás** megadhat egy mappát, ahol a jelentés tárolni szeretné.  

     Kattintson a **Tovább** gombra.  

5.  Az **Összefoglalás** lapon tekintse át a beállításokat. Kattintson a **előző** módosíthatja a beállításokat, vagy kattintson a **következő** jelentés létrehozása a Configuration Manager alkalmazásban.  

6.  Az a **megerősítő** kattintson **Bezárás** a varázslóból való kilépéshez, és nyissa meg a jelentéskészítőt a jelentés beállításainak megadásához. Adja meg a felhasználónevét és jelszavát, ha a rendszer kéri, és kattintson a **OK**. Ha a jelentéskészítő nincs telepítve a számítógépen, a telepítéshez kéri. Kattintson a **futtatása** a jelentések módosításához és készítéséhez szükséges jelentéskészítő telepítéséhez.  

7.  A Microsoft Report Builderben adja meg a jelentés SQL-utasítás vagy az SQL-utasítás létrehozása az elérhető SQL Server-nézetekben oszlopok használatával, adja meg a jelentés paramétereit, és így tovább.  

8.  Kattintson a **futtatása** gombra a jelentés futtatásához. Győződjön meg arról, hogy a jelentés a várt információkat tartalmazza. Kattintson a **tervezési** visszatérhet a tervezés nézetbe, és módosíthatja a jelentést, szükség esetén.  

9. Kattintson a **mentése** elemre kattintva mentse a jelentést a jelentéskészítő kiszolgáló. Az új jelentést futtathat a **jelentések** csomópontja a **figyelés** munkaterületen.  

##  <a name="BKMK_ManageReportSubscriptions"></a>Jelentés-előfizetések kezelése  
 Az SQL Server Reporting Services jelentés-előfizetések segítségével úgy konfigurálhatja a megadott jelentések automatikus elküldését e-mailben vagy fájlmegosztásba rendszeres időközönként. Használja a **-előfizetés létrehozása varázsló** a System Center 2012 Configuration Manager használatával konfigurálhatja a jelentés-előfizetéseket.  

###  <a name="BKMK_ReportSubscriptionFileShare"></a>A jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő küldéséhez a fájlmegosztáshoz  
 A jelentés-előfizetés jelentést küld egy fájlmegosztás létrehozásakor a rendszer átmásolja a megadott formátumban a fájlmegosztáshoz megadott. Előfizetés, és egyszerre csak egy jelentés kézbesítési kérése.  

 Üzemeltetett és a jelentéskészítő kiszolgáló által kezelt jelentésekkel ellentétben a megosztott mappába küldött jelentések statikus fájlok. A jelentés a meghatározott interaktív funkcióit nem működnek a fájlrendszerben fájlként tárolt jelentésekben a. Az interaktív funkciókat statikus elemek helyettesítik. Ha a jelentés diagramokat tartalmaz, az alapértelmezett megjelenítése szerepel. Ha a jelentés másik jelentésre mutató hivatkozást tartalmaz, a hivatkozás statikus szövegként jelenik meg. Ha meg szeretné őrizni a kézbesített jelentésekben interaktív funkcióit, használja az e-mailek kézbesítését. E-mailek kézbesítésével kapcsolatos további információkért tekintse meg a [jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő e-mailben](#BKMK_ReportSubscriptionEmail) későbbi szakaszában talál.  

 Amikor létrehoz egy előfizetést, amely fájlmegosztásba küldi a jelentést, célmappaként meg kell adnia egy meglevő mappába. A jelentéskészítő kiszolgáló nem mappák létrehozása a fájlrendszerben. A mappának elérhetőnek kell lennie a hálózaton keresztül. Az előfizetés a célmappa megadásakor UNC-útvonalat használ, és nem tartalmazzák a záró fordított a mappa elérési. Például egy érvényes UNC elérési utat, a célmappa értéke: \\ \\ &lt;kiszolgálónév\>\\reportfiles\\műveletek\\2011.  

 Jelentések megjeleníthetők a különböző fájlformátumok, például MHTML- vagy Excel. Mentse a jelentést meghatározott fájlformátumban, válassza ki a megfelelő formátumot, az előfizetés létrehozásakor. Például az Excel formátumának választásával menti a jelentést Microsoft Excel-fájlként. Bármelyik támogatott megjelenítési formátumot kiválaszthatja, de némelyik formátum jobban működik a fájlként való megjelenítés során.  

 A következő eljárás segítségével a jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő küldéséhez a fájlmegosztáshoz.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-to-a-file-share"></a>A jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő küldéséhez a fájlmegosztáshoz  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **jelentéskészítési** kattintson **jelentések** elemre az elérhető jelentések megjelenítéséhez. Kiválaszthatja a jelentés mappája. csak az adott mappában jelentéseket listázásához.  

3.  Jelölje ki az előfizetésbe felvenni kívánt jelentést majd a a **Home** lap a **jelentéscsoport** kattintson **előfizetés létrehozása** megnyitásához a **előfizetés létrehozása varázsló**.  

4.  Az a **előfizetés kézbesítése** lapon, a következő beállításokat:  

    -   A jelentést kézbesítette: Válassza ki **Windows fájlmegosztás** képes biztosítani a jelentés egy fájlmegosztásba mentheti.  

    -   **Fájlnév**: Adja meg a jelentés nevét. Alapértelmezés szerint a jelentésfájl nem tartalmaz egy fájlnévkiterjesztést. Válassza ki **létrehozásakor fájlkiterjesztés hozzáadása** automatikusan fájlkiterjesztés hozzáadása Ez a jelentés a megjelenítési formátumának alapján.  

    -   **Elérési út**: Adjon meg egy UNC elérési útja egy létező mappára, ahol ezt a jelentést kézbesíteni szeretné \(például \\ \\ &lt;kiszolgálónév\>\\&lt;kiszolgálómegosztás\>\\&lt;jelentésmappa\>\).  

        > [!NOTE]  
        >  Később megadott felhasználónévnek, ezen az oldalon kell van erre a kiszolgálómegosztásra eléréséhez és írási engedéllyel rendelkezni a rendeltetési mappára.  

    -   **Megjelenítési formátum**: Válassza ki a jelentésfájl részére a következő formátumok egyikét:  

        -   **XML-fájl jelentési adatokkal**: A jelentést XML formátumban menti.  

        -   **Fürt megosztott kötetei szolgáltatás \(vesszővel tagolt\)**: A jelentés mentése a vesszővel\-elválasztott\-érték formátuma.  

        -   **TIFF-fájl**: A jelentést TIFF formátumban menti.  

        -   **Acrobat \(PDF\) fájl**: A jelentést Acrobat Portable Document Format menti.  

        -   **HTML 4.0**: A jelentést olyan csak a HTML 4.0-t támogató böngészőkkel megtekinthető weblapként menti. Az Internet Explorer 5 és újabb verziói támogatják a HTML 4.0-s verzióját.  

            > [!NOTE]  
            >  Ha a jelentésben képek is vannak, a HTML 4.0 formátum azokat nem veszi be a fájlt.  

        -   **MHTML \(webarchívum\)**: A jelentést MIME HTML formátumban menti \(mhtml\), ez megtekinthető sok webböngészővel.  

        -   **RPL-megjelenítő**: A jelentés mentése a jelentés lapelrendezés \(RPL\) formátumban.  

        -   **Excel**: A jelentést Microsoft Excel munkafüzetként menti.  

        -   **Word**: A jelentést Microsoft Word dokumentumként menti.  

    -   **Felhasználónév**: Adjon meg egy Windows felhasználói fiók engedéllyel rendelkeznek a célként megadott kiszolgálómegosztásra és mappára. A felhasználói fiókhoz kell elérhetik az erre a kiszolgálómegosztásra, és rendelkezik írási engedéllyel a rendeltetési mappára.  

    -   **Jelszó**: Adja meg a Windows felhasználói fiók jelszavát. A **jelszó megerősítése**, re\-adja meg a jelszót.  

    -   Válassza ki, konfigurálhatja a viselkedését, ha a célmappa létezik azonos nevű fájl a következő lehetőségek közül:  

        -   **Meglévő fájl felülírása egy újabb verzióval**: Meghatározza, hogy ha a jelentésfájl már létezik, az új verzió felülírja.  

        -   **Meglévő fájl felülírásának mellőzése**: Meghatározza, hogy ha a jelentésfájl már létezik, nincs olyan művelet.  

        -   **Fájlnevek növelése újabb verziók hozzáadásakor**: Meghatározza, hogy ha a jelentésfájl már létezik, egy számot fűzzön hozzá az új jelentés fájlnevéhez, hogy megkülönböztesse a többi verziótól.  

    -   **Leírás**: A jelentés-előfizetés leírását adja meg.  

     Kattintson a **Tovább** gombra.  

5.  Az a **előfizetés ütemezése** lapon, válassza ki a jelentés-előfizetés a következő kézbesítési ütemezési lehetőségek egyike:  

    -   **Megosztott ütemezés használata**: A megosztott ütemezés egy olyan előzőleg definiált ütemezés, amelyet más jelentés-előfizetések kell használni. Jelölje be a jelölőnégyzetet, és válassza a megosztott ütemezés a listában, ha bármelyik lett megadva.  

    -   **Hozzon létre új ütemezést**: Konfigurálja az ütemezést, amelyiken ez a jelentés fut, hogy tartalmazza az időköz, kezdő időpontja és és a záró dátum ehhez az előfizetéshez.  

6.  Az a **előfizetés paraméterei** csoportjában adja meg a jelentés felügyelet nélküli futtatásakor használt paramétereit. Ha a jelentésnek nincsenek paraméterei, ez a lap nem jelenik meg.  

7.  Az a **összegzés** lapján tekintse át a jelentés-előfizetési beállítások. Kattintson a **előző** módosíthatja a beállításokat, vagy kattintson a **tovább** a jelentés-előfizetés létrehozása.  

8.  A varázslóból való kilépéshez a **Befejezés** lapon kattintson a **Bezárás** gombra. Győződjön meg arról, hogy a jelentés-előfizetés sikeresen létrejött-e. Megtekintheti és módosíthatja a jelentés-előfizetések a **előfizetések** csomópontjából **jelentéskészítési** a a **figyelés** munkaterületen.  

###  <a name="BKMK_ReportSubscriptionEmail"></a>A jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő e-mailben  
 Amikor létrehoz egy jelentés-előfizetés fájlmegosztásba a jelentést e-mailben, egy e-mailt küld a címzettek konfigurált, és a jelentés mellékletként. A jelentéskészítő kiszolgáló nem ellenőrzi az e-mail címeket, és kéri le a levelezési kiszolgálótól. Ismernie kell előzetesen e-mail címeket szeretne használni. Alapértelmezés szerint egy érvényes e-mail fiókhoz a szervezeten kívül vagy belül jelentések is e-mail. A következő e-mail kézbesítési lehetőségek közül választhat:  

-   Értesítés és hiperhivatkozás küldése a létrehozott jelentésre mutató.  

-   Egy beágyazott vagy a csatolt jelentést küld. A megjelenítési formátum és a böngésző határozza meg, hogy a jelentés beágyazott vagy csatlakoztatott. Ha a böngésző támogatja a HTML 4.0 és az MHTML FORMÁTUMOT, és az MHTML választja \(webarchívum\) formátum megjelenítést alkalmazni, a jelentés be lesz ágyazva az üzenet részeként. Minden egyéb megjelenítési formátum \(CSV, PDF, Word, és így tovább\) kézbesítésére mellékletekként jelentéseket. A Reporting Services nem ellenőrzi a melléklet vagy az üzenet mérete az elküldésük előtt. Ha a melléklet vagy az üzenet túllépi a levelezési kiszolgáló által engedélyezett méretet, a jelentés nem érkezik.  

> [!IMPORTANT]  
>  Konfigurálnia kell az e-mail beállításokat a Reporting Services a **E-mail** kézbesítési lehetőség csak akkor érhető el. További információ a Reporting Services e-mail beállításainak konfigurálásáról: [jelentéskiszolgáló konfigurálása e-mailben kézbesítésre](http://go.microsoft.com/fwlink/p/?LinkId=226668) az SQL Server Online könyvekben található.  

 A következő eljárással jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő e-mail használatával.  

#### <a name="to-create-a-report-subscription-to-deliver-a-report-by-email"></a>A jelentés-előfizetés létrehozása a jelentések fájlmegosztásba történő e-mailben  

-   Kattintson a Configuration Manager konzolon **figyelés**.  

-   Az a **figyelés** munkaterületet, bontsa ki a **jelentéskészítési** kattintson **jelentések** elemre az elérhető jelentések megjelenítéséhez. Kiválaszthatja a jelentés mappája. az egyetlen elemet az adott mappában jelentéseket.  

-   Jelölje ki az előfizetésbe felvenni kívánt jelentést majd a a **Home** lap a **jelentéscsoport** kattintson **előfizetés létrehozása** megnyitásához a **előfizetés létrehozása varázsló**.  

-   Az a **előfizetés kézbesítése** lapon, a következő beállításokat:  

    -   **A jelentést kézbesítette**: Válassza ki **E\-mail** képes biztosítani a jelentés egy e-mail üzenet mellékleteként.  

    -   **To**: Adjon meg egy érvényes e-mail címet, ezt a jelentést küldeni.  

        > [!NOTE]  
        >  Több e-mail címzett összes e-mail címet pontosvesszővel elválasztva adhat meg.  

    -   **Cc**: Megadhat egy e-mail címet, másolja ezt a jelentést.  

    -   **Bcc**: Szükség esetén adja meg a jelentés másolatát kapó rejtett küldjön egy e-mail címet.  

    -   **Válasz**: Adja meg a címet kell használni, ha a címzett válaszol az e-mailt.  

    -   **Tulajdonos**: Adja meg az előfizetési e-mail üzenet tárgysorát.  

    -   **Prioritás**: Válassza ki az e-mail üzenet prioritásjelölőjét. Select **Low**, **Normal**, or **High**. A prioritási beállítás segítségével a Microsoft Exchange megjelölje az e-mail üzenet fontosságát.  

    -   **Megjegyzés**: Adja meg a szöveget, fel kell venni az előfizetési e-mail üzenet törzsét.  

    -   **Leírás**: Adja meg a jelentés-előfizetés leírását.  

    -   **Hivatkozással**: Az e-mail üzenet törzsét egy, az előfizetett jelentésre mutató URL-címet tartalmazza.  

    -   **Jelentéssel**: Adja meg, hogy a jelentés csatolva van-e az e\-e-mail-üzenetet. A jelentés csatolva formátumban van megadva a **megjelenítési formátum** listája.  

    -   **Megjelenítési formátum**: A csatolt jelentés az alábbi formátumok közül választhat:  

        -   **XML-fájl jelentési adatokkal**: A jelentést XML formátumban menti.  

        -   **Fürt megosztott kötetei szolgáltatás \(vesszővel tagolt\)**: A jelentés mentése a vesszővel\-elválasztott\-érték formátuma.  

        -   **TIFF-fájl**: A jelentést TIFF formátumban menti.  

        -   **Acrobat \(PDF\) fájl**: A jelentést Acrobat Portable Document Format menti.  

        -   **MHTML \(webarchívum\)**: A jelentést MIME HTML formátumban menti \(mhtml\), ez megtekinthető sok webböngészővel.  

        -   **Excel**: A jelentést Microsoft Excel munkafüzetként menti.  

        -   **Word**: A jelentést Microsoft Word dokumentumként menti.  

-   Az a **előfizetés ütemezése** lapon, válassza ki a jelentés-előfizetés a következő kézbesítési ütemezési lehetőségek egyike:  

    -   **Megosztott ütemezés használata**: A megosztott ütemezés egy olyan előzőleg definiált ütemezés, amelyet más jelentés-előfizetések kell használni. Jelölje be a jelölőnégyzetet, és válassza a megosztott ütemezés a listában, ha bármelyik lett megadva.  

    -   **Hozzon létre új ütemezést**: Az ütemezés beállítása, amely a jelentés futását, többek között az időköz, kezdési ideje és a dátum és a záró dátum ehhez az előfizetéshez.  

-   Az a **előfizetés paraméterei** csoportjában adja meg a jelentés felügyelet nélküli futtatásakor használt paramétereit. Ha a jelentésnek nincsenek paraméterei, ez a lap nem jelenik meg.  

-   Az a **összegzés** lapján tekintse át a jelentés-előfizetési beállítások. Kattintson a **előző** módosíthatja a beállításokat, vagy kattintson a **tovább** a jelentés-előfizetés létrehozása.  

-   A varázslóból való kilépéshez a **Befejezés** lapon kattintson a **Bezárás** gombra. Győződjön meg arról, hogy a jelentés-előfizetés sikeresen létrejött-e. Megtekintheti és módosíthatja a jelentés-előfizetések a **előfizetések** csomópontjából **jelentéskészítési** a a **figyelés** munkaterületen.  

