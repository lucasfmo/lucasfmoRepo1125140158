---
title: "A System Center Configuration Manager további kezelésének beállítása |} Microsoft Docs"
description: "A System Center Configuration Manager további kezelésének beállítása."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4877d674-6bbc-4e16-810c-daad70c74daa
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 947d2a85f2ac68c7ccaf9a1237fd60e89e7d1d10
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="set-up-additional-management-with-system-center-configuration-manager"></a>A System Center Configuration Managerrel további kezelésének beállítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

(Választható) További felügyeleti beállíthat eszközök regisztrálása előtt. Kezelési megoldásokba hozható létre és telepítése után az eszközök regisztrálása, bár számos szervezet szeretné telepíteni őket a felügyeleti eszközök kerülnek.

**Konfigurációelemek** melyekkel kezelheti a beállításokat, például a PIN kódot, vagy a regisztrált eszközökön eszközplatform alapján titkosítás megkövetelése:
- [Windows 10 és Windows 8.1-eszközök](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Windows Phone-eszközök](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)
- [iOS és Mac-eszközök](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)
- [Android és Samsung KNOX Standard eszközökhöz](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)

**Alkalmazások** kezelt eszközökre telepíthető:
- [iOS-alkalmazások](creating-ios-applications.md)
- [A Mac-alkalmazások](../../apps/get-started/creating-mac-computer-applications.md)
- [Windows-számítógépes alkalmazások](../../apps/get-started/creating-windows-applications.md)
- [Windows Phone-alkalmazások](creating-windows-phone-applications.md)
- [Az Android-alkalmazások](creating-android-applications.md)

**Feltételes hozzáférés** lehetővé teszi, hogy a kezelése, beleértve a vállalati erőforrásokhoz való hozzáférés:  
- [E-mail-hozzáférés](manage-email-access.md)
- [SharePoint-hozzáférés](manage-sharepoint-online-access.md)
- [Skype vállalati hozzáférés](manage-skype-for-business-online-access.md)
- [Dinamikus CRM Online](manage-dynamics-crm-online-access.md)

**Többtényezős hitelesítés (MFA)** lehetővé teszi, hogy egynél több ellenőrzési metódus, amely egy kritikus fontosságú második biztonsági réteget ad a felhasználói bejelentkezéseket és tranzakciókat igényelnek.
Korábban kerülne az Intune-konzolon, vagy a Configuration Manager konzol többtényezős hitelesítés beállítása az Intune-ban történő regisztrációt. Most, hogy bejelentkezni a [Microsoft Azure-portálon](https://manage.windowsazure.com) Intune hitelesítő adataival, és az Azure AD MFA-beállítás konfigurálásához. További tudnivalókért lásd: [a Microsoft Intune a többtényezős hitelesítést](https://aka.ms/mfa_ad).

> [!div class="button"]
[< Előző lépés](enable-platform-enrollment.md)[következő lépés >  ](verify-mdm-configuration.md)

