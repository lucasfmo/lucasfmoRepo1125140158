---
title: "Helyek és hierarchiák alapjai |} Microsoft Docs"
description: "A System Center Configuration Manager-helyek és hierarchiák alapszintű adatainak beolvasása."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 68527c0e82861106b7ec28b34bffa8fd74b2dd4a
ms.openlocfilehash: f13f38be2a19ab8a1ead246e5272515dd0570984
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-sites-and-hierarchies-for-system-center-configuration-manager"></a>A System Center Configuration Manager helyeinek és hierarchiáinak alapjai

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager központi telepítés Active Directory-tartományban kell telepíteni. A központi telepítés foundation tartalmazza a helyek hierarchiáját alkotó egy vagy több Configuration Manager-helyek. Egyetlen helytől egészen a többhelyes hierarchiákig a telepített helyek típusa és elhelyezkedése szükség esetén biztosítja a telepítés vertikális méretezésének (bővítésének) a lehetőségét. Ezenkívül továbbítja a kulcsszolgáltatásokat a kezelt felhasználóknak és eszközöknek.

## <a name="hierarchies-of-sites"></a>Helyhierarchiák
Amikor először telepíti a System Center Configuration Manager, az első a Configuration Manager-hely telepítésekor meghatározza, hogy a hierarchia hatókörét. Az első Configuration Manager-hely fog kezelésére használt eszközök és felhasználók a vállalati alapját. Az első helynek központi adminisztrációs hely vagy önálló elsődleges helyet kell lennie.  

 A *központi adminisztrációs hely* nagyméretű telepítésekhez megfelelő, egy központi felügyeleti ponttal biztosít, és a globális hálózati infrastruktúrában elosztott eszközök támogatásához szükséges rugalmasságot biztosít. A központi adminisztrációs hely telepítése után szüksége lesz egy vagy több elsődleges helyet is gyermekhelyként telepítéséhez. Ez a konfiguráció szükség, mert a központi adminisztrációs hely nem támogatja közvetlenül az elsődleges hely funkciója eszközök kezeléséhez. A központi adminisztrációs hely támogatja a több gyermek elsődleges helyeken. A gyermek elsődleges helyeken használt eszközök közvetlen kezeléséhez, és a hálózati sávszélesség szabályozására, ha a kezelt eszközök földrajzilag különböző helyeken vannak.  

 A *önálló elsődleges hely* kisebb környezetekhez megfelelő, és további helyek telepítése nélkül eszközök kezelésére is használható. Bár az önálló elsődleges hely korlátozhatja a központi telepítés méretét, azt egy későbbi időpontban, egy új központi adminisztrációs hely telepítésével bővíti a hierarchiát esetet nem támogatják. A helybővítés az önálló elsődleges hely egy gyermek elsődleges hely válik, és telepítheti a további elsődleges gyermekhelyeket az új központi adminisztrációs hely alá. Ezután az első központi telepítésben a vállalat jövőbeli növekedésének megfelelően bővítheti.  

> [!TIP]  
>  Önálló elsődleges hely és egy elsődleges helyet is valóban a ugyanolyan típusú: elsődleges hely. A névkülönbség oka a központi adminisztrációs hely használata esetén létrejövő hierarchikus kapcsolat. Ez a hierarchikus kapcsolat korlátozhatja a telepítés bizonyos helyrendszerszerepkörök, amelyek a Configuration Manager funkcióihoz. Ez a korlátozás szerepkörök az oka, hogy egyes helyrendszer-szerepkörök csak a hierarchia legfelső szintű helyén, a központi adminisztrációs hely vagy önálló elsődleges hely telepíthető.  

 Az első hely telepítése után további helyeket telepíthet. Ha az első hely központi adminisztrációs helyet, majd telepítheti egy vagy több gyermek elsődleges helyeken. Az elsődleges hely (önálló vagy elsődleges gyermekhely) telepítése után telepíthet egy vagy több másodlagos helyet.  

 A *másodlagos helyek* csak gyermekhelyként telepíthetők egy elsődleges hely alatt. Ez a helytípus kibővíti az elsődleges helyek hatókörét az olyan helyeken lévő eszközök kezeléséhez, amelyek lassú hálózati kapcsolattal rendelkeznek az elsődleges helyhez. Annak ellenére, hogy a másodlagos hely az elsődleges hely bővítése, az elsődleges hely kezeli az összes ügyfél. A másodlagos hely támogatást biztosít a távoli helyen eszközökhöz. Támogatást biztosít által tömöríti és kezeli a hálózaton küldött adatokat (deploy) az ügyfelek számára, és, hogy az ügyfelek küldenek vissza a helyre.  

 Az alábbi diagramokon példákat láthat a helyek ezen kialakításaira.  

 ![Hierarchia példák](media/Hierarchy_examples.png)  

 További információ a következő témakörökben:  

-   [A System Center Configuration Manager bemutatása](../../core/understand/introduction.md)  

-   [Helyek hierarchiájának tervezése a System Center Configuration Managerhez](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)  

-   [System Center Configuration Manager-helyek telepítése](/sccm/core/servers/deploy/install/installing-sites)  

## <a name="site-system-servers-and-site-system-roles"></a>Helyrendszer-kiszolgálók és helyrendszerszerepkörök  
 Minden egyes Configuration Manager-hely telepítése *helyrendszer-szerepkörök* felügyeleti műveleteket támogató. A következő szerepkörök alapértelmezés szerint települnek a hely telepítésekor:

-   A helykiszolgáló szerepkör van hozzárendelve a hely telepítéséhez használt számítógépnek.

-   A Helyadatbázis-kiszolgáló szerepkör van hozzárendelve, amely a helyadatbázist tároló SQL Server.

Egyéb helyrendszerszerepkörök megadása nem kötelező, és csak használata, amikor a helyrendszerszerepkör aktív funkcióit használni kívánt. A helyrendszerszerepkört tartalmazó összes számítógép helyrendszer-kiszolgálónak tekintendő.  

 Kisebb üzemelő példánya a Configuration Manager előfordulhat, hogy először futtatja a hely összes helyrendszerszerepköröket a helykiszolgáló számítógépen közvetlenül. Ezt követően a felügyelt környezet és az igények növekedésével, további helyrendszer-szerepköröket működtető olyan növelje a hely hatékonyságát, a további eszközök számára szolgáltatásokat nyújtó további helyrendszer-kiszolgálók telepítése esetén.  

 A különböző helyrendszerszerepkörökkel kapcsolatos információkért lásd: [helyrendszer-szerepkörök](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) a [helyrendszer-kiszolgálók és helyrendszerszerepkörök tervezése a System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).

## <a name="publishing-site-information-to-active-directory-domain-services"></a>A helyinformációk közzététele az Active Directory tartományi szolgáltatásokban  
 Kezelés a Configuration Manager egyszerűsítése érdekében a Configuration Manager által használt részletes adatok támogatásához az Active Directory-séma kiterjesztése, és már rendelkezik a helyek közzétegyék a kulcsfontosságú adatokat az Active Directory tartományi szolgáltatásokban (AD DS). Majd a kezelni kívánt számítógépek biztonságosan beolvasható hellyel kapcsolatos információkat az AD DS megbízható forrásából. Az ügyfelek által lekérhető információk azonosítják az elérhető helyeket, a helyrendszer-kiszolgálókat és az adott helyrendszer-kiszolgálók által biztosított szolgáltatásokat.  

 *Az Active Directory-séma kiterjesztése* az egyes erdőkhöz csak egyszer történik, és előtt vagy után a Configuration Manager telepítése végezhető.   A séma kiterjesztésekor létre kell hoznia egy új Active Directory-tárolót minden olyan tartományban rendszerkezelési nevű. A tároló található ügyfelek számára adatokat közzétevő Configuration Manager-hely tartalmaz. További információkért lásd: [hely közzététele az Active Directory előkészítéséhez](../../core/plan-design/network/extend-the-active-directory-schema.md).  

 *Helyadatok közzététele* javítja a Configuration Manager-hierarchia biztonságát és csökkenti az adminisztratív terhelést, de nincs szükség az alapvető a Configuration Manager funkcióihoz.  

