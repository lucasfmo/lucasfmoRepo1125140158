---
title: "Hardverleltár konfigurálása |} Microsoft Docs"
description: "Hardverleltár beállítása az összes ügyfél vagy a System Center Configuration Manager gyűjtemény."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 0baadb95ec8dbb945f1a611ebb95a03cec3199bd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>Hardverleltár konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ezzel az eljárással konfigurálhatja a hardverleltár alapértelmezett ügyfélbeállításait, amelyek a hierarchia minden ügyfélszámítógépére érvényesek lesznek. Ha ezeket a beállításokat csak néhány ügyfélszámítógépen szeretné alkalmazni, hozzon létre egyéni ügyfél-eszközbeállítást és rendelje hozzá olyan gyűjteményhez, ami azokat az eszközöket tartalmazza, amelyeken hardverleltárt szeretne használni. Lásd: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../../core/clients/deploy/configure-client-settings.md).  

> [!NOTE]  
>  Ha egy ügyféleszköz az ügyfélbeállítások több készletétől kap hardverleltár-beállításokat, az ügyfél hardverleltár-jelentése összevonva fogja tartalmazni az egyes beállításkészletekből származó hardverleltárosztályokat.  

### <a name="to-configure-hardware-inventory"></a>Hardverleltár konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett ügyfélbeállítások**.  

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett beállítások** párbeszédpanelen válassza ki **Hardverleltár**.  

6.  Az **Eszközbeállítások** listában állítsa be a következőket:  

    -   **Hardverleltár engedélyezése az ügyfelek** – Itt adhatja meg **igaz**.  

    -   **Hardverleltár-ütemezés** -kattintson **ütemezés** adja meg az intervallumot, amellyel az ügyfelek a Hardverleltár összegyűjtéséhez.  

7.  Konfigurálja az egyéb [Hardverleltár elérhető ügyfélbeállításait](../../../../core/clients/deploy/about-client-settings.md#hardware-inventory) , amelyekre szüksége van.  

Az ügyféleszközök ezeket a felhasználói beállításokat fogják használni, amikor legközelebb letöltik az ügyfélházirendet. Egyetlen ügyfél házirendlekérésének kezdeményezéséről a [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../../core/clients/manage/manage-clients.md) című témakör nyújt tájékoztatást.  

