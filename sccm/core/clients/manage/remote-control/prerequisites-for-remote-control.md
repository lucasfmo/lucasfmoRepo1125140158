---
title: "A távvezérlés előfeltételei |} Microsoft Docs"
description: "A távvezérlés előfeltételei a System Center Configuration Managerben beolvasása."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: e08bca886dfc0730ab45ab899754394ae61335e3
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>A System Center Configuration Manager Távvezérlés előfeltételei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager Távvezérlés vannak külső függőségei és a függőségek a termékben.  

## <a name="dependencies-external-to-configuration-manager"></a>A Configuration Manager alkalmazáson kívüli függőségek  

|Függőség|További információ|  
|----------------|----------------------|  
|A számítógép videokártya-illesztőprogramja|A távvezérlés optimális teljesítményének biztosítása érdekében győződjön meg arról, hogy az ügyfélszámítógépeken a legfrissebb videoillesztő van telepítve.|  

 A Windows Embedded, Windows Embedded for Point of Service (POS) és Windows Fundamentals for Legacy PCs rendszerű eszközök nem támogatják a távvezérlés megjelenítőjét, a távvezérlési ügyfelet viszont igen.  

 Configuration Manager távvezérlése Systems Management Server 2003 vagy a Configuration Manager 2007 rendszerű ügyfélszámítógépek távoli felügyeletéhez nem használható.  

> [!NOTE]  
>  A távvezérléshez egyetlen Windows-szolgáltatás sem szükséges külső függőségként.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>A távvezérlés megjelenítőjéhez támogatott operációs rendszerek  
 A következő táblázat a távvezérlés megjelenítőjéhez támogatott operációs rendszerekről nyújt információt. Ügyfelek támogatott operációs rendszerekkel kapcsolatos információkért lásd: [által támogatott konfigurációk a System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md).  

|Operációs rendszer|Megjelenítő támogatása|További információ|  
|----------------------|--------------------|----------------------|  
|Windows XP (32 bites)|Igen|A távvezérlés megjelenítőjének ezen operációs rendszer futtatásához először le kell töltenie és telepítse a [távoli asztali kapcsolat (RDC) ügyfélprogramjának frissítését (KB969084) 7.0](https://www.microsoft.com/en-us/download/details.aspx?id=12767) a Microsoft Download Center webhelyről.|  
|Windows XP (64 bites)|Nem|Nem áll rendelkezésre további információ.|  
|Windows Vista (32 bites)|Igen|A távvezérlés megjelenítőjének ezen operációs rendszer futtatásához először le kell töltenie és telepítse a [távoli asztali kapcsolat (RDC) ügyfélprogramjának frissítését (KB969084) 7.0](https://www.microsoft.com/en-us/download/details.aspx?id=12767) a Microsoft Download Center webhelyről.|  
|Windows Vista (64 bites)|Igen|A távvezérlés megjelenítőjének ezen operációs rendszer futtatásához először le kell töltenie és telepítse a [távoli asztali kapcsolat (RDC) ügyfélprogramjának frissítését (KB969084) 7.0](https://www.microsoft.com/en-us/download/details.aspx?id=12767) a Microsoft Download Center webhelyről.|  
|Windows 7 (32 bites)|Igen|Nem áll rendelkezésre további információ.|  
|Windows 7 (64 bites)|Igen|Nem áll rendelkezésre további információ.|  
|Windows Server 2003 (32 bites)|Nem|Nem áll rendelkezésre további információ.|  
|Windows Server 2003 (64 bites)|Nem|Nem áll rendelkezésre további információ.|  
|Windows Server 2008 (32 bites)|Nem|Nem áll rendelkezésre további információ.|  
|Windows Server 2008 (64 bites)|Nem|Nem áll rendelkezésre további információ.|  
|Windows Server 2008 R2 (64 bites)|Igen|Nem áll rendelkezésre további információ.|  

## <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  

|Függőség|További információ|  
|----------------|----------------------|  
|A távvezérlést engedélyezni kell az ügyfelek számára|Alapértelmezés szerint a távvezérlés nincs engedélyezve a Configuration Manager telepítésekor. Engedélyezze és konfigurálja a távvezérlés kapcsolatos információkért lásd: [a Távvezérlés konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/remote-control/configuring-remote-control.md).|  
|Jelentéskészítési szolgáltatási pont|Ahhoz, hogy tudja futtatni a távvezérlésre vonatkozó jelentéseket, telepíteni kell a jelentéskészítési szolgáltatási pont helyrendszerszerepkörét. További információ: [Jelentéskészítés a System Center Configuration Managerben](../../../../core/servers/manage/reporting.md).|  
|Biztonsági engedélyek a távvezérlés kezeléséhez|Gyűjtemény-erőforrások eléréséhez, és a Configuration Manager konzolról egy távvezérlési munkamenet indítása: **AMT szabályozása**, **olvasási**, **erőforrás olvasása**, és **távvezérlési** engedély a **gyűjtemény** objektum.<br /><br /> A **Távolieszköz-kezelő** biztonsági szerepkör tartalmazza azokat az engedélyeket, a Configuration Manager Távvezérlés kezeléséhez szükségesek.<br /><br /> További információkért lásd: [szerepkör alapú felügyelet a System Center Configuration Manager konfigurálása](../../../../core/servers/deploy/configure/configure-role-based-administration.md).<br /><br /> Emellett azokat a felhasználókat, akiknek engedélyt kíván adni a távvezérlés használatára, hozzá kell adnia a távvezérlés és távsegítség engedélyezett megtekintőinek listájához a **Táveszközök** ügyfélbeállításaiak **A távvezérlés és a távsegítség feljogosított megjelenítői** lehetőségével.|  

