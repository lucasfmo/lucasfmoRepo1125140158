---
title: "Feladatütemezési lépéseket BIOS kezeléséhez UEFI alakításához |} A Configuration Manager"
description: "Ismerje meg, hogyan szabhatja testre egy operációs rendszer központi telepítésének feladatütemezése FAT32 partíció UEFI való előkészítéséhez."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: 528ce515c86c4e778532290026a90a46476c4576
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Feladatütemezési lépések UEFI alakításához BIOS kezelése
Windows 10 UEFI-kompatibilis eszközök igénylő számos új biztonsági szolgáltatásokat biztosítja. Lehetséges, hogy a modern Windows rendszerű számítógépek, amelyek támogatják az UEFI, de a hagyományos BIOS-t használ. Egy eszköz konvertálása UEFI megköveteli, hogy lépjen a minden számítógéphez, a merevlemez újraparticionálása, és megfelelően újrakonfigurálja a belső vezérlőprogram. Feladatütemezések a Configuration Manager használatával, a merevlemez-meghajtó előkészítése BIOS UEFI átalakítás, BIOS átalakítása UEFI a helybeni verziófrissítés részeként és UEFI információgyűjtés Hardverleltár részeként.

## <a name="hardware-inventory-collects-uefi-information"></a>Hardverleltár UEFI adatokat gyűjt.
1702 verziójától kezdve egy új Hardverleltár-osztály (**SMS_Firmware**) és a tulajdonság (**UEFI**) elérhető segítségével meghatározhatja, hogy a számítógép UEFI üzemmódban indul. Ha a számítógép UEFI módban indul el a **UEFI** tulajdonsága **igaz**. Ez a Hardverleltár alapértelmezés szerint engedélyezve van. Hardverleltár kapcsolatos további információkért lásd: [konfigurálása a Hardverleltár](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="create-a-custom-task-sequence-to-prepare-the-hard-drive-for-bios-to-uefi-conversion"></a>Hozzon létre egy egyéni feladatütemezést BIOS UEFI alakításához a merevlemez-meghajtó előkészítése
A Configuration Manager verziója 1610 kezdődően most testre egy operációs rendszer központi telepítésének feladatütemezése TSUEFIDrive, új változó, hogy a **számítógép újraindítása** lépés való áttérés UEFI a merevlemez-meghajtón FAT32 partíció készítse elő. A következő eljárás azt mutatja, hogyan hozhat létre feladatütemezési lépések a merevlemez-meghajtó előkészítése a BIOS UEFI alakításához.

### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>A FAT32 partíció előkészítése UEFI átalakítása:
Egy meglévő feladatütemezés egy operációs rendszer telepítéséhez a ehhez a BIOS UEFI alakításához lépéseket egy új csoportot adja hozzá.

1. Hozzon létre egy új feladatütemezési csoport, a lépéseket a fájlok és beállítások rögzítése után, és a lépéseket az operációs rendszer telepítése előtt. Hozzon létre például egy csoport után a **rögzítése fájlok és beállítások** nevű csoport **BIOS-UEFI**.
2. Az a **beállítások** lap az új csoport hozzáadása egy új feladatütemezési változó feltételként ahol **_SMSTSBootUEFI** van **nem egyenlő** való **igaz**. Ez megakadályozza, hogy a csoport lépéseit futtatását, ha a számítógép már UEFI módban van.

  ![BIOS UEFI-csoporthoz](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. Az új csoporthoz, adja hozzá a **számítógép újraindítása** feladatütemezési lépést. A **adja meg, mi legyen futtatva az újraindítás után**, jelölje be **a feladatütemezéshez hozzárendelt rendszerindító lemezkép kijelölt** a számítógép indítása a Windows PE környezetben.  
4. Az a **beállítások** lapon maradva adja hozzá a feladatütemezési változó feltételként ahol **_SMSTSInWinPE értéke hamis**. Ez megakadályozza, hogy ez a lépés futtatása, ha a számítógép már a Windows PE környezetben.

  ![Indítsa újra a számítógépet. lépés](../../core/get-started/media/restart-in-windows-pe.png)
5. Adjon hozzá egy lépést, az OEM eszköz, amelyek a rendszer a belső vezérlőprogram BIOS UEFI indításához. Ez általában lesz egy **parancssor futtatása** feladatütemezési lépés a parancssorral, az OEM eszköz elindításához.
6. A lemez formázása és particionálása feladatütemezési lépés a merevlemez formázása és particionálása hozzáadása. A lépés tegye a következőket:
  1. Hozzon létre a FAT32-partíció, konvertálja UEFI az operációs rendszer telepítése előtt. Válasszon **GPT** a **lemez típusa**.
    ![Lemez lépés formázása és particionálása](../media/format-and-partition-disk.png)
  2. Ugrás a FAT32 partíció tulajdonságainak. Adja meg **TSUEFIDrive** a a **változó** mező. Amikor a feladatütemezés azt észleli, hogy ezt a változót, akkor készítse elő az UEFI-átmenet a számítógép újraindítása előtt.
    ![Partíció tulajdonságai](../../core/get-started/media/partition-properties.png)
  3. Hozzon létre egy NTFS-partíciót a Feladatütemező motor használó menteni az állapotot és a naplófájlok tárolására szolgáló.
7. Adja hozzá a **számítógép újraindítása** feladatütemezési lépést. A **adja meg, mi legyen futtatva az újraindítás után**, jelölje be **a feladatütemezéshez hozzárendelt rendszerindító lemezkép kijelölt** a számítógép indítása a Windows PE környezetben.  

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>A BIOS átalakítása UEFI helybeni frissítés során
Windows 10 Creators frissítés egy egyszerű átalakítás eszközt, amely automatizálja az UEFI-kompatibilis hardveres a merevlemez újraparticionálása folyamatát, és az átalakítás eszközzel integrálódik a Windows 7, Windows 10 helyi frissítési folyamat vezet be. Ha az eszköz együttesen az operációs rendszer frissítési feladatütemezés és az OEM-eszközt, amely a belső vezérlőprogram a BIOS UEFI alakítja, átválthat a számítógépek BIOS UEFI helyben frissítés a Windows 10 Creators frissítés során.

**Követelmények**:
- Windows 10 Creators frissítése
- Számítógépek, amelyek támogatják az UEFI-
- OEM eszköz, amely a számítógép belső vezérlőprogramja a BIOS UEFI alakítja

### <a name="to-convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>BIOS átalakítása UEFI helybeni frissítés során
1. Hozzon létre egy operációsrendszer-frissítési feladatütemezést, amely elvégzi a Windows 10 Creators Update helybeni frissítés.
2. Szerkessze a feladatütemezést. Az a **utófeldolgozás csoportjához**, az alábbi feladatütemezési lépések hozzáadása:
   1. Az általános, vegye fel a **parancssor futtatása** lépés. A parancssor felveszi az a MBR2GPT eszköz adott coverts MBR-lemezek lemez módosítása adatok vagy törlése a lemezről nélkül. A parancssorban írja be a következőt:  **MBR2GPT/Convert /disk:0 /AllowFullOS**. Választhatja azt is, a MBR2GPT futtatásához. A következő EXE-eszköz a teljes operációs rendszer helyett Windows PE környezetben. Ehhez adja hozzá a lépés újraindítja a számítógépet a lépés futtatásához a MBR2GPT WinPE környezetet. A következő EXE eszköz és a /AllowFullOS beállítás eltávolítása a parancssorból. Az eszköz és a rendelkezésre álló lehetőségeket, lásd: [MBR2GPT. EXE](https://technet.microsoft.com/itpro/windows/deploy/mbr-to-gpt).
   2. Adjon hozzá egy lépést, az OEM eszköz, amelyek a rendszer a belső vezérlőprogram BIOS UEFI indításához. Ez általában lesz egy parancssor futtatása feladatütemezési lépés a parancssorral, az OEM eszköz elindításához.
   3. Az általános, vegye fel a **számítógép újraindítása** lépés. Adja meg mi legyen futtatva az újraindítás után, jelölje be **a jelenleg telepített alapértelmezett operációs rendszer**.
3. A feladatütemezés központi telepítése.

