---
title: "Az Intune-nal kezelt eszközök megfelelőségének kezeléséhez |} Microsoft Docs"
description: "System Center Configuration Manager megfelelőségi beállítások információ feldolgozása révén olyan gyakori forgatókönyveket tartalmaz."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9e83007f-e81c-4b7e-b47e-b01d7b19cfbc
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: b3a63f6c55c317c9c84d4394dfdcb9f1cbbbc90b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="managing-compliance-on-devices-managed-with-intune"></a>Az Intune-nal kezelt eszközök megfelelőségének kezeléséhez

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Ezek a forgatókönyvek bevezetést a System Center Configuration Manager megfelelőségi beállítások használatával feldolgozása révén olyan gyakori forgatókönyveket tartalmaz, akkor léphetnek fel.  

 Ha már ismeri a megfelelőségi beállításokat, az összes használt funkcióra vonatkozó részletes dokumentációt megtalálható a [az Intune-nal felügyelt eszközök konfigurációelemei](#configuration-items-for-devices-managed-with-intune) szakasz.  

 [Ismerkedés a megfelelőségi beállítások](../../compliance/get-started/get-started-with-compliance-settings.md) nyújt a megfelelőségi beállítások alapjairól és [tervezése és megfelelőségi beállítások konfigurálása](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md) segít a szükséges előfeltételek teljesítéséről.  

## <a name="general-information-for-each-scenario"></a>Az egyes forgatókönyvekre vonatkozó általános információk  
 Minden forgatókönyvben egy adott feladatot végrehajtó konfigurációelemet kell létrehozni. Nyissa meg a Konfigurációelem létrehozása varázslót, és kövesse az alábbi lépéseket:  

1.  Kattintson a Configuration Manager konzolon **eszközök és megfelelőség** > **megfelelőségi beállítások** > **Konfigurációelemek**.  

3.  A **Kezdőlap** lap **Létrehozás** csoportjában kattintson a **Konfigurációelem létrehozása**elemre.  

4.  A Konfigurációelem létrehozása varázsló az alábbiakban látható **Általános** lapján adja meg a konfigurációelem nevét és leírását, majd válassza ki a témakör egyes forgatókönyveihez megfelelő konfigurációelem-típust.  

     ![A konfigurációelem létrehozása varázsló Általános lapja jeleníti meg.](media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-81-and-windows-10-devices-managed-with-intune"></a>Az Intune-nal felügyelt Windows 8.1 és Windows 10-es eszközök forgatókönyvei  

### <a name="scenario-restrict-access-to-the-app-store-on-all-windows-pcs"></a>Forgatókönyv: Az app store minden Windows-számítógépeken való hozzáférés korlátozása  
 Ezen forgatókönyv esetében Ön egy olyan vállalat rendszergazdája, amely rendkívül bizalmas információkat kezel, ezért korlátozni szeretné, hogy a felhasználók milyen alkalmazásokat telepíthetnek. Minden Windows 10 rendszerű számítógépen szeretné megakadályozni a felhasználókat abban, hogy alkalmazásokat töltsenek le a Windows áruházból, ezért a elvégzi az alábbi műveleteket.  

1.  A Konfigurációelem létrehozása varázsló **Általános** lapján válassza a **Windows 8.1 és Windows 10** konfigurációelem-típust, majd kattintson a **Tovább**gombra.  

2.  Az a **által támogatott platformok** lapon, válassza ki az összes Windows 10-platformot.  

3.  Az **Eszközbeállítások** lapon válassza az **Áruház**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  Az **Áruház** lapon az **Alkalmazásáruház** beállítás értékeként válassza a **Letiltott**lehetőséget.  

5.  Jelölje be a **Nem megfelelő beállítások szervizelése** lehetőséget annak biztosítása érdekében, hogy a rendszer minden számítógépre alkalmazza a módosítást.  

6.  A konfigurációelem létrehozásához fejezze be a varázslót.  

 Ezután már használhatja az információk a [gyakori feladatok létrehozása és telepítése a referenciakonfigurációk](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) témakör segítségével telepítheti a létrehozott konfigurációt eszközökre.  

## <a name="scenarios-for-windows-phone-devices-managed-with-intune"></a>Az Intune-nal kezelt Windows Phone-eszközök forgatókönyvei  

### <a name="scenario-disable-the-use-of-screen-capture-on-a-windows-phone"></a>Forgatókönyv: A Windows Phone képernyőfelvétel-készítés használatának letiltása  
 Ezen forgatókönyv esetében vállalata Windows Phone 8.1 rendszerű eszközöket használ, amelyek egy bizalmas adatokat tartalmazó értékesítési alkalmazást futtatnak. A vállalat védelme érdekében szeretné letiltani a képernyőfelvétel-készítés használatát azon eszközön, amely potenciálisan felhasználható bizalmas adatoknak a vállalat kívülre való elküldésére.  

1.  A Konfigurációelem létrehozása varázsló **Általános** lapján válassza a **Windows Phone** konfigurációelem-típust, majd kattintson a **Tovább**gombra.  

2.  Az a **által támogatott platformok** lapon jelölje be **összes Windows Phone 8.1** platformokon.  

3.  Az **Eszközbeállítások** lapon válassza az **Eszköz**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  Az **Eszköz** lapon a **Képernyőfelvétel** beállítás értékeként válassza **Letiltott**lehetőséget.  

5.  Jelölje be a **Nem megfelelő beállítások szervizelése** lehetőséget annak biztosítása érdekében, hogy a rendszer minden Windows 8.1 rendszerű eszközre alkalmazza a módosítást.  

6.  A konfigurációelem létrehozásához fejezze be a varázslót.  

 Ezután már használhatja az információk a [gyakori feladatok létrehozása és telepítése a System Center Configuration Managerrel referenciakonfigurációk](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) témakör segítségével telepítheti a létrehozott konfigurációt eszközökre.  

## <a name="scenarios-for-ios-and-mac-os-x-devices-managed-with-intune"></a>IOS és Mac OS X rendszerű eszközök Intune-nal felügyelt forgatókönyvei  

### <a name="scenario-disable-the-camera-on-ios-devices"></a>Forgatókönyv: Az iOS-eszközökön a kamera letiltása  
 Ezen forgatókönyv esetében vállalata új termékekhez készít tervrajzokat. Ezek olyan bizalmas információkat tartalmaznak, amelyek kiszivárgását meg kell akadályozni. Mivel a vállalat iPhone-okat és iPadeket bocsát az alkalmazottak részére, le szeretné tiltani a fényképezőgép használatát ezen eszközökön, hogy ne lehessen a tervek lefényképezésére használni őket.  

1.  A Konfigurációelem létrehozása varázsló **Általános** lapján válassza az **iOS és Mac OS X** konfigurációelem-típust, majd kattintson a **Tovább**gombra.  

2.  Az a **által támogatott platformok** lapon, válassza ki az összes iPhone és iPad-eszközplatformot.  

3.  Az **Eszközbeállítások** lapon válassza a **Biztonság**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  Az **Eszköz** lapon a **Fényképezőgép** beállítás értékeként válassza a **Letiltott**lehetőséget.  

5.  Jelölje be a **Nem megfelelő beállítások szervizelése** lehetőséget annak biztosítása érdekében, hogy a rendszer minden iOS-eszközre alkalmazza a módosítást.  

6.  A konfigurációelem létrehozásához fejezze be a varázslót.  

 Ezután már használhatja az információk a [gyakori feladatok létrehozása és telepítése a System Center Configuration Managerrel referenciakonfigurációk](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) témakör segítségével telepítheti a létrehozott konfigurációt eszközökre.  

## <a name="scenarios-for-android-and-samsung-knox-standard-devices-managed-with-intune"></a>Az Intune-nal felügyelt Android és Samsung KNOX Standard eszközökhöz forgatókönyvek  

### <a name="scenario-require-a-password-on-all-android-5-devices"></a>Forgatókönyv: Jelszó kérése a minden Android 5-eszközökhöz  
 Ezen forgatókönyv esetében egy olyan konfigurációelemet hoz létre Android 5-eszközökhöz, amely megköveteli a felhasználóktól, hogy állítsanak be egy legalább 6 karakterből álló jelszót az eszközeiken. Ezenfelül, ha a felhasználó egymás után 5 alkalommal helytelen jelszót ad meg, az összes adat törlődik az eszközről.  

1.  A Konfigurációelem létrehozása varázsló **Általános** lapján válassza az **Android és Samsung KNOX** konfigurációelem-típust, majd kattintson a **Tovább**gombra.  

2.  Az a **által támogatott platformok** lapon, válassza ki a csak **Android 5** (annak biztosítására, hogy a beállítások csak érvényben erre a platformra).  

3.  Az **Eszközbeállítások** lapon válassza a **Jelszó**lehetőséget, majd kattintson a **Tovább**gombra.  

4.  A **Jelszó** lapon adja meg a következő beállításokat:  

    -   **Jelszóbeállítások megkövetelése az eszközökön** > **Kötelező**  

    -   **Jelszó minimális hossza (karakter)** > **6**  

    -   **Sikertelen bejelentkezési próbálkozások száma az eszköz törlése előtt** > **5**  

5.  A konfigurációelem létrehozásához fejezze be a varázslót.  

 Ezután már használhatja az információk a [gyakori feladatok létrehozása és telepítése a referenciakonfigurációk](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) témakör segítségével telepítheti a létrehozott konfigurációt eszközökre.  

## <a name="configuration-items-for-devices-managed-with-intune"></a>Az Intune-nal felügyelt eszközök konfigurációelemei

A következő System Center Configuration Manager konfigurációelem-típusok olyan eszközök esetében, amelyeket nem felügyel a Configuration Manager-ügyfél, például a Microsoft Intune-nal regisztrált eszközök érhetők el.  

 -   [Az Intune-nal felügyelt Windows 8.1 és Windows 10-eszközökhöz a konfigurációelemek létrehozása](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)  

 -   [Az Intune-nal felügyelt Windows Phone-eszközökhöz a konfigurációelemek létrehozása](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)  

 -   [Az Intune-nal felügyelt iOS és Mac OS X rendszerű eszközök konfigurációelemek létrehozása](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)  

 -   [Az Intune-nal felügyelt Android és Samsung KNOX Standard eszközökhöz konfigurációelemek létrehozása](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)  

