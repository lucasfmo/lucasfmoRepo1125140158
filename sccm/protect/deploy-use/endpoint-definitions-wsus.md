---
title: "Az Endpoint Protection kártevő-definíciókat a WSUS |} Microsoft Docs"
definition: Learn how to configure Windows Server Updates Services to auto-approve definition updates.
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a34d9401-83e4-471d-8e23-b8042fc11c90
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 0e606b25065fa25c782d1b5f3fbf164e60733353
ms.contentlocale: hu-hu
ms.lasthandoff: 05/17/2017


---

# <a name="enable-endpoint-protection-malware-definitions-to-download-from-windows-server-update-services-wsus-for-configuration-manager"></a>Az Endpoint Protection kártevő-definíciók letöltése a Windows Server Update Services (WSUS) a Configuration Manager engedélyezése

*Vonatkozik: A System Center Configuration Manager (aktuális ág)*

 Ha a WSUS szolgáltatást használja a kártevőirtó-definíciók naprakészen tartására, beállíthatja, hogy az automatikusan hagyja jóvá a definíciófrissítéseket. Bár a Configuration Manager szoftverfrissítéseinek használata a definíciók naprakészen tartásának ajánlott módja, a felhasználók definíciófrissítések manuális kezdeményezését módszerként is konfigurálhatja a WSUS. Az alábbi eljárásokkal állíthatja be a WSUS-t a definíciók frissítési forrásaként.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-configuration-manager-software-updates"></a>A Configuration Manager szoftverfrissítések Endpoint Protection definíciófrissítéseinek szinkronizálása

1.  A Configuration Manager konzolon kattintson az **Adminisztráció**elemre.

2.  Az **Adminisztráció** munkaterületen bontsa ki a **Helykonfiguráció**csomópontot, majd kattintson a **Helyek**lehetőségre.

3.  Válassza ki a helyet, amely tartalmazza a szoftverfrissítési pontot. A **Beállítások** csoportban kattintson a **Helyösszetevők konfigurálása**, majd a **Szoftverfrissítési pont**elemre.

4.  A **Szoftverfrissítési pont összetevő tulajdonságai** párbeszédpanel **Besorolások** lapján jelölje be a **Definíciófrissítések** jelölőnégyzetet.

5.  Adja meg a WSUS által frissített **termékeket** :

    -   A Windows 8.1-es és régebbi verziók esetében a **Szoftverfrissítési pont összetevő tulajdonságai** párbeszédpanel **Termékek** lapján jelölje be a **Forefront Endpoint Protection 2010** jelölőnégyzetet.

    -   A Windows 10-es és újabb verziók esetében a **Szoftverfrissítési pont összetevő tulajdonságai** párbeszédpanel **Termékek** lapján jelölje be a **Windows Defender** és a **Windows Technical Preview 2** jelölőnégyzetet.

6.  Kattintson az **OK** gombra a **Szoftverfrissítési pont összetevő tulajdonságai** párbeszédpanel bezárásához.

 A következő eljárással konfigurálhatja az Endpoint Protection-frissítések, amikor a WSUS-kiszolgáló nincs integrálva a Configuration Manager-környezetben.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus"></a>Az Endpoint Protection definíciófrissítéseinek szinkronizálása a különálló WSUS szolgáltatásban

1.  A WSUS felügyeleti konzolján bontsa ki a **Számítógépek**csomópontot, kattintson a **Beállítások**elemre, majd kattintson a **Termékek és besorolások**elemre.

2.  Adja meg a WSUS által frissített **termékeket** :

    -   A Windows 8.1-es és régebbi verziók esetében a **Szoftverfrissítési pont összetevő tulajdonságai** párbeszédpanel **Termékek** lapján jelölje be a **Forefront Endpoint Protection 2010** jelölőnégyzetet.

    -   A Windows 10-es és újabb verziók esetében a **Szoftverfrissítési pont összetevő tulajdonságai** párbeszédpanel **Termékek** lapján jelölje be a **Windows Defender** és a **Windows Technical Preview 2** jelölőnégyzetet.

3.  A **Termékek és besorolások** párbeszédpanel **Besorolások** lapján jelölje be a **Definíciófrissítések** és a **Frissítések** jelölőnégyzetet.

## <a name="approving-definition-updates"></a>A definíciófrissítések jóváhagyása
 Az Endpoint Protection definíciófrissítéseinek jóváhagyott legyen, és le kell a WSUS-kiszolgálót, mielőtt azokat a rendelkezésre álló frissítések listáját kérő ügyfeleknek nyújtott. Az ügyfelek csatlakoznak a WSUS-kiszolgálóhoz a megfelelő frissítések kereséséhez, majd kérik a legújabb jóváhagyott definíciófrissítéseket.

### <a name="to-approve-definitions-and-updates-in-wsus"></a>A definíciók és a frissítések jóváhagyása a WSUS-ben

1.  A WSUS felügyeleti konzolján kattintson a **Frissítések**lehetőségre, majd a **Minden frissítés** lehetőségre vagy arra a frissítési osztályra, amelyet szeretne jóváhagyni.

2.  A frissítések listáján kattintson a jobb gombbal arra az egy vagy több frissítésre, amelynek engedélyezni szeretné a telepítését, majd kattintson a **Jóváhagyás**gombra.

3.  A **Frissítések jóváhagyása** párbeszédpanelen jelölje ki azt a számítógépcsoportot, amelynek engedélyezni szeretné a frissítését, és kattintson a **Telepítésre jóváhagyva**lehetőségre.

 Manuális jóváhagyás mellett is beállíthatja a definíciófrissítések automatikus jóváhagyási szabályok, és az Endpoint Protection frissíti. Ezzel konfigurálja a WSUS automatikusan jóváhagyja az Endpoint Protection definíciófrissítéseinek WSUS által letöltött.

### <a name="to-configure-an-automatic-approval-rule"></a>Automatikus jóváhagyási szabály konfigurálása

1.  A WSUS felügyeleti konzolján kattintson a **Beállítások**, majd az **Automatikus jóváhagyások**lehetőségre.

2.  A **Frissítési szabályok** lapon kattintson az **Új szabály**elemre.

3.  Az a **szabály hozzáadása** párbeszédpanel **1. lépés: Válassza a Tulajdonságok**, jelölje be a **frissítés esetén egy adott besorolásban történik** jelölőnégyzetet.

4.  A **2. lépés: A Tulajdonságok szerkesztése**, kattintson a **bármely besorolás**.

5.  Törölje az összes jelölőnégyzetet a **Definíciófrissítések**kivételével, és kattintson az **OK**gombra.

6.  Az a **szabály hozzáadása** párbeszédpanel **1. lépés: Válassza a Tulajdonságok**, jelölje be a **frissítés esetén egy adott termékben** jelölőnégyzetet.

7.  A **2. lépés: A Tulajdonságok szerkesztése**, kattintson a **bármely termék**.

8.  Törölje az összes jelölőnégyzetet a Windows 8.1-es és régebbi verzióknál a **Forefront Endpoint Protection** vagy a Windows 10-es és újabb verzióknál a **Windows Defender** kivételével, és kattintson az **OK**gombra.

9. A **3. lépés: Adjon meg egy nevet**, adja meg a szabály nevét, és kattintson a **OK**.

10. Az **Automatikus jóváhagyások** párbeszédpanelen jelölje be a jelölőnégyzetet az újonnan létrehozott szabály mezőben, és kattintson a **szabály futtatása**elemre.

> [!NOTE]
>  A WSUS-kiszolgálón és az ügyfélszámítógépeken a teljesítmény maximalizálásához utasítsa el a régi definíciófrissítéseket. A feladat elvégzéséhez automatikus jóváhagyást állíthat be a változatokhoz és automatikus elutasítást a lejárt frissítésekhez. További információért olvassa el a [938947-es számú cikket a Microsoft tudásbázisában](http://go.microsoft.com/fwlink/p/?LinkId=204078).

> [!div class="button"]
[Következő lépés >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Vissza >](endpoint-configure-alerts.md)

