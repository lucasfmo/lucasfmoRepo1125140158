---
title: "Támogatása Windows 10 |} Microsoft Docs"
description: "További tudnivalók a Windows 10-verziók által támogatott ügyfelek vagy az OSD a System Center Configuration Managerrel."
ms.custom: na
ms.date: 05/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 5
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ed5efcf7b305f8bee6e99e00c5285f6ae7033d82
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Windows 10-támogatása a System Center Configuration Managerben  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 Ez a témakör részletesen a különböző verzióihoz készült System Center Configuration Manager aktuális ágának használata a Windows 10-es verzióját. Ez a következő teendőket foglalja magában:
 -  Windows 10-et a Configuration Manager-ügyfél.
 -  A Windows 10-es Windows Assessment and Deployment Kit (ADK) csomagot.

## <a name="windows-10-as-a-client"></a>Windows 10-et egy ügyfél
A Configuration Manager megkísérli támogatást nyújt a ügyfélként minden új Windows 10-es verzió a lehető leghamarabb követően, hogy a Windows-verziókban. Mivel a termékek külön fejlesztési és kiadás ütemezése, a támogatást, amely a Configuration Manager függ a verziók és az egyes termékek kiadási.

Például a Configuration Manager verziója után a mátrix eldobja [verzió támogatása](/sccm/core/servers/manage/current-branch-versions-supported) karakterlánccal végződik-e. Hasonlóképpen például a vállalati 2015 LTSB vagy 1607 (CBB) Windows 10-verziók támogatását eldobja a mátrix a Configuration Manager támogatott konfigurációk listáját való eltávolításakor. Lásd: [elavult operációs rendszerek](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) további információt.

-   A következő információk kiegészítések [ügyfelek és eszközök támogatott operációs rendszerekről](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Ha a hosszú távú karbantartási ág a Configuration Manager használatához [támogatott konfigurációi a hosszú távú karbantartási ág](/sccm/core/understand/supported-configurations-for-ltsb).

|Windows 10-verziók                    |A Configuration Manager 1606          |A Configuration Manager 1610          |    A Configuration Manager 1702 |
|---------------------|-----|-----|-----|
|Vállalati 2015 LTSB                   |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |
|1507 <br />(*verziója esetén lásd:*)            |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |
|1511-ES (CB), (CBB)<br />(*verziója esetén lásd:*) |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |
|Vállalati 2016 LTSB                   |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |
|1607 (CB)    <br />Évforduló frissítés<br />(*verziója esetén lásd:*)      |![Visszafelé kompatibilis](media/blue_compat.png) |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |
|1607 (CBB)    <br />Évforduló frissítés<br />(*verziója esetén lásd:*)      |![Nem támogatott](media/Red_X.png)   |![Támogatott](media/green_check.png) |![Támogatott](media/green_check.png) |
|1703 (CB)    <br />Creators frissítése<br />(*verziója esetén lásd:*)      |![Nem támogatott](media/Red_X.png)   |![Nem támogatott](media/Red_X.png) |![Visszafelé kompatibilis](media/blue_compat.png) |


**Verziója esetén:** Vállalati, Pro, Education, Pro oktatási   

|Kulcs|
|--|
|![Támogatott](media/green_check.png) = **támogatott**  |
|![Nem támogatott](media/blue_compat.png)  = **Backwards kompatibilis** – Ez azt jelenti, hogy meglévő felügyeleti ügyfélszolgáltatásokat (Hardverleltár, szoftverleltár, szoftverfrissítések, stb.) a Windows 10 aktuális ágának új build kell működniük. Olyan ismert probléma vagy figyelmeztetések dokumentálni lesz. <br><br>Ez a megközelítés lehetővé teszi az telepítéséhez és kezeléséhez új Windows 10 CB lehetőséget az alkalmazás kompatibilitási támogatási nap egy épít, anélkül, hogy egy új Configuration Manager frissítési verzióra. |
|![Támogatott](media/Red_X.png) = **nem támogatott**|


## <a name="windows-10-adk"></a>Windows 10 ADK
A Configuration Managerrel, operációs rendszerek központi telepítéséhez a [a Windows ADK csomag külső függőségként](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) szükséges.

A következő táblázat a Windows 10 ADK, amely csak akkor használhatja a Configuration Manager különböző verziói verzióinak listázása.

|Windows 10 ADK-verzió |A Configuration Manager 1606 |A Configuration Manager 1610  |A Configuration Manager 1702 |
|--------------------|-----|-----|-----|
|1507  |![Nem támogatott](media/Red_X.png)         |![Nem támogatott](media/Red_X.png)  |![Nem támogatott](media/Red_X.png)|
|1511  |![Visszafelé kompatibilis](media/blue_compat.png)|![Nem támogatott](media/Red_X.png)  |![Nem támogatott](media/Red_X.png)|
|1607  |![Támogatott](media/green_check.png)       |![Támogatott](media/green_check.png)|![Visszafelé kompatibilis](media/blue_compat.png) |
|1703  |![Nem támogatott](media/Red_X.png)         |![Nem támogatott](media/Red_X.png)  |![Támogatott](media/green_check.png) |  

|Kulcs|
|--|
|![Támogatott](media/green_check.png) = **támogatott** – a Windows ADK megfelelő telepít Windows-verzió Windows javasolja. Például, használja a Windows ADK for Windows 10 verzióra 1703 Windows 10-es verzió 1703 telepítésekor.  |
|![Visszafelé kompatibilis](media/blue_compat.png)  = **visszamenőlegesen kompatibilis** – Ez a kombináció nem lett tesztelve, de kell működnie. Olyan ismert probléma vagy figyelmeztetések dokumentálni lesz. |
|![Támogatott](media/Red_X.png) = **nem támogatott**|

