---

title: "Szoftverfrissítések szinkronizálásának kezelése |} Microsoft Docs"
description: "Ezen lépések segítségével ütemezni a szoftverfrissítések szinkronizálását, manuálisan indítsa el a szoftverfrissítések szinkronizálását, és figyelheti a szoftverfrissítések szinkronizálását."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: ea8698c4-9df5-4cf5-8b62-ab93115b4769
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: e68170a16a6a908e035247ed9c0f3cc6cdbe1983
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---

#  <a name="BKMK_SUMSync"></a> Szoftverfrissítések szinkronizálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 A Configuration Manager szoftverfrissítés-szinkronizálási folyamata letölti a szoftverfrissítési metaadatokat, amely megfelel a konfigurált. Ez magában foglalja a konkrét termékeket, besorolások és nyelvek. Általában a szoftverfrissítési pont a központi adminisztrációs helyen vagy önálló elsődleges helyen, a Microsoft Update szolgáltatásból kéri le a metaadatokat. Ezt követően a legfelső szintű hely szinkronizálási kérelmet küld más helyekre. Amikor egy hely megkapja a szinkronizálási kérelmet a szülő hely, a hely a szoftverfrissítési pont lekéri a szoftverfrissítések metaadatait a felsőbb rétegbeli a [szinkronizálási forrás](../plan-design/plan-for-software-updates.md#BKMK_SyncSource). További információ a szoftverfrissítések szinkronizálási folyamatának: [a szoftverfrissítések szinkronizálási](../understand/software-updates-introduction.md#BKMK_Synchronization).

Szoftverfrissítés-szinkronizálás a legfelső szintű helyen a szoftverfrissítési pont tulajdonságaiban ütemezhető konfigurálnia. A szinkronizálási ütemezés konfigurálását követően általában nincs szükség az ütemezés módosítására. Ha mégis szükség lenne rá, lehetőség van a szoftverfrissítések szinkronizálásának manuális kezdeményezésére is.

  > [!NOTE]  
  >  Szoftverfrissítési pontok kapcsolódnia kell a fölérendelt szinkronizálási forrás a szoftverfrissítések szinkronizálásához. Ha egy szoftverfrissítési pontot leválasztanak a saját felsőbb réteggel való szinkronizálási forrásától, a szoftverfrissítések exportálással és importálással szinkronizálhatók. Erről bővebben lásd: [Szoftverfrissítések szinkronizálása leválasztott szoftverfrissítési pontról](synchronize-software-updates-disconnected.md).  

## <a name="schedule-software-updates-synchronization"></a>Ütemezze a szoftverfrissítések szinkronizálását
A szoftverfrissítések szinkronizálásához ütemezést állít be, amikor a legfelső szintű szoftverfrissítési pont szinkronizálási ütemezett dátum és idő a Microsoft Update szolgáltatással indul. Az egyéni ütemezés lehetővé teszi a szoftverfrissítések szinkronizálásához a dátumot és időpontot, amikor a WSUS server, a helykiszolgáló és a hálózat terhelése alacsony. Például beállíthatja az ütemezést, hogy a szoftverfrissítéseket szinkronizálja a rendszer minden héten hajnali 2:00-kor. Az ütemezett szinkronizálás alatt a helyadatbázisba kerül az utolsó ütemezett szinkronizálás óta a szoftverfrissítési metaadatban történ összes változás. Ez a szoftverfrissítések új metaadataira, illetve a módosított, eltávolított vagy lejárt metaadatokra is vonatkozik.

Az alábbi eljárásokkal a legfelső szintű helyen szoftverfrissítések szinkronizálásának ütemezéséhez.  

#### <a name="to-schedule-software-updates-synchronization"></a>Szoftverfrissítések szinkronizálásának ütemezése  

  1.  A Configuration Manager-konzolon kattintson az **Adminisztráció**elemre.  

  2.  Az Adminisztráció munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Helyek**lehetőségre.  

  3.  Az eredmények ablaktáblán kattintson a központi felügyeleti helyre vagy az önálló elsődleges helyre.  

  4.  A **Kezdőlap** **Beállítások** csoportjában nyissa meg a **Helyösszetevők konfigurálása**elemet, majd kattintson a **Szoftverfrissítési pont**elemre.  

  5.  Válassza a Szoftverfrissítési pont összetevő tulajdonságai párbeszédpanelen az **Ütemezett szinkronizálás engedélyezése**elemet, majd adja meg a szinkronizálás ütemezését.  

## <a name="manually-start-software-updates-synchronization"></a>Manuálisan indítsa el a szoftverfrissítések szinkronizálása
Manuális módszerrel is kezdeményezhető a szoftverfrissítések szinkronizálását a legfelső szintű helyen a Configuration Manager konzolon a a **minden szoftverfrissítés** csomópontja a **szoftverkönyvtár** munkaterületen.  

Az alábbi eljárásokkal a legfelső szintű helyen szoftverfrissítések szinkronizálásának manuális elindításához.  

#### <a name="to-manually-start-software-updates-synchronization"></a>Manuálisan elindítani a szoftvert a frissítések szinkronizálás  

  1.  A központi adminisztrációs hely vagy önálló elsődleges helyhez csatlakozó Configuration Manager konzolon kattintson **szoftverkönyvtár**.  

  2.  A Szoftverkönyvtár munkaterületen bontsa ki a **Szoftverfrissítések** pontot, majd kattintson a **Minden szoftverfrissítés** vagy a **Szoftverfrissítési csoportok**elemre.  

  3.  A **Kezdőlap** **Létrehozás** csoportjában kattintson a **Szoftverfrissítések szinkronizálása**elemre. Kattintson az **Igen** gombra a párbeszédpanelen annak megerősítéséhez, hogy el szeretné indítani a szinkronizálási folyamatot.  

   Miután elindította a szinkronizálást a szoftverfrissítési ponton, a szinkronizálási folyamatot a Configuration Manager konzol összes szoftverfrissítési pontján figyelheti a hierarchiában. Kövesse az alábbi eljárást a szoftverfrissítések szinkronizálásának figyeléséhez.  


## <a name="monitor-software-updates-synchronization"></a>A figyelő a szoftverfrissítések szinkronizálását
Miután elindította a szinkronizálást, a hierarchia összes szoftverfrissítési pontján a folyamat figyelése a Configuration Manager konzol segítségével. Kövesse az alábbi eljárást a szoftverfrissítések szinkronizálásának figyeléséhez. Szoftverfrissítések, beleértve a szinkronizálási folyamat figyelésével kapcsolatos további információk: [szoftverfrissítések figyelése](../deploy-use/monitor-software-updates.md).

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>A szoftverfrissítések szinkronizálási folyamatának figyelése  

  1.  Kattintson a Configuration Manager konzolon **figyelés**.  

  2.  A **Figyelés** munkaterületen kattintson a **Szoftverfrissítési pont szinkronizálási állapota**elemre.  

    A Configuration Manager-hierarchia szoftverfrissítési pontjai az eredmények ablaktábláján jelennek meg. Ebben a nézetben figyelheti az összes szoftverfrissítési pont szinkronizálási állapotát. Ha a szinkronizálási folyamatról részletesebb információkra van szüksége, áttekintheti a helykiszolgálókon a <*ConfigMgrInstallationPath*>\Logs mappában található wsyncmgr.log fájlt.  

## <a name="next-steps"></a>További lépések
Szoftverfrissítések első szinkronizálása, vagy nincsenek új besorolások vagy termékek érhető el, miután be kell után [az új besorolások és termékek konfigurálása](configure-classifications-and-products.md) szoftverfrissítéseket szinkronizálja az új feltételeket.

Szükséges, a feltételeknek a szoftverfrissítések szinkronizálását követően [szoftverfrissítések beállításainak kezelése](manage-settings-for-software-updates.md).  

