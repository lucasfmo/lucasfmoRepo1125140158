---
title: "A System Center Configuration Manager és a Microsoft Intune hibrid Android-eszközök kezelésének beállítása |} Microsoft Docs"
description: "A Configuration Manager és az Intune Android rendszerű mobileszközök felügyeletének előkészítéséhez."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: 9
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 27a92dc1c3710ff55f0b145386319dda371533d9
ms.openlocfilehash: 0e93cd55ce49afb6395dcbe758c933bf509dd367
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hibrid Android-eszközkezelés beállítása a System Center Configuration Managerrel és a Microsoft Intune-nal

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A témakörben leírtak segítségével az informatikai rendszergazda hibrid Android-és Android munkahelyi eszközök regisztráláshoz. A rendszergazda ezután használhatja a System Center Configuration Manager beállított Microsoft Intune-előfizetés az eszközök felügyeletére. A Google Play áruházból letölthető az Androidos munkahelyiportál-alkalmazást, amellyel beléptethetők az Android-(beleértve a Samsung KNOX Standard) és az Android munkahelyi eszközök. 

A Configuration Manager rendszergazdaként a megfelelőségi beállítások kezeléséhez, törlési vagy Android-eszköz törlése, telepítheti alkalmazásokat, és szoftver- és Hardverleltár készítését. Ha az Androidos munkahelyi portál alkalmazás nincs telepítve az Android-eszközökön, majd nem lesz az összes felügyeleti funkcióit biztosítja (például a leltári és megfelelőségi beállítások), de továbbra is telepíthet alkalmazásokat Androidos eszközökre.  

## <a name="enable-android-enrollment"></a>Android-eszközök regisztrációjának engedélyezése  
Az alábbi lépéseket a munkahelyi profil (Ez azt jelenti, hogy a "klasszikus Android" beléptetési) nélkül Android-eszközök kezelése a Configuration Manager segítségével.

1. Mielőtt bármely platformhoz regisztráció beállítása az Előfeltételek és eljárások alapján Befejezés [telepítő hibrid MDM](setup-hybrid-mdm.md).  
2. A Configuration Manager konzolján a a **felügyeleti** munkaterületen, válassza a **áttekintése** > **Felhőszolgáltatások** > **Microsoft Intune-előfizetés** , és válassza az Intune-előfizetés.  
3. Az a **Home** lapra a **előfizetés** csoportjában válassza **platformok konfigurálása** > **Android**.  
4. Az a **Microsoft Intune-előfizetés tulajdonságai** párbeszédpanelen válassza ki a **Android** fülre és ellenőrizze a **Android-igénylés engedélyezése** mezőbe.  

 Miután elkészült a beállítással, kell tudassa a felhasználókkal, hogyan regisztrálhatják eszközeiket. Lásd: [Mit kell tudniuk a felhasználóknak eszközeik regisztrálásáról?](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) Ezek az információk a Microsoft Intune és a Configuration Manager által felügyelt mobileszközökre egyaránt vonatkoznak.

## <a name="enable-android-for-work-enrollment"></a>Android engedélyezi a munkahelyi
Az alábbi lépéseket a munkahelyi profil (Ez azt jelenti, hogy a "klasszikus Android" beléptetési) nélkül Android-eszközök kezelése a Configuration Manager segítségével.

1. https://accounts.google.com/SignUp munkahelyi rendszergazdai fiókot használja az Android Google-fiók létrehozása. Vagy, jelentkezzen be a fiókot, amely az összes Android munkahelyi felügyeleti feladatok az adott Intune-bérlőt lesz társítva. Ez lehet egy Google-fiókba, amelyet használ a rendszergazdákat, akik Android-eszközök kezeléséhez. Ez az a szervezet által használt kezelésére és alkalmazások közzététele a Play munkahelyi konzol a Google-fiók. Ehhez a fiókhoz használandó hagyja jóvá a Play Store munkahelyi alkalmazásokat, így nyomon követjük, hogy a fiók nevét és jelszavát.
2. Android-eszközök regisztrációjának engedélyezéséhez az Intune-bérlőjéhez tartozik, amely a Configuration Managerben kezeli a Google-fiók kötés:
   1. A Configuration Manager konzolján a a **felügyeleti** munkaterületen, válassza a **áttekintése** > **Felhőszolgáltatások** > **Microsoft Intune-előfizetések** , és válassza az Intune-előfizetés.
   2. Az a **Home** lapra a **előfizetés** csoportjában válassza **platformok konfigurálása** > **Android for Work**.
   3. A párbeszédpanelen válassza a **Android konfigurálása az Intune-konzolon munka**. Az Intune-konzolon megnyitása a böngészőben.
   4. Az Intune rendszergazdai hitelesítő adatok segítségével jelentkezzen be az Intune-portál.
   5. Válasszon **konfigurálása** Google Play áruházból Android munkahelyi webhely megnyitásához.
   6. A Google bejelentkezési lapon adja meg a Google-fiók hitelesítő adatait az 1. lépés, és adja meg a vállalati adatok.
3. Amikor visszatér az Intune-portál, Android for Work engedélyezve van, és három regisztrációs beállítások érhetők el Android munkahelyi eszközök:
   - **Az összes eszköz kezelését, Android** (letiltva). Minden Android-eszközök, beleértve az eszközök, amelyek támogatják az Android for Work hagyományos Android-eszközök regisztrálása.
   - **Támogatott eszközök munkára Android rendszer kezelése** (engedélyezve). Minden olyan eszköz, amely támogatja az Android for Work munkahelyi eszközök regisztrálása, Android. Bármely Android-eszköz nem támogatja az Android for Work mint egy hagyományos Android-eszköz regisztrálva van.
   - **Ezek a csoportok csak a felhasználók által támogatott eszközök munkára Android rendszer kezelése** (csak az egyes csoportok engedélyezve). Lehetővé teszi, hogy a felhasználók korlátozott számú munkahelyi felügyeleti célozhat meg Android. Eszközök, amelyek támogatják az Android for Work be vannak léptetve, Android munkahelyi eszközök csak akkor, ha a kijelölt csoportok tagjai lépteti be azokat. Minden egyéb eszköz regisztrált Android-eszközök.

> [!NOTE]
> Egy ismert probléma megakadályozza, hogy a **kezelése támogatott eszközök csak ebben a csoportokban lévő felhasználók Android for Work** várt módon működik parancsát. A felhasználói eszközök az Azure ad-ben megadott helyett Android for Work Android, csoportok fognak beléptetni. Ahhoz, hogy a munka Android, kell használnia a **munka Android rendszer összes támogatott eszközök kezelése** lehetőséget.


Miután elkészült a beállítással, kell tudassa a felhasználókkal, hogyan regisztrálhatják eszközeiket. Lásd: [Mit kell tudniuk a felhasználóknak eszközeik regisztrálásáról?](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) Ezek az információk a Microsoft Intune és a Configuration Manager által felügyelt mobileszközökre egyaránt vonatkoznak.

A kötés befejezésekor megjelenik a a fiók nevét és a szervezet neve, az Intune-portálon. Ezen a ponton zárja be mindkét böngészőkben.

### <a name="enroll-an-android-for-work-device"></a>Az Android munkahelyi eszköz regisztrálása
A felhasználók hogyan Android igényléséhez munkahelyi eszközök hasonlít a regisztrációt az Android. Felhasználók letöltheti és telepítheti a vállalati portál alkalmazás Android a mobileszközükön. Az alkalmazás kéri a munkahelyi profilt létrehozni a regisztrációs folyamat részeként. A munkahelyi profil létrehozása után felhasználók a vállalati portál felügyelt verzióját kell váltania. A felügyelt vállalati portál jobb alsó sarokban kis narancssárga táskát címkéje.

### <a name="manage-android-for-work-devices"></a>Android munkahelyi eszközök kezelése
Miután engedélyezte a Android munkahelyi regisztrálásra, végezheti el az alábbi felügyeleti feladatokat az Androidos munkahelyi eszközök:
- [Alkalmazások jóváhagyása](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Konfigurációelemek létrehozása](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [A megfelelőségi beállítások kezeléséhez](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [Az e-mail profilok kezeléséhez](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Szelektíven törölheti a munkahelyi profil](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)

> [!div class="button"]
[< Előző lépés](create-service-connection-point.md)[következő lépés >  ](set-up-additional-management.md)

