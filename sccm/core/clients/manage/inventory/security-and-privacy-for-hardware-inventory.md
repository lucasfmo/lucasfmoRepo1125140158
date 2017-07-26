---
title: "Hardver készlet biztonsági adatvédelmi |} Microsoft Docs"
description: "A Hardverleltár biztonsági és adatvédelmi tudnivalókat a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 62e20d86-db6d-4a1f-b14a-905a9de31698
caps.latest.revision: 6
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: ec182ec3102e0f4ae8bcf3d1ef843b25510b6ce6
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-hardware-inventory-in-system-center-configuration-manager"></a>A hardverleltár biztonsága és adatvédelme a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a Hardverleltár a System Center Configuration Manager biztonsági és adatvédelmi tudnivalókat tartalmazza.  

##  <a name="BKMK_Security_HardwareInventory"></a> Ajánlott biztonsági eljárások a hardverleltár használatához  
 A hardverleltáradatok az ügyfelektől való begyűjtésekor használja az alábbi ajánlott biztonsági eljárásokat:  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Leltáradatok aláírása és titkosítása|Ha az ügyfelek a HTTPS protokollal kommunikálnak a felügyeleti pontokkal, az összes általuk küldött adat titkosítva van az SSL használatával. Ha azonban az ügyfélszámítógépek a HTTP protokollal kommunikálnak az intraneten lévő felügyeleti pontokkal, az ügyfélleltáradatok és az összegyűjtött fájlok aláírás és titkosítás nélkül is elküldhetők. Győződjön meg arról, hogy a hely úgy van konfigurálva, hogy megkövetelje az aláírást és titkosítást használjon. Emellett ha az ügyfelek támogatják az SHA-256 algoritmus használatát, állítsa be az SHA-256 megkövetelésének lehetőségét.|  
|Fokozott biztonságú környezetekben ne gyűjtse az IDMIF- és NOIDMIF-fájlokat.|Az IDMIF- és NOIDMIF-fájlok gyűjtésével bővítheti a hardverleltározást. Ha szükséges, a Configuration Manager új táblákat hoz létre vagy módosítja a meglévő táblákat a Configuration Manager adatbázisban az IDMIF és NOIDMIF-fájlok tulajdonságainak kezeléséhez. A Configuration Manager azonban nem ellenőrzi IDMIF és NOIDMIF-fájlokat, így ezek a fájlok felhasználhatók táblák módosítására, melyeket nem kívánja módosítani. Az érvényes adatok felülírhatók érvénytelen adatokkal. Emellett nagy mennyiségű adat adható hozzá, és ezen adatok feldolgozása késéseket okozhat az összes Configuration Manager funkcióihoz. A kockázatok csökkentése érdekében a hardverleltár **MIF-fájlok gyűjtése** ügyfélbeállítását konfigurálja a **Nincs**értékre.|  

### <a name="security-issues-for-hardware-inventory"></a>A hardverleltár biztonsági problémái  
 A leltáradatok gyűjtése potenciális biztonsági réseket tesz elérhetővé. A támadók a következőket hajthatják végre:  

-   Érvénytelen adatok küldése, melyeket a felügyeleti pont akkor is elfogad, ha a szoftverleltár ügyfélbeállítása le van tiltva, és a fájlgyűjtés nincs engedélyezve.  

-   Rendkívül nagy mennyiségű adat küldése egyetlen fájlban vagy nagy mennyiségű fájlban, ami szolgáltatásmegtagadást okozhat.  

-   Hozzáférés a Configuration Manager az átvitel során.  

 Helyi rendszergazdai jogosultságokkal rendelkező felhasználók bármilyen adatokat elküldhetnek leltáradatokként, mert nem tekinti a Configuration Manager mérvadónak begyűjtött leltáradatokat.  

 A hardverleltár alapértelmezés szerint engedélyezve van ügyfélbeállításként.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Adatvédelmi információ a hardverleltárhoz  
 Hardverleltár a Configuration Manager-ügyfelek a beállításjegyzékben és a WMI-ben tárolt adatok lekérését teszi lehetővé. A szoftverleltár az összes, megadott típusú fájl felderítését, vagy a megadott fájlok az ügyfelekről való begyűjtését teszi lehetővé. Az Eszközintelligencia szolgáltatás a hardver- és szoftverleltár kibővítésével, illetve új licenckezelési funkciók hozzáadásával javítja a leltározási képességeket.  

 A hardverleltár alapértelmezés szerint engedélyezve van ügyfélbeállításként, és a begyűjtött WMI-adatokat a megadott beállítások határozzák meg. A szoftverleltár alapértelmezés szerint engedélyezve van ügyfélbeállításként, de a rendszer alapértelmezés szerint nem gyűjt fájlokat. A leltározási adatgyűjtés automatikusan engedélyezve van, a hardverleltár engedélyezni kívánt jelentési osztályait azonban kiválaszthatja.  

 A rendszer nem küld leltáradatokat a Microsoftnak. Hardverleltár-információk a Configuration Manager adatbázisban tárolódik. Ha az ügyfelek a HTTPS protokollal csatlakoznak a felügyeleti pontokhoz, az általuk a helyre küldött leltáradatok az átvitel során titkosítva vannak. Ha az ügyfelek a HTTP protokollal csatlakoznak a felügyeleti pontokhoz, lehetősége van engedélyezni a leltár titkosítását. Az adatbázis titkosítás nélkül tárolja a leltáradatokat. Az adatbázis addig őrzi meg ezeket az adatokat, amíg nem törli azokat az **Elavult leltárelőzmények törlése** vagy az **Elavult gyűjteményfájlok törlése** helykarbantartási feladat 90 naponta. Beállíthatja a törlési időközt.  

 A hardverleltár, a szoftverleltár, a fájlgyűjtés vagy a leltározási adatgyűjtés konfigurálása előtt gondolja át az adatvédelmi követelményeket.  

