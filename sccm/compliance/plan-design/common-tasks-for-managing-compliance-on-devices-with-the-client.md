---
title: "Megfelelőségi ügyfél által felügyelt eszközök – Configuration Manager általános felügyeleti feladatai |} Microsoft Docs"
description: "System Center Configuration Manager megfelelőségi beállítások információ feldolgozása révén olyan gyakori forgatókönyveket tartalmaz."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e345791-74db-41ad-b472-024ce6521daf
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 991eff171dce95590a7f050e0d3b07f98c0224b3
ms.openlocfilehash: 2012ab5e55da8d707fd668e0163b42fe7d56c72f
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="common-tasks-for-managing-compliance-on-devices-with-the-system-center-configuration-manager-client"></a>A System Center Configuration Manager-ügyfél rendelkező eszközök megfelelőségének kezeléséhez kapcsolódó gyakori feladatok

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A témakörben található forgatókönyvek bevezetést a System Center Configuration Manager megfelelőségi beállítások használatával feldolgozása révén olyan gyakori forgatókönyveket tartalmaz, akkor léphetnek fel.  

 Ha már ismeri a megfelelőségi beállításokat, az összes használt funkcióra vonatkozó részletes dokumentációt megtalálható a [a System Center Configuration Manager-ügyféllel felügyelt eszközök konfigurációelemei](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md) szakasz.  

 Megkezdése előtt olvassa el a [Ismerkedés a megfelelőségi beállítások](../../compliance/get-started/get-started-with-compliance-settings.md) néhány alapvető tudnivalók a megfelelőségi beállítások, valamint is [tervezése és megfelelőségi beállítások konfigurálása](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) megvalósításához szükséges előfeltételeket.  

## <a name="general-information-for-each-scenario"></a>Az egyes forgatókönyvekre vonatkozó általános információk  
 Minden forgatókönyvben egy adott feladatot végrehajtó konfigurációelemet kell létrehozni. Nyissa meg a Konfigurációelem létrehozása varázslót, és kövesse az alábbi lépéseket:  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Konfigurációelemek**.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  

4.  A Konfigurációelem létrehozása varázsló az alábbiakban látható **Általános** lapján adja meg a konfigurációelem nevét és leírását, majd válassza ki a témakör egyes forgatókönyveihez megfelelő konfigurációelem-típust.  

     ![A konfigurációelem létrehozása varázsló Általános lapja jeleníti meg.](/sccm/compliance/plan-design/media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-10-devices-managed-with-the-configuration-manager-client"></a>Forgatókönyvek Configuration Manager-ügyféllel felügyelt Windows 10 rendszerű eszközökhöz  

### <a name="scenario-disable-the-use-of-bluetooth-on-windows-10-devices"></a>Forgatókönyv: A Windows 10 rendszerű eszközökön a Bluetooth használatának tiltása  
 Ebben a forgatókönyvben a biztonsági részleg az eszközök Bluetooth-képességet a bizalmas vállalati adatok a vállalaton kívülre való továbbításának lehetséges módjaként azonosította. Nemrég frissített minden számítógépet Windows 10-re, és úgy dönt, hogy letiltja az eszközök Bluetooth-képességeit.  

1.  A Konfigurációelem létrehozása varázsló **Általános** lapján válassza a **Windows 10** konfigurációelem-típust, majd kattintson a **Tovább**gombra.  

2.  A varázsló **Támogatott platformok** lapján válasszon ki minden Windows 10-platformot.  

3.  Az **Eszközbeállítások** lapon válassza az **Eszköz**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  Az **Eszköz** lapon a **Bluetooth** beállítás értékeként állítsa be a **Tiltott**lehetőséget.  

5.  Jelölje be a **Nem megfelelő beállítások szervizelése** lehetőséget annak biztosítása érdekében, hogy a rendszer minden Windows 10 rendszerű eszközre alkalmazza a módosítást.  

6.  A konfigurációelem létrehozásához fejezze be a varázslót.  

 Ezután már használhatja az információk a [gyakori feladatok létrehozása és telepítése a System Center Configuration Managerrel referenciakonfigurációk](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) témakör segítségével telepítheti a létrehozott konfigurációt eszközökre.  

## <a name="scenarios-for-windows-desktop-and-server-computers-managed-with-the-configuration-manager-client"></a>Forgatókönyvek Configuration Manager-ügyféllel felügyelt Windows rendszerű asztali és kiszolgáló-számítógépekhez  
 A Configuration Manager-ügyfelet futtató Mac számítógépeken megfelelőség értékelésére két lehetőség közül választhat:  

-   Egy Mac OS X-beállításokat tartalmazó (plist) fájl értékelése.  

-   Egyéni parancsfájl használata és a parancsfájl által visszaadott eredmények értékelése.  

 További információkért lásd: [a System Center Configuration Manager ügyfélalkalmazással felügyelt Mac OS X-eszközökön a konfigurálási elemeinek létrehozásáról](../../compliance/deploy-use/create-configuration-items-for-mac-os-x-devices-managed-with-the-client.md).  

### <a name="scenario-remediate-an-incorrect-registry-value-on-windows-desktop-computers"></a>Forgatókönyv: Windows rendszerű asztali számítógépeken egy helytelen beállításazonosító javítása  
 Ebben a forgatókönyvben azt tapasztalja, hogy egy fontos üzletági alkalmazás nem fut megfelelően néhány Windows 8.1 rendszerű kezelt számítógépen. A vizsgálat során azt találja, hogy ezt az okozza, hogy a **HKEY_LOCAL_MACHINE\SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1** nevű beállításkulcs egyes számítógépeken a **0** értékre van állítva. Az üzletági alkalmazás sikeres futtatásához ezt az értéket az **1**értékre kell állítani.  

 Ezzel az eljárással egy konfigurációelemet hozhat létre, mely figyeli a nem megfelelő beállításkulcs-értékeket, és ha talál ilyet, azt automatikusan javítja.  

1.  A Konfigurációelem létrehozása varázsló **Általános** lapján válassza a **Windows rendszerű asztali számítógépek és kiszolgálók (egyéni)** konfigurációelem-típust, majd kattintson a **Tovább**gombra.  

2.  A varázsló **Támogatott platformok** lapján válassza a **Windows 8.1** lehetőséget (annak biztosítása érdekében, hogy a konfigurációelem csak az érintett számítógépekre vonatkozzon).  

3.  A **Beállítások** lapon kattintson az **Új** lehetőségre egy új beállítás létrehozásához.  

4.  A **Beállítás létrehozása** párbeszédpanel **Általános** lapján állítsa be a következőket:  

    -   **Név** > **Példa beállítás**  

    -   **Beállítástípus** > **Beállításazonosító**  

    -   **Adattípus** > **Egész** (mivel az érték csak egy számot tartalmaz)  

    -   **Struktúra** > **HKEY_LOCAL_MACHINE**  

    -   **Kulcs** > **SOFTWARE\Woodgrove\LOB App\Configuration\Configuration1**  

    -   **Érték** > **1** (a szükséges érték)  

5.  A **Beállítás létrehozása** párbeszédpanel **Megfelelőségi szabályok** lapján kattintson az **Új**lehetőségre, majd a **Szabály létrehozása** párbeszédpanelen állítsa be a következőket:  

    -   **Név** > **Példa szabály**  

    -   **Kiválasztott beállítás** – győződjön meg róla, hogy a **Példa beállítás**a kiválasztott beállítás.  

    -   **Szabály típusa** > **Érték**  

    -   **A beállításnak meg kell felelnie a következő szabálynak** – ellenőrizze, hogy a beállítás neve helyes-e, és konfigurálja a beállítást azt megadva, hogy a beállítás értékének **1**-nek kell lennie.  

    -   **Nem megfelelő szabályok szervizelése** – jelölőnégyzet bejelölésével győződjön meg arról, hogy a Configuration Manager alaphelyzetbe állítja a beállításkulcs-érték a helyes értékre, ha annak értéke helytelen.  

6.  A konfigurációelem létrehozásához fejezze be a varázslót.  

 Ezután már használhatja az információk a [gyakori feladatok létrehozása és telepítése a referenciakonfigurációk](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) témakör segítségével telepítheti a létrehozott konfigurációt eszközökre.  

