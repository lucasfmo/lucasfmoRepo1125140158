---
title: "A Windows központi telepítése a hálózaton keresztül PXE használatával |} Microsoft Docs"
description: "Operációs rendszer PXE környezetből indított központi telepítéseket használ, egy számítógép operációs rendszerének frissítése vagy a Windows új verziójának telepítése egy új számítógépre."
ms.custom: na
ms.date: 12/07/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
caps.latest.revision: 19
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f44505c977b511223a083a960f871371c0ff133
ms.openlocfilehash: b22cdbd42693078caa47f41182ce73ea881c3515
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>A Windows központi telepítése a hálózaton keresztül PXE segítségével a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Operációs rendszerek PXE környezetből kezdeményezett központi telepítése a System Center Configuration Managerben lehetővé teszik az ügyfélszámítógépek kérjék és operációs rendszerek központi telepítése a hálózaton keresztül. Ennél a központi operációsrendszer-telepítési módszernél az operációs rendszer lemezképét, valamint egy x86- és egy x64-alapú Windows PE rendszerindító lemezképet kell küldeni egy olyan terjesztési pontra, amely konfigurálva van a PXE rendszerindítási kérelmek fogadására.  

> [!NOTE]  
>  Ha kizárólag x64-alapú BIOS-szal rendelkező számítógépek számára hoz létre központi operációsrendszer-telepítést, mind az x64-es, mind az x86-os rendszerindító lemezképnek elérhetőnek kell lennie a terjesztési ponton.  

 A PXE környezetből indított központi operációsrendszer-telepítések a következő telepítési helyzetekben alkalmazhatók:  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

 Hajtsa végre egy operációsrendszer-telepítési forgatókönyv lépéseit. Ezután az alábbi szakaszok alapján készítheti elő a PXE környezetből indított központi telepítéseket.  

##  <a name="BKMK_Configure"></a> Legalább egy létező terjesztési pont konfigurálása a PXE-kérelmek fogadásához  
 Operációs rendszerek központi telepítéséhez a Configuration Manager-ügyfelek, amelyek PXE rendszerindítási kérelmeket, válaszoljanak a PXE rendszerindítási kérelmekre egy vagy több terjesztési pontot kell használnia.  További információ a PXE engedélyezve van a terjesztési ponton, tekintse meg a [konfigurálása a terjesztési pontokat, hogy fogadja a PXE Rendszerindítási kérelmek](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).  

## <a name="prepare-a-pxe-enabled-boot-image"></a>PXE-képes rendszerindító lemezkép előkészítése  
 Ha PXE használatával szeretné végezni az operációs rendszer központi telepítését, 32 bites (x86) és 64 bites (x64) PXE-képes rendszerindító lemezképre is szüksége lesz, amelyek egy vagy több PXE-képes kiterjesztési pontra vannak terjesztve. A következő információk segítségével engedélyezheti a PXE-t a rendszerindító lemezképen, majd terjesztheti a lemezképet a terjesztési pontokon:  

-   Ha egy rendszerindító lemezképen szeretné engedélyezni a PXE-t, a rendszerindító lemezkép tulajdonságai között az  **Adatforrás** lapon válassza **A rendszerindító lemezkép központi telepítése a PXE-képes terjesztési pontról** lehetőséget.  

-   Ha módosítja a rendszerindító lemezkép tulajdonságait, terjessze újra a rendszerindító lemezképet a terjesztési pontokon. További információkért lásd: [tartalomterjesztés](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_PXEExclusionList"></a> Kizárási lista létrehozása PXE központi telepítésekhez  
 Ha a PXE használatával végzi az operációs rendszer központi telepítését, minden terjesztési ponton létrehozhat egy kizárási listát, amely segítségével figyelmen kívül hagyhatja a listán szereplő számítógépektől érkező PXE rendszerindítási kérelmeket. A kizárási lista azon számítógépek MAC-címét tartalmazza, amelyek kérelmeit a terjesztési pontnak mellőznie kell. Ezek a számítógépek nem kapják meg a központi telepítési feladatütemezések a Configuration Manager által a PXE típusú központi telepítéshez.  

 A PXE használatát kizáró listák létrehozásához a következő lépések használhatók.  

#### <a name="to-create-the-exclusion-list"></a>Kizárási lista létrehozása  

1.  Hozzon létre a PXE képességű terjesztési ponton egy szövegfájlt. A szövegfájl neve legyen például **pxeExceptions.txt**.  

2.  Használjon olyan egyszerű szokásos szövegszerkesztőt, mint a Jegyzettömb. A MAC-cím egyes értékeit egymástól válassza el kettősponttal, és írja mindegyik címet külön sorba. Például így: `01:23:45:67:89:ab`  

3.  Mentse a szövegfájlt a PXE képességű terjesztési pont helyrendszer-kiszolgálójára. A szövegfájl a kiszolgálón bárhova menthető.  

4.  Szerkessze a PXE képességű terjesztési pont beállításjegyzékét, hogy létrehozza a **MACIgnoreListFile** beállításkulcsot, ez tartalmazza a PXE képességű terjesztési pont helyrendszer-kiszolgálón a szövegfájl helyének teljes elérési útját karakterlánc típusú értékként. A beállításjegyzékben használja a következő elérési utat:  

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  A Beállításszerkesztő nem megfelelő használatával olyan súlyos problémákat okozhat, amelyek az operációs rendszer újratelepítését tehetik szükségessé. A Microsoft nem tudja garantálni, hogy a Beállításszerkesztő nem megfelelő használatából eredő problémákat meg tudja oldani. A Beállításszerkesztőt saját kockázatára használhatja.  

     A beállításjegyzéki változtatás után nincs szükség a kiszolgáló újraindítására.  

##  <a name="BKMK_RamDiskTFTP"></a>A RamDisk TFTP-blokkméret és ablakméret  
Testreszabhatja a RamDisk TFTP-blokkméret és a Configuration Manager verziója 1606, az ablak mérete, a PXE-képes terjesztési pontok verziótól kezdve. Ha testreszabta a hálózatot, akkor a rendszerindító lemezkép letöltése időtúllépési hiba miatt sikertelen lehet, ha a blokk vagy az ablak mérete túl nagy. A RamDisk TFTP blokkméretének és ablakméretének testreszabásával lehetővé válik a TFTP-forgalom optimalizálása, amikor PXE-t használ a konkrét hálózati követelmények teljesítésére. A leghatékonyabb konfiguráció meghatározásához tesztelje a testreszabott beállításokat a környezetében. További információkért lásd: [testreszabhatja a RamDisk TFTP-blokkméret és ablakméret a PXE-képes terjesztési pontokon](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="configure-deployment-settings"></a>Központi telepítési beállítások konfigurálása  
 A PXE környezetben kezdeményezett központi operációsrendszer-telepítésekhez úgy kell beállítania a központi telepítést, hogy elérhetővé tegye az operációs rendszert a PXE rendszerindítási kérelmek számára. Ezt a Szoftver központi telepítése varázsló **Központi telepítési beállítások** lapján, vagy a központi telepítés tulajdonságainak **Központi telepítési beállítások** lapján konfigurálhatja.  Az **Elérhetővé tétel a következők számára** beállításnál konfigurálja a következők egyikét:  

-   Configuration Manager ügyfelek, média és PXE  

-   Csak média és PXE  

-   Csak média és PXE (rejtett)  

##  <a name="BKMK_Deploy"></a> A feladatütemezés végrehajtása  
 Az operációs rendszer központi telepítése egy célgyűjteménybe További információk: [Feladatütemezés telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Amikor PXE segítségével telepít operációs rendszert, beállíthatja, hogy a központi telepítés kötelező vagy elérhető legyen.  

-   **Kötelező központi telepítés**: A kötelező központi telepítések felhasználói beavatkozás nélkül használják a PXE. A felhasználó nem kerülheti el a PXE rendszerindítást. Ha azonban a felhasználó a terjesztési pont válasza előtt szakítja meg a PXE rendszerindítást, az operációs rendszer telepítésére nem kerül sor.  

-   **Elérhető központi telepítés**: Rendelkezésre álló telepítések igénylik, hogy a felhasználó a célszámítógépnél jelen-e, hogy megnyomja az F12 billentyűt a PXE rendszerindítási folyamatának folytatásához. Ha a felhasználó nincs jelen az F12 megnyomásához, a számítógép az aktuális operációs rendszerrel, vagy a következő igénybe vehető rendszerindító eszközről tölt be.  

 Egy szükséges PXE központi telepítés újratelepíthető, ha törli a Configuration Manager-gyűjteményhez vagy számítógéphez társított utolsó PXE központi telepítés állapotának újból telepítheti. Ez a művelet visszaállítja az adott központi telepítés állapotát és újratelepíti a legfrissebb szükséges központi telepítéseket.  

> [!IMPORTANT]  
>  A PXE protokoll nem biztonságos. Gondoskodjon róla, hogy a PXE kiszolgáló és a PXE ügyfél fizikailag biztonságos hálózaton, például adatközpontban legyen, hogy megakadályozza a hely jogosulatlan elérését.  

##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>A rendszerindító lemezkép hogyan van kiválasztva a PXE rendszerindítást ügyfelek?
Amikor egy ügyfél PXE elindul, a Configuration Manager ellátja az ügyfelet, egy rendszerindító lemezképhez használatára. -Től kezdődően a Configuration Manager verziója 1606 Configuration Manager használ a rendszerindító lemezképet egy architektúra pontos egyezés Ha elérhető ilyen. A pontos architektúrával rendszerindító lemezkép nem érhető el, ha a Configuration Manager rendszerindító lemezképet használ egy kompatibilis architektúrával. A következő lista ismerteti, hogyan legyen kiválasztva a rendszerindító lemezképek PXE rendszerindítást ügyfelek.
1. A Configuration Manager a Helyadatbázis, a rendszer rekord, amely megfelel a MAC-címét vagy SMBIOS az ügyfél rendszerindítását kívánó jelenjenek meg.
    > [!NOTE]
    > Ha olyan számítógépre, amely nincs hozzárendelve a helyhez PXE rendszerindítást hajt végre egy differenet vonatkozóan, a házirendek nem láthatók a számítógéphez. Például ha egy ügyfél már hozzá van rendelve helyszín, a felügyeleti pont és terjesztési pont a B hely nem lesz fér hozzá a házirendek a hely és az ügyfél fog sikeresen nem PXE-rendszerindítást.
2. A Configuration Manager a rendszer rekord, az 1. lépésben található telepített feladatütemezések keresi.
3. A feladatütemezések a 2. lépésben található a listában a Configuration Manager rendszerindító próbáló ügyfél architektúrájának megfelelő rendszerindító lemezképhez keresi. Ha rendszerindító lemezképet a azonos architektúrával található, a rendszerindító lemezképet használja.

4. Ha a rendszerindító lemezképek nem található a azonos architecuture rendelkező, a Configuration Manager keresi a rendszerindító lemezkép (a listából az feladatütemezés a 2. lépésben található), amely az ügyfél rendszerindítását kívánó architektúrájával kompatibilis. Például egy 64 bites ügyfél kompatibilis 32 bites és 64 bites rendszerindító lemezképekkel. Csak a 32 bites rendszerindító lemezképek 32 bites ügyfél esetén. UEFI-ügyfél csak a 64 bites rendszerindító lemezképek esetén.

