---
title: "A System Center Configuration Manager szolgáltatáskapcsolódási pontot létrehozása |} Microsoft Docs"
description: "A System Center Configuration Manager szolgáltatáskapcsolódási pontot létrehozni."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 617abb22-d22f-41fb-a76b-1c4259e419d2
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 9a21d02cb2a50162e5de50481f0f27f2dd7a616c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="create-a-service-connection-point-with-system-center-configuration-manager-and-microsoft-intune"></a>A szolgáltatáskapcsolódási pont létrehozása a System Center Configuration Manager és a Microsoft Intune

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután létrehozta az előfizetést, telepítheti a szolgáltatáskapcsolódási pont helyrendszerszerepkört, amellyel csatlakozhat az Intune szolgáltatáshoz. Ez a helyrendszerszerepkör fogja leküldeni a beállításokat és az alkalmazásokat az Intune szolgáltatásnak.

 A szolgáltatáskapcsolódási pont beállításokat és szoftvertelepítési információkat küld a Configuration Manager és állapot- és beolvassa a mobileszközökről. A Configuration Manager szolgáltatás úgy működik, mint egy átjáró, amelyik kommunikál a mobileszközökkel és tárolja a beállításokat.

> [!NOTE]
>  A szolgáltatáskapcsolódási pont helyrendszerszerepkör csak központi adminisztrációs helyen vagy önálló elsődleges helyen telepíthető. A szolgáltatáskapcsolódási pontnak kapcsolódnia kell az internethez.


## <a name="configure-the-service-connection-point-role"></a>A szolgáltatási kapcsolódási pont szerepkör konfigurálása

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **helyek**, és kattintson a **kiszolgálók és Helyrendszerszerepkörök**.

3.  Adja hozzá a **Szolgáltatáskapcsolódási pont** szerepkört egy új vagy meglévő helyrendszer-kiszolgálóhoz az erre vonatkozó lépésben leírtak szerint:

    -   Új helyrendszer-kiszolgáló: Az a **Home** lap a **létrehozása** csoportjában kattintson a **helyrendszer-kiszolgáló létrehozása** a helyrendszer-kiszolgáló létrehozása varázsló elindításához.

    -   Meglévő helyrendszer-kiszolgálóra: Kattintson arra a kiszolgálóra, amelyre a szolgáltatáskapcsolódási pont szerepkörrel telepíteni szeretné. A Helyrendszer-szerepkörök hozzáadása varázsló elindításához kattintson a **Kezdőlap** lap **Kiszolgáló** csoportjában található **Helyrendszer-szerepkörök hozzáadása** elemre.

4.  A **Rendszerszerepkör kiválasztása** lapon válassza a **Szolgáltatáskapcsolódási pont** elemet, majd kattintson a **Tovább** gombra.
![A szolgáltatáskapcsolódási pont létrehozása](../media/mdm-service-connection-point.png)

* Fejezze be a varázslót.

## <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>Hogyan végzi a szolgáltatáskapcsolódási pont a hitelesítést a Microsoft Intune szolgáltatással?
 A szolgáltatáskapcsolódási pont a kiterjesztett Configuration Manager által a felhőalapú Intune-hoz, amely felügyeli a mobileszközöket az interneten keresztül, hogy kapcsolatot létesít. A szolgáltatáskapcsolódási pont a következőképpen hitelesíti az Intune szolgáltatással:

1.  Intune-előfizetést a Configuration Manager konzolon hozzon létre, amikor a Configuration Manager felügyeleti hitelesítése az Azure Active Directoryhoz, amely átirányítja a felhasználókat a megfelelő ADFS-kiszolgálóhoz tartozó felhasználónevet és jelszót kérjen a csatlakozással. Majd Intune-ban a bérlő számára kiadják a tanúsítványokat.

2.  Az 1. lépésben létrejött tanúsítványt a rendszer telepíti a szolgáltatáskapcsolódási pont helyszerepkörre, és a Microsoft Intune szolgáltatással zajló minden további kommunikáció hitelesítése ezzel történik.

> [!div class="button"]
[< Előző lépés](terms-and-conditions.md)[következő lépés >  ](enable-platform-enrollment.md)

