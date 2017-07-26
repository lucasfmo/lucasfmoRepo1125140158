---
title: "Érvényesítési állapotváltásainak az Eszközintelligencia |} Microsoft Docs"
description: "Példák az érvényesítési Állapotváltások az Eszközintelligencia a System Center Configuration Managerben."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6230a6e5-a1f6-459b-84f1-07fbde0e70f0
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: f280e06f34c0ed355b7c2652c571e36eb6684c59
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="example-validation-state-transitions-for-asset-intelligence-in-system-center-configuration-manager"></a>Érvényesítési állapotváltásainak az Eszközintelligencia a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Az Eszközintelligencia érvényesítési állapotai a System Center Configuration Manager nem statikusak, és megváltozhatnak, amelyek az Eszközintelligencia-katalógusban tárolt adatokat érintő felügyeleti műveleteket. Ez a témakör példákat a lehetséges érvényesítési Állapotváltások.

##  <a name="BKMK_UncategorizedIsCategorized"></a> Kategorizálatlan katalóguselem a rendszergazda által kategorizálva  

|**Állapotváltás**|**Állapotváltás leírása**|  
|--------------------------|--------------------------------------|  
|**Kategorizálatlan**|Leltározott szoftvercím, amelyet a System Center Online korábban nem kategorizált vagy amelyet a rendszergazda felvett az eszközintelligencia-katalógusba.|  
|**Kategorizálatlan** – **Felhasználóáltal definiált**|A kategorizálatlan elemet a rendszergazda kategorizálta.|  

##  <a name="BKMK_CategorizedIsReCategorized"></a> Kategorizált katalóguselem a rendszergazda által újrakategorizálva  

|**Állapotváltás**|**Állapotváltás leírása**|  
|--------------------------|--------------------------------------|  
|**Ellenőrizve**|A System Center Online kutatói meghatározták a katalóguselemet, és az szerepel az eszközintelligencia-katalógusban.|  
|**Ellenőrizve** – **Felhasználó által definiált**|Az ellenőrzött katalóguselemet a rendszergazda újrakategorizálta.|  

> [!NOTE]  
>  Mivel a System Center Online-tól származó kategorizálási információ tárolása az adatbázisban történik, és nem törölhető, a rendszergazda később visszaállhat a System Center Online kategorizálására.  

##  <a name="BKMK_UserDefinedIsRecategorized"></a> Felhasználó által definiált katalóguselem a System Center Online által újrakategorizálva  

|**Állapotváltás**|**Állapotváltás leírása**|  
|--------------------------|--------------------------------------|  
|**Kategorizálatlan**|Az eszközintelligencia-katalógusba felvettek egy, a System Center Online, illetve a rendszergazda által korábban nem kategorizált, leltározott szoftvercímet.|  
|**Felhasználó által definiált**|A kategorizálatlan elemet a rendszergazda kategorizálta.|  
|**Felhasználó által definiált** – **Frissíthető**|Egy felhasználó által definiált elemet a System Center Online másképp definiált az eszközintelligencia-katalógus egymás utáni manuális tömeges frissítése során.<br /><br /> A rendszergazda a **Szoftverrészletek ütközésének feloldása** párbeszédpanelt használva eldöntheti, hogy az új kategorizálási információt vagy a korábbi, felhasználó által definiált értéket használja-e.|  
|**Frissíthető** – **Ellenőrizve**|A rendszergazda a **Szoftverrészletek ütközésének feloldása** párbeszédpanelt használja az előző katalógusfrissítés során a System Center Online-tól kapott új kategorizálási információ használatához.|  
|vagy||  
|**Frissíthető** – **Felhasználó által definiált**|A rendszergazda a **Szoftverrészletek ütközésének feloldása** párbeszédpanelt használja a felhasználó által definiált előző érték használatához.|  

> [!NOTE]  
>  Mivel a System Center Online-tól származó kategorizálási információ tárolása az adatbázisban történik, és nem törölhető, a rendszergazda később visszaállhat a System Center Online kategorizálására.  

##  <a name="BKMK_UncategorizedIsSubmitted"></a> Kategorizálatlan katalóguselem kategorizálásra elküldve a System Center Online rendszerhez  

|**Állapotváltás**|**Állapotváltás leírása**|  
|--------------------------|--------------------------------------|  
|**Kategorizálatlan**|Az Eszközintelligencia-adatbázisba felvettek egy, a System Center Online, illetve a rendszergazda által korábban nem kategorizált, leltározott szoftvercímet.|  
|**Kategorizálatlan** – **Függőben**|A kategorizálatlan katalóguselemet a rendszergazda kategorizálásra elküldte a System Center Online rendszerhez|  
|**Függőben** – **Ellenőrizve**|A System Center Online kategorizálta az elemet. A rendszergazda tömeges katalógusfrissítést használva vagy az eszközintelligencia-katalógus szinkronizálásával importálja az elemet az eszközintelligencia-katalógusba. Mindkettő az Eszközintelligencia szinkronizálási pont helyrendszer-szerepkör használatával érhető el.|  

##  <a name="BKMK_UserDefinedIsSubmitted"></a> Felhasználó által definiált katalóguselem kategorizálásra elküldve a System Center Online-hez  

|**Állapotváltás**|**Állapotváltás leírása**|  
|--------------------------|--------------------------------------|  
|**Kategorizálatlan**|Az eszközintelligencia-adatbázisba felvettek egy, a System Center Online, illetve egy rendszergazda által korábban nem kategorizált, leltározott szoftvercímet.|  
|**Felhasználó által definiált**|Ön kategorizálta a kategorizálatlan elemet.|  
|**Felhasználó által definiált** – **Függőben**|A felhasználó által definiált elemet elküldi kategorizálásra a System Center Online-hoz.|  
|**Függőben** – **Frissíthető**|Az egymás utáni katalógusszinkronizálás során a System Center Online másképp definiált egy felhasználó által definiált elemet. Az **Ütközés feloldása** műveletet használva eldöntheti, hogy az új kategorizálási információt vagy a korábbi, felhasználó által definiált értéket szeretné-e használni. Az ütközések feloldása kapcsolatos további információkért lásd: [szoftver részletek ütközések feloldása](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails).|  
|**Frissíthető** – **Ellenőrizve**|Használhatja az **Ütközés feloldása** műveletet, és kijelölheti a System Center Online-tól az előző katalógusfrissítés során kapott új kategorizálási információt. Az ütközések feloldása kapcsolatos további információkért lásd: [szoftver részletek ütközések feloldása](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails).|  
|vagy||  
|**Frissíthető** – **Felhasználó által definiált**|Használhatja az **Ütközés feloldása** műveletet, és kijelölheti a korábbi, felhasználó által definiált érték használatát. Az ütközések feloldása kapcsolatos további információkért lásd: [szoftver részletek ütközések feloldása](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails).|  

> [!NOTE]  
>  Mivel a System Center Online-tól származó kategorizálási információ tárolása az adatbázisban történik, és nem törölhető, később visszaállíthatja a System Center Online kategorizálását.  

