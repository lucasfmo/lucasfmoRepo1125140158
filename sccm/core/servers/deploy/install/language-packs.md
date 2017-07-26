---
title: Nyelvi csomagok |} Microsoft Docs
description: "További tudnivalók a nyelvi támogatás a System Center Configuration Managerben elérhető."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: e7075eb675353be130fdcc867d9e4dd1009dab35
ms.openlocfilehash: 47da3c531289ddf13d357bde8bbda85d79ed2803
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="language-packs-in-system-center-configuration-manager"></a>Nyelvi csomagok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ez a témakör a System Center Configuration Manager nyelvi támogatására vonatkozó technikai részleteket.  

## <a name="BKMK_SupLanguagePacks"></a>Támogatott operációs rendszer nyelve  
 Telepítheti a megjelenítési nyelvek támogatását a következő táblázatok telepítésével **kiszolgálói nyelvi csomagokat** vagy **ügyféloldali nyelvi csomagok** egy központi adminisztrációs helyen és az elsődleges helyeken. A kiszolgáló és az ügyfél támogatásához az elérhető nyelvi csomagok fájljait egy hely a helyrendszer-telepítési folyamat során olyan nyelveket választ ki.

 Nyelvi csomagok fájljait lesznek letöltve, amikor az Előfeltételek és újraterjeszthető fájlok letöltésének részeként futtatja a telepítőt. Is használhat, [a telepítő letöltési segédprogramja](setup-downloader.md) ezek a fájlok letöltését, mielőtt elindítaná a telepítőt.   

 Az alábbi táblázat segítségével egy nyelv, amely támogatja a kiszolgálók és ügyfélszámítógépek kívánt területibeállítás-azonosító van leképezve. További információ a területibeállítás-azonosítókról: [Microsoft által területibeállítás-azonosítók](http://go.microsoft.com/fwlink/p/?LinkId=252609).  

### <a name="server-languages"></a>Kiszolgálónyelvek  

|Kiszolgáló nyelve|Területibeállítás-azonosító (LCID)|Három betűs kód|  
|---------------------|------------------------|-----------------------|  
|Angol (alapértelmezett)|0409|ENU|  
|kínai (hagyományos, Hongkong, KKT)|0c04|ZHH|  
|kínai (egyszerűsített)|0804|CHS|  
|kínai (hagyományos, Tajvan)|0404|CHT|  
|Cseh|0405|CSY|  
|Holland - Hollandia|0413|NLD|  
|Francia|040c|FRA|  
|Német|0407|DEU|  
|Magyar|040e|HUN|  
|Olasz - Olaszország|0410|ITA|  
|Japán|0411|JPN|  
|koreai|0412|KOR|  
|Lengyel|0415|PLK|  
|Portugál - Brazília|0416|PTB|  
|Portugál - Portugália|0816|PTG|  
|Orosz|0419|RUS|  
|Spanyol – Spanyolország|0c0a|ESN|  
|Svéd|041d|SVE|  
|Török|041f|TRK|  

### <a name="client-languages"></a>Ügyfélnyelvek  

|Ügyfélrendszer nyelve|Területibeállítás-azonosító (LCID)|Három betűs kód|  
|---------------------|------------------------|-----------------------|  
|Angol (alapértelmezett)|0409|ENG|  
|kínai (hagyományos, Hongkong, KKT)|0c04|ZHH|  
|Egyszerűsített kínai|0804|CHS|  
|kínai (hagyományos, Tajvan)|0404|CHT|  
|Cseh|0405|CSY|  
|Dán|0406|DAN|  
|Holland - Hollandia|0413|NLD|  
|Finn|040b|FIN|  
|Francia|040c|FRA|  
|Német|0407|DEU|  
|Görög|0408|ELL|  
|Magyar|040e|HUN|  
|Olasz - Olaszország|0410|ITA|  
|Japán|0411|JPN|  
|koreai|0412|KOR|  
|Norvég|0414|NOR|  
|Lengyel|0415|PLK|  
|Portugál (brazíliai)|0416|PTB|  
|portugál (Portugália)|0816|PTG|  
|Orosz|0419|RUS|  
|Spanyol – Spanyolország|0c0a|ESN|  
|Svéd|041d|SVE|  
|Török|041f|TRK|  

### <a name="mobile-device-client-languages"></a>Mobileszközi nyelvek  
 Amikor mobileszköz nyelvek támogatását, minden támogatott mobileszközügyfelek nyelveinek érhetők el. A mobileszközök támogatásához nem választhat külön nyelvi csomagot.  

### <a name="identify-installed-language-packs"></a>Telepített nyelvi csomagok azonosítása  
A Configuration Manager-ügyfelet futtató számítógépen telepített nyelvi csomagok azonosításához keresse meg a területibeállítás-Azonosítójáról (LCID) a számítógép beállításjegyzékében a telepített nyelvi csomagok. Ez az információ érhető el:

 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs**  

Ez ez információ begyűjthető a Hardverleltár használatával, és majd kialakítható olyan egyéni jelentés, a nyelvi a részletek megtekintéséhez. További információ az egyéni Hardverleltár összeállításának: [Hardverleltár konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/inventory/configure-hardware-inventory.md). Jelentések létrehozásával kapcsolatos további információkért lásd: a [kezelése a Configuration Manager jelentések](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md#BKMK_ManageReports) szakasz a [műveletek és karbantartás a System Center Configuration Manager jelentéskészítési](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md) témakör.  

