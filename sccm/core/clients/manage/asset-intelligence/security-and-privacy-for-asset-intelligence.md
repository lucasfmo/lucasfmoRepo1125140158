---
title: "Asset Intelligence biztonsági adatvédelmi |} Microsoft Docs"
description: "Az Eszközintelligencia biztonsági és adatvédelmi tudnivalókat a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d0c6f7a0-dcae-4e6d-aa28-35d464d97ff7
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: b12054cce52e2b83715a083d78a62e06b5127a2f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-asset-intelligence-in-system-center-configuration-manager"></a>Biztonság és adatvédelem az Eszközintelligencia a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a biztonsági és adatvédelmi tudnivalókat a System Center Configuration Manager Eszközintelligencia tartalmazza.  

##  <a name="BKMK_Security_AI"></a> Az Eszközintelligencia szolgáltatás biztonságára vonatkozó bevált gyakorlatok  
 Az Eszközintelligencia használata során a következő bevált biztonsági gyakorlatok betartása ajánlott:  

|Bevált biztonsági gyakorlat|További információ|  
|----------------------------|----------------------|  
|Licencfájl (Microsoft mennyiségi licencelési fájl vagy általános licenckimutatási fájl) importálásakor gondoskodjon a fájl és a kommunikációs csatorna biztonságáról.|Az NTFS fájlrendszer engedélyeinek segítségével biztosítsa, hogy csak a jogosult felhasználók férjenek hozzá a licencfájlokhoz, valamint Server Message Block (SMB) típusú aláírás használatával gondoskodjon az adatok épségéről, miközben azok az importálási folyamat során a helykiszolgálóra kerülnek át.|  
|A licencfájlok importálása során törekedjen minél kevesebb engedély kiosztására.|A licencfájlokat importáló rendszergazdának szerepköralapú adminisztráció használatával biztosítson engedélyt az Eszközintelligencia kezeléséhez. A beépített Eszközkezelő szerepkör rendelkezik ezzel az engedéllyel.|  

##  <a name="BKMK_Privacy_HardwareInventory"></a> Az Eszközintelligencia szolgáltatással kapcsolatos adatvédelmi tudnivalók  
 Az Eszközintelligencia bővíti a Configuration Manager eszköz látható a vállalat magasabb szintű biztosításához. Az Eszközintelligencia szolgáltatás adatgyűjtési funkcióját a rendszer nem engedélyezi automatikusan. A hardverleltár jelentési osztályainak engedélyezésével módosíthatja a gyűjtött információk típusát. További információkért lásd: [Eszközintelligencia konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Eszközintelligencia szolgáltatás adatait a Configuration Manager adatbázisban tárolódik a Hardverleltár-információk azonos módon. Ha az ügyfelek HTTPS protokoll használatával kapcsolódnak a felügyeleti pontokhoz, az adatokat a rendszer a felügyeleti pontra való átvitel során mindig titkosítja. Ha az ügyfelek HTTP protokollal kapcsolódnak, beállíthatja a leltáradatok átvitelének aláírását és titkosítását. A leltáradatokat a rendszer titkosítás nélkül tárolja az adatbázisban. Ezek az adatok addig maradnak az adatbázisban, amíg a 90 naponta végrehajtott **Elavult leltárelőzmények törlése** helykarbantartási feladat el nem távolítja azokat. Beállíthatja a törlési időközt.  

 Az Eszközintelligencia szolgáltatás nem küld információt a Microsoftnak a felhasználókról, a számítógépekről és a licenchasználatról. Dönthet úgy, hogy a System Center Online kérelmeit kategorizálásra küldi. Ennek keretében egy vagy több kategorizálatlan szoftvercímet megjelölhet és kivizsgálás vagy kategorizálás céljából elküldhet a System Center Online-nak. A feltöltését követően a Microsoft kutatói azonosítják és kategorizálják a szoftvert, majd ezt az információt elérhetővé teszik az online szolgáltatást használó összes ügyfél számára. Amikor a System Center Online-nak adatokat küld, érdemes a következő adatvédelmi szempontokat figyelembe venni:  

-   Feltöltéskor a rendszer csak a kiválasztott, általános szoftveradatokat (név, kiadó stb.) küldi el a System Center Online-nak. A leltáradatokat a rendszer nem küldi el feltöltéskor.  

-   A feltöltés soha nem automatikusan történik, és a rendszer kialakítása nem teszi lehetővé e feladat automatizálását. Az egyes szoftverek feltöltésének kiválasztását és jóváhagyását manuális módszerrel kell elvégezni.  

-   A feltöltési folyamat megkezdése előtt egy párbeszédpanelen megjelenik, hogy pontosan milyen adatok lesznek feltöltve.  

-   A rendszer nem küld licencadatokat a Microsoftnak. A Configuration Manager-adatbázis különálló részén a licencekre vonatkozó információkat tárolja, és nem lehet küldeni a Microsoftnak.  

-   Minden feltöltött szoftver nyilvános lesz abban az értelemben, hogy az adott alkalmazáshoz és a kategorizálásához kapcsolódó információ bekerül a System Center Online Eszközintelligencia-katalógusába, és a katalógus más felhasználói számára is letöltődik.  

-   Az Eszközintelligencia-katalógus nem rögzíti a szoftvercím forrását, és azt nem teszi elérhetővé más ügyfelek számára. Arra azonban ügyelnie kell, hogy ne töltsön fel olyan alkalmazáscímeket, amelyek személyes adatot tartalmaznak.  

-   A már feltöltött adatok nem hívhatók vissza.  

 Az Eszközintelligencia szolgáltatás adatgyűjtésének konfigurálását megelőzően, illetve mielőtt eldöntené, hogy szeretne-e információkat küldeni a System Center Online-nak, vegye figyelembe munkahelye adatvédelmi követelményeit.  

