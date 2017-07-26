---
title: "Helyrendszerszerepkörök tervezése |} Microsoft Docs"
description: "Fontolja meg a helyrendszer-kiszolgálók és helyrendszerszerepkörök, a System Center Configuration Manager-hierarchia tervezésekor."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a93ea730c39cce9dc46036f5aa6ece4a62679d0f
ms.openlocfilehash: 0d16d362b798c194645f987088ba8a95a7be3f19
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-site-system-servers-and-site-system-roles-for-system-center-configuration-manager"></a>Helyrendszer-kiszolgálók és helyrendszerepkörök tervezése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Minden System Center Configuration Manager-hely telepítése a kiszolgálóra, amely tartalmaz egy **helyrendszer-kiszolgáló**. A helyhez emellett a helykiszolgálótól távoli számítógépeken futó helyrendszer-kiszolgálók is tartozhatnak. A helyrendszer-kiszolgálók (azaz a helykiszolgálók vagy a távoli helyrendszer kiszolgálói) támogatják a **helyrendszerszerepköröket**.


##  <a name="bkmk_siteservers"></a> Helyrendszer-kiszolgálók  
 Helyrendszerszerepkör telepíthető olyan számítógépre, amikor a számítógép helyrendszer-kiszolgáló lesz. Minden hely egy vagy több további helyrendszer-kiszolgálókat is telepíthet. Választhatja azt is, nem a további helyrendszer-kiszolgálók telepítése, futtassa az összes helyrendszer-szerepkörök közvetlenül a hely kiszolgálóján. Minden helyrendszer egy vagy több helyrendszer-szerepkörök támogatja. További kiszolgálók segítségével bontsa ki a hely és ossza meg a helyrendszer-szerepkörök olyan kiszolgálón elhelyezni Processzorterhelés megoszlik közöttük.  

 Annak eldöntéséhez, hogy a helyrendszer-kiszolgáló hozzáadását, győződjön meg arról, a kiszolgáló megfelel-e a tervezett használattól előfeltételeit. Akkor is érdemes veheti fel egy hálózati helyre való kommunikációra tervezett végpontokkal a helykiszolgálón, tartományi erőforrások, a felhőalapú helyekkel, helyrendszer-kiszolgálók és ügyfelek elegendő sávszélesség álljon).  

 Ha a helyrendszer-kiszolgáló proxy használatára konfigurálnia helyrendszer-szerepkörök, lásd: [proxykiszolgálót használni képes Helyrendszerszerepkörök](#bkmk_proxy).  

##  <a name="bkmk_planroles"></a> Site system roles  
 A helyrendszerszerepköröket számítógépekre kell telepíteni. Céljuk, hogy további funkciókat biztosítsanak a hely számára. Példák:  

-   További felügyeleti pontokat, hogy a helyek által támogatott további eszközöket, akár a helyhez támogatott kapacitásnak.  

-   Bontsa ki a tartalmi infrastruktúra, a eszközök és felhasználók tartalomterjesztés teljesítményének növelése újabb terjesztési pontokat.  

-   Egy vagy több szolgáltatás-specifikus helyrendszer-szerepkörök. Például egy szoftverfrissítési pont lehetővé teszi, hogy a felügyelt eszközök szoftverfrissítések kezelése, vagy a jelentéskészítési szolgáltatási pont lehetővé teszi, hogy a jelentések futtatásával figyelése és megismerése, vagy a telepítéssel kapcsolatos információkat.  


Másik Configuration Manager-helyek támogathatják helyrendszerszerepkörök más-más részhalmazához. A támogatott helyrendszerszerepkörök készlete attól függ, hogy milyen típusú helyet (egy központi adminisztrációs hely, elsődleges hely vagy másodlagos helyhez). A hierarchia topológiája szintén korlátozhatja, hogy egy adott szerepkört mely helytípusokon lehet elhelyezni. A szolgáltatáskapcsolati pont például kizárólag a hierarchia legfelső szintű helyén támogatott, amely lehet központi adminisztrációs hely vagy önálló elsődleges hely. Ezt a szerepkört az alárendelt elsődleges helyek, illetve a másodlagos helyek nem támogatják.  

Egy hely telepítése után áthelyezheti helyét, az egyes helyrendszer-szerepkörök alapértelmezett helyükről a helyrendszer-kiszolgálón egy másik kiszolgálóra. Például ez igaz a felügyeleti pontot vagy terjesztési pont, amely egy elsődleges vagy másodlagos helykiszolgálón alapértelmezés szerint telepítésre kerülnek. Is telepíthet több példányt bizonyos helyrendszerszerepkörök a hely funkcióinak kiterjesztése (további szolgáltatások biztosítása ügyfelek), és az üzleti követelményeknek. Egyes szerepkörök szükség, míg mások nem kötelező.  

-   **A Configuration Manager helykiszolgálón.** Ez a szerepkör azonosítja a kiszolgáló, ahol a Configuration Manager telepítőt egy hely telepítése vagy a kiszolgáló, amelyen másodlagos helyet telepít. Ezt a szerepkört kizárólag a hely eltávolítását követően lehet áthelyezni vagy eltávolítani.  

-   **A Configuration Manager-helyrendszer.** Ez a szerepkör van hozzárendelve minden számítógép, amelyen egy helyet, vagy egy helyrendszerszerepkör telepítése. Ezt a szerepkört kizárólag az utolsó helyrendszerszerepkörnek a számítógépről való eltávolítását követően lehet áthelyezni vagy eltávolítani.  

-   **A Configuration Manager összetevő helyrendszerszerepkör.** Ez a szerepkör azonosítja a helyrendszert, hogy fut az SMS Executive szolgáltatás példánya, és más szerepkörök, például a felügyeleti pontok támogatásához szükséges. Ezt a szerepkört kizárólag az utolsó releváns helyrendszerszerepkörnek a számítógépről való eltávolítását követően lehet áthelyezni vagy eltávolítani.  

-   **A Configuration Manager Helyadatbázis-kiszolgáló.** Ezt a szerepkört a helyrendszer-kiszolgáló számára egy példányát a Helyadatbázis, a webhely tartsa van hozzárendelve. Ezt a szerepkört csak áthelyezhető egy új kiszolgálóra úgy módosítja a helyet a helyadatbázist tároló SQL Server eltérő példányát segítségével.  

-   **SMS-szolgáltatót.** Az SMS-szolgáltató szerepkört minden egyes Configuration Manager konzol és a Helyadatbázis közötti illesztőfelület SMS-szolgáltató példányát futtató számítógépre van hozzárendelve. Alapértelmezés szerint ez a szerepkör automatikusan telepíti a központi adminisztrációs hely és elsődleges helyek helykiszolgálójára. Az egyes helyeken a további rendszergazda felhasználóknak való hozzáférés biztosításához további példányokat is telepíthet.  

     További szolgáltatók telepítéséhez futtatnia kell a Configuration Manager telepítőjét [az SMS-szolgáltató kezeléséről](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider). Majd telepítse a további szolgáltatók további számítógépekre. Csak telepítheti az SMS-szolgáltató egy példányát a számítógépen, és a számítógép a helykiszolgálóval azonos tartományban kell lennie.  

-   **Az Alkalmazáskatalógus webszolgáltatási pontja.** Helyrendszerszerepkör, amely szoftverinformációt szolgáltat az alkalmazáskatalógus webhelyének a szoftverkönyvtárból. A szerepkört csak az elsődleges helyek támogatják, de több példánya is telepíthető egy adott helyre vagy egy hierarchia több különböző helyére.  

-   **Az Alkalmazáskatalógus weboldal-elérési pontja.** Helyrendszerszerepkör, amely megadja a felhasználóknak az elérhető szoftverek listáját az alkalmazáskatalógusból. A szerepkört csak az elsődleges helyek támogatják, de több példánya is telepíthető egy adott helyre vagy egy hierarchia több különböző helyére.  

     Az Alkalmazáskatalógus támogatja az ügyfélszámítógépek az interneten, esetén biztonsági okokból az Alkalmazáskatalógus weboldal-elérési pontja telepítéséhez a szegélyhálózaton a biztonság, és telepítse az Alkalmazáskatalógus webszolgáltatási pontja az intraneten.  

-   **Eszközintelligencia szinkronizációs pontja.** Olyan helyrendszerszerepkör, amely kapcsolódik a Microsoft számára, hogy letöltse az Eszközintelligencia-katalógus adatait. Ezt a szerepkört is feltölti a kategóriába nem sorolt címeket, hogy a későbbiekben a katalógus tekinthető meg. Egy hierarchiában csak egyetlen példány futhat ebből a szerepkörből, és, hogy a legfelső szintű helyen a hierarchia (központi adminisztrációs hely vagy önálló elsődleges helyen) kell lennie. Ha egy önálló elsődleges helyet nagyobb hierarchiává bővít, távolítsa el ezt a szerepkört az elsődleges helyről, és az telepítse a központi adminisztrációs helyen.   További információkért lásd: [A System Center Configuration Manager Eszközintelligencia szolgáltatása](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Tanúsítványregisztrációs pont.** Olyan helyrendszerszerepkör, amely a hálózati eszközök tanúsítványigénylési szolgáltatását futtató kiszolgálóval kommunikálva. Ezt a szerepkört az egyszerű tanúsítványigénylési protokoll (SCEP) használó eszköztanúsítvány-kérelmeket kezeli. Ezt a szerepkört kizárólag az elsődleges hely és a központi adminisztrációs hely támogatja.

     Habár egyetlen tanúsítványregisztrációs pont az egész hierarchiát képes ellátni, érdemes lehet ezt a szerepkört a helyen, és több helyen több példányt telepítsen ugyanabba a hierarchiába. Ez segítheti a terheléselosztás. Ha egy hierarchiában több példány is működik, az ügyfeleket a rendszer véletlenszerűen rendeli a tanúsítványregisztrációs pontok egyikéhez.  

     Minden egyes tanúsítványregisztrációs pontnak egy külön példányt kell elérnie a Hálózati eszközök tanúsítványigénylési szolgáltatásából. Nem lehet beállítani, hogy több tanúsítványregisztrációs pont is a Hálózati eszközök tanúsítványigénylési szolgáltatásának ugyanazt a példányát használja. Ezenfelül a tanúsítvány regisztrációs pontja nem telepíthető arra a kiszolgálóra, amelyen a Hálózati eszközök tanúsítványigénylési szolgáltatása fut.  

- **Felügyeleti átjáró összekötőpontja felhő.** Helyrendszerszerepkörrel folytatott kommunikáció a [felhő adatkezelési átjáró](/sccm/core/clients/manage/setup-cloud-management-gateway).

-   **Terjesztési pont.** Helyrendszerszerepkör, amely az ügyfelek által letölthető forrásfájlokat tartalmazza, például alkalmazástartalmat, szoftvercsomagokat, szoftverfrissítéseket, operációs rendszerek lemezképeit és rendszerindító lemezképeket. Ez a szerepkör alapértelmezés szerint települ a helykiszolgáló számítógépre az új elsődleges és másodlagos helyek telepítésekor. Ezt a szerepkört egy központi adminisztrációs helyen nem támogatott. Ennek a helyrendszerszerepkörnek több példányát is telepítheti egy támogatott helyre, illetve egy hierarchia több különböző helyére. További információk: [A System Center Configuration Manager tartalomkezelésének alapvető fogalmai](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) és [A System Center Configuration Managerhez kapcsolódó tartalom és tartalomkezelési infrastruktúra felügyelete](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   **Tartalék állapotkezelő pontot.** Olyan helyrendszerszerepkör, amelynek segítségével figyelheti az ügyféltelepítéseket, és azonosíthatja a nem felügyelt miatt ügyfelek nem tudnak kommunikálni a felügyeleti ponttal. A szerepkört csak az elsődleges helyek támogatják, de több példánya is telepíthető egy adott helyre, vagy egy hierarchia több különböző helyére. További információk: [A tartalom forráshelyei – esetek](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).


-   **Endpoint Protection-pont.** Olyan helyrendszerszerepkör, amely a Configuration Manager az Endpoint Protection licencfeltételeinek elfogadására, és a felhő Protection Service alapértelmezett tagságának konfigurálására használ. Egy hierarchiában csak egyetlen példány futhat ebből a szerepkörből, és, hogy a legfelső szintű helyen a hierarchia (központi adminisztrációs hely vagy önálló elsődleges helyen) kell lennie. Ha egy önálló elsődleges helyet nagyobb hierarchiává bővít, távolítsa el ezt a szerepkört az elsődleges helyről, és az telepítse a központi adminisztrációs helyen. További információkért lásd: [a System Center Configuration Managerben az Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md).  

-   **A beléptetési pont.** Olyan helyrendszerszerepkör, amely a Configuration Manager PKI-tanúsítványokat használ a mobileszközök és Mac számítógépek beléptetésének. A szerepkört csak az elsődleges helyek támogatják, de több példánya is telepíthető egy adott helyre vagy egy hierarchia több különböző helyére.  

     Ha a felhasználó mobileszközöket léptet be a Configuration Manager használatával, és a felhasználó Active Directory-fiókja olyan erdőben van, amelynek nincs biztonságos kapcsolata a helykiszolgáló erdőjével, telepítenie kell a beléptetési pont az a felhasználó erdőjében. A felhasználó aztán hitelesíthető.  

-   **Beléptetési proxypont.** Olyan helyrendszerszerepkör, amely a mobileszközök és Mac számítógépekhez a Configuration Manager beléptetési kéréseit kezeli. A szerepkört csak az elsődleges helyek támogatják, de több példánya is telepíthető egy adott helyre vagy egy hierarchia több különböző helyére.  

     Ha támogatja a mobileszközöket az interneten, a beléptetési proxypont a szegélyhálózaton a biztonság, és telepítse a beléptetési pont az intraneten.  

-   **Exchange Server-összekötőt.** Ez a szerepkör kapcsolatos információkért lásd: [mobileszközök kezelése a System Center Configuration Manager és az Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)  

-   **Felügyeleti pont.** Olyan helyrendszerszerepkör, amely a házirendek és a szolgáltatások helyére vonatkozó információkat biztosít az ügyfelek számára, és a konfigurációs adatokat fogad az ügyfelektől.  

    Ez a szerepkör alapértelmezés szerint települ a helykiszolgáló számítógépre az új elsődleges és másodlagos helyek telepítésekor. Elsődleges helyek támogatják a szerepkör több példányát. Egyetlen felügyeleti pontot a másodlagos helyek támogatják, az ügyfelek a számítógép és a felhasználó helyi pont házirendhez (a felügyeleti pont egy másodlagos helyen nevezzük egy proxy felügyeleti pont).  

     Felügyeleti pontok HTTP vagy HTTPs támogatására, valamint a System Center Configuration Manager helyszíni mobileszköz-kezelés felügyelt mobileszközök támogatására is beállítható. [A System Center Configuration Manager felügyeleti pontjainak adatbázis-replikái](../../../core/servers/deploy/configure/database-replicas-for-management-points.md) használhatók annak a CPU-terhelésnek a csökkentésére, amelyet a felügyeleti pontok rónak a helyadatbázis-kiszolgálóra az ügyfelektől érkező kérelmek kiszolgálása során.  

-   **Jelentéskészítési szolgáltatási pontot.** Olyan helyrendszerszerepkör, amely az SQL Server Reporting Services a jelentések létrehozását és kezelését a Configuration Manager számára. Ez a szerepkör támogatott elsődleges helyek és a központi adminisztrációs helyen, és egy támogatott helyre a szerepkör több példányát is telepítheti. További információkért lásd: [A jelentéskészítés tervezése a System Center Configuration Managerben](../../../core/servers/manage/planning-for-reporting.md).  

-   **Szolgáltatáskapcsolódási pont.** Olyan helyrendszerszerepkör, amelyekkel mobileszközök kezelése a Microsoft Intune és a helyszíni mobileszköz-kezelést. Ez a szerepkör is feltölti a webhely-használati adatait, és szükséges a frissítések a Configuration Manager számára a Configuration Manager konzolban. Egy hierarchiában csak egyetlen példány futhat ebből a szerepkörből, és, hogy a legfelső szintű helyen a hierarchia (központi adminisztrációs hely vagy önálló elsődleges helyen) kell lennie. Ha egy önálló elsődleges helyet nagyobb hierarchiává bővít, távolítsa el ezt a szerepkört az elsődleges helyről, és az telepítse a központi adminisztrációs helyen. További információk: [A System Center Configuration Manager szolgáltatáskapcsolódási pontjának ismertetése](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   **A szoftverfrissítési pont.** Olyan helyrendszerszerepkör, amely a Windows Server Update Services (WSUS) használatával biztosít szoftverfrissítéseket a Configuration Manager-ügyfelek számára. Ez a szerepkör összes helyek támogatják:  

    -   A WSUS szinkronizálja a központi adminisztrációs hely a helyrendszer telepítéséhez.  

    -   Állítsa be ezt a szerepkört minden egyes példánya alárendelt elsődleges helyeken szinkronizálja a központi adminisztrációs hely.  

    -   A másodlagos helyekre is érdemes lehet szoftverfrissítési pontot telepíteni, ha lassú a hálózati adatátvitel.  

    További információk: [Szoftverfrissítések tervezése a System Center Configuration Managerben](../../../sum/plan-design/plan-for-software-updates.md).  

-   **Állapotáttelepítési pont.** Helyrendszerszerepkör, amely a felhasználói állapot adatait tárolja, amikor a számítógépekre új operációs rendszert kell áttelepíteni. Ezt a szerepkört az elsődleges helyeken és a másodlagos helyeken támogatott. Egy hierarchia több példánya a helyen, illetve több helyre is telepíthető. Ha további információkra kíváncsi arról, hogyan tárolhatja a felhasználói állapotokat az operációs rendszer központi telepítése során, olvassa el a következő cikket: [A felhasználói állapot kezelése a System Center Configuration Managerben](../../../osd/get-started/manage-user-state.md).  

-   **Rendszerállapot-érvényesítési pont.** A helyrendszerszerepkör a Configuration Manager-konzolon látható marad, de már nem használatos.  

###  <a name="bkmk_proxy"></a> Proxykiszolgálót használni képes helyrendszerszerepkörök  
 Egyes Configuration Manager helyrendszerszerepkörök internetkapcsolatot igényelnek, és fogja használni a proxykiszolgálót, amikor a helyrendszer-kiszolgáló szerepkört üzemeltető van konfigurálva, legalább egy. Ez a kapcsolat jellemzően a a **rendszer** annak a számítógépnek, ahol a helyrendszer-szerepkör telepítve van a környezetben. A kapcsolat nem használhat proxykonfigurációt a tipikus felhasználói fiókokhoz. Ha proxykiszolgáló szükséges az internetkapcsolat befejezéséhez, be kell állítania a számítógépet proxykiszolgáló használatára:  

-   A proxykiszolgáló beállíthat egy helyrendszer-szerepkör telepítésekor.  

-   Adja hozzá, vagy módosíthatja a proxykiszolgáló azon konfigurációját a Configuration Manager-konzol használata esetén.  

-   Ugyanazt a proxykiszolgálót egy helyrendszer-kiszolgálón proxykiszolgáló-konfigurációt használó összes helyrendszerszerepkör szolgál. Ha a különböző helyrendszerszerepkörök különböző proxykiszolgálókat használjanak van szüksége, telepítenie kell a helyrendszer-szerepkörök a különböző helyrendszer-kiszolgáló számítógépre.  

-   Ha módosítja a proxykiszolgáló konfigurációját, vagy új helyrendszerszerepkört telepít egy olyan számítógépre, amelyen már van érvényes proxykiszolgáló-konfiguráció, a rendszer felülírja a régi konfigurációt az újjal.  


A proxykiszolgálót a helyrendszer-szerepkörök beállításával kapcsolatos eljárások leírását a [a System Center Configuration Manager helyrendszer-szerepkörök hozzáadásához](../../../core/servers/deploy/configure/add-site-system-roles.md) témakör.  

A következő helyrendszerszerepkörök használhatnak proxykiszolgálót:  

-   **Eszközintelligencia szinkronizációs pontja.** E helyrendszerszerepkör csatlakozik a Microsoft, a proxykiszolgáló azon konfigurációját használja az Eszközintelligencia szinkronizálási pontját üzemeltető számítógépen.  

-   **Felhőalapú terjesztési pont.** A felhő alapú terjesztési pontok használatakor a felhőalapú terjesztési pontot felügyelő elsődleges helykiszolgálónak kapcsolódnia kell a Microsoft Azure kiépítéséhez, figyeléséhez és a terjesztési pontra történő tartalomterjesztés kell lennie. Ha proxykiszolgáló szükséges ehhez a kapcsolathoz, be kell állítania a proxykiszolgálót az elsődleges hely kiszolgálóján. A felhő alapú terjesztési pont, az Azure-ban a proxykiszolgáló nem tudja beállítani. További információkért lásd: a [Roxybeállítások felhőszolgáltatásokat kezelő elsődleges helyekhez](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md#BKMK_ConfigProxyforCloud) szakasz a [felhő alapú terjesztési pontok telepítése a Microsoft Azure a System Center Configuration Manager](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md) témakör.  

-   **Exchange Server-összekötőt.** A helyrendszerszerepkör Exchange-kiszolgálóhoz kapcsolódik, és a proxykiszolgáló azon konfigurációját használja az Exchange Server-összekötőt üzemeltető számítógépen.  

-   **A szoftverfrissítési pont.** Ez a helyrendszerszerepkör kapcsolatot létesít a javítókészletek letöltéséhez és frissítésekkel kapcsolatos információk szinkronizálásához a Microsoft Update lehet szükség. Általában a proxykiszolgáló beállításakor minden egyes helyrendszerszerepkörhöz a számítógépen, amely a proxykiszolgáló használatát támogatja a proxykiszolgálót használ. Nincs szükség további konfigurációra. Kivétel ez alól a szoftverfrissítési pontokon. Alapértelmezés szerint a szoftverfrissítések pont nem használja az elérhető proxykiszolgálót, kivéve, ha a szoftverfrissítések pont beállítása során is engedélyezik a következő beállításokat:  

    -   **Proxykiszolgáló használata a szoftverfrissítések szinkronizálásakor**  

    -   **Proxykiszolgáló használata tartalom automatikus központi telepítési szabályokkal történő letöltésekor**  

    > [!TIP]  
    >  Bármelyik beállítás kiválasztása előtt proxykiszolgálót a helyrendszer-kiszolgálón, amelyen a szoftverfrissítések pont kell állítani. A rendszer csak a megjelölt funkciókhoz használja a proxykiszolgálót.  

 Szoftverfrissítési pontok proxykiszolgálóival kapcsolatban további információkért tekintse meg a "Proxykiszolgáló beállításai" szakaszának [egy szoftverfrissítési pont telepítése](../../../sum/get-started/install-a-software-update-point.md) témakör.  

-   **Szolgáltatáskapcsolódási pont.** Ha be kell online (nem offline), a helyrendszerszerepkör kapcsolatot létesít a Microsoft Intune és a Microsoft felhőalapú szolgáltatásából.  

