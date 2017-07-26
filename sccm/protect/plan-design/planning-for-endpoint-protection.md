---
title: "Az Endpoint Protection tervezése |} Microsoft Docs"
ms.custom: na
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7610bbd3-a67f-4a09-8115-e35d40d43b42
caps.latest.revision: 16
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 6c4273dae99ec8db2cf827f463b973e876d0d35b
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-endpoint-protection-in-system-center-configuration-manager"></a>Az Endpoint Protection tervezése a System Center Configuration Managerben

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*


A System Center Configuration Managerben az Endpoint Protection lehetővé teszi, hogy a Configuration Manager-hierarchiában lévő ügyfélszámítógépek kártevőirtó-házirendjeit és Windows tűzfal kezelését.  

> [!IMPORTANT]  
>  Az Endpoint Protection használatával kezelheti a Configuration Manager hierarchiájában lévő ügyfelek licenc.  

Ha az Endpoint Protection használata a Configuration Managerrel, a következő előnyöket közül választhat:  

-   Kártevőirtó-házirendek, a Windows tűzfal beállításainak konfigurálása és kezelése a Windows Defender Advanced Threat Protection számítógépek kijelölt csoportján  

-   Használja a Configuration Manager szoftverfrissítései által letöltheti a legújabb kártevőirtó-definíciós fájlok ügyfélszámítógépek naprakész állapotban tartása érdekében  

-   E-mail értesítéseket küldhet, konzolon belüli figyelést használhat és jelentéseket tekinthet meg, melyekkel tájékoztathatja a rendszergazda felhasználókat, ha kártevőket észlel az ügyfélszámítógépeken.  

Windows 10-es számítógépeknek a végpontvédelem kezeléséhez nincs szükség semmilyen további ügyfél. A Windows 8.1 és korábbi számítógépek az Endpoint Protection telepítése mellett a Configuration Manager-ügyfél a saját ügyfelét. Az Endpoint Protection-ügyfél a következő funkciókkal rendelkezik:  

-   Kártevők és kémprogramok észlelése és eltávolítása  

-   Rootkitek észlelése és eltávolítása  

-   Kritikus biztonsági rések értékelése, automatikus definíció- és motorfrissítések  

-   Hálózati biztonsági rések észlelése a Hálózatvizsgáló rendszerrel  

-   Integráció a felhő védelmi szolgáltatás jelentések küldése a kártevőkről a Microsoftnak. Ha igénybe veszi ezt a szolgáltatást, a Windows Defender vagy az Endpoint Protection-ügyfél letöltheti a legújabb definíciókat a kártevő-kezelési központ Ha azonosítatlan kártevőt észlel a számítógépen.  

> [!NOTE]  
>  Az Endpoint Protection-ügyfelet telepítheti Hyper-v-T futtató kiszolgálóra, és a támogatott operációs rendszerekkel rendelkező Vendég virtuális gépeken. Túlzott CPU-használat megelőzése érdekében a Endpoint Protection műveletek beépített, véletlenszerű késleltetés van a, hogy a szolgáltatások nem futtatható egyidejűleg.  

  Emellett az Endpoint Protection a Configuration Manager lehetővé teszi a Windows tűzfal beállításait a Configuration Manager konzolon.  

 [Példa: System Center Endpoint Protection használata a számítógépek a System Center Configuration Managerben kártevők elleni védelméhez](../deploy-use/scenarios-endpoint-protection.md) bemutatja, hogyan lehet konfigurálni, és az Endpoint Protection és a Windows tűzfal kezelése.  

## <a name="managing-malware-with-endpoint-protection"></a>Kártevők kezelése az Endpoint Protectionben  

A Configuration Managerben az Endpoint Protection kártevőirtó-házirendek, amelyek tartalmazzák az Endpoint Protection ügyfél konfigurációk létrehozását teszi lehetővé. Ezután telepítheti a kártevőirtó-házirendeket az ügyfélszámítógépeken és figyelheti azokat a **Endpoint Protection állapota** csomópontja a **figyelés** munkaterületet, vagy a Configuration Manager-jelentések használatával.  

 További információ:  

-   [Hozzon létre és telepítheti a kártevőirtó-házirendeket a System Center Configuration Managerben az Endpoint Protection](../deploy-use/endpoint-antimalware-policies.md) – hozzon létre, telepítheti és figyelheti a kártevőirtó-házirendek a konfigurálható beállítások listájával  

-   [A System Center Configuration Managerben az Endpoint Protection figyelése](../deploy-use/monitor-endpoint-protection.md) – Tevékenységjelentések, fertőzött ügyfélszámítógépek és további figyelési.   

-   [Kártevőirtó házirendek kezelése és a tűzfal beállításait a System Center Configuration Managerben az Endpoint Protection](../deploy-use/endpoint-antimalware-firewall.md) – a házirend prioritásának módosításához [kártevőirtó](../deploy-use/endpoint-antimalware-firewall.md#manage-antimalware-policies) vagy [tűzfal](../deploy-use/endpoint-antimalware-firewall.md#manage-windows-firewall-policies), [az ügyfélszámítógépeken észlelt kártevők](../deploy-use/endpoint-antimalware-firewall.md#remediate-detected-malware), és más feladatok

## <a name="managing-windows-firewall-with-endpoint-protection"></a>Windows tűzfal kezelése Endpoint Protectionnel  
 A Configuration Managerben az Endpoint Protection az ügyfélszámítógépeken a Windows tűzfal alapvető felügyeleti biztosít. Az egyes hálózati profiloknál megadhatja például a következő beállításokat:  

-   A Windows tűzfal engedélyezése vagy letiltása  

-   A bejövő kapcsolatok tiltása, az engedélyezett programok listáján lévőket is beleértve  

-   A felhasználó értesítése, ha a Windows tűzfal új programot blokkol  

> [!NOTE]  
>  Az Endpoint Protection csak a Windows tűzfal kezelését támogatja.  

  Szabályzatok létrehozása és telepítése a Windows tűzfal az Endpoint Protection kapcsolatos további információkért lásd: [létrehozásáról és központi telepítése a Windows tűzfal házirendek Endpoint Protection a System Center Configuration Managerben](../deploy-use/create-windows-firewall-policies.md).  

## <a name="windows-defender-advanced-threat-protection"></a>A Windows Defender komplex veszélyforrások elleni védelem

Kezdve 1606 a Configuration Manager verziója (aktuális ág), az Endpoint Protection segítségével kezelni és megfigyelni a Windows Defender Advanced Threat Protection (ATP). A Windows Defender ATP egy új szolgáltatás, amely segítségére lesz a vállalatok számára, hogy észlelni, vizsgálja meg és a hálózat a speciális támadások válaszolni. Lásd: [Windows Defender komplex veszélyforrások elleni védelem](../deploy-use/windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Az Endpoint Protection munkafolyamata  
 A következő ábra segítségével megismerheti a munkafolyamatot, hogy az Endpoint Protection implementálásának a Configuration Manager-hierarchiában.  

 ![Az Endpoint Protection munkafolyamata](../media/Endpoint-Protection-Workflow.gif)

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Endpoint Protection-ügyfelek Mac számítógépeken és Linux-kiszolgálókon  
 A System Center Endpoint Protection-ügyfelet tartalmaz, a Linux és Mac számítógépek számára. Ezek az ügyfelek nem biztosít a Configuration Manager; Ehelyett a következő termékeket kell letöltenie a [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

> [!IMPORTANT]  
>  Az Endpoint Protection linuxos és Mac-es telepítési fájljainak letöltéséhez rendelkeznie kell Microsoft mennyiségi licenccel.  

 Ezeket a termékeket nem felügyelheti a Configuration Manager-konzolról. A System Center Operations Manager felügyeleti csomag azonban tartalmazza a telepítési fájlokat, így a linuxos ügyfeleket kezelheti az Operations Manager használatával.  

 Az Endpoint Protection-ügyfelek Linux és Mac rendszerű számítógépekre való telepítésével és felügyeletével kapcsolatos további információkért a termékek dokumentációiból tájékozódhat, amelyek a **Dokumentáció** mappában találhatók.

## <a name="best-practices-for-endpoint-protection-in-configuration-manager"></a>A Endpoint Protection bevált gyakorlatai a Configuration Managerben  
 A System Center 2012 Configuration Managerben futó Endpoint Protectionben a következő bevált gyakorlatokat használhatja.  

### <a name="configure-custom-client-settings-for-endpoint-protection"></a>Az Endpoint Protection egyedi ügyfélbeállítások konfigurálása  
 Az Endpoint Protection ügyfélbeállítások konfigurálásakor ne használja az alapértelmezett ügyfélbeállításokat, mert a beállítások a hierarchiában lévő összes számítógépre vonatkoznak. Ehelyett használhat egyéni ügyfélbeállításokat, amelyeket hozzárendelhet a hierarchiában lévő számítógép-gyűjteményekhez.  

 Egyedi ügyfélbeállítások konfigurálásakor a következő lehetőségek érhetők el:  

-   Testre szabhatja környezete egyes részeinek kártevőirtó és biztonsági beállításait.  
-   Tesztelheti a Endpoint Protection futó számítógépek egy kis csoportján, mielőtt telepítené az alkalmazást az egész hierarchiát.  
-   A gyűjteménybe, az Endpoint Protection-ügyfél központi telepítésének fázisait időszakosan felvett újabb ügyfelekkel.  

### <a name="distributing-definition-updates-by-using-software-updates"></a>Szoftverfrissítések általi definíciófrissítés-terjesztés  
 Ha a Configuration Manager szoftverfrissítések segítségével terjeszti a definíciófrissítéseket, fontolja meg helyezi el egy csomagot, amely nem tartalmaz más szoftverfrissítést. Ezáltal a definíciófrissítési csomag kisebb lesz, és gyorsabban replikálódhat a terjesztési pontokra.

