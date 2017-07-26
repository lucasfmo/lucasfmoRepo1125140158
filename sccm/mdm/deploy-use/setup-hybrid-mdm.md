---
title: "A telepítő hibrid MDM |} Microsoft Docs"
description: "A Configuration Manager és az Intune-ban a hibrid rendszerű eszközök regisztrálásának beállítása."
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
ms.openlocfilehash: c494fcc38955571c06507278a1ae88e5777b5708
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017

---

# <a name="setup-hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hibrid mobileszköz-kezelés (MDM) a System Center Configuration Manager és a Microsoft Intune beállítása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


IOS, Windows és Configuration Manager Android-eszközök kezeléséhez, azok regisztrálva kell lennie az Intune-ban. Használja az alábbi lépések végrehajtásával hibrid eszközregisztráció beállítása a Configuration Manager Intune-nal. Az alábbi lépések végrehajtásával teszi lehetővé "megteremthetők a saját eszközök" (BYOD) regisztrációjával a felhasználók számára. Ezeket a lépéseket előfeltételei is [BYOD-eszközök regisztrálása](enroll-hybrid-ios-mac.md) és [vállalat által birtokolt eszközök regisztrálása](enroll-company-owned-devices.md).

 |Lépések|Részletek|  
 |-----------|-------------|  
 |**1. lépés:** [Az MDM-gyűjtemény létrehozása](create-mdm-collection.md)|A felhasználók, amelyek az eszközök regisztrálása a Configuration Manager felhasználói gyűjtemény létrehozása|  
 |**2. lépés:** [Tartománynevekre vonatkozó követelményeknek](confirm-dns.md)|Erősítse meg a szervezet tartományi névszolgáltatás (DNS) és Active Directory-felhasználók kezelése MDM-követelményeknek megfelelő|
 |**3. lépés:** [Intune-előfizetés konfigurálása](configure-intune-subscription.md)|Az Intune szolgáltatás lehetővé teszi az eszközök kezelését az interneten keresztül.|  
 |**4. lépés:** [Adja hozzá a feltételek és kikötések](terms-and-conditions.md)| Feltételek és kikötések, amelyhez felhasználóknak hozzá kell járulniuk ahhoz, hogy használhassák a vállalati portál alkalmazás létrehozása|
 |**5. lépés:** [Szolgáltatáskapcsolódási pont létrehozása](create-service-connection-point.md)|A szolgáltatáskapcsolódási pont beállításokat és szoftvertelepítési információkat küld a Configuration Manager és állapot- és beolvassa a mobileszközökről. |  
 |**6. lépés:** [Platform-igénylés engedélyezése](enable-platform-enrollment.md)|MDM-regisztráció iOS és Windows rendszerű eszközökhöz további lépéseket igényelnek a szolgáltatás és eszközök közötti kommunikációhoz. Android további konfigurációra van szükség.|  
 |**7. lépés:** [További kezelésének beállítása](set-up-additional-management.md)|(Választható) Konfigurációelemek és a regisztrált eszközök feltételes hozzáférés beállítása|
 |**8. lépés:** [MDM-konfiguráció ellenőrzése](verify-mdm-configuration.md)|Ellenőrizze, hogy a szolgáltatáskapcsolódási pont sikeresen létrejött-e a naplófájlok megtekintése és a felhasználói fiókok szinkronizálása.|

Az Intune nélkül a Configuration Manager keres?
> [!div class="button"]
[Intune dokumentumok megtekintése >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)


## <a name="enroll-devices"></a>Eszközök regisztrálása
Hibrid telepítés befejezése után az eszközök regisztrálása a Configuration Managerben című számos módon:
- **Vállalati tulajdonú (COD) eszközök:** [Vállalati tulajdonban lévő eszközök regisztrálása](enroll-company-owned-devices.md) a vállalat által birtokolt eszközök regisztrálása módjai különböző platform-specifikus nyújt útmutatást.
- **Felhasználó által birtokolt (eszközök használata BYOD) eszközök:** [Felhasználó által birtokolt (eszközök használata BYOD) eszközök regisztrálása](enroll-hybrid-ios-mac.md) a felhasználó által birtokolt eszközök regisztrálása módjai nyújt útmutatást.

