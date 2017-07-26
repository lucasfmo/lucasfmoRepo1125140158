---
title: "Az Eszközállapot-igazolás |} Microsoft Docs"
description: "További tudnivalók az Eszközállapot-igazolás funkciókat megtekinthető a Configuration Manager konzolon."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f9de33-b277-4500-acd6-e7d90a2947c9
caps.latest.revision: 17
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 54b3433a002b8ef29059bab04458138348f95d66
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="health-attestation-for-system-center-configuration-manager"></a>Állapotigazolás a System Center Configuration Managerhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A rendszergazdák megtekinthetik a [Windows 10 eszközállapot-igazolás](https://technet.microsoft.com/library/mt592023.aspx) állapotát a Configuration Manager konzolján.  Az eszközállapot-igazolással a rendszergazdák bekapcsolhatják az ügyfélszámítógépeken következő megbízható BIOS-, TPM- és rendszerindítószoftver-konfigurációkat:  

-   Korai indítású kártevőirtó – A Korai indítású kártevőirtó (ELAM) a rendszer indítása és a külső fejlesztésű illesztőprogramok inicializálása előtt nyújt védelmet a számítógépnek. [How to turn on ELAM (Az ELAM bekapcsolása) (Az ELAM bekapcsolása)](https://gallery.technet.microsoft.com/How-to-turn-on-Early-84552ec5)  
-   BitLocker – A Windows BitLocker meghajtótitkosítási szoftver segítségével a Windows operációs rendszer kötetén tárolt összes adat titkosítható.  [A BitLocker bekapcsolása](https://gallery.technet.microsoft.com/How-to-turn-on-BitLocker-34294d3d)  
-   Biztonságos rendszerindítás – A Biztonságos rendszerindítás egy biztonsági szabvány, melyet a számítógépipar szereplői fejlesztettek ki. Arról gondoskodik, hogy a számítógép kizárólag a gyártó által biztonságosnak ítélt szoftverekkel induljon el. [További tudnivalók a Biztonságos rendszerindítás szabványról (angol nyelven)](https://technet.microsoft.com/library/hh824987.aspx)  
-   Kódintegritás – A Kódintegritás funkció a memóriába való minden egyes betöltés során ellenőrzi az illesztőprogramok és rendszerfájlok integritását, ezzel magasabb fokú biztonságot garantál az operációs rendszer számára. [További tudnivalók a Kódintegritás funkcióról (angol nyelven)](https://technet.microsoft.com/library/dd348642.aspx)  

Ez a funkció elérhető a Configuration Manager által kezelt számítógépek és helyszíni erőforrások, valamint a Microsoft Intune által kezelt mobileszközök számára. A rendszergazdák meghatározhatják, hogy a jelentéskészítés a felhővel vagy a helyszíni infrastruktúrában történjen-e. Helyszíni készülékállapot-igazolás lehetővé teszi a rendszergazda nyomon követhesse internetkapcsolattal nem rendelkező számítógépek ügyfél figyelését.

## <a name="enable-health-attestation"></a>Az Állapotigazolás engedélyezése

 **Követelmények:**  

-   A Windows 10 1607 vagy Windows Server 2016-os verziója 1607 a rendszerű [engedélyezett az Eszközállapot-igazolás](https://technet.microsoft.com/windows-server-docs/security/device-health-attestation)
-    A TPM 1.2-es vagy TPM 2-t eszközök
-   A Configuration Manager-ügyfél ügynöke és has.spserv.microsoft.com (a 443-as port) közötti kommunikáció Eszközállapot-igazolási szolgáltatás (felhőfelügyelet) vagy az eszköz állapotát tanúsítvány használatára konfigurált felügyeleti ponttal (helyszíni)

### <a name="how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Az Állapotigazolás szolgáltatás kommunikációjának bekapcsolása a Configuration Manager-ügyfélszámítógépeken

Ezzel az eljárással engedélyezése az eszköz állapotigazolási állapotfigyelés az internethez csatlakozó eszközökön.

1.  A Configuration Manager konzolon válassza az **Adminisztráció** > **Áttekintés** > **Ügyfélbeállítások**elemet.  Nyissa meg a **Számítógépügynök** beállítások lapját.  
2.  Az **Alapértelmezett beállítások** párbeszédpanelen válassza a **Számítógépügynök** lehetőséget, majd görgessen le **Az állapotigazolási szolgáltatással való kommunikáció engedélyezése**elemhez  
3.  Állítsa **Az állapotigazolási szolgáltatással való kommunikáció engedélyezése** beállítást **Igen**értékre, majd kattintson az **OK**gombra.  
4. Az eszközöknek jelenteniük kell az eszközök állapotának gyűjteményeket célozhat meg.

### <a name="how-to-enable-on-premises-health-attestation-service-communication-on-configuration-manager-client-computers"></a>A helyszíni állapotigazolási szolgáltatás kommunikációjának bekapcsolása a Configuration Manager-ügyfélszámítógépeken
Ezzel az eljárással engedélyezése az eszköz állapotigazolási állapotfigyelés a helyszíni eszközök, amelyek nem kapcsolódnak az internethez.

A Configuration Manager 1702 verziótól kezdődően a helyszíni eszközök állapotfigyelő állapotigazolási szolgáltatás URL-címe lehet megadni a a felügyeleti pont internetkapcsolattal nem rendelkező ügyfél eszközök támogatásához.

1. A Configuration Manager-konzolon lépjen a **felügyeleti** > **áttekintése** > **Helykonfiguráció** > **helyek**.
2. Kattintson a jobb gombbal a felügyeleti ponttal, amely a helyszíni eszközök állapotfigyelő igazolás ügyfél támogatására, és válassza ki az elsődleges vagy másodlagos helyhez **helyösszetevők konfigurálása** > **felügyeleti pont**. A **felügyeleti pont összetevő tulajdonságai** lap megnyitásakor.
3. Az a **speciális beállítások** lapon jelölje be **Hozzáadás** , és adja meg egy érvényes a helyszíni eszközök állapotfigyelő állapotigazolási szolgáltatás URL-címe. Több URL-címeket adhat hozzá. Ha több helyszíni URL-cím van megadva, az ügyfelek összes kap, és véletlenszerűen választ ki kell használni.
4.  A Configuration Manager konzolon válassza az **Adminisztráció** > **Áttekintés** > **Ügyfélbeállítások**elemet.  Nyissa meg a **Számítógépügynök** beállítások lapját.  
5.  Az a **alapértelmezett beállítások** párbeszédpanelen jelölje ki **Számítógépügynök** majd görgessen le a **helyszíni Attestaion állapotszolgáltatás**, és **Igen**.
6. Az eszközöknek jelenteniük kell az ügyfélügynök-beállítások engedélyezése az eszköz állapotát állapotigazolási jelentés az eszközök állapotának gyűjteményeket célozhat meg.

Is **szerkesztése** vagy **eltávolítása** eszköz állapotfigyelő állapotigazolási szolgáltatás URL-címeit.

> [!NOTE]
> Ha az Eszközállapot-igazolás a frissítése előtt használt a Configuration Manager 1702, a helyszíni URL-címeket az ügyfélügynök-beállítások megadott van előre megadhat a felügyeleti pont tulajdonságai a frissítés során. A helyi ügyfelek továbbra is használja az URL-címet megadva az ügyfélügynök, amíg nem frissítik őket. Ezek ezután vált, a felügyeleti ponton megadott URL-címek egyikére.

## <a name="monitor-device-health-attestation"></a>A figyelő az Eszközállapot-igazolás

1.  Az eszközállapot-igazolás nézetének megtekintéséhez menjen a Configuration Manager konzolon a **Figyelés** munkaterületre, kattintson a **Biztonság** csomópontra, majd válassza az **Állapotigazolás**elemet.  
2.  Megjelenik az eszközállapot-igazolás.  

A Configuration Manager eszközállapot-igazolás a következőket jeleníti meg:  

-   **Health Attestation Status** (Állapotigazolási állapot) – a megfelelő, nem megfelelő, hiba és ismeretlen állapotú eszközök eloszlását jeleníti meg  
-   **Állapotigazolási jelentést küldő eszközök** – megjeleníti, hogy az eszközök hány százaléka küld állapotigazolási jelentést  
-   **Nem megfelelő eszközök ügyféltípus szerint** – a nem megfelelő mobileszközök és számítógépek részarányát jeleníti meg  
-   **Hiányzó állapotigazolással kapcsolatos főbb beállítások** – beállítás szerint osztályozva megjeleníti, hogy hány eszköznél hiányzik valamilyen állapotigazolási beállítás

Az Eszközállapot-igazolás ügyfélállapot segítségével a Configuration Manager által a Microsoft Intune-nal kezelt eszközök megfelelőségi szabályzatainak feltételes hozzáférésére vonatkozó szabályok meghatározásához. Részletes információ: [Eszközök megfelelőségi házirendjének kezelése a System Center Configuration Managerrel](/sccm/protect/deploy-use/device-compliance-policies).  

