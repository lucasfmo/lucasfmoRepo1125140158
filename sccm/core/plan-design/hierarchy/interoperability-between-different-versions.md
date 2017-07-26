---
title: "Együttműködés a Configuration Manager verziói között |} Microsoft Docs"
description: "Megtudhatja, hogyan ugyanazon a hálózaton lévő több System Center Configuration Manager-hierarchia közötti ütközések elkerülése érdekében."
ms.custom: na
ms.date: 1/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 28593d271603ff9775425327996d844d7ed358cd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="interoperability-between-different-versions-of-system-center-configuration-manager"></a>Együttműködés a System Center Configuration Manager különböző verziói között

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Telepítéséhez és működtetéséhez több független hierarchiákat a System Center Configuration Manager ugyanazon a hálózaton. Azonban a Configuration Manager különböző hierarchiái nem működnek együtt az áttelepítési folyamat kívül, mert mindegyik hierarchia kell állítani, közöttük ütközések elkerülése érdekében. Ezenkívül létrehozhat adott konfigurációval elérheti az Ön által kezelt erőforrások kommunikálni a helyrendszerekkel, a megfelelő hierarchiából.  

 A következő szakaszok ismertetik a Configuration Manager különböző verzióinak használatát egy hálózaton:  

-   [Együttműködés a System Center Configuration Manager és a termék korábbi verziói között](#BKMK_SupConfigInterop)  

-   [Együttműködés a Configuration Manager konzollal](#BKMK_ConsoleInterop)  

-   [A Configuration Manager korlátozásai vegyes verziójú hierarchiákban](#bkmk_mixed)  

##  <a name="BKMK_SupConfigInterop"></a> Együttműködés a System Center Configuration Manager és a termék korábbi verziói között  
 Különböző verziójú helyek nem szerepelhet egyszerre a(z) ugyanabba a hierarchiába tartozik, kivéve a System Center 2012 Configuration Manager a System Center Configuration Manager vagy egy újabb verzióra (konzolon belüli frissítések) egy System Center Configuration Manager verzióra a frissítési folyamat során.   

 Mivel központilag telepítheti a System Center Configuration Manager hely- és hierarchia-párhuzamos meglévő System Center 2012 Configuration Manager-hely vagy hierarchia, azt javasoljuk, hogy azt tervezi, hogy bármely verziójú ügyfelek egy akadályozzák a verziójáról a helyhez való csatlakozást.

Például, ha két vagy több Configuration Manager-hierarchia határai átfedésben vannak (lásd: [egymással átfedésben lévő határok](/sccm/core/servers/deploy/configure/boundary-groups#overlapping-boundaries)), amelyek tartalmazzák az azonos hálózati helyet, az ajánlott eljárás minden új ügyfél hozzárendelése automatikus helyhozzárendelés használata helyett egy adott helyhez. A System Center 2012 Configuration Manager automatikus helyhozzárendelés kapcsolatos információkért lásd: [ügyfelek hozzárendelése a System Center Configuration Manager hely](../../../core/clients/deploy/assign-clients-to-a-site.md).  

 Emellett a System Center Configuration Managerből származó helyrendszerszerepkört üzemeltető számítógépen a System Center 2012 Configuration Manager ügyfél nem telepíthet, és nem is telepítése a System Center Configuration Manager-ügyfél egy olyan helyrendszerszerepkör, a System Center 2012 Configuration Manager üzemeltető számítógépen.  

 Hasonlóképpen, a következő ügyfelek és a következő virtuális magánhálózati (VPN) kapcsolat nem támogatottak:  

-   A System Center 2012 Configuration Manager vagy a korábbi verziójú ügyfél  

-   A System Center 2012 Configuration Manager vagy korábbi eszközfelügyeleti ügyfél  

-   Windows CE Platform Builder eszközfelügyeleti ügyfél (bármilyen verzió)  

-   System Center Mobile Device Manager VPN-kapcsolat  

###  <a name="BKMK_SupConfigSiteAssignment"></a> Az ügyfelek helyhozzárendelésének szempontjai  
 A System Center Configuration Manager-ügyfelek csak egyetlen elsődleges helyet is hozzárendelhető. Ha automatikus helyhozzárendelést használnak az ügyfelek helyhez rendelésére az ügyféltelepítés során, és több határcsoport tartalmazza ugyanazt a határt, valamint eltérő helyek vannak hozzárendelve az egyes határcsoportokhoz, akkor egy ügyfél konkrét helyhozzárendelése előre nem meghatározható.  

 Ha több Configuration Manager-helyek és hierarchiák határai átfedésben vannak, az ügyfelek előfordulhat, hogy nem kell a helyhez hozzárendelt várható, vagy egyáltalán nem lesznek hozzárendelve helyhez egyáltalán.  

 A System Center Configuration Manager-ügyfelek a Configuration Manager-hely verziójának ellenőrzése előtt végzik a helyhozzárendelést, és nem rendelhető hozzá egy korábbi verziót, amikor, és ha a hely határai átfedésben vannak. Azonban a System Center 2012 Configuration Manager ügyfelek helytelenül hozzárendelni a System Center Configuration Manager-hely.  

 Megakadályozza a felhasználókat hozzárendelésének a nem megfelelő helyhez, amikor két hierarchia határai átfedésben vannak, azt javasoljuk, hogy konfigurálja-e egy adott helyhez rendelése a Configuration Manager ügyfél telepítési paramétereit.  

##  <a name="bkmk_mixed"></a>A Configuration Manager korlátozásai vegyes verziójú hierarchiában  
 Amikor a System Center Configuration Manager-hely frissítésének folyamata, vannak olyan helyzetek, amikor különböző helyek különböző verziói működnek. Előfordulhat például, hogy egy új verzióra frissít egy központi adminisztrációs helyet, de a hely karbantartási időszakai miatt egy vagy több elsődleges hely esetleg csak egy későbbi dátumon és időpontban frissül.  

 Bizonyos funkciók nem érhetőek el, ha egy adott hierarchia különböző helyei eltérő verziókat használnak. Ez hatással lehet a Configuration Manager konzolon a Configuration Manager-objektumok kezelése, és melyik szolgáltatás működik, az ügyfelek számára. A Configuration Manager újabb verziója funkciói általában nem érhető el helyeken vagy ügyfeleknél, amelyek egy alacsonyabb verziójú szervizcsomaggal működnek.  

### <a name="limitations-when-upgrading--configuration-manager"></a>Korlátozások a Configuration Manager frissítéskor  

|Objektum|Részletek|  
|------------|-------------|  
|Hálózatelérési fiók|**Ha a System Center 2012 Configuration Manager frissítése System Center Configuration Manager:** A hálózatelérési fiók adatainak frissített a System Center Configuration Manager központi adminisztrációs helyhez csatlakozó Configuration Manager konzolon való megtekintésekor a konzol nem jeleníti meg, hogy a System Center 2012 Configuration Manager futtató elsődleges helyeken konfigurált fiókok adatait. Miután az elsődleges hely a központi adminisztrációs hely verziójával megegyező verzióra frissít, a fiók részletei láthatók a a konzolon.<br /><br /> **Ha a verziófrissítést a System Center Configuration Manager verziói között:** Amikor a hálózatelérési fiók adatainak a System Center Configuration Manager új verzióra frissített központi adminisztrációs helyhez kapcsolódó Configuration Manager konzolról, a konzol nem jeleníti meg, amely a korábbi verziót futtató elsődleges helyeken konfigurált fiókok adatait. Miután az elsődleges hely a központi adminisztrációs hely verziójával megegyező verzióra frissít, a fiók részletei láthatók a a konzolon.|  
|Rendszerindító lemezképek az operációs rendszerek központi telepítéséhez|**Ha a System Center 2012 Configuration Manager frissítése System Center Configuration Manager:**  Amikor egy hierarchia legfelső szintű helyét frissíti a System Center Configuration Manager, az alapértelmezett rendszerindító lemezképek automatikusan frissülnek a rendszerindító lemezképekbe készült Windows Assessment and Deployment Kit 10 (Windows ADK) alapján. Használja a következő rendszerindító lemezképekbe csak a System Center Configuration Manager-helyeken lévő ügyfelek központi telepítésére. További információk: [Az operációs rendszer központi telepítésének tervezése a System Center Configuration Managerben](../../../osd/plan-design/planning-for-operating-system-deployment-interoperability.md).<br /><br /> **Ha a verziófrissítést a System Center Configuration Manager verziói között:** Mindaddig, amíg cm6long új verziói nem frissíti, amely használatban van a Windows ADK-verziót, nincs nincs hatással a rendszerindító lemezképeket.|  
|Új feladatütemezési lépések|Amikor olyan feladatütemezést hoz létre egy Configuration Manager verziója, amely nem érhető el egy korábbi verziójában bevezetett lépéssel, a következő problémák léphetnek fel:<br /><br /> – Hiba lép fel, szerkesztheti a feladatütemezést, amely a Configuration Manager korábbi verziója fut. a hely megkísérlésekor.<br /><br /> – A feladatütemezés nem fut a Configuration Manager-ügyfél korábbi verzióját futtató számítógépen.|  
|Ügyfél az alsó szintű felügyeleti pont kommunikációja|A Configuration Manager-ügyfél egy korábbi verziójú, mint az ügyfél futtató helyen lévő felügyeleti ponttal kommunikáló csak használható funkciókat, amelyeket a Configuration Manager régebbi verziója támogat. Például ha telepít tartalmat egy ügyfélre, mely egy, az adott verzióra még nem frissített felügyeleti ponttal kommunikál a közelmúltban frissítették a System Center Configuration Manager-hellyel, hogy az ügyfél nem használhatja a legújabb verzió új funkcióit.|  

##  <a name="BKMK_ConsoleInterop"></a>Együttműködés a Configuration Manager konzol  
 A következő táblázat a Configuration Manager verzióit vegyesen használó környezetben a Configuration Manager konzol használatával kapcsolatos információt tartalmazza.  

|Együttműködési környezet|További információ|  
|----------------------------------|----------------------|  
|A System Center 2012 Configuration Manager és a System Center Configuration Manager tartalmazó környezet|Configuration Manager-hely kezeléséhez, a konzol és a konzol csatlakozik a helyhez is kell futtatnia a Configuration Manager azonos verzióját. Például nem használható a System Center 2012 Configuration Manager konzol a System Center Configuration Manager-hely kezeléséhez, vagy fordítva.<br /><br /> A System Center 2012 Configuration Manager konzol és a System Center Configuration Manager konzol telepítéséhez ugyanazon a számítógépen nem támogatott.|  
|A System Center Configuration Manager többféle verzióját tartalmazó környezet|A System Center Configuration Manager nem támogatja a több mint egy számítógépen egyetlen Configuration Manager konzol telepítése. A System Center Configuration Manager különböző verzióihoz való több konzolok használatához telepítenie kell az egyes konzolokat ugyanarra a gépre.<br /><br /> Egy új verzióra történő frissítése a hierarchiában lévő helyek folyamata közben csatlakoztathat egy konzolt egy újabb verziójával és az információk megjelenítése, hogy a hierarchiában lévő többi hely futtató helyhez. Ez a konfiguráció azonban nem ajánlott, mivel előfordulhat, hogy a konzol verziója és a Configuration Manager hely verziója közötti különbségek adatproblémákat okoznak is, és elérhető a legújabb termékverzióra frissítve néhány funkció nem lesz elérhető a konzolon. <br />< /br / > a hely kezeléséhez, a konzol használatakor olyan verzióra, amely nem egyezik meg a hely verziója nem támogatott. Ezzel az adatok elveszhetnek, és kockáztatja a webhely biztonságát. Például nem támogatott verziójából 1610 konzol használatát a 1606 verziót futtató helyen kezelheti. |

