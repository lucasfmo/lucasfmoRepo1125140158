---
title: "Internet-hozzáférés felügyelt böngészőszabályzatokkal kezelése |} Microsoft Docs"
description: "Telepítheti az Intune Managed Browsert kezelésére, és az Internet-hozzáférés korlátozása."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e25e00c-c9a8-473f-bcb7-ea989f6ca3c5
caps.latest.revision: 6
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: d2dd2c25a2714851ba1e71414cabcef38d3ce014
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-internet-access-using-managed-browser-policies-with-system-center-configuration-manager"></a>Internet-hozzáférés kezelése Managed Browser-szabályzatokkal a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben, telepítheti az Intune Managed Browser (egy webböngésző-alkalmazás) és társíthatja egy felügyeltböngésző-szabályzathoz. Felügyeltböngésző-szabályzatot állít be egy engedélyezési vagy blokklista, korlátozza a webhelyeket, amelyeket a felügyelt böngésző felhasználói ugorhat.  

 Mivel az alkalmazás felügyelt alkalmazás, is mobilalkalmazás-felügyeleti házirendek vonatkoznak rá, például szabályozhatja a kivágási, másolási és beillesztési. Ez megakadályozza, hogy a képernyőképek készítését, és biztosítja azt is, hogy hivatkozások olyan témakörökre mutatnak csak megnyitása felügyelt alkalmazásokban. További információkért lásd: [alkalmazások mobilalkalmazás-kezelési házirendekkel védelme](protect-apps-using-mam-policies.md).  

> [!IMPORTANT]  
>  Ha maguk a felhasználók telepítik a felügyelt böngészőt, azt semmilyen Ön által megadott szabályzat nem fogja felügyelni. Győződjön meg arról, hogy a böngészőben a Configuration Manager által felügyelt-e, hogy el kell távolítaniuk az alkalmazást, mielőtt Ön telepítené a számukra felügyelt alkalmazásként.  

 Felügyeltböngésző-szabályzatokat a következő eszköztípusok esetében hozhat létre:  

-   Android 4 vagy újabb rendszerű eszközök  

-   iOS 7 vagy újabb rendszerű eszközök  

> [!NOTE]  
>  További információt és az Intune Managed Browser alkalmazás letöltéséhez lásd: [iTunes](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) IOS- és [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en) Android rendszerhez.  

## <a name="create-a-managed-browser-policy"></a>Felügyeltböngésző-szabályzat létrehozása.  

1.  Kattintson a Configuration Manager konzol **szoftverkönyvtár** > **Alkalmazáskezelés** > **alkalmazáskezelési házirendek**.  

3.  Az a **Home** lap a **létrehozása** csoportjában válassza **Alkalmazáskezelési házirend létrehozása**.  

4.  Az a **általános** lapon adja meg a nevét és a házirend leírását, és válassza a **következő**.  

5.  Az a **Házirendtípus** lapon válassza ki a platformot, válassza ki **Managed Browser** házirend írja be, és válassza a **tovább**.  

     A **Managed Browser** lapon válasszon az alábbi lehetőségek közül:  

    -   **A Managed browser csak a lenti URL-címeket megnyitásához**– adja meg, amelyeket a felügyelt böngésző megnyithat URL-címek listáját.  

    -   **A Managed browser nem nyithatja meg a lenti URL-címeket**– adja meg, hogy a felügyelt böngésző le lesz tiltva, nyitó URL-címek listáját.  

    > [!NOTE]  
    >  Ugyanabban a felügyeltböngésző-szabályzatban nem adhat meg egyszerre engedélyezett és tiltott URL-címeket is.  

     További információk az URL-formátumokra is megadhat, az engedélyezett és tiltott URL-címeket ebben a cikkben lásd URL-formátum.  

    > [!NOTE]  
    >  Az általános típusú szabályzattal lehetővé teszi az összhangban azokat a vállalat megfelelőségi és biztonsági házirendeket a központilag telepített alkalmazások működésének módosítását. A korlátozott alkalmazásokban például korlátozhatja a vágás, a másolás és a beillesztés műveletet. Az általános házirend típusával kapcsolatban bővebben lásd: [alkalmazások mobilalkalmazás-kezelési házirendekkel védelme](protect-apps-using-mam-policies.md).  

6.  Fejezze be a varázsló futtatását.  

Az új házirend megjelenik a **Szoftverkönyvtár** munkaterület **Alkalmazáskezelési házirendek** csomópontjában.  

## <a name="create-a-software-deployment-for-the-managed-browser-app"></a>A felügyelt böngészőalkalmazás szoftvertelepítésének létrehozása  
 Miután létrehozta a Managed Browser-szabályzatot, létrehozhat egy szoftvertelepítési típust a Managed Browser alkalmazáshoz. Mindkét egy általános és a felügyelt böngésző házirendet a felügyelt böngészőalkalmazás kell hozzárendelni.  

 További információkért lásd: [alkalmazásokat](create-applications.md).  

## <a name="security-and-privacy-for-the-managed-browser"></a>Felügyelt böngésző – biztonság és adatvédelem  

-   Az iOS-eszközökön, amelyek lejárt vagy nem megbízható tanúsítványok webhelyekhez nem lehet megnyitni.  

-   A felügyelt böngésző nem használja a felhasználók eszközein futó beépített böngésző beállításait. A felügyelt böngésző nincs hozzáférése ezeket a beállításokat.  

-   Ha úgy konfigurálja a beállításokat **egyszerű PIN-kód megkövetelése a hozzáféréshez** vagy **vállalati hitelesítő adatok megkövetelése a hozzáféréshez** egy mobilalkalmazás-kezelési házirendek a felügyelt böngésző egy felhasználó a hitelesítési lapon kattintson a Súgó gombra, és folytassa a egyetlen helyhez sem – akár egy hozzáadni a felügyeltböngésző-szabályzat blokklistájához.  

-   A felügyelt böngésző csak akkor képes blokkolni a hozzáférést a webhelyekhez, ha azokat közvetlenül érik el. Nem képes blokkolni a hozzáférést, ha a felhasználó köztes szolgáltatások (például egy fordítási szolgáltatás) használatával éri el a webhelyet.  

## <a name="reference-information"></a>Kapcsolódó információk  

###  <a name="url-format-for-allowed-and-blocked-urls"></a>Az engedélyezett és a blokkolt URL-címek URL-formátuma  

Az alábbi táblázat azokat az engedélyezett formátumokat és helyettesítő karaktereket ismerteti, amelyek az URL-címek engedélyezési és blokklistákban való megadásakor használhatók.  

-   A csillag (**\***) helyettesítő karakter es szimbólum a megengedett minták alábbi listájának szabályai szerint használható.  

-   Az URL-címek listába történő bevitelekor ellenőrizze, hogy az URL-címet a **http** vagy a **https** előtaggal adta-e meg.  

-   A címben portszámokat is megadhat. Ha nem ad meg portszámot, a rendszer a következő értékeket használja:  

    -   HTTP – 80-as port  

    -   HTTPS – 443-as port  

     A portszám helyettesítő karakterrel való megadása nem támogatott. Példa: **http://www.contoso.com:\*** és **http://www.contoso.com: /\***  

-   Az alábbi táblázat az URL-címek megadásakor használható mintákat ismerteti:  

    |URL-cím|Egyezik|Nem egyezik|  
    |---------|-------------|--------------------|  
    |http://www.contoso.com<br /><br /> Egyetlen lapnak felel meg|www.contoso.com|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> contoso.com/|  
    |http://contoso.com<br /><br /> Egyetlen lapnak felel meg|contoso.com/|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com|  
    |http://www.contoso.com/*<br /><br /> Az összes www.contoso.com karakterlánccal kezdődő URL-cím|www.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com/videos/tvshows|host.contoso.com<br /><br /> host.contoso.com/images|  
    |http://*.contoso.com/\*<br /><br /> A contoso.com összes altartománya|developer.contoso.com/resources<br /><br /> news.contoso.com/images<br /><br /> news.contoso.com/videos|contoso.host.com|  
    |http://www.contoso.com/images<br /><br /> Egyetlen mappa|www.contoso.com/images|www.contoso.com/images/dogs|  
    |http://www.contoso.com:80<br /><br /> Egyetlen lap, amely portszámot használ|http://www.contoso.com:80||  
    |https://www.contoso.com<br /><br /> Egyetlen biztonságos lap|https://www.contoso.com|http://www.contoso.com|  
    |http://www.contoso.com/images/*<br /><br /> Egyetlen mappa és annak összes almappája|www.contoso.com/images/dogs<br /><br /> www.contoso.com/images/cats|www.contoso.com/videos|  

-   Az alábbi példák nem engedélyezett beviteleket szemléltetnek:  

    -   *.com  

    -   *.contoso /\*  

    -   www.contoso.com/*images  

    -   www.contoso.com/*images\*pigs  

    -   www.contoso.com/page*  

    -   IP-címek  

    -   https://*  

    -   http://*  

    -   http://www.contoso.com:*  

    -   http://www.contoso.com: /*  

> [!NOTE]  
>  *. microsoft.com mindig engedélyezve van.  

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>Az engedélyezési lista és a blokklista közötti ütközések feloldása  
 Ha egy eszközön több felügyeltböngésző-szabályzatot léptet érvénybe, és ezek beállításai ütköznek, a rendszer mind a módot (engedélyezés vagy letiltás), mind az URL-listákat kiértékeli. Ütközés esetén a következőképpen viselkedik:  

-   Ha a módok mindegyik szabályzatban azonosak, de az URL-listák eltérőek, az URL-címeket nem kényszeríti az eszközön.  

-   Ha a módok mindegyik szabályzatban eltérőek, de az URL-listák azonosak, az URL-címeket nem kényszeríti az eszközön.  

-   Ha az eszközön első alkalommal léptet érvénybe felügyeltböngésző-szabályzatot, és két szabályzat ütközik, a rendszer nem kényszeríti ki az URL-cím használatát az eszközön. A konfliktusokat a **Házirend** munkaterület **Házirendütközések** csomópontjában tekintheti meg.  

-   Ha egy eszközön már érvénybe léptetett felügyeltböngésző-szabályzatot, és egy második érvénybe léptetett szabályzat ütköző beállításokat tartalmaz, az eredeti beállítások nem módosulnak az eszközön. A konfliktusokat a **Házirend** munkaterület **Házirendütközések** csomópontjában tekintheti meg.  

