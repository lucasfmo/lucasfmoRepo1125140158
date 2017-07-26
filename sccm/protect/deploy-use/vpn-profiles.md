---
title: A VPN-profilok a System Center Configuration Managerben |} Microsoft Docs
description: "Ismerje meg, hogyan használható a VPN-profilok a System Center Configuration Manager VPN-beállításokat telepíthet a szervezethez tartozó felhasználók."
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: e07a80c1a59043b74cda7219f78c5fef66989ba8
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>A VPN-profilok a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A VPN-profilok a System Center Configuration Manager (más néven a ConfigMgr vagy a SCCM) segítségével a VPN-beállításokat telepíthet a szervezethez tartozó felhasználók. Ezen beállítások telepítésével lecsökkentheti a vállalati hálózaton lévő erőforrások eléréséhez szükséges végfelhasználói beavatkozást.  

 Például szeretne a beállítások a Windows RT operációs rendszert futtató minden eszköz a vállalati hálózaton lévő egyik fájlmegosztáshoz való kapcsolódáshoz szükséges kiépítéséhez. Egy szükséges ahhoz, hogy csatlakoznak a vállalati hálózathoz, majd ezt a profilt minden felhasználó számára telepíti a hierarchiában található Windows RT rendszerű eszközökre beállításokat tartalmazó VPN-profilt hozhat létre. Windows RT-eszközök felhasználói tekintse meg a VPN-kapcsolat rendelkezésre álló hálózatok listájában, és ezt a hálózatot minimális erőfeszítéssel csatlakozhatnak.  

 VPN-profil létrehozásakor számos biztonsági beállításai, többek között olyan kiszolgáló ellenőrzési és ügyfél-hitelesítési tanúsítvánnyal, a System Center Configuration Manager tanúsítványprofilok használatával kiépített is megadhat. További információk a tanúsítványprofilokról: [Tanúsítványprofilok a System Center Configuration Managerben](introduction-to-certificate-profiles.md).  

 Az alábbi szakaszok azt ismertetik, hogy mely eszközökre, konfigurálhatja a VPN-profilok a Configuration Manager használata.

 Lásd: [a mobileszközök VPN-profilok](/sccm/mdm/deploy-use/create-vpn-profiles) áttekintheti az eszközöket beállíthatja a Configuration Manager használata a Microsoft Intune-nal.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>A VPN-profilok a Configuration Manager használata esetén  
 A következő táblázat ismerteti a VPN-profilok is konfigurálhatja a különböző eszközplatformokat.  

|Kapcsolat típusa|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|Nem|Nem|Nem|Nem|  
|**Pulse Secure**|Igen|Nem|Igen|Igen|  
|**F5 Edge Client**|Igen|Nem|Igen|Igen|  
|**Dell SonicWALL Mobile Connect**|Igen|Nem|Igen|Igen|  
|**Check Point mobil VPN**|Igen|Nem|Igen|Igen|  
|**Microsoft SSL (SSTP)**|Igen|Igen|Igen|Nem|  
|**Microsoft Automatic**|Igen|Igen|Igen|Nem|  
|**IKEv2**|Igen|Igen|Igen|Nem|  
|**PPTP**|Igen|Igen|Igen|Nem|  
|**L2TP**|Igen|Igen|Igen|Nem|  

### <a name="next-steps"></a>További lépések  
 A következő témakörök segítségével, tervezése, konfigurálásához, működtetéséhez és karbantartása a Configuration Manager VPN-profilok.  

-   [A System Center Configuration Manager VPN-profilok használatának előfeltételei](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Biztonság és adatvédelem a VPN-profilok a System Center Configuration Managerben](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)

