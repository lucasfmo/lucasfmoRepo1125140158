---
title: "Gyűjtemények Előfeltételek |} Microsoft Docs"
description: "Gyűjtemények a System Center Configuration Manager használatára vonatkozó Előfeltételek beolvasása."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a53e4cf1-518a-4210-9c16-022c4261d2fe
caps.latest.revision: 7
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 41fc3eb20a7441939eb0dc80bc121c8f3ea322b2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-collections-in-system-center-configuration-manager"></a>A System Center Configuration Managerben gyűjteményekre vonatkozó Előfeltételek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager gyűjtemények csak a terméken belüli függőségekkel tartalmaz.  

## <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  

|Függőség|További információ|  
|----------------|----------------------|  
|Jelentéskészítési szolgáltatási pont|Ahhoz, hogy tudja futtatni a gyűjtemények jelentéseit, telepíteni kell a jelentéskészítési szolgáltatási pont helyrendszerszerepkörét. További információ: [Jelentéskészítés a System Center Configuration Managerben](../../../../core/servers/manage/reporting.md).|  
|A gyűjtemények kezeléséhez előbb meg kell adni bizonyos biztonsági engedélyeket.|A megfelelőségi beállítások kezeléséhez a következő biztonsági engedélyekkel kell rendelkeznie:<br /><br /> -A gyűjtemények létrehozásához és kezeléséhez: **Hozzon létre**, **törlése**, **módosítása**, **mappa módosítása**, **objektum áthelyezése**, **olvasási** és **erőforrás olvasása** a a **gyűjtemény** objektum.<br /><br /> -Gyűjteménybeállítások kezeléséhez: **Gyűjtési beállítás módosításához** a a **gyűjtemény** objektum.<br /><br /> A **Mappa módosítása** engedély az összes gyűjteménymappához szükséges, beleértve a gyökérmappát is.|  

