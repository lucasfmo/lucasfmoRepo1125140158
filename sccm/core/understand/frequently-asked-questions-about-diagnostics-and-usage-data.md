---
title: "Diagnosztikai adatok – gyakori kérdések |} Microsoft Docs"
description: "Keresés a System Center Configuration Manager diagnosztikai és használati adatok kapcsolatos gyakori kérdésekre."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fe32aa2-d594-4ad0-a291-b8f5395ac50b
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6cf291d79c1c5d9540f809fcb00e7ab48e0c3d3b
ms.openlocfilehash: 177a30a30f6b8579fa1956d28581d4f9d3a11838
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="frequently-asked-questions-about-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>A System Center Configuration Manager diagnosztikai és használati adataival kapcsolatos gyakori kérdések

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A következő vannak kapcsolatos gyakori kérdések a diagnosztikai és használati adatok a System Center Configuration Manager:  

###  <a name="bkmk_off"></a> Hogyan lehet kikapcsolni a telemetriát?  
Telemetria nem kapcsolható ki. Azonban dönthet úgy gyűjtött telemetriai adatok szintjét. Is használhatja a szolgáltatáskapcsolódási pont offline módban telemetriai adatokat elküldésekor kezeléséhez.

A Configuration Manager aktuális ágának támogatásához a Windows 10 és a Microsoft Intune új verzióit rendszeresen frissíteni kell. A Microsoft megköveteli legalább az alapszintű diagnosztikai és használati adatokat a termék naprakészen tartása, a frissítési élmény javításához, és javíthatja a minőségének és biztonságának a termék.

###  <a name="bkmk_retention"></a> Mi az adatmegőrzés időtartama?  
 A diagnosztikai és használati adatok egy évig őrzi meg a rendszer.  

###  <a name="bkmk_update"></a> A rendszer küld diagnosztikai és használati adatokat a termék telepítésekor vagy frissítésekor?  
 Nem. A diagnosztikai és a használati adatok küldése a hely telepítése és működőképes állapotba hozása után kezdődik el.  

###  <a name="bkmk_frequency"></a> Milyen gyakran történik az adatküldés?  
 Az SQL tárolt eljárások minden hetedik napon futnak (az a dátum a hely telepítve van). Online módban a szolgáltatáskapcsolati pont állítható be az adatok feltöltésére a lekérdezések futtatása után. Offline módban a rendszergazda tölti fel az adatokat a szolgáltatáskapcsolati eszköz használatával. (Vegye figyelembe, hogy az adatok nem kezdetben érhető el a hely telepítését követő hét napon kapcsolat nélküli használatra.)  

###  <a name="bkmk_network"></a> Az adatok felhasználhatók hálózati térkép létrehozásához?  
 Ahogy az a diagnosztikai és használati adatok gyűjtése a System Center Configuration Manager szintek leírása, a helyadatok között megtalálhatók az egyes helyek időzóna-információk. Ezt az információt biztosíthat a földrajzi elhelyezkedéséről és globális eloszlásáról a hierarchiában lévő helyek betekintést. Azonban nem szerepelnek hálózati adatok összegyűjtötték, (ilyen IP-címek vagy földrajzi információk részletes).
 - [Diagnosztikai adatok az 1511-es](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
 - [Diagnosztikai adatok az 1602-es](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
 - [Diagnosztikai adatok 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)
 - [Diagnosztikai adatok 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)


###  <a name="bkmk_tables"></a> Az adatgyűjtés kiterjed az egyéni táblák adataira is?  
 Nem. Diagnosztikai és használati adatok alapértelmezett terméktábláiból az adatbázisban tárolt SQL-eljárások gyűjtik (ezek mindegyike fűzve előtagként **TEL_** ). Az SQL sémaészlelési lekérdezésének részeként az összes táblanévből kivonat készül az ismert alapértékekkel történő összehasonlításához. Ez meg tudja állapítani, hogy létezik-e egyéni táblák az adatbázisban (vagyis az adatbázisséma ki van bővítve az alapértelmezett), de nem minden ilyen táblákban található adatokat.  

###  <a name="bkmk_databases"></a>Az egyéb adatbázisok nevére vagy adataira is más adatbázisokban?  
 Nem. Az adatokat gyűjtő tárolt eljárások a helyadatbázisra korlátozódnak.  

## <a name="see-also"></a>További információ  
 [Diagnosztikai és használati adatokat a System Center Configuration Managerhez](../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)

