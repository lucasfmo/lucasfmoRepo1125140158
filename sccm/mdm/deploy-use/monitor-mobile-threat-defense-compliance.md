---
title: "Mobile fenyegetés védelmi megfelelőségének figyeléséhez |} System Center Configuration Managerben"
description: "A figyelő a Mobile fenyegetés védelmi partner megfelelőségi állapotát a Configuration Manager manager konzolról"
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 8edf83a0f761dfc16274ce49c3aa2b878c7fe6cd
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="monitor-mobile-threat-defense-compliance"></a>**Mobile fenyegetés védelmi megfelelőségének figyelése**

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

## <a name="to-monitor-the-overall-compliance-status"></a>Az összesített megfelelőségi állapot figyelése

A mobil fenyegetés védelmi állapot figyelése:

1.  A Configuration Manager-konzolon kattintson a **figyelés** munkaterületen.

2.  Az a **figyelés** munkaterületet, kattintson arra a **biztonsági** csomópont.

Megtekintheti a megfelelőségi állapotát a különböző fenyegetések szintű visual diagram formátumban jelenik meg összegzését. Kattintson az egyes szakaszok a diagramok, például a további részletek: 

- Az eszközöket, amelyek nem megfelelő platformon száma
- Az eszköz megfelelőségi állapotát kapcsolatos hibákat

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>Az egyes megfelelőségi állapotának figyelése

Az egyes eszköz állapota is látható:

1.  A Configuration Manager-konzolon kattintson a **eszközök és megfelelőség** munkaterületen.

2.  Kattintson a **eszközök**.

> [!TIP] 
> Hozzáadhat a **fenyegetés eszközmegfelelőség** és a **eszköz veszélyforrás adott szintjéhez** oszlopok állapotát tekintheti meg. Ezekben az oszlopokban alapértelmezés szerint nem jelenik meg.

## <a name="device-threat-protection-tab"></a>Eszköz veszélyforrások elleni védelem lap

Emellett a **eszközök** képernyőn válassza ki a meghatározott eszközöket, majd kattintson a a **veszélyforrások elleni Eszközvédelem** lap, amely további adatokat szolgáltat az eszköz megfelelőségi állapotát. Az oszlopneveket és a várt értékek segítségével alatt található elemez az eszköz megfelelőségi állapotát.

> [!IMPORTANT] 
> A veszélyforrások elleni Eszközvédelem lapon csak mutatja Ha a kiválasztott eszköz mobileszköz.

|Oszlopnév|Alapértelmezés szerint látható|Leírás| 
|-|-|-|
|**Leírás**| Igen | A Mobile fenyegetés védelmi partner által biztosított a fenyegetések adatait. |
|**Utolsó frissítés időpontja**| Igen | A legutóbbi alkalommal küldött a Mobile fenyegetés védelmi partner részletes információkat az Intune-hoz fenyegetések frissítése. |
|**Fenyegetés súlyossága**| Igen | Fenyegetés súlyossági egy egyedi fenyegetés a Mobile fenyegetés védelmi partner konzolon a rendszergazda a konfiguráció alapján definíciója. Rendelkezik a következő három érték egyikét: **Low**, **Medium** or **High** |
|**Fenyegetés állapota**| Igen | A fenyegetés az eszköz aktuális állapotát. Lehetséges állapota: **Aktív**, **feloldva** vagy **figyelmen kívül hagyja:** Azt jelzi, hogy a felhasználó figyelmen kívül hagyja az eszközön a fenyegetés, azonban a fenyegetés továbbra is megtalálhatók. |
|**Fenyegetés-típus**| Igen | Mobile fenyegetés védelmi partner típusú fenyegetés. A lehetséges értékek: **App**, **File** or **OS** |
|**Az AAD Fiókazonosító**| Nem | Az Azure Active Directory egyedi azonosítója. |
|**Besorolás**| Igen | A megadott fenyegetés osztályozása Mobile fenyegetés védelmi partner. A lehetséges értékek: **Legfelső szintű engedélyező, Riskware, reklámprogramok, Chargeware, DataLeak, trójai, féreg, vírus, kiaknázásához hátsó, Botot, AppDropper, ClickFraud, levélszemét, kémprogramok, SurveillanceWare, a biztonsági rés, ismeretlen, legfelső szintű Jailbrake, kapcsolat, TollFraud, SideloadedApp** |
|**Eszközazonosító**| Nem | Az Azure Active Directory objektum jelölő azonosító a kártevőveszély-információ a munkahelyhez csatlakoztatott eszközön. |
|**Fenyegetés-azonosító**| Nem | Mobile fenyegetés védelmi partner jönnek létre, a fenyegetés egyedi azonosítója. A fenyegetés Azonosítót használja a feloldási nyomon követését. |
|**Fenyegetés URL-címe**| Nem | Ha létezik, a fenyegetés URL-hivatkozásokat biztonsági a Mobile fenyegetés védelmi partner által létrehozott felügyeleti konzol nézete a megadott fenyegetést. |

> [!TIP] 
> Ügyeljen arra, hogy engedélyezze az oszlopokat, amelyek nem **látható alapértelmezés szerint** az eszközök a mobileszköz fenyegetés védelmi megfelelőségi állapotával kapcsolatos további részletek megtekintéséhez.

