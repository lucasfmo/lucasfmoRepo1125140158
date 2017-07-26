---
title: "Ismeretlen számítógépek központi telepítésének előkészítése |} Microsoft Docs"
description: "Ismerje meg az operációs rendszerek központi telepítése a System Center Configuration Manager-környezetben a Configuration Manager által nem kezelt számítógépekre."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e447e34-0943-49ed-b6ba-3efebf3566c1
caps.latest.revision: 10
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 445e76950f0605da917f3d0e7e71557d969e3c2d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-for-unknown-computer-deployments-in-system-center-configuration-manager"></a>Felkészülés az ismeretlen számítógépekre való központi telepítésre a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Olvassa el a témakör az operációs rendszerek központi telepítése a System Center Configuration Manager-környezetben található ismeretlen számítógépeken. Ismeretlen számítógépen olyan számítógép, a Configuration Manager által nem kezelt. Ez azt jelenti, hogy nincs-e ezekhez a számítógépekhez a Configuration Manager-adatbázis rekord. Az ismeretlen számítógépek a következők:  

-   Egy számítógép, amelyen nincs telepítve a Configuration Manager-ügyfél  

-   Olyan számítógép, amely nincs importálva a Configuration Managerbe  

-   Egy számítógép, amelyet a rendszer nem észlelt a Configuration Manager által  

 A következő központi telepítési módszerekkel telepíthet operációs rendszereket ismeretlen számítógépekre:  

-   [A Windows központi telepítése a hálózaton keresztül PXE használatával](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)  

-   [Rendszerindító adathordozó használatával az operációs rendszerek központi telepítéséhez](../deploy-use/create-bootable-media.md)  

-   [A manuálisan előkészített adathordozó használatával az operációs rendszerek központi telepítéséhez](../deploy-use/create-prestaged-media.md)  

## <a name="unknown-computer-deployment-workflow"></a>Az ismeretlen számítógépekre való központi telepítés munkafolyamata  
 A következő alapvető munkafolyamattal telepíthető egy operációs rendszer egy ismeretlen számítógépre:  

-   Válasszon ki egy, a központi telepítéshez használandó ismeretlenszámítógép-objektumot. Az operációs rendszer központi telepítését elvégezheti egy, a **Minden ismeretlen számítógép** gyűjteményben található ismeretlenszámítógép-objektumon, vagy felveheti a **Minden ismeretlen számítógép** gyűjteményben szereplő objektumokat egy másik gyűjteménybe. A Configuration Manager biztosít két ismeretlenszámítógép-objektumon a **minden ismeretlen számítógép** gyűjtemény. Az egyik objektum x86 számítógépekhez, a másik objektum x64 számítógépekhez használható.  

    > [!NOTE]  
    >  Az **x86 ismeretlen számítógép** objektum csak x86-képes számítógépekhez használható. Az **x64 ismeretlen számítógép** objektum x86- és x64-képes számítógépekhez használható. Más megfogalmazásban: ezek az objektumok a célszámítógép architektúráját jellemzik. Nem a célszámítógépen telepíteni kívánt operációs rendszert határozzák meg.  

-   Az ismeretlen számítógépekre való központi telepítéshez konfiguráljon egy PXE-képes terjesztési pontot vagy hozzon létre adathordozót.  

-   Végezze el az operációs rendszer telepítéséhez készült feladatütemezés központi telepítését.  

## <a name="unknown-computer-installation-process"></a>Ismeretlen számítógép telepítésének folyamata  
 A számítógép első indításakor a PXE Környezetből vagy adathordozóról, a Configuration Manager ellenőrzi, hogy a számítógéphez tartozó rekord létezik-e a Configuration Manager adatbázisába. Ha van rekord, a Configuration Manager ellenőrzi, hogy vannak-e megadva bármilyen feladatütemezés a bejegyzéshez. Ha nincs rekord, a Configuration Manager ellenőrzi, hogy vannak-e megadva bármilyen feladatütemezés ismeretlenszámítógép-objektumot a. Mindkét esetben a Configuration Manager hajtja végre a következő műveletek egyikét:  

-   Ha van elérhető feladatütemezés, a Configuration Manager rákérdez a felhasználónál a feladatütemezés futtatása.  

-   Ha van előírt feladatütemezés, a Configuration Manager automatikusan futtatja a feladatütemezést.  

-   Ha a feladatütemezés a rekordhoz nincs telepítve, a Configuration Manager hibaüzenetet ad, hogy van-e a célszámítógépre vonatkozóan nincs beállított feladatütemezés.  

 Ismeretlen számítógép indításakor a Configuration Manager a számítógép felismeri az ismeretlen számítógépek hanem nem kiépített számítógép. Ez azt jelenti, hogy a számítógép most már fogadni tudja a feladatütemezéseket, amelyek az ismeretlen számítógép objektumához be vannak állítva. A telepített feladatütemezés ezt követően telepít egy operációsrendszer-lemezkép tartalmaznia kell a Configuration Manager-ügyfél.  

 A Configuration Manager-ügyfél telepítése után a számítógéphez tartozó rekord jön létre, és a számítógép belekerül a megfelelő Configuration Manager-gyűjteményhez. Ha a számítógépnek az operációs rendszer lemezképét vagy a Configuration Manager-ügyfél telepítése nem sikerül, a számítógéphez egy "Ismeretlen" rekord jön létre, és a számítógép megjelenik a **minden rendszer** gyűjtemény.  

> [!NOTE]  
>  A feladatütemezés az operációs rendszer lemezképének telepítése alatt gyűjteményváltozókat be tud olvasni, de erről a számítógépről nem tudja elérni a számítógép változóit.  

##  <a name="BKMK_EnablingUnknown"></a> Ismeretlen számítógép támogatásának engedélyezése  
 A következő információk alapján engedélyezhető az ismeretlen számítógépek támogatása a PXE környezettel, rendszerindító adathordozóval vagy manuálisan előkészített adathordozóval végzett központi telepítések esetén.  

-   **PXE**  

     A **PXE** lapon jelölje be az **Ismeretlen számítógépek támogatásának engedélyezése** jelölőnégyzetet egy olyan terjesztési pontnál, amelyen engedélyezve van a PXE környezet használata. További információk: [Terjesztési pontok konfigurálása PXE-kérelmek fogadásához](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).  

-   **Rendszerindító adathordozók**  

     Jelölje be az **Ismeretlen számítógépek támogatásának engedélyezése** jelölőnégyzetet a Feladatütemezési média létrehozása varázsló **Biztonság** lapján. További információk: [Terjesztési pontok konfigurálása PXE-kérelmek fogadásához](prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint) és [A Windows központi telepítése a hálózaton keresztül PXE segítségével a System Center Configuration Managerben](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

-   **Előkészített adathordozó**  

     Jelölje be az **Ismeretlen számítógépek támogatásának engedélyezése** jelölőnégyzetet a Feladatütemezési média létrehozása varázsló **Biztonság** lapján. További információ: [Manuálisan előkészített adathordozó létrehozása a System Center Configuration Managerrel](../deploy-use/create-prestaged-media.md).  

