---
title: "Gyűjtemények biztonsága és adatvédelme |} Microsoft Docs"
description: "Gyakorlati tanácsok a biztonság és adatvédelem a System Center Configuration Manager gyűjtemények beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30bf2451-5415-4be2-ba8d-21759370cd83
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 0cade975e96220e193db1de92816f97cd253532d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-collections-in-system-center-configuration-manager"></a>Biztonság és adatvédelem a System Center Configuration Manager gyűjtemények

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör ajánlott biztonsági eljárások és adatvédelmi információ a gyűjtemények a System Center Configuration Managerben.  

 Nincs kifejezetten a Configuration Manager-gyűjtemények adatvédelmi információ. A gyűjtemények erőforrások, többek között felhasználók és eszközök tárolói. A gyűjteménytagság gyakran a Configuration Manager normál működés során gyűjtött adatok függ. Felderítésből vagy leltárból gyűjtött erőforrásadatok használatával például gyűjtemények konfigurálhatók arra, hogy tartalmazzák a megadott feltételeket teljesítő eszközöket. A gyűjtemények az ügyfélkezelési műveletek aktuális állapotinformációiról, például a szoftverek telepítéséről és a megfelelőség ellenőrzéséről is tájékoztathatnak. E lekérdezésalapú gyűjtemények mellett a rendszergazdák erőforrásokat is felvehetnek a gyűjteményekbe.  

 További információ a gyűjtemények: [a System Center Configuration Manager gyűjteményeinek bemutatása](../../../../core/clients/manage/collections/introduction-to-collections.md). További információ a biztonsági gyakorlatok és adatvédelmi információ a Configuration Manager műveleteihez gyűjteménytagság konfigurálásához használható: [ajánlott biztonsági eljárások és adatvédelmi információk a System Center Configuration Manager](../../../../core/plan-design/security/security-best-practices-and-privacy-information.md).  

## <a name="security-best-practices-for-collections"></a>Ajánlott biztonsági eljárások gyűjteményekhez  
 Gyűjtemények esetén az alábbi ajánlott biztonsági eljárás használható.  

|Ajánlott biztonsági eljárás|További információ|  
|----------------------------|----------------------|  
|Amikor egy hálózati helyre mentett MOF (Managed Object Format) formátumú fájlt használva exportál vagy importál egy gyűjteményt, gondoskodjon a hely és a hálózati csatorna biztonságáról.|Korlátozza a hálózati mappához hozzáférő felhasználók körét.<br /><br /> A hálózati hely és helykiszolgáló között SMB- (Server Message Block-) alapú aláírást vagy IP-biztonságot (IPsec) használva akadályozza meg, hogy a támadók illetéktelenül módosíthassák az exportált gyűjteményadatokat. Használja az IPsec protokollt az adatok titkosításához a hálózatban az információ felfedésének megakadályozására.|  

### <a name="security-issues-for-collections"></a>Gyűjtemények biztonsági problémái  
 A gyűjteményeknél az alábbi biztonsági problémák tapasztalhatók:  

-   Gyűjteményváltozók használata esetén a helyi rendszergazdák bizalmas adatokhoz férhetnek hozzá.  

     Gyűjteményváltozók használhatók az operációs rendszerek telepítésekor.  

