---
title: "Áttelepítési biztonsági és adatvédelmi |} Microsoft Docs"
description: "Ajánlott biztonsági eljárások és adatvédelmi tájékoztatás az áttelepítéshez a System Center Configuration Manager környezetben kapják meg."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6893fce1-7ad5-4151-9ba9-3096871e8e4a
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e3d3f4194b06442e34c10988a20fe9ca40ac5d7
ms.openlocfilehash: 8aa6971d75924ab5bcacd70c330913097ecf8717
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-migration-to-system-center-configuration-manager"></a>Biztonság és adatvédelem a System Center Configuration Manager áttelepítési

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör ajánlott biztonsági eljárások és adatvédelmi tájékoztatás az áttelepítéshez a System Center Configuration Manager környezethez.  

## <a name="security-best-practices-for-migration"></a>Áttelepítés biztonsági védelmének bevált gyakorlata  
 Használja az alábbi ajánlott biztonsági eljárás áttelepítéshez.  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|A felhasználói fiók helyett a forráshely SMS-szolgáltató fiókja és a forráshely SQL Server fiókjaként számítógépfiókját használják.|Ha egy felhasználói fiókot kell használnia az áttelepítéshez, törölje a fiók áttelepítés befejezésekor.|  
|Használjon IPSec protokollt, amikor tartalmat telepít át egy forráshely terjesztési pontról a célhelyi terjesztési pontra.|Bár az áttelepített tartalom kivonatolt, hogy észlelje az illetéktelen módosítást, ha az adatok módosulnak az átvitel közben, az áttelepítés sikertelen lesz.|  
|Korlátozza és figyelje a rendszergazdákat, akik létrehozhatnak áttelepítési feladatokat.|A célhierarchia az adatbázis épségét, hogy a rendszergazda úgy dönt, hogy importálja a forráshierarchia adatok integritásának függ. Emellett a rendszergazda felhasználó minden adatot is olvashat a forráshierarchiából.|  

### <a name="security-issues-for-migration"></a>Az áttelepítés biztonsági kihívásai  
Áttelepítés a következő biztonsági problémákra rendelkezik:  

-   Ügyfelek, amelyek blokkoltak a forráshelyen sikeresen hozzárendelést kaphatnak a célhierarchiában ügyfélrekordjuk áttelepítése előtt.  

     Bár a Configuration Manager megtartja az áttelepített ügyfelek számára a blokkolt állapotát, az ügyfél sikeresen hozzárendelést a célhierarchiában, ha a hozzárendelés az ügyfélrekord áttelepítésének befejezése előtt történik.  

-   A naplózási üzenetek nem települnek át.  

Ha telepít át adatokat a forráshelyről a célhelyre, naplózási információi elvesznek a forráshierarchiából.  

## <a name="privacy-information-for-migration"></a>Adatvédelmi tájékoztatás az áttelepítéshez  
 Az áttelepítés felderíti az adatokat azokból a helyadatbázisokból a forrási infrastruktúrában azonosítható, és ezeket az adatokat az adatbázisban tárolja a célhierarchiában. A System Center Configuration Manager felderíthesse a forráshelyen vagy hierarchiában információkat a szolgáltatásokat, amelyek engedélyezve lettek a forráskörnyezetben, valamint a kezelési műveletek, az adott forráskörnyezetben végrehajtott függ.  

 További információt a biztonsági és adatvédelmi információkat lásd: a következő témaköröket:  

-   További információ az adatvédelemről a Configuration Manager 2007, lásd: [biztonsága és adatvédelme a Configuration Manager 2007](http://go.microsoft.com/fwlink/p/?LinkId=216450) a Configuration Manager 2007 dokumentációs könyvtárában.  

-   A System Center 2012 Configuration Manager adatvédelmi információkkal kapcsolatos további információkért lásd: [biztonsága és adatvédelme a System Center 2012 Configuration Manager](https://technet.microsoft.com/library/gg682033.aspx) a System Center 2012 Configuration Manager dokumentációs könyvtárában.  

-   A System Center Configuration Manager adatvédelmi információkkal kapcsolatos további információkért lásd: [biztonsága és adatvédelme a System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

Áttelepítheti vagy azok egy részét a támogatott adatok egy forráshelyről a célhierarchiába.  

Az áttelepítés alapértelmezés szerint nincs engedélyezve, és több konfigurációs lépésre van szükség. Áttelepítési adatokat a Microsoftnak nem küldi el.  

Olyan forráshierarchiából telepít át adatokat, mielőtt gondolja át az adatvédelmi követelményeit.  

