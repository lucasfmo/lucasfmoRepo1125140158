---
title: "Válassza ki azt az Intune önálló vagy hibrid MDM |} Microsoft Docs"
description: "Válassza ki, hogy hibrid mobileszköz-kezelés az Intune és a Configuration Manager telepíti, vagy futtassa az Intune önálló verziójának."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: cbdcf686b9565c56c7a6fca6086d94d9e45f641a
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Választás a Microsoft Intune önálló és hibrid mobileszköz-kezelés a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A legfontosabb gyakran feltett kérdés a mobileszköz-kezelés (MDM) a Microsoft Intune-nal kapcsolatban az "Integrálja az Intune a Configuration Managerrel (hibrid MDM) vagy érdemes az Intune önálló futtassa a felhőkonfiguráció csak?" A kérdés megválaszolásához gondosan kell hasonlítsa össze a két lehetőség és fontolja meg az Intune önálló korai 2017 érkező frissítéseket.

## <a name="what-is-intune-standalone"></a>Újdonságok az Intune önálló?

Az Intune önálló egy kizárólag felhőalapú mobileszköz-kezelési megoldás, amely magában foglalja a helyi erőforrások és a segítségével elérhető egy webkonzol bárhol a világon. Észak-Amerikában, Európában és Ázsiában Intune adatközpontok üzemelteti. Mivel az Intune egy felhőalapú szolgáltatás, Intune-felügyelet telepítene egy viszonylag rövid időkereten eszközét. Is választhatja, hogy az Intune önálló, ha a szervezet van helyezi át a felhőbe.

## <a name="what-is-hybrid-mdm-with-configuration-manager"></a>Mi az a hibrid MDM és a Configuration Managerben?

Hibrid mobileszköz-kezelési egy olyan megoldás, Intune-t használja a szállítási csatorna házirendek, profilok és-eszközökön, de a Configuration Manager helyszíni infrastruktúra segítségével tárolja és felügyelheti a tartalom és felügyelje az eszközöket. Dönthet a hibrid MDM, ha már rendelkezik egy jelentős a Configuration Managerben, és szeretnék bővíteni úgy, hogy a mobileszközök felügyeletéhez. A hibrid megvalósítás "egytáblás, üveghatású" vezérlő, ami azt jelenti, hogy a mobileszközök Intune-ban, valamint a számítógépek és kiszolgálók a hagyományos Configuration Manager-ügyféllel kezelésére használhatja az ugyanazon a helyszíni infrastruktúra és a felügyeleti konzol biztosítja.

## <a name="whats-coming-to-intune-standalone-in-early-2017"></a>Mi várható önálló Intune-telepítésekre korai 2017

Önálló és hibrid közötti választ, ha kell figyelembe venni szolgáltatások korai 2017 az Intune önálló verziója hamarosan. Hibrid mobileszköz-kezelési ma, több olyan speciális funkciót, ezért az egyes ügyfelek válassza a hibrid MDM Intune önálló verziója helyett az eszközök kezelésére korábban már rendelkezik:

-   Programozott hozzáférés (API) – SDK-t és a PowerShell felügyeleti lehetőségeket.

-   Egyéni jelentéskészítési – egyéni jelentések létrehozása.

-   Szerepköralapú hozzáférés-vezérlés – felügyeleti funkciók rendelt szerepkörök alapján korlátozza a hozzáférést.

-   Méretezhető – központi telepítése, és több mint 100 000 mobileszköz kezelése.

-   Egytáblás, üveghatású – hagyományos PC-ügyfelek, mind az Intune által felügyelt eszközök ugyanarról a konzolról kezelheti.

Ha jelenleg az Intune üzembe helyezésének a tervezéséhez és tesztelés, a tesztelés és a telepítés több hónap ablakának rendelkezik megkezdése, érdemes most azzal, hogy a felhőalapú szolgáltatáshoz érkező frissítéseket tartalmazza-e a további funkcióit az Intune önálló verziójának kiválasztása. Teljes 2017 naptári év első felében az Intune önálló frissítések, amelyek nagy részét a Configuration Manager hibrid telepítés fejlett funkciói biztosítják fog kapni. Az Intune önálló hamarosan áthelyezése a Microsoft Azure cloud platform és az azt fogja rendelkezik bővített méretezhetőséget, szerepkörön alapuló hozzáférés az Azure portál, egyéni jelentések és programozott hozzáférés az Azure Graph API-n keresztül.

Megváltoztathatja az önálló Intune-telepítésekre hibrid, illetve a hibrid önálló, de a Microsoft támogatási szolgálatához és műveletek súgó igényel. Elutasításuk és beléptetés összes eszközt, a felügyeleti hatóság módosítását is szükséges.  Microsoft dolgozik a jövőbeli szolgáltatásfrissítés átváltását konfigurációk élmény javítása.

