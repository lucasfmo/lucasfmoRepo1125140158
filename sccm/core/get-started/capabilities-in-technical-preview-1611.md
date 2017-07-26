---
title: "A Technical Preview-ban 1611 Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, 1611 verziója."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d2ad00e8-9f10-41b6-816a-d8542c23a22e
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 5e77ebbfd3f3d573d903fe58024a22feb9884e4a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1611-for-system-center-configuration-manager"></a>A rendszer 1611 Technical Preview képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*



Ez a cikk ismerteti az új szolgáltatásokat, amelyek a Technical Preview a System Center Configuration Manager, 1611 verzió érhető el. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.    

**A Technical Preview kiadással kapcsolatos ismert problémák:**   
- ***Előfeltételek állapotát***: 1611 verzió telepítésekor Előfeltételek összesített állapotát lehet megjeleníteni, mivel figyelmeztetésekkel lefutott, de nem jelenik meg, hogy a figyelmeztetések mely előfeltételek. Ezt okozhatja a következő két Előfeltételek:
  - SQL-Index létrehozása memóriával kapcsolatos lehetőségek
  - Ellenőrzi az SQL Server támogatott verziójára  

 Mivel ezek csak a figyelmeztetések, akkor figyelmen kívül hagyható.

- ***PowerShell***: Amikor a Configuration Manager konzoljáról csatlakozik a Windows PowerShell, a következő hiba akkor fordulhat elő: **Microsoft.ConfigurationManagement.PowerShell.Types.ps1xml kabinetfájl nincs digitálisan aláírva**.  

   A megoldás azáltal, hogy bizonyos fájlok 1610 verziójából származó aláírt verziók. A következő kiterjesztésű fájlok a **&lt;telepítési könyvtár > \AdminConsole\bin\**  a verzió 1610 telepítési mappájában: **.psd1**, **.ps1xml**, és **.psm1**. Illessze be ezeket a fájlokat, azokat a **&lt;telepítési könyvtár > \AdminConsole\bin\**  mappa a Technical Preview 1611 telepítésében, felülírja a fájlokat 1611 verzióját.


**Új funkciókat próbálhatja ki ebben a következők:**  

## <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Elérhető központi telepítések és a feladatütemezés tartalmának előzetes gyorsítótárazása
A technical preview esetében az elérhető központi telepítések és a feladatütemezések választhatja ki, hogy az ügyfelek csak a kapcsolódó tartalom letöltése előtt a felhasználó telepíti a tartalmat az előzetes szolgáltatás használatához.

Például tételezzük fel kívánt feladatütemezés központi telepítése Windows 10 helyi frissítési, csak egy feladatütemezést szeretné, hogy az összes felhasználó számára, és több architektúrák és/vagy nyelveken. Az aktuális ág, ha az elérhető központi telepítés létrehozásához, majd a felhasználó rákattint **telepítése** akkori letölti a tartalmat, a Szoftverközpont. Ez biztosítja, hogy a további időt megkezdheti a telepítés előtt. Azt is megteheti az aktuális ág Ha hoz létre az elérhető feladatütemezéseket, az összes tartalmat a feladatütemezésben hivatkozott le. Ez magában foglalja az operációs rendszer verziófrissítő csomagjának összes nyelvekhez és architektúráinak megfelelően. Egy körülbelül 3 GB-nál, ha a letöltőcsomag Igen tekintélyes lehet.

A tartalom előzetes funkció lehetővé teszi a beállítás lehetővé teszi az ügyfél csak a megfelelő tartalom letöltésére, amint azt a központi telepítés kap. Ezért, amikor a felhasználó kattint **telepítése** a Szoftverközpontban, készen áll a tartalmat, és a telepítés megkezdése gyorsan, mert a tartalom a helyi merevlemez-meghajtón.

### <a name="to-configure-the-pre-cache-feature"></a>Az előzetes szolgáltatás konfigurálása

1. Operációs rendszer adott architektúrák és nyelvek frissítési csomagokat hozzon létre. Adja meg a architektúra és nyelvi a **adatforrás** a csomag fülre. A nyelv, használja a decimális átalakítás (például 1033 az angol nyelvű tájékoztatáshoz decimális és 0x0409 megfelel a hexadecimális). További információkért lásd: [hozzon létre egy feladatütemezést az operációs rendszer verziófrissítéséhez](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    Az architektúra és nyelvi értékek segítségével felel meg a feladat feladatütemezési lépés feltételeket, amelyek annak meghatározásához, hogy az operációs rendszer verziófrissítő csomagjának előre gyorsítótárazza a következő lépésben létrehoz.
2. Hozzon létre egy feladatütemezést, a különböző nyelvekhez és architektúrák feltételes lépéseit. Például angol nyelvű létrehozhat egy lépést, a következőhöz hasonló:

    ![előtti gyorsítótár tulajdonságai](media/precacheproperties2.png)

    ![előtti gyorsítótár beállításai](media/precacheoptions2.png)  

3. A feladatütemezés központi telepítése. Az előzetes szolgáltatás számára konfigurálja a következőket:
    - Az a **általános** lapon jelölje be **előre letölteni a tartalmat a Feladatütemező**.
    - A a **központi telepítési beállítások** lapra, konfigurálja a feladatütemezést a **elérhető** a **célú**. Ha létrehoz egy **szükséges** központi telepítését, az előzetes funkciók nem működnek.
    - Az a **ütemezés** lapon, az a **ütemezni, amikor a központi telepítés rendelkezésre áll** beállításnál válassza ki a jövőben egy időpontot, amely az ügyfelek elegendő idő előre a tartalom gyorsítótárazása, mielőtt a központi telepítést szeretné elérhetővé tenni a felhasználók számára. Például beállíthatja az elérhetőséget 3 órát a jövőben hagyjon elegendő időt a tartalmat előre összeállított kell lennie.  
    - Az a **terjesztési pontok** lapon a **központi telepítési beállítások** beállításait. Ha a tartalom a felhasználó a telepítés megkezdése előtt nincsenek gyorsítótárazva az ügyfélen előre, ezeket a beállításokat használja.


### <a name="user-experience"></a>A felhasználói felületet
- Ha az ügyfél megkapja a központi telepítés házirendet, elindul, a tartalmat előre gyorsítótárazásához. Ez magában foglalja az összes hivatkozott tartalom (a többi csomag típus), és csak az operációs rendszer verziófrissítő csomagjának, amely megfelel az ügyfél a feltételek alapján, hogy megadta-e a feladatütemezés.
- Ha a központi telepítést szeretné elérhetővé tenni a felhasználóknak (beállítása a **ütemezés** lapon a központi telepítés), egy értesítés jeleníti meg tájékoztatják a felhasználókat az új központi telepítés kapcsolatos, és a központi telepítés látható lesz a Szoftverközpontban. A felhasználó megnyithatja a szoftverközpont, és kattintson a **telepítése** a telepítés elindításához.
- Ha a tartalom nem teljesen előre összeállított, akkor a megadott beállításokat fogja használni a **rendszerbe állítási beállításának** lapon. Azt javasoljuk, hogy nincs-e elegendő idő között a központi telepítés létrehozásakor és az idő, amelyben a központi telepítés felhasználók számára engedélyezése az ügyfelek elegendő idő előzetes gyorsítótárazása a tartalom elérhetővé válnak.


## <a name="see-also"></a>Lásd még:
[A System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md)

