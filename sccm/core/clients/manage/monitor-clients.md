---
title: "Ügyfelek - Configuration Manager figyelése |} Microsoft Docs"
description: "Részletes útmutatást szerezni a System Center Configuration Manager ügyfelek figyelése."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
caps.latest.revision: 23
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 08a4d9b29871b49e3118aef949572cef64940f96
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-clients-in-system-center-configuration-manager"></a>Ügyfelek figyelése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


 Ha a System Center Configuration Manager ügyfélalkalmazás telepítve van a Windows rendszerű számítógépek és eszközök a hely, figyelheti azok állapotát és tevékenységét a Configuration Manager konzolon.  

##  <a name="bkmk_about"></a> Az ügyfélállapot áttekintése  
 A Configuration Manager kínál az alábbi típusú információkat ügyfélállapotként:  

-   **Ügyfél online állapota** -Configuration Manager 1602-es verziójától kezdve ez az állapot azt jelzi, hogy a számítógép online állapotban-e vagy sem. A számítógép akkor számít online állapotúnak, ha csatlakozik a hozzá rendelt felügyeleti ponthoz.  Azt jelzi, hogy az ügyfél online, azt pingszerű üzeneteket küld a felügyeleti pont. Ha a felügyeleti pont nem kap üzenetet körülbelül 5 percig, akkor offline állapotúnak tekinti az ügyfelet.  

-   **Az ügyfél tevékenységét** -azt jelzi, hogy az ügyfél nem aktív kommunikáció zajlik a Configuration Manager az elmúlt 7 napban. Ha az ügyfél 7 napig nem kér házirend-frissítést, nem küld „szívverés” üzenetet vagy nem küld hardverleltárt, akkor az ügyfél inaktívnak számít.  

-   **Az ügyfél-ellenőrzési** -azt jelzi, hogy a Configuration Manager-ügyfél a számítógépén fut a rendszeres ellenőrzés sikeres.  A szolgáltatás ellenőrzi a számítógépet, és ha talál hibákat, egyeseket ki is tud javítani közülük. További tudnivalók: [Az ügyfél-ellenőrzési szolgáltatás által végzett ellenőrzések és szervizelések](#BKMK_ClientHealth).  

     Windows 7 rendszert futtató számítógépeken az ügyfélellenőrzés ütemezett feladatként fut. Későbbi operációs rendszereken az ügyfélellenőrzés automatikusan fut a Windows karbantartási időszak alatt.  

     A szervizelést konfigurálhatja úgy, hogy bizonyos számítógépeken, például egy üzletmenet szempontjából kritikus kiszolgálón ne fusson. Emellett ha nincsenek további kiértékelni kívánt elemek, segítségével a Configuration Manager megfelelőségi beállítások az átfogó állapotát, tevékenység és a szervezeti számítógépek megfelelőségének figyeléséhez átfogó megoldást nyújt. További információ a megfelelőségi beállításokról: [A megfelelőségi beállítások tervezése és konfigurálása a System Center Configuration Managerben](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md).  

##  <a name="bkmk_indStatus"></a> Az egyes ügyfelek állapotának figyelése  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **eszközök** , vagy válasszon egy gyűjtemény **Eszközgyűjtemények**.  

     A Configuration Manager 1602-es verziójától kezdve az egyes sorok elején látható ikon jelzi az eszköz online állapotát:  

    |||  
    |-|-|  
    |![online állapot ikon ügyfeleknek](../../../core/clients/manage/media/online-status-icon.png)|Az eszköz online állapotú.|  
    |![offline állapot ikon ügyfeleknek](../../../core/clients/manage/media/offline-status-icon.png)|Az eszköz offline állapotú.|  
    |![ismeretlen állapot ikon ügyfeleknek](../../../core/clients/manage/media/unknown-status-icon.png)|Az online állapot ismeretlen.|  
    |![nem telepített ügyfél](../../../core/clients/manage/media/client-not-installed.png)|Az ügyfél nincs telepítve az eszközön.|  

2.  A részletes online állapotát, az ügyfél online állapotának adatait a nézethez történő hozzáadáshoz eszköz jobb gombbal az oszlopfejlécre, majd kattintson a hozzáadni kívánt online állapot mezőket. A felvehető oszlopok a következők:  

    -   **Online eszközállapot** – Azt jelzi, hogy az ügyfél jelenleg online vagy offline állapotú. (Ez az információ megegyezik az ikonok által).  

    -   **Legutóbbi online állapot ideje** – Azt jelzi, hogy az ügyfél online állapota mikor változott online-ra.  

    -   **Legutóbbi offline állapot ideje** – Azt jelzi, hogy az állapot mikor változott offline-ra.  

3.  Kattintson egy meghatározott ügyfélre a lista ablaktáblájában, ekkor a részletek ablaktáblájában megjelennek az állapot részletes adatai, például az ügyfél tevékenysége és az ügyfél ellenőrzései.  

##  <a name="bkmk_allStatus"></a> Az összes ügyfél állapotának figyelése  

1.  Kattintson a Configuration Manager konzolon **figyelés** > **ügyfélállapot**. A konzol ezen lapján tekintheti át az ügyféltevékenység és az ügyfél-ellenőrzések helyhez tartozó statisztikai adatait.  Másik gyűjtemény választásával módosíthatja is az információk körét.  

2.  A jelentett statisztikai adatok részleteinek feltárásához, kattintson a jelentett információ nevére (például **rendelkezik ügyfélellenőrzésen megfelelt vagy eredményt vissza nem küldő aktív ügyfelek**), és tekintse át az információkat az egyes ügyfelekhez.  

3.  Kattintson a **ügyféltevékenység** a Configuration Manager-hely az ügyfél tevékenységét ábrázoló diagramok megjelenítéséhez.  

4.  Kattintson a **Ügyfélellenőrzésnél** a Configuration Manager hely ellenőrzi az ügyfél állapotát ábrázoló diagramok megjelenítéséhez.  

 Konfigurálhat értesítéseket arról, amikor az ügyfelek ellenőrzik az eredményeket, amikor az ügyfélaktivitás egy adott százalék alá csökken egy gyűjtemény ügyfelein, illetve amikor a szervizelés sikertelen az ügyfelek egy adott százalékán. További információ az ügyfélbeállítások konfigurálásáról: [Ügyfélállapot-beállítások konfigurálása a Configuration Managerben](../../../core/clients/deploy/configure-client-status.md).  

##  <a name="BKMK_ClientHealth"></a> Az ügyfél-ellenőrzési szolgáltatás által végzett ellenőrzések és szervizelések  
 Az ügyfél-ellenőrzési szolgáltatás az alábbi ellenőrzéseket és szervizeléseket végzi el.  

|Ügyfélellenőrzés|Szervizelési műveletek|További információ|  
|------------------|------------------------|----------------------|  
|Annak ellenőrzése, hogy a közelmúltban futott-e ügyfélellenőrzés|Ügyfélellenőrzés futtatása|Annak ellenőrzése, hogy az elmúlt három napban futott-e legalább egyszer ügyfélellenőrzés.|  
|Annak ellenőrzése, hogy telepítve vannak-e az ügyfél előfeltételei|Az ügyfél előfeltételeinek telepítése|Ellenőrzi, hogy telepítve vannak-e az ügyfél előfeltételei. Az előfeltételek felderítéséhez beolvassa az ügyfél telepítési mappájában lévő ccmsetup.xml fájlt.|  
|WMI-tárház integritási tesztje|A Configuration Manager-ügyfél újratelepítése|Ellenőrzi, hogy megtalálhatók-e a Configuration Manager-ügyfél bejegyzései a WMI-ben.|  
|Annak ellenőrzése, hogy fut-e az ügyfélszolgáltatás|Az ügyfélszolgáltatás (SMS-ügynök gazdaszolgáltatása) elindítása|Nem áll rendelkezésre további információ|  
|WMI eseményelnyelő tesztje.|Az ügyfélszolgáltatás újraindítása|Ellenőrizze, hogy a Configuration Manager kapcsolatos WMI eseményelnyelő elvész.|  
|Annak ellenőrzése, hogy létezik-e a Windows Management Instrumentation (WMI) szolgáltatás|Nincs szervizelés|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy megfelelően van-e telepítve az ügyfél|Az ügyfél újratelepítése|Nem áll rendelkezésre további információ|  
|WMI-tárház olvasási és írási tesztje|A WMI-tárház alaphelyzetbe állítása és a Configuration Manager-ügyfél újratelepítése|Ennek az ügyfélellenőrzésnek a szervizelése csak olyan számítógépen hajtható végre, amelyen Windows Server 2003, Windows XP (64 bites) vagy régebbi verziójú operációs rendszer működik.|  
|Annak ellenőrzése, hogy a kártevőirtó szolgáltatás indítási típusa automatikus-e|A szolgáltatás indítási típusának visszaállítása automatikusra|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy fut-e a kártevőirtó szolgáltatás|A kártevőirtó szolgáltatás elindítása|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a Windows Update szolgáltatás indítási típusa automatikus vagy kézi-e|A szolgáltatás indítási típusának visszaállítása automatikusra|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy az ügyfélszolgáltatás (SMS-ügynök gazdaszolgáltatása) indítási típusa automatikus-e|A szolgáltatás indítási típusának visszaállítása automatikusra|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy fut-e a Windows Management Instrumentation (WMI) szolgáltatás|A Windows Management Instrumentation szolgáltatás elindítása|Nem áll rendelkezésre további információ|  
|A Microsoft SQL CE adatbázis épségének ellenőrzése|A Configuration Manager-ügyfél újratelepítése|Nem áll rendelkezésre további információ|  
|A Microsoft Policy Platform WMI-integritási tesztje|A Microsoft Policy Platform kijavítása|Nem áll rendelkezésre további információ|  
|A Microsoft Policy Platform szolgáltatás meglétének ellenőrzése|A Microsoft Policy Platform kijavítása|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a Microsoft Policy Platform szolgáltatás indítási típusa kézi-e|A szolgáltatás indítási típusának visszaállítása kézire|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy létezik-e a háttérben futó intelligens átviteli szolgáltatás|Nincs szervizelés|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a háttérben futó intelligens átviteli szolgáltatás indítási típusa automatikus vagy kézi-e|A szolgáltatás indítási típusának visszaállítása automatikusra|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a Network Inspection szolgáltatás indítási típusa kézi-e|A szolgáltatás indítási típusának visszaállítása kézire, ha telepítve van|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a Windows Management Instrumentation (WMI) szolgáltatás indítási típusa automatikus-e|A szolgáltatás indítási típusának visszaállítása automatikusra|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a Windows Update szolgáltatás indítási típusa automatikus vagy kézi-e a Windows 8 rendszerű számítógépeken|A szolgáltatás indítási típusának visszaállítása kézire|Nem áll rendelkezésre további információ|  
|Az ügyfélszolgáltatás (SMS-ügynök gazdaszolgáltatása) meglétének ellenőrzése|Nincs szervizelés|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy a Configuration Manager – távvezérlési szolgáltatás indítási típusa automatikus vagy kézi-e|A szolgáltatás indítási típusának visszaállítása automatikusra|Nem áll rendelkezésre további információ|  
|Annak ellenőrzése, hogy fut-e a Configuration Manager – távvezérlési szolgáltatás|A távvezérlési szolgáltatás elindítása|Nem áll rendelkezésre további információ|  
|Az ügyféloldali WMI-szolgáltató épségének ellenőrzése|A Windows Management Instrumentation szolgáltatás újraindítása|Ennek az ügyfélellenőrzésnek a szervizelése csak olyan számítógépen hajtható végre, amelyen Windows Server 2003, Windows XP (64 bites) vagy régebbi operációs rendszer működik.|  
|Az ébresztési proxy szolgáltatás (ConfigMgr ébresztési proxy) futásának ellenőrzése|A ConfigMgr ébresztési proxy szolgáltatás elindítása|Ezt az ügyfélellenőrzést csak akkor, ha a **energiagazdálkodás**: **Az ébresztési proxy engedélyezése** ügyfélbeállítás értéke **Igen** a támogatott ügyfél operációs rendszereken.|  
|Annak ellenőrzése, hogy az ébresztési proxy szolgáltatás (ConfigMgr ébresztési proxy) indítási típusa automatikus-e|A ConfigMgr ébresztési proxy szolgáltatás indítási típusának visszaállítása automatikusra|Ezt az ügyfélellenőrzést csak akkor, ha a **energiagazdálkodás**: **Az ébresztési proxy engedélyezése** ügyfélbeállítás értéke **Igen** a támogatott ügyfél operációs rendszereken.|  

## <a name="client-deployment-log-files"></a>Ügyfél-telepítési naplófájlok
Az ügyfél-telepítési és felügyeleti műveletek által használt naplófájlok kapcsolatos információkért lásd: [naplófájlok a System Center Configuration Managerben](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs).

