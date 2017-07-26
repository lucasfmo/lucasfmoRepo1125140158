---
title: "Biztonság és adatvédelem a lekérdezések |} Microsoft Docs"
description: "Ismerje meg a biztonsági és adatvédelmi gyakorlati tanácsok a helyadatbázisból információ lekérdezésekor."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30080620-20d3-4c38-b8dd-db5516e1acae
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 09f7bdaa29a01fb2a38aa223db56b5bce3bc5205
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-queries-in-system-center-configuration-manager"></a>Biztonság és adatvédelem a lekérdezések a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben lekérdezések lehetővé teszik, hogy információt lekérni a Helyadatbázis, a megadott feltételek alapján. A Configuration Manager normál működés során a Helyadatbázis-adatokat gyűjti. Felderítésből vagy leltárból gyűjtött adatok használatával például lekérdezések konfigurálhatók arra, hogy azonosítsák a megadott feltételeket teljesítő eszközöket.  

 Lekérdezésekkel kapcsolatos további információkért lásd: [a System Center Configuration Manager lekérdezéseinek bemutatása](../../../core/servers/manage/introduction-to-queries.md). További információ a biztonsági gyakorlatok és adatvédelmi információ a Configuration Manager műveleteihez a lekérdezések használatával lekérhető információkat gyűjtő: [biztonsága és adatvédelme a System Center Configuration Manager](../../../core/plan-design/security/security-and-privacy.md).  

## <a name="security-best-practices-for-queries"></a>Ajánlott biztonsági eljárások lekérdezésekhez  
 Lekérdezésekhez az alábbi ajánlott biztonsági eljárás használhatók.  

|Ajánlott biztonsági eljárás|További információ|  
|----------------------------|----------------------|  
|Amikor egy hálózati helyen mentett lekérdezést exportál vagy importál, gondoskodjon a hely és a hálózati csatorna biztonságáról.|Korlátozza a hálózati mappához hozzáférő felhasználók körét.<br /><br /> A hálózati hely és helykiszolgáló között SMB- (Server Message Block-) alapú aláírást vagy IP-biztonságot (IPsec) használva akadályozza meg, hogy a támadók az importálás előtt illetéktelenül módosíthassák a lekérdezési adatokat.|  

## <a name="see-also"></a>Lásd még:  
 [Lekérdezések technikai útmutató a System Center Configuration Managerhez](../../../core/servers/manage/queries-technical-reference.md)

