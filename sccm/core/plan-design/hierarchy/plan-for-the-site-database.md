---
title: "A hely adatbázisának megtervezése |} Microsoft Docs"
description: "A System Center Configuration Manager-hierarchia tervezésekor gondolja át a helyadatbázist és a Helyadatbázis-kiszolgáló szerepkör."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 104fb4cc-6e83-40a3-8e6b-ac909fb9ec7d
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cec63ed7781e236dbf5e8baa0a468193ea794339
ms.openlocfilehash: d4efe1f013dbb74efca79cd27f7248fc085c7424
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-site-database-for-system-center-configuration-manager"></a>A System Center Configuration Manager helyadatbázisának megtervezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Helyadatbázis-kiszolgáló a Microsoft SQL Server támogatott verzióját futtató számítógép. SQL Server információkat a Configuration Manager-helyek tárolására szolgál. A Configuration Manager-hierarchiában minden hely tartalmaz egy helyadatbázist és egy kiszolgálót, amely a Helyadatbázis-kiszolgáló szerepkör van hozzárendelve.  

-   A központi adminisztrációs helyek és elsődleges helyek esetén SQL Server a helykiszolgálón, vagy telepíthet telepítése az SQL Server a helykiszolgálótól eltérő számítógépen.  

-   Másodlagos helyeken használhatja az SQL Server Express a teljes SQL Server telepítése helyett. Az adatbázis-kiszolgáló kell, azonban a másodlagos helykiszolgálón futtatja a.  

A következő SQL Server-beállítások segítségével a Helyadatbázis futtatására:  

-   Az SQL Server alapértelmezett példánya  

-   Nevesített példány egyetlen SQL Servert futtató számítógépen  

-   Nevesített példány az SQL Server fürtözött példányán  

-   Egy SQL Server AlwaysOn rendelkezésre állási csoport (a System Center Configuration Manager 1602-es verziójától kezdődően)


A Helyadatbázis futtatására, az SQL Server meg kell felelnie a részletes [SQL Server-verziók támogatása a System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  



## <a name="remote-database-server-location-considerations"></a>Távoli adatbázis-kiszolgáló helyét használata  

Ha egy távoli adatbázis-kiszolgáló számítógépen használja, gondoskodjon arról, hogy a beavatkozó hálózati kapcsolat magas rendelkezésre állású, nagy sávszélességű hálózati kapcsolat. A helykiszolgáló és bizonyos helyrendszerszerepkörökre folyamatosan kommunikálnia kell a távoli kiszolgálóhoz, amelyen a Helyadatbázis.

-   Az adatbázis-kiszolgáló folytatott kommunikációhoz szükséges sávszélesség számos különböző hely- és ügyfélbeállítástól kombinációja függ. Ezért a tényleges sávszélességre van szüksége nem megfelelően meghatározható.  

-   Minél több, SMS szolgáltatót futtató számítógép csatlakozik a helyadatbázishoz, annál nagyobb sávszélességre van szükség.  

-   Az SQL Server rendszert futtató számítógépen, amely rendelkezik kétirányú megbízhatósági kapcsolattal a helykiszolgáló és az SMS-szolgáltatót futtató összes számítógépen tartományban kell lennie.  

-   Nem használható fürtözött SQL Server a helyadatbázis-kiszolgálóhoz, ha a helyadatbázis ugyanott van, ahol a helykiszolgáló.  


Általában a helyrendszer-kiszolgálót helyrendszer-szerepkörét innen egyetlen Configuration Manager-hely támogatja. Azonban segítségével több SQL Server-példány az SQL Servert futtató fürtözött vagy nem fürtözött kiszolgálókon másik Configuration Manager-helyek adatbázisának futtatására. A különböző helyek adatbázisainak kezeléséhez az SQL Server mindegyik példányán egyedi kommunikációs portot kell beállítani.  

