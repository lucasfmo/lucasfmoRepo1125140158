---
title: "A Lookout integrációs hibaelhárítása |} System Center Configuration Managerben"
description: "Ez a témakör ismerteti a hibaelhárítási problémák, amelyek általában a Lookout integráció."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e36b98c7-d0f4-4dd6-bac3-6a6c4b4bf841
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 4fd2d3b8aae6a2f42e7c6a87723d16368be30984
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Hibaelhárítás a Lookout integráció az Intune-nal

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

## <a name="troubleshoot-login-errors"></a>Bejelentkezési hibák elhárítása
### <a name="403-errors"></a>403-as hiba
A 403-as hiba jelenhet meg, amikor bejelentkezik a [a Lookout MTP konzol](https://aad.lookout.com): **nincs engedélye a szolgáltatás eléréséhez** Ez akkor fordulhat elő, amikor a megadott felhasználónév nem tagja az Azure Active Directory (Azure AD) csoport, amely a Lookout MTP elérésére.

A lookout MTP van konfigurálva ahhoz, hogy a csak a felhasználók egy konfigurált Azure ad-csoport elérhető legyen. Ha nem tudja, melyik az a csoport a Lookout MTP-alapú hozzáférés van beállítva, forduljon a Lookout támogatási szolgálatához.

Felveheti a kapcsolatot a Lookout támogatását a következő módszerek:

* E-mail:enterprisesupport@lookout.com
* Jelentkezzen be a [MTP-konzol](http://aad.lookout.com), és keresse meg a **támogatási** modul.
* Ugrás: https://enterprise.support.lookout.com/hc/en-us/requests és később egy támogatási kérést.

### <a name="unable-to-sign-in"></a>Nem lehet bejelentkezni
Ha az Azure AD globális rendszergazdai jogú felhasználó nem fogadta el a kezdeti Lookout beállítás a következő hiba jelenhet meg.

![képernyőfelvétel a Lookout bejelentkezési képernyőt jeleníti meg az bejelentkezési hiba](media/lookout-consent-not-accepted-error.png)

A probléma megoldásához, a globális rendszergazdai jogú felhasználó kell https://aad.lookout.com/les?action=consent bejelentkezni, és fogadja el a rendszer a telepítő kezdeményezheti. További részletes információk találhatók [a Lookout MTP előfizetés beállítása](set-up-your-subscription-with-lookout.md) témakör

## <a name="troubleshoot-device-status-issues"></a>Eszközök állapotának kapcsolatos problémák elhárítása

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Az eszköz nem jelenik meg a Lookout MTP konzol eszközök listája

Ez az alábbi esetek egyikében fordulhat elő:
* Ha az eszköz felhasználójának nincs a **beléptetési csoport** megadott a **a Lookout MTP konzol**.  Az a **rendszer** modul, keresse fel a **Intune-összekötő** lapra, és tekintse meg a **beléptetési felügyeleti** beállításait.  Meg kell jelennie egy vagy több Azure AD-csoportokhoz regisztrálásra.  Győződjön meg arról, hogy a hiányzó eszköz birtokló felhasználó a megadott egyik része az Azure Active Directory csoportokat.  A konfigurált lekérdezési időközt tart beléptetési csoporthoz hozzáadott új felhasználó (az 5 perc az alapértelmezett érték) láthatja az eszközt, megjelennek a **eszközök** a Lookout MTP konzol modul.

* Ha az eszköz a Lookout MTP által nem támogatott.  Eszközök, amelyek nem támogatott fog megjelenni a **kezelt eszközök** a Lookout MTP konzolon connector beállításai.

### <a name="device-continues-to-be-reported-as-pending"></a>Eszköz továbbra is jelentett **függőben**

Egy eszköz, amely azt **függőben lévő** azt jelenti, hogy a végfelhasználó nem keressen olyan munkahelyi alkalmazás megnyitása és gombra kattintott a **aktiválás** gombra. Az eszköz aktiválási a Lookout munkahelyi alkalmazások a további tudnivalókért olvassa el a következő témakörben:

[Android-eszközön a Lookout for Work telepítésére kéri](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>A Lookout MTP-konzolon az eszköznek aktívként jelenik, de nem rendelkezik egy eszközön.
Ez azt jelenti, hogy az eszköz felhasználójának nincs a beléptetési csoportban, a Lookout MTP konzolon megadott.   Egy eszköz tud bejutni a állapotban van, ha a felhasználó az eszköz tulajdonosa a beléptetési csoport el lett távolítva, vagy a beléptetési csoportnak, amely a felhasználó tagja legyen el lett távolítva.

Az a **rendszer** nyissa meg a Lookout MTP konzolon modul a **Intune-összekötő** lapot, és tekintse át a **beléptetési** beállításait.  Meg kell jelennie egy vagy több Azure AD-csoportokhoz regisztrálásra.  Győződjön meg arról, hogy a felhasználó az eszköz tulajdonosa legyen-e a megadott Azure AD-csoport egyik része.

Egy eszköz ebben az állapotban van, amíg a Lookout értesítsék a felhasználót semmilyen észlelt fenyegetéssel folytatódik, de nem küld a kártevőveszély-információ az Intune-hoz.

### <a name="device-shows-disconnected-state"></a>Eszköz leválasztott állapotát mutatja.

Leválasztott azt jelenti, hogy a Lookout MTP nem egy előre beállított idő időszakban hallgatni az eszközről (alapértelmezett érték 7 nap legalább 30 nap). Ez azt jelenti, hogy vagy a vállalati portál alkalmazást, vagy keressen olyan munkahelyi alkalmazás nincs telepítve az eszközön, vagy eltávolították. Az alkalmazások újratelepítése kell a probléma megoldásához. Amikor a felhasználó megnyitja a lookout for Work alkalmazást, és aktiválja az alkalmazást, és az eszköz resyncs a Lookout MTP és az Intune.

### <a name="forcing-a-resync-on-the-device"></a>Az eszközön egy újraszinkronizálási kényszerítése
Az a **eszközök** modul a rendszergazda letiltotta az MTP-konzolon, válassza ki az eszközt, és törölheti azt.   Amikor legközelebb az eszköz tulajdonosa megnyitja keressen olyan munkahelyi alkalmazások és TAP **aktiválás**, az eszköz állapotát a teljes újraszinkronizálási fog tenni.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>Az eszköz tulajdonosa már nem használja ezt az eszközt
Kell törlése az eszközről, és kérje meg az új felhasználót a regisztrálása [ebben a témakörben](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe).


Is elvégezheti a **eszközök** a Lookout MTP konzol modul válassza **törlése**.

Mindaddig, amíg az új felhasználó a Lookout MTP-konzolon megadott beléptetési csoportok valamelyikében van, az eszköz az Azure AD hozzárendeli az eszközt, hogy az új felhasználó egyszer jelenik meg.

## <a name="compliance-remediation-workflows"></a>Megfelelőség szervizelési munkafolyamatok
[Android-eszközön a Lookout for Work telepítésére kéri]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Hárítsa el a Lookout for Work Android-eszközön található fenyegetést szeretne](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

