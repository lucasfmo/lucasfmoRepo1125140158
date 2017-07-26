---
title: "BitLocker előzetes kiépítése Windows PE |} Microsoft Docs"
description: "A Preprovision BitLocker feladat a Configuration Manager lehetővé teszi, hogy a BitLocker a Windows előtelepítési környezetből operációs rendszer központi telepítése előtt."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c7c94ba0-d709-4129-8077-075a8abaea1c
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: baca498dbc5b8e168852aa3c18ee23a9c483e69c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="preprovision-bitlocker-in-windows-pe-with-system-center-configuration-manager"></a>BitLocker előzetes kiépítése Windows PE környezetben a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A **kiépítés előtti BitLocker** feladatütemezési lépés a System Center Configuration Manager lehetővé teszi, hogy engedélyezze a Bitlockert a Windows előtelepítési környezetből (Windows PE) operációs rendszer telepítését megelőzően. A merevlemezen csak a használatban lévő terület titkosított, így a titkosítás sokkal gyorsabb. Ehhez egy véletlenszerűen létrehozott, üres védelmi modult alkalmaz a rendszer a formázott köteten, és a kötetet még a Windows telepítési folyamatának futása előtt titkosítja. A BitLocker előzetes kiépítésének lehetősége a Windows 8 és Windows Server 2012 rendszerekben jelent meg. Ugyanakkor konkrét lépések végrehajtásával lehetősége van a BitLocker előzetesen kiépítésére, majd a Windows 7 telepítésére egy merevlemezen. Amikor befejeződött a Windows 7 telepítése, be kell állítani egy BitLocker-kulcsvédőt, mert a Windows 7 BitLocker vezérlőpultja nem támogatja az üres védelmi modullal működő BitLocker funkciót. Vagy a **BitLocker engedélyezése** lépéssel, vagy a manage-bde.exe parancssori eszközzel meg kell adnia egy kulcsvédőt.  

 Általában a következő műveleteket kell elvégezni ahhoz, hogy a később a Windows 7 telepítéséhez használandó számítógépen sikeresen el tudja végezni a BitLocker előzetes kiépítését:  

-   A számítógép újraindítása a Windows PE környezetben  

    > [!IMPORTANT]  
    >  A BitLocker előzetes kiépítéséhez olyan rendszerindító lemezképet kell használnia, amelyben a Windows PE 4-es vagy újabb verziója található. További információ a támogatott Windows PE-verziók a Configuration Manager: [külső függőségei a Configuration Manager](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_ExternalDependencies).  

-   A merevlemez particionálása és formázása  

-   ben a  

-   A Windows 7 rendszer telepítése konkrét operációs rendszeri és hálózati beállításokkal  

-   Kulcsvédő hozzáadása a BitLockerhez  

 A Configuration Manager, az ajánlott módszer a BitLocker előzetes felülvizsgálatához a merevlemezen, és Windows 7 telepítése, hogy új feladatütemezést hoz lére, és válassza ki **meglévő lemezképcsomag telepítése** a a **új feladatütemezés létrehozása** oldalán a **feladatütemezés létrehozása varázsló**. A varázsló az alábbi táblázatban felsorolt feladatütemezési lépéseket hozza létre.  

> [!NOTE]  
>  A feladatütemezés a varázslóban megadott beállításoktól függően további lépéseket is tartalmazhat. Szerepelhet például a **Windows beállítások rögzítése** lépés, ha a varázsló **Állapotáttelepítés** lapján megadta a **Microsoft Windows beállítások rögzítése** beállítást.  

|Feladatütemezési lépés|Részletek|  
|------------------------|-------------|  
|BitLocker inaktívvá tétele|Ez a lépés letiltja a BitLocker-titkosítást, amennyiben éppen engedélyezett állapotú. További információkért lásd: [BitLocker inaktívvá tétele](../understand/task-sequence-steps.md#BKMK_DisableBitLocker).|  
|A számítógép újraindítása a Windows PE környezetben|Ez a lépés a számítógépet a feladatütemezéshez hozzárendelt rendszerindító lemezkép futtatásával a Windows PE környezetben indítja újra. A BitLocker előzetes kiépítéséhez olyan rendszerindító lemezképet kell használnia, amelyben a Windows PE 4-es vagy újabb verziója található. További információkért lásd: [számítógép újraindítása](../understand/task-sequence-steps.md#BKMK_RestartComputer).|  
|0 lemez particionálása - BIOS<br /><br /> 0 lemez particionálása - UEFI|Ezek a lépések a célszámítógép megadott meghajtóját a BIOS vagy a UEFI használatával formázzák és particionálják. A feladatütemezés a UEFI-t használja, amennyiben azt észleli, hogy a célszámítógép UEFI módban van. További információkért lásd: [lemez formázása és particionálása](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk).|  
|ben a|Ezzel a lépéssel engedélyezheti a BitLocker szolgáltatást egy meghajtón a Windows PE környezetben. A merevlemezen csak a használatban lévő terület lesz titkosított. Mivel az előző lépésben particionálta és formázta a merevlemezt, nincsenek adatok, így a titkosítás nagyon gyorsan elkészül. További információkért lásd: [kiépítés előtti BitLocker](../understand/task-sequence-steps.md#BKMK_PreProvisionBitLocker).|  
|Operációs rendszer alkalmazása|Ez a lépés elkészíti a válaszfájlt, amelynek használatával az operációs rendszer telepítése megtörténik a célszámítógépen, és az OSDTargetSystemDrive feladatütemezési változót beállítja annak a partíciónak a meghajtóbetűjelére, amely az operációs rendszer fájljait tartalmazza. A válaszfájlt és a változót a Windows és ConfigMgr beállítása lépés használja az operációs rendszer telepítésére. További információkért lásd: [Operációs rendszer lemezképének alkalmazása](../understand/task-sequence-steps.md#BKMK_ApplyOperatingSystemImage).|  
|Windows-beállítások alkalmazása|Ez a lépés a Windows beállításait hozzáadja a válaszfájlhoz. A válaszfájlt a Windows és ConfigMgr beállítása lépés használja az operációs rendszer telepítésére. További információkért lásd: [a Windows-beállítások alkalmazása](../understand/task-sequence-steps.md#BKMK_ApplyWindowsSettings).|  
|Hálózati beállítások alkalmazása|Ez a lépés a hálózat beállításait hozzáadja a válaszfájlhoz. A válaszfájlt a Windows és ConfigMgr beállítása lépés használja az operációs rendszer telepítésére. További információkért lásd: [alkalmazni a hálózati beállítások lépés](../understand/task-sequence-steps.md#BKMK_ApplyNetworkSettings).|  
|Eszközillesztők alkalmazása|Ez a lépés egyezteti az illesztőprogramokat, és telepítő őket az operációs rendszer központi telepítésének részeként. További információkért lásd: [illesztőprogramok automatikus alkalmazása](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers).|  
|Windows és ConfigMgr beállítása|Ez a lépés hajtja végre az átállást a Windows PE környezetről az új operációs rendszerre. Ez a feladatütemezési lépés bármely operációs rendszer központi telepítésének kötelező része. A Configuration Manager-ügyfél telepíti az új operációs rendszerbe, és előkészíti a feladatütemezés végrehajtásának folytatását az új operációs rendszerben. További információkért lásd: [Windows és ConfigMgr beállítása](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).|  
|BitLocker engedélyezése|Ez a lépés engedélyezi a merevlemezen a BitLocker-titkosítást, és beállítja a kulcsvédőket. Mivel a merevlemezen a kiépítés előtti ponton aktívvá vált a BitLocker, ez a lépés nagyon gyorsan elkészül. A Windows 7 rendszernél követelmény a kulcsvédő hozzáadása. Ha nem használja ezt a lépést, a manage-bde.exe parancssori eszköz futtatásával állíthat be kulcsvédőt. További információkért lásd: [BitLocker engedélyezése](../understand/task-sequence-steps.md#BKMK_EnableBitLocker).|  

