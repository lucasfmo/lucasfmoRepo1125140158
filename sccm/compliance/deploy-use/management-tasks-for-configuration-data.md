---
title: "Konfigurációs adatok kezelése |} Microsoft Docs"
description: "Miután létrehozott és az alapkonfigurációktól a System Center Configuration Managerben, a más parancsok segítségével különféle műveleteket hajtson végre."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b48c693c-d2b0-4707-a5dd-fe92172c49fe
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 1a6084834384e695b49a71fe23833049c86f8dbc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-configuration-data-in-system-center-configuration-manager"></a>Kezelheti a konfigurációs adatok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Miután létrehozott konfigurációs elemeket és referenciakonfigurációkat a System Center Configuration Managerben, további parancsok is segítik a különféle műveleteket hajtson végre.  

## <a name="manage-configuration-items"></a>Konfigurációelemek kezelése  

-   Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások** > **Konfigurációelemek**, válassza ki a kezelni kívánt konfigurációelemet, majd válassza ki a kezelési feladatot.  

|Kezelési feladat|Részletek|  
|---------------------|-------------|  
|**Gyermek-konfigurációelem létrehozása**|A **Gyermek-konfigurációelem létrehozása varázsló** megnyitása, melyben a kiválasztott konfigurációelemből létrehozhat egy gyermek-konfigurációelemet.<br /><br /> Mobileszköz-konfigurációelemekből nem hozhatók létre gyermek-konfigurációelemek.<br /><br /> További információkért lásd: [gyermek-konfigurációelemek létrehozása](../../compliance/deploy-use/create-child-configuration-items.md).|  
|**Változat-nyilvántartás**|A **Konfigurációelem változat-nyilvántartása** párbeszédpanel megnyitása, melyen megtekintheti és kezelheti a kiválasztott konfigurációelem korábbi változatait.|  
|**XML-definíció megtekintése**|A kiválasztott konfigurációelem XML-definíciós fájljának megjelenítése egy új ablakban. Ez az információ akkor lehet hasznos, ha manuálisan szeretné szerkeszteni a konfigurációs adatokat.|  
|**Exportálásálás**|A konfigurációelem exportálása egy kabinetfájl (.cab) formájában, megadva, hogy az az adott helyen készült. Ezután importálhatja azt ugyanaz vagy egy másik Configuration Manager-hely. A rendszer a konfigurációs adatokat DCM-kivonattá alakítja.|  
|**Másolás**|Másolat készítése a kiválasztott konfigurációelemről a megadott névvel. Az új konfigurációelem semmilyen kapcsolatot nem őriz meg az eredeti konfigurációelemmel. Ez azt jelenti, hogy a másolt konfigurációelem nem fog a későbbiekben is konfigurációs adatokat örökölni az eredeti konfigurációelemtől.|  
|**Törlés**|A **Konfigurációelem törlése** párbeszédpanel megnyitása, melyen áttekintheti az esetleges, az adott konfigurációelemre mutató hivatkozásokat.<br /><br /> Ahhoz, hogy törölhessen egy konfigurációelemet, el kell távolítania minden, az adott konfigurációelemre mutató hivatkozást.|  

## <a name="manage-configuration-baselines"></a>Alapkonfigurációk kezelése  

-   Az a **eszközök és megfelelőség** munkaterületet, bontsa ki a **megfelelőségi beállítások** > **Referenciakonfigurációk**, válassza ki a kezelni kívánt alapkonfigurációt, majd válassza ki a kezelési feladatot.  


|Kezelési feladat|Részletek|  
|---------------------|-------------|  
|**Tagok megjelenítése**|Az összes, az alapkonfiguráció által hivatkozott konfigurációelem megjelenítése.|  
|**Összefoglalás ütemezése**|A megjelenített adatok konfigurálja az ütemezést, amely szerint a **Referenciakonfigurációk** csomópont a Configuration Manager konzol frissül, a Helyadatbázis legfrissebb adataival.|  
|**Összefoglalás futtatása**|Az összefoglalás hatására az **Alapkonfigurációk** csomópontban megjelenített adatok a helyadatbázis legfrissebb adataival lesznek frissítve. A művelet végrehajtása több percig is eltarthat. Előfordulhat, hogy a **Frissítés** lehetőségre kell kattintania ahhoz, hogy a konzolon megjelenjenek a legfrissebb adatok.|  
|**XML-definíció megtekintése**|A kiválasztott alapkonfiguráció XML-definíciós fájljának megjelenítése egy új ablakban. Ez az információ akkor lehet hasznos, ha manuálisan szeretné szerkeszteni a konfigurációs adatokat.|  
|**Engedélyezés**|Az adott alapkonfiguráció a megfelelőség figyeléséhez való használatának engedélyezése.|  
|**Letiltás**|Az adott alapkonfiguráció letiltása, amely hatására az annak való megfelelőség már nem lesz értékelve az ügyfélszámítógépeken. Az erre az alapkonfigurációra hivatkozó alapkonfigurációk is le lesznek tiltva.|  
|**Exportálásálás**|Az alapkonfiguráció exportálása egy kabinetfájl (.cab) formájában, megadva, hogy az az adott helyen készült. Ezután importálhatja azt ugyanaz vagy egy másik Configuration Manager-hely. A rendszer a konfigurációs adatokat DCM-kivonattá alakítja.<br /><br /> Konfigurációs adatok importálásával kapcsolatos információkért lásd: [konfigurációs adatok importálása](../../compliance/deploy-use/import-configuration-data.md).|  
|**Másolás**|Másolat készítése a kiválasztott alapkonfigurációról a megadott névvel. Az új alapkonfiguráció semmilyen kapcsolatot nem őriz meg az eredeti alapkonfigurációval.|  
|**Törlés**|Az **Alapkonfiguráció törlése** párbeszédpanel megnyitása, melyen áttekintheti az esetleges, az adott alapkonfigurációra mutató hivatkozásokat.<br /><br /> Ahhoz, hogy törölhessen egy alapkonfigurációt, el kell távolítania minden, az adott alapkonfigurációra mutató hivatkozást.|  
|**Telepítés**|Az **Alapkonfiguráció központi telepítése** párbeszédpanel megnyitása, amelyen egy vagy több alapkonfiguráció a hierarchiában lévő eszközökre való központi telepítését végezheti el.<br /><br /> További információkért lásd: [alapkonfigurációk központi telepítése](../../compliance/deploy-use/deploy-configuration-baselines.md).|  

