---
title: "Hozzon létre és telepítsen egy alkalmazást |} Microsoft Docs"
description: "Hozzon létre és telepítsen egy alkalmazást egy sor üzleti alkalmazást tartalmazó, és megtudhatja, hogyan hatékonyan kezelheti az alkalmazásokat."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6516db6f4c09fdd173b498c58ccc411847752c4e
ms.openlocfilehash: bbbf278f5d31c51bfe061dd44e170f7ab1ca70ad
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-and-deploy-an-application-with-system-center-configuration-manager"></a>Alkalmazás létrehozása és központi telepítése a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ebben a témakörben bemutatjuk ugrani, hozzon létre egy alkalmazást a System Center Configuration Managerrel. Ebben a példában, akkor hozhat létre, és telepítsen egy alkalmazást, amely tartalmazza egy sor üzleti alkalmazás nevű **Contoso.msi**, telepíteni kell a vállalat Windows 10 operációs rendszert futtató összes számítógépeken. Menet megtanulhatja, számos, az alkalmazások hatékony kezelésében is van.  

 Ez az eljárás célja, hogy áttekintést, létrehozása és központi telepítése a Configuration Manager-alkalmazásokkal. Azonban nem terjed ki a konfigurációs beállítások, vagy hozzon létre és telepíthet központilag alkalmazásokat más platformokra.  

 Részletes, amely kapcsolódik a minden egyes platformhoz tekintse meg a következő témakörök egyikét:  

-   [Windows-alkalmazások létrehozása](../../apps/get-started/creating-windows-applications.md)  
-   [IOS-alkalmazások létrehozása](../../apps/get-started/creating-ios-applications.md)  
-   [Az Android-alkalmazások létrehozása](../../apps/get-started/creating-android-applications.md)  
-   [Windows Phone-alkalmazások létrehozása](../../apps/get-started/creating-windows-phone-applications.md)  
-   [Mac számítógépekhez készült alkalmazások létrehozása](../../apps/get-started/creating-mac-computer-applications.md)  
-   [Linux és UNIX kiszolgálók alkalmazásainak létrehozása](../../apps/get-started/creating-linux-and-unix-server-applications.md)
-   [Windows Embedded-alkalmazások létrehozása](../../apps/get-started/creating-windows-embedded-applications.md)


Ha már ismeri a Configuration Manager-alkalmazásokkal, kihagyhatja az ebben a témakörben. Azonban érdemes áttekinteni [alkalmazásokat](../../apps/deploy-use/create-applications.md) tájékozódhat az összes a rendelkezésre álló lehetőségek létrehozása és központi telepítésekor az alkalmazást.  

## <a name="before-you-start"></a>Előkészületek  

Győződjön meg arról, hogy már olvasta található információk [Alkalmazáskezelés bemutatása](/sccm/apps/understand/introduction-to-application-management) , hogy készítse elő a helyet az alkalmazások telepítéséhez, és hogy tudomásul veszi, hogy a jelen témakörben használt terminológiával.  

 Győződjön meg arról, hogy a telepítési fájlokat is, a **Contoso.msi** app a hálózaton elérhető helyen vannak.  

## <a name="create-the-configuration-manager-application"></a>A Configuration Manager-alkalmazás létrehozása  

### <a name="to-start-the-create-application-wizard-and-create-the-application"></a>Alkalmazás létrehozása varázsló elindítása és az alkalmazás létrehozása  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **alkalmazás létrehozása**.  

4.  Az a **általános** oldalán a **alkalmazás létrehozása varázsló**, válassza a **a telepítési fájlokból az alkalmazás adatainak automatikus észlelése**. Ez előtti tölti fel néhány információt, hogy a rendszer kiolvassa a .msi fájlt a varázsló információt. Majd adja meg a következőket:  

    -   **Típus**: Válasszon **Windows Installer (\*.msi fájlt)**.  

    -   **Hely**: Adja meg az elérési utat (vagy válasszon **Tallózás** a hely kijelöléséhez) telepítőfájl **Contoso.msi**. Vegye figyelembe, hogy a helyét a formában kell megadni  *\\\Server\Share\File* megtalálja a telepítőfájlokat, hogy a Configuration Manager.  

    Akkor lesz végül, amelyet az alábbi képernyőfelvételen a következőképpen néz:  

    ![Alkalmazás kezelése varázsló Általános lap](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  

5.  Válasszon **következő**. Az a **importálási adatok** lapján megjelenik néhány adat az alkalmazásról és a kapcsolódó fájlokat, a Configuration Manager importált. Ha elkészült, válassza ki a **következő** újra.  

6.  Az a **általános információkat** lapon adhat meg további információkat az alkalmazás rendezésében és azonosításában a Configuration Manager konzol segítségével.  

     Emellett a **telepítőprogram** mező lehetővé teszi, hogy adja meg a teljes parancssort az alkalmazás telepítésére a számítógépeken használható. Szerkesztheti a saját tulajdonságok kiegészítheti (például **/q** felügyelet nélküli telepítéshez).  

    > [!TIP]  
    >  Előfordulhat, hogy az alkalmazás telepítőfájljainak importálásakor a rendszer már automatikusan kitöltötte a lap egyes mezőit.  

     Az alábbi képernyőfelvételhez hasonló képernyő lesz végül:  

     ![Alkalmazás felügyeleti varázslólap általános információk](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  

7.  Válasszon **következő**. Az Összegzés lapon ellenőrizze az alkalmazás beállításait, és fejezze be a varázslót.  

 Ezzel az alkalmazás létrehozása befejeződött. A található, a **szoftverkönyvtár** munkaterületet, bontsa ki **Alkalmazáskezelés**, és válassza a **alkalmazások**. Az alkalmazás a következőképpen jelenik meg:  

 ![Végső app kép](/sccm/apps/get-started/media/Final-app-graphic.png)  

## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>Vizsgálja meg az alkalmazás és a központi telepítési típus tulajdonságait  

Most, hogy létrehozott egy alkalmazást, pontosíthatja az alkalmazás beállításait, ha szeretné. Tekintse meg az alkalmazás tulajdonságait, válassza ki az alkalmazást, majd a a **Home** lapján a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

 Az a **< Contoso\> alkalmazástulajdonságok** párbeszédpanelen konfigurálhatja az alkalmazás működésének pontosítsa számos elem megjelenik. Az összes konfigurálható beállításokkal kapcsolatos részletekért lásd: [alkalmazásokat](../../apps/deploy-use/create-applications.md). A jelen példában csak az alkalmazás központi telepítési típusának néhány tulajdonságát módosítjuk.  

 Válassza ki a **központi telepítési típusok** lapon > **Contoso alkalmazást** központi telepítési típus > **szerkesztése**.     

Ekkor az alábbihoz hasonló párbeszédpanel fog megjelenni:  

![Alkalmazás felügyeleti alkalmazás tulajdonságai lap](/sccm/apps/get-started/media/App-management-app-properties-page.png)  

## <a name="add-a-requirement-to-the-deployment-type"></a>Követelmény hozzáadása a központi telepítési típushoz  
 A követelmények olyan feltételeket határoznak meg, amelyeknek teljesülniük kell ahhoz, hogy az alkalmazást telepíteni lehessen egy eszközön.  Beépített követelmények közül választhat, vagy létrehozhat saját. Ebben a példában adjon hozzá egy követelményt, hogy az alkalmazás csak get telepítve a Windows 10 rendszert futtató számítógépeken.  

1.  A központi telepítési típus tulajdonságai lapon imént megnyitott, válassza ki a **követelmények** fülre.  

2.  Válasszon **Hozzáadás** megnyitásához a **követelmény létrehozása** párbeszédpanel megnyitásához.  

3.  A **Követelmény létrehozása** párbeszédpanelen adja meg a következő információkat:  

    -   **Kategória**: **Eszköz**  

    -   **Az állapot**: **Operációs rendszer**  

    -   **Szabály típusa**: **Érték**  

    -   **Operátor**: **Egyik**  

    -   Az operációs rendszerek listáján válassza a **Windows 10**lehetőséget.  

    Ekkor a következőhöz hasonló párbeszédpanel jelenik meg:  

    ![Felügyeleti követelmények oldalra](/sccm/apps/get-started/media/App-management-requirements-page.png)  

4.  Válasszon **OK** minden megnyitott tulajdonságlap bezárása. Ezután térjen vissza a **alkalmazások** lista a Configuration Manager konzolon.  

> [!TIP]  
>  Követelményekkel csökkenthető van szüksége a Configuration Manager-gyűjtemények száma. Mivel az imént beállította, hogy az alkalmazás csak Windows 10 rendszert futtató számítógépeken beolvasása telepítve, később központilag telepítheti az olyan gyűjteményhez, amely számos különböző operációs rendszert futtató számítógépet tartalmaz. De az alkalmazás csak get telepítve a Windows 10 rendszerű számítógépeken.  

## <a name="add-the-application-content-to-a-distribution-point"></a>Az alkalmazástartalom hozzáadása terjesztési ponthoz  

Az alkalmazás számítógépekre telepíteni, győződjön meg róla, hogy az alkalmazás tartalmának másolását egy terjesztési pontra. Számítógépek hozzáférni a terjesztési pont, az alkalmazás telepítéséhez.  

> [!TIP]  
>  Terjesztési pontok és a Configuration Manager tartalomkezelési kapcsolatos információért lásd: [tartalom és tartalomkezelési infrastruktúra kezelése](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár**.  

2.  Az a **szoftverkönyvtár** munkaterületet, bontsa ki a **alkalmazások**. Ezt követően az alkalmazások listájában válassza a **Contoso alkalmazást** létrehozott.  

3.  Az a **Home** lap a **telepítési** csoportjában válassza **tartalom terjesztése**.  

4.  Az a **általános** oldalán a **tartalom terjesztése varázsló**, ellenőrizze, hogy az alkalmazás neve helyesen-e, és válassza a **következő**.  

5.  Az a **tartalom** lapján tekintse át az információkat, amelyek a terjesztési pontra lesznek másolva, és válassza a **következő**.  

6.  Az a **tartalom cél** lapon, válassza ki **Hozzáadás** jelölje be egy vagy több terjesztési pontokat vagy terjesztésipont-csoportok az alkalmazástartalom telepítéséhez.  

7.  Fejezze be a varázslót.  

Ellenőrizheti, hogy az alkalmazástartalmat sikeresen másolta-e a terjesztési pontot a **figyelés** munkaterületen, a **terjesztés állapota** > **Tartalomállapot**.  

## <a name="deploy-the-application"></a>Az alkalmazás központi telepítése  

Ezután telepítse az alkalmazást egy eszközgyűjteménybe a hierarchiában. Ebben a példában az alkalmazást telepít központilag a **minden rendszer** eszközgyűjteményt.  

> [!TIP]  
>  Ne feledje, hogy csak Windows 10-es számítógépekre telepíti az alkalmazást, amely a korábban kiválasztott követelmények miatt.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazások**.  

3.  Az alkalmazások listájában jelölje ki a korábban létrehozott alkalmazás (**Contoso alkalmazást**), majd a a **Home** lapra a **telepítési** csoportjában válassza **telepítés**.  

4.  A a **általános** oldalán a **szoftver központi telepítése varázsló**, válassza a **Tallózás** jelölje be a **minden rendszer** eszközgyűjteményt.  

5.  Az a **tartalom** lapján ellenőrizze, hogy van-e jelölve a terjesztési pont, amelyből el kívánja számítógépekre telepíteni az alkalmazást.  

6.  Az a **központi telepítési beállítások** lapon, győződjön meg arról, hogy a központi telepítés céljának beállítása **telepítése**, és a központi telepítési céllal van megadva **szükséges**.  

    > [!TIP]  
    >  A központi telepítés célja értékre állításával **szükséges**, akkor győződjön meg arról, hogy az alkalmazás telepítve van-e a számítógépek megfelelnek az Ön által beállított követelményeknek. Ha ez az érték **Elérhető**, a felhasználók igény szerint telepíthetik az alkalmazást a Szoftverközpontból.  

7.  Az **Ütemezés** lapon megadhatja az alkalmazás telepítésének idejét. Ebben a példában válassza **Az elérhetőséget követően amint lehet**beállítást.  

8.  Az a **felhasználói élmény** lapon, válassza ki **következő** az alapértelmezett értékeit elfogadásához.  

9. Fejezze be a varázslót.  

Olvassa el a következő **az alkalmazás figyelése** szakaszban az alkalmazás központi telepítésének állapotát tekintheti meg.  

## <a name="monitor-the-application"></a>Az alkalmazás figyelése  
 Ebben a szakaszban az imént telepített alkalmazás központi telepítési állapotának gyorsan át lesz igénybe vehet.  

### <a name="to-review-the-deployment-status"></a>A központi telepítés állapotának áttekintése  

1.  Kattintson a Configuration Manager konzol **figyelés** > **központi telepítések**.  

3.  Válassza ki a központi telepítések listájáról a **Contoso alkalmazást**.  

4.  Az a **Home** lap a **telepítési** csoportjában válassza **állapotának megtekintése**.  

5.  Válasszon egyet a következő lapokon az alkalmazás telepítésére vonatkozó további állapotfrissítések megtekintéséhez:  

    -   **Sikeres**: Az alkalmazás telepítése sikeresen megtörtént a jelzett számítógépeken.  

    -   **A folyamatban lévő**: Az alkalmazás még nem fejeződött be telepítése.  

    -   **Hiba**: Hiba történt a jelzett számítógépeken az alkalmazás telepítése. A hibával kapcsolatos további információk is láthatók.  

    -   **Nem teljesített követelmények**: Nincs telepítési kísérlet történt a jelzett eszközökre, mert nem feleltek meg a beállított követelményeinek (ebben a példában, mivel azok nem futnak Windows 10).  

    -   **Ismeretlen**: A Configuration Manager szolgáltatás nem tudta jelenteni a központi telepítés állapotát. Próbálkozzon újra később.  

> [!TIP]  
>  Néhány módon figyelheti az alkalmazások központi telepítéseit. Teljes részletekért lásd: [alkalmazások figyeléséhez](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

## <a name="end-user-experience"></a>Végfelhasználói élmény  

Configuration Manager és a Windows 10-es futó felügyelt számítógépeken rendelkező felhasználók látják, egy üzenet arról, hogy telepíteniük kell a Contoso alkalmazást. Amint elfogadják a telepítést, az alkalmazást telepíti.  

