---
title: "Áttelepítési Előfeltételek |} Microsoft Docs"
description: "Ismerje meg a Configuration Manager támogatott forráshely nyelv és az áttelepítéshez szükséges konfigurációk támogatott verzióit."
ms.custom: na
ms.date: 3/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec976930-7467-4d3c-b33c-991bf408a74a
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ee7f69bd65152deffb2456d9807e1e8fee8802ec
ms.openlocfilehash: cd90f5462ac4bb4c0a2021e6d5dde65161b9c5f6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-migration-in-system-center-configuration-manager"></a>A migrálás előfeltételei a System Center Configuration Manager rendszerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Áttelepítéséhez a támogatott forráshierarchiából, a System Center Configuration Manager áttelepítési műveletek konfigurálására és futtatására célhely belül alkalmazható a Configuration Manager-forráshelyről, és engedélyek hozzáféréssel kell rendelkeznie.  

 Olvassa el a következő szakaszok segítenek megérteni a Configuration Manager verziói által támogatott az áttelepítést, és a konfigurálást.  

-   [A Configuration Manager áttelepítéshez támogatott verziói](#BKMK_SupportedMigrationVersions)  

-   [Az áttelepítéshez támogatott forráshelyi nyelvek](#BKMK_SorceSiteLanguage)  

-   [Az áttelepítéshez szükséges konfigurációk](#BKMK_Required_Configurations)  

##  <a name="BKMK_SupportedMigrationVersions"></a> A Configuration Manager áttelepítéshez támogatott verziói  
 A Configuration Manager következő verzióinak bármelyikét futtató forráshierarchiából áttelepítheti az adatokat:  

-   A Configuration Manager 2007 SP2 (áttelepítéshez, a Configuration Manager 2007 R2 vagy R3 verzióját a forráshely a rendszer nem veszi figyelembe. Mindaddig, amíg a forrás hely fut SP2, helyek az R2 vagy az R3 verziójú bővítmény telepítve vannak támogatva az áttelepítéshez a System Center Configuration Manager).  

-   A System Center 2012 Configuration Manager SP2 vagy System Center 2012 R2 Configuration Manager SP1.  

    > [!TIP]  
    >  Az áttelepítés mellett a System Center 2012 Configuration Manager-System Center Configuration Manager futtató helyek helyszíni frissítését is használhatja.  

-   A System Center Configuration Manager hierarchiája a System Center Configuration Manager azonos vagy régebbi verzió.  

  Például ha a rendeltetési hierarchiában, amely futtatja a System Center Configuration Manager 1606, használhat áttelepítési adatok másolása egy 1606 vagy az 1602-es verzióját futtató forráshierarchia. Azonban Ön nem tudta áttelepíteni adatokat a forráshierarchia 1610 futtató.  


##  <a name="BKMK_SorceSiteLanguage"></a> Az áttelepítéshez támogatott forráshelyi nyelvek  
 Configuration Manager-hierarchia közötti áttelepítésekor az adatok a célhierarchiában a nyelvileg semleges formátumban tárolódik a System Center Configuration Manager. Konfigurációs Manager2007 nem tárolja nyelvileg semleges formátumúak adatok, mert az áttelepítési folyamat kell ezeket az objektumokat konvertálnia formátuma az áttelepítés során a Configuration Manager 2007. Ezért csak a Configuration Manager 2007 forráshelyei, amely a következő nyelvek valamelyikével lettek telepítve vannak támogatva az áttelepítéshez:  

-   Angol  

-   Francia  

-   Német  

-   Japán  

-   koreai  

-   Orosz  

-   Egyszerűsített kínai  

-   Kínai (hagyományos)  

Ha a System Center 2012 Configuration Manager vagy a System Center Configuration Manager hierarchiából telepít át adatokat, nincsenek nincs korlátozás a forráshely nyelvére. A forráshely adatbázisában az objektumok már nyelvileg semleges formátumúak.  

##  <a name="BKMK_Required_Configurations"></a> Az áttelepítéshez szükséges konfigurációk  
Az áttelepítéshez és az áttelepítési műveletekhez szükséges konfigurációk a következők:  

-   **Konfigurálása, futtatása és figyelése a Configuration Manager konzolon áttelepítési:**  

     A célként megadott helyen az Ön fiókjához társítva kell lenni a szerepkör alapú **Infrastruktúra-rendszergazda**biztonsági szerepkörnek. Ez a biztonsági szerepkör engedélyezi az összes áttelepítési műveletet, amelyek közé tartozik az áttelepítési feladatok létrehozása, a tisztítás, a figyelés, valamint a terjesztési pontok megosztási és frissítési művelete is.  

-   **Adatgyűjtés:**  

     Ahhoz, hogy a célhely adatgyűjtést végezzen, az egyes forráshelyek részére a következő két forráshely-elérési fiókot kell konfigurálni:  

    -   **Forráshelyfiók:** Ennek a fióknak a forráshelyi SMS Provider elérésére szolgál.  

        -   Egy konfigurációs Manager2007 SP2 forráshelye esetén ennek a fióknak szükséges **olvasási** engedéllyel valamennyi forráshelyi objektumhoz.  

        -   A System Center 2012 Configuration Manager vagy a System Center Configuration Managerben forráshelyi adatbázisfiókot a fióknak **olvasási** engedély valamennyi forráshelyi objektumhoz, engedélyeket a fiókhoz szerepkör alapú felügyelettel. A szerepköralapú felügyelet használatáról lásd: [A System Center Configuration Manager szerepköralapú adminisztrációjának alapjai](../../core/understand/fundamentals-of-role-based-administration.md).  

    -   **Forráshelyi adatbázisfiók:** Ez a fiók használható a forráshely SQL Server-adatbázis eléréséhez, és megköveteli **Connect**, **Execute**, és **kiválasztása** engedélyeket a forráshely adatbázisához.  

    Ezek a fiókok konfigurálhatók az új forráshierarchia konfigurálásakor, kiegészítő forráshely adatgyűjtésekor, illetve akkor, amikor újrakonfigurálja a forráshely hitelesítőadatait. Ezek a fiókok használhatnak tartományi felhasználói fiókot, vagy megadhatja részükre a célhierarchia legfelső szintű számítógépének fiókját.  

    > [!IMPORTANT]  
    >  Használatakor a Configuration Manager-számítógép fiókját az egyik hozzáférési fiókként, gondoskodjon arról, hogy ez a fiók tagja-e a biztonsági csoport **elosztott COM-felhasználók** a tartományban, amelyikben a forráshely van.  

    Adatgyűjtéskor a következő hálózati protokollok és portok vannak használatban:  

    -   A NetBIOS/SMB - 445 (TCP)  

    -   RPC (WMI) - 135 (TCP)  

    -   SQL Server - A TCP portokat a forráshelyi és a célhelyi adatbázis is használja.  

-   **Szoftverfrissítések áttelepítése:**  

     A szoftverfrissítések áttelepítése előtt a célhierarchiát szoftverfrissítési ponttal kell konfigurálni. További információ: [Szoftverfrissítések áttelepítésének tervezése](../../core/migration/planning-for-the-migration-of-objects.md#Plan_migrate_Software_updates).  

-   **Terjesztési pontok megosztása:**  

     A forráshelyről valamelyik terjesztési pont megosztásához a célhierarchiában legalább egy elsődleges helynek vagy a központi felügyeleti helynek az ügyfél gépek kérelmeihez ugyanazon portszámot kell használni, mint amit a forráshely használ. További információ az ügyfélkérelmekhez használt portokról: [Ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-communication-ports.md)  

     Az egyes forráshelyeknél csak azok a helyrendszer-kiszolgálóra telepített terjesztési pontok megosztottak, amelyek az FQDN használatával lettek konfigurálva.  

     Továbbá, hogy egy System Center 2012 Configuration Manager vagy a System Center Configuration Managerben forráshelyi terjesztési pont megosztásához a **Forráshelyfiók** (amely fér hozzá az SMS-szolgáltató a forráshely kiszolgálója számára), rendelkeznie kell **módosítás** engedélyeket a **hely** objektum a forrás. Ezt az engedélyt a fiók részére a szerepkör alapú felügyelet használatával kell megadni. A szerepköralapú felügyelet használatáról lásd: [A System Center Configuration Manager szerepköralapú adminisztrációjának alapjai](../../core/understand/fundamentals-of-role-based-administration.md).  


-   **Terjesztési pontok frissítése vagy ismételt hozzárendelése:**  

     A forráshelyi SMS Provider adatainak gyűjtésére konfigurált **Forráshely-elérési fiók** a következő engedélyekkel kell, hogy rendelkezzen:  

    -   Konfigurációs Manager2007 terjesztési pont frissítéséhez a fióknak **olvasási**, **Execute**, és **törlése** engedélyeket a **hely** osztály a konfigurációs Manager2007 helykiszolgálón, hogy sikeresen eltávolíthassa a terjesztési pont konfigurációs Manager2007 forráshelyről  

    -   A System Center 2012 Configuration Manager vagy a System Center Configuration Manager terjesztési pont ismételt hozzárendelése, a fióknak rendelkeznie kell **módosítás** engedéllyel a **hely** objektum a forrás. Ezt az engedélyt a fiók részére a szerepkör alapú felügyelet használatával kell megadni. A szerepköralapú felügyelet használatáról lásd: [A System Center Configuration Manager szerepköralapú adminisztrációjának alapjai](../../core/understand/fundamentals-of-role-based-administration.md).  

     A terjesztési pont sikeres frissítéséhez vagy új hierarchiához való hozzárendeléséhez azoknak a portoknak, amelyek a terjesztési pontot a forráshierarchiában felügyelt helyen az ügyféli kérelmek részére lettek konfigurálva, azonosnak kell lenni azokkal, amelyek a terjesztési pontot majdan felügyelő célhelyen az ügyféli kérelmek részére lettek konfigurálva. További információ az ügyfélkérelmekhez használt portokról: [Ügyfél-kommunikációs portok konfigurálása a System Center Configuration Managerben](../../core/clients/deploy/configure-client-communication-ports.md).  

