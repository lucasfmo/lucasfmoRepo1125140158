---
title: "Hozzon létre egy egyéni feladatütemezést |} Microsoft Docs"
description: "Egy egyéni feladatütemezést a System Center Configuration Managerrel vegyen fel olyan lépéseket a feladatütemezés szerkesztésével."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b9800a66-7541-47ca-8276-da8ef6cb6d1b
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 03c844084c72fc52806123d9f4c11a410a3ec775
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-custom-task-sequence-with-system-center-configuration-manager"></a>Egyéni feladatütemezés létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Egyéni feladatütemezés létrehozása a System Center Configuration Managerben, ha nincs feladatütemezési lépést tartalmaz. A feladatütemezés létrehozása után szerkesztenie kell azt és hozzá kell adnia a szükséges feladatütemezési lépéseket.  

##  <a name="BKMK_CustomTS"></a> Egyéni feladatütemezés létrehozása  
 Az alábbi eljárással hozhat létre egyéni feladatütemezést.  

#### <a name="to-create-a-custom-task-sequence"></a>Egyéni feladatütemezés létrehozása  

1.  A Configuration Manager konzolon kattintson a **Szoftverkönyvtár**elemre.  

2.  A **Szoftverkönyvtár** munkaterületen bontsa ki az **Operációs rendszerek**pontot, majd kattintson a **Feladatütemezések**elemre.  

3.  A Feladatütemezés létrehozása varázsló elindításához kattintson a **Kezdőlap** **Létrehozás** csoportjában található **Feladatütemezés létrehozása** elemre.  

4.  A **Új feladatütemezés létrehozása** lapon válassza az **Új egyéni feladatütemezés létrehozása**lehetőséget.  

5.  A **Feladatütemezés adatai** lapon adja meg a feladatütemezés nevét, leírását és igény szerint azt a rendszerindító lemezképet, amelyet a feladatütemezésnek használni kell, azután fejezze be a varázslót.  

 A feladatütemezés létrehozása varázsló befejezése után a Configuration Manager felveszi az egyéni feladatütemezést a **feladatütemezések** csomópont. Ezután felveheti a szükséges lépéseket a feladatütemezés szerkesztésével.  

 Rendelkezésre álló feladatütemezési lépések listáját lásd: [feladatütemezési lépéseket](../understand/task-sequence-steps.md).  

 A feladatütemezés szerkesztésével kapcsolatos további információkért lásd: [a feladatütemezések szerkesztésével](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 A feladatütemezéseket leggyakrabban az operációs rendszer központi telepítésével kapcsolatos feladatok automatizálásához használhatja, de számos különböző feladat automatizálásához hozhat létre egyéni feladatütemezéseket. További információkért lásd: [hozzon létre egy feladatütemezést az operációs rendszer központi telepítése](create-a-task-sequence-for-non-operating-system-deployments.md).  

 ## <a name="next-steps"></a>További lépések
 [A feladatütemezés központi telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)

