---
title: "A hosszú távú karbantartási ág bemutatása |} Microsoft Docs"
description: "További tudnivalók a hosszú távú karbantartási ág a System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 91c1ca860069c6ebe0d20230c4620bf3f68735a2
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>A hosszú távú karbantartási ág a System Center Configuration Manager bemutatása

*Vonatkozik: A System Center Configuration Manager (hosszú távú karbantartási ág)*

A hosszú távú karbantartási ág (LTSB) a System Center Configuration Manager különböző ág a Configuration Manager, amely az összes ügyfél számára elérhető telepítési lehetőség. Azonban az egyetlen lehetőség a felhasználók, akik megszűnik, a szoftver megbízhatósági (SA) segítségével vagy a megfelelő előfizetés jogosultság a Configuration Manager.


A Configuration Manager verziója 1606 alapján, a LTSB lecsökkentette képest, hogy az aktuális ág a Configuration Manager funkcióit.

 > [!TIP]   
 > Ha a keresett elágazásai információ **Windows Server**, lásd: [Windows Server 2016 új aktuális üzleti ág karbantartási kapcsoló]( https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

## <a name="features-that-are-not-available-in-the-ltsb-of-configuration-manager"></a>Nem érhető el a Configuration Manager LTSB szolgáltatásokat
A Configuration Manager aktuális ág a következő funkciókat, amelyek esetén nem érhető el a LTSB támogatja:

-   A konzolon belüli frissítések hozzáadott új szolgáltatásait és fejlesztéseit.
-   Újonnan kiadott operációs rendszerek támogatása a Helykiszolgálók és ügyfelek használják.
-   A támogatásához egy Microsoft Intune-előfizetés használata:
    -   Hibrid mobileszköz-felügyelet (MDM) konfigurációban az Intune-ban
    -   A helyszíni MDM
-   A Windows 10 karbantartási irányítópult és a karbantartási tervek, beleértve a támogatása a legutóbbi Windows 10 aktuális ág (CB) és az aktuális ág üzleti (CBB) verzióit.  
-   Windows Server és a Windows 10 LTSB későbbi kiadásaiban támogatása
-   Eszközintelligencia
-   Felhőalapú terjesztési pontok
-   Exchange online-hoz, az Exchange-összekötő    

Bár támogatja a LTSB ezeket a funkciókat nem érhető el, néhány funkció marad a Configuration Manager konzolon az látható, de nem kell kijelölt vagy használt.


## <a name="find-documentation-for-the-ltsb"></a>A LTSB dokumentációjában található
A LTSB aktuális ág verzión 1606 alapul. A termék dokumentációjában használja a [aktuális ág dokumentáció](https://docs.microsoft.com/sccm/), figyelmeztetések és a LTSB vonatkozó korlátozások. A következő online témakörök azonosítja ezen korlátozásokkal és korlátozások:

-      [A hosszú távú karbantartási ág bemutatása](introduction-to-the-ltsb.md): (Ez a témakör)
-      [A hosszú távú karbantartási ág telepítése](install-the-ltsb.md)
-      [Frissítse a hosszú távú karbantartási ág az aktuális ág](convert-to-current-branch.md)
-      [A hosszú távú karbantartási ág támogatott konfigurációk](supported-configurations-for-ltsb.md)
-   [A hosszú távú karbantartási ág a Configuration Manager kezelése](manage-the-ltsb.md)

Ha hivatkozik LTSB az aktuális ág dokumentációját, 1606 verziójára vonatkoznak, adatokat is alkalmazható a LTSB. A LTSB nem támogatja a szolgáltatások és -adatokat bevezetett 1610 verziójával vagy újabb.


## <a name="licensing-overview-for-the-ltsb"></a>A LTSB licencelési áttekintése   
Az aktív szoftverfrissítési megbízhatósági (SA) a System Center Configuration Manager-licencet, vagy a 2016. október 1-én egyenértékű előfizetés jogosultsággal rendelkező felhasználók a 2016. októberi verziót 1606 kiadásával a System Center Configuration Manager jogosult. Ügyfelek jogosultságokkal a System Center Configuration Manager 1 2016 októberétől kezdve, a következőnél megkeresi a telepítés után két licencelt beállítások: Aktuális ág és hosszú távú karbantartási ág (LTSB).

Ügyfelek, amelyek, a System Center Configuration Manager végleges jogokat biztosítják Önnek, vagy, amelyek lehetővé teszik a rendszergazdai (SA) vagy előfizetés felhasználásától. október 1 után telepítheti a System Center Configuration Manager LTSB buildelése időpontjában aktuális verzióját.

[Teljes feltételek és kikötések a Microsoft mennyiségi licencelési programok keresztül megvásárolt termékek itt található](http://go.microsoft.com/fwlink/?LinkId=800052).

Lásd: [licencelési System Center Configuration Manager és az](learn-more-editions.md) Configuration Manager ágak licencelésével kapcsolatban további információt.

## <a name="next-steps"></a>További lépések

Ha úgy dönt, hogy a Configuration Manager LTSB-e a környezetében, helyes-e ág [telepítése egy új LTSB](/sccm/core/understand/install-the-ltsb#install-a-new-site) hely új hierarchia, részeként vagy [System Center 2012 Configuration Manager hely frissítése](/sccm/core/understand/install-the-ltsb#upgrade-from-system-center-2012-configuration-manager) és a hierarchiában.

Ha nem rendelkezik a telepítési adathordozón, lásd: [System Center 2016 dokumentáció](https://technet.microsoft.com/system-center-docs/system-center) információ a System Center 2016 beszerzésére, mely tartalmazza a System Center Configuration Manager LTSB telepítéséhez használható.  

