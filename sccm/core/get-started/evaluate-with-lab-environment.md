---
title: "Configuration Manager kiértékelése |} Microsoft Docs"
description: "Hozzon létre egy legyen a szervezet a System Center Configuration Manager kiértékelése laborkörnyezetben."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
caps.latest.revision: 25
caps.handback.revision: 0
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0ea90d3f3bef80b8acf9018a1338ae05fc948af4
ms.openlocfilehash: d7ea785ab1beee09b9adda735a87f89bc9481620
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="evaluate-system-center-configuration-manager-by-building-your-own-lab-environment"></a>A System Center Configuration Manager kiértékelése saját laborkörnyezet kiépítésével

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Információk a System Center Configuration Manager kiértékeléséhez használható laborkörnyezet létrehozásához.  

 A System Center Configuration Manager egy összetett és erőteljes eszköz a felhasználók, eszközök és szoftverek kezeléséhez. Alaposan értékelje ki a System Center Configuration Manager teljes telepítése előtt ajánlott, hogy a gyakorlati gyakorlatok fogalmi ismertetése párhuzamosan is.  

 Ez az útmutató elsősorban célja a rendszergazdák, akik kiértékelik a vállalati környezetben használható a Configuration Manager számára:  

-   Rendszergazdák számára, akik a megoldás teljes mértékben a számítógépek, kiszolgálók és mobileszközök kezeléséhez  

-   A magas biztonsági szintű iparágakban a helyszíni Eszközkezelés biztonságát és a felhőalapú Eszközkezelés rugalmasságával igénylő rendszergazdák  

-   Rendszergazdák, akik meg szeretnék felfelé azok helyszíni server architektúra kezelése  

## <a name="what-this-lab-does"></a>A laborgyakorlat célja  
 A fő létrehozása, a laborkörnyezet célja, hogy a felhasználók tisztában vannak a Configuration Manager dolgozni, és a ezáltal elmélyítse a Configuration Manager biztosítson. A Configuration Manager aktuális verziójának gyors összeállítását két kiszolgáló használatával fogja bízná:  

-   Egy, az Active Directory, a tartományvezérlő és a DNS-kiszolgáló tárolja.  

-   Egy, amelyen a Configuration Manager és az összes kapcsolódó SQL Server-összetevőt  

Az ügyfélgépek a Hyper-V-n belül vannak telepítve. A laborkörnyezet teljesen virtualizált rendszerként is futtatható egyetlen kiszolgálón.  

## <a name="what-this-lab-does-not-do"></a>Mi nem célja a laborgyakorlatnak?  
 Ebben a tesztkörnyezetben nem végigvezeti az összes Configuration Manager forgatókönyv. Nem célja a azonnal aktív környezetbe lehessen áttelepíteni.  

 A laborgyakorlat összeállításával egy működő környezettel fog rendelkezni, amelyben dolgozhat. De ebben a környezetben nem lesz optimalizálva a rendszerteljesítmény, merevlemezterület-kezelés és SQL Server tárterület például tényezők.  

##  <a name="BKMK_EvalRec"></a>A labor létrehozása előtt javasolt elolvasni  
 Nincs elérhető rengeteg hasznos tartalom [dokumentáció a System Center Configuration Manager](http://docs.microsoft.com/sccm/). Azt javasoljuk, hogy olvassa el a következő témakörök a könyvtár a labor létrehozása előtt:  

-   A Configuration Manager konzol végfelhasználói portállal és példaforgatókönyvek: kapcsolatos alapfogalmak [System Center Configuration Manager bemutatása](../../core/understand/introduction.md).  

-   További tudnivalók a Configuration Manager elsődleges felügyeleti funkcióit [funkciók és képességek a System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md).  

-   Az ismeretek megerősítése: [a System Center Configuration Manager – alapok](../../core/understand/fundamentals.md).  

-   Ismerje meg, a biztonsági szerepkörök fontosságát [szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../core/understand/fundamentals-of-role-based-administration.md).  

-   További tudnivalók a Tartalomkezelés [tartalomkezelési fogalmak](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Útmutató: a központi telepítés a teljes napi feladatok sikeresen támogatásához [ismertetése ügyfelek és a System Center Configuration Manager szolgáltatáskeresés](../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

