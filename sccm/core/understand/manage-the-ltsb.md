---
title: "A LTSB kezelése |} Microsoft Docs"
description: "Felügyeleti különbségek a LTSB a System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8da2887a-fd8e-438c-b926-849c121f7fdf
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 9c6f349ead906532a7a58df74609de976769e251
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-the-long-term-servicing-branch-of-configuration-manager"></a>A hosszú távú karbantartási ág a Configuration Manager kezelése

*Vonatkozik: A System Center Configuration Manager (hosszú távú karbantartási ág)*

A hosszú távú karbantartási ág (LTSB) a System Center Configuration Manager használata esetén a következő azt segítenek megérteni, hogyan kezelheti az infrastruktúra érintő fontos változások.

Mivel a LTSB aktuális ág verziójával 1606 (például az Intune-nal és a felhőalapú szolgáltatásokkal kivétel) egyenértékű, használhatja a tervezési, telepítési, konfigurációs és napi felügyeleti feladatok többsége azonosak.

Például a LTSB használható a helyek, a helytípusok, az ügyfelek és a általános infrastruktúra száma azonos az aktuális ág. Ezért a hely és a hierarchiában található tervezési és kialakítási témakörök az aktuális ág útmutatás használhat. Hasonlóképpen a LTSB mindkét elágazásokat, például a szoftverfrissítéseket és az operációs rendszer központi telepítése által támogatott szolgáltatások használja a kikötésekkel nem is hozzáférhetnek az aktuális ág 1606 verzió után bevezetett szolgáltatás változások az aktuális ág dokumentáció szakaszt található útmutatást.

Az alábbi szakaszok információt nyújtanak készül kezelése, amelyek nincsenek hasonló feladatokat.

## <a name="updates-and-servicing"></a>Frissítések és karbantartás
Csak a kritikus fontosságú biztonsági frissítéseket a LTSB érhető el, a konzolon belüli frissítések történnek.  

Az aktuális ág későbbi rendszeres frissítésével kapcsolatos információkat a konzolon látható, de nem érhetik el a LTSB. Azok a rendszer nem tölti le, és nem lehet telepíteni.

Kritikus biztonsági javítások támogatásához a konzolon belüli frissítések, egy LTSB hely használatát igényli [a szolgáltatáskapcsolódási pont](/sccm/core/servers/deploy/configure/about-the-service-connection-point). Az aktuális ág megtörtént az e helyrendszerszerepkör konfigurálható online vagy offline módban. A LTSB gyűjt, és az aktuális ág ugyanazokat az telemetriai és használati adatokat küldi el.

A LTSB a gyorsjavítás-telepítő és a frissítés Frissítésregisztráló eszköz használatát támogatja, az aktuális ág leírtak szerint.

Frissítések és karbantartás kapcsolatos általános információkért lásd: [frissítések a Configuration Manager](/sccm/core/servers/manage/updates).


## <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>Módosítások történtek a hely bővítése és a CD-n. Legújabb mappa
Amikor futtatja a LTSB és egy önálló elsődleges helyet egy új központi adminisztrációs hely telepítésével bővíti, telepítő és a verzió 1606 alapterv adathordozóról forrásfájlokat kell használnia. Az aktuális ág futtassa a telepítőt, és a CD-ről forrásfájlok segítségével. Legfrissebb mappát.

Bár nem futtathatja a telepítő a hely kibővítése a CD-ről. Legfrissebb mappát, továbbra is a CD-ről. Legfrissebb mappát a site recovery, és új gyermek elsődleges hely telepítésekor, ha az első LTSB hely egy központi adminisztrációs helyhez volt.

További információ a hely bővítése: [kibővít egy önálló elsődleges helyet](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site). További információ a CD-n. Legfrissebb mappát, lásd: [a CD-ről. Legújabb mappa](/sccm/core/servers/manage/the-cd.latest-folder).


## <a name="recovery"></a>Helyreállítás
Amikor helyreállít egy helyet, vissza kell állítania a hely vagy a Helyadatbázis az eredeti ág. Nem lehet helyreállítani az aktuális ág Helyadatbázis LTSB verzióra, vagy fordítva.

