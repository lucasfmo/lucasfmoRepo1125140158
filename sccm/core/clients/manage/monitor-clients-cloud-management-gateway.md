---
title: "A figyelő felügyeleti átjáró - a Configuration Manager |} Microsoft Docs"
description: 
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: daa0790995dc13ec2c78ae2d98a9eb38c0bcf8ae
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>A figyelő felhő adatkezelési átjárót a Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

1610, miután a felhő management gateway szolgáltatás fut, és azt keresztül csatlakozik az ügyfelek verziójától kezdve, figyelheti az ügyfelek és a hálózati forgalmat, hogy ha tudja, hogyan működik-e a szolgáltatás.

## <a name="monitor-clients"></a>A figyelő ügyfelek

A felhő management gateway szolgáltatás keresztül csatlakozó ügyfelek jelennek meg a Configuration Manager konzol azonos módon helyszíni ügyfelek tegye. További információkért lásd: [ügyfelek figyelése](monitor-clients.md).

## <a name="monitor-traffic-in-the-console"></a>A konzol forgalmat figyelő

A Configuration Manager konzol használatával a felhő adatkezelési átjáró forgalmát képes figyelni:

1. Lépjen **felügyelet > Felhőszolgáltatások > Cloud az adatkezelési átjáró**.

2. A lista ablaktáblájában jelölje ki a felhő management gateway szolgáltatás.

3. A forgalom tekintse meg a részleteket tartalmazó ablaktáblán, a felhő felügyeleti átjáró csatlakozási szerepkör és a helyrendszer-szerepkörök csatlakozik.

## <a name="set-up-outbound-traffic-alerts"></a>Kimenő forgalom riasztások beállítása

Kimenő forgalom figyelmeztetés azt jelzi, ha a forgalom megközelíti a 14 napos (2 hét) küszöbértéket segítségével. Lehetősége van a lehetőség a forgalom riasztások beállítását, a felhő management gateway szolgáltatás létrehozásakor. Ha kihagyja a része, továbbra is állíthatja be a riasztások után fut a szolgáltatás. És a riasztási beállítások bármikor is módosíthatja.

1. Lépjen **felügyelet > Felhőszolgáltatások > Cloud az adatkezelési átjáró**.

2. Kattintson a jobb gombbal a felügyeleti átjáró felhőszolgáltatás a lista ablaktáblájában, és válassza a **tulajdonságok**.

3. Kattintson a riasztások lapra, és válassza a (vagy kikapcsolásához) a küszöbérték és riasztások tartalmazzák. Adja meg a 14 napos küszöbértéke (GB) a és a különböző riasztási szintű előléptetése küszöbérték százalékos aránya.

4. Kattintson a **OK** befejezése.

## <a name="monitor-logs"></a>A figyelő naplók

A felhő management gateway szolgáltatás bejegyzések fájlok száma hoz létre. További információkért lásd: [a Configuration Manager naplóinak](/sccm/core/plan-design/hierarchy/log-files).

