---
title: "Konfigurálhatja az Endpoint Protection |} Microsoft Docs"
description: "Ismerje meg, hogyan állíthat be a Configuration Manager frissítse és terjessze a Windows Defender kártevő-definíciókat."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a8218e23743dafaf8ff1166142cf2dcca1212133
ms.openlocfilehash: 6917644d6719a1ca636713aa5aebf277927123c8
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="configure-endpoint-protection"></a>Endpoint Protection konfigurálása

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

Mielőtt Endpoint Protection használatával kezelheti a biztonsági és a Configuration Manager ügyfél-számítógépeken kártevő szoftverek, elvégezhető kell az ebben a témakörben részletesen ismertetett konfigurációs lépéseket.  

## <a name="how-to-configure-endpoint-protection-in-configuration-manager"></a>Az Endpoint Protection konfigurálása a Configuration Managerben  
 Az Endpoint Protection a Configuration Manager alkalmazásban van a termék külső és függőségei.  

### <a name="steps-to-configure-endpoint-protection-in-configuration-manager"></a>Lépések végrehajtásával konfigurálhatja az Endpoint Protection a Configuration Managerben  
 A következő táblázatban megtalálja az Endpoint Protection szoftver használatának lépéseivel és részleteivel, valamint a konfigurálással kapcsolatos további információkat.  

> [!IMPORTANT]  
>  Ha az endpoint protection Windows 10-es számítógépeken kezeli, majd konfigurálnia kell frissítse és terjessze a Windows Defender kártevő-definíciókat a Configuration Manager. A Windows Defender a Windows 10 de SCEPInstall kell lennie az Endpoint Protection telepítve, és egyéni ügyfélbeállítások (**5. lépés** alatt) továbbra is szükséges.  

|Lépések|Részletek|  
|-----------|-------------|  
|**1. lépés:** [Az Endpoint Protection pont helyrendszer-szerepkör létrehozása](endpoint-protection-site-role.md)|Az Endpoint Protection használata előtt telepítenie kell az Endpoint Protection-pont helyrendszerszerepkört. Csak egy helyrendszer-kiszolgálóra lehet telepíteni, és a központi adminisztrációs hely vagy önálló elsődleges hely hierarchiájának a tetejére kell telepíteni. |  
|**2. lépés:** [Az Endpoint Protection riasztások konfigurálása](endpoint-configure-alerts.md)|A riasztások tájékoztatják a rendszergazdát bizonyos eseményekről, például a kártevők általi fertőzésről. A riasztások a **Figyelés** munkaterület **Riasztások** csomópontjában jelennek meg, vagy elküldhetők e-mailben a megadott felhasználóknak. |  
|**3. lépés:** [Endpoint Protection-ügyfelek a definíciófrissítések forrásainak konfigurálása](endpoint-definition-updates.md)|Az Endpoint Protection beállítható úgy, hogy a különböző forrásokból használja a definíciófrissítések letöltésére. |  
|**4. lépés:** [Az alapértelmezett kártevőirtó-házirend konfigurálása és egyéni kártevőirtó-házirendek létrehozása](endpoint-antimalware-policies.md)|Az alapértelmezett kártevőirtó-házirend vonatkozik, az Endpoint Protection-ügyfél telepítésekor. Alapértelmezés szerint a rendszer minden hatályba helyezett egyéni házirendet alkalmaz az ügyfél telepítését követő 60 percen belül. Győződjön meg arról, hogy kártevőirtó-házirendek konfigurálta, az Endpoint Protection ügyfél telepítése előtt. |  
|**5. lépés:** [Az Endpoint Protection egyedi ügyfélbeállítások konfigurálása](endpoint-protection-configure-client.md)|Egyéni ügyfélbeállítások segítségével a hierarchiában lévő gyűjtemény számítógépeire Endpoint Protection beállításainak konfigurálása.<br /><br /> Megjegyezés: Ne konfigurálja az Endpoint Protection-ügyfél alapértelmezett beállításait, ha nem biztos, hogy ezek a beállítások a hierarchiában lévő összes számítógépre alkalmazni szeretné. |  

