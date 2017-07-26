---
title: "Tűzfalak és a tartományok |} Microsoft Docs"
description: "Beállítása tűzfalak, portok és tartományok előkészítése a System Center Configuration Manager-kommunikáció"
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bd20983eeca47bdd63e0385440e6c8d64901b902
ms.openlocfilehash: 4a2a8f96a900a2c4959ae3ff59232771ece95991
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>Tűzfalak, portok és tartományok a System Center Configuration Manager beállítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Előkészíti a hálózatot a System Center Configuration Manager támogatására, tervezze meg a Configuration Manager által használt kommunikációs infrastruktúrát, például a tűzfalak beállításával.  

|Szempont|Részletek|  
|-------------------|-------------|  
|**Portok és protokollok** , hogy használja-e a Configuration Manager különböző képességeket. Bizonyos portok használata kötelező, és egyéb testreszabható **tartományokat és szolgáltatásokat**.|A legtöbb Configuration Manager-kommunikáció nagyrészt közös portokon HTTP és a 443-as HTTPS-kommunikáció például a 80-as porton. Azonban [bizonyos helyrendszerszerepkörök támogatják az egyéni webhelyek használata](/sccm/core/plan-design/network/websites-for-site-system-servers) és egyéni portok használatát.<br /><br /> **A Configuration Manager telepítése előtt**, azonosíthatja a portokat, amelyet szeretne használni, és megfelelően állítsa be a tűzfalon.<br /><br /> **Ha módosítania kell egy portot** telepítése után a Configuration Manager, ne felejtse el frissíteni eszközökön és a hálózati tűzfalak és is módosítható az a port a Configuration Manager konfigurációja.<br /><br /> További információk: </br>- [Ügyfél-kommunikációs portok konfigurálása](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [A Configuration Managerben használt portok](../../../core/plan-design/hierarchy/ports.md) </br>- [A szolgáltatáskapcsolódási pont a internetelérési követelményei](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)|  
|**Tartományok és szolgáltatások** , hogy Helykiszolgálók és ügyfelek kell használni.|A Configuration Manager képességek megkövetelheti a Helykiszolgálók és ügyfelek hozzáférjenek bizonyos szolgáltatásokhoz és tartományokhoz, például a windowsudpate.microsoft.com webhelyhez vagy a Microsoft Intune szolgáltatással az interneten.<br /><br /> Ha a mobileszközök kezeléséhez a Microsoft Intune fog használni, is be kell állítania a hozzáférést [portok és tartományok, amelyek az Intune-ban van szükség.](https://docs.microsoft.com/en-us/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)|  
|**Proxykiszolgálók** helyrendszer-kiszolgálók és az ügyfél-kommunikációhoz. A különböző helyrendszer-kiszolgálók és ügyfelek külön proxykiszolgálókat is megadhat.|Ezeket a konfigurációkat a helyrendszer-szerepkör vagy az ügyfél telepítése során elvégezni, mert csak kell figyelembe vennie a proxykiszolgáló-konfigurációk későbbi felhasználás helyrendszerszerepkörök és az ügyfelek konfigurálásakor.<br /><br /> Ha nem biztos abban, a központi telepítés kell proxykiszolgálókat használjanak, tekintse át a [proxykiszolgáló-támogatás a System Center Configuration Managerben](../../../core/plan-design/network/proxy-server-support.md) helyrendszerszerepkörök és egy proxykiszolgálót használhat ügyfél műveleteket.|   
|  

