---
title: "A Windows szolgáltatás |} Microsoft Docs"
description: "A szolgáltatási segítségével szabályozhatja a frissítések telepítésekor a System Center Configuration Manager-helyek."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca4886d4-7173-46be-8dcd-1657d5b0deb9
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d0735c170820259ac8bb6706aac7cc5569a1628
ms.openlocfilehash: d06a2a955ff59fa84bb844033fe31874fc735087
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
#  <a name="service-windows-for-site-servers"></a>Szolgáltatási időkeretek Helykiszolgálók számára

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A központi adminisztrációs helyek és az elsődleges helyeken vezérlőhöz szolgáltatás windows konfigurálhatja, ha a konzolon belüli frissítések telepítheti.  Beállíthatja, hogy a több windows helykiszolgálóra vonatkozó összes szolgáltatás windows kombinációja határozza meg a frissítések telepítése időkeretet.

Ha a nem szolgáltatási időkeretet van konfigurálva:
- **A legfelső szintű helyen** (egy központi adminisztrációs hely vagy önálló elsődleges helyen) úgy dönt, hogy mikor kell a frissítés telepítésének elindítása.
- **Egy elsődleges helyen**, a frissítés automatikusan telepíti a frissítést a központi adminisztrációs hely telepítésének befejezése után.
- **Egy másodlagos helyen**, frissítések soha nem indul el automatikusan. Ehelyett manuálisan kell elindítani a frissítés telepítésének a konzolról, ha a szülő elsődleges hely a frissítés telepítve van.

Amikor szolgáltatási időkeretet konfigurálni:
- **A legfelső szintű helyen**, nem lesz a Configuration Manager konzolon belül bármely új frissítést a telepítés elindításához. Még a szolgáltatási időkeretet konfigurálni a hely automatikusan letölti a frissítéseket, azok készen állnak a telepítésre.  
- **Egy elsődleges helyen**, egy központi adminisztrációs helyen telepített frissítések töltse le az elsődleges helyre, de nem automatikusan start. Fel blokkolja a szolgáltatási időkeretre használatát egy frissítést a telepítés indítása sikertelen. Egyszerre szolgáltatás windows már nem a blokk frissítésére, telepítés a frissítés telepítése automatikusan elindul.
- **A másodlagos helyek** nem támogatják a windows szolgáltatás, és nem telepíti automatikusan a frissítéseket. A másodlagos hely az elsődleges szülőhely frissítés telepítése után megkezdheti a konzol a másodlagos hely frissítése.

## <a name="to-configure-a-service-window"></a>A szolgáltatási időkeret konfigurálása

1.  Nyissa meg a Configuration Manager konzolon **felügyeleti** > **Helykonfiguráció** > **helyek**, majd válassza ki a helykiszolgáló, ahol a szolgáltatási időkeretet konfigurálni szeretné.  

2.  Ezután nyissa meg a helykiszolgáló **Tulajdonságok** menüjét, ahol a **Szolgáltatási időkeret** lapon egy vagy több szolgáltatási időkeretet is megadhat az adott helykiszolgálóhoz.  

