---
title: "Testre szabhatja a rendszerindító lemezképek - Configuration Manager |} Microsoft Docs"
description: "Ismerje meg a rendszerindító lemezkép testreszabása a Configuration Manager vagy a Deployment Image Servicing and Management (DISM) parancssori eszköz segítségével többféle módon."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cbfc406-d009-446d-8fee-4938de48c919
caps.latest.revision: 15
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: ab2ecb64c9c80b4effed79ba08769c99473db0c4
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="customize-boot-images-with-system-center-configuration-manager"></a>Rendszerindító lemezképek testreszabása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Minden egyes Configuration Manager verziója a Windows Assessment and Deployment Kit (Windows ADK) meghatározott verzióját támogatja. Szolgáltatás, vagy testre rendszerindító lemezképeket a Configuration Manager konzolról, amikor egy Windows ADK támogatott verziójából származó Windows PE-verzión alapulnak. A többi rendszerindító lemezképfájlt más módszerrel kell testre szabnia, például a Windows AIK és a Windows ADK részét képező Deployment Image Servicing and Management (DISM) nevű parancssori eszköz segítségével.  

 A következő biztosít a Windows ADK támogatott verzióit, a Windows PE azon verzióját a rendszerindító lemezkép alapul a Configuration Manager konzoljáról testre szabható és a Windows PE azon verzióit, amelyeken a rendszerindító lemezkép alapul, hogy a DISM segítségével testreszabható, és a Configuration Manager a kép adja.  

-   **Windows ADK-verzió**  

     Windows ADK for Windows 10  

-   **A Configuration Manager konzoljáról testre szabható rendszerindító lemezképekhez használható Windows PE-verziók**  

     Windows PE 10  

-   **A Configuration Manager konzoljáról nem testre szabható rendszerindító lemezképekhez támogatott Windows PE-verziók**  

     Windows PE 3.1<sup>1</sup> és Windows PE 5  

     <sup>1</sup> csak hozzáadhat egy rendszerindító lemezképet a Configuration Manager során, a Windows PE 3.1 rendszeren alapul. Telepítse a Windows AIK Supplement for Windows 7 SP1 szoftvert a Windows AIK for Windows 7 (Windows PE 3) frissítéséhez a Windows AIK Supplement for Windows 7 SP1 (Windows PE 3.1) verzióra. A Windows AIK Supplement for Windows 7 SP1 a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=5188)tölthető le.  

     Például ha a Configuration Manager, testre szabhatja a Windows ADK for Windows 10 (Windows PE 10-alapú) rendszerindító lemezképeket a Configuration Manager konzoljáról. Noha a Windows PE 5 alapú rendszerindító lemezképek támogatottak, egy másik számítógépen kell testre szabnia azokat, és a Windows ADK for Windows 8-cal telepített DISM-verziót kell használnia. Ezt követően a rendszerindító lemezképet is hozzáadhat a Configuration Manager-konzolra.  

 A jelen témakör eljárásai bemutatják, hogyan lehet a választható összetevők a rendszerindító lemezképhez Configuration Manager megköveteli a következő Windows PE-csomagok segítségével:  

-   **WinPE-WMI**: A Windows Management Instrumentation (WMI) támogatást.  

-   **WinPE-Scripting**: A Windows Script Host (WSH) támogatást.  

-   **WinPE-WDS-Tools**: Telepíti a Windows-telepítési szolgáltatások eszközei.  

 Más Windows PE-csomagokat is hozzáadhat. A következő forrásanyagok további információkat nyújtanak a rendszerindító lemezképhez adható, választható összetevőkről.  

-   A Windows PE 5 esetén lásd: [WinPE: Adja hozzá a packages (Optional Components Reference)](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx)  

-   Windows PE 3.1 esetén lásd a [Csomag hozzáadása Windows PE-lemezképhez](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) témakört a Windows 7 TechNet dokumentációs könyvtárában.  

> [!NOTE]
>Amikor olyan testreszabott rendszerindító lemezképről indítja el a WinPE környezetet, amely tartalmazza a hozzáadott eszközöket, a WinPE-ben a kívánt eszköz futtatásához nyisson meg egy parancssort, majd írja be az eszköz fájlnevét. Ezek az eszközök helyét a rendszer automatikusan hozzáadja a path változóban. Csak akkor vehető fel a parancssorba, ha a **parancstámogatás engedélyezése (csak tesztelés)** beállítás ki van választva a **testreszabási** a rendszerindító lemezkép tulajdonságai lapon.

## <a name="customize-a-boot-image-that-uses-windows-pe-5"></a>A Windows PE 5-öt használó rendszerindító lemezkép testreszabása  
 A Windows PE 5-öt használó rendszerindító lemezképek testreszabásához telepítse a Windows ADK-t, és a DISM nevű parancssori eszközzel csatlakoztassa a rendszerindító lemezképet, adja hozzá a választható összetevőket és illesztőprogramokat, majd véglegesítse a rendszerindító lemezképen elvégzett módosításokat. Rendszerindító lemezkép testreszabásához kövesse a következő eljárást.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-5"></a>A Windows PE 5-öt használó rendszerindító lemezkép testreszabása  

1.  A Windows ADK telepítését egy olyan számítógépre, amelyen nincs más verziójú Windows AIK vagy Windows ADK, és nincsen telepítve az összes Configuration Manager összetevőt.  

2.  Töltse le a Windows ADK for Windows 8.1-et a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=39982).  

3.  Másolja a rendszerindító lemezképet (wimpe.wim) a Windows ADK telepítési mappájából (például <*telepítési útvonal*> \Windows Kits\\<*verzió*> \Assessment és Deployment Kit\Windows Preinstallation környezet\\<*x86 vagy amd64*>\\<*területi*>) a számítógépen, amelyről testre fogja szabni a rendszerindító lemezkép célmappába. Ez az eljárás a C:\WinPEWAIK nevet használja a célmappa neveként.  

4.  A DISM segítségével csatlakoztassa a rendszerindító lemezképet egy helyi Windows PE-mappához. Gépelje be például a következő parancssort:  

     **DISM.exe/Mount-Wim /WimFile:C:\WinPEWAIK\winpe.wim/index: 1 /mountdir:C:\WinPEMount**  

     ahol a C:\WinPEWAIK a rendszerindító lemezképet tartalmazó mappa, míg a C:\WinPEMount a csatlakoztatott mappa.  

    > [!NOTE]
    >  A DISM-ről részletesebben lásd a [DISM – A Deployment Image Servicing and Management műszaki ismertetője](http://technet.microsoft.com/library/hh824821.aspx) témakört a Windows 8.1 és a Windows 8 TechNet dokumentációs könyvtárában.

5.  A rendszerindító lemezkép csatlakoztatása után a DISM segítségével adjon választható összetevőket a rendszerindító lemezképhez. A Windows PE 5-ben a 64 bites választható összetevők a következő helyen találhatók: <*telepítési útvonal*>\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs.  

    > [!NOTE]
    >  Ez az eljárás a következő helyet használja a választható összetevőkhöz: C:\Program fájlok (x86) \Windows Kits\8.1\Assessment and Deployment Kit\Windows előtelepítési Environment\amd64\WinPE_OCs. Az Ön által használt elérési út a Windows ADK verziójától és a telepítés közben választott beállításoktól függően eltérhet.  

     A választható összetevők telepítéséhez gépelje be a következőket:  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wmi.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-scripting.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wds-tools.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-SecureStartup.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-SecureStartup_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-WMI_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-Scripting** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<locale\>* **\WinPE-WDS-Tools_** *<locale\>* **.cab"**  

     Ahol a C:\WinPEMount a csatlakoztatott mappa és a területi beállítás az összetevők területi beállítása. Az **en-us** területi beállításhoz például a következőket kell beírni:  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files (x86) \Windows Kits\8.1\Assessment és Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WDS-Tools_en-us.cab"**  

    > [!TIP]
    >  További információért a rendszerindító lemezképhez adható, választható összetevőkről lásd [A Windows PE választható összetevőinek ismertetése](http://technet.microsoft.com/library/hh824926.aspx) témakört a Windows 8.1 és a Windows 8 TechNet dokumentációs könyvtárában.  

6.  Szükség esetén a DISM segítségével adhat meghatározott illesztőprogramokat a rendszerindító lemezképhez. Ha illesztőprogramokat szeretne a rendszerindító lemezképhez adni, gépelje be a következőt:  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:<** *az .inf illesztőprogramfájl elérési útja* **>**  

     „C:\WinPEMount” a csatlakoztatott mappa elérési útja.  

7.  A rendszerindító lemezképfájl leválasztásához és a változások véglegesítéséhez gépelje be a következőt:  

     **DISM.exe/unmount-WIM /mountdir:C:\WinPEMount/Commit**  

     „C:\WinPEMount” a csatlakoztatott mappa elérési útja.  

8.  Adja meg a frissített rendszerindító lemezképet a Configuration Manager számára, hogy használható legyen a feladatütemezésekben. A frissített rendszerindító lemezkép importálásához kövesse az alábbi lépéseket:  

    1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

    2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

    3.  A Rendszerindító lemezkép hozzáadása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Rendszerindító lemezkép hozzáadása** elemre.  

    4.  Az **Adatforrás** oldalon adja meg az alábbi beállításokat, majd kattintson a **Tovább** gombra.  

        -   Az **Elérési út** mezőben adja meg a frissített rendszerindító lemezképfájl elérési útvonalát. A megadott elérési útnak UNC formátumú, érvényes hálózati elérési útnak kell lennie. For example:  **\\\\<***servername***>\\<***WinPEWAIK share***>\winpe.wim**.  

        -   Jelölje ki a rendszerindító lemezképet a **Rendszerindító lemezkép** legördülő listán. Ha a WIM-fájl több rendszerindító lemezképet is tartalmaz, mindegyik lemezkép szerepel a felsorolásban.  

    5.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább** gombra.  

        -   A **Név** mezőbe írjon be egy egyedi nevet a rendszerindító lemezképhez.  

        -   A **Verzió** mezőben adjon meg egy verziószámot a rendszerindító lemezképhez.  

        -   A **Megjegyzés** mezőben adjon meg rövid leírást a rendszerindító lemezkép használatáról.  

    6.  Fejezze be a varázslót.  

9. A rendszerindító lemezképben engedélyezheti a parancsrendszerhéjat a hibakeresés és a Windows PE-ben történő hibaelhárítás érdekében. A parancsrendszerhéj engedélyezéséhez kövesse az alábbi lépéseket.  

    1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

    2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

    3.  Keresse meg az új rendszerindító lemezképet a listában, és keresse meg a lemezkép csomagazonosítóját. A csomagazonosítót a rendszerindító lemezkép **Lemezkép-azonosító** nevű oszlopában találja.  

    4.  A parancssorba gépelje be a **wbemtest** parancsot a Windows Management Instrumentation – tesztelés párbeszédpanel megnyitásához.  

    5.  Type **\\\\<***SMS Provider Computer***>\root\sms\site_<***sitecode***>** in **Namespace**, and then click **Connect**.  

    6.  Kattintson a **Példány megnyitása** lehetőségre, gépelje be az **sms_bootimagepackage.packageID="<csomagazonosító\>"** sort, és kattintson az **OK** gombra. A csomagazonosító helyére a 3. lépésben megkeresett értéket írja.  

    7.  Kattintson az **Objektum frissítése** gombra, majd az **EnableLabShell** lehetőségre a **Tulajdonságok** ablaktáblán.  

    8.  Kattintson a **Tulajdonság szerkesztése** gombra, módosítsa a beállítást **Igaz** értékre, majd kattintson a **Tulajdonság mentése** gombra.  

    9. Kattintson a **Objektum mentése** gombra, és zárja be a Windows Management Instrumentation Testert.  

10. Mielőtt a rendszerindító lemezképet feladatütemezésben használhatná, el kell küldenie azt a terjesztési pontokra, a terjesztésipont-csoportokra vagy a terjesztésipont-csoportokhoz társított gyűjteményekre. A rendszerindító lemezkép terjesztéséhez kövesse az alábbi lépéseket.  

    1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

    2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

    3.  Kattintson a 3. lépésben átmásolt rendszerindító lemezképre.  

    4.  A **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Terjesztési pontok frissítése** elemre.  

## <a name="customize-a-boot-image-that-uses-windows-pe-31"></a>A Windows PE 3.1-et használó rendszerindító lemezkép testreszabása  
 A Windows PE 3.1-et használó rendszerindító lemezkép testreszabásához telepítenie kell a Windows AIK-t, a Windows AIK Supplement for Windows 7 SP1-et, és a DISM nevű parancssori eszköz segítségével csatlakoztatnia kell a rendszerindító lemezképet, fel kell vennie a választható összetevőket és illesztőprogramokat, és véglegesítenie kell a rendszerindító lemezképen elvégzett módosításokat. Rendszerindító lemezkép testreszabásához kövesse a következő eljárást.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-31"></a>A Windows PE 3.1-öt használó rendszerindító lemezkép testreszabása  

1.  A Windows AIK telepíthető olyan számítógépre, amelyen nincs más verziójú Windows AIK vagy Windows ADK, és nincsen telepítve az összes Configuration Manager összetevőt. Töltse le a Windows AIK-t a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=5753).  

2.  Telepítse a Windows AIK Supplement for Windows 7 SP1 szoftvert az 1. lépésben szereplő számítógépre. A Windows AIK Supplement for Windows 7 SP1 a [Microsoft letöltőközpontból](http://www.microsoft.com/download/details.aspx?id=5188) tölthető le.  

3.  Másolja át a rendszerindító lemezképet (wimpe.wim) a Windows AIK telepítési mappájából (például <*TelepítésiÚtvonal*>\Windows AIK\Tools\PETools\amd64\\) annak a számítógépnek az egyik mappájába, amelyikről testre fogja szabni a rendszerindító lemezképet. Ez az eljárás a C:\WinPEWAIK nevet használja mappanévként.  

4.  A DISM segítségével csatlakoztassa a rendszerindító lemezképet egy helyi Windows PE-mappához. Gépelje be például a következő parancssort:  

     **DISM.exe/Mount-Wim /WimFile:C:\WinPEWAIK\winpe.wim/index: 1 /mountdir:C:\WinPEMount**  

     ahol a C:\WinPEWAIK a rendszerindító lemezképet tartalmazó mappa, míg a C:\WinPEMount a csatlakoztatott mappa.  

    > [!NOTE]
    >  A DISM-ről részletesebben lásd [A Deployment Image Servicing and Management műszaki ismertetője](http://technet.microsoft.com/library/dd744256\(v=ws.10\).aspx) témakört a Windows 7 TechNet dokumentációs könyvtárában.  

5.  A rendszerindító lemezkép csatlakoztatása után a DISM segítségével adjon választható összetevőket a rendszerindító lemezképhez. A Windows PE 3.1-ben a választható összetevők például a <*TelepítésiÚtvonal*>\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\ mappában találhatók.  

    > [!NOTE]
    >  Ez az eljárás a következő helyet használja a választható összetevőkhöz: C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs. Az Ön által használt elérési út a Windows AIK verziójától és a telepítés közben választott beállításoktól függően eltérhet.  

     A választható összetevők telepítéséhez gépelje be a következőket:  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wmi.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-scripting.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wds-tools.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<locale\>* **\winpe-wmi_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<locale\>* **\winpe-scripting_** *<locale\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<locale\>* **\winpe-wds-tools_** *<locale\>* **.cab"**  

     Ahol a C:\WinPEMount a csatlakoztatott mappa és a területi beállítás az összetevők területi beállítása. Az **en-us** területi beállításhoz például a következőket kell beírni:  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wmi_en-us.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-scripting_en-us.cab"**  

     **DISM.exe /image:C:\WinPEMount Add-Package PackagePath: "C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wds-tools_en-us.cab"**  

    > [!TIP]
    >  A rendszerindító lemezképhez adható különböző csomagokról lásd a [Csomag hozzáadása Windows PE-lemezképhez](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) témakört a Windows 7 TechNet dokumentációs könyvtárában.  

6.  Szükség esetén a DISM segítségével adhat meghatározott illesztőprogramokat a rendszerindító lemezképhez. Ha illesztőprogramokat szeretne a rendszerindító lemezképhez adni, gépelje be a következőt:  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:<** *az .inf illesztőprogramfájl elérési útja* **>**  

     „C:\WinPEMount” a csatlakoztatott mappa elérési útja.  

7.  A rendszerindító lemezképfájl leválasztásához és a változások véglegesítéséhez gépelje be a következőt:  

     **DISM.exe/unmount-WIM /mountdir:C:\WinPEMount/Commit**  

     „C:\WinPEMount” a csatlakoztatott mappa elérési útja.  

8.  Adja meg a frissített rendszerindító lemezképet a Configuration Manager számára, hogy használható legyen a feladatütemezésekben. A frissített rendszerindító lemezkép importálásához kövesse az alábbi lépéseket:  

    1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

    2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

    3.  A Rendszerindító lemezkép hozzáadása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Rendszerindító lemezkép hozzáadása** elemre.  

    4.  Az **Adatforrás** oldalon adja meg az alábbi beállításokat, majd kattintson a **Tovább** gombra.  

        -   Az **Elérési út** mezőben adja meg a frissített rendszerindító lemezképfájl elérési útvonalát. A megadott elérési útnak UNC formátumú, érvényes hálózati elérési útnak kell lennie. For example:  **\\\\<***servername***>\\<***WinPEWAIK share***>\winpe.wim**.  

        -   Jelölje ki a rendszerindító lemezképet a **Rendszerindító lemezkép** legördülő listán. Ha a WIM-fájl több rendszerindító lemezképet is tartalmaz, mindegyik lemezkép szerepel a felsorolásban.  

    5.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább** gombra.  

        -   A **Név** mezőbe írjon be egy egyedi nevet a rendszerindító lemezképhez.  

        -   A **Verzió** mezőben adjon meg egy verziószámot a rendszerindító lemezképhez.  

        -   A **Megjegyzés** mezőben adjon meg rövid leírást a rendszerindító lemezkép használatáról.  

    6.  Fejezze be a varázslót.  

9. A rendszerindító lemezképben engedélyezheti a parancsrendszerhéjat a hibakeresés és a Windows PE-ben történő hibaelhárítás érdekében. A parancsrendszerhéj engedélyezéséhez kövesse az alábbi lépéseket.  

    1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

    2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

    3.  Keresse meg az új rendszerindító lemezképet a listában, és keresse meg a lemezkép csomagazonosítóját. A csomagazonosítót a rendszerindító lemezkép **Lemezkép-azonosító** nevű oszlopában találja.  

    4.  A parancssorba gépelje be a **wbemtest** parancsot a Windows Management Instrumentation – tesztelés párbeszédpanel megnyitásához.  

    5.  Type **\\\\<***SMS Provider Computer***>\root\sms\site_<***sitecode***>** in **Namespace**, and then click **Connect**.  

    6.  Kattintson a **Példány megnyitása** lehetőségre, gépelje be az **sms_bootimagepackage.packageID="<csomagazonosító\>"** sort, és kattintson az **OK** gombra. A csomagazonosító helyére a 3. lépésben megkeresett értéket írja.  

    7.  Kattintson az **Objektum frissítése** gombra, majd az **EnableLabShell** lehetőségre a **Tulajdonságok** ablaktáblán.  

    8.  Kattintson a **Tulajdonság szerkesztése** gombra, módosítsa a beállítást **Igaz** értékre, majd kattintson a **Tulajdonság mentése** gombra.  

    9. Kattintson a **Objektum mentése** gombra, és zárja be a Windows Management Instrumentation Testert.  

10. Mielőtt a rendszerindító lemezképet feladatütemezésben használhatná, el kell küldenie azt a terjesztési pontokra, a terjesztésipont-csoportokra vagy a terjesztésipont-csoportokhoz társított gyűjteményekre. A rendszerindító lemezkép terjesztéséhez kövesse az alábbi lépéseket.  

    1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

    2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek** pontot, majd kattintson a **Rendszerindító lemezképek** elemre.  

    3.  Kattintson a 3. lépésben átmásolt rendszerindító lemezképre.  

    4.  A **Kezdőlap** **Központi telepítés** csoportjában kattintson a **Terjesztési pontok frissítése** elemre.  

