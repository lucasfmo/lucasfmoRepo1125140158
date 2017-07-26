---
title: "Hardverleltár megjelenítése |} Microsoft dokumentumok |} Az erőforrás-kezelő"
description: "Erőforrás-kezelővel a System Center Configuration Managerben Hardverleltár megjelenítése."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
caps.latest.revision: 7
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: e39fa60a5d215fa1b0a98d4463058497e63a4d4f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/29/2017


---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-system-center-configuration-manager"></a>A hardverleltár megjelenítése az erőforrás-kezelővel a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Erőforrás-kezelővel a System Center Configuration Managerben a hierarchiában lévő ügyfelekről gyűjtött Hardverleltár vonatkozó információk megtekintése.  

> [!NOTE]  
>  Az erőforrás-kezelő semmilyen leltáradatot nem jelenít meg, amíg le nem futott egy hardverleltározási ciklus az ügyfélen, amelyhez csatlakozik.  

 Az erőforrás-kezelő rendelkezik a hardverleltárral kapcsolatos alábbi szakaszokat:  

-   **Hardver** -tartalmazza az adott ügyféleszközről begyűjtött legfrissebb Hardverleltár.  **Munkaállomás állapota** rendelkezik, amikor az eszköz által legutóbb elvégzett Hardverleltár dátumát és időpontját.  

-   **Hardverelőzmények** -a legutóbbi Hardverleltár óta módosított leltározott elemek előzményeit tartalmazza. Minden elem tartalmaz egy **aktuális** csomópont és egy vagy több *< dátum\>*  csomópontok. Összehasonlíthatja az aktuális csomópont egy előzménycsomóponttal módosított elemek felderítése céljából információkat.  

    > [!NOTE]  
    >  A Configuration Manager Hardverleltár-előzményeket őrzi meg a megadott napok számát a **elavult Leltárelőzmények törlése** helykarbantartási feladat  

> [!NOTE]  
>  A Linux és UNIX rendszert futtató ügyfelek hardverleltárának megtekintésére vonatkozó információért lásd: [A Linux és UNIX rendszerű kiszolgálókhoz készült ügyfelek figyelése a System Center Configuration Managerben](../../../../core/clients/manage/monitor-clients-for-linux-and-unix-servers.md).  

### <a name="how-to-run-resource-explorer-from-the-configuration-manager-console"></a>Az erőforrás-kezelő futtatása a Configuration Manager konzolról  

1.  Kattintson a Configuration Manager konzol **eszközök és megfelelőség** > **eszközök**, vagy nyisson meg egy gyűjteményt, amely eszközöket jelenít meg.  

3.  Válassza ki a megtekinteni kívánt leltárt tartalmazó számítógépre, majd a a **Home** lapon > **eszközök** csoportjában válassza **Start** >  **erőforrás-kezelő**.   

4.  Kattintson a jobb gombbal a tetszőleges elemre a jobb oldali ablaktáblájában a **erőforrás-kezelő** ablakban válassza **tulajdonságok** megnyitásához a *< elem neve\>***tulajdonságok** párbeszédpanelt, amelyen megtekintheti az összegyűjtött leltáradatokat olvashatóbb formátumban.  


