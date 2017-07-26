---
title: "Tanúsítvány-profilok biztonsága és adatvédelme |} Microsoft Docs"
description: "A biztonság a felhasználók és eszközök a System Center Configuration Managerben tanúsítványprofilok kezelésének ajánlott eljárásai megismerése."
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3393db41-900a-44c5-b950-2d46a35a198c
caps.latest.revision: 7
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8a5dc7361da34f3e6b926acd35c72c0c0767ce70
ms.openlocfilehash: c51787ad3fa0bdb285017cfab1ca6931afba9ea6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-certificate-profiles-in-system-center-configuration-manager"></a>Tanúsítványprofilok biztonsága és adatvédelme a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


##  <a name="security-best-practices-for-certificate-profiles"></a>Bevált biztonsági gyakorlatok tanúsítványprofilokhoz  
 A felhasználókhoz és eszközökhöz tartozó tanúsítványprofilok kezelésekor alkalmazza a következő bevált biztonsági gyakorlatokat.  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|A hálózati eszközök tanúsítványigénylési szolgáltatásával kapcsolatos bevált biztonsági gyakorlatok azonosítása és betartása (beleértve az IIS szolgáltatásban a hálózati eszközök tanúsítványigénylési szolgáltatásának beállítását az SSL használatának megkövetelésére és az ügyféltanúsítványok figyelmen kívül hagyására).|Lásd: [Útmutató a hálózati eszközök tanúsítványigénylési szolgáltatásához](http://go.microsoft.com/fwlink/p/?LinkId=309016) a TechNet Active Directory-tanúsítványszolgáltatásról szóló tartalomtárában.|  
|Az SCEP-tanúsítványprofilok konfigurálásánál az eszközök, illetve az infrastruktúra által támogatott legbiztonságosabb beállításokat adja meg.|Azonosítsa, vezesse be, és tartsa be az eszközeire és infrastruktúrájára vonatkozóan ajánlott bevált biztonsági gyakorlatokat.|  
|A felhasználó-eszköz kapcsolatot manuálisan adja meg, ne hagyja a felhasználóknak, hogy azonosítsák az elsődleges eszközüket. Ezen kívül ne engedélyezze a használat alapú konfigurálást.|Ha egy SCEP-tanúsítványprofilnál a **Tanúsítványigénylés engedélyezése csak a felhasználó elsődleges eszközén** beállításra kattint, ne vegye figyelembe irányadóként a felhasználóktól vagy az eszköztől kapott adatokat. Amennyiben ezzel a konfigurációval telepít SCEP-tanúsítványprofilokat, és egy megbízható rendszergazda felhasználó nem adja meg a felhasználó-eszköz kapcsolatot, előfordulhat, hogy nem jogosult felhasználók emelt szintű jogosultságokhoz jutnak, és tanúsítványokat kapnak a hitelesítéshez.<br /><br /> **Megjegyzés:** Ha engedélyezi a használat alapú konfigurálást, az információk gyűjtése a System Center Configuration Manager által nem védett állapotüzenetek használatával. A biztonsági kockázat enyhítése érdekében az ügyfélszámítógépek és a felügyeleti pont között használjon SMB-aláírást vagy IPsec-et.|  
|A tanúsítványsablonokhoz ne adjon a felhasználóknak olvasási és beléptetési engedélyeket, vagy a tanúsítványregisztrációs pontot úgy konfigurálja, hogy kihagyja a tanúsítványsablon ellenőrzését.|Bár a Configuration Manager támogatja a további ellenőrzést, ha a biztonsági engedélyek az olvasási és beléptetési a felhasználók számára, és konfigurálhatja a tanúsítványregisztrációs pontot az ellenőrzés kihagyására, amennyiben a hitelesítés nem lehetséges, egyik konfiguráció sem a biztonsági szempontból ajánlott. További tájékoztatásért lásd: [Tanúsítványsablonok engedélyeinek tervezése a System Center Configuration Manager tanúsítványprofiljaihoz](../../protect/plan-design/planning-for-certificate-template-permissions.md).|  

## <a name="privacy-information-for-certificate-profiles"></a>Adatvédelmi tudnivalók tanúsítványprofilokhoz  
 Tanúsítványprofilok használatával elvégezheti a legfelső szintű hitelesítésszolgáltatói és ügyféltanúsítványok központi telepítését, majd kiértékelheti, hogy a profilok alkalmazása után az eszközök a követelményeknek megfelelővé válnak-e. A felügyeleti pont a megfelelőségi információkat a helykiszolgálónak továbbítja, és a System Center Configuration Manager a hely adatbázisában tárolja ezeket az információkat. A megfelelőségi adatok között szerepelnek a tanúsítványok tulajdonságai is, például a tulajdonos neve és az ujjlenyomat. Az adatok titkosítva vannak, amikor az eszközök elküldik azokat a felügyeleti pontnak, azonban a helyadatbázis titkosítás nélkül tárolja az adatokat. Az adatbázis mindaddig megőrzi az adatokat, amíg az **Elavult Configuration Management adatok törlése** helykarbantartási feladat az alapértelmezett 90 napos időszak után nem törli őket. Beállíthatja a törlési időközt. A program nem küld megfelelőségi adatokat a Microsoftnak.  

 A tanúsítvány profilok használják, hogy a Configuration Manager által összegyűjtött felderítés információ. A felderítés adatvédelmi információiról további információt a [Biztonság és adatvédelem a System Center Configuration Managerben](../../core/plan-design/security/security-and-privacy.md) témakör **Adatvédelmi tájékoztatás a felderítéshez** cím szakaszában talál.  

> [!NOTE]  
>  A felhasználók vagy eszközök számára kiállított tanúsítványok bizalmas információk elérését tehetik lehetővé.  

 Az eszközök alapértelmezés szerint nem értékelik ki a tanúsítványprofilokat. Emellett konfigurálni kell a tanúsítványprofilokat, és aztán el kell végezni azok központi telepítését a felhasználóknál vagy eszközökön.  

 A tanúsítványprofilok konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

