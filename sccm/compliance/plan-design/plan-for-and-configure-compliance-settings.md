---
title: "Tervezze meg és konfigurálhatja a megfelelőségi beállítások |} Microsoft Docs"
description: "Információ az Előfeltételek és a megfelelőségi beállítások a System Center Configuration Managerben való munkához konfigurációs feladatok."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ea20b01-676a-4cc2-b328-0098a41b202e
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: d26ac3de58d2f0ef447725e63fc2d8adda6ea06c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-and-configure-compliance-settings-in-system-center-configuration-manager"></a>A megfelelőségi beállítások tervezése és konfigurálása a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt elkezdené a System Center Configuration Manager megfelelőségi beállításainak használatát, nincsenek meg kell ismernie néhány előfeltételt és néhány konfigurációs feladatot, el kell végeznie.  

## <a name="prerequisites-for-compliance-settings"></a>A megfelelőségi beállítások használatának előfeltételei  

|Előfeltétel|További információ|  
|------------------|----------------------|  
|A Windows Configuration Manager-ügyfelek kell engedélyezni és konfigurálni a megfelelőség kiértékelését.|Lásd az alábbi|  
|Ha szeretne jelentéseket futtatni, konfigurálnia kell a jelentéskészítést a helyen.|[Jelentéskészítés a System Center Configuration Manager alkalmazásban](../../core/servers/manage/reporting.md)|  
|Szükséges biztonsági engedélyekkel.|A **Megfelelőségibeállítás-kezelő** biztonsági szerepkör tartalmazza a megfelelőségi beállítások, a felhasználói adatokat és profilokat tartalmazó konfigurációs elemek és a távoli kapcsolati profilok kezeléséhez szükséges engedélyeket.<br /><br /> [Szerepköralapú Adminisztráció konfigurálása](../../core/servers/deploy/configure/configure-role-based-administration.md)|  

##  <a name="enable-and-configure-compliance-settings-for-windows-pcs-only"></a>Engedélyezze és konfigurálja a megfelelőségi beállítások (a csak Windows rendszerű számítógépek)  

Ezzel az eljárással konfigurálhatja a megfelelőségi beállítások alapértelmezett ügyfélbeállításait, és alkalmazhatja azokat a hierarchia összes számítógépére. Ha ezeket a beállításokat csak néhány számítógépen szeretné alkalmazni, hozzon létre egyéni ügyfélbeállítást az eszközökhöz, és rendelje hozzá az azokat a számítógépeket tartalmazó gyűjteményhez, amelyeken megfelelőségi beállításokat szeretne alkalmazni. Egyéni Eszközbeállítás létrehozásáról további információk: [ügyfélbeállítások konfigurálása](../../core/clients/deploy/configure-client-settings.md).  

> [!TIP]  
>  Más eszköztípusok esetében nem szükséges további konfiguráció a megfelelőségi beállítások kiértékeléséhez.  

1.  Kattintson a Configuration Manager konzolon **felügyeleti** > **ügyfélbeállítások** > **alapértelmezett beállítások**.  
2.  A **Kezdőlap** **Tulajdonságok** csoportjában kattintson a **Tulajdonságok**elemre.  
3.  Az **Alapértelmezett beállítások** párbeszédpanelen kattintson a **Megfelelőségi beállítások**elemre.  
4.  Állítsa be a megfelelőségi beállítások következő ügyfélbeállításait:
    - **Megfelelés kiértékelésének engedélyezése az ügyfelek** -beállítása **igaz** Ha ki szeretné értékelni a megfelelőség az ügyféleszközökön.
    - **A megfelelés kiértékelésének ütemezése** -kattintson **ütemezés** Ha szeretné módosítani a megfelelőség értékelésének alapértelmezett ütemezését az ügyféleszközökön.
    - **Felhasználói adatok és profilok engedélyezése** -engedélyezi ezt a beállítást, ha szeretne létrehozni, és a felhasználói adatokat és profilokat tartalmazó konfigurációs elemeket telepíteni a Windows rendszerű számítógépekre. További információkért lásd: [felhasználói adatokat és profilokat tartalmazó konfigurációelemek létrehozása](/sccm/compliance/deploy-use/create-remote-connection-profiles).
5. Kattintson az **OK** gombra az **Alapértelmezett beállítások** párbeszédpanel bezárásához.  

Az ügyfélszámítógépek ezekkel a beállításokkal lesznek konfigurálva, amikor legközelebb letöltik az ügyfélházirendet.  

