---
title: "Szoftverleltár beállítása |} Microsoft Docs"
description: "Szoftverleltár konfigurálása, és a mappák kihagyása a szoftverleltárból a Configuration Manager alkalmazásban."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f86559de-092a-4ce8-9b43-5d7530e0b763
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: e60cec71c425e5e42d450cbeee366528d4b42405
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>Szoftverleltár konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Ezzel az eljárással konfigurálhatja a szoftverleltár alapértelmezett ügyfélbeállításait, amelyek a hierarchia minden számítógépére érvényesek lesznek. Ha alkalmazza ezeket a beállításokat csak néhány számítógépen szeretné, hozzon létre egy egyéni ügyfélbeállítást az eszközökhöz, és rendelje hozzá egy gyűjteményhez, amely tartalmazza a szoftverleltár használni kívánt számítógépeket. Egyéni Eszközbeállítás létrehozásáról további információk: [ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../../core/clients/deploy/configure-client-settings.md).  

## <a name="to-configure-software-inventory"></a>Szoftverleltár konfigurálása  

1.  Kattintson a Configuration Manager konzol **felügyeleti** > **ügyfélbeállítások****alapértelmezett ügyfélbeállítások**.    

4.  Az a **Home** lap a **tulajdonságok** csoportjában válassza **tulajdonságok**.  

5.  Az a **alapértelmezett beállítások** párbeszédpanelen válassza ki **szoftverleltár**.  

6.  Az **Eszközbeállítások** listában állítsa be a következő értékeket:  

    -   **Szoftverleltár engedélyezése az ügyfelek** – a legördülő listában válassza a **igaz**.  

    -   **Ütemezés szoftver szoftverleltárral és fájlgyűjtéssel adatgyűjtési ütemezést** – beállítja, milyen gyakorisággal gyűjtenek szoftverleltárt és fájlokat.   

7.  Adja meg a szükséges ügyfélbeállításokat. Szoftverleltár elérhető ügyfélbeállításait konfigurálható listájáért lásd: a [szoftverleltár](../../../../core/clients/deploy/about-client-settings.md#software-inventory) szakasz a [információ a System Center Configuration Manager ügyfélbeállításainak](../../../../core/clients/deploy/about-client-settings.md) témakör.  

 Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet. Egyetlen ügyfél házirendlekérésének kezdeményezéséről a [Ügyfélszoftverek kezelése a System Center Configuration Managerben](../../../../core/clients/manage/manage-clients.md) című témakör nyújt tájékoztatást.  


## <a name="to-exclude-folders-from-software-inventory"></a>Mappák kihagyása a szoftverleltárból  

1.  A Notepad.exe használatával hozzon létre egy **Skpswi.dat**nevű, üres fájlt.  

2.  Kattintson a jobb gombbal a **Skpswi.dat** fájlra, majd kattintson a **Tulajdonságok**menüpontra. A Skpswi.dat fájl tulajdonságait között jelölje be a **Rejtett** attribútumot.  

3.  Helyezze a **Skpswi.dat** fájlt minden olyan ügyfél merevlemezének gyökérkönyvtárába, illetve minden olyan mappaszerkezet legfelső szintjére, amelyet ki szeretne hagyni a szoftverleltárból.  

> [!NOTE]  
>  A szoftverleltár nem készít újabb leltárt az ügyfél meghajtójáról mindaddig, amíg a fájlt nem törlik a meghajtóról vagy az ügyfélszámítógépről.
