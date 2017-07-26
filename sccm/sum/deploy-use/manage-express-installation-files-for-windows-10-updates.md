---
title: "Windows 10 frissítései expressz telepítési fájlok kezelni |} Microsoft Docs"
description: "A Configuration Manager támogatja az expressz telepítési fájlok a Windows 10, amely kisebb tölt le és gyorsabb telepítési biztosít az ügyfeleken."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/24/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b8d8af88-e8ac-4deb-921b-975e2d2afd80
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7b13f3dea5a3ae413ca6b8150ec24e1632a4d4d
ms.openlocfilehash: fcdcbcde61402b47871d51deba32d23867a78370
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

## <a name="manage-express-installation-files-for-windows-10-updates"></a>Windows 10-es frissítés esetén expressz telepítési fájlokat kezelése
A Configuration Manager verziója 1702 verziótól kezdve a Configuration Manager támogatja az expressz telepítési fájlok a Windows 10-frissítéseket. Ha Windows 10 támogatott verzióját használja, a Configuration Manager beállítások segítségével csak az aktuális hónap Windows 10 összegző frissítése és az előző hónap frissítés közötti változások letöltése. Az Expressz telepítés fájljai nélkül Configuration Manager letölti a teljes Windows 10-es összesítő frissítéssel (beleértve az előző hónap összes frissítését) minden hónapban. Az expressz telepítési fájlok használatával biztosít a kisebb tölt le és gyorsabb telepítési idejét, az ügyfeleken.

> [!IMPORTANT]
> Támogatja a beállítások során az expressz telepítési fájlok használata érhető el a Configuration Manager verziója 1702, az operációs rendszer esetén az ügyféltámogatás elérhető a Windows 10 1607 verziójával a Windows Update Agent frissítése. Ez a frissítés megtalálható a 2017. április 11 (frissítő kedd) a frissítések. Ezekről a frissítésekről további információkért lásd: [támogatja a cikk 4015217](http://support.microsoft.com/kb/4015217). A jövőbeli frissítésekre expressz kisebb letöltések fogja használni. Windows 10 1607 frissítés nélkül verziója és a korábbi verziók nem támogatják az expressz telepítési fájlok.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>A kiszolgálón a Windows 10-frissítés esetén expressz telepítési fájlokat a letöltésének engedélyezése
A Windows 10 expressz telepítési fájlok metaadatait szinkronizálás megkezdéséhez engedélyeznie kell azt a szoftverfrissítési pont tulajdonságai.
1.    A Configuration Manager-konzolon lépjen a **felügyeleti** > **Helykonfiguráció** > **helyek**.
2.    Válassza ki a központi adminisztrációs hely vagy önálló elsődleges helyen.
3.    A **Kezdőlap** **Beállítások** csoportjában nyissa meg a **Helyösszetevők konfigurálása**elemet, majd kattintson a **Szoftverfrissítési pont**elemre. Az a **frissítési fájlok** csoportjában válassza **töltse le az összes jóváhagyott frissítések teljes fájlokat és expressz telepítési fájlok a Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Az Expressz telepítés fájljainak letöltése és telepítése az ügyfelek támogatásának engedélyezése
Ahhoz, hogy az expressz telepítési fájlok támogatása az ügyfeleken, engedélyeznie kell az expressz telepítési fájlok az ügyfél beállításai szakaszában szoftverfrissítések ügyfeleken. Ezzel létrehoz egy új HTTP-figyelő, amely figyeli a kéréseket a megadott porton expressz telepítési fájlok letöltéséhez. Amennyiben az ügyfél beállításait ennek a funkciónak az ügyfélen a telepít, akkor megkísérli a különbözeti között az aktuális hónap Windows 10 összegző frissítése és az előző hónap frissítés letöltése (ügyfelek verziónak kell futnia. a Windows 10, hogy támogatja az expressz telepítési fájlok).
1.    Az Expressz telepítés fájljai a szoftverfrissítési pont összetevő tulajdonságai (az előző eljárásban) támogatásának engedélyezéséhez.
2.    A Configuration Manager-konzolon lépjen a **felügyeleti** > **ügyfélbeállítások**.
3.    Jelölje ki a megfelelő ügyfélbeállítások, ezt a a **Home** lapra, majd **tulajdonságok**.
4.    Válassza ki a **szoftverfrissítések** lapján konfigurálhatja **Igen** a a **engedélyezése az ügyfeleken Express frissítések telepítésének** beállítása és konfigurálása az ügyfélen a HTTP-figyelő által használt port a **Express frissítések tartalom letöltéséhez használt Port** beállítást.

