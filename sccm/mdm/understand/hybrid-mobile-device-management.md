---
title: "Hibrid mobileszköz-kezelés (MDM) – a Configuration Manager és a Microsoft Intune |} Microsoft Docs"
description: "További tudnivalók a hibrid mobileszköz-kezelés (MDM) a System Center Configuration Manager és a Microsoft Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
caps.latest.revision: 34
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: e54478a03807c939ffa64ff39a21ef6f9ea4ae2d
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hibrid mobileszköz-felügyelet a System Center Configuration Managerrel és a Microsoft Intune-nal

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


IOS, Windows és a Configuration Manager és a Microsoft Intune Android-eszközök kezelése A kezelési feladatok kezelése a Configuration Manager konzoljáról ahol elvégezhető a többi a kezelési feladatot az integrált Microsoft Intune online szolgáltatással az interneten keresztül.  A Configuration Manager segítségével biztonságos, kezelt módon lehetővé teszik a felhasználók a vállalati erőforrások eléréséhez az eszközeiken. A kezelés, vállalati adatok során, ha engedélyezi, hogy a felhasználók regisztrálhatják saját személyes vagy vállalati tulajdonú eszközök férhessenek hozzá a vállalati adatok védelme. Felügyeleti képességek eszközökön:

-   Eszközök kivonása és a rajtuk található összes adat törlése
-   Megfelelőségi beállítások (például jelszavak, biztonság, barangolás, titkosítás és vezeték nélküli kommunikáció) konfigurálása
-   Az üzletági (LOB) alkalmazások telepítése eszközökre
-   Alkalmazások telepítése a Windows Áruházhoz, a Windows Phone Áruházhoz, az App Store-hoz és Google Playhez csatlakozó eszközökre
-   Hardverleltár készítése
-   Szoftverleltár készítése beépített jelentésekkel.

Milyen új szolgáltatásairól érhetők el a hibrid MDM további talál [What's new in hibrid mobileszköz-kezelés](../understand/whats-new-in-hybrid-mobile-device-management.md).

Jelen dokumentum céljából feltételezzük, hogy a Configuration Manager segítségével kezelheti a számítógépek, és szeretné bővíteni a Configuration Manager konzol, az Intune-nal a mobileszközök kezeléséhez. Az Intune és a hibrid mobileszköz-felügyelet közötti különbségek ismertetése: [válasszon a Microsoft Intune önálló és hibrid mobileszköz-kezelés a System Center Configuration Managerrel](choose-between-standalone-intune-and-hybrid-mobile-device-management.md).

A Configuration Manager Intune-nal történő bővítése, után regisztrálni és vállalati tulajdonú eszközök felügyeletét, de a felhasználók számára személyes eszközeik regisztrálásához. Vállalat által birtokolt eszközök kezelésére is alkalmas a Configuration Manager Intune-nal.

## <a name="hybrid-mdm-enrollment"></a>A hibrid MDM-regisztráció
A hibrid felügyelet vonja az eszközöket, ezeket az eszköznek regisztrálva kell lennie a szolgáltatással. Hogyan regisztrálják az eszközöket a eszközök attól függ, az eszköz típusát, a tulajdonosi és a szükséges felügyelet szintje.
- "Megteremthetők a saját eszközök" (BYOD) regisztrációjával lehetővé teszi, hogy a felhasználók regisztrálhatják saját személyes telefonokon, táblagépeken vagy számítógépekhez.
- Vállalat által birtokolt eszközök (COD) regisztrálása lehetővé teszi, hogy a helyzetekben, például a távoli törléssel, a megosztott eszközökre és a felhasználó-eszköz kapcsolatot.
- Ha [Exchange ActiveSync](../plan-design/device-enrollment-methods.md#mobile-device-management-with-exchange-activesync-and-configuration-manager), vagy a helyszínen vagy a felhőben szolgáltatott kezelésének engedélyezéséhez, egyszerű Intune-ban nem regisztrált. Windows rendszerű számítógépek segítségével is kezelhető [Intune ügyfélszoftver](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).

