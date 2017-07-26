---
title: "Wi-Fi és VPN-profilok biztonsága és adatvédelme |} Microsoft Docs"
description: "Ismerje meg a biztonsági eszközök a System Center Configuration Manager Wi-Fi és VPN-profilok kezelésére vonatkozó ajánlott eljárások."
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
caps.latest.revision: 4
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8a5dc7361da34f3e6b926acd35c72c0c0767ce70
ms.openlocfilehash: 6d1d0a393a2ce614ae5f819475bd47b05e699b45
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Biztonság és adatvédelem a Wi-Fi és VPN-profilok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

##  <a name="security-best-practices-for-wi-fi--and-vpn-profiles"></a>Bevált biztonsági gyakorlatok Wi-Fi és VPN-profilok  
 Használja az alábbi ajánlott biztonsági eljárásokkal eszközökhöz tartozó Wi-Fi és VPN-profilok kezelésekor.  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Amikor csak lehetséges, adja meg a Wi-Fi és VPN-infrastruktúra és az ügyféloldali operációs rendszerek által támogatott legbiztonságosabb beállításokat.|Wi-Fi és VPN-profilokkal kényelmesen, központilag terjeszthetők és az eszközök által már támogatott Wi-Fi és VPN-beállítások kezelése. A Configuration Manager nem adja hozzá a Wi-Fi vagy VPN-funkcióit.<br /><br /> Azonosítsa, vezesse be, és tartsa be az eszközeire és infrastruktúrájára vonatkozóan ajánlott bevált biztonsági gyakorlatokat.|  

## <a name="privacy-information-for-wi-fi-profiles"></a>Biztonsági információk Wi-Fi profilokhoz  
 Wi-Fi és VPN-profilok használatával ügyféleszközöket konfigurálhat Wi-Fi és VPN-kiszolgálók csatlakozhat, és majd kiértékelheti, hogy az eszközök a követelményeknek megfelelővé válnak a profilok alkalmazása után történő. A felügyeleti pont a helykiszolgálónak továbbítja a megfelelőségi információkat, az információk pedig a hely adatbázisában tárolódnak. Az adatok titkosítva vannak, amikor az eszközök elküldik azokat a felügyeleti pontnak, azonban a helyadatbázis titkosítás nélkül tárolja az adatokat. Az adatbázis mindaddig megőrzi az adatokat, amíg az **Elavult Configuration Management adatok törlése** helykarbantartási feladat nem törli őket. Alapértelmezés szerint a törlési időszak hossza 90 nap, de ez módosítható. A program nem küld megfelelőségi adatokat a Microsoftnak.  

 Alapértelmezés szerint az eszközök nem értékelik ki Wi-Fi és VPN-profilokkal. Emellett meg kell a profilok is konfigurálhatók, és ezután telepíthet a felhasználók számára.  

 Wi-Fi vagy VPN-profilok konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

