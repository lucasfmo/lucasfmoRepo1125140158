---
title: "Adatok és a helyinfrastruktúra védelme |} Microsoft Docs"
description: "Megtudhatja, hogyan megvédeni a szervezet erőforrásaihoz kitettség vagy rosszindulatú támadás a System Center Configuration Managerrel."
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2117f786-d521-4790-9e8d-ec096c63c9d7
caps.latest.revision: 8
author: Robstack
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8679df3f8a3b692391537bacd6144a4f2fae357b
ms.openlocfilehash: d527cb4bfb55ca50c8d2a0fed7c427af5747fe99
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="protect-data-and-site-infrastructure-with-system-center-configuration-manager"></a>Az adatok és a hely infrastruktúrájának védelme a System Center Configuration Managerrel

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


Az infrastruktúra és az adatok rosszindulatú támadások és más veszélyforrások elleni védelme érdekében olyan rendszerre van szüksége, amelyben a felhasználók biztonságosan férhetnek hozzá a szervezet erőforrásaihoz. Az alábbi témakörök ismerteti a System Center Configuration Manager (más néven a ConfigMgr vagy a SCCM) használata a hozzáférés engedélyezését, és hogyan védheti a szervezet erőforrásaihoz.  

-   A VPN-kapcsolat VPN-profilok használatával való engedélyezésével megkönnyítheti a felhasználók számára a vállalati erőforrások elérését. További információ: [VPN-profilok a System Center Configuration Managerben](../deploy-use/vpn-profiles.md).  

-   A Wi-Fi profilok olyan eszközök és erőforrások használatát teszik lehetővé, amelyekkel a szervezetnél található eszközökön könnyebben lehet létrehozni, telepíteni és figyelemmel kísérni a vezeték nélküli hálózati beállításokat. Ezeknek a beállításoknak a központi telepítésével minimálisra csökkenthető a végfelhasználók részéről az erőfeszítés, amely a vállalati vezeték nélküli hálózathoz való kapcsolódáshoz szükséges. További információ: [Wi-Fi profilok a System Center Configuration Managerben](/sccm/protect/deploy-use/create-wifi-profiles).  

-   [A tanúsítványprofilok a System Center Configuration Managerben](../deploy-use/introduction-to-certificate-profiles.md) ismerteti, hogyan lehet ellátja az eszközöket a felhasználók a vállalati erőforrások eléréséhez szükséges tanúsítványokat.  

-   [A System Center Endpoint Protection](../deploy-use/endpoint-protection.md) lehetővé teszi az ügyfélszámítógépek kártevőirtó-házirendjeit és a Windows tűzfal kezelését.  

-   Feltételes hozzáférés segítségével biztosíthatja a levelezés és más szolgáltatásokat a Microsoft Intune-nal regisztrált eszközök segítségével, a [kezelése a System Center Configuration Manager-szolgáltatásokhoz való hozzáférés](../deploy-use/manage-access-to-services.md).  

-   Az e-mail profilok eszközkészletet és erőforrásokat biztosítanak az e-mail beállítások eszközökön történő létrehozásához, központi telepítéséhez és figyeléséhez. Ez lehetővé teszi, hogy a felhasználók személyes eszközükön beállítások megadása nélkül érhessék el vállalatuk e-mail szolgáltatását. További információ: [E-mail-profilok a System Center Configuration Managerben](../deploy-use/introduction-to-email-profiles.md).  

-   Configuration Manager lehetővé teszi az integrációt a Windows Hello-üzleti (korábbi nevén Microsoft Passport for Work), amely egy alternatív bejelentkezési módszer, amely Active Directoryt vagy egy Azure Active Directory-fiókot használ jelszó, intelligens kártya vagy virtuális intelligens kártya helyett. További információ: [üzleti beállításait a System Center Configuration Managerben a Windows Hello-](../deploy-use/windows-hello-for-business-settings.md).  

