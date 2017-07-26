---
title: "Az Intune-előfizetése társítva a System Center Configuration Managerrel |} Microsoft Docs"
description: "Kezelése a System Center Configuration Managerrel kapcsolatos Intune-előfizetést."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 2e0b3cd1070d0f8adb1219acd33c3126d2758a49
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>Az Intune-előfizetése társítva a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha a Microsoft Intune (a próba-előfizetés vagy fizetős) felvétele a Configuration Managerbe, és akkor kell váltani egy másik Intune-előfizetést, is törölnie kell a **Microsoft Intune-előfizetés** és a **szolgáltatáskapcsolódási pont** egy új előfizetés hozzáadása előtt a Configuration Manager konzoljáról.

> [!NOTE]
> A hibrid mobileszköz-kezelés egyszerre csak egy Intune-előfizetés is meg.

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Intune-előfizetés törlése a Configuration Managerből

> [!IMPORTANT]
>  Az összes tartalmat, ideértve a felhasználói regisztrációkat, házirendeket és az Intune-előfizetés által kezelt eszközök konfigurált alkalmazástelepítéseket is törlődnek, az előfizetés törlése.

1.  Nyissa meg a Configuration Manager konzol **felügyeleti** > **áttekintése** > **Felhőszolgáltatások** > **Microsoft Intune-előfizetések**.

2.  Kattintson a jobb gombbal az a felsorolt **Microsoft Intune-előfizetés**, és kattintson a **törlése**.

3.   A varázslóban kattintson **távolítsa el a Microsoft Intune-előfizetést a Configuration Manager**, kattintson a **tovább**, és kattintson a **tovább** újra, hogy az előfizetés eltávolítása.


## <a name="how-to-remove-the-service-connection-point-role"></a>A szolgáltatási kapcsolódási pont szerepkör eltávolítása

1.  Ugrás a **felügyeleti** > **áttekintése** > **hely konfigurációs** > **kiszolgálók és Helyrendszerszerepkörök**.

2.  Válassza ki a **Szolgáltatáskapcsolati pont** szerepkört futtató kiszolgálót.

3.  A **Helyrendszer-szerepkörök** listában válassza a **Szolgáltatáskapcsolati pont** lehetőséget, majd kattintson a **Szerepkör eltávolítása** parancsra a menüszalagon. Hagyja jóvá a szerepkör eltávolítását. A szolgáltatáskapcsolódási pont törlődik.

Ezt követően létrehozhat egy új szolgáltatáskapcsolati pontot, új Intune-előfizetést vehet fel a Configuration Managerbe, és MDM-szolgáltatóként állíthatja be a Configuration Managert.

## <a name="how-to-change-mdm-authority-to-intune"></a>Az Intune MDM-szolgáltató módosítása

1610 verziójától kezdve lehet váltani a Mobileszköz-kezelő szolgáltatóként a Configuration Manager Intune-ban. A szolgáltatásról. hamarosan már az.

