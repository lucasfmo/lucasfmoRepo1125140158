---
title: "A távvezérlés biztonsági adatvédelmi |} Microsoft Docs"
description: "A távvezérlés biztonsági és adatvédelmi tudnivalókat a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 272ee86b-d3d9-4fd9-b5c4-73e490e1a1e4
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 03b8ede7fa4f4c02ffb551bb28fe2db234d39b12
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-remote-control-in-system-center-configuration-manager"></a>Biztonság és adatvédelem a System Center Configuration Manager Távvezérlés

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a biztonsági és adatvédelmi tudnivalókat a System Center 2012 Configuration Manager Távvezérlés tartalmazza.  

##  <a name="BKMK_Security_HardwareInventory"></a> A távvezérléshez kapcsolódó ajánlott biztonsági eljárások  
 Az ügyfélszámítógépek távvezérlés segítségével való kezelésekor alkalmazza a következő bevált biztonsági gyakorlatokat.  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Ne folytassa a távoli számítógéphez való csatlakozást, ha Kerberos-hitelesítés helyett NTLM használatos.|Ha a Configuration Manager azt észleli, hogy a távvezérlési munkamenet hitelesítése Kerberos helyett NTLM használatával, akkor egy megjelenő figyelmezteti, hogy a távoli számítógép identitása nem ellenőrizhető. Ne folytassa a távvezérlési munkamenetet. Az NTLM-hitelesítés gyengébb hitelesítési protokoll, mint a Kerberos, és sebezhető az ismétlési és megszemélyesítési támadásokkal szemben.|  
|Ne engedélyezze a vágólap megosztását a távvezérlés megjelenítőjében.|A vágólap támogatja az olyan objektumokat, mint például a végrehajtható és a szövegfájlok, és ezáltal a gazdagép felhasználója a távvezérlési munkamenet során a forrásszámítógépen futtathat programokat.|  
|Ne adja meg kiemelt jogosultságokkal rendelkező fiókok jelszavát, amikor a számítógép távoli felügyelet alatt áll.|Előfordulhat ugyanis, hogy egy, a billentyűzetbemenetet figyelő szoftver rögzíti a jelszót. Amennyiben az ügyfélszámítógépen futó program nem az, amit a távvezérlés felhasználója feltételez, szintúgy előfordulhat, hogy a program rögzíti a jelszót. Szükség esetén a végfelhasználónak kell megadnia a fiókokat és a jelszavakat.|  
|Zárolja a billentyűzetet és az egeret a távvezérlési munkamenet során.|Ha a Configuration Manager azt észleli, hogy a távvezérlési kapcsolat megszakadt, a Configuration Manager automatikusan zárolja a billentyűzet és egér annak, hogy egy felhasználó ne vehesse át a távvezérlési munkamenet irányítását. Előfordulhat azonban, hogy az észlelés nem történik meg azonnal, vagy – a távvezérlési szolgáltatás megszakadása esetén – akár egyáltalán nem.<br /><br /> Válassza a **Távoli billentyűzet és egér használatának zárolása** műveletet a **ConfigMgr távvezérlés** ablakban.|  
|Ne engedje meg, hogy a felhasználók a Szoftverközpontban letilthassák a távvezérlés beállításait.|A felhasználók utáni kémkedés megelőzése érdekében ne engedélyezze **A felhasználók megváltoztathatják a házirend vagy az értesítés beállításait a szoftverközpontban** ügyfélbeállítást.<br /><br /> Ez a beállítás akkor a számítógép nem a bejelentkezett felhasználó számára.|  
|Engedélyezze a Windows tűzfal **Tartomány** profilját.|Engedélyezze az **Ügyfelek távvezérlésének engedélyezése tűzfalkivételt** , majd válassza a **Tartomány** Windows tűzfalprofilt az intranetes számítógépekhez.|  
|Ha egy távvezérlési munkamenet során kijelentkezik, majd egy másik felhasználóként jelentkezik be, a távvezérlési munkamenet leválasztása előtt győződjön meg arról, hogy valóban kijelentkezett.|Abban az esetben, ha nem jelentkezik ki, a munkamenet nyitva marad.|  
|Ne adjon helyi rendszergazdai jogosultságot a felhasználóknak.|Amikor a felhasználók számára helyi rendszergazdai jogosultságokat ad meg, előfordulhat, hogy azok át tudják venni a távvezérlési munkamenetet, vagy veszélyeztethetik hitelesítő adatainak biztonságát.|  
|Csoportházirend vagy a Configuration Manager segítségével konfigurálhatja a távsegítségre vonatkozó beállítások, de soha sem egyszerre mindkettőre.|A Configuration Manager és a csoportházirend segítségével a távsegítségre vonatkozó beállítások konfigurációs módosításokat. Ha a csoportházirend frissül az ügyfélszámítógépen, alapértelmezés szerint csak azon házirendek módosításával optimalizálja a folyamatot, amelyek megváltoztak a kiszolgálón. A Configuration Manager módosítja a helyi biztonsági házirendet, amely előfordulhat, hogy nem írható felül, kivéve, ha a csoportházirend-frissítés kényszeríti a beállításait.<br /><br /> A házirend mindkét helyen történő beállítása inkonzisztens eredményhez vezethet. Válassza ezen módszerek egyikét a távsegítségre vonatkozó beállítások konfigurálásához.|  
|Engedélyezze az **Adatkérés a felhasználónak a távvezérlés engedélyezéséhez**ügyfélbeállítást.|Bár vannak lehetőségek az ügyfélbeállítás megkerülésére, amely a távvezérlési munkamenetek megerősítésére kéri a felhasználót, a beállítás engedélyezése csökkenti annak esélyét, hogy bizalmas jellegű feladatok végzése közben kémkedjenek a felhasználók után.<br /><br /> Ezenfelül figyelmeztesse a felhasználókat arra, hogy ellenőrizzék a távvezérlési munkamenet során megjelenített fióknevet, és válasszák le a munkamenetet, ha azt gyanítják, hogy a fiók nem engedélyezett.|  
|Korlátozza a feljogosított megjelenítők listáját.|A távvezérlés használatához a felhasználónak nincs szüksége helyi rendszergazdai jogosultságokra.|  

### <a name="security-issues-for-remote-control"></a>A távvezérlés biztonsági problémái  
 Az ügyfélszámítógépek távvezérlés használatával való kezelése a következő biztonsági problémákat veti fel:  

-   A távvezérlés naplózási üzenetei nem tekinthetők megbízhatónak.  

     Ha elindít egy távvezérlési munkamenetet, majd alternatív hitelesítő adatok használatával bejelentkezik, a naplózási üzeneteket az eredeti fiók küldi, nem pedig az alternatív hitelesítő adatokat használó fiók.  

     A naplózási üzenetek nem kerülnek, ha a távvezérlés a bináris fájlok másolása helyett a Configuration Manager konzol telepítéséhez, és futtassa a távvezérlés parancsot a parancssorba.  

##  <a name="BKMK_Privacy_HardwareInventory"></a> A távvezérléssel kapcsolatos adatvédelmi információk  
 Távvezérlés lehetővé teszi a Configuration Manager ügyfélszámítógépeken aktív munkamenetek megtekintését és azokon a számítógépeken tárolt összes adatot megtekintheti. A távvezérlés alapértelmezés szerint nincs engedélyezve.  

 Bár a távvezérlést konfigurálhatja egy jól látható, a felhasználó beleegyezését kérő figyelmeztetés megjelenítésére a távvezérlési munkamenet kezdete előtt, engedélyük és tudomásuk nélkül is figyelheti a felhasználókat. Beállíthatja a Csak megtekintés hozzáférési szintet (ekkor semmi sem módosítható a távvezérlésben), illetve a Teljes hozzáférés szintet is. A távvezérlési munkamenetben megjelenik a csatlakozó rendszergazda fiókja, hogy a felhasználók azonosíthassák, hogy ki csatlakozik a számítógépükhöz.  

 Alapértelmezés szerint a Configuration Manager engedélyt ad a helyi Rendszergazdák csoport távvezérlés.  

 A távvezérlés konfigurálása előtt gondolja át az adatvédelmi követelményeit.  

