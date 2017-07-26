---
title: "Eszközök megfelelőségének biztosítása |} Microsoft Docs"
description: "System Center Configuration Manager konfigurációját és megfelelőségét a szervezetben lévő eszközök kezelésére."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7568c9aa-b99e-4466-bfc8-0301aa376930
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: f7ecfe550d2e28579ea873442b2a68dc1c7c5483
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="ensure-device-compliance-with-system-center-configuration-manager"></a>Eszközök megfelelőségének biztosítása a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Manager megfelelőségi beállítások lehetővé teszi az eszközök és konfigurációját és megfelelőségét a szervezetben lévő eszközök kezeléséhez szükséges erőforrások. Így könnyebben felelhet meg a következő üzleti követelményeknek:  

-   Az Ön által kezelt Windows alapú PC-k, Mac rendszerű számítógépek, kiszolgálók és mobileszközök konfigurációinak összehasonlítása a saját vagy más gyártóktól származó bevált konfigurációkkal  

-   A jogosulatlan eszköz-konfigurációk azonosítása  

-   Jelentés a szabályzatoknak és belső biztonsági házirendeknek való megfelelésről  

-   Biztonsági rések azonosítása  

-   Az ügyfélszolgálat tájékoztatása az incidensek és problémák előfordulásának lehetséges okairól a nem megfelelő konfigurációk azonosítása által  

-   A mobileszközök néhány nem megfelelő beállításának automatikus javítása  

-   Problémák javítása alkalmazások, csomagok és programok vagy parancsfájlok telepít egy gyűjteményhez, amely automatikusan töltődik jelentés nem megfelelő eszközök  


## <a name="get-started"></a>Első lépések  
 Alapvető tudnivalók a megfelelőségi beállításokról és a velük végrehajtható feladatokról.  

 [A megfelelőségi beállítások beolvasása használatába](../../compliance/get-started/get-started-with-compliance-settings.md)  

## <a name="plan-and-design"></a>A tervezési és kialakítási  
 A megfelelőségi beállítások használatának megkezdése előtt győződjön meg róla, hogy megvalósította a témakörben tárgyalt szükséges előfeltételeket.  

 [Tervezze meg, és a megfelelőségi beállítások konfigurálása](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

## <a name="common-tasks"></a>Gyakori feladatok  
 Ebben a szakaszban találhat olyan gyakori forgatókönyveket tartalmaz, amelyek bemutatják, hogyan használhatja a megfelelőségi beállítások a Configuration Manager alkalmazásban.  

 [Megfelelőség kezeléséhez kapcsolódó gyakori feladatok](../../compliance/plan-design/common-tasks-for-managing-compliance.md)  

## <a name="remote-connection-profiles"></a>Távoli kapcsolati profilok  
 Ezzel a konfigurációelem-típussal konfigurálhatja a felhasználók számítógépeit arra, hogy távolról elérjék a munkahelyi számítógépeket, amikor nem csatlakoznak a tartományhoz, vagy ha a felhasználók személyi számítógépei az interneten keresztül csatlakoznak.  

 [Távoli kapcsolati profilok létrehozása](/sccm/compliance/deploy-use/create-remote-connection-profiles)  

## <a name="user-data-and-profiles"></a>Felhasználói adatok és profilok  
 Ez a konfigurációelem-típus olyan beállításokat tartalmaz, melyekkel kezelhető a mappaátirányítás, az offline fájlok és a barangoló profilok a Windows 8 vagy újabb rendszerű számítógépeken a hierarchiában lévő felhasználók számára.  

 [Felhasználói adatokat és profilokat tartalmazó konfigurációelemek létrehozása](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)  

## <a name="windows-edition-upgrade-policy"></a>A Windows Kiadásfrissítési házirend  
 A kiadásfrissítési házirend lehetővé teszi a Windows 10 rendszerű eszközök automatikus újabb verzióra való frissítését. Megadhat egy termékkulcsot a Windows 10 asztali verzióinak frissítéséhez, vagy egy, a Windows 10 Mobile és a Windows 10 Holographic rendszert futtató eszközök frissítéséhez használható licencfájlt.  

 [A Kiadásfrissítési házirend frissítése Windows-eszközök](/sccm/compliance/deploy-use/upgrade-windows-version)  

