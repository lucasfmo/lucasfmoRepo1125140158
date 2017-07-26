---
title: "Az iOS és Mac hibrid kezelése a System Center Configuration Manager és a Microsoft Intune |} Microsoft Docs"
description: "A System Center Configuration Manager és a Microsoft Intune iOS-eszközök kezelésének beállítása."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 5eae4400-58ca-4c71-804c-6a585cd3df5d
caps.latest.revision: 10
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 02af275ede0ab8578adb0615458b285819d65c9c
ms.openlocfilehash: 848721b564316234ad900fcbf968098002a4bb4e
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-ios-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Hibrid iOS MDM eszközkezelés beállítása a System Center Configuration Managerrel és a Microsoft Intune-nal

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A Configuration Manager és az Intune-ban, engedélyezhető a BYOD ("saját eszközök használata) alapú iOS és Mac OS X-eszközregisztráció a vállalati e-mailek és az iPhone-, iPad- és Mac-felhasználók erőforrásokhoz való hozzáférést. Miután a felhasználók telepítették a Munkahelyi Microsoft Intune-portál alkalmazást, az eszközeikre szabályzat alkalmazható. Az iOS-és Mac-eszközök kezeléséhez APNs-tanúsítványt szükséges importálni az Apple-től. Ez a tanúsítvány lehetővé teszi az Intune számára az iOS- és Mac-eszközök kezelését, és egy akkreditált és titkosított IP-kapcsolatot létesít a mobileszköz-kezelő szolgáltató szolgáltatásaival.  

 A vállalati tulajdonban lévő iOS-eszközöket is regisztrálhatja.  Lásd: [vállalati tulajdonban lévő eszközök regisztrálása](enroll-company-owned-devices.md).  

## <a name="enable-ios-device-enrollment"></a>iOS-eszközök regisztrációjának engedélyezése  
 Az iOS-eszközök regisztrációjának támogatásához kövesse az alábbi lépéseket:  

#### <a name="set-up-ios-device-enrollment-in-configuration-manager"></a>iOS-eszközök regisztrációjának beállítása a Configuration Managerben  

1.  **Előfeltételek** – mielőtt bármely platformhoz beléptetési állíthat be végezze el a szükséges előfeltételek és eljárások [telepítő hibrid MDM](setup-hybrid-mdm.md).    

2.  **Tanúsítvány-aláírási kérelem letöltése** – Tanúsítvány-aláírási kérelemfájlra (.csr) van szükség ahhoz, hogy APNs-tanúsítványt igényeljen az Apple-től.  

    1.  A Configuration Manager konzol **Adminisztráció** munkaterületén válassza a **Felhőszolgáltatások**> **Microsoft Intune-előfizetés**elemet.  

    2.  A **Kezdőlapon** kattintson az **APN szolgáltatás tanúsítványkérésének létrehozása**elemre. Megjelenik az **APN szolgáltatás tanúsítványkérésének beszerzése** párbeszédpanel.  

    3.  A**Tallózás** gombra válassza ki a helyet, ahová menteni szeretné az új tanúsítvány-aláírási kérés (.csr) fájlját. Mentse helyileg a tanúsítvány-aláírási kérelem (.csr) fájlját.  

    4.  Kattintson a **Letöltés**lehetőségre. A rendszer letölti az új Microsoft Intune .csr fájlt, és a Configuration Manager menti azt. A .csr fájl a megbízhatósági kapcsolat tanúsítványának Apple Push Certificates portálról való beszerzésére szolgál.  

3.  **APNs-tanúsítvány igénylése az Apple-től** – Az Apple Push Notification szolgáltatás (APNs) tanúsítványa használható megbízhatósági kapcsolat létrehozására a felügyeleti szolgáltatás, az Intune és a regisztrált iOS-mobileszközök között.  

    1.  Nyissa meg az [Apple Push Certificates portált](http://go.microsoft.com/fwlink/?LinkId=269844) egy böngészőben, és jelentkezzen be a vállalati Apple ID azonosítójával. Később ezzel az Apple-azonosítóval újíthatja meg az APNs-tanúsítványt.  

    2.  A tanúsítvány-aláírási kérésfájlt (.csr) használva fejezze be a varázslót. Töltse le az APNs-tanúsítványt, és mentse helyileg a .pem fájlt. Az APNs-Tanúsítványfájl (.pem) az Apple Push Notification-kiszolgáló és az Intune mobileszköz-felügyeleti szolgáltatója közötti megbízhatósági kapcsolat létrehozására szolgál.  

4.  **Regisztráció engedélyezése és az APNs-tanúsítvány feltöltése** – Az iOS-eszközök regisztrációjának engedélyezéséhez töltse fel az APNs-tanúsítványt.  

    1.  A Configuration Manager konzol **Adminisztráció** munkaterületén válassza a **Felhőszolgáltatások** > **Microsoft Intune-előfizetés**elemet.  

    2.  A **Kezdőlap** **Előfizetés** csoportjában kattintson a **Platformok konfigurálása** > **iOS**elemre.  

        > [!NOTE]  
        >  Csak azt követően töltse fel az Apple Push Notification szolgáltatás (APNs) tanúsítványát, miután engedélyezte az iOS-eszközök regisztrációját a Configuration Manager konzolban.  

    3.  A **Microsoft Intune Előfizetés tulajdonságai** párbeszédpanel **iOS** lapján jelölje be az **iOS-igénylés engedélyezése** jelölőnégyzetet.  

    4.  Kattintson a **Tallózás**gombra, majd keresse meg az Apple-től letöltött APNs-tanúsítvány (.cer) fájlját. A Configuration Manager megjeleníti az APNs-tanúsítvány adatait. Az **OK** gombra kattintva mentse az APN szolgáltatás tanúsítványát az Intune-ba.  

 Ha elvégezte a beállításokat, tudassa a felhasználókkal, hogyan regisztrálhatják eszközeiket. Lásd: [Mit kell tudniuk a felhasználóknak eszközeik regisztrálásáról?](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) Ezek az információk a Microsoft Intune és a Configuration Manager által felügyelt mobileszközökre egyaránt vonatkoznak.

> [!div class="button"]
[< Előző lépés](create-service-connection-point.md)[következő lépés >  ](set-up-additional-management.md)

