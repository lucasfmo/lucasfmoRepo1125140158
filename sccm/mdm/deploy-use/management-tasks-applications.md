---
title: "Kezelheti az alkalmazásokat a System Center Configuration Managerben |} Microsoft Docs"
description: "Kezeli az alkalmazásokat a System Center Configuration Managerben."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: bc7bb99bc526ed0bbaaad15fc9af39fa8b7c3893
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="manage-applications-in-system-center-configuration-manager"></a>Kezelheti az alkalmazásokat a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Kezelheti az eszközöket a Microsoft Intune-nal vagy a Configuration Manager helyszíni Eszközkezelés típusaival kapcsolatban további alkalmazás kezelheti:
- Windows Phone-alkalmazáscsomag (*.xap fájl)
- Csomag hozzáadása iOS-hez (*.ipa fájl)
- Alkalmazáscsomag az Androidhoz (*.apk fájl)
- Alkalmazáscsomag Androidhoz a Google Playről
- Windows Phone-alkalmazáscsomag (a Windows Phone Áruházban)
- Windows Installer mobileszköz-felügyelettel
- Webalkalmazás

Ez a témakör részletes információkat létrehozását és kezelését a hibrid MDM-mel vagy a helyszíni MDM használó alkalmazások

[System Center Configuration Manager-alkalmazásokkal kapcsolatos felügyeleti feladatok](../../apps/deploy-use/management-tasks-applications.md) további általános információkat nyújt azokról a System Center Configuration Manager-alkalmazások és központi telepítési típusok kezelése.

## <a name="deploying-and-monitoring-apps"></a>Alkalmazások telepítését és megfigyelését

Telepítését és megfigyelését az alkalmazások a System Center Configuration Managerben áll a mobileszközök ugyanazzal az eljárással a helyszíni eszközök, például a hordozható és asztali számítógépek vannak. Elolvashatja, telepítését és megfigyelését alkalmazások kapcsolatos általános információkat a következő témakörök segítségével:

- [Telepíthet központilag alkalmazásokat a System Center Configuration Managerben](../../apps/deploy-use/deploy-applications.md)
- [Alkalmazások figyelése a System Center Configuration Managerben](../../apps/deploy-use/monitor-applications-from-the-console.md)

Az alábbiakban a tartsa szem előtt, telepítését és megfigyelését az alkalmazások, ha mobileszköz-kezelés jellemző szempontokat.

- MDM által regisztrált eszközök nem támogatják a szimulált központi telepítés, a felhasználói élmény vagy az ütemezéssel kapcsolatos beállításait.

- Ha már rendelkezik egy congured a központi telepítés is társíthat iOS alkalmazás-konfigurációs házirend. Lásd: [iOS-alkalmazások konfigurálása alkalmazás-konfigurációs házirendek](configure-ios-apps-with-app-configuration-policies.md).

### <a name="next-steps"></a>További lépések

Végül kívánt alkalmazás módosíthatók, távolítsa el az alkalmazást, vagy cserélje le egy már telepített alkalmazás egy új alkalmazást. Olvassa végig [frissítése és kivonása a System Center Configuration Managerrel alkalmazások](../../apps/deploy-use/update-and-retire-applications.md) ezek képességekről.

