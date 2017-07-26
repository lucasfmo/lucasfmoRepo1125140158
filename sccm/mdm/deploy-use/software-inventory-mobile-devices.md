---
title: "A Microsoft Intune-nal beléptetett mobileszközökhöz szoftverleltár |} Microsoft Docs"
description: "Szoftverleltár a Microsoft Intune-nal beléptetett mobileszközök esetében."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0eae17a-60a8-4132-91af-0b10ad338c92
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 2ed79d02535768de136947e4a5b63ad186d9a3cd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="software-inventory-for-mobile-devices-enrolled-with-microsoft-intune"></a>Szoftverleltár a Microsoft Intune-ban regisztrált mobileszközökön

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Begyűjtheti a mobileszközökön telepített alkalmazások készlet. A leltárba bevont alkalmazások köre attól függően eltér, hogy munkahelyi vagy saját eszközről van-e szó. Személyes eszközök az csak leltárba bevont alkalmazások nem a Microsoft Intune által kezelt alkalmazások.  

> [!NOTE]  
>  A mobileszközökön telepített alkalmazások leltárát a rendszer részeként gyűjti be a [Hardverleltár](mobile-device-hardware-inventory-hybrid.md) folyamat.  

 Az alábbiakban a személyes tulajdonú és vállalati tulajdonú eszközök leltárba bevont alkalmazások.  

|Platform|Személyes tulajdonú eszközök esetében|Vállalati tulajdonú eszközök esetében|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (nélkül a Configuration Manager-ügyfél)|Csak felügyelt alkalmazások|Csak felügyelt alkalmazások|
|Windows 8.1 (nélkül a Configuration Manager-ügyfél)|Csak felügyelt alkalmazások|Csak felügyelt alkalmazások|  
|Windows Phone 8|Csak felügyelt alkalmazások|Csak felügyelt alkalmazások|  
|Windows RT|Csak felügyelt alkalmazások|Csak felügyelt alkalmazások|  
|iOS|Csak felügyelt alkalmazások|Az összes, az eszközön telepített alkalmazás|  
|Android|Csak felügyelt alkalmazások|Az összes, az eszközön telepített alkalmazás|  

Lásd: [szoftverleltár bemutatása](../../core/clients/manage/inventory/introduction-to-software-inventory.md) és [szoftverleltár konfigurálása ](../../core/clients/manage/inventory/configure-software-inventory.md) részletes információk szoftver-nyilvántartási fájl kapcsolatos információk összegyűjtéséhez az ügyféleszközökön.

