---
title: "Ügyfél-központitelepítési állapot figyelése |} Microsoft Docs"
description: "A System Center Configuration Manager ügyfél-központitelepítési állapot figyelése."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 20a573b3-53cb-4ed5-bae1-7542f533ed20
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3d9d02d8c56aea17e563112f92173c2b56781da6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-client-deployment-status-in-system-center-configuration-manager"></a>Ügyfél-központitelepítési állapot figyelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az ügyfelek központi telepítése sok időt vehet igénybe, és előfordulhat, hogy a telepítés nem minden esetben jár elsőre sikerrel. A System Center Configuration Manager konzol segítségével nyomon követheti a gyűjteményben lévő ügyfelek telepítésének ügyfél-központitelepítési állapot valós idejű jelentéseket biztosít.  

> [!NOTE]  
>  Az ügyfelek telepítésének legjobb és legmegbízhatóbb módja van a Configuration Manager-konzollal (ebben a cikkben leírtak). A konzol **Figyelés** munkaterületének **Ügyfélállapot** része pontosan és valós időben jeleníti meg az ügyfelek telepítési állapotát. Az ügyfelek telepítését más eszközökkel (például a Windows Server Kiszolgálókezelő alkalmazásával vagy a System Center Operations Manager alkalmazással) is nyomon követheti, ebben az esetben azonban előfordulhat, hogy a normál ügyféltelepítési műveletek is riasztásokat váltanak ki. Az ügyféltelepítési program (CCMSetup.exe) különböző környezetekben való futása következtében ezek az eszközök olyan téves riasztásokat és figyelmeztetéseket generálhatnak, amelyek nem tükrözik hitelesen az ügyféltelepítés állapotát.  

 A konzol **Figyelés** munkaterületén a megadott gyűjteményben a következő állapotok segítségével követheti nyomon az ügyféltelepítéseket:  

-   Compliant (Megfelelő)  

-   Folyamatban  

-   Nem megfelelő  

-   Sikertelen  

-   Ismeretlen  

 A Configuration Manager az üzemi ügyfelek és az üzem előtti ügyfelek telepítéséről készít jelentést. A Configuration Manager ezenfelül készít egy grafikont is az adott időszakon belül sikertelenül zárult ügyféltelepítésekről, amelynek segítségével megállapíthatja, hogy mit kell tennie a telepítések során fellépő hibák elhárítása és a telepítés általános sikerességének javítása érdekében.  

## <a name="to-monitor-client-deployments"></a>Az ügyféltelepítések nyomon követése  

-   Kattintson a Configuration Manager konzolon **figyelés** > **ügyfélállapot**.  

-   A figyelni kívánt ügyfél verziójától függően kattintson az **Üzemi ügyféltelepítés** vagy az **Üzem előtti ügyféltelepítés** elemre.  

-   Tekintse meg az ügyféltelepítési állapotokat, valamint az ügyféltelepítés során fellépő hibákat bemutató grafikonokat.  

-   A jelentés hatókörének módosításához, kattintson a **Tallózás...**  , és válasszon egy másik gyűjteményt.  

 Üzem előtti ügyféltelepítéssel kapcsolatot kapcsolatos további információkért lásd: [ügyfélfrissítések tesztelése egy üzem előtti gyűjteményben a System Center Configuration Managerben az](../../../core/clients/manage/upgrade/test-client-upgrades.md).

 > [!NOTE]
 > Előfordulhat, hogy egy üzem előtti gyűjteménnyel helyrendszerszerepköröket üzemeltető számítógépeken a központi telepítési állapot jelentett **nem kompatibilis** még ha az ügyfél telepítése sikerült. Amikor előlépteti az ügyfelet üzemre, a telepítési állapota helyesen szerepel a jelentésekben.   

 A telepített ügyfelek állapotának figyelése: [Ügyfelek figyelése a System Center Configuration Managerben](../../../core/clients/manage/monitor-clients.md)  

 A Configuration Manager jelentéseinek segítségével az ügyfelek állapotára vonatkozó további információkért a helyen található. További információk a jelentések futtatásáról: [Jelentéskészítés a System Center Configuration Managerben](../../../core/servers/manage/reporting.md).  

