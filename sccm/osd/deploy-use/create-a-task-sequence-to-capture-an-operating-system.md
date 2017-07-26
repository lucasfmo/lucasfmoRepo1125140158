---
title: "Hozzon létre egy feladatütemezést az operációs rendszer rögzítéséhez |} Microsoft Docs"
description: "Összeállítása és rögzítése feladatütemezés egy referencia-számítógép, amely tartalmazza az adott illesztőprogramok és a szoftverfrissítéseket az operációs rendszer együtt alkot."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25e4ac68-0e78-4bbe-b8fc-3898b372c4e8
caps.latest.revision: 19
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: e9320e40b8e5031ffa3da5e5149c7da718cc87d5
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-to-capture-an-operating-system-in-system-center-configuration-manager"></a>Hozzon létre egy feladatütemezést, rögzítheti egy operációs rendszer a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Feladatütemezés egy operációs rendszer központi telepítését egy számítógépre a System Center Configuration Manager használatakor a számítógép telepíti az operációs rendszer lemezképét a feladatütemezésben megadott. Az operációs rendszer lemezképének testreszabásához – hogy adott illesztőprogramokat, alkalmazásokat, szoftverfrissítéseket stb. tartalmazzon – elkészítési feladatütemezés használatával összeállít egy referencia-számítógépet, majd arról a számítógépről rögzíti az operációs rendszer lemezképét. Ha már rendelkezik egy telepíthető referencia-számítógéppel, létrehozhat egyéni feladatütemezést az operációs rendszer rögzítéséhez. A következő szakaszok segítségével rögzíthet egyéni operációs rendszert.  

##  <a name="BKMK_BuildCaptureTS"></a> Referencia-számítógép elkészítése feladatütemezés használatával  
 Az elkészítési feladatütemezés particionálja és formázza a referencia-számítógépet, telepíti az operációs rendszer, valamint a Configuration Manager-ügyfél, alkalmazások és szoftverek frissítések, és majd rögzíti az operációs rendszer a referencia-számítógépről. A feladatütemezéssel társított csomagoknak, például az alkalmazásoknak a terjesztési pontokon elérhetőknek kell lenniük, mielőtt létrehozná az elkészítési feladatütemezést.  

###  <a name="BKMK_CreatePackages"></a> Operációs rendszerek telepítésének előkészítése  
 Az operációs rendszerek telepítése számos forgatókönyv szerint végezhető a környezetében. A legtöbb esetben létrehoz egy feladatütemezést, és bejelöli a **Meglévő lemezképcsomag telepítése** választógombot a Feladatütemezés létrehozása varázslóban az operációs rendszer, a szoftverfrissítések és alkalmazások telepítéséhez, valamint a felhasználói beállítások áttelepítéséhez. Mielőtt feladatütemezést hozna létre az operációs rendszer telepítéséhez, az alábbiakról kell gondoskodni:  

-   **Kötelező**  

    -   A [rendszerindító lemezkép](../get-started/manage-boot-images.md) a Configuration Manager konzol elérhetőnek kell lennie.  

    -   Egy [operációsrendszer-lemezkép](../get-started/manage-operating-system-images.md) a Configuration Manager konzol elérhetőnek kell lennie.  

-   **Kötelező (használat esetén)**  

    -   [Illesztőprogram-csomagok](../get-started/manage-drivers.md) , amelyik tartalmazza a szükséges Windows-illesztőprogramok a referencia-számítógép hardverének támogatásához a Configuration Manager konzol elérhetőnek kell lennie. A feladatütemezési lépések kezelheti az illesztőprogramokat kapcsolatos további információkért lásd: [eszközillesztők telepítése feladatütemezések használatával](../get-started/manage-drivers.md#BKMK_TSDrivers).  

    -   [Szoftverfrissítések](../../sum/get-started/synchronize-software-updates.md) szinkronizálni kell a Configuration Manager konzolon.  

    -   [Alkalmazások](../../apps/deploy-use/create-applications.md) fel kell venni a Configuration Manager konzolon.  

###  <a name="BKMK_CreateBuildCaptureTS"></a> Elkészítési feladatütemezés létrehozása  
 A következő eljárással feladatütemezés segítségével összeállíthat egy referencia-számítógépet, és rögzítheti az operációs rendszert.  

#### <a name="to-create-a-task-sequence-that-builds-and-captures-an-operating-system-image"></a>Operációsrendszer-kép készítésére és rögzítésére szolgáló feladatütemezés létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  Az **Új feladatütemezés létrehozása** lapon kattintson **A referencia operációs rendszer lemezképének elkészítése**lehetőségre.  

5.  A **Feladatütemezés adatai** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Feladatütemezés neve**: Adjon meg egy nevet, amely azonosítja a feladatütemezést.  

    -   **Leírás**: Adja meg a az operációs rendszer a feladatütemezés által létrehozott például a feladatütemezés által végrehajtandó feladat leírását.  

    -   **Rendszerindító lemezkép**: Adja meg a rendszerindító lemezképet, telepíti az operációs rendszer lemezképét.  

        > [!IMPORTANT]  
        >  A rendszerindító lemezkép architektúrájának kompatibilisnek kell lennie a célszámítógép hardverarchitektúrájával.  

6.  **A Windows telepítése** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Lemezképcsomag**: Adja meg az operációs rendszer lemezképének csomagját, amely az operációs rendszer telepítéséhez szükséges fájlokat tartalmazza.  

    -   **Lemezképindex**: Adja meg az operációs rendszer telepítéséhez. Ha az operációs rendszer lemezképe több verziót tartalmaz, válassza ki a telepíteni kívánt verziót.  

    -   **Termékkulcs**: Adja meg a telepítendő Windows operációs rendszer termékkulcsát. Kódolt mennyiségi licenckulcsot és normál termékkulcsot egyaránt megadhat. Nem kódolt termékkulcs használata esetén mindegyik 5 karakterből álló csoportot kötőjellel (-) kell egymástól elválasztani. Példa: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Kiszolgáló licencelési módja**: Adja meg, hogy a kiszolgálói licenc **Munkaállomásonként**, **kiszolgálónként**, vagy nincs megadva licenc. Ha a kiszolgálói licenc beállítása **Kiszolgálónként**, adja meg a kiszolgálói kapcsolatok maximális számát is.  

    -   Adja meg, hogyan legyen kezelve az operációs rendszer telepítésekor használt rendszergazdai fiók.  

        -   **Véletlenszerűen generálja a helyi rendszergazda jelszavát, és tiltsa le a fiókot az összes támogatott platformon**: Adja meg, hogy a Configuration Manager hozzon létre egy véletlenszerű jelszót a helyi rendszergazdai fiókhoz, és tiltsa le a fiókot az operációs rendszer központi telepítésekor.  

        -   **Engedélyezze a fiókot, és adja meg a helyi rendszergazda jelszavát**: Adja meg, hogy ugyanazt a jelszót a helyi rendszergazdai fiókhoz minden számítógépen van használni, amelyikre az operációs rendszer telepítve lesz.  

7.  A **Hálózat beállítása** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Csatlakozás munkacsoporthoz**: Adja meg, hogy felvenni a célszámítógépet egy munkacsoporthoz, az operációs rendszer központi telepítésekor.  

    -   **Csatlakozás tartományhoz**: Adja meg, hogy felvenni a célszámítógépet egy tartományba az operációs rendszer központi telepítésekor. A **Tartomány**mezőben adja meg a tartomány nevét.  

        > [!IMPORTANT]  
        >  A helyi erdőben a tartományok megkereséséhez lehetőség van a tallózásra, de távoli erdő esetén be kell írni a tartomány nevét.  

         Lehetőség van szervezeti egység (OU) megadására is. Ez egy nem kötelezően megadandó beállítás, amely annak a szervezeti egységnek az LDAP X.500 szerinti megkülönböztető nevét adja meg, amelyben létre kell hozni a számítógép fiókját, amennyiben az még nem létezik.  

    -   **Fiók**: Adja meg a felhasználónevet és a megadott tartományhoz való csatlakozáshoz engedéllyel rendelkező fiók jelszavát. Például: *tartomány\felhasználó* vagy *%változó%*.  

        > [!IMPORTANT]  
        >  Ha a tartománybeállítások vagy a munkacsoport-beállítások áttelepítését tervezi, meg kell adnia az érvényes tartományi hitelesítő adatokat.  

8.  Az a **Configuration Manager telepítése** csoportjában adja meg a Configuration Manager-ügyfélcsomag, a Configuration Manager-ügyfél telepítéséhez adja hozzá a szükséges szükséges az ügyfél telepítéséhez, majd kattintson a tulajdonságokat a forrásfájlokat tartalmazó **következő**.  

     További információ a ügyfelek telepítéséhez használható tulajdonságokról: [vonatkozó ügyfél-telepítési tulajdonságok](../../core/clients/deploy/about-client-installation-properties.md).  

9. A **Frissítésekkel együtt** lapon adja meg, hogy milyen szoftverfrissítéseket szeretne telepíteni: a szükséges szoftverfrissítéseket, minden szoftverfrissítést, vagy egyet sem; azután kattintson a **Tovább**gombra. Ha a szoftverfrissítések telepítését választja, a Configuration Manager csak azokat a frissítéseket, amelyek telepíti a gyűjteményeket, amelyek a célszámítógép a tagja legyen.  

10. Az **Alkalmazások telepítése** oldalon adja meg a célszámítógépen telepítendő alkalmazásokat, majd kattintson a **Tovább**gombra. Ha több alkalmazást ad meg, lehetősége van a folytatáshoz a feladatsorrendet is megadni, amennyiben egy adott alkalmazást nem sikerült telepíteni.  

11. A **Rendszer-előkészítés** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Csomag**: Adja meg a Configuration Manager-csomagot, amely tartalmazza a referencia-számítógép beállításainak rögzítéséhez a Sysprep megfelelő verzióját.  

         Windows Vista vagy későbbi operációs rendszer esetén a Sysprep automatikusan telepítve van a számítógépen, és nem kell csomagot megadni.  

12. A **Lemezkép tulajdonságai** lapon adja meg a következő beállításokat az operációs rendszer lemezképe számára, majd kattintson a **Tovább**gombra.  

    -   **Által létrehozott**: Adja meg az operációs rendszer lemezképét létrehozó felhasználó neve.  

    -   **Verzió**: Adjon meg egy felhasználó által meghatározott verziószámot, amely az operációs rendszer lemezképéhez tartozik.  

    -   **Leírás**: Adja meg az operációs rendszer lemezképének felhasználói leírását.  

13. A **Lemezkép rögzítése** lapon adja meg a következő beállításokat, majd kattintson a **Tovább**gombra.  

    -   **Elérési út**: Megadhat egy megosztott hálózati mappát, ahová a kimeneti. WIM-fájlban tárolja. Ez a fájl tartalmazza az operációsrendszer-képet, amely a varázsló segítségével megadott beállítások szerint jön létre. Ha a megadott mappában már van egy .WIM fájl, a rendszer felülírja a meglévő fájlt.  

    -   **Fiók**: Adja meg a Windows-fiókot, amelyik eléri a lemezképet tároló hálózati megosztást.  

14. Fejezze be a varázslót.  

15. A feladatütemezés további lépéseinek megadásához jelölje ki a létrehozott feladatütemezést, és kattintson a **Szerkesztés**elemre. A feladatütemezés szerkesztésével kapcsolatos információkért lásd: [a feladatütemezések szerkesztésével](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 A feladatütemezés telepítése a referencia-számítógépen az alábbi módszerek valamelyikével:  

-   Ha a referencia-számítógépen a Configuration Manager-ügyfél, hajtsa végre az, és rögzítheti a feladatütemezést a referencia-számítógépet tartalmazó gyűjteményen. Az operációs rendszer lemezképének telepítésével kapcsolatos információkért lásd: [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](create-a-task-sequence-to-install-an-operating-system.md).  

    > [!NOTE]  
    >  Ha a feladatütemezéshez lemezparticionálási lépés tartozik, a feladatütemezés végrehajtásakor ne adja meg a **Program letöltése** beállítást.  

-   Ha a referencia-számítógép nincs a Configuration Manager-ügyfél, vagy ha szeretné manuálisan futtatja a feladatütemezést a referencia-számítógépen, futtassa a **feladatütemezési média létrehozása varázsló** rendszerindító adathordozó létrehozásához. Rendszerindító adathordozó létrehozásával kapcsolatos további információkért lásd: [létrehozásának folyamatáról](create-bootable-media.md).  

##  <a name="BKMK_CaptureExistingRefComputer"></a> Operációs rendszer lemezképének rögzítése meglévő referencia-számítógépről  
 Ha egy referencia-számítógép már készen áll a rögzítéshez, létrehozhat egy feladatütemezést, amely rögzíti az operációs rendszert a referencia-számítógépről. Az **Operációs rendszer lemezképének rögzítése** feladatütemezési lépéssel egy vagy több lemezképet rögzíthet a referencia-számítógépről, majd egy képfájlban (.wim) tárolhatja őket a megadott hálózati megosztáson. A referencia-számítógép rendszerindító lemezkép használatával elindult Windows PE környezetben, a referencia-számítógépen mindegyik merevlemez külön lemezképként van rögzítve a .wim fájlban. Ha a hivatkozott számítógépen több meghajtó van, az eredményül kapott .wim fájl minden kötethez egy különálló lemezképet fog tartalmazni. Csak az NTFS vagy FAT32 fájlrendszerrel formázott kötetek lesznek rögzítve. Az egyéb formátumú, illetve az USB-kötetek figyelmen kívül lesznek hagyva.  

 A következő eljárás használatával rögzítheti az operációs rendszer lemezképét egy meglévő referencia-számítógépről.  

#### <a name="to-capture-an-operating-system-from-an-existing-reference-computer"></a>Operációs rendszer rögzítése meglévő referencia-számítógépről  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  A **Új feladatütemezés létrehozása** lapon válassza az **Új egyéni feladatütemezés létrehozása**lehetőséget.  

5.  A **Feladatütemezés adatai** lapon adja meg a feladatütemezés nevét és leírását.  

6.  Adja meg a feladatütemezés rendszerindító lemezképét. A rendszerindító lemezkép a referencia-számítógép Windows PE környezetben való elindítására szolgál.  További információkért lásd: [rendszerindító lemezképek kezelése](../get-started/manage-boot-images.md).  

7.  Fejezze be a varázslót.  

8.  A **Feladatütemezések**részen válassza ki az egyéni feladatütemezést, majd a **Kezdőlap** lap **Feladatütemezés** csoportjában a **Szerkesztés** gombra kattintva nyissa meg a feladatütemezés-szerkesztőt.  

9. Használja ezt a lépést, ha a Configuration Manager-ügyfél telepítve van a referencia-számítógépen.  

     Kattintson a **Hozzáadás**, kattintson a **lemezképek**, és kattintson a [ConfigMgr-ügyfél előkészítése a rögzítéshez](../understand/task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture). Ez a feladatütemezési lépés szükséges a Configuration Manager-ügyfél a referencia-számítógépen, és felkészíti a rögzítésre a lemezkép-készítési folyamat részeként.  

10. Kattintson a **Hozzáadás**, kattintson a **lemezképek**, és kattintson a [Windows előkészítése a rögzítéshez](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture). Ez a feladatütemezési művelet futtatja a Sysprep eszközt, majd a feladatütemezéshez megadott Windows PE rendszerindító lemezképpel indítja újra a számítógépet. Ez a művelet akkor végezhető el sikeresen, ha a referencia-számítógép nincs tartományhoz csatlakoztatva.  

11. Kattintson a **Hozzáadás**, kattintson a **lemezképek**, és kattintson a [operációs rendszer lemezképének rögzítése](../understand/task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  Ez a feladatütemezési lépés csak Windows PE környezetből rögzíti a merevlemez-meghajtókat a referencia-számítógépen. Konfigurálja az alábbi beállításokat a feladatütemezési lépéshez.  

    -   **Név** és **leírás**: Szükség esetén változtassa meg a feladatütemezési lépés nevét és leírását.  

    -   **Cél**: Megadhat egy megosztott hálózati mappát, ahová a kimeneti. WIM-fájlban tárolja. Ez a fájl tartalmazza az operációsrendszer-képet, amely a varázsló segítségével megadott beállítások szerint jön létre. Ha a megadott mappában már van egy .WIM fájl, a rendszer felülírja a meglévő fájlt.  

    -   **Leírás**, **verzió**, és **által létrehozott**: Igény szerint adja meg a rögzíteni kívánt kép adatait.  

    -   **Operációs rendszer lemezképének rögzítése fiók**: Adja meg a Windows-fiók, amely jogosult a hálózati megosztáson megadott. A **Beállítás** gombra kattintva adhatja meg a Windows-fiók nevét.  

     Kattintson az **OK** gombra a feladatütemezés-szerkesztő bezárásához.  

 A feladatütemezés telepítése a referencia-számítógépen az alábbi módszerek valamelyikével:  

-   Ha a referencia-számítógépen a Configuration Manager-ügyfél, a feladatütemezés telepítene a referencia-számítógépet tartalmazó gyűjteményen. Az operációs rendszer lemezképének telepítésével kapcsolatos információkért lásd: [hozzon létre egy feladatütemezést az operációs rendszer telepítéséhez](create-a-task-sequence-to-install-an-operating-system.md).  

-   Ha a referencia-számítógép nincs a Configuration Manager-ügyfél, vagy ha szeretné manuálisan futtatja a feladatütemezést a referencia-számítógépen, futtassa a **feladatütemezési média létrehozása varázsló** rendszerindító adathordozó létrehozásához. Rendszerindító adathordozó létrehozásával kapcsolatos további információkért lásd: [létrehozásának folyamatáról](create-bootable-media.md).  

##  <a name="BKMK_BuildandCaptureTSExample"></a> Operációsrendszer-kép készítésére és rögzítésére szolgáló feladatütemezés példája  
 Az alábbi táblázatot útmutatóként használva hozzon létre egy feladatütemezést az operációsrendszer-kép készítésére és rögzítésére. A táblázat segítséget nyújt a feladatütemezési lépések általános sorrendjének meghatározásához és a lépések logikai csoportokba rendezéséhez és szerkezetének kialakításához. Az Ön által létrehozott feladatütemezés eltérhet ettől a példától, és több vagy kevesebb feladatütemezési lépést tartalmazhat.  

> [!IMPORTANT]  
>  Mindig a Feladatütemezés létrehozása varázsló segítségével hozzon létre ilyen típusú feladatütemezést.  

 Ha az **Új feladatütemezés** varázsló segítségével hozza létre ezt az új feladatütemezést, a feladatütemezési lépések neveinek némelyike eltér attól, mint ha manuálisan adta volna hozzá ezeket a feladatütemezési lépéseket egy meglévő feladatütemezéshez. Az alábbi táblázatban láthatók az elnevezési eltérések:  

|Új feladatütemezés varázsló feladatütemezési lépésének neve|Feladatütemezés-szerkesztő egyenértékű lépésének neve|  
|------------------------------------------------------|-----------------------------------------------|  
|Újraindítás Windows PE környezetben|Újraindítás Windows PE környezetben vagy merevlemezen|  
|0 lemez particionálása|Lemez formázása és particionálása|  
|Eszközillesztők alkalmazása|Illesztőprogramok automatikus alkalmazása|  
|Frissítések telepítése|Szoftverfrissítések telepítése|  
|Csatlakozás munkacsoporthoz|Csatlakozás tartományhoz vagy munkacsoporthoz|  
|ConfigMgr-ügyfél előkészítése a rögzítéshez|Prepare ConfigMgr Client for Capture|  
|Operációs rendszer előkészítése|Prepare Windows for Capture|  
|Kép készítése a referencia-számítógépről|Operációs rendszer lemezképének rögzítése|  

|Feladatütemezési csoport/lépés|Hivatkozás|  
|-------------------------------|---------------|  
|A referencia-számítógép összeállítása – **(Új feladatütemezési csoport)**|Feladatütemezési csoport létrehozása. A feladatütemezési csoportok a jobb rendezés és hibaellenőrzés érdekében összefogják a hasonló feladatütemezési lépéseket.<br /><br /> Ez a csoport a referencia-számítógépek összeállításához szükséges műveleteket tartalmazza.|  
|Újraindítás Windows PE környezetben|Ezt a feladatütemezési lépést használva adhatja meg célszámítógép újraindítási beállításait. Ez a lépés üzenetben tájékoztatja a felhasználót a számítógép újraindításáról, hogy a telepítés folytatódhasson.<br /><br /> Ez a lépés a csak olvasható **_SMSTSInWinPE** feladatütemezési változót használja. Ha a kapcsolódó érték **hamis** , a feladatütemezési lépés folytatódik.|  
|0 lemez particionálása|Ezt a feladatütemezési lépést használva adhatja meg a célszámítógépen a merevlemez formázásához szükséges műveleteket. Az alapértelmezett lemezszám a **0**.<br /><br /> Ez a lépés a csak olvasható **_SMSTSClientCache** feladatütemezési változót használja. Ez a lépés akkor fog futni, ha a Configuration Manager-ügyfél gyorsítótára nem létezik.|  
|Operációs rendszer alkalmazása|Ezt a feladatütemezési lépést használva telepíthet egy megadott operációsrendszer-képet a célszámítógépen. Ez a lépés az adott köteten (a Configuration Manager-specifikus vezérlési fájlok) kivételével minden fájl törlése után a WIM-fájlban a megfelelő soros lemezköteten a cél számítógépen található összes kötetlemezképet vonatkozik.|  
|Windows-beállítások alkalmazása|Ezzel a feladatütemezési lépéssel konfigurálhatja a Windows-beállítások konfigurációs adatait a célszámítógéphez.|  
|Hálózati beállítások alkalmazása|Ezzel a feladatütemezési lépéssel adhatja meg a célszámítógép hálózati vagy munkacsoport-konfigurációs adatait.|  
|Eszközillesztők alkalmazása|Ezzel a feladatütemezési lépéssel egyeztetheti és telepítheti az illesztőprogramokat az operációs rendszer telepítésének részeként. **Az összes kategóriából származó illesztőprogram figyelembevétele** választógombot bejelölve engedélyezheti, hogy a Windows telepítő minden meglévő illesztőprogram-kategóriában keressen, **Az illesztőprogramok figyelembevételének korlátozása a kiválasztott kategóriákra**választógombot bejelölve pedig korlátozhatja, hogy a Windows telepítő mely illesztőprogram-kategóriákban keressen.<br /><br /> Ez a lépés a csak olvasható **_SMSTSMediaType** feladatütemezési változót használja. Ha a kapcsolódó érték nem egyezik meg a **FullMedia** értékkel, ez a feladatütemezési lépés fog futni.|  
|Windows és ConfigMgr beállítása|Ez a feladatütemezési lépés használatával a Configuration Manager ügyfélszoftver telepítéséhez. A Configuration Manager telepíti, és regisztrálja a Configuration Manager-ügyfél GUID Azonosítóját. A szükséges telepítési paramétereket a **Telepítés tulajdonságai** ablakban rendelheti hozzá.|  
|Frissítések telepítése|Ezzel a feladatütemezési lépéssel adja meg, hogy a szoftverfrissítések hogyan legyenek telepítve a célszámítógépen. A rendszer ezen feladatütemezési lépés futtatásáig nem értékeli ki, hogy a célszámítógépen alkalmazhatóak-e szoftverfrissítések. Ezen a ponton a célszámítógépen a szoftverfrissítések bármely más Configuration Manager által felügyelt-ügyfélhez hasonlóan értékeli ki.<br /><br /> Ez a lépés a csak olvasható **_SMSTSMediaType** feladatütemezési változót használja. Ha a kapcsolódó érték nem egyezik meg a **FullMedia** értékkel, ez a feladatütemezési lépés fog futni.|  
|Kép készítése a referencia-számítógépről – **(Új feladatütemezési csoport)**|Másik feladatütemezési csoport létrehozása. Ez a csoport tartalmazza a referencia-számítógép előkészítéséhez és rögzítéséhez szükséges lépéseket.|  
|Csatlakozás munkacsoporthoz|Ezzel a feladatütemezési lépéssel adhatja meg azokat az információkat, amelyek a célszámítógép munkacsoporthoz való csatlakozásához szükségesek.|  
|Prepare ConfigMgr Client for Capture|Ebben a lépésben a referencia-számítógépen a Configuration Manager-ügyfél érvénybe használja, és felkészíti a rögzítésre a lemezkép-készítési folyamat részeként|  
|Operációs rendszer előkészítése|E feladatütemezési lépés használatával adhatja meg a Windows-beállítások referencia-számítógépről történő rögzítésekor használandó Sysprep-beállításokat. Ez a feladatütemezési lépés futtatja a Sysprep eszközt, majd a feladatütemezéshez megadott Windows PE rendszerindító lemezképpel újraindítja a számítógépet.|  
|Operációs rendszer lemezképének rögzítése|E feladatütemezési lépés használatával adhatja meg a kép mentésekor használandó meglévő hálózati megosztást és WIM-fájlt. Ez a hely szolgál a csomag forráshelyeként, amikor az **Operációsrendszer-lemezkép hozzáadása varázsló**használatával vesz fel egy operációsrendszer-lemezképcsomagot.|  

 Miután elkészült egy lemezkép rögzítésével a referencia-számítógépen, ne rögzítsen rajta újabb operációsrendszer-lemezképet, mert a beállításjegyzék-bejegyzések a kezdeti konfiguráció során jönnek létre. Minden újabb operációsrendszer-lemezkép rögzítéséhez újabb referencia-számítógépet kell létrehozni. Ha ugyanazon a referencia-számítógép segítségével jövőbeli operációsrendszer-lemezképek készítését tervezi, először távolítsa el a Configuration Manager-ügyfél, és telepítse a Configuration Manager-ügyfél.  

## <a name="next-steps"></a>További lépések  
[Vállalati operációs rendszerek központi telepítésének módszerei](methods-to-deploy-enterprise-operating-systems.md)

