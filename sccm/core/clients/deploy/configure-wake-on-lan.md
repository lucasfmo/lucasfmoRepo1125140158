---
title: "Hálózati ébresztés konfigurálása |} Microsoft Docs"
description: "Válassza ki a hálózati ébresztés beállításait a System Center Configuration Managerben."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b475a0c8-85d6-4cc4-b11f-32c0cc98239e
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 9c920651ba1dc6e0a28df458d28956126ddbaff0
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-configure-wake-on-lan-in-system-center-configuration-manager"></a>Útmutató a System Center Configuration Manager hálózati ébresztés konfigurálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Adjon meg hálózati beállításait a System Center Configuration Manager ébresztési, ha azt szeretné, hogy számítógépek telepítéséhez szükséges szoftverek, szoftverfrissítések, az alkalmazások, a feladatütemezések és a programok például alvó állapotból.

A hálózati ébresztést kiegészítheti az ébresztési proxy ügyfélbeállításaival. Azonban az ébresztési proxy használatához először a hálózati ébresztés engedélyezése a webhelyhez, és adja meg **csak ébresztési csomagok használata** és a **egyedi küldéses** LAN átviteli módja ébresztés beállítás. Az ébresztési megoldás alkalmi kapcsolatok, például a távoli asztali kapcsolatot is támogatja.

Az első eljárással egy elsődleges hely hálózati ébresztésre konfigurálásához. Ezután a második eljárás segítségével konfigurálhatja az ébresztési proxy ügyfélbeállításokkal. Ez a második eljárás az ébresztési proxy beállítások a hierarchia összes számítógépére érvényes alapértelmezett ügyfélbeállításait konfigurálja. Ha azt szeretné, hogy ezek a beállítások csak a kijelölt számítógépen szeretné alkalmazni, hozzon létre eszközbeállítást, és rendelje hozzá egy gyűjteményhez, amely tartalmazza ébresztési proxy konfigurálni kívánt számítógépeket. További információ az egyedi ügyfélbeállítások létrehozásáról: [Az ügyfélbeállítások konfigurálása a System Center Configuration Managerben](../../../core/clients/deploy/configure-client-settings.md).

Egy számítógép, amely megkapja az ébresztési proxy ügyfélbeállításokkal valószínűleg felfüggeszti a hálózati kapcsolat, 1 – 3 másodpercet. Ennek oka az, hogy az ügyfél-kód alaphelyzetbe állítását a hálózati kártyát ahhoz, hogy az ébresztési proxy illesztőprogram rajta.

> [!WARNING]
> A hálózati szolgáltatások váratlan megszakadását elkerülendő, először mérje fel, az ébresztési proxy egy elszigetelt, de reprezentatív hálózati infrastruktúrán. Egyéni ügyfélbeállítások használatával a tesztelést kiterjessze néhány alhálózaton a számítógépek egy kijelölt csoportját. Az ébresztési proxyról kapcsolatos további információkért lásd: [tervezése a System Center Configuration Manager ügyfelek felébresztése](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

## <a name="to-configure-wake-on-lan-for-a-site"></a>A hálózati ébresztés konfigurálása egy helyhez

1. Nyissa meg a Configuration Manager konzol **Adminisztráció > Helykonfiguráció > helyek**.
2. Az elsődleges hely konfigurálása, majd kattintson **tulajdonságok**.
3. Kattintson a **hálózati ébresztés** lapot, és adja meg az ehhez a webhelyhez szükséges beállításokat. Az ébresztési proxy támogatásához, gondoskodjon róla, hogy **csak ébresztési csomagok használata** és **egyedi küldéses**. További információkért lásd: [tervezése a System Center Configuration Manager ügyfelek felébresztése](../../../core/clients/deploy/plan/plan-wake-up-clients.md).
4. Kattintson a **OK** , és ismételje meg az eljárást a hierarchia összes elsődleges helyén.

## <a name="to-configure-wake-up-proxy-client-settings"></a>Ébresztési proxy ügyfélbeállítások konfigurálása

1. Nyissa meg a Configuration Manager konzol **Adminisztráció > ügyfélbeállítások**.
2. Kattintson a **alapértelmezett ügyfélbeállítások**, és kattintson a **tulajdonságok**.
3. Válassza ki **energiagazdálkodás** majd **Igen** a **engedélyezi az ébresztési proxyt**.
4. Tekintse át, és ha szükséges, a más ébresztési proxy beállításainak konfigurálása. A beállításokkal további információk: [beállítások](../../../core/clients/deploy/about-client-settings.md#power-management).
5. Kattintson a **OK** zárja be a párbeszédpanelt, majd **OK** az alapértelmezett ügyfélbeállítások párbeszédpanel bezárásához.

Az alábbi hálózati ébresztés jelentések használatával figyelheti a telepítés és az ébresztési proxy beállításait:

- Ébresztési proxy telepítési állapotának összegzése
- Ébresztési proxy telepítési állapotának részletei

> [!TIP]
> Annak megállapítására, hogy működik-e az ébresztési proxy, tesztelje a kapcsolatot egy alvó számítógéphez. Például egy adott számítógépen lévő megosztott mappához csatlakoztassa, vagy próbáljon meg csatlakozni a számítógép távoli asztali kapcsolattal. Ha közvetlen hozzáférést, ellenőrizze, hogy az IPv6 előtagok működnek-e úgy, ugyanazokat a teszteket, amelyek jelenleg az interneten lévő alvó számítógépnél.

