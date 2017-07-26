---
title: "Előzetes funkciók |} Microsoft Docs"
description: "Előzetes funkciók a System Center Configuration Managerben"
ms.custom: na
ms.date: 4/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: b12fcb3c372c34ee47306a9b536c3d0c4764b8be
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>Előzetes funkciók a System Center Configuration Managerben
*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Előzetes kiadású szolgáltatások olyan funkciókat, amelyek szerepelnek az aktuális ág éles környezetben is tesztelhessék őket. Ezeket teljes mértékben támogatottak, de továbbra is az aktív fejlesztés és módosítások fordulhat elő, amíg azok kilépni a kiadás előtti kategória.

 Előzetes funkciók használata előtt meg kell adni a hozzájárulási belül a Configuration Manager konzol előzetes verziójú szolgáltatás használatára, válassza ki, és azok használatának engedélyezése előtt.  

Egy egyszeri művelet nem vonható vissza hierarchiánként alapuló. Amíg nem adja meg a hozzájárulási, nem engedélyezhető a előzetes kiadású szolgáltatások frissítéseket is.

Hozzájárulás, biztosítva a nyissa meg a konzol **felügyeleti** > **Helykonfiguráció** > **helyek**, és válassza a **Hierarchiabeállítások**. Az a **általános** lapra, majd **előzetes kiadású szolgáltatások használandó hozzájárulás**.

 > [!NOTE]
 > Ha már engedélyezte előzetes kiadású szolgáltatások frissíti az 1602-es, a frissítés újabb verzió telepítése előtt, azokat a funkciókat is engedélyezett marad használható akkor is, ha nem ad a hozzájárulási előzetes kiadású szolgáltatások használatára.

Egy frissítés, amely tartalmazza az előzetes kiadású szolgáltatások telepítésekor ezek nem látható a frissítések és karbantartás-kezelő varázsló a frissítésben szereplő rendszeres szolgáltatásokkal:
  - **Ha adott hozzájárulási:** A frissítések és karbantartás-kezelő varázsló az előzetes funkciók engedélyezheti a frissítés telepítésekor. Ehhez egyszerűen válassza ki az előzetes funkciókat úgy, mint bármely más funkciót.     

    Megvárhatja, szükség esetén később egy előzetes verziójú funkció engedélyezéséhez a **felügyeleti** > **frissítés és karbantartás** > **szolgáltatások** a konzol csomópontjában. Az a **szolgáltatások** csomópont válassza ki a szolgáltatást, és válassza a **bekapcsolása**. Ez a beállítás nem érhető el, amíg nem adja meg a hozzájárulásukat adják. (Előtt verzió 1702, frissítés és karbantartás alatt állt **felügyeleti** > **Cloud Services**.)
  -   **Ha nem adott hozzájárulási:** Amikor telepít egy frissítést, előzetes kiadású szolgáltatások legyenek láthatók a frissítések és karbantartás-kezelő varázsló, de szürkén jelennek meg, és nem lehet engedélyezni. A frissítés telepítése után megtekintheti ezeket a funkciókat az a **szolgáltatásait** csomópont, de nem engedélyezheti ezeket után adott hozzájárulási **Hierarchiabeállítások**.

Ha egy önálló elsődleges helyen hozzájárulási rendelte, és ezután bontsa ki a hierarchia egy új központi adminisztrációs hely telepítésével, meg kell adni a hozzájárulási újra a központi adminisztrációs helyen.

 Egy előzetes verziójú funkció engedélyezésével, a Configuration Manager-hierarchia kezelője (HMAN) kell feldolgozni a módosítást, mielőtt elérhetővé válik, hogy a szolgáltatás. A módosítás következményeivel feldolgozási gyakran azonnali, de HMAN feldolgozási ciklus függően akár 30 percet is igénybe vehet. A módosítás feldolgozása után újra kell indítania a konzolt, új felhasználói Felületet, az adott szolgáltatáshoz kapcsolódó megtekintése előtt.

**A következő előzetes kiadású szolgáltatások érhetők el:**

 |Szolgáltatás          |Kiadás előtti fel van véve | A teljes szolgáltatás fel van véve|  
|------------------|---------------------|---------------------|
| Őr eszközkezelés a Configuration Managerrel |  [1702 verziója](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Ellenőrizze a végrehajtható fájlok futtatásának egy alkalmazás telepítése előtt  |   [1702 verziója](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Data Warehouse szolgáltatási pont  |  [1702 verziója](/sccm/core/servers/manage/data-warehouse) |![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| A tartalmak terjesztéséhez, az ügyfelek számára társ-gyorsítótárazás |  [1610 verziója](/sccm/core/plan-design/hierarchy/client-peer-cache) |![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Felügyeleti átjáró |  [1610 verziója](/sccm/core/clients/manage/plan-cloud-management-gateway) |![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Ügyfél adatforrások irányítópult |  [1610 verziója](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard) |![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| A Microsoft Operations Management Suite-összekötő  | [1606 verziója](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Fürttámogató gyűjtemény (a csoport-szolgáltatás) karbantartás| [Az 1602-es verzió](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![még nem](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
|Feltételes hozzáférés a System Center Configuration Manager által felügyelt számítógépekhez | [Az 1602-es verzió](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)     | [1702 verziója](/sccm/mdm/deploy-use/manage-access-to-services)                     |

