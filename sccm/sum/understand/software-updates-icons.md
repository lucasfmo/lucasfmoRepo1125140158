---
title: "Szoftverfrissítésekhez használt ikonok |} Microsoft Docs"
description: "A Configuration Manager konzol egy a szinkronizált frissítés vagy a szoftverfrissítési csoport állapotát jelző ikonok tartalmazza."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 63c5ef72-5715-4d86-85a2-71beba469fab
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 04c5ccc53263b2672096b564695a636bfb28d952
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="icons-used-for-software-updates-in-system-center-configuration-manager"></a>A System Center Configuration Managerben szoftverfrissítésekhez használt ikonok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Szinkronizált szoftverfrissítések jelennek meg a Configuration Manager konzolon, és az egyes szoftverfrissítések első oszlopa egy ikont, amely egy adott állapotot jelöl tartalmaz. A szoftverfrissítési csoportokat szintén egy ikon jelöli, mely a csoporthoz tartozó szoftverfrissítések állapotáról nyújt tájékoztatást. Ez a szakasz a szoftverfrissítési ikonokról és azok jelentéséről tartalmaz információkat.  

## <a name="icons-for-software-updates"></a>Szoftverfrissítési ikonok  
 A szinkronizált szoftverfrissítéseket az alábbi ikonok jelölik.  

### <a name="normal-icon"></a>Normál ikon  
 ![ikon](../media/Normal.jpg "normál ikon") a zöld nyíl ikon normál szoftverfrissítést jelöl.  

 **Leírás:**  

 A normál szoftverfrissítéseket a rendszer szinkronizálta és készen állnak a központi telepítésére.  

 **Fontos információk:**  

 Nincsenek speciális tudnivalók.  

### <a name="expired-icon"></a>Lejárt ikon  
 ![ikon](../media/Expired.jpg "lejárt ikon") a Fekete X ikon lejárt szoftverfrissítést jelöl. A lejárt szoftverfrissítések megtekintésével is azonosíthatja a **lejárt** a szoftverfrissítés a Configuration Manager konzol tartalmáról oszlop.  

 **Leírás:**  

 A lejárt szoftverfrissítések korábban telepítve lettek az ügyfélszámítógépekre, de lejártuk után többé nem hozható létre velük központi telepítés. Lejárt szoftverfrissítések frissítések aktív központi telepítés el lesznek távolítva, és már nem lesz elérhető az ügyfelek számára.  

 **Fontos információk:**  

 Nincsenek speciális tudnivalók.

### <a name="superseded-icon"></a>Felváltott ikon  
 ![ikon](../media/Superseded.jpg "felváltott ikon") a sárga csillag ikon felváltott szoftverfrissítést jelöl. Felváltott szoftverfrissítések megtekintésével is azonosíthatja a **felváltott** a szoftverfrissítés a Configuration Manager konzol tartalmáról oszlop.  

 **Leírás:**  

 A felváltott szoftverfrissítéseket leváltotta a szoftverfrissítés egy újabb verziója. Amikor egy szoftverfrissítés felvált egy másik szoftverfrissítés, az általában az alábbiak egyikét eredményezi:  

-   Javít, fejleszt vagy bővít egy korábbi frissítésekben már megjelent javítást.  

-   Javítja a szoftverfrissítés telepítésének jóváhagyása esetén az ügyfelek által telepített szoftverfrissítési fájlcsomag hatékonyságát. A felváltott frissítés tartalmazhat például olyan fájlokat, amelyek már nem relevánsak a javítás vagy az új szoftverfrissítés által aktuálisan támogatott operációs rendszerek számára, ezért ezeket a fájlokat a frissítést felváltó szoftverfrissítési fájlcsomag nem tartalmazza.  

-   A termék újabb verzióját frissíti, más szóval nem alkalmazható a termék régebbi verzióira vagy konfigurációira. A szoftverfrissítések más szoftverfrissítéseket is felülírhatnak, ha azokat a nyelvi támogatás bővítése érdekében módosították. Előfordulhat például, hogy a Microsoft Office termékfrissítésének egy újabb verziójával megszűnik egy régebbi operációs rendszer támogatása, azonban újabb támogatott nyelvek kerülnek a szoftverfrissítés eredeti kiadásába.  

 A Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanel Helyettesítési szabályok lapján beállíthatja a felváltott szoftverfrissítések kezelését. További információkért lásd: [Helyettesítési szabályok](../plan-design/plan-for-software-updates.md#BKMK_SupersedenceRules).  

 **Fontos információk:**  

 Ha lehetséges, az ügyfélszámítógépekre a felváltott szoftverfrissítés helyett az azt felváltó szoftverfrissítést telepítse. A szoftverfrissítést felváltó szoftverfrissítések listáját a szoftverfrissítés tulajdonságainak **Helyettesítési információk** lapján jelenítheti meg.  

### <a name="invalid-icon"></a>Érvénytelen ikon  
 ![ikon](../media/Invalid.jpg "érvénytelen ikon") a piros X ikon érvénytelen szoftverfrissítést jelöl.  

 **Leírás:**  

 Az érvénytelen szoftverfrissítések egy aktív központi telepítés részét képezik, de a tartalom (a szoftverfrissítési fájlok) valamilyen okból nem áll rendelkezésre. Ez az alábbi esetekben fordulhat elő:  

-   Sikeresen elvégezte a szoftverfrissítés központi telepítését, de a szoftverfrissítési fájlt törölték a központi telepítési csomagból, és többé nem érhető el.  

-   Létrehozott egy szoftverfrissítési központi telepítést egy helyen, és a központi telepítési objektumot sikerült replikálni egy alárendelt helyre, azonban a központi telepítési csomagot nem sikerült az alárendelt helyre replikálni.  

 **Fontos információk:**  

 Ha a szoftverfrissítés tartalma hiányzik, az ügyfelek nem tudják telepíteni a szoftverfrissítést, amíg a tartalom elérhetővé nem válik egy terjesztési pontot. A tartalmat a **Továbbterjesztés** művelettel ismét továbbíthatja a terjesztési pontokra. Ha egy fölérendelt helyen létrehozott központi telepítés részét képező szoftverfrissítés tartalma hiányzik, a szoftverfrissítést replikálni kell az alárendelt helyre, vagy tovább kell terjeszteni oda. További információ a tartalmak továbbterjesztésről: [a terjesztett tartalom kezeléséhez](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

### <a name="metadata-only-icon"></a>Csak metaadat ikon
 ![ikon](../media/MetadataOnly.png "csak metaadat ikon") a kék nyíl ikon a csak metaadatokat tartalmazó szoftverfrissítést jelöl.

 **Leírás:**  

 Csak metaadatokat tartalmazó szoftverfrissítések jelentéskészítés a Configuration Manager konzolon érhetők el. A csak metaadatokat tartalmazó szoftverfrissítések nem telepíthetők és tölthetők le, mert a szoftverfrissítés metaadataihoz nem kapcsolódnak szoftverfrissítési fájlok.  

 **Fontos információk:**  

 A csak metaadatokat tartalmazó szoftverfrissítések kizárólag jelentéskészítési célokat szolgálnak és nem használhatók szoftverfrissítések központi telepítésére.  

## <a name="icons-for-software-update-groups"></a>Szoftverfrissítési csoportok ikonjai  
 A szoftverfrissítési csoportokat az alábbi ikonok jelölik.  

### <a name="normal-icon"></a>Normál ikon  
 ![ikon](../media/Normal.jpg "normál ikon") a zöld nyíl ikon a csak normál szoftverfrissítéseket tartalmazó szoftverfrissítési csoportot jelöl.  

 **Fontos információk:**  

 Nincsenek speciális tudnivalók.  

### <a name="expired-icon"></a>Lejárt ikon  
 ![ikon](../media/Expired.jpg "lejárt ikon") a Fekete X ikon olyan szoftverfrissítési csoportot, amely egy vagy több lejárt szoftverfrissítést tartalmaz jelöl.  

 **Fontos információk:**  

 Ha lehetséges, mindig távolítsa el vagy cserélje le a szoftverfrissítési csoportban található lejárt szoftverfrissítéseket.  

### <a name="superseded-icon"></a>Felváltott ikon  
 ![ikon](../media/Superseded.jpg "felváltott ikon") a sárga csillag ikon jelöli egy szoftverfrissítési csoport, amely tartalmaz egy vagy több felváltott szoftverfrissítései.  

 **Fontos információk:**  

 Ha lehetséges, a szoftverfrissítési csoportban található felváltott szoftverfrissítéseket cserélje le az azokat felváltó szoftverfrissítésre.  

### <a name="invalid-icon"></a>Érvénytelen ikon  
 ![ikon](../media/Invalid.jpg "érvénytelen ikon") a piros X ikon olyan szoftverfrissítési csoportot, amely egy vagy több érvénytelen szoftverfrissítést tartalmaz jelöl.  

 **Fontos információk:**  

 Ha a szoftverfrissítés tartalma hiányzik, az ügyfelek nem tudják telepíteni a szoftverfrissítést, amíg a tartalom elérhetővé nem válik egy terjesztési pontot. A tartalmat a **Továbbterjesztés** művelettel ismét továbbíthatja a terjesztési pontokra. Ha egy fölérendelt helyen létrehozott központi telepítés részét képező szoftverfrissítés tartalma hiányzik, a szoftverfrissítést replikálni kell az alárendelt helyre, vagy tovább kell terjeszteni oda. További információ a tartalmak továbbterjesztésről: [a terjesztett tartalom kezeléséhez](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_manage).  

