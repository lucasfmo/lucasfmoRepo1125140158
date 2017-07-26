---
title: "E-mail profilok használatának előfeltételei |} Microsoft Docs"
description: "További tudnivalók az e-mail profilok a System Center Configuration Manager és a függőségek, külsőleg mind a terméken belüli."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dccf0b73-43bd-4545-8914-114168ebad36
caps.latest.revision: 5
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: 451317db1d7aab888c03d1a099b9ce25311e06d0
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="email-profile-prerequisites"></a>E-mail profil Előfeltételek

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

E-mail profilok a System Center Configuration Managerben olyan függőségekkel rendelkeznek, külsőleg, mind a terméken belül.  

## <a name="configuration-manager-dependencies"></a>A Configuration Manager függőségei  

|Függőség|További információ|  
|----------------|----------------------|  
|Az e-mail profilok kezeléséhez rendelkeznie kell a megfelelő biztonsági engedélyekkel.|A vállalati erőforrás-hozzáférési beállítások, például az e-mail profilok kezeléséhez az alábbi biztonsági engedélyekkel kell rendelkeznie:<br /><br /> -A megtekintése, és riasztásokat és jelentéseket az e-mail profilok kezelése: **Hozzon létre**, **törlése**, **módosítás**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** engedélyeit a **riasztások** objektum.<br /><br /> -Hozhat létre, és a tanúsítványprofilok kezeléséhez: **Szerzői házirend**, **jelentés módosítása**, **olvasási** és **jelentés futtatása** engedélyeit a **Tanúsítványprofil** objektum.<br /><br /> -Az e-mail profilok telepítésének kezelése: **Konfigurációs házirendek központi telepítése**, **ügyfélállapot-riasztás módosítása**, **olvasási**, és **erőforrás olvasása** engedélyeit a **gyűjtemény** objektum.<br /><br /> -Az összes konfigurálási házirend kezeléséhez: **Hozzon létre**, **törlése**, **módosítás**, **olvasási** és **biztonsági hatókör megadása** engedélyeit a **konfigurációs házirend** objektum.<br /><br /> -E-mail profilokhoz kapcsolódó lekérdezések futtatásához: **Olvasási** engedély a **lekérdezés** objektum.<br /><br /> -Az e-mail profilok adatainak megtekintése a System Center Configuration Manager konzolon: **Olvasási** engedély a **hely** objektum.<br /><br /> -Az e-mail-profilokra vonatkozó állapotüzenetek megtekintéséhez: **Olvasási** engedély a **állapotüzenetek** objektum.<br /><br /> -Hozhat létre, és az e-mail profilok kezeléséhez: **Szerzői házirend**, **jelentés módosítása**, **olvasási**, és **jelentés futtatása** engedélyeit a **Communications Provisioning Profile** objektum.<br /><br /> A **Company Resource Access Manager** biztonsági szerepkör tartalmazza azokat az engedélyeket, amelyek a System Center Configuration Managerben az e-mail profilok kezeléséhez szükségesek. További információ: [A biztonság konfigurálása a System Center Configuration Managerben](../../core/plan-design/security/configure-security.md).|  
|A mail Active Directory-attribútum|Ha szeretné létrehozni a felhasználók e-mail címét az e-mail profilban a felhasználó elsődleges SMTP-címének használatával, a System Center Configuration Manager felhasználófelderítési funkcióját úgy kell konfigurálni, felderítéséhez a **mail** (Ez alapértelmezés szerint van konfigurálva) Active Directory-attribútumot.|  

## <a name="external-dependencies"></a>Külső függőségek  

|Függőség|További információ|  
|----------------|----------------------|  
|A mail Active Directory-attribútum|Ha szeretné létrehozni a felhasználók e-mail címét az e-mail profilban a felhasználó elsődleges SMTP-címének használatával, a címnek már léteznie kell a **mail** Active Directory-attribútumban.<br /><br /> További információt a Windows Server dokumentációjában talál.|

