---
title: "Gyermek-konfigurációelemek létrehozása |} Microsoft Docs"
description: "Gyermek konfigurációelemek létrehozása a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 33d4a2d5a09af74e1d76ac9b34a42b749f5bf7ef
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-child-configuration-items-in-system-center-configuration-manager"></a>Gyermek configuration konfigurációelemek létrehozása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Gyermek-konfigurációelemek a System Center Configuration Manager konfigurációelemek, amelyek megőrzik a kapcsolatot az eredeti konfigurációelemmel, abban az eredeti konfigurációt öröklik a szülő konfigurációelemtől másolatai.  

Gyermek-konfigurációelem tulajdonságainak megtekintésekor a Configuration Manager konzol nem szerkeszthetők az örökölt objektumokat és beállításokat és azok érvényességi feltételeit. Azonban hozzáadhat további érvényességi feltételeket a gyermek-konfigurációelemhez majd szerkesztheti azokat, valamint új objektumokat és beállításokat is adhat a gyermek-konfigurációelemhez.
A szokásos létrehozásának és szerkesztésének gyermek-konfigurációelem célja az eredeti konfigurációelem az üzleti követelményeknek megfelelő finomítása.  

> [!NOTE]  
>  Gyermek-konfigurációelemek csak a **Windows asztali számítógépek és kiszolgálók (egyéni)**típusú konfigurációelemekből hozhatók létre.  

## <a name="to-create-a-child-configuration-item"></a>Gyermek-konfigurációelem létrehozása  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Konfigurációelemek**.  

3.  Válassza ki a **Konfigurációelemek** listából azt az elemet, amelyből gyermek-konfigurációelemet szeretne létrehozni, majd a **Kezdőlap** lap **Konfigurációelem** csoportjában kattintson a **Gyermek-konfigurációelem létrehozása**lehetőségre.  

4.  A **Gyermek-konfigurációelem létrehozása varázsló** **Általános**lapján kiválaszthatja a szülő konfigurációelem a gyermekelem létrehozásához használni kívánt változatát. A varázsló további lépései megegyeznek a szokásos konfigurációelemek létrehozásának lépéseivel. További információkért lásd: [Windows asztali és kiszolgáló számítógépekhez egyéni konfigurációelemek létrehozása](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md).  

5.  Fejezze be a varázslót. Az új gyermek-konfigurációelem megjelenik a **Konfigurációelemek** listában.  

