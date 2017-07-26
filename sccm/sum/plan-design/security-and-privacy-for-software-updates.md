---

title: "Biztonság és adatvédelem a szoftverfrissítések |} Microsoft Docs"
description: "Kövesse az alábbi gyakorlati tanácsok a biztonsági szoftverfrissítések, és miként kezeli a Configuration Manager az adatvédelemről megismerése."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 41d6d5d8-ba84-4efb-b105-4d1eed239824
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 4b4f045138abc14b6e93b3b990c5f3a8b4f2f952
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---
# <a name="security-and-privacy-for-software-updates-in-system-center-configuration-manager"></a>A szoftverfrissítések biztonsága és adatvédelme a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör biztonsági és adatvédelmi információ a szoftverfrissítések a System Center Configuration Managerben.  

##  <a name="BKMK_Security_HardwareInventory"></a> A szoftverfrissítés biztonsági védelmének bevált gyakorlata  
 A szoftverfrissítések ügyfélgépekre telepítéséhez jól használható a következő bevált eljárás:  

-   Ne változtassa meg a szoftverfrissítési csomagok alapértelmezett engedélyeit.  

     A szoftverfrissítési csomagok beállítása alapértelmezetten az, hogy a rendszergazdák a **Teljes hozzáférés** , a felhasználók pedig az **Olvasás** engedéllyel rendelkeznek. Ha megváltoztatja ezeket az engedélyeket, lehetővé válhat, hogy egy támadó hozzáadjon, eltávolítson vagy töröljön szoftverfrissítéseket.  

-   Teljes hozzáférés a szoftverfrissítések letöltési helyéhez.  

     Az SMS-szolgáltatónak, a helykiszolgáló elérésére szolgáló számítógépek fiókjainak, valamint azoknak a rendszergazda felhasználóknak, akik a szoftverfrissítéseket ténylegesen letöltik a letöltési helyre **Írás** hozzáféréssel kell rendelkeznie a letöltési helyre. Ezért a letöltési hely hozzáférését megfelelően kell korlátozni, hogy csökkenjen a szoftverfrissítési forrásfájlok támadók általi módosításának kockázata.  

     Ha a letöltési helyre az UNC megosztást használja, akkor a hálózati csatornát is biztonságossá kell tenni az IPsec vagy az SMB aláírású protokollal, hogy megakadályozza a szoftverfrissítés forrásfájljainak illetéktelen módosítását a hálózati átvitel közben.  

-   A központi telepítésekben az idő kiértékelése a világidő (UTC) szerinti legyen.  

     Ha a világidő helyett helyi időt használ, előfordulhat, hogy a felhasználók a számítógépükön lévő időzóna megváltoztatásával késleltethetik a szoftverfrissítések telepítését.  

-   A Windows Server Update Services (WSUS) szolgáltatás biztonsága érdekében engedélyezni kell rá az SSL használatát, és a bevált gyakorlat szerint kell eljárni.  

     Ismerje meg és kövesse a biztonsági védelmének bevált gyakorlata a Configuration Managerrel használt WSUS verziójának.  

    > [!IMPORTANT]  
    >  Ha a WSUS kiszolgálóján a szoftverfrissítési pontot az SSL kommunikáció használatára konfigurálja, virtuális gyökereket is konfigurálni kell az SSL részére a WSUS kiszolgálóján.  

-   Engedélyezze a CRL-ellenőrzést.  

     Alapértelmezés szerint a Configuration Manager nem ellenőrzi a visszavont tanúsítványok listáját (CRL), hogy ellenőrizze a szoftverfrissítések aláírását, a számítógépekre telepítésük előtt. A visszavonttanúsítvány-lista minden alkalommal történő ellenőrzése nagyobb védelmet kínál a visszavont tanúsítványokkal szemben, de csatlakozási késedelmet és többlet feldolgozást eredményez a CRL-ellenőrzést végző számítógépeken.  

     Tanúsítvány-visszavonási listát engedélyezésével kapcsolatos további információ a szoftverfrissítések-ellenőrzésének engedélyezéséről: [a System Center Configuration Manager szoftverfrissítések CRL-ellenőrzésének engedélyezése](../get-started/manage-settings-for-software-updates.md#crl-checking-for-software-updates).  

-   A WSUS szolgáltatás konfigurálása egyéni webhelyi használathoz.  

     Ha a WSUS telepítése a szoftverfrissítési pontra történik választhat, hogy ahhoz az IIS létező alapértelmezett webhelyét használja, vagy egyéni WSUS webhelyet hozzon létre. Hozzon létre egyéni webhelyet a WSUS Szolgáltatáshoz, így nem osztja meg ugyanazt a webhelyet a más Configuration Manager helyrendszerei vagy más alkalmazások által használt dedikált virtuális webhelyen a WSUS szolgáltatásait az IIS kiszolgálója.  

     További információkért lásd: [WSUS beállítása egy egyéni webhely használatára](plan-for-software-updates.md#BKMK_CustomWebSite).  

##  <a name="BKMK_Privacy_HardwareInventory"></a>Adatvédelmi információ a szoftverfrissítésekhez  
 A szoftverfrissítések megvizsgálják az ügyfélgépeket abból a szempontból, hogy milyen szoftverfrissítésre van szükségük, és ezt az információt küldik a helyadatbázisba. A szoftverfrissítési folyamat során a Configuration Manager információt továbbíthat között ügyfelek és kiszolgálók, amelyek a számítógépet és annak bejelentkezési fiókjait azonosítják.  

 A Configuration Manager a szoftver központi telepítésére vonatkozó állapotadatokat megőrzi. Az állapotadatok az átvitel és a tárolás során nem titkosítottak. Állapotadatok a Configuration Manager-adatbázis tárolja, és nem törli azokat az adatbázis-karbantartási feladatokat. A rendszer semmilyen állapotadatot nem küld a Microsoftnak.  

 Configuration Manager szoftverfrissítések a szoftverfrissítések ügyfélgépekre telepítésére történő felhasználása is vonatkozik szoftver licencfeltételeit, amelyiket frissíti, amely a szoftverlicenc-feltételek a System Center Configuration Manager elkülönül. Mindig tekintse át, és fogadja el a szoftverfrissítések a Configuration Manager használatával történő telepítése előtt a szoftverfrissítések licencelési feltételeit.  

 A Configuration Manager nem valósítja meg a szoftverfrissítések alapértelmezés szerint, és több konfigurációs lépésre van szükség, előtt a szolgáltatás által gyűjtött információk.  

 A szoftverfrissítések konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

