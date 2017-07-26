---
title: "Az ügyfelek blokkolása |} Microsoft Docs"
description: "Rendszerbiztonság ügyfél hozzáférésének blokkolása a System Center Configuration Manager használatával."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54ef5fbb-521d-4ca5-a1c5-61e6f538d71e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3e323ab90ec4cc274581e19065fd7d81c0c11c35
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="determine-whether-to-block-clients-in-system-center-configuration-manager"></a>Annak meghatározása, hogy szükséges-e az ügyfelek blokkolása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha egy ügyfélszámítógép vagy mobileszköz típusú ügyfél már nem megbízható, blokkolhatja az ügyfelet a System Center 2012 Configuration Manager konzolon. Blokkolt ügyfeleket a Configuration Manager-infrastruktúra visszautasítja, hogy azok nem kommunikálhatnak helyrendszerek tölthetnek le házirendeket, tölthet fel leltári adatokat vagy küldhetnek állapotinformációkat vagy -üzeneteket.  

 Az ügyfelet a hozzárendelt helyéről kell blokkolnia és feloldania, nem egy másodlagos helyről vagy a központi felügyeleti helyről.  

> [!IMPORTANT]  
>  Bár blokkolja-e a Configuration Manager segítségével a Configuration Manager-hely védelmét, akkor ne használja a ezt a szolgáltatást a hely védelmét a nem megbízható számítógépekhez vagy mobil eszközökhöz, ha megengedi az ügyfeleknek kommunikálni a helyrendszerekkel HTTP, mert a blokkolt ügyfél újracsatlakozhatnak a helyhez egy új önaláírt tanúsítvány- és hardverkövetelményeinek. Inkább használja a blokkolás funkciót az operációs rendszerek központi telepítésére használt, elveszett vagy sérült biztonságú rendszerindító adathordozók letiltására, és ha a helyrendszerek fogadják a HTTPS-ügyfélkapcsolatokat.  

 A helyet ISV-proxy tanúsítvány használatával elérő ügyfeleket nem lehet blokkolni. Az ISV-proxytanúsítványokkal kapcsolatos további információkért tekintse meg a System Center Configuration Manager Software Development Kit (SDK).  

 Ha a helyrendszerek elfogadják a HTTPS-ügyfélkapcsolatokat, és a használt nyilvános kulcsú infrastruktúra (PKI) támogatja a visszavont tanúsítványok listáját (CRL), érdemes a tanúsítványok visszavonását használnia elsődleges védelmi vonalként a potenciálisan veszélyeztetett tanúsítványokkal szemben. A Configuration Manager ügyfelek blokkolása másodlagos védelmi vonalként szolgálhat-hierarchia védelmére.  

##  <a name="BKMK_Block_vs_CRL"></a> Szempontok az ügyfelek blokkolásához  

-   Ez a beállítás HTTP és HTTPS ügyfélkapcsolatok esetén is használható, de korlátozott biztonságot nyújt, ha az ügyfelek HTTP használatával csatlakoznak a helyrendszerekhez.  

-   A Configuration Manager rendszergazda felhasználói jogosultak egy ügyfél blokkolására, és a műveletet a Configuration Manager konzolon.  

-   Ügyfél-kommunikáció a Configuration Manager-hierarchia fogja elutasítani.  

    > [!NOTE]  
    >  Ugyanaz az ügyfél sikeresen regisztrálhat egy másik Configuration Manager hierarchiából.  

-   Az ügyfél azonnal blokkolva lett a Configuration Manager-hely.  

-   Segít megvédeni a helyrendszereket a potenciálisan veszélyeztető számítógépektől és mobileszközöktől.  

## <a name="considerations-for-using-certificate-revocation"></a>Szempontok a tanúsítvány-visszavonás használatához  

-   Ez a beállítás HTTPS Windows ügyfélkapcsolatok esetén használható, ha a nyilvános kulcsú infrastruktúra támogatja a visszavont tanúsítványok listáját (CRL).  

     A Mac ügyfelek mindig elvégzik a CRL ellenőrzését, és ezt a funkciót nem lehet letiltani.  

     Bár a mobileszközök nem használják a visszavont tanúsítványok listáját a helyrendszerek tanúsítványainak ellenőrzésére, a tanúsítványok visszavonása, és be van jelölve a Configuration Manager által.  

-   Nyilvános kulcsokra épülő infrastruktúra rendszergazdái jogosultak egy tanúsítvány visszavonására, és a műveletet a Configuration Manager-konzolon kívülről.  

-   Az ügyfél kommunikációját el lehet utasítani minden olyan számítógépről vagy mobileszközről, mely igényli ezt az ügyféltanúsítványt.  

-   Valószínűleg késleltetés lesz a tanúsítvány visszavonása és a helyrendszerek által a visszavont tanúsítványok módosított listájának (CRL) letöltése között.  

-   Sok PKI-telepítésnél ez a késleltetés akár egy napnál is hosszabb idő lehet. Az Active Directory tanúsítványszolgáltatásánál például az alapértelmezett lejárati időtartam egy hét a teljes CRL-re, és egy nap a változás CRL-re.  

-   Segít megvédeni a helyrendszereket és ügyfeleket a potenciálisan veszélyeztető számítógépektől és mobileszközöktől.  

    > [!NOTE]  
    >  További védelmet biztosíthat az IIS-t futtató helyrendszereknek az ismeretlen ügyfelek ellen, ha az IIS-ben konfigurálja a megbízható tanúsítványok listáját (CTL).  

