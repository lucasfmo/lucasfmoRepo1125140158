---
title: "Virtuális merevlemezek kezelése feladatütemezés használatával |} Microsoft Docs"
description: "Hozzon létre virtuális merevlemez módosítása, alkalmazások és szoftverfrissítések hozzáadása és a virtuális Merevlemezeket közzéteheti a System Center Virtual Machine Manager (VMM) a Configuration Manager alkalmazásból."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0212b023-804a-4f84-b880-7a59cdb49c67
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: f77af4b8fcb193ed44511c0e5eea7290f55dbbf8
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-a-task-sequence-to-manage-virtual-hard-disks-in-system-center-configuration-manager"></a>A System Center Configuration Manager virtuális merevlemezek kezelése feladatütemezés használatával

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben is kezelheti a virtuális merevlemezek (VHD), és integrálhatja az adatközpontjába a Configuration Manager konzolon a létrehozott virtuális merevlemezeket. Pontosabban, létrehozhatják és a virtuális merevlemez módosítása, alkalmazásokat és szoftverfrissítéseket adhat hozzá a virtuális Merevlemezekhez, és a virtuális Merevlemezeket közzéteheti a System Center Virtual Machine Manager (VMM) a Configuration Manager konzoljáról.  

 A következő részekben a Configuration Manager virtuális merevlemezek kezeléséhez.

## <a name="prerequisites"></a>Előfeltételek  
 A művelet elkezdése előtt ellenőrizze a következő előfeltételeket:  

-   A számítógépnek, amelyről a virtuális merevlemezeket kezeli, a következő operációs rendszerek egyikével kell működnie:  

    -   Windows 8.1 x64  

    -   Windows 8 x64  

    -   Windows Server 2008 R2  

    -   Windows Server 2012  

    -   Windows Server 2012 R2  

-   Virtualizációnak engedélyezve kell lennie a BIOS-ban, és a Hyper-V telepítenie kell a Configuration Manager konzol virtuális merevlemezek kezeléséhez futtató számítógépen. Emellett ajánlott telepíteni a Hyper-V kezelőeszközöket is a virtuális merevlemezek tesztelésének és hibaelhárításának megkönnyítéséhez. Ha például az smsts.log fájl figyelésével szeretné nyomon követni a feladatütemezésének előrehaladását, rendelkeznie kell a Hyper-V kezelőeszközök telepített példányával. További információ a Hyper-V használatához kapcsolódó követelményekről: [A Hyper-V telepítésének előfeltételei](http://technet.microsoft.com/library/cc731898.aspx).  

    > [!IMPORTANT]  
    >  A virtuális merevlemez létrehozásának folyamata processzoridő- és memóriaigényes művelet. Ezért ajánlott virtuális merevlemezeket kezeli, amely nincs telepítve a helykiszolgálón a Configuration Manager konzolon.  

-   A helykiszolgálónak **Írás** hozzáférési engedéllyel kell rendelkeznie ahhoz a mappához, amely a VHD-fájlt fogja tartalmazni, amikor a helykiszolgálóhoz képest távoli számítógépről kezeli a virtuális merevlemezeket.  

-   Ellenőrizze, hogy van-e elegendő szabad lemezterület azon a számítógépen, amelyről a virtuális merevlemezeket kezeli. A virtuális merevlemez lemezterület-igénye az operációs rendszertől és a telepített alkalmazásoktól függ.  

-   Ellenőrizze, hogy van-e elegendő memória azon a számítógépen, amelyről a virtuális merevlemezeket kezeli. A virtuális merevlemez létrehozásának folyamata során a virtuális gép 2 GB memória használatára van beállítva.  

-   Telepítse a System Center Virtual Machine Manager (VMM) konzolt arra a számítógépre, amelyről feltölti a virtuális merevlemezt a VMM eszközbe. A VMM konzolt telepítheti a virtuális merevlemezek kezeléséhez használt számítógéptől különböző számítógépre, ami azt jelenti, hogy a virtuális merevlemez VMM eszközbe való importálásához nincs szükség a Hyper-V telepítésére.  

    > [!NOTE]  
    >  Ha a VMM-konzol telepítése a Configuration Manager konzol meg van nyitva, a VMM konzol telepítésének befejeződése után újra kell indítani a Configuration Manager konzolon. Ellenkező esetben a Configuration Manager nem sikeresen csatlakozni a VMM felügyeleti kiszolgálóhoz a virtuális merevlemez feltöltéséhez.  

##  <a name="BKMK_CreateVHDSteps"></a> A virtuális merevlemezek létrehozásának lépései  
 Virtuális merevlemez létrehozásához létre kell hoznia egy feladatütemezést, amely tartalmazza a virtuális merevlemez létrehozásának lépéseit, majd ezt a feladatütemezést kell használnia a Virtuális merevlemez létrehozása varázslóban a virtuális merevlemez létrehozásához. A következő részek ismertetik a virtuális merevlemez létrehozásának lépéseit.  

###  <a name="BKMK_CreateTS"></a> Feladatütemezés létrehozása a virtuális merevlemezhez  
 Létre kell hoznia egy feladatütemezést, amely a virtuális merevlemez létrehozásához szükséges lépéseket fogja tartalmazni. A Feladatütemezés létrehozása varázsló **Meglévő lemezképcsomag telepítése virtuális merevlemezre** funkciójával hozhatja létre a virtuális merevlemez létrehozásához használandó lépéseket. A varázsló például létrehozza a következő kötelező lépéseket: Újraindítás a Windows PE környezetben, Lemez formázása és particionálása, Operációs rendszer alkalmazása és Számítógép leállítása. A teljes operációs rendszer környezetében nem hozhat létre virtuális merevlemezt. Emellett a Configuration Manager alkalmazásnak meg kell várnia a virtuális gép leállását, csak ezután fejezheti be a csomag. A varázsló alapértelmezés szerint 5 perc várakozás után állítja le a virtuális gépet. A feladatütemezés létrehozása után további lépéseket is felvehet, ha szükséges.  

> [!IMPORTANT]  
>  A következő művelet létrehozza a feladatütemezést a **Meglévő lemezképcsomag telepítése virtuális merevlemezre** funkció használatával, amely automatikusan felveszi a virtuális merevlemez sikeres létrehozásához szükséges lépéseket. Ha meglévő feladatütemezés használatát választja, vagy kézzel hozza létre a feladatütemezést, ne feledje, hogy a feladatütemezés végére fel kell vennie a Számítógép leállítása lépést. E lépés nélkül nem törlődik az ideiglenes virtuális gép, és a virtuális merevlemez létrehozásának folyamata nem fejeződik be. A varázsló azonban befejeződik, és sikeresnek jelzi a műveletet.  

 A következő művelet végrehajtásával készítheti el a virtuális merevlemez létrehozásához szükséges feladatütemezést:  

#### <a name="to-create-the-task-sequence-to-create-the-vhd"></a>A virtuális merevlemezt létrehozó feladatütemezés elkészítése  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  Az **Új feladatütemezés létrehozása** lapon kattintson a **Meglévő lemezképcsomag telepítése**lehetőségre, majd kattintson a **Tovább**gombra.  

5.  A **Feladatütemezés adatai** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Feladatütemezés neve**: Adjon meg egy nevet, amely azonosítja a feladatütemezést.  

    -   **Leírás**: Adja meg a feladatütemezés leírását.  

    -   **Rendszerindító lemezkép**: Adja meg a rendszerindító lemezképet, telepíti az operációs rendszert a célszámítógépen. További információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

6.  **A Windows telepítése** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Lemezképcsomag**: Adja meg a telepítendő operációs rendszer lemezképét tartalmazó csomagot.  

    -   **Kép**: Ha az operációs rendszer lemezképcsomagja több lemezképet tartalmaz, adja meg a telepítendő operációs rendszer lemezképét indexét.  

    -   **Termékkulcs**: Adja meg a telepítendő Windows operációs rendszer termékkulcsát. Kódolt mennyiségi licenckulcsot és normál termékkulcsot egyaránt megadhat. Nem kódolt termékkulcs használata esetén mindegyik 5 karakterből álló csoportot kötőjellel (-) kell egymástól elválasztani. Példa: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Kiszolgáló licencelési módja**: Adja meg, hogy a kiszolgálói licenc **Munkaállomásonként**, **kiszolgálónként**, vagy nincs megadva licenc. Ha a kiszolgálói licenc beállítása **Kiszolgálónként**, adja meg a kiszolgálói kapcsolatok maximális számát is.  

    -   Adja meg, hogyan legyen kezelve az operációs rendszer lemezképének telepítésekor használt rendszergazdai fiók.  

        -   **Véletlenszerűen generálja a helyi rendszergazda jelszavát, és tiltsa le a fiókot az összes támogatott platformon (ajánlott)**: Használja ezt a beállítást választva a varázsló véletlenszerűen a helyi rendszergazdai fiók jelszavát, és tiltsa le a fiókot az operációs rendszer lemezképének központi telepítésekor.  

        -   **Engedélyezze a fiókot, és adja meg a helyi rendszergazda jelszavát**: Ez a beállítás segítségével meghatározott jelszót használja a helyi rendszergazdai fiókhoz minden számítógépen, amelyre az operációs rendszer lemezképét telepíti.  

7.  A **Hálózat beállítása** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Csatlakozás munkacsoporthoz**: Adja meg, hogy felvenni a célszámítógépet egy munkacsoporthoz.  

    -   **Csatlakozás tartományhoz**: Adja meg, hogy felvenni a célszámítógépet egy tartományba. A **Tartomány**mezőben adja meg a tartomány nevét.  

        > [!IMPORTANT]  
        >  A helyi erdőben a tartományok megkereséséhez lehetőség van a tallózásra, de távoli erdő esetén be kell írni a tartomány nevét.  

         Lehetőség van szervezeti egység (OU) megadására is. Ez egy nem kötelezően megadandó beállítás, amely annak a szervezeti egységnek az LDAP X.500 szerinti megkülönböztető nevét adja meg, amelyben létre kell hozni a számítógép fiókját, amennyiben az még nem létezik.  

    -   **Fiók**: Adja meg a felhasználónevet és a megadott tartományhoz való csatlakozáshoz engedéllyel rendelkező fiók jelszavát. Például: *tartomány\felhasználó* vagy *%változó%*.  

8.  Az a **Configuration Manager telepítése** adja meg azokat a célszámítógépen telepíteni, és kattintson a Configuration Manager ügyfélcsomag **következő**.  

9. Az **Alkalmazások telepítése** oldalon adja meg a célszámítógépen telepítendő alkalmazásokat, majd kattintson a **Tovább**gombra. Ha több alkalmazást ad meg, lehetősége van a folytatáshoz a feladatsorrendet is megadni, amennyiben egy adott alkalmazást nem sikerült telepíteni.  

10. Fejezze be a varázslót.  

###  <a name="BKMK_CreateVHD"></a> Virtuális merevlemez létrehozása  
 Miután létrehozta a virtuális merevlemez feladatütemezését, a Virtuális merevlemez létrehozása varázsló használatával hozza létre a virtuális merevlemezt.  

> [!IMPORTANT]  
>  Mielőtt elkezdi a műveletet, ellenőrizze, hogy teljesülnek-e a témakör elején felsorolt előfeltételek.  

 Az alábbi eljárással hozhat létre virtuális merevlemezt.  

#### <a name="to-create-a-vhd"></a>Virtuális merevlemez létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Virtuális merevlemezek**elemre.  

3.  A Virtuális merevlemez létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Virtuális merevlemez létrehozása** elemre.  

    > [!NOTE]  
    >  Hyper-V telepítve kell lennie azon a számítógépen, amelyen a Configuration Manager konzolon, ahol a virtuális merevlemezeket kezeli, vagy a **virtuális merevlemez létrehozása** beállítás nincs engedélyezve. További információ a Hyper-V használatához kapcsolódó követelményekről: [A Hyper-V telepítésének előfeltételei](http://technet.microsoft.com/library/cc731898.aspx).  

    > [!TIP]  
    >  A virtuális merevlemezek rendezéséhez hozzon létre egy új mappát, vagy válasszon egy meglévő mappát a **Virtuális merevlemezek** csomópontban, és kattintson a **Virtuális merevlemez létrehozása** elemre a mappánál.  

4.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Név**: Adjon egyedi nevet a virtuális merevlemez.  

    -   **Verzió**: Adja meg a virtuális merevlemez verziószámát. Ez nem kötelező beállítás.  

    -   **Megjegyzés**: Adja meg a virtuális merevlemez leírását.  

    -   **Elérési út**: Adja meg a varázsló által létrehozandó VHD-fájl elérési útját és nevét.  

         Érvényes hálózati elérési utat kell megadnia UNC formátumban. Például:  **\\\servername\\< megosztásnév\>\\< fájlnév\>.vhd**.  

        > [!WARNING]  
        >  Rendelkeznie kell a Configuration Manager **írási** engedéllyel a megadott elérési út a virtuális merevlemez létrehozásához. Ha a Configuration Manager nem tud hozzáférni az elérési út, bejegyzi a kapcsolódó hibát a helykiszolgálón a distmgr.log naplófájlba.  

5.  A **Feladatütemezés** lapon adja meg az előző részben leírtak szerint létrehozott feladatütemezést, és kattintson a **Tovább**gombra.  

6.  A **Terjesztési pontok** oldalon válasszon ki egy vagy több olyan terjesztési pontot, amelynél megtalálható a feladatütemezéshez szükséges tartalom, majd kattintson a **Tovább**gombra.  

7.  A **Testreszabás** lapon kattintson a **Tovább**gombra. A virtuális merevlemez létrehozásának folyamata figyelmen kívül hagyja az ezen a lapon megadott beállításokat.  

8.  Ellenőrizze a beállításokat, és kattintson a **Tovább**gombra. A varázsló létrehozza a virtuális merevlemezt.  

    > [!TIP]  
    >  A virtuális merevlemez létrehozásának befejezése különböző hosszúságú időt vehet igénybe. Amíg a varázsló ezzel a folyamattal van elfoglalva, a következő naplófájlokban figyelheti a folyamat előrehaladását. Alapértelmezés szerint a naplókat a(z) % a Configuration Manager konzolt futtató számítógépen található*ProgramFiles(x86)*%\Microsoft Configuration Manager\AdminConsole\AdminUILog.  
    >   
    >  -   **CreateTSMedia.log**: Amikor létrehozza a feladatütemezés adathordozóját, a varázsló írja az adatokat az ebbe a naplófájlba. Ezt a naplófájl áttekintve követheti nyomon a varázsló által végrehajtott folyamat előrehaladását, amikor létrehozza az önálló adathordozót.  
    > -   **DeployToVHD.log**: Amikor végighalad a virtuális merevlemez létrehozásának folyamata, a varázsló írja az adatokat az ebbe a naplófájlba. Ezt a naplófájlt áttekintve követheti nyomon a varázsló által végrehajtott folyamat egyes lépéseit, miután a varázsló létrehozta az önálló adathordozót.  
    >   
    >  Ezenkívül az operációs rendszer telepítésének elkezdődésekor megnyithatja a Hyper-V Manager alkalmazást (ha telepítette a számítógépre a Hyper-V kezelőeszközöket), és a varázsló által létrehozott ideiglenes virtuális géphez csatlakozva figyelheti a feladatütemezés futását. A virtuális gépről figyelheti az smsts.log naplófájlban a feladatütemezés folyamatának előrehaladását. Ha probléma fordul elő a feladatütemezés valamelyik lépésének végrehajtásakor, ezt a naplófájlt használhatja a probléma megoldásához. Az smsts.log naplófájl helye van, az \windows\temp\smstslog\smsts.log a merevlemez formázása előtt, valamint a c:\\_SMSTaskSequence\Logs\Smstslog\ formázása után. A feladatütemezés lépéseinek végrehajtása után a virtuális gép 5 perc elteltével (alapértelmezés szerint) leáll, és törlődik.  

 Miután a Configuration Manager a virtuális Merevlemezt hoz létre, a található a **virtuális merevlemezek** a Configuration Manager konzolon, a csomópont a **operációs rendszer központi telepítésének** csomópontja a **szoftverkönyvtár** munkaterületen.  

> [!NOTE]  
>  A Configuration Manager a virtuális merevlemez forráshelyéhez csatlakozva kéri le a virtuális merevlemez méretére. Ha a Configuration Manager nem tud hozzáférni a VHD-fájl **0** jelenik meg a **méret (KB)** a virtuális merevlemez oszlop.  

##  <a name="BKMK_ModifyVHDSteps"></a> A meglévő virtuális merevlemezek módosításának lépései  
 A virtuális merevlemezek módosításához létre kell hoznia egy feladatütemezést, amely a virtuális merevlemez módosításának lépéseit tartalmazza. Ezután válassza ki a feladatütemezést a Virtuális merevlemez módosítása varázslóban. A varázsló csatlakoztatja a virtuális merevlemezt a virtuális géphez, futtatja a feladatütemezést a virtuális merevlemezen, majd frissíti a VHD-fájlt. A következő részek ismertetik a virtuális merevlemez módosításának lépéseit.  

###  <a name="BKMK_ModifyTS"></a> Feladatütemezés létrehozása a virtuális merevlemez módosításához  
 Meglévő virtuális merevlemez módosításához első lépésként létre kell hoznia egy feladatütemezést. Ekkor csak azokat a lépéseket adja meg, amelyekre szükség van a feladatütemezés módosításához. Ha például egy alkalmazást szeretne hozzáadni a virtuális merevlemezhez, hozzon létre egy egyéni feladatütemezést, és csak az Alkalmazás telepítése lépést adja hozzá ehhez a feladatütemezéshez.  

 A következő művelet végrehajtásával készítheti el a virtuális merevlemez módosításához szükséges feladatütemezést.  

#### <a name="to-create-a-custom-task-sequence-to-modify-the-vhd"></a>Egyéni feladatütemezés létrehozása a virtuális merevlemez módosításához  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  Az **Új feladatütemezés létrehozása** lapon válassza az **Új egyéni feladatütemezés létrehozása**beállítást, majd kattintson a **Tovább**gombra.  

5.  A **Feladatütemezés adatai** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Feladatütemezés neve**: Adjon meg egy nevet, amely azonosítja a feladatütemezést.  

    -   **Leírás**: Adja meg a feladatütemezés leírását.  

    -   **Rendszerindító lemezkép**: Adja meg a rendszerindító lemezképet, telepíti az operációs rendszert a célszámítógépen. További információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

6.  Fejezze be a varázslót.  

 A következő művelet végrehajtásával vegye fel a szükséges lépéseket az egyéni feladatütemezésbe.  

#### <a name="to-add-task-sequence-steps-to-the-custom-task-sequence"></a>A szükséges lépések hozzáadása az egyéni feladatütemezéshez  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**csomópontot, kattintson a **Feladatütemezések**elemre, és válassza ki az előzőleg létrehozott egyéni feladatütemezést.  

3.  A **Kezdőlap** **Feladatütemezés** csoportjában kattintson a **Szerkesztés** elemre a feladatütemezés-szerkesztő elindításához.  

4.  Adja hozzá a feladatütemezéshez a virtuális merevlemez módosításához használandó lépéseket.  

5.  Kattintson az **OK** gombra a feladatütemezés-szerkesztőből való kilépéshez.  

###  <a name="BKMK_ModifyVHD"></a> Virtuális merevlemez módosítása  
 Miután létrehozta a virtuális merevlemez feladatütemezését, a Virtuális merevlemez módosítása varázsló használatával módosíthatja a virtuális merevlemezt.  

 Az alábbi eljárással módosíthatja a virtuális merevlemezeket.  

#### <a name="to-modify-a-vhd"></a>Virtuális merevlemez módosítása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, kattintson a **Virtuális merevlemezek**elemre, és válassza ki a módosítandó virtuális merevlemezt.  

3.  A **Kezdőlap** **Virtuális merevlemez** csoportjában kattintson a **Virtuális merevlemez módosítása** elemre a Virtuális merevlemez módosítása varázsló elindításához.  

    > [!NOTE]  
    >  Hyper-V telepítve kell lennie azon a számítógépen, amelyen a Configuration Manager konzolon, ahol a virtuális merevlemezeket kezeli, vagy a **virtuális merevlemez módosítása** beállítás nincs engedélyezve. További információ a Hyper-V használatához kapcsolódó követelményekről: [A Hyper-V telepítésének előfeltételei](http://technet.microsoft.com/library/cc731898.aspx).  

4.  Az **Általános** lapon hagyja jóvá a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Név**: Megadja a virtuális merevlemez egyedi nevét.  

    -   **Verzió**: A virtuális merevlemez verziószáma. Ez nem kötelező beállítás.  

    -   **Megjegyzés**: Meghatározza a virtuális merevlemez leírását.  

    -   **Elérési út**: A elérési útját és fájlnevét adja meg, ahol a VHD-fájl található. Ez a beállítás nem módosítható.  

        > [!WARNING]  
        >  Rendelkeznie kell a Configuration Manager **írási** engedéllyel a megadott elérési út a virtuális merevlemez létrehozásához. Ha a Configuration Manager nem tud hozzáférni az elérési út, bejegyzi a kapcsolódó hibát a helykiszolgálón a distmgr.log naplófájlba.  

5.  A **Feladatütemezés** lapon adja meg az előző részben leírtak szerint létrehozott egyéni feladatütemezést, és kattintson a **Tovább**gombra.  

6.  A **Terjesztési pontok** oldalon válasszon ki egy vagy több olyan terjesztési pontot, amelynél megtalálható a feladatütemezéshez szükséges tartalom, majd kattintson a **Tovább**gombra.  

7.  A **Testreszabás** lapon kattintson a **Tovább**gombra. A virtuális merevlemez módosításának folyamata figyelmen kívül hagyja az ezen a lapon megadott beállításokat.  

8.  Ellenőrizze a beállításokat, és kattintson a **Tovább**gombra. A varázsló létrehozza a módosított virtuális merevlemezt.  

    > [!TIP]  
    >  A virtuális merevlemez módosításának befejezése különböző hosszúságú időt vehet igénybe. Amíg a varázsló ezzel a folyamattal van elfoglalva, a következő naplófájlokban figyelheti a folyamat előrehaladását. Alapértelmezés szerint a naplókat a(z) % a Configuration Manager konzolt futtató számítógépen található*ProgramFiles(x86)*%\Microsoft Configuration Manager\AdminConsole\AdminUILog.  
    >   
    >  -   **CreateTSMedia.log**: Amikor létrehozza a feladatütemezés adathordozóját, a varázsló írja az adatokat az ebbe a naplófájlba. Ezt a naplófájl áttekintve követheti nyomon a varázsló által végrehajtott folyamat előrehaladását, amikor létrehozza az önálló adathordozót.  
    > -   **DeployToVHD.log**: Amikor végighalad a virtuális merevlemez módosításának folyamatán, a varázsló írja az adatokat az ebbe a naplófájlba. Ezt a naplófájlt áttekintve követheti nyomon a varázsló által végrehajtott folyamat egyes lépéseit, miután a varázsló létrehozta az önálló adathordozót.  
    >   
    >  Ezenkívül megnyithatja a Hyper-V Manager alkalmazást (ha telepítette a számítógépre a Hyper-V kezelőeszközöket), és a varázsló által létrehozott ideiglenes virtuális géphez csatlakozva figyelheti a feladatütemezés futását. A virtuális gépről figyelheti az smsts.log naplófájlban a feladatütemezés folyamatának előrehaladását. Ha probléma fordul elő a feladatütemezés valamelyik lépésének végrehajtásakor, ezt a naplófájlt használhatja a probléma megoldásához. Az smsts.log naplófájl helye van, az \windows\temp\smstslog\smsts.log a merevlemez formázása előtt, valamint a c:\\_SMSTaskSequence\Logs\Smstslog\ formázása után. A feladatütemezés lépéseinek végrehajtása után a virtuális gép 5 perc elteltével (alapértelmezés szerint) leáll, és törlődik.  

##  <a name="BKMK_ApplyUpdates"></a> Szoftverfrissítések alkalmazása a virtuális merevlemezekre  
 Időnként megjelennek olyan szoftverfrissítések, amelyek alkalmazhatók a virtuális merevlemezen lévő operációs rendszerre. Ezeket az alkalmazható szoftverfrissítéseket a virtuális merevlemezre vonatkozóan egy megadott ütemterv szerint lehet végrehajtani. A megadott ütemezés szerint meg a Configuration Manager végrehajtja a kiválasztott szoftverfrissítéseket a virtuális Merevlemezhez.  

 A virtuális merevlemezre vonatkozó információ, beleértve a virtuális merevlemez létrehozása idején már végrehajtott szoftverfrissítéseket is, a helyadatbázisban tárolódik. A virtuális merevlemez eredeti létrehozása óta alkalmazott szoftverfrissítéseket a rendszer szintén a helyadatbázisban tárolja. A virtuális merevlemez szoftverfrissítését végző varázsló elindításakor lekéri azon alkalmazható szoftverfrissítések listáját, amelyek még nem lettek végrehajtva a kijelölt virtuális merevlemezen.  

 Kiválaszthatja a **Folytatás hiba** kiválasztott beállítást folytathatja a szoftverfrissítések alkalmazását a Configuration Manager frissíti, még akkor is, ha hiba történt egy vagy több szoftvert, hogy mely frissítéseket.  

> [!NOTE]  
>  A szoftverfrissítések a helykiszolgálón lévő tartalomkönyvtárból másolódnak.  

 Kövesse az alábbi lépéseket a szoftverfissítések alkalmazásához virtuális merevlemezekre.  

#### <a name="to-apply-software-updates-to-a-vhd"></a>Szoftverfrissítések alkalmazása a virtuális merevlemezekre  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Virtuális merevlemezek**elemre.  

3.  Jelölje ki a virtuális merevlemezt, amelyre alkalmazni szeretné a szoftverfrissítéseket.  

4.  A varázsló elindításához kattintson a **Kezdőlap** **Virtuális merevlemez** csoportjában a **Frissítések ütemezése** elemre.  

5.  A **Frissítések kiválasztása** oldalon jelölje ki a virtuális merevlemezen végrehajtani kívánt szoftverfrissítéseket, majd kattintson a **Tovább**gombra.  

6.  Az **Ütemezés beállítása** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    1.  **Ütemezés**: Adja meg a ütemezését a szoftverfrissítések hajtson végre a virtuális merevlemezhez.  

    2.  **Folytatás hiba**: Szoftverfrissítések alkalmazása a lemezképen, még akkor is, ha a hiba továbbra is ezt a beállítást.  

7.  Az **Összefoglalás** lapon ellenőrizze az adatokat, majd kattintson a **Tovább**gombra.  

8.  A **Befejezés** lapon ellenőrizze, hogy a szoftverfrissítések alkalmazása sikeresen megtörtént-e az operációs rendszer lemezképén.  

##  <a name="BKMK_ImportToVMM"></a> A virtuális merevlemez importálása a System Center Virtual Machine Manager eszközbe  
 A System Center VMM egy kezelési megoldás a virtualizált adatközponthoz, mely lehetővé teszi a felhasználók számára a virtualizációs állomás, valamint a hálózati és tárolási erőforrások beállítását és kezelését virtuális gépek létrehozásához és telepítéséhez az Ön által korábban létrehozott magánfelhőkre. Miután a virtuális merevlemez létrehozása a Configuration Managerben, importálhatja és kezelheti a VMM-mel.  

> [!TIP]  
>  Mielőtt feltöltene egy virtuális merevlemezt a VMM eszközbe, ellenőrizze, hogy a VMM konzol megfelelően csatlakozik-e a VMM felügyeleti kiszolgálóhoz.  

 Az alábbi eljárással importálhat virtuális merevlemezt a VMM eszközbe.  

#### <a name="to-import-a-vhd-to-vmm"></a>Virtuális merevlemez importálása a VMM eszközbe  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Virtuális merevlemezek**elemre.  

3.  A **Kezdőlapon** a **Virtuális merevlemez** csoportban kattintson a **Feltöltés a Virtual Machine Manager eszközbe** elemre a Virtual Machine Manager varázslóba való feltöltés indításához.  

4.  Az **Általános** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **VMM-kiszolgáló nevét**: Adja meg a számítógép, amelyen telepítve van a VMM felügyeleti kiszolgáló teljes Tartománynevét. A varázsló csatlakozik a VMM felügyeleti kiszolgálóhoz, és letölti onnan a kiszolgálóhoz tartozó könyvtármegosztásokat.  

    -   **VMM-tármegosztást**: Adja meg a VMM könyvtármegosztást a legördülő listából.  

    -   **Titkosítatlan átvitel használata**: Válassza ezt a beállítást, a VHD-fájlt át a VMM felügyeleti kiszolgáló, a rendszer titkosítás nélkül.  

5.  Az Összefoglalás lapon ellenőrizze a beállításokat, majd hajtsa végre a varázsló lépéseit. A VHD-fájl feltöltéséhez szükséges idő a VHD-fájl méretétől és a VMM felügyeleti kiszolgáló hálózati sávszélességétől függően változhat.  

