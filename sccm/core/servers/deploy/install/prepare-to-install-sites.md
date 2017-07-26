---
title: "Helyek telepítése előkészítése |} Microsoft Docs"
description: "Ha több Configuration Manager-hely telepítéséhez, olvassa el ezt az információt segítséget időt takaríthat meg, és hogy megelőzhesse a hibákat."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9089e1b5-cba4-42bd-a2de-126ef882a3af
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 73c34d40d70fb3ae5f8702f3d5f1e5b51a1b28a7
ms.openlocfilehash: 829f2d44a9b8d203a5b753ebb6d8f759b1a05111
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="prepare-to-install-system-center-configuration-manager-sites"></a>Felkészülés a System Center Configuration Manager-helyek telepítése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Egy vagy több System Center Configuration Manager-hely sikeres telepítésének előkészítése, ismerkedjen meg a részleteket a cikkben. Ezeket a lépéseket is takaríthat meg időben több hely telepítése során, és segít megelőzni missteps, ami okozhatja azt újra kell telepítenie egy vagy több hely szükséges.

> [!TIP]
> Kezelése a System Center Configuration Manager-hely és hierarchia-infrastruktúra, a feltételek *frissítése*, *frissítése*, és *telepítése* használt három különböző fogalmi kört alkotnak. Minden kifejezéshez használatáról információkért lásd: [frissítés, frissítés és telepítés](/sccm/core/understand/upgrade-update-install).

## <a name="bkmk_options"></a>Különböző típusú helyek telepítésének beállításait
Új Configuration Manager-hely telepítésekor a forrásfájlokat, melyekkel verziója függ, amelyek már (ha van ilyen) a hierarchiában lévő helyek verzióját. A telepítési módszereket, amelyekkel függ a telepítendő hely típusát.  

Egy hely telepítése előtt győződjön meg arról, hogy a hierarchia tervezett, és, hogy tudomásul veszi a telepítendő hely típusát. További információkért lásd: [helyek hierarchiájának tervezése](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).


### <a name="first-site"></a>Első hely
Az első hely, amely telepít egy hierarchiában egy önálló elsődleges helyet vagy központi adminisztrációs hely lesz.

**Telepítési adathordozó**: A központi adminisztrációs hely vagy önálló elsődleges hely új hierarchia első helyének telepítéséhez kell [használja egy alapkonfigurációt](../../../../core/servers/manage/updates.md#bkmk_Baselines) a Configuration Manager. Ne telepítse a frissített forrásfájlokat egy új hierarchia első helyének a [CD-ről. Legújabb mappa](../../../../core/servers/manage/the-cd.latest-folder.md) webhelyek.

**Telepítési módszer**: Mindkét webhely típusú segítségével telepítheti a [Configuration Manager telepítő varázsló](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md), vagy beállíthatja, hogy a parancsfájlt egy [parancsprogrammal létrehozva a parancssori telepítés](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).


### <a name="additional-sites"></a>További webhelyek
Az első hely telepítése után bármikor hozzáadhat további helyeket. A következő beállítások érhetők el helyek hozzáadása (akár [korlátok támogatott](../../../../core/plan-design/configs/size-and-scale-numbers.md)):

|Helyet, amely rendelkezik|Telepíthet további hely típusa|
|---|---|
|Központi adminisztrációs hely|Gyermek elsődleges hely|
|Gyermek elsődleges hely|Másodlagos hely|
|Önálló elsődleges hely|Másodlagos hely (bővítheti az elsődleges hely, amely alakítja át az önálló elsődleges hely egy alárendelt elsődleges helyre)|

**Telepítési adathordozó**: Ha egy önálló elsődleges hely központi adminisztrációs helyet telepít, vagy ha új elsődleges gyermekhelyet telepít egy meglévő hierarchiához, kell használnia (forrásfájlokat tartalmazó) telepítési adathordozóján, amely ugyanolyan verziójúak, mint a meglévő webhelyet vagy webhelyeket.

> [!IMPORTANT]
> Ha a konzolon belüli frissítések, amelyek megváltoztak a már telepített helyeken verzióját telepítette, ne használja az eredeti telepítési adathordozóján. Ehelyett adott esetben a forrásfájlok használata a [CD-ről. Legújabb mappa](../../../../core/servers/manage/the-cd.latest-folder.md) frissített hely. A Configuration Manager megköveteli, hogy a meglévő helyet, amely az új hely kapcsolódni fog verziójának megfelelő forrásfájlokat használja.

A Configuration Manager konzol egy másodlagos helyre kell telepíteni. Ily módon a másodlagos helyek mindig használatával telepített forrásfájljait a szülő elsődleges hely.

**Telepítési módszer**: A további helyek telepítésekor használt módszer attól függ, hogy a telepítendő hely típusát.
-   **Adja hozzá a központi adminisztrációs hely**:  A Configuration Manager telepítő varázsló vagy a parancsprogram-alapú parancssor segítségével telepítse az új központi adminisztrációs hely lehet a meglévő önálló elsődleges helyet. További információkért lásd: [önálló elsődleges hely kibővítése](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand).
-   **Adja hozzá a gyermek elsődleges helyek**:  A Configuration Manager telepítő varázsló vagy a parancssori telepítés segítségével adja hozzá a gyermek elsődleges helyek a központi adminisztrációs hely alá.
-   **Másodlagos hely**:  A Configuration Manager konzol segítségével egy másodlagos helyet telepítsen egy elsődleges hely alá. Egyéb metódusok nem támogatottak a másodlagos helyek hozzáadásához.

## <a name="bkmk_tasks"></a>Közös telepítés megkezdése előtt elvégzendő feladatok
-   **A telepítéshez használandó hierarchia-topológiát ismertetése**    
További információkért lásd: [helyek hierarchiájának tervezése a System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

-   **Készítse elő, és konfigurálja az egyes kiszolgálók Előfeltételek és használja a Configuration Manager támogatott konfigurációi**         
További információk: [Hely és helyrendszer előfeltételei](../../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

-   **A Helyadatbázis tárolásához SQL-kiszolgáló telepítése és konfigurálása**     
További információkért lásd: [SQL Server-verziók támogatása a System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   **A Configuration Manager támogatására hálózati környezet előkészítése**      
További információkért lásd: [tűzfalak, portok és tartományok előkészítése a Configuration Manager konfigurálása](../../../../core/plan-design/network/configure-firewalls-ports-domains.md).  

- **Ha nyilvános kulcsokra épülő infrastruktúra (PKI) fog használni, készítse elő az infrastruktúrát és a tanúsítványok**      
További információkért lásd: [PKI-tanúsítványkövetelmények a Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).

-   **Telepítse a legújabb biztonsági frissítéseket fog helykiszolgálóként vagy helyrendszer-kiszolgálók használatára, és szükség esetén indítsa újra őket számítógépeken**

## <a name="bkmk_sitecodes"></a>A helynevek és a helykódok
Helykódok és helynevek azonosításához és kezeléséhez a Configuration Manager-hierarchiában lévő helyek szolgálnak. A Configuration Manager konzolján a Helykód és helynév megjelennek a &lt; *Helykód*\> - &lt;*helynév* \> formátumban. Használ a hierarchiában helykódoknak egyedinek kell lennie. Ha az Active Directory-séma ki van bővítve a Configuration Manager és a helyek adatokat tesznek közzé, az Active Directory-erdőn belül használt helykódoknak egyedi kell még akkor is, ha azokat használja egy másik Configuration Manager-hierarchiában, vagy ha a korábbi Configuration Manager telepítése használt. Győződjön meg arról, hogy a helykódok és helynevek alapos megtervezéséről a hierarchia központi telepítése előtt.

### <a name="specify-a-site-code-and-site-name"></a>A Helykód és helynév megadása
A Configuration Manager telepítő futtatásakor kéri a Helykód és helynév a központi adminisztrációs hely, és minden elsődleges hely és a másodlagos hely telepítéséhez. Egy olyan helykódot egyedi módon kell azonosítania a hierarchia mindegyik helyén. A Helykód mappanevekben szerepel, mert soha ne használja a Helykód, a következő neveket, többek között a Configuration Manager és a Windows számára fenntartott nevek:
  -  AUX
  -  CON
  -  NUL
  -  PRN
  -  SMS

> [!NOTE]
> A Configuration Manager telepítő nem ellenőrzi, hogy a hely kódja nem már használatban van.

Adja meg a helykódot egy helyhez, ha futtatja a Configuration Manager telepítő, három alfanumerikus karaktert kell megadnia. Csak betűk *A* keresztül *Z* és a számok *0* keresztül *9*, bármilyen kombinációban engedélyezettek a helykódok. Betűk vagy számok sorrendje nincs hatással a kommunikációt a helyek közötti rendelkezik. Például nincs szükség ahhoz, hogy megnevezzen egy elsődleges hely *ABC* és egy másodlagos hely *DEF*.

A hely neve a hely felhasználóbarát azonosítója. Csak a karaktert használhat *A* keresztül *Z*, *egy* keresztül *z*, *0* keresztül *9*, és a kötőjel (*-*) a hely neve.

> [!IMPORTANT]
> A Helykód vagy a hely neve a hely telepítése után a változás nem támogatott.

### <a name="reuse-a-site-code"></a>Egy helykódot többször használ
Helykódok nem használható egynél többször a Configuration Manager-hierarchia központi adminisztrációs hely vagy elsődleges helyhez, akkor is, ha az eredeti hely és a hely kódja eltávolították. Ha egy helykódot többször használ, akkor kockázatok objektumazonosítók ütközését a hierarchiában. Újrahasználhatja a helykódot egy másodlagos hely esetén a másodlagos hely és a hely kódja már nem használja a Configuration Manager-hierarchiában vagy az Active Directory-erdőben.

## <a name="limits-and-restrictions-for-installed-sites"></a>Korlátai és korlátozásai telepített helyeken
Egy hely telepítése előtt fontos tudni, hogy a következő korlátozások vonatkoznak, amelyek érvényesek a helyek és hierarchiák hely:
-   A telepítő futtatása után a következő hely tulajdonságai nem módosíthatók a hely eltávolítása és újratelepítése az új értékek használatával nélkül:  
  -   Programfájlok telepítési könyvtára  
  -   Helykód  
  -   Hely leírása  
-   Ha az a hierarchia egy központi adminisztrációs helyet tartalmaz:  
  -   A Configuration Manager nem támogatja a hierarchiából önálló elsődleges hely létrehozásához, vagy csatlakoztassa azt egy másik hierarchiából elsődleges gyermekhely áthelyezését. Ehelyett a gyermek elsődleges hely eltávolítása, és telepítse újra egy új önálló elsődleges helyet, vagy a központi adminisztrációs helyet egy másik hierarchia egy másik hely.  


## <a name="bkmk_optionalsteps"></a>A telepítő futtatása előtt nem kötelező lépések
**Manuális futtatása [a telepítő letöltési segédprogramja](../../../../core/servers/deploy/install/setup-downloader.md)**

A Configuration Manager a frissített telepítési fájlok letöltéséhez a telepítő letöltési segédprogramja is futtathatja. Ha a számítógépet, ha futtatja a telepítő nem csatlakozik az internethez, vagy ha várhatóan több helykiszolgálót telepít, érdemes a telepítő letöltési segédprogramjával töltse le a szükséges frissítések a telepítő. További információt a következő:
-  Alapértelmezés szerint a telepítő csatlakozik az internethez a frissített telepítési fájlok letöltéséhez.
-  Alapértelmezés szerint a fájlok a Redist mappában vannak tárolva.
-  Közvetlenül telepíthet egy olyan helyre a hálózaton, ahol korábban tárolta ezeket a fájlokat egy példányát.

**Manuális futtatása [előfeltétel-ellenőrző](../../../../core/servers/deploy/install/prerequisite-checker.md)**

Problémák azonosítása és megoldása hely telepítéséhez a telepítő futtatása előtt, és a kiszolgálón a helyrendszerszerepkörök telepítése előtt, futtathatja az előfeltétel-ellenőrző. Az előfeltétel-ellenőrző biztosíthatja, hogy a számítógép megfelel-e a helykiszolgáló vagy helyrendszerszerepkör üzemeltetésének követelményeit. További információt a következő:
 -  Alapértelmezés szerint a telepítő futtatja az előfeltétel-ellenőrző.
 -  Ha hiba történik, a telepítő leállítja a probléma a megoldásáig.

**Azonosítsa a lehetséges portokat**

Azonosíthatja, hogy a helyrendszerek és ügyfelek számára a lehetséges portokat. További információt a következő:
 -  Alapértelmezés szerint a helyrendszerek és ügyfelek előre definiált portok használatára való kommunikációhoz.
 -  A telepítés során más portok konfigurálhatja.

 További információkért lásd: [a System Center Configuration Managerben használt portok](../../../../core/plan-design/hierarchy/ports.md).

