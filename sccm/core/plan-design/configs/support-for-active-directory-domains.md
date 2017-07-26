---
title: "Active Directory-tartományok támogatott |} Microsoft Docs"
description: "A tagsági követelményei a System Center Configuration Manager helyrendszer beolvasása az Active Directory-tartományban."
ms.custom: na
ms.date: 3/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8c5a13f8-42d5-4898-b7b6-e594dae8b335
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f397efe458fd85124d2a83d4a869642015fd4a5
ms.openlocfilehash: 2654ab4eaaaf6a4bf3bd7dca9908e7033647dc2c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="supported-active-directory-domains-for-system-center-configuration-manager"></a>Támogatott a System Center Configuration Manager Active Directory-tartományok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az összes System Center Configuration Manager-helyrendszer egy támogatott Windows Server Active Directory-tartomány tagjának kell lennie. A Configuration Manager ügyfélszámítógépeken lehet tartományi tag vagy egy munkacsoport tagjai.  

 **Követelmények és korlátozások:**  

-   Tartományi tagság a szegélyhálózaton (más néven DMZ, demilitarizált zóna és demilitarizált) internetalapú ügyfélfelügyeletet támogató helyrendszerek vonatkozik.  

-   Egy számítógép, amelyen helyrendszerszerepkör működik a következők módosítása nem támogatott:  

    -   Tartományi tagság  

    -   Tartománynév  

    -   Számítógép neve  

Ezek a módosítások végrehajtása előtt el kell távolítania a helyrendszer-szerepkör (beleértve a helyet, ha azt egy helyrendszer-kiszolgáló).  

**A következő tartományi funkcionális szintű tartományok támogatottak:**  
- Windows Server 2016

- Windows Server 2012 R2  

- Windows Server 2012

- Windows Server 2008 R2

- Windows Server 2008  







##  <a name="bkmk_Disjoint"></a> Különálló névtér  
A Configuration Manager telepítése helyrendszerek és ügyfelek támogatja a különálló névtérrel rendelkező tartományban.  

A különálló névtér forgatókönyvben egyike annak a számítógépnek az elsődleges tartománynévrendszer (DNS) utótag, amelyben az Active Directory DNS-neve nem egyezik a számítógépet tartalmazó. A számítógépet, amelynek az elsődleges DNS-utótagja nem egyezik, különállónak nevezzük. Egy másik különálló névtér forgatókönyv akkor fordul elő, ha a tartományvezérlő NetBIOS-tartománynév nem egyezik meg az Active Directory DNS-neve.  

A következő táblázat ismerteti a különálló névterek támogatott forgatókönyveit.  

|Forgatókönyv|További információ|  
|--------------|----------------------|  
|**1. forgatókönyv:**<br /><br /> A tartományvezérlő elsődleges DNS-utótagja eltér az Active Directory DNS-tartománynevétől. A tartományba tartozó számítógépek lehetnek különállók, vagy nem különállók.|Ebben a forgatókönyvben a tartományvezérlő elsődleges DNS-utótagja eltér az Active Directory DNS-tartománynevétől. Ebben a forgatókönyvben a tartományvezérlő különálló. A tartományban található számítógépek (például a helykiszolgálók és -számítógépek) elsődleges DNS-utótagja a tartományvezérlő elsődleges DNS-utótagjával vagy az Active Directory DNS-tartománynevével egyezik meg.|  
|**2. forgatókönyv:**<br /><br /> Az Active Directory-tartományba tartozó számítógépek még akkor is különállóak, ha a tartományvezérlő nem az.|Ebben a forgatókönyvben egy helyrendszer telepítésének helyt adó, a tartományba tartozó számítógép elsődleges DNS-utótagja eltér az Active Directory DNS-tartománynevétől, de a tartományvezérlő elsődleges DNS-utótagja megegyezik azzal. Ebben a forgatókönyvben a tartományvezérlő nem különálló, de a tartományba tartozó számítógép az. A Configuration Manager-ügyfelet futtató számítógépek lehetnek egy elsődleges DNS-utótagot, az elsődleges DNS-utótagja a különálló helyrendszer-kiszolgáló vagy az Active Directory DNS-tartománynevével egyezik.|  

 Ha engedélyezni szeretné, hogy egy számítógép elérhesse a különálló tartományvezérlőket, módosítsa a **msDS-AllowedDNSSuffixes** Active Directory attribútumát a tartományobjektum-tárolóban. Mindkét DNS-utótagokat hozzá kell adnia a attribútum.  

 Ezenkívül győződjön meg arról, hogy a DNS-utótagok keresési listája, amelyek a szervezeten belül vannak telepítve az összes DNS-névterek tartalmazza-e, hogy konfigurálnia kell a keresési listája az egyes számítógépek a tartományban, amelyhez különálló. Győződjön meg arról, hogy a névterek listája tartalmazza a következőt: az elsődleges DNS-utótagja a tartományvezérlő, a DNS-tartománynevet és összes további névteret azon egyéb olyan kiszolgálókat, a Configuration Manager előfordulhat, hogy működik együtt. A Csoportházirend kezelése konzol segítségével konfiguráhatja a **tartománynévrendszer (DNS) utótag-keresési** listáját.  

> [!IMPORTANT]  
>  Amikor egy számítógépre a Configuration Manager hivatkozik, adja meg a számítógép az elsődleges DNS-utótag használatával. Az utótagnak meg kell egyeznie a teljesen minősített tartománynevét, amely néven van regisztrálva a **dnsHostName** attribútum az Active Directory-tartomány és a rendszer társított egyszerű szolgáltatásnévvel.  

##  <a name="bkmk_SLD"></a> Egycímkés tartományok  
 A Configuration Manager támogatja a helyrendszerek és ügyfelek egycímkés tartományban a következő feltételek teljesülése esetén:  

-   Az Active Directory tartományi szolgáltatások egycímkés tartományt különálló DNS névtér, amely rendelkezik egy érvényes legfelső szintű tartományt kell konfigurálni.  

     **Példa:** A Contoso egycímkés tartomány úgy van konfigurálva, a különálló névtérrel rendelkezzen a contoso.com DNS-ben. Ezért ha megadja a DNS-utótag a Configuration Managerben a Contoso tartományban lévő számítógép, megadhatja "a Contoso.com" és a nem a "Contoso".  

-   A Distributed összetevő Object Model (DCOM) kapcsolatokat a rendszerkörnyezetben található Helykiszolgálók között sikeres kell lennie a Kerberos-hitelesítés használatával.  

