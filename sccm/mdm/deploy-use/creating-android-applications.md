---
title: "Az Android-alkalmazások létrehozása |} Microsoft Docs"
description: "Tekintse meg, milyen szempontokat kell figyelembe kell venni a fiók létrehozása és központi telepítésekor az alkalmazások Android-eszközökhöz."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 27a92dc1c3710ff55f0b145386319dda371533d9
ms.openlocfilehash: d3b20a59a9147e09e58f04f83f97fd72ebfef5a1
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>Az Android-alkalmazások létrehozása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager alkalmazás rendelkezik egy vagy több központi telepítési típust, amely a telepítési fájlokat és információkat tartalmazzák, amelyek szükségesek a szoftverek eszközre telepítéséhez. A központi telepítési típus szabályokat, amelyek adja meg, mikor és hogyan a szoftver központi telepítése is rendelkezik.  

 A következő módszerekkel hozhatók létre alkalmazások:  

-   Az alkalmazás és központi telepítési típusok automatikus létrehozása a alkalmazástelepítő fájlok olvasásával.  
-   Az alkalmazás manuális létrehozása központi telepítési típusok későbbi hozzáadásával.  
-   Alkalmazás importálása fájlból.  

Lásd: [alkalmazás létrehozása varázsló elindítása](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard) a Configuration Manager-alkalmazások létrehozása és központi telepítési típusok szükséges lépéseket. Emellett vegye az alábbiakat is figyelembe létrehozása és központi telepítésekor az Android-eszközökhöz készült alkalmazások.  

## <a name="general-considerations-for-android-apps"></a>Android-alkalmazásokkal kapcsolatos általános szempontokról

A Configuration Manager Android rendszerhez a következő alkalmazástípusok telepítését támogatja:

|Eszköz típusa|Támogatott fájlok|
|-|-|
|Android|.apk|

A következő központi telepítési műveletek támogatottak:

|Eszköz típusa|Támogatott műveletek|
|-|-|
|Android|**Rendelkezésre álló**, **szükséges**. A felhasználónak bele kell egyeznie a telepítése vagy eltávolítása.

## <a name="approve-and-deploy-android-for-work-apps"></a>Jóváhagyhatja és telepítheti az Android munkahelyi alkalmazások
A Configuration Manager rendszergazdaként is jóvá és telepíthet alkalmazásokat a a [a munkahelyi webhely lejátszása](https://play.google.com/work), és az alkalmazások telepítése a munkahelyi eszközök felügyelt Android.

Kövesse az alábbi lépéseket a Play Store munkahelyi alkalmazások, a Configuration Manager konzol szinkronizálása őket, és munkahelyi eszközök felügyelt Android történő központi telepítésére. Alkalmazások telepítése a felhasználók munkahelyi profilok, lesz szüksége a Play áruházban a munkahelyi alkalmazások jóváhagyásához, és majd a az alkalmazásokat a Configuration Manager konzol szinkronizálása.

1. Nyisson meg egy böngészőt, és navigáljon: https://play.google.com/work.
2. Jelentkezzen be, akkor az Intune-bérlő kötve Google-rendszergazdai fiók használatával.
3. Tallózással alkalmazásokat szeretne telepíteni a környezetben, és válassza a **jóváhagyás** minden Android for Work az alkalmazás elérhetővé tétele.
4. Nyissa meg a Configuration Manager konzol **rendszergazda** > **áttekintése** > **Felhőszolgáltatások** > **Android for Work** válassza **szinkronizálási**.
5. Várjon, amíg az alkalmazások szinkronizálása, és folytassa a akár 10 percet **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **Áruházbeli alkalmazások Licencadatai**.
6. Válassza ki egy alkalmazást a Play áruházból munka szinkronizálva, és válassza a **alkalmazás létrehozása**.
7. A varázsló befejezéséhez, és válassza a **Bezárás**.
8. Ugrás a **szoftverkönyvtár** > **áttekintése** > **Alkalmazáskezelés** > **alkalmazások**, válassza ki az Android munkahelyi alkalmazás és központi telepítése a szokásos módon.

Play szinkronizálva munkahelyi alkalmazásokat a Configuration Managerrel, jóvá kell hagynia a legalább egy alkalmazást a munkahelyi webhely Playről először.

