---
title: "Vállalati által birtokolt eszközök - regisztrálása a Configuration Manager |} Microsoft Docs"
description: "További információk a különböző módszereket hibrid telepítések esetén a Configuration Manager céges eszközök regisztrálására."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
caps.latest.revision: 13
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f0b503d8c9eba2dd1b6eb4c41ec40c001b727326
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-company-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Hibrid telepítések esetén a Configuration Manager a vállalat által birtokolt eszközök regisztrálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Szervezet vagy vállalat által birtokolt eszközök (COD) az eszköz és a vásárlásának módjától függően többféleképpen a felügyeletbe állapotba helyezhetők.  

## <a name="enroll-device-enrollment-program-ios-devices"></a>Készülékregisztrációs programban részt vevő iOS-eszközök regisztrálása  
 Egy regisztrációs profilt telepít "keresztül az" eszközök az Apple Device Enrollment Program keretében vásárolt. Amikor a felhasználó beállítási asszisztenst futtatja az eszközön, az eszköz regisztrálva van az Intune-ban.  DEP programon keresztül regisztrált eszközök regisztrációját nem törölhetik felhasználók. Lásd: [IOS-eszközök Eszközregisztrációs Program (DEP) regisztrálása hibrid telepítések esetén a Configuration Manager](../../mdm/deploy-use/ios-device-enrollment-program-for-hybrid.md).  

## <a name="enroll-ios-devices-with-apple-configurator"></a>Az Apple Configurator eszközzel iOS-eszközök regisztrálása  
 Ennél a módszernél a rendszergazdát, hogy USB az iOS-eszköz csatlakozni a regisztráció előkonfigurálásához Apple Configuratort futtató Mac számítógép. Ezután a felhasználóikhoz kerülnek eszközöket a felhasználók, akik a beállítási asszisztens folyamatának futtatása során munkahelyi vagy iskolai hitelesítő adataikkal konfigurálják az eszközt, és befejezik a regisztrációs folyamatot. Lásd: [IOS-eszközök hibrid regisztrálása a Configuration Manager Apple Configurator eszközzel](../../mdm/deploy-use/ios-hybrid-enrollment-using-apple-configurator.md).  

## <a name="device-enrollment-manager"></a>Az Eszközregisztráció-kezelő  
 A szervezetek a Intune használatával kezeli a nagy számú mobileszközökre egy készülékregisztráció-kezelői fiók nevű egyetlen felhasználói fiókkal. Miután létrehozta a készülékregisztráció-kezelői fiókot, a fiók használható használó kezelő több, mint a normál felhasználók számára alapértelmezés szerint engedélyezett szokásos öt eszköz regisztrálására. Csak az adott felhasználó által nem használt eszközök regisztrálása az eszközregisztráció-kezelő eszközök működik. Ezek az eszközök olyan POS- vagy segédprogram-alkalmazásokhoz, például jó, de alkalmasak olyan felhasználók, akik e-mailek vagy a vállalati erőforrásokhoz való hozzáférést. Lásd: [eszközök regisztrálása készülékregisztráció-kezelőt a Configuration Manager a](../../mdm/deploy-use/enroll-devices-with-device-enrollment-manager.md).  

## <a name="user-affinity-for-managed-devices"></a>A felügyelt eszközök felhasználói affinitás  
 A vállalati tulajdonú eszközök profilok konfigurálásakor a rendszergazda adhat meg, hogy támogatják-e a kezelt eszközök *felhasználókapcsolat* amely azonosítja az egy adott felhasználó az eszközhöz. A **user affinity** konfigurált eszközökön az alkalmazások letöltéséhez és az eszközök felügyeletéhez a Vállalati portál alkalmazást is telepítheti és futtathatja. Lásd: [felhasználókapcsolat a hibrid felügyelt eszközöket a Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

## <a name="manage-devices-with-activation-lock"></a>Az aktiválási zár eszközök kezelése  
 A Microsoft Intune segít iOS aktiválási zára, egy szolgáltatás find My iPhone alkalmazást az iOS 7.1 és újabb rendszerű eszközök kezelése. Ha a Find My iPhone alkalmazást használják egy eszközön, az aktiválási zár automatikusan engedélyezve lesz. Lásd: [kezelhető az iOS aktiválási zára a System Center Configuration Managerrel](../../mdm/deploy-use/manage-ios-activation-lock.md).

 ## <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Előzetes deklarálása IMEI- vagy iOS-sorozatszámokat rendelkező eszközök

Vállalat által birtokolt eszközök importálása az állomás nemzetközi mobilkészülék-azonosító (IMEI) számokat vagy iOS-sorozatszámokat alapján azonosíthatja. Feltöltheti az eszközök IMEI-számának tartalmazó vesszővel tagolt (.csv) fájlt, vagy meg manuálisan is beírhatja az eszközadatokat.  Lásd: [eszközök előzetes deklarálása hardver azonosítószámát](../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

