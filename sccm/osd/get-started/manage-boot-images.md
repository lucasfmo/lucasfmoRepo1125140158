---
title: "Rendszerindító lemezképek - Configuration Manager kezelése |} Microsoft Docs"
description: "A Configuration Managerben bemutatják, hogyan kezelheti a Windows PE rendszerindító lemezképek, operációsrendszer-telepítés során használt."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
caps.latest.revision: 23
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0cf2ac6440588ccf4848baa7a195f78e8675447d
ms.openlocfilehash: c6a1eb9ccaee45eb242fb320cb6b492d1a39d349
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-boot-images-with-system-center-configuration-manager"></a>Rendszerindító lemezképek kezelése a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager rendszerindító lemezkép van egy [Windows PE (WinPE)](https://msdn.microsoft.com/library/windows/hardware/dn938389%28v=vs.85%29.aspx) egy operációs rendszer központi telepítése során használt kép. A WinPE-ben a számítógépek rendszerindító lemezképekkel indíthatók el. A WinPE egy olyan minimális méretű operációs rendszer, amely korlátozott összetevőkkel és szolgáltatásokkal készíti elő a célszámítógépet a Windows telepítésére.  A következő részekben a rendszerindító lemezképek kezeléséhez.

## <a name="BKMK_BootImageDefault"></a>Alapértelmezett rendszerindító lemezképek
A Configuration Manager két alapértelmezett rendszerindító lemezképet biztosít: Egyik x64 támogatásához, x86 platformokat platformokon. Ezeket a lemezképeket tárolja: \\ \\ *kiszolgálónév*> \SMS_ <*Helykód*> \osd\boot\\<*x64*> vagy <*i386*>. Az alapértelmezett rendszerindító lemezképek frissítése, vagy attól függően, hogy az elvégzendő újragenerálása.

**Frissítések és karbantartás a Configuration Manager legújabb verziójának telepítéséhez** 1702 verziójától kezdve, amikor a Windows ADK-verzió frissítése, és kövesse a frissítések és karbantartás a Configuration Manager legújabb verziójának telepítése a Configuration Manager újragenerálja az alapértelmezett rendszerindító lemezképeket. Ez magában foglalja a új Windows PE verziót a frissített Windows ADK, az új verziót a Configuration Manager-ügyfél, illesztőprogramok, testreszabások, stb. Egyéni rendszerindító lemezképeket nem módosulnak.

Verzió 1702, mielőtt a Configuration Manager frissíti a meglévő rendszerindító lemezképet (boot.wim) az ügyfél összetevők, illesztőprogramok, testreszabások, stb., de nem fogja használni a Windows ADK a legújabb Windows PE verziót. Manuálisan módosítania kell a rendszerindító lemezképet használja a Windows ADK új verziója.

**Frissítés a Configuration Manager 2012 a Configuration Manager aktuális ág (CB)** Configuration Manager 2012 Configuration Manager CB frissíti a telepítési folyamat használatával, ha a Configuration Manager művelettel újragenerálja az alapértelmezett rendszerindító lemezképeket. Ez magában foglalja a frissített a Windows ADK, a Configuration Manager-ügyfél új verziójának új Windows PE verziót, és minden egyéni változatlanok maradnak. Egyéni rendszerindító lemezképeket nem módosulnak.

**Terjesztési pontok frissítése a rendszerindító lemezképpel** használata esetén a **terjesztési pontok frissítése** művelet a **rendszerindító lemezképek** csomópontot a Configuration Manager konzolon, a Configuration Manager az alapértelmezett rendszerindító lemezképek frissíti az ügyfél összetevők, illesztőprogramok, testreszabások, stb., de nem fogja használni a Windows ADK a legújabb Windows PE verziót. Egyéni rendszerindító lemezképeket nem módosulnak.

Is fontolja meg a fenti műveletek a következők:
- A forrás illesztőprogram-objektumoknak érvényes, beleértve az illesztőprogram forrásfájljainak, vagy az illesztőprogramok nem lesz felvéve a rendszerindító lemezképekhez a helyen kell lennie.
- Az alapértelmezett rendszerindító lemezképeket, nem alapuló, még akkor is, ha használják a ugyanazon a Windows PE azon verzióját, rendszerindító lemezképek nem módosulnak.
- A módosított rendszerindító lemezképeket a terjesztési pontokra kell terjesztenie.
- A módosított rendszerindító lemezképeket használó adathordozókat újra létre kell hoznia.
- Ha nem szeretné, hogy a testre szabott/alapértelmezett rendszerindító lemezképek automatikusan frissüljenek, tárolja őket az alapértelmezett helyen.

> [!NOTE]
> A Configuration Manager nyomkövetési napló eszköz bekerül minden rendszerindító lemezképbe felvett a **szoftverkönyvtár**. Ha a Windows PE környezetben, megkezdheti írja be a Configuration Manager nyomkövetési napló eszköz **CMTrace** a parancssorból.  

##  <a name="BKMK_BootImageCustom"></a>Rendszerindító lemezkép testreszabása  
 Testre szabhatja a rendszerindító lemezképet, vagy [a rendszerindító lemezképek módosításával](#BKMK_ModifyBootImages), a Configuration Manager konzolról, amikor egy Windows ADK támogatott verziójából származó Windows PE-verzión alapul. Amikor egy helyet új verzióval frissít, és a Windows ADK új verziója települ, a rendszer az egyéni rendszerindító lemezképeket (amelyek nem az alapértelmezett rendszerindító lemezképek helyén találhatók) nem frissíti a Windows ADK új verziójával. Ebben az esetben nem kell a Configuration Manager konzolon a rendszerindító lemezképek testreszabhatók. a lemezképek ugyanakkor ugyanúgy fognak működni, mint a frissítés előtt.  

 Amikor egy adott rendszerindító lemezkép a helyen telepített Windows ADK-tól eltérő verzión alapul, akkor más módszerrel kell testreszabnia a rendszerindító lemezképeket, például a Windows AIK és a Windows ADK részét képező Deployment Image Servicing and Management (DISM) nevű parancssori eszköz segítségével. További információkért lásd: [rendszerindító lemezképek testreszabása](customize-boot-images.md).  

##  <a name="BKMK_AddBootImages"></a>Rendszerindító lemezkép hozzáadása  

 Hely telepítése során a Configuration Manager automatikusan hozzáadja a Windows ADK támogatott verziójából származó Windows PE-verzión alapuló rendszerindító lemezképeket. Attól függően, hogy a Configuration Manager verziója valószínűleg egy másik, a Windows ADK támogatott verziójából származó Windows PE-verzión alapuló rendszerindító lemezképek hozzáadására.  Ha a Windows PE nem támogatott verzióját tartalmazó rendszerindító lemezképet próbál meg hozzáadni, hiba történik.  

 A következő szakasz a Windows ADK támogatott verzióit, a Windows PE azon verzióját a rendszerindító lemezkép alapul a Configuration Manager konzoljáról testre szabható és a Windows PE azon verzióit, amelyeken a rendszerindító lemezkép alapul, hogy a DISM segítségével testreszabható, és ezután hozzáadhatja a lemezképet a Configuration Manager tartalmaz.  

-   **Windows ADK-verzió**  

     Windows ADK for Windows 10  

-   **A Configuration Manager konzoljáról testre szabható rendszerindító lemezképekhez használható Windows PE-verziók**  

     Windows PE 10  

-   **A Configuration Manager konzoljáról nem testre szabható rendszerindító lemezképekhez támogatott Windows PE-verziók**  

     Windows PE 3.1<sup>1</sup> és Windows PE 5  

     <sup>1</sup> csak hozzáadhat egy rendszerindító lemezképet a Configuration Manager során, a Windows PE 3.1 rendszeren alapul. Telepítse a Windows AIK Supplement for Windows 7 SP1 szoftvert a Windows AIK for Windows 7 (Windows PE 3) frissítéséhez a Windows AIK Supplement for Windows 7 SP1 (Windows PE 3.1) verzióra. A Windows AIK Supplement for Windows 7 SP1 a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=5188)tölthető le.  

     Például ha a Configuration Manager, testre szabhatja a Windows ADK for Windows 10 (a Windows PE 10-alapú) rendszerindító lemezképeket a Configuration Manager konzoljáról. Noha a Windows PE 5 alapú rendszerindító lemezképek támogatottak, egy másik számítógépen kell testre szabnia azokat, és a Windows ADK for Windows 8-cal telepített DISM-verziót kell használnia. Ezt követően a rendszerindító lemezképet is hozzáadhat a Configuration Manager-konzolra. További információ a lépésekről, amelyekkel testre szabhatja a rendszerindító lemezképeket (választható összetevők és illesztőprogramok hozzáadása), engedélyezheti a parancstámogatást a rendszerindító lemezképhez, hozzáadhatja a rendszerindító lemezképet a Configuration Manager konzolt, és a terjesztési pontokat frissíteni a rendszerindító lemezképet, lásd: [rendszerindító lemezképek testreszabása](customize-boot-images.md).

 A következő eljárással adhat hozzá rendszerindító lemezképet manuálisan.  

#### <a name="to-add-a-boot-image"></a>Rendszerindító lemezkép hozzáadása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

3.  A Rendszerindító lemezkép hozzáadása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Rendszerindító lemezkép hozzáadása** elemre.  

4.  Az **Adatforrás** oldalon adja meg az alábbi beállításokat, majd kattintson a **Tovább** gombra.  

    -   Az **Elérési út** mezőben adja meg a rendszerindító lemezkép WIM-fájljának elérési útvonalát.  

         A megadott elérési útnak UNC formátumú, érvényes hálózati elérési útnak kell lennie. For example: \\\\<*servername*\\<*sharename*>\\<*bootimagename*>.wim.  

    -   Jelölje ki a rendszerindító lemezképet a **Rendszerindító lemezkép** legördülő listán. Ha a WIM-fájl több rendszerindító lemezképet is tartalmaz, válassza ki a megfelelő lemezképet.  

5.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább** gombra.  

    -   A **Név** mezőbe írjon be egy egyedi nevet a rendszerindító lemezképhez.  

    -   A **Verzió** mezőben adjon meg egy verziószámot a rendszerindító lemezképhez.  

    -   A **Megjegyzés** mezőben adjon meg rövid leírást a rendszerindító lemezkép használatáról.  

6.  Fejezze be a varázslót.  

 A rendszerindító lemezkép megjelenik a **rendszerindító lemezkép** csomópont a Configuration Manager konzol. Mielőtt azonban a rendszerindító lemezképet operációs rendszer központi telepítéséhez használhatná, a rendszerindító lemezképet el kell juttatnia terjesztési pontokra, terjesztésipont-csoportokra vagy terjesztésipont-csoportokhoz társított gyűjteményekbe.  

> [!NOTE]  
>  Ha bejelöli a **rendszerindító lemezkép** csomópont a Configuration Manager konzolon a **méret (KB)** oszlopában láthatók az egyes rendszerindító lemezképek kibontott mérete. Azonban a Configuration Manager rendszerindító lemezképet a hálózaton keresztül küldi el, amikor egy tömörített példányát küldi a képet, általában sokkal kisebb, mint szerepel a **méret (KB)** oszlop.  

##  <a name="BKMK_DistributeBootImages"></a>Rendszerindító lemezképek terjesztési pontra történő terjesztése  
 A rendszerindító lemezképek terjesztése ugyanúgy történik a terjesztési pontokra, mint más tartalmaké. A legtöbb esetben az operációs rendszer központi telepítéséhez és adathordozók létrehozásához legalább egy terjesztési pontra el kell juttatnia a rendszerindító lemezképet.  

> [!NOTE]  
>  Ha a PXE környezettel szeretné elvégezni egy operációs rendszer központi telepítését, vegye figyelembe a következőket a rendszerindító lemezkép terjesztése előtt:  
>   
>  -   A terjesztési pontnak konfigurálva kell lennie a PXE-kérelmek fogadásához.  
> -   Egy x86-os és egy x64-es PXE-kompatibilis rendszerindító lemezképet is el kell juttatnia legalább egy PXE-kompatibilis terjesztési pontra.  
> -   A Configuration Manager továbbítja a rendszerindító lemezképet a **RemoteInstall** a PXE-képes terjesztési pont mappájába.  
>   
>  Operációs rendszerek központi telepítése a PXE használatával kapcsolatos további információkért lásd: [PXE használatával a Windows központi telepítése a hálózaton keresztül](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Rendszerindító lemezkép terjesztésére vonatkozó lépésekért lásd: [Tartalom terjesztése](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_ModifyBootImages"></a>Rendszerindító lemezkép módosítása  
 Eszközillesztőket adhat hozzá a lemezképhez vagy távolíthat el abból, illetve szerkesztheti a rendszerindító lemezképhez társított tulajdonságokat. A hozzáadott vagy eltávolított eszközillesztők lehetnek például hálózati adapterek vagy háttértár-illesztőprogramok. A rendszerindító lemezképek módosításakor a következő tényezőket kell figyelembe venni:  

-   Ahhoz, hogy eszközillesztőket adhasson hozzá a rendszerindító lemezképhez, azokat importálni és engedélyezni kell az illesztőprogram-katalógusban.  

-   Rendszerindító lemezkép módosításakor a rendszerindító lemezkép által hivatkozott társított csomagok nem változnak meg.  

-   Miután változtatásokat hajtott végre egy rendszerindító lemezképen, **frissítenie** kell a rendszerindító lemezképet azokon a terjesztési pontokon, amelyeken már megtalálható, hogy a rendszerindító lemezkép legújabb verziója legyen elérhető. További információ: [Manage content you have distributed](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkmanagea-manage-the-content-you-have-distributed) (Terjesztett tartalom kezelése).  

 Az alábbi eljárással módosíthat egy rendszerindító lemezképet.  

#### <a name="to-modify-the-properties-of-a-boot-image"></a>Rendszerindító lemezkép tulajdonságainak módosítása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

3.  Jelölje ki a módosítani kívánt rendszerindító lemezképet.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok** gombra az adott rendszerindító lemezképhez tartozó **Tulajdonságok** párbeszédpanel megnyitásához.  

5.  A rendszerindító lemezkép működésének módosításához adja meg a következő beállítások bármelyikét:  

    -   Ha a rendszerindító lemezkép tulajdonságait külső eszköz használatával módosította, a **Lemezképek** lapon kattintson az **Újrabetöltés** gombra.  

    -   Az **Illesztőprogramok** lapon vegye fel a WinPE rendszerindításához szükséges Windows-eszközillesztőket. Az eszközillesztők hozzáadásakor vegye figyelembe a következőket:  

        -   Válassza ki **a rendszerindító lemezkép architektúrájának nem megfelelő illesztőprogramok elrejtése** megjelenítendő csak a rendszerindító lemezkép architektúrájának illesztőprogramjait. Az architektúra a gyártó által az .INF fájlban ismertetett architektúrán alapul.  

        -   Jelölje be a **Nem tárolási vagy hálózati osztályban található illesztőprogramok elrejtése (rendszerindító lemezképek esetén)** beállítást, hogy csak a tárolási és hálózati illesztőprogramok jelenjenek meg, elrejtve a rendszerindító lemezképek esetén általában nem szükséges alkalmazásokat, például a video- vagy modem-illesztőprogramokat.  

        -   Jelölje be a **Digitális aláírás nélküli illesztőprogramok elrejtése** beállítást a digitális aláírással nem rendelkező illesztőprogramok elrejtéséhez.  

        -   Ajánlott eljárásként elegendő a hálózati adapterek és a háttértárak illesztőprogramjait felvenni a rendszerindító lemezképbe, kivéve ha követelmény, hogy a WinPE más illesztőprogramokat is tartalmazzon.  

        -   Mivel a WinPE eleve számos beépített illesztőprogramot tartalmaz, csak azon hálózati adapterek és háttértárak illesztőprogramját vegye fel, amelyeket a Windows PE nem biztosít.  

        -   Ügyeljen arra, hogy a rendszerindító lemezképbe felvett illesztőprogramok megfeleljenek a rendszerindító lemezkép architektúrájának.  

        > [!NOTE]  
        >  Rendszerindító lemezképbe való felvételük előtt az eszközillesztőket importálnia kell az illesztőprogramok katalógusába. Eszközillesztők importálása kapcsolatos információkért lásd: [kezelheti az illesztőprogramokat](manage-drivers.md).  

    -   A **Testreszabás** lapon jelölje be a következő beállítások bármelyikét:  

        -   Jelölje be az **Indítás előtti parancsok engedélyezése** négyzetet a feladatütemezés előtt futtatni kívánt parancs megadásához. Ha az indítás előtti parancsok engedélyezve vannak, megadhatja a futtatni kívánt parancssort, megadhatja, hogy a parancs futtatásához szükségesek-e támogatófájlok, és ha igen, ezeknek a fájloknak a forráshelyét.  

            > [!WARNING]  
            >  A **cmd /c** karakterláncot hozzá kell adni a parancssor elejéhez. Ha nem adja meg a **cmd /c** karakterláncot, a parancssor a futtatás után nem fog bezáródni. A központi telepítés ebben az esetben várakozni fog a parancs befejezésére, és nem fogja elkezdeni a többi konfigurált parancsot vagy műveletet.  

            > [!TIP]  
            >  Feladatütemezési média létrehozásakor a a feladatütemezés írja a Csomagazonosítót és az előindítási parancssort, beleértve a feladatütemezési változók, a Configuration Manager konzolt futtató számítógépen a CreateTSMedia.log naplófájlba értékét. Ebben a naplófájlban ellenőrizheti a feladatütemezési változók értékét.  

        -   A **Windows PE háttér** beállításainak megadásával határozza meg, hogy a Windows PE alapértelmezett hátterét vagy egy egyéni hátteret szeretne használni.  

        -   Jelölje be a **Parancstámogatás engedélyezése (csak tesztelés)** beállítást a parancssor **F8** billentyűvel végzett megnyitásához a rendszerindító lemezkép központi telepítésekor. Ez hasznos a központi telepítés tesztelésekor a hibaelhárításnál. Éles központi telepítési környezetben a beállítás használata nem javasolt.  

        -   Konfigurálja a Windows PE ideiglenes területet, amely a WinPE által használt ideiglenes tárhely (RAM-meghajtó). Például amikor egy alkalmazás fut a WinPE környezetben, és ideiglenes fájlok írására van szüksége, a WinPE egy merevlemez jelenlétének szimulálásához átirányítja ezeket a fájlokat a memóriában található ideiglenes területre. A WinPE alapértelmezés szerint az írható memória 32 MB méretű területét foglalja le.  

    -   Az **Adatforrás** lapon módosítsa a következő beállítások bármelyikét:  

        -   Állítsa be a **Lemezkép elérési útja** és a **Lemezképindex** beállításokat a rendszerindító lemezkép forrásfájljának módosításához.  

        -   Jelölje be a **Terjesztési pontok ütemezett frissítése** beállítást egy, a rendszerindító lemezkép frissítéséhez tartozó ütemezés létrehozásához.  

        -   Jelölje be a **Tartalom megőrzése az ügyfél gyorsítótárában** beállítást, ha nem szeretné, hogy a csomag tartalma elévüljön az ügyfél gyorsítótárában, amikor más tartalmaknak kell helyet biztosítani.  

        -   Jelölje be a **Bináris különbözeti replikáció engedélyezése** beállítást annak megadásához, hogy a rendszer csak a megváltozott fájlokat terjessze a rendszerindító lemezképcsomag a terjesztési ponton való frissítésekor. Ez a beállítás jelentősen csökkenti a helyek közötti hálózati adatforgalmat, különösen akkor, ha a rendszerindító lemezképcsomag mérete nagy, és a változások viszonylag csekély mértékűek.  

        -   Jelölje be **A rendszerindító lemezkép központi telepítése a PXE-képes terjesztési pontról** beállítást, ha a rendszerindító lemezképet PXE-képes központi telepítésben használja.  

            > [!NOTE]  
            >  További információkért lásd: [PXE használatával a Windows központi telepítése a hálózaton keresztül](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   Az **Adatelérés** lapon válassza a következő beállítások bármelyikét:  

        -   Adja meg a **Csomagmegosztási beállítások** értékeit, ha azt szeretné, hogy az ügyfelek a hálózatról telepítsék a csomag tartalmát.  

        -   Állítsa be a **csomag frissítési beállítások** határozza meg, hogyan felhasználók leválasztása a terjesztési pontot a Configuration Manager számára. Lehet, hogy a Configuration Manager nem tudja frissíteni a rendszerindító lemezképet, ha felhasználók csatlakoznak a terjesztési pontra.  

    -   A **Terjesztési beállítások** lapon válassza a következő beállítások bármelyikét:  

        -   Az a **terjesztési prioritás** listában, adja meg a prioritási szintet, amelyet a Configuration Manager használata, amikor több csomagot küld ugyanarra a terjesztési pontra.  

        -   Jelölje be **A csomag tartalmának terjesztése az előnyben részesített terjesztési pontokra** beállítást, ha engedélyezni szeretné az igény szerinti tartalomterjesztést az előnyben részesített terjesztési pontokra. Ha ez a beállítás engedélyezve van, a felügyeleti pont az összes előnyben részesített terjesztési pontra terjeszti a tartalmat, amikor egy ügyfél a csomaghoz tartozó tartalmat igényel, és a tartalom nem áll rendelkezésre egyetlen előnyben részesített terjesztési ponton sem.  

        -   Adja meg a **Manuálisan előkészített terjesztési pontok beállításai** értékeit annak meghatározásához, hogyan szeretné küldeni a rendszerindító lemezképet olyan terjesztési pontokra, amelyeknél engedélyezve van a manuálisan előkészített tartalom.  

            > [!NOTE]  
            >  További információ az előkészített tartalmakról: [Tartalom előkészítése](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkprestagea-use-prestaged-content).  

    -   A **Tartalom helye** lapon jelölje ki a terjesztési pontot vagy a terjesztésipont-csoportot, és hajtsa végre a következők közül a megfelelő műveletet:  

        -   Kattintson a **Továbbterjesztés** elemre a rendszerindító lemezkép újbóli terjesztéséhez a kijelölt terjesztési pontra vagy terjesztésipont-csoportra.  

        -   Kattintson az **Érvényesítés** elemre a rendszerindító lemezképcsomag sértetlenségének ellenőrzéséhez a kijelölt terjesztési ponton vagy terjesztésipont-csoporton.  

    -   Az a **választható összetevők** lapra, adja meg az összetevőket, amelyek a Windows PE-Lemezképhez hozzáadott Configuration Managerrel történő használathoz. További információ a rendelkezésre álló választható összetevőkről: [WinPE: Adja hozzá a packages (Optional Components Reference)](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx).  

    -   A **Biztonság** lapon jelöljön ki egy rendszergazdát, és módosítsa az általa végrehajtható műveleteket.  

6.  A tulajdonságok beállítása után kattintson az **OK** gombra.  

##  <a name="BKMK_BootImagePXE"></a>Rendszerindító lemezkép központi telepítése a PXE-képes terjesztési pontról konfigurálása  
 A rendszerindító lemezkép PXE-t támogató operációs rendszer központi telepítésére való használata előtt konfigurálnia kell a rendszerindító lemezképet egy PXE-képes terjesztési pontról történő központi telepítésre.  

#### <a name="to-configure-a-boot-image-to-deploy-from-a-pxe-enabled-distribution-point"></a>Rendszerindító lemezkép konfigurálása a PXE-t támogató terjesztési pontról való központi telepítéshez  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

3.  Jelölje ki a módosítani kívánt rendszerindító lemezképet.  

4.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok** gombra az adott rendszerindító lemezképhez tartozó **Tulajdonságok** párbeszédpanel megnyitásához.  

5.  Az **Adatforrás** lapon válassza **A rendszerindító lemezkép központi telepítése a PXE-képes terjesztési pontról** lehetőséget.  

    > [!NOTE]  
    >  További információkért lásd: [PXE használatával a Windows központi telepítése a hálózaton keresztül](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

6.  A tulajdonságok beállítása után kattintson az **OK** gombra.  

##  <a name="BKMK_BootImageLanguage"></a>Rendszerindító lemezkép központi telepítéséhez több nyelv konfigurálása  
 A rendszerindító lemezképek nyelvsemlegesek. Ez lehetővé teszi, hogy a WinPE környezetben egyetlen rendszerindító lemezképen különböző nyelveken jelenítse meg a feladatütemezést, amennyiben hozzáadja az adott nyelvek támogatását a Windows PE választható összetevői közül, illetve a feladatütemezés megfelelő változójának beállításával megadja a megjeleníthető nyelveket. A központilag telepített operációs rendszer nyelve nem függ össze a Configuration Manager verziójától függetlenül a WinPE környezetben megjelenített nyelvvel. A felhasználónak megjelenített nyelv meghatározása a következőképpen történik:  

-   Amikor egy felhasználó futtatja a feladatütemezést egy meglévő operációs rendszerből, a Configuration Manager automatikusan a felhasználóhoz beállított nyelvet használja. Ha a feladatütemezés automatikusan fut egy kötelező telepítési határidő miatt, a Configuration Manager az operációs rendszer nyelvét használja.  

-   Az operációs rendszerek PXE vagy adathordozó használatával végrehajtott telepítésekor az SMSTSLanguageFolder változóban állíthatja be a nyelv azonosító értékét, egy indítás előtti parancs részeként. Amikor a számítógép a WinPE környezetben indul el, az üzenetek a változóban megadott nyelven jelennek meg. Ha nem sikerül hozzáférni a nyelvi erőforrásfájlhoz a megadott mappában, vagy nem állítja be a változót, az üzenetek a WinPE nyelvén jelennek meg.  

    > [!NOTE]  
    >  Ha az adathordozó jelszavas védelemmel van ellátva, a jelszót kérő üzenet mindig a WinPE nyelvén jelenik meg.  

 Az alábbiak végrehajtásával állíthatja be a WinPE nyelvét operációs rendszerek PXE vagy adathordozó használatával kezdeményezett központi telepítései esetében.  

#### <a name="to-set-the-windows-pe-language-for-a-pxe-or-media-initiated-operating-system-deployment"></a>A Windows PE nyelvének beállítása operációs rendszerek PXE vagy adathordozó használatával kezdeményezett telepítésekor  

1.  Győződjön meg arról, hogy a megfelelő feladatütemezési erőforrásfájl (tsres.dll) a megfelelő nyelvi mappában van a helykiszolgálón, mielőtt frissíti a rendszerindító lemezképet. Az angol nyelvű erőforrásfájl például a következő helyen található: <*ConfigMgrtelepítésimappája*>\OSD\bin\x64\00000409\tsres.dll.  

2.  Az indítás előtti parancs részeként az SMSTSLanguageFolder környezeti változót állítsa a megfelelő nyelvi azonosítóra. A nyelvi azonosítót decimális, nem pedig hexadecimális értékként kell megadni. Ha például angolra szeretné állítani a nyelvi változót, az 1033 decimális értéket kell megadnia a mappanévben használt 00000409 hexadecimális érték helyett.  

