---
title: "Biztonság és adatvédelem a megfelelőségi beállítások |} Microsoft Docs"
description: "Ismerje meg a biztonsággal kapcsolatos ajánlott eljárások a megfelelőségi beállítások a System Center Configuration Managerben."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1c409244-6778-4970-a99c-d2508c9cf62b
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: e7dc554ffcd23978eed44819b525f6cc239b2135
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-compliance-settings-in-system-center-configuration-manager"></a>Biztonság és adatvédelem a System Center Configuration Manager megfelelőségi beállítások

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


## <a name="security-best-practices-for-compliance-settings"></a>A megfelelőségi beállítások biztonsági védelmének bevált gyakorlata  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Ne figyelje a bizalmas adatokat.|Az információk felfedésének elkerülése érdekében ne állítsa be a konfigurációelemeket a feltehetően bizalmas adatok figyelésére.|  
|Ne konfiguráljon olyan megfelelőségi szabályokat, amelyek végfelhasználók által módosítható adatokat használnak.|Ha a felhasználók által módosítható adatok, például konfigurációválasztásokhoz tartozó beállításjegyzék-beállítások alapján hoz létre megfelelőségi szabályt, a megfelelőségi eredmények nem lesznek megbízhatók.|  
|Csak akkor importáljon külső forrásból Microsoft System Center konfigurációs csomagokat vagy más konfigurációs adatokat, ha azok egy megbízható közzétevő digitális aláírásával rendelkeznek.|A közzétett konfigurációs adatok digitális aláírással láthatók el, hogy ellenőrizni lehessen a közzétételi forrást, valamint azt, hogy az adatokat nem módosították. Ha a digitális aláírás ellenőrzése sikertelen, a rendszer figyelmezteti és rákérdez az importálás folytatására. Ne importáljon aláíratlan adatokat, ha nem tudja ellenőrizni az adatok forrását és sértetlenségét.|  
|Alkalmazzon hozzáférés-vezérlést a referencia-számítógépek védelméhez.|Amikor egy rendszergazda felhasználó egy referencia-számítógépet tallózással megkeresve konfigurálja a beállításjegyzékben vagy a fájlrendszerben található beállításokat, győződjön meg arról, hogy a referencia-számítógép biztonsága nem sérült.|  
|Ha tallózással keres referencia-számítógépet, biztonságossá kell tennie a kommunikációs csatornát.|Ha a hálózaton keresztül továbbított adatok illetéktelen megakadályozásához használja az IP-biztonság (IPsec) vagy kiszolgálói üzenetblokk (SMB) a Configuration Manager konzolt futtató számítógép és a referencia-számítógép között.|  
|Korlátozza és a figyelje azokat a rendszergazdákat, akik megfelelőségibeállítás-kezelői biztonsági szerepkörrel rendelkeznek.|A **megfelelőségibeállítás-kezelői** szerepkört kapott rendszergazda felhasználók minden eszköz és a hierarchiában lévő összes felhasználó számára telepíthetnek konfigurációelemeket. A konfigurációelemek nagyon hatékonyak lehetnek, például parancsfájlokat és a beállításjegyzék újrakonfigurálását is tartalmazhatják.|  

## <a name="privacy-information-for-compliance-settings"></a>Adatvédelmi információ a megfelelőségi beállításokhoz  
 A megfelelőségi beállítások segítségével értékelhető, hogy az ügyféleszközök megfelelnek-e a referenciakonfigurációkban központilag telepített konfigurációs elemeknek. Egyes beállítások automatikusan is kijavíthatók, ha nem megfelelőek. A  felügyeleti pont a megfelelőségi információkat a helykiszolgálónak továbbítja, és azokat a hely adatbázisa tárolja. Az adatok titkosítva vannak, amikor az eszközök elküldik azokat a felügyeleti pontnak, azonban a helyadatbázis titkosítás nélkül tárolja az adatokat. Ezek az adatok addig maradnak az adatbázisban, amíg a 90 naponta végrehajtott **Elavult Configuration Management adatok törlése** helykarbantartási feladat el nem távolítja azokat. Beállíthatja a törlési időközt. A program nem küld megfelelőségi adatokat a Microsoftnak.  

 Az eszközök alapértelmezés szerint nem értékelik ki a megfelelőségi beállításokat. Ezenfelül konfigurálnia kell a konfigurációelemeket és referenciakonfigurációkat, majd telepíteni őket az eszközökre.  

