---
title: "A Windows központi telepítése a hálózaton keresztül rendszerindító adathordozó használatával |} Microsoft Docs"
description: "A System Center Configuration Managerben az rendszerindító adathordozóról kezdeményezett központi telepítések használja az operációs rendszer központi telepítését, a célszámítógép elindításakor."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: beb730efbe4d9bae7c4c97f4e587c8919bd79049
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Rendszerindító adathordozó használatával a Windows központi telepítése a hálózaton a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager telepítő rendszerindító adathordozó lehetővé teszik, hogy az operációs rendszer központi telepítését, a célszámítógép elindításakor. A célszámítógép elindításakor lekéri a hálózatból a feladatütemezést, az operációs rendszer lemezképét és a szükséges egyéb tartalmat. Mivel az adathordozó nem tartalmazza ezt a tartalmat, lehetősége van a tartalom frissítése az adathordozó újbóli létrehozása nélkül.  

 Az operációs rendszer központi telepítése a következő operációsrendszer-telepítési helyzetekben végezhető el csoportos küldéssel a hálózaton keresztül:  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

-   [Meglévő számítógép cseréje és a beállítások átvitele](replace-an-existing-computer-and-transfer-settings.md)  

 Hajtsa végre egy operációsrendszer-telepítési forgatókönyv lépéseit. Ezután az alábbi szakaszok alapján telepítheti az operációs rendszert rendszerindító adathordozó használatával.  

## <a name="configure-deployment-settings"></a>Központi telepítési beállítások konfigurálása  
 Ha rendszerindító adathordozót szeretne használni az operációs rendszer központi telepítésének folyamata során, úgy kell konfigurálnia a központi telepítést, hogy elérhetővé tegye az operációs rendszert adathordozók számára. Ezt a Szoftver központi telepítése varázsló **Központi telepítési beállítások** lapján, vagy a központi telepítés tulajdonságainak **Központi telepítési beállítások** lapján konfigurálhatja.  Az **Elérhetővé tétel a következők számára** beállításnál konfigurálja a következők egyikét:  

-   **Configuration Manager ügyfelek, média és PXE**  

-   **Csak média és PXE**  

-   **Csak média és PXE (rejtett)**  

## <a name="create-the-bootable-media"></a>A rendszerindító adathordozó létrehozása  
 Megadhatja, hogy a rendszerindító adathordozó USB flash meghajtó vagy CD/DVD-készlet legyen. Az adathordozót elindító számítógépnek támogatnia kell a rendszerindító meghajtóként kiválasztott lehetőséget. További információkért lásd: [létrehozásának folyamatáról](create-bootable-media.md).  

##  <a name="BKMK_Deploy"></a> Az operációs rendszer telepítése rendszerindító adathordozóról  
 Az operációs rendszer telepítéséhez helyezze be a rendszerindító adathordozót a számítógép egy rendszerindító meghajtójába, majd kapcsolja be a számítógépet.  

