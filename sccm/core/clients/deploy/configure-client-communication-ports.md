---
title: "Ügyfél-kommunikációs portok konfigurálása |} Microsoft Docs"
description: "A System Center Configuration Manager ügyfél-kommunikációs portok beállítása"
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 406bbdbf-ab4a-4121-a68b-154f96ea14ec
caps.latest.revision: 5
caps.handback.revision: 0
author: robstack
ms.author: robstackmsft
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 63e033fdb436930ac5f37e7408ca9292bc444560
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-client-communication-ports-in-system-center-configuration-manager"></a>Ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Módosíthatja a portszámok, amelyek a System Center Configuration Manager-ügyfelek a HTTP és HTTPS-kommunikációra használó helyrendszerekkel kommunikálnak. Bár a HTTP vagy HTTPS nagyobb eséllyel tartják be van állítva a tűzfalakon, HTTP vagy HTTPS PROTOKOLLT használó ügyfélértesítésnek további CPU-használat és a memória mint egy egyéni portszám a felügyeleti pont számítógépén. Ha hagyományos ébresztési csomagok használatával az ügyfelek felébresztéséhez a portnak a számát is megadható.  

 A HTTP és HTTPS-kérelmek portjának megadásakor megadhat egy alapértelmezett portszámot és egy másodlagos portszámot is. Ügyfelek automatikusan ismételje meg a másik portot, ha nem sikerül az alapértelmezett port a kommunikáció. A HTTP és HTTPS-adatkommunikáció beállításait adhatja meg.  

 Az alapértelmezett értékeket, az ügyfélgépek kérelmeihez használt portszámokról: **80** a HTTP-forgalom és **443-as** a HTTPS-forgalmat. Csak akkor, ha nem szeretné használni az alapértékeket, módosítsa őket. Egyéni portokat használ a jellemző forgatókönyv használata esetén az alapértelmezett webhely helyett egyéni webhelyet az IIS-ben. Ha megváltoztatja az alapértelmezett portszámok, az IIS alapértelmezett webhelye, és más alkalmazások is használhatja az alapértelmezett webhely, valószínűleg sikertelen lesz.  

> [!IMPORTANT]  
>  A következmények átgondolása nélkül ne változtassa meg a portszámokat a Configuration Manager alkalmazásban. Példák:  
>   
>  -   Ha megváltoztatja az ügyfélkérelem-szolgáltatás helykonfigurációban portszámait, és a meglévő ügyfeleket nem állítja be az új portszámok használatára, ezek az ügyfelek felügyelet nélküli ügyfelekké válnak.  
> -   Mielőtt konfigurálna egy nem alapértelmezett portszámot, győződjön meg arról, hogy tűzfalak és az összes beavatkozó hálózati eszköz támogatja ezt a konfigurációt és szükséges, módosítsa megfelelően. Ha Ön kezeli az interneten lévő ügyfelek és módosítsa az alapértelmezett HTTPS portszám 443-as, útválasztók és tűzfalak az interneten blokkolhatják ezt a kommunikációt.  

 Győződjön meg arról, hogy az ügyfelek ne váljanak felügyelet nélküli a portszámok módosítása után, az ügyfelek az új portszámok használatára be kell állítani. Ha megváltoztatja a kérelmek portjait az elsődleges helyen, a csatlakoztatott másodlagos helyek automatikusan öröklik az új portkonfigurációt. Ez a témakör az eljárással konfigurálhatja a kérelmek portjait az elsődleges helyen.  

> [!NOTE]  
>  További információ a Linux és UNIX rendszerű számítógépeken lévő ügyfelek kérelemportjainak konfigurálásáról: [Kérelemportjainak konfigurálása a Linux és UNIX rendszerű ügyfél](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigLnUClientCommuincations).  

 Ha a Configuration Manager-hely közzé van téve az Active Directory tartományi szolgáltatásokban, az információhoz hozzáférő új és meglévő ügyfelek automatikusan konfigurálják a helyük portbeállításait, és nem kell további műveleteket végrehajtania. Az Active Directory Domain Servicesben közzétett információkhoz a következő ügyfelek nem tudnak hozzáférni: munkacsoportba tartozó ügyfelek, másik Active Directory-erdőhöz tartozó ügyfelek, a csak internetes felügyeletre beállított ügyfelek, valamint azok az ügyfelek, amelyek aktuálisan az interneten működnek. Ha ezek az ügyfelek telepítése után megváltoztatja az alapértelmezett portszámok, telepítse újra őket, és az új ügyfelek telepítéséhez az alábbi módszerek egyikének használatával:  

-   Telepítse újra az ügyfeleket az Ügyfélleküldéses telepítés varázsló használatával. Az ügyfélleküldéses telepítés automatikusan konfigurálja a hely aktuális portkonfigurációjának ügyfelek. Az Ügyfélleküldéses telepítés varázsló használatával kapcsolatos további információkért lásd: [Configuration Manager-ügyfelek telepítése Ügyfélleküldés használatával hogyan](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

-   Telepítse újra az ügyfeleket a CCMSetup.exe és a client.msi telepítési tulajdonságait CCMHTTPPORT és CMHTTPSPORT tulajdonságának használatával. Ezek a Tulajdonságok kapcsolatos további információkért lásd: [vonatkozó ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties.md).  

-   Telepítse újra az ügyfelet olyan módszer használatával, amely megkeresi az Active Directory Domain Servicesben a Configuration Manager-ügyfél telepítési tulajdonságait. További információ: [Információ az Active Directory tartományi szolgáltatásokban közzétett ügyfél-telepítési tulajdonságokról a System Center Configuration Managerben](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

 Konfigurálja újra a portszámokat a meglévő ügyfelek, a parancsfájl PORTSWITCH is használhatja. A telepítési adathordozó smssetup\tools\portconfiguration mappájában található a megadott VBS.  

> [!IMPORTANT]  
>  Meglévő és új ügyfelek, amelyek jelenleg az interneten konfigurálnia kell a nem alapértelmezett portszámokat tulajdonságok a CCMSetup.exe client.msi CCMHTTPPORT és CMHTTPSPORT tulajdonságának.  

 Miután megváltoztatta a kérelmek portjait a helyen, a teljes helyre érvényes ügyfélleküldéses telepítési módszer használatával telepített új ügyfelek automatikusan van konfigurálva a hely aktuális portszámainak.  

#### <a name="to-configure-the-client-communication-port-numbers-for-a-site"></a>Az ügyfél kommunikációs portjainak számairól hely konfigurálása  

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.  

2.  Az a **felügyeleti** munkaterületet, bontsa ki a **Helykonfiguráció**, kattintson a **helyek**, és válassza ki a konfigurálni kívánt elsődleges helyre.  

3.  A a **Home** lapra, majd **tulajdonságok**, majd kattintson a **portok** lapon.  

4.  Válassza ki valamelyik elemet, majd kattintson a Tulajdonságok ikonra kattintva jelenítse meg a **Port adatai** párbeszédpanel megnyitásához.  

5.  Az a **Port adatai** párbeszédpanelen adja meg a portszámot és a leírást az elemhez, és kattintson **OK**.  

6.  Válassza ki **egyéni webhely használata** használata, egyéni webhelynevet **SMSWeb** IIS-t futtató helyrendszerek.  

7.  A helyre vonatkozó tulajdonságok párbeszédpanelének bezárásához kattintson az **OK** gombra.  

 Ismételje meg ezt az eljárást a hierarchiában található összes elsődleges helyre vonatkozóan.

