---
title: "Helyrendszerszerepkörök telepítése |} Microsoft Docs"
description: "Varázslók segítségével helyrendszer-szerepkörök hozzáadása egy meglévő vagy új helyrendszer-kiszolgálóra a helyen."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61f5c774-7667-44ae-b8e4-a4951318b183
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8370e3b102afed518e8154d4944ab420188faccf
ms.openlocfilehash: 76b070f8e203cc0c751f35e5a4b4904504786c04
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="install-site-system-roles-for-system-center-configuration-manager"></a>Helyrendszerszerepkörök hozzáadása a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager konzol segítségével helyrendszerszerepkörök telepítése két varázslók rendelkezik:  

-   **Helyrendszer-szerepkörök hozzáadása varázsló**: A varázsló segítségével helyrendszer-szerepkörök hozzáadása egy meglévő helyrendszer-kiszolgáló a helyen.  

-   **Helyrendszer-kiszolgáló létrehozása varázsló**: A varázsló segítségével adja meg az új kiszolgáló helyrendszer-kiszolgálót, és telepítse egy vagy több helyrendszer-szerepkörök a kiszolgálón. Ez a varázsló megegyezik a **helyrendszer-szerepkörök hozzáadása varázslóval**, azzal a különbséggel, hogy az első oldalon meg kell adnia a nevét a kiszolgáló és a hely, amelyben telepíteni szeretné.  

Egy helyrendszer-szerepkör (beleértve az SMS-szolgáltató példánya) távoli számítógépen való telepítésekor a távoli számítógép számítógépfiókját kerül, a helykiszolgáló helyi csoportjához. Ha a hely tartományvezérlőn van telepítve, a csoport a helykiszolgálón egy helyi csoport helyett tartományi csoport. Ebben az esetben a távoli helyrendszer-szerepkör nincs működési mindaddig, amíg a hely system szerepkör számítógép újraindul, vagy a Kerberos-jegy frissítik a távoli számítógép fiókjához tartozó. További információk: [A System Center Configuration Managerben használt fiókok](../../../../core/plan-design/hierarchy/accounts.md).  

A helyrendszer-szerepkör telepítése, előtt közvetlenül a Configuration Manager ellenőrzi a célszámítógép megfelel a kiválasztott helyrendszerszerepkörök előfeltételeit. A következő helyrendszerszerepkörök telepítéséről megismerése:  

-   Alapértelmezés szerint a Configuration Manager telepíti a helyrendszerszerepkört, ha a telepítési fájlok lesznek telepítve az első elérhető NTFS formátumú lemezegységre a legtöbb szabad lemezterülettel rendelkezik. A Configuration Manager adott lemezegységeken, hozzon létre egy üres fájlt **no_sms_on_drive.sms**. Másolja a meghajtó gyökérmappájába a helyrendszer-kiszolgáló telepítése előtt.  

-   A Configuration Manager használ a **helyrendszer-telepítési fiók** helyrendszerszerepkörök telepítéséhez. Ez a fiók hozzon létre egy új helyrendszer-kiszolgáló vagy a helyrendszer-szerepkörök hozzáadása egy meglévő helyrendszer-kiszolgálóra vonatkozó varázslóban adja meg. Alapértelmezés szerint ez a fiók a helyi rendszer fiók a helykiszolgáló számítógépén, de megadhatja a helyrendszer-telepítési fiók egy tartományi felhasználói fiókot. További információk: [A System Center Configuration Managerben használt fiókok](../../../../core/plan-design/hierarchy/accounts.md).  

##  <a name="bkmk_Install"></a>Helyrendszerszerepkörök telepítése egy meglévő helyrendszer-kiszolgálón  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Kiszolgálók és helyrendszerszerepkörök**elemre. Ezután válassza ki az új helyrendszerszerepkörökhöz használni kívánt kiszolgálót.  

3.  A **Kezdőlap** **Kiszolgáló** csoportjában kattintson a **Helyrendszerszerepkörök hozzáadása**elemre.  

4.  Az a **általános** lapon tekintse át a beállításokat, és kattintson a **következő**.  

    > [!TIP]  
    >  Az Internet eléréséhez a helyrendszer-szerepkör, győződjön meg arról, hogy megadja az internetes teljesen minősített tartománynevét (FQDN).  

5.  Az a **Proxy** csoportjában adja meg egy proxykiszolgáló beállításait, ha a helyrendszer-kiszolgálón futó helyrendszer-szerepkörök proxykiszolgáló az interneten lévő helyekhez való csatlakozáshoz szükséges. Ezután kattintson a **Tovább** gombra.  

6.  Az a **Rendszerszerepkör kiválasztása** lapon, válassza ki a helyrendszer-szerepkörök hozzáadása, és kattintson a kívánt **következő**.  

7.  Fejezze be a varázslót.  

> [!TIP]  
>  A Windows PowerShell-parancsmag, a New-CMSiteSystemServer, az ezzel az eljárással azonos funkciót hajt végre. További információkért lásd: [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) a System Center 2012 Configuration Manager SP1 parancsmagokat ismertető dokumentációjában.  

## <a name="to-install-site-system-roles-on-a-new-site-system-server"></a>Helyrendszerszerepkörök telepítése új helyrendszer-kiszolgálón  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Kiszolgálók és helyrendszerszerepkörök**elemre.  

3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Helyrendszer-kiszolgáló létrehozása**lehetőségre.  

4.  Az **Általános** lapon adja meg a helyrendszer általános beállításait, majd kattintson a **Tovább**gombra.  

    > [!TIP]  
    >  Az új helyrendszerszerepkör hozzáférni az internetről, adjon meg egy internetes teljes Tartománynevet.  

5.  Az a **Proxy** csoportjában adja meg egy proxykiszolgáló beállításait, ha a helyrendszer-kiszolgálón futó helyrendszer-szerepkörök proxykiszolgáló az interneten lévő helyekhez való csatlakozáshoz szükséges. Ezután kattintson a **Tovább** gombra.  

6.  Az a **Rendszerszerepkör kiválasztása** lapon, válassza ki a helyrendszer-szerepkörök hozzáadása, és kattintson a kívánt **következő**.  

7.  Fejezze be a varázslót.  

> [!TIP]  
>  A Windows PowerShell-parancsmag, a New-CMSiteSystemServer, az ezzel az eljárással azonos funkciót hajt végre. További információkért lásd: [New-CMSiteSystemServer](http://go.microsoft.com/fwlink/p/?LinkID=271414) a System Center 2012 Configuration Manager SP1 parancsmagokat ismertető dokumentációjában.  

