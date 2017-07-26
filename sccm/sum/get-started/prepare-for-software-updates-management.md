---

title: "Szoftverfrissítések kezelése előkészítése |} Microsoft Docs"
description: "Felkészülés a frissítések kezelésére, végezze el ezeket a feladatokat a megfelelőségvizsgálati adatai megjelennek a System Center Configuration Manager konzol."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 01907900-e28b-4cd7-9479-42906416707b
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 5c34bd1ea108dffda10c30281fb9c97ba38ae1ae
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="prepare-for-software-updates-management"></a>Készítse elő a szoftverfrissítések kezelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt a szoftverfrissítés megfelelőségvizsgálati adatai megjeleníti a System Center Configuration Manager-konzolon, és mielőtt telepíthetné a szoftverfrissítéseket ügyfélszámítógépekre, el kell végeznie az az alábbi szakaszokban található.

## <a name="step-1-install-a-software-update-point"></a>1. lépés: A szoftverfrissítési pont telepítése  
A szoftverfrissítési pont szükséges a központi adminisztrációs hely vagy önálló elsődleges helyet, és az elsődleges helyeken engedélyezi a szoftverhasználat-szoftverfrissítések megfelelőségi vizsgálata, és szeretne szoftvert telepíteni frissítéseit az ügyfelekre. Másodlagos helyeken a szoftverfrissítési pont telepítése nem kötelező. További információkért lásd: [egy szoftverfrissítési pont telepítése](install-a-software-update-point.md)  

## <a name="step-2-synchronize-software-updates"></a>2. lépés: Szoftverfrissítések szinkronizálása
A szoftverfrissítések szinkronizálását az Ön által konfigurált feltételeknek megfelelő szoftverfrissítési metaadatok lekérését jelenti. Szoftverfrissítések nem jelennek meg a Configuration Manager konzolon, amíg a szoftverfrissítések szinkronizálása. További információkért lásd: [szinkronizálhatók a szoftverfrissítések](synchronize-software-updates.md).   

## <a name="step-3-configure-classifications-and-products-to-synchronize"></a>3. lépés: Besorolások és termékek szinkronizálása konfigurálása
Ezt a beállítást a központi felügyeleti helyen vagy önálló elsődleges helyen hajtsa végre. Szoftverfrissítések első szinkronizálása után a Configuration Manager beolvassa a besorolások és termékek frissített listáját. Most választhat a szoftverfrissítési pont összetevő tulajdonságai új beállításokat. Az új besorolások és termékek konfigurálása után ismételje meg a 2. Indítsa el az új feltétel szoftverfrissítési metaadatok lekérése céljából, a szoftverfrissítések szinkronizálását. További információkért lásd: [besorolások és termékek szinkronizálása konfigurálása](configure-classifications-and-products.md).

## <a name="step-4-manage-settings-for-software-updates"></a>4. lépés: A szoftverfrissítések beállításainak kezelése
Miután szinkronizálja a szoftverfrissítéseket, ellenőrizze a Configuration Manager-ügyfél beállításainak, a Csoportházirend konfigurálásának és a szoftverfrissítések beállításainak szoftverfrissítések központi telepítése előtt. További információkért lásd: [szoftverfrissítések beállításainak kezelése](manage-settings-for-software-updates.md).

