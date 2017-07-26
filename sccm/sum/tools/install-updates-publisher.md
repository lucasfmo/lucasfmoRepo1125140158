---
title: "Telepítse a frissítés-közzétevő |} Microsoft Docs"
description: "Telepítse a System Center Updates Publisher a környezetben"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab5cda93-b67c-4aa5-904d-7b63ce790aa0
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: 996766d0bd9ab2a3acb1970414f0ae511d97fbff
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="install-updates-publisher"></a>Telepítse a frissítés-közzétevő

*Vonatkozik: A System Center frissítés-közzétevő*

A jelen témakörben található információk segítségével beszerzése, telepítése és beállítása a frissítés-közzétevő a környezetben való használatra.


## <a name="prerequisites-and-limitations"></a>Előfeltételek és korlátozások
A következő részek telepítése és használata a frissítés-közzétevő és korlátozások vagy ismert problémákat a használatra vonatkozó követelményeknek.

### <a name="operating-systems"></a>Operációs rendszerek
Telepítheti és futtathatja az Updates Publisher egy a következő operációs rendszerek 64 bites verzióján. Nincsenek, legalacsonyabb szintű összesítő frissítés vagy pack követelményei.

-   Windows Server 2016 (Standard, Datacenter)
-   Windows Server 2012 R2 (Standard, Datacenter)
-   Windows 10 (Pro, Education, Pro, Education, vállalati)
-   Windows 8.1 (Professional, Enterprise)

### <a name="prerequisites"></a>Előfeltételek
A következő szükségesek az Updates Publishert futtató számítógépen.

-   **64 bites operációs rendszer**: A frissítés-közzétevő telepítéséhez használt számítógépnek 64 bites operációs rendszernek kell futnia.
-   **A WSUS 4.0-s vagy újabb**:
    -   A Windows Server telepítése az alapértelmezett felügyeleti konzolból, amellyel megfeleljen ennek a követelménynek.
    -   A Windows 10 és Windows 8.1, telepítse a [távoli kiszolgáló felügyeleti eszközei (RSAT) a Windows operációs rendszerek](https://support.microsoft.com/help/2693643/remote-server-administration-tools-rsat-for-windows-operating-systems). Ez telepíti a szükséges támogatást Updates Publisher használatáról (*API és PowerShell-parancsmagok*, és *felhasználói felület felügyeleti konzolja*).
-   **Engedélyek**:
    -   Telepítés: Helyi rendszergazda
    -   A legtöbb műveletek: helyi felhasználói
    -   Közzététel vagy WSUS igénylő műveletek: A WSUS kiszolgáló WSUS-rendszergazdák csoport tagja.

### <a name="supported-languages"></a>Támogatott nyelvek
Frissítés-közzétevő csak angol nyelven érhető el, de kezelheti az infrastruktúra egyéb nyelvekhez. A nyelvi támogatás attól függ, hogy a feladat, például a közzététel, létrehozása és szerkesztése a frissítéseket.

Exportálásakor, vagy a frissítések közzétételéhez, frissítés-közzétevő címét és a számítógép területi beállításainak az Updates Publishert futtató alapján szoftverfrissítés leírását jeleníti meg.

Például létrehozhat egy angol és spanyol nyelven címe szoftverfrissítést.

-   Ha egy számítógépen, amelynek nyelv az angol alapértelmezés szerint a frissítés hoz létre, mutatunk be, hogy a cím és egy leírást az angol.
-   Ha akkor exportálása vagy az, hogy a frissítés közzététele egy számítógépre, amelynek a területi beállítás spanyol, az adott számítógépen mutatunk be a címet és egy leírást az spanyol.

### <a name="publishing"></a>Közzététel
Ha közzéteszi a szoftverfrissítéseket, megadhatja a szoftver bináris fájl nyelve. Megadhatja, hogy a bináris nyelvsemleges-e. A következő nyelveket támogatja:

-   arab
-   Kínai (Hongkong, KKT)
-   Kínai (hagyományos)
-   kínai (egyszerűsített)
-   Cseh
-   Dán
-   holland
-   Angol
-   Finn
-   Francia
-   Német
-   Görög
-   héber
-   Magyar
-   Olasz
-   Japán
-   koreai
-   Norvég
-   Lengyel
-   portugál
-   Portugál (brazíliai)
-   Orosz
-   Spanyol
-   Svéd
-   Török

### <a name="software-update-titles-and-descriptions"></a>Szoftverek frissítési címét és leírását
A következő nyelveket támogatja software update címét és leírását.

-   Kínai (hagyományos)
-   kínai (egyszerűsített)
-   Angol
-   Francia
-   Német
-   Olasz
-   Japán
-   koreai
-   Portugál (brazíliai)
-   Orosz
-   Spanyol



## <a name="install-updates-publisher"></a>Telepítse a frissítés-közzétevő
Beolvasása a **UpdatesPubliser.msi** System Center Updates Publisher való telepítéséhez a [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=847967).

A frissítés-közzétevő telepítéséhez futtassa **UpdatesPublisher.msi** egy számítógépen, amely megfelel a *Előfeltételek*. A telepítő létrehozza a frissítés-közzétevő futtatásához szükséges fájlok a következő mappát:  *&lt;elérési&gt;\Program Files\Microsoft\UpdatesPublisher*.

Mivel ez a mappa tartalmaz az Updates Publisher használatáról szükséges összes fájlt, másolja a mappát és annak tartalmát egy új helyet, vagy a számítógép, és kövesse a frissítés-közzétevő arról a helyről. Azonban az új helyet, vagy a számítógép meg kell felelnie az Updates Publisher állításának előfeltételei.

Telepítés befejezése után futtassa **UpdatesPublisher.exe** a a *UpdatesPublisher* mappa Updates Publisher elindításához.

## <a name="next-steps"></a>További lépések
 Miután telepítette a frissítés-közzétevő, javasoljuk, hogy [beállításainak konfigurálásáról](/tools/updates-publisher-options) a frissítés-közzétevő. Egyes frissítés-közzétevő funkcióinak használata előtt konfigurálnia kell néhány beállításait.

 Azonban, ha szeretné használni az alapértelmezett beállításokat, és nem tervezi a frissítések telepítése megtörténik egy frissítési kiszolgálón vagy a kezelt eszközökre, de is ugorhat vonatkozó jogosultság [software update katalógusok kezelése](/tools/updates-publisher-catalogs), vagy [szoftverfrissítések létrehozása](/tools/create-updates-with-updates-publisher) , és hozzon létre saját frissítés katalógusok.

