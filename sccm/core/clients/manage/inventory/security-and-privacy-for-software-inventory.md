---
title: "Szoftver készlet biztonsági adatvédelmi |} Microsoft Docs"
description: "A szoftverleltár biztonsági és adatvédelmi tudnivalókat a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8e68e1fb-a8ec-4543-bb8a-cbbaf184a418
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 7652e46d2168e2de623fa8e6d5b8663701764244
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-software-inventory-in-system-center-configuration-manager"></a>Biztonság és adatvédelem a System Center Configuration Manager szoftverleltár

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a szoftverleltár a System Center Configuration Manager biztonsági és adatvédelmi tudnivalókat tartalmazza.  

##  <a name="BKMK_Security_HardwareInventory"></a> A szoftverleltárhoz kapcsolódó ajánlott biztonsági eljárások  
 A szoftverleltáradatok az ügyfelektől való begyűjtésekor használja az alábbi ajánlott biztonsági eljárásokat:  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Leltáradatok aláírása és titkosítása|Ha az ügyfelek a HTTPS protokollal kommunikálnak a felügyeleti pontokkal, az összes általuk küldött adat titkosítva van az SSL használatával. Ha azonban az ügyfélszámítógépek a HTTP protokollal kommunikálnak az intraneten lévő felügyeleti pontokkal, az ügyfélleltáradatok és az összegyűjtött fájlok aláírás és titkosítás nélkül is elküldhetők. Győződjön meg arról, hogy a hely úgy van konfigurálva, hogy megkövetelje az aláírást és titkosítást használjon. Emellett ha az ügyfelek támogatják az SHA-256 algoritmus használatát, állítsa be az SHA-256 megkövetelésének lehetőségét.|  
|A fájlgyűjtést ne használja kritikus fontosságú fájlok vagy bizalmas információk gyűjtésére.|A Configuration Manager szoftverleltár a LocalSystem fiók, mely képes a kritikus rendszerfájlok, például a beállításjegyzék és a biztonságifiók-adatbázis másolatainak gyűjtésére összes jogosultságát használja. Ha ezek a fájlok elérhetők a helykiszolgálón, egy, a tárolt fájlok helyéhez Erőforrás olvasása jogosultságokkal vagy NTFS jogosultságokkal rendelkező személy elemezheti azok tartalmát, és akár az ügyféllel kapcsolatos fontos részleteket is feltárhat, melyekkel veszélyeztetheti annak biztonságát.|  
|Helyi rendszergazdai jogosultságok korlátozása az ügyfélszámítógépeken|A helyi rendszergazdai jogosultságokkal rendelkező felhasználók érvénytelen adatokat küldhetnek el leltáradatokként.|  

### <a name="security-issues-for-software-inventory"></a>A szoftverleltár biztonsági problémái  
 A leltáradatok gyűjtése potenciális biztonsági réseket tesz elérhetővé. A támadók a következőket hajthatják végre:  

-   Érvénytelen adatok küldése, melyeket a felügyeleti pont akkor is elfogad, ha a szoftverleltár ügyfélbeállítása le van tiltva, és a fájlgyűjtés nincs engedélyezve.  

-   Rendkívül nagy mennyiségű adat küldése egyetlen fájlban vagy nagy mennyiségű fájlban, ami szolgáltatásmegtagadást okozhat.  

-   Hozzáférés a Configuration Manager az átvitel során.  

 Ha a felhasználók tisztában vannak vele, hogy egy **Skpswi.dat** nevű rejtett fájl létrehozásával és egy ügyfél merevlemezének gyökerében való elhelyezésével kizárhatják azt a szoftverleltárból, nem fog tudni szoftverleltáradatokat gyűjteni az adott számítógépről.  

 Helyi rendszergazdai jogosultságokkal rendelkező felhasználók bármilyen adatokat elküldhetnek leltáradatokként, mert nem tekinti a Configuration Manager mérvadónak begyűjtött leltáradatokat.  

 A szoftverleltár alapértelmezés szerint engedélyezve van ügyfélbeállításként.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Adatvédelmi információ a szoftverleltárhoz  
 Hardverleltár a Configuration Manager-ügyfelek a beállításjegyzékben és a WMI-ben tárolt adatok lekérését teszi lehetővé. A szoftverleltár az összes, megadott típusú fájl felderítését, vagy a megadott fájlok az ügyfelekről való begyűjtését teszi lehetővé. Az Eszközintelligencia szolgáltatás a hardver- és szoftverleltár kibővítésével, illetve új licenckezelési funkciók hozzáadásával javítja a leltározási képességeket.  

 A hardverleltár alapértelmezés szerint engedélyezve van ügyfélbeállításként, és a begyűjtött WMI-adatokat a megadott beállítások határozzák meg. A szoftverleltár alapértelmezés szerint engedélyezve van ügyfélbeállításként, de a rendszer alapértelmezés szerint nem gyűjt fájlokat. A leltározási adatgyűjtés automatikusan engedélyezve van, a hardverleltár engedélyezni kívánt jelentési osztályait azonban kiválaszthatja.  

 A rendszer nem küld leltáradatokat a Microsoftnak. Hardverleltár-információk a Configuration Manager adatbázisban tárolódik. Ha az ügyfelek a HTTPS protokollal csatlakoznak a felügyeleti pontokhoz, az általuk a helyre küldött leltáradatok az átvitel során titkosítva vannak. Ha az ügyfelek a HTTP protokollal csatlakoznak a felügyeleti pontokhoz, lehetősége van engedélyezni a leltár titkosítását. Az adatbázis titkosítás nélkül tárolja a leltáradatokat. Az adatbázis addig őrzi meg ezeket az adatokat, amíg nem törli azokat az **Elavult leltárelőzmények törlése** vagy az **Elavult gyűjteményfájlok törlése** helykarbantartási feladat 90 naponta. Beállíthatja a törlési időközt.  

 A hardverleltár, a szoftverleltár, a fájlgyűjtés vagy a leltározási adatgyűjtés konfigurálása előtt gondolja át az adatvédelmi követelményeket.  

