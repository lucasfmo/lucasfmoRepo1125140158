---
title: "Magas kockázatú központi telepítések felügyeletéhez szükséges |} Microsoft Docs"
description: "Megtudhatja, hogyan konfigurálja a hely beállításait a System Center Configuration Manager figyelmeztető rendszergazdák, ha a magas kockázatú központi telepítést hoznak létre."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 8b5564f39f07a67a3c9278379ed59ca415603d21
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="settings-to-manage-high-risk-deployments-for-system-center-configuration-manager"></a>A System Center Configuration Manager magas kockázatú telepítések felügyeletéhez szükséges beállításai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Managerrel, konfigurálhatja a hely beállításait, melyek figyelmeztetik a rendszergazda Ha a magas kockázatú feladatütemezési központi telepítést hoznak létre. A magas kockázatú központi telepítés:  

-   Egy automatikusan végzett központi telepítés  

-   Nem várt eredményekhez vezethet  

 Például egy feladatütemezést, amely célú **szükséges** egy operációs rendszert központilag telepítő nagy kockázatúnak minősül.  

 Nem kívánt magas kockázatú központi telepítés kockázatának csökkentése érdekében, konfigurálhatja a központi telepítés ellenőrzési beállításai a méretkorlátozásokról:  

-   **Gyűjtemény méretkorlátozásai**: A központi telepítés meghaladja a határt több ügyfelet tartalmazó gyűjtemények elrejtése.  

    -   **Alapértelmezett méret**: Ez a beállítás alapértelmezés szerint gyűjteményeket, amelyek több ügyfelet, mint a korlátot, a központi telepítés létrehozásakor elrejti. Megtekintheti ezeket a gyűjteményeket továbbra is a központi telepítés létrehozásakor, de alapértelmezés szerint el vannak rejtve. Az alapértelmezett érték 100. A beállítás figyelmen kívül hagyásához írja be a 0 értéket.  

    -   **Maximális méret**: Ez a beállítás mindig elrejti a gyűjteményeket, amelyek több ügyfelet, mint a korlátot, a központi telepítés létrehozásakor. Az alapértelmezett érték 0, amely a beállítás figyelmen kívül hagyását eredményezi. A **Maximális méret** értékének nagyobbnak kell lennie az **Alapértelmezett méret** értékénél.  

     Állítsa például **alapértelmezett méret** 100 és a **maximális mérete** beállításé pedig 1000. A magas kockázatú központi telepítés létrehozásakor a **gyűjtemény választása** ablak csak jelenik meg a gyűjteményeket, amelyek 100-nál kevesebb ügyfelet tartalmaznak. Ha törli a **elrejtése gyűjtemények száma nagyobb, mint a siteâ "™ s minimális méretre vonatkozó konfigurációja** beállítás, az ablak megjeleníti az 1000-nél kevesebb ügyfelet tartalmazó gyűjteményeket.  

-   **Helyrendszer-kiszolgálókat tartalmazó gyűjtemények**: Letilthatja a központi telepítéseket, vagy a telepítés létrehozása, ha a célgyűjtemény helyrendszerszerepkörrel rendelkező számítógépet tartalmaz előtt ellenőrzést követelhet meg. Ha egy telepítés le van tiltva, ki kell választania egy másik gyűjteményt, amely megfelel a telepítés ellenőrzési követelményeinek.  

> [!NOTE]  
>  A magas kockázatú központi telepítések mindig az egyéni, a felhasználó által létrehozott, valamint a beépített **Ismeretlen számítógépek** gyűjteményre korlátozódnak. Magas kockázatú központi telepítés létrehozásakor nem jelölhet ki olyan beépített gyűjteményeket, mint a **Minden rendszer**.  

### <a name="to-configure-deployment-verification-for-a-site"></a>A telepítés ellenőrzésének konfigurálása egy helyhez  

1.  Kattintson a Configuration Manager konzol **felügyeleti** >**Helykonfiguráció** > **helyek**, majd válassza ki a konfigurálni kívánt elsődleges helyre.  

2.  A a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**, majd válassza a **telepítés ellenőrzésének** lapon.  

3.  Miután beállította a használni kívánt konfigurációkat, válassza ki a **OK** a konfiguráció mentéséhez.  

### <a name="see-also"></a>További információ  
 [Helyek és hierarchiák a System Center Configuration Manager konfigurálása](../../core/servers/deploy/configure/configure-sites-and-hierarchies.md)

