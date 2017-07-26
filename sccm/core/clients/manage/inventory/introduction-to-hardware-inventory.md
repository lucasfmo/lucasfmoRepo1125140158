---
title: "Hardverleltár - Configuration Manager |} Microsoft Docs"
description: "Bevezetés az Hardverleltár a System Center Configuration Managerben."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: c64f0b42bff25e8e91cf9101d6fbb538634eab15
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-hardware-inventory-in-system-center-configuration-manager"></a>A System Center Configuration Manager hardverleltárának bemutatása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A szervezet ügyféleszközök hardverkonfigurációjáról kapcsolatos információk összegyűjtéséhez használja a System Center Configuration Managerben az Hardverleltár. Hardverleltár engedélyezéséhez az ügyfélbeállítások között engedélyezni kell a **Hardverleltár engedélyezése az ügyfeleken** beállítást.  

 Miután Hardverleltár engedélyezve van, és az ügyfél által futtatott egy hardverleltározási ciklust, az ügyfél az adatokat küld egy felügyeleti pont az ügyfél telephelyén található. A felügyeleti pont ezután továbbítja a leltáradatokat a Configuration Manager helykiszolgálón, amely a helyadatbázisban tárolja a leltáradatokat. A hardverleltár az ügyfélbeállításokban megadott ütemezés szerint fut le az ügyfeleken.  

 Többféle módszer segítségével a Configuration Manager által gyűjtött hardverleltározási adatok megtekintéséhez. Ezek a következők:  

-   [Adott hardverkonfiguráción alapuló eszközöket visszaadó lekérdezések létrehozása](../../../../core/servers/manage/queries-technical-reference.md).  

-   [Adott hardverkonfiguráción alapuló, lekérdezésalapú gyűjtemények létrehozása](../../../../core/clients/manage/collections/introduction-to-collections.md). A lekérdezésalapú gyűjteménytagságok ütemezés szerint automatikusan frissülnek. A gyűjtemények számos feladatra, például szoftverek telepítésére használhatók. .  

-   [A szervezetben használt hardverkonfigurációk részletes adatait megjelenítő jelentéseket futtathat](../../../../core/servers/manage/reporting.md).   

-   [Erőforrás-kezelővel](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) az ügyféleszközökről begyűjtött Hardverleltár részletes adatainak megtekintéséhez.   

 Amikor egy ügyféleszközön szoftverleltár fut le, az első visszaadott leltáradat mindig egy teljes leltár. Az ezt követő leltáradatok csak különbözeti leltáradatokat tartalmaznak. A helykiszolgáló abban a sorrendben dolgozza fel a különbözeti leltáradatokat, amelyben beérkeznek. Ha egy ügyfél különbözeti adatai hiányoznak, a helykiszolgáló elutasítja a további különbözeti adatokat, és utasítja az ügyfelet egy teljes leltározási ciklus futtatására.  

 A Configuration Manager korlátozott támogatást nyújt a kétrendszeres számítógépek. A Configuration Manager felderíthesse a kétrendszeres számítógépek, de csak leltáradatait adja vissza az operációs rendszer, amely már aktív volt a leltározási ciklus időben futtattak.  

> [!NOTE]  
>  Hardverleltár Linux és UNIX rendszerű ügyfeleken való használatával kapcsolatos információkért lásd: [Hardverleltár Linux és UNIX rendszeren a System Center Configuration Managerben](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md).  

## <a name="extending-configuration-manager-hardware-inventory"></a>A Configuration Manager-hardverleltár kibővítése  
 A beépített Hardverleltár a Configuration Manager mellett is segítségével a következő módszerek egyikét bővíteni a hardverleltárt további információk gyűjtéséhez:  

- Engedélyezése, letiltása, hozzáadhat és eltávolíthatja a Hardverleltár leltárosztályait a Hardverleltár a Configuration Manager konzoljáról. |}  
- NOIDMIF-fájlok ügyféleszközök, amelyekről nem készíthető leltár a Configuration Manager által kapcsolatos információk összegyűjtéséhez használja. Ilyen adatok például az eszközszámokkal kapcsolatos azon információk, amelyek csak címkeként léteznek az adott eszközön. A NOIDMIF-fájlokra épülő leltárt automatikusan ahhoz az ügyféleszközhöz társítja a program, amelyről a leltáradatok származnak.  
- IDMIF-fájlok eszközök, amelyek nem kapcsolódnak a Configuration Manager ügyfelek, például, kivetítőkről, fénymásolókról és hálózati nyomtatókról kapcsolatos információk összegyűjtéséhez használja.  

 További információ az ezekkel a módszerekkel bővíteni a hardverleltárt a Configuration Manager: [Hardverleltár konfigurálása a System Center Configuration Managerben](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

