---
title: "Beléptetésihely-rendszerek webhelyei |} Microsoft Docs"
description: "Tudnivalók az alapértelmezett és egyéni webhelyeket a helyrendszer-kiszolgálókhoz a System Center Configuration Managerben."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 681f0893-e83b-476e-9ec0-a5dc7c9deeb6
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26bbec1e8d6c53ce297689ba4390b9347229eb15
ms.openlocfilehash: 886ff3b8e867fc340c79648a57feae81653b0ccd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="websites-for-site-system-servers-in-system-center-configuration-manager"></a>Helyrendszer-kiszolgálók webhelyei a System Center Configuration Manager alkalmazásban

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Több Configuration Manager helyrendszer-szerepkörök Microsoft Internet Information Services (IIS) használata szükséges, és használja az alapértelmezett IIS-webhely a helyrendszeri szolgáltatások működtetéséhez. Ha más webes alkalmazásokat is kell futtatnia kiszolgáló és a beállítások nem kompatibilisek a Configuration Managerrel, fontolja meg egy egyéni webhely használatát a Configuration Manager.  

> [!TIP]  
>  Biztonsági szempontból ajánlott hoz dedikáljon külön kiszolgálót az IIS szolgáltatást igénylő Configuration Manager helyrendszerekhez. Ha más webalkalmazásokat is futtatnia a Configuration Manager helyrendszer, növeli az adott számítógép támadási felületét.  




##  <a name="BKMK_What2Know"></a>Tudnivalók az egyéni webhelyek használatának kiválasztása előtt  
 Alapértelmezés szerint a helyrendszerszerepkörök az IIS **alapértelmezett webhelyét** használják. Ez be van állítva automatikusan a helyrendszer-szerepkör telepítésekor. Az elsődleges helyeken azonban ehelyett egyéni webhelyeket is használhat. Ha egyéni webhelyeket használ:  

-   Egyéni webhelyek engedélyezve vannak az egyes helyrendszer-kiszolgálók vagy szerepkörök ahelyett, hogy a teljes hely.  

-   Az elsődleges helyeken minden egy alkalmazható helyrendszerszerepkört futtató számítógépre kell kell állítani a nevű egyéni webhely **SMSWEB**. Amíg ezt a webhelyet hoz létre, és a helyrendszer-szerepkörök adott számítógépen lévő beállítása az egyéni webhely használatára, előfordulhat, hogy ügyfelek nem lesznek képesek kommunikálni a helyrendszer-szerepkörök adott számítógépen.  

-   Mivel a másodlagos helyek automatikusan egyéni webhely használatára, ha az elsődleges szülőhely úgy van beállítva, így akkor is létre kell hoznia egyéni webhelyet az IIS-ben minden másodlagos helyrendszer-kiszolgálóra, amely szükséges az IIS vannak beállítva.  


  **Egyéni webhelyek használatának előfeltételei:**  

 Mielőtt engedélyezné az egyéni webhely használatát a helyen, el kell végeznie a következőket:  

-   Létre kell hoznia egy **SMSWEB** nevű egyéni webhelyet az IIS szolgáltatásban minden olyan helyrendszer-kiszolgálón, amelyhez szükséges az IIS használata. Ezt az elsődleges helyen és az alárendelt másodlagos helyeken is végezze el.  

-   Állítsa be az egyéni webhely ugyanazt a portot, amely a Configuration Manager ügyfél-kommunikációhoz (ügyfélkérelmekhez használt port) beállítása válaszolni.  

-   Minden egyéni vagy alapértelmezett webhely egyéni mappát használó, egy példányt az alapértelmezett dokumentum adja meg a webhelyet tároló gyökérmappába az a hely számára. Például egy Windows Server 2008 R2 rendelkező számítógépen alapértelmezett konfigurációjú **iisstart.htm** az alapértelmezett egyik rendelkezésre álló típusok. Ez a fájl az alapértelmezett webhely gyökérkönyvtárában található, és ezt a fájlt (vagy az alapértelmezett dokumentum adja meg a másolata) másolata majd helyez az egyéni SMSWEB webhelyet tároló gyökérmappába. Alapértelmezett dokumentumtípusokkal kapcsolatos további [alapértelmezett dokumentum &lt;defaultDocument\> az IIS](http://www.iis.net/configreference/system.webserver/defaultdocument).  

**Az IIS követelményeiről:**
**a következő helyrendszerszerepkörökhöz szükséges az IIS és a webhely a helyrendszeri szolgáltatások futtatására:**  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Terjesztési pont  

-   Beléptetési pont  

-   Beléptetési proxypont  

-   Tartalék állapotkezelő pont  

-   Felügyeleti pont  

-   Szoftverfrissítési pont  

-   Állapotáttelepítési pont  

További szempontok:  

-   Egy elsődleges hely egyéni webhelyeket engedélyezve van, ha adott helyhez rendelt ügyfelek a rendszer átirányítja a megfelelő helyrendszer-kiszolgáló alapértelmezett webhelyek helyett az egyéni webhelyek kommunikálni  

-   Ha egy elsődleges helyhez egyéni webhelyeket használ, fontolja meg a hierarchiájában, és győződjön meg arról, hogy az ügyfelek sikeresen választhatnak a hierarchiában összes elsődleges hely egyéni webhelyeket. (Barangolásról akkor beszélünk, ha egy ügyfélszámítógép egy másik hely által kezelt új hálózati szegmensbe kerül. Barangolás befolyásolhatja erőforrásokat, amelyek egy ügyfél érhet el helyileg ahelyett, hogy WAN-kapcsolaton keresztül).  

-   Helyrendszer-szerepkörök, amelyek használják az IIS szolgáltatást, de nem fogadnak ügyfélcsatlakozást, például a jelentéskészítési szolgáltatási pont az egyéni SMSWEB webhelyet is használhatja az alapértelmezett webhely helyett.  

-   Egyéni webhelyek hozzárendelését követelik meg, amely eltérő a számítógép alapértelmezett webhely által használt portszámokat. Egy alapértelmezett és egy egyéni webhely nem futhat egyszerre, ha mindkét webhely ugyanazokat a TCP/IP-portokat próbálja használni.  

-   A TCP/IP-portokat, amelyeket állít be az IIS Szolgáltatásban az egyéni webhely számára meg kell egyeznie a hely ügyfélkérelmeinek.  

## <a name="switch-between-default-and-custom-websites"></a>Váltás az alapértelmezett és az egyéni webhelyek között  
Bár ellenőrizheti, vagy törölje a jelet az egyéni webhelyek egy elsődleges helyen (a beállítás a hely tulajdonságainak Általános lapján) bármikor jelölőnégyzetből, tervezze meg gondosan a módosítás előtt. Ha módosítja a konfigurációt, a alkalmazható helyrendszerszerepkört az elsődleges helyen és az alárendelt másodlagos helyének kell eltávolítása és újratelepítése:  

A rendszer a következő szerepköröket **automatikusan újratelepíti**:  

-   Felügyeleti pont  

-   Terjesztési pont  

-   Szoftverfrissítési pont  

-   Tartalék állapotkezelő pont  

-   Állapotáttelepítési pont  

A következő szerepköröket **manuálisan kell újratelepíteni**:  

-   Alkalmazáskatalógus webszolgáltatási pontja  

-   Alkalmazáskatalógus weboldal-elérési pontja  

-   Beléptetési pont  

-   Beléptetési proxypont  

Egyéb rendelkezések:  

-   Ha megváltoztatja az alapértelmezett webhelyről egyéni webhely használatára, a Configuration Manager nem távolítja el a régi virtuális könyvtárakat. Ha el szeretné távolítani a Configuration Manager által használt fájlokat, kézzel kell törölnie a virtuális könyvtárakat, amelyek az alapértelmezett webhely alatt lettek létrehozva.  

-   Ha módosítja a hely egyéni webhelyeket használjon, a helyhez már hozzárendelt ügyfeleket újra kell konfigurálni az új ügyfélkérelmekhez használt portok az egyéni webhelyek használata. Lásd: [ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-communication-ports.md).  

## <a name="set-up-custom-websites"></a>Egyéni webhelyek beállítása  
Mivel az egyéni webhelyek létrehozásának lépései a különböző operációsrendszer-verziókban eltérőek, a pontos lépéseket a saját operációsrendszer-verziójára vonatkozó dokumentációban találhatja meg, de ha alkalmazhatók, használja a következő információkat:  

-   A webhely neve legyen: **SMSWEB**.  

-   HTTPS beállításakor a konfigurálás mentése előtt meg kell adnia egy SSL-tanúsítványt.  

-   Az egyéni webhely létrehozása után távolítsa el az egyéni webhely portjait, amelyekkel az IIS más webhelyeiről:  

    1.  Szerkessze a **kötések** a más webhelyek távolítsa el, amelyek pontosan megegyeznek portjait rendelt a **SMSWEB** webhely.  

    2.  Indítsa el a **SMSWEB** webhelyet.  

    3.  Indítsa el újra az **SMS_SITE_COMPONENT_MANAGER** szolgáltatást a hely helykiszolgálóján.  

