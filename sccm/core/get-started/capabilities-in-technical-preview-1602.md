---
title: "A Technical Preview 1602-es Configuration Manager lehetőségeit"
description: "További tudnivalók a Technical Preview elérhető szolgáltatások a System Center Configuration Manager, az 1602-es verzió."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 2354f885aaf69683004ad78f0e1978e78fee9145
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>A Technical Preview 1602-es rendszer képességei Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (Technical Preview-ban)*

Ez a cikk bemutatja a Technical Preview a System Center Configuration Manager, 1602-es verziójában elérhető funkciókat. A verzió frissítése, és új képességeket adhat a Configuration Manager technical preview-helyeken telepítheti. A technical preview ezen verziója a telepítés előtt tekintse át a bevezető témakört, [a System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md), megismerkedhet a általános követelményei és korlátozásai technikai előzetes kiadásról, hogyan használja, és hogyan visszajelzést a technical Preview verzióinak szolgáltatásai közötti frissítéséhez.  

 Új funkciókat próbálhatja ki ebben a következők:  

##  <a name="BKMK_MDM"></a>Mobileszköz-felügyelet fejlesztései  

### <a name="ios-activation-lock"></a>iOS aktiválási zára  
 A System Center Configuration Manager segíthet az iOS aktiválási zárának kezelésében, amely az iOS 7.1 és újabb rendszerű eszközök Find My iPhone alkalmazásának egyik funkciója. Ha a Find My iPhone alkalmazást használják egy eszközön, az aktiválási zár automatikusan engedélyezve lesz. Az engedélyezése után meg kell adni a felhasználó Apple ID azonosítóját és jelszavát ahhoz, hogy el lehessen végezni a következők bármelyikét:  

-   A Find My iPhone alkalmazás kikapcsolása  

-   Az eszköz alaphelyzetbe állítása  

-   Az eszköz újraaktiválása  

 A Configuration Manager kérhetnek a felügyelt és a felügyeletlen, iOS 7.1 és újabb rendszerű eszközök aktiválási Zárának állapotát. A felügyelt eszközök esetén az Intune le tudja kérdezni az aktiválásizár-áthidaló kódot, és közvetlenül ki tudja adni azt az eszköznek.  

 További információkért lásd: [az iOS-eszközök aktiválási zár megkerülésével a Configuration Manager védelme](/sccm/mdm/deploy-use/manage-ios-activation-lock)  

##  <a name="BKMK_SC1601"></a>Az 1602-es verziójában a szoftverközpont fejlesztései  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Frissítse a számítógép számítógép- és felhasználói házirendet a Szoftverközpontból  
 Egy új beállítás **házirend szinkronizálása** hozzá lett adva a **beállítások** > **számítógép-karbantartás** Szoftverközpont a számítógép frissíti a Configuration Manager-számítógép- és felhasználói házirendjét okozó oldalán.  

##  <a name="BKMK_Win10Servicing"></a>A Windows 10 karbantartásának fejlesztései  
 Az 1602-es Technical Preview a Windows 10 karbantartásának következő fejlesztései jelentek meg:  

-   Új szűrőbeállítások a karbantartási tervek.  Most már szűrhet az **nyelvi**, **szükséges**, és **cím**. Csak a megadott feltételeknek megfelelő frissítések lesznek hozzáadva a társított központi telepítéshez.  

-   Ha bejelöli a **frissítések** szoftverfrissítési besorolás szinkronizálási frissíti, egy figyelmeztető párbeszédpanel jelenik meg, amely azt jelzi, hogy a WSUS [3095113-as gyorsjavítást](https://support.microsoft.com/kb/3095113) szoftverfrissítések sikeres szinkronizálásához szükséges és a Windows 10 karbantartásának megfelelő működéséhez.  A párbeszédpanelről megnyithatja a Tudásbázis a gyorsjavítások.  

-   Windows 10 frissítései most már csak a megjelenített a **Windows 10 karbantartása** \ **minden Windows 10-frissítés** csomópont a Configuration Manager konzol. Ezek a frissítések továbbiakban nem jelennek meg a **szoftverfrissítések** \ **minden szoftverfrissítés** csomópont.  

-   Egy párbeszédpanelt, melyben tájékoztatja őket arról, hogy frissíti az operációs rendszer végfelhasználók számára a Windows 10 frissítési csomagjait kell adnia.  

