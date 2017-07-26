---
title: "Egyéni jelentések készítése |} Microsoft Docs"
description: "Adja meg a jelentésmodellek az üzleti követelményeknek, és telepíteni a jelentésmodellek a Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f2df88b4-c348-4dcf-854a-54fd6eedf485
caps.latest.revision: 5
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 9951dd9333ebef00c7acd5d72b20a02382e3206c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="creating-custom-report-models-for-system-center-configuration-manager-in-sql-server-reporting-services"></a>A System Center Configuration Manager az SQL Server Reporting Services egyéni jelentéskészítési modellek létrehozása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Jelentésmodell-mintákat megtalálhatók a System Center Configuration Managerben, de a saját üzleti követelményeinek megfelelően jelentésmodelleket is definiálhat, és a megfelelő jelentésmodellt telepítheti a Configuration Manager felhasználhatja a modellen alapuló új jelentések elkészítéséhez. A következő táblázat tartalmazza az alapszintű jelentésmodellek létrehozásának és központi telepítésének lépéseit.  

> [!NOTE]  
>  További információ az összetettebb jelentésmodellek létrehozásáról: [Steps for Creating an Advanced Report Model in SQL Server Reporting Services](#AdvancedReportModel) című rész a jelen témakörben.  

|Lépés|Leírás|További információ|  
|----------|-----------------|----------------------|  
|Ellenőrizze, hogy telepítve van-e az SQL Server Business Intelligence Development Studio.|A jelentésmodellek az SQL Server Business Intelligence Development Studio használatával tervezhetők meg és hozhatók létre. Ellenőrizze, hogy az SQL Server Business Intelligence Development Studio telepítve van-e azon a számítógépen, amelyen létre kívánja hozni az egyéni jelentésmodellt.|Az SQL Server Business Intelligence Development Studio használatáról az SQL Server 2008 dokumentációjában olvashat bővebben.|  
|Hozzon létre egy jelentésmodell-projektet.|A jelentésmodell-projekt tartalmazza az adatforrás definícióját (.ds-fájl), az adatforrásnézet definícióját (.dsv-fájl), valamint a jelentésmodellt (.smdl-fájl).|További tudnivalókat a jelen témakör [To create the report model project](#BKMK_CreateReportModelProject) című szakaszában találhat.|  
|Definiálja a jelentésmodell adatforrását.|A jelentésmodell-projekt létrehozása után definiálnia kell egy adatforrást, amelyből beolvashatja az üzleti adatokat. Ez általában a Configuration Manager-hely adatbázisába.|További tudnivalókat a jelen témakör [To define the data source for the report model](#BKMK_DefineReportModelDataSource) című szakaszában találhat.|  
|Definiálja a jelentésmodell adatforrásnézetét.|A jelentésmodell-projektben használandó adatforrások definiálása után a következő lépés a projekt adatforrásnézetének definiálása. Az adatforrásnézet egy logikai adatmodell, amely egy vagy több adatforráson alapul. Az adatforrásnézetek foglalják magukban az alapul szolgáló adatforrások által tartalmazott fizikai objektumokat, például a táblákat és a nézeteket. Az SQL Server Reporting Services állítja elő a jelentésmodellt az adatforrásnézetből.<br /><br /> Az adatforrásnézetek megkönnyítik a modelltervezési folyamatot azzal, hogy szemléletes módon jelenítik meg a megadott adatokat. Az adatforrásnézetben az alapul szolgáló adatforrás megváltoztatása nélkül nevezheti át a táblákat és a mezőket, és veheti fel az összesítő mezőket és a származtatott táblákat. A modell hatékonysága érdekében csak azokat a táblákat vegye fel az adatforrásnézetbe, amelyeket használni fog.|További tudnivalókat a jelen témakör [To define the data source view for the report model](#BKMK_DefineReportModelDataSourceView) című szakaszában találhat.|  
|Hozzon létre egy jelentésmodellt.|A jelentésmodell az adatbázisnak az a felső szintű rétege, amely az üzleti entitásokat, a mezőket és a szerepköröket azonosítja. A Jelentéskészítő felhasználói a közzétett modellek segítségével készíthetnek jelentéseket úgy, hogy nem kell mélyrehatóan ismerniük az adatbázis felépítését, és nem kell lekérdezéseket létrehozniuk. A modelleket kapcsolódó jelentéselemek készletei alkotják, amelyekhez könnyen megjegyezhető név tartozik. Ezekben a készletekben előre megadott kapcsolatokkal szerepelnek az üzletei elemek, és előre megadott számításokat is tartalmaznak. A modellek az SDML (Semantic Model Definition Language) nevű XML-nyelven definiálhatók. A jelentésmodellfájlok fájlnévkiterjesztése .smdl.|További tudnivalókat a jelen témakör [To create the report model](#BKMK_CreateReportModel) című szakaszában találhat.|  
|Tegye közzé a jelentésmodellt.|A létrehozott modellt közzé kell tennie egy jelentéskészítő kiszolgálón, hogy felhasználhassa a jelentések létrehozásához. A közzétett modell tartalmazni fogja az adatforrást és az adatforrásnézetet.|További tudnivalókat a jelen témakör [To publish the report model for use in SQL Server Reporting Services](#BKMK_PublishReportModel) című szakaszában találhat.|  
|A jelentésmodell telepítése a Configuration Manager|Az egyéni jelentésmodell használata előtt a **jelentés létrehozása varázsló** modellalapú jelentés létrehozása, ha már telepítette a jelentésmodellt a Configuration Manager.|További tudnivalókat a jelen témakör [To deploy the custom report model to Configuration Manager](#BKMK_DeployReportModel) című szakaszában találhat.|  

## <a name="steps-for-creating-a-basic-report-model-in-sql-server-reporting-services"></a>Az alapszintű jelentésmodellek létrehozásának lépései az SQL Server Reporting Services szoftverben  
 A következő eljárásokkal hozhat létre olyan alapszintű jelentésmodellt, amely a hely felhasználói használhatja a Configuration Manager adatbázisának valamelyik nézetében lévő adatok alapján adott modellalapú jelentések készítéséhez. Ekkor olyan jelentésmodellt hoz létre, amely a helyen található ügyfélszámítógépek adatait jeleníti meg a jelentés készítője számára. Ez az adatokat a **v_R_System** megtekintése a Configuration Manager adatbázisába.  

 Ellenőrizze, hogy a műveletek végrehajtásához használandó számítógépen telepítve van-e az SQL Server Business Intelligence Development Studio, és hogy a számítógép tud-e hálózati kapcsolatot létesíteni a jelentéskészítési szolgáltatási pont kiszolgálójával. Az SQL Server Business Intelligence Development Studio használatáról az SQL Server 2008 dokumentációjában olvashat bővebben.  

###  <a name="BKMK_CreateReportModelProject"></a> To create the report model project  

1.  Kattintson a **Start**gombra, és válassza a **Microsoft SQL Server 2008**, majd az **SQL Server Business Intelligence Development Studio**parancsot.  

2.  Miután az **SQL Server Business Intelligence Development Studio** megnyílt a Microsoft Visual Studio alkalmazásban, válassza a **Fájl**menü **Új**, majd **Projekt**parancsát.  

3.  Az **Új projekt** párbeszédpanelen válassza a **Sablonok** lista **Jelentésmodell-projekt** elemét.  

4.  A **Név** mezőbe írja be a jelentésmodell nevét. Ehhez a példához írja be a következőt: **Simple_Model**.  

5.  A jelentésmodell-projekt létrehozásához kattintson az **OK**gombra.  

6.  A **Simple_Model** megoldás megjelenik a **Megoldáskezelő**ablaktáblában.  

    > [!NOTE]  
    >  Ha nem látható a **Megoldáskezelő** ablaktábla, válassza a **Nézet**menü **Megoldáskezelő**parancsát.  

###  <a name="BKMK_DefineReportModelDataSource"></a> To define the data source for the report model  

1.  Az **SQL Server Business Intelligence Development Studio** **Megoldáskezelő**ablaktáblájában az egér jobb gombjával kattintson az **Adatforrások** elemre, és válassza az **Új adatforrás hozzáadása**lehetőséget.  

2.  Az **Üdvözli az Adatforrás varázsló** lapon kattintson a **Tovább**gombra.  

3.  A **Válassza ki a kapcsolat definiálásának módját** lapon válassza az **Adatforrás létrehozása meglévő vagy új kapcsolat alapján** lehetőséget, és kattintson az **Új**gombra.  

4.  A **Csatlakozáskezelő** párbeszédpanelen adja meg a következő csatlakozási tulajdonságokat az adatforráshoz:  

    -   **Kiszolgálónév**: Írja be a Configuration Manager Helyadatbázis-kiszolgáló nevét, vagy válassza ki a listából. Ha az alapértelmezett példány helyett egy nevesített példányt dolgozik, írja be a &lt; *adatbázis-kiszolgáló*>\\&lt;*példánynév*>.  

    -   Válassza a **Windows-hitelesítés használata**beállítást.  

    -   A **válasszon vagy adjon meg egy adatbázisnevet** listára, válassza ki a Configuration Manager helyadatbázisának nevét.  

5.  Az adatbázis-kapcsolat kipróbálásához kattintson a **Kapcsolat tesztelése**gombra.  

6.  Ha a csatlakozás sikeres, az **OK** gombra kattintva zárja be a **Csatlakozáskezelő** párbeszédpanelt. Ha nem sikerül a csatlakozás, ellenőrizze a megadott adatok helyességét, majd kattintson újból a **Kapcsolat tesztelése** gombra.  

7.  A **Válassza ki a kapcsolat definiálásának módját** lapon ellenőrizze, hogy meg van-e adva az **Adatforrás létrehozása meglévő vagy új kapcsolat alapján** beállítás. Ellenőrizze, hogy az imént megadott adatforrás ki van-e választva az **Adatkapcsolatok**listán, és kattintson a **Tovább**gombra.  

8.  Az **Adatforrás neve**mezőben adja meg az adatforrás nevét, és kattintson a **Befejezés**gombra. Ehhez a példához írja be a következőt: **Simple_Model**.  

9. A **Simple_Model.ds** adatforrás megjelenik a **Megoldáskezelő** ablaktábla **Adatforrások** csomópontjában.  

    > [!NOTE]  
    >  Meglévő adatforrás tulajdonságainak szerkesztéséhez kattintson duplán az adatforrásra a **Megoldáskezelő** ablaktábla **Adatforrások** mappájában, ezzel megjeleníti az adatforrás tulajdonságait az Adatforrás-tervezőben.  

###  <a name="BKMK_DefineReportModelDataSourceView"></a> To define the data source view for the report model  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson az **Adatforrásnézetek** elemre, és válassza az **Új adatforrásnézet hozzáadása**lehetőséget.  

2.  Az **Üdvözli az Adatforrásnézet varázsló** lapon kattintson a **Tovább**gombra. Megjelenik az **Adatforrás kiválasztása** lap.  

3.  A **Relációs adatforrások** ablakban ellenőrizze, hogy a **Simple_Model** adatforrás van-e kiválasztva, és kattintson a **Tovább**gombra.  

4.  A **Táblák és nézetek kijelölése** lapon lévő **Rendelkezésre álló objektumok** listájában válassza ki a következő nézetet a jelentésmodellhez: **v_R_System (dbo)**.  

    > [!TIP]  
    >  A **Rendelkezésre álló objektumok** lista áttekintésének megkönnyítéséhez kattintson a **Név** fejlécre a lista tetején, ezzel betűrendben jelenítheti meg az objektumokat.  

5.  A nézet kijelölése után a **>** gombra kattintva helyezze át az objektumot a **Befoglalt objektumok** elemét.  

6.  Ha megjelenik a **Névegyeztetés** lap, fogadja el az itt szereplő beállításokat, és kattintson a **Tovább**gombra.  

7.  Miután kiválasztotta a szükséges objektumokat, kattintson a **Tovább**gombra, és adja meg az adatforrásnézet nevét. Ehhez a példához írja be a következőt: **Simple_Model**.  

8.  Kattintson a **Befejezés**gombra. A **Simple_Model.dsv** adatforrásnézet megjelenik a **Megoldáskezelő** ablaktábla **Adatforrásnézetek**mappájában.  

###  <a name="BKMK_CreateReportModel"></a> To create the report model  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson a **Jelentésmodellek** elemre, és válassza az **Új jelentésmodell hozzáadása**lehetőséget.  

2.  Az **Üdvözli a Jelentésmodell varázsló** lapon kattintson a **Tovább**gombra.  

3.  Az **Adatforrásnézetek kiválasztása** lapon jelölje ki az adatforrásnézetet a **Rendelkezésre álló adatforrásnézetek** listában, és kattintson a **Tovább**gombra. Ehhez a példához válassza ki a következőt: **Simple_Model.dsv**.  

4.  A **Jelentésmodell létrehozási szabályainak kiválasztása** lapon fogadja el az alapértékeket, és kattintson a **Tovább**gombra.  

5.  A **Modell statisztikai adatainak összegyűjtése** lapon ellenőrizze, hogy ki van-e választva a **Modell statisztikai adatainak frissítése a létrehozása előtt** beállítás, és kattintson a **Tovább**gombra.  

6.  **A varázsló befejezése** lapon adja meg a jelentésmodell nevét. Ebben a példában a **Simple_Model** névnek kell megjelennie.  

7.  A varázsló befejezéséhez és a jelentésmodell létrehozásához kattintson a **Futtatás**gombra.  

8.  A varázslóból való kilépéshez kattintson a **Befejezés**gombra. A jelentésmodell megjelenik a Tervezés ablakban.  

###  <a name="BKMK_PublishReportModel"></a> To publish the report model for use in SQL Server Reporting Services  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson a jelentésmodellre, és válassza a **Telepítés**parancsot. Ebben a példában a jelentésmodellt a **Simple_Model.smdl**fájl tartalmazza.  

2.  Figyelje a telepítés állapotát az **SQL Server Business Intelligence Development Studio** ablak bal alsó sarkában. A telepítés befejezését a **Telepítés sikeres** felirat megjelenése jelzi. Ha nem sikerül a telepítés, a hiba oka megjelenik a **Kimenet** ablakban. Az új jelentés ekkor elérhető az SQL Server Reporting Services webhelyén.  

3.  Válassza a **Fájl**menü **Összes mentése**parancsát, majd zárja be az **SQL Server Business Intelligence Development Studio**ablakot.  

###  <a name="BKMK_DeployReportModel"></a> To deploy the custom report model to Configuration Manager  

1.  Keresse meg azt a mappát, amely a létrehozott jelentésmodell-projektet tartalmazza. Például %*USERPROFILE*%\Documents\Visual Studio 2008\Projects\\*&lt;projektnevet\>.*  

2.  Másolja át a következő fájlokat a jelentésmodell-projekt mappájából egy ideiglenes mappába a számítógépen:  

    -   *&lt;A modell neve\>*  **.dsv**  

    -   *&lt;A modell neve\>*  **.smdl**  

3.  Nyissa meg ezeket a fájlokat egyszerű szövegszerkesztőben, például a Jegyzettömbben.  

4.  A fájl  *&lt;modellnév\>***.dsv**, keresse meg az első sort, amelyben a következő fájl:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine"\>**  

     Módosítsa ezt a sort a következőre:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine" xmlns:xsi = "RelationalDataSourceView"\>**  

5.  Másolja a Windows vágólapra a fájl teljes tartalmát.  

6.  Zárja be a fájlt  *&lt;modellnév\>***.dsv**.  

7.  A fájl  *&lt;modellnév\>***.smdl**, keresse meg az utolsó három sort a fájl, amely a következőképpen jelenik meg:  

     `</Entity>`  

     `</Entities>`  

     `</SemanticModel>`  

8.  Illessze be a fájl tartalmát  *&lt;modellnév\>***.dsv** közvetlenül a fájl utolsó sora elé (**&lt;SemanticModel\>**).  

9. Mentse és zárja be a fájl  *&lt;modellnév\>***.smdl**.  

10. A fájl másolása  *&lt;modellnév\>***.smdl** mappához *% programfiles %*\Microsoft Configuration Manager \AdminConsole\XmlStorage\Other a Configuration Manager helykiszolgálón.  

    > [!IMPORTANT]  
    >  Miután átmásolta a jelentésmodell fájlját a Configuration Manager-kiszolgálóra, ki kell lépnie és a Configuration Manager konzol újraindítása után is használhatja a jelentésmodellt a **jelentés létrehozása varázsló**.  

##  <a name="AdvancedReportModel"></a> Steps for Creating an Advanced Report Model in SQL Server Reporting Services  
 A következő eljárásokkal hozhat létre olyan összetett jelentésmodellt, amely a hely felhasználói használhatja a Configuration Manager adatbázisának több nézetében lévő adatok alapján adott modellalapú jelentések készítéséhez. Ekkor olyan jelentésmodellt hoz létre, amely az ügyfélszámítógépek és az ügyfélszámítógépekre telepített operációs rendszerek adatait jeleníti meg a jelentés készítője számára. Ez az információ a Configuration Manager adatbázisa a következő nézeteiből lehet lekérni:  

-   **V_R_System**: Felderített számítógépeket és a Configuration Manager-ügyfél adatait tartalmazza.  

-   **V_GS_OPERATING_SYSTEM**: Az ügyfélszámítógépen telepített operációs rendszer adatait tartalmazza.  

 Az előző nézetek kijelölt elemei együtt egy listába kerülnek, barátságos nevet kapnak, majd a jelentés készítője számára megjelennek a Jelentéskészítőben, így szerepeltetheti azokat saját jelentéseiben.  

 Ellenőrizze, hogy a műveletek végrehajtásához használandó számítógépen telepítve van-e az SQL Server Business Intelligence Development Studio, és hogy a számítógép tud-e hálózati kapcsolatot létesíteni a jelentéskészítési szolgáltatási pont kiszolgálójával. Az SQL Server Business Intelligence Development Studio használatáról az SQL Server dokumentációjában olvashat bővebben.  

#### <a name="to-create-the-report-model-project"></a>To create the report model project  

1.  Kattintson a **Start**gombra, és válassza a **Microsoft SQL Server 2008**, majd az **SQL Server Business Intelligence Development Studio**parancsot.  

2.  Miután az **SQL Server Business Intelligence Development Studio** megnyílt a Microsoft Visual Studio alkalmazásban, válassza a **Fájl**menü **Új**, majd **Projekt**parancsát.  

3.  Az **Új projekt** párbeszédpanelen válassza a **Sablonok** lista **Jelentésmodell-projekt** elemét.  

4.  A **Név** mezőbe írja be a jelentésmodell nevét. Ehhez a példához írja be a következőt: **Advanced_Model**.  

5.  A jelentésmodell-projekt létrehozásához kattintson az **OK**gombra.  

6.  Az **Advanced_Model** megoldás megjelenik a **Megoldáskezelő**ablaktáblában.  

    > [!NOTE]  
    >  Ha nem látható a **Megoldáskezelő** ablaktábla, válassza a **Nézet**menü **Megoldáskezelő**parancsát.  

#### <a name="to-define-the-data-source-for-the-report-model"></a>To define the data source for the report model  

1.  Az **SQL Server Business Intelligence Development Studio** **Megoldáskezelő**ablaktáblájában az egér jobb gombjával kattintson az **Adatforrások** elemre, és válassza az **Új adatforrás hozzáadása**lehetőséget.  

2.  Az **Üdvözli az Adatforrás varázsló** lapon kattintson a **Tovább**gombra.  

3.  A **Válassza ki a kapcsolat definiálásának módját** lapon válassza az **Adatforrás létrehozása meglévő vagy új kapcsolat alapján** lehetőséget, és kattintson az **Új**gombra.  

4.  A **Csatlakozáskezelő** párbeszédpanelen adja meg a következő csatlakozási tulajdonságokat az adatforráshoz:  

    -   **Kiszolgálónév**: Írja be a Configuration Manager Helyadatbázis-kiszolgáló nevét, vagy válassza ki a listából. Ha az alapértelmezett példány helyett egy nevesített példányt dolgozik, írja be a &lt; *adatbázis-kiszolgáló*>\\&lt;*példánynév*>.  

    -   Válassza a **Windows-hitelesítés használata**beállítást.  

    -   Az a **válasszon vagy adjon meg egy adatbázisnevet** listára, válassza ki a Configuration Manager helyadatbázisának nevét.  

5.  Az adatbázis-kapcsolat kipróbálásához kattintson a **Kapcsolat tesztelése**gombra.  

6.  Ha a csatlakozás sikeres, az **OK** gombra kattintva zárja be a **Csatlakozáskezelő** párbeszédpanelt. Ha nem sikerül a csatlakozás, ellenőrizze a megadott adatok helyességét, majd kattintson újból a **Kapcsolat tesztelése** gombra.  

7.  A **Válassza ki a kapcsolat definiálásának módját** lapon ellenőrizze, hogy meg van-e adva az **Adatforrás létrehozása meglévő vagy új kapcsolat alapján** beállítás. Ellenőrizze, hogy az imént megadott adatforrás ki van-e választva az **Adatkapcsolatok** listán, és kattintson a **Tovább**gombra.  

8.  Az **Adatforrás neve**mezőben adja meg az adatforrás nevét, és kattintson a **Befejezés**gombra. Ehhez a példához írja be a következőt: **Advanced_Model**.  

9. Az **Advanced_Model.ds** adatforrás megjelenik a **Megoldáskezelő** ablaktábla **Adatforrások** csomópontjában.  

    > [!NOTE]  
    >  Meglévő adatforrás tulajdonságainak szerkesztéséhez kattintson duplán az adatforrásra a **Megoldáskezelő** ablaktábla **Adatforrások** mappájában, ezzel megjeleníti az adatforrás tulajdonságait az Adatforrás-tervezőben.  

#### <a name="to-define-the-data-source-view-for-the-report-model"></a>To define the data source view for the report model  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson az **Adatforrásnézetek** elemre, és válassza az **Új adatforrásnézet hozzáadása**lehetőséget.  

2.  Az **Üdvözli az Adatforrásnézet varázsló** lapon kattintson a **Tovább**gombra. Megjelenik az **Adatforrás kiválasztása** lap.  

3.  A **Relációs adatforrások** ablakban ellenőrizze, hogy az **Advanced_Model** adatforrás van-e kiválasztva, és kattintson a **Tovább**gombra.  

4.  A **Táblák és nézetek kijelölése** lapon lévő **Rendelkezésre álló objektumok** listájában válassza ki a következő nézeteket a jelentésmodellhez:  

    -   **v_R_System (dbo)**  

    -   **v_GS_OPERATING_SYSTEM (dbo)**  

     Az egyes nézetek kijelölése után a **>** gombra kattintva helyezze át az objektumot a **Befoglalt objektumok** elemét.  

    > [!TIP]  
    >  A **Rendelkezésre álló objektumok** lista áttekintésének megkönnyítéséhez kattintson a **Név** fejlécre a lista tetején, ezzel betűrendben jelenítheti meg az objektumokat.  

5.  Ha megjelenik a **Névegyeztetés** párbeszédpanel, fogadja el az itt szereplő beállításokat, és kattintson a **Tovább**gombra.  

6.  Miután kiválasztotta a szükséges objektumokat, kattintson a **Tovább**gombra, és adja meg az adatforrásnézet nevét. Ehhez a példához írja be a következőt: **Advanced_Model**.  

7.  Kattintson a **Befejezés**gombra. Az **Advanced_Model.dsv** adatforrásnézet megjelenik a **Megoldáskezelő** ablaktábla **Adatforrásnézetek**mappájában.  

#### <a name="to-define-relationships-in-the-data-source-view"></a>Kapcsolatok definiálása az adatforrásnézetben  

1.  A Tervezés ablak megnyitásához kattintson duplán az **Advanced_Model.dsv**lehetőségre a **Megoldáskezelőben** .  

2.  A **Táblázat lecserélése** parancs kiválasztásához kattintson az egér jobb gombjával a **v_R_System**ablak címsorára, majd az **Új elnevezett lekérdezéssel**lehetőségre.  

3.  Az **Elnevezett lekérdezés létrehozása** párbeszédpanelben kattintson a **Táblázat hozzáadása** ikonra (általában az utolsó ikon a menüszalagon).  

4.  A **Táblázat hozzáadása** párbeszédpanelben kattintson a **Nézetek** lapra, jelölje ki a **V_GS_OPERATING_SYSTEM** elemet a listában, és kattintson a **Hozzáadás**gombra.  

5.  Kattintson a **Bezárás** gombra a **Táblázat hozzáadása** párbeszédpanel bezárásához.  

6.  Az **Elnevezett lekérdezés létrehozása** párbeszédpanelen adja meg a következő információkat:  

    -   **név:** Adja meg a lekérdezés nevét. Ehhez a példához írja be a következőt: **Advanced_Model**.  

    -   **Leírás:** Adja meg a lekérdezés leírását. Ennél a példánál adja meg a **Reporting Services jelentésmodell – példa**leírást.  

7.  A **v_R_System** ablakban jelölje ki a következő elemeket az objektumok listájában, így azok megjelennek a jelentésmodellben:  

    -   **ResourceID**  

    -   **ResourceType**  

    -   **Active0**  

    -   **AD_Domain_Name0**  

    -   **AD_SiteName0**  

    -   **Client0**  

    -   **Client_Type0**  

    -   **Client_Version0**  

    -   **CPUType0**  

    -   **Hardware_ID0**  

    -   **User_Domain0**  

    -   **User_Name0**  

    -   **Netbios_Name0**  

    -   **Operating_System_Name_and0**  

8.  A **v_GS_OPERATING_SYSTEM** mezőben jelölje ki a következő elemeket az objektumok listájában, így azok megjelennek a jelentésmodellben:  

    -   **ResourceID**  

    -   **Caption0**  

    -   **CountryCode0**  

    -   **CSDVersion0**  

    -   **Description0**  

    -   **InstallDate0**  

    -   **LastBootUpTime0**  

    -   **Locale0**  

    -   **Manufacturer0**  

    -   **Version0**  

    -   **WindowsDirectory0**  

9. Ha azt szeretné, hogy az objektumok egy listaként jelenjenek meg a jelentés készítője számára ezekben a nézetekben, akkor egy összekapcsolással meg kell adnia a kapcsolatot a két tábla vagy nézet között. A két nézetet a mindkét nézetben megjelenő **ResourceID**objektum segítségével kapcsolhatja össze.  

10. A **v_R_System** ablakban kattintson a **ResourceID** objektumra, és húzza rá a **v_GS_OPERATING_SYSTEM** ablakban lévő **ResourceID** objektumra.  

11. Kattintson az **OK**gombra.  

12. Az **Advanced_Model** ablak kerül a **v_R_System** ablak helyére, és a jelentésmodellhez szükséges minden objektumot tartalmazza a **v_R_System** és a **v_GS_OPERATING_SYSTEM** nézetekből. Most törölheti a **v_GS_OPERATING_SYSTEM** ablakot az Adatforrásnézet-tervezőből. A **Táblázat törlése adatforrásnézetből** lehetőség kijelöléséhez kattintson a **v_GS_OPERATING_SYSTEM**ablak címsorára az egér jobb gombjával. Az **Objektumok törlése** párbeszédpanelben kattintson az **OK** gombra a törlés jóváhagyásához.  

13. Kattintson a **Fájl**menü **Összes mentése**parancsára.  

#### <a name="to-create-the-report-model"></a>To create the report model  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson a **Jelentésmodellek** elemre, és válassza az **Új jelentésmodell hozzáadása**lehetőséget.  

2.  Az **Üdvözli a Jelentésmodell varázsló** lapon kattintson a **Tovább**gombra.  

3.  Az **Adatforrásnézetek kiválasztása** lapon jelölje ki az adatforrásnézetet a **Rendelkezésre álló adatforrásnézetek** listában, és kattintson a **Tovább**gombra. Ehhez a példához válassza ki a következőt: **Simple_Model.dsv**.  

4.  A **Jelentésmodell létrehozási szabályainak kiválasztása** lapon ne módosítsa az alapértékeket, és kattintson a **Tovább**gombra.  

5.  A **Modell statisztikai adatainak összegyűjtése** lapon ellenőrizze, hogy ki van-e választva a **Modell statisztikai adatainak frissítése a létrehozása előtt** beállítás, és kattintson a **Tovább**gombra.  

6.  **A varázsló befejezése** lapon adja meg a jelentésmodell nevét. Ebben a példában az **Advanced_Model** névnek kell megjelennie.  

7.  A varázsló befejezéséhez és a jelentésmodell létrehozásához kattintson a **Futtatás**gombra.  

8.  A varázslóból való kilépéshez kattintson a **Befejezés**gombra.  

9. A jelentésmodell megjelenik a Tervezés ablakban.  

#### <a name="to-modify-object-names-in-the-report-model"></a>Objektumnevek módosítása a jelentésmodellben  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson az egyik jelentésmodellre, és válassza a **Nézettervező**lehetőséget. Ehhez a példához válassza ki a következőt: **Advanced_Model.smdl**.  

2.  A jelentésmodell Tervezés nézetében kattintson az egér jobb gombjával az egyik objektum nevére, és válassza az **Átnevezés**parancsot.  

3.  Adjon új nevet a kijelölt objektumnak, és nyomja meg az Enter billentyűt. Átnevezheti például a **CSD_Version_0** objektumot, és a **Windows szervizcsomag verziója**nevet adhatja neki.  

4.  Ha befejezte az objektum átnevezését, kattintson a **Fájl**menüre, majd az **Összes mentése**parancsra.  

#### <a name="to-publish-the-report-model-for-use-in-sql-server-reporting-services"></a>To publish the report model for use in SQL Server Reporting Services  

1.  A **Megoldáskezelő**ablaktáblában az egér jobb gombjával kattintson az **Advanced_Model.smdl** lehetőségre, és válassza a **Telepítés**parancsot.  

2.  Figyelje a telepítés állapotát az **SQL Server Business Intelligence Development Studio** ablak bal alsó sarkában. A telepítés befejezését a **Telepítés sikeres** felirat megjelenése jelzi. Ha nem sikerül a telepítés, a hiba oka megjelenik a **Kimenet** ablakban. Az új jelentés ekkor elérhető az SQL Server Reporting Services webhelyén.  

3.  Válassza a **Fájl**menü **Összes mentése**parancsát, majd zárja be az **SQL Server Business Intelligence Development Studio**ablakot.  

#### <a name="to-deploy-the-custom-report-model-to-configuration-manager"></a>To deploy the custom report model to Configuration Manager  

1.  Keresse meg azt a mappát, amely a létrehozott jelentésmodell-projektet tartalmazza. Például %*USERPROFILE*%\Documents\Visual Studio 2008\Projects\\*&lt;projektnevet\>.*  

2.  Másolja át a következő fájlokat a jelentésmodell-projekt mappájából egy ideiglenes mappába a számítógépen:  

    -   *&lt;A modell neve\>*  **.dsv**  

    -   *&lt;A modell neve\>*  **.smdl**  

3.  Nyissa meg ezeket a fájlokat egyszerű szövegszerkesztőben, például a Jegyzettömbben.  

4.  A fájl  *&lt;modellnév\>***.dsv**, keresse meg az első sort, amelyben a következő fájl:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine"\>**  

     Módosítsa ezt a sort a következőre:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine" xmlns:xsi = "RelationalDataSourceView"\>**  

5.  Másolja a Windows vágólapra a fájl teljes tartalmát.  

6.  Zárja be a fájlt  *&lt;modellnév\>***.dsv**.  

7.  A fájl  *&lt;modellnév\>***.smdl**, keresse meg az utolsó három sort a fájl, amely a következőképpen jelenik meg:  

     `</Entity>`  

     `</Entities>`  

     `</SemanticModel>`  

8.  Illessze be a fájl tartalmát  *&lt;modellnév\>***.dsv** közvetlenül a fájl utolsó sora elé (**&lt;SemanticModel\>**).  

9. Mentse és zárja be a fájl  *&lt;modellnév\>***.smdl**.  

10. A fájl másolása  *&lt;modellnév\>***.smdl** mappához *% programfiles %*\Microsoft Configuration Manager\AdminConsole\XmlStorage\Other a Configuration Manager helykiszolgálón.  

    > [!IMPORTANT]  
    >  Miután átmásolta a jelentésmodell fájlját a Configuration Manager-kiszolgálóra, ki kell lépnie és a Configuration Manager konzol újraindítása után is használhatja a jelentésmodellt a **jelentés létrehozása varázsló**.  

