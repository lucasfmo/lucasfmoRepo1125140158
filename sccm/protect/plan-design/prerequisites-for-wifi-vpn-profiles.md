---
title: "Wi-Fi és VPN-profilok Előfeltételek |} Microsoft Docs"
description: "További információk a tanúsítványprofilokat, a Wi-Fi profilok és a VPN-profilok a System Center Configuration Managerben kezeléséhez szükséges biztonsági engedélyekkel."
ms.custom: na
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d2dacb2d-ab3b-42a2-8dc8-94da31f993c2
caps.latest.revision: 5
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31b68ede677df8b86412a334d1d100041a0e659e
ms.openlocfilehash: 309b0363f9b3ec4a31b8323b9e64c9f73060c281
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Wi-Fi és VPN-profilok a System Center Configuration Manager használatának előfeltételei

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Wi-Fi és VPN-profilok a System Center Configuration Manager csak a terméken belüli függőségekkel rendelkeznek.  

 A következő biztonsági engedélyekkel kell rendelkeznie ahhoz, hogy kezelni tudja a vállalat erőforrásainak hozzáférési beállításait, így a tanúsítványprofilokat, a WIFI-profilokat és a VPN-profilokat:  

-   Megtekintéséhez, és a Wi-Fi és a profilok riasztásainak és jelentéseinek kezelése: **Hozzon létre**, **törlése**, **módosítás**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** a a **riasztások** objektum.  

-   Hozzon létre, és a tanúsítványprofilok kezeléséhez: **Szerzői házirend**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** a a **Tanúsítványprofil** objektum.  

-   Wi-Fi, tanúsítvány és a VPN-profilok központi telepítésének kezeléséhez: **Konfigurációs házirendek központi telepítése**, **ügyfélállapot-riasztás módosítása**, **olvasási**, és **erőforrás olvasása** a a **gyűjtemény** objektum.  

-   Az összes konfigurálási házirend kezeléséhez: **Hozzon létre**, **törlése**, **módosítás**, **olvasási**, és **biztonsági hatókör megadása** a a **konfigurációs házirend** objektum.  

-   Wi-Fi és VPN-profilokhoz kapcsolódó lekérdezések futtatásához: **Olvasási** engedély a **lekérdezés** objektum.  

-   Wi-Fi és VPN-profilok adatainak megtekintése a System Center Configuration Manager konzolon: **Olvasási** engedély a **hely** objektum.  

-   Wi-Fi és VPN-profilokra vonatkozó állapotüzenetek megtekintéséhez: **Olvasási** engedély a **állapotüzenetek** objektum.  

-   Hozzon létre, és módosítsa a megbízható Hitelesítésszolgáltatói tanúsítvány profilja: **Szerzői házirend**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** a a **megbízható Hitelesítésszolgáltatói tanúsítvány profilja** objektum.  

-   Hozzon létre, és a VPN-profilok kezeléséhez: **Szerzői házirend**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** a a **VPN-profil** objektum.  

-   Hozzon létre és Wi-Fi profilok kezeléséhez: **Szerzői házirend**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** a a **Wi-Fi profil** objektum.  

 A **Company Resource Access Manager** biztonsági szerepkör tartalmazza azokat az engedélyeket, a System Center Configuration Manager Wi-Fi profilok kezeléséhez szükségesek. További információ: [A biztonság konfigurálása a System Center Configuration Managerben](../../core/plan-design/security/configure-security.md).

