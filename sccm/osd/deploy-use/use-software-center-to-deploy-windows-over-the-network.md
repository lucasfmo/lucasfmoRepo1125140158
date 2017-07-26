---
title: "Windows központi telepítése a hálózaton keresztül használja a Szoftverközpontot |} Microsoft Docs"
description: "Az operációs rendszer telepítene a Szoftverközpont egy meglévő számítógép a Windows új verziójára frissítsen, vagy a Windows frissítése a legújabb verzióra."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 4c3ec20396da37d36f908af527f445a7a736e0ac
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-software-center-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>A Windows központi telepítése a hálózaton keresztül a Szoftverközpont használatával a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A feladatütemezés egy operációs rendszer telepítése a System Center Configuration Managerben elérhetővé tehető a Szoftverközpontban. Az operációs rendszer központi telepítése a következő operációsrendszer-telepítési helyzetekben végezhető el a Szoftverközpontban:  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows frissítése a legújabb verzióra](upgrade-windows-to-the-latest-version.md)  

 Hajtsa végre egy operációsrendszer-telepítési forgatókönyv lépéseit. Ezután az alábbi szakaszok alapján készítheti elő a Szoftverközpontban elérhető központi telepítéseket.  

## <a name="configure-deployment-settings"></a>Központi telepítési beállítások konfigurálása  
 Ha azt szeretné, hogy az operációs rendszer központi telepítése a szoftverközpontban elérhető legyen, konfigurálnia kell a központi telepítés elérhetővé az operációs rendszer Configuration Manager-ügyfelek számára. Ezt a Szoftver központi telepítése varázsló **Központi telepítési beállítások** lapján, vagy a központi telepítés tulajdonságainak **Központi telepítési beállítások** lapján konfigurálhatja.  Az **A következő elérhetővé tétele** beállításhoz vagy a **Csak Configuration Manager-ügyfelek** vagy a **Configuration Manager-ügyfelek, média és PXE**értéket állítsa be. Az operációs rendszer a központi telepítése után megjelenik a célgyűjtemény tagjai számára a Szoftverközpontban.  

##  <a name="BKMK_Deploy"></a> A feladatütemezés központi telepítése számítógépekre  
 Végezze el a az operációs rendszer központi telepítését egy célgyűjteményben. További információ: [Feladatütemezés központi telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Operációs rendszerek a Szoftverközponthoz való központi telepítésekor beállítható, hogy a központi telepítés kötelező vagy elérhető legyen.  

-   **Kötelező központi telepítés**: Szükséges központi telepítések lehetővé teszi az operációs rendszer a Szoftverközpontban, de az automatikusan fog elindulni a beállított hozzárendelési ütemezés szerint.  

-   **Elérhető központi telepítés**: A szoftverközpontban az operációs rendszer elérhető lesz, és a felhasználó igény szerint telepítheti azt.  

