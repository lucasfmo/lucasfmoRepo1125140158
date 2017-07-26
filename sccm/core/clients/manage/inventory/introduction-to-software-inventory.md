---
title: "A szoftverleltár |} Microsoft Docs"
description: "Ismerkedjen meg a szoftverleltár a System Center Configuration Managerben."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: 969f2d28649853ddc95860fe72597d6d2c9a94e9
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-software-inventory-in-system-center-configuration-manager"></a>Szoftverleltár a System Center Configuration Manager bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A szoftverleltárral az ügyféleszközökön fájlokról gyűjthetők adatok. A szoftverleltár is fájlokat gyűjthet az ügyféleszközökön, és tárolja őket a helykiszolgálón. Ha úgy dönt, a szoftverleltár gyűjtött a **szoftverleltározás engedélyezése az ügyfelek** beállítása az ügyfélbeállításokban, amelyen is ütemezheti a műveletet.  

Szoftverleltár engedélyezése, és egy szoftverleltározási ciklus lefutása után az ügyfél az adatokat küld egy felügyeleti pont az ügyfél telephelyén található. A felügyeleti pont ezután továbbítja a leltáradatokat a Configuration Manager-kiszolgálóra, ami a hely adatbázisában tárolja az információkat.   

 Íme a szoftverleltár adatainak megtekintéséhez:  

-   [Lekérdezések létrehozása](../../../../core/servers/manage/queries-technical-reference.md) , amelyek eszközök térjen vissza a megadott fájlt.   

-   Hozzon létre [lekérdezésalapú gyűjtemények](../../../../core/clients/manage/collections/introduction-to-collections.md) , amely tartalmazza az eszközt a megadott fájlt.   

-   [Jelentések futtatása](../../../../core/servers/manage/reporting.md) , amelyek részletesen bemutatják fájlok eszközökön.

-   Használjon [erőforrás-kezelő](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md) megvizsgálhatja a leltározott és ügyféleszközökről begyűjtött fájlok részletes információkat.   

 Amikor egy ügyféleszközön szoftverleltár fut, az első jelentés egy teljes leltár. További jelentések csak különbözeti leltáradatokat tartalmaznak. A helykiszolgáló különbözeti adatokat kapott sorrendben dolgozza fel. Ha egy ügyfél különbözeti adatai hiányoznak, a helykiszolgáló elutasítja a további különbözeti adatokat, és utasítja az ügyfelet egy teljes leltárat futtat.  

 A Configuration Manager is kétrendszeres számítógépek felderítésére, de csak az operációs rendszer, amely a készlet időpontjában aktív volt leltáradatokat adja vissza.  

**Mobileszközök:** Lásd: [szoftverleltár mobileszközök Microsoft Intune-nal regisztrált](../../../../mdm/deploy-use/software-inventory-mobile-devices.md) mobileszközökön telepített alkalmazások szoftverleltár begyűjtése az információt.

