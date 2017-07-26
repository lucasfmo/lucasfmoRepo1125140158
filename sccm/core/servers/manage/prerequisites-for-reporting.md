---
title: "A jelentéskészítés előfeltételei |} Microsoft Docs"
description: "Ismerje meg, amely hatással lehet az Ön miként használja a jelentéskészítés a System Center Configuration Manager különböző függőségek."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
caps.latest.revision: 5
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 70034213442f4c3d5a28ab65c2ceb51aa64320ad
ms.openlocfilehash: 2e624eb2ea061a4eb7d92365410fada335640224
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-reporting-in-system-center-configuration-manager"></a>A System Center Configuration Managerben a jelentéskészítés előfeltételei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager jelentéskészítési jelentéskészítésnek külső és a termékben lévő függőségei is.  

## <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  
 A következő táblázat felsorolja a jelentéskészítés külső függőségeit.  

|Előfeltétel|További információ|  
|------------------|----------------------|  
|SQL Server Reporting Services|Használhatja a jelentéskészítés a Configuration Managerben, akkor telepítenie és konfigurálnia kell az SQL Server Reporting Services.<br /><br /> A Reporting Servicesnek az adott környezetben való megtervezéséről és központi telepítéséről az SQL Server 2008 online könyvek [Reporting Services](http://go.microsoft.com/fwlink/p/?LinkId=212032) része tartalmaz további információt.|  
|A helyrendszerszerepkörök függőségei a jelentéskészítési szolgáltatási pontot futtató számítógépekre vonatkozóan.|[A System Center Configuration Manager támogatott konfigurációk](../../../core/plan-design/configs/supported-configurations.md)|  

## <a name="dependencies-internal-to-configuration-manager"></a>A Configuration Manageren belüli függőségek  
 A következő táblázat felsorolja a jelentéskészítés a Configuration Managerben függőségeit.  

|Előfeltétel|További információ|  
|------------------|----------------------|  
|Jelentéskészítési szolgáltatási pont|A jelentéskészítési szolgáltatási pont helyrendszer-szerepkör be kell állítani a Configuration Manager jelentéskészítési használata előtt. Telepítésének és konfigurálásának módjáról további információ a jelentéskészítési szolgáltatási pontok telepítéséről [konfigurálása a System Center Configuration Manager jelentéskészítési](../../../core/servers/manage/configuring-reporting.md).|  

## <a name="supported-sql-server-versions-for-the-reporting-services-point"></a>Támogatott SQL Server-verziók a jelentéskészítési szolgáltatási ponton  
 A Reporting Services-adatbázis egy 64 bites SQL Server-telepítés alapértelmezett, illetve elnevezett példányára egyaránt telepíthető. Az SQL Server-példány a helyrendszer-kiszolgálóval közösen, illetve távoli számítógépen is elhelyezhető.  

 Az alábbi táblázat felsorolja a jelentéskészítési szolgáltatási pont által támogatott SQL Server-verziókat.  

|SQL Server verziója|Jelentéskészítési szolgáltatási pont|  
|------------------------|------------------------------|  
|SP2 szervizcsomaggal rendelkező SQL Server legalább 9-es összesítő frissítéssel<br /><br /> -Standard<br />-A vállalati<br />– Datacenter|Igen|  
|SP3 szervizcsomaggal rendelkező SQL Server 2008 legalább 4-es összesítő frissítéssel<br /><br /> -Standard<br />-A vállalati<br />– Datacenter|Igen|  
|SP1 szervizcsomaggal rendelkező SQL Server 2008 R2 legalább 6-os összesítő frissítéssel<br /><br /> -Standard<br />-A vállalati<br />– Datacenter|Igen|  
|SP2 szervizcsomaggal rendelkező SQL Server 2008 R2<br /><br /> -Standard<br />-A vállalati<br />– Datacenter|Igen|  
|SP1 szervizcsomaggal rendelkező SQL Server Express 2008 R2 legalább 4-es összesítő frissítéssel|Nem támogatott|  
|SP2 szervizcsomaggal rendelkező SQL Server Express 2008 R2|Nem támogatott|  
|SQL Server 2012, legalább 2-es összesítő frissítéssel<br /><br /> -Standard<br />-A vállalati|Igen|  
|SP1 szervizcsomaggal rendelkező SQL Server 2012, legalacsonyabb szintű összesítő frissítés nélkül<br /><br /> -Standard<br />-A vállalati|Igen|  
|SQL Server 2014<br /><br /> -Standard<br />-A vállalati|Igen|
|SQL Server 2016<br /><br /> -Standard<br />-A vállalati|Igen|
|SQL Server 2016 SP1<br /><br /> -Standard<br />-A vállalati|Igen|
## <a name="next-steps"></a>További lépések
[Műveletek és karbantartás a jelentéskészítéshez](operations-and-maintenance-for-reporting.md)

