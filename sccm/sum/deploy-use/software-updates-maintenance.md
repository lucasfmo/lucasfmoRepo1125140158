---

title: "Szoftverfrissítések, karbantartási |} Microsoft Docs"
description: "A Configuration Manager frissítéseinek karbantartásához, ütemezheti a WSUS-karbantartási feladat, vagy manuálisan is futtatható."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 1590c623f7bc2f42a8617f110de5321212732a03
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---
# <a name="software-updates-maintenance"></a>A szoftverfrissítések karbantartás

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ütemezett és a WSUS karbantartási feladat futtatása a Configuration Manager konzolról, vagy manuálisan futtatható a WSUS-karbantartási feladat a szoftverfrissítési pont összetevő tulajdonságai. Amikor a WSUS-karbantartási feladat futtatását választja, a művelet futtatni fogja a következő szoftverfrissítések szinkronizálását. A lejárt szoftverfrissítések elutasított állapotra lesznek állítva a WSUS-kiszolgálón, és a Windows Update Agent a továbbiakban nem keresi ezeket a szoftverfrissítéseket a számítógépeken. A WSUS-karbantartási feladat 30 naponta fut.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>A WSUS-karbantartási feladat ütemezése és futtatása  

1.  A Configuration Manager-konzolon lépjen a **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **helyek**.  

2.  A **Beállítások** csoportban a **Helyösszetevők konfigurálása** elemre, majd a **Szoftverfrissítési pont** lehetőségre kattintva nyissa meg a szoftverfrissítési pont összetevő tulajdonságait.  

3.  Kattintson a **Helyettesítési szabályok** fülre, válassza a **WSUS karbantartása varázsló futtatását**, és kattintson az **OK**gombra.

