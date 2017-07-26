---
title: "A Windows frissítése a legújabb verzió |} Microsoft Docs"
description: "Útmutató a Configuration Manager segítségével az operációs rendszer frissítése Windows 7 vagy újabb Windows 10-es."
ms.custom: na
ms.date: 02/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 288a4c649f371d9701fe7249449356aa222bf372
ms.openlocfilehash: 35f04e237efffbdb12893f658950a99dc0b98b85
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>A Windows frissítése a legújabb verzióra a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör ismerteti a System Center Configuration Manager egy számítógép operációs rendszerének frissítése a Windows 7 vagy újabb Windows 10 lépéseit. Különböző központi telepítési módszerek, például különálló adathordozó vagy a Szoftverközpont használata közül választhat. A Windows 10-re való helyben végzett frissítés forgatókönyve:  

-   Frissíti az operációs rendszert a jelenleg Windows 7, Windows 8 vagy Windows 8.1 rendszerű számítógépeken. Végezhet a Windows 10-buildek közötti frissítéseket is. Például frissítheti a Windows 10 RTM-et a Windows 10 1511-es verziójára.  

-   Megőrzi az alkalmazásokat, a beállításokat és a felhasználói adatokat a számítógépen.  

-   Nincsenek külső függőségei, mint például a Windows ADK.  

-   Általában gyorsabb és rugalmasabb az operációs rendszerek hagyományos központi telepítéseinél.  

 Az alábbi szakaszok azt ismertetik, hogyan végezheti el az operációs rendszerek központi telepítését a hálózaton keresztül feladatütemezésekkel.  

##  <a name="BKMK_Plan"></a> Terv  

-   **Az operációs rendszer verziófrissítéséhez készült feladatütemezésre vonatkozó korlátozások áttekintése**  

     Tekintse át az alábbi, az operációs rendszer verziófrissítéséhez készült feladatütemezésre vonatkozó követelményeket és korlátozásokat, és győződjön meg arról, hogy az megfelel az igényeinek:  

    -   Csak olyan feladatütemezési lépéseket adhat hozzá, amelyek az operációs rendszerek központi telepítését és a számítógépek konfigurálását magában foglaló alapvető feladathoz kapcsolódnak. Ez magában foglalja a csomagok, alkalmazások vagy frissítések telepítésére, továbbá a parancssorok és a PowerShell futtatására, valamint a dinamikus változók beállítására szolgáló lépéseket.  

    -   A frissítési feladatütemezés központi telepítése előtt ellenőrizze, hogy a számítógépekre telepített illesztőprogramok és alkalmazások kompatibilisek-e a Windows 10-zel.  

    -   Az alábbi feladatok nem kompatibilisek a helyben végzett frissítéssel, ezért ezek esetében az operációs rendszer központi telepítését a hagyományos módon kell végrehajtania:  

        -   A számítógépek tartományi tagságának módosítása vagy a Helyi rendszergazdák frissítése.  

        -   A számítógép alapvető módosítása, beleértve a lemezparticionálást, az architektúra x86-ról x64-re váltását, az UEFI megvalósítását vagy az operációs rendszer alapnyelvének módosítását.  

        -   Nincsenek beleértve egy alapként szolgáló egyéni lemezkép, az egyéni követelmények 3 használatával<sup>távoli asztali</sup> féltől származó lemeztitkosítás, vagy offline WinPE-műveletek szükséges.  

-   **Infrastruktúrával kapcsolatos követelmények tervezése és implementálása**  

     A frissítési forgatókönyv egyetlen előfeltétele, hogy rendelkezzen egy terjesztési ponttal, mely elérhető az operációs rendszer verziófrissítő csomagja és a feladatütemezéshez hozzáadott bármilyen egyéb csomag számára. További információkért lásd: [telepítése vagy módosíthatja a terjesztési pontokat](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

##  <a name="BKMK_Configure"></a> Konfigurálás  

1.  **Az operációs rendszer verziófrissítő csomagjának előkészítése**  

     A Windows 10 verziófrissítő csomagja tartalmazza a célszámítógép operációs rendszerének verziófrissítéséhez szükséges forrásfájlokat. A verziófrissítő csomag kiadásának, architektúrájának és nyelvének azonosnak kell lennie a frissíteni kívánt ügyfelekével.  További információkért lásd: [operációs rendszer verziófrissítő csomagjainak kezelése](../get-started/manage-operating-system-upgrade-packages.md).  

2.  **Feladatütemezés létrehozása az operációs rendszer verziófrissítéséhez**  

     Az alábbi témakörben található lépésekkel [hozzon létre egy feladatütemezést az operációs rendszer verziófrissítéséhez](create-a-task-sequence-to-upgrade-an-operating-system.md) automatizálhatja az operációs rendszer frissítése.  

    > [FONTOS] Különálló adathordozó használatakor meg kell adnia egy rendszerindító lemezképfájlt a feladatütemezés elérhető nem lesz elérhető a feladatütemezési média varázsló.


    > [!NOTE]  
    >  Jellemző használata lépéseit [hozzon létre egy feladatütemezést az operációs rendszer verziófrissítéséhez](create-a-task-sequence-to-upgrade-an-operating-system.md) operációs rendszer verziófrissítéséhez készült Windows 10-re feladatütemezés létrehozásához. A feladatütemezés tartalmazza az operációs rendszer verziófrissítésének elvégzése lépés, valamint a javasolt további lépéseket, és a csoportok a-végpontok kezelése frissítés. Azonban hozzon létre egy egyéni feladatütemezést, és adja hozzá a [operációs rendszer verziófrissítésének elvégzése](../understand/task-sequence-steps.md#BKMK_UpgradeOS) feladatütemezési lépés az operációs rendszer frissítéséhez. Ez az egyetlen lépés, amely szükséges az operációs rendszer Windows 10-re való frissítéséhez. Ha ez a módszer választása esetén is hozzáadhat a [számítógép újraindítása](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer) lépés a frissítés befejezéséhez az operációs rendszer verziófrissítésének elvégzése lépés után. Ügyeljen arra, hogy használja a **a jelenleg telepített alapértelmezett operációs rendszer** indítsa újra a számítógépet a telepített operációs rendszer és a nem a Windows PE a beállítással.  

##  <a name="BKMK_Deploy"></a> Telepítés  

-   Az operációs rendszer központi telepítéséhez használja a következő módszerek egyikét:  

    -   [Windows központi telepítése a hálózaton keresztül a Szoftverközpont használatával](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [Windows központi telepítése a hálózaton keresztül nélkül a különálló adathordozó használatával](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

## <a name="monitor"></a>Figyelő  

-   **A feladatütemezés központi telepítésének figyelése**  

     A feladatütemezési központi telepítés az operációs rendszer verziófrissítéséhez figyeléséről lásd: [operációs rendszer központi telepítésének figyelése](monitor-operating-system-deployments.md).  

