---
title: "Frissítse a hosszú távú karbantartási ág az aktuális ág |} Microsoft Docs"
description: "Megtudhatja, hogyan alakíthatja át a hosszú távú karbantartási ág helyet aktuális ág helyhez."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec5b54cf-62b7-4ed1-9bb3-e8c63b9641c8
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 60631bc0346bd78d704e7129bb755af504c59b1b
ms.openlocfilehash: 6e7edc85630d22c5bbba1ff66bd1199903db76db
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---


# <a name="upgrade-the-long-term-servicing-branch-to-the-current-branch"></a>Frissítse a hosszú távú karbantartási ág az aktuális ág

*Vonatkozik: A System Center Configuration Manager (hosszú távú karbantartási ág)*

A témakör segítségével megtudhatja, hogyan (Konvertálás) frissítése a hely és a hierarchia, a hosszú távú karbantartási ág (LTSB) a Configuration Manager aktuális ágának futtató.

Ha a jelenlegi frissítési garancia szerződés (vagy hasonló jogokat), amely engedélyezi a jogosultságokat az aktuális ág használatára, az aktuális ág számára átalakíthatja a telepítést a LTSB.  Ennek oka egy egyirányú átalakítás nem támogatott az aktuális ág hely átalakításához a LTSB.

Ha több hellyel rendelkezik, csak alakíthatja át a a hierarchia legfelső szintű helyet kell. Miután a legfelső szintű helyén alakul:
- A gyermek elsődleges helyek automatikusan konvertálni.
-    A Configuration Manager konzolon másodlagos helyeket manuálisan frissíteni kell.

## <a name="run-setup-to-convert-the-long-term-servicing-branch"></a>Futtassa a telepítőt a hosszú távú karbantartási ág konvertálni
A legfelső szintű helyen a hierarchia, Configuration Manager telepítőt az alapszintű verziót tartalmazó adathordozó jogosult és kiválasztása **karbantartási hely**.  A licencelési oldal jelenik meg, amikor, majd válassza ki az aktuális ág beállítását, és fejezze be a varázslót.

Ha a webhely az aktuális ág rendelkezik konvertálva, korábban elérhető funkciók és képességek lesz használható.

> [!NOTE]  
> Alapszintű verziót tartalmazó adathordozó jogosult egy adathordozó, amelyen a rendszer a egyenlőnek vagy annál újabb, mint a LTSB telepítését.

Például mivel a LTSB 1606 verzión alapul, nem használható az eredeti 1511-es adathordozó az aktuális ág konvertálása. Ehelyett, futtassa a telepítőt a azonos verziójú 1606 alapszintű verziót tartalmazó adathordozó a LTSB hely telepítéséhez használt, és az aktuális ág licencelési lehetőséget.  Alternatív megoldásként az aktuális ág egy újabb alapkonfigurációt már ki van adva, a telepítő a adott alapkonfiguráció adathordozóról is futtathatja.

Alapkonfiguráció verziók listáját lásd: **alapkonfiguráció és frissítési verziók** a [frissíti a Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="use-the-configuration-manager-console-to-convert-the-long-term-servicing-branch"></a>A Configuration Manager konzol használatával alakítsa át a hosszú távú karbantartási ág
Ha a webhely a LTSB fut, használhatja a következő lehetőséget a Configuration Manager konzolon az aktuális ág átalakítása:

 1. Nyissa meg a a konzol **felügyeleti** > **Helykonfiguráció** > **helyek**, majd nyissa meg **Hierarchiabeállítások**.  

 2. Válassza ki, hogy az aktuális ág átalakítása, majd kattintson a beállítás **alkalmaz**.  

Ha a webhely az aktuális ág rendelkezik konvertálva, korábban elérhető funkciók és képességek lesz használható.

