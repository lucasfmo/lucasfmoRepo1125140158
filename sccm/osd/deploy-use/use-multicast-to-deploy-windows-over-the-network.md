---
title: "Windows központi telepítése a hálózaton keresztül használjon csoportos |} Microsoft Docs"
description: "Csoportos küldés használatára a System Center Configuration Manager környezetben, hogy több számítógép is az operációs rendszer lemezkép egyidejű letöltését."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 55266696aa7340fddda3a57ff90e20222ff665a5
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Csoportos küldés használatára a Windows központi telepítése a hálózaton a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A csoportos küldés esetén olyan hálózatoptimalizálási módszer, amely használható a System Center Configuration Manager környezetben, ahol több ügyfél valószínűleg egyszerre ugyanazon operációs rendszer lemezképét letöltése. A csoportos küldés használatakor egyidejűleg több számítógép is letölti ugyanazon operációs rendszer lemezképét, mivel azt a terjesztési pont küldi csoportosan ahelyett, hogy az adatok másolatát mindegyik ügyfélgéphez külön kapcsolaton kellene küldenie.  

 Az operációs rendszer központi telepítése a következő operációsrendszer-telepítési helyzetekben végezhető el csoportos küldéssel a hálózaton keresztül:  

-   [A Windows új verziójára meglévő számítógép frissítése](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [A Windows új verziójának telepítése egy új (operációs rendszer nélküli) számítógépre](install-new-windows-version-new-computer-bare-metal.md)  

 Hajtsa végre egy operációsrendszer-telepítési forgatókönyv lépéseit. Ezután az alábbi szakaszok alapján biztosíthatja a csoportos küldés támogatását.  

##  <a name="BKMK_Configure"></a> Terjesztési pont konfigurálása a csoportos küldés támogatásához  
 Ahhoz, hogy csoportos küldést használhasson az operációs rendszerek központi telepítéséhez, konfigurálnia kell egy terjesztési pontot a csoportos küldés támogatására. További információkért lásd: [konfigurálása a csoportos küldés támogatásához a terjesztési pontok](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast).  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>Operációsrendszer-lemezkép előkészítése csoportos küldéssel történő központi telepítésre  
 Az operációs rendszer lemezképének csomagját csoportos küldéshez konfigurálásáról lásd: [az operációs rendszer lemezképének előkészítése csoportos központi telepítést](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast).  

##  <a name="BKMK_Deploy"></a> A feladatütemezés központi telepítése  
 Az operációs rendszer központi telepítése egy célgyűjteménybe További információk: [Feladatütemezés telepítése](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

