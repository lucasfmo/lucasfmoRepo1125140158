---

title: "Konfigurálhatja az Endpoint Protection |} Microsoft Docs"
description: "Ismerje meg, válassza ki, és módszerek konfigurálása az Endpoint Protection a System Center Configuration Managerben a kártevőirtó-definíciók naprakészen tartása az ügyfélszámítógépeken."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 537dd2a7-4e44-4877-b8dd-5e1499407f8d
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: b5da7900a4f8e2f330c4dcb2cac00b45099bd909
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017



---

#  <a name="configure-definition-updates-for-endpoint-protection"></a>Az Endpoint Protection definíciófrissítéseinek konfigurálása  

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Az Endpoint Protection a System Center Configuration Managerben segítségével többféle módszer bármelyikét naprakészen a kártevőirtó-definíciókat az ügyfélszámítógépeken a hierarchiában. Az ebben a témakörben olvasható információk segítséget nyújtanak e módszerek kiválasztásához és konfigurálásához.

 A kártevőirtó-definíciók frissítéséhez az alábbi módszerek közül használhat egyet vagy többet is:

-   [A Configuration Managerből terjesztett frissítések](endpoint-definitions-configmgr.md) -ezt a módszert használja a Configuration Manager szoftverfrissítések definíció- és keresőmotor-frissítéseket telepíthet a hierarchiában található számítógépekre.

-   [A Windows Server Update Services (WSUS) terjesztett frissítések](endpoint-definitions-wsus.md) – Ez a módszer a WSUS infrastruktúrát használja a definíció- és keresőmotor-frissítések képes biztosítani a számítógépekre.

-   [A Microsoft Update rendszerből terjesztett frissítések](endpoint-definitions-microsoft-updates.md) – Ez a módszer lehetővé teszi, hogy a számítógépek közvetlen csatlakoztatása a Microsoft Update definíció- és keresőmotor-frissítések letöltéséhez. Ez a módszer hasznos lehet a vállalati hálózathoz ritkán csatlakozó számítógépek esetében.

-   [A Microsoft Malware Protection Center rendszerből terjesztett frissítések](endpoint-definitions-protection-center.md) – Ez a módszer definíciófrissítések töltik le a Microsoft Malware Protection Centerben.

-   [Frissítések az UNC fájlmegosztásokból](endpoint-definitions-network.md) – ezzel a módszerrel mentheti a legújabb definíció- és keresőmotor-frissítések megosztott helyre a hálózaton. Az ügyfelek ezután hozzáférhetnek a hálózathoz a frissítések telepítéséhez.

 Több forrást is konfigurálhat a definíciófrissítésekhez, és szabályozhatja azok értékelési és alkalmazási sorrendjét. Ezt **A definíciófrissítések forrásainak konfigurálása** párbeszédpanelen teheti meg a kártevőirtó-házirend létrehozásakor.

> [!IMPORTANT]
>  Windows 10 rendszerű számítógépeken az Endpoint Protection, hogy a Windows Defender kártevő-definíciók frissítése kell konfigurálni.

## <a name="how-to-configure-definition-update-sources"></a>A definíciófrissítési források konfigurálása
 Az alábbi eljárással konfigurálhatja a definíciófrissítések forrásait az egyes kártevőirtó-házirendekkel való használatra.

1.  Kattintson a Configuration Manager-konzolon az **Eszközök és megfelelőség**elemre.

2.  Az **Eszközök és megfelelőség** munkaterületen bontsa ki az **Endpoint Protection**csomópontot, majd kattintson a **Kártevőirtó-házirendek**lehetőségre.

3.  Nyissa meg az **Alapértelmezett kártevőirtó-házirend** tulajdonságlapját, vagy hozzon létre egy új kártevőirtó-házirendet. Kártevőirtó-házirendek létrehozásával kapcsolatos további információkért lásd: [létrehozása és a System Center Configuration Managerben az Endpoint Protection kártevőirtó-házirendek telepítése](endpoint-antimalware-policies.md).

4.  A kártevőirtó Tulajdonságok párbeszédpanelének **Definíciófrissítések** szakaszában kattintson a **Forrás beállítása**elemre.

5.  **A definíciófrissítések forrásainak konfigurálása** párbeszédpanelen jelölje ki a definíciók frissítéséhez használandó forrásokat. A források felhasználási sorrendjének módosításához kattintson a **Fel** vagy a **Le** nyílra.

6.  Kattintson az **OK** gombra **A definíciófrissítések forrásainak konfigurálása** párbeszédpanel bezárásához.

## <a name="configure-endpoint-protection-definitions"></a>Endpoint Protection definícióinak konfigurálása

-   [A Configuration Managerből terjesztett frissítések](endpoint-definitions-configmgr.md) -ezt a módszert használja a Configuration Manager szoftverfrissítések definíció- és keresőmotor-frissítéseket telepíthet a hierarchiában található számítógépekre.

-   [A Windows Server Update Services (WSUS) terjesztett frissítések](endpoint-definitions-wsus.md) – Ez a módszer a WSUS infrastruktúrát használja a definíció- és keresőmotor-frissítések képes biztosítani a számítógépekre.

-   [A Microsoft Update rendszerből terjesztett frissítések](endpoint-definitions-microsoft-updates.md) – Ez a módszer lehetővé teszi, hogy a számítógépek közvetlen csatlakoztatása a Microsoft Update definíció- és keresőmotor-frissítések letöltéséhez. Ez a módszer hasznos lehet a vállalati hálózathoz ritkán csatlakozó számítógépek esetében.

-   A Microsoft Malware Protection Center - rendszerből terjesztett frissítések ezt a módszert töltik le definíciófrissítéseket a Microsoft Malware Protection Centerben.

-   [Frissítések az UNC fájlmegosztásokból](endpoint-definitions-network.md) – ezzel a módszerrel mentheti a legújabb definíció- és keresőmotor-frissítések megosztott helyre a hálózaton. Az ügyfelek ezután hozzáférhetnek a hálózathoz a frissítések telepítéséhez.

