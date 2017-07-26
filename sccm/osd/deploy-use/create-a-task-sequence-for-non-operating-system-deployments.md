---
title: "Hozzon létre egy feladatütemezést az operációs rendszer központi telepítése |} Microsoft Docs"
description: "Hozzon létre a feladatütemezéseket, amelyek nem kapcsolódnak a központi telepítése az operációs rendszerek, például szoftverterjesztéssel, illesztőprogramok frissítését, szerkesztése, felhasználói állapotok stb."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: b4b04907f2cd48d81e864e46ca47c14a0b98a9f7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-for-non-operating-system-deployments-with-system-center-configuration-manager"></a>Hozzon létre egy feladatütemezést az operációs rendszer központi telepítése a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Feladatütemezések a System Center Configuration Manager segítségével automatizálhatja a különböző feladatok a környezetben. Ezek a feladatok elsősorban az operációs rendszerek központi telepítéséhez készültek és ilyen szempontból lettek tesztelve.  A Configuration Manager számos egyéb funkcióval, amelyeket elsődleges technológiaként használhat olyan helyzetekben, mint rendelkezik [alkalmazástelepítés](../../apps/understand/introduction-to-application-management.md), [a szoftverfrissítések telepítése](../../sum/understand/software-updates-introduction.md), [beállítások konfigurálása](../../compliance/understand/ensure-device-compliance.md), vagy egyéni automatizálás. Emellett vannak más megfontolandó Microsoft System Center automatizálási technológiák is, mint az [Orchestrator](https://technet.microsoft.com/library/hh237242.aspx) és a [Szolgáltatáskezelési automatizálás](https://technet.microsoft.com/library/dn469260.aspx) .  

A feladatütemezések rugalmasságuknak köszönhetően nagyon hatékony eszközök, és hogyan használhatja ezeket az ügyfélbeállítások konfigurálása, szoftverek terjesztését, illesztőprogramok frissítését, felhasználói állapotok módosítását és más az operációs rendszerek központi telepítésétől független feladatokat végrehajtani. Létrehozhat egy egyéni feladatütemezést tetszőleges számú feladat hozzáadásához. Az egyéni feladatütemezés az operációs rendszer központi telepítéséhez használata támogatott a Configuration Manager alkalmazásban. Azonban ha egy feladat feladatütemezési eredményez nemkívánatos vagy inkonzisztens eredményeket, tekintse meg a művelet feltárásában. Ez elvégezhető egyszerűbb lépéseket, a műveletek között, több feladatütemezések felosztásával vagy véve egy szakaszos létrehozása és tesztelése a feladatütemezést olyan módon készíthető elő.

 Az operációs rendszer központi telepítésének egyéni feladatütemezés használata támogatott a következő lépéseket:  

-   [Készültség ellenőrzése](../understand/task-sequence-steps.md#BKMK_CheckReadiness)  

-   [Csatlakozás hálózati mappához](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder)  

-   [Csomag tartalmának letöltése](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent)  

-   [Alkalmazás telepítése](../understand/task-sequence-steps.md#BKMK_InstallApplication)  

-   [Csomag telepítése](../understand/task-sequence-steps.md#BKMK_InstallPackage)  

-   [Telepítse a szoftverfrissítéseket](../understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates)  

-   [Indítsa újra a számítógépet](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer)  

-   [Parancssor futtatása](../understand/task-sequence-steps.md#BKMK_RunCommandLine)  

-   [PowerShell parancsfájl futtatása](../understand/task-sequence-steps.md#BKMK_RunPowerShellScript)  

-   [Dinamikus változók megadása](../understand/task-sequence-steps.md#BKMK_SetDynamicVariables)  

-   [Feladatütemezési változó beállítása](../understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable)  

## <a name="next-steps"></a>További lépések
[A feladatütemezés központi telepítése](manage-task-sequences-to-automate-tasks.md#a-namebkmkdeploytsa-deploy-a-task-sequence)

