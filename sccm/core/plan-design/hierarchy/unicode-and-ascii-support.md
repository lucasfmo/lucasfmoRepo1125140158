---
title: "Unicode és ASCII-támogatás |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager-objektumok Unicode és ASCII karaktereket támogatja."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bdec799-905f-48bc-aed5-2d92134739e8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: b35e747c8c297d61bb549b9767c4318f51e5fdb4
ms.openlocfilehash: 18f1c64c1f27001a0fdfbab4236d09a5bc279272
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="unicode-and-ascii-support-in-system-center-configuration-manager"></a>Unicode és ASCII-támogatás a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager a legtöbb objektumot Unicode karakterek használatával hozza létre. Azonban több olyan objektum csak az ASCII karaktereket támogatja, vagy egyéb korlátozások is érvényesek rajtuk.  

 Az alábbi szakaszok az objektumokat, amelyek az ASCII karakterkészletet csak karaktert kell használnia, vagy további korlátozásokkal rendelkezik, amelyek tartalmazzák.  

-   [ASCII karaktereket használó objektumok](#BKMK_ASCIIchar)  

-   [További korlátozások](#BKMK_OtherCharLimitations)  

-   [Nem honosított Configuration Manager-objektumok](#BKMK_LangNonLocalize)  

##  <a name="BKMK_ASCIIchar"></a>ASCII karaktereket használó objektumok  
 A Configuration Manager támogatja az ASCII-karakterkészletet csak a következő objektumok létrehozásakor:  

-   Helykód  

-   Minden hely rendszer kiszolgáló számítógépneve  

-   A Configuration Manager következő fiókjai:  

    > [!NOTE]  
    >  Ezeket a fiókokat támogatja az ASCII-karakterek és a RUS karakterek orosz futtató helyen.  

    -   Ügyfélleküldéses telepítési fiók  

    -   Állapotreferencia közzétételi fiók  

    -   Állapotreferencia fiók  

    -   Felügyeleti pont adatbázis-csatlakozási fiók  

    -   Hálózatelérési fiók  

    -   Csomag-hozzáférési fiók  

    -   Szabványos feladó fiók  

    -   Helyrendszer-telepítési fiók  

    -   Szoftverfrissítési pont csatlakozási fiókja  

    -   Szoftverfrissítési pont proxy-kiszolgálói fiókja  

    > [!NOTE]  
    >  A szerepköralapú felügyelethez megadott fiókok támogatja a Unicode használatát.  
    >   
    >  A jelentéskészítési szolgáltatási pont fiókja támogatja a Unicode használatát, RUS karakterek kivételével.  

-   Teljesen minősített tartománynevét (FQDN) a Helykiszolgálók és helyrendszerek  

-   A Configuration Manager telepítési útvonala  

-   SQL Server-példányok neve  

-   A következő helyrendszerszerepkörök elérési útja:  

    -   Alkalmazáskatalógus webszolgáltatási pontja  

    -   Alkalmazáskatalógus weboldal-elérési pontja  

    -   Beléptetési pont  

    -   Beléptetési proxypont  

    -   Jelentéskészítési szolgáltatási pont  

    -   állapotáttelepítési pont  

-   A következő mappák elérési útja:  

    -   Ügyfél felhasználóáttelepítési adatokat tároló mappa  

    -   A mappa, amely tartalmazza a Configuration Manager jelentései  

    -   A Configuration Manager biztonsági mentési tároló mappa  

    -   A hely telepítése a telepítési forrásfájlokat tároló mappa  

    -   A telepítő által használandó letöltéseket az előfeltételt jelentő tároló mappa  

-   A következő objektumok elérési útja:  

    -   IIS-webhely  

    -   Virtuális alkalmazások telepítési útvonala  

    -   Virtuális alkalmazás neve  

-   A következő AMT és sávon kívüli felügyeleti objektumok:  

    -   Az AMT-alapú számítógép teljes Tartományneve  

    -   Az AMT-alapú számítógép számítógépneve  

    -   A tartomány NetBIOS-neve  

    -   A vezeték nélküli profil neve és SSID azonosítója  

    -   A megbízható legfelső szintű hitelesítésszolgáltató neve  

    -   A név a hitelesítésszolgáltató (CA) és a sablonnevek  

    -   A fájl nevét és az IDE-átirányítási lemezképfájl elérési útja  

    -   Az AMT-adattároló tartalma  

-   Rendszerindító adathordozó ISO-fájl neve  

##  <a name="BKMK_OtherCharLimitations"></a>További korlátozások  
 További korlátozások a támogatott karakterkészletek és nyelvi verziók a következők:  

-   A Configuration Manager nem támogatja a helykiszolgáló számítógép területi beállításainak megváltoztatását.  

-   Vállalati hitelesítésszolgáltató (CA) nem támogatja a kétbájtos karakterkészletet (DBCS) használó ügyfélszámítógép-neveket. A használható ügyfélszámítógép-neveket az IA5 karakterkészlet PKI-korláozásai korlátozza. Emellett a Configuration Manager nem támogatja a hitelesítésszolgáltató-neveket vagy tulajdonosnév-értékeket kétbájtos Karaktereket használó.  

##  <a name="BKMK_LangNonLocalize"></a>Nem honosított Configuration Manager-objektumok  
 A Configuration Manager-adatbázis általa tárolt legtöbb objektum esetében támogatjta a Unicode használatát, és ha lehetséges, operációs rendszer a számítógép területi beállításainak megfelelő nyelven jeleníti meg ezt az információt. Az ügyfél kezelőfelülete vagy a Configuration Manager konzol megjelenítheti a számítógép operációs rendszer nyelvén a számítógép területi beállításainak egyeznie kell a helyen telepített egy ügyfél vagy kiszolgáló nyelvével.  

 Azonban több Configuration Manager objektum nem támogatja a Unicode használatát, és azok adatbázisban tárolódnak az ASCII KARAKTERTÁBLA használatával, vagy lehetnek további nyelvi korlátozások. Ezek az információk mindig az ASCII karakterkészlet használatával vagy az objektum létrehozásakor használatban volt nyelven jelenik meg.  

