---
title: "Az energiagazdálkodás előfeltételei |} Microsoft Docs"
description: "Az energiagazdálkodás előfeltételei a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c062f13-3c1f-4621-9cae-de0e322aa03f
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: 711ef491899846b86bfed0355ac7fd0f9d509c4f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-power-management-in-system-center-configuration-manager"></a>Előfeltételek az energiagazdálkodáshoz a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben az energiagazdálkodás jelentéskészítésnek külső és a termékben lévő függőségei is.  

## <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  
 Az alábbi táblázat felsorolja a Configuration Manager külső függőségeit használatára energiagazdálkodás vonatkozó.  

|Függőség|További információ|  
|----------------|----------------------|  
|Az ügyfélszámítógépeknek támogatnia kell a szükséges energiaállapotokat|Az energiagazdálkodás összes funkciójának használatához az ügyfélszámítógépeknek támogatniuk kell az alvó állapot, a hibernálás, az alvó állapotból való felébresztés és a hibernált állapotból való felébresztés műveleteit. Az **Energiaellátási lehetőségek** jelentéssel határozhatja meg, hogy a számítógépek támogatják-e ezeket a műveleteket. További információkért lásd: [energiaellátási lehetőségek jelentés](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Capabilites) témakör [figyelés és tervezés a System Center Configuration Managerben az energiagazdálkodás hogyan](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).|  

## <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  
 A következő táblázat a függőségeket a Configuration Manager használatára energiagazdálkodás vonatkozó.  

|Függőség|További információ|  
|----------------|----------------------|  
|Az energiagazdálkodást az energiasémák létrehozása előtt kell engedélyezni.|Engedélyezze és konfigurálja az energiagazdálkodás kapcsolatos információkért lásd: [az energiagazdálkodás konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/power/configuring-power-management.md).|  
|Jelentéskészítési szolgáltatási pont|Az energiagazdálkodási jelentésék megtekintéséhez konfigurálnia kell egy jelentéskészítési szolgáltatási pontot. További információ: [Jelentéskészítés a System Center Configuration Managerben](../../../../core/servers/manage/reporting.md).|  

