---
title: "Kiértékelési telepítések frissítése |} Microsoft Docs"
description: "Próbaverzió frissítése teljes változatra a System Center Configuration Manager útmutató."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9a32f5a3-9917-434f-9811-106170f404be
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d1bf0fdc3e735eb31492476fd46f008620150c0b
ms.openlocfilehash: 8f951805c2fc25059965c15c94934c0f8546735c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="upgrade-an-evaluation-installation-of-system-center-configuration-manager-to-a-full-installation"></a>Próbaverzió frissítése a System Center Configuration Manager teljes verzióra

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ha a System Center Configuration Manager próbaverziójáról, telepítette 180 nap elteltével, a Configuration Manager konzol csak olvashatóvá válik, amíg nem aktiválja a terméket a **Helykarbantartás** oldalon a telepítő. Előtt vagy a 180 napos időszak után bármikor lehetősége van a próbaverzió frissítése teljes változatra.  

> [!NOTE]  
>  Amikor a Configuration Manager konzol csatlakozik a Configuration Manager próbaverziójáról van szó, a konzol címsorában megjelenik az, hogy hány napig maradnak, amíg a próbaverzió lejártáig. A napok számát nem automatikusan, hogy csak frissíti, amikor egy új kapcsolatot egy helyhez.  

 A következő próbaverziót futtató helyek frissíthetők:  

-   Központi adminisztrációs hely  
-   Elsődleges hely  

A másodlagos helyek a rendszer nem kezeli próbaverzióként, mert nem kell módosítani a másodlagos helyek a elsődleges szülőhelyük teljes verzióra történő frissítése után.  

A próbaverzió licencelt verzióra való frissítést Előfeltételek:  

-   A frissítés során használandó érvényes termékkel kell rendelkeznie.  
-   A fióknak rendelkeznie kell **rendszergazda** jogosultságokkal azon a számítógépen, amelyen a hely telepítve van.  

### <a name="to-upgrade-an-evaluation-version-of-configuration-manager-to-a-licensed-version"></a>A Configuration Manager próbaverziójának frissítése licencelt verzióra  

1.  A helyrendszer-kiszolgálón futtassa **Setup.exe** (Configuration Manager telepítő) a Configuration Manager telepítési mappájából (**%path%\BIN\X64**). Mivel a hely helykarbantartási beállításai nem érhetők el, amikor a telepítő telepítési adathordozóról a helykiszolgálón a Configuration Manager mappában található telepítőprogramot kell futtatni.  
2.  Az a **előkészületek** lapon jelölje be **következő**.  
3.  Az a **bevezetés** lapon jelölje be **helykarbantartás végrehajtása vagy a hely alaphelyzetbe állítása**, majd válassza ki **következő**.  
4.  Az a **Helykarbantartás** lapon jelölje be **a próbaverziót frissítse egy licencelt kiadásra**, adjon meg egy érvényes termékkulcsot, és válassza **következő**.  
5.  Az a **Microsoft szoftverlicenc-szerződés** lapon olvassa el és fogadja el a licencfeltételeket, és válassza ki **következő**.  
6.  Az a **konfigurációs** lapon jelölje be **Bezárás** a varázsló befejezéséhez.  

    > [!NOTE]  
    >  A fennmaradó frissített helyhez kapcsolódó Configuration Manager konzol címsorában található utalhat, hogy a hely még próbaverzió, amíg újra a konzolt a helyhez.  

