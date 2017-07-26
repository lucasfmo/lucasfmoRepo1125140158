---
title: "A helyszíni MDM - Configuration Manager telepítése a szerepkörök |} Microsoft Docs"
description: "Helyrendszerszerepkörök telepítése a helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
caps.latest.revision: 9
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 4913606e2f8a36e0004f711b24ecd836d0485124
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="install-site-system-roles-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Helyrendszerszerepkörök telepítése a helyszíni mobileszközök kezeléséhez a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a\-helyszíni mobileszköz-kezelés a Configuration Manager-hely infrastruktúráját a következő helyrendszerszerepköröket igényli:  

-   Beléptetési pont  

-   Beléptetési proxypont  

-   Terjesztési pont  

-   Eszközfelügyeleti pont  

-   Szolgáltatáskapcsolódási pont  

 Ha a hozzáadni kívánt\-helyszíni mobileszköz-kezelés, amely a legtöbb számítógépet és a Configuration Manager ügyfélszoftver segítségével felügyelt eszközöket a szervezetben, lehetséges, hogy a meglévő infrastruktúra részeként már telepített helyrendszerszerepkörök többsége. Ha nem, lásd: [a System Center Configuration Manager helyrendszer-szerepkörök hozzáadásához](../../core/servers/deploy/configure/add-site-system-roles.md) adja hozzá a webhely teljes olvashat.  

> [!NOTE]  
>  Ha az eszköz felügyeleti pont helyrendszerszerepkörrel adatbázis-replikákat használ, az újonnan beléptetett eszközöket csak akkor fognak kapcsolódni az eszközfelügyeleti pont, amíg az adatbázis-replikát szinkronizálja azt. Ez a kapcsolódási hiba akkor fordul elő, mert az adatbázis-replika nem rendelkezik az újonnan regisztrált eszközről, a sikeres csatlakozáshoz szükséges információt. Replikák szinkronizálása 5 percenként, így eszközök nem fogják tudni csatlakoztatni az első 5 perc után beléptetési (általában 2 kapcsolódási kísérletek), amely után az eszköz sikeresen fog csatlakozni a.  

 E meglévő helyrendszerszerepköröket használ, vagy újakat ad hozzá, konfigurálnia kell azokat a modern eszközök kezelésére használható. A terjesztési pont és a működéséhez az eszközfelügyeleti pont konfigurálása az alábbi lépésekkel\-helyszíni mobileszköz-kezelés:  

> [!NOTE]  
>  A Configuration Manager aktuális ágának csak az intranetes kapcsolatokat támogatja eszközökről a terjesztési pontokra és az eszközfelügyeleti pontjain lévő\-helyszíni mobileszköz-kezelés. Azonban Ha Mac OS X rendszerű számítógépek is kezel, ezek az ügyfelek ezen helyrendszerszerepkörökhöz internetes kapcsolatokat igényelnek. Ebben az esetben a terjesztési pont és az eszközfelügyeleti pont tulajdonságainak konfigurálásakor kell használnia a **intranetes és internetes kapcsolatok engedélyezése** beállítást használja.  

### <a name="to-configure-site-system-roles-to-manage-modern-devices"></a>Helyrendszerszerepkörök modern eszközök kezelésére való konfigurálása:  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **kiszolgálók és Helyrendszerszerepkörök**.  

2.  Jelölje be helyrendszer-kiszolgáló a terjesztési pontot vagy az eszközfelügyeleti ponton szeretne konfigurálni, nyissa meg az tulajdonságait **helyrendszer** , és győződjön meg arról, hogy van megadva teljes tartománynév. Kattintson az **OK** gombra.  

3.  Nyissa meg a terjesztési pont tulajdonságait helyrendszer-szerepkör. Az Általános lapon győződjön meg arról, hogy **HTTPS** kiválasztva, és jelölje be **engedélyezése csak az intranetes kapcsolatok**.  

     Ha Mac számítógépeket a Configuration Manager-ügyféllel külön is felügyel, **intranetes és internetes kapcsolatok engedélyezése** helyette.  

    > [!NOTE]  
    >  Az intranetes kapcsolatokhoz konfigurált terjesztési pontokon helyhatárokat beállítani szükséges. A Configuration Manager aktuális ágának csak támogatja az IPv4-tartományok határait\-helyszíni mobileszköz-kezelés. Helyhatárok konfigurálásáról további információkért lásd: [helyhatárok és határcsoportok megadása a System Center Configuration Manager](../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

4.  Jelölje be a jelölőnégyzetet a **engedélyezze a terjesztési ponthoz való csatlakozás eszközök**, és kattintson a **OK**.  

5.  Nyissa meg a felügyeleti pont tulajdonságait helyrendszer-szerepkör. Az Általános lapon győződjön meg arról, hogy **HTTPS** kiválasztva, majd jelölje be **engedélyezése csak az intranetes kapcsolatok**.  

     Ha Mac számítógépeket a Configuration Manager-ügyféllel külön is felügyel, **intranetes és internetes kapcsolatok engedélyezése** helyette.  

6.  Jelölje be a jelölőnégyzetet a **mobil eszközök és a Mac számítógépen, hogy a felügyeleti pont használatának engedélyezése**. Kattintson az **OK** gombra.  

     Ez gyakorlatilag egy eszközfelügyeleti ponttá a felügyeleti pontot bekapcsolása.  

 Ha a helyrendszer-szerepkörök hozzáadása és modern eszközök kezelésére konfigurálva, majd konfigurálja a megbízható végpontként regisztrálása és a felügyelt eszközökkel való kommunikáció során a szerepköröket üzemeltető kiszolgálókat kell. Lásd: [helyszíni mobileszközök kezeléséhez a System Center Configuration Manager megbízható kommunikációhoz szükséges tanúsítványok beállítása](../../mdm/get-started/set-up-certificates-on-premises-mdm.md) további információt.  

