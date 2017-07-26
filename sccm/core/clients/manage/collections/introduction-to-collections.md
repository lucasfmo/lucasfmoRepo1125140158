---
title: "Gyűjtemények bemutatása |} Microsoft Docs"
description: "Ismerkedjen meg a System Center Configuration Manager gyűjtemények használatával."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
caps.latest.revision: 8
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 547d231d48ccbc8241e9f1f8f71e3750b266b73e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>A System Center Configuration Manager gyűjteményeinek bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Gyűjtemények segítségével erőforrások kezelhető egységekbe rendezheti. Az ügyfél felügyeleti igényeinek megfelelően, és egyszerre több erőforrást a műveletek végrehajtásához gyűjteményeket hozhat létre. 

A kezelési feladatok támaszkodnak, vagy egy vagy több gyűjteményt használata szükséges. Bár minden rendszer beépített gyűjteményt, akkor felügyeleti feladatok használata nem ajánlott. Hozzon létre egyéni gyűjteményeket, amelyekkel pontosabban azonosíthatja meg olyan feladatra, felhasználók vagy eszközök.  

 Beépített és egyéni gyűjtemények jelennek meg a **Felhasználógyűjtemények** és **Eszközgyűjtemények** csomópontjának a **eszközök és megfelelőség** munkaterület a Configuration Manager konzolon.  

 Nemrég megtekintett gyűjtemények jelennek meg a **felhasználók** csomópont és a a **eszközök** csomópontja a **eszközök és megfelelőség** munkaterületen.  

Íme néhány példa a gyűjtemény használja:  

|Művelet|Példa|  
|---------|-------|  
|Erőforrások csoportosítása|A szervezet hierarchiáján alapuló erőforrások gyűjtemények hozhat létre.<br /><br /> Például létrehozhat egy gyűjtemény összes számítógép található a "Londoni központ" Active Directory szervezeti egység (OU). Ez a típusú gyűjtemény létrehozásával kapcsolatos további információkért lásd: [gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md).<br /><br /> Ez a gyűjtemény műveletek, például az Endpoint Protection-beállítások konfigurálása, eszközök energiagazdálkodási beállításainak konfigurálása, vagy a Configuration Manager-ügyfél telepítése használhat.|  
|[Alkalmazástelepítés]|Az összes olyan számítógép, amely nem rendelkezik a Microsoft Office 2013 telepítve van, és majd központilag telepítenie kell az adott gyűjtemény összes számítógépén gyűjtemény hozható létre.<br /><br /> Ennek a feladatnak az elvégzésére alkalmazáskövetelményeket is használhat. További információkért lásd: [Alkalmazások létrehozása a System Center Configuration Managerrel](../../../../apps/deploy-use/create-applications.md).|  
|[Ügyfélbeállítások kezelése](../../../../core/clients/deploy/about-client-settings.md)|Bár az alapértelmezett ügyfélbeállítások a Configuration Managerben az összes eszközre és minden felhasználóra vonatkoznak, létrehozhat egyéni ügyfélbeállításokat, amelyek eszközök vagy felhasználók gyűjteményére vonatkoznak.<br /><br /> Például ha azt szeretné, hogy a távvezérlés néhány kivételével az összes eszközön elérhető legyen, konfigurálja az alapértelmezett ügyfélbeállítások segítségével lehetővé teszi a távvezérlés, majd konfigurálja az egyéni ügyfélbeállításokat, amelyek nem lehetővé teszi a távvezérlés, és telepíteni azokat az kivételes ügyfelek gyűjteményébe. |  
|[Energiagazdálkodás](../power/introduction-to-power-management.md)|Beállíthatja, hogy adott energiaellátási beállítások gyűjteményenként.|  
|[Szerepkör alapú felügyelet](../../../../core/servers/deploy/configure/configure-role-based-administration.md)|Használja a gyűjtemények szabályozhatja, melyik felhasználói csoportokra van a különböző funkciók eléréséhez a Configuration Manager konzolon.|  
|[Karbantartási időszakok](../../../../core/clients/manage/collections/use-maintenance-windows.md)|A karbantartási időszakok határozza meg egy időszakot, amikor Configuration Manager különböző műveleteivel lehet elvégezni egy eszközgyűjtemény tagjain. |  


## <a name="collection-types-in-configuration-manager"></a>A Configuration Manager gyűjteménytípusai  
 Configuration Manager rendelkezzen a beépített gyűjteményeket, gyakori műveletekhez, és egyéni gyűjtemények is létrehozhat.   

### <a name="built-in-collections"></a>Beépített gyűjtemények  
 Alapértelmezés szerint a Configuration Manager tartalmazza a következő gyűjteményeket, amely nem módosítható.  

|**Gyűjtemény neve**|Leírás|  
|-------------------------|-----------------|  
|**Minden felhasználói csoport**|Az Active Directory biztonságicsoport-felderítési módszerével észlelt felhasználói csoportokat tartalmazza.|  
|**Minden felhasználó**|Az Active Directory-felhasználófelderítési módszerével észlelt felhasználókat tartalmazza.|  
|**Minden felhasználó és felhasználói csoport**|A Minden felhasználó és Minden felhasználói csoport gyűjteményt tartalmazza. Ez a gyűjtemény felhasználói és felhasználóicsoport-erőforrások legnagyobb hatókörét tartalmazza.|  
|**Minden asztali és kiszolgálóügyfél**|A Configuration Manager-ügyféllel rendelkező kiszolgálói és asztali eszközöket tartalmazza. A tagságot a Szívveréses felderítés funkció tartja nyilván.|  
|**Minden mobileszköz**|A Configuration Manager által kezelt mobileszközöket tartalmazza. A tagság azokra a mobileszközökre korlátozott, amelyek sikeresen hozzá lettek rendelve egy helyhez, vagy amelyeket felderített az Exchange Server-összekötő.|  
|**Minden rendszer**|Az összes asztali és Kiszolgálóügyfél, minden mobileszköz és a minden ismeretlen számítógép gyűjteményt és a Microsoft Intune által beléptetett minden mobileszköz tartalmazza. Ez a gyűjtemény eszközerőforrások legnagyobb hatókörét tartalmazza.|  
|**Minden ismeretlen számítógép**|Általános számítógépes rekordokat tartalmaz több számítógépplatformhoz. Ennek a gyűjteménynek a segítségével operációs rendszert telepíthet feladatütemezés és PXE-rendszerindítás, rendszerindító adathordozó vagy előkészített adathordozó használatával.|  

### <a name="custom-collections"></a>Egyéni gyűjtemények  
 A Configuration Manager létrehoz egy egyéni gyűjteményt, ha adott gyűjtemény tagsága határozza meg egy vagy több gyűjteményszabály leírtak [gyűjtemények létrehozása a System Center Configuration Managerben](../../../../core/clients/manage/collections/create-collections.md). 


