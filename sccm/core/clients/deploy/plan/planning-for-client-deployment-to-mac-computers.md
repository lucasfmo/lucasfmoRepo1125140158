---
title: "Ügyfelek Mac számítógépekre való központi telepítésének megtervezése |} Microsoft Docs"
description: "Tervezze meg a Mac számítógépekre a System Center Configuration Managerben történő központi ügyféltelepítésre."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d15ae3f-de42-461f-a907-c43873da22d2
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 75bddb41d4d1cf209fa7595c52b5a6aa831ba3dd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-client-deployment-to-mac-computers-in-system-center-configuration-manager"></a>A Mac számítógépekre a System Center Configuration Manager ügyfél központi telepítésének tervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager-ügyfelet telepítheti Mac számítógépekre, a Mac OS X operációs rendszert futtat, és az alábbi felügyeleti szolgáltatásokat használhatja:  

-   **Hardverleltár**  

     Hardverleltár a Configuration Manager segítségével hardverére vonatkozó információk gyűjtése, és a telepített alkalmazások Mac számítógépeken. Ez az információ majd a Configuration Manager konzolon az erőforrás-kezelőben tekinthetők meg és gyűjtemények, lekérdezések és jelentések létrehozásához használt. További információkért lásd: [System Center Configuration Manager a Hardverleltár megjelenítése az erőforrás-kezelő használatával](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

     A Configuration Manager az alábbi hardverinformációkat gyűjti a Mac számítógépekről:  

    -   Processzor  

    -   Számítógéprendszer  

    -   Lemezmeghajtó  

    -   Lemezpartíció  

    -   Hálózati Adapter  

    -   Operációs rendszer  

    -   Szolgáltatás  

    -   Folyamat  

    -   Telepített szoftverek  

    -   Számítógéprendszer-termék  

    -   USB-vezérlő  

    -   USB-eszközzel  

    -   CD-ROM-meghajtó  

    -   Videovezérlő  

    -   Asztali Monitor  

    -   Hordozható akkumulátor  

    -   Fizikai memória  

    -   Nyomtató  

    > [!IMPORTANT]  
    >  A Mac számítógépekről hardverleltározással gyűjtött hardverinformációk nem terjeszthetők ki.  

-   **Megfelelőségi beállítások**  

     A Configuration Manager megfelelőségi beállítások segítségével ellenőrizhető, és szervizelheti azokat a Mac OS X egyéni (.plist) beállításokat. Például nem sikerült a kezdőlap adatgyűjtéséhez a Safari webböngésző-beállításokat érvényesítő, vagy győződjön meg arról, hogy az Apple tűzfal engedélyezve van. Rendszerhéj-parancsfájlok használatával figyelheti és javíthatja a beállításokat a MAC OS X.  

-   **Alkalmazáskezelés**  

     A Configuration Manager szoftver központi telepítése Mac számítógépekre is. A következő szoftverformátumok telepíthetők a Mac számítógépekhez:  

    -   Apple-lemezképfájl (. DMG)  

    -   Meta Package-fájl (. MPKG)  

    -   Mac OS X telepítőcsomag (. PKG)  

    -   Mac OS X-alkalmazás (. AZ ALKALMAZÁS)  

 Ha a Configuration Manager-ügyfél Mac számítógépekre telepíti, a következő felügyeleti képességeket, amelyek a Configuration Manager-ügyfél Windows-alapú számítógépek által támogatott nem használható:  

-   Ügyfél leküldéses telepítése  

-   Operációs rendszer központi telepítése  

-   Szoftverfrissítések  

    > [!NOTE]  
    >  Alkalmazások kezelése a Configuration Manager segítségével központilag a szükséges Mac OS X-szoftverfrissítéseket a Mac számítógépekre. Megfelelőségi beállítások segítségével emellett győződjön meg arról, hogy a számítógépek rendelkeznek a szükséges szoftverfrissítéseket.  

-   Karbantartási időszakok  

-   Távvezérlés  

-   Energiagazdálkodás  

-   Ügyfélállapot ellenőrzése és hibák elhárítása  

 A Configuration Manager Mac-ügyfél telepítésének és konfigurálásának módjáról további információkért lásd: [ügyfélszoftverek központi telepítése Mac-számítógépekre a System Center Configuration Managerben](../../../../core/clients/deploy/deploy-clients-to-macs.md).

