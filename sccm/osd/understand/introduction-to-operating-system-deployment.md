---
title: "Operációs rendszer központi telepítése – bevezetés |} Microsoft Docs"
description: "Tisztában lennie a fogalmakkal, mielőtt az operációs rendszerek központi telepítése a Configuration Manager környezetben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d9a1c545-8301-492c-832f-2c108ff93c77
caps.latest.revision: 12
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 55a9f1caedcfa810e9a97e43626e4cf5fdbcfa0d
ms.openlocfilehash: 2baa6b7dbd66ab41bc9b67e8f43c313be233153c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-operating-system-deployment-in-system-center-configuration-manager"></a>Operációs rendszer központi telepítése a System Center Configuration Managerben – bevezetés

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager segítségével számos különböző módon az operációs rendszerek központi telepítéséhez. Olvassa el ebben a szakaszban megtudhatja, hogyan operációs rendszerek központi telepítéséhez és a feladatok automatizálásához. 

##  <a name="BKMK_OSDeploymentProcess"></a> Az operációs rendszer központi telepítésének folyamata  
 A Configuration Manager segítségével az operációs rendszer telepítése több módszert kínál. A választott központi telepítési módszertől függetlenül van néhány művelet, amelyet mindenképpen végre kell hajtania:  

-   Azonosítsa azokat a Windows-eszközillesztőket, amelyek szükségesek a rendszerindító lemezkép elindításához, illetve a kívánt operációsrendszer-kép telepítéséhez.  

-   Válassza ki a célszámítógép elindításához használni kívánt rendszerindító lemezképet.  

-   Feladatütemezés segítségével készítsen lemezképet arról az operációs rendszerről, amelyet központilag telepíteni fog. Másik megoldásként használhat alapértelmezett operációsrendszer-képet is.  

-   Küldje el terjesztési pontra a rendszerindító lemezképet, az operációs rendszer lemezképét és a kapcsolódó tartalmakat.  

-   Hozzon létre egy feladatütemezést, amely végrehajtja a rendszerindító lemezkép és az operációs rendszer lemezképének központi telepítését.  

-   Telepítse a feladatütemezést a megfelelő számítógép-gyűjteményre.  

-   Kövesse nyomon a telepítést.  

##  <a name="BKMK_OSDScenarios"></a> Operációs rendszerek központi telepítési forgatókönyvei  
 Nincsenek sok operációsrendszer-telepítési helyzetekben a Configuration Manager olyan közül választhat a környezettől és az operációs rendszer telepítési céljától függően.  Például a meglévő számítógép particionálása és formázása után telepítheti a Windows új verzióját, vagy frissítheti a Windowst a legújabb verzióra. Segítségével meghatározhatja, hogy az üzembe helyezési módszer az igényeinek megfelelő, tekintse át a [a vállalati operációs rendszerek központi telepítésének forgatókönyvei](../deploy-use/scenarios-to-deploy-enterprise-operating-systems.md).  Az operációs rendszer központi telepítésekor a következő forgatókönyvek közül választhat:  

-   [A Windows frissítése a legújabb verzióra](../deploy-use/upgrade-windows-to-the-latest-version.md)  

-   [A Windows új verziójára meglévő számítógép frissítése](../deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](../deploy-use/install-new-windows-version-new-computer-bare-metal.md)  

-   [Meglévő számítógép cseréje és a beállítások átvitele](../deploy-use/replace-an-existing-computer-and-transfer-settings.md)  

##  <a name="BKMK_OSDMethods"></a> Módszerek operációs rendszerek központi telepítésére  
 Több módon is használhatja a Configuration Manager-ügyfélszámítógépek operációs rendszerek központi telepítéséhez.  

-   **PXE Környezetből kezdeményezett központi telepítések**: PXE környezetből kezdeményezett központi telepítések lehetővé teszik az ügyfélszámítógépek kérjenek központi telepítést a hálózaton keresztül. Ennél a központi telepítési módszernél az operációs rendszer lemezképét és egy Windows PE rendszerindító lemezképet kell küldeni egy olyan terjesztési pontra, amely konfigurálva van a PXE rendszerindítási kérelmek fogadására. További információ: [A Windows központi telepítése a hálózaton keresztül PXE segítségével a System Center Configuration Managerben](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

-   **Operációs rendszerek elérhetővé tétele a Szoftverközpontban**: Az operációs rendszerek központi telepítéséhez, és tegye elérhetővé a szoftverközpontban. Configuration Manager-ügyfelek is kezdeményezhető az operációs rendszer telepítése a Szoftverközpontból. További információkért lásd: [meglévő számítógép cseréje és a beállítások átvitele](../deploy-use/replace-an-existing-computer-and-transfer-settings.md).  

-   **Csoportos központi telepítést**: Csoportos központi telepítést hálózati sávszélesség takarítható meg az adatok másolatát küldése minden egyes ügyfélnek külön kapcsolaton keresztül helyett több ügyfélnek egyszerre küldik. Ennél a központi telepítési módszernél az operációs rendszer lemezképét kell elküldeni egy terjesztési pontra. Ez a terjesztési pont hajtja végre a lemezkép központi telepítését, amikor az ügyfélszámítógépek kérik a telepítést. További információkért lásd: [Windows központi telepítése a hálózaton keresztül használjon csoportos](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

-   **Rendszerindító adathordozóról kezdeményezett központi telepítések**: Rendszerindító adathordozóról kezdeményezett központi telepítések lehetővé teszik, hogy az operációs rendszer központi telepítését, a célszámítógép elindításakor. A célszámítógép elindításakor lekéri a hálózatból a feladatütemezést, az operációs rendszer lemezképét és a szükséges egyéb tartalmat. Mivel az adathordozó nem tartalmazza ezt a tartalmat, lehetősége van a tartalom frissítése az adathordozó újbóli létrehozása nélkül. További információkért lásd: [létrehozásának folyamatáról](../deploy-use/create-bootable-media.md).  

-   **Különálló adathordozós telepítések**: Az operációs rendszer különálló adathordozó használatával indított központi telepítéseit a következő feltételek esetében alkalmazhatja:  

    -   Olyan környezetekben, ahol nem célszerű a hálózaton keresztül átmásolni az operációs rendszer lemezképét vagy egyéb nagyméretű csomagokat.  

    -   Olyan környezetekben, ahol nincs hálózati kapcsolat vagy kicsi a hálózati kapcsolat sávszélessége.  

     További információkért lásd: [különálló adathordozó létrehozása](../deploy-use/create-stand-alone-media.md).  

-   **Manuálisan előkészített adathordozóval végrehajtott központi telepítés**: Manuálisan előkészített adathordozóval végrehajtott központi telepítés lehetővé teszik, hogy az operációs rendszer telepítése olyan számítógépre, amelyen nincsenek teljesen kiépítve. A manuálisan előkészített adathordozó egy Windows Imaging Format (WIM) fájl, amelyiket a gyártó, illetve a Configuration Manager környezethez nem csatlakoztatott vállalati előkészítő központ egy operációs rendszer nélküli számítógépen telepítve.  

     Később a Configuration Manager környezetben a számítógép a rendszerindító lemezképet használja az adathordozón elindul, és ezután csatlakozik a helyfelügyeleti ponthoz az elérhető feladatütemezéseket, amelyek befejezik a letöltési folyamatot. Ezzel a módszerrel csökkenthető a hálózati forgalom, mivel a rendszerindító lemezkép és az operációs rendszer lemezképe már a célszámítógépen van. Megadhatók a manuálisan előkészített adathordozóhoz hozzáadni kívánt alkalmazások, csomagok és illesztőprogram-csomagok. További információkért lásd: [hozza létre a manuálisan előkészített adathordozó](../deploy-use/create-prestaged-media.md).  

##  <a name="BKMK_BootImages"></a> Rendszerindító lemezképek  
 A Configuration Manager rendszerindító lemezkép az operációs rendszer központi telepítése során használt Windows PE (WinPE)-lemezképhez. A WinPE-ben a számítógépek rendszerindító lemezképekkel indíthatók el. A WinPE egy olyan minimális méretű operációs rendszer, amely korlátozott összetevőkkel és szolgáltatásokkal készíti elő a célszámítógépet a Windows telepítésére. A Configuration Manager két rendszerindító lemezképet biztosít: Egyik x64 támogatásához, x86 platformokat platformokon. Ezek alapértelmezett rendszerindító lemezképek minősülnek. Hozzon létre, és adja hozzá a Configuration Manager rendszerindító lemezképek egyéni lemezképek minősülnek. Alapértelmezett rendszerindító lemezképek cserélhetők Configuration Manager frissítéskor. További információ a rendszerindító lemezképekről: [A rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

##  <a name="BKMK_OSImages"></a> Operációsrendszer-lemezképek  
 A Configuration Managerben az operációsrendszer-lemezképek tárolása WIM formátumú fájlokban történik, amelyek azoknak a referenciafájloknak és -mappáknak a tömörített gyűjteményét tartalmazzák, amelyekre szükség van az operációs rendszer sikeres telepítéséhez és konfigurációjához a számítógépen. Az operációs rendszerek minden központi telepítési forgatókönyve esetén ki kell választania egy operációsrendszer-lemezképet. Az alapértelmezett operációsrendszer-lemezképet is használhatja, vagy egy Ön által konfigurált referencia-számítógépről is összeállíthatja az operációs rendszer lemezképét. További információkért lásd: [operációsrendszer-lemezképek kezelése](../get-started/manage-operating-system-images.md).  

##  <a name="BKMK_OSUpgradePackages"></a> Operációs rendszer verziófrissítő csomagjai  
 Az operációs rendszer verziófrissítő csomagjai az operációs rendszer frissítésére alkalmasak. Az operációs rendszer központi telepítését ilyen esetben a telepítő kezdeményezi. Importálja az operációs rendszer verziófrissítő csomagjainak a Configuration Manager egy DVD-ről vagy csatlakoztatott ISO-fájl. További információkért lásd: [operációs rendszer verziófrissítő csomagjainak kezelése](../get-started/manage-operating-system-upgrade-packages.md).  

##  <a name="BKMK_OSDMedia"></a> Adathordozók operációs rendszerek központi telepítéséhez  
 Többféle adathordozót is létrehozhat az operációs rendszerek központi telepítéséhez. Ebbe beletartozik a médiarögzítésű adathordozó is, amely az operációs rendszerek központi telepítéséhez használandó operációsrendszer-lemezképek, manuálisan előkészített lemezképek és rendszerindító lemezképek létrehozására használható. Adathordozó használatával telepíthet az operációs rendszerek olyan számítógépekre, amelyik nincs hálózati kapcsolat vagy egy kis sávszélességű kapcsolaton keresztül kell, hogy a Configuration Manager-hely. Adathordozó használatával kapcsolatos további információkért lásd: [feladatütemezési média létrehozása](../deploy-use/create-task-sequence-media.md).  

##  <a name="BKMK_DeviceDrivers"></a> Eszközillesztők  
 Az eszközillesztőket úgy is telepítheti a célszámítógépeken, hogy nem adja hozzá őket a telepítendő operációs rendszer rendszerképéhez. A Configuration Manager biztosít egy illesztőprogram-katalógust, amely az összes Configuration Manager alkalmazásba importálható eszközillesztők hivatkozásait tartalmazza. Az illesztőprogram-katalógusban található a **szoftverkönyvtár** munkaterület és a következő két csomópontot tartalmazza: **Illesztőprogramok** és **illesztőprogram-csomagok**. Az **Illesztőprogramok** csomópontban található az illesztőprogram-katalógusba importált összes illesztőprogram listája. Ebben a csomópontban áttekintheti az egyes importált illesztőprogramok adatait, megváltoztathatja azt, hogy az egyes illesztőprogramok melyik rendszerindító lemezképhez vagy illesztőprogram-csomaghoz tartoznak, engedélyezheti és letilthatja az illesztőprogramokat stb. További információkért lásd: [kezelheti az illesztőprogramokat](../get-started/manage-drivers.md).  

##  <a name="BKMK_OSDUserState"></a> Felhasználói állapot mentése és visszaállítása  
 Az operációs rendszerek központi telepítésekor mentheti a felhasználói állapotot a célszámítógépről, majd az operációs rendszer központi telepítésének végrehajtása után visszaállíthatja a felhasználói állapotot a célszámítógépen. A műveletet rendszerint akkor használhatja, amikor az operációs rendszer telepítése a Configuration Manager-ügyfélszámítógépen.  

 A felhasználói állapot adatai feladatütemezések használatával rögzíthetők és állíthatók helyre. A rögzített felhasználói állapot adatai a következő módszerek egyikével állíthatók vissza:  

-   A felhasználó állapot adatait tárolhatja távoli helyen egy állapotáttelepítési pont konfigurálásával. A Rögzítés feladatütemezés elküldi az adatokat az állapotáttelepítési pontra. Az operációs rendszer központi telepítésének végrehajtása után pedig a Visszaállítás feladatütemezés lekéri az adatokat, és helyreállítja a felhasználói állapotot a célszámítógépen.  

-   A felhasználó állapot adatait tárolhatja helyben. Ebben az esetben a Rögzítés feladatütemezés a célszámítógép megadott helyére másolja a felhasználói adatokat. Az operációs rendszer központi telepítésének végrehajtása után a Visszaállítás feladatütemezés erről a helyről kéri le a felhasználói adatokat.  

-   Megadhat rögzített hivatkozásokat, amelyek használatával az eredeti helyükre állíthatja vissza a felhasználói adatokat. Ebben az esetben a felhasználói állapot adatai a meghajtón maradnak a régi operációs rendszer eltávolításakor. Az operációs rendszer központi telepítésének végrehajtása után a Visszaállítás feladatütemezés a rögzített hivatkozások használatával állítja vissza a felhasználói állapot adatait az eredeti helyükre.  

 További információ [felhasználói állapot kezelése](../get-started/manage-user-state.md).  

##  <a name="BKMK_UnknownComputer"></a> Központi telepítés ismeretlen számítógépekre  
 Az operációs rendszer telepítene a Configuration Manager által nem kezelt számítógépekre. Nincs rekord ezekhez a számítógépekhez a Configuration Manager adatbázisába. Az ilyen számítógépekre ismeretlen számítógépként hivatkozunk. Az ismeretlen számítógépek a következők:  

-   Egy számítógép, amelyen nincs telepítve a Configuration Manager-ügyfél  

-   Olyan számítógép, amely nincs importálva a Configuration Managerbe  

-   Olyan számítógép, amely nem észlelhető a Configuration Manager által  

 További információkért lásd: [Ismeretlen számítógépek központi telepítésének előkészítéséhez](../get-started/prepare-for-unknown-computer-deployments.md).  

##  <a name="BKMK_UDA"></a> Felhasználók társítása számítógépekhez  
 Amikor operációs rendszer központi telepítését hajtja végre, a felhasználókat összekapcsolhatja a célszámítógéppel a felhasználó-eszköz kapcsolatot igénylő műveletek támogatásához. Amikor hozzárendel egy felhasználót a célszámítógéphez, a rendszergazda a későbbiekben a felhasználóhoz rendelt bármelyik számítógépen végrehajthat olyan műveleteket, mint például az alkalmazások központi telepítése meghatározott felhasználó számítógépére. Amikor azonban operációs rendszer központi telepítését végzi, az operációs rendszert nem telepítheti meghatározott felhasználó számítógépére. További információkért lásd: [rendelje hozzá a felhasználókat a célszámítógéppel](../get-started/associate-users-with-a-destination-computer.md).  

##  <a name="BKMK_TaskSequences"></a> Feladatütemezések használata a lépések automatizálásához  
 A Configuration Manager környezetben feladatokat különféle feladatütemezéseket hozhat létre. A feladatütemezés által végrehajtott műveletek az ütemezés lépései között definiálhatók. A feladatütemezés futtatásakor a rendszer minden egyes lépést végrehajt parancssori szinten, felhasználói beavatkozás nélkül. A feladatütemezések a következőkre használhatók:  

-   [Hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md)  

-   [Hozzon létre egy feladatütemezést az operációs rendszer központi telepítése](../deploy-use/create-a-task-sequence-for-non-operating-system-deployments.md)  

-   [Hozzon létre egy feladatütemezést az operációs rendszer rögzítéséhez](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md)  

-   [Felhasználói állapot rögzítéséhez és visszaállításához a feladatütemezés létrehozása](../deploy-use/create-a-task-sequence-to-capture-and-restore-user-state.md)  

-   [Egyéni feladatütemezés létrehozása](../deploy-use/create-a-custom-task-sequence.md)  

