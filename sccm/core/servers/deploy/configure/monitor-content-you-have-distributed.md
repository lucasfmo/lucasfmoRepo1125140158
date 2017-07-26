---
title: "A tartalmak figyelését |} Microsoft Docs"
description: "Megtudhatja, hogyan figyelheti a terjesztett tartalmakat a Configuration Manager konzol használatával."
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 82e8a693-9adf-4ca3-8484-7e101c34c7c1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 7659d5789b8ce4e9e0b585a331c8f68869c9492d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="monitor-content-you-have-distributed-with-system-center-configuration-manager"></a>A System Center Configuration Managerrel terjesztett tartalom figyelése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager konzol használatával figyelheti a terjesztett tartalmakat, beleértve:  

-   Az állapot, az összes csomagtípus található a társított terjesztési pontokhoz képest.  
-   A csomag tartalmának tartalomérvényesítési állapotát.  
-   Egy adott terjesztésipont-csoporthoz hozzárendelt tartalom állapotát.  
-   A terjesztési ponthoz rendelt tartalom állapotát.  
-   Választható szolgáltatások az egyes terjesztési pontok (tartalomérvényesítés, PXE és csoportos küldés) állapotát.  

> [!NOTE]  
>  A Configuration Manager csak figyeli a tartalmat egy terjesztési ponton lévő tartalomtárba. A csomag vagy egyéni megosztás terjesztési pontján tárolt tartalmat a rendszer nem figyeli.  

##  <a name="BKMK_ContentStatus"></a> Tartalomállapot figyelése  
 A tartalomcsomagokkal kapcsolatos tudnivalók a **Figyelés** munkaterület **Tartalomállapot** csomópontján találhatók. A Configuration Manager konzolon megtekintheti az információkat, például:  

-   A csomag nevét.  
-   A típus.  
-   Hány terjesztési pontokat a csomag el lett küldve.  
-   A megfelelési arány.  
-   A csomag létrehozásának.  
-   A csomagazonosító.  
-   Az adatforrás verzióját.  

Akkor is találhat részletes állapotadatait a csomagot, valamint a csomag terjesztési állapotával többek között:  

-   A hibák száma.  
-   A függőben lévő terjesztéseket.  
-   A telepítések számát.

Emellett kezelheti azokat a terjesztéseket, amely a folyamatban lévő terjesztési pontra, vagy amelyek nem tudtak juttassa el a tartalmat egy terjesztési pontra:  

-   A beállítás törlése vagy újraterjesztése tartalom érhető el egy adott terjesztési ponthoz tartozó terjesztési feladatnak a központi telepítési állapotüzenetét megtekintésekor a **eszköz adatai** ablaktáblán. Ezen az ablaktáblán található vagy a **folyamatban lévő** lapon vagy a **hiba** lapján a **Tartalomállapot** csomópont.  
-   Ezen felül a feladat részleteit a feladat befejeződött, a munka adatainak megtekintésekor százalékos megjelenítése a **folyamatban lévő** fülre. A feladat részleteit is megjelenhet egy feladat maradó újrapróbálkozások száma, valamint, hogy mennyi ideig előtt a következő újrapróbálkozási következik be, az elérhető munka adatainak megtekintésekor az **hiba** fülre.  

Folyamatban egy telepítés, amely még nem fejeződött be, leállítja az adott tartalom áthelyezését szolgáló terjesztési feladat:  

-   A központi telepítés, majd azt jelzik, hogy a terjesztés meghiúsult, és hogy egy felhasználói művelet megszakította a frissítések állapotának.  
-   Megjelenik az új állapot a **hiba** fülre.  

> [!TIP]  
>  Amikor a központi telepítés már majdnem befejeződött, nem lehetséges, hogy a terjesztés megszakításának művelete nem ér, a terjesztési pontra történő terjesztés befejezése előtt. Ha ez történik, a központi telepítés megszakítására szolgáló műveletet figyelmen kívül hagyja, és a központi telepítés állapota sikeresként jelenik meg.  

> [!NOTE]  
>  Bár a lehetőségen megszakítsa a terjesztést egy helykiszolgálón található terjesztési pontok, ennek nincs hatása. Ennek oka az, a helykiszolgáló és a terjesztési pont helyrendszer-megosztáson található a azonos egypéldányos tartalomtárhoz konvertál. Nincs levő terjesztési feladat megszakításához.  

Ha újraterjeszti azt a tartalmat, amelynek áthelyezése egy terjesztési pontra korábban meghiúsult, a Configuration Manager azonnal megkezdi a újratelepíteni ezt a tartalmat a terjesztési pontra. A Configuration Manager frissíti a központi telepítés a folyamatban lévő adott lévőre állapotát.  

Az alábbi eljárások segítségével megtekintheti a tartalomállapotot, és kezelheti azokat a terjesztéseket, amelyek a folyamatban lévő vagy amelyek nem tudtak.  

### <a name="to-monitor-content-status"></a>Tartalomállapot figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **Tartalomállapot**. A program megjeleníti a csomagokat.  

3.  Válassza ki a csomagot, amelynek részletes állapotadatait meg szeretné.  

4.  A **Kezdőlapon** kattintson az **Állapot megtekintése elemre**. Ekkor megjelennek a csomag részletes állapotadatai.  

### <a name="to-cancel-a-distribution-that-remains-in-progress"></a>Megszakítja a terjesztési pontok folyamatban  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **Tartalomállapot**. A program megjeleníti a csomagokat.  

3.  Válassza ki a kezelése, és a részleteket tartalmazó ablaktáblán kattintson a kívánt csomagot **állapotának megtekintése**.  

4.  Az a **eszköz adatai** ablaktábláján a **folyamatban lévő** lapra, kattintson a jobb gombbal a megszakítja, és válassza ki a kívánt terjesztési bejegyzésre **Mégse**.  

5.  Kattintson a **Igen** gombra a művelet megerősítéséhez és az adott terjesztési pontra történő terjesztési feladat megszakításához.  

### <a name="to-redistribute-content-that-failed-to-distribute"></a>Elvégzi a tartalmat, amelynek terjesztése meghiúsult  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **Tartalomállapot**. A program megjeleníti a csomagokat.  

3.  Válassza ki a kezelése, és a részleteket tartalmazó ablaktáblán kattintson a kívánt csomagot **állapotának megtekintése**.  

4.  Az a **eszköz adatai** ablaktábláján a **hiba** lapra, kattintson a jobb gombbal a újraterjesztése, és válassza ki a kívánt terjesztési bejegyzésre **újraterjeszteni**.  

5.  Kattintson a **Igen** a művelet megerősítéséhez és az adott terjesztési pontra az Újraterjesztési folyamat elindításához.  

## <a name="distribution-point-group-status"></a>Terjesztésipont-csoport állapota  
A **Figyelés** munkaterületen a **Terjesztésipont-csoport állapota** csomópont a terjesztésipont-csoportokról szolgáltat adatokat. Áttekintheti az információkat, például:  

-   A terjesztésipont-csoport nevét.  
-   A leírás.  
-   Terjesztési pontok számának meghatározásakor tagjai-e a terjesztési pont csoport.  
-   Csomagok számát a csoporthoz vannak rendelve.  
-   A terjesztésipont-csoport állapota.  
-   A megfelelési arány.  

Az alábbi részletes állapotadatait is megtekintheti:  

-   Hibák a terjesztésipont-csoportnak.  
-   Terjesztések jelenleg folyamatban vannak.
-   Hány terjesztése sikeresen megtörtént.  

### <a name="to-monitor-distribution-point-group-status"></a>Terjesztésipont-csoport állapotának figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **terjesztésipont-csoport állapota**. Megjelennek a terjesztésipont-csoportok.  

3.  Válassza ki a terjesztésipont-csoportot, amelynek részletes állapotadatait meg szeretné.  

4.  A **Kezdőlapon** kattintson az **Állapot megtekintése elemre**. Ekkor megjelennek a terjesztésipont-csoport részletes állapotadatai.  

## <a name="distribution-point-configuration-status"></a>Terjesztési pont konfigurációs állapota  
 A **Figyelés** munkaterületen a **Terjesztési pont konfigurációs állapota** csomópont a terjesztési pontról szolgáltat adatokat. Áttekintheti, hogy mely attribútumok engedélyezve vannak a terjesztési pont a PXE, csoportos küldésű, például tartalom érvényesítése és a terjesztési pont terjesztési állapotát. Megtekintheti továbbá a terjesztési pont részletes állapotadatait.  

> [!WARNING]  
>  Terjesztési pont konfigurációs állapota relatív az utolsó 24 órában. Ha a terjesztési pont hibát, majd helyreáll, előfordulhat, hogy az a hibaállapot a terjesztési pont helyreállása után legfeljebb 24 óráig jelenik meg.  

Terjesztési pont konfigurációs állapotának megtekintéséhez a következő eljárást használhatja.  

### <a name="to-monitor-distribution-point-configuration-status"></a>Terjesztési pont konfigurációs állapotának figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés**.  

2.  Az a **figyelés** munkaterületet, bontsa ki a **terjesztés állapota**, és kattintson a **terjesztési pont konfigurációs állapota**. Megjelennek a terjesztési pontok.  

3.  Válassza ki a kívánt terjesztési pont állapotinformáció terjesztési pontot.  

4.  Az eredmények ablaktáblájában jelenítse meg a **Részletek** lapot. Ekkor megjelennek a terjesztési pont állapotadatai.  

## <a name="client-data-sources-dashboard"></a>Ügyfél adatforrások irányítópult
1610 verziójával kezdve használhatja a **Ügyféladatforrások** használatának megismeréséhez irányítópult [társ-gyorsítótárazás](/sccm/core/plan-design/hierarchy/client-peer-cache) a környezetben. Az irányítópult adatokat jeleníti-ügyfelek a tartalom és a jelentés a hely biztonsági információk letöltése után elindul. Ez akár 24 órát is igénybe vehet.

> [!TIP]  
> **Ügyfél társ-gyorsítótárazás** és a **Ügyféladatforrások** irányítópult 1610 verziójában bevezetett előzetes funkciók. Mielőtt a Ügyféladatforrások irányítópult válik a konzolon látható engedélyeznie kell az ügyfél társ-gyorsítótárazás. Ahhoz, hogy az ügyfél társ-gyorsítótárazás, lásd: [használata a frissítések előzetes kiadású szolgáltatások](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease). Adatok megjelenítése indításra engedélyezését követően akár 24 óráig is eltarthat.

Nyissa meg a a konzol **figyelés** > **terjesztés állapota** > **Ügyféladatforrások**. Itt adhatja meg azt a az irányítópultra alkalmazandó időszakot. Ezt követően a kijelzőn kiválaszthatja a határcsoportot vagy csomagot, amelynek meg szeretné tekinteni az adatokat. Ha az adatok megtekintésekor is az egérrel a felületen házirend adatforrásokat, illetve a különböző tartalom kapcsolatos további részletek megtekintéséhez.

Adatai közé tartoznak a következők:  
- **Ügyfél tartalomforrások**: Megjeleníti a forrás, amelyekről az ügyfelek tartalmat kapott.
- **Terjesztési pontok**: A kijelölt Határcsoport részét képező terjesztési pontok számát jeleníti meg.
- **Az ügyfelek a terjesztési pont használt**: A kijelölt Határcsoportban lévő ügyfelek számának tartalmazza hány használt terjesztési pont tartalmát.
- **Gyorsítótár források partnert**: A kijelölt határcsoport tartalmazza hány társközi gyorsítótár források jelentett letöltési előzményeiket.
- **Ügyfelek, használja a társ**: A kijelölt Határcsoportban lévő ügyfelek számának tartalmazza felhasznált társ-gyorsítótárazási forrástól tartalom eléréséhez.



Is használhatja, egy új jelentés, **Ügyféladatforrások – összefoglalás**, az egyes határcsoportokban ügyféladatforrások összegzésének megtekintése.

