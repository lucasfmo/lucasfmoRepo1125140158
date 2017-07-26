---
title: "A Helyhierarchia - Configuration Manager kialakítása |} Microsoft Docs"
description: "Ismerje meg a rendelkezésre álló topológiákat és a System Center Configuration Manager kezelési lehetőségek, így megtervezheti a hely hierarchiáját."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
caps.latest.revision: 22
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 35e48666f4d1a2363304650f960531fd0630a291
ms.openlocfilehash: e346e83b0ae0dc7a612cef7a7b9fb1fdb42236bc
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="design-a-hierarchy-of-sites-for-system-center-configuration-manager"></a>Helyek hierarchiájának tervezése a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager új hierarchia első helyének telepítéséhez tanácsos megértéséhez a rendelkezésre álló topológiák Configuration Manager, az elérhető helyeket típusú és egymással a kapcsolatok és egyes helytípusokra biztosító kezelési hatókörét.
Ezután után tartalomkezelési lehetőségeket, így csökkentheti a telepítenie kell a helyek számát figyelembe véve, megtervezheti a topológia, amely hatékonyan szolgál. az aktuális üzleti igényeknek megfelelően, és később kiterjesztheti az jövőbeli növekedésének kezelése.  

> [!NOTE]
> Egy új Configuration Manager telepítésének megtervezésekor vegye figyelembe a [kibocsátási megjegyzéseket]( /sccm/core/servers/deploy/install/release-notes), amely részletesen aktív verziókban aktuális problémák. A kibocsátási megjegyzések a Configuration Manager minden ág vonatkozik.  Azonban ha használja a [Technical Preview fiókirodai]( /sccm/core/get-started/technical-preview), található problémák csak a fiókirodában jellemző a Technical Preview egyes verziójának a dokumentációjában.  

##  <a name="bkmk_topology"></a>Hierarchiatopológia  
 Hierarchia topológiák közé egyetlen önálló elsődleges helyhez csatlakoztatott elsődleges és másodlagos helyek a központi adminisztrációs hely a hierarchia legfelső szintű (legfelső rétegében) helyen csoportja számára.   A típus a legfontosabb szempont a hierarchiában használt helyek száma pedig általában számát és típusát az eszközök kell támogatnia, az alábbiak szerint:   

 **Önálló elsődleges hely:** Önálló elsődleges helyet használja, ha egyetlen elsődleges hely támogathatja az összes, az eszközök és felhasználók kezelése (lásd: [méretezés és skálázási számok](/sccm/core/plan-design/configs/size-and-scale-numbers)). Ez a topológia akkor is sikeres, ha a vállalat különböző földrajzi helyeket sikeresen kiszolgálta egyetlen elsődleges hely.  Hálózati forgalom kezeléséhez, használhatja az előnyben részesített felügyeleti pontok és a tartalmi infrastruktúra alapos megtervezésével (lásd: [a System Center Configuration Manager tartalomkezelésének alapvető fogalmai](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)).  

 A topológia az alábbi előnyöket biztosítja:  

-   Egyszerűbb adminisztratív terhelést.  

-   Egyszerűsített hozzárendelése és a rendelkezésre álló erőforrások és szolgáltatások felderítése.  

-   A helyek közötti adatbázis-replikáció útján bevezetett lehetséges lag eltávolítása.

-   Egy önálló elsődleges hierarchia központi adminisztrációs hellyel rendelkező nagyobb hierarchiává bontsa beállítás. Ez lehetővé teszi később új elsődleges helyek telepítését a központi telepítés kibővítéséhez.  


**Egy vagy több gyermek elsődleges hely központi adminisztrációs hely:** Ez a topológia akkor használja, ha egynél több elsődleges helyet, az eszközök és felhasználók felügyeletének támogatásához szükséges.  Ez szükséges akkor, ha több, mint amennyit egyetlen elsődleges hely használni kell. A topológia az alábbi előnyöket biztosítja:  


-   Akár 25 elsődleges helyet, amelyek lehetővé teszik, hogy a hierarchia kibővítését támogatja.  

-   A központi adminisztrációs hely mindig (kivéve, ha a hely újratelepítését) fogja használni. Ez a beállítás állandó. A gyermek elsődleges helyek abba, hogy önálló elsődleges hely nem választható le.

 Az alábbi szakaszok segítségével jobban megértheti, hogy mikor használjon egy adott hely- vagy tartalomkezelési beállítást, és ne egy további helyet.  

##  <a name="BKMK_ChooseCAS"></a>Mikor használjon központi adminisztrációs hely  
 Egész hierarchiára vonatkozó beállítások konfigurálása és figyelheti az összes webhelyről és a hierarchiában lévő objektumok a központi adminisztrációs hely. Ez a helytípus nem közvetlenül felügyeli az ügyfeleket, hanem összehangolja a helyek közötti adatreplikálás, helyek és a hierarchián belüli ügyfelek konfigurációit is beleértve.  

**A következő információk segítségével eldöntheti, hogy mikor telepítsen központi adminisztrációs hely:**  

-   A központi adminisztrációs hely a hierarchia legfelső szintű hely.  

-   Ha olyan hierarchiát, amelyben több elsődleges hely van, egy központi adminisztrációs helyet kell telepítenie és kell lennie az első hely telepítésekor.  

-   A központi adminisztrációs hely gyermekhelyei csak elsődleges helyek lehetnek.  

-   A központi adminisztrációs helyhez nem rendelhetők ügyfelek lehet.  

-   A központi adminisztrációs hely nem támogatja az ügyfelek, például a felügyeleti pontok és terjesztési pontok közvetlenül támogató helyrendszerszerepköröket.  

-   A hierarchiában található összes ügyfelet felügyelheti, és helykezelési tevékenységeket végezhet bármelyik gyermekhelyre vonatkozóan a központi adminisztrációs helyhez kapcsolódó Configuration Manager-konzol használata esetén. Ez magában foglalhatja felügyeleti pontok vagy más helyrendszerszerepköröket, az alárendelt elsődleges vagy másodlagos hely telepítését.  

-   Ha rendelkezik központi adminisztrációs hellyel, ez a hely az egyetlen, ahol a hierarchiához tartozó összes hely adatai megtekinthetők. Ezek az adatok tartoznak a szoftverleltár és az állapotüzeneteket.  

-   Társítja a futtatandó az egyes helyeken felderítési módszereket konfigurálhatja a központi adminisztrációs helyről a hierarchián belüli felderítési műveleteket.  

-   A hierarchia biztonságának felügyelete érdekében különböző biztonsági szerepköröket, biztonsági hatóköröket és gyűjteményeket társíthat az egyes rendszergazda felhasználókhoz. Ezek a beállítások a hierarchia minden helyére érvényesek.  

-   A fájlreplikáció és az adatbázis-replikáció konfigurálásával szabályozhatja a helyek közti kommunikációt a hierarchián belül. Például ütemezheti a helyadatok adatbázis-replikáció, és felügyelheti a sávszélességet a helyek közötti fájlalapú adatok átviteléhez.  

##  <a name="BKMK_ChoosePriimary"></a>Mikor használjon elsődleges hely  
 Az elsődleges helyek ügyfelek kezelésére szolgálnak. Az elsődleges hely telepíthető gyermekhelyként (egy központi adminisztrációs hely alá) vagy egy új hierarchia első helyeként. Egy elsődleges hely egy hierarchia első helyének telepített egy önálló elsődleges helyet hoz létre. A gyermek elsődleges helyek, mind az önálló elsődleges helyek támogatják a másodlagos helyek az elsődleges hely alárendelt helyein.  

 Az alábbi okokból érdemes elsődleges helyet használni:  

-   Az eszközök és felhasználók kezeléséhez.  

-   Az eszközöket szeretne felügyelni egy hierarchián számának növeléséhez.  

-   Egy további csatlakozási pontra van biztosít a felügyeleti, a telepítés.  

-   A szervezet felügyeleti követelményeinek kielégítése érdekében. Például azzal a céllal telepíthet egy elsődleges hely kezeléséhez a telepítési tartalom átvitelét egy kis sávszélességű hálózaton keresztül egy távoli helyen. Azonban a System Center Configuration Managerrel, segítségével beállítások hálózati sávszélesség használatának szabályozása, egy terjesztési pontra történő adatátvitel során. A tartalomkezelési képesség szükségtelenné teheti további helyek telepítésekor.  


**A következő információk segítségével eldöntheti, hogy mikor telepítsen elsődleges helyet:**  

-   Az elsődleges hely lehet önálló elsődleges hely vagy egy nagyobb hierarchia elsődleges gyermekhelyet. Ha az elsődleges hely egy központi adminisztrációs hellyel rendelkező hierarchia része, adatbázis-replikálás útján történik az adatok többszörözése a helyek között. Kivéve, ha több ügyfelet támogatásához szükséges, és az eszközök, mint amennyit egyetlen elsődleges hely támogathat, fontolja meg egy önálló elsődleges hely telepítése.  Önálló elsődleges hely telepítése után azt, hogy egy új központi adminisztrációs hely méretezést kívánó a központi telepítés bővítheti.  

-   Az elsődleges hely csak a központi adminisztrációs hely támogatja a szülőhely között.  

-   Az elsődleges hely gyermekei csak másodlagos helyek gyermekhelyei, és több másodlagos gyermekhelyet is is tud kezelni.  

-   Elsődleges helyek feladata, hogy feldolgozzák a hozzájuk rendelt ügyfelektől származó összes ügyféladatot találhatók.  

-   Elsődleges helyek adatbázis-replikáció útján kommunikálnak közvetlenül a központi adminisztrációs hellyel (amelyet automatikusan állít be egy új hely telepítésekor) használják.  

##  <a name="BKMK_ChooseSecondary"></a>Mikor használjon másodlagos helyet  
 A másodlagos helyek használatával alacsony sávszélességű hálózatokon keresztül a központi telepítési tartalmak és ügyféladatok adatok kezeléséhez.  

 A másodlagos helyek a központi adminisztrációs hely vagy a másodlagos hely közvetlen elsődleges szülőhelyéről kezelheti. Másodlagos helyeket egy elsődleges helyhez kell csatolni, és nem helyezhető át egy másik szülőhely gyermekhelyeként és majd újból telepíteni kell őket az új elsődleges hely alatti alárendelt helyként nélkül.

Azonban Ön közötti tartalomtovábbítás segítségével két másodlagos társhely kezeléséhez a telepítési tartalom fájlalapú replikálását. Ügyfél adatok átviteléhez az elsődleges helyhez, a másodlagos hely fájlalapú replikációt használ. A másodlagos hely adatbázis-replikációt is használ az elsődleges szülőhellyel folytatott kommunikációhoz.  

 Az alábbi esetekben érdemes másodlagos helyet telepíteni:  

-   A rendszergazda felhasználó egy helyi csatlakozási pontra nincs szükség.  

-   A telepítési tartalom átvitelét a hierarchia alacsonyabb szintjén levő helyek kell kezelni.  

-   A hierarchiában magasabban levő helyeknek küldött ügyfél-információkat kell kezelni.  

 Ha nem szeretne másodlagos helyet telepíteni, és vannak távoli helyeken levő ügyfelei, használhatja a Windows BranchCache szolgáltatást, vagy telepíthet olyan terjesztési pontokat, amelyek alkalmasak a sávszélesség-szabályozásra és az ütemezésre. A tartalomkezelési lehetőségeket használhatja, vagy a másodlagos helyek nélkül, és segíthetnek, hogy kevesebb helyre és kiszolgálóra kell telepítenie. További információ a Configuration Manager tartalomkezelési lehetőségeiről: [határozza meg, mikor érdemes tartalomkezelési lehetőségeket használni](#BKMK_ChooseSecondaryorDP).  


**A következő információk segítségével eldöntheti, hogy mikor telepítsen másodlagos helyet:**  

-   A másodlagos helyek automatikusan telepíti az SQL Server Express telepítése során Ha nem érhető el az SQL Server helyi példányát.  

-   Másodlagos hely telepítéséhez a Configuration Manager konzol telepítő közvetlenül a számítógépen futó helyett kezdeményezni.  

-   A másodlagos helyek az adatokat egy részhalmazát használják, a helyadatbázisban, amely csökkenti az adatbázis-replikáció a szülő elsődleges hely és a másodlagos hely között replikált adatok mennyiségét.  

-   Másodlagos hely továbbítani a fájlalapú tartalmat a többi másodlagos helynek, amelyek egy közös szülő elsődleges hely.  

-   Másodlagos hely telepítésekor automatikusan telepít egy felügyeleti és terjesztési pontot a másodlagos helykiszolgálón.  

##  <a name="BKMK_ChooseSecondaryorDP"></a>Határozza meg, mikor érdemes tartalomkezelési lehetőségeket használni  
 Távoli hálózati helyeken található ügyfelek esetén célszerűbb lehet igénybe venni a tartalomkezelési lehetőségeket ahelyett, hogy egy elsődleges vagy másodlagos helyet telepítene. Többnyire nincs is szükség hely telepítésére használja a Windows BranchCache szolgáltatást, beállítja a sávszélesség-szabályozást a terjesztési pontokon, vagy manuálisan másolja a tartalmat a terjesztési pontokra (előkészített tartalom).  


**Vegye figyelembe az alábbi feltételek bármelyike egy újabb hely telepítése helyett terjesztési pontot:**  

-   A hálózat sávszélessége elegendő az ügyfélszámítógépek kommunikálni egy felügyeleti pontot, és letöltik az ügyfélházirendet, elküldhessék a leltárt, az állapotjelentést és a felderítési adatokat a távoli helyen.  

-   Háttérben futó intelligens átviteli szolgáltatás (BITS) nem biztosítanak elegendő sávszélesség-szabályozást a hálózati követelmények teljesítéséhez.  

 A Configuration Manager tartalomkezelési lehetőségeket kapcsolatos további információkért lásd: [a System Center Configuration Manager tartalomkezelésének alapvető fogalmai](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

##  <a name="bkmk_beyond"></a>Hierarchiatopológia túl  
 Egy kezdeti hierarchia topológia mellett fontolja meg, mely szolgáltatások vagy funkciók lesznek elérhetők a különböző helyeken lévő a hierarchia (helyrendszer-szerepkörök), és hogyan az egész hierarchiára vonatkozó konfigurációk és képességek az infrastruktúra fogja kezelni. A következő általános szempontok külön témakörök ismertetnek. Ezek fontosak, mivel befolyásolhatják, vagy a hierarchia tervezését várhatóan:  

-   Ha tervezi [felügyeli a számítógépeket és eszközöket a System Center Configuration Managerrel](/sccm/core/clients/manage/manage-clients), vegye figyelembe, hogy az Ön által kezelt eszközök a helyszínen, a felhőben, vagy felhasználó által birtokolt eszközök (BYOD).  Emellett vegye figyelembe, hogyan kezelni kívánt eszközöket, amelyek több felügyeleti beállítások, például közvetlenül a Configuration Manager által kezelt Windows 10-számítógépeket támogatja, vagy ha integráció a Microsoft Intune-nal.  

-   Milyen hatással van a rendelkezésre álló hálózati infrastruktúra az távoli helyek közötti adatáramlásra megértéséhez (lásd: [a hálózati környezet előkészítése a System Center Configuration Manager](/sccm/core/plan-design/network/configure-firewalls-ports-domains)). Is gondolja át, ahol a felhasználók és a kezelt eszközökre telepített találhatók földrajzilag, és hogy az infrastruktúra hozzáféréskor a vállalati tartományhoz, vagy az interneten keresztül.  

-   Kezelheti a történő hatékony terjesztéséhez (fájlok és alkalmazások) központilag telepített adatok eszközök tartalomtárolású infrastruktúra tervezése (lásd: [tartalom és tartalomkezelési infrastruktúra kezelése a System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)).  

-   Meghatározza, melyik [funkciók és képességek a System Center Configuration Manager](../../../core/plan-design/changes/features-and-capabilities.md) tervez használni, a helyrendszer-szerepkörök vagy a Windows infrastruktúra szükséges és mely helyeken a több helyet tartalmazó hierarchiában helyezhetők üzembe őket az a hálózati és a kiszolgáló erőforrásainak leghatékonyabb kihasználását.  

-   Ügyeljen adatai és eszközei biztonságára, használhat PKI-tanúsítványt is. Lásd: [PKI-tanúsítványkövetelmények a System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  


**Tekintse át a külön helyekre vonatkozó a következő forrásokat:**  

-   [A System Center Configuration Manager SMS-szolgáltató tervezése](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)  

-   [A Helyadatbázis tervezése a System Center Configuration Managerhez](../../../core/plan-design/hierarchy/plan-for-the-site-database.md)  

-   [A System Center Configuration Manager helyrendszer-kiszolgálók és helyrendszerszerepkörök tervezése](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)  

-   [A System Center Configuration Managerben a biztonság tervezése](../../../core/plan-design/security/plan-for-security.md)  

-   A [Hálózati sávszélesség kezelése](../../../core/plan-design/hierarchy/manage-network-bandwidth.md)tartalom helyen belüli központi telepítése esetén  


**Vegye figyelembe a helyeket és hierarchiákat áthidaló konfigurációkat:**  

-   [A System Center Configuration Manager által támogatott magas rendelkezésre állási lehetőségek](/sccm/protect/understand/high-availability-options) helyek és hierarchiák részére

-   [Az Active Directory-séma kiterjesztése a System Center Configuration Manager](../../../core/plan-design/network/extend-the-active-directory-schema.md) és helyek konfigurálása [helyadatok közzététele a System Center Configuration Managerhez](../../../core/servers/deploy/configure/publish-site-data.md)  

-   [A System Center Configuration Manager helyek közötti adatátvitel](../../../core/servers/manage/data-transfers-between-sites.md)  

-   [Szerepkör alapú felügyelet a System Center Configuration Manager – alapok](../../../core/understand/fundamentals-of-role-based-administration.md)

