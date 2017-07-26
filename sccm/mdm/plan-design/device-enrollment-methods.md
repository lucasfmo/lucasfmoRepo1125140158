---
title: "Hibrid mobileszköz-kezelési eszközök regisztrálási módszerei |} Microsoft Docs"
description: "Eszközök regisztrálási módszereinek a hibrid mobileszköz-kezelést."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b81d06dc-3844-4117-9937-16732a227994
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: e09e639e939b846cdc162681f9d7bd4c39cd6fbf
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="overview-of-device-enrollment-methods"></a>Az eszközök regisztrálási módszereinek áttekintése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager Intune-nal bővítése után regisztrálása és vállalati tulajdonú eszközök felügyeletét, vagy a felhasználók számára személyes eszközeik regisztrálásához. Vállalat által birtokolt eszközök kezelésére is alkalmas a Configuration Manager Intune-nal.

A következő táblázat a regisztrálási módszereit, valamint a támogatott képességek. Ezek a képességek közé tartoznak:
- **Törlési** – az eszköz gyári, eltávolít minden adatot. [Eszközök kivonása](../deploy-use/wipe-lock-reset-devices.md)
- **Kapcsolat** -eszközök társítja a felhasználókat. A mobilalkalmazás-kezelés (MAM) és a feltételes hozzáférés a vállalati adatok szükséges. [Felhasználói affinitás](../deploy-use/user-affinity-for-hybrid-managed-devices.md)
- **Zárolási** megakadályozza, hogy a felhasználók az eszköz eltávolítása a felügyelet alól. iOS-eszközök felügyelt mód kérése a zárolás. [Távoli zárolás](../deploy-use/wipe-lock-reset-devices.md#remote-lock)

**iOS-regisztrálási módszerei**

| **Módszer** |    **Összes adat törlése** |    **Kapcsolat**    |    **Zárolás** | **Részletek** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD –](#byod)** | Nem|    Igen |    Nem | [További](../deploy-use/enable-platform-enrollment.md)|
|**[DEM](#dem)**|    Nem |Nem |Nem    | [További](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|
|**[ADATVÉGREHAJTÁS MEGAKADÁLYOZÁSA](#dep)**|    Igen |    Nem kötelező megadni |    Nem kötelező megadni|[További](../deploy-use/ios-device-enrollment-program-for-hybrid.md)|
|**[USB-RENDSZERGAZDAI (SA)](#usb-sa)**|    Igen |    Nem kötelező megadni |    Nem| [További](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)|

**A Windows és Android regisztrálási módszerei**

| **Módszer** |    **Összes adat törlése** |    **Kapcsolat**    |    **Zárolás** | **Részletek**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD –](#byod)** | Nem|    Igen |    Nem | [További](../deploy-use/enroll-hybrid-windows.md)|
|**[DEM](#dem)**|    Nem |Nem |Nem    |[További](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|

Adott sorozata alapján kérdést, amelyek segítenek a megfelelő metódus található című [válassza ki az eszközök regisztrálása](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>BYOD –
"Megteremthetők a saját eszközök" (BYOD)-felhasználók számára a vállalati portál alkalmazás telepítésekor és az eszköz regisztrálását. A felhasználók csatlakozni a vállalati hálózathoz való csatlakozás a tartományhoz vagy az Azure Active Directory segítségével. BYOD engedélyezése beléptetési előfeltétele a legtöbb platformra sok kezelésére. Lásd: [telepítő hibrid MDM](../deploy-use/setup-hybrid-mdm.md). ([Vissza a tábla a](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Vállalati tulajdonú eszközök
Vállalat által birtokolt eszközök (COD) kezelheti a Configuration Manager konzolon. iOS-eszközök regisztrálása közvetlenül az Apple által biztosított eszközökkel. Összes eszköztípusra rendszergazdaként vagy az eszközregisztráció-kezelő segítségével kezelője regisztrálhatók. IMEI-számmal rendelkező eszközöket is azonosítani és megjelölhető vállalati tulajdonú való kezelésére.

[A vállalat által birtokolt eszközök regisztrálása](../deploy-use/enroll-company-owned-devices.md)

### <a name="dem"></a>DEM
Az eszközregisztráció-kezelő rendszer egy különleges felhasználói fiókkal több céges eszközök regisztrálására és kezelésére használt. Kezelők is telepíthetik a vállalati portált, és több, felhasználó nélküli eszközt regisztrálhatnak. További információ [DEM](../deploy-use/enroll-devices-with-device-enrollment-manager.md). ([Vissza a tábla a](#overview-of-device-enrollment-methods))

### <a name="dep"></a>ADATVÉGREHAJTÁS MEGAKADÁLYOZÁSA
Apple eszköz beléptetési Program (DEP) felügyeleti lehetővé teszi, hogy a házirend létrehozása és alkalmazása "keresztüli" megvásárolt és a DEP által felügyelt iOS-eszközökhöz Az eszköz regisztrálva van, amikor a felhasználó először az eszköz bekapcsolása és az IOS-alapú beállítási asszisztenst futtatja. Ez a metódus támogatja **IOS-eszközök felügyelt** módját, amely a következő funkciókat engedélyezi:
  -    Zárolt regisztráció
  -    Feltételes hozzáférés
  -    Függetlenítés észlelése
  -    Mobilalkalmazás-kezelés

További információ [DEP](../deploy-use/ios-device-enrollment-program-for-hybrid.md). ([Vissza a tábla a](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-RENDSZERGAZDAI (SA)
Az USB-csatlakozóval csatlakoztatott, beállítási Asszisztenssel való regisztrációt. A rendszergazda létrehoz egy házirendet, és exportálja azt az Apple Configuratorba. USB-csatlakozóval csatlakoztatott, vállalati tulajdonú eszközök előkészítése házirend. A rendszergazdának minden eszközt manuálisan kell regisztrálnia. A felhasználók megkapják az eszközeiket, és futtassa a beállítási asszisztens, az eszköz regisztrálását. Ez a metódus támogatja **IOS-eszközök felügyelt** módját, amely a következő funkciókat engedélyezi:
  -    Feltételes hozzáférés
  -    Függetlenítés észlelése
  -    Mobilalkalmazás-kezelés

További információ [Telepítősegéddel végzett regisztráció az Apple Configurator eszközzel](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md). ([Vissza a tábla a](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-configuration-manager"></a>Mobileszköz-kezelés az Exchange ActiveSync és a Configuration Manager
Mobileszközök, amelyek nincsenek regisztrálva, de az Exchange ActiveSync (EAS) csatlakozzon, amely EAS MDM-szabályzat használata az Intune által kezelhető. Intune-ban az Exchange-összekötő segítségével kommunikál az EAS, a helyszíni és felhőben üzemeltetett.

[Mobileszköz-kezelés az Exchange ActiveSync és az Intune-ban](../deploy-use/manage-mobile-devices-with-exchange-activesync.md)

