---
title: "Használhatja a kiterjesztett együttműködés az aktuális ág |} Microsoft Docs"
description: "További tudnivalók az ügyfél a a hosszú távú karbantartási ág a Configuration Manager aktuális ágának hellyel rendelkező használatával."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: 0
author: robstackmsft
ms.author: robstack
Robots: NOINDEX,NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 4cc339e28110a3097c318b61224ae7692c47a31a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="use-the-client-software-from-the-version-1606-baseline-media-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>A kliensszoftver a verzió 1606 alapszintű verziót tartalmazó adathordozó használja az aktuális ág webhely a későbbi verzióiban kiterjesztett való

*Vonatkozik: A System Center Configuration Manager (aktuális ág), (hosszú távú karbantartási ág)*  

Használhatja a Configuration Manager ügyfélszoftver Windows rendszerű számítógépek (client.msi) a verzió 1606 alapterv adathordozóról DVD kapott a System Center 2016 vagy az egy vagy a System Center Configuration Manager (aktuális ág és hosszú távú karbantartási ág 1606) kiadása aktuális ág helyhez tartozó eszközök kezeléséhez. Ez az ügyfél a kiterjesztett együttműködési ügyfél neve.

## <a name="how-this-scenario-works"></a>Ebben a forgatókönyvben működése:
Általában az az aktuális ág egy új konzolon belüli frissítés telepítésekor ügyfelek automatikusan frissíti az ügyfélszoftvert, hogy használhassák az említett új szolgáltatásokat.

Az ebben az esetben használja az aktuális ág, és az új szolgáltatásokat és a frissítések kap. A legtöbb ügyfelek az aktuális ág futtassa az ügyfélszoftvert, és is frissíti a ügyfélszoftvert minden verzióra frissítés telepítése. Azonban egy olyan részhalmazán, amely nem szeretne kapni a kliensszoftver-frissítések, kritikus rendszerek, a kiterjesztett együttműködési ügyfél telepítése. Ezek az ügyfelek nem új ügyfélszoftvert telepíti, amíg hozzájuk explicit módon telepítheti az ügyfélszoftver új verzióját.

További információ az automatikus frissítés a Configuration Manager új verziójának telepítésekor az aktuális ág ügyfelek megakadályozása 1610 aktuális ág verziójával használható.

Az aktuális ág hely 1606 vagy újabb verzióját kell futtatnia.

## <a name="the-extended-interoperability-client-software"></a>A kiterjesztett együttműködési ügyfélszoftver
Használhatja a kiterjesztett együttműködés a System Center 2016 vagy a System Center Configuration Manager (aktuális ág és hosszú távú karbantartási ág 1606) kiadása ügyfél aktuális ág hellyel rendelkező, két év után a kiadás, amely 2016. október 12. a általános rendelkezésre állását az ügyfél használata támogatott.

Tervezze meg a kiterjesztett együttműködési ügyfél az aktuális ág támogatási előtt az ügyfél lejár a felügyelt eszközök frissítéséhez. Így az ügyfél új verziójának letöltése a Microsoft és a frissített ügyfél szoftver telepítését az eszközökön, amelyek az aktuális kiterjesztett együttműködési ügyfél.

**A kiterjesztett együttműködési ügyfél korlátozások:**
-     A kiterjesztett együttműködési kliens szoftver frissítései nem érhetők el a konzolon belüli frissítések segítségével. További részletek a frissített ügyfélszoftvert adja meg egy frissített ügyfelet kiadásakor.

## <a name="identify-the-client-version-you-use"></a>Az ügyfél verzióját használja azonosítása
Az alábbiakban a fő ügyfél-verziónkénti aktuális ág és LTSB is elérhető:

|Ügyfél verziója|Ágak és -verzió |  
|----------------|---------------------|
|5.00.8325.xxxx |    -Aktuális ága 1511-es|
|5.00.8355.xxxx    |-Aktuális ág 1602-es|
|5.00.8412.1307    |-Aktuális ág 1606 </br> -Aktuális ág 1606 a 1606 gyorsjavítás összesítő (KB3186654)</br>-a verzió 1606 alapterv adathordozóról kiterjesztett együttműködési ügyfél|  

Az ügyfél megtekintheti az ügyfél verziója a **általános** a Configuration Manager Vezérlőpulton található kisalkalmazásával lapján.

Az a **összetevők** lapon, a kisalkalmazásával, néhány összetevőt különböző értékek megjelenítése. Például egy ügyfél verziójához 8412.1307, néhány összetevőt is szerepelhet, 5.00.8412. **1000** vagy 5.00.8412. **1006**.  Különbözik-e ez az utolsó négy számjegye néhány összetevőt nem jelent problémát, és nem jelent frissítése sikertelen. az összetevő a jelenlegi ügyfélverzióról való.

