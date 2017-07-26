---
title: "IOS aktiválási zár kezelése |} Microsoft Docs"
description: "Kezelhető az iOS aktiválási zár a System Center Configuration Managerrel."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2745bac-e1b4-4dac-8ac7-32f1c820bc9c
caps.latest.revision: 9
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 88bef04a52f716ae13afc21c25d33dea06a3fc9c
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="manage-ios-activation-lock-with-system-center-configuration-manager"></a>Az iOS aktiválási zár kezelése a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Manager segíthet az iOS aktiválási zárának kezelésében, amely az iOS 7.1 és újabb rendszerű eszközök Find My iPhone alkalmazásának egyik funkciója. Ha a funkció be van kapcsolva, meg kell adni a felhasználó Apple ID azonosítóját és jelszavát ahhoz, hogy el lehessen végezni az alábbiak bármelyikét:

- A Find My iPhone alkalmazás kikapcsolása
- Az eszköz alaphelyzetbe állítása
- Az eszköz újraaktiválása

Ha **nem felügyelt** eszközön használja a Find My iPhone alkalmazást, az aktiválási zár automatikusan bekapcsol.

A **felügyelt eszközökön** az aktiválási zárat a Configuration Manager megfelelőségi beállításaiban kell engedélyezni.

> [!TIP]
> Az iOS-eszközök felügyelt módja lehetővé teszi az eszközök az Apple Configurator eszközzel való zárolását, így meghatározott üzleti célokra korlátozva annak funkcióit. A felügyelt mód általánosságban csak céges eszközökhöz használható.

Az aktiválási zár segít biztosítani az iOS-eszközök biztonságát, és növeli a megtalálásuk esélyét azok elvesztésekor vagy ellopásakor, ugyanakkor ez a funkció számos kihívást is jelenthet Ön, mint rendszergazda számára. Példa:

- Egy felhasználó beállítja az aktiválási zárat egy eszközön. A felhasználó később elhagyja a céget és visszaszolgáltatja az eszközt. A felhasználó Apple ID azonosítója és jelszava nélkül semmilyen módon nem lehet újraaktiválni az eszközt, még az összes adat törlése után sem.
- Szüksége van egy jelentésre az összes eszközről, amelyen engedélyezve van az aktiválási zár.
- A szervezetben egy eszközfrissítés során néhány eszközt másik részleghez szeretne rendelni. Csak azokat az eszközöket lehet újból hozzárendelni, amelyeken nincs engedélyezve az aktiválási zár.


Az Apple az ilyen problémák megoldására vezette be az aktiválási zár megkerülését az iOS 7.1-ben. Ez lehetővé teszi az aktiválási zár a felhasználó Apple ID azonosítója és jelszava nélkül való eltávolítását a felügyelt eszközökről. A felügyelt eszközök létre tudnak hozni egy eszközspecifikus aktiválásizár-áthidaló kódot, mely az Apple aktiválási kiszolgálóján van tárolva.

További részleteket az aktiválási zárról [itt](https://support.apple.com/HT201365)olvashat.

## <a name="how-configuration-manager-helps-you-manage-activation-lock"></a>Az aktiválási zár kezelése a Configuration Managerrel

A Configuration Manager kétféle módon segíthet az aktiválási zár kezelésében:

1. Az aktiválási zár engedélyezése felügyelt eszközökön.
2. Az aktiválási zár megkerülése felügyelt eszközökön.

> [!IMPORTANT]
> Az aktiválási zár nem kerülhető meg nem felügyelt eszközökön.

Vállalati eszközök esetében ez a következő üzleti előnyökkel jár:



- A felhasználó élvezheti a Find My iPhone alkalmazás biztonsági előnyeit
- Lehetővé teheti, hogy a felhasználó annak tudatában végezhesse a munkáját, hogy az eszközt ki lehet vonni vagy fel lehet oldani annak zárolását, amikor a használatának módosítására van szükség


## <a name="enable-activation-lock-on-supervised-devices"></a>Aktiválási zár engedélyezése felügyelt eszközök

A Configuration Manager megfelelőségi beállításaiban hozzon létre és telepítsen egy **iOS és Mac OS X** típusú konfigurációelemet, hogy engedélyezze az aktiválási zárat felügyelt eszközökön:

1. **iOS és Mac OS X** típusú konfigurációelemek létrehozásáról a [Konfigurációelemek létrehozása a System Center Configuration Manager ügyfélalkalmazás nélkül felügyelt iOS és Mac OS X rendszerű eszközökhöz](/sccm/compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client) című Tudásbázis-cikkből tájékozódhat.
2. A Konfigurációelem létrehozása varázsló **Rendszerbiztonság** lapján az **Aktiválási zár engedélyezése (csak felügyelt módban)** lehetőséget állítsa **Engedélyezett**értékre.
3. [Adja hozzá a konfigurációelemet egy referenciakonfigurációhoz](/sccm/compliance/deploy-use/create-configuration-baselines).
4. [Ezt a referenciakonfigurációt telepítse](/sccm/compliance/deploy-use/deploy-configuration-baselines) azokat az iOS-eszközöket tartalmazó gyűjteményen, amelyeken engedélyezni szeretné az aktiválási zárat.

> [!IMPORTANT]
> Ezt az eljárást csak akkor kövesse, ha a birtokában van az eszköz. Ha nincs, az aktiválási zár megkerülése ez esetben is megtörténik, és az eszközt éppen birtokló személynek teljes hozzáférése lesz az eszközhöz, aki így kikapcsolhatja a Find My iPhone funkciót, alaphelyzetbe állíthatja vagy újraaktiválhatja az eszközt.

Csak felügyelt eszközökön kerülheti meg az aktiválási zárat vagy kérheti le annak áthidaló kódját; ha nem felügyelt eszközön próbálja megkerülni az aktiválási zárat vagy megtekinteni az áthidaló kódot, az hibát fog eredményezni.



## <a name="view-the-activation-lock-bypass-code"></a>Az aktiválási Zárjának megkerüléséhez szükséges kód megtekintése

1. Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.
2. Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközök**elemre.
3. Válassza ki a felügyelt módban lévő regisztrált eszközt, amelyen engedélyezve van az aktiválási zár.
4. A **Kezdőlap** lap **Eszközök** csoportjában kattintson a **Távoli eszközök műveletei** > **Aktiválási zár áthidaló kódjának megjelenítése**lehetőségre.
5. Az **Aktiválási zár áthidaló kódja** párbeszédpanelben megjelenik a kiválasztott eszközhöz tartozó áthidaló kód.

## <a name="bypass-activation-lock"></a>Az aktiválási zár megkerülése

1. Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.
2. Az **Eszközök és megfelelőség** munkaterületen kattintson az **Eszközök**elemre.
3. Válassza ki a felügyelt módban lévő regisztrált eszközt, amelyen engedélyezve van az aktiválási zár.
3. A **Kezdőlap** lap **Eszközök** csoportjában kattintson a **Távoli eszközök műveletei** > **Aktiválási zár megkerülése**lehetőségre.
5. Olvassa el a figyelmeztető párbeszédpanelben megjelenő üzeneteket, majd ha befejezte, kattintson az **Igen** gombra.
6. A zárolásfeloldási kérés állapotát az alábbi helyeken ellenőrizheti:

    - Az eszköz felderítési adataiban, az eszköztulajdonságok párbeszédpanelen.
    - Az **Eszközök** nézet **Aktiválási zár megkerülésének állapota** oszlopában (alapértelmezés szerint ez az oszlop rejtett).
    - A részletek ablaktáblában az **Összefoglalás** lap **Távoli eszköz műveletadatai** szakaszában (ha egy eszköz ki van jelölve).

