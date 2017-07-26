---
title: "Kapcsolat eszköz szolgáltatás |} Microsoft Docs"
description: "További információ erről az eszközről, amely lehetővé teszi a használati adatok manuális feltöltéséhez Configuration Manager felhőszolgáltatáshoz való kapcsolódáshoz."
ms.custom: na
ms.date: 4/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e4964c5-43cb-4372-9a89-b62ae6a4775c
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 32f7fc4ef9c8e8d3c2ec8eeaf9a3174bad992ffb
ms.openlocfilehash: 0da80521bf223a765c3731f8ad59623d85a4c9fa
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-service-connection-tool-for-system-center-configuration-manager"></a>A System Center Configuration Manager szolgáltatáskapcsolódási eszközének használata

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a **szolgáltatáskapcsolódási eszközt** amikor a szolgáltatáskapcsolódási pont offline módban van, vagy ha a Configuration Manager helyrendszer-kiszolgálói nem kapcsolódnak az internethez. Az eszköz segítségével a hely naprakész állapotban tartása a legújabb frissítéseket a Configuration Manager.  

Futtatásakor az eszköz manuálisan csatlakozik a Configuration Manager felhőszolgáltatáshoz a hierarchiához kapcsolódó használati adatok feltöltése, és a frissítések letöltéséhez. A használati adatok feltöltése ahhoz szükséges, hogy a felhőszolgáltatás a megfelelő frissítéseket biztosíthassa a környezethez.  

## <a name="prerequisites-for-using-the-service-connection-tool"></a>A szolgáltatáskapcsolódási eszköz használatának előfeltételei
A következő: Előfeltételek és ismert problémákat.

**Előfeltételek:**

-   Egy telepített szolgáltatáskapcsolódási pont, amelyen az **Offline, csatlakozás igény esetén**beállítás lett konfigurálva.  

-   Az eszközt a parancssorból kell futtatni.  

-   Minden számítógépnek, amelyen az eszköz fut (beleértve a szolgáltatáskapcsolódási pont számítógépét és az internethez kapcsolódó számítógépet is) 64 bites operációs rendszerrel kell működnie, és telepítve kell lennie rajta a következőknek:  

    -   A **Visual C++ terjeszthető csomagjának** x86- és x64-alapú fájljai.   Alapértelmezés szerint a Configuration Manager telepíti a x64 verzióját a számítógépen, amely a szolgáltatáskapcsolódási pontot futtatja.  

         Ha szeretné letölteni a Visual C++ csomag fájljait, keresse fel a [Visual C++ Redistributable Packages for Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=40784) (Visual C++ terjeszthető csomagok a Visual Studio 2013-hoz) oldalt a Microsoft letöltőközpontban.  

    -   A .NET-keretrendszer 4.5.2-es vagy újabb verziója.  

-   Az eszköz futtatásához használt fióknak rendelkeznie kell a következőkkel:
    -   **Helyi rendszergazdai** engedély azon a számítógépen, amely a szolgáltatáskapcsolódási pontot futtatja (amelyen az eszköz fut).
    -   **Olvasási** engedély a helyadatbázishoz.  



-   Szüksége lesz egy elegendő szabad területtel rendelkező USB-meghajtóra, vagy valamilyen más módszerre a fájlok átviteléhez a szolgáltatáskapcsati pont számítógépe és az internetkapcsolattal rendelkező számítógép között. (Ebben a forgatókönyvben azt feltételezzük, hogy a hely és a felügyelt számítógépek közvetlenül nem kapcsolódnak az internethez.)  



## <a name="use-the-service-connection-tool"></a>A szolgáltatáskapcsolódási eszköz használata  

 A szolgáltatáskapcsolódási eszköz található (**serviceconnectiontool.exe**), a Configuration Manager telepítési adathordozójának **%path%\smssetup\tools\ServiceConnectionTool** mappa. A szolgáltatáskapcsolódási eszköz, amely megfelel a Configuration Manager verziója, amelyekkel mindig használata.


 Ebben az eljárásban a parancssori példák a következő fájlneveket és mappahelyeket használják (nem feltétlenül kell ezeket megadnia, használhat a környezetnek és a preferenciáinak megfelelő elérési utakat és fájlneveket):  

-   Kiszolgálók közötti átvitel céljából adatokat tároló USB-meghajtó elérési útja:  **D:\USB\\**  

-   A helyről exportált adatokat tartalmazó .cab-fájl nevét: **UsageData.cab**  

-   A letöltött frissítések a Configuration Manager a rendszer hol tárolja a kiszolgálók közötti átvitel üres mappa neve: **UpdatePacks**  

A szolgáltatáskapcsolódási pontot üzemeltető számítógépen:  

-   Nyissa meg a parancssort rendszergazdaként, majd lépjen arra a helyre, amely a **serviceconnectiontool.exe**fájlt tartalmazza.  

     Alapértelmezés szerint megtalálható ez az eszköz a Configuration Manager telepítési adathordozójának **%path%\smssetup\tools\ServiceConnectionTool** mappa. A szolgáltatáskapcsolódási eszköz működéséhez a mappán belül minden fájlnak azonos mappában kell lennie.  

A következő paranccsal utasíthatja arra az eszközt, hogy készítse elő a használati adatokat tartalmazó .cab-fájlt, és másolja a megadott helyre. A .cab-fájlban található adatok azon alapulnak, hogy a hely milyen szintű diagnosztikai adatok gyűjtésére van konfigurálva. (lásd: [Diagnosztikai és használati adatok a System Center Configuration Managerben](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)).  A .cab-fájl létrehozásához futtassa a következő parancsot:  

-   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

Emellett a ServiceConnectionTool mappát teljes tartalmával együtt az USB-meghajtóra kell másolnia, vagy más módon elérhetővé kell tennie azt a 3. és a 4. lépésben használni kívánt számítógép számára.  

### <a name="overview"></a>Áttekintés
**A szolgáltatáskapcsolódási eszköz használata három fő lépésből áll:**  

1.  **Készítse elő**:  Ez a lépés a szolgáltatáskapcsolódási pontot üzemeltető számítógépen fut. Az eszköz futtatásakor a használati adatok egy .cab fájlba helyezi, és azt egy USB-meghajtón tárolja (vagy másodlagos átviteli helyen adja meg).  

2.  **Csatlakozás**: Ebben a lépésben az eszközt, amely kapcsolódik az internethez, így a használati adatok feltöltése és majd a frissítések letöltése távoli számítógépen futtatja.  

3.  **Importálás**: Ez a lépés a szolgáltatáskapcsolódási pontot üzemeltető számítógépen fut. Futtatásakor az eszköz meg a letöltött importálja, és hozzáadja a helyet, majd megtekintheti és ezek a frissítések telepítése a Configuration Manager konzoljáról.  

Az 1606-os verziótól kezdve a Microsofthoz való csatlakozáskor több .cab fájlt is feltölthet egyszerre (mindegyiket különböző hierarchiából), valamint megadhatja a proxykiszolgálót és a proxykiszolgáló felhasználóját.   

**Több .cab fájl feltöltéséhez végezze el a következőket:**
 -  A különböző hierarchiákból exportált .cab fájlokat helyezze ugyanabba a mappába. Minden fájlnévnek egyedinek kell lennie. A fájlokat szükség esetén manuálisan átnevezheti.
 -  Amikor az adatok Microsofthoz való feltöltéséhez futtatja a parancsot, adja meg a .cab fájlokat tartalmazó mappa helyét. (A 1606-os verzió előtt egyszerre csak egyetlen hierarchiából lehetett adatot feltölteni, és a mappában lévő .cab fájl nevét is meg kellett adni.)
 -  Amikor az importálási feladatot futtatja egy hierarchia szolgáltatáskapcsolódási pontján, az eszköz automatikusan importálja az adott hierarchia adatait.  

**Proxykiszolgáló megadása:**  
A proxykiszolgáló megadásánál az alábbi választható paramétereket is használhatja (ezeknek a paramétereknek a használatáról további információt talál a jelen témakör Parancssori paraméterek szakaszában):
  - **-proxyserveruri [proxykiszolgáló teljes tartományneve]**  Ezzel a paraméterrel megadhatja az ehhez a kapcsolathoz használt proxykiszolgálót.
  -  **-proxyusername [felhasználónév]**  Ezzel a paraméterrel megadhatja a proxykiszolgáló felhasználóját.



### <a name="to-use-the-service-connection-tool"></a>A szolgáltatáskapcsolódási eszköz használata  

1.  A szolgáltatáskapcsolódási pontot üzemeltető számítógépen:  

    -   Nyissa meg a parancssort rendszergazdaként, majd lépjen arra a helyre, amely a **serviceconnectiontool.exe**fájlt tartalmazza.   

2.  A következő paranccsal utasíthatja arra az eszközt, hogy készítse elő a használati adatokat tartalmazó .cab-fájlt, és másolja azt a megadott helyre:  

    -   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

    Ha egyszerre több hierarchiából tölt fel .cab fájlokat, a mappa mindegyik .cab fájljának egyedi névvel kell rendelkeznie. A mappához adandó fájlokat manuálisan is átnevezheti.

    Ha szeretné megtekinteni a Configuration Manager felhőszolgáltatásba való feltöltésre összegyűjtött használati információkat, a következő paranccsal exportálhatja azokat egy .csv-fájlba, amelyet azután az Excellel vagy egy hasonló alkalmazással tekinthet meg:  

    -   **serviceconnectiontool.exe -export -dest D:\USB\UsageData.csv**  

3.  Az előkészítési lépés befejezése után csatlakoztassa az USB-meghajtót egy olyan számítógéphez, amely kapcsolódik az internethez, vagy más módon tegye elérhetővé az adatokat az internetkapcsolattal rendelkező gép számára.  

4.  Az internetkapcsolattal rendelkező számítógépen nyissa meg a parancssort rendszergazdai jogosultságokkal, majd lépjen abba a mappába, amely a  **serviceconnectiontool.exe** eszközt és az eszköz mappájából származó további fájlokat tartalmazza.  

5.  A használati információk feltöltésének és a Configuration Managerhez tartozó frissítések letöltésének elindításához futtassa a következő parancsot:  

    -   **serviceconnectiontool.exe-connect - usagedatasrc D:\USB - updatepackdest D:\USB\UpdatePacks**

    Ennek a parancsnak a használatához további példákat talál a jelen témakör [Parancssori kapcsolók](../../../core/servers/manage/use-the-service-connection-tool.md#bkmk_cmd) szakaszában.

    > [!NOTE]  
    >  A Configuration Manager felhőszolgáltatáshoz való kapcsolódásra szolgáló parancs futtatásakor a következőhöz hasonló hiba adódhat:  
    >   
    >  -   Nem kezelt kivétel: System.UnauthorizedAccessException:  
    >   
    >      A következő elérési úthoz való hozzáférés megtagadva: 'C:\  
    >     Users\br\AppData\Local\Temp\extractmanifestcab\95F8A562.sql'.  
    >   
    > Ez a hiba nyugodtan figyelmen kívül hagyható – ha megjelenik, zárja be a hibaüzenetet, és folytassa a parancs futtatását.  

6.  Ha befejeződött a Configuration Managerhez tartozó frissítések letöltése, csatlakoztassa az USB-meghajtót a szolgáltatáskapcsolódási pontot futtató számítógéphez, vagy más módon tegye elérhetővé az adatokat a gép számára.  

7.  A szolgáltatáskapcsolódási pontot futtató számítógépen nyissa meg a parancssort rendszergazdai jogosultságokkal, lépjen a **serviceconnectiontool.exe**fájlt tartalmazó mappába, majd futtassa a következő parancsot:  

    -   **serviceconnectiontool.exe -import -updatepacksrc D:\USB\UpdatePacks**  

8.  Ha az importálás befejeződött, bezárhatja a parancssort. (Csak a vonatkozó hierarchia frissítései lesznek importálva).  

9. Nyissa meg a Configuration Manager konzolt, és navigáljon a **felügyeleti** > **frissítés és karbantartás**. A korábban importált frissítések már elérhetők telepítésre. (Előtt verzió 1702, frissítés és karbantartás alatt állt **felügyeleti** > **Felhőszolgáltatások**.)

 A frissítések telepítésével kapcsolatban lásd: [A System Center Configuration Manager konzolon elérhető frissítések telepítése](../../../core/servers/manage/install-in-console-updates.md).  

## <a name="bkmk_cmd"></a> Parancssori kapcsolók  
 A szolgáltatáskapcsolódási pont kezelésére szolgáló eszközre vonatkozó információk megtekintéséhez nyissa meg a parancssort, lépjen abba a mappába, amelyben az eszköz található, majd futtassa a  **serviceconnectiontool.exe**parancsot.  

|Parancssori kapcsolók|Részletek|  
|---------------------------|-------------|  
|**-prepare -usagedatadest [meghajtó:][elérési_út][fájlnév.cab]**|Ezzel a paranccsal tárolhatók az aktuális használati adatok egy .cab-fájlban.<br /><br /> A parancsot **helyi rendszergazdaként** futtassa a szolgáltatáskapcsolódási pontot üzemeltető kiszolgálón.<br /><br /> Például:   **-prepare -usagedatadest D:\USB\Usagedata.cab**|    
|**-connect -usagedatasrc [meghajtó:][elérési út] -updatepackdest [meghajtó:][elérési út] -proxyserveruri [proxykiszolgáló teljes tartományneve] -proxyusername [felhasználónév]** <br /> <br /> Ha a Configuration Manager 1606-os előtti verzióját használja, meg kell adnia a .cab fájl nevét, a proxykiszolgálóra vonatkozó kapcsolók pedig nem használhatók.  A parancs támogatott paraméterei az alábbiak: <br /> **-connect -usagedatasrc [meghajtó:][elérési út][fájlnév] -updatepackdest [meghajtó:][elérési út]** |Ezzel a paranccsal kapcsolódhat a Configuration Manager felhőszolgáltatásához a használati adatokat tartalmazó .cab fájlok feltöltéséhez a megadott helyről, és az elérhető frissítési csomagok és konzoltartalmak letöltéséhez. A proxykiszolgálóra vonatkozó kapcsolók használata nem kötelező.<br /><br /> A parancsot **helyi rendszergazdaként** futtassa az internetkapcsolattal rendelkező számítógépen.<br /><br /> Példa a proxykiszolgáló nélküli kapcsolódáshoz: **-connect -usagedatasrc D:\USB\ -updatepackdest D:\USB\UpdatePacks** <br /><br /> Példa a kapcsolódásra proxykiszolgáló használatával: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks -proxyserveruri itgproxy.redmond.corp.microsoft.com -proxyusername Meg** <br /><br /> Ha 1606-os előtti verziót használ, meg kell adnia a .cab fájl nevét, proxykiszolgáló pedig nem adható meg. Például használja ezt a parancsot: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks**|      
|**-import -updatepacksrc [meghajtó:][elérési_út]**|Ezzel a paranccsal importálhatók a korábban a Configuration Manager-konzolra letöltött frissítési csomagok és konzoltartalmak.<br /><br /> A parancsot **helyi rendszergazdaként** futtassa a szolgáltatáskapcsolódási pontot üzemeltető kiszolgálón.<br /><br /> Például:  **-import -updatepacksrc D:\USB\UpdatePacks**|  
|**-export -dest [meghajtó:][elérési_út][fájlnév.csv]**|Ezzel a paranccsal exportálhatja a használati adatokat .csv fájlba, amelyet ezután megtekinthet.<br /><br /> A parancsot **helyi rendszergazdaként** futtassa a szolgáltatáskapcsolódási pontot üzemeltető kiszolgálón.<br /><br /> Például: **-export -dest D:\USB\usagedata.csv**|  

