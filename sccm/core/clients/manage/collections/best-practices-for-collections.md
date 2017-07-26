---
title: "Gyakorlati tanácsok a gyűjtemények |} Microsoft Docs"
description: "Ajánlott eljárások gyűjteményekhez a System Center Configuration Managerben a beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a2abb79-9ae5-4a25-9e18-5dcf528de3bf
caps.latest.revision: 4
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: fd62af3910c0745e0f1105417701b894e10cbbac
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-collections-in-system-center-configuration-manager"></a>Ajánlott eljárások gyűjteményekhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Használja a következő ajánlott eljárások gyűjteményekhez a System Center Configuration Managerben.  

## <a name="do-not-use-incremental-updates-for-a-large-number-of-collections"></a>Ne használjon növekményes frissítéseket nagy mennyiségű gyűjteményhez  
 A **Növekményes frissítések használata a gyűjteményhez** beállítás engedélyezésekor ez a konfiguráció kiértékelési késésekhez vezethet, ha sok gyűjtemény esetében engedélyezi azt. A küszöbérték a hierarchia körülbelül 200 gyűjteménye. A pontos szám a következő tényezőktől függ:  

-   A gyűjtemények teljes száma  

-   Az új erőforrások a hierarchiához való hozzáadásának és abban való módosításának gyakorisága  

-   A hierarchiában lévő ügyfelek száma  

-   A hierarchiában lévő gyűjteménytagsági szabályok összetettsége  

## <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>Ügyeljen arra, hogy a karbantartási időszakok kellőképpen hosszúak legyenek a kritikus szoftverfrissítések telepítésére  
 Eszközgyűjtemények, amelyekkel korlátozható az, hogy a Configuration Manager mikor telepíthet szoftvereket az ezeknek az eszközöknek karbantartási időszakokat állíthat be. Túl rövid karbantartási időszak konfigurálása esetén előfordulhat, hogy az ügyfél nem tudja telepíteni a kritikus szoftverfrissítéseket, így védtelen marad azokkal a támadásokkal szemben, amelyek elhárítására az érintett frissítések hivatottak.  

