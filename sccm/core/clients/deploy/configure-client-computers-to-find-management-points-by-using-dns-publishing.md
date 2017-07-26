---
title: "Ügyfelek keresése felügyeleti pontok DNS-közzététel konfigurálása |} Microsoft Docs"
description: "Állítsa be a felügyeleti pont keresésére DNS-közzététel segítségével a System Center Configuration Manager ügyfélszámítógépeken."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 03cec407-0f9f-454f-a360-b005af738d29
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d016ec3fe106b2d90b3c14b4f9296aed4d198644
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-computers-to-find-management-points-by-using-dns-publishing-in-system-center-configuration-manager"></a>Konfigurálása az ügyfélszámítógépek számára, hogy a felügyeleti pont keresésére DNS-közzététel segítségével a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager ügyfelek elő kell készítenie a felügyeleti pontok végzik a helyhozzárendelést és a további folyamatos felügyelet folytatásához. Az intraneten a legbiztonságosabb módszer a felügyeleti pontok megtalálására az ügyfelek által az Active Directory tartományi szolgáltatások használata. Ha azonban az ügyfelek nem használhatják ezt a szolgáltatáskeresési módszert (például nem lett kibővítve az Active Directory séma, vagy az ügyfelek munkacsoportiak), elsődleges szolgáltatáskeresési módszerként használható a DNS-közzététel.  

> [!NOTE]  
>  Linux vagy UNIX alapú ügyfél telepítésekor, kezdeti kapcsolati pontként felügyeleti pontot kell megadni. Az ügyfél Linux és UNIX rendszerű telepítésével kapcsolatos információkért lásd: [üzembe helyezése UNIX és Linux-kiszolgálókon a System Center Configuration Manager ügyfelek](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

 A DNS-közzététel felügyeleti pontokhoz használata előtt, meg kell győződni arról, hogy az intraneten a DNS kiszolgálók rendelkeznek a szolgáltatási hely erőforrásrekordjaival (SRV RR) és a megfelelő gazdagép (A vagy AAA) erőforrásrekordjaival a helyfelügyeleti pont részére. A szolgáltatási hely erőforrásrekordjait automatikusan létrehozhatók, a Configuration Manager által, vagy manuálisan, a DNS azon rendszergazdája, aki a rekordokat hozza létre a DNS-ben.  

 További információ a DNS-közzétételről mint a szolgáltatás helyének meghatározására szolgáló módszerről a Configuration Manager-ügyfelek: [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

 Az ügyfelek alapértelmezetten a DNS tartományuk felügyeleti pontjaiban keresnek. Azonban ha az ügyfelek tartomány közzétéve felügyeleti pont, manuálisan konfigurálnia kell az ügyfelek egy felügyeleti pont DNS-utótagot. Ez a DNS-utótag konfigurálható az ügyfelekhez a telepítésük közben vagy után:  

-   Az ügyfelekhez a telepítésük közben a felügyeleti pont utótagja a CCMSetup Client.msi tulajdonságaival konfigurálható.  

-   Az ügyfelekhez a telepítésük után a felügyeleti pont utótagja a Vezérlőpulton a **Configuration Manager - Tulajdonságok**használatával konfigurálható.  

#### <a name="to-configure-clients-for-a-management-point-suffix-during-client-installation"></a>A felügyeleti pont utótagjának ügyfelekhez konfigurálása a telepítésük közben  

-   Az ügyfelet a CCMSetup Client.msi következő tulajdonságával kell telepíteni:  

    -   **DNSSUFFIX =**  *&lt;felügyeletipont-tartomány\>*  

         Ha a hely több felügyeleti ponttal rendelkezik, és azok több tartományban vannak, csak egyet adjon meg. Ha az ügyfelek felügyeleti ponthoz csatlakoznak ebben a tartományban, letöltik az elérhető felügyeleti pontok listáját, ami más tartományok felügyeleti pontjait is tartalmazza.  

     CCMSetup parancssori tulajdonságaival kapcsolatos további információkért lásd: [vonatkozó ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties.md).  

#### <a name="to-configure-clients-for-a-management-point-suffix-after-client-installation"></a>A felügyeleti pont utótagjának ügyfelekhez konfigurálása a telepítésük után  

1.  Az ügyfélszámítógépen navigáljon a Vezérlőpult **Configuration Manager**eleméhez, majd kattintson rá duplán a **Tulajdonságok**elemre.  

2.  A **Hely** lapon adja meg a felügyeleti pont DNS-utótagját, majd kattintson az **OK**gombra.  

     Ha a hely több felügyeleti ponttal rendelkezik, és azok több tartományban vannak, csak egyet adjon meg. Ha az ügyfelek felügyeleti ponthoz csatlakoznak ebben a tartományban, letöltik az elérhető felügyeleti pontok listáját, ami más tartományok felügyeleti pontjait is tartalmazza.

