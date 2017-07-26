---
title: "Linux/UNIX rendszerű ügyfelek - Configuration Manager figyelése |} Microsoft Docs"
description: "A Linux és UNIX rendszerű kiszolgálókon a System Center Configuration Manager ügyfelek figyelése."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d6478fa75c27e07e22702f3f8d5577df73ebdd48
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>A Linux és UNIX rendszerű kiszolgálókhoz készült ügyfelek figyelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager konzolon, ugyanazokkal a módszerekkel segítségével tekintse meg a Windows-alapú ügyfelekről a Linux és UNIX rendszerű kiszolgálókról információk is megtekinthetők.  

 Többek között az alábbi információkat tekintheti meg:  

-   Az ügyfelektől, a Configuration Manager konzol irányítópultok a állapotának részletei  

-   Az alapértelmezett Configuration Manager-jelentések ügyfelek adatait  

-   Az erőforrás-kezelő leltáradatait  

 A következő szakaszok ismertetik ezeket az adatokat lekérni az erőforrás-kezelő és a jelentések kapa.  

##  <a name="BKMK_UseResourceExpforLnU"></a>Erőforrás-kezelő használata a Linux és UNIX rendszerű kiszolgálókhoz készült leltár megtekintése  

 Után a Configuration Manager-ügyfél elküldte a hardverleltárat a Configuration Manager-hely, erőforrás-kezelő segítségével megtekintheti az adatokat. A Configuration Manager-ügyfél Linux és UNIX rendszerű nem veszi fel új osztályokat vagy nézeteket a leltározáshoz az erőforrás-kezelővel. A Linux és UNIX rendszerre vonatkozó leltáradatokat meglévő WMI-osztályokra képezi le. Az erőforrás-kezelő használatával a Windows-alapú besorolásokkal tekintheti meg a Linux és UNIX rendszerű kiszolgálók leltáradatait.  

 Így például a Linux és UNIX rendszerű kiszolgálókon található összes natívan telepített program listáját is gyűjtheti. Ilyen natívan telepített programok például az **.rpms** a Linux vagy a **.pkgs** a Solaris esetében. Után készlet egy Linux vagy UNIX rendszerű ügyfél elküldte, megtekintheti az összes natívan telepített Linux vagy UNIX program listáját az erőforrás-kezelőben a Configuration Manager konzolon.  

 Az erőforrás-kezelő használatával kapcsolatos információkért lásd: [System Center Configuration Manager a Hardverleltár megjelenítése az erőforrás-kezelő használatával](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

##  <a name="BKMK_UseReportsforLnU"></a> Jelentések használata a Linux és UNIX rendszerű kiszolgálók információinak megtekintéséhez  
 Jelentések a Configuration Manager Linux és UNIX-kiszolgálókból, valamint információkat a Windows-alapú számítógépekről származó információkat tartalmaznak. A Linux és UNIX rendszerek adatainak a jelentésekbe való integrálásához nincs szükség további beállításokra.  

 Például az Operációsrendszer-verziók száma jelentés futtatásakor megjelenik a különböző operációs rendszerek listája és az egyes rendszereket futtató ügyfelek száma. A jelentés a különböző operációs rendszereken futó másik Configuration Manager-ügyfelek által küldött hardverleltáradatokon alapul.  

 Emellett Linux- vagy UNIX-specifikus kiszolgálóadatokat tartalmazó egyéni jelentések is készíthetők. Az **Operating System** (operációs rendszer) hardverleltárosztály **Caption** (felirat) tulajdonsága egy olyan hasznos jellemző, amelynek segítségével azonosíthatja a különböző operációs rendszereket a jelentéskészítési lekérdezésben.  

 A Configuration Manager-jelentésekkel kapcsolatos további információkért lásd: [a System Center Configuration Manager jelentéskészítési](../../../core/servers/manage/reporting.md).  

