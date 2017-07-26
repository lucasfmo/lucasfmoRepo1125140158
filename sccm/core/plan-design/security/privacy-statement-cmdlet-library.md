---
title: "A System Center Configuration Manager adatvédelmi nyilatkozata – Configuration Manager cmdletlLibrary |} Microsoft Docs"
description: "További tudnivalók arról, hogy a Microsoft hogyan gyűjti és használja a System Center Configuration Manager cmdlet library kapcsolódó adatokat."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bec00fb4-1ac0-4e49-b330-0871b3722459
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3d6799ad46e0fe69333aba0662f18c9153c17bda
ms.openlocfilehash: 3936075555cc0bb370ea6e42c7e720b864d565f7
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="system-center-configuration-manager-privacy-statement---configuration-manager-cmdlet-library"></a>A System Center Configuration Manager adatvédelmi nyilatkozata – Configuration Manager cmdlet library

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A jelen adatvédelmi nyilatkozat vonatkozik a System Center Configuration Manager Cmdlet Library szolgáltatásaira is.  

## <a name="usage-data"></a>Használati adatok  
 **A szolgáltatás funkciója:**   
A System Center Configuration Manager cmdlet library lehetővé teszi a Configuration Manager hierarchiáinak kezelését Windows PowerShell-parancsmagok és parancsfájlok segítségével. A cmdlet library használatáról a parancsmagokat a könyvtárban a trendek és használati minták azonosításához adatokat gyűjt. A cmdlet library is gyűjti a típusát és a parancsmagok használatakor előforduló hibák számát.  

 **Összegyűjtött, feldolgozott vagy továbbított információk:**   
Az összegyűjtött használati adatok indítása, leállítása és leállítja a parancsmagok, elavult parancsmagok és tevékenységi metrikák műveleteihez Systems Management Server (SMS) szolgáltató, amely kapcsolódik a parancsmagok futtatása magában foglalja. Ezek az információk nem alkalmasak személyazonosításra.  Összegyűjtött hibainformációk adja vissza az hibákról és a hiba részletei tartalmaz. Egyes hibák részletes jelentései véletlenül tartalmazhatnak egyéni azonosítókat, például a számítógéphez csatlakoztatott eszközök sorozatszámát. A cmdlet library szűri, és távolítsa el a Microsofthoz történő átvitelhez előtt egyéni azonosítókat a hibajelentésekben található adatok anonymizes.  

 **Az információk felhasználása:**   
Ez az információ minőségének, biztonsági és a termékek és szolgáltatások kínálunk integritásának javítására használjuk.  

 **Döntési és szabályozási lehetőségek:**   
A használati adatok funkció alapértelmezés szerint engedélyezve van. A System Center Configuration Manager cmdlet library szabályozza ezeket a funkciókat két beállításkulcsot tartalmaz.  

 A teljes elutasításhoz meg kell adnia az alábbi két beállításkulcs-értéket a Windows esemény-nyomkövetés (ETW) szolgáltatóinak mindegyikéhez:  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0 (használati adatok elutasítása a meghajtószolgáltató esetén)  

-   HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0 (a parancsmagokkal kapcsolatos használati adatok küldésének kikapcsolása)  

 A használati adatok beállításainak módosítása arra a számítógépre vonatkozik, amelyen azok létrejöttek.  

 További (gyűjtemény) használati adatok konfigurálásáról lásd: a [System Center Configuration Manager Cmdlet Library dokumentációjában](https://technet.microsoft.com/en-us/library/dn958404.aspx).   

