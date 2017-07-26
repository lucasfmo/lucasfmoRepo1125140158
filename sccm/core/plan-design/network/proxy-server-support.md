---
title: "Proxykiszolgáló-támogatás |} Microsoft Docs"
description: "További tudnivalók a System Center Configuration Manager helyrendszer-kiszolgálók és ügyfelek használt proxy kiszolgálók támogatása."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c4f30e4839709722b216262b21d7b51c07d24d1e
ms.openlocfilehash: dc36be47310d2c2178c974a2b503d0b5f9f6e2ec
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="proxy-server-support-in-system-center-configuration-manager"></a>Proxykiszolgáló-támogatás a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

System Center Configuration Manager helyrendszer-kiszolgálók és az ügyfelek egy proxykiszolgálót használhat.  

## <a name="site-system-servers"></a>Helyrendszer-kiszolgálók  
Ha a helyrendszer-szerepköröket kell csatlakozni az internethez, konfigurálhatja azokat egy proxykiszolgáló használatára.  

-   Helyrendszer-kiszolgálót futtató számítógépre egy olyan egy proxykiszolgálót lehet megadni, hogy ugyanazon a számítógépen az összes helyrendszer-szerepkörök által közösen használt támogatja. Ha a különálló proxykiszolgálókra különböző szerepeknek vagy egy példánya van szüksége, ezeket a szerepköröket különálló helyrendszer-kiszolgálókon kell elhelyezni.  

-   Amikor új proxykiszolgáló-beállításainak, amely már rendelkezik egy proxykiszolgálót helyrendszer-kiszolgálót konfigurál, a rendszer felülírja az eredeti konfigurációt.  

-   A proxy kapcsolatai a helyrendszerszerepkört üzemeltető számítógép **Rendszer** fiókját használják.  

A következő helyrendszerszerepkörök csatlakozni az internethez, és igényelhetnek proxykiszolgálót.  A helyrendszerszerepkörök egy kivétellel további konfiguráció nélkül képesek proxyt használni. Ez a kivétel a szoftverfrissítési pont. Az alábbi lista tartalmaz, amely egy szoftverfrissítési ponthoz szükséges további beállításokkal kapcsolatos információkat:  

**Eszközintelligencia szinkronizációs pontja** -e helyrendszerszerepkör a Microsofthoz kapcsolódik, és a proxykiszolgáló azon konfigurációját használja az Eszközintelligencia szinkronizálási pontját üzemeltető számítógépen.  

**Felhőalapú terjesztési pont** – a proxykiszolgálót a felhőalapú terjesztési pont, akár a felhőalapú terjesztési pontot kezelő elsődleges helyen a proxy beállítása.  

Ennek konfigurálásához a következőknek kell teljesülniük az elsődleges helykiszolgálóra vonatkozóan:  

-   Csatlakozni a Microsoft Azure állítsa be, felügyelete és a terjesztési pontra történő tartalomterjesztés képesnek kell lennie.  

-   Adott számítógép rendszer fiókját használja a kapcsolat.  

-   A számítógép alapértelmezett webböngésző használja.  

A felhő alapú terjesztési ponton a Microsoft Azure-ban proxykiszolgáló nem tudja beállítani.  

**Felhőcsatlakozási pont** -e helyrendszerszerepkör csatlakozik a Configuration Manager felhőszolgáltatáshoz verzió frissítések letöltése a Configuration Manager és a szolgáltatáskapcsolódási pontot futtató számítógépen beállított proxykiszolgálót használ.  

**Exchange Server-összekötő** -e helyrendszerszerepkör Exchange-kiszolgálóhoz csatlakozik, és a proxykiszolgáló azon konfigurációját használja az Exchange Server-összekötőt üzemeltető számítógépen.  

**Szolgáltatáskapcsolódási pont** -e helyrendszerszerepkör csatlakozik a Microsoft Intune és a proxykiszolgáló azon konfigurációját használja a szolgáltatáskapcsolódási pontot üzemeltető számítógépen.  

**Szoftverfrissítési pont** – Ez a helyrendszerszerepkör használhatja a proxyt, amikor csatlakozik a Microsoft Update-hez a javítókészletek letöltése és a frissítésekre vonatkozó információk szinkronizálása érdekében. Szoftverfrissítési pontok akkor használnak proxyt csak a következő beállítások Ha engedélyezi ezt a beállítást, a szoftverfrissítési pont beállítása:  

-   **Proxykiszolgáló használata a szoftverfrissítések szinkronizálásakor**  

-   **Proxykiszolgáló használata tartalom automatikus központi telepítési szabályok alkalmazásával letöltésekor** (számára elérhető, amíg ez a beállítás nem használják a másodlagos helyek szoftverfrissítési pontjaihoz.)  

Az aktív szoftverfrissítési pont lapon a helyrendszer-szerepkörök hozzáadása varázsló vagy a konfigurálja a proxykiszolgáló beállításait a **általános** lapján **szoftverfrissítési pont összetevő tulajdonságai**.  

-   A proxykiszolgáló beállításai csak a helyen lévő szoftverfrissítési pontra vonatkoznak.  

-   Proxykiszolgáló beállításai csak akkor áll rendelkezésre, ha a proxykiszolgáló már be van állítva a szoftverfrissítési pontot üzemeltető helyrendszer-kiszolgáló.  

> [!NOTE]  
>  Alapértelmezés szerint a rendszer az automatikus központi telepítési szabály futásakor az automatikus központi telepítési szabály létrehozási kiszolgálójának **Rendszer** fiókját használja az internetcsatlakozáshoz és a szoftverfrissítések letöltéséhez.  
>   
>  Ha a fiók nem férhet hozzá az internethez, szoftverfrissítések letöltése sikertelen lesz, és a következő bejegyzés kerül a ruleengine.log naplófájlba: **Nem sikerült a frissítés letöltése az internetről. Hiba = 12007.**  

#### <a name="to-set-up-the-proxy-server-for-a-site-system-server"></a>A proxykiszolgálót egy helyrendszer-kiszolgáló beállítása  

1.  Kattintson a Configuration Manager konzol **felügyeleti**, bontsa ki a **Helykonfiguráció**, és válassza a **kiszolgálók és Helyrendszerszerepkörök**.  

2.  Válassza ki a helyrendszer-kiszolgáló, a részletek ablaktáblán kattintson a jobb gombbal a szerkeszteni kívánt **Helyrendszert**, és válassza a **tulajdonságok**.  

3.  A helyrendszer tulajdonságai részen válassza ki a **Proxy** lapon, majd állítsa be az elsődleges helykiszolgáló proxybeállításait.  

4.  Válasszon **OK** való az új proxykiszolgáló-konfiguráció mentéséhez.  

