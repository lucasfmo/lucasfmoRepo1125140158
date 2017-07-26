---
title: "Mac számítógépekhez készült alkalmazások létrehozása |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozása és központi telepítésekor az alkalmazások Mac számítógépeken."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab1aecdd-d943-44f5-b0a9-e8fe7439e5d6
caps.latest.revision: 9
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ba45f36c517114f7a8d2be8d9056e1b2a800dd4f
ms.openlocfilehash: ffd66a4047ec253704e9772e2c3e3a4d9db7c46f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-mac-computer-applications-with-system-center-configuration-manager"></a>Mac számítógépekhez készült alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A következő szempontokat vegye figyelembe, létrehozása és központi telepítésekor az alkalmazások Mac számítógépeken.  

> [!IMPORTANT]  
>  Ebben a témakörben szereplő eljárások alkalmazások Mac számítógépek, amelyeken telepítve van a Configuration Manager-ügyfél telepítése terjednek ki. A Microsoft Intune-ba beléptetett Mac számítógépek nem támogatják az alkalmazások központi telepítését.  

## <a name="general-considerations"></a>Általános megfontolások  
 System Center Configuration Manager segítségével a Configuration Manager Mac ügyfelet futtató Mac számítógépekre központilag telepíthetők alkalmazások. Szoftverek telepíthetők központilag Mac számítógépekre lépései hasonlóak a lépéseket, a szoftver központi telepítése Windows rendszerű számítógépekre. Azonban ahhoz, hogy alkalmazások létrehozása és telepítése a Configuration Manager által felügyelt Mac számítógépeken, vegye figyelembe a következőket:  

-   Mac-alkalmazáscsomagok Mac számítógépekre történő telepítése előtt kell használnia a **CMAppUtil** eszközt egy Mac számítógépen a Configuration Manager által olvasható formátumba alakítsa át a ezeket az alkalmazásokat.  

-   A Configuration Manager nem támogatja a felhasználók Mac-alkalmazások központi telepítését. Ehelyett a központi telepítéseket kell tenni az eszközök. Hasonlóképpen, Mac-alkalmazások központi telepítése, a Configuration Manager nem támogatja a **előzetes központi telepítés a felhasználó elsődleges eszközén** beállítást a **központi telepítési beállítások** oldalán a **szoftver központi telepítése varázsló**.  

-   A Mac-alkalmazások szimulált központi telepítéseket támogatnak.  

-   **Elérhető**célú Mac számítógépekre központilag nem telepíthetők alkalmazások.  

-   A központi szoftvertelepítés közben történő ébresztésicsomag-küldési beállítás Mac számítógépeken nem támogatott.  

-   Mac számítógépek nem támogatják a háttérben futó intelligens átviteli szolgáltatás (BITS) alkalmazás tartalom letöltése. Ha egy alkalmazás letöltése meghiúsul, a rendszer újraindítja az elejétől.  

-   A Configuration Manager nem támogatja a globális feltételeket Mac számítógépeken történő KözpontiTelepítés-típusok létrehozásakor.  

## <a name="steps-to-create-and-deploy-an-application"></a>Hozzon létre és telepítsen egy alkalmazást lépései  
 A következő táblázat a lépéseket, részleteket és létrehozásának és központi telepítése az alkalmazások Mac számítógépeken.  

|Lépés|Részletek|  
|----------|-------------|  
|**1. lépés**: A Configuration Manager Mac-alkalmazások előkészítése|A Configuration Manager-alkalmazásokat tudna Mac szoftvercsomagokból hozhat létre, mielőtt kell használnia a **CMAppUtil** eszközt egy Mac számítógépen, a Configuration Manager a Mac-szoftvert konvertálható**.cmmac** fájl.|  
|**2. lépés**: A Mac szoftvert tartalmazó Configuration Manager-alkalmazás létrehozása|Használja a **alkalmazás létrehozása varázsló** a Mac szoftverhez tartozó alkalmazások létrehozásához.|  
|**3. lépés**: A Mac-alkalmazás központi telepítési típus létrehozása|Ezt a lépést csak akkor kell megtenni, ha az információt nem importálta automatikusan az alkalmazásból.|  
|**4. lépés**: A Mac-alkalmazás központi telepítése|Használja a **szoftver központi telepítése varázsló** Mac számítógépeken az alkalmazás telepítéséhez.|  
|**5. lépés**: A Mac-alkalmazás központi telepítésének figyelése|Kövesse nyomon az alkalmazások Mac számítógépekre történő telepítésének sikerességét.|  

## <a name="supplemental-procedures-to-create-and-deploy-applications-for-mac-computers"></a>Kiegészítő eljárások alkalmazások Mac számítógépeken történő létrehozásához és központi telepítéséhez  
 Az alábbi eljárások segítségével Mac számítógépekhez a Configuration Manager által kezelt alkalmazások létrehozása és telepítése.  

###  <a name="step-1-prepare-mac-applications-for-configuration-manager"></a>1. lépés: A Configuration Manager Mac-alkalmazások előkészítése  
 A folyamat létrehozásának és központi telepítése a Configuration Manager-alkalmazások Mac számítógépek számára a Windows rendszerű számítógépeken a telepítési folyamat hasonlít. Azonban Mac-telepítési típusokat tartalmazó Configuration Manager-alkalmazások létrehozása előtt elő kell készítenie az alkalmazásokat használatával a **CMAppUtil** eszköz. Az eszköz a Mac-ügyfélszoftver telepítőfájljaival együtt töltődik le. A **CMAppUtil** eszköz képes információt gyűjteni az alkalmazásról, így például észlelési adatokat is a következő Mac-csomagokból:  

-   Apple-lemezképfájl (.dmg)  

-   Meta Package-fájl (.mpkg)  

-   Mac OS X telepítőcsomag (.pkg)  

-   Mac OS X-alkalmazás (.app)  

Az alkalmazásinformációk összegyűjtése után a **CMAppUtil** eszköz létrehoz egy **.cmmac**kiterjesztésű fájlt. Ez a fájl tartalmazza a Mac szoftver telepítési fájljait és azon észlelési módszerek információit, amelyekkel kiértékelheti, hogy az alkalmazás már telepítve van-e. A**CMAppUtil** olyan **.dmg** -fájlokat is fel tud dolgozni, amelyek több Mac alkalmazást tartalmaznak, és mindegyik alkalmazáshoz különböző telepítési típusokat tud létrehozni.  

1.  Másolja a Mac szoftvertelepítő csomagot abba a mappába a Mac számítógépen, amelyikbe kibontotta a Microsoft letöltőközpontból beszerzett **macclient.dmg** fájl tartalmát.  

2.  Ugyanezen a Mac számítógépen nyisson egy terminálablakot, és keresse meg azt a mappát, amelyikbe kibontotta a **macclient.dmg** fájl tartalmát.  

3.  Keresse meg a **eszközök** mappa, és futtassa a következő parancssori parancsot:  

     **./CMAppUtil** *<tulajdonságok\>*  

     Például, hogy a konvertálandó elnevezésű Apple lemezképfájl tartalmát **szoftverem.dmg** a felhasználó asztali mappájában tárolt egy **cmmac** fájl ugyanabba a mappába. Is szeretne létrehozni **cmmac** fájlok, amelyek szerepelnek a lemezképfájl összes alkalmazáshoz. Ehhez írja be a következő parancssort:  

     **./CMApputil –c /Users/** *<Felhasználónév\>* **/Desktop/MySoftware.dmg -o /Users/** *<Felhasználónév\>* **/Desktop -a**  

    > [!NOTE]  
    >  Az alkalmazás neve nem lehet hosszabb 128 karakternél.  

     A **CMAppUtil**eszközhöz tartozó beállításokat az alábbi táblázatban olvasható parancssori tulajdonságokkal tudja megadni:  

    |Tulajdonság|További információ|  
    |--------------|----------------------|  
    |**-h**|A parancssori tulajdonságok megjelenítése.|  
    |**-r**|A megadott **detection.xml** fájl **.cmmac** kimenetének kiírása az **stdout**kimeneti adatfolyamba. A kimenet tartalmazza a **.cmmac** -fájl létrehozásához használt **CMAppUtil** eszköz észlelési paramétereit és verziószámát.|  
    |**-c**|Adja meg a forrásfájl kell alakítani.|  
    |**-o**|Adja meg a kimeneti elérési útvonal a-c tulajdonsággal együtt.|  
    |**-a**|Automatikusan létrehozza az összes alkalmazás és a lemezképfájllal csomagok a-c tulajdonsággal együtt használható .cmmac fájlok.|  
    |**-s**|A **detection.xml** létrehozásának kihagyása, ha nem található észlelési paraméter, továbbá a **.cmmac** fájl kényszerített létrehozása a **detection.xml** fájl nélkül.|  
    |**-v**|Részletesebb kimenet megjelenítése a **CMAppUtil** eszközből a diagnosztikai adatokkal együtt.|  

4.  Annak biztosítása, hogy a **.cmmac** fájl a megadott kimeneti mappában jöjjön létre.  

###  <a name="create-a-configuration-manager-application-that-contains-the-mac-software"></a>A Mac szoftvert tartalmazó Configuration Manager-alkalmazás létrehozása  

A következő eljárással hozhat létre egy alkalmazást a Configuration Manager által felügyelt Mac számítógépeken.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás létrehozása**.  

4.  Az a **általános** oldalán a **alkalmazás létrehozása varázsló**, jelölje be **a telepítési fájlokból az alkalmazás adatainak automatikus észlelése**.  

    > [!NOTE]  
    >  Ha az alkalmazással kapcsolatos adatok megadása saját kezűleg szeretné, válassza ki a **az alkalmazás adatainak manuális megadása**. Az információk manuális megadására vonatkozó további információkért lásd: [Alkalmazások létrehozása a System Center Configuration Managerrel](../../apps/deploy-use/create-applications.md).  

5.  A **Típus** legördülő listában válassza a **Mac OS X**elemet.  

6.  Az a **hely** mezőben adja meg az UNC elérési útnak a képernyőn  *\\ \\< server\>\\< megosztás\>\\< fájlnév\>*  a Mac alkalmazástelepítő fájl (**.cmmac** fájl) alkalmazással kapcsolatos információk észleléséhez. Választhatja a **Tallózás** keresse meg és adja meg a telepítőfájl helyét.  

    > [!NOTE]  
    >  Az alkalmazást tartalmazó UNC elérési útnak elérhetőnek kell lennie.  

7.  Válasszon **következő**.  

8.  Az a **importálási adatok** oldalán a **alkalmazás létrehozása varázsló**, tekintse át az importált információkat. Ha szükséges, választhat **előző** lépjen vissza, és kijavíthatja az esetleges hibákat. Válasszon **tovább** a folytatáshoz.  

9. Az a **általános információkat** oldalán a **alkalmazás létrehozása varázsló**, adja meg az alkalmazásadatokat, például az alkalmazás nevét, a megjegyzéseket, a verziót és a egy nem kötelező hivatkozást, amellyel hivatkozni, a Configuration Manager konzolon az alkalmazás adatait.  

    > [!NOTE]  
    >  Már egy része az alkalmazás adatainak lehet ezen a lapon, ha korábban már beolvasták őket az alkalmazástelepítő fájlokból.  

10. Válasszon **következő**, ellenőrizze az alkalmazás adatait a **összegzés** lapon, és fejezze be a **alkalmazás létrehozása varázsló**.  

11. Az új alkalmazás megjelenik a **alkalmazások** csomópont a Configuration Manager konzol.  

###  <a name="step-3-create-a-deployment-type-for-the-mac-application"></a>3. lépés: A Mac-alkalmazás központi telepítési típus létrehozása  
 A következő eljárással hozhat létre a központi telepítési típus a Configuration Manager által felügyelt Mac számítógépeken.  

> [!NOTE]  
>  Ha automatikusan importált az alkalmazással kapcsolatos információkat a **alkalmazás létrehozása varázsló**, az alkalmazás központi telepítési típust lehet, hogy már létrejött.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Válasszon ki egy alkalmazást. Ezt követően a **Home** lap a **alkalmazás** csoportjában válassza **központi telepítési típus létrehozása** az alkalmazás egy új központi telepítési típus létrehozásához.  

    > [!NOTE]  
    >  Úgy is elindíthatja a **központi telepítési típus varázsló** a a **alkalmazás létrehozása varázsló** pedig a **központi telepítési típusok** lapján a *< alkalmazás neve\>*  **tulajdonságok** párbeszédpanel.  

4.  Az a **általános** oldalán a **központi telepítési típus varázsló**, a a **típus** legördülő listában válassza **Mac OS X**.  

5.  Az a **hely** mezőben adja meg az UNC elérési útnak alakúnak \\ \\< server\>\\< megosztás\>\\< fájlnév\> az alkalmazástelepítő fájl (**.cmmac** fájl). Választhatja a **Tallózás** keresse meg és adja meg a telepítőfájl helyét.  

    > [!NOTE]  
    >  Az alkalmazást tartalmazó UNC elérési útnak elérhetőnek kell lennie.  

6.  Válasszon **következő**.  

7.  Az importált információkat a **Központi telepítési típus varázsló** **Importálási adatok**lapján tekintheti meg. Szükség esetén válasszon **előző** visszalép, és kijavíthatja az esetleges hibákat. Válasszon **tovább** a folytatáshoz.  

8.  A **Központi telepítési típus varázsló** **Általános információ**lapján adhatja meg az alkalmazásadatokat, például az alkalmazás nevét, a megjegyzéseket, illetve a központitelepítés-típushoz rendelkezésre álló nyelveket.  

    > [!NOTE]  
    >  Már egy része a központi telepítési típussal kapcsolatos információk lehet ezen a lapon, ha korábban már beolvasták őket az alkalmazástelepítő fájlokból.  

9. Válasszon **következő**.  

10. Az a **követelmények** oldalán a **központi telepítési típus varázsló**, megadhatja a feltételeket, amelyeknek teljesülniük kell ahhoz a központi telepítési típus Mac számítógépekre telepíthető.  

11. Válasszon **Hozzáadás** megnyitásához a **követelmény létrehozása** párbeszédpanel megnyitásához és új követelmény hozzáadásához.  

    > [!NOTE]  
    >  Az új követelményeket is hozzáadhat a **követelmények** lapján a *< telepítési típus neve\>*  **tulajdonságok** párbeszédpanel.  

12. A **Kategória** legördülő listában válassza ki, hogy az adott követelmény eszközre vonatkozik.  

13. Az a **feltétel** legördülő listára, válassza ki a feltételt, annak ellenőrzéséhez, hogy a Mac számítógép megfelel-e a telepítési követelményeknek használni kívánt. A lista tartalma a kiválasztott kategória függ.  

14. Az a **operátor** legördülő menüben válassza ki az üzemeltető segítségével összehasonlítja a választott feltételt és a megadott értéket annak ellenőrzéséhez, hogy a felhasználó vagy az eszköz megfelel-e a telepítési követelményeknek. Az elérhető operátorok a választott feltételtől függenek.  

15. Az a **érték** mezőben adja meg az értékeket a választott feltétellel és operátorral együtt annak ellenőrzéséhez, hogy a felhasználó vagy az eszköz megfelel-e a telepítési követelményeknek. A lehetséges értékek a feltétellel és operátorral kiválasztott függenek.

16. Válasszon **OK** menteni a követelményszabályoknak, és zárja be a **követelmény létrehozása** párbeszédpanel megnyitásához.  

17. Az a **követelmények** oldalán a **központi telepítési típus varázsló**, válassza a **következő**.  

18. A varázsló számára elvégzendő műveleteket a **Központi telepítési típus varázsló** **Összefoglalás**lapján tekintheti meg.  Szükség esetén válasszon **előző** visszalép, és központi telepítési típus beállításainak módosításához. Válasszon **tovább** a központi telepítési típus létrehozásához.  

19. Után a **folyamatban** lapon befejeződik, tekintse át a végrehajtandó műveleteket került sor, és válassza a **Bezárás** befejezéséhez a **központi telepítési típus varázsló**.  

20. Ha a varázslót a **alkalmazás létrehozása varázsló**, ismét megjelenik a **központi telepítési típusok** lap.  

###  <a name="deploy-the-mac-application"></a>A Mac-alkalmazás központi telepítése  
 A Mac számítógépek számára az alkalmazás központi telepítéséről lépései megegyeznek a lépések Windows rendszerű számítógépekre, az alábbi eltérések kivételével az alkalmazás központi telepítéséről:  

-   A felhasználók számára történő központi alkalmazástelepítés nem támogatott.  

-   Az **Elérhető** céllal rendelkező központi telepítések nincsenek támogatva.  

-   A **előzetes központi telepítés a felhasználó elsődleges eszközén** beállítást a **központi telepítési beállítások** oldalán a **szoftver központi telepítése varázsló** nem támogatott.  

-   Mivel a Mac számítógépek nem támogatják a Szoftverközpont használatát, a **felhasználói értesítések** a a **felhasználói élmény** oldalán a **szoftver központi telepítése varázsló** figyelmen kívül hagyja.  

-   A központi szoftvertelepítés közben történő ébresztésicsomag-küldési beállítás Mac számítógépeken nem támogatott.  

> [!NOTE]  
>  Csak a Mac számítógépeket tartalmazó gyűjteményhez, hozhat létre. Ehhez hozzon létre egy gyűjteményt, amely egy lekérdezési szabályt és használja a mintaként megadott WQL-lekérdezést használja a [lekérdezések létrehozása](../../core/servers/manage/create-queries.md) témakör.  

 További információkért lásd: [telepíthet központilag alkalmazásokat](../../apps/deploy-use/deploy-applications.md).  

###  <a name="step-5-monitor-the-deployment-of-the-mac-application"></a>5. lépés: A Mac-alkalmazás központi telepítésének figyelése  
 Mac számítógépekre alkalmazástelepítések figyeléséről a Windows rendszerű számítógépekre alkalmazástelepítések figyeléséről, ahogyan használhatja ugyanazt a folyamatot.  

 További információkért lásd: [alkalmazások figyeléséhez](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

