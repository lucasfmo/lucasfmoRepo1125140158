---
title: "A 1606 alapszintű verziót tartalmazó adathordozó hely telepítése |} Microsoft Docs"
description: "Telepítse vagy frissítse a LTSB a System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4f9a5fd-f573-4b99-ad93-b2c76812e922
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 39653604ba5fd8e1fe9dd4d42889221d983f9bec
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="install-and-upgrade-with-the-version-1606-baseline-media-for-system-center-configuration-manager"></a>Telepítés és frissítés verziójával 1606 alapszintű verziót tartalmazó adathordozó a System Center Configuration Managerhez

*Vonatkozik:  A System Center Configuration Manager (aktuális ág), (hosszú távú karbantartási ág)*

Telepítő futtatásakor a verzió 1606 alapterv adathordozóról a Configuration Manager, a hosszú távú karbantartási ág vagy az aktuális ág hely System Center Configuration Manager is telepítheti.

Az alapszintű verziót tartalmazó adathordozó érhető el a DVD-n a Microsoft System Center 2016 részeként, vagy a System Center Configuration Manager (aktuális ág és hosszú távú karbantartási ág 1606) feloldása. Alapszintű verziót tartalmazó adathordozóról, lásd: [alapkonfiguráció és frissítési verziók](/sccm/core/servers/manage/updates#baseline-and-udpate-versions).


A verzió 1606 alapszintű verziót tartalmazó adathordozó használatakor a hely telepítéséhez vagy frissítéséhez van:
- A *aktuális ág hely* , amely egy olyan webhely, az első telepített használatával az 1511-es alapszintű verziót tartalmazó adathordozóról, és majd a frissített verzió 1606 plusz a 1606 összegző gyorsjavítás - KB3186654 egyenértékű.
-    Egy *LTSB hely* , amely az aktuális ág helyhez, amelyen összegző verzió 1606 plusz a 1606 gyorsjavítás - KB3186654 egyenértékű. Az alapszintű verziót tartalmazó adathordozó már tartalmazza a gyorsjavítás kumulatív frissítést.  De a LTSB nem támogatja a szolgáltatások vagy az aktuális ág, ahogy az az elérhető képességek [bemutatása, hogy a hosszú távú karbantartási ág a System Center Configuration Manager](introduction-to-the-ltsb.md).

Ha nem ismeri a System Center Configuration Manager ággal, lásd: [melyik Configuration Manager fiókirodai használandó](which-branch-should-i-use.md).




## <a name="changes-to-setup-with-the-1606-baseline-media"></a>A telepítő a 1606 alapterv adathordozó módosításai
A 1606 alapszintű verziót tartalmazó adathordozó a telepítő a Configuration Manager-ben jelenik meg a következő módosításokat.

### <a name="branch-and-edition"></a>Ág és edition
A telepítő futtatásakor most lehetősége lesz a licencelés lap, ahol kiválaszthatja a fiókiroda a Configuration Manager telepíti. Az aktuális ág vagy a LTSB licencelt való telepítése, vagy választhat, hogy az aktuális ág nem licencelt telepítésként próbaverzióját.

További információkért lásd: [licencelés és a System Center Configuration Manager az](learn-more-editions.md).

### <a name="software-assurance-expiration"></a>Software Assurance lejárata
A telepítés során lehetősége van a adja meg a **Software Assurance lejárati dátum** érték. Ez az egy választható értéket, amely tetszés szerinti emlékeztetőként is megadhat.

> [!NOTE]
> A Microsoft nem ellenőrzi a lejárati dátumot adjon meg, és ne használja ezt a dátumot licencérvényesítés.  Ehelyett használhatja a lejárati dátum emlékeztetőként. Ez akkor hasznos, mert a Configuration Manager rendszeresen ellenőrzi az új szoftverfrissítések kínált online, és a megbízhatósági szoftverlicencek állapotának a további frissítések használatára jogosult aktuális kell lennie.    

- A adhatja meg a dátumértéket a **termékkulcs** a telepítő varázsló futtatásakor a telepítő a System Center Configuration Manager verziójából származó 1606 alapszintű verziót tartalmazó adathordozóról.
- Ez a dátum kiválasztásával is megadható **Hierarchiabeállítások tulajdonságai** > **licencelés** a Configuration Manager konzolon.

További információkért lásd: "Frissítési garancián egyezmények" a [licencelés és a System Center Configuration Manager az](learn-more-editions.md).


### <a name="additional-pre-upgrade-configurations"></a>További frissítés előtti konfigurálási feladatokat
A System Center 2012 Configuration Manager a LTSB a frissítés megkezdése előtt a frissítés előtti ellenőrzőlista részeként a következő további lépéseket kell végrehajtani.  
Távolítsa el a helyrendszerszerepköröket, amely nem támogatja a LTSB:
- Eszközintelligencia-katalógus szinkronizálási pontja
- Microsoft Intune-összekötő
- Felhőalapú terjesztési pontok

További információkért lásd: [frissítése a System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).


### <a name="new-scripted-installation-options"></a>Új parancsfájlból történő telepítést beállítások
A verzió 1606 alapszintű verziót tartalmazó adathordozó egy felügyelet nélküli parancsfájl új fájlkulcs támogatja a parancsfájlból végzett telepítéseknél egy új, legfelső szintű helyéhez. Ez a telepítése egy új önálló elsődleges helyet vagy központi adminisztrációs hely hozzáadása a helybővítés részeként vonatkozik.

Ha egy felügyelet nélküli parancsfájllal licencelt ág telepítése, hozzá kell adnia a következő szakaszban, a kulcsneveket és az értékeket a parancsfájl beállítások területén. Ezeket az értékeket az aktuális ág próbaverziójának telepítése parancsfájllal történő használatához nincs szükség:  

 **SABranchOptions**
-     **Kulcsnév: SAActive**
  - Értékek: 0 vagy 1.  
  - Részletek:  0 telepíti a nem licencelt próbaverziójának aktuális ág, valamint 1 egy licencelt kiadásra.   

- **CurrentBranch**
  - Értékek: 0 vagy 1.  
  - Részletek:  0 telepíti a hosszú távú karbantartási ág, valamint 1 az aktuális ág.  

Például egy licencelt kiadásra aktuális ág telepítéséhez használhatja:

  **Kulcsnév: SABranchOptions**
   -    **SAActive = 1**
   - **CurrentBranch = 1**


> [!IMPORTANT]  
> **SABranchOptions** csak az alapszintű verziót tartalmazó adathordozó működik a telepítést. Amikor a telepítő CD-ről nem alkalmazható. A hely legújabb mappa korábban telepítette a verzió 1606 alapszintű verziót tartalmazó adathordozó használatával.
>
> **SABranchOptions** nem vonatkozik a parancsprogram-alapú frissítés a System Center 2012 Configuration Manager és az aktuális ág mindig eredményez.

További információkért lásd: [System Center Configuration Manager-helyek telepítése a parancssor használatával](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites).


## <a name="install-a-new-site"></a>Új hely telepítése
Ha a 1606 alapterv adathordozóval vagy ág új hely telepítése, használata a webhely tervezése, előkészítése, és a telepítési eljárások részletes ismertetését lásd: a [telepítése a System Center Configuration Manager-helyek](/sccm/core/servers/deploy/install/installing-sites) témakör hozzáadásával a telepítő az alábbiakat:

- A telepítés során ki kell választania a fiókiroda a Configuration Manager telepíteni kívánt, és a frissítési garancia kapcsolatos részletek is megadhat.
- Minden hely egy hierarchia ugyanazon fiókiroda kell futtatnia. Különböző helyeken lehet LTSB és az aktuális ág vegyesen hierarchiája nem támogatott.
-    Új parancsfájlból történő telepítést. További információkért lásd: "Új parancsprogrammal létrehozva telepítéstípus" a cikk korábbi részében.

## <a name="expand-a-stand-alone-primary-site"></a>Önálló elsődleges hely
A LTSB futtató önálló elsődleges hely bővítheti.  A folyamat ugyanolyan helyzetet teremt, mint egy szerint az aktuális ág helyhez:

- Az új központi adminisztrációs hely telepítésekor a telepítő az eredeti forrás-adathordozóján a LTSB hely telepítéséhez is használt kell használnia. A telepítő CD-ről. Ebben a forgatókönyvben a legfrissebb mappát nem támogatott.

További információ a hely kibővítése című "Kibővít egy önálló elsődleges helyet" [a telepítővarázslóval hely telepítése](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).

## <a name="upgrade-from-system-center-2012-configuration-manager"></a>Frissítés a System Center 2012 Configuration Managerben
Amikor frissíti a System Center 2012 Configuration Manager, a hely tervezése, előkészítése, és eljárásokat használhatja a ismertetett a [frissítése a System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager) témakör, de a következő módosítja:

**Az aktuális ág frissítés:**
- A telepítés során ki kell választania az aktuális ág, és a frissítési garancia kapcsolatos részletek is megadhat.
-     Új parancsfájlból történő telepítést. További információkért lásd: "Új parancsprogrammal létrehozva telepítéstípus" a cikk korábbi részében.

**A LTSB frissítés:**  
- A frissítés előtti ellenőrzőlista a következő további lépéseket.
- A telepítés során ki kell választania a LTSB, és a frissítési garancia kapcsolatos részletek is megadhat.
- Csak frissítheti a System Center 2012 Configuration Manager Service Pack 2 vagy a System Center 2012 R2 Configuration Manager Service Pack 1 szervizcsomaggal futtató helyen.

### <a name="in-place-upgrade-paths-for-the-1606-baseline-media"></a>Helyi a 1606 alapszintű verziót tartalmazó adathordozó frissítési útvonalai
A 1606 alapszintű verziót tartalmazó adathordozó segítségével frissítse egy licencelt kiadásra a System Center Configuration Manager a következő:
- A System Center 2012 Configuration Manager Service Pack 2.
- A System Center 2012 R2 Configuration Manager Service Pack 1.

Az adathordozó segítségével a nem licencelt próbaverzió frissítéséhez aktuális ág az aktuális ág teljes mértékben licencelt verziójára.

A hordozó nem támogatja a frissítését:
- Egyéb System Center 2012 Configuration Manager verziói.
- A Configuration Manager 2007-es vagy korábbi.
- Egy kiadási jelölt telepítése a System Center Configuration Manager.

## <a name="about-the-cdlatest-folder-and-the-ltsb"></a>Tudnivalók a CD-n. Legújabb mappa és a LTSB
A Configuration Manager hozza létre, a CD-n adathordozóval korlátozásai a következők. Legújabb mappában található a helykiszolgálón. Ezek a korlátozások vonatkoznak a LTSB futtató helyek:

A CD-n adathordozót. Támogatott legfrissebb mappát:
- A Site recovery.
- A helykarbantartás.
- További alárendelt elsődleges hely telepítésekor.

A CD-n adathordozót. Legújabb mappa nem támogatott:  
- A központi adminisztrációs hely telepítése a helybővítés részeként.

További információkért lásd: [a CD-n. Legújabb mappa](/sccm/core/servers/manage/the-cd.latest-folder).

## <a name="backup-recovery-and-site-maintenance-for-the-ltsb"></a>Biztonsági mentési, helyreállítási és a LTSB a hely karbantartása
Készítsen biztonsági másolatot, helyreállítás vagy helykarbantartás futtatása a LTSB futtató helyen, használja a útmutatás és eljárások a [biztonsági mentés és helyreállítás a System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

Használja a Configuration Manager telepítő CD-ről. A biztonsági mentés a LTSB webhely legfrissebb mappát.

