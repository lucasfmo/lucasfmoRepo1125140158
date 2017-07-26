---
title: Az Endpoint Protection |} Microsoft Docs
description: "Útmutató a Configuration Manager-hierarchiában lévő ügyfélszámítógépek kártevőirtó-házirendjeit és Windows tűzfal kezelése."
ms.custom: na
ms.date: 02/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 76c90f64-d729-456b-8304-01852cd66fb6
caps.latest.revision: 11
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 3c31271f3e3ae7aa45da03b3d75fd78242330646
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---
# <a name="endpoint-protection"></a>Endpoint Protection

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

A System Center Configuration Managerben az Endpoint Protection lehetővé teszi, hogy a Configuration Manager-hierarchiában lévő ügyfélszámítógépek kártevőirtó-házirendjeit és Windows tűzfal kezelését.  

> [!IMPORTANT]  
>  Az Endpoint Protection használatával kezelheti a Configuration Manager hierarchiájában lévő ügyfelek licenc.  

 Ha az Endpoint Protection használata a Configuration Managerrel, a következő előnyöket közül választhat:  

-   Kártevőirtó-házirendek, a Windows tűzfal beállításainak konfigurálása és kezelése a Windows Defender Advanced Threat Protection számítógépek kijelölt csoportján  
-   Használja a Configuration Manager szoftverfrissítései által letöltheti a legújabb kártevőirtó-definíciós fájlok ügyfélszámítógépek naprakész állapotban tartása érdekében  
-   E-mail értesítéseket küldhet, konzolon belüli figyelést használhat és jelentéseket tekinthet meg, melyekkel tájékoztathatja a rendszergazda felhasználókat, ha kártevőket észlel az ügyfélszámítógépeken.  

A Windows 10 és Windows Server 2016-os számítógépek kezdve a Windows Defender már telepítve van. A fenti operációs rendszerek egy felügyeleti a Windows Defender-ügyfél a Configuration Manager-ügyfél telepítésekor. Windows 8.1 és korábbi számítógépek az Endpoint Protection ügyfél telepítve van a Configuration Manager-ügyféllel. A Windows Defender és az Endpoint Protection-ügyfél a következő képességekkel rendelkeznek:  

-   Kártevők és kémprogramok észlelése és eltávolítása  
-   Rootkitek észlelése és eltávolítása  
-   Kritikus biztonsági rések értékelése, automatikus definíció- és motorfrissítések  
-   Hálózati biztonsági rések észlelése a Hálózatvizsgáló rendszerrel  
-   Integráció a felhő védelmi szolgáltatás jelentések küldése a kártevőkről a Microsoftnak. Ha igénybe veszi ezt a szolgáltatást, az Endpoint Protection-ügyfél vagy a Windows Defender letöltheti a kártevőkezelési központ legfrissebb definícióit, ha azonosítatlan kártevőt észlel a számítógépen.  

> [!NOTE]  
>  Az Endpoint Protection-ügyfelet telepítheti Hyper-v-T futtató kiszolgálóra, és a támogatott operációs rendszerekkel rendelkező Vendég virtuális gépeken. Túlzott CPU-használat megelőzése érdekében az Endpoint Protection műveletek, hogy a védelmi szolgáltatás nem futtatható egyidejűleg rendelkezik beépített véletlenszerű késleltetéssel végzi.  

 Emellett az Endpoint Protection a Configuration Manager lehetővé teszi a Windows tűzfal beállításait a Configuration Manager konzolon.  

 [Példa: System Center Endpoint Protection használata a számítógépek a System Center Configuration Managerben kártevők elleni védelméhez](scenarios-endpoint-protection.md) Endpoint Protection és a Windows tűzfalon.  


## <a name="managing-malware-with-endpoint-protection"></a>Kártevők kezelése az Endpoint Protectionben  
 A Configuration Managerben az Endpoint Protection kártevőirtó-házirendek, amelyek tartalmazzák az Endpoint Protection ügyfél konfigurációk létrehozását teszi lehetővé. Ezután telepítheti a kártevőirtó-házirendeket az ügyfélszámítógépeken és figyelheti azokat a **Endpoint Protection állapota** csomópontjából **biztonsági** a a **figyelés** munkaterületet, vagy a Configuration Manager-jelentések használatával.  

 További információ:  

-   [Hozzon létre és telepítheti a kártevőirtó-házirendeket a System Center Configuration Managerben az Endpoint Protection](endpoint-antimalware-policies.md) – hozzon létre, telepítheti és figyelheti a kártevőirtó-házirendek a konfigurálható beállítások listájával  

-   [A System Center Configuration Managerben az Endpoint Protection figyelése](monitor-endpoint-protection.md) – Tevékenységjelentések, fertőzött ügyfélszámítógépek és további figyelési.  

-   [Kártevőirtó-házirendek kezelése, és a tűzfal beállításait a System Center Configuration Managerben az Endpoint Protection](endpoint-antimalware-firewall.md) -ügyfélszámítógépeken észlelt kártevők eltávolítása  


## <a name="managing-windows-firewall-with-endpoint-protection"></a>Windows tűzfal kezelése Endpoint Protectionnel  
 A Configuration Managerben az Endpoint Protection az ügyfélszámítógépeken a Windows tűzfal alapvető felügyeleti biztosít. Az egyes hálózati profiloknál megadhatja például a következő beállításokat:  

-   A Windows tűzfal engedélyezése vagy letiltása  

-   A bejövő kapcsolatok tiltása, az engedélyezett programok listáján lévőket is beleértve  

-   A felhasználó értesítése, ha a Windows tűzfal új programot blokkol  

> [!NOTE]  
>  Az Endpoint Protection csak a Windows tűzfal kezelését támogatja.  


 Szabályzatok létrehozása és telepítése a Windows tűzfal az Endpoint Protection kapcsolatos további információkért lásd: [létrehozásáról és központi telepítése a Windows tűzfal házirendek Endpoint Protection a System Center Configuration Managerben](create-windows-firewall-policies.md).  


## <a name="windows-defender-advanced-threat-protection"></a>A Windows Defender komplex veszélyforrások elleni védelem

Kezdve 1606 a Configuration Manager verziója (aktuális ág), az Endpoint Protection segítségével kezelni és megfigyelni a Windows Defender Advanced Threat Protection (ATP). A Windows Defender ATP egy új szolgáltatás, amely segítségére lesz a vállalatok számára, hogy észlelni, vizsgálja meg és a hálózat a speciális támadások válaszolni. Lásd: [Windows Defender komplex veszélyforrások elleni védelem](windows-defender-advanced-threat-protection.md).

## <a name="endpoint-protection-workflow"></a>Az Endpoint Protection munkafolyamata  
 A következő ábra segítségével megismerheti a munkafolyamatot, hogy az Endpoint Protection implementálásának a Configuration Manager-hierarchiában.  

 ![Az Endpoint Protection munkafolyamata](../media/Endpoint-Protection-Workflow.gif)  

## <a name="endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Endpoint Protection-ügyfelek Mac számítógépeken és Linux-kiszolgálókon  
 A System Center Endpoint Protection tartalmazza az Endpoint Protection-ügyfelet Linux és Mac számítógépek. Ezek az ügyfelek nem biztosít a Configuration Manager; Ehelyett a következő termékeket kell letöltenie a [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).  

-   System Center 2012 Endpoint Protection Mac rendszerre  

-   System Center 2012 Endpoint Protection Linux rendszerre  


> [!IMPORTANT]  
>  Az Endpoint Protection linuxos és Mac-es telepítési fájljainak letöltéséhez rendelkeznie kell Microsoft mennyiségi licenccel.  

 Ezeket a termékeket nem felügyelheti a Configuration Manager-konzolról. A System Center Operations Manager felügyeleti csomag azonban tartalmazza a telepítési fájlokat, így a linuxos ügyfeleket kezelheti az Operations Manager használatával.  

### <a name="how-to-get-the-endpoint-protection-client-for-mac-computers-and-linux-servers"></a>Hogyan kérhet az Endpoint Protection-ügyfelet Mac számítógépekre és Linux-kiszolgálókon

Az alábbi lépések segítségével töltse le a lemezképet fájlt tartalmazó az Endpoint Protection-ügyfélszoftver és a Mac számítógépekre és Linux kiszolgálók dokumentációjában talál.
1. Jelentkezzen be a [Microsoft Volume Licensing Service Center](https://www.microsoft.com/licensing/servicecenter/default.aspx).
2. Válassza ki a **letölti és a kulcsok** lap tetején található a webhelyen.
3. A termék szűrő **System Center Endpoint Protection (aktuális ág)**.
4. A hivatkozásra kattintva **letöltése**
5. Kattintson a **Folytatás**gombra. Több fájl, amelyek közül az egyik nevű kell megjelennie: **A System Center Endpoint Protection (aktuális ág - verzió 1606) a Linux operációs rendszert futtató és a Macintosh OS többnyelvű 32 vagy 64 bites 1507 MB ISO**.
6. Kattintson a nyíl ikonra a fájl letöltéséhez. A Fájlnév **SW_DVD5_Sys_Ctr_Endpnt_Prtctn_1606_MultiLang_EptProt_Lin_Mac_MLF_X21-30777. ISO**.

 Az Endpoint Protection-ügyfelek Linux és Mac rendszerű számítógépekre való telepítésével és felügyeletével kapcsolatos további információkért a termékek dokumentációiból tájékozódhat, amelyek a **Dokumentáció** mappában találhatók.

